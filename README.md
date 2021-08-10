# Node-RED

http://nodered.org

[![Build Status](https://travis-ci.org/node-red/node-red.svg?branch=master)](https://travis-ci.org/node-red/node-red)
[![Coverage Status](https://coveralls.io/repos/node-red/node-red/badge.svg?branch=master)](https://coveralls.io/r/node-red/node-red?branch=master)

Low-code programming for event-driven applications.

![Node-RED: Low-code programming for event-driven applications](http://nodered.org/images/node-red-screenshot.png)

## Quick Start

Check out http://nodered.org/docs/getting-started/ for full instructions on getting
started.

1. `sudo npm install -g --unsafe-perm node-red`
2. `node-red`
3. Open <http://localhost:1880>

## Getting Help

More documentation can be found [here](http://nodered.org/docs).

For further help, or general discussion, please use the [Node-RED Forum](https://discourse.nodered.org) or [slack team](https://nodered.org/slack).

## Developers

If you want to run the latest code from git, here's how to get started:

1. Clone the code:

        git clone https://github.com/node-red/node-red.git
        cd node-red

2. Install the node-red dependencies

        npm install

3. Build the code

        npm run build

4. Run

        npm start

## Contributing

Before raising a pull-request, please read our
[contributing guide](https://github.com/node-red/node-red/blob/master/CONTRIBUTING.md).

This project adheres to the [Contributor Covenant 1.4](http://contributor-covenant.org/version/1/4/).
 By participating, you are expected to uphold this code. Please report unacceptable
 behavior to any of the project's core team at team@nodered.org.

## Authors

Node-RED is a project of the [OpenJS Foundation](https://openjsf.org).

It was created by [IBM Emerging Technology](https://www.ibm.com/blogs/emerging-technology/).

* Nick O'Leary [@knolleary](http://twitter.com/knolleary)
* Dave Conway-Jones [@ceejay](http://twitter.com/ceejay)



## Copyright and license

Copyright OpenJS Foundation and other contributors, https://openjsf.org under [the Apache 2.0 license](LICENSE).

# Alteções Denox
Alterações visuais para embedar Node-RED no GO

Salvamento automático e retirada de avisos pós salvamento
Pasta: node-red/packages/node_modules/@node-red/editor-client/src/js/ui/deploy.js
Editar arquivo deploy.js:
function save(skipValidation,force) {
        //Comentar linhas
        // $("#red-ui-header-shade").show();
        // $("#red-ui-editor-shade").show();
        // $("#red-ui-palette-shade").show();
        // $("#red-ui-sidebar-shade").show();
        ...
        //Comentar retorno visual
	if (hasUnusedConfig) {
            // RED.notify(
            // '<p>'+RED._("deploy.successfulDeploy")+'</p>'+
            // '<p>'+RED._("deploy.unusedConfigNodes")+' <a href="#" onclick="RED.sidebar.config.show(true); return false;">'+RED._("deploy.unusedConfigNodesLink")+'</a></p>',"success",false,6000);
        } else {
            // RED.notify('<p>'+RED._("deploy.successfulDeploy")+'</p>',"success");
        }
                
	//Antes do return
	//Funcao que executa repetição de salvar a cada 1s
	
        setInterval(save, 1000);

	return {
	  ...
	}
}

# Alteração visual para retirada da barra de menu principal
# ARQUIVO 01
Path: node-red/packages/node_modules/@node-red/editor-client/src/sass/header.scss
Alteração de arquivos scss:
// Adicionar no inicio do arquivo
#red-ui-main-container.hide{
    //Remover espaço barra de menu
    top: 0px !important;
}

Adicionar em #red-ui-header
#red-ui-header {
	....
	//Não mostrar barra de menu com logo
	display: none;
	span.red-ui-header-logo { ...
}

# ARQUIVO 02
Path: node-red/packages/node_modules/@node-red/editor-client/src/sass/tabs.scss
Alteração em .red-ui-tab-button
.red-ui-tab-button {
   ...
   display: none;
}

Adicionar:
#red-ui-tab-context-link-button{
    display: none !important;
}

#red-ui-tab-config-link-button{
    display: none !important;
}

.red-ui-tab-link-button-menu{
    display: none !important;
}

# ARQUIVO 03
Path: node-red/packages/node_modules/@node-red/editor-client/src/sass/workspace.scss
Adicionar acima de #red-ui-workspace-tabs:not:

#red-ui-workspace-tabs{
    display: none;
}


OBS: Após alteração é necessário compilar
npm run build

E iniciar
npm start
