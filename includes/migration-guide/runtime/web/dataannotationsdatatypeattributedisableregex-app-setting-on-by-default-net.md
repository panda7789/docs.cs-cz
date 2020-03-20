---
ms.openlocfilehash: 94c582d25ae1cd2249ed2e3774134a86cf77327b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73085545"
---
### <a name="dataannotationsdatatypeattributedisableregex-app-setting-is-on-by-default-in-net-framework-472"></a>"dataAnnotations:dataTypeAttribute:disableRegEx" je ve výchozím nastavení zapnuto v rozhraní .NET Framework 4.7.2

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6.1<code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code>bylo zavedeno nastavení aplikace ( ), které uživatelům umožňuje zakázat <xref:System.ComponentModel.DataAnnotations.EmailAddressAttribute?displayProperty=nameWithType>používání <xref:System.ComponentModel.DataAnnotations.UrlAttribute?displayProperty=nameWithType>regulárních výrazů v atributech datového typu (například , a <xref:System.ComponentModel.DataAnnotations.PhoneAttribute?displayProperty=nameWithType>). To pomáhá snížit zranitelnost zabezpečení, například vyhnout se možnosti útoku odmítnutí služby pomocí specifických regulárních výrazů.<br/>V rozhraní .NET Framework 4.6.1 bylo toto nastavení <code>false</code> aplikace pro zakázání využití regexu ve výchozím nastavení nastaveno na hodnotu. Počínaje rozhraním .NET Framework 4.7.2 je <code>true</code> tento přepínač konfigurace ve výchozím nastavení nastaven na hodnotu dále snížit zabezpečení webových aplikací, které cílí na rozhraní .NET Framework 4.7.2 a vyšší.|
|Návrh|Pokud zjistíte, že regulární výrazy ve webové aplikaci nefungují po upgradu na rozhraní <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> .NET <code>false</code> Framework 4.7.2, můžete aktualizovat hodnotu nastavení a vrátit se k předchozímu chování.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot; value=&quot;false&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7.2|
|Typ|Modul runtime|
