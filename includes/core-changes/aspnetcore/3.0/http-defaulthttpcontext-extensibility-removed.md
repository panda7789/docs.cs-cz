---
ms.openlocfilehash: 177617569a93e09f4c2a05acc21dce362edd58bc
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394312"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a><span data-ttu-id="793ef-101">HTTP: rozšíření DefaultHttpContext bylo odebráno.</span><span class="sxs-lookup"><span data-stu-id="793ef-101">HTTP: DefaultHttpContext extensibility removed</span></span>

<span data-ttu-id="793ef-102">V rámci vylepšení výkonu ASP.NET Core 3,0 se rozšíření `DefaultHttpContext` odebralo.</span><span class="sxs-lookup"><span data-stu-id="793ef-102">As part of ASP.NET Core 3.0 performance improvements, the extensibility of `DefaultHttpContext` was removed.</span></span> <span data-ttu-id="793ef-103">Třída je nyní `sealed`.</span><span class="sxs-lookup"><span data-stu-id="793ef-103">The class is now `sealed`.</span></span> <span data-ttu-id="793ef-104">Další informace najdete v tématu [ASPNET/AspNetCore # 6504](https://github.com/aspnet/AspNetCore/pull/6504).</span><span class="sxs-lookup"><span data-stu-id="793ef-104">For more information, see [aspnet/AspNetCore#6504](https://github.com/aspnet/AspNetCore/pull/6504).</span></span>

<span data-ttu-id="793ef-105">Pokud testy jednotek používají `Mock<DefaultHttpContext>`, použijte místo toho `Mock<HttpContext>`.</span><span class="sxs-lookup"><span data-stu-id="793ef-105">If your unit tests use `Mock<DefaultHttpContext>`, use `Mock<HttpContext>` instead.</span></span> 

<span data-ttu-id="793ef-106">Diskuzi najdete v tématu [ASPNET/AspNetCore # 6534](https://github.com/aspnet/AspNetCore/issues/6534).</span><span class="sxs-lookup"><span data-stu-id="793ef-106">For discussion, see [aspnet/AspNetCore#6534](https://github.com/aspnet/AspNetCore/issues/6534).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="793ef-107">Představená verze</span><span class="sxs-lookup"><span data-stu-id="793ef-107">Version introduced</span></span>

<span data-ttu-id="793ef-108">3.0</span><span class="sxs-lookup"><span data-stu-id="793ef-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="793ef-109">Staré chování</span><span class="sxs-lookup"><span data-stu-id="793ef-109">Old behavior</span></span>

<span data-ttu-id="793ef-110">Třídy mohou odvozovat z `DefaultHttpContext`.</span><span class="sxs-lookup"><span data-stu-id="793ef-110">Classes can derive from `DefaultHttpContext`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="793ef-111">Nové chování</span><span class="sxs-lookup"><span data-stu-id="793ef-111">New behavior</span></span>

<span data-ttu-id="793ef-112">Třídy nemůžou být odvozené od `DefaultHttpContext`.</span><span class="sxs-lookup"><span data-stu-id="793ef-112">Classes can't derive from `DefaultHttpContext`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="793ef-113">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="793ef-113">Reason for change</span></span>

<span data-ttu-id="793ef-114">Toto rozšíření bylo zpočátku umožněno sdružování `HttpContext`, ale zavedlo zbytečné složitosti a narušilo další optimalizace.</span><span class="sxs-lookup"><span data-stu-id="793ef-114">The extensibility was provided initially to allow pooling of the `HttpContext`, but it introduced unnecessary complexity and impeded other optimizations.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="793ef-115">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="793ef-115">Recommended action</span></span>

<span data-ttu-id="793ef-116">Pokud v testech jednotek používáte `Mock<DefaultHttpContext>`, začněte místo toho použít `Mock<HttpContext>`.</span><span class="sxs-lookup"><span data-stu-id="793ef-116">If you're using `Mock<DefaultHttpContext>` in your unit tests, begin using `Mock<HttpContext>` instead.</span></span> 

#### <a name="category"></a><span data-ttu-id="793ef-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="793ef-117">Category</span></span>

<span data-ttu-id="793ef-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="793ef-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="793ef-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="793ef-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
