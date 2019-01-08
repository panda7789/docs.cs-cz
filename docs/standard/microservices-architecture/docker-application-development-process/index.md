---
title: Aplikace založené na proces vývoje pro Docker
description: Získáte základní přehled možností pro vývoj aplikací založených na Dockeru. Díky volbě Visual Studio pro Windows, Visual Studio pro Mac nebo Visual Studio Code pro podporu více platforem (Windows, Mac a Linux).
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/27/2018
ms.openlocfilehash: eb87f9a214dbffe71dae1e1739f2563c08fac280
ms.sourcegitcommit: d09c77414e9e4fc72c79b04deee7a756a120674e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2019
ms.locfileid: "54084924"
---
# <a name="development-process-for-docker-based-applications"></a>Proces vývoje pro aplikace založené na Dockeru

*Vývoj kontejnerizovaných aplikací .NET způsobem, který rádi používáte, IDE, zaměřuje sadou Visual Studio a Visual Studio tools for Docker nebo rozhraní příkazového řádku/Editor, zaměřuje pomocí rozhraní příkazového řádku Dockeru a Visual Studio Code.*

## <a name="development-environment-for-docker-apps"></a>Vývojové prostředí pro aplikace Dockeru

### <a name="development-tool-choices-ide-or-editor"></a>Volba nástroje pro vývoj: Prostředím IDE nebo editorem

Ať už dáváte přednost úplné a výkonné IDE nebo editoru jednoduchý a flexibilní, společnost Microsoft má nástroje, které můžete použít pro vývoj aplikací Dockeru.

**Visual Studio (pro Windows).** Při vývoji aplikací dockeru pomocí sady Visual Studio, doporučujeme použít Visual Studio 2017 verze 15.7 nebo novější, která se dodává s nástroji pro Docker již integrované. Nástroje pro Docker umožňují vyvíjet, spouštět a ověřovat aplikace přímo v cílovém prostředí Docker. Můžete stisknutím klávesy F5 ke spuštění a ladění aplikace (jedním kontejnerem nebo více kontejnerů) přímo do hostitele Docker nebo stisknutím kláves CTRL + F5, upravit a aktualizovat aplikace bez nutnosti znovu sestavovat kontejner. Toto je nejvýkonnější vývoj volbou pro aplikace založené na Dockeru.

**Visual Studio pro Mac.** Je integrované vývojové prostředí, vývoj Xamarin Studio, spuštěné v systému macOS a podporuje Docker od poloviny 2017. To by měl být upřednostňovanou volbu pro vývojáře pracující na počítačích Mac, které také chtějí využívat výkonné integrované vývojové prostředí.

**Visual Studio Code a Dockeru CLI**. Pokud dáváte přednost jednoduchý a multiplatformní editor, který podporuje jakýkoli jazyk pro vývoj, můžete použít Microsoft Visual Studio Code (VS Code) a rozhraní příkazového řádku Dockeru. Toto je postup vývoj multiplatformních aplikací pro Mac, Linux a Windows. Kromě toho Visual Studio Code podporuje rozšíření pro Docker, jako je například technologie IntelliSense pro soubory Dockerfile a místní úlohy spouštět příkazy Dockeru z editoru.

Nainstalováním [Docker Community Edition (CE)](https://www.docker.com/community-edition) nástroje, jednotné rozhraní příkazového řádku Dockeru můžete použít k vytváření aplikací pro Windows a Linux.

### <a name="additional-resources"></a>Další zdroje

- **Visual Studio**. Oficiální web. \
  [*https://visualstudio.microsoft.com/vs/*](https://visualstudio.microsoft.com/vs/)

- **Visual Studio Code**. Oficiální web. \
  [*https://code.visualstudio.com/download*](https://code.visualstudio.com/download)

- **Docker Community Edition (CE) pro Mac a Windows** \
  [*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)

## <a name="net-languages-and-frameworks-for-docker-containers"></a>Jazyky .NET a rozhraní pro kontejnery Dockeru

Jak je uvedeno v předchozí části této příručky, můžete rozhraní .NET Framework, .NET Core a open source projektu Mono při vývoji Docker kontejnerizovaných aplikací .NET. Můžete vyvíjet v jazyce C\#, F\#, nebo při cílení na Linuxu nebo Windows, kontejnery, v závislosti na tom, které rozhraní .NET framework se používá jazyka Visual Basic. Další podrobnosti o about.NET jazyky, naleznete v příspěvku blogu [The jazyková strategie .NET](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/).

>[!div class="step-by-step"]
>[Předchozí](../architect-microservice-container-applications/using-azure-service-fabric.md)
>[další](docker-app-development-workflow.md)