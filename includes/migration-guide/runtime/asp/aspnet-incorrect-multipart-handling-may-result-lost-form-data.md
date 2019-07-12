---
ms.openlocfilehash: 6a99ed916e4e86e85d7ebc2d6ea36a6372c00206
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802675"
---
### <a name="aspnet-incorrect-multipart-handling-may-result-in-lost-form-data"></a>Nesprávné zpracování s více částmi. technologie ASP.NET může vést ke ztrátě dat.

|   |   |
|---|---|
|Podrobnosti|V aplikacích, které jsou cíleny na rozhraní .NET Framework 4.7.2 a starší verze technologie ASP.Net může být nesprávně analyzovat hodnoty hranic s více částmi. výsledkem dat formuláře nedostupnosti během provádění požadavku. Aplikací určených pro rozhraní .NET Framework 4.8 nebo novější verze správně analyzovat s více částmi. data, takže formulář hodnoty jsou k dispozici během provádění požadavku.|
|Doporučení|Spouští se k aplikacím běžícím v rozhraní .NET Framework 4.8, při cílení na rozhraní .NET Framework 4.8 nebo novější pomocí <code>targetFrameworkVersion</code> element, změní výchozí chování pro odstranění oddělovače. Při cílení na předchozí verze rozhraní framework nebo bez použití <code>targetFrameworkVersion</code>, koncové oddělovače pro některé hodnoty jsou stále vrátil. Toto chování je také možné explicitně řídit pomocí <code>appSetting</code>:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:UseLegacyMultiValueHeaderHandling&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Scope|Neznámé|
|Version|4.8|
|type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Web.HttpRequest.Form?displayProperty=nameWithType></li><li><xref:System.Web.HttpRequest.Files?displayProperty=nameWithType></li><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|

