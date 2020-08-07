---
title: Vývojové prostředí pro aplikace Dockeru
description: Získejte informace o nejdůležitějších možnostech vývojářských nástrojů, které podporují životní cyklus vývojového prostředí Docker.
ms.date: 08/06/2020
ms.openlocfilehash: 07b42b2bd05ab16ba0fbf61863b050ee2c9e242b
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916025"
---
# <a name="development-environment-for-docker-apps"></a><span data-ttu-id="e6846-103">Vývojové prostředí pro aplikace Dockeru</span><span class="sxs-lookup"><span data-stu-id="e6846-103">Development environment for Docker apps</span></span>

## <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="e6846-104">Možnosti vývojových nástrojů: IDE nebo Editor</span><span class="sxs-lookup"><span data-stu-id="e6846-104">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="e6846-105">Bez ohledu na to, jestli dáváte přednost celému a výkonnému integrovanému vývojového prostředí (IDE) nebo odlehčenému a agilnímu editoru, Microsoft vás zajímá, pokud je součástí vývoje aplikací Docker.</span><span class="sxs-lookup"><span data-stu-id="e6846-105">No matter if you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when it comes to developing Docker applications.</span></span>

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a><span data-ttu-id="e6846-106">Visual Studio Code a Docker CLI (nástroje pro různé platformy pro Mac, Linux a Windows)</span><span class="sxs-lookup"><span data-stu-id="e6846-106">Visual Studio Code and Docker CLI (cross-platform tools for Mac, Linux, and Windows)</span></span>

<span data-ttu-id="e6846-107">Pokud dáváte přednost zjednodušenému editoru pro různé platformy, který podporuje jazyk vývoje, můžete použít Visual Studio Code a Docker CLI.</span><span class="sxs-lookup"><span data-stu-id="e6846-107">If you prefer a lightweight, cross-platform editor supporting any development language, you can use Visual Studio Code and Docker CLI.</span></span> <span data-ttu-id="e6846-108">Tyto produkty poskytují jednoduché a stále robustní prostředí, které je důležité pro zjednodušení pracovního postupu vývojářů.</span><span class="sxs-lookup"><span data-stu-id="e6846-108">These products provide a simple yet robust experience, which is critical for streamlining the developer workflow.</span></span> <span data-ttu-id="e6846-109">Když nainstalujete "Docker pro Mac" nebo "Docker for Windows" (vývojové prostředí), můžou vývojáři Docker používat k vytváření aplikací pro Windows i Linux (běhové prostředí) jeden Docker CLI.</span><span class="sxs-lookup"><span data-stu-id="e6846-109">By installing "Docker for Mac" or "Docker for Windows" (development environment), Docker developers can use a single Docker CLI to build apps for both Windows or Linux (runtime environment).</span></span> <span data-ttu-id="e6846-110">Navíc Visual Studio Code podporuje rozšíření pro Docker pomocí IntelliSense pro fázemi a úlohy zástupce pro spouštění příkazů Docker z editoru.</span><span class="sxs-lookup"><span data-stu-id="e6846-110">Plus, Visual Studio Code supports extensions for Docker with IntelliSense for Dockerfiles and shortcut-tasks to run Docker commands from the editor.</span></span>

> [!NOTE]
> <span data-ttu-id="e6846-111">Pokud chcete stáhnout Visual Studio Code, pokračujte na <https://code.visualstudio.com/download> .</span><span class="sxs-lookup"><span data-stu-id="e6846-111">To download Visual Studio Code, go to <https://code.visualstudio.com/download>.</span></span>
>
> <span data-ttu-id="e6846-112">Chcete-li stáhnout Docker pro Mac a Windows, pokračujte na <https://www.docker.com/products/docker> .</span><span class="sxs-lookup"><span data-stu-id="e6846-112">To download Docker for Mac and Windows, go to <https://www.docker.com/products/docker>.</span></span>

### <a name="visual-studio-with-docker-tools-windows-development-machine"></a><span data-ttu-id="e6846-113">Visual Studio s nástroji Docker (vývojový počítač s Windows)</span><span class="sxs-lookup"><span data-stu-id="e6846-113">Visual Studio with Docker Tools (Windows development machine)</span></span>

<span data-ttu-id="e6846-114">Doporučuje se používat Visual Studio 2019 s integrovanými nástroji Docker, které jsou povolené.</span><span class="sxs-lookup"><span data-stu-id="e6846-114">It's recommend that you use Visual Studio 2019 with the built-in Docker Tools enabled.</span></span> <span data-ttu-id="e6846-115">Se sadou Visual Studio můžete vyvíjet, spouštět a ověřovat aplikace přímo ve zvoleném prostředí Docker.</span><span class="sxs-lookup"><span data-stu-id="e6846-115">With Visual Studio, you can develop, run, and validate your applications directly in the chosen Docker environment.</span></span> <span data-ttu-id="e6846-116">Stiskněte klávesu F5, chcete-li ladit aplikaci (jeden kontejner nebo více kontejnerů) přímo v hostiteli Docker, nebo stiskněte klávesy CTRL + F5 pro úpravu a aktualizaci aplikace bez nutnosti opětovného sestavení kontejneru.</span><span class="sxs-lookup"><span data-stu-id="e6846-116">Press F5 to debug your application (single container or multiple containers) directly in a Docker host, or press Ctrl+F5 to edit and refresh your app without having to rebuild the container.</span></span> <span data-ttu-id="e6846-117">Je to nejjednodušší a nejúčinnější volba pro vývojáře v systému Windows k vytvoření kontejnerů Docker pro Linux nebo Windows.</span><span class="sxs-lookup"><span data-stu-id="e6846-117">It's the simplest and most powerful choice for Windows developers to create Docker containers for Linux or Windows.</span></span>

### <a name="visual-studio-for-mac-mac-development-machine"></a><span data-ttu-id="e6846-118">Visual Studio pro Mac (počítač pro vývoj Mac)</span><span class="sxs-lookup"><span data-stu-id="e6846-118">Visual Studio for Mac (Mac development machine)</span></span>

<span data-ttu-id="e6846-119">Při vývoji aplikací založených na Docker můžete použít [Visual Studio pro Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) .</span><span class="sxs-lookup"><span data-stu-id="e6846-119">You can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) when developing Docker-based applications.</span></span> <span data-ttu-id="e6846-120">Visual Studio pro Mac nabízí bohatší integrované vývojové prostředí (IDE) ve srovnání s Visual Studio Code for Mac.</span><span class="sxs-lookup"><span data-stu-id="e6846-120">Visual Studio for Mac offers a richer IDE when compared to Visual Studio Code for Mac.</span></span>

## <a name="language-and-framework-choices"></a><span data-ttu-id="e6846-121">Volby jazyka a architektury</span><span class="sxs-lookup"><span data-stu-id="e6846-121">Language and framework choices</span></span>

<span data-ttu-id="e6846-122">Můžete vyvíjet aplikace Docker pomocí nástrojů Microsoftu pro většinu moderních jazyků.</span><span class="sxs-lookup"><span data-stu-id="e6846-122">You can develop Docker applications using Microsoft tools with most modern languages.</span></span> <span data-ttu-id="e6846-123">Následuje úvodní seznam, ale nejste omezeni na něj:</span><span class="sxs-lookup"><span data-stu-id="e6846-123">The following is an initial list, but you're not limited to it:</span></span>

- <span data-ttu-id="e6846-124">.NET Core a ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e6846-124">.NET Core and ASP.NET Core</span></span>
- <span data-ttu-id="e6846-125">Node.js</span><span class="sxs-lookup"><span data-stu-id="e6846-125">Node.js</span></span>
- <span data-ttu-id="e6846-126">Přejít</span><span class="sxs-lookup"><span data-stu-id="e6846-126">Go</span></span>
- <span data-ttu-id="e6846-127">Java</span><span class="sxs-lookup"><span data-stu-id="e6846-127">Java</span></span>
- <span data-ttu-id="e6846-128">Ruby</span><span class="sxs-lookup"><span data-stu-id="e6846-128">Ruby</span></span>
- <span data-ttu-id="e6846-129">Python</span><span class="sxs-lookup"><span data-stu-id="e6846-129">Python</span></span>

<span data-ttu-id="e6846-130">V podstatě můžete použít moderní jazyk podporovaný Docker v systému Linux nebo Windows.</span><span class="sxs-lookup"><span data-stu-id="e6846-130">Basically, you can use any modern language supported by Docker in Linux or Windows.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e6846-131">[Předchozí](deploy-azure-kubernetes-service.md) 
> [Další](docker-apps-inner-loop-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="e6846-131">[Previous](deploy-azure-kubernetes-service.md)
[Next](docker-apps-inner-loop-workflow.md)</span></span>
