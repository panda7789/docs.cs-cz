---
ms.openlocfilehash: c5e4b5619394f99a419fe48aee190ad741ea8c0d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73041656"
---
### <a name="identity-ui-uses-static-web-assets-feature"></a>Identita: uživatelské rozhraní používá funkci statických webových prostředků.

ASP.NET Core 3,0 zavedlo funkci statického webového prostředku a uživatelské rozhraní identity ho přijalo.

#### <a name="change-description"></a>Změnit popis

Následkem toho, že uživatelské rozhraní identity přijímá funkci statických webových prostředků:

- Výběr architektury se dá provést pomocí vlastnosti `IdentityUIFrameworkVersion` v souboru projektu.
- Výchozím rozhraním uživatelského rozhraní identity je Bootstrap 4. Spouštěcí rutina 3 dosáhla konce životnosti a měli byste zvážit migraci na podporovanou verzi.

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Výchozí architektura uživatelského rozhraní pro uživatelské rozhraní identity byla **bootstrap 3**. ROZHRANÍ .NET Framework může být nakonfigurováno pomocí parametru pro volání metody `AddDefaultUI` v `Startup.ConfigureServices`.

#### <a name="new-behavior"></a>Nové chování

Výchozí architektura uživatelského rozhraní pro uživatelské rozhraní identity je **bootstrap 4**. ROZHRANÍ .NET Framework musí být nakonfigurováno v souboru projektu místo ve volání metody `AddDefaultUI`.

#### <a name="reason-for-change"></a>Důvod změny

Při přijetí funkce statických webových prostředků se vyžaduje, aby se konfigurace architektury uživatelského rozhraní přesunula na MSBuild. Rozhodnutí, na které rozhraní vkládat, je rozhodnutí o době sestavení, ne rozhodnutí za běhu.

#### <a name="recommended-action"></a>Doporučená akce

Zkontrolujte uživatelské rozhraní lokality a ujistěte se, že jsou nové součásti s rutinou Bootstrap 4 kompatibilní. V případě potřeby použijte vlastnost `IdentityUIFrameworkVersion` MSBuild a vraťte se k rutině Bootstrap 3. Přidejte vlastnost do prvku `<PropertyGroup>` v souboru projektu:

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
