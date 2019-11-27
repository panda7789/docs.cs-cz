---
ms.openlocfilehash: 7a55641b3673dc4d8d9b328f0de99b7247ca51d4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450882"
---

<span data-ttu-id="89db1-101">Balíčky přidané do kanálů správce balíčků jsou pojmenovány ve formátu zneužitelných: `{product}-{type}-{version}`.</span><span class="sxs-lookup"><span data-stu-id="89db1-101">The packages added to the package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="89db1-102">\ **produktu**</span><span class="sxs-lookup"><span data-stu-id="89db1-102">**product**\</span></span>
<span data-ttu-id="89db1-103">Typ produktu .NET, který se má nainstalovat</span><span class="sxs-lookup"><span data-stu-id="89db1-103">The type of .NET product to install.</span></span> <span data-ttu-id="89db1-104">Platné možnosti jsou:</span><span class="sxs-lookup"><span data-stu-id="89db1-104">Valid options are:</span></span>

  - <span data-ttu-id="89db1-105">DotNet</span><span class="sxs-lookup"><span data-stu-id="89db1-105">dotnet</span></span>
  - <span data-ttu-id="89db1-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="89db1-106">aspnetcore</span></span>

- <span data-ttu-id="89db1-107">**zadejte**</span><span class="sxs-lookup"><span data-stu-id="89db1-107">**type**</span></span>\
<span data-ttu-id="89db1-108">Zvolí sadu SDK nebo modul runtime.</span><span class="sxs-lookup"><span data-stu-id="89db1-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="89db1-109">Platné možnosti jsou:</span><span class="sxs-lookup"><span data-stu-id="89db1-109">Valid options are:</span></span>

  - <span data-ttu-id="89db1-110">sdk</span><span class="sxs-lookup"><span data-stu-id="89db1-110">sdk</span></span>
  - <span data-ttu-id="89db1-111">modul runtime</span><span class="sxs-lookup"><span data-stu-id="89db1-111">runtime</span></span>

- <span data-ttu-id="89db1-112">\ **verze**</span><span class="sxs-lookup"><span data-stu-id="89db1-112">**version**\</span></span>
<span data-ttu-id="89db1-113">Verze sady SDK nebo modulu runtime, která má být nainstalována.</span><span class="sxs-lookup"><span data-stu-id="89db1-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="89db1-114">V tomto článku se vždycky dostanou pokyny pro nejnovější podporovanou verzi.</span><span class="sxs-lookup"><span data-stu-id="89db1-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="89db1-115">Platné možnosti jsou všechny vydané verze, například:</span><span class="sxs-lookup"><span data-stu-id="89db1-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="89db1-116">3,0</span><span class="sxs-lookup"><span data-stu-id="89db1-116">3.0</span></span>
  - <span data-ttu-id="89db1-117">2.2</span><span class="sxs-lookup"><span data-stu-id="89db1-117">2.2</span></span>
  - <span data-ttu-id="89db1-118">2.1</span><span class="sxs-lookup"><span data-stu-id="89db1-118">2.1</span></span>

### <a name="examples"></a><span data-ttu-id="89db1-119">Příklady</span><span class="sxs-lookup"><span data-stu-id="89db1-119">Examples</span></span>

- <span data-ttu-id="89db1-120">Instalace sady .NET Core 2,2 SDK: `dotnet-sdk-2.2`</span><span class="sxs-lookup"><span data-stu-id="89db1-120">Install the .NET Core 2.2 SDK: `dotnet-sdk-2.2`</span></span>
- <span data-ttu-id="89db1-121">Instalace modulu runtime ASP.NET Core 3,0: `aspnetcore-runtime-3.0`</span><span class="sxs-lookup"><span data-stu-id="89db1-121">Install the ASP.NET Core 3.0 runtime: `aspnetcore-runtime-3.0`</span></span>
- <span data-ttu-id="89db1-122">Instalace modulu runtime .NET Core 2,1: `dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="89db1-122">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>

### <a name="troubleshoot"></a><span data-ttu-id="89db1-123">Řešení problémů</span><span class="sxs-lookup"><span data-stu-id="89db1-123">Troubleshoot</span></span>

<span data-ttu-id="89db1-124">Pokud kombinace balíčku nefunguje, není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="89db1-124">If the package combination doesn't work, it's not available.</span></span> <span data-ttu-id="89db1-125">Například sada SDK není ASP.NET Core, součásti sady SDK jsou součástí .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="89db1-125">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="89db1-126">Hodnota `aspnetcore-sdk-2.2` není správná a měla by být `dotnet-sdk-2.2`</span><span class="sxs-lookup"><span data-stu-id="89db1-126">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`</span></span>
