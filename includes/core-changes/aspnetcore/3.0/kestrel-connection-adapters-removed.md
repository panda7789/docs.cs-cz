---
ms.openlocfilehash: a916af91670dc9c5ceb2ff759cd8ae308fb2c2dc
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394368"
---
### <a name="kestrel-connection-adapters-removed"></a><span data-ttu-id="485d8-101">Kestrel: odebrané adaptéry připojení</span><span class="sxs-lookup"><span data-stu-id="485d8-101">Kestrel: Connection adapters removed</span></span>

<span data-ttu-id="485d8-102">V rámci přesunutí na přesunutí rozhraní API "pubternal" na `public` se koncept `IConnectionAdapter` odebral z Kestrel.</span><span class="sxs-lookup"><span data-stu-id="485d8-102">As part of the move to move "pubternal" APIs to `public`, the concept of an `IConnectionAdapter` was removed from Kestrel.</span></span> <span data-ttu-id="485d8-103">Připojovací adaptéry se nahrazují pomocí middleware připojení (podobně jako middleware HTTP v kanálu ASP.NET Core, ale u připojení nižší úrovně).</span><span class="sxs-lookup"><span data-stu-id="485d8-103">Connection adapters are being replaced with connection middleware (similar to HTTP middleware in the ASP.NET Core pipeline, but for lower-level connections).</span></span> <span data-ttu-id="485d8-104">Protokolování HTTPS a připojení se přesunulo z připojovacích adaptérů na middleware připojení.</span><span class="sxs-lookup"><span data-stu-id="485d8-104">HTTPS and connection logging have moved from connection adapters to connection middleware.</span></span> <span data-ttu-id="485d8-105">Tyto metody rozšíření by měly nadále fungovat bez problémů, ale podrobnosti implementace se změnily.</span><span class="sxs-lookup"><span data-stu-id="485d8-105">Those extension methods should continue to work seamlessly, but the implementation details have changed.</span></span>

<span data-ttu-id="485d8-106">Další informace najdete v tématu [ASPNET/AspNetCore # 11412](https://github.com/aspnet/AspNetCore/pull/11412).</span><span class="sxs-lookup"><span data-stu-id="485d8-106">For more information, see [aspnet/AspNetCore#11412](https://github.com/aspnet/AspNetCore/pull/11412).</span></span> <span data-ttu-id="485d8-107">Diskuzi najdete v tématu [ASPNET/AspNetCore # 11475](https://github.com/aspnet/AspNetCore/issues/11475).</span><span class="sxs-lookup"><span data-stu-id="485d8-107">For discussion, see [aspnet/AspNetCore#11475](https://github.com/aspnet/AspNetCore/issues/11475).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="485d8-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="485d8-108">Version introduced</span></span>

<span data-ttu-id="485d8-109">3.0</span><span class="sxs-lookup"><span data-stu-id="485d8-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="485d8-110">Staré chování</span><span class="sxs-lookup"><span data-stu-id="485d8-110">Old behavior</span></span>

<span data-ttu-id="485d8-111">Komponenty rozšiřitelnosti Kestrel byly vytvořeny pomocí `IConnectionAdapter`.</span><span class="sxs-lookup"><span data-stu-id="485d8-111">Kestrel extensibility components were created using `IConnectionAdapter`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="485d8-112">Nové chování</span><span class="sxs-lookup"><span data-stu-id="485d8-112">New behavior</span></span>

<span data-ttu-id="485d8-113">Komponenty rozšiřitelnosti Kestrel se vytvářejí jako [middleware](https://github.com/aspnet/AspNetCore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span><span class="sxs-lookup"><span data-stu-id="485d8-113">Kestrel extensibility components are created as [middleware](https://github.com/aspnet/AspNetCore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="485d8-114">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="485d8-114">Reason for change</span></span>

<span data-ttu-id="485d8-115">Tato změna je určená k zajištění flexibilní rozšiřitelné architektury.</span><span class="sxs-lookup"><span data-stu-id="485d8-115">This change is intended to provide a more flexible extensibility architecture.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="485d8-116">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="485d8-116">Recommended action</span></span>

<span data-ttu-id="485d8-117">Převeďte všechny implementace `IConnectionAdapter`, aby používaly nový vzor middlewaru, jak je znázorněno [zde](https://github.com/aspnet/AspNetCore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span><span class="sxs-lookup"><span data-stu-id="485d8-117">Convert any implementations of `IConnectionAdapter` to use the new middleware pattern as shown [here](https://github.com/aspnet/AspNetCore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span></span>

#### <a name="category"></a><span data-ttu-id="485d8-118">Kategorie</span><span class="sxs-lookup"><span data-stu-id="485d8-118">Category</span></span>

<span data-ttu-id="485d8-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="485d8-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="485d8-120">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="485d8-120">Affected APIs</span></span>

`Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

-->
