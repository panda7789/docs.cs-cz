---
ms.openlocfilehash: 0b42e320ba439a4cfc196471fc6dd4b3c15cd9d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859161"
---
### <a name="workflow-checksums-changed-from-md5-to-sha1"></a>Kontrolní součty pracovního postupu změněny z MD5 na SHA1

|   |   |
|---|---|
|Podrobnosti|Pro podporu ladění pomocí sady Visual Studio generuje za běhový čas pracovního postupu kontrolní součet pro instanci pracovního postupu pomocí algoritmu hash. V rozhraní .NET Framework 4.6.2 a starších verzích algoritmus hash kontrolního součtu pracovního postupu použil algoritmus MD5, který způsoboval problémy v systémech s podporou FIPS. Počínaje rozhraním .NET Framework 4.7 je algoritmus SHA1. Pokud váš kód má trvalé tyto kontrolní součty, budou nekompatibilní.|
|Návrh|Pokud váš kód nemůže načíst instance pracovního postupu z <code>AppContext</code> důvodu &quot;selhání kontrolního součtu, zkuste nastavit přepínač&quot; Switch.System.Activities.UseMD5ForWFDebugger na true. V kódu:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Activities.UseMD5ForWFDebugger&quot;, true);&#13;&#10;</code></pre>Nebo v konfiguraci:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Activities.UseMD5ForWFDebugger=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7|
|Typ|Změna cílení|
