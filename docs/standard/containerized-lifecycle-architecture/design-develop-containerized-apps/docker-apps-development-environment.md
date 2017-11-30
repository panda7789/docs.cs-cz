---
title: "Vývojové prostředí pro Docker aplikace"
description: "Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: eedba16136ad394bda45cc871944f9b876c8ee38
ms.sourcegitcommit: 6f49c973f62855ffd6c4a322903e7dd50c5c1b50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2017
---
# <a name="development-environment-for-docker-apps"></a>Vývojové prostředí pro Docker aplikace

## <a name="development-tools-choices-ide-or-editor"></a>Vývojových nástrojů volby: IDE nebo editoru

Bez ohledu Pokud dáváte přednost úplné a výkonné IDE nebo jednoduchý a agilní editor, společnost Microsoft nemá je popsané, pokud jde o vývoj aplikací Docker.

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a>Visual Studio Code a příkazového řádku Dockeru (nástroje a platformy pro Mac, Linux a Windows)

Pokud dáváte přednost lightweight, napříč platformami editor podpora žádný jazyk vývoj, můžete použít Visual Studio Code a příkazového řádku Dockeru. Tyto produkty poskytují jednoduché, ale robustní prostředí, což je velmi důležitá pro zjednodušení pracovního postupu developer. Nainstalováním "Docker pro Mac" nebo "Docker pro systém Windows" (vývojové prostředí) Docker mohou vývojáři jednoho příkazového řádku Dockeru pro vývoj aplikací pro Windows nebo Linux (prostředí runtime). Navíc Visual Studio Code podporuje rozšíření pro Docker pomocí IntelliSense pro Dockerfiles a zástupce úlohy ke spuštění příkazů Docker v editoru.

> [!NOTE]
> Chcete-li stáhnout Visual Studio Code, přejděte na <https://code.visualstudio.com/download>.

Chcete-li stáhnout Docker pro Mac a Windows, přejděte na <http://www.docker.com/products/docker>.

### <a name="visual-studio-with-docker-tools"></a>Visual Studio s nástroji Docker

Pokud používáte Visual Studio 2015 můžete nainstalovat nástroje rozšíření "Docker Tools pro sadu Visual Studio". Pro Visual Studio 2017 nástroje Docker pocházet integrované již. V obou případech můžete vyvíjet, spuštění a ověření aplikace přímo ve zvolené Docker prostředí. F5 vaší aplikace (kontejner jednoho nebo několika kontejnerů) přímo do Docker hostitele s laděním nebo stiskněte klávesu Ctrl + F5 upravte a aktualizujte aplikaci bez nutnosti znovu sestavit kontejneru. Toto je nejjednodušší a výkonnější volba pro vývojáře systému Windows vytváření Docker kontejnery pro Linux nebo Windows.

> [!NOTE]
> Chcete-li stáhnout Docker nástrojů pro Visual Studio, přejděte na <https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>.

## <a name="language-and-framework-choices"></a>Možnosti jazyka a framework

Můžete vyvíjet aplikace Docker a nástroje Microsoft s většina moderních jazyků. Toto je počáteční seznam, ale nejste omezeni na ni:

-   .NET core a ASP.NET Core

-   Node.js

-   Golang

-   Java

-   Ruby

-   Python

V podstatě můžete použít jakýkoli moderní jazyk podporuje Docker v systému Linux nebo Windows.


>[!div class="step-by-step"]
[Předchozí] (orchestraci vysokou škálovatelnost availability.md) [Další] (docker aplikace vnitřní smyčky workflow.md)
