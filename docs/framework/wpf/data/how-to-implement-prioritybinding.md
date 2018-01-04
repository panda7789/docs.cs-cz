---
title: "Postupy: Implementace rozhraní PriorityBinding"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 13b254867200897acad2868e396d152a5f9efcbd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-prioritybinding"></a><span data-ttu-id="5997e-102">Postupy: Implementace rozhraní PriorityBinding</span><span class="sxs-lookup"><span data-stu-id="5997e-102">How to: Implement PriorityBinding</span></span>
<span data-ttu-id="5997e-103"><xref:System.Windows.Data.PriorityBinding>v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] funguje tak, že zadáte seznam vazeb.</span><span class="sxs-lookup"><span data-stu-id="5997e-103"><xref:System.Windows.Data.PriorityBinding> in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] works by specifying a list of bindings.</span></span> <span data-ttu-id="5997e-104">Seznam vazeb je nejnižší priorita seřazena z nejvyšší prioritou.</span><span class="sxs-lookup"><span data-stu-id="5997e-104">The list of bindings is ordered from highest priority to lowest priority.</span></span> <span data-ttu-id="5997e-105">Jestliže nejvyšší prioritou vazby vrací hodnotu úspěšně při zpracování nejsou nikdy potřeba zpracovat vazby v seznamu.</span><span class="sxs-lookup"><span data-stu-id="5997e-105">If the highest priority binding returns a value successfully when it is processed then there is never a need to process the other bindings in the list.</span></span> <span data-ttu-id="5997e-106">Může to být případě, že nejvyšší prioritou vazby trvá dlouhou dobu k vyhodnocení, další nejvyšší prioritou, která vrátí hodnotu úspěšně bude používat, dokud vazbu s vyšší prioritou vrací hodnotu úspěšně.</span><span class="sxs-lookup"><span data-stu-id="5997e-106">It could be the case that the highest priority binding takes a long time to be evaluated, the next highest priority that returns a value successfully will be used until a binding of a higher priority returns a value successfully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5997e-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="5997e-107">Example</span></span>  
 <span data-ttu-id="5997e-108">K předvedení způsobu <xref:System.Windows.Data.PriorityBinding> funguje, `AsyncDataSource` objekt byl vytvořen s následujícími třemi vlastnostmi: `FastDP`, `SlowerDP`, a `SlowestDP`.</span><span class="sxs-lookup"><span data-stu-id="5997e-108">To demonstrate how <xref:System.Windows.Data.PriorityBinding> works, the `AsyncDataSource` object has been created with the following three properties: `FastDP`, `SlowerDP`, and `SlowestDP`.</span></span>  
  
 <span data-ttu-id="5997e-109">Přistupující objekt get z `FastDP` vrací hodnotu `_fastDP` – datový člen.</span><span class="sxs-lookup"><span data-stu-id="5997e-109">The get accessor of `FastDP` returns the value of the `_fastDP` data member.</span></span>  
  
 <span data-ttu-id="5997e-110">Přistupující objekt get z `SlowerDP` čeká 3 sekund před vrácením hodnotu `_slowerDP` – datový člen.</span><span class="sxs-lookup"><span data-stu-id="5997e-110">The get accessor of `SlowerDP` waits for 3 seconds before returning the value of the `_slowerDP` data member.</span></span>  
  
 <span data-ttu-id="5997e-111">Přistupující objekt get z `SlowestDP` čeká na 5 sekund před vrácením hodnotu `_slowestDP` – datový člen.</span><span class="sxs-lookup"><span data-stu-id="5997e-111">The get accessor of `SlowestDP` waits for 5 seconds before returning the value of the `_slowestDP` data member.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5997e-112">V tomto příkladu je pouze pro demonstrační účely.</span><span class="sxs-lookup"><span data-stu-id="5997e-112">This example is for demonstration purposes only.</span></span> <span data-ttu-id="5997e-113">[!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] Pokyny nedoporučujeme definování vlastností, které jsou pořadí podle velikosti pomalejší, než by bylo pole sady.</span><span class="sxs-lookup"><span data-stu-id="5997e-113">The [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] guidelines recommend against defining properties that are orders of magnitude slower than a field set would be.</span></span> <span data-ttu-id="5997e-114">Další informace najdete v tématu [NIB: výběr mezi vlastnosti a metody](http://msdn.microsoft.com/en-us/55825e8f-7e2e-448a-9505-7217cc91b1af).</span><span class="sxs-lookup"><span data-stu-id="5997e-114">For more information, see [NIB: Choosing Between Properties and Methods](http://msdn.microsoft.com/en-us/55825e8f-7e2e-448a-9505-7217cc91b1af).</span></span>  
  
 [!code-csharp[PriorityBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 <span data-ttu-id="5997e-115"><xref:System.Windows.Controls.TextBlock.Text%2A> Vlastnost váže k výše `AsyncDS` pomocí <xref:System.Windows.Data.PriorityBinding>:</span><span class="sxs-lookup"><span data-stu-id="5997e-115">The <xref:System.Windows.Controls.TextBlock.Text%2A> property binds to the above `AsyncDS` using <xref:System.Windows.Data.PriorityBinding>:</span></span>  
  
 [!code-xaml[PriorityBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="5997e-116">Když modul vazby zpracovává <xref:System.Windows.Data.Binding> objekty, začíná prvním <xref:System.Windows.Data.Binding>, která je vázána `SlowestDP` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5997e-116">When the binding engine processes the <xref:System.Windows.Data.Binding> objects, it starts with the first <xref:System.Windows.Data.Binding>, which is bound to the `SlowestDP` property.</span></span> <span data-ttu-id="5997e-117">Pokud to <xref:System.Windows.Data.Binding> je zpracování nevrátí hodnotu úspěšně vzhledem k tomu, že ho je v režimu spánku po dobu 5 sekund, takže další <xref:System.Windows.Data.Binding> zpracování elementu.</span><span class="sxs-lookup"><span data-stu-id="5997e-117">When this <xref:System.Windows.Data.Binding> is processed, it does not return a value successfully because it is sleeping for 5 seconds, so the next <xref:System.Windows.Data.Binding> element is processed.</span></span> <span data-ttu-id="5997e-118">Další <xref:System.Windows.Data.Binding> nevrátí hodnotu úspěšně vzhledem k tomu, že je pozastaveno pro 3 sekund.</span><span class="sxs-lookup"><span data-stu-id="5997e-118">The next <xref:System.Windows.Data.Binding> does not return a value successfully because it is sleeping for 3 seconds.</span></span> <span data-ttu-id="5997e-119">Modul vazby pak se posouvá do další <xref:System.Windows.Data.Binding> element, který je vázána `FastDP` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5997e-119">The binding engine then moves onto the next <xref:System.Windows.Data.Binding> element, which is bound to the `FastDP` property.</span></span> <span data-ttu-id="5997e-120">To <xref:System.Windows.Data.Binding> vrátí hodnotu "Rychlé hodnota".</span><span class="sxs-lookup"><span data-stu-id="5997e-120">This <xref:System.Windows.Data.Binding> returns the value "Fast Value".</span></span> <span data-ttu-id="5997e-121"><xref:System.Windows.Controls.TextBlock> Teď zobrazuje hodnotu "Rychlé hodnota".</span><span class="sxs-lookup"><span data-stu-id="5997e-121">The <xref:System.Windows.Controls.TextBlock> now displays the value "Fast Value".</span></span>  
  
 <span data-ttu-id="5997e-122">Po uplynutí 3 sekund `SlowerDP` vlastnost vrací hodnotu "Nižší hodnota".</span><span class="sxs-lookup"><span data-stu-id="5997e-122">After 3 seconds elapses, the `SlowerDP` property returns the value "Slower Value".</span></span> <span data-ttu-id="5997e-123"><xref:System.Windows.Controls.TextBlock> Pak zobrazí hodnotu "Nižší hodnota".</span><span class="sxs-lookup"><span data-stu-id="5997e-123">The <xref:System.Windows.Controls.TextBlock> then displays the value "Slower Value".</span></span>  
  
 <span data-ttu-id="5997e-124">Po uplynutí 5 sekund `SlowestDP` vlastnost vrací hodnotu "Nejpomalejší hodnota".</span><span class="sxs-lookup"><span data-stu-id="5997e-124">After 5 seconds elapses, the `SlowestDP` property returns the value "Slowest Value".</span></span> <span data-ttu-id="5997e-125">Této vazby má nejvyšší prioritu, protože je uvedená jako první.</span><span class="sxs-lookup"><span data-stu-id="5997e-125">That binding has the highest priority because it is listed first.</span></span> <span data-ttu-id="5997e-126"><xref:System.Windows.Controls.TextBlock> Teď zobrazuje hodnotu "Nejpomalejší hodnota".</span><span class="sxs-lookup"><span data-stu-id="5997e-126">The <xref:System.Windows.Controls.TextBlock> now displays the value "Slowest Value".</span></span>  
  
 <span data-ttu-id="5997e-127">V tématu <xref:System.Windows.Data.PriorityBinding> informace o co se považuje za úspěšné vrácená hodnota z vazbu.</span><span class="sxs-lookup"><span data-stu-id="5997e-127">See <xref:System.Windows.Data.PriorityBinding> for information about what is considered a successful return value from a binding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5997e-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="5997e-128">See Also</span></span>  
 <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="5997e-129">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="5997e-129">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="5997e-130">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="5997e-130">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
