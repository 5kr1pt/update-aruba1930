# Atualização de Firmware do Aruba Instant On 1930 Switch

## Pré-requisitos

- **Firmware**: arquivo `.zip` baixado no portal de firmwares Instant On 1930 ([Instant On 1930 - Switching Software Portal](https://community.instant-on.hpe.com/blogs/jamie-easly1/2020/06/03/instant-on-1930-switching-software-portal?)).
- **Ferramenta de descompactação** (ex.: `unzip` no Linux ou 7-Zip no Windows).  
- **Acesso**: IP do switch e credenciais de administrador.  No meu caso joguei no DHCP ele pegou um IP e acessei via Interface Web
- **Conectividade**: PC na mesma rede do switch.

---

## 1. Download do Firmware

1. Acesse o portal de firmwares Instant On 1930:  
https://community.instant-on.hpe.com/blogs/jamie-easly1/2020/06/03/instant-on-1930-switching-software-portal?

2. Na tabela **Software**, clique em **Download** na versão desejada (ex.: **3.1.0**).  
	![[Pasted image 20250519084046.png]]
3. Salve o arquivo `.zip` no seu computador

---

## 2. Extração do Arquivo

```bash
# Exemplo no Linux
unzip Instant_On_1930_3.1.0.zip -d firmware_1930
Dentro de firmware_1930, localize o arquivo .swi (ex.: 1930-v3.1.0.swi). 
Aruba Instant On Community
```
Via Windows é so usar o descompactador da sua preferência e pegar o arquivo ``.swi``

3. Acesso à Interface Web
Abra o navegador em https://$IP_DO_SWITCH/.

Faça login com usuário e senha de administrador.
Por padrão o usuário e senha é:
Login: admin
Senha: Em branco

Ao acessar ele pedirá para configurar um novo usuário e senha:
![[Pasted image 20250519084534.png]]

4. Atualização de Firmware

>Antes de terminar essa etapa, certifique-se que se você fez alguma atualização no Switch, como descrição, informação de contato e outras coisas ele perderá se você nao clicar no disquete de salvar no canto superior direito.

No menu lateral, vá em:
Maintenance → Backup and Update Files → Update 
Aruba Instant On Community
![[Pasted image 20250519084652.png]]

![[Pasted image 20250519084712.png]]

Clique em Choose File, selecione o ``.swi`` extraído e depois em Upload.

![[Pasted image 20250519085013.png]]

Após o upload, clique em ``Start File Transfer`` para iniciar a atualização.
![[Pasted image 20250519093913.png]]

O switch reiniciará automaticamente. Aguarde a conclusão.

5. Verificação
Refaça login após o reboot.

Em Information → System Info, confira Firmware Version para confirmar.

Em caso de erro “wrong magic number”, certifique-se de usar o arquivo .swi correto (não o .bin). 
Aruba Instant On Community
