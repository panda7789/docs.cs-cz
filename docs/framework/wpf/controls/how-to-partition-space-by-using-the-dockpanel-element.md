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
ms.openlocfilehash: d22a808ce3ab95e3b351408bf4cc372a335da553
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960189"
---
# <a name="how-to-partition-space-by-using-the-dockpanel-element"></a>Postupy: Rozdělení prostoru pomocí elementu DockPanel
Následující příklad vytvoří jednoduché [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] rozhraní <xref:System.Windows.Controls.DockPanel> pomocí elementu. <xref:System.Windows.Controls.DockPanel> Oddíly dostupné místo pro jeho podřízené prvky.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se <xref:System.Windows.Controls.DockPanel.Dock%2A> používá vlastnost, která je připojená vlastnost, k ukotvení <xref:System.Windows.Controls.Border> dvou identických <xref:System.Windows.Controls.Dock.Top> prvků v prostoru děleného v oddílu. Třetí <xref:System.Windows.Controls.Border> prvek je ukotven <xref:System.Windows.Controls.Dock.Left>na, s jeho šířkou nastavenou na 200 pixelů. Čtvrtá <xref:System.Windows.Controls.Border> je ukotvená <xref:System.Windows.Controls.Dock.Bottom> na obrazovce. Poslední <xref:System.Windows.Controls.Border> prvek automaticky vyplní zbývající prostor.  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
> Ve výchozím nastavení poslední podřízená položka <xref:System.Windows.Controls.DockPanel> elementu vyplní zbývající nepřidělené místo. Pokud toto chování nechcete, nastavte `LastChildFill="False"`.  
  
 Kompilovaná aplikace poskytuje nové uživatelské rozhraní, které vypadá takto.  
  
 ![Typický scénář DockPanel.](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.DockPanel>
- [Přehled panelu](panels-overview.md)
