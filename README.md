```markdown
# Driver Realtek RTL8111/RTL8168 no Ubuntu/Linux Mint

Se você possui um adaptador de rede Realtek RTL8111/8168/8211/8411 PCI Express Gigabit Ethernet, pode garantir o funcionamento ideal instalando o driver `r8168`, mais compatível com este hardware.

## Instalação do Driver `r8168` com DKMS

Siga os passos abaixo:

### 1. Atualize os repositórios e instale o DKMS:
```bash
sudo apt update
sudo apt install dkms
```

### 2. Instale o pacote `r8168-dkms`:
```bash
sudo apt install r8168-dkms
```
Este pacote compilará e ativará o driver automaticamente para o kernel atual e futuros, utilizando o DKMS.

### 3. Desative o driver `r8169` e ative o `r8168`:
```bash
sudo modprobe -r r8169
sudo modprobe r8168
```

### 4. Reinicie o sistema:
```bash
sudo reboot
```

### Verificação:
Após reiniciar, confirme se o driver `r8168` está ativo:
```bash
sudo lshw -C network
```
Procure pela linha `driver=r8168`.

## Teste de Velocidade de Internet (Opcional)
Instale o `speedtest` e realize testes via terminal. Copie e salve o código abaixo em um arquivo chamado `speed.sh`:
```bash
#!/bin/bash
sudo apt update
sudo apt install -y speedtest-cli
echo "Instalação concluída! Para realizar o teste de velocidade, digite: speedtest"
```

### Torne o script executável e execute:
```bash
chmod +x speed.sh
./speed.sh
```

Após a instalação, use o comando `speedtest` para testar sua conexão.

---

## Nota
Se preferir instalar o driver manualmente, baixe-o do site oficial da [Realtek]() e siga as instruções de compilação. Porém, a abordagem via DKMS é mais simples e automatizada.
```
