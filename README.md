# beame-windows-installer
The Windows Installer tools are set of commands to install all prerequisites such as NPM, OpenSSL and more before installing the main component

This setup was designed to run on a windows 64 bits machine running .net framework 4.5 and was tested with windows server 2012 and 2016


## Running

The executable has to be run with Administrator permissions. If not given, it'll warn about the fact and exit.

### Interactively
In interactive mode, it'll display a menu with the available installation options
Currently they are:

    1. Gatekeeper
    2. BeameSDK
    7. Dependencies
    9. Exit
 
 Typing the wanted number and pressing enter will allow the option to be executed.
 
 Option 7 installs just the dependencies, while option 1 and 2 installs the dependencies together with the described product.
 
### Non-interactive
 Calling the executable with the option number as argument will allow an auto-select of that option. 


## Application Settings

Under the file `app.config` installer settings can be configured.

To do so, add the properties as `<add key="GatekeeperName" value="Beame Gatekeeper"/>` inside the `<appSettings>` tag.

Please not that all values are text fields

### Available settings
* GatekeeperName

    Name of the gatekeeper, will identify the gatekeeper in the mobile app and ui. e.g `Beame Gatekeeper`
* GatekeeperMode

    Type of gatekeeper to install. Can be `Gatekeeper`  or  `CentralLogin`

* EncryptUserData

    Configures gatekeeper option to encrypt user data. Can be `true` or `false` 

* AllowDirectSignin

    Configures gatekeeper option to allow direct login from the mobile phone (no need for a browser). Can be `true` or `false` 

* PublicRegistration

    Configures gatekeeper option to allow public user registration. Can be `true` or `false` 

* RegistrationImageRequired

    Configures gatekeeper option to require registration and login with user photo validation workload. Can be `true` or `false` 

* ProxyAddressProtocol

    Protocol of the proxy connection (`http` or `https`)
* ProxyAddressFqdn

    Proxy fqdn to use. Empty means no proxy
* ProxyAddressPort

    Proxy port to use
* ProxyAddressExcludes

    Addresses that ignore proxy settings (e.g. local network) separated by a ','
    Wildcard * can be used.
    e.g: `127.0.0.1,localhost,10.*`
* ExternalOcspServerFqdn

    Beame external Oscp server that also allows the communication of ntp. Required in case of proxy.
    e.g: `iep9bs1p7cj3cmit.tl5h1ipgobrdqsj6.v1.p.beameio.net`
    
* CustomGatekeeper

    Local path to the custom gatekeeper. The file needs to be a zip with the gatekeeper folder structure.
    When this property is not empty, this file will be used for the installation of the beame-gatekeeper.
* CustomGatekeeperCSS

    Local path to the custom gatekeeper css. The file needs to be a zip with the gatekeeper folder structure.
    Similar to the CustomGatekeeper setting, When this proterty is not empty, after the installation of the released gatekeeper and overriding by the customgatekeeper (if defined),  this file will override the installed gatekeeper with the contained files.

If any custom gatekeeper property is defined, the npm install and gulp options are executed on the final folder.

