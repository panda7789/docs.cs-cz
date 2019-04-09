---
title: 'Postupy: Získání nebo nastavení hodnoty ukotvení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dock values [WPF], setting
- Dock values [WPF], getting
ms.assetid: fcf4ab8a-c7cd-4835-8d04-de1c999ab4a8
ms.openlocfilehash: fb6c8a7d62aa09a6e1d82cb4079d1425a7f39f8c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160730"
---
# <a name="how-to-get-or-set-a-dock-value"></a>Postupy: Získání nebo nastavení hodnoty ukotvení
Následující příklad ukazuje, jak přiřadit <xref:System.Windows.Controls.Dock> hodnotu objektu. V příkladu se používá <xref:System.Windows.Controls.DockPanel.GetDock%2A> a <xref:System.Windows.Controls.DockPanel.SetDock%2A> metody <xref:System.Windows.Controls.DockPanel>.  
  
## <a name="example"></a>Příklad  
 Tento příklad vytvoří instanci <xref:System.Windows.Controls.TextBlock> elementu, `txt1`a přiřadí <xref:System.Windows.Controls.Dock> hodnotu `Top` pomocí <xref:System.Windows.Controls.DockPanel.SetDock%2A> metoda <xref:System.Windows.Controls.DockPanel>. Potom přidá hodnotu <xref:System.Windows.Controls.Dock> vlastnost <xref:System.Windows.Controls.TextBlock.Text%2A> z <xref:System.Windows.Controls.TextBlock> elementu s použitím <xref:System.Windows.Controls.DockPanel.GetDock%2A> metoda. Nakonec příklad přidá <xref:System.Windows.Controls.TextBlock> do nadřazeného elementu <xref:System.Windows.Controls.DockPanel>, `dp1`.  
  
 [!code-csharp[DockPanelSetDock#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelSetDock/CSharp/DockPanel_SetDock.cs#1)]
 [!code-vb[DockPanelSetDock#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelSetDock/VisualBasic/DockPanel_SetDock.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.DockPanel>
- <xref:System.Windows.Controls.DockPanel.GetDock%2A>
- <xref:System.Windows.Controls.DockPanel.SetDock%2A>
- [Přehled panelů](panels-overview.md)
