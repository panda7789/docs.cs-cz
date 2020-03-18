---
title: Vývojové prostředí pro aplikace Dockeru
description: Seznamte se s nejdůležitějšími možnostmi vývojových nástrojů, které podporují životní cyklus vývoje Dockeru.
ms.date: 02/15/2019
ms.openlocfilehash: 35236e75f47e830d0970ca9cfd074d9a69e6f85c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "71214300"
---
# <a name="development-environment-for-docker-apps"></a>Vývojové prostředí pro aplikace Dockeru

## <a name="development-tools-choices-ide-or-editor"></a>Volby vývojových nástrojů: IDE nebo editor

Bez ohledu na to, zda dáváte přednost úplnému a výkonnému rozhraní IDE nebo lehkému a agilnímu editoru, společnost Microsoft vás pokryje, pokud jde o vývoj aplikací Dockeru.

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a>Visual Studio Code a Docker CLI (nástroje pro různé platformy pro Mac, Linux a Windows)

Pokud dáváte přednost lehký editor pro více platforem podporující jakýkoli vývojový jazyk, můžete použít Visual Studio Code a Docker CLI. Tyto produkty poskytují jednoduché, ale robustní prostředí, což je důležité pro zjednodušení pracovního postupu pro vývojáře. Instalací "Docker for Mac" nebo "Docker for Windows" (vývojové prostředí) můžou vývojáři Dockeru používat jeden rozhraní CLI Dockeru k vytváření aplikací pro Windows i Linux (runtime prostředí). Visual Studio Code navíc podporuje rozšíření pro Docker s IntelliSense pro Dockerfiles a zkratkové úlohy pro spouštění příkazů Dockeru z editoru.

> [!NOTE]
> Chcete-li stáhnout kód <https://code.visualstudio.com/download>sady Visual Studio, přejděte na stránku .
>
> Pokud chcete stáhnout Docker pro <https://www.docker.com/products/docker>Mac a Windows, přejděte na .

### <a name="visual-studio-with-docker-tools-windows-development-machine"></a>Visual Studio s nástroji Docker Tools (vývojový počítač windows)

Doporučujeme používat Visual Studio 2017 (nebo novější) s integrovanými nástroji Dockeru. Pomocí sady Visual Studio můžete vyvíjet, spouštět a ověřovat aplikace přímo ve zvoleném prostředí Dockeru. Stisknutím klávesy F5 ladíte aplikaci (jeden kontejner nebo více kontejnerů) přímo v hostiteli Dockeru nebo stisknutím kombinace kláves Ctrl+F5 upravte a aktualizujte aplikaci bez nutnosti obnovovat kontejner. Je to nejjednodušší a nejvýkonnější volba pro vývojáře Windows vytvářet kontejnery Docker pro Linux nebo Windows.

### <a name="visual-studio-for-mac-mac-development-machine"></a>Visual Studio pro Mac (mac vývojový počítač)

[Visual Studio pro Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) můžete použít při vývoji aplikací založených na Dockeru. Visual Studio pro Mac nabízí bohatší IDE ve srovnání s Visual Studio Code for Mac.

## <a name="language-and-framework-choices"></a>Jazykové a rámcové volby

Aplikace Dockeru můžete vyvíjet pomocí nástrojů Microsoftu s většinou moderních jazyků. Následuje počáteční seznam, ale nejste omezeni na něj:

- .NET Core a ASP.NET Core
- Node.js
- Přejít
- Java
- Ruby
- Python

V podstatě můžete použít libovolný moderní jazyk podporovaný Dockerem v Linuxu nebo Windows.

>[!div class="step-by-step"]
>[Předchozí](deploy-azure-kubernetes-service.md)
>[další](docker-apps-inner-loop-workflow.md)
