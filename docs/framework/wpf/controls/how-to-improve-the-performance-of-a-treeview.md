---
title: 'Postupy: Zvýšení výkonu TreeView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TreeView control [WPF], improving the performance
ms.assetid: b792c740-cf2b-4da8-8ba8-3d2e5a821874
ms.openlocfilehash: 75f17c770af89f08fedfd3c8193a916901fe6f79
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-improve-the-performance-of-a-treeview"></a>Postupy: Zvýšení výkonu TreeView
Pokud <xref:System.Windows.Controls.TreeView> obsahuje mnoho položek, množství času potřebné k načtení může způsobit významné zpoždění v uživatelském rozhraní. Čas načítání lze vylepšit nastavení `VirtualizingStackPanel.IsVirtualizing` přidružená vlastnost k `true`.  Uživatelské rozhraní také může být pomalé reagovat, když se uživatel posune <xref:System.Windows.Controls.TreeView> pomocí kolečka myši nebo přetažením úchytu posuvníku. Může zlepšit výkon <xref:System.Windows.Controls.TreeView> když uživatel posune nastavením `VirtualizingStackPanel.VirtualizationMode` přidružená vlastnost k <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.  
  
## <a name="example"></a>Příklad  
  
## <a name="description"></a>Popis  
Následující příklad vytvoří <xref:System.Windows.Controls.TreeView> , který nastavuje `VirtualizingStackPanel.IsVirtualizing` přidružená vlastnost na hodnotu true a `VirtualizingStackPanel.VirtualizationMode` přidružená vlastnost k <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> za účelem optimalizace jeho výkon.  
  
## <a name="code"></a>Kód  
 [!code-xaml[RecycleItemContainerShippets#VirtualizingTreeView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizingtreeview)]  
  
 Následující příklad ukazuje data, že předchozí příklad používá.  
  
 [!code-csharp[RecycleItemContainerShippets#TreeViewData](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#treeviewdata)]
 [!code-vb[RecycleItemContainerShippets#TreeViewData](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#treeviewdata)]  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
