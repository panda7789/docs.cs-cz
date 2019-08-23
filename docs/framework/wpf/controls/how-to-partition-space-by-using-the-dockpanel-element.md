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
# <a name="how-to-partition-space-by-using-the-dockpanel-element"></a><span data-ttu-id="559d3-102">Postupy: Rozdělení prostoru pomocí elementu DockPanel</span><span class="sxs-lookup"><span data-stu-id="559d3-102">How to: Partition Space by Using the DockPanel Element</span></span>
<span data-ttu-id="559d3-103">Následující příklad vytvoří jednoduché [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] rozhraní <xref:System.Windows.Controls.DockPanel> pomocí elementu.</span><span class="sxs-lookup"><span data-stu-id="559d3-103">The following example creates a simple [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] framework using a <xref:System.Windows.Controls.DockPanel> element.</span></span> <span data-ttu-id="559d3-104"><xref:System.Windows.Controls.DockPanel> Oddíly dostupné místo pro jeho podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="559d3-104">The <xref:System.Windows.Controls.DockPanel> partitions available space to its child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="559d3-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="559d3-105">Example</span></span>  
 <span data-ttu-id="559d3-106">V tomto příkladu se <xref:System.Windows.Controls.DockPanel.Dock%2A> používá vlastnost, která je připojená vlastnost, k ukotvení <xref:System.Windows.Controls.Border> dvou identických <xref:System.Windows.Controls.Dock.Top> prvků v prostoru děleného v oddílu.</span><span class="sxs-lookup"><span data-stu-id="559d3-106">This example uses the <xref:System.Windows.Controls.DockPanel.Dock%2A> property, which is an attached property, to dock two identical <xref:System.Windows.Controls.Border> elements at the <xref:System.Windows.Controls.Dock.Top> of the partitioned space.</span></span> <span data-ttu-id="559d3-107">Třetí <xref:System.Windows.Controls.Border> prvek je ukotven <xref:System.Windows.Controls.Dock.Left>na, s jeho šířkou nastavenou na 200 pixelů.</span><span class="sxs-lookup"><span data-stu-id="559d3-107">A third <xref:System.Windows.Controls.Border> element is docked to the <xref:System.Windows.Controls.Dock.Left>, with its width set to 200 pixels.</span></span> <span data-ttu-id="559d3-108">Čtvrtá <xref:System.Windows.Controls.Border> je ukotvená <xref:System.Windows.Controls.Dock.Bottom> na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="559d3-108">A fourth <xref:System.Windows.Controls.Border> is docked to the <xref:System.Windows.Controls.Dock.Bottom> of the screen.</span></span> <span data-ttu-id="559d3-109">Poslední <xref:System.Windows.Controls.Border> prvek automaticky vyplní zbývající prostor.</span><span class="sxs-lookup"><span data-stu-id="559d3-109">The last <xref:System.Windows.Controls.Border> element automatically fills the remaining space.</span></span>  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
> <span data-ttu-id="559d3-110">Ve výchozím nastavení poslední podřízená položka <xref:System.Windows.Controls.DockPanel> elementu vyplní zbývající nepřidělené místo.</span><span class="sxs-lookup"><span data-stu-id="559d3-110">By default, the last child of a <xref:System.Windows.Controls.DockPanel> element fills the remaining unallocated space.</span></span> <span data-ttu-id="559d3-111">Pokud toto chování nechcete, nastavte `LastChildFill="False"`.</span><span class="sxs-lookup"><span data-stu-id="559d3-111">If you do not want this behavior, set `LastChildFill="False"`.</span></span>  
  
 <span data-ttu-id="559d3-112">Kompilovaná aplikace poskytuje nové uživatelské rozhraní, které vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="559d3-112">The compiled application yields a new UI that looks like this.</span></span>  
  
 <span data-ttu-id="559d3-113">![Typický scénář DockPanel.](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")</span><span class="sxs-lookup"><span data-stu-id="559d3-113">![A typical DockPanel scenario.](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="559d3-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="559d3-114">See also</span></span>

- <xref:System.Windows.Controls.DockPanel>
- [<span data-ttu-id="559d3-115">Přehled panelu</span><span class="sxs-lookup"><span data-stu-id="559d3-115">Panels Overview</span></span>](panels-overview.md)
