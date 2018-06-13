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
ms.locfileid: "33553881"
---
# <a name="how-to-partition-space-by-using-the-dockpanel-element"></a><span data-ttu-id="510b7-102">Postupy: Rozdělení prostoru pomocí elementu DockPanel</span><span class="sxs-lookup"><span data-stu-id="510b7-102">How to: Partition Space by Using the DockPanel Element</span></span>
<span data-ttu-id="510b7-103">Následující příklad vytvoří jednoduchou [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] framework pomocí <xref:System.Windows.Controls.DockPanel> elementu.</span><span class="sxs-lookup"><span data-stu-id="510b7-103">The following example creates a simple [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] framework using a <xref:System.Windows.Controls.DockPanel> element.</span></span> <span data-ttu-id="510b7-104"><xref:System.Windows.Controls.DockPanel> Oddíly dostupné místo na její podřízené elementy.</span><span class="sxs-lookup"><span data-stu-id="510b7-104">The <xref:System.Windows.Controls.DockPanel> partitions available space to its child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="510b7-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="510b7-105">Example</span></span>  
 <span data-ttu-id="510b7-106">Tento příklad používá <xref:System.Windows.Controls.DockPanel.Dock%2A> vlastnost, která je přidružená vlastnost, k ukotvení dva identické <xref:System.Windows.Controls.Border> prvky v <xref:System.Windows.Controls.Dock.Top> oddílů místa.</span><span class="sxs-lookup"><span data-stu-id="510b7-106">This example uses the <xref:System.Windows.Controls.DockPanel.Dock%2A> property, which is an attached property, to dock two identical <xref:System.Windows.Controls.Border> elements at the <xref:System.Windows.Controls.Dock.Top> of the partitioned space.</span></span> <span data-ttu-id="510b7-107">Třetí <xref:System.Windows.Controls.Border> element ukotven <xref:System.Windows.Controls.Dock.Left>, s celou šířku nastaveno na 200 pixelů.</span><span class="sxs-lookup"><span data-stu-id="510b7-107">A third <xref:System.Windows.Controls.Border> element is docked to the <xref:System.Windows.Controls.Dock.Left>, with its width set to 200 pixels.</span></span> <span data-ttu-id="510b7-108">Čtvrtý <xref:System.Windows.Controls.Border> ukotven <xref:System.Windows.Controls.Dock.Bottom> obrazovky.</span><span class="sxs-lookup"><span data-stu-id="510b7-108">A fourth <xref:System.Windows.Controls.Border> is docked to the <xref:System.Windows.Controls.Dock.Bottom> of the screen.</span></span> <span data-ttu-id="510b7-109">Poslední <xref:System.Windows.Controls.Border> element automaticky vyplní zbývající prostor.</span><span class="sxs-lookup"><span data-stu-id="510b7-109">The last <xref:System.Windows.Controls.Border> element automatically fills the remaining space.</span></span>  
  
 [!code-cpp[DockPanelOvwSample#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
>  <span data-ttu-id="510b7-110">Ve výchozím nastavení posledního podřízeného člena <xref:System.Windows.Controls.DockPanel> element doplní zbývající volné místo.</span><span class="sxs-lookup"><span data-stu-id="510b7-110">By default, the last child of a <xref:System.Windows.Controls.DockPanel> element fills the remaining unallocated space.</span></span> <span data-ttu-id="510b7-111">Pokud nechcete, aby toto chování, nastavte `LastChildFill="False"`.</span><span class="sxs-lookup"><span data-stu-id="510b7-111">If you do not want this behavior, set `LastChildFill="False"`.</span></span>  
  
 <span data-ttu-id="510b7-112">Kompilované aplikace vypočítá nové uživatelské rozhraní, které vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="510b7-112">The compiled application yields a new UI that looks like this.</span></span>  
  
 <span data-ttu-id="510b7-113">![Typický scénář DockPanel. ] (../../../../docs/framework/wpf/controls/media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")</span><span class="sxs-lookup"><span data-stu-id="510b7-113">![A typical DockPanel scenario.](../../../../docs/framework/wpf/controls/media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="510b7-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="510b7-114">See Also</span></span>  
 <xref:System.Windows.Controls.DockPanel>  
 [<span data-ttu-id="510b7-115">Přehled panelu</span><span class="sxs-lookup"><span data-stu-id="510b7-115">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
