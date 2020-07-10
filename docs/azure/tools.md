---
title: Nástroje pro vývojáře na platformě Azure .NET
description: Získejte nástroje pro zahájení používání knihoven Azure .NET z prostředí Windows, Linux a Mac.
ms.date: 06/19/2020
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: fa645b152f15550b25a3542ba0cdbb43799536b9
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174907"
---
# <a name="azure-tools-for-developing-with-net"></a><span data-ttu-id="af845-103">Nástroje Azure pro vývoj s využitím .NET</span><span class="sxs-lookup"><span data-stu-id="af845-103">Azure tools for developing with .NET</span></span>

## <a name="sdk-downloads"></a><span data-ttu-id="af845-104">Soubory sady SDK ke stažení</span><span class="sxs-lookup"><span data-stu-id="af845-104">SDK downloads</span></span>

<span data-ttu-id="af845-105">Knihovny Azure pro .NET jsou implementované jako [balíčky NuGet](https://www.nuget.org/packages?q=windowsazureofficial).</span><span class="sxs-lookup"><span data-stu-id="af845-105">Azure libraries for .NET are implemented as [NuGet packages](https://www.nuget.org/packages?q=windowsazureofficial).</span></span> <span data-ttu-id="af845-106">Podívejte se na [referenční informace k rozhraní API](/dotnet/api/overview/azure/?view=azure-dotnet) pro referenční dokumentaci organizované službou Azure.</span><span class="sxs-lookup"><span data-stu-id="af845-106">See the [API Reference](/dotnet/api/overview/azure/?view=azure-dotnet) for reference documentation organized by Azure service.</span></span>

## <a name="development-tools"></a><span data-ttu-id="af845-107">Vývojářské nástroje</span><span class="sxs-lookup"><span data-stu-id="af845-107">Development tools</span></span>

<span data-ttu-id="af845-108">Visual Studio obsahuje nástroje pro řadu předdefinovaných služeb Azure.</span><span class="sxs-lookup"><span data-stu-id="af845-108">Visual Studio has tooling for many Azure services built-in.</span></span> <span data-ttu-id="af845-109">Některé služby Azure mají k dispozici další nástroje nebo emulátory, například [Průzkumník služby Azure Storage](https://azure.microsoft.com/features/storage-explorer/).</span><span class="sxs-lookup"><span data-stu-id="af845-109">Some Azure services have additional tools or emulators available, such as [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/).</span></span> <span data-ttu-id="af845-110">V případě potřeby si přečtěte dokumentaci ke službě Azure pro všechny další nástroje.</span><span class="sxs-lookup"><span data-stu-id="af845-110">See the documentation for your Azure service for any additional tools, if necessary.</span></span>

<span data-ttu-id="af845-111">Níže vyberte preferované vývojové prostředí.</span><span class="sxs-lookup"><span data-stu-id="af845-111">Select your preferred development environment below.</span></span>

## <a name="visual-studio-on-windows"></a>[<span data-ttu-id="af845-112">Visual Studio ve Windows</span><span class="sxs-lookup"><span data-stu-id="af845-112">Visual Studio on Windows</span></span>](#tab/vs)

<span data-ttu-id="af845-113">Visual Studio verze 2017 a novější má integrovanou podporu pro vývoj pro Azure.</span><span class="sxs-lookup"><span data-stu-id="af845-113">Visual Studio version 2017 and later have built-in support for Azure development.</span></span> <span data-ttu-id="af845-114">Níže uvedené kroky popisují povolení podpory vývoje Azure v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="af845-114">The below steps describe enabling Azure development support in Visual Studio.</span></span>

<span data-ttu-id="af845-115">V případě sady Visual Studio 2015 a starších verzí <a href="vs2015-install.md">postupujte podle těchto pokynů</a>.</span><span class="sxs-lookup"><span data-stu-id="af845-115">For Visual Studio 2015 and earlier, <a href="vs2015-install.md">follow these instructions</a>.</span></span>

### <a name="step-1-download-visual-studio-2019"></a><span data-ttu-id="af845-116">Krok 1: stažení sady Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="af845-116">Step 1: Download Visual Studio 2019</span></span>

<span data-ttu-id="af845-117">Pokud již máte nainstalováno Visual Studio 2019, můžete tento krok přeskočit.</span><span class="sxs-lookup"><span data-stu-id="af845-117">You can skip this step if you already have Visual Studio 2019 installed.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="af845-118">Stáhněte si Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="af845-118">Download Visual Studio 2019</span></span>](https://www.visualstudio.com/downloads/)

### <a name="step-2-install-the-two-azure-workloads"></a><span data-ttu-id="af845-119">Krok 2: instalace dvou úloh Azure</span><span class="sxs-lookup"><span data-stu-id="af845-119">Step 2: Install the two Azure workloads</span></span>

<span data-ttu-id="af845-120">V instalačním programu sady Visual Studio nainstalujte Visual Studio (nebo upravte existující instalaci).</span><span class="sxs-lookup"><span data-stu-id="af845-120">In the Visual Studio installer, install Visual Studio (or modify an existing installation).</span></span> <span data-ttu-id="af845-121">Ujistěte se, že jsou vybrané úlohy vývoje a *ASP.NET a* vývoj pro web *Azure* .</span><span class="sxs-lookup"><span data-stu-id="af845-121">Make sure the *Azure development* and *ASP.NET and web development* workloads are selected.</span></span>

### <a name="step-3-develop-with-net-on-azure"></a><span data-ttu-id="af845-122">Krok 3: vývoj s využitím .NET v Azure</span><span class="sxs-lookup"><span data-stu-id="af845-122">Step 3: Develop with .NET on Azure</span></span>

<span data-ttu-id="af845-123">Začněte [nasazením první ASP.NET Core webové aplikace v Azure App Service](/azure/app-service-web/app-service-web-get-started-dotnet).</span><span class="sxs-lookup"><span data-stu-id="af845-123">Get started by [deploying your first ASP.NET Core web app on Azure App Service](/azure/app-service-web/app-service-web-get-started-dotnet).</span></span>

## <a name="visual-studio-code-cross-platform"></a>[<span data-ttu-id="af845-124">Visual Studio Code (pro různé platformy)</span><span class="sxs-lookup"><span data-stu-id="af845-124">Visual Studio Code (cross-platform)</span></span>](#tab/vscode)

<span data-ttu-id="af845-125">Visual Studio Code má všechno, co potřebujete pro vývoj pro Azure na různých platformách.</span><span class="sxs-lookup"><span data-stu-id="af845-125">Visual Studio Code has everything you need for cross-platform Azure development.</span></span>

### <a name="step-1-download-the-net-core-sdk"></a><span data-ttu-id="af845-126">Krok 1: stažení .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="af845-126">Step 1: Download the .NET Core SDK</span></span>

<span data-ttu-id="af845-127">Sada SDK a nástroje příkazového řádku pro aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="af845-127">The SDK and command-line tools for .NET Core apps.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="af845-128">Stáhnout .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="af845-128">Download .NET Core SDK</span></span>](https://dotnet.microsoft.com/download)

### <a name="step-2-visual-studio-code"></a><span data-ttu-id="af845-129">Krok 2: Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="af845-129">Step 2: Visual Studio Code</span></span>

<span data-ttu-id="af845-130">Upravit a ladit aplikace .NET Core v jakémkoli operačním systému: Windows, Mac a Linux.</span><span class="sxs-lookup"><span data-stu-id="af845-130">Edit and debug .NET Core apps on any operating system: Windows, Mac, and Linux.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="af845-131">Stáhnout Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="af845-131">Download Visual Studio Code</span></span>](https://code.visualstudio.com)

### <a name="step-3-azure-tools-extension"></a><span data-ttu-id="af845-132">Krok 3: rozšíření nástrojů Azure</span><span class="sxs-lookup"><span data-stu-id="af845-132">Step 3: Azure Tools extension</span></span>

<span data-ttu-id="af845-133">Nainstalujte rozšíření Azure Tools v Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="af845-133">Install the Azure Tools extension in Visual Studio Code.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="af845-134">Nainstalovat rozšíření nástrojů Azure</span><span class="sxs-lookup"><span data-stu-id="af845-134">Install Azure Tools extension</span></span>](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack)

### <a name="step-4-develop-with-net-on-azure"></a><span data-ttu-id="af845-135">Krok 4: vývoj s využitím .NET v Azure</span><span class="sxs-lookup"><span data-stu-id="af845-135">Step 4: Develop with .NET on Azure</span></span>

<span data-ttu-id="af845-136">Začněte [nasazením první ASP.NET Core webové aplikace v Azure App Service v systému Linux](/azure/app-service/containers/quickstart-dotnetcore).</span><span class="sxs-lookup"><span data-stu-id="af845-136">Get started by [deploying your first ASP.NET Core web app on Azure App Service on Linux](/azure/app-service/containers/quickstart-dotnetcore).</span></span>

---
