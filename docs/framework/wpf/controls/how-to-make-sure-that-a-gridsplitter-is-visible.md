---
title: 'Postupy: Kontrola viditelnosti objektu GridSplitter'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: GridSplitter control [WPF], ensuring visibility of
ms.assetid: 0a62a964-89c8-48f0-9023-5df721a8cf47
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b7587a093b2b43856a05693bb785a0465211782
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-sure-that-a-gridsplitter-is-visible"></a><span data-ttu-id="c5b4e-102">Postupy: Kontrola viditelnosti objektu GridSplitter</span><span class="sxs-lookup"><span data-stu-id="c5b4e-102">How to: Make Sure That a GridSplitter Is Visible</span></span>
<span data-ttu-id="c5b4e-103">Tento příklad ukazuje, jak zajistit <xref:System.Windows.Controls.GridSplitter> z jiných ovládacích prvků v není skrytý ovládací prvek <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="c5b4e-103">This example shows how to make sure a <xref:System.Windows.Controls.GridSplitter> control is not hidden by the other controls in a <xref:System.Windows.Controls.Grid>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5b4e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="c5b4e-104">Example</span></span>  
 <span data-ttu-id="c5b4e-105"><xref:System.Windows.Controls.Panel.Children%2A> z <xref:System.Windows.Controls.Grid> řízení se zobrazují v pořadí, že jsou definovány v kód.</span><span class="sxs-lookup"><span data-stu-id="c5b4e-105">The <xref:System.Windows.Controls.Panel.Children%2A> of a <xref:System.Windows.Controls.Grid> control are rendered in the order that they are defined in markup or code.</span></span> <span data-ttu-id="c5b4e-106"><xref:System.Windows.Controls.GridSplitter>ovládací prvky můžete skrytý za další ovládací prvky, pokud nejsou definovány jako poslední elementů v <xref:System.Windows.Controls.Panel.Children%2A> kolekce nebo je zadat další ovládací prvky a vyšší <xref:System.Windows.Controls.Panel.ZIndexProperty>.</span><span class="sxs-lookup"><span data-stu-id="c5b4e-106"><xref:System.Windows.Controls.GridSplitter> controls can be hidden by other controls if you do not define them as the last elements in the <xref:System.Windows.Controls.Panel.Children%2A> collection or if you give other controls a higher <xref:System.Windows.Controls.Panel.ZIndexProperty>.</span></span>  
  
 <span data-ttu-id="c5b4e-107">Aby se zabránilo Skrytá <xref:System.Windows.Controls.GridSplitter> ovládací prvky, proveďte jednu z následujících akcí.</span><span class="sxs-lookup"><span data-stu-id="c5b4e-107">To prevent hidden <xref:System.Windows.Controls.GridSplitter> controls, do one of the following.</span></span>  
  
-   <span data-ttu-id="c5b4e-108">Ujistěte se, že <xref:System.Windows.Controls.GridSplitter> ovládací prvky jsou poslední <xref:System.Windows.Controls.Panel.Children%2A> přidán do <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="c5b4e-108">Make sure that <xref:System.Windows.Controls.GridSplitter> controls are the last <xref:System.Windows.Controls.Panel.Children%2A> added to the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="c5b4e-109">Následující příklad ukazuje <xref:System.Windows.Controls.GridSplitter> jako posledním prvkem v <xref:System.Windows.Controls.Panel.Children%2A> kolekce <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="c5b4e-109">The following example shows the <xref:System.Windows.Controls.GridSplitter> as the last element in the <xref:System.Windows.Controls.Panel.Children%2A> collection of the <xref:System.Windows.Controls.Grid>.</span></span>  
  
 [!code-xaml[GridSplitterSnips#GridSplitterLastChild](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterlastchild)]  
  
-   <span data-ttu-id="c5b4e-110">Nastavte <xref:System.Windows.Controls.Panel.ZIndexProperty> na <xref:System.Windows.Controls.GridSplitter> vyšší než ovládací prvek, který by jinak skrýt.</span><span class="sxs-lookup"><span data-stu-id="c5b4e-110">Set the <xref:System.Windows.Controls.Panel.ZIndexProperty> on the <xref:System.Windows.Controls.GridSplitter> to be higher than a control that would otherwise hide it.</span></span> <span data-ttu-id="c5b4e-111">Poskytuje následující příklad <xref:System.Windows.Controls.GridSplitter> řízení a vyšší <xref:System.Windows.Controls.Panel.ZIndexProperty> než <xref:System.Windows.Controls.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c5b4e-111">The following example gives the <xref:System.Windows.Controls.GridSplitter> control a higher <xref:System.Windows.Controls.Panel.ZIndexProperty> than the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[GridSplitterSnips#GridSplitterZIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterzindex)]  
  
-   <span data-ttu-id="c5b4e-112">Nastavení okrajů na ovládací prvek, který by jinak skrýt <xref:System.Windows.Controls.GridSplitter> tak, aby <xref:System.Windows.Controls.GridSplitter> zpřístupněn.</span><span class="sxs-lookup"><span data-stu-id="c5b4e-112">Set margins on the control that would otherwise hide the <xref:System.Windows.Controls.GridSplitter> so that the <xref:System.Windows.Controls.GridSplitter> is exposed.</span></span> <span data-ttu-id="c5b4e-113">Následující příklad nastaví okrajů pro ovládací prvek, který by jinak překrytí a skrýt <xref:System.Windows.Controls.GridSplitter>.</span><span class="sxs-lookup"><span data-stu-id="c5b4e-113">The following example sets margins on a control that would otherwise overlay and hide the <xref:System.Windows.Controls.GridSplitter>.</span></span>  
  
 [!code-xaml[GridSplitterSnips#GridSplitterMargin](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplittermargin)]  
  
## <a name="see-also"></a><span data-ttu-id="c5b4e-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="c5b4e-114">See Also</span></span>  
 <xref:System.Windows.Controls.GridSplitter>  
 [<span data-ttu-id="c5b4e-115">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="c5b4e-115">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
