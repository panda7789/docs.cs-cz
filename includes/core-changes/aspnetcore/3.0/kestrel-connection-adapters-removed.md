---
ms.openlocfilehash: 06d5f48566c239e37355496c3f27163d952602c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901713"
---
### <a name="kestrel-connection-adapters-removed"></a><span data-ttu-id="0963e-101">Poštolka: Připojení adaptéry odstraněny</span><span class="sxs-lookup"><span data-stu-id="0963e-101">Kestrel: Connection adapters removed</span></span>

<span data-ttu-id="0963e-102">V rámci přesunu "pubternal" API `public`do aplikace byl `IConnectionAdapter` z Kestrelu odstraněn koncept konceptu a.</span><span class="sxs-lookup"><span data-stu-id="0963e-102">As part of the move to move "pubternal" APIs to `public`, the concept of an `IConnectionAdapter` was removed from Kestrel.</span></span> <span data-ttu-id="0963e-103">Adaptéry připojení jsou nahrazovány middleware připojení (podobně jako http middleware v kanálu ASP.NET Core, ale pro připojení nižší úrovně).</span><span class="sxs-lookup"><span data-stu-id="0963e-103">Connection adapters are being replaced with connection middleware (similar to HTTP middleware in the ASP.NET Core pipeline, but for lower-level connections).</span></span> <span data-ttu-id="0963e-104">Protokolování protokolu HTTPS a připojení se přesunulo z adaptérů připojení na middleware připojení.</span><span class="sxs-lookup"><span data-stu-id="0963e-104">HTTPS and connection logging have moved from connection adapters to connection middleware.</span></span> <span data-ttu-id="0963e-105">Tyto metody rozšíření by měly i nadále fungovat bez problémů, ale podrobnosti implementace se změnily.</span><span class="sxs-lookup"><span data-stu-id="0963e-105">Those extension methods should continue to work seamlessly, but the implementation details have changed.</span></span>

<span data-ttu-id="0963e-106">Další informace naleznete [v tématu dotnet/aspnetcore#11412](https://github.com/dotnet/aspnetcore/pull/11412).</span><span class="sxs-lookup"><span data-stu-id="0963e-106">For more information, see [dotnet/aspnetcore#11412](https://github.com/dotnet/aspnetcore/pull/11412).</span></span> <span data-ttu-id="0963e-107">Diskuse naleznete [v tématu dotnet/aspnetcore#11475](https://github.com/dotnet/aspnetcore/issues/11475).</span><span class="sxs-lookup"><span data-stu-id="0963e-107">For discussion, see [dotnet/aspnetcore#11475](https://github.com/dotnet/aspnetcore/issues/11475).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0963e-108">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="0963e-108">Version introduced</span></span>

<span data-ttu-id="0963e-109">3.0</span><span class="sxs-lookup"><span data-stu-id="0963e-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="0963e-110">Staré chování</span><span class="sxs-lookup"><span data-stu-id="0963e-110">Old behavior</span></span>

<span data-ttu-id="0963e-111">Součásti rozšiřitelnosti kestrelu `IConnectionAdapter`byly vytvořeny pomocí .</span><span class="sxs-lookup"><span data-stu-id="0963e-111">Kestrel extensibility components were created using `IConnectionAdapter`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="0963e-112">Nové chování</span><span class="sxs-lookup"><span data-stu-id="0963e-112">New behavior</span></span>

<span data-ttu-id="0963e-113">Komponenty rozšiřitelnosti kestrelu jsou vytvořeny jako [middleware](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span><span class="sxs-lookup"><span data-stu-id="0963e-113">Kestrel extensibility components are created as [middleware](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="0963e-114">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="0963e-114">Reason for change</span></span>

<span data-ttu-id="0963e-115">Tato změna má poskytnout flexibilnější architekturu rozšiřitelnosti.</span><span class="sxs-lookup"><span data-stu-id="0963e-115">This change is intended to provide a more flexible extensibility architecture.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0963e-116">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="0963e-116">Recommended action</span></span>

<span data-ttu-id="0963e-117">Převést všechny `IConnectionAdapter` implementace použít nový middleware vzor, jak je znázorněno [zde](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span><span class="sxs-lookup"><span data-stu-id="0963e-117">Convert any implementations of `IConnectionAdapter` to use the new middleware pattern as shown [here](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span></span>

#### <a name="category"></a><span data-ttu-id="0963e-118">Kategorie</span><span class="sxs-lookup"><span data-stu-id="0963e-118">Category</span></span>

<span data-ttu-id="0963e-119">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="0963e-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0963e-120">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="0963e-120">Affected APIs</span></span>

`Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

-->
