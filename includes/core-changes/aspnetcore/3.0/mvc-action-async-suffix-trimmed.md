---
ms.openlocfilehash: 58b1190e3e6a3168d35700eed655f6756e076a29
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901802"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a><span data-ttu-id="0f665-101">MVC: Asynchronní přípona oříznutá z názvů akcí kontroleru</span><span class="sxs-lookup"><span data-stu-id="0f665-101">MVC: Async suffix trimmed from controller action names</span></span>

<span data-ttu-id="0f665-102">Jako součást adresování [dotnet/aspnetcore#4849](https://github.com/dotnet/aspnetcore/issues/4849)ASP.NET Core MVC `Async` ve výchozím nastavení ořízne příponu z názvů akcí.</span><span class="sxs-lookup"><span data-stu-id="0f665-102">As part of addressing [dotnet/aspnetcore#4849](https://github.com/dotnet/aspnetcore/issues/4849), ASP.NET Core MVC trims the suffix `Async` from action names by default.</span></span> <span data-ttu-id="0f665-103">Počínaje ASP.NET jádrem 3.0, tato změna ovlivňuje směrování i generování propojení.</span><span class="sxs-lookup"><span data-stu-id="0f665-103">Starting with ASP.NET Core 3.0, this change affects both routing and link generation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0f665-104">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="0f665-104">Version introduced</span></span>

<span data-ttu-id="0f665-105">3.0</span><span class="sxs-lookup"><span data-stu-id="0f665-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="0f665-106">Staré chování</span><span class="sxs-lookup"><span data-stu-id="0f665-106">Old behavior</span></span>

<span data-ttu-id="0f665-107">Vezměte v úvahu následující ASP.NET core MVC řadič:</span><span class="sxs-lookup"><span data-stu-id="0f665-107">Consider the following ASP.NET Core MVC controller:</span></span>

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

<span data-ttu-id="0f665-108">Akce je směrovatelná `Product/ListAsync`přes .</span><span class="sxs-lookup"><span data-stu-id="0f665-108">The action is routable via `Product/ListAsync`.</span></span> <span data-ttu-id="0f665-109">Generování propojení vyžaduje `Async` zadání přípony.</span><span class="sxs-lookup"><span data-stu-id="0f665-109">Link generation requires specifying the `Async` suffix.</span></span> <span data-ttu-id="0f665-110">Například:</span><span class="sxs-lookup"><span data-stu-id="0f665-110">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="ListAsync">List</a>
```

#### <a name="new-behavior"></a><span data-ttu-id="0f665-111">Nové chování</span><span class="sxs-lookup"><span data-stu-id="0f665-111">New behavior</span></span>

<span data-ttu-id="0f665-112">V ASP.NET Core 3.0 je akce `Product/List`směrovatelná přes .</span><span class="sxs-lookup"><span data-stu-id="0f665-112">In ASP.NET Core 3.0, the action is routable via `Product/List`.</span></span> <span data-ttu-id="0f665-113">Kód generování propojení by `Async` měl vynechat příponu.</span><span class="sxs-lookup"><span data-stu-id="0f665-113">Link generation code should omit the `Async` suffix.</span></span> <span data-ttu-id="0f665-114">Například:</span><span class="sxs-lookup"><span data-stu-id="0f665-114">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="List">List</a>
```

<span data-ttu-id="0f665-115">Tato změna nemá vliv na `[ActionName]` názvy zadané pomocí atributu.</span><span class="sxs-lookup"><span data-stu-id="0f665-115">This change doesn't affect names specified using the `[ActionName]` attribute.</span></span> <span data-ttu-id="0f665-116">Nové chování lze zakázat `MvcOptions.SuppressAsyncSuffixInActionNames` `false` nastavením na v `Startup.ConfigureServices`:</span><span class="sxs-lookup"><span data-stu-id="0f665-116">The new behavior can be disabled by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="reason-for-change"></a><span data-ttu-id="0f665-117">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="0f665-117">Reason for change</span></span>

<span data-ttu-id="0f665-118">Podle konvence asynchronní metody .NET jsou suffix s `Async`.</span><span class="sxs-lookup"><span data-stu-id="0f665-118">By convention, asynchronous .NET methods are suffixed with `Async`.</span></span> <span data-ttu-id="0f665-119">Však když metoda definuje akci MVC, je nežádoucí použít `Async` příponu.</span><span class="sxs-lookup"><span data-stu-id="0f665-119">However, when a method defines an MVC action, it's undesirable to use the `Async` suffix.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0f665-120">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="0f665-120">Recommended action</span></span>

<span data-ttu-id="0f665-121">Pokud vaše aplikace závisí na akcích MVC, které zachovávají příponu názvu, `Async` zvolte jednu z následujících možností zmírnění:</span><span class="sxs-lookup"><span data-stu-id="0f665-121">If your app depends on MVC actions preserving the name's `Async` suffix, choose one of the following mitigations:</span></span>

- <span data-ttu-id="0f665-122">Pomocí `[ActionName]` atributu zachovejte původní název.</span><span class="sxs-lookup"><span data-stu-id="0f665-122">Use the `[ActionName]` attribute to preserve the original name.</span></span>
- <span data-ttu-id="0f665-123">Přejmenování zcela zakažte `false` `Startup.ConfigureServices`nastavením `MvcOptions.SuppressAsyncSuffixInActionNames` v :</span><span class="sxs-lookup"><span data-stu-id="0f665-123">Disable the renaming entirely by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="category"></a><span data-ttu-id="0f665-124">Kategorie</span><span class="sxs-lookup"><span data-stu-id="0f665-124">Category</span></span>

<span data-ttu-id="0f665-125">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="0f665-125">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0f665-126">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="0f665-126">Affected APIs</span></span>

<span data-ttu-id="0f665-127">Žádný</span><span class="sxs-lookup"><span data-stu-id="0f665-127">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
