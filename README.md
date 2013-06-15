
O Que é o Firefox OS?
==================================================================================

O Firefox OS é um novo sistema operacional móvel desenvolvido pelo projeto Boot to Gecko (B2G) da Mozilla. Ele usa o Kernel do Linux e inicializa em um sistema baseado no Gecko que permite que os usuários utilizem apps inteiramente desenvolvidos utilizando HTML, Javascript e outras APIs da Web Aberta.


Arquitetura do Firefox OS
==================================================================================

- Gaia
Coleção de aplicativos web que fazem a UI

- Gecko
Motor de JS e Renderização de HTML, APIs amigáveis para acesso ao hardware

- Gonk
Kernel Linux, Device drivers e camada de abstração do hardware


Firefox OS Simulator
==================================================================================

https://hacks.mozilla.org/2013/03/firefox-os-simulator-previewing-version-3-0/


Exemplo de manifesto
==================================================================================
```
{
  "name": "Meu App",
  "description": "Minha descrição",
  "launch_path": "/",
  "icons": { "128": "/img/icon-128.png" },
  "developer": {
    "name": "Meu nome ou organização",
    "url": "http://sua-pagina-aqui.org"
  }
}
```


Instalando apps a partir da web
==================================================================================

```
var installapp = navigator.mozApps.install(manifestURL);
installapp.onsuccess = function(data) {
  // App foi instalada
};
installapp.onerror = function() {
 // App não foi instalada, informações em 
 // installapp.error.name
};
```


Tres níveis de acesso…
==================================================================================

- Apps hospedados 
armazenada no seu servidor, fácil de atualizar, acesso ao hardware limitado.

- Apps privilegiados
verificada pelo Marketplace, utiliza uma Politica de Segurança de Conteúdo, armazenada em um servidor confiável.

- Apps certificados
parte do sistema operacional, apenas para a Mozilla e parceiros.


Web APIs (apps hospedados)
==================================================================================

Vibration API
Screen Orientation
Geolocation API
Mouse Lock API
Open WebApps
Network Information API
Battery Status API
Alarm API
Push Notifications API
WebFM API / FMRadio
WebPayment
IndexedDB
Ambient light sensor
Proximity sensor
Notification

https://hacks.mozilla.org/2013/02/using-webapis-to-make-the-web-layer-more-capable/


Web APIs (apps privilegiadas)
==================================================================================

Device Storage API
Browser API
TCP Socket API
Contacts API
systemXHR


Web APIs (certified apps)
==================================================================================

WebTelephony
WebSMS
Idle API
Settings API
Power Management API
Mobile Connection API
WiFi Information API
WebBluetooth
Permissions API
Network Stats API
Camera API
Time/Clock API
Attention screen
Voicemail


Contacts API
==================================================================================

```
var contact = new mozContact();

contact.init({name: "Odin"});

var request = navigator.mozContacts.save(contact);

request.onsuccess = function() {
	// contato salvo com sucesso
};
request.onerror = function() {
	// não foi possível salvar o contato
};
```


Web Activities
==================================================================================

configure
costcontrol
dial
open
pick
record
save-bookmark
share
view
new, exemplo: “websms/sms” or “webcontacts/contact”

https://wiki.mozilla.org/WebAPI/WebActivities


Discando para um telefone
==================================================================================

```
var call = new MozActivity({
  name: "dial",
  data: {
    number: "26091048"
  }
});
```


Pegando uma imagem
==================================================================================

```
var getphoto = new MozActivity({
  name: "pick",
  data: {
    type: ["image/png", "image/jpg", "image/jpeg"]
  }
});
```


Pegando uma imagem
==================================================================================

```
getphoto.onsuccess = function () {
  var img = document.createElement("img");
  if (this.result.blob.type.indexOf("image") != -1) {
    img.src = window.URL.createObjectURL(this.result.blob);
  }
};
getphoto.onerror = function () { // erro!
};
```


Requisitos
==================================================================================

1. Baixar o Firefox Nightly em http://nightly.mozilla.org.
2. Instalar o Simulador do Firefox OS.
	Firefox em Inglês: Tools → Add-ons
	Firefox em Português: Ferramentas → Complementos
3. Utilizar um bom editor de textos como por exemplo:
	Brackets (OSX/WIN): http://brackets.io/.
	SublimeText2 (OSX/WIN/LINUX): http://www.sublimetext.com/.


Open Web Apps
==================================================================================

Open Web Apps suportam mais que apenas o Firefox OS. Elas podem ser instaladas nas seguintes plataformas:

    Firefox OS.
    Android via Firefox for Android.
    Desktop via Firefox Aurora.

Perguntas & Respostas
==================================================================================

http://mozillabrasil.org.br/
http://www.mozilla.org/about/manifesto.pt-br.html
https://wiki.mozilla.org/WebAPI
https://wiki.mozilla.org/Apps
https://marketplace.firefox.com/pt-BR/
https://marketplace.firefox.org/pt-BR/developers
Baixe o Simulador do Firefox OS: Firefox OS 3.0 Simulator
Use (e contribua!) para a Mozilla Developer Network
http://geeksphone.com/pt-br/


==================================================================================

    http://andregarzia.com
    @soapdog
    http://mozillabrasil.org.br

