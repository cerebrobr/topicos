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
- Padrão POSIX
- Richard Stallman inicia o projeto GNU em 1984 com a intenção de criar um sistema Unix-like, mas com distribuição livre.
- Em 1991, Linus Torvalds á início a criação do Linux. Atualmente, o Linux é o Kernel, enquanto as ferramentas, shell e arquivos de sistema fazem parte do GNU. Por isso, damos o nome de GNU/Linux.

### Kernel

- Camada de nível mais baixo do Unix.
- Controla processos, dispositivos de entrada/saída, operações de arquivos do sistema e outras funções necessárias para a operação do sistema.
- Contruído para um hardware específico.
- Não pode ser manuseado pelo usuário (geralmente)
- Facilita a criação e gerenciamento de processos (muitas vezes chamados de _jobs_ ou _tasks_).
- O Kernel manuseia a memória do sistema. Quando um processo é iniciado, mas a memória física não oferece mais suporte para a execução desta tarefa, a memória virtual entra em ação para acomodar este processo, movendo algumas partes para o disco rígido. Quando esta mesma porção é solicitada novamente, ela retorna para a memória física. Este procedimento é chamado de _paging_.
- Ainda temos outro aspecto quanto a memória, chamado de _swap_. Neste caso, o processo é movido por completo para o disco rigído. O espaço destinado a este processo no disco rígido chama-se _swap espace_ no Unix. É importante certificar-se de que o espaço destinado para este processo seja suficiente, do contrário o usuário será punido com uma perda de performance considerável.

### Shell

- É o interpretador da linha de comando.
- Reponsável por permitir a interação entre o usuário e as operaçõs no sistema.
- Existem três Shells primários: Bourne Shell (conhecido como _sh_), C Shell (_csh_) e Korn Shell (_ksh_).
- Não somente, existem outras variantes para o Shell. Utilize a que estiver mais adequada par as suas necessidades.

### Componentes

- São os utilitários e arquivos do sistema. É o que torna capaz a visualização, organização e interação de modo consistente com os arquivos e diretórios disponíveis em dispositivos de armazenamento pelo usuário.


## Sistema

### Inicialização

- Chamamos de _boot process_, o processo que ocorre entre a posição inicial do seu sistema (desligado), até o momento em que o seu sistema está completamente carregado/disponível/acessível.
- O processo de identificação do device é chamado de _bootstrapping_.
- O dispositívo de _boot_ não precisa ser um dispositivo físico. O mesmo pode ser feito através da rede ou por um dispositivo de armazenamento externo (USB, CD-ROM).
- O dispositivo de _boot_ contém apenas as informações necessárias para carregar o sistema operacional.
- Após o _bootstrapping_, o Kernel começa a ser carregado.

### Autenticação

- O _Log In_ e _Log Out_ pode ser efetuado através de uma GUI ou no CLI, depende da variante que estiver sendo utilizada (Mac, Solaris, Linux, etc).
- No momento da autenticação através do CLI temos um banner, o qual consiste, geralmente, de 3 (três) linhas indicando a versão do OS, do kernel e o host/ip da rede.
- Em sistemas públicos, estas informações devem ser ocultadas por razões de segurança.
- É possível utilizar a autenticação remota através do protocolo TCP/IP.
- Este protocolo permite a transferência de dados entre diferentes sistemas.
- Alguns métodos para login remoto são: ssh, telnet, sftp, ftp.
- Haviam outros métodos para conexão remota, mas foram abandonados por questões de segurança. São eles: rcp, rlogin e rsh.
- O `telnet` possui a mesma função do `rsh` e do `rlogin`, já o `ftp` é similar ao `rcp`.
- Para haver a comunicação entre os sistemas (local <-> remoto), o acesso precisa estar liberado (sem firewalls ou restrições do sistema).

#### Via SSH

- Possibilita acesso remoto a fim de possibilitar a execução de comandos em outro sistema.
- O uso é feito com, no mínimo: `<commando> <hostname>`
- `commando`: refere-se ao protocolo de comunicação que o usuário deseja utilizar
- `hostname`: refere-se ao nome atual da máquina ou o IP da rede (192.168.0.*).
- Dar preferência o uso do _SSH_ ao _telnet_, pois a sessão será encriptada.
- Caso seja o primeiro acesso remoto, uma chave de autenticação será registrada na máquina. Caso alguém tente modificá-la ou ter acesso ao sistema que não seja por essa chave, o usuário (admin) será notificado.
- Ao utilizar `ssh hostname`, o protocolo assumi que o usuário deseja logar no sistema remoto com o mesmo nome do usuário.
- Para acessar com outro _username_, é preciso declarar no Shell com: `ssh username@hostname`.

#### Via telnet

- Nem todos os sistemas permitem o uso de SSH, sendo assim será necessário o uso do telnet.
- Não realiza a encriptação de dados durante a sessão (local <-> remoto).
- Outra diferença é que o telnet vai abrir um prompt para que seja inserido o _username_ e _password_.
- Nem sempre o `telnet` sabe que

### Finalizar / Desligar o sistema

- Após completar o trabalho, recomenda-se sair apropriadamente do sistema para não interromper os processos de forma abrupta.
- Deve-se utilizar o `exit` ou `logout` para finalizar a sessão.
- Para desligar o sistema, o usuário pode utilizar os comandos: `halt`, `init 0`, `init 6`, `poweroff`, `reboot`, `shutdown`.
- Nem todos os sistemas rodam estes comandos. Para saber mais, utilize o _man pages_.

### Man Pages

- Para rodar o manual de algum comando disponível no UNIX, basta digitar `man <commando>`.


## Usuários e Grupos

**Em progresso**

## Arquivos do Sistema

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

**Em progresso**

## Shell Script

**Em progresso**

## Utilidades para UNIX Admins

**Em progresso**
