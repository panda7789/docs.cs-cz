---
ms.openlocfilehash: 135d59de135c8416d384b221379f912c8a9172ad
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621968"
---
### <a name="aspnet-incorrect-multipart-handling-may-result-in-lost-form-data"></a>ASP.NET nesprávné zpracování více částí může způsobit ztrátu dat z formuláře.

#### <a name="details"></a>Podrobnosti

V aplikacích, které cílí na .NET Framework 4.7.2 a starších verzí, může ASP.Net nesprávně analyzovat hodnoty mezních hodnot v částech, takže během provádění žádosti nejsou dostupná data formuláře. Aplikace, které cílí na .NET Framework 4,8 nebo novější verze správně analyzují data ze všech částí, takže hodnoty formulářů jsou k dispozici během provádění žádosti.

#### <a name="suggestion"></a>Návrh

Počínaje aplikacemi, které běží na .NET Framework 4,8, při cílení .NET Framework 4,8 nebo novějším pomocí <code>targetFrameworkVersion</code> elementu se výchozí chování změní na oddělovače pruhů. Když cílíte na předchozí verze rozhraní nebo nepoužíváte <code>targetFrameworkVersion</code> , koncové oddělovače pro některé hodnoty se pořád vrátí. Toto chování je možné také explicitně řídit pomocí <code>appSetting</code> :<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:UseLegacyMultiValueHeaderHandling&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Není známo|
|Verze|4,8|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Web.HttpRequest.Form?displayProperty=nameWithType></li><li><xref:System.Web.HttpRequest.Files?displayProperty=nameWithType></li><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|
