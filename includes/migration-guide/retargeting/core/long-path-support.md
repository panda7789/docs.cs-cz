---
ms.openlocfilehash: 506218195417548880a9d8d10508a570a7769682
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859249"
---
### <a name="long-path-support"></a>Podpora dlouhých cest

|   |   |
|---|---|
|Podrobnosti|Počínaje aplikacemi, které cílí na rozhraní .NET Framework 4.6.2, jsou podporovány dlouhé cesty (až <code>MAX_PATH</code>32 kB znaků) a bylo odebráno omezení délky cesty o 260 znaků (nebo ) . Pro aplikace, které jsou překompilovány na cíl .NET Framework 4.6.2, cesty kódu, který dříve <xref:System.IO.PathTooLongException?displayProperty=name> <xref:System.IO.PathTooLongException?displayProperty=name> hodil, protože cesta překročila 260 znaků, nyní vyvolá pouze za následujících podmínek:<ul><li>Délka cesty je větší <xref:System.Int16.MaxValue> než (32 767) znaků.</li><li>Operační systém <code>COR_E_PATHTOOLONG</code> vrátí nebo jeho ekvivalent.</li></ul>Pro aplikace, které cílí na rozhraní .NET Framework 4.6.1 <xref:System.IO.PathTooLongException?displayProperty=name> a starší verze, runtime automaticky vyvolá vždy, když cesta překročí 260 znaků.|
|Návrh|U aplikací, které cílí na rozhraní .NET Framework 4.6.2, se můžete odhlásit <code>&lt;runtime&gt;</code> z podpory <code>app.config</code> dlouhé cesty, pokud to není žádoucí, přidáním následujícího textu do části souboru:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.BlockLongPaths=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>U aplikací, které cílí na starší verze rozhraní .NET Framework, ale běží v rozhraní .NET Framework 4.6.2 nebo novějším, se můžete přihlásit k podpoře dlouhé cesty přidáním následujících položek do <code>&lt;runtime&gt;</code> části <code>app.config</code> souboru:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.BlockLongPaths=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.6.2|
|Typ|Změna cílení|
