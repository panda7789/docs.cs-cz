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
ms.openlocfilehash: 76449c88f9a720741c8ed61255e04a40e6a8613f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776202"
---
# <a name="how-to-draw-text-to-a-controls-background"></a><span data-ttu-id="2988b-102">Postupy: Vykreslení textu na pozadí ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="2988b-102">How to: Draw Text to a Control's Background</span></span>
<span data-ttu-id="2988b-103">Text můžete nakreslit přímo na pozadí ovládacího prvku převedením textový řetězec <xref:System.Windows.Media.FormattedText> objektu a nakreslením objektu na ovládací prvek <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="2988b-103">You can draw text directly to the background of a control by converting a text string to a <xref:System.Windows.Media.FormattedText> object, and then drawing the object to the control's <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="2988b-104">Tento postup můžete použít také pro kreslení na pozadí objekty odvozené z <xref:System.Windows.Controls.Panel>, jako například <xref:System.Windows.Controls.Canvas> a <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="2988b-104">You can also use this technique for drawing to the background of objects derived from <xref:System.Windows.Controls.Panel>, such as <xref:System.Windows.Controls.Canvas> and <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
 <span data-ttu-id="2988b-105">![Ovládací prvky zobrazení textu jako pozadí](./media/drawtext2background01.png "DrawText2Background01")</span><span class="sxs-lookup"><span data-stu-id="2988b-105">![Controls displaying text as background](./media/drawtext2background01.png "DrawText2Background01")</span></span>  
<span data-ttu-id="2988b-106">Příklad ovládacích prvků s vlastním textem pozadí</span><span class="sxs-lookup"><span data-stu-id="2988b-106">Example of controls with custom text backgrounds</span></span>  
  
## <a name="example"></a><span data-ttu-id="2988b-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="2988b-107">Example</span></span>  
 <span data-ttu-id="2988b-108">Chcete-li vykreslení na pozadí ovládacího prvku, vytvořte nový <xref:System.Windows.Media.DrawingBrush> objektu a nakreslit text převedený na objekt <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="2988b-108">To draw to the background of a control, create a new <xref:System.Windows.Media.DrawingBrush> object and draw the converted text to the object's <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="2988b-109">Pak přiřaďte nové <xref:System.Windows.Media.DrawingBrush> na pozadí ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2988b-109">Then, assign the new <xref:System.Windows.Media.DrawingBrush> to the control's background property.</span></span>  
  
 <span data-ttu-id="2988b-110">Následující příklad kódu ukazuje, jak vytvořit <xref:System.Windows.Media.FormattedText> objektu a vykreslení na pozadí <xref:System.Windows.Controls.Label> a <xref:System.Windows.Controls.Button> objektu.</span><span class="sxs-lookup"><span data-stu-id="2988b-110">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and draw to the background of a <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Button> object.</span></span>  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a><span data-ttu-id="2988b-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2988b-111">See also</span></span>

- <xref:System.Windows.Media.FormattedText>
- [<span data-ttu-id="2988b-112">Kreslení formátovaného textu</span><span class="sxs-lookup"><span data-stu-id="2988b-112">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
