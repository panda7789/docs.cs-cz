---
ms.openlocfilehash: 82103d82a6f68c62f3532608718bc71b0ba126bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901958"
---
### <a name="hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle"></a><span data-ttu-id="bc914-101">Hosting: AspNetCoreModule V1 odstraněn z Windows Hosting Bundle</span><span class="sxs-lookup"><span data-stu-id="bc914-101">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>

<span data-ttu-id="bc914-102">Počínaje ASP.NET Core 3.0, Windows Hosting Bundle nebude obsahovat AspNetCoreModule (ANCM) V1.</span><span class="sxs-lookup"><span data-stu-id="bc914-102">Starting with ASP.NET Core 3.0, the Windows Hosting Bundle won't contain AspNetCoreModule (ANCM) V1.</span></span>

<span data-ttu-id="bc914-103">ANCM V2 je zpětně kompatibilní s ANCM OutOfProcess a je doporučeno pro použití s aplikacemi ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="bc914-103">ANCM V2 is backwards compatible with ANCM OutOfProcess and is recommended for use with ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="bc914-104">Diskuse naleznete [v tématu dotnet/aspnetcore#7095](https://github.com/dotnet/aspnetcore/issues/7095).</span><span class="sxs-lookup"><span data-stu-id="bc914-104">For discussion, see [dotnet/aspnetcore#7095](https://github.com/dotnet/aspnetcore/issues/7095).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="bc914-105">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="bc914-105">Version introduced</span></span>

<span data-ttu-id="bc914-106">3.0</span><span class="sxs-lookup"><span data-stu-id="bc914-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="bc914-107">Staré chování</span><span class="sxs-lookup"><span data-stu-id="bc914-107">Old behavior</span></span>

<span data-ttu-id="bc914-108">ANCM V1 je součástí balíčku Windows Hosting.</span><span class="sxs-lookup"><span data-stu-id="bc914-108">ANCM V1 is included in the Windows Hosting Bundle.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="bc914-109">Nové chování</span><span class="sxs-lookup"><span data-stu-id="bc914-109">New behavior</span></span>

<span data-ttu-id="bc914-110">ANCM V1 není součástí balíčku Windows Hosting.</span><span class="sxs-lookup"><span data-stu-id="bc914-110">ANCM V1 isn't included in the Windows Hosting Bundle.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="bc914-111">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="bc914-111">Reason for change</span></span>

<span data-ttu-id="bc914-112">ANCM V2 je zpětně kompatibilní s ANCM OutOfProcess a je doporučeno pro použití s aplikacemi ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="bc914-112">ANCM V2 is backwards compatible with ANCM OutOfProcess and is recommended for use with ASP.NET Core 3.0 apps.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="bc914-113">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="bc914-113">Recommended action</span></span>

<span data-ttu-id="bc914-114">S aplikacemi core 3.0 ASP.NET Core 3.0 používejte ANCM V2.</span><span class="sxs-lookup"><span data-stu-id="bc914-114">Use ANCM V2 with ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="bc914-115">Pokud je vyžadovánan cm V1, lze jej nainstalovat pomocí ASP.NET Core 2.1 nebo 2.2 Windows Hosting Bundle.</span><span class="sxs-lookup"><span data-stu-id="bc914-115">If ANCM V1 is required, it can be installed using the ASP.NET Core 2.1 or 2.2 Windows Hosting Bundle.</span></span>

<span data-ttu-id="bc914-116">Tato změna přeruší ASP.NET aplikací core 3.0, které:</span><span class="sxs-lookup"><span data-stu-id="bc914-116">This change will break ASP.NET Core 3.0 apps that:</span></span>

- <span data-ttu-id="bc914-117">Explicitně se rozhodl pro `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`použití ANCM V1 s .</span><span class="sxs-lookup"><span data-stu-id="bc914-117">Explicitly opted into using ANCM V1 with `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`.</span></span>
- <span data-ttu-id="bc914-118">Mít vlastní *web.config* `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`soubor s .</span><span class="sxs-lookup"><span data-stu-id="bc914-118">Have a custom *web.config* file with `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`.</span></span>

#### <a name="category"></a><span data-ttu-id="bc914-119">Kategorie</span><span class="sxs-lookup"><span data-stu-id="bc914-119">Category</span></span>

<span data-ttu-id="bc914-120">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="bc914-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bc914-121">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="bc914-121">Affected APIs</span></span>

<span data-ttu-id="bc914-122">Žádný</span><span class="sxs-lookup"><span data-stu-id="bc914-122">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
