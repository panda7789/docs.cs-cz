---
ms.openlocfilehash: 16b9fde49f513643a37f65f3e926a34fc991c55a
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394077"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a><span data-ttu-id="f3b83-101">Hostování: ObjectPoolProvider se odebral ze závislostí WebHostBuilder.</span><span class="sxs-lookup"><span data-stu-id="f3b83-101">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>

<span data-ttu-id="f3b83-102">V rámci zvýšení ASP.NET Core platíte za Play se `ObjectPoolProvider` odebral z hlavní sady závislostí.</span><span class="sxs-lookup"><span data-stu-id="f3b83-102">As part of making ASP.NET Core more pay for play, the `ObjectPoolProvider` was removed from the main set of dependencies.</span></span> <span data-ttu-id="f3b83-103">Konkrétní komponenty spoléhají na `ObjectPoolProvider` nyní přidat sami sebe.</span><span class="sxs-lookup"><span data-stu-id="f3b83-103">Specific components relying on `ObjectPoolProvider` now add it themselves.</span></span>

<span data-ttu-id="f3b83-104">Diskuzi najdete v tématu [ASPNET/AspNetCore # 5944](https://github.com/aspnet/AspNetCore/issues/5944).</span><span class="sxs-lookup"><span data-stu-id="f3b83-104">For discussion, see [aspnet/AspNetCore#5944](https://github.com/aspnet/AspNetCore/issues/5944).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f3b83-105">Představená verze</span><span class="sxs-lookup"><span data-stu-id="f3b83-105">Version introduced</span></span>

<span data-ttu-id="f3b83-106">3.0</span><span class="sxs-lookup"><span data-stu-id="f3b83-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="f3b83-107">Staré chování</span><span class="sxs-lookup"><span data-stu-id="f3b83-107">Old behavior</span></span>

<span data-ttu-id="f3b83-108">`WebHostBuilder` poskytuje ve výchozím nastavení `ObjectPoolProvider` v kontejneru DI.</span><span class="sxs-lookup"><span data-stu-id="f3b83-108">`WebHostBuilder` provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="f3b83-109">Nové chování</span><span class="sxs-lookup"><span data-stu-id="f3b83-109">New behavior</span></span>

<span data-ttu-id="f3b83-110">`WebHostBuilder` již ve výchozím nastavení v kontejneru DI neposkytuje `ObjectPoolProvider`.</span><span class="sxs-lookup"><span data-stu-id="f3b83-110">`WebHostBuilder` no longer provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f3b83-111">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="f3b83-111">Reason for change</span></span>

<span data-ttu-id="f3b83-112">Tato změna se provedla, aby se zajistilo ASP.NET Core více platíte za Play.</span><span class="sxs-lookup"><span data-stu-id="f3b83-112">This change was made to make ASP.NET Core more pay for play.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f3b83-113">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="f3b83-113">Recommended action</span></span>

<span data-ttu-id="f3b83-114">Pokud vaše komponenta vyžaduje `ObjectPoolProvider`, je nutné ji přidat k vašim závislostem prostřednictvím `IServiceCollection`.</span><span class="sxs-lookup"><span data-stu-id="f3b83-114">If your component requires `ObjectPoolProvider`, it needs to be added to your dependencies via the `IServiceCollection`.</span></span>

#### <a name="category"></a><span data-ttu-id="f3b83-115">Kategorie</span><span class="sxs-lookup"><span data-stu-id="f3b83-115">Category</span></span>

<span data-ttu-id="f3b83-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f3b83-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f3b83-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="f3b83-117">Affected APIs</span></span>

<span data-ttu-id="f3b83-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="f3b83-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
