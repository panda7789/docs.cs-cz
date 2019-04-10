---
ms.openlocfilehash: 0b42e320ba439a4cfc196471fc6dd4b3c15cd9d2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236407"
---
### <a name="workflow-checksums-changed-from-md5-to-sha1"></a>Kontrolní součty pracovního postupu změněn z MD5, SHA1

|   |   |
|---|---|
|Podrobnosti|V zájmu podpory ladění pomocí sady Visual Studio generuje modul runtime pracovního postupu kontrolního součtu pro instanci pracovního postupu pomocí algoritmu hash. V rozhraní .NET Framework 4.6.2 a starší verze pracovního postupu kontrolní součet hash používá algoritmus MD5, který způsobil problémy s podporou standardu FIPS v systémech. Od verze rozhraní .NET Framework 4.7, se algoritmus SHA1. Pokud váš kód obsahuje trvalé těchto kontrolních součtů, budou kompatibilní.|
|Doporučení|Pokud váš kód nelze načíst instance pracovního postupu, protože došlo k chybě kontrolního součtu, zkuste <code>AppContext</code> přepnout &quot;Switch.System.Activities.UseMD5ForWFDebugger&quot; na hodnotu true. V kódu:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Activities.UseMD5ForWFDebugger&quot;, true);&#13;&#10;</code></pre>Nebo v konfiguraci:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Activities.UseMD5ForWFDebugger=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7|
|Type|Změna cílení|
