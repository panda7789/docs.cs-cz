---
ms.openlocfilehash: e6b0387d9d04aa979de289ea0c5caa6c76f4d1be
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802675"
---
### <a name="aspnet-incorrect-multipart-handling-may-result-in-lost-form-data"></a>ASP.NET Nesprávné vícedílné zpracování může způsobit ztrátu dat formuláře.

|   |   |
|---|---|
|Podrobnosti|V aplikacích, které cílí na rozhraní .NET Framework 4.7.2 a starší verze, může ASP.Net nesprávně analyzovat vícedílné hraniční hodnoty, což vede k tomu, že data formuláře nejsou během provádění požadavku k dispozici. Aplikace, které cílí na rozhraní .NET Framework 4.8 nebo novější verze správně analyzovat vícedílná data, takže hodnoty formuláře jsou k dispozici během provádění požadavku.|
|Návrh|Počínaje aplikacemi spuštěnými v rozhraní .NET Framework 4.8 při cílení <code>targetFrameworkVersion</code> na rozhraní .NET Framework 4.8 nebo novější pomocí prvku se výchozí chování změní na oddělovače pruhů. Při cílení předchozí verze architektury <code>targetFrameworkVersion</code>nebo nepoužíváte , koncové oddělovače pro některé hodnoty jsou stále vráceny. Toto chování lze také <code>appSetting</code>explicitně ovládat pomocí :<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:UseLegacyMultiValueHeaderHandling&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Není známo|
|Version|4.8|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Web.HttpRequest.Form?displayProperty=nameWithType></li><li><xref:System.Web.HttpRequest.Files?displayProperty=nameWithType></li><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|
