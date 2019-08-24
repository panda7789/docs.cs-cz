---
ms.openlocfilehash: 3b94c88809513e31a5f226bcfce39abbfa4de378
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70017369"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a>ASP.NET parametr ValidationContext. member není NULL při použití vlastních DataAnnotations. ValidationAttribute

|   |   |
|---|---|
|Podrobnosti|V .NET Framework 4.7.2 a starších verzích při použití vlastní <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType> <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> vlastnost se vrátí <code>null</code>.  V .NET Framework 4,8 vrátí název člena.|
|Doporučení|Předchozí chování obnovíte přidáním následujícího nastavení do konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Toto chování se změní v nadcházející verzi služby, když budete muset explicitně vyjádřit nové chování. Vlastnost vrátí hodnotu, která není null pro vlastní `ValidationAttribute` , `aspnet:GetValidationMemberName` Pokud je přepínač nastaven na `true`hodnotu.|
|Scope|Neznámé|
|Version|4.8|
|type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|
