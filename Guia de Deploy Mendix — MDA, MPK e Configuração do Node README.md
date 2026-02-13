# Guia de Deploy Mendix — MDA, MPK e Configuração de Node

Este guia documenta o processo completo de:
- Importar um MPK no Mendix Studio Pro  
- Criar um Deployment Package (MDA)  
- Fazer deploy no Mendix Portal (Free Cloud ou Licensed Node)  
- Configurar o Node após o deploy  
- Entender as diferenças entre MDA e MPK  

---

# 1. Quando o cliente envia um MDA ou MPK

Antes de começar, é essencial perceber a diferença:

| Tipo | Uso | Onde se abre | Para que serve |
|------|------|--------------|----------------|
| **MPK** | Código‑fonte | Mendix Studio Pro | Criar/editar projeto e gerar MDA |
| **MDA** | Deployment Package | Mendix Portal | Fazer deploy no Node |

---

# 1.1. Passos quando recebes um **MPK**

### 1. Validar o ficheiro
- Confirmar nome, versão e integridade.

---

### 2. Importar o MPK no Mendix Studio Pro  
*(⚠️ Apenas MPK é importado aqui. MDA não se importa no Studio Pro.)*

File → Import App Package

Código

![import](https://github.com/user-attachments/assets/d51167e6-ee1d-49d6-816b-59b4450f1561)

---

### 3. Criar um Deployment Package (MDA)
Após abrir o MPK:

App → Create Deployment Package

 

![create1](https://github.com/user-attachments/assets/f6528716-ab77-4bc4-b01a-f6c411c84abd)
![create2](https://github.com/user-attachments/assets/acd8350d-5d04-4df1-9d8c-37de677e8819)

---

# 1.2. Passos quando recebes um **MDA**

Se o cliente já enviou o MDA → **não precisas do Studio Pro**.

O processo é feito diretamente no Mendix Portal.

---

# 2. Fazer upload do MDA no Mendix Portal

No Mendix Portal:

App → Deployment → Environment → Deployment Packages → Upload Deployment Package

 

![upload](https://github.com/user-attachments/assets/4fa49f68-e2e9-4d61-ab1b-64fb65a69198)
![uploaded](https://github.com/user-attachments/assets/a40097f5-09cf-457c-9472-d91b6ca6bc28)

---

# 3. Aceder ao ambiente de produção

App → Deployment → Environment → Production → Details

 

![prod-details](https://github.com/user-attachments/assets/32b42ffc-afe9-4585-ab6b-060209b9f6dd)

---

# 4. (Opcional) Limpar ambiente

Clear Environment → Clear Model and Database

 

![clear1](https://github.com/user-attachments/assets/e8882842-aa4b-4030-be7c-bc0d3fb4627b)
![clear2](https://github.com/user-attachments/assets/b7451248-84f4-4c66-b9bc-234a6d3a8a5a)

---

# 5. Selecionar o package para deploy

Deployment → Production → Select Package

 

![select-package](https://github.com/user-attachments/assets/5ba34c3a-00b4-4cf0-9cd4-c26c618fff37)
![package-list](https://github.com/user-attachments/assets/2c5a6620-a6cb-4fae-a513-4eb8a0a63bef)

---

# 6. Configurar o ambiente (Constants, Scheduled Events)

Se existirem constants, aparecem aqui:

![constants](https://github.com/user-attachments/assets/8bc86fea-d7f3-481b-a314-b0cb4bade4a7)

---

# 7. Escolher tipo de promoção

Opções:

- **Staged** → aplica no próximo restart  
- **Promote without backup** → quando não há dados a preservar  
- **Take backup before promoting** → recomendado em produção  

![promote1](https://github.com/user-attachments/assets/1be60d14-310f-4507-8a8c-995f908a5099)
![promote2](https://github.com/user-attachments/assets/9511b60f-33b0-40e4-acf5-4b3edfc398f3)

---

# 8. Ver logs em tempo real

Monitoring → Logs → View Live Log

 

![logs1](https://github.com/user-attachments/assets/c5cb6711-3072-40a8-bf17-cdd3214c23b8)
![logs2](https://github.com/user-attachments/assets/ab1d4144-17f4-4618-9cba-864683a6926d)
![logs3](https://github.com/user-attachments/assets/0dc7ca30-f823-4fc5-a668-cebb88285ba9)

Aguardar até o estado ficar:

Promoted → Running

 

![promoted](https://github.com/user-attachments/assets/a95e7ebc-225f-466a-a806-ecce8b93c3d3)

---

# 9. Validar a aplicação

View App

 

![view-app](https://github.com/user-attachments/assets/8c0fad19-a3cf-45f3-800b-6e69921b876d)
![app-up](https://github.com/user-attachments/assets/e24c14f0-a6b7-4faf-a869-b32ced36696a)

---

# 10. Alterar password do administrador

Environments → Production → Details → ⋮ → Change Admin Password

 

![admin-pass1](https://github.com/user-attachments/assets/e605b8a2-581a-4d45-9eef-6f4e3c3dde7d)
![admin-pass2](https://github.com/user-attachments/assets/a9e39db3-b75b-412f-8f70-f5a61adbe1dd)
![login-test](https://github.com/user-attachments/assets/c260d410-f4d9-4cbf-8f01-6e298adb286e)

---
