---
ms.openlocfilehash: ef3e4f9f8145677732b9d2e66d416be277697f55
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920638"
---

<span data-ttu-id="71582-101">Balíčky přidané do kanálů správce balíčků jsou pojmenovány ve formátu zneužitelných: `{product}-{type}-{version}`.</span><span class="sxs-lookup"><span data-stu-id="71582-101">The packages added to the package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="71582-102">\ **produktu**</span><span class="sxs-lookup"><span data-stu-id="71582-102">**product**\</span></span>
<span data-ttu-id="71582-103">Typ produktu .NET, který se má nainstalovat</span><span class="sxs-lookup"><span data-stu-id="71582-103">The type of .NET product to install.</span></span> <span data-ttu-id="71582-104">Platné možnosti jsou:</span><span class="sxs-lookup"><span data-stu-id="71582-104">Valid options are:</span></span>

  - <span data-ttu-id="71582-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="71582-105">dotnet</span></span>
  - <span data-ttu-id="71582-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="71582-106">aspnetcore</span></span>

- <span data-ttu-id="71582-107">**zadejte**</span><span class="sxs-lookup"><span data-stu-id="71582-107">**type**</span></span>\
<span data-ttu-id="71582-108">Zvolí sadu SDK nebo modul runtime.</span><span class="sxs-lookup"><span data-stu-id="71582-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="71582-109">Platné možnosti jsou:</span><span class="sxs-lookup"><span data-stu-id="71582-109">Valid options are:</span></span>

  - <span data-ttu-id="71582-110">sdk</span><span class="sxs-lookup"><span data-stu-id="71582-110">sdk</span></span>
  - <span data-ttu-id="71582-111">modul runtime</span><span class="sxs-lookup"><span data-stu-id="71582-111">runtime</span></span>

- <span data-ttu-id="71582-112">\ **verze**</span><span class="sxs-lookup"><span data-stu-id="71582-112">**version**\</span></span>
<span data-ttu-id="71582-113">Verze sady SDK nebo modulu runtime, která má být nainstalována.</span><span class="sxs-lookup"><span data-stu-id="71582-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="71582-114">V tomto článku se vždycky dostanou pokyny pro nejnovější podporovanou verzi.</span><span class="sxs-lookup"><span data-stu-id="71582-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="71582-115">Platné možnosti jsou všechny vydané verze, například:</span><span class="sxs-lookup"><span data-stu-id="71582-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="71582-116">3,0</span><span class="sxs-lookup"><span data-stu-id="71582-116">3.0</span></span>
  - <span data-ttu-id="71582-117">2.2</span><span class="sxs-lookup"><span data-stu-id="71582-117">2.2</span></span>
  - <span data-ttu-id="71582-118">2.1</span><span class="sxs-lookup"><span data-stu-id="71582-118">2.1</span></span>

### <a name="examples"></a><span data-ttu-id="71582-119">Příklady</span><span class="sxs-lookup"><span data-stu-id="71582-119">Examples</span></span>

- <span data-ttu-id="71582-120">Instalace sady .NET Core 2,2 SDK: `dotnet-sdk-2.2`</span><span class="sxs-lookup"><span data-stu-id="71582-120">Install the .NET Core 2.2 SDK: `dotnet-sdk-2.2`</span></span>
- <span data-ttu-id="71582-121">Instalace modulu runtime ASP.NET Core 3,1: `aspnetcore-runtime-3.1`</span><span class="sxs-lookup"><span data-stu-id="71582-121">Install the ASP.NET Core 3.1 runtime: `aspnetcore-runtime-3.1`</span></span>
- <span data-ttu-id="71582-122">Instalace modulu runtime .NET Core 2,1: `dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="71582-122">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>

### <a name="package-missing"></a><span data-ttu-id="71582-123">Chybějící balíček</span><span class="sxs-lookup"><span data-stu-id="71582-123">Package missing</span></span>

<span data-ttu-id="71582-124">Pokud kombinace verze balíčku nefunguje, není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="71582-124">If the package-version combination doesn't work, it's not available.</span></span> <span data-ttu-id="71582-125">Například sada SDK není ASP.NET Core, součásti sady SDK jsou součástí .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="71582-125">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="71582-126">Hodnota `aspnetcore-sdk-2.2` není správná a měla by být `dotnet-sdk-2.2`.</span><span class="sxs-lookup"><span data-stu-id="71582-126">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`.</span></span>
