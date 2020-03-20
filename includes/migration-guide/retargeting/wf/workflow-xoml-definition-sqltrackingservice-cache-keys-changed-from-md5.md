---
ms.openlocfilehash: 4254cceab0048341b32fe5babf53b5ea3e5a52d6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "72846997"
---
### <a name="workflow-xoml-definition-and-sqltrackingservice-cache-keys-changed-from-md5-to-sha256"></a>Definice jazyka AOML pracovního postupu a klíče mezipaměti SqlTrackingService byly změněny z MD5 na SHA256

|   |   |
|---|---|
|Podrobnosti|Runtime pracovního postupu v aplikaci uchovává mezipaměť definic pracovních postupů definovaných v XOML. Služba SqlTrackingService také uchovává mezipaměť, která je zamýšlena řetězci. Tyto mezipaměti jsou zakódovány hodnotami, které obsahují hodnotu hash kontrolního součtu. V rozhraní .NET Framework 4.7.2 a starších verzích tento algoritmus hash kontrolního součtu používal algoritmus MD5, který způsoboval problémy v systémech s podporou FIPS. Počínaje rozhraním .NET Framework 4.8 je použitý algoritmus SHA256. S touto změnou by neměl být problém s kompatibilitou, protože hodnoty jsou přepočítány při každém spuštění modulu Runtime pracovního postupu a služby SqlTrackingService. Poskytli jsme však vtípky, které zákazníkům umožňují vrátit se zpět k používání staršího algoritmu hash, pokud je to nutné.|
|Návrh|Pokud tato změna představuje problém při provádění pracovních postupů, <code>AppContext</code> zkuste nastavit jeden nebo oba přepínače:<ul><li>&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot; na true.</li><li>&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot; na true.</li></ul>V kódu:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot;, true);&#13;&#10;System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot;, true);&#13;&#10;</code></pre>Nebo v konfiguračním souboru (to musí být v <xref:System.Workflow.Runtime.WorkflowRuntime> konfiguračním souboru pro aplikaci, která vytváří objekt):<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey=true&quot; /&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKeytrue&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.8|
|Typ|Změna cílení|
