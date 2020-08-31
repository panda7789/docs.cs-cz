---
ms.openlocfilehash: 7723892a33bf7dd8e475b2f696db5d9ab287e182
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602990"
---

<span data-ttu-id="259d6-101">Balíčky přidané do kanálů správce balíčků jsou pojmenovány ve formátu zneužitelných: `{product}-{type}-{version}` .</span><span class="sxs-lookup"><span data-stu-id="259d6-101">The packages added to package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="259d6-102">**produktu**</span><span class="sxs-lookup"><span data-stu-id="259d6-102">**product**</span></span>\
<span data-ttu-id="259d6-103">Typ produktu .NET, který se má nainstalovat</span><span class="sxs-lookup"><span data-stu-id="259d6-103">The type of .NET product to install.</span></span> <span data-ttu-id="259d6-104">Platné možnosti jsou:</span><span class="sxs-lookup"><span data-stu-id="259d6-104">Valid options are:</span></span>

  - <span data-ttu-id="259d6-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="259d6-105">dotnet</span></span>
  - <span data-ttu-id="259d6-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="259d6-106">aspnetcore</span></span>

- <span data-ttu-id="259d6-107">**textový**</span><span class="sxs-lookup"><span data-stu-id="259d6-107">**type**</span></span>\
<span data-ttu-id="259d6-108">Zvolí sadu SDK nebo modul runtime.</span><span class="sxs-lookup"><span data-stu-id="259d6-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="259d6-109">Platné možnosti jsou:</span><span class="sxs-lookup"><span data-stu-id="259d6-109">Valid options are:</span></span>

  - <span data-ttu-id="259d6-110">SDK</span><span class="sxs-lookup"><span data-stu-id="259d6-110">sdk</span></span>
  - <span data-ttu-id="259d6-111">modul runtime</span><span class="sxs-lookup"><span data-stu-id="259d6-111">runtime</span></span>

- <span data-ttu-id="259d6-112">**znění**</span><span class="sxs-lookup"><span data-stu-id="259d6-112">**version**</span></span>\
<span data-ttu-id="259d6-113">Verze sady SDK nebo modulu runtime, která má být nainstalována.</span><span class="sxs-lookup"><span data-stu-id="259d6-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="259d6-114">V tomto článku se vždycky dostanou pokyny pro nejnovější podporovanou verzi.</span><span class="sxs-lookup"><span data-stu-id="259d6-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="259d6-115">Platné možnosti jsou všechny vydané verze, například:</span><span class="sxs-lookup"><span data-stu-id="259d6-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="259d6-116">3.1</span><span class="sxs-lookup"><span data-stu-id="259d6-116">3.1</span></span>
  - <span data-ttu-id="259d6-117">3,0</span><span class="sxs-lookup"><span data-stu-id="259d6-117">3.0</span></span>
  - <span data-ttu-id="259d6-118">2.1</span><span class="sxs-lookup"><span data-stu-id="259d6-118">2.1</span></span>

  <span data-ttu-id="259d6-119">Je možné, že sada SDK/modul runtime, kterou se pokoušíte stáhnout, není k dispozici pro distribuci systému Linux.</span><span class="sxs-lookup"><span data-stu-id="259d6-119">It's possible the SDK/runtime you're trying to download is not available for your Linux distribution.</span></span> <span data-ttu-id="259d6-120">Seznam podporovaných distribucí najdete v tématu [závislosti a požadavky .NET Core](../linux.md).</span><span class="sxs-lookup"><span data-stu-id="259d6-120">For a list of supported distributions, see [.NET Core dependencies and requirements](../linux.md).</span></span>

### <a name="examples"></a><span data-ttu-id="259d6-121">Příklady</span><span class="sxs-lookup"><span data-stu-id="259d6-121">Examples</span></span>

- <span data-ttu-id="259d6-122">Instalace modulu runtime ASP.NET Core 3,1: `aspnetcore-runtime-3.1`</span><span class="sxs-lookup"><span data-stu-id="259d6-122">Install the ASP.NET Core 3.1 runtime: `aspnetcore-runtime-3.1`</span></span>
- <span data-ttu-id="259d6-123">Nainstalujte modul runtime .NET Core 2,1: `dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="259d6-123">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>
- <span data-ttu-id="259d6-124">Nainstalujte sadu .NET Core 3,1 SDK: `dotnet-sdk-3.1`</span><span class="sxs-lookup"><span data-stu-id="259d6-124">Install the .NET Core 3.1 SDK: `dotnet-sdk-3.1`</span></span>

### <a name="package-missing"></a><span data-ttu-id="259d6-125">Chybějící balíček</span><span class="sxs-lookup"><span data-stu-id="259d6-125">Package missing</span></span>

<span data-ttu-id="259d6-126">Pokud kombinace verze balíčku nefunguje, není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="259d6-126">If the package-version combination doesn't work, it's not available.</span></span> <span data-ttu-id="259d6-127">Například sada SDK není ASP.NET Core, součásti sady SDK jsou součástí .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="259d6-127">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="259d6-128">Hodnota `aspnetcore-sdk-2.2` je nesprávná a měla by být `dotnet-sdk-2.2` .</span><span class="sxs-lookup"><span data-stu-id="259d6-128">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`.</span></span> <span data-ttu-id="259d6-129">Seznam distribucí pro Linux podporovaných rozhraním .NET Core najdete v tématu [závislosti a požadavky .NET Core](../linux.md).</span><span class="sxs-lookup"><span data-stu-id="259d6-129">For a list of Linux distributions supported by .NET Core, see [.NET Core dependencies and requirements](../linux.md).</span></span>
