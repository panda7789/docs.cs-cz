---
title: 'Postupy: Implementace rozhraní PriorityBinding'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
ms.openlocfilehash: 343b0aca4736905f3a0cbff5a0f76b170da0c920
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459783"
---
# <a name="how-to-implement-prioritybinding"></a><span data-ttu-id="6bb8d-102">Postupy: Implementace rozhraní PriorityBinding</span><span class="sxs-lookup"><span data-stu-id="6bb8d-102">How to: Implement PriorityBinding</span></span>
<span data-ttu-id="6bb8d-103"><xref:System.Windows.Data.PriorityBinding> v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] funguje tak, že se určí seznam vazeb.</span><span class="sxs-lookup"><span data-stu-id="6bb8d-103"><xref:System.Windows.Data.PriorityBinding> in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] works by specifying a list of bindings.</span></span> <span data-ttu-id="6bb8d-104">Seznam vazeb je seřazen od nejvyšší priority až po nejnižší prioritu.</span><span class="sxs-lookup"><span data-stu-id="6bb8d-104">The list of bindings is ordered from highest priority to lowest priority.</span></span> <span data-ttu-id="6bb8d-105">Pokud vazba s nejvyšší prioritou vrátí hodnotu úspěšně při zpracování, pak není nikdy nutné zpracovat ostatní vazby v seznamu.</span><span class="sxs-lookup"><span data-stu-id="6bb8d-105">If the highest priority binding returns a value successfully when it is processed then there is never a need to process the other bindings in the list.</span></span> <span data-ttu-id="6bb8d-106">Může se jednat o případ, že je vyhodnocování vazby s nejvyšší prioritou trvat dlouhou dobu, bude použita další nejvyšší priorita, která vrátí hodnotu, dokud vazba s vyšší prioritou nevrátí hodnotu úspěšně.</span><span class="sxs-lookup"><span data-stu-id="6bb8d-106">It could be the case that the highest priority binding takes a long time to be evaluated, the next highest priority that returns a value successfully will be used until a binding of a higher priority returns a value successfully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bb8d-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="6bb8d-107">Example</span></span>  
 <span data-ttu-id="6bb8d-108">Chcete-li předvést, jak <xref:System.Windows.Data.PriorityBinding> funguje, byl vytvořen objekt `AsyncDataSource` pomocí následujících tří vlastností: `FastDP`, `SlowerDP`a `SlowestDP`.</span><span class="sxs-lookup"><span data-stu-id="6bb8d-108">To demonstrate how <xref:System.Windows.Data.PriorityBinding> works, the `AsyncDataSource` object has been created with the following three properties: `FastDP`, `SlowerDP`, and `SlowestDP`.</span></span>  
  
 <span data-ttu-id="6bb8d-109">Přistupující objekt get pro `FastDP` vrací hodnotu datového členu `_fastDP`.</span><span class="sxs-lookup"><span data-stu-id="6bb8d-109">The get accessor of `FastDP` returns the value of the `_fastDP` data member.</span></span>  
  
 <span data-ttu-id="6bb8d-110">Přistupující objekt get pro `SlowerDP` čeká 3 sekundy před vrácením hodnoty datového členu `_slowerDP`.</span><span class="sxs-lookup"><span data-stu-id="6bb8d-110">The get accessor of `SlowerDP` waits for 3 seconds before returning the value of the `_slowerDP` data member.</span></span>  
  
 <span data-ttu-id="6bb8d-111">Přistupující objekt get pro `SlowestDP` čeká 5 sekund před vrácením hodnoty datového členu `_slowestDP`.</span><span class="sxs-lookup"><span data-stu-id="6bb8d-111">The get accessor of `SlowestDP` waits for 5 seconds before returning the value of the `_slowestDP` data member.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6bb8d-112">Tento příklad je určen pouze pro demonstrační účely.</span><span class="sxs-lookup"><span data-stu-id="6bb8d-112">This example is for demonstration purposes only.</span></span> <span data-ttu-id="6bb8d-113">Pokyny pro rozhraní .NET doporučují před definováním vlastností, které jsou objednávkami s nižšími rozměry, než je sada polí.</span><span class="sxs-lookup"><span data-stu-id="6bb8d-113">The .NET guidelines recommend against defining properties that are orders of magnitude slower than a field set would be.</span></span> <span data-ttu-id="6bb8d-114">Další informace naleznete v tématu [Výběr mezi vlastnostmi a metodami](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229054(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="6bb8d-114">For more information, see [Choosing Between Properties and Methods](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229054(v=vs.100)).</span></span>  
  
 [!code-csharp[PriorityBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 <span data-ttu-id="6bb8d-115">Vlastnost <xref:System.Windows.Controls.TextBlock.Text%2A> se váže k výše uvedenému `AsyncDS` pomocí <xref:System.Windows.Data.PriorityBinding>:</span><span class="sxs-lookup"><span data-stu-id="6bb8d-115">The <xref:System.Windows.Controls.TextBlock.Text%2A> property binds to the above `AsyncDS` using <xref:System.Windows.Data.PriorityBinding>:</span></span>  
  
 [!code-xaml[PriorityBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="6bb8d-116">Když modul vazby zpracovává objekty <xref:System.Windows.Data.Binding>, začíná prvním <xref:System.Windows.Data.Binding>, která je svázána s vlastností `SlowestDP`.</span><span class="sxs-lookup"><span data-stu-id="6bb8d-116">When the binding engine processes the <xref:System.Windows.Data.Binding> objects, it starts with the first <xref:System.Windows.Data.Binding>, which is bound to the `SlowestDP` property.</span></span> <span data-ttu-id="6bb8d-117">Při zpracování tohoto <xref:System.Windows.Data.Binding> nevrátí hodnotu úspěšně, protože je v režimu spánku po dobu 5 sekund, takže se zpracuje další prvek <xref:System.Windows.Data.Binding>.</span><span class="sxs-lookup"><span data-stu-id="6bb8d-117">When this <xref:System.Windows.Data.Binding> is processed, it does not return a value successfully because it is sleeping for 5 seconds, so the next <xref:System.Windows.Data.Binding> element is processed.</span></span> <span data-ttu-id="6bb8d-118">Následující <xref:System.Windows.Data.Binding> nevrátí hodnotu úspěšně, protože je v režimu spánku po dobu 3 sekund.</span><span class="sxs-lookup"><span data-stu-id="6bb8d-118">The next <xref:System.Windows.Data.Binding> does not return a value successfully because it is sleeping for 3 seconds.</span></span> <span data-ttu-id="6bb8d-119">Modul vazby se pak přesune na další <xref:System.Windows.Data.Binding> element, který je svázán s vlastností `FastDP`.</span><span class="sxs-lookup"><span data-stu-id="6bb8d-119">The binding engine then moves onto the next <xref:System.Windows.Data.Binding> element, which is bound to the `FastDP` property.</span></span> <span data-ttu-id="6bb8d-120">Tato <xref:System.Windows.Data.Binding> vrátí hodnotu "Rychlá hodnota".</span><span class="sxs-lookup"><span data-stu-id="6bb8d-120">This <xref:System.Windows.Data.Binding> returns the value "Fast Value".</span></span> <span data-ttu-id="6bb8d-121"><xref:System.Windows.Controls.TextBlock> nyní zobrazí hodnotu "Rychlá hodnota".</span><span class="sxs-lookup"><span data-stu-id="6bb8d-121">The <xref:System.Windows.Controls.TextBlock> now displays the value "Fast Value".</span></span>  
  
 <span data-ttu-id="6bb8d-122">Po 3 sekundách uplynou vlastnost `SlowerDP` vrátí hodnotu "pomalejší hodnota".</span><span class="sxs-lookup"><span data-stu-id="6bb8d-122">After 3 seconds elapses, the `SlowerDP` property returns the value "Slower Value".</span></span> <span data-ttu-id="6bb8d-123"><xref:System.Windows.Controls.TextBlock> pak zobrazí hodnotu "pomalejší hodnota".</span><span class="sxs-lookup"><span data-stu-id="6bb8d-123">The <xref:System.Windows.Controls.TextBlock> then displays the value "Slower Value".</span></span>  
  
 <span data-ttu-id="6bb8d-124">Po uplynutí 5 sekund vrátí vlastnost `SlowestDP` hodnotu nejnižší hodnota.</span><span class="sxs-lookup"><span data-stu-id="6bb8d-124">After 5 seconds elapses, the `SlowestDP` property returns the value "Slowest Value".</span></span> <span data-ttu-id="6bb8d-125">Tato vazba má nejvyšší prioritu, protože je uvedena jako první.</span><span class="sxs-lookup"><span data-stu-id="6bb8d-125">That binding has the highest priority because it is listed first.</span></span> <span data-ttu-id="6bb8d-126"><xref:System.Windows.Controls.TextBlock> nyní zobrazuje hodnotu nejpomalejších hodnot.</span><span class="sxs-lookup"><span data-stu-id="6bb8d-126">The <xref:System.Windows.Controls.TextBlock> now displays the value "Slowest Value".</span></span>  
  
 <span data-ttu-id="6bb8d-127">Informace o tom, co se považuje za úspěšnou návratovou hodnotu z vazby, najdete v tématu <xref:System.Windows.Data.PriorityBinding>.</span><span class="sxs-lookup"><span data-stu-id="6bb8d-127">See <xref:System.Windows.Data.PriorityBinding> for information about what is considered a successful return value from a binding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bb8d-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6bb8d-128">See also</span></span>

- <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>
- [<span data-ttu-id="6bb8d-129">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="6bb8d-129">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="6bb8d-130">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="6bb8d-130">How-to Topics</span></span>](data-binding-how-to-topics.md)
