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
ms.openlocfilehash: 6b10fbcd14236f9259dc5772e7f8763c1602d0fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-partition-space-by-using-the-dockpanel-element"></a>Postupy: Rozdělení prostoru pomocí elementu DockPanel
Následující příklad vytvoří jednoduchou [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] framework pomocí <xref:System.Windows.Controls.DockPanel> elementu. <xref:System.Windows.Controls.DockPanel> Oddíly dostupné místo na její podřízené elementy.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Windows.Controls.DockPanel.Dock%2A> vlastnost, která je přidružená vlastnost, k ukotvení dva identické <xref:System.Windows.Controls.Border> prvky v <xref:System.Windows.Controls.Dock.Top> oddílů místa. Třetí <xref:System.Windows.Controls.Border> element ukotven <xref:System.Windows.Controls.Dock.Left>, s celou šířku nastaveno na 200 pixelů. Čtvrtý <xref:System.Windows.Controls.Border> ukotven <xref:System.Windows.Controls.Dock.Bottom> obrazovky. Poslední <xref:System.Windows.Controls.Border> element automaticky vyplní zbývající prostor.  
  
 [!code-cpp[DockPanelOvwSample#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
>  Ve výchozím nastavení posledního podřízeného člena <xref:System.Windows.Controls.DockPanel> element doplní zbývající volné místo. Pokud nechcete, aby toto chování, nastavte `LastChildFill="False"`.  
  
 Kompilované aplikace vypočítá nové uživatelské rozhraní, které vypadá takto.  
  
 ![Typický scénář DockPanel. ] (../../../../docs/framework/wpf/controls/media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.DockPanel>  
 [Přehled panelu](../../../../docs/framework/wpf/controls/panels-overview.md)
