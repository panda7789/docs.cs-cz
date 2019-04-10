---
title: Vývojové prostředí pro aplikace Dockeru
description: Seznámení s nejdůležitějších možností nástroj pro vývoj, které podporují Docker vývojového cyklu.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 3a2fcbe3b9380083622b6ce72cea4bab17d7c2ea
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59318816"
---
# <a name="development-environment-for-docker-apps"></a><span data-ttu-id="96736-103">Vývojové prostředí pro aplikace Dockeru</span><span class="sxs-lookup"><span data-stu-id="96736-103">Development environment for Docker apps</span></span>

## <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="96736-104">Možnosti vývojářských nástrojů: Prostředím IDE nebo editorem</span><span class="sxs-lookup"><span data-stu-id="96736-104">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="96736-105">Bez ohledu na to pokud dáváte přednost úplné a výkonné IDE nebo editorem jednoduchý a flexibilní, Microsoft vám kryje záda při rozhodování o vývoji aplikací Dockeru.</span><span class="sxs-lookup"><span data-stu-id="96736-105">No matter if you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when it comes to developing Docker applications.</span></span>

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a><span data-ttu-id="96736-106">Visual Studio Code a rozhraní příkazového řádku Dockeru (nástrojů pro různé platformy pro Windows, Mac a Linux)</span><span class="sxs-lookup"><span data-stu-id="96736-106">Visual Studio Code and Docker CLI (cross-platform tools for Mac, Linux, and Windows)</span></span>

<span data-ttu-id="96736-107">Pokud dáváte přednost zjednodušené, multiplatformní editor podporuje libovolný jazyk vývoj, můžete použít Visual Studio Code a rozhraní příkazového řádku Dockeru.</span><span class="sxs-lookup"><span data-stu-id="96736-107">If you prefer a lightweight, cross-platform editor supporting any development language, you can use Visual Studio Code and Docker CLI.</span></span> <span data-ttu-id="96736-108">Tyto produkty poskytují jednoduché a přitom robustní prostředí, což je velmi důležité pro zjednodušení pracovních postupů vývojářů.</span><span class="sxs-lookup"><span data-stu-id="96736-108">These products provide a simple yet robust experience, which is critical for streamlining the developer workflow.</span></span> <span data-ttu-id="96736-109">Nainstalováním "Dockeru pro Mac" nebo "Docker pro Windows" (vývojové prostředí) Dockeru mohou vývojáři jednotné rozhraní příkazového řádku Dockeru k vytváření aplikací pro Windows nebo Linuxem (prostředí runtime).</span><span class="sxs-lookup"><span data-stu-id="96736-109">By installing "Docker for Mac" or "Docker for Windows" (development environment), Docker developers can use a single Docker CLI to build apps for both Windows or Linux (runtime environment).</span></span> <span data-ttu-id="96736-110">Kromě toho Visual Studio Code podporuje rozšíření Dockeru s podporou technologie IntelliSense pro soubory Dockerfile a místní úlohy spouštět příkazy Dockeru z editoru.</span><span class="sxs-lookup"><span data-stu-id="96736-110">Plus, Visual Studio Code supports extensions for Docker with IntelliSense for Dockerfiles and shortcut-tasks to run Docker commands from the editor.</span></span>

> [!NOTE]
>
> <span data-ttu-id="96736-111">Pokud chcete stáhnout Visual Studio Code, přejděte na <https://code.visualstudio.com/download>.</span><span class="sxs-lookup"><span data-stu-id="96736-111">To download Visual Studio Code, go to <https://code.visualstudio.com/download>.</span></span>
>
> <span data-ttu-id="96736-112">Chcete-li stáhnout Docker pro Mac a Windows, přejděte na <https://www.docker.com/products/docker>.</span><span class="sxs-lookup"><span data-stu-id="96736-112">To download Docker for Mac and Windows, go to <https://www.docker.com/products/docker>.</span></span>

### <a name="visual-studio-with-docker-tools-windows-development-machine"></a><span data-ttu-id="96736-113">Visual Studio s Docker Tools (Windows vývojovém počítači)</span><span class="sxs-lookup"><span data-stu-id="96736-113">Visual Studio with Docker Tools (Windows development machine)</span></span>

<span data-ttu-id="96736-114">Doporučujeme použít Visual Studio 2017 (nebo novější) s integrovanou nástroje Dockeru povolena.</span><span class="sxs-lookup"><span data-stu-id="96736-114">We recommend you use Visual Studio 2017 (or later) with the built-in Docker Tools enabled.</span></span> <span data-ttu-id="96736-115">Pomocí sady Visual Studio můžete vyvíjet, spouštět a ověřovat aplikace přímo ve zvoleném prostředí Dockeru.</span><span class="sxs-lookup"><span data-stu-id="96736-115">With Visual Studio, you can develop, run, and validate your applications directly in the chosen Docker environment.</span></span> <span data-ttu-id="96736-116">Stisknutím klávesy F5 pro ladění vaší aplikace (jedním kontejnerem nebo více kontejnerů) přímo do hostitele Docker nebo stisknutím kláves Ctrl + F5, upravit a aktualizovat aplikace bez nutnosti znovu sestavovat kontejner.</span><span class="sxs-lookup"><span data-stu-id="96736-116">Press F5 to debug your application (single container or multiple containers) directly in a Docker host, or press Ctrl+F5 to edit and refresh your app without having to rebuild the container.</span></span> <span data-ttu-id="96736-117">Jedná se o nejjednodušší a nejvýkonnější volbu pro vývojáře Windows k vytvoření kontejnerů Dockeru pro Windows nebo Linuxem.</span><span class="sxs-lookup"><span data-stu-id="96736-117">It's the simplest and most powerful choice for Windows developers to create Docker containers for Linux or Windows.</span></span>

### <a name="visual-studio-for-mac-mac-development-machine"></a><span data-ttu-id="96736-118">Visual Studio pro Mac (vývoj pro počítač Mac)</span><span class="sxs-lookup"><span data-stu-id="96736-118">Visual Studio for Mac (Mac development machine)</span></span>

<span data-ttu-id="96736-119">Můžete použít [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) při vývoji aplikací založených na Dockeru.</span><span class="sxs-lookup"><span data-stu-id="96736-119">You can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) when developing Docker-based applications.</span></span> <span data-ttu-id="96736-120">Visual Studio pro Mac nabízí bohatší IDE ve srovnání s Visual Studio Code pro Mac</span><span class="sxs-lookup"><span data-stu-id="96736-120">Visual Studio for Mac offers a richer IDE when compared to Visual Studio Code for Mac.</span></span>

## <a name="language-and-framework-choices"></a><span data-ttu-id="96736-121">Volby jazyka a framework</span><span class="sxs-lookup"><span data-stu-id="96736-121">Language and framework choices</span></span>

<span data-ttu-id="96736-122">Můžete vyvíjet aplikace Dockeru pomocí nástrojů společnosti Microsoft s většinou moderních jazyků.</span><span class="sxs-lookup"><span data-stu-id="96736-122">You can develop Docker applications using Microsoft tools with most modern languages.</span></span> <span data-ttu-id="96736-123">Toto je počáteční seznam, ale nejste omezeni pouze na něj:</span><span class="sxs-lookup"><span data-stu-id="96736-123">The following is an initial list, but you're not limited to it:</span></span>

- <span data-ttu-id="96736-124">.NET Core a ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="96736-124">.NET Core and ASP.NET Core</span></span>
- <span data-ttu-id="96736-125">Node.js</span><span class="sxs-lookup"><span data-stu-id="96736-125">Node.js</span></span>
- <span data-ttu-id="96736-126">Go</span><span class="sxs-lookup"><span data-stu-id="96736-126">Go</span></span>
- <span data-ttu-id="96736-127">Java</span><span class="sxs-lookup"><span data-stu-id="96736-127">Java</span></span>
- <span data-ttu-id="96736-128">Ruby</span><span class="sxs-lookup"><span data-stu-id="96736-128">Ruby</span></span>
- <span data-ttu-id="96736-129">Python</span><span class="sxs-lookup"><span data-stu-id="96736-129">Python</span></span>

<span data-ttu-id="96736-130">V podstatě můžete použít libovolný moderní jazyk podporuje Docker v Linuxu nebo Windows.</span><span class="sxs-lookup"><span data-stu-id="96736-130">Basically, you can use any modern language supported by Docker in Linux or Windows.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="96736-131">[Předchozí](deploy-azure-kubernetes-service.md)
>[další](docker-apps-inner-loop-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="96736-131">[Previous](deploy-azure-kubernetes-service.md)
[Next](docker-apps-inner-loop-workflow.md)</span></span>
