---
ms.openlocfilehash: 1b4b0aba3ea24682ae972bf283ac387692c83781
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75902032"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a><span data-ttu-id="edd02-101">HTTP: rozšíření DefaultHttpContext bylo odebráno.</span><span class="sxs-lookup"><span data-stu-id="edd02-101">HTTP: DefaultHttpContext extensibility removed</span></span>

<span data-ttu-id="edd02-102">V rámci vylepšení výkonu ASP.NET Core 3,0 se rozšíření `DefaultHttpContext` odebralo.</span><span class="sxs-lookup"><span data-stu-id="edd02-102">As part of ASP.NET Core 3.0 performance improvements, the extensibility of `DefaultHttpContext` was removed.</span></span> <span data-ttu-id="edd02-103">Třída je nyní `sealed`.</span><span class="sxs-lookup"><span data-stu-id="edd02-103">The class is now `sealed`.</span></span> <span data-ttu-id="edd02-104">Další informace naleznete v tématu [dotnet/aspnetcore # 6504](https://github.com/dotnet/aspnetcore/pull/6504).</span><span class="sxs-lookup"><span data-stu-id="edd02-104">For more information, see [dotnet/aspnetcore#6504](https://github.com/dotnet/aspnetcore/pull/6504).</span></span>

<span data-ttu-id="edd02-105">Pokud testy jednotek používají `Mock<DefaultHttpContext>`, použijte místo toho `Mock<HttpContext>`.</span><span class="sxs-lookup"><span data-stu-id="edd02-105">If your unit tests use `Mock<DefaultHttpContext>`, use `Mock<HttpContext>` instead.</span></span>

<span data-ttu-id="edd02-106">Diskuzi najdete v tématu [dotnet/aspnetcore # 6534](https://github.com/dotnet/aspnetcore/issues/6534).</span><span class="sxs-lookup"><span data-stu-id="edd02-106">For discussion, see [dotnet/aspnetcore#6534](https://github.com/dotnet/aspnetcore/issues/6534).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="edd02-107">Představená verze</span><span class="sxs-lookup"><span data-stu-id="edd02-107">Version introduced</span></span>

<span data-ttu-id="edd02-108">3,0</span><span class="sxs-lookup"><span data-stu-id="edd02-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="edd02-109">Staré chování</span><span class="sxs-lookup"><span data-stu-id="edd02-109">Old behavior</span></span>

<span data-ttu-id="edd02-110">Třídy mohou odvozovat z `DefaultHttpContext`.</span><span class="sxs-lookup"><span data-stu-id="edd02-110">Classes can derive from `DefaultHttpContext`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="edd02-111">Nové chování</span><span class="sxs-lookup"><span data-stu-id="edd02-111">New behavior</span></span>

<span data-ttu-id="edd02-112">Třídy nelze odvodit z `DefaultHttpContext`.</span><span class="sxs-lookup"><span data-stu-id="edd02-112">Classes can't derive from `DefaultHttpContext`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="edd02-113">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="edd02-113">Reason for change</span></span>

<span data-ttu-id="edd02-114">Tato rozšiřitelná služba byla zpočátku k dispozici, aby umožňovala sdružování `HttpContext`, ale zavedla zbytečné složitosti a bránila jiným optimalizacím.</span><span class="sxs-lookup"><span data-stu-id="edd02-114">The extensibility was provided initially to allow pooling of the `HttpContext`, but it introduced unnecessary complexity and impeded other optimizations.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="edd02-115">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="edd02-115">Recommended action</span></span>

<span data-ttu-id="edd02-116">Pokud používáte `Mock<DefaultHttpContext>` při testování částí, začněte místo toho používat `Mock<HttpContext>`.</span><span class="sxs-lookup"><span data-stu-id="edd02-116">If you're using `Mock<DefaultHttpContext>` in your unit tests, begin using `Mock<HttpContext>` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="edd02-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="edd02-117">Category</span></span>

<span data-ttu-id="edd02-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="edd02-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="edd02-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="edd02-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
