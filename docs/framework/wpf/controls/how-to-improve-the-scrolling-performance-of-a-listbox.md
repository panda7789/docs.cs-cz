---
title: "Postupy: Zvýšení výkonu posunování prvku ListBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListBox control [WPF], reusing item containers
- ListBox control [WPF], improving scrolling performance
ms.assetid: 1e2bf8f3-c8ce-47f7-a400-a7fe11d1a848
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 58435948a3ddd8042b95b30b8d6cbdba984f34d5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
