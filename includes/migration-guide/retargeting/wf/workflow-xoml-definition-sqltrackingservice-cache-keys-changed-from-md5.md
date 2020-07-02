---
ms.openlocfilehash: 7a7ecf052276fe8e62463498b83230d466630c79
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616239"
---
### <a name="workflow-xoml-definition-and-sqltrackingservice-cache-keys-changed-from-md5-to-sha256"></a>Definice a klíče mezipaměti SqlTrackingService se změnily z procesu MD5 na SHA256.

#### <a name="details"></a>Podrobnosti

Modul runtime pracovního postupu v uchovává mezipaměť definicí pracovních postupů definovaných v XOML. SqlTrackingService také udržuje mezipaměť, která je označena řetězci. Tyto mezipaměti se účtují podle hodnot, které zahrnují hodnotu hash kontrolního součtu. V .NET Framework 4.7.2 a dřívějších verzích tato kontrolní hodnota hash použila algoritmus MD5, který způsobil problémy se systémy s podporou standardu FIPS. Počínaje .NET Framework 4,8 se používá algoritmus SHA256. Při této změně by neměl dojít k potížím s kompatibilitou, protože hodnoty jsou přepočítány pokaždé, když je spuštěn modul runtime pracovního postupu a SqlTrackingService. Poskytli jsme ale adaptivní, abychom zákazníkům umožnili vrátit se k využití staršího algoritmu hash, pokud je to potřeba.

#### <a name="suggestion"></a>Návrh

Pokud tato změna představuje problém při provádění pracovních postupů, zkuste nastavit jeden nebo oba `AppContext` přepínače:

- &quot;Switch.System. Workflow. Runtime. UseLegacyHashForWorkflowDefinitionDispenserCacheKey &quot; na hodnotu true.
- &quot;Switch.System. Workflow. Runtime. UseLegacyHashForSqlTrackingCacheKey &quot; na hodnotu true.
V kódu:

<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot;, true);&#13;&#10;System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot;, true);&#13;&#10;</code></pre>

Nebo v konfiguračním souboru (musí být v konfiguračním souboru pro aplikaci, která vytváří <xref:System.Workflow.Runtime.WorkflowRuntime> objekt):

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey=true&quot; /&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKeytrue&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4,8         |
| Typ    | Změna cílení |
