# NightwatchJs

Este é um repositório para que eu nunca esqueça como instalar o Nightwatch. E aproveitando, para você, que esteja lendo isso aqui, te ajude de alguma forma. Compartilhar conhecimento é uma dádiva!

# Nightwatch.js, o quê é?
É uma estrutura de testes automatizada tanto para aplicativos e sites que permite usar Javascript.



# Etapas de instalação.

1. Baixe o Node (o mais recente, Long-Term Support (LTS) version)
2. Instale o Node (apenas dê next-next-next)

# Preparando a workspace.
1. Abra o Terminal window
2. Mude para o seu diretório pessoal digitando: cd ~
3. Crie um novo diretório chamado “automation”: mkdir automation
4. Agora mude para este novo diretório: cd automation
5. Crie uma nova pasta para arquivos binários: mkdir bin
6. Agora crie uma pasta para testes: mkdir tests

# Selenium server.
O Nightwatch.js usa o Selenium para realizar testes, então você precisará de uma cópia do Selenium Server:
Você pode achar mais fácil abrir essa pasta fora do Terminal.
Vá até a página Downloads do Selenium e clique no link de download da versão mais recente do Selenium Standalone Server.
Isso deve baixar um arquivo JAR, basta copiar/colar este arquivo na pasta bin.


# Driver do Chrome.
Agora você irá precisar do Chrome, caso não tenha ainda, a gente espera você instalar...
Este driver permite que o Selenium controle o Chrome para você. As etapas para buscar isso são muito semelhantes às etapas do Selenium Server acima:
Navegue até a página de downloads de driver do Chrome e clique no link para a versão mais recente.
Você verá uma lista de arquivos ZIP; clique no link relevante para o seu sistema operacional.
Uma vez baixado, você deve extrair o conteúdo deste arquivo ZIP para a pasta bin que criamos nas etapas acima.


# Instalando o Nightwatch.js.
Crie um arquivo de configuração do Nightwatch.
Agora que você seguiu todas as etapas acima, você deve ter uma pasta chamada automação, que contém uma pasta bin com uma cópia do Selenium Standalone Server e do Chrome Driver e uma pasta vazia de testes.
A próxima coisa que vamos fazer é criar um arquivo de configuração para o Nightwatch.js se referir.
Abra seu editor de texto favorito e crie um arquivo chamado nightwatch.json. Salve isso na pasta de automação.
Cole o seguinte conteúdo neste novo arquivo:

```json
{
  "src_folders" : ["tests"],
  "output_folder" : "reports",

  "selenium" : {
    "start_process" : true,
    "server_path" : "bin/selenium-server-standalone-3.0.1.jar",
    "log_path" : "",
    "port" : 4444,

    "cli_args" : {
      "webdriver.chrome.driver" : "bin/chromedriver"
    }
  },

  "test_settings" : {
    "default" : {
      "launch_url" : "http://localhost",
      "selenium_port"  : 4444,
      "selenium_host"  : "localhost",
      "silent": true,

      "screenshots" : {
        "enabled" : false,
        "path" : ""
      },

      "desiredCapabilities": {
        "browserName": "chrome"
      }
    }
  }
}
```

# Instalar Nightwatch.
Abra sua janela do Terminal. Se você ainda não estiver lá, altere para o diretório de automação digitando cd ~ / automation.
Instale o nightwatch digitando npm install nightwatch.
É importante observar que você pode instalar o nightwatch globalmente em sua máquina digitando npm install -g nightwatch. Isso tem a vantagem de permitir que você execute nightwatch de qualquer pasta, no entanto eu prefiro uma instalação local.

# Seu primeiro teste
Crie um novo arquivo dentro de sua pasta de automação / testes chamada firstTest.js.
Cole o seguinte conteúdo e salve o arquivo:

```javascript
module.exports = {
  'Basic Google search' : function (browser) {
    browser
      .url('https://www.google.com')
      .waitForElementVisible('input[name="q"]', 1000)
      .setValue('input[name="q"]', 'Guinea pig existential crisis')
      .submitForm('form')
      .waitForElementVisible('#resultStats', 1000)
      .assert.urlContains('q=Guinea+pig')
      .end();
  }
};
```

Agora, para o momento da verdade, na janela do Terminal (dentro do diretório de automação), simplesmente execute o nó node_modules / nightwatch / bin / nightwatch.
Você deve abrir o Chrome e realizar uma pesquisa básica.



Obs.: Não esquecer de sempre ir no site do Nightwatch para tirar dúvidas.




Thanks mailosaur.com
It's all your credits!

