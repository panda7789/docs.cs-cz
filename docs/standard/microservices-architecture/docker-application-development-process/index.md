---
title: "Aplikace založené na procesu vývoje pro Docker"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Aplikace založené na procesu vývoje pro Docker"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 97dfa3261c8ddc7a869b0991673b7a8d298972dd
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="development-process-for-docker-based-applications"></a>Proces vývoje aplikace založené na Docker

*Vývoj kontejnerizované aplikací .NET způsob, jak se vám líbí, buď IDE zaměřuje pomocí sady Visual Studio a Visual Studio tools pro Docker nebo rozhraní příkazového řádku/editoru zaměřuje pomocí příkazového řádku Dockeru a Visual Studio Code.*

## <a name="development-environment-for-docker-apps"></a>Vývojové prostředí pro Docker aplikace

### <a name="development-tool-choices-ide-or-editor"></a>Volba nástroje vývoj: IDE nebo editoru

Jestli chcete úplné a výkonné IDE nebo jednoduchý a agilní editoru, společnost Microsoft nemá nástroje, které můžete použít pro vývoj aplikací Docker.

**Visual Studio (pro Windows)**. K vývoji aplikací na základě Docker, použijte Visual Studio 2017 nebo novější verze, které je součástí nástrojů pro Docker již předdefinované. Nástroje pro Docker umožňují vývoj, spuštění a ověření aplikace přímo v cílovém prostředí Docker. Můžete stisknutím klávesy F5 spusťte a ladění aplikace (kontejner jednoho nebo několika kontejnerů) přímo do hostitelů Docker nebo stiskněte klávesu CTRL + F5 a upravte a aktualizujte aplikaci bez nutnosti znovu sestavit kontejneru. Toto je nejúčinnějších vývoj volbou pro aplikace založené na Docker.

**Visual Studio pro Mac**. Je IDE, vývoje Xamarin Studio, který běží v systému macOS a podporuje vývoj aplikací na základě Docker. To by měl být upřednostňovanou volbou pro vývojáře, kteří pracují na počítačích Mac a kteří používat Výkonné IDE.

**Visual Studio Code a Docker CLI**. Pokud dáváte přednost jednoduchý a napříč platformami editor, který podporuje žádný jazyk vývoj, můžete použít Microsoft Visual Studio Code (kód VS) a rozhraní příkazového řádku Dockeru. Toto je vývoj pro různé platformy přístup pro Mac, Linux a Windows.

Nainstalováním [Docker Community Edition (CE)](https://www.docker.com/community-edition) nástroje, můžete použít jeden příkazového řádku Dockeru pro vývoj aplikací pro Windows a Linux. Kromě toho Visual Studio Code podporuje rozšíření pro Docker například IntelliSense pro Dockerfiles a zástupce úlohy ke spuštění příkazů Docker v editoru.

### <a name="additional-resources"></a>Další zdroje

-   **Visual Studio Tools pro Docker**
    [*https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker*](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)

-   **Visual Studio Code**. Oficiální web.
    [*https://Code.VisualStudio.com/download*](https://code.visualstudio.com/download)

-   **Docker Community Edition (CE) pro Mac a Windows**
    [*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)

## <a name="net-languages-and-frameworks-for-docker-containers"></a>Rozhraní .NET jazyků a rozhraní pro Docker kontejnery

Jak je uvedeno v předchozích částech tohoto průvodce, můžete rozhraní .NET Framework, .NET Core a open-source Mono projekt při vývoj Docker kontejnerizované aplikací .NET. Můžete vyvíjet v jazyce C\#, F\#, nebo Visual Basic, pokud je cílem Linux nebo Windows kontejnerů, v závislosti na tom, které rozhraní .NET framework se používá. Pro další jazyky about.NET podrobnosti naleznete v příspěvku blogu [strategie jazyk rozhraní .NET](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/).


>[!div class="step-by-step"]
[Předchozí] (.. / architect-microservice-container-applications/using-azure-service-fabric.md) [Další] (docker-app-development-workflow.md)
