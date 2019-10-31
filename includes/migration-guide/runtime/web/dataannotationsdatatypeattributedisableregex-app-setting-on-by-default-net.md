---
ms.openlocfilehash: 94c582d25ae1cd2249ed2e3774134a86cf77327b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085545"
---
### <a name="dataannotationsdatatypeattributedisableregex-app-setting-is-on-by-default-in-net-framework-472"></a>nastavení aplikace "DataAnnotations: dataTypeAttribute: disableRegEx" je ve výchozím nastavení zapnuté v .NET Framework 4.7.2

|   |   |
|---|---|
|Podrobnosti|V .NET Framework 4.6.1 bylo zavedeno nastavení aplikace (<code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code>), které umožňuje uživatelům zakázat použití regulárních výrazů v atributech datových typů (například <xref:System.ComponentModel.DataAnnotations.EmailAddressAttribute?displayProperty=nameWithType>, <xref:System.ComponentModel.DataAnnotations.UrlAttribute?displayProperty=nameWithType>a <xref:System.ComponentModel.DataAnnotations.PhoneAttribute?displayProperty=nameWithType>). To pomáhá snižovat zranitelnost zabezpečení, jako je například vyloučení možnosti útoku DOS pomocí konkrétních regulárních výrazů.<br/>V .NET Framework 4.6.1 bylo toto nastavení aplikace pro vypnutí použití regulárního výrazu ve výchozím nastavení nastaveno na hodnotu <code>false</code>. Počínaje .NET Framework 4.7.2 je tento přepínač konfigurace nastaven na <code>true</code> ve výchozím nastavení, aby bylo možné dále snižovat zabezpečení webových aplikací, které cílí na .NET Framework 4.7.2 a vyšší.|
|Doporučení|Pokud zjistíte, že tyto regulární výrazy ve webové aplikaci po upgradu na .NET Framework 4.7.2 nefungují, můžete aktualizovat hodnotu nastavení <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> na <code>false</code> a vrátit se k předchozímu chování.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot; value=&quot;false&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7.2|
|Typ|Modul runtime|
