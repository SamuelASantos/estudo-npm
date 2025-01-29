## O que é NPM?
NPM (Node Package Manager) é o **gerenciador de pacotes do Node.js**, utilizado para instalar, gerenciar e compartilhar bibliotecas e dependências de projetos JavaScript. Ele é uma ferramenta essencial para desenvolvedores que trabalham com JavaScript e Node.js, permitindo o uso de pacotes de terceiros para acelerar o desenvolvimento.

[Site oficial para baixar o NODE que vem com o NPM](https://nodejs.org/pt)

### 🔹 **Principais funcionalidades do NPM**:
- 📦 **Instalar pacotes**: Permite adicionar bibliotecas e frameworks ao projeto com comandos simples, como `npm install express`.
- 🔄 **Gerenciar dependências**: Mantém um arquivo `package.json` que registra todas as bibliotecas usadas no projeto.
- 🚀 **Executar scripts**: Facilita a automação de tarefas, como iniciar um servidor ou rodar testes (`npm run start`).
- 🌎 **Publicar pacotes**: Desenvolvedores podem criar e compartilhar seus próprios pacotes na plataforma [NPM Registry](https://www.npmjs.com/).

### 🔹 **Comandos básicos do NPM**:
```sh
# Inicializar um projeto (cria um package.json)
npm init -y

# Instalar um pacote (exemplo: Express)
npm install express

# Instalar um pacote globalmente
npm install -g nodemon

# Atualizar pacotes do projeto
npm update

# Remover um pacote
npm uninstall express

# Executar um script definido no package.json
npm run start
```

NPM é amplamente utilizado no ecossistema JavaScript, especialmente em projetos **frontend** (React, Vue, Angular) e **backend** (Node.js). 🚀

## NPM init e package.json

### 📌 **Review: `npm init` e `package.json`**  

#### 🔹 **`npm init` – Inicializando um Projeto Node.js**  
O comando `npm init` é usado para **criar um novo projeto Node.js** e gerar um arquivo `package.json`, que gerencia as dependências e metadados do projeto.  

##### 🛠 **Principais opções do `npm init`**:  
- `npm init` → Inicia um assistente interativo para preencher manualmente o `package.json`.  
- `npm init -y` → Cria o `package.json` automaticamente com valores padrão.  

##### 📌 **Exemplo de uso**:  
```sh
npm init
# ou para pular perguntas:
npm init -y
```

---

#### 🔹 **`package.json` – O Arquivo de Configuração do Projeto**  
O `package.json` é o **arquivo de configuração principal** de um projeto Node.js. Ele armazena informações como nome do projeto, versão, autor, dependências e scripts.  

##### 📄 **Exemplo de `package.json`**:  
```json
{
  "name": "meu-projeto",
  "version": "1.0.0",
  "description": "Um projeto exemplo com Node.js",
  "main": "index.js",
  "scripts": {
    "start": "node index.js"
  },
  "dependencies": {
    "express": "^4.18.2"
  },
  "devDependencies": {
    "nodemon": "^2.0.22"
  }
}
```

##### 🔥 **Principais seções do `package.json`**:
- **`name`**: Nome do projeto.  
- **`version`**: Versão do projeto.  
- **`description`**: Breve descrição do projeto.  
- **`main`**: Arquivo principal do projeto.  
- **`scripts`**: Comandos customizados (`npm run start`).  
- **`dependencies`**: Pacotes necessários para rodar o projeto.  
- **`devDependencies`**: Pacotes usados apenas no ambiente de desenvolvimento.  

---

#### ✅ **Conclusão**  
O `npm init` é essencial para estruturar um projeto Node.js corretamente, enquanto o `package.json` funciona como um **manual de instruções** do projeto, garantindo organização e controle sobre as dependências. 🚀

### 🚀 **Como Resolver o Erro `about_Execution_Policies` ao Executar `npm` no Windows**  

Esse erro acontece porque o **PowerShell** bloqueia a execução de scripts por padrão, por motivos de segurança. Isso pode impedir a execução de comandos do `npm`, como `npm install` ou `npm run`.  

---

### 🔹 **Solução: Alterar a Política de Execução**  

#### ✅ **1. Verificar a Política Atual**  
Abra o **PowerShell** como **Administrador** e digite:  
```powershell
Get-ExecutionPolicy
```
Se o resultado for `Restricted`, significa que a execução de scripts está bloqueada.

---

#### ✅ **2. Alterar a Política para Permitir Scripts**  
Para permitir a execução de scripts, use o seguinte comando no **PowerShell (Admin)**:  
```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
```
🔹 **Explicação:**  
- `RemoteSigned` → Permite executar scripts locais sem restrições, mas exige assinatura digital para scripts baixados da internet.  
- `-Scope CurrentUser` → Aplica a mudança apenas para o usuário atual, sem afetar todo o sistema.  

⚠️ **Se solicitado, confirme pressionando `A` (Sim para todos).**  

---

#### ✅ **3. Testar o `npm` Novamente**  
Agora, tente rodar o comando novamente:  
```sh
npm install
```
Se o erro persistir, feche e reabra o terminal ou reinicie o computador.

### ✅ **Conclusão**  

O erro `about_Execution_Policies` ocorre por restrições do Windows, mas pode ser resolvido alterando a política para `RemoteSigned`. Essa mudança permite que o `npm` e outros scripts sejam executados corretamente no PowerShell. 🚀

## 📌 **`NPM install` e `Node Modules`**

#### 🔹 **`npm install` – Instalando Dependências**  
O comando `npm install` (ou `npm i`) é usado para instalar todas as dependências listadas no `package.json`.  

##### 📌 **Comandos Principais**  
```sh
# Instalar todas as dependências do package.json
npm install

# Instalar um pacote específico (exemplo: Express)
npm install express

# Instalar um pacote como dependência de desenvolvimento
npm install nodemon --save-dev

# Instalar um pacote globalmente (disponível em todo o sistema)
npm install -g typescript

# Reinstalar todas as dependências
rm -rf node_modules package-lock.json && npm install
```

---

#### 🔹 **`node_modules` – A Pasta de Dependências**  
A pasta `node_modules` contém **todos os pacotes instalados pelo NPM**. Ela pode ficar grande, pois cada pacote pode ter suas próprias dependências.  

##### 📄 **Importante**:
- **Não é necessário versionar `node_modules`** no GitHub. O recomendado é adicionar `node_modules` ao `.gitignore`.
- Se a pasta for apagada, basta rodar `npm install` para reinstalar tudo com base no `package.json`.

---

#### 🔥 **Conclusão**  
O `npm install` é essencial para gerenciar dependências, enquanto `node_modules` armazena os pacotes instalados. Para manter um projeto organizado, o `package.json` e o `package-lock.json` garantem que todos os desenvolvedores usem as mesmas versões das dependências. 🚀


### 📌 **`npm remove` – Removendo Dependências**  

O comando `npm remove` (ou `npm uninstall`) é usado para **remover pacotes instalados** de um projeto Node.js.  

---

### 🔹 **Comandos Principais**  

#### ✅ **Remover um pacote específico**  
```sh
npm remove nome-do-pacote
# ou
npm uninstall nome-do-pacote
```
🔹 **Exemplo**:  
```sh
npm remove express
```
Isso removerá o pacote `express` do projeto e do `package.json`.

---

#### ✅ **Remover uma dependência de desenvolvimento**  
```sh
npm remove nome-do-pacote --save-dev
```
🔹 **Exemplo**:  
```sh
npm remove nodemon --save-dev
```
Isso removerá `nodemon` da seção `devDependencies` do `package.json`.

---

#### ✅ **Remover um pacote globalmente**  
```sh
npm remove -g nome-do-pacote
```
🔹 **Exemplo**:  
```sh
npm remove -g typescript
```
Isso removerá `typescript` do sistema, tornando-o indisponível globalmente.

---

### 🔥 **Conclusão**  
O `npm remove` é essencial para manter o projeto limpo e organizado, eliminando pacotes desnecessários. Sempre verifique o `package.json` após remover pacotes para garantir que o projeto continue funcionando corretamente. 🚀


### 📌 **Dependências de Desenvolvimento (`devDependencies`) no NPM**  

As **dependências de desenvolvimento** são pacotes que **só são necessários durante o desenvolvimento** do projeto, mas **não são usadas em produção**. Elas são registradas na seção `"devDependencies"` do `package.json`.  

---

### 🔹 **Como Adicionar Dependências de Desenvolvimento**  
Use a flag `--save-dev` ao instalar pacotes:  
```sh
npm install nome-do-pacote --save-dev
```
🔹 **Exemplo:**  
```sh
npm install nodemon --save-dev
```
Isso adicionará `nodemon` apenas como dependência de desenvolvimento.

---

### 🔹 **Exemplo de `package.json` com `devDependencies`**  
```json
{
  "dependencies": {
    "express": "^4.18.2"
  },
  "devDependencies": {
    "nodemon": "^2.0.22",
    "jest": "^29.6.3"
  }
}
```
🔹 **Explicação:**  
- `dependencies`: Pacotes necessários para rodar o projeto em produção.  
- `devDependencies`: Pacotes usados apenas no desenvolvimento, como **testes, ferramentas de automação e linters**.  

---

### 🔹 **Exemplos de Dependências de Desenvolvimento**  
| Pacote | Função |
|--------|--------|
| `nodemon` | Reinicia o servidor automaticamente ao detectar mudanças no código |
| `jest` | Framework de testes para JavaScript |
| `eslint` | Analisa o código e ajuda a manter boas práticas |
| `webpack` | Empacotador de módulos para otimizar o código |
| `babel` | Transpila código moderno para versões compatíveis com navegadores antigos |

---

### 🔹 **Como Remover Dependências de Desenvolvimento**  
```sh
npm remove nome-do-pacote --save-dev
```
🔹 **Exemplo:**  
```sh
npm remove jest --save-dev
```

---

### 🔥 **Conclusão**  
As **`devDependencies`** ajudam a manter o projeto organizado, garantindo que ferramentas de desenvolvimento não sejam incluídas no ambiente de produção. 🚀


### 📌 **Como Subir um Projeto NPM no GitHub com `.gitignore`**  

Ao subir um projeto Node.js no GitHub, é essencial ignorar arquivos desnecessários, como a pasta `node_modules`. O `.gitignore` evita que arquivos grandes e gerados automaticamente sejam versionados, mantendo o repositório limpo e eficiente.  

---

### 🔹 **Passo a Passo para Subir um Projeto NPM no GitHub**  

#### ✅ **1. Criar o Repositório no GitHub**  
1. Acesse [GitHub](https://github.com) e crie um novo repositório.  
2. Copie a URL do repositório remoto.  

---

#### ✅ **2. Criar o `.gitignore` para um Projeto Node.js**  
Crie um arquivo `.gitignore` na raiz do projeto e adicione:  

```txt
# Ignorar a pasta node_modules
node_modules/

# Ignorar arquivos de log
npm-debug.log
yarn-error.log

# Ignorar arquivos de dependências travadas
package-lock.json

# Ignorar pastas de build (caso use Webpack, TypeScript, etc.)
dist/
build/

# Ignorar arquivos de ambiente
.env
```

Isso impede que arquivos desnecessários sejam enviados para o GitHub.

---

#### ✅ **3. Inicializar o Git e Subir o Projeto**  
Abra o terminal na pasta do projeto e execute:  

```sh
# Inicializar o repositório Git
git init

# Adicionar todos os arquivos (exceto os ignorados pelo .gitignore)
git add .

# Criar um commit com uma mensagem descritiva
git commit -m "Primeiro commit - Inicializando o projeto"

# Adicionar o repositório remoto (substitua pela URL do seu repositório)
git remote add origin https://github.com/seu-usuario/seu-repositorio.git

# Enviar o projeto para o GitHub
git push -u origin main
```

Se estiver usando outra branch, substitua `main` pelo nome correto.

---

#### ✅ **4. Clonar o Projeto Sem `node_modules`**  
Quando outro desenvolvedor clonar o projeto, ele pode instalar as dependências com:  

```sh
git clone https://github.com/seu-usuario/seu-repositorio.git
cd seu-repositorio
npm install
```

Isso recriará a pasta `node_modules` automaticamente.

---

### 🔥 **Conclusão**  
Ao configurar corretamente o `.gitignore`, você evita subir arquivos desnecessários para o GitHub, mantendo o repositório limpo e eficiente. 🚀


## 📌 **Yarn – Gerenciador de Pacotes para Node.js**  

O **Yarn** é uma alternativa ao `npm` para gerenciar pacotes em projetos Node.js. Ele foi criado pelo Facebook para melhorar o desempenho, segurança e confiabilidade na instalação de dependências.  

---

## 🔹 **Principais Vantagens do Yarn**  
✅ **Mais rápido** – Usa cache para evitar downloads repetidos.  
✅ **Instalação paralela** – Baixa pacotes simultaneamente, acelerando o processo.  
✅ **Maior segurança** – Usa `yarn.lock` para garantir versões consistentes.  
✅ **Melhor controle de dependências** – Resolve conflitos de versão de forma mais eficiente.  

---

## 🔹 **Instalação do Yarn**  
Se você já tem o **Node.js** instalado, pode instalar o Yarn globalmente com:  

```sh
npm install -g yarn
```
Para verificar a instalação:  
```sh
yarn --version
```

---

## 🔹 **Principais Comandos do Yarn**  

### ✅ **Inicializar um Projeto**  
```sh
yarn init
```
Cria um `package.json` interativo, semelhante ao `npm init`.

---

### ✅ **Instalar Dependências**  
```sh
yarn install
```
Baixa todas as dependências do `package.json` e cria/atualiza o `yarn.lock`.

---

### ✅ **Adicionar Pacotes**  
```sh
yarn add nome-do-pacote
```
🔹 **Exemplos:**  
```sh
yarn add express       # Adiciona como dependência normal
yarn add nodemon --dev # Adiciona como dependência de desenvolvimento
yarn add typescript -g # Instala globalmente
```

---

### ✅ **Remover Pacotes**  
```sh
yarn remove nome-do-pacote
```

---

### ✅ **Atualizar Dependências**  
```sh
yarn upgrade
```
Ou para atualizar um pacote específico:  
```sh
yarn upgrade nome-do-pacote
```

---

### ✅ **Executar Scripts**  
Se houver scripts no `package.json`, você pode rodá-los com:  
```sh
yarn run nome-do-script
```
🔹 **Exemplo:**  
```json
"scripts": {
  "start": "node app.js"
}
```
```sh
yarn start
```

---

## 🔥 **Conclusão**  
O **Yarn** é uma alternativa eficiente ao `npm`, oferecendo mais velocidade, segurança e controle sobre dependências. Se você busca um gerenciador de pacotes mais otimizado, vale a pena usá-lo! 🚀