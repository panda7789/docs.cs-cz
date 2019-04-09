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
ms.openlocfilehash: 0e51a1e3a2d14754147dbd36f170127a7e978acd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074609"
---
# <a name="how-to-use-a-pen-to-draw-rectangles"></a><span data-ttu-id="9f6d8-102">Postupy: Kreslení obdélníků pomocí pera</span><span class="sxs-lookup"><span data-stu-id="9f6d8-102">How to: Use a Pen to Draw Rectangles</span></span>
<span data-ttu-id="9f6d8-103">Kreslení obdélníků, je nutné <xref:System.Drawing.Graphics> objektu a <xref:System.Drawing.Pen> objektu.</span><span class="sxs-lookup"><span data-stu-id="9f6d8-103">To draw rectangles, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="9f6d8-104"><xref:System.Drawing.Graphics> Objekt, který poskytuje <xref:System.Drawing.Graphics.DrawRectangle%2A> metody a <xref:System.Drawing.Pen> ukládá funkce na řádku, jako je barva a šířka.</span><span class="sxs-lookup"><span data-stu-id="9f6d8-104">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawRectangle%2A> method, and the <xref:System.Drawing.Pen> object stores features of the line, such as color and width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f6d8-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f6d8-105">Example</span></span>  
 <span data-ttu-id="9f6d8-106">Kreslení obdélníku s jeho levého horního rohu v následujícím příkladu (10, 10).</span><span class="sxs-lookup"><span data-stu-id="9f6d8-106">The following example draws a rectangle with its upper-left corner at (10, 10).</span></span> <span data-ttu-id="9f6d8-107">Obdélník má 100 šířku a výšku 50.</span><span class="sxs-lookup"><span data-stu-id="9f6d8-107">The rectangle has a width of 100 and a height of 50.</span></span> <span data-ttu-id="9f6d8-108">Druhý argument předaný do <xref:System.Drawing.Pen.%23ctor%2A> konstruktor znamená, že šířka pera je 5 pixelů.</span><span class="sxs-lookup"><span data-stu-id="9f6d8-108">The second argument passed to the <xref:System.Drawing.Pen.%23ctor%2A> constructor indicates that the pen width is 5 pixels.</span></span>  
  
 <span data-ttu-id="9f6d8-109">Při vykreslení obdélníku pera je zarovnaný na střed v obdélníku hranice.</span><span class="sxs-lookup"><span data-stu-id="9f6d8-109">When the rectangle is drawn, the pen is centered on the rectangle's boundary.</span></span> <span data-ttu-id="9f6d8-110">Vzhledem k tomu, že šířka pera je 5, strany pravoúhelníku se vykreslený 5 pixelů široký, například je vykreslen této 1 pixelu na dané hranice lze na samotný jsou vykreslovány 2 pixelů uvnitř, a jsou vykreslovány 2 pixelů na povrchu.</span><span class="sxs-lookup"><span data-stu-id="9f6d8-110">Because the pen width is 5, the sides of the rectangle are drawn 5 pixels wide, such that 1 pixel is drawn on the boundary itself, 2 pixels are drawn on the inside, and 2 pixels are drawn on the outside.</span></span> <span data-ttu-id="9f6d8-111">Podrobné informace o psaní perem zarovnání naleznete v tématu [jak: Nastavení šířky a pera a zarovnání](how-to-set-pen-width-and-alignment.md).</span><span class="sxs-lookup"><span data-stu-id="9f6d8-111">For more details on pen alignment, see [How to: Set Pen Width and Alignment](how-to-set-pen-width-and-alignment.md).</span></span>  
  
 <span data-ttu-id="9f6d8-112">Výsledný obdélníku na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="9f6d8-112">The following illustration shows the resulting rectangle.</span></span> <span data-ttu-id="9f6d8-113">Zobrazit tečkované čáry, kde obdélník by byl nakreslen diagram Pokud šířku pera je jeden pixel.</span><span class="sxs-lookup"><span data-stu-id="9f6d8-113">The dotted lines show where the rectangle would have been drawn if the pen width had been one pixel.</span></span> <span data-ttu-id="9f6d8-114">Zvětšeným zobrazením levého horního rohu obdélníku ukazuje, že se na tyto tečkované čáry na silný černý řádky.</span><span class="sxs-lookup"><span data-stu-id="9f6d8-114">The enlarged view of the upper-left corner of the rectangle shows that the thick black lines are centered on those dotted lines.</span></span>  
  
 ![Snímek obrazovky zobrazující vykresleného obdélníku s černý a tečkované čáry.](./media/how-to-use-a-pen-to-draw-rectangles/drawn-rectangle-black-lines-dotted-lines.gif)  
  
 [!code-csharp[System.Drawing.UsingAPen#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingAPen#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9f6d8-116">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="9f6d8-116">Compiling the Code</span></span>  
 <span data-ttu-id="9f6d8-117">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs>`e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="9f6d8-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f6d8-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f6d8-118">See also</span></span>

- [<span data-ttu-id="9f6d8-119">Kreslení čar a obrazců pomocí pera</span><span class="sxs-lookup"><span data-stu-id="9f6d8-119">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
