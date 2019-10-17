---
ms.openlocfilehash: 959f3959c28c7d0159be7a213986345e2865b9a2
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394441"
---
### <a name="shared-framework-removed-microsoftaspnetcoreall"></a><span data-ttu-id="b7064-101">Sdílené rozhraní: odebrali jsme Microsoft. AspNetCore. All.</span><span class="sxs-lookup"><span data-stu-id="b7064-101">Shared framework: Removed Microsoft.AspNetCore.All</span></span>

<span data-ttu-id="b7064-102">Počínaje ASP.NET Core 3,0 se již nevyrábí `Microsoft.AspNetCore.All` Metapackage a porovnání `Microsoft.AspNetCore.All` sdílené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b7064-102">Starting in ASP.NET Core 3.0, the `Microsoft.AspNetCore.All` metapackage and the matching `Microsoft.AspNetCore.All` shared framework are no longer produced.</span></span> <span data-ttu-id="b7064-103">Tento balíček je k dispozici v ASP.NET Core 2,2 a bude nadále získávat aktualizace údržby v ASP.NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="b7064-103">This package is available in ASP.NET Core 2.2 and will continue to receive servicing updates in ASP.NET Core 2.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b7064-104">Představená verze</span><span class="sxs-lookup"><span data-stu-id="b7064-104">Version introduced</span></span>

<span data-ttu-id="b7064-105">3.0</span><span class="sxs-lookup"><span data-stu-id="b7064-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="b7064-106">Staré chování</span><span class="sxs-lookup"><span data-stu-id="b7064-106">Old behavior</span></span>

<span data-ttu-id="b7064-107">Aplikace můžou použít `Microsoft.AspNetCore.All` Metapackage k cílení na sdílenou architekturu `Microsoft.AspNetCore.All` v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b7064-107">Apps could use the `Microsoft.AspNetCore.All` metapackage to target the `Microsoft.AspNetCore.All` shared framework on .NET Core.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="b7064-108">Nové chování</span><span class="sxs-lookup"><span data-stu-id="b7064-108">New behavior</span></span>

<span data-ttu-id="b7064-109">.NET Core 3,0 neobsahuje sdílené rozhraní `Microsoft.AspNetCore.All`.</span><span class="sxs-lookup"><span data-stu-id="b7064-109">.NET Core 3.0 doesn't include a `Microsoft.AspNetCore.All` shared framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b7064-110">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="b7064-110">Reason for change</span></span>

<span data-ttu-id="b7064-111">@No__t-0 Metapackage zahrnoval velký počet externích závislostí.</span><span class="sxs-lookup"><span data-stu-id="b7064-111">The `Microsoft.AspNetCore.All` metapackage included a large number of external dependencies.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b7064-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="b7064-112">Recommended action</span></span>

<span data-ttu-id="b7064-113">Migrujte projekt tak, aby používal rozhraní `Microsoft.AspNetCore.App`.</span><span class="sxs-lookup"><span data-stu-id="b7064-113">Migrate your project to use the `Microsoft.AspNetCore.App` framework.</span></span> <span data-ttu-id="b7064-114">Komponenty, které byly dříve dostupné v `Microsoft.AspNetCore.All`, jsou stále k dispozici v NuGet.</span><span class="sxs-lookup"><span data-stu-id="b7064-114">Components that were previously available in `Microsoft.AspNetCore.All` are still available on NuGet.</span></span> <span data-ttu-id="b7064-115">Tyto komponenty se teď nasazují s vaší aplikací, takže se nezahrne do sdíleného rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b7064-115">Those components are now deployed with your app instead of being included in the shared framework.</span></span>

#### <a name="category"></a><span data-ttu-id="b7064-116">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b7064-116">Category</span></span>

<span data-ttu-id="b7064-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b7064-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b7064-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="b7064-118">Affected APIs</span></span>

<span data-ttu-id="b7064-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="b7064-119">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
