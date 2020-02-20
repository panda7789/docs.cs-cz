---
title: Proces vývoje pro aplikace založené na Docker
description: Získejte podrobný přehled možností vývoje aplikací využívajících Docker. Použití sady Visual Studio pro Windows, Visual Studio pro Mac nebo Visual Studio Code pro podporu multiplatformní (Windows, macOS a Linux).
ms.date: 01/30/2020
ms.openlocfilehash: 799aa6fc742a8fb763ec5a7ae3cf3f70f89bed6d
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77502722"
---
# <a name="development-process-for-docker-based-applications"></a>Proces vývoje pro aplikace založené na Docker

*Vývoj aplikací .NET pomocí integrovaného vývojového prostředí (IDE), které se zaměřuje na sady Visual Studio a Visual Studio Tools pro Docker nebo CLI/editor, se zaměřuje na rozhraní Docker CLI a Visual Studio Code.*

## <a name="development-environment-for-docker-apps"></a>Vývojové prostředí pro aplikace Dockeru

### <a name="development-tool-choices-ide-or-editor"></a>Možnosti vývojového nástroje: IDE nebo Editor

Bez ohledu na to, jestli dáváte přednost celému a výkonnému integrovanému vývojovém prostředí (IDE) nebo odlehčenému a agilnímu editoru, Microsoft nabízí nástroje, které můžete použít pro vývoj aplikací Dock

**Visual Studio (pro Windows).** Vývoj aplikací .NET Core 3,1 na bázi Docker v systému Visual Studio vyžaduje Visual Studio 2019 verze 16,4 nebo novější. Visual Studio 2019 obsahuje nástroje pro Docker, které jsou už integrované. Nástroje pro Docker umožňují vyvíjet, spouštět a ověřovat vaše aplikace přímo v cílovém prostředí Docker. Stisknutím klávesy F5 můžete spustit a ladit aplikaci (jeden kontejner nebo více kontejnerů) přímo do hostitele Docker nebo stisknutím kláves CTRL + F5 upravit a aktualizovat aplikaci, aniž by bylo nutné znovu sestavit kontejner. Toto je nejvýkonnější volba pro vývoj aplikací využívajících Docker.

**Visual Studio pro Mac.** Jedná se o integrované vývojové prostředí (IDE), vývoj Xamarin Studio spuštěný v macOS. Pro vývoj pro .NET Core 3,1 vyžaduje verze 8,4 nebo novější. To by mělo být Upřednostňovaná volba pro vývojáře pracující v macOSch počítačích, kteří také chtějí používat výkonné integrované vývojové prostředí (IDE).

**Visual Studio Code a Docker CLI**. Pokud dáváte přednost zjednodušenému editoru pro různé platformy, který podporuje libovolný vývojový jazyk, můžete použít Visual Studio Code a Docker CLI. Toto je přístup pro vývoj pro různé platformy pro macOS, Linux a Windows. Kromě toho Visual Studio Code podporuje rozšíření pro Docker, jako je například IntelliSense pro úlohy fázemi a zástupce pro spouštění příkazů Docker z editoru.

Když nainstalujete [Docker Desktop Community Edition (CE)](https://hub.docker.com/search/?type=edition&offering=community), můžete k sestavování aplikací pro Windows i Linux použít jedno rozhraní Docker CLI.

### <a name="additional-resources"></a>Další zdroje

- Sadu **Visual Studio**. Oficiální lokalita. \
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
