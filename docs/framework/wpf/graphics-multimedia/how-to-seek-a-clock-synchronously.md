---
title: 'Postupy: Synchronní vyhledání hodin'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clocks [WPF], seeking synchronously
- seeking clocks synchronously [WPF]
ms.assetid: e5b7529b-b7d0-40d2-9e1d-fa4b5e736e96
ms.openlocfilehash: d8e7b0f4bfa3a59814d87bfb6d7e8b40bd80f6e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559851"
---
# <a name="how-to-seek-a-clock-synchronously"></a><span data-ttu-id="8181f-102">Postupy: Synchronní vyhledání hodin</span><span class="sxs-lookup"><span data-stu-id="8181f-102">How to: Seek a Clock Synchronously</span></span>
<span data-ttu-id="8181f-103">Použití <xref:System.Windows.Media.Animation.ClockController.SeekAlignedToLastTick%2A> metoda k vyhledání hodiny k určitému bodu synchronně.</span><span class="sxs-lookup"><span data-stu-id="8181f-103">Use the <xref:System.Windows.Media.Animation.ClockController.SeekAlignedToLastTick%2A> method to seek a clock to a specific point synchronously.</span></span> <span data-ttu-id="8181f-104">Následující příklad ukazuje, jak <xref:System.Windows.Media.Animation.ClockController.Seek%2A> a <xref:System.Windows.Media.Animation.ClockController.SeekAlignedToLastTick%2A> metody <xref:System.Windows.Media.Animation.ClockController>.</span><span class="sxs-lookup"><span data-stu-id="8181f-104">The following example demonstrates both the <xref:System.Windows.Media.Animation.ClockController.Seek%2A> and <xref:System.Windows.Media.Animation.ClockController.SeekAlignedToLastTick%2A> methods of a <xref:System.Windows.Media.Animation.ClockController>.</span></span>  
  
 <span data-ttu-id="8181f-105">Tento příklad ukazuje, jak hledat <xref:System.Windows.Media.Animation.Clock>; příklad znázorňující způsob vyhledání scénáře, najdete v článku [hledat synchronně Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-seek-a-storyboard-synchronously.md) .</span><span class="sxs-lookup"><span data-stu-id="8181f-105">This example shows how to seek a <xref:System.Windows.Media.Animation.Clock>; for an example showing how to seek a storyboard, see [Seek a Storyboard Synchronously](../../../../docs/framework/wpf/graphics-multimedia/how-to-seek-a-storyboard-synchronously.md) .</span></span>  
  
## <a name="example"></a><span data-ttu-id="8181f-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="8181f-106">Example</span></span>  
 [!code-csharp[ClockController_procedural_snip#ClockControllerSeekExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClockController_procedural_snip/CSharp/SeekAlignedToLastTickExample.cs#clockcontrollerseekexample)]
 [!code-vb[ClockController_procedural_snip#ClockControllerSeekExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClockController_procedural_snip/visualbasic/seekalignedtolasttickexample.vb#clockcontrollerseekexample)]
