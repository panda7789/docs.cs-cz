---
ms.openlocfilehash: 51b3c1b3e3d61b23a0511ca807afef0269ac9ee4
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77466132"
---

<span data-ttu-id="d19f7-101">Balíčky přidané do kanálů správce balíčků jsou pojmenovány ve formátu zneužitelných: `{product}-{type}-{version}`.</span><span class="sxs-lookup"><span data-stu-id="d19f7-101">The packages added to the package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="d19f7-102">\ **produktu**</span><span class="sxs-lookup"><span data-stu-id="d19f7-102">**product**\</span></span>
<span data-ttu-id="d19f7-103">Typ produktu .NET, který se má nainstalovat</span><span class="sxs-lookup"><span data-stu-id="d19f7-103">The type of .NET product to install.</span></span> <span data-ttu-id="d19f7-104">Platné možnosti jsou:</span><span class="sxs-lookup"><span data-stu-id="d19f7-104">Valid options are:</span></span>

  - <span data-ttu-id="d19f7-105">DotNet</span><span class="sxs-lookup"><span data-stu-id="d19f7-105">dotnet</span></span>
  - <span data-ttu-id="d19f7-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="d19f7-106">aspnetcore</span></span>

- <span data-ttu-id="d19f7-107">**zadejte**</span><span class="sxs-lookup"><span data-stu-id="d19f7-107">**type**</span></span>\
<span data-ttu-id="d19f7-108">Zvolí sadu SDK nebo modul runtime.</span><span class="sxs-lookup"><span data-stu-id="d19f7-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="d19f7-109">Platné možnosti jsou:</span><span class="sxs-lookup"><span data-stu-id="d19f7-109">Valid options are:</span></span>

  - <span data-ttu-id="d19f7-110">SDK</span><span class="sxs-lookup"><span data-stu-id="d19f7-110">sdk</span></span>
  - <span data-ttu-id="d19f7-111">modul runtime</span><span class="sxs-lookup"><span data-stu-id="d19f7-111">runtime</span></span>

- <span data-ttu-id="d19f7-112">\ **verze**</span><span class="sxs-lookup"><span data-stu-id="d19f7-112">**version**\</span></span>
<span data-ttu-id="d19f7-113">Verze sady SDK nebo modulu runtime, která má být nainstalována.</span><span class="sxs-lookup"><span data-stu-id="d19f7-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="d19f7-114">V tomto článku se vždycky dostanou pokyny pro nejnovější podporovanou verzi.</span><span class="sxs-lookup"><span data-stu-id="d19f7-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="d19f7-115">Platné možnosti jsou všechny vydané verze, například:</span><span class="sxs-lookup"><span data-stu-id="d19f7-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="d19f7-116">3.1</span><span class="sxs-lookup"><span data-stu-id="d19f7-116">3.1</span></span>
  - <span data-ttu-id="d19f7-117">3.0</span><span class="sxs-lookup"><span data-stu-id="d19f7-117">3.0</span></span>
  - <span data-ttu-id="d19f7-118">2.1</span><span class="sxs-lookup"><span data-stu-id="d19f7-118">2.1</span></span>

  <span data-ttu-id="d19f7-119">Je možné, že sada SDK/modul runtime, kterou se pokoušíte stáhnout, není k dispozici pro distribuci systému Linux.</span><span class="sxs-lookup"><span data-stu-id="d19f7-119">It's possible the SDK/runtime you're trying to download is not available for your Linux distribution.</span></span> <span data-ttu-id="d19f7-120">Seznam podporovaných distribucí najdete v tématu [závislosti a požadavky .NET Core](../dependencies.md?pivots=os-linux).</span><span class="sxs-lookup"><span data-stu-id="d19f7-120">For a list of supported distributions, see [.NET Core dependencies and requirements](../dependencies.md?pivots=os-linux).</span></span>

### <a name="examples"></a><span data-ttu-id="d19f7-121">Příklady</span><span class="sxs-lookup"><span data-stu-id="d19f7-121">Examples</span></span>

- <span data-ttu-id="d19f7-122">Instalace modulu runtime ASP.NET Core 3,1: `aspnetcore-runtime-3.1`</span><span class="sxs-lookup"><span data-stu-id="d19f7-122">Install the ASP.NET Core 3.1 runtime: `aspnetcore-runtime-3.1`</span></span>
- <span data-ttu-id="d19f7-123">Instalace modulu runtime .NET Core 2,1: `dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="d19f7-123">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>
- <span data-ttu-id="d19f7-124">Instalace sady .NET Core 3,0 SDK: `dotnet-sdk-3.0`</span><span class="sxs-lookup"><span data-stu-id="d19f7-124">Install the .NET Core 3.0 SDK: `dotnet-sdk-3.0`</span></span>

### <a name="package-missing"></a><span data-ttu-id="d19f7-125">Chybějící balíček</span><span class="sxs-lookup"><span data-stu-id="d19f7-125">Package missing</span></span>

<span data-ttu-id="d19f7-126">Pokud kombinace verze balíčku nefunguje, není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="d19f7-126">If the package-version combination doesn't work, it's not available.</span></span> <span data-ttu-id="d19f7-127">Například sada SDK není ASP.NET Core, součásti sady SDK jsou součástí .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="d19f7-127">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="d19f7-128">Hodnota `aspnetcore-sdk-2.2` není správná a měla by být `dotnet-sdk-2.2`.</span><span class="sxs-lookup"><span data-stu-id="d19f7-128">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`.</span></span> <span data-ttu-id="d19f7-129">Seznam distribucí pro Linux podporovaných rozhraním .NET Core najdete v tématu [závislosti a požadavky .NET Core](../dependencies.md?pivots=os-linux).</span><span class="sxs-lookup"><span data-stu-id="d19f7-129">For a list of Linux distributions supported by .NET Core, see [.NET Core dependencies and requirements](../dependencies.md?pivots=os-linux).</span></span>
