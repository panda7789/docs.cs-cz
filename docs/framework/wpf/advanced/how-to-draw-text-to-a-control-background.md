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
# <a name="how-to-draw-text-to-a-controls-background"></a><span data-ttu-id="1c88e-102">Postupy: Vykreslení textu na pozadí ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="1c88e-102">How to: Draw Text to a Control's Background</span></span>
<span data-ttu-id="1c88e-103">Text lze nakreslit přímo na pozadí ovládacího prvku tak, že převedete textový řetězec na objekt <xref:System.Windows.Media.FormattedText> a následně objekt nakreslíte do <xref:System.Windows.Media.DrawingContext>ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1c88e-103">You can draw text directly to the background of a control by converting a text string to a <xref:System.Windows.Media.FormattedText> object, and then drawing the object to the control's <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="1c88e-104">Tento postup můžete použít také pro kreslení na pozadí objektů odvozených z <xref:System.Windows.Controls.Panel>, jako je například <xref:System.Windows.Controls.Canvas> a <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="1c88e-104">You can also use this technique for drawing to the background of objects derived from <xref:System.Windows.Controls.Panel>, such as <xref:System.Windows.Controls.Canvas> and <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
 <span data-ttu-id="1c88e-105">![Snímek obrazovky s ovládacími prvky, které zobrazují text jako pozadí](./media/how-to-draw-text-to-a-control-background/draw-text-background.png "DrawText2Background01")</span><span class="sxs-lookup"><span data-stu-id="1c88e-105">![Screenshot of controls displaying text as background.](./media/how-to-draw-text-to-a-control-background/draw-text-background.png "DrawText2Background01")</span></span>  
<span data-ttu-id="1c88e-106">Příklady ovládacích prvků s vlastním pozadím textu</span><span class="sxs-lookup"><span data-stu-id="1c88e-106">Example of controls with custom text backgrounds</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c88e-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="1c88e-107">Example</span></span>  
 <span data-ttu-id="1c88e-108">Chcete-li nakreslit na pozadí ovládacího prvku, vytvořte nový objekt <xref:System.Windows.Media.DrawingBrush> a nakreslete převedený text do <xref:System.Windows.Media.DrawingContext>objektu.</span><span class="sxs-lookup"><span data-stu-id="1c88e-108">To draw to the background of a control, create a new <xref:System.Windows.Media.DrawingBrush> object and draw the converted text to the object's <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="1c88e-109">Pak přiřaďte nový <xref:System.Windows.Media.DrawingBrush> vlastnosti pozadí ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1c88e-109">Then, assign the new <xref:System.Windows.Media.DrawingBrush> to the control's background property.</span></span>  
  
 <span data-ttu-id="1c88e-110">Následující příklad kódu ukazuje, jak vytvořit objekt <xref:System.Windows.Media.FormattedText> a nakreslit na pozadí objektu <xref:System.Windows.Controls.Label> a <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="1c88e-110">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and draw to the background of a <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Button> object.</span></span>  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a><span data-ttu-id="1c88e-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1c88e-111">See also</span></span>

- <xref:System.Windows.Media.FormattedText>
- [<span data-ttu-id="1c88e-112">Kreslení formátovaného textu</span><span class="sxs-lookup"><span data-stu-id="1c88e-112">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
