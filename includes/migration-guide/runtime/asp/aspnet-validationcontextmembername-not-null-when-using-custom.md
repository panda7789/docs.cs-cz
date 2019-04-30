---
ms.openlocfilehash: 86cb328052c7a643cbd6080d222348d40179fdad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61764416"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a>ValidationContext.MemberName technologie ASP.NET nemá hodnotu NULL, při použití vlastního DataAnnotations.ValidationAttribute

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.7.2 a předchozími verzemi, při použití vlastního <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>, <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> vrátí vlastnost <code>null</code>.  V rozhraní .NET Framework 4.8 vrátí název člena.|
|Doporučení|Výchozí chování <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> vlastnosti zůstávají stejné.  Načíst platnou hodnotu z <code>ValidationContext.MemberName</code> vlastnost, přidejte následující nastavení do konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Neznámé|
|Version|4.8|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|
