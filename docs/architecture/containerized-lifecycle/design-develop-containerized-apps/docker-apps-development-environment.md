---
title: Vývojové prostředí pro aplikace Dockeru
description: Získejte informace o nejdůležitějších možnostech vývojářských nástrojů, které podporují životní cyklus vývojového prostředí Docker.
ms.date: 04/16/2020
ms.openlocfilehash: b1df16db88fa85f794407c989f5428030c4cddf7
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83394891"
---
# <a name="development-environment-for-docker-apps"></a>Vývojové prostředí pro aplikace Dockeru

## <a name="development-tools-choices-ide-or-editor"></a>Možnosti vývojových nástrojů: IDE nebo Editor

Bez ohledu na to, jestli dáváte přednost celému a výkonnému integrovanému vývojového prostředí (IDE) nebo odlehčenému a agilnímu editoru, Microsoft vás zajímá, pokud je součástí vývoje aplikací Docker.

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a>Visual Studio Code a Docker CLI (nástroje pro různé platformy pro Mac, Linux a Windows)

Pokud dáváte přednost zjednodušenému editoru pro různé platformy, který podporuje jazyk vývoje, můžete použít Visual Studio Code a Docker CLI. Tyto produkty poskytují jednoduché a stále robustní prostředí, které je důležité pro zjednodušení pracovního postupu vývojářů. Když nainstalujete "Docker pro Mac" nebo "Docker for Windows" (vývojové prostředí), můžou vývojáři Docker používat k vytváření aplikací pro Windows i Linux (běhové prostředí) jeden Docker CLI. Navíc Visual Studio Code podporuje rozšíření pro Docker pomocí IntelliSense pro fázemi a úlohy zástupce pro spouštění příkazů Docker z editoru.

> [!NOTE]
> Pokud chcete stáhnout Visual Studio Code, pokračujte na <https://code.visualstudio.com/download> .
>
> Chcete-li stáhnout Docker pro Mac a Windows, pokračujte na <https://www.docker.com/products/docker> .

### <a name="visual-studio-with-docker-tools-windows-development-machine"></a>Visual Studio s nástroji Docker (vývojový počítač s Windows)

Doporučujeme používat Visual Studio 2019 s povolenými integrovanými nástroji Docker. Se sadou Visual Studio můžete vyvíjet, spouštět a ověřovat aplikace přímo ve zvoleném prostředí Docker. Stiskněte klávesu F5, chcete-li ladit aplikaci (jeden kontejner nebo více kontejnerů) přímo v hostiteli Docker, nebo stiskněte klávesy CTRL + F5 pro úpravu a aktualizaci aplikace bez nutnosti opětovného sestavení kontejneru. Je to nejjednodušší a nejúčinnější volba pro vývojáře v systému Windows k vytvoření kontejnerů Docker pro Linux nebo Windows.

### <a name="visual-studio-for-mac-mac-development-machine"></a>Visual Studio pro Mac (počítač pro vývoj Mac)

Při vývoji aplikací založených na Docker můžete použít [Visual Studio pro Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) . Visual Studio pro Mac nabízí bohatší integrované vývojové prostředí (IDE) ve srovnání s Visual Studio Code for Mac.

## <a name="language-and-framework-choices"></a>Volby jazyka a architektury

Můžete vyvíjet aplikace Docker pomocí nástrojů Microsoftu pro většinu moderních jazyků. Následuje úvodní seznam, ale nejste omezeni na něj:

- .NET Core a ASP.NET Core
- Node.js
- Přejít
- Java
- Ruby
- Python

V podstatě můžete použít moderní jazyk podporovaný Docker v systému Linux nebo Windows.

>[!div class="step-by-step"]
>[Předchozí](deploy-azure-kubernetes-service.md) 
> [Další](docker-apps-inner-loop-workflow.md)
