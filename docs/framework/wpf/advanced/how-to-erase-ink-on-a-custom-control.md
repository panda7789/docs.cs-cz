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
# <a name="how-to-erase-ink-on-a-custom-control"></a>Postupy: Smazání inkoustu na vlastním ovládacím prvku
<xref:System.Windows.Ink.IncrementalStrokeHitTester> Určuje, jestli aktuálně vykresleného stroke protíná jinou stroke.  To je užitečné pro vytvoření ovládacího prvku, který umožňuje uživateli vymazat části tah, tak, jak uživatel může na <xref:System.Windows.Controls.InkCanvas> při <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> je nastavena na <xref:System.Windows.Controls.InkCanvasEditingMode.EraseByPoint>.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří vlastní ovládací prvek, který umožňuje uživateli vymazat části tahů.  Tento příklad vytvoří ovládací prvek, který obsahuje inkoustu po jeho inicializaci.  Vytvoření ovládacího prvku, který shromažďuje rukopisu, najdete v tématu [vytvoření ovládacího prvku vstupu inkoustu](creating-an-ink-input-control.md).  
  
 [!code-csharp[HowToEraseInk#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToEraseInk/CSharp/InkEraser.cs#1)]
 [!code-vb[HowToEraseInk#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToEraseInk/VisualBasic/InkEraser.vb#1)]
