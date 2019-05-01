---
title: Proces vývoje aplikací založených na Dockeru
description: Získáte základní přehled možností pro vývoj aplikací založených na Dockeru. Díky volbě Visual Studio pro Windows, Visual Studio pro Mac nebo Visual Studio Code pro podporu více platforem (Windows, Mac a Linux).
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/27/2018
ms.openlocfilehash: de4ec036be4611ee56823ced3e0cddca5c32b900
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61977694"
---
# <a name="development-process-for-docker-based-applications"></a><span data-ttu-id="b0608-104">Proces vývoje pro aplikace založené na Dockeru</span><span class="sxs-lookup"><span data-stu-id="b0608-104">Development Process for Docker-Based Applications</span></span>

<span data-ttu-id="b0608-105">*Vývoj kontejnerizovaných aplikací .NET způsobem, který rádi používáte, IDE, zaměřuje sadou Visual Studio a Visual Studio tools for Docker nebo rozhraní příkazového řádku/Editor, zaměřuje pomocí rozhraní příkazového řádku Dockeru a Visual Studio Code.*</span><span class="sxs-lookup"><span data-stu-id="b0608-105">*Develop containerized .NET applications the way you like, either IDE focused with Visual Studio and Visual Studio tools for Docker or CLI/Editor focused with Docker CLI and Visual Studio Code.*</span></span>

## <a name="development-environment-for-docker-apps"></a><span data-ttu-id="b0608-106">Vývojové prostředí pro aplikace Dockeru</span><span class="sxs-lookup"><span data-stu-id="b0608-106">Development environment for Docker apps</span></span>

### <a name="development-tool-choices-ide-or-editor"></a><span data-ttu-id="b0608-107">Volba nástroje pro vývoj: Prostředím IDE nebo editorem</span><span class="sxs-lookup"><span data-stu-id="b0608-107">Development tool choices: IDE or editor</span></span>

<span data-ttu-id="b0608-108">Ať už dáváte přednost úplné a výkonné IDE nebo editoru jednoduchý a flexibilní, společnost Microsoft má nástroje, které můžete použít pro vývoj aplikací Dockeru.</span><span class="sxs-lookup"><span data-stu-id="b0608-108">Whether you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has tools that you can use for developing Docker applications.</span></span>

<span data-ttu-id="b0608-109">**Visual Studio (for Windows).**</span><span class="sxs-lookup"><span data-stu-id="b0608-109">**Visual Studio (for Windows).**</span></span> <span data-ttu-id="b0608-110">Při vývoji aplikací dockeru pomocí sady Visual Studio, doporučujeme použít Visual Studio 2017 verze 15.7 nebo novější, která se dodává s nástroji pro Docker již integrované.</span><span class="sxs-lookup"><span data-stu-id="b0608-110">When developing Docker-based applications with Visual Studio, it's recommended to use Visual Studio 2017 version 15.7 or later, that comes with tools for Docker already built-in.</span></span> <span data-ttu-id="b0608-111">Nástroje pro Docker umožňují vyvíjet, spouštět a ověřovat aplikace přímo v cílovém prostředí Docker.</span><span class="sxs-lookup"><span data-stu-id="b0608-111">The tools for Docker let you develop, run, and validate your applications directly in the target Docker environment.</span></span> <span data-ttu-id="b0608-112">Můžete stisknutím klávesy F5 ke spuštění a ladění aplikace (jedním kontejnerem nebo více kontejnerů) přímo do hostitele Docker nebo stisknutím kláves CTRL + F5, upravit a aktualizovat aplikace bez nutnosti znovu sestavovat kontejner.</span><span class="sxs-lookup"><span data-stu-id="b0608-112">You can press F5 to run and debug your application (single container or multiple containers) directly into a Docker host, or press CTRL+F5 to edit and refresh your application without having to rebuild the container.</span></span> <span data-ttu-id="b0608-113">Toto je nejvýkonnější vývoj volbou pro aplikace založené na Dockeru.</span><span class="sxs-lookup"><span data-stu-id="b0608-113">This is the most powerful development choice for Docker-based apps.</span></span>

<span data-ttu-id="b0608-114">**Visual Studio for Mac.**</span><span class="sxs-lookup"><span data-stu-id="b0608-114">**Visual Studio for Mac.**</span></span> <span data-ttu-id="b0608-115">Je integrované vývojové prostředí, vývoj Xamarin Studio, spuštěné v systému macOS a podporuje Docker od poloviny 2017.</span><span class="sxs-lookup"><span data-stu-id="b0608-115">It's an IDE, evolution of Xamarin Studio, running in macOS and supports Docker since mid-2017.</span></span> <span data-ttu-id="b0608-116">To by měl být upřednostňovanou volbu pro vývojáře pracující na počítačích Mac, které také chtějí využívat výkonné integrované vývojové prostředí.</span><span class="sxs-lookup"><span data-stu-id="b0608-116">This should be the preferred choice for developers working in Mac machines who also want to use a powerful IDE.</span></span>

<span data-ttu-id="b0608-117">**Visual Studio Code a Dockeru CLI**.</span><span class="sxs-lookup"><span data-stu-id="b0608-117">**Visual Studio Code and Docker CLI**.</span></span> <span data-ttu-id="b0608-118">Pokud dáváte přednost jednoduchý a multiplatformní editor, který podporuje jakýkoli jazyk pro vývoj, můžete použít Microsoft Visual Studio Code (VS Code) a rozhraní příkazového řádku Dockeru.</span><span class="sxs-lookup"><span data-stu-id="b0608-118">If you prefer a lightweight and cross-platform editor that supports any development language, you can use Microsoft Visual Studio Code (VS Code) and the Docker CLI.</span></span> <span data-ttu-id="b0608-119">Toto je postup vývoj multiplatformních aplikací pro Mac, Linux a Windows.</span><span class="sxs-lookup"><span data-stu-id="b0608-119">This is a cross-platform development approach for Mac, Linux, and Windows.</span></span> <span data-ttu-id="b0608-120">Kromě toho Visual Studio Code podporuje rozšíření pro Docker, jako je například technologie IntelliSense pro soubory Dockerfile a místní úlohy spouštět příkazy Dockeru z editoru.</span><span class="sxs-lookup"><span data-stu-id="b0608-120">Additionally, Visual Studio Code supports extensions for Docker such as IntelliSense for Dockerfiles and shortcut tasks to run Docker commands from the editor.</span></span>

<span data-ttu-id="b0608-121">Nainstalováním [Docker Community Edition (CE)](https://www.docker.com/community-edition) nástroje, jednotné rozhraní příkazového řádku Dockeru můžete použít k vytváření aplikací pro Windows a Linux.</span><span class="sxs-lookup"><span data-stu-id="b0608-121">By installing [Docker Community Edition (CE)](https://www.docker.com/community-edition) tools, you can use a single Docker CLI to build apps for both Windows and Linux.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="b0608-122">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="b0608-122">Additional resources</span></span>

- <span data-ttu-id="b0608-123">**Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="b0608-123">**Visual Studio**.</span></span> <span data-ttu-id="b0608-124">Oficiální web.</span><span class="sxs-lookup"><span data-stu-id="b0608-124">Official site.</span></span> \
  [https://visualstudio.microsoft.com/vs/](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

- <span data-ttu-id="b0608-125">**Visual Studio Code**.</span><span class="sxs-lookup"><span data-stu-id="b0608-125">**Visual Studio Code**.</span></span> <span data-ttu-id="b0608-126">Oficiální web.</span><span class="sxs-lookup"><span data-stu-id="b0608-126">Official site.</span></span> \
  <https://code.visualstudio.com/download>

- <span data-ttu-id="b0608-127">**Docker Community Edition (CE) pro Mac a Windows** \\</span><span class="sxs-lookup"><span data-stu-id="b0608-127">**Docker Community Edition (CE) for Mac and Windows** \\</span></span>
  [https://www.docker.com/community-editions](https://www.docker.com/community-edition)

## <a name="net-languages-and-frameworks-for-docker-containers"></a><span data-ttu-id="b0608-128">Jazyky .NET a rozhraní pro kontejnery Dockeru</span><span class="sxs-lookup"><span data-stu-id="b0608-128">.NET languages and frameworks for Docker containers</span></span>

<span data-ttu-id="b0608-129">Jak je uvedeno v předchozí části této příručky, můžete rozhraní .NET Framework, .NET Core a open source projektu Mono při vývoji Docker kontejnerizovaných aplikací .NET.</span><span class="sxs-lookup"><span data-stu-id="b0608-129">As mentioned in earlier sections of this guide, you can use .NET Framework, .NET Core, or the open-source Mono project when developing Docker containerized .NET applications.</span></span> <span data-ttu-id="b0608-130">Můžete vyvíjet v jazyce C\#, F\#, nebo při cílení na Linuxu nebo Windows, kontejnery, v závislosti na tom, které rozhraní .NET framework se používá jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b0608-130">You can develop in C\#, F\#, or Visual Basic when targeting Linux or Windows Containers, depending on which .NET framework is in use.</span></span> <span data-ttu-id="b0608-131">Další podrobnosti o about.NET jazyky, naleznete v příspěvku blogu [The jazyková strategie .NET](https://devblogs.microsoft.com/dotnet/the-net-language-strategy/).</span><span class="sxs-lookup"><span data-stu-id="b0608-131">For more details about.NET languages, see the blog post [The .NET Language Strategy](https://devblogs.microsoft.com/dotnet/the-net-language-strategy/).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b0608-132">[Předchozí](../architect-microservice-container-applications/using-azure-service-fabric.md)
>[další](docker-app-development-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b0608-132">[Previous](../architect-microservice-container-applications/using-azure-service-fabric.md)
[Next](docker-app-development-workflow.md)</span></span>
