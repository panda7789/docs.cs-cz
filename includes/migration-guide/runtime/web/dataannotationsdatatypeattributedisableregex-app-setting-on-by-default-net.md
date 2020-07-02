---
ms.openlocfilehash: f17efc89b738a9fd20cc687de1dae01a44664271
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621097"
---
### <a name="dataannotationsdatatypeattributedisableregex-app-setting-is-on-by-default-in-net-framework-472"></a>nastavení aplikace "DataAnnotations: dataTypeAttribute: disableRegEx" je ve výchozím nastavení zapnuté v .NET Framework 4.7.2

#### <a name="details"></a>Podrobnosti

V .NET Framework 4.6.1 <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> bylo zavedeno nastavení aplikace (), které umožňuje uživatelům zakázat použití regulárních výrazů v atributech datových typů (například <xref:System.ComponentModel.DataAnnotations.EmailAddressAttribute?displayProperty=nameWithType> , <xref:System.ComponentModel.DataAnnotations.UrlAttribute?displayProperty=nameWithType> a <xref:System.ComponentModel.DataAnnotations.PhoneAttribute?displayProperty=nameWithType> ). To pomáhá snižovat zranitelnost zabezpečení, jako je například vyloučení možnosti útoku DOS pomocí konkrétních regulárních výrazů.<br/>V .NET Framework 4.6.1 bylo toto nastavení aplikace pro vypnutí použití regulárního výrazu standardně nastaveno <code>false</code> . Počínaje .NET Framework 4.7.2 je tento přepínač konfigurace ve výchozím nastavení nastaven tak, <code>true</code> aby dále omezil zabezpečení webových aplikací, které cílí na .NET Framework 4.7.2 a vyšší.

#### <a name="suggestion"></a>Návrh

Pokud zjistíte, že tyto regulární výrazy ve webové aplikaci po upgradu na .NET Framework 4.7.2 nefungují, můžete aktualizovat hodnotu <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> nastavení na <code>false</code> předchozí chování.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot; value=&quot;false&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.7.2|
|Typ|Modul runtime|
