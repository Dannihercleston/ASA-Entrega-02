# ASA-Entrega-02

Este projeto entrega um **Microserviço HTTP com Docker Compose** para os seguintes serviços:

- ✅ Servidor DNS com uma zona primária (`asa.br`)
- ✅ Servidor proxy reverso (NGINX) com certificado SSL
- ✅ Dois servidores web com páginas HTML personalizadas acessadas via proxy

---

## 📁 Estrutura do Projeto


ASA-Entrega-02/
├── docker-compose.yml # Orquestra os serviços
├── proxy/
│ ├── nginx.conf # Configuração do proxy reverso
│ └── certs/
│ ├── cert.pem # Certificado SSL (autoassinado)
│ └── key.pem # Chave privada do certificado
├── web1/
│ └── index.html # Página personalizada 1
├── web2/
│ └── index.html # Página personalizada 2
├── dns/
│ ├── named.conf # Configuração principal do BIND9
│ └── db.asa.br # Zona DNS primária
└── README.md # Documentação do projeto




---

## 🚀 Como Executar

### 1. Clone o repositório:

````
git clone https://github.com/Dannihercleston/ASA-Entrega-02
cd ASA-Entrega-02
````
Gere o certificado SSL (caso ainda não tenha):
````
openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
  -keyout proxy/certs/key.pem \
  -out proxy/certs/cert.pem \
  -subj "/CN=asa.br"
````

Suba a infraestrutura com Docker Compose:
````
docker compose up -d
````
🌐 Acesse os Serviços

    https://asa.br/web1 → Página Web 1

    https://asa.br/web2 → Página Web 2

⚠️ O navegador pode emitir um alerta de certificado, pois o SSL é autoassinado. Clique em "Avançado" para prosseguir.


🔍 Testes e Validações
Verificar funcionamento do proxy com SSL:

````
curl -kI https://asa.br/web1
curl -kI https://asa.br/web2
````
Verificar resolução DNS (opcional):
````
dig @asa.br
````
🛠️ Tecnologias Utilizadas

    Docker

    Docker Compose

    NGINX

    OpenSSL (para certificados SSL)

    BIND9 (DNS)

    HTML/CSS básico

