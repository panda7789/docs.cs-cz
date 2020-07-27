---
title: 'Postupy: Použití SelectedValue, SelectedValuePath a SelectedItem'
description: Naučte se používat vlastnosti SelectedValue a SelectedValuePath k určení hodnoty pro SelectedItem prvku TreeView Windows Presentation Foundation.
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
ms.openlocfilehash: ddac2455dee0bf69d25307340eddd5364e43e823
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166271"
---
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a><span data-ttu-id="9c6c5-103">Postupy: Použití SelectedValue, SelectedValuePath a SelectedItem</span><span class="sxs-lookup"><span data-stu-id="9c6c5-103">How to: Use SelectedValue, SelectedValuePath, and SelectedItem</span></span>
<span data-ttu-id="9c6c5-104">Tento příklad ukazuje, jak použít <xref:System.Windows.Controls.TreeView.SelectedValue%2A> vlastnosti a <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> k určení hodnoty pro <xref:System.Windows.Controls.TreeView.SelectedItem%2A> <xref:System.Windows.Controls.TreeView> .</span><span class="sxs-lookup"><span data-stu-id="9c6c5-104">This example shows how to use the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> and <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> properties to specify a value for the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> of a <xref:System.Windows.Controls.TreeView>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c6c5-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="9c6c5-105">Example</span></span>  
 <span data-ttu-id="9c6c5-106"><xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>Vlastnost poskytuje způsob, jak zadat <xref:System.Windows.Controls.TreeView.SelectedValue%2A> pro <xref:System.Windows.Controls.TreeView.SelectedItem%2A> v <xref:System.Windows.Controls.TreeView> .</span><span class="sxs-lookup"><span data-stu-id="9c6c5-106">The <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> property provides a way to specify a <xref:System.Windows.Controls.TreeView.SelectedValue%2A> for the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> in a <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="9c6c5-107"><xref:System.Windows.Controls.TreeView.SelectedItem%2A>Představuje objekt v <xref:System.Windows.Controls.ItemsControl.Items%2A> kolekci a <xref:System.Windows.Controls.TreeView> zobrazí hodnotu jedné vlastnosti vybrané položky.</span><span class="sxs-lookup"><span data-stu-id="9c6c5-107">The <xref:System.Windows.Controls.TreeView.SelectedItem%2A> represents an object in the <xref:System.Windows.Controls.ItemsControl.Items%2A> collection and the <xref:System.Windows.Controls.TreeView> displays the value of a single property of the selected item.</span></span> <span data-ttu-id="9c6c5-108"><xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>Vlastnost určuje cestu k vlastnosti, která se používá k určení hodnoty <xref:System.Windows.Controls.TreeView.SelectedValue%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9c6c5-108">The <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> property specifies the path to the property that is used to determine the value of the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> property.</span></span> <span data-ttu-id="9c6c5-109">Příklady v tomto tématu ilustrují tento koncept.</span><span class="sxs-lookup"><span data-stu-id="9c6c5-109">The examples in this topic illustrate this concept.</span></span>  
  
 <span data-ttu-id="9c6c5-110">Následující příklad ukazuje <xref:System.Windows.Data.XmlDataProvider> , který obsahuje informace o zaměstnancích.</span><span class="sxs-lookup"><span data-stu-id="9c6c5-110">The following example shows an <xref:System.Windows.Data.XmlDataProvider> that contains employee information.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 <span data-ttu-id="9c6c5-111">Následující příklad definuje <xref:System.Windows.HierarchicalDataTemplate> , který ukazuje `EmployeeName` a `EmployeeWorkDay` `Employee` .</span><span class="sxs-lookup"><span data-stu-id="9c6c5-111">The following example defines a <xref:System.Windows.HierarchicalDataTemplate> that displays the `EmployeeName` and `EmployeeWorkDay` of the `Employee`.</span></span> <span data-ttu-id="9c6c5-112">Všimněte si, že <xref:System.Windows.HierarchicalDataTemplate> neurčuje `EmployeeNumber` jako součást šablony.</span><span class="sxs-lookup"><span data-stu-id="9c6c5-112">Note that the <xref:System.Windows.HierarchicalDataTemplate> does not specify the `EmployeeNumber` as part of the template.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 <span data-ttu-id="9c6c5-113">Následující příklad ukazuje <xref:System.Windows.Controls.TreeView> , který používá dříve definovaný <xref:System.Windows.HierarchicalDataTemplate> a který nastavuje <xref:System.Windows.Controls.TreeView.SelectedValue%2A> vlastnost na `EmployeeNumber` .</span><span class="sxs-lookup"><span data-stu-id="9c6c5-113">The following example shows a <xref:System.Windows.Controls.TreeView> that uses the previously defined <xref:System.Windows.HierarchicalDataTemplate> and that sets the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> property to the `EmployeeNumber`.</span></span> <span data-ttu-id="9c6c5-114">Když vyberete `EmployeeName` v <xref:System.Windows.Controls.TreeView> , <xref:System.Windows.Controls.TreeView.SelectedItem%2A> vlastnost vrátí `EmployeeInfo` datovou položku, která odpovídá vybranému `EmployeeName` .</span><span class="sxs-lookup"><span data-stu-id="9c6c5-114">When you select an `EmployeeName` in the <xref:System.Windows.Controls.TreeView>, the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> property returns the `EmployeeInfo` data item that corresponds to the selected `EmployeeName`.</span></span> <span data-ttu-id="9c6c5-115">Protože je však <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> <xref:System.Windows.Controls.TreeView> nastaveno na `EmployeeNumber` , <xref:System.Windows.Controls.TreeView.SelectedValue%2A> je nastavena na `EmployeeNumber` .</span><span class="sxs-lookup"><span data-stu-id="9c6c5-115">However, because the <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> of this <xref:System.Windows.Controls.TreeView> is set to `EmployeeNumber`, the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> is set to the `EmployeeNumber`.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a><span data-ttu-id="9c6c5-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="9c6c5-116">See also</span></span>

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [<span data-ttu-id="9c6c5-117">TreeView – přehled</span><span class="sxs-lookup"><span data-stu-id="9c6c5-117">TreeView Overview</span></span>](treeview-overview.md)
- [<span data-ttu-id="9c6c5-118">– postupy</span><span class="sxs-lookup"><span data-stu-id="9c6c5-118">How-to Topics</span></span>](treeview-how-to-topics.md)
