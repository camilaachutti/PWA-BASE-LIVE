## Publicação

### Noções de Terminal
O terminal nada mais é que outra forma de interagir com o computador. Estamos habituados a utilizar uma interface gráfica composta de janelas e ícones para realizar as tarefas que necessitamos no dia-a-dia, como abrir um editor de texto, salvar um arquivo ou acessar uma página da internet.

Essas mesmas atividades podem ser realizadas unicamente através de comandos no terminal. Ainda que esse método possua uma maior curva de aprendizado, ele possibilita uma flexibilidade e agilidade muito grande, de forma que ele se torna uma ferramenta de trabalho diário da maioria dos programadores.

```
windows: procure por *cmd* no menu iniciar  
macos: procure por *terminal* no Spotlight
```

| Comando | Descrição |
|---------|-----------|
| cd | muda de diretório |
| dir (windows) | lista os arquivos do diretório atual |
| ls (mac/linux) | lista os arquivos do diretório atual |

### Firebase
O Firebase é um serviço cloud do Google que permite, entre outras coisas, a hospedagem gratuita de sites. Vamos utilizá-lo para publicar os trabalhos que realizarmos no curso. Para isso, precisamos de três coisas: uma conta no Google, um projeto criado no Firebase e o programa de terminal do Firebase instalado em nosso computador (Firebase CLI).

#### 1) Como instalar o Firebase CLI
O pré-requisito para instalar o Firebase CLI é possuir o NodeJS instalado no computador. O NodeJS é um ambiente de execução de Javascript para terminal, e pode ser baixado através do site [https://nodejs.org].

Após a instalação do NodeJS, basta abrir o terminal e usar o comando:

`npm install -g firebase-cli` (windows)

`sudo npm install -g firebase-cli` (macos/linux)

#### 2) Como criar um novo projeto no Firebase
1- Acessar o Firebase através de uma conta do Google em [https://firebase.google.com/]

2- Clicar em *Go to Console*

3- Clicar em *Add Project*

4- Digitar o nome para seu projeto e aceitar os termos de serviço

5- Clicar em *Create Project*

#### 3) Como publicar um site no Firebase
1- Abrir o terminal

2- Copie o caminho da pasta através do gerenciador de arquivos

3- Digite `cd caminho/para/pasta` no terminal e pressione enter

4- Digite `firebase init` e pressione enter

5- Na lista apresentada, escolha a opção *Hosting* com a barra de espaços e pressione enter

6- Selecione o projeto que você criou anteriormente Firebase e pressione enter

7- *What do you want to use as your public directory?* Digite `.` e pressione enter

8- *Configure as a single-page app (rewrite all urls to /index.html)?* Digite `n` e pressione enter

9- O menu interativo irá encerrar. Digite o comando `firebase deploy` e pressione enter

No final irão aparecer o 2 links de acesso, onde o segundo será possível ver seu site online.

## Aplicativos Mobile

### Opção 1: Aplicativos Nativos
Essa é a forma padrão para programar uma app mobile. Como as plataformas possuem kits de desenvolvimento diferentes, é necessário criar duas versões do aplicativo, uma para Android e outra para iOS.

**Vantagens:** maior performance e flexibilidade de uso de recursos plataforma.
**Desvantagens:** maior custo e tempo de desenvolvimento, manutenção de duas bases de código.

### Opção 2: Aplicativos Nativos com base de código compartilhada
Para resolver o problema de manter duas bases de código, surgiram frameworks que unificam o fluxo de desenvolvimento e, a partir de um único código fonte, compila-se duas versões do aplicativo. O Xamarin da Microsoft e o React Native do Facebook são exemplos dessa abordagem.

**Vantagens:** maior agilidade no desenvolvimento e alteração de apps
**Desvantagens:** menor flexibilidade para uso de recursos nativos, ainda é necessário fazer ajustes específicos por plataforma

### Opção 3: Aplicativos Híbridos
Essa abordagem emprega o uso de tecnologias web para criar a interface do aplicativo, ou  seja, o aplicativo em realidade é um "site" que é instalado no celular através de uma camada de código nativa. Para usar recursos nativos do celular (GPS, acelerômetro, giroscópio, push notification), o Javascript tem acesso a uma interface de programação que faz a ponte entre o código web e o nativo. O Cordova e o Ionic são os exemplos mais famosos de plataformas para desenvolvimento de apps híbridos.

**Vantagens:** é uma das formas mais rápidas e baratas para desenvolvimento de apps, um programador web pode reutilizar seus conhecimentos de HTML, CSS e JS
**Desvantagens:** menor performance e maior quantidade de limitações em relação a apps puramente nativos

### Opção 4: PWA
O PWA (Progressive Web Apps) é uma opção relativamente nova para o desenvolvimento de aplicações mobile. Ela consiste em uma aplicação puramente web que pode ser instalada no celular diretamente do browser, mantendo funcionalidades offline e com um ícone para acesso disponível na gaveta de aplicativos. As novas versões dos sistemas iOS e Android suportam os PWAs, o que tem aumentado significativamente sua popularidade.

**Vantagens:** é uma das formas mais rápidas e baratas para desenvolvimento de apps, um programador web pode reutilizar seus conhecimentos de HTML, CSS e JS
**Desvantagens:** menor performance e maior quantidade de limitações em relação a apps puramente nativos

> Quer identificar um PWA? Basta utilizar o Lighthouse. Trata-se de uma extensão do Google Chrome produzida pelo próprio Google que faz diversos testes com a página, como testes de cache offline ou com uma conexão de internet ruim, responsividade em diferentes resoluções, tempo de carregamento, meta informações, etc.

## Como criar um PWA
Para ser identificado corretamente como um PWA, um site precisa atender alguns requisitos:

1- Possuir um manifest.json, que fornece metadados sobre a instalação ao app
2- Possuir um service-worker, que faz o cache de informações para acesso offline
3- Ser servido em conexão criptografada (HTTPS)
4- Ser responsivo, possuir tempo rápido de carregamento e funcionar nos principais browsers

> Para ver essa lista com detalhes, visite a página oficial do Google em https://developers.google.com/web/progressive-web-apps/checklist

> Utilizar como base para a criação dos PWAs o código disponível em https://github.com/mastertech-aulas/pwa-base

### O manifest.json

O arquivo manifest.json deve ser criado na pasta raiz do site e deve ser referenciado no head da página da seguinte forma:

```
<link rel="manifest" href="/manifest.json">
```

Este é um exemplo do conteúdo do arquivo com as propriedades mais comuns:
```
{
  "name": "Meu App",
  "short_name": "MApp",
  "icons": [
    {
      "src": "img/icon-192.png",
      "sizes": "192x192",
      "type": "image/png"
    },
    {
      "src": "img/icon-512.png",
      "sizes": "512x512",
      "type": "image/png"
    }
  ],
  "start_url": "/index.html",
  "display": "fullscreen",
  "background_color": "#3E4EB8",
  "theme_color": "#2F3BA2"
}
```

**name**: O nome completo do app.

**short_name**: O nome que é efetivamente utilizado abaixo do ícone do app, após instalado.

**icons**: Ícone para o app. O exemplo mostra dois tamanhos padrão para o ícone, porém não são os únicos tamanhos disponíveis. Note que cada arquivo de imagem deve conter exatamente a resolução em pixels descrita.

**start_url**: Arquivo de HTML que é utilizado como página principal da aplicação.

**display**: Determina o comportamento do app após instalado no celular.
- *fullscreen* exibe o app em tela cheia, sem a barra de navegação do browser e a barra de status do sistema operacional do celular
- *standalone* exibe o app de forma similar à outros apps nativos
- *browser* exibe o app dentro do browser, similar à um website

**background_color**: Cor de fundo da aplicação enquanto o CSS não é carregado. Afeta a *splash screen* no Android, que é a tela de carregamento inicial de um app.

**theme_color**: Cor do tema do app. Afeta características diversas, como a cor da barra de status na parte superior do sistema Android.

### O service-worker

O service worker é essencialmente um arquivo de Javascript que funciona de forma independente à página e tem a tarefa de interceptar requisições para a web e fazer o cache de informações para o funcionamento offline da aplicação.

Vamos utilizar um modelo padrão de service-worker que faz o cache de todos os arquivos estáticos do site (folhas de estilo, scripts, imagens, etc):

```
let cacheName = 'meu-app-cache-v1';
let filesToCache = [
    '/',
    '/index.html',
    '/main.js',
    '/main.css'
];

self.addEventListener('install', function(event) {
    console.log('[ServiceWorker] Install');
    event.waitUntil(
        caches.open(cacheName).then(function(cache) {
            console.log('[ServiceWorker] Caching app shell');
            return cache.addAll(filesToCache);
        })
    );
});

self.addEventListener('fetch', function(event) {
    console.log('[Service Worker] Fetch', event.request.url);    
    event.respondWith(
        caches.match(event.request).then(function(response) {
            return response || fetch(event.request);
        })
    );
});

self.addEventListener('activate', function(event) {
    console.log('[ServiceWorker] Activate');
    event.waitUntil(
        caches.keys().then(function(keyList) {
            return Promise.all(keyList.map(function(key) {
                if (key !== cacheName) {
                    console.log('[ServiceWorker] Removing old cache', key);
                    return caches.delete(key);
                }
            }));
        })
    );
});
```

É importante adicionar qualquer arquivo que deve estar disponível offline dentro do vetor **filesToCache**. Cuidado ao manipular essa variável, pois a adição de qualquer arquivo inexistente irá gerar um erro que impede o funcionamento do service-worker.

O service-worker deve então ser referenciado dentro de um script que está vinculado à página, visto que não há forma de referenciá-lo diretamente do HTML. O seguinte código registra o service-worker em browsers compatíveis:

```
if ('serviceWorker' in navigator) {
    navigator.serviceWorker
    .register('./service-worker.js')
    .then(function() {
        console.log('Service Worker Registered');
    }, function(error){
        console.error(error);
    });
}
```
