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
ms.openlocfilehash: 8ca4d7e753282a7c1d2236a70535e10d5109cd3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Přehled panelů](../../../../docs/framework/wpf/controls/panels-overview.md)
