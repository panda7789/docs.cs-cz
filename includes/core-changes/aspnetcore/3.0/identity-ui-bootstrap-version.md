---
ms.openlocfilehash: c8f44ae1a500ed240dbff7d9a2c1479af368b7f1
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394345"
---
### <a name="identity-default-bootstrap-version-of-ui-changed"></a>Identita: výchozí počáteční verze uživatelského rozhraní se změnila.

Počínaje ASP.NET Core 3,0 se v uživatelském rozhraní identity standardně používá verze 4 Bootstrap.

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Volání metody `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` bylo stejné jako `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`.

#### <a name="new-behavior"></a>Nové chování

Volání metody `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` je stejné jako `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`.

#### <a name="reason-for-change"></a>Důvod změny

Služba Bootstrap 4 byla vydána během období ASP.NET Core 3,0.

#### <a name="recommended-action"></a>Doporučená akce

Tuto změnu ovlivníte, pokud použijete výchozí uživatelské rozhraní identity a přidáte ho do `Startup.ConfigureServices`, jak je znázorněno v následujícím příkladu:

```csharp
services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();
```

Proveďte jednu z následujících akcí:

- Migrujte aplikaci tak, aby používala Bootstrap 4 pomocí jejich [Průvodce migrací](https://getbootstrap.com/docs/4.0/migration).
- Aktualizujte `Startup.ConfigureServices`, aby se vynutilo použití spouštěcí rutiny 3. Příklad:

    ```csharp
    services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);
    ```

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádné

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
