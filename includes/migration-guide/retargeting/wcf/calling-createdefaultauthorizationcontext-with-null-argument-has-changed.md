---
ms.openlocfilehash: c5a061dffa1deb66e1769d6ec70dfa2155ac6a31
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615706"
---
### <a name="calling-createdefaultauthorizationcontext-with-a-null-argument-has-changed"></a>Volání CreateDefaultAuthorizationContext s argumentem null se změnilo.

#### <a name="details"></a>Podrobnosti

Implementace <xref:System.IdentityModel.Policy.AuthorizationContext?displayProperty=fullName> vrácená voláním <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=fullName> s argumentem s hodnotou null authorizationPolicies se změnila jeho implementace v .NET Framework 4,6.

#### <a name="suggestion"></a>Návrh

Ve výjimečných případech můžou aplikace WCF, které používají vlastní ověřování, zobrazovat rozdíly v chování. V takových případech je možné předchozí chování obnovit jedním ze dvou způsobů:

- Znovu zkompilujte aplikaci a Zaměřte se na starší verzi .NET Framework než 4,6. Pro služby hostované službou IIS použijte `<httpRuntime targetFramework="x.x">` element k zacílení na starší verzi .NET Framework.
- Přidejte následující řádek do `<appSettings>` části souboru app.config:

    ```xml
    <add key="appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext" value="true" />
    ```

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.6         |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=nameWithType>
