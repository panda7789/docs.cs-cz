---
ms.openlocfilehash: 58b1190e3e6a3168d35700eed655f6756e076a29
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901802"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a>MVC: Asynchronní přípona oříznutá z názvů akcí kontroleru

Jako součást adresování [dotnet/aspnetcore#4849](https://github.com/dotnet/aspnetcore/issues/4849)ASP.NET Core MVC `Async` ve výchozím nastavení ořízne příponu z názvů akcí. Počínaje ASP.NET jádrem 3.0, tato změna ovlivňuje směrování i generování propojení.

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Vezměte v úvahu následující ASP.NET core MVC řadič:

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

Akce je směrovatelná `Product/ListAsync`přes . Generování propojení vyžaduje `Async` zadání přípony. Například:

```cshtml
<a asp-controller="Product" asp-action="ListAsync">List</a>
```

#### <a name="new-behavior"></a>Nové chování

V ASP.NET Core 3.0 je akce `Product/List`směrovatelná přes . Kód generování propojení by `Async` měl vynechat příponu. Například:

```cshtml
<a asp-controller="Product" asp-action="List">List</a>
```

Tato změna nemá vliv na `[ActionName]` názvy zadané pomocí atributu. Nové chování lze zakázat `MvcOptions.SuppressAsyncSuffixInActionNames` `false` nastavením na v `Startup.ConfigureServices`:

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="reason-for-change"></a>Důvod změny

Podle konvence asynchronní metody .NET jsou suffix s `Async`. Však když metoda definuje akci MVC, je nežádoucí použít `Async` příponu.

#### <a name="recommended-action"></a>Doporučená akce

Pokud vaše aplikace závisí na akcích MVC, které zachovávají příponu názvu, `Async` zvolte jednu z následujících možností zmírnění:

- Pomocí `[ActionName]` atributu zachovejte původní název.
- Přejmenování zcela zakažte `false` `Startup.ConfigureServices`nastavením `MvcOptions.SuppressAsyncSuffixInActionNames` v :

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádný

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
