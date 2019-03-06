---
title: 'Postupy: Zvýšení výkonu TreeView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TreeView control [WPF], improving the performance
ms.assetid: b792c740-cf2b-4da8-8ba8-3d2e5a821874
ms.openlocfilehash: d04d5997e6f02a4227704b668fdf19324ea20f26
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364733"
---
# <a name="how-to-improve-the-performance-of-a-treeview"></a><span data-ttu-id="ba3d4-102">Postupy: Zvýšení výkonu TreeView</span><span class="sxs-lookup"><span data-stu-id="ba3d4-102">How to: Improve the Performance of a TreeView</span></span>
<span data-ttu-id="ba3d4-103">Pokud <xref:System.Windows.Controls.TreeView> obsahuje mnoho položek množství čas potřebný k načtení může způsobit, že k poměrně dlouhodobému výpadku v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ba3d4-103">If a <xref:System.Windows.Controls.TreeView> contains many items, the amount of time it takes to load may cause a significant delay in the user interface.</span></span> <span data-ttu-id="ba3d4-104">Doba načtení můžete zvýšit tak, že nastavíte `VirtualizingStackPanel.IsVirtualizing` připojené vlastnosti `true`.</span><span class="sxs-lookup"><span data-stu-id="ba3d4-104">You can improve the load time by setting the `VirtualizingStackPanel.IsVirtualizing` attached property to `true`.</span></span>  <span data-ttu-id="ba3d4-105">Uživatelské rozhraní může být také pomalá reagovat pokaždé, když bude uživatel posouvat <xref:System.Windows.Controls.TreeView> pomocí kolečka myši nebo přetažením thumb posuvník.</span><span class="sxs-lookup"><span data-stu-id="ba3d4-105">The UI might also be slow to react when a user scrolls the <xref:System.Windows.Controls.TreeView> by using the mouse wheel or dragging the thumb of a scrollbar.</span></span> <span data-ttu-id="ba3d4-106">Můžete zvýšit výkon <xref:System.Windows.Controls.TreeView> při procházení tak, že nastavíte `VirtualizingStackPanel.VirtualizationMode` připojené vlastnosti <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ba3d4-106">You can improve the performance of the <xref:System.Windows.Controls.TreeView> when the user scrolls by setting the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba3d4-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="ba3d4-107">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="ba3d4-108">Popis</span><span class="sxs-lookup"><span data-stu-id="ba3d4-108">Description</span></span>  
<span data-ttu-id="ba3d4-109">Následující příklad vytvoří <xref:System.Windows.Controls.TreeView> , který nastavuje `VirtualizingStackPanel.IsVirtualizing` přidružená vlastnost na hodnotu true a `VirtualizingStackPanel.VirtualizationMode` připojené vlastnosti <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> optimalizace jeho výkonu.</span><span class="sxs-lookup"><span data-stu-id="ba3d4-109">The following example creates a <xref:System.Windows.Controls.TreeView> that sets the `VirtualizingStackPanel.IsVirtualizing` attached property to true and the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> to optimize its performance.</span></span>  
  
## <a name="code"></a><span data-ttu-id="ba3d4-110">Kód</span><span class="sxs-lookup"><span data-stu-id="ba3d4-110">Code</span></span>  
 [!code-xaml[RecycleItemContainerShippets#VirtualizingTreeView](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizingtreeview)]  
  
 <span data-ttu-id="ba3d4-111">Následující příklad ukazuje data předchozího příkladu.</span><span class="sxs-lookup"><span data-stu-id="ba3d4-111">The following example shows the data that the previous example uses.</span></span>  
  
 [!code-csharp[RecycleItemContainerShippets#TreeViewData](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#treeviewdata)]
 [!code-vb[RecycleItemContainerShippets#TreeViewData](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#treeviewdata)]  
  
## <a name="see-also"></a><span data-ttu-id="ba3d4-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ba3d4-112">See also</span></span>
- [<span data-ttu-id="ba3d4-113">Ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="ba3d4-113">Controls</span></span>](../advanced/optimizing-performance-controls.md)
