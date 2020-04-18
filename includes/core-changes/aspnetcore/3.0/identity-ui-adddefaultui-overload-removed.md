---
ms.openlocfilehash: 474f039cf00cb48761bfe7b7c4a0a9c6300cd820
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "81637194"
---
### <a name="identity-adddefaultui-method-overload-removed"></a>Identita: Přetížení metody AddDefaultUI bylo odebráno.

Počínaje ASP.NET Core 3.0, [identityBuilderUIExtensions.AddDefaultUI(IdentityBuilder,UIFramework)](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_) přetížení metody již neexistuje.

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="reason-for-change"></a>Důvod změny

Tato změna byla výsledkem přijetí funkce statické webové datové zdroje.

#### <a name="recommended-action"></a>Doporučená akce

Volání <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> namísto přetížení, které trvá dva argumenty. Pokud používáte Bootstrap 3, přidejte také `<PropertyGroup>` následující řádek do prvku v souboru projektu:

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

[IdentityBuilderUIExtensions.AddDefaultUI(IdentityBuilder,UIFramework)](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_)

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
