---
ms.openlocfilehash: 4d99d0b6e99a7a9b976cf11832b33ad3bdc6d299
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901719"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a><span data-ttu-id="f1b64-101">Hostování: ObjectPoolProvider se odebral ze závislostí WebHostBuilder.</span><span class="sxs-lookup"><span data-stu-id="f1b64-101">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>

<span data-ttu-id="f1b64-102">V rámci zvýšení ASP.NET Core platíte za Play se `ObjectPoolProvider` odebral z hlavní sady závislostí.</span><span class="sxs-lookup"><span data-stu-id="f1b64-102">As part of making ASP.NET Core more pay for play, the `ObjectPoolProvider` was removed from the main set of dependencies.</span></span> <span data-ttu-id="f1b64-103">Konkrétní komponenty, které se spoléhají na `ObjectPoolProvider` nyní přidat sami sebe.</span><span class="sxs-lookup"><span data-stu-id="f1b64-103">Specific components relying on `ObjectPoolProvider` now add it themselves.</span></span>

<span data-ttu-id="f1b64-104">Diskuzi najdete v tématu [dotnet/aspnetcore # 5944](https://github.com/dotnet/aspnetcore/issues/5944).</span><span class="sxs-lookup"><span data-stu-id="f1b64-104">For discussion, see [dotnet/aspnetcore#5944](https://github.com/dotnet/aspnetcore/issues/5944).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f1b64-105">Představená verze</span><span class="sxs-lookup"><span data-stu-id="f1b64-105">Version introduced</span></span>

<span data-ttu-id="f1b64-106">3,0</span><span class="sxs-lookup"><span data-stu-id="f1b64-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="f1b64-107">Staré chování</span><span class="sxs-lookup"><span data-stu-id="f1b64-107">Old behavior</span></span>

<span data-ttu-id="f1b64-108">`WebHostBuilder` poskytuje `ObjectPoolProvider` ve výchozím nastavení v kontejneru DI.</span><span class="sxs-lookup"><span data-stu-id="f1b64-108">`WebHostBuilder` provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="f1b64-109">Nové chování</span><span class="sxs-lookup"><span data-stu-id="f1b64-109">New behavior</span></span>

<span data-ttu-id="f1b64-110">`WebHostBuilder` už v kontejneru DI neposkytuje `ObjectPoolProvider` ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="f1b64-110">`WebHostBuilder` no longer provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f1b64-111">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="f1b64-111">Reason for change</span></span>

<span data-ttu-id="f1b64-112">Tato změna se provedla, aby se zajistilo ASP.NET Core více platíte za Play.</span><span class="sxs-lookup"><span data-stu-id="f1b64-112">This change was made to make ASP.NET Core more pay for play.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f1b64-113">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="f1b64-113">Recommended action</span></span>

<span data-ttu-id="f1b64-114">Pokud vaše komponenta vyžaduje `ObjectPoolProvider`, je nutné ji přidat do svých závislostí prostřednictvím `IServiceCollection`.</span><span class="sxs-lookup"><span data-stu-id="f1b64-114">If your component requires `ObjectPoolProvider`, it needs to be added to your dependencies via the `IServiceCollection`.</span></span>

#### <a name="category"></a><span data-ttu-id="f1b64-115">Kategorie</span><span class="sxs-lookup"><span data-stu-id="f1b64-115">Category</span></span>

<span data-ttu-id="f1b64-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f1b64-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f1b64-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="f1b64-117">Affected APIs</span></span>

<span data-ttu-id="f1b64-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="f1b64-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
