---
title: 'Postupy: Vytvoření jednoduchého nebo složitého zobrazení TreeViews'
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], creating
- Control class [WPF], TreeView [WPF], creating
ms.assetid: 1defbb78-b8e7-4c0e-b650-576453ac828d
ms.openlocfilehash: 7edb4933ebcc0f0d2cb02754238c2342ee9dd4a2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62031912"
---
# <a name="how-to-create-simple-or-complex-treeviews"></a><span data-ttu-id="720d0-102">Postupy: Vytvoření jednoduchého nebo složitého zobrazení TreeViews</span><span class="sxs-lookup"><span data-stu-id="720d0-102">How to: Create Simple or Complex TreeViews</span></span>
<span data-ttu-id="720d0-103">Tento příklad ukazuje, jak vytvořit jednoduché nebo složité <xref:System.Windows.Controls.TreeView> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="720d0-103">This example shows how to create simple or complex <xref:System.Windows.Controls.TreeView> controls.</span></span>  
  
 <span data-ttu-id="720d0-104">A <xref:System.Windows.Controls.TreeView> se skládá z hierarchie <xref:System.Windows.Controls.TreeViewItem> ovládací prvky, které mohou obsahovat jednoduché textových řetězců a také mnohem složitější obsahu, jako například <xref:System.Windows.Controls.Button> ovládací prvky nebo <xref:System.Windows.Controls.StackPanel> s vložený obsah.</span><span class="sxs-lookup"><span data-stu-id="720d0-104">A <xref:System.Windows.Controls.TreeView> consists of a hierarchy of <xref:System.Windows.Controls.TreeViewItem> controls, which can contain simple text strings and also more complex content, such as <xref:System.Windows.Controls.Button> controls or a <xref:System.Windows.Controls.StackPanel> with embedded content.</span></span> <span data-ttu-id="720d0-105">Můžete explicitně definovat <xref:System.Windows.Controls.TreeView> obsah nebo zdroj dat může poskytovat obsahu.</span><span class="sxs-lookup"><span data-stu-id="720d0-105">You can explicitly define the <xref:System.Windows.Controls.TreeView> content or a data source can provide the content.</span></span> <span data-ttu-id="720d0-106">Toto téma obsahuje příklady těchto konceptů.</span><span class="sxs-lookup"><span data-stu-id="720d0-106">This topic provides examples of these concepts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="720d0-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="720d0-107">Example</span></span>  
 <span data-ttu-id="720d0-108"><xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> Vlastnost <xref:System.Windows.Controls.TreeViewItem> obsahuje obsah, který <xref:System.Windows.Controls.TreeView> zobrazí pro danou položku.</span><span class="sxs-lookup"><span data-stu-id="720d0-108">The <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property of the <xref:System.Windows.Controls.TreeViewItem> contains the content that the <xref:System.Windows.Controls.TreeView> displays for that item.</span></span> <span data-ttu-id="720d0-109">A <xref:System.Windows.Controls.TreeViewItem> může mít také <xref:System.Windows.Controls.TreeViewItem> ovládací prvky jako jeho podřízené prvky a můžete definovat pomocí těchto podřízených elementů <xref:System.Windows.Controls.ItemsControl.Items%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="720d0-109">A <xref:System.Windows.Controls.TreeViewItem> can also have <xref:System.Windows.Controls.TreeViewItem> controls as its child elements and you can define these child elements by using the <xref:System.Windows.Controls.ItemsControl.Items%2A> property.</span></span>  
  
 <span data-ttu-id="720d0-110">Následující příklad ukazuje, jak explicitně definovat <xref:System.Windows.Controls.TreeViewItem> obsahu tak, že nastavíte <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> vlastnost textový řetězec.</span><span class="sxs-lookup"><span data-stu-id="720d0-110">The following example shows how to explicitly define <xref:System.Windows.Controls.TreeViewItem> content by setting the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property to a text string.</span></span>  
  
 [!code-xaml[TreeViewSimple#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#1)]  
  
 <span data-ttu-id="720d0-111">Následující příklad ukazuje, jak definovat podřízené prvky <xref:System.Windows.Controls.TreeViewItem> definováním <xref:System.Windows.Controls.ItemsControl.Items%2A> , které jsou <xref:System.Windows.Controls.Button> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="720d0-111">The following example show how to define child elements of a <xref:System.Windows.Controls.TreeViewItem> by defining <xref:System.Windows.Controls.ItemsControl.Items%2A> that are <xref:System.Windows.Controls.Button> controls.</span></span>  
  
 [!code-xaml[TreeViewSimple#3](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#3)]  
  
 <span data-ttu-id="720d0-112">Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.TreeView> kde <xref:System.Windows.Data.XmlDataProvider> poskytuje <xref:System.Windows.Controls.TreeViewItem> obsah a <xref:System.Windows.HierarchicalDataTemplate> definuje vzhled elementů obsah.</span><span class="sxs-lookup"><span data-stu-id="720d0-112">The following example shows how to create a <xref:System.Windows.Controls.TreeView> where an <xref:System.Windows.Data.XmlDataProvider> provides <xref:System.Windows.Controls.TreeViewItem> content and a <xref:System.Windows.HierarchicalDataTemplate> defines the appearance of the content.</span></span>  
  
 [!code-xaml[TreeViewSimple#6](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#6)]  
  
 [!code-xaml[TreeViewSimple#7](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#7)]  
  
 [!code-xaml[TreeViewSimple#5](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#5)]  
  
 <span data-ttu-id="720d0-113">Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.TreeView> kde <xref:System.Windows.Controls.TreeViewItem> obsahuje obsah <xref:System.Windows.Controls.DockPanel> ovládací prvky, které se mají vložit obsah.</span><span class="sxs-lookup"><span data-stu-id="720d0-113">The following example shows how to create a <xref:System.Windows.Controls.TreeView> where the <xref:System.Windows.Controls.TreeViewItem> content contains <xref:System.Windows.Controls.DockPanel> controls that have embedded content.</span></span>  
  
 [!code-xaml[TreeViewSimple#9](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#9)]  
  
## <a name="see-also"></a><span data-ttu-id="720d0-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="720d0-114">See also</span></span>

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [<span data-ttu-id="720d0-115">TreeView – přehled</span><span class="sxs-lookup"><span data-stu-id="720d0-115">TreeView Overview</span></span>](treeview-overview.md)
- [<span data-ttu-id="720d0-116">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="720d0-116">How-to Topics</span></span>](treeview-how-to-topics.md)
