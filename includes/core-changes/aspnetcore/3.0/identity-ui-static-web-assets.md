---
ms.openlocfilehash: c5e4b5619394f99a419fe48aee190ad741ea8c0d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73041656"
---
### <a name="identity-ui-uses-static-web-assets-feature"></a>Identita: Uživatelské uživatelské zařízení používá funkci statických webových datových zdrojů

ASP.NET Core 3.0 představil statickou funkci webových datových zdrojů a uživatelské uživatelské uživatelské číslo identity ji přijalo.

#### <a name="change-description"></a>Popis změny

V důsledku identity uživatelského uživatelského prvku přijetí statické webové datové zdroje funkce:

- Výběr architektury se provádí `IdentityUIFrameworkVersion` pomocí vlastnosti v souboru projektu.
- Bootstrap 4 je výchozí rozhraní ui pro rozhraní identity. Bootstrap 3 dosáhl konce životnosti a měli byste zvážit migraci na podporovanou verzi.

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Výchozí rozhraní ui pro identity ui byl **Bootstrap 3**. Rozhraní ui lze nakonfigurovat pomocí `AddDefaultUI` parametru `Startup.ConfigureServices`volání metody v .

#### <a name="new-behavior"></a>Nové chování

Výchozí rozhraní ui pro identity ui je **Bootstrap 4**. Rozhraní ui musí být nakonfigurovánv souboru `AddDefaultUI` projektu, nikoli ve volání metody.

#### <a name="reason-for-change"></a>Důvod změny

Přijetí funkce statické webové datové zdroje vyžaduje, aby konfigurace rozhraní rozhraní přesunout do MSBuild. Rozhodnutí, na kterém rámci vložit je sestavení rozhodnutí, nikoli runtime rozhodnutí.

#### <a name="recommended-action"></a>Doporučená akce

Zkontrolujte své rozhraní webu, abyste se ujistili, že nové komponenty Bootstrap 4 jsou kompatibilní. V případě potřeby `IdentityUIFrameworkVersion` použijte msbuild vlastnost vrátit do Bootstrap 3. Přidejte vlastnost `<PropertyGroup>` do prvku v souboru projektu:

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
