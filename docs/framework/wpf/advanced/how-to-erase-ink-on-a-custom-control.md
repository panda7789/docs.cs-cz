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
---
# <a name="how-to-erase-ink-on-a-custom-control"></a>Postupy: Smazání inkoustu na vlastním ovládacím prvku
<xref:System.Windows.Ink.IncrementalStrokeHitTester> Určuje, jestli aktuálně vykresleného tahu protíná jinou tahu.  To je užitečné pro vytvoření ovládacího prvku, který umožňuje uživatelům vymazat části tahu, způsob uživatel může na <xref:System.Windows.Controls.InkCanvas> při <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> je nastaven na <xref:System.Windows.Controls.InkCanvasEditingMode.EraseByPoint>.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří vlastní ovládací prvek, který umožňuje uživatelům vymazat části tahy.  Tento příklad vytvoří ovládacího prvku, který obsahuje element ink při inicializaci.  Vytvoření ovládacího prvku, který shromažďuje rukopisu, naleznete v části [vytvoření ovládacího prvku rukopisu vstup](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).  
  
 [!code-csharp[HowToEraseInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToEraseInk/CSharp/InkEraser.cs#1)]
 [!code-vb[HowToEraseInk#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToEraseInk/VisualBasic/InkEraser.vb#1)]
