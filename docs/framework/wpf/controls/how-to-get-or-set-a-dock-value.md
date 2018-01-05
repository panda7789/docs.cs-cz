---
title: "Postupy: Načtení a nastavení hodnoty ukotvení"
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
- Dock values [WPF], setting
- Dock values [WPF], getting
ms.assetid: fcf4ab8a-c7cd-4835-8d04-de1c999ab4a8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7d663acf446ee2f7a36fc2d0c8605c31a0f2a84
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-or-set-a-dock-value"></a>Postupy: Načtení a nastavení hodnoty ukotvení
Následující příklad ukazuje, jak přiřadit <xref:System.Windows.Controls.Dock> hodnotu objektu. V příkladu se používá <xref:System.Windows.Controls.DockPanel.GetDock%2A> a <xref:System.Windows.Controls.DockPanel.SetDock%2A> metody <xref:System.Windows.Controls.DockPanel>.  
  
## <a name="example"></a>Příklad  
 V příkladu se vytváří instance <xref:System.Windows.Controls.TextBlock> elementu `txt1`a přiřadí <xref:System.Windows.Controls.Dock> hodnotu `Top` pomocí <xref:System.Windows.Controls.DockPanel.SetDock%2A> metodu <xref:System.Windows.Controls.DockPanel>. Potom přidá hodnotu <xref:System.Windows.Controls.Dock> vlastnost, která má <xref:System.Windows.Controls.TextBlock.Text%2A> z <xref:System.Windows.Controls.TextBlock> element pomocí <xref:System.Windows.Controls.DockPanel.GetDock%2A> metoda. Nakonec v příkladu přidáme <xref:System.Windows.Controls.TextBlock> element s nadřazeným <xref:System.Windows.Controls.DockPanel>, `dp1`.  
  
 [!code-csharp[DockPanelSetDock#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelSetDock/CSharp/DockPanel_SetDock.cs#1)]
 [!code-vb[DockPanelSetDock#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelSetDock/VisualBasic/DockPanel_SetDock.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.DockPanel>  
 <xref:System.Windows.Controls.DockPanel.GetDock%2A>  
 <xref:System.Windows.Controls.DockPanel.SetDock%2A>  
 [Přehled panelu](../../../../docs/framework/wpf/controls/panels-overview.md)
