# Gerenciamento de Instâncias EC2 na AWS

## Descrição do Projeto  
Este repositório foi criado como parte do **Desafio de Projeto da DIO**, com o objetivo de consolidar os conhecimentos sobre **gerenciamento de instâncias EC2** na **Amazon Web Services (AWS)**.  
Durante a prática, criei uma instância EC2 configurada com a **AMI Amazon Linux 2023 Kernel 6.12**, utilizando automação via **User Data** para instalação e configuração de um servidor web Apache.

---

## 🎯 Objetivos de Aprendizagem
- Criar e configurar uma instância EC2 na AWS.  
- Compreender o funcionamento de AMIs, tipos de instância e VPCs.  
- Automatizar a instalação de serviços com scripts de inicialização.  
- Registrar e documentar o processo técnico no GitHub.

---

## ⚙️ Configuração da Instância EC2

| **Item** | **Configuração** |
|-----------|------------------|
| **AMI** | Amazon Linux 2023 (Kernel 6.12) |
| **Tipo de instância** | t3.micro |
| **Par de chaves** | Prossegui sem par de chaves |
| **VPC** | Lab VPC (pré-configurada) |
| **Grupo de segurança** | Criei apenas uma regra de entrada http |
| **Armazenamento** | 8 GB padrão EBS |
| **Script de inicialização (User Data)** | Instalação e configuração automática do servidor Apache |

---

## 🧩 Script Utilizado no User Data
O script abaixo foi adicionado no campo **“Dados do Usuário”** durante a criação da instância EC2.  
Ele realiza a instalação e configuração automática de um servidor Apache, cria uma página HTML simples e garante que o serviço inicie automaticamente com o sistema.

```bash
#!/bin/bash
# Atualiza o sistema
yum update -y

# Instala o servidor Apache (httpd)
yum install -y httpd

# Inicia o serviço e configura para inicializar automaticamente
systemctl enable httpd
systemctl start httpd

# Cria uma página web simples
echo '<html><h1>Hello From Your Web Server!</h1></html>' > /var/www/html/index.html
```

---

## 📸 Prints da Instância

### Diagrama do Projeto 

> 🧩 *Diagrama criado por mim como parte do desafio para representar a arquitetura do projeto.*

![Diagrama](/1.Gerenciando_Instancias_EC2/img/diagrama-desafio-dio.drawio.png)

### Instância em execução
![Instância em execução](/desafios_code_girls_2025/1.Gerenciando_Instancias_EC2/img/instancia-rodando.png)

### Regras de Entrada Aplicada
![regras de entrada](/desafios_code_girls_2025/1.Gerenciando_Instancias_EC2/img/regras-de-entrada.png)

### Página Web acessada via IP público
![Página Web Apache](/desafios_code_girls_2025/1.Gerenciando_Instancias_EC2/img/pagina-web.png)

> ⚠️ **Observação:** Esta instância já foi encerrada e não está mais em execução.  
> As imagens aqui apresentadas são apenas para fins de documentação do desafio.

---

## 💬 Conclusão
Realizar este desafio foi uma ótima forma de consolidar o que aprendi sobre o serviço **Amazon EC2** e entender melhor como cada etapa da configuração influencia o funcionamento de uma instância.  
Durante a prática, pude criar e personalizar uma instância usando o **Amazon Linux 2023**, configurar rede, armazenamento e automatizar a instalação de um servidor web com um script simples no **User Data**.
