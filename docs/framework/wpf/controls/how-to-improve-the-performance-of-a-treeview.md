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
# <a name="how-to-improve-the-performance-of-a-treeview"></a>Postupy: Zvýšení výkonu TreeView
Pokud <xref:System.Windows.Controls.TreeView> obsahuje mnoho položek množství čas potřebný k načtení může způsobit, že k poměrně dlouhodobému výpadku v uživatelském rozhraní. Doba načtení můžete zvýšit tak, že nastavíte `VirtualizingStackPanel.IsVirtualizing` připojené vlastnosti `true`.  Uživatelské rozhraní může být také pomalá reagovat pokaždé, když bude uživatel posouvat <xref:System.Windows.Controls.TreeView> pomocí kolečka myši nebo přetažením thumb posuvník. Můžete zvýšit výkon <xref:System.Windows.Controls.TreeView> při procházení tak, že nastavíte `VirtualizingStackPanel.VirtualizationMode` připojené vlastnosti <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.  
  
## <a name="example"></a>Příklad  
  
## <a name="description"></a>Popis  
Následující příklad vytvoří <xref:System.Windows.Controls.TreeView> , který nastavuje `VirtualizingStackPanel.IsVirtualizing` přidružená vlastnost na hodnotu true a `VirtualizingStackPanel.VirtualizationMode` připojené vlastnosti <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> optimalizace jeho výkonu.  
  
## <a name="code"></a>Kód  
 [!code-xaml[RecycleItemContainerShippets#VirtualizingTreeView](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizingtreeview)]  
  
 Následující příklad ukazuje data předchozího příkladu.  
  
 [!code-csharp[RecycleItemContainerShippets#TreeViewData](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#treeviewdata)]
 [!code-vb[RecycleItemContainerShippets#TreeViewData](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#treeviewdata)]  
  
## <a name="see-also"></a>Viz také:
- [Ovládací prvky](../advanced/optimizing-performance-controls.md)
