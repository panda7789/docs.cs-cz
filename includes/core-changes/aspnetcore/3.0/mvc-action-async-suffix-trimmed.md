---
ms.openlocfilehash: 503d61cb86c83e2f32ad40c60a127ae255ef71b0
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198403"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a>MVC: asynchronní přípona se ořízne z názvů akcí řadiče.

Jako součást adresování [ASPNET/AspNetCore # 4849](https://github.com/aspnet/AspNetCore/issues/4849)ASP.NET Core MVC ořízne příponu `Async` z názvů akcí ve výchozím nastavení. Od ASP.NET Core 3,0 Tato změna ovlivní vytváření směrování i propojení.

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Vezměte v úvahu následující ASP.NET Core kontroler MVC:

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

Akce je směrovatelný přes `Product/ListAsync`. Generování propojení vyžaduje určení přípony `Async`. Příklad:

```cshtml
<a asp-controller="Product" asp-action="ListAsync">List</a>
```

#### <a name="new-behavior"></a>Nové chování

V ASP.NET Core 3,0 je akce směrovatelný přes `Product/List`. Kód pro generování odkazů by měl vynechat příponu `Async`. Příklad:

```cshtml
<a asp-controller="Product" asp-action="List">List</a>
```

Tato změna nemá vliv na názvy zadané pomocí atributu `[ActionName]`. Nové chování je možné zakázat nastavením `MvcOptions.SuppressAsyncSuffixInActionNames` na `false` v `Startup.ConfigureServices`:

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="reason-for-change"></a>Důvod změny

Podle konvence jsou asynchronní metody .NET s příponou `Async`. Pokud však Metoda definuje akci MVC, je nežádoucí použít příponu `Async`.

#### <a name="recommended-action"></a>Doporučená akce

Pokud vaše aplikace závisí na akcích MVC, které zachovávají příponu `Async`, vyberte jednu z následujících rizik:

- Použijte atribut `[ActionName]` k zachování původního názvu.
- Zakažte úplné přejmenování nastavením `MvcOptions.SuppressAsyncSuffixInActionNames` na `false` v `Startup.ConfigureServices`:

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádné

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
