---
ms.openlocfilehash: 4340ed7444681b4601dea50c93926b0ee0c07eec
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134114"
---

<span data-ttu-id="e3720-101">Balíčky přidané do informačních kanálů správce balíčků jsou `{product}-{type}-{version}`pojmenovány v hackovatelném formátu: .</span><span class="sxs-lookup"><span data-stu-id="e3720-101">The packages added to the package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="e3720-102">**Produktu**</span><span class="sxs-lookup"><span data-stu-id="e3720-102">**product**</span></span>\
<span data-ttu-id="e3720-103">Typ produktu .NET k instalaci.</span><span class="sxs-lookup"><span data-stu-id="e3720-103">The type of .NET product to install.</span></span> <span data-ttu-id="e3720-104">Platné možnosti jsou:</span><span class="sxs-lookup"><span data-stu-id="e3720-104">Valid options are:</span></span>

  - <span data-ttu-id="e3720-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="e3720-105">dotnet</span></span>
  - <span data-ttu-id="e3720-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="e3720-106">aspnetcore</span></span>

- <span data-ttu-id="e3720-107">**Typ**</span><span class="sxs-lookup"><span data-stu-id="e3720-107">**type**</span></span>\
<span data-ttu-id="e3720-108">Vybere sadu SDK nebo runtime.</span><span class="sxs-lookup"><span data-stu-id="e3720-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="e3720-109">Platné možnosti jsou:</span><span class="sxs-lookup"><span data-stu-id="e3720-109">Valid options are:</span></span>

  - <span data-ttu-id="e3720-110">SDK</span><span class="sxs-lookup"><span data-stu-id="e3720-110">sdk</span></span>
  - <span data-ttu-id="e3720-111">modul runtime</span><span class="sxs-lookup"><span data-stu-id="e3720-111">runtime</span></span>

- <span data-ttu-id="e3720-112">**Verze**</span><span class="sxs-lookup"><span data-stu-id="e3720-112">**version**</span></span>\
<span data-ttu-id="e3720-113">Verze sady SDK nebo runtime k instalaci.</span><span class="sxs-lookup"><span data-stu-id="e3720-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="e3720-114">Tento článek bude vždy dávat pokyny pro nejnovější podporovanou verzi.</span><span class="sxs-lookup"><span data-stu-id="e3720-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="e3720-115">Platné možnosti jsou všechny vydané verze, například:</span><span class="sxs-lookup"><span data-stu-id="e3720-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="e3720-116">3.1</span><span class="sxs-lookup"><span data-stu-id="e3720-116">3.1</span></span>
  - <span data-ttu-id="e3720-117">3.0</span><span class="sxs-lookup"><span data-stu-id="e3720-117">3.0</span></span>
  - <span data-ttu-id="e3720-118">2.1</span><span class="sxs-lookup"><span data-stu-id="e3720-118">2.1</span></span>

  <span data-ttu-id="e3720-119">Je možné, že sada SDK/runtime, kterou se pokoušíte stáhnout, není k dispozici pro distribuci Linuxu.</span><span class="sxs-lookup"><span data-stu-id="e3720-119">It's possible the SDK/runtime you're trying to download is not available for your Linux distribution.</span></span> <span data-ttu-id="e3720-120">Seznam podporovaných distribucí naleznete [v tématu .NET Core závislosti a požadavky](../dependencies.md?pivots=os-linux).</span><span class="sxs-lookup"><span data-stu-id="e3720-120">For a list of supported distributions, see [.NET Core dependencies and requirements](../dependencies.md?pivots=os-linux).</span></span>

### <a name="examples"></a><span data-ttu-id="e3720-121">Příklady</span><span class="sxs-lookup"><span data-stu-id="e3720-121">Examples</span></span>

- <span data-ttu-id="e3720-122">Nainstalujte ASP.NET core 3.1 runtime:`aspnetcore-runtime-3.1`</span><span class="sxs-lookup"><span data-stu-id="e3720-122">Install the ASP.NET Core 3.1 runtime: `aspnetcore-runtime-3.1`</span></span>
- <span data-ttu-id="e3720-123">Nainstalujte runtime .NET Core 2.1:`dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="e3720-123">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>
- <span data-ttu-id="e3720-124">Nainstalujte sdk .NET Core 3.1:`dotnet-sdk-3.1`</span><span class="sxs-lookup"><span data-stu-id="e3720-124">Install the .NET Core 3.1 SDK: `dotnet-sdk-3.1`</span></span>

### <a name="package-missing"></a><span data-ttu-id="e3720-125">Balíček chybí.</span><span class="sxs-lookup"><span data-stu-id="e3720-125">Package missing</span></span>

<span data-ttu-id="e3720-126">Pokud kombinace verze balíčku nefunguje, není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="e3720-126">If the package-version combination doesn't work, it's not available.</span></span> <span data-ttu-id="e3720-127">Například neexistuje ASP.NET core sdk, součásti Sady SDK jsou součástí sady .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="e3720-127">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="e3720-128">Hodnota `aspnetcore-sdk-2.2` je nesprávná `dotnet-sdk-2.2`a měla by být .</span><span class="sxs-lookup"><span data-stu-id="e3720-128">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`.</span></span> <span data-ttu-id="e3720-129">Seznam linuxových distribucí podporovaných rozhraním .NET Core naleznete v [tématu .NET Core závislostí a požadavků](../dependencies.md?pivots=os-linux).</span><span class="sxs-lookup"><span data-stu-id="e3720-129">For a list of Linux distributions supported by .NET Core, see [.NET Core dependencies and requirements](../dependencies.md?pivots=os-linux).</span></span>
