---
title: Nástroje pro vývojáře v Azure .NET a .NET Core
description: Získejte nástroje pro zahájení používání knihoven Azure .NET z prostředí Windows, Linux a Mac.
ms.date: 10/01/2018
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: 1c6370e4b3e5e6e901ba6ef56c65d794f3da5abe
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2020
ms.locfileid: "82071939"
---
# <a name="tools-for-net-and-net-core-azure-developers"></a><span data-ttu-id="6632a-103">Nástroje pro vývojáře na platformě Azure pro .NET a .NET Core</span><span class="sxs-lookup"><span data-stu-id="6632a-103">Tools for .NET and .NET Core Azure developers</span></span>

## <a name="sdk-downloads"></a><span data-ttu-id="6632a-104">Soubory sady SDK ke stažení</span><span class="sxs-lookup"><span data-stu-id="6632a-104">SDK downloads</span></span>

<span data-ttu-id="6632a-105">Knihovny Azure pro .NET jsou implementované jako [balíčky NuGet](https://www.nuget.org/packages?q=windowsazureofficial).</span><span class="sxs-lookup"><span data-stu-id="6632a-105">Azure libraries for .NET are implemented as [NuGet packages](https://www.nuget.org/packages?q=windowsazureofficial).</span></span> <span data-ttu-id="6632a-106">Pokyny k instalaci uspořádané podle služby Azure najdete v [referenčních informacích k rozhraní API](/dotnet/api/overview/azure/?view=azure-dotnet) .</span><span class="sxs-lookup"><span data-stu-id="6632a-106">See the [API Reference](/dotnet/api/overview/azure/?view=azure-dotnet) for installation instructions organized by Azure service.</span></span>

## <a name="development-tools"></a><span data-ttu-id="6632a-107">Vývojářské nástroje</span><span class="sxs-lookup"><span data-stu-id="6632a-107">Development tools</span></span>

<span data-ttu-id="6632a-108">Visual Studio obsahuje nástroje pro řadu předdefinovaných služeb Azure.</span><span class="sxs-lookup"><span data-stu-id="6632a-108">Visual Studio has tooling for many Azure services built-in.</span></span> <span data-ttu-id="6632a-109">Některé služby Azure mají k dispozici další nástroje nebo emulátory, například [Průzkumník služby Azure Storage](https://azure.microsoft.com/features/storage-explorer/).</span><span class="sxs-lookup"><span data-stu-id="6632a-109">Some Azure services have additional tools or emulators available, such as [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/).</span></span> <span data-ttu-id="6632a-110">V případě potřeby si přečtěte dokumentaci ke službě Azure pro všechny další nástroje.</span><span class="sxs-lookup"><span data-stu-id="6632a-110">See the documentation for your Azure service for any additional tools, if necessary.</span></span>

<span data-ttu-id="6632a-111">Tyto pokyny nainstalují Doporučené počáteční vývojové prostředí pro váš operační systém.</span><span class="sxs-lookup"><span data-stu-id="6632a-111">These instructions install the recommended starting development environment for your operating system.</span></span>

## <a name="windows"></a>[<span data-ttu-id="6632a-112">Windows</span><span class="sxs-lookup"><span data-stu-id="6632a-112">Windows</span></span>](#tab/windows)

<span data-ttu-id="6632a-113">Visual Studio verze 2017 a novější mají integrovanou podporu pro vývoj pro Azure.</span><span class="sxs-lookup"><span data-stu-id="6632a-113">Visual Studio versions 2017 and later have built-in support for Azure development.</span></span> <span data-ttu-id="6632a-114">Níže uvedené kroky popisují povolení podpory vývoje Azure v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6632a-114">The below steps describe enabling Azure development support in Visual Studio.</span></span>

<span data-ttu-id="6632a-115">V případě sady Visual Studio 2015 a starších verzí <a href="vs2015-install.md">postupujte podle těchto pokynů</a>.</span><span class="sxs-lookup"><span data-stu-id="6632a-115">For Visual Studio 2015 and earlier, <a href="vs2015-install.md">follow these instructions</a>.</span></span>

### <a name="step-1-download-visual-studio-2019"></a><span data-ttu-id="6632a-116">Krok 1: stažení sady Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="6632a-116">Step 1: Download Visual Studio 2019</span></span>

<span data-ttu-id="6632a-117">Pokud již máte nainstalováno Visual Studio 2019, můžete tento krok přeskočit.</span><span class="sxs-lookup"><span data-stu-id="6632a-117">You can skip this step if you already have Visual Studio 2019 installed.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6632a-118">Stáhněte si Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="6632a-118">Download Visual Studio 2019</span></span>](https://www.visualstudio.com/downloads/)

### <a name="step-2-install-the-two-azure-workloads"></a><span data-ttu-id="6632a-119">Krok 2: instalace dvou úloh Azure</span><span class="sxs-lookup"><span data-stu-id="6632a-119">Step 2: Install the two Azure workloads</span></span>

<span data-ttu-id="6632a-120">V instalačním programu sady Visual Studio nainstalujte Visual Studio (nebo upravte existující instalaci).</span><span class="sxs-lookup"><span data-stu-id="6632a-120">In the Visual Studio installer, install Visual Studio (or modify an existing installation).</span></span> <span data-ttu-id="6632a-121">Ujistěte se, že jsou vybrané úlohy vývoje a *ASP.NET a* vývoj pro web *Azure* .</span><span class="sxs-lookup"><span data-stu-id="6632a-121">Make sure the *Azure development* and *ASP.NET and web development* workloads are selected.</span></span>

### <a name="step-3-develop-with-net-on-azure"></a><span data-ttu-id="6632a-122">Krok 3: vývoj s využitím .NET v Azure</span><span class="sxs-lookup"><span data-stu-id="6632a-122">Step 3: Develop with .NET on Azure</span></span>

<span data-ttu-id="6632a-123">Začněte [nasazením první ASP.NET Core webové aplikace v Azure App Service](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-dotnet).</span><span class="sxs-lookup"><span data-stu-id="6632a-123">Get started by [deploying your first ASP.NET Core web app on Azure App Service](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-dotnet).</span></span>

## <a name="macos"></a>[<span data-ttu-id="6632a-124">macOS</span><span class="sxs-lookup"><span data-stu-id="6632a-124">macOS</span></span>](#tab/macos)

<span data-ttu-id="6632a-125">Visual Studio pro Mac má všechno, co potřebujete pro vývoj pro Azure.</span><span class="sxs-lookup"><span data-stu-id="6632a-125">Visual Studio for Mac has everything you need for Azure development.</span></span>

### <a name="step-1-download-visual-studio-for-mac"></a><span data-ttu-id="6632a-126">Krok 1: stažení Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="6632a-126">Step 1: Download Visual Studio for Mac</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6632a-127">Stáhnout Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="6632a-127">Download Visual Studio for Mac</span></span>](https://www.visualstudio.com/vs/visual-studio-mac/)

<span data-ttu-id="6632a-128">Během instalace jsou ve výchozím nastavení vybrané nástroje Azure.</span><span class="sxs-lookup"><span data-stu-id="6632a-128">During installation, Azure tools are selected by default.</span></span>

## <a name="linux"></a>[<span data-ttu-id="6632a-129">Linux</span><span class="sxs-lookup"><span data-stu-id="6632a-129">Linux</span></span>](#tab/linux)

<span data-ttu-id="6632a-130">Visual Studio Code má vše, co potřebujete pro vývoj pro Azure v systému Linux.</span><span class="sxs-lookup"><span data-stu-id="6632a-130">Visual Studio Code has everything you need for Azure development on Linux.</span></span>

### <a name="step-1-download-the-net-core-sdk"></a><span data-ttu-id="6632a-131">Krok 1: stažení .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="6632a-131">Step 1: Download the .NET Core SDK</span></span>

<span data-ttu-id="6632a-132">Sada SDK a nástroje příkazového řádku pro aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="6632a-132">The SDK and command-line tools for .NET Core apps.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6632a-133">Stáhnout .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="6632a-133">Download .NET Core SDK</span></span>](https://dotnet.microsoft.com/download)

### <a name="step-2-visual-studio-code"></a><span data-ttu-id="6632a-134">Krok 2: Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="6632a-134">Step 2: Visual Studio Code</span></span>

<span data-ttu-id="6632a-135">Upravit a ladit aplikace .NET Core v jakémkoli operačním systému: Windows, Mac a Linux.</span><span class="sxs-lookup"><span data-stu-id="6632a-135">Edit and debug .NET Core apps on any operating system: Windows, Mac, and Linux.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6632a-136">Stáhnout Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="6632a-136">Download Visual Studio Code</span></span>](https://code.visualstudio.com)

---
