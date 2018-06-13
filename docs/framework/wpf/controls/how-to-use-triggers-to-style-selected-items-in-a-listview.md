---
title: 'Postupy: Nastavení stylu vybraných položek v zobrazení ListView použitím aktivačních procedur'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 1e2bdce0-afe8-4507-9b18-f33de43de25a
ms.openlocfilehash: 1741ce84fab1639409a7c834845573239c51cc35
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554908"
---
# <a name="how-to-use-triggers-to-style-selected-items-in-a-listview"></a><span data-ttu-id="b5313-102">Postupy: Nastavení stylu vybraných položek v zobrazení ListView použitím aktivačních procedur</span><span class="sxs-lookup"><span data-stu-id="b5313-102">How to: Use Triggers to Style Selected Items in a ListView</span></span>
<span data-ttu-id="b5313-103">Tento příklad ukazuje, jak definovat <xref:System.Windows.Style.Triggers%2A> pro <xref:System.Windows.Controls.ListViewItem> ovládacího prvku tak, aby při hodnotu vlastnosti <xref:System.Windows.Controls.ListViewItem> změny, <xref:System.Windows.Style> z <xref:System.Windows.Controls.ListViewItem> změnách v reakci.</span><span class="sxs-lookup"><span data-stu-id="b5313-103">This example shows how to define <xref:System.Windows.Style.Triggers%2A> for a <xref:System.Windows.Controls.ListViewItem> control so that when a property value of a <xref:System.Windows.Controls.ListViewItem> changes, the <xref:System.Windows.Style> of the <xref:System.Windows.Controls.ListViewItem> changes in response.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5313-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="b5313-104">Example</span></span>  
 <span data-ttu-id="b5313-105">Pokud chcete <xref:System.Windows.Style> z <xref:System.Windows.Controls.ListViewItem> Chcete-li změnit v reakci na změny vlastností, definovat <xref:System.Windows.Style.Triggers%2A> pro <xref:System.Windows.Style> změnit.</span><span class="sxs-lookup"><span data-stu-id="b5313-105">If you want the <xref:System.Windows.Style> of a <xref:System.Windows.Controls.ListViewItem> to change in response to property changes, define <xref:System.Windows.Style.Triggers%2A> for the <xref:System.Windows.Style> change.</span></span>  
  
 <span data-ttu-id="b5313-106">V následujícím příkladu definuje <xref:System.Windows.Trigger> , který nastavuje <xref:System.Windows.Controls.Control.Foreground%2A> vlastnost <xref:System.Windows.Media.Brushes.Blue%2A> a změny <xref:System.Windows.FrameworkElement.Cursor%2A> zobrazíte <xref:System.Windows.Input.CursorType.Hand> při <xref:System.Windows.UIElement.IsMouseOver%2A> změny vlastností do `true`.</span><span class="sxs-lookup"><span data-stu-id="b5313-106">The following example defines a <xref:System.Windows.Trigger> that sets the <xref:System.Windows.Controls.Control.Foreground%2A> property to <xref:System.Windows.Media.Brushes.Blue%2A> and changes the <xref:System.Windows.FrameworkElement.Cursor%2A> to display a <xref:System.Windows.Input.CursorType.Hand> when the <xref:System.Windows.UIElement.IsMouseOver%2A> property changes to `true`.</span></span>  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#Trigger](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#trigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
 <span data-ttu-id="b5313-107">V následujícím příkladu definuje <xref:System.Windows.MultiTrigger> , který nastavuje <xref:System.Windows.Controls.Control.Foreground%2A> vlastnost <xref:System.Windows.Controls.ListViewItem> k <xref:System.Windows.Media.Brushes.Yellow%2A> při <xref:System.Windows.Controls.ListViewItem> vybrané položky a má fokus klávesnice.</span><span class="sxs-lookup"><span data-stu-id="b5313-107">The following example defines a <xref:System.Windows.MultiTrigger> that sets the <xref:System.Windows.Controls.Control.Foreground%2A> property of a <xref:System.Windows.Controls.ListViewItem> to <xref:System.Windows.Media.Brushes.Yellow%2A> when the <xref:System.Windows.Controls.ListViewItem> is the selected item and has keyboard focus.</span></span>  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#MultiTrigger](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#multitrigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
## <a name="see-also"></a><span data-ttu-id="b5313-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5313-108">See Also</span></span>  
 <xref:System.Windows.Controls.Control>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="b5313-109">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="b5313-109">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="b5313-110">ListView – přehled</span><span class="sxs-lookup"><span data-stu-id="b5313-110">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="b5313-111">GridView – přehled</span><span class="sxs-lookup"><span data-stu-id="b5313-111">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
