---
title: Aplikace založené na proces vývoje pro Docker
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Aplikace založené na proces vývoje pro Docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 7736c1fe4cb1a2a4553ba36cecceab37e2fe90c4
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53144465"
---
# <a name="development-process-for-docker-based-applications"></a><span data-ttu-id="73a7b-103">Proces vývoje pro aplikace založené na Dockeru</span><span class="sxs-lookup"><span data-stu-id="73a7b-103">Development Process for Docker-Based Applications</span></span>

<span data-ttu-id="73a7b-104">*Vývoj kontejnerizovaných aplikací .NET způsobem, který rádi používáte, IDE, zaměřuje sadou Visual Studio a Visual Studio tools for Docker nebo rozhraní příkazového řádku/Editor, zaměřuje pomocí rozhraní příkazového řádku Dockeru a Visual Studio Code.*</span><span class="sxs-lookup"><span data-stu-id="73a7b-104">*Develop containerized .NET applications the way you like, either IDE focused with Visual Studio and Visual Studio tools for Docker or CLI/Editor focused with Docker CLI and Visual Studio Code.*</span></span>

## <a name="development-environment-for-docker-apps"></a><span data-ttu-id="73a7b-105">Vývojové prostředí pro aplikace Dockeru</span><span class="sxs-lookup"><span data-stu-id="73a7b-105">Development environment for Docker apps</span></span>

### <a name="development-tool-choices-ide-or-editor"></a><span data-ttu-id="73a7b-106">Volba nástroje pro vývoj: Prostředím IDE nebo editorem</span><span class="sxs-lookup"><span data-stu-id="73a7b-106">Development tool choices: IDE or editor</span></span>

<span data-ttu-id="73a7b-107">Ať už dáváte přednost úplné a výkonné IDE nebo editoru jednoduchý a flexibilní, společnost Microsoft má nástroje, které můžete použít pro vývoj aplikací Dockeru.</span><span class="sxs-lookup"><span data-stu-id="73a7b-107">Whether you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has tools that you can use for developing Docker applications.</span></span>

<span data-ttu-id="73a7b-108">**Visual Studio (pro Windows)**.</span><span class="sxs-lookup"><span data-stu-id="73a7b-108">**Visual Studio (for Windows)**.</span></span> <span data-ttu-id="73a7b-109">K vývoji aplikací založených na Dockeru pomocí sady Visual Studio 2017 nebo novější verze, které je součástí nástrojů pro Docker již integrované.</span><span class="sxs-lookup"><span data-stu-id="73a7b-109">To develop Docker-based applications, use Visual Studio 2017 or later versions that comes with tools for Docker already built-in.</span></span> <span data-ttu-id="73a7b-110">Nástroje pro Docker umožňují vyvíjet, spouštět a ověřovat aplikace přímo v cílovém prostředí Docker.</span><span class="sxs-lookup"><span data-stu-id="73a7b-110">The tools for Docker let you develop, run, and validate your applications directly in the target Docker environment.</span></span> <span data-ttu-id="73a7b-111">Můžete stisknutím klávesy F5 ke spuštění a ladění aplikace (jedním kontejnerem nebo více kontejnerů) přímo do hostitele Docker nebo stisknutím kláves CTRL + F5, upravit a aktualizovat aplikace bez nutnosti znovu sestavovat kontejner.</span><span class="sxs-lookup"><span data-stu-id="73a7b-111">You can press F5 to run and debug your application (single container or multiple containers) directly into a Docker host, or press CTRL+F5 to edit and refresh your application without having to rebuild the container.</span></span> <span data-ttu-id="73a7b-112">Toto je nejvýkonnější vývoj volbou pro aplikace založené na Dockeru.</span><span class="sxs-lookup"><span data-stu-id="73a7b-112">This is the most powerful development choice for Docker-based apps.</span></span>

<span data-ttu-id="73a7b-113">**Visual Studio for Mac**.</span><span class="sxs-lookup"><span data-stu-id="73a7b-113">**Visual Studio for Mac**.</span></span> <span data-ttu-id="73a7b-114">Je integrované vývojové prostředí, vývoj Xamarin Studio, který běží v systému macOS a podporuje vývoj aplikací založených na Dockeru.</span><span class="sxs-lookup"><span data-stu-id="73a7b-114">It is an IDE, evolution of Xamarin Studio, that runs on macOS and supports Docker-based application development.</span></span> <span data-ttu-id="73a7b-115">To by měl být upřednostňovanou volbu pro vývojáře pracující na počítačích Mac, které také chtějí využívat výkonné integrované vývojové prostředí.</span><span class="sxs-lookup"><span data-stu-id="73a7b-115">This should be the preferred choice for developers working in Mac machines who also want to use a powerful IDE.</span></span>

<span data-ttu-id="73a7b-116">**Visual Studio Code a Dockeru CLI**.</span><span class="sxs-lookup"><span data-stu-id="73a7b-116">**Visual Studio Code and Docker CLI**.</span></span> <span data-ttu-id="73a7b-117">Pokud dáváte přednost jednoduchý a multiplatformní editor, který podporuje jakýkoli jazyk pro vývoj, můžete použít Microsoft Visual Studio Code (VS Code) a rozhraní příkazového řádku Dockeru.</span><span class="sxs-lookup"><span data-stu-id="73a7b-117">If you prefer a lightweight and cross-platform editor that supports any development language, you can use Microsoft Visual Studio Code (VS Code) and the Docker CLI.</span></span> <span data-ttu-id="73a7b-118">Toto je postup vývoj multiplatformních aplikací pro Mac, Linux a Windows.</span><span class="sxs-lookup"><span data-stu-id="73a7b-118">This is a cross-platform development approach for Mac, Linux, and Windows.</span></span>

<span data-ttu-id="73a7b-119">Nainstalováním [Docker Community Edition (CE)](https://www.docker.com/community-edition) nástroje, jednotné rozhraní příkazového řádku Dockeru můžete použít k vytváření aplikací pro Windows a Linux.</span><span class="sxs-lookup"><span data-stu-id="73a7b-119">By installing [Docker Community Edition (CE)](https://www.docker.com/community-edition) tools, you can use a single Docker CLI to build apps for both Windows and Linux.</span></span> <span data-ttu-id="73a7b-120">Kromě toho Visual Studio Code podporuje rozšíření pro Docker, jako je například technologie IntelliSense pro soubory Dockerfile a místní úlohy spouštět příkazy Dockeru z editoru.</span><span class="sxs-lookup"><span data-stu-id="73a7b-120">Additionally, Visual Studio Code supports extensions for Docker such as IntelliSense for Dockerfiles and shortcut tasks to run Docker commands from the editor.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="73a7b-121">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="73a7b-121">Additional resources</span></span>

-   <span data-ttu-id="73a7b-122">**Visual Studio Tools for Docker**
    [*https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker*](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)</span><span class="sxs-lookup"><span data-stu-id="73a7b-122">**Visual Studio Tools for Docker**
[*https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker*](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)</span></span>

-   <span data-ttu-id="73a7b-123">**Visual Studio Code**.</span><span class="sxs-lookup"><span data-stu-id="73a7b-123">**Visual Studio Code**.</span></span> <span data-ttu-id="73a7b-124">Oficiální web.</span><span class="sxs-lookup"><span data-stu-id="73a7b-124">Official site.</span></span>
    [*https://code.visualstudio.com/download*](https://code.visualstudio.com/download)

-   <span data-ttu-id="73a7b-125">**Docker Community Edition (CE) pro Mac a Windows**
    [*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)</span><span class="sxs-lookup"><span data-stu-id="73a7b-125">**Docker Community Edition (CE) for Mac and Windows**
[*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)</span></span>

## <a name="net-languages-and-frameworks-for-docker-containers"></a><span data-ttu-id="73a7b-126">Jazyky .NET a rozhraní pro kontejnery Dockeru</span><span class="sxs-lookup"><span data-stu-id="73a7b-126">.NET languages and frameworks for Docker containers</span></span>

<span data-ttu-id="73a7b-127">Jak je uvedeno v předchozí části této příručky, můžete rozhraní .NET Framework, .NET Core a open source projektu Mono při vývoji Docker kontejnerizovaných aplikací .NET.</span><span class="sxs-lookup"><span data-stu-id="73a7b-127">As mentioned in earlier sections of this guide, you can use .NET Framework, .NET Core, or the open-source Mono project when developing Docker containerized .NET applications.</span></span> <span data-ttu-id="73a7b-128">Můžete vyvíjet v jazyce C\#, F\#, nebo při cílení na Linuxu nebo Windows, kontejnery, v závislosti na tom, které rozhraní .NET framework se používá jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="73a7b-128">You can develop in C\#, F\#, or Visual Basic when targeting Linux or Windows Containers, depending on which .NET framework is in use.</span></span> <span data-ttu-id="73a7b-129">Další podrobnosti o about.NET jazyky, naleznete v příspěvku blogu [The jazyková strategie .NET](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/).</span><span class="sxs-lookup"><span data-stu-id="73a7b-129">For more details about.NET languages, see the blog post [The .NET Language Strategy](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="73a7b-130">[Předchozí](../architect-microservice-container-applications/using-azure-service-fabric.md)
>[další](docker-app-development-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="73a7b-130">[Previous](../architect-microservice-container-applications/using-azure-service-fabric.md)
[Next](docker-app-development-workflow.md)</span></span>