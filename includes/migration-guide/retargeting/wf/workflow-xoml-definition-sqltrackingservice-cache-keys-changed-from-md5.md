---
ms.openlocfilehash: 82e2794f262548105f9b7cb12204eaa8138e0630
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783203"
---
### <a name="workflow-xoml-definition-and-sqltrackingservice-cache-keys-changed-from-md5-to-sha256"></a>Definici XOML pracovního postupu a klíče mezipaměti SqlTrackingService změnil z MD5 SHA256

|   |   |
|---|---|
|Podrobnosti|Modul Runtime pracovního postupu v udržuje mezipaměť definice pracovního postupu v XOML. SqlTrackingService také udržuje mezipaměť, která je s klíči řetězce. Tyto mezipaměti jsou klíčovány pomocí hodnot, které zahrnují součet hash. V rozhraní .NET Framework 4.7.2 a dřívějších verzích Tento kontrolní součet hash používá algoritmus MD5, který způsobil problémy s podporou standardu FIPS v systémech. Počínaje 4.8 rozhraní .NET Framework, je použitý algoritmus SHA256. Nesmí být problém kompatibilita s touto změnou vzhledem k tomu, že hodnoty se přepočítávají pokaždé, když je spuštěn modul Runtime pracovního postupu a SqlTrackingService. Ale uvádíme adaptivní tak, aby zákazníci chtít vrátit k používání starší verze algoritmu hash v případě potřeby.|
|Doporučení|Pokud se tato změna představuje problém při provádění pracovních postupů, zkuste jeden nebo oba <code>AppContext</code> přepínače:<ul><li>&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot; to true.</li><li>&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot; to true.</li></ul>V kódu:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot;, true);&#13;&#10;System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot;, true);&#13;&#10;</code></pre>Nebo v konfiguračním souboru (Toto musí být v konfiguračním souboru aplikace, který vytváří <xref:System.Workflow.Runtime.WorkflowRuntime> objekt):<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey=true&quot; /&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKeytrue&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.8|
|Type|Změna cílení|
