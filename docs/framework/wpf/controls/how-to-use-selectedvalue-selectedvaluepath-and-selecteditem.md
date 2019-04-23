---
title: 'Postupy: Použití SelectedValue, SelectedValuePath a SelectedItem'
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], SelectedValue properties
- Control class [WPF], SelectedItem properties
- Control class [WPF], TreeView properties
- Control class [WPF], SelectedValue properties
- TreeView control [WPF], SelectedItem properties
- SelectedValue [WPF], SelectedValuePath properties
- TreeView control [WPF], SelectedValuePath properties
- Control class [WPF], SelectedValuePath properties
- SelectedValue [WPF], SelectedItem properties
ms.assetid: 2fc92ad4-f02c-4f89-bbe9-d4978a7af0db
ms.openlocfilehash: d9f7a8f04f53b7d38a49dfef2c947dfa1c2d263d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59169699"
---
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a><span data-ttu-id="6c81d-102">Postupy: Použití SelectedValue, SelectedValuePath a SelectedItem</span><span class="sxs-lookup"><span data-stu-id="6c81d-102">How to: Use SelectedValue, SelectedValuePath, and SelectedItem</span></span>
<span data-ttu-id="6c81d-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Controls.TreeView.SelectedValue%2A> a <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> vlastnosti, které chcete zadat hodnotu <xref:System.Windows.Controls.TreeView.SelectedItem%2A> z <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="6c81d-103">This example shows how to use the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> and <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> properties to specify a value for the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> of a <xref:System.Windows.Controls.TreeView>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c81d-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="6c81d-104">Example</span></span>  
 <span data-ttu-id="6c81d-105"><xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> Vlastnost poskytuje způsob, jak určit <xref:System.Windows.Controls.TreeView.SelectedValue%2A> pro <xref:System.Windows.Controls.TreeView.SelectedItem%2A> v <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="6c81d-105">The <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> property provides a way to specify a <xref:System.Windows.Controls.TreeView.SelectedValue%2A> for the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> in a <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="6c81d-106"><xref:System.Windows.Controls.TreeView.SelectedItem%2A> Představuje objekt <xref:System.Windows.Controls.ItemsControl.Items%2A> kolekce a <xref:System.Windows.Controls.TreeView> zobrazuje hodnotu jedné vlastnosti vybrané položky.</span><span class="sxs-lookup"><span data-stu-id="6c81d-106">The <xref:System.Windows.Controls.TreeView.SelectedItem%2A> represents an object in the <xref:System.Windows.Controls.ItemsControl.Items%2A> collection and the <xref:System.Windows.Controls.TreeView> displays the value of a single property of the selected item.</span></span> <span data-ttu-id="6c81d-107"><xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> Vlastnost určuje cestu k vlastnosti, která se používá k určení hodnoty <xref:System.Windows.Controls.TreeView.SelectedValue%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6c81d-107">The <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> property specifies the path to the property that is used to determine the value of the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> property.</span></span> <span data-ttu-id="6c81d-108">Příklady v tomto tématu ilustrují tento koncept.</span><span class="sxs-lookup"><span data-stu-id="6c81d-108">The examples in this topic illustrate this concept.</span></span>  
  
 <span data-ttu-id="6c81d-109">Následující příklad ukazuje <xref:System.Windows.Data.XmlDataProvider> , který obsahuje informace o zaměstnancích.</span><span class="sxs-lookup"><span data-stu-id="6c81d-109">The following example shows an <xref:System.Windows.Data.XmlDataProvider> that contains employee information.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 <span data-ttu-id="6c81d-110">Následující příklad definuje <xref:System.Windows.HierarchicalDataTemplate> , který se zobrazí `EmployeeName` a `EmployeeWorkDay` z `Employee`.</span><span class="sxs-lookup"><span data-stu-id="6c81d-110">The following example defines a <xref:System.Windows.HierarchicalDataTemplate> that displays the `EmployeeName` and `EmployeeWorkDay` of the `Employee`.</span></span> <span data-ttu-id="6c81d-111">Všimněte si, že <xref:System.Windows.HierarchicalDataTemplate> neurčuje `EmployeeNumber` jako součást šablony.</span><span class="sxs-lookup"><span data-stu-id="6c81d-111">Note that the <xref:System.Windows.HierarchicalDataTemplate> does not specify the `EmployeeNumber` as part of the template.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 <span data-ttu-id="6c81d-112">Následující příklad ukazuje <xref:System.Windows.Controls.TreeView> , která používá dříve definované <xref:System.Windows.HierarchicalDataTemplate> a nastaví se <xref:System.Windows.Controls.TreeView.SelectedValue%2A> vlastnost `EmployeeNumber`.</span><span class="sxs-lookup"><span data-stu-id="6c81d-112">The following example shows a <xref:System.Windows.Controls.TreeView> that uses the previously defined <xref:System.Windows.HierarchicalDataTemplate> and that sets the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> property to the `EmployeeNumber`.</span></span> <span data-ttu-id="6c81d-113">Když vyberete `EmployeeName` v <xref:System.Windows.Controls.TreeView>, <xref:System.Windows.Controls.TreeView.SelectedItem%2A> vrátí vlastnost `EmployeeInfo` datová položka, která odpovídá vybrané `EmployeeName`.</span><span class="sxs-lookup"><span data-stu-id="6c81d-113">When you select an `EmployeeName` in the <xref:System.Windows.Controls.TreeView>, the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> property returns the `EmployeeInfo` data item that corresponds to the selected `EmployeeName`.</span></span> <span data-ttu-id="6c81d-114">Ale protože <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> tohoto <xref:System.Windows.Controls.TreeView> je nastavena na `EmployeeNumber`, <xref:System.Windows.Controls.TreeView.SelectedValue%2A> je nastavena na `EmployeeNumber`.</span><span class="sxs-lookup"><span data-stu-id="6c81d-114">However, because the <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> of this <xref:System.Windows.Controls.TreeView> is set to `EmployeeNumber`, the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> is set to the `EmployeeNumber`.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a><span data-ttu-id="6c81d-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6c81d-115">See also</span></span>

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [<span data-ttu-id="6c81d-116">TreeView – přehled</span><span class="sxs-lookup"><span data-stu-id="6c81d-116">TreeView Overview</span></span>](treeview-overview.md)
- [<span data-ttu-id="6c81d-117">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="6c81d-117">How-to Topics</span></span>](treeview-how-to-topics.md)
