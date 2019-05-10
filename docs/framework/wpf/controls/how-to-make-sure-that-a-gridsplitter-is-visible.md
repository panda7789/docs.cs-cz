---
title: 'Postupy: Kontrola viditelnosti objektu GridSplitter'
ms.date: 03/30/2017
helpviewer_keywords:
- GridSplitter control [WPF], ensuring visibility of
ms.assetid: 0a62a964-89c8-48f0-9023-5df721a8cf47
ms.openlocfilehash: 2085ac5cec206d8692a1267acf132688f0aa9082
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663306"
---
# <a name="how-to-make-sure-that-a-gridsplitter-is-visible"></a><span data-ttu-id="ce340-102">Postupy: Kontrola viditelnosti objektu GridSplitter</span><span class="sxs-lookup"><span data-stu-id="ce340-102">How to: Make Sure That a GridSplitter Is Visible</span></span>
<span data-ttu-id="ce340-103">Tento příklad ukazuje, jak Ujistěte se, že <xref:System.Windows.Controls.GridSplitter> jiné ovládací prvky v není skrytý ovládací prvek <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="ce340-103">This example shows how to make sure a <xref:System.Windows.Controls.GridSplitter> control is not hidden by the other controls in a <xref:System.Windows.Controls.Grid>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce340-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce340-104">Example</span></span>  
 <span data-ttu-id="ce340-105"><xref:System.Windows.Controls.Panel.Children%2A> z <xref:System.Windows.Controls.Grid> ovládací prvek se zobrazují v pořadí, že jsou definovány v značek nebo kódu.</span><span class="sxs-lookup"><span data-stu-id="ce340-105">The <xref:System.Windows.Controls.Panel.Children%2A> of a <xref:System.Windows.Controls.Grid> control are rendered in the order that they are defined in markup or code.</span></span> <span data-ttu-id="ce340-106"><xref:System.Windows.Controls.GridSplitter> ovládací prvky lze skrýt ovládací prvky, pokud není definován jako poslední prvky v <xref:System.Windows.Controls.Panel.Children%2A> kolekce nebo pokud poskytnete další ovládací prvky a vyšší <xref:System.Windows.Controls.Panel.ZIndexProperty>.</span><span class="sxs-lookup"><span data-stu-id="ce340-106"><xref:System.Windows.Controls.GridSplitter> controls can be hidden by other controls if you do not define them as the last elements in the <xref:System.Windows.Controls.Panel.Children%2A> collection or if you give other controls a higher <xref:System.Windows.Controls.Panel.ZIndexProperty>.</span></span>  
  
 <span data-ttu-id="ce340-107">Aby se zabránilo skryté <xref:System.Windows.Controls.GridSplitter> ovládací prvky, proveďte jednu z následujících akcí.</span><span class="sxs-lookup"><span data-stu-id="ce340-107">To prevent hidden <xref:System.Windows.Controls.GridSplitter> controls, do one of the following.</span></span>  
  
- <span data-ttu-id="ce340-108">Ujistěte se, že <xref:System.Windows.Controls.GridSplitter> ovládací prvky jsou poslední <xref:System.Windows.Controls.Panel.Children%2A> přidán do <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="ce340-108">Make sure that <xref:System.Windows.Controls.GridSplitter> controls are the last <xref:System.Windows.Controls.Panel.Children%2A> added to the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="ce340-109">Následující příklad ukazuje <xref:System.Windows.Controls.GridSplitter> jako po posledním prvku v <xref:System.Windows.Controls.Panel.Children%2A> kolekce <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="ce340-109">The following example shows the <xref:System.Windows.Controls.GridSplitter> as the last element in the <xref:System.Windows.Controls.Panel.Children%2A> collection of the <xref:System.Windows.Controls.Grid>.</span></span>  
  
 [!code-xaml[GridSplitterSnips#GridSplitterLastChild](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterlastchild)]  
  
- <span data-ttu-id="ce340-110">Nastavte <xref:System.Windows.Controls.Panel.ZIndexProperty> na <xref:System.Windows.Controls.GridSplitter> vyšší než ovládací prvek, který by jinak skrýt.</span><span class="sxs-lookup"><span data-stu-id="ce340-110">Set the <xref:System.Windows.Controls.Panel.ZIndexProperty> on the <xref:System.Windows.Controls.GridSplitter> to be higher than a control that would otherwise hide it.</span></span> <span data-ttu-id="ce340-111">Následující příklad dává <xref:System.Windows.Controls.GridSplitter> řídit vyšší <xref:System.Windows.Controls.Panel.ZIndexProperty> než <xref:System.Windows.Controls.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ce340-111">The following example gives the <xref:System.Windows.Controls.GridSplitter> control a higher <xref:System.Windows.Controls.Panel.ZIndexProperty> than the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[GridSplitterSnips#GridSplitterZIndex](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterzindex)]  
  
- <span data-ttu-id="ce340-112">Nastavit okraje ovládacího prvku, který by jinak skrýt <xref:System.Windows.Controls.GridSplitter> tak, aby <xref:System.Windows.Controls.GridSplitter> je přístupný.</span><span class="sxs-lookup"><span data-stu-id="ce340-112">Set margins on the control that would otherwise hide the <xref:System.Windows.Controls.GridSplitter> so that the <xref:System.Windows.Controls.GridSplitter> is exposed.</span></span> <span data-ttu-id="ce340-113">Následující příklad nastaví na ovládací prvek, který by jinak překrytí a skrýt okraje <xref:System.Windows.Controls.GridSplitter>.</span><span class="sxs-lookup"><span data-stu-id="ce340-113">The following example sets margins on a control that would otherwise overlay and hide the <xref:System.Windows.Controls.GridSplitter>.</span></span>  
  
 [!code-xaml[GridSplitterSnips#GridSplitterMargin](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplittermargin)]  
  
## <a name="see-also"></a><span data-ttu-id="ce340-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ce340-114">See also</span></span>

- <xref:System.Windows.Controls.GridSplitter>
- [<span data-ttu-id="ce340-115">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="ce340-115">How-to Topics</span></span>](gridsplitter-how-to-topics.md)
