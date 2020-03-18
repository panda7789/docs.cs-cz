---
ms.openlocfilehash: 4d99d0b6e99a7a9b976cf11832b33ad3bdc6d299
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901719"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a><span data-ttu-id="d157c-101">Hostování: Objekt Usvého zprostředkovatele objectpoolu odebrán ze závislostí WebHostBuilder</span><span class="sxs-lookup"><span data-stu-id="d157c-101">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>

<span data-ttu-id="d157c-102">Jako součást toho, ASP.NET Core více `ObjectPoolProvider` platit za hru, byl odstraněn z hlavní sady závislostí.</span><span class="sxs-lookup"><span data-stu-id="d157c-102">As part of making ASP.NET Core more pay for play, the `ObjectPoolProvider` was removed from the main set of dependencies.</span></span> <span data-ttu-id="d157c-103">Konkrétní součásti, `ObjectPoolProvider` na které se spoléhají, nyní přidávají sami.</span><span class="sxs-lookup"><span data-stu-id="d157c-103">Specific components relying on `ObjectPoolProvider` now add it themselves.</span></span>

<span data-ttu-id="d157c-104">Diskuse naleznete [v tématu dotnet/aspnetcore#5944](https://github.com/dotnet/aspnetcore/issues/5944).</span><span class="sxs-lookup"><span data-stu-id="d157c-104">For discussion, see [dotnet/aspnetcore#5944](https://github.com/dotnet/aspnetcore/issues/5944).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d157c-105">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="d157c-105">Version introduced</span></span>

<span data-ttu-id="d157c-106">3.0</span><span class="sxs-lookup"><span data-stu-id="d157c-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d157c-107">Staré chování</span><span class="sxs-lookup"><span data-stu-id="d157c-107">Old behavior</span></span>

<span data-ttu-id="d157c-108">`WebHostBuilder`poskytuje `ObjectPoolProvider` ve výchozím nastavení v kontejneru DI.</span><span class="sxs-lookup"><span data-stu-id="d157c-108">`WebHostBuilder` provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d157c-109">Nové chování</span><span class="sxs-lookup"><span data-stu-id="d157c-109">New behavior</span></span>

<span data-ttu-id="d157c-110">`WebHostBuilder`již poskytuje `ObjectPoolProvider` ve výchozím nastavení v kontejneru DI.</span><span class="sxs-lookup"><span data-stu-id="d157c-110">`WebHostBuilder` no longer provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d157c-111">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="d157c-111">Reason for change</span></span>

<span data-ttu-id="d157c-112">Tato změna byla provedena, aby se ASP.NET Core více platit za hru.</span><span class="sxs-lookup"><span data-stu-id="d157c-112">This change was made to make ASP.NET Core more pay for play.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d157c-113">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="d157c-113">Recommended action</span></span>

<span data-ttu-id="d157c-114">Pokud vaše `ObjectPoolProvider`komponenta vyžaduje , je třeba přidat `IServiceCollection`do vašich závislostí prostřednictvím .</span><span class="sxs-lookup"><span data-stu-id="d157c-114">If your component requires `ObjectPoolProvider`, it needs to be added to your dependencies via the `IServiceCollection`.</span></span>

#### <a name="category"></a><span data-ttu-id="d157c-115">Kategorie</span><span class="sxs-lookup"><span data-stu-id="d157c-115">Category</span></span>

<span data-ttu-id="d157c-116">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d157c-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d157c-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="d157c-117">Affected APIs</span></span>

<span data-ttu-id="d157c-118">Žádný</span><span class="sxs-lookup"><span data-stu-id="d157c-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
