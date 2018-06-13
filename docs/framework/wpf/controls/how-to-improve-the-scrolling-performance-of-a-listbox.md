---
title: 'Postupy: Zvýšení výkonu posunování prvku ListBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListBox control [WPF], reusing item containers
- ListBox control [WPF], improving scrolling performance
ms.assetid: 1e2bf8f3-c8ce-47f7-a400-a7fe11d1a848
ms.openlocfilehash: 224b996ad97d9a71ce43023143b68c2ab5b8467b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552789"
---
# <a name="how-to-improve-the-scrolling-performance-of-a-listbox"></a>Postupy: Zvýšení výkonu posunování prvku ListBox
Pokud <xref:System.Windows.Controls.ListBox> obsahuje mnoho položek rozhraní odpověď uživatele může být pomalé, co uživatel posune <xref:System.Windows.Controls.ListBox> pomocí kolečka myši nebo přetažením úchytu posuvníku. Může zlepšit výkon <xref:System.Windows.Controls.ListBox> když uživatel posune nastavením `VirtualizingStackPanel.VirtualizationMode` přidružená vlastnost k <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.  
  
## <a name="example"></a>Příklad  
  
## <a name="description"></a>Popis  
Následující příklad vytvoří <xref:System.Windows.Controls.ListBox> a nastaví `VirtualizingStackPanel.VirtualizationMode` přidružená vlastnost k <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> ke zlepšení výkonu při posouvání.  
  
## <a name="code"></a>Kód  
 [!code-xaml[RecycleItemContainerShippets#VirtualizationMode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizationmode)]  
  
 Následující příklad ukazuje data, že předchozí příklad používá.  
  
 [!code-csharp[RecycleItemContainerShippets#ListBoxData](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#listboxdata)]
 [!code-vb[RecycleItemContainerShippets#ListBoxData](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#listboxdata)]
