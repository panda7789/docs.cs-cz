---
title: 'Postupy: Vykreslení textu na pozadí ovládacího prvku'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], drawing text to backgrounds
- text [WPF], drawing to control backgrounds
- drawing [WPF], text to control backgrounds
- backgrounds [WPF], drawing text to
- typography [WPF], drawing text to control backgrounds
ms.assetid: 686d8fba-f61c-4974-a871-c635d67a7f69
ms.openlocfilehash: 14300f763b67c6ac67ee408de2009c328d499c13
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424377"
---
# <a name="how-to-draw-text-to-a-controls-background"></a>Postupy: Vykreslení textu na pozadí ovládacího prvku
Text lze nakreslit přímo na pozadí ovládacího prvku tak, že převedete textový řetězec na objekt <xref:System.Windows.Media.FormattedText> a následně objekt nakreslíte do <xref:System.Windows.Media.DrawingContext>ovládacího prvku. Tento postup můžete použít také pro kreslení na pozadí objektů odvozených z <xref:System.Windows.Controls.Panel>, jako je například <xref:System.Windows.Controls.Canvas> a <xref:System.Windows.Controls.StackPanel>.  
  
 ![Snímek obrazovky s ovládacími prvky, které zobrazují text jako pozadí](./media/how-to-draw-text-to-a-control-background/draw-text-background.png "DrawText2Background01")  
Příklady ovládacích prvků s vlastním pozadím textu  
  
## <a name="example"></a>Příklad  
 Chcete-li nakreslit na pozadí ovládacího prvku, vytvořte nový objekt <xref:System.Windows.Media.DrawingBrush> a nakreslete převedený text do <xref:System.Windows.Media.DrawingContext>objektu. Pak přiřaďte nový <xref:System.Windows.Media.DrawingBrush> vlastnosti pozadí ovládacího prvku.  
  
 Následující příklad kódu ukazuje, jak vytvořit objekt <xref:System.Windows.Media.FormattedText> a nakreslit na pozadí objektu <xref:System.Windows.Controls.Label> a <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.FormattedText>
- [Kreslení formátovaného textu](drawing-formatted-text.md)
