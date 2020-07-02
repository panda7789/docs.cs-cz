---
ms.openlocfilehash: 7a7ecf052276fe8e62463498b83230d466630c79
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616239"
---
### <a name="workflow-xoml-definition-and-sqltrackingservice-cache-keys-changed-from-md5-to-sha256"></a><span data-ttu-id="c4703-101">Definice a klíče mezipaměti SqlTrackingService se změnily z procesu MD5 na SHA256.</span><span class="sxs-lookup"><span data-stu-id="c4703-101">Workflow XOML definition and SqlTrackingService cache keys changed from MD5 to SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="c4703-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="c4703-102">Details</span></span>

<span data-ttu-id="c4703-103">Modul runtime pracovního postupu v uchovává mezipaměť definicí pracovních postupů definovaných v XOML.</span><span class="sxs-lookup"><span data-stu-id="c4703-103">The Workflow Runtime in keeps a cache of workflow definitions defined in XOML.</span></span> <span data-ttu-id="c4703-104">SqlTrackingService také udržuje mezipaměť, která je označena řetězci.</span><span class="sxs-lookup"><span data-stu-id="c4703-104">The SqlTrackingService also keeps a cache that is keyed by strings.</span></span> <span data-ttu-id="c4703-105">Tyto mezipaměti se účtují podle hodnot, které zahrnují hodnotu hash kontrolního součtu.</span><span class="sxs-lookup"><span data-stu-id="c4703-105">These caches are keyed by values that include checksum hash value.</span></span> <span data-ttu-id="c4703-106">V .NET Framework 4.7.2 a dřívějších verzích tato kontrolní hodnota hash použila algoritmus MD5, který způsobil problémy se systémy s podporou standardu FIPS.</span><span class="sxs-lookup"><span data-stu-id="c4703-106">In the .NET Framework 4.7.2 and earlier versions, this checksum hashing used the MD5 algorithm, which caused issues on FIPS-enabled systems.</span></span> <span data-ttu-id="c4703-107">Počínaje .NET Framework 4,8 se používá algoritmus SHA256. Při této změně by neměl dojít k potížím s kompatibilitou, protože hodnoty jsou přepočítány pokaždé, když je spuštěn modul runtime pracovního postupu a SqlTrackingService.</span><span class="sxs-lookup"><span data-stu-id="c4703-107">Starting with the .NET Framework 4.8, the algorithm used is SHA256.There shouldn't be a compatibility issue with this change because the values are recalculated each time the Workflow Runtime and SqlTrackingService is started.</span></span> <span data-ttu-id="c4703-108">Poskytli jsme ale adaptivní, abychom zákazníkům umožnili vrátit se k využití staršího algoritmu hash, pokud je to potřeba.</span><span class="sxs-lookup"><span data-stu-id="c4703-108">However, we have provided quirks to allow customers to revert back to usage of the legacy hashing algorithm, if necessary.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c4703-109">Návrh</span><span class="sxs-lookup"><span data-stu-id="c4703-109">Suggestion</span></span>

<span data-ttu-id="c4703-110">Pokud tato změna představuje problém při provádění pracovních postupů, zkuste nastavit jeden nebo oba `AppContext` přepínače:</span><span class="sxs-lookup"><span data-stu-id="c4703-110">If this change presents a problem when executing workflows, try setting one or both of the `AppContext` switches:</span></span>

- <span data-ttu-id="c4703-111">&quot;Switch.System. Workflow. Runtime. UseLegacyHashForWorkflowDefinitionDispenserCacheKey &quot; na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="c4703-111">&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot; to true.</span></span>
- <span data-ttu-id="c4703-112">&quot;Switch.System. Workflow. Runtime. UseLegacyHashForSqlTrackingCacheKey &quot; na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="c4703-112">&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot; to true.</span></span>
<span data-ttu-id="c4703-113">V kódu:</span><span class="sxs-lookup"><span data-stu-id="c4703-113">In code:</span></span>

<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot;, true);&#13;&#10;System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot;, true);&#13;&#10;</code></pre>

<span data-ttu-id="c4703-114">Nebo v konfiguračním souboru (musí být v konfiguračním souboru pro aplikaci, která vytváří <xref:System.Workflow.Runtime.WorkflowRuntime> objekt):</span><span class="sxs-lookup"><span data-stu-id="c4703-114">Or in the configuration file (this needs to be in the config file for the application that is creating the <xref:System.Workflow.Runtime.WorkflowRuntime> object):</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey=true&quot; /&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKeytrue&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="c4703-115">Name</span><span class="sxs-lookup"><span data-stu-id="c4703-115">Name</span></span>    | <span data-ttu-id="c4703-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="c4703-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c4703-117">Rozsah</span><span class="sxs-lookup"><span data-stu-id="c4703-117">Scope</span></span>   | <span data-ttu-id="c4703-118">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="c4703-118">Minor</span></span>       |
| <span data-ttu-id="c4703-119">Verze</span><span class="sxs-lookup"><span data-stu-id="c4703-119">Version</span></span> | <span data-ttu-id="c4703-120">4,8</span><span class="sxs-lookup"><span data-stu-id="c4703-120">4.8</span></span>         |
| <span data-ttu-id="c4703-121">Typ</span><span class="sxs-lookup"><span data-stu-id="c4703-121">Type</span></span>    | <span data-ttu-id="c4703-122">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="c4703-122">Retargeting</span></span> |
