---
ms.openlocfilehash: f907cb1939e111c586d68243e6b8a8e291974e36
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615720"
---
### <a name="wpf-layout-rounding-of-margins-has-changed"></a><span data-ttu-id="e11fd-101">Změnilo se zaokrouhlování rozložení WPF pro okraje.</span><span class="sxs-lookup"><span data-stu-id="e11fd-101">WPF layout rounding of margins has changed</span></span>

#### <a name="details"></a><span data-ttu-id="e11fd-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e11fd-102">Details</span></span>

<span data-ttu-id="e11fd-103">Způsob, jakým jsou zaoblené okraje zaokrouhleny a ohraničení a pozadí uvnitř nich bylo změněno.</span><span class="sxs-lookup"><span data-stu-id="e11fd-103">The way in which margins are rounded and borders and the background inside of them has changed.</span></span> <span data-ttu-id="e11fd-104">V důsledku této změny:</span><span class="sxs-lookup"><span data-stu-id="e11fd-104">As a result of this change:</span></span>

- <span data-ttu-id="e11fd-105">Šířka nebo výška prvků může být zvětšena nebo zmenšena o jeden pixel.</span><span class="sxs-lookup"><span data-stu-id="e11fd-105">The width or height of elements may grow or shrink by at most one pixel.</span></span>
- <span data-ttu-id="e11fd-106">Umístění objektu lze přesunout o jeden pixel.</span><span class="sxs-lookup"><span data-stu-id="e11fd-106">The placement of an object can move by at most one pixel.</span></span>
- <span data-ttu-id="e11fd-107">Centrované elementy můžou být svisle nebo vodorovně mimo střed o jeden pixel.</span><span class="sxs-lookup"><span data-stu-id="e11fd-107">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>
<span data-ttu-id="e11fd-108">Ve výchozím nastavení je toto nové rozložení povolené jenom pro aplikace, které cílí na .NET Framework 4,6.</span><span class="sxs-lookup"><span data-stu-id="e11fd-108">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e11fd-109">Návrh</span><span class="sxs-lookup"><span data-stu-id="e11fd-109">Suggestion</span></span>

<span data-ttu-id="e11fd-110">Vzhledem k tomu, že tato změna je v úmyslu zabránit tomu, aby se vyloučilo oříznutí pravé nebo dolní části ovládacích prvků WPF s vysokou dpi, aplikace, které cílí na starší verze .NET Framework, ale jsou spuštěné v .NET Framework 4,6, se můžou na toto nové chování zúčastnit přidáním následujícího řádku do `<runtime>` oddílu app.config souboru:</span><span class="sxs-lookup"><span data-stu-id="e11fd-110">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false&quot; /&gt;&#39;&#13;&#10;</code></pre>

<span data-ttu-id="e11fd-111">Aplikace cílené na .NET Framework 4,6, ale chcete, aby ovládací prvky WPF vykreslují pomocí předchozího algoritmu rozložení, mohou tak učinit přidáním následujícího řádku do `<runtime>` části app.config souboru:</span><span class="sxs-lookup"><span data-stu-id="e11fd-111">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the `<runtime>` section of the app.config file:</span></span>

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true&quot; /&gt;&#39;.&#13;&#10;</code></pre>

| <span data-ttu-id="e11fd-112">Name</span><span class="sxs-lookup"><span data-stu-id="e11fd-112">Name</span></span>    | <span data-ttu-id="e11fd-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e11fd-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e11fd-114">Rozsah</span><span class="sxs-lookup"><span data-stu-id="e11fd-114">Scope</span></span>   | <span data-ttu-id="e11fd-115">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="e11fd-115">Minor</span></span>       |
| <span data-ttu-id="e11fd-116">Verze</span><span class="sxs-lookup"><span data-stu-id="e11fd-116">Version</span></span> | <span data-ttu-id="e11fd-117">4.6</span><span class="sxs-lookup"><span data-stu-id="e11fd-117">4.6</span></span>         |
| <span data-ttu-id="e11fd-118">Typ</span><span class="sxs-lookup"><span data-stu-id="e11fd-118">Type</span></span>    | <span data-ttu-id="e11fd-119">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="e11fd-119">Retargeting</span></span> |
