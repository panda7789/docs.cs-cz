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
ms.openlocfilehash: 034ec2e57fb3b6a9b3a81f66f6888a68e2c113d7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910530"
---
# <a name="how-to-find-a-treeviewitem-in-a-treeview"></a><span data-ttu-id="388d4-102">Postupy: Hledání TreeViewItem v objektu TreeView</span><span class="sxs-lookup"><span data-stu-id="388d4-102">How to: Find a TreeViewItem in a TreeView</span></span>
<span data-ttu-id="388d4-103"><xref:System.Windows.Controls.TreeView> Řízení poskytuje pohodlný způsob, jak zobrazit hierarchická data.</span><span class="sxs-lookup"><span data-stu-id="388d4-103">The <xref:System.Windows.Controls.TreeView> control provides a convenient way to display hierarchical data.</span></span> <span data-ttu-id="388d4-104">Pokud vaše <xref:System.Windows.Controls.TreeView> je svázán se zdrojem dat <xref:System.Windows.Controls.TreeView.SelectedItem%2A> vlastnost představuje pohodlný způsob pro vám umožní rychle načíst zvoleného datového objektu.</span><span class="sxs-lookup"><span data-stu-id="388d4-104">If your <xref:System.Windows.Controls.TreeView> is bound to a data source, the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> property provides a convenient way for you to quickly retrieve the selected data object.</span></span> <span data-ttu-id="388d4-105">Je obvykle nejlepší pro práci s podkladového datového objektu, ale v některých případech je nutné programově manipulovat s dat obsahující <xref:System.Windows.Controls.TreeViewItem>.</span><span class="sxs-lookup"><span data-stu-id="388d4-105">It is typically best to work with the underlying data object, but sometimes you may need to programmatically manipulate the data's containing <xref:System.Windows.Controls.TreeViewItem>.</span></span> <span data-ttu-id="388d4-106">Budete například muset prostřednictvím kódu programu rozbalte <xref:System.Windows.Controls.TreeViewItem>, nebo vyberte jiné položce v <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="388d4-106">For example, you may need to programmatically expand the <xref:System.Windows.Controls.TreeViewItem>, or select a different item in the <xref:System.Windows.Controls.TreeView>.</span></span>  
  
 <span data-ttu-id="388d4-107">K vyhledání <xref:System.Windows.Controls.TreeViewItem> , která obsahuje objekt konkrétní data, musí procházet jednotlivé úrovně <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="388d4-107">To find a <xref:System.Windows.Controls.TreeViewItem> that contains a specific data object, you must traverse each level of the <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="388d4-108">Položky v <xref:System.Windows.Controls.TreeView> se také dají Virtualizovat ke zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="388d4-108">The items in a <xref:System.Windows.Controls.TreeView> can also be virtualized to improve performance.</span></span> <span data-ttu-id="388d4-109">V případě, kde může virtualizované položky, je nutné si uvědomit <xref:System.Windows.Controls.TreeViewItem> ke kontrole, zda datový objekt obsahuje.</span><span class="sxs-lookup"><span data-stu-id="388d4-109">In the case where items might be virtualized, you also must realize a <xref:System.Windows.Controls.TreeViewItem> to check whether it contains the data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="388d4-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="388d4-110">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="388d4-111">Popis</span><span class="sxs-lookup"><span data-stu-id="388d4-111">Description</span></span>  
 <span data-ttu-id="388d4-112">Následující příklady hledání <xref:System.Windows.Controls.TreeView> pro konkrétní objekt a vrátí objekt obsahující <xref:System.Windows.Controls.TreeViewItem>.</span><span class="sxs-lookup"><span data-stu-id="388d4-112">The following example searches a <xref:System.Windows.Controls.TreeView> for a specific object and returns the object's containing <xref:System.Windows.Controls.TreeViewItem>.</span></span> <span data-ttu-id="388d4-113">V příkladu se každý zajišťuje <xref:System.Windows.Controls.TreeViewItem> je vytvořena instance tak, aby její podřízené položky lze prohledávat.</span><span class="sxs-lookup"><span data-stu-id="388d4-113">The example ensures that each <xref:System.Windows.Controls.TreeViewItem> is instantiated so that its child items can be searched.</span></span> <span data-ttu-id="388d4-114">Tento příklad funguje taky Pokud <xref:System.Windows.Controls.TreeView> nepoužívá virtualizované položky.</span><span class="sxs-lookup"><span data-stu-id="388d4-114">This example also works if the <xref:System.Windows.Controls.TreeView> does not use virtualized items.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="388d4-115">Následující příklad funguje pro všechny <xref:System.Windows.Controls.TreeView>, bez ohledu na základní datový model a prohledávání všech <xref:System.Windows.Controls.TreeViewItem> dokud nebude nalezen objekt.</span><span class="sxs-lookup"><span data-stu-id="388d4-115">The following example works for any <xref:System.Windows.Controls.TreeView>, regardless of the underlying data model, and searches every <xref:System.Windows.Controls.TreeViewItem> until the object is found.</span></span> <span data-ttu-id="388d4-116">Další technikou, který má lepší výkon je hledání datový model pro zadaný objekt, udržovat přehled o jeho umístění v rámci hierarchie dat a pak vyhledejte odpovídající <xref:System.Windows.Controls.TreeViewItem> v <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="388d4-116">Another technique that has better performance is to search the data model for the specified object, keep track of its location within the data hierarchy, and then find the corresponding <xref:System.Windows.Controls.TreeViewItem> in the <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="388d4-117">Ale techniku, která má lepší výkon vyžaduje znalosti datového modelu a nedá zobecnit pro každá <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="388d4-117">However, the technique that has better performance requires knowledge of the data model and cannot be generalized for any given <xref:System.Windows.Controls.TreeView>.</span></span>  
  
## <a name="code"></a><span data-ttu-id="388d4-118">Kód</span><span class="sxs-lookup"><span data-stu-id="388d4-118">Code</span></span>  
 [!code-csharp[TreeViewFindTVI#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 <span data-ttu-id="388d4-119">Předchozí kód závisí na vlastní <xref:System.Windows.Controls.VirtualizingStackPanel> , která zpřístupní metodu s názvem `BringIntoView`.</span><span class="sxs-lookup"><span data-stu-id="388d4-119">The previous code relies on a custom <xref:System.Windows.Controls.VirtualizingStackPanel> that exposes a method named `BringIntoView`.</span></span> <span data-ttu-id="388d4-120">Následující kód definuje vlastní <xref:System.Windows.Controls.VirtualizingStackPanel>.</span><span class="sxs-lookup"><span data-stu-id="388d4-120">The following code defines the custom <xref:System.Windows.Controls.VirtualizingStackPanel>.</span></span>  
  
 [!code-csharp[TreeViewFindTVI#2](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 <span data-ttu-id="388d4-121">Následující XAML ukazuje, jak vytvořit <xref:System.Windows.Controls.TreeView> , která používá vlastní <xref:System.Windows.Controls.VirtualizingStackPanel>.</span><span class="sxs-lookup"><span data-stu-id="388d4-121">The following XAML shows how to create a <xref:System.Windows.Controls.TreeView> that uses the custom <xref:System.Windows.Controls.VirtualizingStackPanel>.</span></span>  
  
 [!code-xaml[TreeViewFindTVI#3](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="388d4-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="388d4-122">See also</span></span>

- [<span data-ttu-id="388d4-123">Zvýšení výkonu TreeView</span><span class="sxs-lookup"><span data-stu-id="388d4-123">Improve the Performance of a TreeView</span></span>](how-to-improve-the-performance-of-a-treeview.md)
