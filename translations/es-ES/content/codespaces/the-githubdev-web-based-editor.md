---
title: El editor basado en web de github.dev
intro: 'Utiliza el github.dev {% data variables.product.prodname_serverless %} desde tu repositorio o solicitud de incorporación de cambios para crear y confirmar cambios.'
versions:
  feature: githubdev-editor
type: how_to
miniTocMaxHeadingLevel: 3
topics:
  - Codespaces
  - Visual Studio Code
  - Developer
shortTitle: Web-based editor
redirect_from:
  - /codespaces/developing-in-codespaces/web-based-editor
ms.openlocfilehash: 3fce192c2b0e890b2213dfd8f5f18dad1dc7fa05
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2022
ms.locfileid: '147431860'
---
{% note %}

**Nota:** github.dev {% data variables.product.prodname_serverless %} se encuentra actualmente en versión preliminar beta. Puede proporcionar comentarios [en nuestros debates](https://github.com/community/community/discussions/categories/general).

{% endnote %}

## Acerca de {% data variables.product.prodname_serverless %}

El {% data variables.product.prodname_serverless %} presenta una experiencia de edición ligera que se ejecuta completamente en tu buscador. Con el {% data variables.product.prodname_serverless %}, puedes navegar por los archivos y repositorios de código abierto desde {% data variables.product.prodname_dotcom %} y hacer y confirmar cambios de código. Puedes abrir cualquier repositorio, bifurcación o solicitud de cambios en el editor.

El {% data variables.product.prodname_serverless %} se encuentra disponible gratuitamente para todos en {% data variables.product.prodname_dotcom_the_website %}.

El {% data variables.product.prodname_serverless %} proporciona muchos de los beneficios de {% data variables.product.prodname_vscode %}, tales como búsqueda, resaltado de sintaxis y vista de control de código fuente. También puedes utilizar la sincronización de la configuración para compartir tus propios valores de configuración de {% data variables.product.prodname_vscode_shortname %} con el editor. Para obtener más información, consulta "[Sincronización de la configuración](https://code.visualstudio.com/docs/editor/settings-sync)" en la documentación de {% data variables.product.prodname_vscode_shortname %}.

El {% data variables.product.prodname_serverless %} se ejecuta completamente en el área de pruebas de tu buscador. El editor no clona el repositorio, sino que usa la [extensión GitHub Repositories](https://code.visualstudio.com/docs/editor/github#_github-repositories-extension) para llevar a cabo la mayor parte de la funcionalidad que usará. Tu trabajo se guarda en el almacenamiento local de tu buscador hasta que lo confirmes. Debes confirmar tus cambios frecuentemente para asegurarte de que siempre sean accesibles.

## Abrir el {% data variables.product.prodname_serverless %}

Puedes abrir cualquier repositorio de {% data variables.product.prodname_dotcom %} en el {% data variables.product.prodname_serverless %} en cualquiera de las siguientes formas:

- Para abrir el repositorio en la misma pestaña del explorador, presiona `.` al examinar cualquier repositorio o solicitud de incorporación de cambios en {% data variables.product.prodname_dotcom %}.
 
   Para abrir el repositorio en una nueva pestaña del explorador, mantén presionada la tecla mayús y presiona `.`.

- Cambiando la URL de "github.com" a "github.dev".
- Al ver un archivo, usa el menú desplegable situado junto a {% octicon "pencil" aria-label="The edit icon" %} y selecciona **Abrir en github.dev**.

  ![Menú desplegable del botón Editar archivo](/assets/images/help/repository/edit-file-edit-dropdown.png)

## {% data variables.product.prodname_codespaces %} y el {% data variables.product.prodname_serverless %}

Tanto el {% data variables.product.prodname_serverless %} como los {% data variables.product.prodname_github_codespaces %} te permiten editar el código directamente desde tu repositorio. Sin embargo, ambos tienen beneficios ligeramente diferentes, dependiendo de tu caso de uso.

|| {% data variables.product.prodname_serverless %} | {% data variables.product.prodname_codespaces %}|
|-|----------------|---------|
| **Costee** | Libre.      | Costos de cálculo y almacenamiento. Para obtener información sobre los precios, vea "[Precios de Codespaces](/en/billing/managing-billing-for-github-codespaces/about-billing-for-codespaces#codespaces-pricing)".|
| **Disponibilidad** | Disponible para todos en GitHub.com. | Disponible para las organizaciones que utilizan GitHub Team o GitHub Enterprise Cloud. |
| **Inicio** | El {% data variables.product.prodname_serverless %} se abre instantáneamente al presionar una tecla y puedes comenzar a usarlo de inmediato sin tener que esperar por configuraciones o instalaciones adicionales. | Al crear o reanudar un codespace, se le asigna una máquina virtual y el contenedor se configura en función del contenido de un archivo `devcontainer.json`. Esta configuración puede tomar algunos minutos para crear el ambiente. Para más información, vea "[Creación de un codespace](/codespaces/developing-in-codespaces/creating-a-codespace)". |
| **Proceso**  | No hay cálculos asociados, así que no podrás compilar y ejecutar tu código ni utilizar la terminal integrada. | Con {%  data   variables.product.prodname_codespaces %}, obtienes el poder de la MV dedicada en ela que ejecutas y depuras tu aplicación.|
| **Acceso al terminal** | Ninguno. | {% data variables.product.prodname_codespaces %} proporciona un conjunto común de herramientas predeterminadamente, lo que significa que puedes utilizar la terminal como lo harías en tu ambiente local.|
| **Extensiones**  | Solo un subconjunto de extensiones que pueden ejecutarse en la web aparecerá en la Vista de Extensiones y podrá instalarse. Para más información, vea "[Uso de extensiones](#using-extensions)".| Con Codespaces, puedes usar la mayoría de las extensiones del {% data variables.product.prodname_vscode_marketplace %}.|

### Seguir trabajando en {%  data   variables.product.prodname_codespaces %}

Puede iniciar el flujo de trabajo en {% data variables.product.prodname_serverless %} y seguir trabajando en un codespace, siempre que tenga [acceso a {% data variables.product.prodname_codespaces %}](/codespaces/developing-in-codespaces/creating-a-codespace#access-to-codespaces). Si intentas acceder a la Vista de Ejecución y Depuración o a la Terminal, se ten notificará que no están disponibles en {% data variables.product.prodname_serverless %}.

Para continuar el trabajo en un codespace, haga clic en **Continuar trabajando en...** y seleccione **Crear codespace** para crear un codespace en la rama actual. Antes de que elijas esta opción, debes confirmar cualquier cambio.

![Captura de pantalla en la que se muestra el botón "Continuar trabajando en" en la interfaz de usuario](/assets/images/help/codespaces/codespaces-continue-working.png)

## Utilizar el control de código fuente

Cuando utilizas el {% data variables.product.prodname_serverless %}, todas las acciones se administran a través de la Vista de Control de Código Fuente, la cual se ubica en la barra de actividad en la parte izquierda. Para obtener más información sobre la vista Control de código fuente, consulta "[Control de versiones](https://code.visualstudio.com/docs/editor/versioncontrol)" en la documentación de {% data variables.product.prodname_vscode_shortname %}.

Ya que el editor basado en web utiliza la extensión de repositorios de GitHub para alimentar su funcionalidad, puedes cambiar de rama sin necesidad de acumular cambios. Para obtener más información, consulta "[GitHub Repositories](https://code.visualstudio.com/docs/editor/github#_github-repositories-extension)" en la documentación de {% data variables.product.prodname_vscode_shortname %}.

### Creación de una rama

{% data reusables.codespaces.create-or-switch-branch %} Los cambios sin confirmar que haya realizado en la rama anterior estarán disponibles en la nueva.

### Confirmación de los cambios

{% data reusables.codespaces.source-control-commit-changes %} 
5. Una vez que hayas confirmado tus cambios, estos se subirán automáticamente a tu rama de {% data variables.product.prodname_dotcom %}.
### Creación de una solicitud de incorporación de cambios

{% data reusables.codespaces.source-control-pull-request %}

### Trabajar con una solicitud de cambios existente

Puedes utilizar el {% data variables.product.prodname_serverless %} para trabajar con una solicitud de cambios existente.

1. Navega hasta la solicitud de cambios que te gustaría utilizar en el {% data variables.product.prodname_serverless %}.
2. Presione `.` para abrir la solicitud de incorporación de cambios en {% data variables.product.prodname_serverless %}.
3. Una vez que haya realizado los cambios, confírmelos siguiendo los pasos descritos en [Confirmación de los cambios](#commit-your-changes). Tus cambios se confirmarán directamente en la rama, no es necesario subirlos.

## Uso de extensiones

El {% data variables.product.prodname_serverless %} es compatible con las extensiones de {% data variables.product.prodname_vscode_shortname %} que se hayan creado o actualizado específicamente para ejecutarse en la web. A estas extensiones se les conoce como "extensiones web". Para obtener información sobre cómo puedes crear una extensión web o actualizar la extensión existente a fin de que funcione para la web, consulta "[Extensiones web](https://code.visualstudio.com/api/extension-guides/web-extensions)" en la documentación de {% data variables.product.prodname_vscode_shortname %}.

Las extensiones que puedan ejecutarse en {% data variables.product.prodname_serverless %} aparecerán en la Vista de Extensiones y podrán instalarse. Si utilizas la sincronización de ajustes, cualquier extensión compatible también se instala automáticamente. Para obtener información, consulta "[Sincronización de la configuración](https://code.visualstudio.com/docs/editor/settings-sync)" en la documentación de {% data variables.product.prodname_vscode_shortname %}.


## Solución de problemas

Si tienes problemas para abrir el {% data variables.product.prodname_serverless %}, intenta lo siguiente:

- Asegúrate de estar firmado en {% data variables.product.prodname_dotcom %}.
- Inhabilita cualquier bloqueador de anuncios.
- Utiliza una ventana de tu buscador que no esté en modo incógnito para abrir el {% data variables.product.prodname_serverless %}.

### Limitaciones conocidas

- El {% data variables.product.prodname_serverless %} es actualmente compatible en Chrome (y en varios otros buscadores basados en Chromium), Edge, Firefox y Safari. Te recomendamos que utilices las últimas versiones de estos buscadores.
- Es posible que algunos enlaces de teclas no funcionen, dependiendo del buscador que estás utilizando. Estas limitaciones de enlace de claves se documentan en la sección "[Limitaciones y adaptaciones conocidas](https://code.visualstudio.com/docs/remote/codespaces#_known-limitations-and-adaptations)" de la documentación de {% data variables.product.prodname_vscode_shortname %}.
- Es posible que `.` no funcione para abrir {% data variables.product.prodname_serverless %} según el diseño de teclado local. En ese caso, puede abrir cualquier repositorio de {% data variables.product.prodname_dotcom %} en {% data variables.product.prodname_serverless %} si cambia la dirección URL de `github.com` a `github.dev`.
