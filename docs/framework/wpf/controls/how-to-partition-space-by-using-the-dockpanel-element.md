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
# <a name="how-to-partition-space-by-using-the-dockpanel-element"></a><span data-ttu-id="b3d48-102">Postupy: Rozdělení prostoru pomocí elementu DockPanel</span><span class="sxs-lookup"><span data-stu-id="b3d48-102">How to: Partition Space by Using the DockPanel Element</span></span>
<span data-ttu-id="b3d48-103">Následující příklad vytvoří jednoduchý [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] pomocí rozhraní framework <xref:System.Windows.Controls.DockPanel> elementu.</span><span class="sxs-lookup"><span data-stu-id="b3d48-103">The following example creates a simple [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] framework using a <xref:System.Windows.Controls.DockPanel> element.</span></span> <span data-ttu-id="b3d48-104"><xref:System.Windows.Controls.DockPanel> Oddíly dostupné místo na jeho podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="b3d48-104">The <xref:System.Windows.Controls.DockPanel> partitions available space to its child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3d48-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="b3d48-105">Example</span></span>  
 <span data-ttu-id="b3d48-106">V tomto příkladu <xref:System.Windows.Controls.DockPanel.Dock%2A> vlastnost, která je připojená vlastnost, dva identické ukotvení <xref:System.Windows.Controls.Border> prvky v <xref:System.Windows.Controls.Dock.Top> dělené místa.</span><span class="sxs-lookup"><span data-stu-id="b3d48-106">This example uses the <xref:System.Windows.Controls.DockPanel.Dock%2A> property, which is an attached property, to dock two identical <xref:System.Windows.Controls.Border> elements at the <xref:System.Windows.Controls.Dock.Top> of the partitioned space.</span></span> <span data-ttu-id="b3d48-107">Třetí <xref:System.Windows.Controls.Border> prvek ukotven <xref:System.Windows.Controls.Dock.Left>, s jeho šířku nastaveno na 200 pixelů.</span><span class="sxs-lookup"><span data-stu-id="b3d48-107">A third <xref:System.Windows.Controls.Border> element is docked to the <xref:System.Windows.Controls.Dock.Left>, with its width set to 200 pixels.</span></span> <span data-ttu-id="b3d48-108">Čtvrtý <xref:System.Windows.Controls.Border> ukotven <xref:System.Windows.Controls.Dock.Bottom> obrazovky.</span><span class="sxs-lookup"><span data-stu-id="b3d48-108">A fourth <xref:System.Windows.Controls.Border> is docked to the <xref:System.Windows.Controls.Dock.Bottom> of the screen.</span></span> <span data-ttu-id="b3d48-109">Poslední <xref:System.Windows.Controls.Border> element automaticky vyplní zbývající místo.</span><span class="sxs-lookup"><span data-stu-id="b3d48-109">The last <xref:System.Windows.Controls.Border> element automatically fills the remaining space.</span></span>  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
>  <span data-ttu-id="b3d48-110">Ve výchozím nastavení posledního podřízeného člena <xref:System.Windows.Controls.DockPanel> prvek vyplní zbývající volné místo.</span><span class="sxs-lookup"><span data-stu-id="b3d48-110">By default, the last child of a <xref:System.Windows.Controls.DockPanel> element fills the remaining unallocated space.</span></span> <span data-ttu-id="b3d48-111">Pokud nechcete, aby toto chování, nastavte `LastChildFill="False"`.</span><span class="sxs-lookup"><span data-stu-id="b3d48-111">If you do not want this behavior, set `LastChildFill="False"`.</span></span>  
  
 <span data-ttu-id="b3d48-112">Kompilované aplikace poskytuje nové uživatelské rozhraní, který vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="b3d48-112">The compiled application yields a new UI that looks like this.</span></span>  
  
 <span data-ttu-id="b3d48-113">![Typický scénář DockPanel. ](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")</span><span class="sxs-lookup"><span data-stu-id="b3d48-113">![A typical DockPanel scenario.](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3d48-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3d48-114">See also</span></span>

- <xref:System.Windows.Controls.DockPanel>
- [<span data-ttu-id="b3d48-115">Přehled panelů</span><span class="sxs-lookup"><span data-stu-id="b3d48-115">Panels Overview</span></span>](panels-overview.md)
