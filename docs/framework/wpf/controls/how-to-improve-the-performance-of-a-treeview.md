---
title: 'Postupy: Zvýšení výkonu TreeView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TreeView control [WPF], improving the performance
ms.assetid: b792c740-cf2b-4da8-8ba8-3d2e5a821874
ms.openlocfilehash: de1b46da2a7c6c3db0c0c19cdbb654fcf2fbbd6c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771004"
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
