---
title: Proces vývoje aplikací založených na Dockeru
description: Získejte přehled možností pro vývoj aplikací založených na Docker. Použití sady Visual Studio pro Windows, Visual Studio pro Mac nebo Visual Studio Code pro podporu multiplatformní (Windows, Mac a Linux).
ms.date: 09/27/2018
ms.openlocfilehash: 6299d67299948dce1081a211b350e657b2c1b951
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72770127"
---
# <a name="development-process-for-docker-based-applications"></a>Proces vývoje pro aplikace založené na Docker

*Sestavujte kontejnery aplikací .NET tak, jak chcete, ať už se jedná o integrované vývojové prostředí (IDE) se sadou Visual Studio a Visual Studio Tools pro Docker nebo rozhraní příkazového řádku Docker, a Visual Studio Code.*

## <a name="development-environment-for-docker-apps"></a>Vývojové prostředí pro aplikace Dockeru

### <a name="development-tool-choices-ide-or-editor"></a>Možnosti vývojového nástroje: IDE nebo Editor

Bez ohledu na to, jestli dáváte přednost celému a výkonnému integrovanému vývojovém prostředí (IDE) nebo odlehčenému a agilnímu editoru, Microsoft nabízí nástroje, které můžete použít pro vývoj aplikací Dock

**Visual Studio (pro Windows).** Při vývoji aplikací využívajících Docker se sadou Visual Studio se doporučuje použít Visual Studio 2017 verze 15,7 nebo novější, která je dodávána s nástroji pro Docker, který je už integrovaný. Nástroje pro Docker umožňují vyvíjet, spouštět a ověřovat vaše aplikace přímo v cílovém prostředí Docker. Stisknutím klávesy F5 můžete spustit a ladit aplikaci (jeden kontejner nebo více kontejnerů) přímo do hostitele Docker nebo stisknutím kláves CTRL + F5 upravit a aktualizovat aplikaci, aniž by bylo nutné znovu sestavit kontejner. Toto je nejvýkonnější volba pro vývoj aplikací využívajících Docker.

**Visual Studio for Mac.** Je to prostředí IDE, vývoj Xamarin Studio spuštěný v macOS a podporuje Docker od Mid-2017. To by mělo být Upřednostňovaná volba pro vývojáře pracující v počítačích Mac, kteří chtějí také používat výkonné integrované vývojové prostředí (IDE).

**Visual Studio Code a Docker CLI**. Pokud dáváte přednost zjednodušenému editoru pro různé platformy, který podporuje libovolný jazyk vývoje, můžete použít Microsoft Visual Studio kód (VS Code) a Docker CLI. Toto je přístup pro vývoj pro různé platformy pro Mac, Linux a Windows. Kromě toho Visual Studio Code podporuje rozšíření pro Docker, jako je například IntelliSense pro úlohy fázemi a zástupce pro spouštění příkazů Docker z editoru.

Když nainstalujete [Docker Desktop Community Edition (CE)](https://hub.docker.com/search/?type=edition&offering=community), můžete k sestavování aplikací pro Windows i Linux použít jedno rozhraní Docker CLI.

### <a name="additional-resources"></a>Další materiály a zdroje informací

- **Visual Studio**. Oficiální lokalita. \
  [https://visualstudio.microsoft.com/vs/](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

- **Visual Studio Code**. Oficiální lokalita. \
  <https://code.visualstudio.com/download>

- **Docker Desktop pro Windows Community Edition (CE)**  \
  [https://hub.docker.com/editions/community/docker-ce-desktop-windows](https://hub.docker.com/editions/community/docker-ce-desktop-windows)

- **Docker Desktop pro Mac Community Edition (CE)**  \
  [https://hub.docker.com/editions/community/docker-ce-desktop-mac](https://hub.docker.com/editions/community/docker-ce-desktop-mac)

## <a name="net-languages-and-frameworks-for-docker-containers"></a>Jazyky a rozhraní .NET pro kontejnery Docker

Jak je uvedeno v předchozích částech tohoto průvodce, můžete použít .NET Framework, .NET Core nebo open source projekt mono při vývoji aplikací .NET s podporou kontejneru. V závislosti na tom, které rozhraní .NET Framework se používá, můžete vyvíjet v prostředí C\#, F\#nebo Visual Basic. Další podrobnosti o about.NET jazycích najdete v blogovém příspěvku [o strategii jazyka .NET](https://devblogs.microsoft.com/dotnet/the-net-language-strategy/).

>[!div class="step-by-step"]
>[Předchozí](../architect-microservice-container-applications/scalable-available-multi-container-microservice-applications.md)
>[Další](docker-app-development-workflow.md)
