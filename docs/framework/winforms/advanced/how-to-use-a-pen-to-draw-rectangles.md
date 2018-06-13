---
title: 'Postupy: Kreslení obdélníků pomocí pera'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- rectangles [Windows Forms], drawing
- pens [Windows Forms], drawing rectangles
ms.assetid: 54a7fa14-3ad8-4d64-b424-2a12005b250c
ms.openlocfilehash: ad5b436f7162c282198c7a9d3cce4d3ce3fd3c6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524004"
---
# <a name="how-to-use-a-pen-to-draw-rectangles"></a><span data-ttu-id="e67de-102">Postupy: Kreslení obdélníků pomocí pera</span><span class="sxs-lookup"><span data-stu-id="e67de-102">How to: Use a Pen to Draw Rectangles</span></span>
<span data-ttu-id="e67de-103">Kreslení obdélníků, musíte <xref:System.Drawing.Graphics> objektu a <xref:System.Drawing.Pen> objektu.</span><span class="sxs-lookup"><span data-stu-id="e67de-103">To draw rectangles, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="e67de-104"><xref:System.Drawing.Graphics> Objekt poskytuje <xref:System.Drawing.Graphics.DrawRectangle%2A> metody a <xref:System.Drawing.Pen> objekt ukládá funkce na řádku, jako je například barva a šířka.</span><span class="sxs-lookup"><span data-stu-id="e67de-104">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawRectangle%2A> method, and the <xref:System.Drawing.Pen> object stores features of the line, such as color and width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e67de-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="e67de-105">Example</span></span>  
 <span data-ttu-id="e67de-106">Následující příklad nevykresluje obdélníku s jeho levého horního rohu v (10, 10).</span><span class="sxs-lookup"><span data-stu-id="e67de-106">The following example draws a rectangle with its upper-left corner at (10, 10).</span></span> <span data-ttu-id="e67de-107">Rámeček má šířky 100 a výška 50.</span><span class="sxs-lookup"><span data-stu-id="e67de-107">The rectangle has a width of 100 and a height of 50.</span></span> <span data-ttu-id="e67de-108">Druhý argument předaný <xref:System.Drawing.Pen.%23ctor%2A> konstruktor značí, že šířku pera 5 pixelů.</span><span class="sxs-lookup"><span data-stu-id="e67de-108">The second argument passed to the <xref:System.Drawing.Pen.%23ctor%2A> constructor indicates that the pen width is 5 pixels.</span></span>  
  
 <span data-ttu-id="e67de-109">Při sestavování rámeček pera se jedná o obdélníku hranic.</span><span class="sxs-lookup"><span data-stu-id="e67de-109">When the rectangle is drawn, the pen is centered on the rectangle's boundary.</span></span> <span data-ttu-id="e67de-110">Vzhledem k šířce pera je 5, jsou stran obdélníku vykresleného 5 pixelů široké, například tento 1 pixel vykreslením na samotná hranice jsou vykreslovány 2 pixelů uvnitř a 2 pixelů jsou vykreslovány na povrchu.</span><span class="sxs-lookup"><span data-stu-id="e67de-110">Because the pen width is 5, the sides of the rectangle are drawn 5 pixels wide, such that 1 pixel is drawn on the boundary itself, 2 pixels are drawn on the inside, and 2 pixels are drawn on the outside.</span></span> <span data-ttu-id="e67de-111">Další informace o pera zarovnání v [postupy: nastavení šířky a pera a zarovnání](../../../../docs/framework/winforms/advanced/how-to-set-pen-width-and-alignment.md).</span><span class="sxs-lookup"><span data-stu-id="e67de-111">For more details on pen alignment, see [How to: Set Pen Width and Alignment](../../../../docs/framework/winforms/advanced/how-to-set-pen-width-and-alignment.md).</span></span>  
  
 <span data-ttu-id="e67de-112">Následující obrázek znázorňuje výsledné rámeček.</span><span class="sxs-lookup"><span data-stu-id="e67de-112">The following illustration shows the resulting rectangle.</span></span> <span data-ttu-id="e67de-113">Zobrazit čáry s koncovými body, kde rámeček by byly pokud šířku pera je jeden pixel.</span><span class="sxs-lookup"><span data-stu-id="e67de-113">The dotted lines show where the rectangle would have been drawn if the pen width had been one pixel.</span></span> <span data-ttu-id="e67de-114">Práce se zvětšeným zobrazením levého horního rohu obdélníku ukazuje, že se na tyto řádky tečkovaná na silné černé čáry.</span><span class="sxs-lookup"><span data-stu-id="e67de-114">The enlarged view of the upper-left corner of the rectangle shows that the thick black lines are centered on those dotted lines.</span></span>  
  
 <span data-ttu-id="e67de-115">![Pera](../../../../docs/framework/winforms/advanced/media/pens1.gif "pens1")</span><span class="sxs-lookup"><span data-stu-id="e67de-115">![Pens](../../../../docs/framework/winforms/advanced/media/pens1.gif "pens1")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingAPen#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e67de-116">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e67de-116">Compiling the Code</span></span>  
 <span data-ttu-id="e67de-117">V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="e67de-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e67de-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="e67de-118">See Also</span></span>  
 [<span data-ttu-id="e67de-119">Kreslení čar a obrazců pomocí pera</span><span class="sxs-lookup"><span data-stu-id="e67de-119">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
