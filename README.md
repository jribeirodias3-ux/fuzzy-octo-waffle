# fuzzy-octo-waffle
cd repo

git checkout -b feature-branch

# Commit 1
echo "First line of commit 1" >> file.txt
git add file.txt
git commit -m "Commit 1: Added first line to file.txt"

# Commit 2
echo "Second line of commit 2" >> file.txt
git add file.txt
git commit -m "Commit 2: Added second line to file.txt"

# Commit 3
echo "Third line of commit 3" >> file.txt
git add file.txt
git commit -m "Commit 3: Added third line to file.txt"

# Commit 4
echo "Fourth line of commit 4" >> file.txt
git add file.txt
git commit -m "Commit 4: Added fourth line to file.txt"

# Commit 5
echo "Fifth line of commit 5" >> file.txt
git add file.txt
git commit -m "Commit 5: Added fifth line to file.txt"

git push origin feature-branch

git checkout -b minha-feature

echo "Nova funcionalidade" > feature.txt

git add feature.txt
git commit -m "Adiciona nova funcionalidade"

git push origin minha-feature

git checkout main
git pull origin main

.github/workflows/ci.yml

# Linguagem: YAML
name: CI

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    # Passo 1: Checar o código do repositório
    - name: Checkout repository
      uses: actions/checkout@v3

      # Passo 2: Configurar a linguagem (exemplo Node.js)
    - name: Setup Node.js
      uses: actions/setup-node@v3
      with:
        node-version: '18'

    # Passo 3: Instalar dependências
    - name: Install dependencies
      run: npm install

    # Passo 4: Rodar testes
    - name: Run tests
      run: npm test
# language: YAML
name: Continuous Deployment

on:
  push:
    branches:
      - main  # Executa CD ao fazer push na branch principal

jobs:
  build-and-deploy:
    name: Build and Deploy
    runs-on: ubuntu-latest

steps:
      # 1. Fazer checkout do código
      - name: Checkout Repository
        uses: actions/checkout@v3

      # 2. Configurar Node.js
      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '18'

      # 3. Instalar dependências
      - name: Install Dependencies
        run: npm install

      # 4. Rodar testes
      - name: Run Tests
        run: npm test

      # 5. Build do projeto
      - name: Build Project
        run: npm run build

      # 6. Deploy para o servidor
      - name: Deploy to Server via SSH
        uses: easingthemes/ssh-deploy@v2
        with:
          ssh-private-key: ${{ secrets.SSH_PRIVATE_KEY }}
          remote-user: ${{ secrets.REMOTE_USER }}
          server-ip: ${{ secrets.SERVER_IP }}
          remote-path: /var/www/seu-projeto
          local-path: ./build

git add .github/workflows/cd-workflow.yml
git commit -m "Add GitHub Actions CD workflow"
git push origin cd-setup

# language: YAML
name: Build and Push Docker Image

on:
  push:
    branches:
      - main

jobs:
  build-and-push:
    runs-on: ubuntu-latest

    steps:
      # 1. Checa o código do repositório
      - name: Checkout repository
        uses: actions/checkout@v3

      # 2. Loga no Docker Hub
      - name: Log in to Docker Hub
        uses: docker/login-action@v2
        with:
          username: ${{ secrets.DOCKER_USERNAME }}
          password: ${{ secrets.DOCKER_PASSWORD }}

      # 3. Build da imagem Docker
      - name: Build Docker Image
        run: |
          docker build -t meuusuario/minha-aplicacao:latest .

# 4. Push da imagem para Docker Hub
      - name: Push Docker Image
        run: |
          docker push meuusuario/minha-aplicacao:latest
