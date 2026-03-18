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

# Fazer alterações no código
echo "Nova funcionalidade" > feature.txt

# Adicionar e commitar
git add feature.txt
git commit -m "Adiciona nova funcionalidade"

# Enviar para o repositório remoto
git push origin minha-feature

git checkout main
git pull origin main
