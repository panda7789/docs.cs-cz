---
ms.openlocfilehash: 7b5ae84d02b83a10a4b9e002fc2ed4ee0833b84c
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198407"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a><span data-ttu-id="38b8b-101">HTTP: rozšíření DefaultHttpContext bylo odebráno.</span><span class="sxs-lookup"><span data-stu-id="38b8b-101">HTTP: DefaultHttpContext extensibility removed</span></span>

<span data-ttu-id="38b8b-102">V rámci vylepšení výkonu ASP.NET Core 3,0 se rozšíření `DefaultHttpContext` odebralo.</span><span class="sxs-lookup"><span data-stu-id="38b8b-102">As part of ASP.NET Core 3.0 performance improvements, the extensibility of `DefaultHttpContext` was removed.</span></span> <span data-ttu-id="38b8b-103">Třída je nyní `sealed`.</span><span class="sxs-lookup"><span data-stu-id="38b8b-103">The class is now `sealed`.</span></span> <span data-ttu-id="38b8b-104">Další informace najdete v tématu [ASPNET/AspNetCore # 6504](https://github.com/aspnet/AspNetCore/pull/6504).</span><span class="sxs-lookup"><span data-stu-id="38b8b-104">For more information, see [aspnet/AspNetCore#6504](https://github.com/aspnet/AspNetCore/pull/6504).</span></span>

<span data-ttu-id="38b8b-105">Pokud testy jednotek používají `Mock<DefaultHttpContext>`, použijte místo toho `Mock<HttpContext>`.</span><span class="sxs-lookup"><span data-stu-id="38b8b-105">If your unit tests use `Mock<DefaultHttpContext>`, use `Mock<HttpContext>` instead.</span></span>

<span data-ttu-id="38b8b-106">Diskuzi najdete v tématu [ASPNET/AspNetCore # 6534](https://github.com/aspnet/AspNetCore/issues/6534).</span><span class="sxs-lookup"><span data-stu-id="38b8b-106">For discussion, see [aspnet/AspNetCore#6534](https://github.com/aspnet/AspNetCore/issues/6534).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="38b8b-107">Představená verze</span><span class="sxs-lookup"><span data-stu-id="38b8b-107">Version introduced</span></span>

<span data-ttu-id="38b8b-108">3.0</span><span class="sxs-lookup"><span data-stu-id="38b8b-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="38b8b-109">Staré chování</span><span class="sxs-lookup"><span data-stu-id="38b8b-109">Old behavior</span></span>

<span data-ttu-id="38b8b-110">Třídy mohou odvozovat z `DefaultHttpContext`.</span><span class="sxs-lookup"><span data-stu-id="38b8b-110">Classes can derive from `DefaultHttpContext`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="38b8b-111">Nové chování</span><span class="sxs-lookup"><span data-stu-id="38b8b-111">New behavior</span></span>

<span data-ttu-id="38b8b-112">Třídy nemůžou být odvozené od `DefaultHttpContext`.</span><span class="sxs-lookup"><span data-stu-id="38b8b-112">Classes can't derive from `DefaultHttpContext`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="38b8b-113">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="38b8b-113">Reason for change</span></span>

<span data-ttu-id="38b8b-114">Toto rozšíření bylo zpočátku umožněno sdružování `HttpContext`, ale zavedlo zbytečné složitosti a narušilo další optimalizace.</span><span class="sxs-lookup"><span data-stu-id="38b8b-114">The extensibility was provided initially to allow pooling of the `HttpContext`, but it introduced unnecessary complexity and impeded other optimizations.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="38b8b-115">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="38b8b-115">Recommended action</span></span>

<span data-ttu-id="38b8b-116">Pokud v testech jednotek používáte `Mock<DefaultHttpContext>`, začněte místo toho použít `Mock<HttpContext>`.</span><span class="sxs-lookup"><span data-stu-id="38b8b-116">If you're using `Mock<DefaultHttpContext>` in your unit tests, begin using `Mock<HttpContext>` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="38b8b-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="38b8b-117">Category</span></span>

<span data-ttu-id="38b8b-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="38b8b-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="38b8b-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="38b8b-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
