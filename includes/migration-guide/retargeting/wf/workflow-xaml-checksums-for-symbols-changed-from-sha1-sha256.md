---
ms.openlocfilehash: f814703e187726d3988787fac52e5049988fd4d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803452"
---
### <a name="workflow-xaml-checksums-for-symbols-changed-from-sha1-to-sha256"></a>Kontrolní součty XAML pracovního postupu pro symboly změněné ze SHA1 na SHA256

|   |   |
|---|---|
|Podrobnosti|Pro podporu ladění pomocí sady Visual Studio generuje za běhový čas pracovního postupu kontrolní součet pro soubor XAML pracovního postupu pomocí algoritmu hash. V rozhraní .NET Framework 4.6.2 a starších verzích algoritmus hash kontrolního součtu pracovního postupu použil algoritmus MD5, který způsoboval problémy v systémech s podporou FIPS. Počínaje rozhraním .NET Framework 4.7 byl výchozí algoritmus změněn na SHA1. Počínaje rozhraním .NET Framework 4.8 byl výchozí algoritmus změněn na SHA256.|
|Návrh|Pokud váš kód není schopen načíst instance pracovního postupu nebo najít příslušné <code>AppContext</code> &quot;symboly z důvodu selhání kontrolního součtu,&quot; zkuste nastavit přepínač Switch.System.Activities.UseSHA1HashForDebuggerSymbols na true. V kódu:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Activities.UseSHA1HashForDebuggerSymbols&quot;, true);&#13;&#10;</code></pre>Nebo v konfiguraci:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Activities.UseSHA1HashForDebuggerSymbols=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.8|
|Typ|Změna cílení|
