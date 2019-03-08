---
title: Vývojové prostředí pro aplikace Dockeru
description: Seznámení s nejdůležitějších možností nástroj pro vývoj, které podporují Docker vývojového cyklu.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 38a9f8209200635c752f60af90e22ef916796525
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57677237"
---
# <a name="development-environment-for-docker-apps"></a>Vývojové prostředí pro aplikace Dockeru

## <a name="development-tools-choices-ide-or-editor"></a>Možnosti vývojářských nástrojů: Prostředím IDE nebo editorem

Bez ohledu na to pokud dáváte přednost úplné a výkonné IDE nebo editorem jednoduchý a flexibilní, Microsoft vám kryje záda při rozhodování o vývoji aplikací Dockeru.

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a>Visual Studio Code a rozhraní příkazového řádku Dockeru (nástrojů pro různé platformy pro Windows, Mac a Linux)

Pokud dáváte přednost zjednodušené, multiplatformní editor podporuje libovolný jazyk vývoj, můžete použít Visual Studio Code a rozhraní příkazového řádku Dockeru. Tyto produkty poskytují jednoduché a přitom robustní prostředí, což je velmi důležité pro zjednodušení pracovních postupů vývojářů. Nainstalováním "Dockeru pro Mac" nebo "Docker pro Windows" (vývojové prostředí) Dockeru mohou vývojáři jednotné rozhraní příkazového řádku Dockeru k vytváření aplikací pro Windows nebo Linuxem (prostředí runtime). Kromě toho Visual Studio Code podporuje rozšíření Dockeru s podporou technologie IntelliSense pro soubory Dockerfile a místní úlohy spouštět příkazy Dockeru z editoru.

> [!NOTE]
>
> Pokud chcete stáhnout Visual Studio Code, přejděte na <https://code.visualstudio.com/download>.
>
> Chcete-li stáhnout Docker pro Mac a Windows, přejděte na <https://www.docker.com/products/docker>.

### <a name="visual-studio-with-docker-tools-windows-development-machine"></a>Visual Studio s Docker Tools (Windows vývojovém počítači)

Doporučujeme použít Visual Studio 2017 (nebo novější) s integrovanou nástroje Dockeru povolena. Pomocí sady Visual Studio můžete vyvíjet, spouštět a ověřovat aplikace přímo ve zvoleném prostředí Dockeru. Stisknutím klávesy F5 pro ladění vaší aplikace (jedním kontejnerem nebo více kontejnerů) přímo do hostitele Docker nebo stisknutím kláves Ctrl + F5, upravit a aktualizovat aplikace bez nutnosti znovu sestavovat kontejner. Jedná se o nejjednodušší a nejvýkonnější volbu pro vývojáře Windows k vytvoření kontejnerů Dockeru pro Windows nebo Linuxem.

### <a name="visual-studio-for-mac-mac-development-machine"></a>Visual Studio pro Mac (vývoj pro počítač Mac)

Můžete použít [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/) při vývoji aplikací založených na Dockeru. Visual Studio pro Mac nabízí bohatší IDE ve srovnání s Visual Studio Code pro Mac

## <a name="language-and-framework-choices"></a>Volby jazyka a framework

Můžete vyvíjet aplikace Dockeru pomocí nástrojů společnosti Microsoft s většinou moderních jazyků. Toto je počáteční seznam, ale nejste omezeni pouze na něj:

- .NET Core a ASP.NET Core
- Node.js
- Go
- Java
- Ruby
- Python

V podstatě můžete použít libovolný moderní jazyk podporuje Docker v Linuxu nebo Windows.

>[!div class="step-by-step"]
>[Předchozí](deploy-azure-kubernetes-service.md)
>[další](docker-apps-inner-loop-workflow.md)
