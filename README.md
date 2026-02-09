# Mendix-Deployment
Documentation about mendix deployment and mendix cloud
# 📦 Mendix Deployment Package, Cloud Deployment & Control Center Guide

Este documento explica, de forma clara e estruturada:

- Como criar um **deployment package (.mda)** no Mendix  
- Como publicar a aplicação na **Mendix Cloud**  
- Como navegar e utilizar o **Mendix Control Center**  
- Como gerir apps, licenças, ambientes, private cloud e Kubernetes  
- Como monitorizar o estado da organização e das aplicações  

---

# 1. Criar um Deployment Package (MDA)

Um **deployment package (.mda)** é um ficheiro que contém tudo o que o Mendix precisa para correr a aplicação num servidor (on‑prem, Docker, Mendix Cloud, etc.).

## 🔹 Passos para criar o deployment package:

1. No Mendix Studio Pro, pressiona **F7**  
   ou vai a:  
   **App → Create Deployment Package**
<img width="1920" height="1032" alt="image" src="https://github.com/user-attachments/assets/f59781a7-fba1-4a80-a118-09cb7f6d4a14" />

2. Abre-se uma janela de **versionamento**, onde defines:
   - A versão do pacote  
   - A tag de versionamento  
   - (Opcional) Integração com pipelines CI/CD
<img width="718" height="579" alt="image" src="https://github.com/user-attachments/assets/0a310e6f-f983-48f2-a066-fb4a9ba10960" />

3. Clica em **OK**.

4. O Mendix gera o pacote e faz **download automático** do ficheiro `.mda`.

---

# 2. Para que serve o Deployment Package?

O ficheiro `.mda` pode ser usado para:

- **On‑prem Mendix App Server**
- **Imagem Docker do Mendix Runtime**
- **Importar para outro ambiente Mendix Cloud**
- **Ambientes ENSA / QA / PROD**
- **Pipelines CI/CD que vão buscar o código ao repositório**

Este processo cria uma **build estável**, baseada no estado atual do repositório.

## ⚠️ Nota importante:
Antes de criar o package, confirma que:

- A **tag de versionamento** corresponde à versão do Mendix usada no projeto  
- O projeto está limpo e sem erros  

---

# 3. Publicar a App na Mendix Cloud

Depois de criar o deployment package, podes publicar diretamente para a Mendix Cloud.

## 🔹 Passos:

1. No Studio Pro, clica em **Publish**  
   (a app **não pode estar a correr**).
<img width="760" height="458" alt="image" src="https://github.com/user-attachments/assets/c67a4d68-fd90-42fa-a9a4-df5791488a33" />

2. Garante que estás **logado** com a conta Mendix correta.

3. O Mendix vai:
   - Gerar dependências  
   - Criar um pacote  
   - Enviar o pacote para a Cloud  
   - Fazer o deployment no ambiente selecionado  

4. Se tudo correr bem, aparece:  
   **“Your app is published!”**

---

# 4. Alternativa: Botão da Nuvem (Cloud Icon)

No canto superior direito do Studio Pro existe um ícone de **nuvem**.

Este botão faz o mesmo que o Publish:

- Gera o pacote  
- Envia para a cloud  
- Faz o deployment automático  

---

# 5. Possíveis Erros e Como Resolver

## ❌ **Erro: “Something went wrong” ao publicar**
<img width="392" height="148" alt="image" src="https://github.com/user-attachments/assets/cea50bb3-475c-4881-8d0c-9b2d6f97ef6a" />

### 1. Falta de permissões
Verifica se tens acesso à app em:  
**Mendix Portal → Apps → Company Apps**

### 2. JDK configurado incorretamente
Confirma o caminho em:  
**Edit → Preferences → JDK Directory**

### 3. Security Mode incorreto
Para publicar na cloud, o projeto tem de estar em:

Project Security → Production Mode


### 4. Erros no Error Console
A app **não pode ter erros** antes de publicar.

---
<img width="624" height="138" alt="image" src="https://github.com/user-attachments/assets/9fd4e184-9678-4b01-8437-2f8a1fee5f33" />

# 6. Resumo do Processo

1. Criar deployment package (F7)  
2. Confirmar versionamento e dependências  
3. Verificar permissões e JDK  
4. Ativar **Production Mode**  
5. Garantir que não existem erros  
6. Clicar em **Publish** ou no ícone da nuvem  
7. Aguardar: **“Your app is published!”**


<img width="539" height="222" alt="image" src="https://github.com/user-attachments/assets/588a790c-d043-4217-b723-5b0fd677c9ab" />


---

# 🧭 7. Mendix Control Center — Visão Geral

O **Control Center** é o painel central de gestão da tua organização Mendix.

Aqui consegues ver:

- Apps deployadas  
- Apps em private cloud  
- Licenças  
- Utilizadores  
- Estado dos clusters  
- Segurança  
- Configurações da empresa  

---

# 8. Mendix Cloud (Ambientes Pagos)

Dentro do Control Center → **Mendix Cloud**, consegues ver:

### 🔹 Apps a correr (Running)
Ambientes ativos com deploy.

### 🔹 Apps não deployadas (Not Deployed)
Nós criados mas sem deployment.

### 🔹 Private Cloud Apps
Apps associadas à tua conta e deployadas em:

- Azure  
- AWS  
- GCP  
- Kubernetes clusters registados  

### 🔹 Connected Mode
Se o cluster estiver registado e sincronizado:

- CI/CD aparece integrado  
- Logs e métricas disponíveis  
- Deployments controlados pelo Mendix  

---

# 9. Cloud (All Apps)

Mostra **todas as apps** lançadas pela tua organização.

Se fores admin, consegues ver todas.

---

# 10. Other Apps

Apps que:

- Estão deployadas fora da Mendix Cloud  
- Estão em private cloud  
- Foram migradas para ambientes externos  

---

# 11. Deactivated Apps

Apps que foram:

- Removidas do registo  
- Desassociadas do repositório  
- Arquivadas  
- Migradas para private cloud  

---

# 12. Health Dashboard

Mostra o estado dos ambientes.

### Importante:
- Isto **não monitoriza a app**  
- Monitoriza o **cluster** (tipo Prometheus)  
- Mostra:
  - Erros críticos  
  - Estado do nó  
  - Disponibilidade  

---

# 13. Deployed Apps Overview

Mostra todas as apps deployadas.

### Free Apps
- Estado  
- App ID  
- Último deployment  

### Licensed Keys
Apps que:

- Usam licenças pagas  
- Estão em private cloud  
- Precisam de license key se não estiverem em connected mode  

---

# 14. People (Users & Permissions)

Aqui consegues ver:

- Todos os membros da organização  
- Roles e permissões  
- Quem pode fazer deployments  
- Quem pode gerir ambientes  

### Criar utilizadores
É aqui que adicionas novos membros.

---

# 15. Company → Company Settings

Configuras:

- Domínios da empresa  
- Políticas de segurança  
- Configurações globais  

### Nota:
Só podes adicionar admins com email do domínio da empresa.

---

# 16. Company Dashboard

Mostra:

- Estado da licença  
- Estado das apps  
- Versões de Mendix usadas  
- Histórico  
- Segurança  
- Apps deprecated  

---

# 17. Mendix Admins

Mostra:

- Quem tem permissões de deployment  
- Quem é admin  
- Quem pode gerir ambientes pagos  

---

# 18. Marketplace

Permite:

- Importar módulos  
- Atualizar dependências  
- Gerir componentes reutilizáveis  

---

# 19. Project Categories

Permite organizar apps por:

- Equipa  
- Cliente  
- Departamento  
- Tipo de projeto  

---

# 20. Apps Grid (Menu Superior → Apps)

Como admin, consegues:

- Aceder a todas as apps  
- Importar apps para o Studio Pro  
- Ver detalhes, ambientes, permissões  

---

# 21. Deployment Section (Grid → Deployment)

Aqui geres ambientes pagos.

### Quando crias uma app com licença:
- É criado um **nó**  
- Esse nó é o local de deployment  
- Tens de ter a licença ativa  

Depois importas a app para esse nó.

---

# 22. Mendix on Kubernetes (Private Cloud)

Em **Mendix on Kubernetes**, consegues gerir clusters privados:

- Azure AKS  
- AWS EKS  
- Google GKE  
- Oracle Cloud  
- Qualquer Kubernetes compatível  

### Cluster Manager
Permite:

- Registar clusters  
- Ativar connected mode  
- Integrar CI/CD  
- Sincronizar com a conta Mendix  

---

# ✔️ Conclusão Geral

Com este guia consegues:

- Criar deployment packages (.mda)  
- Publicar apps na Mendix Cloud  
- Gerir apps, licenças e ambientes  
- Administrar private cloud e Kubernetes  
- Monitorizar a saúde dos clusters  
- Controlar utilizadores e permissões  
- Organizar e manter toda a infraestrutura Mendix  

