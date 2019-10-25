---
ms.openlocfilehash: 4254cceab0048341b32fe5babf53b5ea3e5a52d6
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "72846997"
---
### <a name="workflow-xoml-definition-and-sqltrackingservice-cache-keys-changed-from-md5-to-sha256"></a>Definice a klíče mezipaměti SqlTrackingService se změnily z procesu MD5 na SHA256.

|   |   |
|---|---|
|Podrobnosti|Modul runtime pracovního postupu v uchovává mezipaměť definicí pracovních postupů definovaných v XOML. SqlTrackingService také udržuje mezipaměť, která je označena řetězci. Tyto mezipaměti se účtují podle hodnot, které zahrnují hodnotu hash kontrolního součtu. V .NET Framework 4.7.2 a dřívějších verzích tato kontrolní hodnota hash použila algoritmus MD5, který způsobil problémy se systémy s podporou standardu FIPS. Počínaje .NET Framework 4,8 se používá algoritmus SHA256. Při této změně by neměl dojít k potížím s kompatibilitou, protože hodnoty jsou přepočítány pokaždé, když je spuštěn modul runtime pracovního postupu a SqlTrackingService. Poskytli jsme ale adaptivní, abychom zákazníkům umožnili vrátit se k využití staršího algoritmu hash, pokud je to potřeba.|
|Doporučení|Pokud tato změna představuje problém při provádění pracovních postupů, zkuste nastavit jeden nebo oba přepínače <code>AppContext</code>:<ul><li>&quot;přepínač. System. Workflow. Runtime. UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot; na hodnotu true.</li><li>&quot;přepínač. System. Workflow. Runtime. UseLegacyHashForSqlTrackingCacheKey&quot; na hodnotu true.</li></ul>V kódu:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot;, true);&#13;&#10;System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot;, true);&#13;&#10;</code></pre>Nebo v konfiguračním souboru (musí být v konfiguračním souboru pro aplikaci, která vytváří objekt <xref:System.Workflow.Runtime.WorkflowRuntime>):<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey=true&quot; /&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKeytrue&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4,8|
|Typ|Změna cílení|
