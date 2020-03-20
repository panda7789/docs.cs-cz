---
ms.openlocfilehash: c0be08023f80bf0f96cc08f34b9ea8c5a73839e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77466063"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a>ASP.NET ValidationContext.MemberName není null při použití vlastních datAnnotations.ValidationAttribute

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.7.2 a starších <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> verzích `null`při použití vlastní <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>, vlastnost vrátí . Ve verzi rozhraní .NET Framework 4.8 před aktualizací z října 2019 vrátí název člena. Počínaje [rozhraním .NET Framework říjen 2019 Náhled souhrnu kvality](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) pro `null` rozhraní .NET Framework 4.8 se vrátí ve výchozím nastavení, ale místo toho se můžete přihlásit a vrátit název člena. |
|Návrh|Přidejte do souboru *web.config* následující nastavení, ve které chcete vlastnost vrátit název člena v [rozhraní .NET Framework říjen 2019 Náhled souhrnu kvality](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) pro rozhraní .NET Framework 4.8 a novější verze:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Ve verzi rozhraní .NET Framework 4.8 před aktualizací z října 2019 obnoví přidání do souboru *web.config* předchozí chování a vrátí vlastnost `null`.|
|Rozsah|Není známo|
|Version|4.8|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|
