---
title: 'Postupy: Smazání inkoustu na vlastním ovládacím prvku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [WPF], erasing ink on
- ink [WPF], erasing on custom control
ms.assetid: d88c50f9-b4d8-4962-a28b-67d6a15a5fe0
ms.openlocfilehash: 66c0d19b368b56821fd4034ec4c7cd397b244ab0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543244"
---
# <a name="how-to-erase-ink-on-a-custom-control"></a><span data-ttu-id="9fcb9-102">Postupy: Smazání inkoustu na vlastním ovládacím prvku</span><span class="sxs-lookup"><span data-stu-id="9fcb9-102">How to: Erase Ink on a Custom Control</span></span>
<span data-ttu-id="9fcb9-103"><xref:System.Windows.Ink.IncrementalStrokeHitTester> Určuje, jestli aktuálně vykresleného tahu protíná jinou tahu.</span><span class="sxs-lookup"><span data-stu-id="9fcb9-103">The <xref:System.Windows.Ink.IncrementalStrokeHitTester> determines whether the currently drawn stroke intersects another stroke.</span></span>  <span data-ttu-id="9fcb9-104">To je užitečné pro vytvoření ovládacího prvku, který umožňuje uživatelům vymazat části tahu, způsob uživatel může na <xref:System.Windows.Controls.InkCanvas> při <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> je nastaven na <xref:System.Windows.Controls.InkCanvasEditingMode.EraseByPoint>.</span><span class="sxs-lookup"><span data-stu-id="9fcb9-104">This is useful for creating a control that enables a user to erase parts of a stroke, the way a user can on an <xref:System.Windows.Controls.InkCanvas> when the <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> is set to <xref:System.Windows.Controls.InkCanvasEditingMode.EraseByPoint>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fcb9-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="9fcb9-105">Example</span></span>  
 <span data-ttu-id="9fcb9-106">Následující příklad vytvoří vlastní ovládací prvek, který umožňuje uživatelům vymazat části tahy.</span><span class="sxs-lookup"><span data-stu-id="9fcb9-106">The following example creates a custom control that enables the user to erase parts of strokes.</span></span>  <span data-ttu-id="9fcb9-107">Tento příklad vytvoří ovládacího prvku, který obsahuje element ink při inicializaci.</span><span class="sxs-lookup"><span data-stu-id="9fcb9-107">This example creates a control that contains ink when it is initialized.</span></span>  <span data-ttu-id="9fcb9-108">Vytvoření ovládacího prvku, který shromažďuje rukopisu, naleznete v části [vytvoření ovládacího prvku rukopisu vstup](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).</span><span class="sxs-lookup"><span data-stu-id="9fcb9-108">To create a control that collects ink, see [Creating an Ink Input Control](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).</span></span>  
  
 [!code-csharp[HowToEraseInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToEraseInk/CSharp/InkEraser.cs#1)]
 [!code-vb[HowToEraseInk#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToEraseInk/VisualBasic/InkEraser.vb#1)]
