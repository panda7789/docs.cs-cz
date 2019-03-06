---
title: 'Postupy: Nastavení stylu vybraných položek v zobrazení ListView použitím aktivačních procedur'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 1e2bdce0-afe8-4507-9b18-f33de43de25a
ms.openlocfilehash: 8c2d4adb2471c0f1891288573ce6b6460b20151d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367918"
---
# <a name="how-to-use-triggers-to-style-selected-items-in-a-listview"></a><span data-ttu-id="58010-102">Postupy: Nastavení stylu vybraných položek v zobrazení ListView použitím aktivačních procedur</span><span class="sxs-lookup"><span data-stu-id="58010-102">How to: Use Triggers to Style Selected Items in a ListView</span></span>
<span data-ttu-id="58010-103">Tento příklad ukazuje, jak definovat <xref:System.Windows.Style.Triggers%2A> pro <xref:System.Windows.Controls.ListViewItem> ovládacího prvku tak, aby při hodnotou vlastnosti <xref:System.Windows.Controls.ListViewItem> změny, <xref:System.Windows.Style> z <xref:System.Windows.Controls.ListViewItem> změnách v reakci.</span><span class="sxs-lookup"><span data-stu-id="58010-103">This example shows how to define <xref:System.Windows.Style.Triggers%2A> for a <xref:System.Windows.Controls.ListViewItem> control so that when a property value of a <xref:System.Windows.Controls.ListViewItem> changes, the <xref:System.Windows.Style> of the <xref:System.Windows.Controls.ListViewItem> changes in response.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58010-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="58010-104">Example</span></span>  
 <span data-ttu-id="58010-105">Pokud chcete, aby <xref:System.Windows.Style> z <xref:System.Windows.Controls.ListViewItem> Chcete-li změnit v reakci na změny vlastností, definujte <xref:System.Windows.Style.Triggers%2A> pro <xref:System.Windows.Style> změnit.</span><span class="sxs-lookup"><span data-stu-id="58010-105">If you want the <xref:System.Windows.Style> of a <xref:System.Windows.Controls.ListViewItem> to change in response to property changes, define <xref:System.Windows.Style.Triggers%2A> for the <xref:System.Windows.Style> change.</span></span>  
  
 <span data-ttu-id="58010-106">Následující příklad definuje <xref:System.Windows.Trigger> , který nastavuje <xref:System.Windows.Controls.Control.Foreground%2A> vlastnost <xref:System.Windows.Media.Brushes.Blue%2A> a změní <xref:System.Windows.FrameworkElement.Cursor%2A> zobrazíte <xref:System.Windows.Input.CursorType.Hand> při <xref:System.Windows.UIElement.IsMouseOver%2A> vlastnost se změní na `true`.</span><span class="sxs-lookup"><span data-stu-id="58010-106">The following example defines a <xref:System.Windows.Trigger> that sets the <xref:System.Windows.Controls.Control.Foreground%2A> property to <xref:System.Windows.Media.Brushes.Blue%2A> and changes the <xref:System.Windows.FrameworkElement.Cursor%2A> to display a <xref:System.Windows.Input.CursorType.Hand> when the <xref:System.Windows.UIElement.IsMouseOver%2A> property changes to `true`.</span></span>  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#Trigger](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#trigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
 <span data-ttu-id="58010-107">Následující příklad definuje <xref:System.Windows.MultiTrigger> , který nastavuje <xref:System.Windows.Controls.Control.Foreground%2A> vlastnost <xref:System.Windows.Controls.ListViewItem> k <xref:System.Windows.Media.Brushes.Yellow%2A> při <xref:System.Windows.Controls.ListViewItem> pro vybranou položku a má fokus klávesnice.</span><span class="sxs-lookup"><span data-stu-id="58010-107">The following example defines a <xref:System.Windows.MultiTrigger> that sets the <xref:System.Windows.Controls.Control.Foreground%2A> property of a <xref:System.Windows.Controls.ListViewItem> to <xref:System.Windows.Media.Brushes.Yellow%2A> when the <xref:System.Windows.Controls.ListViewItem> is the selected item and has keyboard focus.</span></span>  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#MultiTrigger](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#multitrigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
## <a name="see-also"></a><span data-ttu-id="58010-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="58010-108">See also</span></span>
- <xref:System.Windows.Controls.Control>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="58010-109">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="58010-109">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="58010-110">ListView – přehled</span><span class="sxs-lookup"><span data-stu-id="58010-110">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="58010-111">GridView – přehled</span><span class="sxs-lookup"><span data-stu-id="58010-111">GridView Overview</span></span>](gridview-overview.md)
