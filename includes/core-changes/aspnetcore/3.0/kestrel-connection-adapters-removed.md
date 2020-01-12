---
ms.openlocfilehash: 06d5f48566c239e37355496c3f27163d952602c6
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901713"
---
### <a name="kestrel-connection-adapters-removed"></a><span data-ttu-id="9f619-101">Kestrel: odebrané adaptéry připojení</span><span class="sxs-lookup"><span data-stu-id="9f619-101">Kestrel: Connection adapters removed</span></span>

<span data-ttu-id="9f619-102">V rámci přesunutí pro přesunutí rozhraní API "pubternal" na `public`se koncept `IConnectionAdapter` odebral z Kestrel.</span><span class="sxs-lookup"><span data-stu-id="9f619-102">As part of the move to move "pubternal" APIs to `public`, the concept of an `IConnectionAdapter` was removed from Kestrel.</span></span> <span data-ttu-id="9f619-103">Připojovací adaptéry se nahrazují pomocí middleware připojení (podobně jako middleware HTTP v kanálu ASP.NET Core, ale u připojení nižší úrovně).</span><span class="sxs-lookup"><span data-stu-id="9f619-103">Connection adapters are being replaced with connection middleware (similar to HTTP middleware in the ASP.NET Core pipeline, but for lower-level connections).</span></span> <span data-ttu-id="9f619-104">Protokolování HTTPS a připojení se přesunulo z připojovacích adaptérů na middleware připojení.</span><span class="sxs-lookup"><span data-stu-id="9f619-104">HTTPS and connection logging have moved from connection adapters to connection middleware.</span></span> <span data-ttu-id="9f619-105">Tyto metody rozšíření by měly nadále fungovat bez problémů, ale podrobnosti implementace se změnily.</span><span class="sxs-lookup"><span data-stu-id="9f619-105">Those extension methods should continue to work seamlessly, but the implementation details have changed.</span></span>

<span data-ttu-id="9f619-106">Další informace naleznete v tématu [dotnet/aspnetcore # 11412](https://github.com/dotnet/aspnetcore/pull/11412).</span><span class="sxs-lookup"><span data-stu-id="9f619-106">For more information, see [dotnet/aspnetcore#11412](https://github.com/dotnet/aspnetcore/pull/11412).</span></span> <span data-ttu-id="9f619-107">Diskuzi najdete v tématu [dotnet/aspnetcore # 11475](https://github.com/dotnet/aspnetcore/issues/11475).</span><span class="sxs-lookup"><span data-stu-id="9f619-107">For discussion, see [dotnet/aspnetcore#11475](https://github.com/dotnet/aspnetcore/issues/11475).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9f619-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="9f619-108">Version introduced</span></span>

<span data-ttu-id="9f619-109">3,0</span><span class="sxs-lookup"><span data-stu-id="9f619-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="9f619-110">Staré chování</span><span class="sxs-lookup"><span data-stu-id="9f619-110">Old behavior</span></span>

<span data-ttu-id="9f619-111">Komponenty rozšiřitelnosti Kestrel byly vytvořeny pomocí `IConnectionAdapter`.</span><span class="sxs-lookup"><span data-stu-id="9f619-111">Kestrel extensibility components were created using `IConnectionAdapter`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="9f619-112">Nové chování</span><span class="sxs-lookup"><span data-stu-id="9f619-112">New behavior</span></span>

<span data-ttu-id="9f619-113">Komponenty rozšiřitelnosti Kestrel se vytvářejí jako [middleware](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span><span class="sxs-lookup"><span data-stu-id="9f619-113">Kestrel extensibility components are created as [middleware](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="9f619-114">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="9f619-114">Reason for change</span></span>

<span data-ttu-id="9f619-115">Tato změna je určená k zajištění flexibilní rozšiřitelné architektury.</span><span class="sxs-lookup"><span data-stu-id="9f619-115">This change is intended to provide a more flexible extensibility architecture.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9f619-116">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="9f619-116">Recommended action</span></span>

<span data-ttu-id="9f619-117">Převeďte všechny implementace `IConnectionAdapter`, aby používaly nový vzor middlewaru, jak je znázorněno [zde](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span><span class="sxs-lookup"><span data-stu-id="9f619-117">Convert any implementations of `IConnectionAdapter` to use the new middleware pattern as shown [here](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span></span>

#### <a name="category"></a><span data-ttu-id="9f619-118">Kategorie</span><span class="sxs-lookup"><span data-stu-id="9f619-118">Category</span></span>

<span data-ttu-id="9f619-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9f619-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9f619-120">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="9f619-120">Affected APIs</span></span>

`Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

-->
