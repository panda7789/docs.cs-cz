---
ms.openlocfilehash: 503d61cb86c83e2f32ad40c60a127ae255ef71b0
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198403"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a><span data-ttu-id="7862c-101">MVC: asynchronní přípona se ořízne z názvů akcí řadiče.</span><span class="sxs-lookup"><span data-stu-id="7862c-101">MVC: Async suffix trimmed from controller action names</span></span>

<span data-ttu-id="7862c-102">Jako součást adresování [ASPNET/AspNetCore # 4849](https://github.com/aspnet/AspNetCore/issues/4849)ASP.NET Core MVC ořízne příponu `Async` z názvů akcí ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="7862c-102">As part of addressing [aspnet/AspNetCore#4849](https://github.com/aspnet/AspNetCore/issues/4849), ASP.NET Core MVC trims the suffix `Async` from action names by default.</span></span> <span data-ttu-id="7862c-103">Od ASP.NET Core 3,0 Tato změna ovlivní vytváření směrování i propojení.</span><span class="sxs-lookup"><span data-stu-id="7862c-103">Starting with ASP.NET Core 3.0, this change affects both routing and link generation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7862c-104">Představená verze</span><span class="sxs-lookup"><span data-stu-id="7862c-104">Version introduced</span></span>

<span data-ttu-id="7862c-105">3.0</span><span class="sxs-lookup"><span data-stu-id="7862c-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="7862c-106">Staré chování</span><span class="sxs-lookup"><span data-stu-id="7862c-106">Old behavior</span></span>

<span data-ttu-id="7862c-107">Vezměte v úvahu následující ASP.NET Core kontroler MVC:</span><span class="sxs-lookup"><span data-stu-id="7862c-107">Consider the following ASP.NET Core MVC controller:</span></span>

```csharp
public class ProductController : Controller
{
    public async IActionResult ListAsync()
    {
        var model = await DbContext.Products.ToListAsync();
        return View(model);
    }
}
```

<span data-ttu-id="7862c-108">Akce je směrovatelný přes `Product/ListAsync`.</span><span class="sxs-lookup"><span data-stu-id="7862c-108">The action is routable via `Product/ListAsync`.</span></span> <span data-ttu-id="7862c-109">Generování propojení vyžaduje určení přípony `Async`.</span><span class="sxs-lookup"><span data-stu-id="7862c-109">Link generation requires specifying the `Async` suffix.</span></span> <span data-ttu-id="7862c-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="7862c-110">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="ListAsync">List</a>
```

#### <a name="new-behavior"></a><span data-ttu-id="7862c-111">Nové chování</span><span class="sxs-lookup"><span data-stu-id="7862c-111">New behavior</span></span>

<span data-ttu-id="7862c-112">V ASP.NET Core 3,0 je akce směrovatelný přes `Product/List`.</span><span class="sxs-lookup"><span data-stu-id="7862c-112">In ASP.NET Core 3.0, the action is routable via `Product/List`.</span></span> <span data-ttu-id="7862c-113">Kód pro generování odkazů by měl vynechat příponu `Async`.</span><span class="sxs-lookup"><span data-stu-id="7862c-113">Link generation code should omit the `Async` suffix.</span></span> <span data-ttu-id="7862c-114">Příklad:</span><span class="sxs-lookup"><span data-stu-id="7862c-114">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="List">List</a>
```

<span data-ttu-id="7862c-115">Tato změna nemá vliv na názvy zadané pomocí atributu `[ActionName]`.</span><span class="sxs-lookup"><span data-stu-id="7862c-115">This change doesn't affect names specified using the `[ActionName]` attribute.</span></span> <span data-ttu-id="7862c-116">Nové chování je možné zakázat nastavením `MvcOptions.SuppressAsyncSuffixInActionNames` na `false` v `Startup.ConfigureServices`:</span><span class="sxs-lookup"><span data-stu-id="7862c-116">The new behavior can be disabled by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="reason-for-change"></a><span data-ttu-id="7862c-117">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="7862c-117">Reason for change</span></span>

<span data-ttu-id="7862c-118">Podle konvence jsou asynchronní metody .NET s příponou `Async`.</span><span class="sxs-lookup"><span data-stu-id="7862c-118">By convention, asynchronous .NET methods are suffixed with `Async`.</span></span> <span data-ttu-id="7862c-119">Pokud však Metoda definuje akci MVC, je nežádoucí použít příponu `Async`.</span><span class="sxs-lookup"><span data-stu-id="7862c-119">However, when a method defines an MVC action, it's undesirable to use the `Async` suffix.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7862c-120">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="7862c-120">Recommended action</span></span>

<span data-ttu-id="7862c-121">Pokud vaše aplikace závisí na akcích MVC, které zachovávají příponu `Async`, vyberte jednu z následujících rizik:</span><span class="sxs-lookup"><span data-stu-id="7862c-121">If your app depends on MVC actions preserving the name's `Async` suffix, choose one of the following mitigations:</span></span>

- <span data-ttu-id="7862c-122">Použijte atribut `[ActionName]` k zachování původního názvu.</span><span class="sxs-lookup"><span data-stu-id="7862c-122">Use the `[ActionName]` attribute to preserve the original name.</span></span>
- <span data-ttu-id="7862c-123">Zakažte úplné přejmenování nastavením `MvcOptions.SuppressAsyncSuffixInActionNames` na `false` v `Startup.ConfigureServices`:</span><span class="sxs-lookup"><span data-stu-id="7862c-123">Disable the renaming entirely by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="category"></a><span data-ttu-id="7862c-124">Kategorie</span><span class="sxs-lookup"><span data-stu-id="7862c-124">Category</span></span>

<span data-ttu-id="7862c-125">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7862c-125">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7862c-126">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="7862c-126">Affected APIs</span></span>

<span data-ttu-id="7862c-127">Žádné</span><span class="sxs-lookup"><span data-stu-id="7862c-127">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
