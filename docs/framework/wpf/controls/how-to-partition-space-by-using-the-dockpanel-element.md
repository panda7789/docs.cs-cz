---
title: 'Postupy: Rozdělení prostoru pomocí elementu DockPanel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], DockPanel
- DockPanel control [WPF], partitioning space
- partitioning space [WPF]
ms.assetid: a219b9e5-b205-4438-89b5-0a137ac463ab
ms.openlocfilehash: ab51270644bf370944ebc933c765b40c528681c5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158883"
---
# <a name="how-to-partition-space-by-using-the-dockpanel-element"></a>Postupy: Rozdělení prostoru pomocí elementu DockPanel
Následující příklad vytvoří jednoduchý [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] pomocí rozhraní framework <xref:System.Windows.Controls.DockPanel> elementu. <xref:System.Windows.Controls.DockPanel> Oddíly dostupné místo na jeho podřízené prvky.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu <xref:System.Windows.Controls.DockPanel.Dock%2A> vlastnost, která je připojená vlastnost, dva identické ukotvení <xref:System.Windows.Controls.Border> prvky v <xref:System.Windows.Controls.Dock.Top> dělené místa. Třetí <xref:System.Windows.Controls.Border> prvek ukotven <xref:System.Windows.Controls.Dock.Left>, s jeho šířku nastaveno na 200 pixelů. Čtvrtý <xref:System.Windows.Controls.Border> ukotven <xref:System.Windows.Controls.Dock.Bottom> obrazovky. Poslední <xref:System.Windows.Controls.Border> element automaticky vyplní zbývající místo.  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
>  Ve výchozím nastavení posledního podřízeného člena <xref:System.Windows.Controls.DockPanel> prvek vyplní zbývající volné místo. Pokud nechcete, aby toto chování, nastavte `LastChildFill="False"`.  
  
 Kompilované aplikace poskytuje nové uživatelské rozhraní, který vypadá takto.  
  
 ![Typický scénář DockPanel. ](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.DockPanel>
- [Přehled panelů](panels-overview.md)
