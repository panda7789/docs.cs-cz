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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59160730"
---
# <a name="how-to-get-or-set-a-dock-value"></a><span data-ttu-id="1632d-102">Postupy: Získání nebo nastavení hodnoty ukotvení</span><span class="sxs-lookup"><span data-stu-id="1632d-102">How to: Get or Set a Dock Value</span></span>
<span data-ttu-id="1632d-103">Následující příklad ukazuje, jak přiřadit <xref:System.Windows.Controls.Dock> hodnotu objektu.</span><span class="sxs-lookup"><span data-stu-id="1632d-103">The following example shows how to assign a <xref:System.Windows.Controls.Dock> value for an object.</span></span> <span data-ttu-id="1632d-104">V příkladu se používá <xref:System.Windows.Controls.DockPanel.GetDock%2A> a <xref:System.Windows.Controls.DockPanel.SetDock%2A> metody <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="1632d-104">The example uses the <xref:System.Windows.Controls.DockPanel.GetDock%2A> and <xref:System.Windows.Controls.DockPanel.SetDock%2A> methods of <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1632d-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="1632d-105">Example</span></span>  
 <span data-ttu-id="1632d-106">Tento příklad vytvoří instanci <xref:System.Windows.Controls.TextBlock> elementu, `txt1`a přiřadí <xref:System.Windows.Controls.Dock> hodnotu `Top` pomocí <xref:System.Windows.Controls.DockPanel.SetDock%2A> metoda <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="1632d-106">The example creates an instance of the <xref:System.Windows.Controls.TextBlock> element, `txt1`, and assigns a <xref:System.Windows.Controls.Dock> value of `Top` by using the <xref:System.Windows.Controls.DockPanel.SetDock%2A> method of <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="1632d-107">Potom přidá hodnotu <xref:System.Windows.Controls.Dock> vlastnost <xref:System.Windows.Controls.TextBlock.Text%2A> z <xref:System.Windows.Controls.TextBlock> elementu s použitím <xref:System.Windows.Controls.DockPanel.GetDock%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="1632d-107">It then appends the value of the <xref:System.Windows.Controls.Dock> property to the <xref:System.Windows.Controls.TextBlock.Text%2A> of the <xref:System.Windows.Controls.TextBlock> element by using the <xref:System.Windows.Controls.DockPanel.GetDock%2A> method.</span></span> <span data-ttu-id="1632d-108">Nakonec příklad přidá <xref:System.Windows.Controls.TextBlock> do nadřazeného elementu <xref:System.Windows.Controls.DockPanel>, `dp1`.</span><span class="sxs-lookup"><span data-stu-id="1632d-108">Finally, the example adds the <xref:System.Windows.Controls.TextBlock> element to the parent <xref:System.Windows.Controls.DockPanel>, `dp1`.</span></span>  
  
 [!code-csharp[DockPanelSetDock#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelSetDock/CSharp/DockPanel_SetDock.cs#1)]
 [!code-vb[DockPanelSetDock#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelSetDock/VisualBasic/DockPanel_SetDock.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1632d-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1632d-109">See also</span></span>

- <xref:System.Windows.Controls.DockPanel>
- <xref:System.Windows.Controls.DockPanel.GetDock%2A>
- <xref:System.Windows.Controls.DockPanel.SetDock%2A>
- [<span data-ttu-id="1632d-110">Přehled panelu</span><span class="sxs-lookup"><span data-stu-id="1632d-110">Panels Overview</span></span>](panels-overview.md)
