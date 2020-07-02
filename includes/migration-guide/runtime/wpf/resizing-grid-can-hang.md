---
ms.openlocfilehash: 86169b5c9a20678647153c951550e590a5bce588
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622236"
---
### <a name="resizing-a-grid-can-hang"></a><span data-ttu-id="dd5e9-101">Změna velikosti mřížky může zavěsit</span><span class="sxs-lookup"><span data-stu-id="dd5e9-101">Resizing a Grid can hang</span></span>

#### <a name="details"></a><span data-ttu-id="dd5e9-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="dd5e9-102">Details</span></span>

<span data-ttu-id="dd5e9-103">Nekonečná smyčka může nastat během rozložení <code>T:System.Windows.Controls.Grid</code> za následujících okolností:</span><span class="sxs-lookup"><span data-stu-id="dd5e9-103">An infinite loop can occur during layout of a <code>T:System.Windows.Controls.Grid</code> under the following circumstances:</span></span><ul><li><span data-ttu-id="dd5e9-104">Definice řádků obsahují dva \* řádky, deklaruje MinHeight a MaxHeight.</span><span class="sxs-lookup"><span data-stu-id="dd5e9-104">Row definitions contain two \*-rows, both declaring a MinHeight and a MaxHeight.</span></span></li><li><span data-ttu-id="dd5e9-105">Obsah \* řádků nepřekračuje odpovídající MaxHeight</span><span class="sxs-lookup"><span data-stu-id="dd5e9-105">Content of the \*-rows doesn't exceed the corresponding MaxHeight</span></span></li><li><span data-ttu-id="dd5e9-106">Dostupná výška mřížky se překročí prvním MinHeight (a dalšími pevnými nebo automatickými řádky).</span><span class="sxs-lookup"><span data-stu-id="dd5e9-106">The Grid's available height is exceeded by the first MinHeight (plus any other fixed or Auto rows)</span></span></li><li><span data-ttu-id="dd5e9-107">Cíle aplikace .NET Framework 4,7 nebo výslovný na algoritmus alokace 4,7 nastavením<code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></span><span class="sxs-lookup"><span data-stu-id="dd5e9-107">The app targets .NET Framework 4.7, or opts in to the 4.7 allocation algorithm by setting <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></span></span></li></ul><span data-ttu-id="dd5e9-108">Smyčka by také probíhala s více než dvěma řádky nebo v podobných případech pro sloupce.</span><span class="sxs-lookup"><span data-stu-id="dd5e9-108">The loop would also happen with more than two rows, or in the analogous case for columns.</span></span> <span data-ttu-id="dd5e9-109">Problém je vyřešen .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="dd5e9-109">The issue is fixed in .NET Framework 4.7.1.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="dd5e9-110">Návrh</span><span class="sxs-lookup"><span data-stu-id="dd5e9-110">Suggestion</span></span>

<span data-ttu-id="dd5e9-111">Upgradujte na .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="dd5e9-111">Upgrade to .NET Framework 4.7.1.</span></span>  <span data-ttu-id="dd5e9-112">Případně, pokud nepotřebujete algoritmus přidělování 4,7, můžete použít následující nastavení konfigurace:</span><span class="sxs-lookup"><span data-stu-id="dd5e9-112">Alternatively, if you don't need the 4.7 allocation algorithm you can use the following configuration setting:</span></span><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="dd5e9-113">Name</span><span class="sxs-lookup"><span data-stu-id="dd5e9-113">Name</span></span>    | <span data-ttu-id="dd5e9-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="dd5e9-114">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="dd5e9-115">Rozsah</span><span class="sxs-lookup"><span data-stu-id="dd5e9-115">Scope</span></span>   |<span data-ttu-id="dd5e9-116">Edge</span><span class="sxs-lookup"><span data-stu-id="dd5e9-116">Edge</span></span>|
|<span data-ttu-id="dd5e9-117">Verze</span><span class="sxs-lookup"><span data-stu-id="dd5e9-117">Version</span></span>|<span data-ttu-id="dd5e9-118">4,7</span><span class="sxs-lookup"><span data-stu-id="dd5e9-118">4.7</span></span>|
|<span data-ttu-id="dd5e9-119">Typ</span><span class="sxs-lookup"><span data-stu-id="dd5e9-119">Type</span></span>|<span data-ttu-id="dd5e9-120">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="dd5e9-120">Runtime</span></span>|
