---
title: 'Postupy: Kreslení čáry vyplněné texturou'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- lines [Windows Forms], texture
- drawing lines [Windows Forms], texture
ms.assetid: dc9118cc-f3c2-42e5-8173-f46d41d18fd5
ms.openlocfilehash: 1895c752340d8d764205b5a32b9af0861303841a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522185"
---
# <a name="how-to-draw-a-line-filled-with-a-texture"></a><span data-ttu-id="a7aa5-102">Postupy: Kreslení čáry vyplněné texturou</span><span class="sxs-lookup"><span data-stu-id="a7aa5-102">How to: Draw a Line Filled with a Texture</span></span>
<span data-ttu-id="a7aa5-103">Místo kreslení čáry s plnou barvou, můžete kreslení čáry texturou.</span><span class="sxs-lookup"><span data-stu-id="a7aa5-103">Instead of drawing a line with a solid color, you can draw a line with a texture.</span></span> <span data-ttu-id="a7aa5-104">Kreslení čar a křivek texturou, vytvoření <xref:System.Drawing.TextureBrush> objektu a který předat <xref:System.Drawing.TextureBrush> do objektu <xref:System.Drawing.Pen.%23ctor%2A> konstruktor.</span><span class="sxs-lookup"><span data-stu-id="a7aa5-104">To draw lines and curves with a texture, create a <xref:System.Drawing.TextureBrush> object, and pass that <xref:System.Drawing.TextureBrush> object to a <xref:System.Drawing.Pen.%23ctor%2A> constructor.</span></span> <span data-ttu-id="a7aa5-105">Rastrový obrázek přidružené štětce texture slouží k dlaždici rovině (tedy bez zásahu uživatele), a když pera nevykresluje řádek nebo křivky, tahu pera umožňuje odhalit určité pixelů vedle sebe texture.</span><span class="sxs-lookup"><span data-stu-id="a7aa5-105">The bitmap associated with the texture brush is used to tile the plane (invisibly), and when the pen draws a line or curve, the stroke of the pen uncovers certain pixels of the tiled texture.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7aa5-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="a7aa5-106">Example</span></span>  
 <span data-ttu-id="a7aa5-107">Následující příklad vytvoří <xref:System.Drawing.Bitmap> objektu ze souboru `Texture1.jpg`.</span><span class="sxs-lookup"><span data-stu-id="a7aa5-107">The following example creates a <xref:System.Drawing.Bitmap> object from the file `Texture1.jpg`.</span></span> <span data-ttu-id="a7aa5-108">Tento rastrový obrázek se používá pro konstrukci <xref:System.Drawing.TextureBrush> objekt a <xref:System.Drawing.TextureBrush> objekt se používá pro konstrukci <xref:System.Drawing.Pen> objektu.</span><span class="sxs-lookup"><span data-stu-id="a7aa5-108">That bitmap is used to construct a <xref:System.Drawing.TextureBrush> object, and the <xref:System.Drawing.TextureBrush> object is used to construct a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="a7aa5-109">Volání <xref:System.Drawing.Graphics.DrawImage%2A> nevykresluje bitmap s jeho levého horního rohu v (0, 0).</span><span class="sxs-lookup"><span data-stu-id="a7aa5-109">The call to <xref:System.Drawing.Graphics.DrawImage%2A> draws the bitmap with its upper-left corner at (0, 0).</span></span> <span data-ttu-id="a7aa5-110">Volání <xref:System.Drawing.Graphics.DrawEllipse%2A> používá <xref:System.Drawing.Pen> objektu k vykreslení texturou třemi tečkami.</span><span class="sxs-lookup"><span data-stu-id="a7aa5-110">The call to <xref:System.Drawing.Graphics.DrawEllipse%2A> uses the <xref:System.Drawing.Pen> object to draw a textured ellipse.</span></span>  
  
 <span data-ttu-id="a7aa5-111">Následující obrázek znázorňuje bitovou mapu a texturou třemi tečkami.</span><span class="sxs-lookup"><span data-stu-id="a7aa5-111">The following illustration shows the bitmap and the textured ellipse.</span></span>  
  
 <span data-ttu-id="a7aa5-112">![Pera](../../../../docs/framework/winforms/advanced/media/pens7.png "pens7")</span><span class="sxs-lookup"><span data-stu-id="a7aa5-112">![Pens](../../../../docs/framework/winforms/advanced/media/pens7.png "pens7")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.UsingAPen#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a7aa5-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="a7aa5-113">Compiling the Code</span></span>  
 <span data-ttu-id="a7aa5-114">Vytvoření formuláře Windows a zpracování formuláře <xref:System.Windows.Forms.Control.Paint> událostí.</span><span class="sxs-lookup"><span data-stu-id="a7aa5-114">Create a Windows Form and handle the form's <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="a7aa5-115">Předchozí kód vložte do <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="a7aa5-115">Paste the preceding code into the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="a7aa5-116">Nahraďte `Texture.jpg` s bitovou kopií platné ve vašem systému.</span><span class="sxs-lookup"><span data-stu-id="a7aa5-116">Replace `Texture.jpg` with an image valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7aa5-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="a7aa5-117">See Also</span></span>  
 [<span data-ttu-id="a7aa5-118">Kreslení čar a obrazců pomocí pera</span><span class="sxs-lookup"><span data-stu-id="a7aa5-118">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [<span data-ttu-id="a7aa5-119">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a7aa5-119">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
