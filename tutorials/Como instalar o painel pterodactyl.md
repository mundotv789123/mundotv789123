### **Nesse tópico estarei ensinando a instalar o painel pterodactyl de forma simples e rápido.**

> Primeiro devemos nos atentar a versão do sistema operacional, a versão que irei usar é o ubuntu 20.04 (lembrando que também funciona para versões 20.X/18.X).

> A instalação será auxiliada atráves de um script que estarei disponibilizando no meu perfil do [github](https://github.com/mundotv789123/scripts/blob/master/install/pterodactyl_ssl.sh).

> Antes de iniciar a instalação vamos primeiro preparar nossa vps/dedicado.
A instalação exige que um nome de domínio esteja dedicado apenas para o painel, exemplo: painel.seudomínio.com
Lembrando que para esse tutorial iremos mantes o proxy do cloudflare desativado, para desativar basta desmarcar a nuvem do cloudflare.

![](https://mundotv789123.pages.dev/imgs/1652539624792.png)

> Verifique antes se todas as portas foram devidamente liberadas.
As portas que o painel pterodactyl precisa para funcionar são.

> - 22 - acesso ssh para executar os comandos de instalação.
> - 80 - servidor web usado pelo certbot para criar um certificado ssl.
> - 443 - servidor web com ssl usado pelo painel.
> - 8443 - node wings usado para acessar os servidores criados no painel.
> - 2022 - porta sftp usado para acessar os arquivos dos servidores criados no painel.

> Após a configuração vamos dar início a instalação.

> Para executar o script basta executar os seguintes comandos.

```bash
wget https://raw.githubusercontent.com/mundotv789123/scripts/master/install/pterodactyl_ssl.sh
chmod +x pterodactyl_ssl.sh
./pterodactyl_ssl.sh
```

![](https://mundotv789123.pages.dev/imgs/1652540268487.png)

> Após executar o script ele irá perguntar qual domínio você deseja usar, basta informar o domínio criado anteriormente.

![](https://mundotv789123.pages.dev/imgs/1652540483149.png)

> Após informar o domínio a instalação das dependenciar irá iniciar.
Nesse ponto o script irá perguntar se você deseja criar o certificado ssl, caso queira fazer a instalação automática basta clicar em y.

![](https://mundotv789123.pages.dev/imgs/1652540583857.png)

> Caso seja sua primeira vez gerando um certificado na vps ele irá pedir seu endereço de e-mail, basta informar e aceitar os termos.

![](https://mundotv789123.pages.dev/imgs/1652540672069.png)

> A partir desse ponto o script irá executar todas as partes chatas da instalação do pterodactyl.

> Quando finalizado ele irá perguntar se você deseja instalar o phpmyadmin, se confirmado o acesso ficará em **painel.seudomínio.com/phpmyadmin**

![](https://mundotv789123.pages.dev/imgs/1652540849291.png)

> Quando finalizado o script irá armazenar as informações de acesso em /root/pterodactyl_password.txt

![](https://mundotv789123.pages.dev/imgs/1652541032846.png)

> A partir daqui irá começar o processo de configuração do painel pterodactyl.

> Primeiro vamos fazer o login acessando nosso domínio informando inicialmente.
> Clicando na engrenagem no canto superior direito iremos acessar a área admin do painel.

![](https://mundotv789123.pages.dev/imgs/1652541149055.png)

> Na aba admin iremos criar uma localização para o node.

![](https://mundotv789123.pages.dev/imgs/1652541207666.png)

![](https://mundotv789123.pages.dev/imgs/1652541237006.png)

![](https://mundotv789123.pages.dev/imgs/1652541299765.png)

> após isso vamos criar um node para o painel

![](https://mundotv789123.pages.dev/imgs/1652541339150.png)

![](https://mundotv789123.pages.dev/imgs/1652541376568.png)

![](https://mundotv789123.pages.dev/imgs/1652541531220.png)

> Como o node está na mesma máquina que o painel optei por usar o mesmo domínio, caso você esteja usando o painel separado irá precisar criar um novo domínio e gerar um certificado ssl para o mesmo.

> Na aba configuration iremos copiar todo o arquivo de configuração.

> Em seguida no terminal iremos executar o seguinte comando nano `/etc/pterodactyl/config.yml` basta clicar com o botão direito e em seguicar colar.

![](https://mundotv789123.pages.dev/imgs/1652541825487.png)

> Após fazer isso basta clicar **ctrl + s** e em seguida **ctrl + x**.

> Em seguinda basta executar o comando `systemctl start wings`.

![](https://mundotv789123.pages.dev/imgs/1652541905590.png)

> Para confirmar se o node está funcionando basta executar `systemctl status wings`.

![](https://mundotv789123.pages.dev/imgs/1652541959398.png)

> Você pode confirmar também se o painel está se comunicando com o node wings.

> Basta verificar se o coração está verde indicando que está online.

![](https://mundotv789123.pages.dev/imgs/1652542039171.png)

> E pronto! seu painel foi instalado com sucesso, agora só criar e configurar o servidores.

> Lembre-se de adicionar as portas dos servidores no node criado.

![](https://mundotv789123.pages.dev/imgs/1652542124916.png)
