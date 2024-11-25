# Como criar uma EC2 na AWS
Criação de Instancia EC2

# Passo 1: Configuração da instância EC2
Acesse o Console AWS
Faça login em sua conta AWS e vá para o serviço EC2.
Clique em Launch Instance
Escolha a imagem Amazon Linux 2 AMI
Selecione o tipo de instância t2.micro
Configure as opções de rede e armazenamento padrão (ou ajuste conforme necessário)
Faça o download da chave privada (.pem) ao configurar o par de chaves para acessar a instância via SSH
Clique em Launch Instance e aguarde a criação

# Passo 2: Conexão via SSH
No terminal do seu computador, acesse o diretório onde está sua chave privada (.pem).
Execute o comando: ssh -i "sua-chave.pem" ec2-user@<IP-da-instância>
Substitua <IP-da-instância> pelo IP público da sua instância

# Passo 3: Gerenciando o armazenamento
No Console AWS, acesse Volumes em Elastic Block Store
Clique em Create Volume e configure o tamanho 8 GiB
Escolha a mesma zona de disponibilidade da sua instância EC2
Clique em Create Volume
Selecione o volume criado, clique em Actions > Attach Volume
Escolha sua instância EC2 e finalize

# Passo 4: Formatando e montando o volume
Execute o comando para listar os discos disponíveis: lsblk
O volume recém-anexado aparecerá como algo como /dev/xvdf.
Substitua xvdf pelo nome do seu volume: sudo mkfs.ext4 /dev/xvdf
Crie um diretório para montar o volume: sudo mkdir /mnt/meuvolume
Monte o volume no diretório criado: sudo mount /dev/xvdf /mnt/meuvolume

# Passo 5: Criação de arquivos
Use o editor nano para criar um arquivo no volume montado: sudo nano /mnt/meuvolume/meuarquivo.txt

# Passo 6: Explorando recursos
Verifique o status do volume:
ls /mnt/meuvolume
df -h
mount
cat /mnt/meuvolume/meuarquivo.txt




