---
ms.openlocfilehash: 7002c74594993ac6bf28643ef3271da356190c66
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621967"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a>ASP.NET parametr ValidationContext. member není NULL při použití vlastních DataAnnotations. ValidationAttribute

#### <a name="details"></a>Podrobnosti

V .NET Framework 4.7.2 a starších verzích při použití vlastní vlastnost se <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType> <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> vrátí `null` . Ve verzi .NET Framework 4,8 před aktualizací z října 2019 vrátí název člena. Počínaje [.NET Framework říjen 2019 Preview se souhrnem kvality](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) pro .NET Framework 4,8 vrátí `null` ve výchozím nastavení, ale můžete se přihlásit a místo toho vrátit název člena.

#### <a name="suggestion"></a>Návrh

Přidejte následující nastavení do souboru *web.config* , aby vlastnost vrátila název člena v [.NET Framework říjnu 2019 Preview kumulativní kvality](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) pro .NET Framework 4,8 a novější verze:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Ve verzi .NET Framework 4,8 před aktualizací z října 2019 je přidáním tohoto souboru do *web.config* obnoven předchozí chování a vrátí se vlastnost `null` .

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Není známo|
|Verze|4,8|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|
