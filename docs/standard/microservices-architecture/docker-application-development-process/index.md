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
# <a name="development-process-for-docker-based-applications"></a><span data-ttu-id="2d371-104">Proces vývoje aplikace založené na Docker</span><span class="sxs-lookup"><span data-stu-id="2d371-104">Development Process for Docker-Based Applications</span></span>

<span data-ttu-id="2d371-105">*Vývoj kontejnerizované aplikací .NET způsob, jak se vám líbí, buď IDE zaměřuje pomocí sady Visual Studio a Visual Studio tools pro Docker nebo rozhraní příkazového řádku/editoru zaměřuje pomocí příkazového řádku Dockeru a Visual Studio Code.*</span><span class="sxs-lookup"><span data-stu-id="2d371-105">*Develop containerized .NET applications the way you like, either IDE focused with Visual Studio and Visual Studio tools for Docker or CLI/Editor focused with Docker CLI and Visual Studio Code.*</span></span>

## <a name="development-environment-for-docker-apps"></a><span data-ttu-id="2d371-106">Vývojové prostředí pro Docker aplikace</span><span class="sxs-lookup"><span data-stu-id="2d371-106">Development environment for Docker apps</span></span>

### <a name="development-tool-choices-ide-or-editor"></a><span data-ttu-id="2d371-107">Volba nástroje vývoj: IDE nebo editoru</span><span class="sxs-lookup"><span data-stu-id="2d371-107">Development tool choices: IDE or editor</span></span>

<span data-ttu-id="2d371-108">Jestli chcete úplné a výkonné IDE nebo jednoduchý a agilní editoru, společnost Microsoft nemá nástroje, které můžete použít pro vývoj aplikací Docker.</span><span class="sxs-lookup"><span data-stu-id="2d371-108">Whether you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has tools that you can use for developing Docker applications.</span></span>

<span data-ttu-id="2d371-109">**Visual Studio (pro Windows)**.</span><span class="sxs-lookup"><span data-stu-id="2d371-109">**Visual Studio (for Windows)**.</span></span> <span data-ttu-id="2d371-110">K vývoji aplikací na základě Docker, použijte Visual Studio 2017 nebo novější verze, které je součástí nástrojů pro Docker již předdefinované.</span><span class="sxs-lookup"><span data-stu-id="2d371-110">To develop Docker-based applications, use Visual Studio 2017 or later versions that comes with tools for Docker already built-in.</span></span> <span data-ttu-id="2d371-111">Nástroje pro Docker umožňují vývoj, spuštění a ověření aplikace přímo v cílovém prostředí Docker.</span><span class="sxs-lookup"><span data-stu-id="2d371-111">The tools for Docker let you develop, run, and validate your applications directly in the target Docker environment.</span></span> <span data-ttu-id="2d371-112">Můžete stisknutím klávesy F5 spusťte a ladění aplikace (kontejner jednoho nebo několika kontejnerů) přímo do hostitelů Docker nebo stiskněte klávesu CTRL + F5 a upravte a aktualizujte aplikaci bez nutnosti znovu sestavit kontejneru.</span><span class="sxs-lookup"><span data-stu-id="2d371-112">You can press F5 to run and debug your application (single container or multiple containers) directly into a Docker host, or press CTRL+F5 to edit and refresh your application without having to rebuild the container.</span></span> <span data-ttu-id="2d371-113">Toto je nejúčinnějších vývoj volbou pro aplikace založené na Docker.</span><span class="sxs-lookup"><span data-stu-id="2d371-113">This is the most powerful development choice for Docker-based apps.</span></span>

<span data-ttu-id="2d371-114">**Visual Studio pro Mac**.</span><span class="sxs-lookup"><span data-stu-id="2d371-114">**Visual Studio for Mac**.</span></span> <span data-ttu-id="2d371-115">Je IDE, vývoje Xamarin Studio, který běží v systému macOS a podporuje vývoj aplikací na základě Docker.</span><span class="sxs-lookup"><span data-stu-id="2d371-115">It is an IDE, evolution of Xamarin Studio, that runs on macOS and supports Docker-based application development.</span></span> <span data-ttu-id="2d371-116">To by měl být upřednostňovanou volbou pro vývojáře, kteří pracují na počítačích Mac a kteří používat Výkonné IDE.</span><span class="sxs-lookup"><span data-stu-id="2d371-116">This should be the preferred choice for developers working in Mac machines who also want to use a powerful IDE.</span></span>

<span data-ttu-id="2d371-117">**Visual Studio Code a Docker CLI**.</span><span class="sxs-lookup"><span data-stu-id="2d371-117">**Visual Studio Code and Docker CLI**.</span></span> <span data-ttu-id="2d371-118">Pokud dáváte přednost jednoduchý a napříč platformami editor, který podporuje žádný jazyk vývoj, můžete použít Microsoft Visual Studio Code (kód VS) a rozhraní příkazového řádku Dockeru.</span><span class="sxs-lookup"><span data-stu-id="2d371-118">If you prefer a lightweight and cross-platform editor that supports any development language, you can use Microsoft Visual Studio Code (VS Code) and the Docker CLI.</span></span> <span data-ttu-id="2d371-119">Toto je vývoj pro různé platformy přístup pro Mac, Linux a Windows.</span><span class="sxs-lookup"><span data-stu-id="2d371-119">This is a cross-platform development approach for Mac, Linux, and Windows.</span></span>

<span data-ttu-id="2d371-120">Nainstalováním [Docker Community Edition (CE)](https://www.docker.com/community-edition) nástroje, můžete použít jeden příkazového řádku Dockeru pro vývoj aplikací pro Windows a Linux.</span><span class="sxs-lookup"><span data-stu-id="2d371-120">By installing [Docker Community Edition (CE)](https://www.docker.com/community-edition) tools, you can use a single Docker CLI to build apps for both Windows and Linux.</span></span> <span data-ttu-id="2d371-121">Kromě toho Visual Studio Code podporuje rozšíření pro Docker například IntelliSense pro Dockerfiles a zástupce úlohy ke spuštění příkazů Docker v editoru.</span><span class="sxs-lookup"><span data-stu-id="2d371-121">Additionally, Visual Studio Code supports extensions for Docker such as IntelliSense for Dockerfiles and shortcut tasks to run Docker commands from the editor.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="2d371-122">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="2d371-122">Additional resources</span></span>

-   <span data-ttu-id="2d371-123">**Visual Studio Tools pro Docker**
    [*https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker*](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)</span><span class="sxs-lookup"><span data-stu-id="2d371-123">**Visual Studio Tools for Docker**
[*https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker*](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)</span></span>

-   <span data-ttu-id="2d371-124">**Visual Studio Code**.</span><span class="sxs-lookup"><span data-stu-id="2d371-124">**Visual Studio Code**.</span></span> <span data-ttu-id="2d371-125">Oficiální web.</span><span class="sxs-lookup"><span data-stu-id="2d371-125">Official site.</span></span>
    [<span data-ttu-id="2d371-126">*https://Code.VisualStudio.com/download*</span><span class="sxs-lookup"><span data-stu-id="2d371-126">*https://code.visualstudio.com/download*</span></span>](https://code.visualstudio.com/download)

-   <span data-ttu-id="2d371-127">**Docker Community Edition (CE) pro Mac a Windows**
    [*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)</span><span class="sxs-lookup"><span data-stu-id="2d371-127">**Docker Community Edition (CE) for Mac and Windows**
[*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)</span></span>

## <a name="net-languages-and-frameworks-for-docker-containers"></a><span data-ttu-id="2d371-128">Rozhraní .NET jazyků a rozhraní pro Docker kontejnery</span><span class="sxs-lookup"><span data-stu-id="2d371-128">.NET languages and frameworks for Docker containers</span></span>

<span data-ttu-id="2d371-129">Jak je uvedeno v předchozích částech tohoto průvodce, můžete rozhraní .NET Framework, .NET Core a open-source Mono projekt při vývoj Docker kontejnerizované aplikací .NET.</span><span class="sxs-lookup"><span data-stu-id="2d371-129">As mentioned in earlier sections of this guide, you can use .NET Framework, .NET Core, or the open-source Mono project when developing Docker containerized .NET applications.</span></span> <span data-ttu-id="2d371-130">Můžete vyvíjet v jazyce C\#, F\#, nebo Visual Basic, pokud je cílem Linux nebo Windows kontejnerů, v závislosti na tom, které rozhraní .NET framework se používá.</span><span class="sxs-lookup"><span data-stu-id="2d371-130">You can develop in C\#, F\#, or Visual Basic when targeting Linux or Windows Containers, depending on which .NET framework is in use.</span></span> <span data-ttu-id="2d371-131">Pro další jazyky about.NET podrobnosti naleznete v příspěvku blogu [strategie jazyk rozhraní .NET](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/).</span><span class="sxs-lookup"><span data-stu-id="2d371-131">For more details about.NET languages, see the blog post [The .NET Language Strategy](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/).</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="2d371-132">[Předchozí] (.. / architect-microservice-container-applications/using-azure-service-fabric.md) [Další] (docker-app-development-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="2d371-132">[Previous] (../architect-microservice-container-applications/using-azure-service-fabric.md) [Next] (docker-app-development-workflow.md)</span></span>
