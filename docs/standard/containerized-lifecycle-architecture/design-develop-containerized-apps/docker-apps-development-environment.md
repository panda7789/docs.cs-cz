---
title: Vývojové prostředí pro Docker aplikace
description: Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ddd1006c8c6728d4d315442f409f8fa33e54f9a3
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="development-environment-for-docker-apps"></a><span data-ttu-id="94297-103">Vývojové prostředí pro Docker aplikace</span><span class="sxs-lookup"><span data-stu-id="94297-103">Development environment for Docker apps</span></span>

## <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="94297-104">Vývojových nástrojů volby: IDE nebo editoru</span><span class="sxs-lookup"><span data-stu-id="94297-104">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="94297-105">Bez ohledu Pokud dáváte přednost úplné a výkonné IDE nebo jednoduchý a agilní editor, společnost Microsoft nemá je popsané, pokud jde o vývoj aplikací Docker.</span><span class="sxs-lookup"><span data-stu-id="94297-105">No matter if you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when it comes to developing Docker applications.</span></span>

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a><span data-ttu-id="94297-106">Visual Studio Code a příkazového řádku Dockeru (nástroje a platformy pro Mac, Linux a Windows)</span><span class="sxs-lookup"><span data-stu-id="94297-106">Visual Studio Code and Docker CLI (cross-platform tools for Mac, Linux, and Windows)</span></span>

<span data-ttu-id="94297-107">Pokud dáváte přednost lightweight, napříč platformami editor podpora žádný jazyk vývoj, můžete použít Visual Studio Code a příkazového řádku Dockeru.</span><span class="sxs-lookup"><span data-stu-id="94297-107">If you prefer a lightweight, cross-platform editor supporting any development language, you can use Visual Studio Code and Docker CLI.</span></span> <span data-ttu-id="94297-108">Tyto produkty poskytují jednoduché, ale robustní prostředí, což je velmi důležitá pro zjednodušení pracovního postupu developer.</span><span class="sxs-lookup"><span data-stu-id="94297-108">These products provide a simple yet robust experience, which is critical for streamlining the developer workflow.</span></span> <span data-ttu-id="94297-109">Nainstalováním "Docker pro Mac" nebo "Docker pro systém Windows" (vývojové prostředí) Docker mohou vývojáři jednoho příkazového řádku Dockeru pro vývoj aplikací pro Windows nebo Linux (prostředí runtime).</span><span class="sxs-lookup"><span data-stu-id="94297-109">By installing "Docker for Mac" or "Docker for Windows" (development environment), Docker developers can use a single Docker CLI to build apps for both Windows or Linux (runtime environment).</span></span> <span data-ttu-id="94297-110">Navíc Visual Studio Code podporuje rozšíření pro Docker pomocí IntelliSense pro Dockerfiles a zástupce úlohy ke spuštění příkazů Docker v editoru.</span><span class="sxs-lookup"><span data-stu-id="94297-110">Plus, Visual Studio Code supports extensions for Docker with IntelliSense for Dockerfiles and shortcut-tasks to run Docker commands from the editor.</span></span>

> [!NOTE]
> <span data-ttu-id="94297-111">Chcete-li stáhnout Visual Studio Code, přejděte na <https://code.visualstudio.com/download>.</span><span class="sxs-lookup"><span data-stu-id="94297-111">To download Visual Studio Code, go to <https://code.visualstudio.com/download>.</span></span>

<span data-ttu-id="94297-112">Chcete-li stáhnout Docker pro Mac a Windows, přejděte na <http://www.docker.com/products/docker>.</span><span class="sxs-lookup"><span data-stu-id="94297-112">To download Docker for Mac and Windows, go to <http://www.docker.com/products/docker>.</span></span>

### <a name="visual-studio-with-docker-tools"></a><span data-ttu-id="94297-113">Visual Studio s nástroji Docker</span><span class="sxs-lookup"><span data-stu-id="94297-113">Visual Studio with Docker Tools</span></span>

<span data-ttu-id="94297-114">Pokud používáte Visual Studio 2015 můžete nainstalovat nástroje rozšíření "Docker Tools pro sadu Visual Studio".</span><span class="sxs-lookup"><span data-stu-id="94297-114">When you're using Visual Studio 2015 you can install the add-on tools "Docker Tools for Visual Studio."</span></span> <span data-ttu-id="94297-115">Pro Visual Studio 2017 nástroje Docker pocházet integrované již.</span><span class="sxs-lookup"><span data-stu-id="94297-115">For Visual Studio 2017, Docker Tools come built in already.</span></span> <span data-ttu-id="94297-116">V obou případech můžete vyvíjet, spuštění a ověření aplikace přímo ve zvolené Docker prostředí.</span><span class="sxs-lookup"><span data-stu-id="94297-116">In both cases you can develop, run, and validate your applications directly in the chosen Docker environment.</span></span> <span data-ttu-id="94297-117">F5 vaší aplikace (kontejner jednoho nebo několika kontejnerů) přímo do Docker hostitele s laděním nebo stiskněte klávesu Ctrl + F5 upravte a aktualizujte aplikaci bez nutnosti znovu sestavit kontejneru.</span><span class="sxs-lookup"><span data-stu-id="94297-117">F5 your application (single container or multiple containers) directly into a Docker host with debugging, or press Ctrl+F5 to edit and refresh your app without having to rebuild the container.</span></span> <span data-ttu-id="94297-118">Toto je nejjednodušší a výkonnější volba pro vývojáře systému Windows vytváření Docker kontejnery pro Linux nebo Windows.</span><span class="sxs-lookup"><span data-stu-id="94297-118">This is the simplest and more powerful choice for Windows developers creating Docker containers for Linux or Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="94297-119">Chcete-li stáhnout Docker nástrojů pro Visual Studio, přejděte na <https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>.</span><span class="sxs-lookup"><span data-stu-id="94297-119">To download Docker Tools for Visual Studio, go to <https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>.</span></span>

## <a name="language-and-framework-choices"></a><span data-ttu-id="94297-120">Možnosti jazyka a framework</span><span class="sxs-lookup"><span data-stu-id="94297-120">Language and framework choices</span></span>

<span data-ttu-id="94297-121">Můžete vyvíjet aplikace Docker a nástroje Microsoft s většina moderních jazyků.</span><span class="sxs-lookup"><span data-stu-id="94297-121">You can develop Docker applications and Microsoft tools with most modern languages.</span></span> <span data-ttu-id="94297-122">Toto je počáteční seznam, ale nejste omezeni na ni:</span><span class="sxs-lookup"><span data-stu-id="94297-122">The following is an initial list, but you are not limited to it:</span></span>

-   <span data-ttu-id="94297-123">.NET core a ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="94297-123">.NET Core and ASP.NET Core</span></span>

-   <span data-ttu-id="94297-124">Node.js</span><span class="sxs-lookup"><span data-stu-id="94297-124">Node.js</span></span>

-   <span data-ttu-id="94297-125">Golang</span><span class="sxs-lookup"><span data-stu-id="94297-125">Golang</span></span>

-   <span data-ttu-id="94297-126">Java</span><span class="sxs-lookup"><span data-stu-id="94297-126">Java</span></span>

-   <span data-ttu-id="94297-127">Ruby</span><span class="sxs-lookup"><span data-stu-id="94297-127">Ruby</span></span>

-   <span data-ttu-id="94297-128">Python</span><span class="sxs-lookup"><span data-stu-id="94297-128">Python</span></span>

<span data-ttu-id="94297-129">V podstatě můžete použít jakýkoli moderní jazyk podporuje Docker v systému Linux nebo Windows.</span><span class="sxs-lookup"><span data-stu-id="94297-129">Basically, you can use any modern language supported by Docker in Linux or Windows.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="94297-130">[Předchozí] (orchestraci vysokou škálovatelnost availability.md) [Další] (docker aplikace vnitřní smyčky workflow.md)</span><span class="sxs-lookup"><span data-stu-id="94297-130">[Previous] (orchestrate-high-scalability-availability.md) [Next] (docker-apps-inner-loop-workflow.md)</span></span>
