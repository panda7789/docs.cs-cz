---
ms.openlocfilehash: eb89cbc72d8b09fd1aa5bc775a6c539eb208fa70
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614574"
---
### <a name="wpf-pointer-based-touch-stack"></a><span data-ttu-id="b40b3-101">Dotykové skládání na základě ukazatele WPF</span><span class="sxs-lookup"><span data-stu-id="b40b3-101">WPF Pointer-Based Touch Stack</span></span>

#### <a name="details"></a><span data-ttu-id="b40b3-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b40b3-102">Details</span></span>

<span data-ttu-id="b40b3-103">Tato změna přičítá možnost Povolit volitelnou sadu funkcí WPF Touch/Stylus založenou na WM_POINTER.</span><span class="sxs-lookup"><span data-stu-id="b40b3-103">This change adds the ability to enable an optional WM_POINTER based WPF touch/stylus stack.</span></span>  <span data-ttu-id="b40b3-104">Vývojáři, kteří to explicitně nepovolují, by se neměli měnit v chování WPF Touch/Stylus. Aktuální známé problémy s volitelnou WM_POINTERou dotykovou a stylusovou vrstvou:</span><span class="sxs-lookup"><span data-stu-id="b40b3-104">Developers that do not explicitly enable this should see no change in WPF touch/stylus behavior.Current Known Issues With optional WM_POINTER based touch/stylus stack:</span></span>

- <span data-ttu-id="b40b3-105">Žádná podpora pro psaní rukou v reálném čase.</span><span class="sxs-lookup"><span data-stu-id="b40b3-105">No support for real-time inking.</span></span>
- <span data-ttu-id="b40b3-106">I když budou rukopisné a StylusPlugIns – i nadále fungovat, budou zpracovány ve vlákně uživatelského rozhraní, což může vést k špatnému výkonu.</span><span class="sxs-lookup"><span data-stu-id="b40b3-106">While inking and StylusPlugins will still work, they will be processed on the UI Thread which can lead to poor performance.</span></span>
- <span data-ttu-id="b40b3-107">Změny chování kvůli změnám v povýšení událostí dotykového/stylusu na události myši</span><span class="sxs-lookup"><span data-stu-id="b40b3-107">Behavioral changes due to changes in promotion from touch/stylus events to mouse events</span></span>
- <span data-ttu-id="b40b3-108">Manipulace se může chovat jinak.</span><span class="sxs-lookup"><span data-stu-id="b40b3-108">Manipulation may behave differently</span></span>
- <span data-ttu-id="b40b3-109">Přetažením nebudete mít k dispozici odpovídající zpětnou vazbu k dotykovému vstupu.</span><span class="sxs-lookup"><span data-stu-id="b40b3-109">Drag/Drop will not show appropriate feedback for touch input</span></span>
- <span data-ttu-id="b40b3-110">To nemá vliv na vstup stylusu.</span><span class="sxs-lookup"><span data-stu-id="b40b3-110">This does not affect stylus input</span></span>
- <span data-ttu-id="b40b3-111">Přetažení už nejde iniciovat na událostech dotyku nebo stylusu.</span><span class="sxs-lookup"><span data-stu-id="b40b3-111">Drag/Drop can no longer be initiated on touch/stylus events</span></span>
- <span data-ttu-id="b40b3-112">To může potenciálně zablokovat aplikaci, dokud se nezjistí vstup z myši.</span><span class="sxs-lookup"><span data-stu-id="b40b3-112">This can potentially hang the application until mouse input is detected.</span></span>
- <span data-ttu-id="b40b3-113">Místo toho by vývojáři měli zahájit přetahování z událostí myši.</span><span class="sxs-lookup"><span data-stu-id="b40b3-113">Instead, developers should initiate drag and drop from mouse events.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b40b3-114">Návrh</span><span class="sxs-lookup"><span data-stu-id="b40b3-114">Suggestion</span></span>

<span data-ttu-id="b40b3-115">Vývojáři, kteří chtějí tuto sadu povolit, můžou do souboru App.config aplikace přidat nebo sloučit následující:</span><span class="sxs-lookup"><span data-stu-id="b40b3-115">Developers who wish to enable this stack can add/merge the following to their application's App.config file:</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Input.Stylus.EnablePointerSupport=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

<span data-ttu-id="b40b3-116">Odebráním tohoto nastavení nebo nastavením hodnoty na hodnotu false dojde k vypnutí tohoto volitelného zásobníku. Všimněte si, že tento zásobník je dostupný jenom pro Windows 10 Creators Update a novější.</span><span class="sxs-lookup"><span data-stu-id="b40b3-116">Removing this or setting the value to false will turn this optional stack off.Note that this stack is available only on Windows 10 Creators Update and above.</span></span>

| <span data-ttu-id="b40b3-117">Name</span><span class="sxs-lookup"><span data-stu-id="b40b3-117">Name</span></span>    | <span data-ttu-id="b40b3-118">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b40b3-118">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b40b3-119">Rozsah</span><span class="sxs-lookup"><span data-stu-id="b40b3-119">Scope</span></span>   | <span data-ttu-id="b40b3-120">Edge</span><span class="sxs-lookup"><span data-stu-id="b40b3-120">Edge</span></span>        |
| <span data-ttu-id="b40b3-121">Verze</span><span class="sxs-lookup"><span data-stu-id="b40b3-121">Version</span></span> | <span data-ttu-id="b40b3-122">4,7</span><span class="sxs-lookup"><span data-stu-id="b40b3-122">4.7</span></span>         |
| <span data-ttu-id="b40b3-123">Typ</span><span class="sxs-lookup"><span data-stu-id="b40b3-123">Type</span></span>    | <span data-ttu-id="b40b3-124">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="b40b3-124">Retargeting</span></span> |
