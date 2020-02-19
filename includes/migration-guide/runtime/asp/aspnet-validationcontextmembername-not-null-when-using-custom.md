---
ms.openlocfilehash: c0be08023f80bf0f96cc08f34b9ea8c5a73839e3
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77466063"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a>ASP.NET parametr ValidationContext. member není NULL při použití vlastních DataAnnotations. ValidationAttribute

|   |   |
|---|---|
|Podrobnosti|V .NET Framework 4.7.2 a starších verzích při použití vlastního <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>vrátí vlastnost <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> `null`. Ve verzi .NET Framework 4,8 před aktualizací z října 2019 vrátí název člena. Počínaje [.NET Framework říjen 2019 Preview o kumulativní kvalitě](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) pro .NET Framework 4,8 vrátí `null` ve výchozím nastavení, ale můžete se přihlásit a místo toho vrátit název člena. |
|Návrh|Přidejte následující nastavení do souboru *Web. config* , aby vlastnost vrátila název člena v [.NET Framework říjnu 2019 Preview kumulativní kvality](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) pro .NET Framework 4,8 a novější verze:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Ve verzi .NET Framework 4,8 před aktualizací z října 2019 je toto přidání do souboru *Web. config* obnoví předchozí chování a vlastnost vrátí `null`.|
|Rozsah|Není známo|
|Verze|4.8|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|
