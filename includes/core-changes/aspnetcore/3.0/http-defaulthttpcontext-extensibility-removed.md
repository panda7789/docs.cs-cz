---
ms.openlocfilehash: 9d138f79fcede4acac837f8d7793aa343ced737c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78290762"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a><span data-ttu-id="bfcea-101">HTTP: VýchozíhttpContext rozšiřitelnost odebrána</span><span class="sxs-lookup"><span data-stu-id="bfcea-101">HTTP: DefaultHttpContext extensibility removed</span></span>

<span data-ttu-id="bfcea-102">Jako součást ASP.NET vylepšení výkonu jádra 3.0 `DefaultHttpContext` byla zrušena rozšiřitelnost.</span><span class="sxs-lookup"><span data-stu-id="bfcea-102">As part of ASP.NET Core 3.0 performance improvements, the extensibility of `DefaultHttpContext` was removed.</span></span> <span data-ttu-id="bfcea-103">Třída je `sealed`nyní .</span><span class="sxs-lookup"><span data-stu-id="bfcea-103">The class is now `sealed`.</span></span> <span data-ttu-id="bfcea-104">Další informace naleznete [v tématu dotnet/aspnetcore#6504](https://github.com/dotnet/aspnetcore/pull/6504).</span><span class="sxs-lookup"><span data-stu-id="bfcea-104">For more information, see [dotnet/aspnetcore#6504](https://github.com/dotnet/aspnetcore/pull/6504).</span></span>

<span data-ttu-id="bfcea-105">Pokud jednotkové `Mock<DefaultHttpContext>`testy `Mock<HttpContext>` používají `new DefaultHttpContext()` , použijte nebo místo.</span><span class="sxs-lookup"><span data-stu-id="bfcea-105">If your unit tests use `Mock<DefaultHttpContext>`, use `Mock<HttpContext>` or `new DefaultHttpContext()` instead.</span></span>

<span data-ttu-id="bfcea-106">Diskuse naleznete [v tématu dotnet/aspnetcore#6534](https://github.com/dotnet/aspnetcore/issues/6534).</span><span class="sxs-lookup"><span data-stu-id="bfcea-106">For discussion, see [dotnet/aspnetcore#6534](https://github.com/dotnet/aspnetcore/issues/6534).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="bfcea-107">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="bfcea-107">Version introduced</span></span>

<span data-ttu-id="bfcea-108">3.0</span><span class="sxs-lookup"><span data-stu-id="bfcea-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="bfcea-109">Staré chování</span><span class="sxs-lookup"><span data-stu-id="bfcea-109">Old behavior</span></span>

<span data-ttu-id="bfcea-110">Třídy mohou `DefaultHttpContext`být odvozeny z .</span><span class="sxs-lookup"><span data-stu-id="bfcea-110">Classes can derive from `DefaultHttpContext`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="bfcea-111">Nové chování</span><span class="sxs-lookup"><span data-stu-id="bfcea-111">New behavior</span></span>

<span data-ttu-id="bfcea-112">Třídy nelze odvodit z `DefaultHttpContext`.</span><span class="sxs-lookup"><span data-stu-id="bfcea-112">Classes can't derive from `DefaultHttpContext`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="bfcea-113">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="bfcea-113">Reason for change</span></span>

<span data-ttu-id="bfcea-114">Rozšiřitelnost byla poskytnuta zpočátku umožnit `HttpContext`sdružování , ale zavedla zbytečnou složitost a bránila dalším optimalizacím.</span><span class="sxs-lookup"><span data-stu-id="bfcea-114">The extensibility was provided initially to allow pooling of the `HttpContext`, but it introduced unnecessary complexity and impeded other optimizations.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="bfcea-115">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="bfcea-115">Recommended action</span></span>

<span data-ttu-id="bfcea-116">Pokud používáte `Mock<DefaultHttpContext>` v testování částí, `Mock<HttpContext>` začněte používat místo.</span><span class="sxs-lookup"><span data-stu-id="bfcea-116">If you're using `Mock<DefaultHttpContext>` in your unit tests, begin using `Mock<HttpContext>` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="bfcea-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="bfcea-117">Category</span></span>

<span data-ttu-id="bfcea-118">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="bfcea-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bfcea-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="bfcea-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
