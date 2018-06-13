---
title: Aplikace založené na procesu vývoje pro Docker
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Aplikace založené na procesu vývoje pro Docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 881817f4f1007edad85eefb9002d56764cbf2a02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574781"
---
# <a name="development-process-for-docker-based-applications"></a><span data-ttu-id="685bd-103">Proces vývoje aplikace založené na Docker</span><span class="sxs-lookup"><span data-stu-id="685bd-103">Development Process for Docker-Based Applications</span></span>

<span data-ttu-id="685bd-104">*Vývoj kontejnerizované aplikací .NET způsob, jak se vám líbí, buď IDE zaměřuje pomocí sady Visual Studio a Visual Studio tools pro Docker nebo rozhraní příkazového řádku/editoru zaměřuje pomocí příkazového řádku Dockeru a Visual Studio Code.*</span><span class="sxs-lookup"><span data-stu-id="685bd-104">*Develop containerized .NET applications the way you like, either IDE focused with Visual Studio and Visual Studio tools for Docker or CLI/Editor focused with Docker CLI and Visual Studio Code.*</span></span>

## <a name="development-environment-for-docker-apps"></a><span data-ttu-id="685bd-105">Vývojové prostředí pro Docker aplikace</span><span class="sxs-lookup"><span data-stu-id="685bd-105">Development environment for Docker apps</span></span>

### <a name="development-tool-choices-ide-or-editor"></a><span data-ttu-id="685bd-106">Volba nástroje vývoj: IDE nebo editoru</span><span class="sxs-lookup"><span data-stu-id="685bd-106">Development tool choices: IDE or editor</span></span>

<span data-ttu-id="685bd-107">Jestli chcete úplné a výkonné IDE nebo jednoduchý a agilní editoru, společnost Microsoft nemá nástroje, které můžete použít pro vývoj aplikací Docker.</span><span class="sxs-lookup"><span data-stu-id="685bd-107">Whether you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has tools that you can use for developing Docker applications.</span></span>

<span data-ttu-id="685bd-108">**Visual Studio (pro Windows)**.</span><span class="sxs-lookup"><span data-stu-id="685bd-108">**Visual Studio (for Windows)**.</span></span> <span data-ttu-id="685bd-109">K vývoji aplikací na základě Docker, použijte Visual Studio 2017 nebo novější verze, které je součástí nástrojů pro Docker již předdefinované.</span><span class="sxs-lookup"><span data-stu-id="685bd-109">To develop Docker-based applications, use Visual Studio 2017 or later versions that comes with tools for Docker already built-in.</span></span> <span data-ttu-id="685bd-110">Nástroje pro Docker umožňují vývoj, spuštění a ověření aplikace přímo v cílovém prostředí Docker.</span><span class="sxs-lookup"><span data-stu-id="685bd-110">The tools for Docker let you develop, run, and validate your applications directly in the target Docker environment.</span></span> <span data-ttu-id="685bd-111">Můžete stisknutím klávesy F5 spusťte a ladění aplikace (kontejner jednoho nebo několika kontejnerů) přímo do hostitelů Docker nebo stiskněte klávesu CTRL + F5 a upravte a aktualizujte aplikaci bez nutnosti znovu sestavit kontejneru.</span><span class="sxs-lookup"><span data-stu-id="685bd-111">You can press F5 to run and debug your application (single container or multiple containers) directly into a Docker host, or press CTRL+F5 to edit and refresh your application without having to rebuild the container.</span></span> <span data-ttu-id="685bd-112">Toto je nejúčinnějších vývoj volbou pro aplikace založené na Docker.</span><span class="sxs-lookup"><span data-stu-id="685bd-112">This is the most powerful development choice for Docker-based apps.</span></span>

<span data-ttu-id="685bd-113">**Visual Studio pro Mac**.</span><span class="sxs-lookup"><span data-stu-id="685bd-113">**Visual Studio for Mac**.</span></span> <span data-ttu-id="685bd-114">Je IDE, vývoje Xamarin Studio, který běží v systému macOS a podporuje vývoj aplikací na základě Docker.</span><span class="sxs-lookup"><span data-stu-id="685bd-114">It is an IDE, evolution of Xamarin Studio, that runs on macOS and supports Docker-based application development.</span></span> <span data-ttu-id="685bd-115">To by měl být upřednostňovanou volbou pro vývojáře, kteří pracují na počítačích Mac a kteří používat Výkonné IDE.</span><span class="sxs-lookup"><span data-stu-id="685bd-115">This should be the preferred choice for developers working in Mac machines who also want to use a powerful IDE.</span></span>

<span data-ttu-id="685bd-116">**Visual Studio Code a Docker CLI**.</span><span class="sxs-lookup"><span data-stu-id="685bd-116">**Visual Studio Code and Docker CLI**.</span></span> <span data-ttu-id="685bd-117">Pokud dáváte přednost jednoduchý a napříč platformami editor, který podporuje žádný jazyk vývoj, můžete použít Microsoft Visual Studio Code (kód VS) a rozhraní příkazového řádku Dockeru.</span><span class="sxs-lookup"><span data-stu-id="685bd-117">If you prefer a lightweight and cross-platform editor that supports any development language, you can use Microsoft Visual Studio Code (VS Code) and the Docker CLI.</span></span> <span data-ttu-id="685bd-118">Toto je vývoj pro různé platformy přístup pro Mac, Linux a Windows.</span><span class="sxs-lookup"><span data-stu-id="685bd-118">This is a cross-platform development approach for Mac, Linux, and Windows.</span></span>

<span data-ttu-id="685bd-119">Nainstalováním [Docker Community Edition (CE)](https://www.docker.com/community-edition) nástroje, můžete použít jeden příkazového řádku Dockeru pro vývoj aplikací pro Windows a Linux.</span><span class="sxs-lookup"><span data-stu-id="685bd-119">By installing [Docker Community Edition (CE)](https://www.docker.com/community-edition) tools, you can use a single Docker CLI to build apps for both Windows and Linux.</span></span> <span data-ttu-id="685bd-120">Kromě toho Visual Studio Code podporuje rozšíření pro Docker například IntelliSense pro Dockerfiles a zástupce úlohy ke spuštění příkazů Docker v editoru.</span><span class="sxs-lookup"><span data-stu-id="685bd-120">Additionally, Visual Studio Code supports extensions for Docker such as IntelliSense for Dockerfiles and shortcut tasks to run Docker commands from the editor.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="685bd-121">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="685bd-121">Additional resources</span></span>

-   <span data-ttu-id="685bd-122">**Visual Studio Tools pro Docker**
    [*https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker*](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)</span><span class="sxs-lookup"><span data-stu-id="685bd-122">**Visual Studio Tools for Docker**
[*https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker*](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)</span></span>

-   <span data-ttu-id="685bd-123">**Visual Studio Code**.</span><span class="sxs-lookup"><span data-stu-id="685bd-123">**Visual Studio Code**.</span></span> <span data-ttu-id="685bd-124">Oficiální web.</span><span class="sxs-lookup"><span data-stu-id="685bd-124">Official site.</span></span>
    [*https://code.visualstudio.com/download*](https://code.visualstudio.com/download)

-   <span data-ttu-id="685bd-125">**Docker Community Edition (CE) pro Mac a Windows**
    [*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)</span><span class="sxs-lookup"><span data-stu-id="685bd-125">**Docker Community Edition (CE) for Mac and Windows**
[*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)</span></span>

## <a name="net-languages-and-frameworks-for-docker-containers"></a><span data-ttu-id="685bd-126">Rozhraní .NET jazyků a rozhraní pro Docker kontejnery</span><span class="sxs-lookup"><span data-stu-id="685bd-126">.NET languages and frameworks for Docker containers</span></span>

<span data-ttu-id="685bd-127">Jak je uvedeno v předchozích částech tohoto průvodce, můžete rozhraní .NET Framework, .NET Core a open-source Mono projekt při vývoj Docker kontejnerizované aplikací .NET.</span><span class="sxs-lookup"><span data-stu-id="685bd-127">As mentioned in earlier sections of this guide, you can use .NET Framework, .NET Core, or the open-source Mono project when developing Docker containerized .NET applications.</span></span> <span data-ttu-id="685bd-128">Můžete vyvíjet v jazyce C\#, F\#, nebo Visual Basic, pokud je cílem Linux nebo Windows kontejnerů, v závislosti na tom, které rozhraní .NET framework se používá.</span><span class="sxs-lookup"><span data-stu-id="685bd-128">You can develop in C\#, F\#, or Visual Basic when targeting Linux or Windows Containers, depending on which .NET framework is in use.</span></span> <span data-ttu-id="685bd-129">Pro další jazyky about.NET podrobnosti naleznete v příspěvku blogu [strategie jazyk rozhraní .NET](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/).</span><span class="sxs-lookup"><span data-stu-id="685bd-129">For more details about.NET languages, see the blog post [The .NET Language Strategy](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/).</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="685bd-130">[Předchozí] (.. / architect-microservice-container-applications/using-azure-service-fabric.md) [Další] (docker-app-development-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="685bd-130">[Previous] (../architect-microservice-container-applications/using-azure-service-fabric.md) [Next] (docker-app-development-workflow.md)</span></span>
