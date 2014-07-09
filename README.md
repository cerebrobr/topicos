<<<<<<< HEAD
# Tópicos
=======
# UNICS

Um documento para o aprendizado do Sistema Operacional Unix com base em tópicos.

## Sumário

- [Introdução](#introdução)
- [Sistema](#sistema)
- [Usuários e Grupos](#usuários-e-grupos)
- [Arquivos do Sistema](#arquivos-do-sistema)
- [Configurações do Ambiente](#configruações-do-ambiente)
- [Comandos do UNIX](#comandos-do-unix)
- [Ferramentas](#ferramentas)
- [Processos](#processos)
- [Rotinas](#rotinas)
- [Segurança](#segurança)
- [Shell Script](#shell-script)
- [Utilidades para UNIX Admins](#utilidades-para-unix-admins)


## Introdução

### Unix

- Existem duas versões primárias do Unix: System V e BSD.
- Foram criados diversas versões (_flavors_) com base nestas duas versões primárias.
- Padrão POSIX.
- Richard Stallman inicia o projeto GNU em 1984 com a intenção de criar um sistema Unix-like, mas com distribuição livre.
- Em 1991, Linus Torvalds dá início a criação do Linux. Atualmente, o Linux é o kernel, enquanto as ferramentas, shell e arquivos de sistema fazem parte do GNU. Por isso, damos o nome de GNU/Linux.

### Kernel

- Camada de nível mais baixo do Unix.
- Controla processos, dispositivos de entrada/saída, operações de arquivos do sistema e outras funções necessárias para a operação do sistema. 
- Construído para um hardware específico.
- Não pode ser manuseado pelo usuário (geralmente).
- Facilita a criação e gerenciamento de processos (muitas vezes chamados de _jobs_ ou _tasks_).
- O kernel manuseia a memória do sistema. Quando um processo é iniciado, mas a memória física não oferece mais suporte para a execução desta tarefa, a memória virtual entra em ação para acomodar este processo, movendo algumas partes para o disco rígido. Quando esta mesma porção é solicitada novamente, ela retorna para a memória física. Este procedimento é chamado de _paging_.
- Ainda temos outro aspecto quanto a memória, chamado de _swap_. Neste caso, o processo é movido por completo para o disco rigído. O espaço destinado a este processo no disco rígido chama-se _swap space_ no Unix. É importante certificar-se de que o espaço destinado para este processo seja suficiente, do contrário o usuário será punido com uma perda de performance considerável.

### Shell

- É o interpretador da linha de comando.
- Reponsável por permitir a interação entre o usuário e as operações no sistema.
- Existem três shells primários: Bourne Shell (conhecido como _sh_), C Shell (_csh_) e Korn Shell (_ksh_).
- Não somente, existem outras variantes para o Shell. Utilize a que estiver mais adequada para as suas necessidades.

### Componentes

- São os utilitários e arquivos do sistema. É o que torna capaz a visualização, organização e interação de modo consistente com os arquivos e diretórios disponíveis em dispositivos de armazenamento pelo usuário.


## Sistema

### Inicialização

- Chamamos de _boot process_, o processo que ocorre entre a posição inicial do seu sistema (desligado), até o momento em que o seu sistema está completamente carregado/disponível/acessível.
- O processo de identificação do device é chamado de _bootstrapping_.
- O dispositívo de _boot_ não precisa ser um dispositivo físico. O mesmo pode ser feito através da rede ou por um dispositivo de armazenamento externo (USB, CD-ROM).
- O dispositivo de _boot_ contém apenas as informações necessárias para carregar o sistema operacional.
- Após o _bootstrapping_, o kernel começa a ser carregado.

### Autenticação

- O _Log In_ e _Log Out_ pode ser efetuado através de uma GUI ou na CLI, depende da variante que estiver sendo utilizada (Mac, Solaris, Linux, etc).
- No momento da autenticação através da CLI temos um banner, o qual consiste, geralmente, de 3 (três) linhas indicando a versão do OS, do kernel e o host/ip da rede.
- Em sistemas públicos, estas informações devem ser ocultadas por razões de segurança.
- É possível utilizar a autenticação remota através do protocolo TCP/IP.
- Este protocolo permite a transferência de dados entre diferentes sistemas.
- Alguns métodos para login remoto são: ssh, telnet, sftp, ftp.
- Haviam outros métodos para conexão remota, mas foram abandonados por questões de segurança. São eles: rcp, rlogin e rsh.
- O `telnet` possui a mesma função do `rsh` e do `rlogin`, já o `ftp` é similar ao `rcp`.
- Para haver a comunicação entre os sistemas (local <-> remoto), o acesso precisa estar liberado (sem firewalls ou restrições do sistema).

#### Via SSH

- Possibilita acesso remoto a fim de possibilitar a execução de comandos em outro sistema.
- O uso é feito com, no mínimo: `<command> <hostname>`
- `command`: refere-se ao protocolo de comunicação que o usuário deseja utilizar.
- `hostname`: refere-se ao nome atual da máquina ou o IP da rede (192.168.0.*).
- Dar preferência o uso do _SSH_ ao _telnet_, pois a sessão será encriptada.
- Caso seja o primeiro acesso remoto, uma chave de autenticação será registrada na máquina. Caso alguém tente modificá-la ou ter acesso ao sistema que não seja por essa chave, o usuário (admin) será notificado.
- Ao utilizar `ssh hostname`, o protocolo assume que o usuário deseja logar no sistema remoto com o mesmo nome do usuário.
- Para acessar com outro usuário, deve-se utilizar o comando `ssh username@hostname`.

#### Via telnet

- Nem todos os sistemas permitem o uso de SSH, sendo assim será necessário o uso do telnet.
- Diferente do _SSH_ a sintaxe mínima do _telnet_ é: ````<command> <address> <port>````. Ex: ````telnet 192.168.0.1 8080````.
- O campo ````address```` não se refere somente a um _endereço_ _de_ _IP_, podendo ser também um _domain_ _name_, por ex: ````telnet google.com 80````.
- Não realiza a encriptação de dados durante a sessão (local <-> remoto).
- Outra diferença é que o telnet vai abrir um prompt para que seja inserido o _username_ e _password_.
- Permite o envio de requisições na rede, como por exemplo uma requisição _HTTP_. Ex: ````telnet google.com 80 GET / HTTP/1.1````
- Nem sempre o `telnet` sabe que

### Finalizar/desligar o sistema

- Após completar o trabalho, recomenda-se sair apropriadamente do sistema para não interromper os processos de forma abrupta.
- Deve-se utilizar os comandos `exit` ou `logout` para finalizar a sessão.
- Para desligar o sistema, o usuário pode utilizar os comandos: `halt`, `init 0`, `init 6`, `poweroff`, `reboot`, `shutdown`.
- Nem todos os sistemas rodam estes comandos. Para saber mais, utilize o _man pages_.

### Man Pages

- Para rodar o manual de algum comando disponível no UNIX, basta digitar `man <command>`.


## Usuários e Grupos

**Em progresso**

## Arquivos do Sistema

- Componente do Unix que habilita a visualização, organização segurança e interação de arquivos e diretórios.
- Existem 3 (três) tipos de _file systems_: orientado a disco, orientado a rede e virtual.
- Orientado a Disco (_disk-oriented_): arquivos do disco rígido, CD-ROM, DVD, USB. Por exemplo: UFS, FAT, NTFS.
- Orientado a Rede (_network-oriented_): arquivos que podem ser acessados por um ambiente remoto. Por exemplo: NFS, Samba e WebDAV.
- Especial: arquivos temporários e de processo.

### Aspectos Básicos

- Uma coleção lógica de arquivos em uma partição no disco.
- Uma partição é, por sua vez, um _container_ de informações.
- No Unix, tudo se inicia a partir do diretório _root_ (este diretório não deve ser confundido com o diretório _root_ do usuário).
- O Unix utiliza uma estrutura hierarquica.
- O UNIX trabalha com camnhos relativos e absolutos, além de ser Case Sensitivity.

### Navegação

**Em progresso**

## Configurações do Ambiente

**Em progresso**

## Comandos do UNIX

**Em progresso**

## Ferramentas

**Em progresso**

## Processos

**Em progresso**

## Rotinas

**Em progresso**

## Segurança

* Hardening SSH - Configurações feitas no `/etc/ssh/sshd_config` 
  1. Não permitir login diretamente pelo usuário root: `PermitRootLogin no`
  2. Usar separação de privilégios durante execução: `UsePrivilegeSeparation yes`
  3. Limitar acesso a usuários ou grupos: `AllowUsers root admin` ou `AllowGroup admins`
  4. Alterar porta padrão: `Port 1234`
  5. Limitar tempo de inatividade do login: `LoginGraceTime 1m`
    

## Shell Script

**Em progresso**

## Utilidades para UNIX Admins

- Usuários logados: `w` ou `who`







>>>>>>> Telnet um pouco mais completo
