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
ms.openlocfilehash: 60e2af64cb0c5b313f4f1201cab70da6a88f61e7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365890"
---
# <a name="how-to-erase-ink-on-a-custom-control"></a><span data-ttu-id="2e2aa-102">Postupy: Smazání inkoustu na vlastním ovládacím prvku</span><span class="sxs-lookup"><span data-stu-id="2e2aa-102">How to: Erase Ink on a Custom Control</span></span>
<span data-ttu-id="2e2aa-103"><xref:System.Windows.Ink.IncrementalStrokeHitTester> Určuje, jestli aktuálně vykresleného stroke protíná jinou stroke.</span><span class="sxs-lookup"><span data-stu-id="2e2aa-103">The <xref:System.Windows.Ink.IncrementalStrokeHitTester> determines whether the currently drawn stroke intersects another stroke.</span></span>  <span data-ttu-id="2e2aa-104">To je užitečné pro vytvoření ovládacího prvku, který umožňuje uživateli vymazat části tah, tak, jak uživatel může na <xref:System.Windows.Controls.InkCanvas> při <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> je nastavena na <xref:System.Windows.Controls.InkCanvasEditingMode.EraseByPoint>.</span><span class="sxs-lookup"><span data-stu-id="2e2aa-104">This is useful for creating a control that enables a user to erase parts of a stroke, the way a user can on an <xref:System.Windows.Controls.InkCanvas> when the <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> is set to <xref:System.Windows.Controls.InkCanvasEditingMode.EraseByPoint>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e2aa-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="2e2aa-105">Example</span></span>  
 <span data-ttu-id="2e2aa-106">Následující příklad vytvoří vlastní ovládací prvek, který umožňuje uživateli vymazat části tahů.</span><span class="sxs-lookup"><span data-stu-id="2e2aa-106">The following example creates a custom control that enables the user to erase parts of strokes.</span></span>  <span data-ttu-id="2e2aa-107">Tento příklad vytvoří ovládací prvek, který obsahuje inkoustu po jeho inicializaci.</span><span class="sxs-lookup"><span data-stu-id="2e2aa-107">This example creates a control that contains ink when it is initialized.</span></span>  <span data-ttu-id="2e2aa-108">Vytvoření ovládacího prvku, který shromažďuje rukopisu, najdete v tématu [vytvoření ovládacího prvku vstupu inkoustu](creating-an-ink-input-control.md).</span><span class="sxs-lookup"><span data-stu-id="2e2aa-108">To create a control that collects ink, see [Creating an Ink Input Control](creating-an-ink-input-control.md).</span></span>  
  
 [!code-csharp[HowToEraseInk#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToEraseInk/CSharp/InkEraser.cs#1)]
 [!code-vb[HowToEraseInk#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToEraseInk/VisualBasic/InkEraser.vb#1)]
