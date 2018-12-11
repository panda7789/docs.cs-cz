---
title: Vývojové prostředí pro aplikace Dockeru
description: Životní cyklus aplikace kontejnerizovaných Dockeru s platformou a nástroji Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 471b52fd577e5560bd93e6da50f2032d63eb2e6f
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152407"
---
# <a name="development-environment-for-docker-apps"></a>Vývojové prostředí pro aplikace Dockeru

## <a name="development-tools-choices-ide-or-editor"></a>Možnosti vývojářských nástrojů: Prostředím IDE nebo editorem

Bez ohledu na to pokud dáváte přednost úplné a výkonné IDE nebo editorem jednoduchý a flexibilní, Microsoft vám kryje záda při rozhodování o vývoji aplikací Dockeru.

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a>Visual Studio Code a rozhraní příkazového řádku Dockeru (nástrojů pro různé platformy pro Windows, Mac a Linux)

Pokud dáváte přednost zjednodušené, multiplatformní editor podporuje libovolný jazyk vývoj, můžete použít Visual Studio Code a rozhraní příkazového řádku Dockeru. Tyto produkty poskytují jednoduché a přitom robustní prostředí, což je velmi důležité pro zjednodušení pracovních postupů vývojářů. Nainstalováním "Dockeru pro Mac" nebo "Docker pro Windows" (vývojové prostředí) Dockeru mohou vývojáři jednotné rozhraní příkazového řádku Dockeru k vytváření aplikací pro Windows nebo Linuxem (prostředí runtime). Kromě toho Visual Studio Code podporuje rozšíření Dockeru s podporou technologie IntelliSense pro soubory Dockerfile a místní úlohy spouštět příkazy Dockeru z editoru.

> [!NOTE]
> Pokud chcete stáhnout Visual Studio Code, přejděte na <https://code.visualstudio.com/download>.

Chcete-li stáhnout Docker pro Mac a Windows, přejděte na <https://www.docker.com/products/docker>.

### <a name="visual-studio-with-docker-tools"></a>Visual Studio s nástroji Dockeru

Pokud používáte Visual Studio 2015 můžete nainstalovat nástroje doplňků "Docker Tools for Visual Studio". Pro Visual Studio 2017 nástroje Dockeru pocházet integrované již. V obou případech můžete vyvíjet spouštět a ověřovat aplikace přímo ve zvoleném prostředí Dockeru. F5 aplikaci (jedním kontejnerem nebo více kontejnerů) přímo do Docker hostování s laděním, nebo stisknutím kláves Ctrl + F5, upravit a aktualizovat aplikace bez nutnosti znovu sestavovat kontejner. Toto je nejjednodušší a výkonnější volbou pro vývojáře Windows vytváření kontejnerů Dockeru pro Linux nebo Windows.

> [!NOTE]
> Chcete-li stáhnout Docker Tools for Visual Studio, přejděte na <https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>.

## <a name="language-and-framework-choices"></a>Volby jazyka a framework

Můžete vyvíjet Docker aplikacím a nástrojům společnosti Microsoft s většinou moderních jazyků. Toto je počáteční seznam, ale nejste omezeni na něj:

-   .NET Core a ASP.NET Core
-   Node.js
-   Golang
-   Java
-   Ruby
-   Python

V podstatě můžete použít libovolný moderní jazyk podporuje Docker v Linuxu nebo Windows.

>[!div class="step-by-step"]
>[Předchozí](orchestrate-high-scalability-availability.md)
>[další](docker-apps-inner-loop-workflow.md)