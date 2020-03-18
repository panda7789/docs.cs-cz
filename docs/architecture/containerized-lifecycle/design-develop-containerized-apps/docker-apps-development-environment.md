---
title: Vývojové prostředí pro aplikace Dockeru
description: Seznamte se s nejdůležitějšími možnostmi vývojových nástrojů, které podporují životní cyklus vývoje Dockeru.
ms.date: 02/15/2019
ms.openlocfilehash: 35236e75f47e830d0970ca9cfd074d9a69e6f85c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "71214300"
---
# <a name="development-environment-for-docker-apps"></a><span data-ttu-id="0fe23-103">Vývojové prostředí pro aplikace Dockeru</span><span class="sxs-lookup"><span data-stu-id="0fe23-103">Development environment for Docker apps</span></span>

## <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="0fe23-104">Volby vývojových nástrojů: IDE nebo editor</span><span class="sxs-lookup"><span data-stu-id="0fe23-104">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="0fe23-105">Bez ohledu na to, zda dáváte přednost úplnému a výkonnému rozhraní IDE nebo lehkému a agilnímu editoru, společnost Microsoft vás pokryje, pokud jde o vývoj aplikací Dockeru.</span><span class="sxs-lookup"><span data-stu-id="0fe23-105">No matter if you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when it comes to developing Docker applications.</span></span>

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a><span data-ttu-id="0fe23-106">Visual Studio Code a Docker CLI (nástroje pro různé platformy pro Mac, Linux a Windows)</span><span class="sxs-lookup"><span data-stu-id="0fe23-106">Visual Studio Code and Docker CLI (cross-platform tools for Mac, Linux, and Windows)</span></span>

<span data-ttu-id="0fe23-107">Pokud dáváte přednost lehký editor pro více platforem podporující jakýkoli vývojový jazyk, můžete použít Visual Studio Code a Docker CLI.</span><span class="sxs-lookup"><span data-stu-id="0fe23-107">If you prefer a lightweight, cross-platform editor supporting any development language, you can use Visual Studio Code and Docker CLI.</span></span> <span data-ttu-id="0fe23-108">Tyto produkty poskytují jednoduché, ale robustní prostředí, což je důležité pro zjednodušení pracovního postupu pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="0fe23-108">These products provide a simple yet robust experience, which is critical for streamlining the developer workflow.</span></span> <span data-ttu-id="0fe23-109">Instalací "Docker for Mac" nebo "Docker for Windows" (vývojové prostředí) můžou vývojáři Dockeru používat jeden rozhraní CLI Dockeru k vytváření aplikací pro Windows i Linux (runtime prostředí).</span><span class="sxs-lookup"><span data-stu-id="0fe23-109">By installing "Docker for Mac" or "Docker for Windows" (development environment), Docker developers can use a single Docker CLI to build apps for both Windows or Linux (runtime environment).</span></span> <span data-ttu-id="0fe23-110">Visual Studio Code navíc podporuje rozšíření pro Docker s IntelliSense pro Dockerfiles a zkratkové úlohy pro spouštění příkazů Dockeru z editoru.</span><span class="sxs-lookup"><span data-stu-id="0fe23-110">Plus, Visual Studio Code supports extensions for Docker with IntelliSense for Dockerfiles and shortcut-tasks to run Docker commands from the editor.</span></span>

> [!NOTE]
> <span data-ttu-id="0fe23-111">Chcete-li stáhnout kód <https://code.visualstudio.com/download>sady Visual Studio, přejděte na stránku .</span><span class="sxs-lookup"><span data-stu-id="0fe23-111">To download Visual Studio Code, go to <https://code.visualstudio.com/download>.</span></span>
>
> <span data-ttu-id="0fe23-112">Pokud chcete stáhnout Docker pro <https://www.docker.com/products/docker>Mac a Windows, přejděte na .</span><span class="sxs-lookup"><span data-stu-id="0fe23-112">To download Docker for Mac and Windows, go to <https://www.docker.com/products/docker>.</span></span>

### <a name="visual-studio-with-docker-tools-windows-development-machine"></a><span data-ttu-id="0fe23-113">Visual Studio s nástroji Docker Tools (vývojový počítač windows)</span><span class="sxs-lookup"><span data-stu-id="0fe23-113">Visual Studio with Docker Tools (Windows development machine)</span></span>

<span data-ttu-id="0fe23-114">Doporučujeme používat Visual Studio 2017 (nebo novější) s integrovanými nástroji Dockeru.</span><span class="sxs-lookup"><span data-stu-id="0fe23-114">We recommend you use Visual Studio 2017 (or later) with the built-in Docker Tools enabled.</span></span> <span data-ttu-id="0fe23-115">Pomocí sady Visual Studio můžete vyvíjet, spouštět a ověřovat aplikace přímo ve zvoleném prostředí Dockeru.</span><span class="sxs-lookup"><span data-stu-id="0fe23-115">With Visual Studio, you can develop, run, and validate your applications directly in the chosen Docker environment.</span></span> <span data-ttu-id="0fe23-116">Stisknutím klávesy F5 ladíte aplikaci (jeden kontejner nebo více kontejnerů) přímo v hostiteli Dockeru nebo stisknutím kombinace kláves Ctrl+F5 upravte a aktualizujte aplikaci bez nutnosti obnovovat kontejner.</span><span class="sxs-lookup"><span data-stu-id="0fe23-116">Press F5 to debug your application (single container or multiple containers) directly in a Docker host, or press Ctrl+F5 to edit and refresh your app without having to rebuild the container.</span></span> <span data-ttu-id="0fe23-117">Je to nejjednodušší a nejvýkonnější volba pro vývojáře Windows vytvářet kontejnery Docker pro Linux nebo Windows.</span><span class="sxs-lookup"><span data-stu-id="0fe23-117">It's the simplest and most powerful choice for Windows developers to create Docker containers for Linux or Windows.</span></span>

### <a name="visual-studio-for-mac-mac-development-machine"></a><span data-ttu-id="0fe23-118">Visual Studio pro Mac (mac vývojový počítač)</span><span class="sxs-lookup"><span data-stu-id="0fe23-118">Visual Studio for Mac (Mac development machine)</span></span>

<span data-ttu-id="0fe23-119">[Visual Studio pro Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) můžete použít při vývoji aplikací založených na Dockeru.</span><span class="sxs-lookup"><span data-stu-id="0fe23-119">You can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) when developing Docker-based applications.</span></span> <span data-ttu-id="0fe23-120">Visual Studio pro Mac nabízí bohatší IDE ve srovnání s Visual Studio Code for Mac.</span><span class="sxs-lookup"><span data-stu-id="0fe23-120">Visual Studio for Mac offers a richer IDE when compared to Visual Studio Code for Mac.</span></span>

## <a name="language-and-framework-choices"></a><span data-ttu-id="0fe23-121">Jazykové a rámcové volby</span><span class="sxs-lookup"><span data-stu-id="0fe23-121">Language and framework choices</span></span>

<span data-ttu-id="0fe23-122">Aplikace Dockeru můžete vyvíjet pomocí nástrojů Microsoftu s většinou moderních jazyků.</span><span class="sxs-lookup"><span data-stu-id="0fe23-122">You can develop Docker applications using Microsoft tools with most modern languages.</span></span> <span data-ttu-id="0fe23-123">Následuje počáteční seznam, ale nejste omezeni na něj:</span><span class="sxs-lookup"><span data-stu-id="0fe23-123">The following is an initial list, but you're not limited to it:</span></span>

- <span data-ttu-id="0fe23-124">.NET Core a ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0fe23-124">.NET Core and ASP.NET Core</span></span>
- <span data-ttu-id="0fe23-125">Node.js</span><span class="sxs-lookup"><span data-stu-id="0fe23-125">Node.js</span></span>
- <span data-ttu-id="0fe23-126">Přejít</span><span class="sxs-lookup"><span data-stu-id="0fe23-126">Go</span></span>
- <span data-ttu-id="0fe23-127">Java</span><span class="sxs-lookup"><span data-stu-id="0fe23-127">Java</span></span>
- <span data-ttu-id="0fe23-128">Ruby</span><span class="sxs-lookup"><span data-stu-id="0fe23-128">Ruby</span></span>
- <span data-ttu-id="0fe23-129">Python</span><span class="sxs-lookup"><span data-stu-id="0fe23-129">Python</span></span>

<span data-ttu-id="0fe23-130">V podstatě můžete použít libovolný moderní jazyk podporovaný Dockerem v Linuxu nebo Windows.</span><span class="sxs-lookup"><span data-stu-id="0fe23-130">Basically, you can use any modern language supported by Docker in Linux or Windows.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0fe23-131">[Předchozí](deploy-azure-kubernetes-service.md)
>[další](docker-apps-inner-loop-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="0fe23-131">[Previous](deploy-azure-kubernetes-service.md)
[Next](docker-apps-inner-loop-workflow.md)</span></span>
