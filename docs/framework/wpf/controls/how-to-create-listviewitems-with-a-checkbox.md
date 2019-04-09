---
title: 'Postupy: Vytvoření ListViewItems pomocí CheckBox'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], ListView
- controls [WPF], CheckBox
- ListView controls [WPF], CheckBox controls
- CheckBox control [WPF], ListView control
ms.assetid: f6d66c7f-906c-4f65-a55a-0ede9d00e26a
ms.openlocfilehash: b09d5ad11b0961febf524cec1e19cb1e59832e44
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083100"
---
# <a name="how-to-create-listviewitems-with-a-checkbox"></a><span data-ttu-id="bf054-102">Postupy: Vytvoření ListViewItems pomocí CheckBox</span><span class="sxs-lookup"><span data-stu-id="bf054-102">How to: Create ListViewItems with a CheckBox</span></span>
<span data-ttu-id="bf054-103">Tento příklad ukazuje, jak zobrazit sloupec <xref:System.Windows.Controls.CheckBox> ovládacích prvků v <xref:System.Windows.Controls.ListView> ovládací prvek, který se používá <xref:System.Windows.Controls.GridView>.</span><span class="sxs-lookup"><span data-stu-id="bf054-103">This example shows how to display a column of <xref:System.Windows.Controls.CheckBox> controls in a <xref:System.Windows.Controls.ListView> control that uses a <xref:System.Windows.Controls.GridView>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf054-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="bf054-104">Example</span></span>  
 <span data-ttu-id="bf054-105">Chcete vytvořit sloupec, který obsahuje <xref:System.Windows.Controls.CheckBox> ovládacích prvků v <xref:System.Windows.Controls.ListView>, vytvořit <xref:System.Windows.DataTemplate> , která obsahuje <xref:System.Windows.Controls.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="bf054-105">To create a column that contains <xref:System.Windows.Controls.CheckBox> controls in a <xref:System.Windows.Controls.ListView>, create a <xref:System.Windows.DataTemplate> that contains a <xref:System.Windows.Controls.CheckBox>.</span></span> <span data-ttu-id="bf054-106">Nastavte <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> z <xref:System.Windows.Controls.GridViewColumn> k <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="bf054-106">Then set the <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> of a <xref:System.Windows.Controls.GridViewColumn> to the <xref:System.Windows.DataTemplate>.</span></span>  
  
 <span data-ttu-id="bf054-107">Následující příklad ukazuje <xref:System.Windows.DataTemplate> , která obsahuje <xref:System.Windows.Controls.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="bf054-107">The following example shows a <xref:System.Windows.DataTemplate> that contains a <xref:System.Windows.Controls.CheckBox>.</span></span> <span data-ttu-id="bf054-108">V příkladu vytvoří vazbu <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> vlastnost <xref:System.Windows.Controls.CheckBox> k <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> hodnotu vlastnosti <xref:System.Windows.Controls.ListViewItem> , který jej obsahuje.</span><span class="sxs-lookup"><span data-stu-id="bf054-108">The example binds the <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> property of the <xref:System.Windows.Controls.CheckBox> to the <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> property value of the <xref:System.Windows.Controls.ListViewItem> that contains it.</span></span> <span data-ttu-id="bf054-109">Proto, když <xref:System.Windows.Controls.ListViewItem> , která obsahuje <xref:System.Windows.Controls.CheckBox> zaškrtnuto, <xref:System.Windows.Controls.CheckBox> je zaškrtnuté políčko.</span><span class="sxs-lookup"><span data-stu-id="bf054-109">Therefore, when the <xref:System.Windows.Controls.ListViewItem> that contains the <xref:System.Windows.Controls.CheckBox> is selected, the <xref:System.Windows.Controls.CheckBox> is checked.</span></span>  
  
 [!code-xaml[ListViewChkBox#CheckBoxDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#checkboxdatatemplate)]  
  
 <span data-ttu-id="bf054-110">Následující příklad ukazuje, jak vytvořit sloupec <xref:System.Windows.Controls.CheckBox> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="bf054-110">The following example shows how to create a column of <xref:System.Windows.Controls.CheckBox> controls.</span></span> <span data-ttu-id="bf054-111">Chcete-li sloupec, příklad nastaví <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> vlastnost <xref:System.Windows.Controls.GridViewColumn> k <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="bf054-111">To make the column, the example sets the <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> property of the <xref:System.Windows.Controls.GridViewColumn> to the <xref:System.Windows.DataTemplate>.</span></span>  
  
 [!code-xaml[ListViewChkBox#GridViewColumnCheckBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#gridviewcolumncheckbox)]  
  
## <a name="see-also"></a><span data-ttu-id="bf054-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bf054-112">See also</span></span>

- <xref:System.Windows.Controls.Control>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="bf054-113">ListView – přehled</span><span class="sxs-lookup"><span data-stu-id="bf054-113">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="bf054-114">– postupy</span><span class="sxs-lookup"><span data-stu-id="bf054-114">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="bf054-115">GridView – přehled</span><span class="sxs-lookup"><span data-stu-id="bf054-115">GridView Overview</span></span>](gridview-overview.md)
