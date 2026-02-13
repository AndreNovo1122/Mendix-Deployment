# Guia de Deploy Mendix — MDA, MPK e Configuração do Node

## 1. Quando o cliente envia um MDA (Mendix Deployment Archive)

O **MDA** é o ficheiro usado para **deploy no Mendix Cloud**.  
É o formato final, já preparado para correr num Node.

### 1.1. Passos quando recebes um MDA

1. **Validar o ficheiro**
   - Confirmar nome, versão e integridade.

2. **Entrar no Mendix Developer Portal**

3. **Fazer upload do MDA**
   - Navegar para: `Environments → Deploy → Upload Package`
   - Selecionar o ficheiro `.mda`
   - Confirmar o upload.

4. **Link Node (associar o package ao ambiente)**
   - Em `Environments`, escolher o ambiente.
   - Em `Available Packages`, selecionar o package.
   - Clicar em **Deploy**.

5. **Start / Restart do ambiente**
   - Clicar em **Start** (se estiver parado) ou **Restart**.
   - Validar logs.
   - Confirmar que a app arrancou corretamente.

### 1.2. Resumo

- O MDA já está pronto para deploy.
- Não é necessário compilar, exportar ou alterar o projeto.
- Fluxo: **Upload → Link → Deploy → Start**.

---

## 2. Quando o cliente envia um MPK (Mendix Project Package)

O **MPK** é o ficheiro do **projeto Mendix**, não é um package de deploy.  
É o equivalente ao “código-fonte”.

### 2.1. Passos quando recebes um MPK

1. **Abrir o MPK no Mendix Studio Pro**
   - Importa o projeto para o ambiente local.

2. **Validar o projeto**
   - Ver dependências.
   - Ver erros de modelação.
   - Ver configurações de ambiente.

3. **Gerar o MDA**
   - No Studio Pro: `App → Export Deployment Package`.
   - Isto cria o ficheiro `.mda`.

4. **Seguir o processo normal do MDA**
   - **Upload → Link Node → Deploy → Start**.

### 2.2. Resumo

- O MPK **não pode ser deployado diretamente**.
- É sempre necessário abrir no Studio Pro e gerar um **MDA**.

---

## 3. Diferenças principais (MDA vs MPK)

| Tipo | O que é              | Para que serve            | Pode ser deployado? | Passos necessários                                      |
|------|----------------------|---------------------------|----------------------|---------------------------------------------------------|
| MDA  | Deployment Archive   | Deploy no Mendix Cloud    | Sim                  | Upload → Link Node → Deploy                            |
| MPK  | Project Package      | Código-fonte do projeto   | Não                  | Abrir no Studio Pro → Exportar MDA → Depois deploy MDA |

---

## 4. Passos seguintes no Node após o deploy do MDA

A partir do momento em que o MDA está carregado e associado ao Node, seguem-se os passos de configuração e validação do ambiente.

### 4.1. Confirmar que o package está ligado ao Node

1. Ir a **Environments** no Mendix Developer Portal.
2. Escolher o ambiente (por exemplo, *Acceptance* ou *Production*).
3. Verificar em **Current Package** se está o MDA correto (nome + versão).

### 4.2. Configurar Constants

1. Dentro do ambiente, ir a **Model Options → Constants**.
2. Preencher/validar os valores das constants (URLs, flags, chaves, etc.).
3. Guardar as alterações.

> Se as constants estiverem incorretas, a aplicação pode não arrancar ou comportar-se de forma errada.

### 4.3. Configurar Scheduled Events

1. Ir a **Model Options → Scheduled Events**.
2. Ativar/desativar os eventos que devem correr neste ambiente.
   - Exemplo: em Production alguns eventos correm, em Acceptance podem estar desligados.
3. Guardar.

### 4.4. Configurar Environment Variables / Custom Settings (se aplicável)

1. Ir a **Runtime → Custom Settings** (ou equivalente, dependendo da versão).
2. Adicionar/validar:
   - URLs externas.
   - Timeouts.
   - Feature flags.
   - Configurações específicas por ambiente.
3. Guardar.

### 4.5. Ver ligações a Base de Dados e Serviços Externos

1. Confirmar configuração da **Database** (normalmente já está feita no Node).
2. Validar se as constants/env vars que apontam para APIs externas estão corretas.
3. Se necessário, alinhar com o cliente quais endpoints usar em cada ambiente.

### 4.6. Start / Restart do Node

1. No ambiente, clicar em **Start** (se estiver parado) ou **Restart**.
2. Confirmar que o estado passa por algo como **Starting → Running**.
3. Aguardar até o Node estar estável.

### 4.7. Verificar Logs

1. Ir à secção **Logs** do ambiente.
2. Filtrar por nível (Info / Warning / Error).
3. Verificar:
   - Se não há erros críticos ao arrancar.
   - Se as conexões a DB e serviços externos foram bem sucedidas.
4. Se houver erros:
   - Corrigir configurações (constants/env vars).
   - Fazer novamente **Restart**.

### 4.8. Validar a aplicação funcionalmente

1. Abrir a URL do ambiente (link disponível no próprio ambiente).
2. Fazer login (se aplicável).
3. Testar:
   - Ecrãs principais.
   - Ações críticas (criar registos, pesquisar, etc.).
   - Integrações chave (APIs, ficheiros, etc.).

### 4.9. (Opcional) Monitorização e Backups

1. Ver **Metrics** (CPU, memória, requests) para perceber se o Node está saudável.
2. Confirmar política de **Backups** (automáticos, horários, retenção).
3. Se for a primeira vez em produção, alinhar com o cliente janelas de manutenção e restart.

---

## 5. Resumo em modo checklist

- [ ] Package correto ligado ao Node.  
- [ ] Constants configuradas.  
- [ ] Scheduled Events ajustados ao ambiente.  
- [ ] Custom Settings / Env vars configuradas.  
- [ ] Base de dados e integrações validadas.  
- [ ] Node em estado **Running**.  
- [ ] Logs sem erros críticos.  
- [ ] Aplicação testada funcionalmente.

