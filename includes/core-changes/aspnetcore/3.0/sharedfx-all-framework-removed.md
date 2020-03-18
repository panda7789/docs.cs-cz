---
ms.openlocfilehash: 959f3959c28c7d0159be7a213986345e2865b9a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394441"
---
### <a name="shared-framework-removed-microsoftaspnetcoreall"></a><span data-ttu-id="0f2a3-101">Sdílený rámec: Odebránmicrosoft.AspNetCore.All</span><span class="sxs-lookup"><span data-stu-id="0f2a3-101">Shared framework: Removed Microsoft.AspNetCore.All</span></span>

<span data-ttu-id="0f2a3-102">Počínaje ASP.NET jádrem 3.0, `Microsoft.AspNetCore.All` metabalíček a odpovídající `Microsoft.AspNetCore.All` sdílené rozhraní jsou již vyrábí.</span><span class="sxs-lookup"><span data-stu-id="0f2a3-102">Starting in ASP.NET Core 3.0, the `Microsoft.AspNetCore.All` metapackage and the matching `Microsoft.AspNetCore.All` shared framework are no longer produced.</span></span> <span data-ttu-id="0f2a3-103">Tento balíček je k dispozici v ASP.NET Core 2.2 a bude i nadále dostávat aktualizace údržby v ASP.NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="0f2a3-103">This package is available in ASP.NET Core 2.2 and will continue to receive servicing updates in ASP.NET Core 2.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0f2a3-104">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="0f2a3-104">Version introduced</span></span>

<span data-ttu-id="0f2a3-105">3.0</span><span class="sxs-lookup"><span data-stu-id="0f2a3-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="0f2a3-106">Staré chování</span><span class="sxs-lookup"><span data-stu-id="0f2a3-106">Old behavior</span></span>

<span data-ttu-id="0f2a3-107">Aplikace mohou `Microsoft.AspNetCore.All` metabalíček použít `Microsoft.AspNetCore.All` k cílení na sdílený rámec na rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0f2a3-107">Apps could use the `Microsoft.AspNetCore.All` metapackage to target the `Microsoft.AspNetCore.All` shared framework on .NET Core.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="0f2a3-108">Nové chování</span><span class="sxs-lookup"><span data-stu-id="0f2a3-108">New behavior</span></span>

<span data-ttu-id="0f2a3-109">.NET Core 3.0 neobsahuje `Microsoft.AspNetCore.All` sdílený rámec.</span><span class="sxs-lookup"><span data-stu-id="0f2a3-109">.NET Core 3.0 doesn't include a `Microsoft.AspNetCore.All` shared framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="0f2a3-110">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="0f2a3-110">Reason for change</span></span>

<span data-ttu-id="0f2a3-111">Metabalíček `Microsoft.AspNetCore.All` obsahoval velký počet externích závislostí.</span><span class="sxs-lookup"><span data-stu-id="0f2a3-111">The `Microsoft.AspNetCore.All` metapackage included a large number of external dependencies.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0f2a3-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="0f2a3-112">Recommended action</span></span>

<span data-ttu-id="0f2a3-113">Migrujte projekt `Microsoft.AspNetCore.App` a použijte rámec.</span><span class="sxs-lookup"><span data-stu-id="0f2a3-113">Migrate your project to use the `Microsoft.AspNetCore.App` framework.</span></span> <span data-ttu-id="0f2a3-114">Součásti, které byly `Microsoft.AspNetCore.All` dříve k dispozici v jsou stále k dispozici na NuGet.</span><span class="sxs-lookup"><span data-stu-id="0f2a3-114">Components that were previously available in `Microsoft.AspNetCore.All` are still available on NuGet.</span></span> <span data-ttu-id="0f2a3-115">Tyto součásti se teď nasazují s vaší aplikací, místo aby byly zahrnuty do sdíleného rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0f2a3-115">Those components are now deployed with your app instead of being included in the shared framework.</span></span>

#### <a name="category"></a><span data-ttu-id="0f2a3-116">Kategorie</span><span class="sxs-lookup"><span data-stu-id="0f2a3-116">Category</span></span>

<span data-ttu-id="0f2a3-117">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="0f2a3-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0f2a3-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="0f2a3-118">Affected APIs</span></span>

<span data-ttu-id="0f2a3-119">Žádný</span><span class="sxs-lookup"><span data-stu-id="0f2a3-119">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
