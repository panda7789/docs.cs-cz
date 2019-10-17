---
ms.openlocfilehash: dc9f37ae0cd6eef2c67e62421571290bba1c2233
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394058"
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

- Pro zachování původního názvu použijte atribut `[ActionName]`.
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
