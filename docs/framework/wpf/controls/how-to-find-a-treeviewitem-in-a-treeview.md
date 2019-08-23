---
title: 'Postupy: Hledání TreeViewItem v objektu TreeView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TreeView control [WPF], finding a TreeViewItem
- TreeViewItem [WPF], finding
ms.assetid: 72ecd40c-3939-4e01-b617-5e9daa6074d9
ms.openlocfilehash: ad72c7a7fb11dfe605db4119dde831b47dd7c5a4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962095"
---
# <a name="how-to-find-a-treeviewitem-in-a-treeview"></a><span data-ttu-id="a8387-102">Postupy: Hledání TreeViewItem v objektu TreeView</span><span class="sxs-lookup"><span data-stu-id="a8387-102">How to: Find a TreeViewItem in a TreeView</span></span>
<span data-ttu-id="a8387-103"><xref:System.Windows.Controls.TreeView> Ovládací prvek poskytuje pohodlný způsob zobrazení hierarchických dat.</span><span class="sxs-lookup"><span data-stu-id="a8387-103">The <xref:System.Windows.Controls.TreeView> control provides a convenient way to display hierarchical data.</span></span> <span data-ttu-id="a8387-104">Pokud je svázán se zdrojem dat <xref:System.Windows.Controls.TreeView.SelectedItem%2A> , poskytuje vlastnost pohodlný způsob, jak rychle načíst vybraný datový objekt. <xref:System.Windows.Controls.TreeView></span><span class="sxs-lookup"><span data-stu-id="a8387-104">If your <xref:System.Windows.Controls.TreeView> is bound to a data source, the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> property provides a convenient way for you to quickly retrieve the selected data object.</span></span> <span data-ttu-id="a8387-105">Obvykle je nejvhodnější pracovat s podkladovým datovým objektem, ale někdy může být nutné programově manipulovat s daty, která obsahují <xref:System.Windows.Controls.TreeViewItem>.</span><span class="sxs-lookup"><span data-stu-id="a8387-105">It is typically best to work with the underlying data object, but sometimes you may need to programmatically manipulate the data's containing <xref:System.Windows.Controls.TreeViewItem>.</span></span> <span data-ttu-id="a8387-106">Například může být nutné programově rozbalit <xref:System.Windows.Controls.TreeViewItem>nebo vybrat jinou položku <xref:System.Windows.Controls.TreeView>v.</span><span class="sxs-lookup"><span data-stu-id="a8387-106">For example, you may need to programmatically expand the <xref:System.Windows.Controls.TreeViewItem>, or select a different item in the <xref:System.Windows.Controls.TreeView>.</span></span>  
  
 <span data-ttu-id="a8387-107">Chcete-li <xref:System.Windows.Controls.TreeViewItem> najít, který obsahuje konkrétní datový objekt, je nutné procházet jednotlivé úrovně. <xref:System.Windows.Controls.TreeView></span><span class="sxs-lookup"><span data-stu-id="a8387-107">To find a <xref:System.Windows.Controls.TreeViewItem> that contains a specific data object, you must traverse each level of the <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="a8387-108">Položky v <xref:System.Windows.Controls.TreeView> může být také virtualizované pro zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="a8387-108">The items in a <xref:System.Windows.Controls.TreeView> can also be virtualized to improve performance.</span></span> <span data-ttu-id="a8387-109">V případě, že položky mohou být virtualizované, je také nutné si uvědomit a <xref:System.Windows.Controls.TreeViewItem> ověřit, zda obsahuje datový objekt.</span><span class="sxs-lookup"><span data-stu-id="a8387-109">In the case where items might be virtualized, you also must realize a <xref:System.Windows.Controls.TreeViewItem> to check whether it contains the data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8387-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="a8387-110">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="a8387-111">Popis</span><span class="sxs-lookup"><span data-stu-id="a8387-111">Description</span></span>  
 <span data-ttu-id="a8387-112">Následující příklad vyhledá <xref:System.Windows.Controls.TreeView> konkrétní objekt a vrátí objekt obsahující <xref:System.Windows.Controls.TreeViewItem>.</span><span class="sxs-lookup"><span data-stu-id="a8387-112">The following example searches a <xref:System.Windows.Controls.TreeView> for a specific object and returns the object's containing <xref:System.Windows.Controls.TreeViewItem>.</span></span> <span data-ttu-id="a8387-113">V příkladu je zajištěna <xref:System.Windows.Controls.TreeViewItem> instance každého z nich, aby bylo možné prohledávat jeho podřízené položky.</span><span class="sxs-lookup"><span data-stu-id="a8387-113">The example ensures that each <xref:System.Windows.Controls.TreeViewItem> is instantiated so that its child items can be searched.</span></span> <span data-ttu-id="a8387-114">Tento příklad funguje také v případě <xref:System.Windows.Controls.TreeView> , že nepoužívá virtualizované položky.</span><span class="sxs-lookup"><span data-stu-id="a8387-114">This example also works if the <xref:System.Windows.Controls.TreeView> does not use virtualized items.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a8387-115">Následující příklad funguje pro všechny <xref:System.Windows.Controls.TreeView>bez ohledu na podkladový datový model a vyhledá každý <xref:System.Windows.Controls.TreeViewItem> , dokud se objekt nenajde.</span><span class="sxs-lookup"><span data-stu-id="a8387-115">The following example works for any <xref:System.Windows.Controls.TreeView>, regardless of the underlying data model, and searches every <xref:System.Windows.Controls.TreeViewItem> until the object is found.</span></span> <span data-ttu-id="a8387-116">Dalším způsobem, který má lepší výkon, je vyhledat datový model pro zadaný objekt, sledovat jeho umístění v rámci hierarchie dat a potom najít odpovídající <xref:System.Windows.Controls.TreeViewItem> <xref:System.Windows.Controls.TreeView>v.</span><span class="sxs-lookup"><span data-stu-id="a8387-116">Another technique that has better performance is to search the data model for the specified object, keep track of its location within the data hierarchy, and then find the corresponding <xref:System.Windows.Controls.TreeViewItem> in the <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="a8387-117">Nicméně technika, která má vyšší výkon, vyžaduje znalost datového modelu a nelze ji zobecnit pro všechny uvedené <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="a8387-117">However, the technique that has better performance requires knowledge of the data model and cannot be generalized for any given <xref:System.Windows.Controls.TreeView>.</span></span>  
  
## <a name="code"></a><span data-ttu-id="a8387-118">Kód</span><span class="sxs-lookup"><span data-stu-id="a8387-118">Code</span></span>  
 [!code-csharp[TreeViewFindTVI#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 <span data-ttu-id="a8387-119">Předchozí kód spoléhá na vlastní <xref:System.Windows.Controls.VirtualizingStackPanel> , který zpřístupňuje metodu s názvem. `BringIntoView`</span><span class="sxs-lookup"><span data-stu-id="a8387-119">The previous code relies on a custom <xref:System.Windows.Controls.VirtualizingStackPanel> that exposes a method named `BringIntoView`.</span></span> <span data-ttu-id="a8387-120">Následující kód definuje vlastní <xref:System.Windows.Controls.VirtualizingStackPanel>.</span><span class="sxs-lookup"><span data-stu-id="a8387-120">The following code defines the custom <xref:System.Windows.Controls.VirtualizingStackPanel>.</span></span>  
  
 [!code-csharp[TreeViewFindTVI#2](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 <span data-ttu-id="a8387-121">Následující kód XAML ukazuje <xref:System.Windows.Controls.TreeView> , jak vytvořit, který používá vlastní. <xref:System.Windows.Controls.VirtualizingStackPanel></span><span class="sxs-lookup"><span data-stu-id="a8387-121">The following XAML shows how to create a <xref:System.Windows.Controls.TreeView> that uses the custom <xref:System.Windows.Controls.VirtualizingStackPanel>.</span></span>  
  
 [!code-xaml[TreeViewFindTVI#3](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="a8387-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a8387-122">See also</span></span>

- [<span data-ttu-id="a8387-123">Zvýšení výkonu TreeView</span><span class="sxs-lookup"><span data-stu-id="a8387-123">Improve the Performance of a TreeView</span></span>](how-to-improve-the-performance-of-a-treeview.md)
