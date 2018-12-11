---
title: Vývojové prostředí pro aplikace Dockeru
description: Životní cyklus aplikace kontejnerizovaných Dockeru s platformou a nástroji Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 471b52fd577e5560bd93e6da50f2032d63eb2e6f
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152407"
---
# <a name="development-environment-for-docker-apps"></a><span data-ttu-id="10be5-103">Vývojové prostředí pro aplikace Dockeru</span><span class="sxs-lookup"><span data-stu-id="10be5-103">Development environment for Docker apps</span></span>

## <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="10be5-104">Možnosti vývojářských nástrojů: Prostředím IDE nebo editorem</span><span class="sxs-lookup"><span data-stu-id="10be5-104">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="10be5-105">Bez ohledu na to pokud dáváte přednost úplné a výkonné IDE nebo editorem jednoduchý a flexibilní, Microsoft vám kryje záda při rozhodování o vývoji aplikací Dockeru.</span><span class="sxs-lookup"><span data-stu-id="10be5-105">No matter if you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when it comes to developing Docker applications.</span></span>

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a><span data-ttu-id="10be5-106">Visual Studio Code a rozhraní příkazového řádku Dockeru (nástrojů pro různé platformy pro Windows, Mac a Linux)</span><span class="sxs-lookup"><span data-stu-id="10be5-106">Visual Studio Code and Docker CLI (cross-platform tools for Mac, Linux, and Windows)</span></span>

<span data-ttu-id="10be5-107">Pokud dáváte přednost zjednodušené, multiplatformní editor podporuje libovolný jazyk vývoj, můžete použít Visual Studio Code a rozhraní příkazového řádku Dockeru.</span><span class="sxs-lookup"><span data-stu-id="10be5-107">If you prefer a lightweight, cross-platform editor supporting any development language, you can use Visual Studio Code and Docker CLI.</span></span> <span data-ttu-id="10be5-108">Tyto produkty poskytují jednoduché a přitom robustní prostředí, což je velmi důležité pro zjednodušení pracovních postupů vývojářů.</span><span class="sxs-lookup"><span data-stu-id="10be5-108">These products provide a simple yet robust experience, which is critical for streamlining the developer workflow.</span></span> <span data-ttu-id="10be5-109">Nainstalováním "Dockeru pro Mac" nebo "Docker pro Windows" (vývojové prostředí) Dockeru mohou vývojáři jednotné rozhraní příkazového řádku Dockeru k vytváření aplikací pro Windows nebo Linuxem (prostředí runtime).</span><span class="sxs-lookup"><span data-stu-id="10be5-109">By installing "Docker for Mac" or "Docker for Windows" (development environment), Docker developers can use a single Docker CLI to build apps for both Windows or Linux (runtime environment).</span></span> <span data-ttu-id="10be5-110">Kromě toho Visual Studio Code podporuje rozšíření Dockeru s podporou technologie IntelliSense pro soubory Dockerfile a místní úlohy spouštět příkazy Dockeru z editoru.</span><span class="sxs-lookup"><span data-stu-id="10be5-110">Plus, Visual Studio Code supports extensions for Docker with IntelliSense for Dockerfiles and shortcut-tasks to run Docker commands from the editor.</span></span>

> [!NOTE]
> <span data-ttu-id="10be5-111">Pokud chcete stáhnout Visual Studio Code, přejděte na <https://code.visualstudio.com/download>.</span><span class="sxs-lookup"><span data-stu-id="10be5-111">To download Visual Studio Code, go to <https://code.visualstudio.com/download>.</span></span>

<span data-ttu-id="10be5-112">Chcete-li stáhnout Docker pro Mac a Windows, přejděte na <https://www.docker.com/products/docker>.</span><span class="sxs-lookup"><span data-stu-id="10be5-112">To download Docker for Mac and Windows, go to <https://www.docker.com/products/docker>.</span></span>

### <a name="visual-studio-with-docker-tools"></a><span data-ttu-id="10be5-113">Visual Studio s nástroji Dockeru</span><span class="sxs-lookup"><span data-stu-id="10be5-113">Visual Studio with Docker Tools</span></span>

<span data-ttu-id="10be5-114">Pokud používáte Visual Studio 2015 můžete nainstalovat nástroje doplňků "Docker Tools for Visual Studio".</span><span class="sxs-lookup"><span data-stu-id="10be5-114">When you're using Visual Studio 2015 you can install the add-on tools "Docker Tools for Visual Studio."</span></span> <span data-ttu-id="10be5-115">Pro Visual Studio 2017 nástroje Dockeru pocházet integrované již.</span><span class="sxs-lookup"><span data-stu-id="10be5-115">For Visual Studio 2017, Docker Tools come built in already.</span></span> <span data-ttu-id="10be5-116">V obou případech můžete vyvíjet spouštět a ověřovat aplikace přímo ve zvoleném prostředí Dockeru.</span><span class="sxs-lookup"><span data-stu-id="10be5-116">In both cases you can develop, run, and validate your applications directly in the chosen Docker environment.</span></span> <span data-ttu-id="10be5-117">F5 aplikaci (jedním kontejnerem nebo více kontejnerů) přímo do Docker hostování s laděním, nebo stisknutím kláves Ctrl + F5, upravit a aktualizovat aplikace bez nutnosti znovu sestavovat kontejner.</span><span class="sxs-lookup"><span data-stu-id="10be5-117">F5 your application (single container or multiple containers) directly into a Docker host with debugging, or press Ctrl+F5 to edit and refresh your app without having to rebuild the container.</span></span> <span data-ttu-id="10be5-118">Toto je nejjednodušší a výkonnější volbou pro vývojáře Windows vytváření kontejnerů Dockeru pro Linux nebo Windows.</span><span class="sxs-lookup"><span data-stu-id="10be5-118">This is the simplest and more powerful choice for Windows developers creating Docker containers for Linux or Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="10be5-119">Chcete-li stáhnout Docker Tools for Visual Studio, přejděte na <https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>.</span><span class="sxs-lookup"><span data-stu-id="10be5-119">To download Docker Tools for Visual Studio, go to <https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>.</span></span>

## <a name="language-and-framework-choices"></a><span data-ttu-id="10be5-120">Volby jazyka a framework</span><span class="sxs-lookup"><span data-stu-id="10be5-120">Language and framework choices</span></span>

<span data-ttu-id="10be5-121">Můžete vyvíjet Docker aplikacím a nástrojům společnosti Microsoft s většinou moderních jazyků.</span><span class="sxs-lookup"><span data-stu-id="10be5-121">You can develop Docker applications and Microsoft tools with most modern languages.</span></span> <span data-ttu-id="10be5-122">Toto je počáteční seznam, ale nejste omezeni na něj:</span><span class="sxs-lookup"><span data-stu-id="10be5-122">The following is an initial list, but you are not limited to it:</span></span>

-   <span data-ttu-id="10be5-123">.NET Core a ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="10be5-123">.NET Core and ASP.NET Core</span></span>
-   <span data-ttu-id="10be5-124">Node.js</span><span class="sxs-lookup"><span data-stu-id="10be5-124">Node.js</span></span>
-   <span data-ttu-id="10be5-125">Golang</span><span class="sxs-lookup"><span data-stu-id="10be5-125">Golang</span></span>
-   <span data-ttu-id="10be5-126">Java</span><span class="sxs-lookup"><span data-stu-id="10be5-126">Java</span></span>
-   <span data-ttu-id="10be5-127">Ruby</span><span class="sxs-lookup"><span data-stu-id="10be5-127">Ruby</span></span>
-   <span data-ttu-id="10be5-128">Python</span><span class="sxs-lookup"><span data-stu-id="10be5-128">Python</span></span>

<span data-ttu-id="10be5-129">V podstatě můžete použít libovolný moderní jazyk podporuje Docker v Linuxu nebo Windows.</span><span class="sxs-lookup"><span data-stu-id="10be5-129">Basically, you can use any modern language supported by Docker in Linux or Windows.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="10be5-130">[Předchozí](orchestrate-high-scalability-availability.md)
>[další](docker-apps-inner-loop-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="10be5-130">[Previous](orchestrate-high-scalability-availability.md)
[Next](docker-apps-inner-loop-workflow.md)</span></span>