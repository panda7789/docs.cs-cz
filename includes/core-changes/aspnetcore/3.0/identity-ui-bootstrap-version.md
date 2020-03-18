---
ms.openlocfilehash: c8f44ae1a500ed240dbff7d9a2c1479af368b7f1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394345"
---
### <a name="identity-default-bootstrap-version-of-ui-changed"></a>Identita: Výchozí bootstrap verze ui změněna

Počínaje ASP.NET Core 3.0, Identity UI výchozí použití verze 4 Bootstrap.

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Volání `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` metody bylo stejné jako`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`

#### <a name="new-behavior"></a>Nové chování

Volání `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` metody je stejné jako`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`

#### <a name="reason-for-change"></a>Důvod změny

Bootstrap 4 byl propuštěn během ASP.NET Core 3.0 časový rámec.

#### <a name="recommended-action"></a>Doporučená akce

Tato změna vás ovlivní, pokud použijete výchozí unové zobrazení identity a přičtete ho, `Startup.ConfigureServices` jak je znázorněno v následujícím příkladu:

```csharp
services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();
```

Proveďte jednu z následujících akcí:

- Migrujte aplikaci a použijte Bootstrap 4 pomocí průvodce [migrací](https://getbootstrap.com/docs/4.0/migration).
- Aktualizace `Startup.ConfigureServices` pro vynucení použití Bootstrap 3. Například:

    ```csharp
    services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);
    ```

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádný

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
