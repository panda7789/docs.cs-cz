---
title: 'Postupy: Řízení funkce alfa blending pomocí režimu skládání'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- alpha blending [Windows Forms], compositing
- colors [Windows Forms], blending
- colors [Windows Forms], controlling transparency
ms.assetid: f331df2d-b395-4b0a-95be-24fec8c9bbb5
ms.openlocfilehash: 15cb111a68cedaec011e88fa4916c292786d16b4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59210688"
---
# <a name="how-to-use-compositing-mode-to-control-alpha-blending"></a><span data-ttu-id="bb0e8-102">Postupy: Řízení funkce alfa blending pomocí režimu skládání</span><span class="sxs-lookup"><span data-stu-id="bb0e8-102">How to: Use Compositing Mode to Control Alpha Blending</span></span>
<span data-ttu-id="bb0e8-103">Může nastat situace, kdy budete chtít vytvořit mimo obrazovku rastrový obrázek, který má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="bb0e8-103">There may be times when you want to create an off-screen bitmap that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="bb0e8-104">Barvy mají hodnoty alfa, které jsou kratší než 255.</span><span class="sxs-lookup"><span data-stu-id="bb0e8-104">Colors have alpha values that are less than 255.</span></span>  
  
-   <span data-ttu-id="bb0e8-105">Barvy nejsou alfa prolnuty mezi sebou při vytváření rastrového obrázku.</span><span class="sxs-lookup"><span data-stu-id="bb0e8-105">Colors are not alpha blended with each other as you create the bitmap.</span></span>  
  
-   <span data-ttu-id="bb0e8-106">Když zobrazíte dokončená rastrového obrázku jsou barvy rastrového obrázku nastaven barvy pozadí na zobrazovací zařízení smíšení alfa.</span><span class="sxs-lookup"><span data-stu-id="bb0e8-106">When you display the finished bitmap, colors in the bitmap are alpha blended with the background colors on the display device.</span></span>  
  
 <span data-ttu-id="bb0e8-107">Chcete-li vytvořit takové rastrový obrázek, vytvořit prázdnou hodnotu <xref:System.Drawing.Bitmap> objektu a pak vytvořit <xref:System.Drawing.Graphics> objektu podle tento rastrový obrázek.</span><span class="sxs-lookup"><span data-stu-id="bb0e8-107">To create such a bitmap, construct a blank <xref:System.Drawing.Bitmap> object, and then construct a <xref:System.Drawing.Graphics> object based on that bitmap.</span></span> <span data-ttu-id="bb0e8-108">Nastavení režimu skládání <xref:System.Drawing.Graphics> objektu <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bb0e8-108">Set the compositing mode of the <xref:System.Drawing.Graphics> object to <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb0e8-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="bb0e8-109">Example</span></span>  
 <span data-ttu-id="bb0e8-110">Následující příklad vytvoří <xref:System.Drawing.Graphics> objektu na základě <xref:System.Drawing.Bitmap> objektu.</span><span class="sxs-lookup"><span data-stu-id="bb0e8-110">The following example creates a <xref:System.Drawing.Graphics> object based on a <xref:System.Drawing.Bitmap> object.</span></span> <span data-ttu-id="bb0e8-111">Tento kód použije <xref:System.Drawing.Graphics> objekt spolu se dvěma poloprůhledných štětců (alfa = 160) k vykreslení na rastrový obrázek.</span><span class="sxs-lookup"><span data-stu-id="bb0e8-111">The code uses the <xref:System.Drawing.Graphics> object along with two semitransparent brushes (alpha = 160) to paint on the bitmap.</span></span> <span data-ttu-id="bb0e8-112">Kód vyplní red tři tečky a zelená elipsa pomocí poloprůhledných štětců.</span><span class="sxs-lookup"><span data-stu-id="bb0e8-112">The code fills a red ellipse and a green ellipse using the semitransparent brushes.</span></span> <span data-ttu-id="bb0e8-113">Zelené elipsy překrývá red elipsy, ale zelené není v kombinaci s červeným protože skládání režim <xref:System.Drawing.Graphics> je nastaven na <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy>.</span><span class="sxs-lookup"><span data-stu-id="bb0e8-113">The green ellipse overlaps the red ellipse, but the green is not blended with the red because the compositing mode of the <xref:System.Drawing.Graphics> object is set to <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy>.</span></span>  
  
 <span data-ttu-id="bb0e8-114">Kód vykreslí rastrového obrázku na obrazovce dvakrát: jednou na bílém pozadí a jakmile na barevné pozadí.</span><span class="sxs-lookup"><span data-stu-id="bb0e8-114">The code draws the bitmap on the screen twice: once on a white background and once on a multicolored background.</span></span> <span data-ttu-id="bb0e8-115">Pixely rastrového obrázku nastaven, které jsou součástí dvou symbol tří teček mít alfa složkou 160, proto se tři tečky v kombinaci s barvy pozadí na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="bb0e8-115">The pixels in the bitmap that are part of the two ellipses have an alpha component of 160, so the ellipses are blended with the background colors on the screen.</span></span>  
  
 <span data-ttu-id="bb0e8-116">Následující obrázek znázorňuje výstup v příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="bb0e8-116">The following illustration shows the output of the code example.</span></span> <span data-ttu-id="bb0e8-117">Všimněte si, že jsou na symbol tří teček v kombinaci s na pozadí, ale nejsou prolnuty mezi sebou.</span><span class="sxs-lookup"><span data-stu-id="bb0e8-117">Note that the ellipses are blended with the background, but they are not blended with each other.</span></span>  
  
 ![Diagram znázorňující tři tečky v kombinaci s na pozadí, ne mezi sebou.](./media/how-to-use-compositing-mode-to-control-alpha-blending/ellipses-blended-background.png)  
  
 <span data-ttu-id="bb0e8-119">Příklad kódu obsahuje tento příkaz:</span><span class="sxs-lookup"><span data-stu-id="bb0e8-119">The code example contains this statement:</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.AlphaBlending#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#41)]  
  
 <span data-ttu-id="bb0e8-120">Pokud chcete na symbol tří teček, chcete-li být smíšené mezi sebou můžou mít na pozadí, změňte, který tento příkaz takto:</span><span class="sxs-lookup"><span data-stu-id="bb0e8-120">If you want the ellipses to be blended with each other as well as with the background, change that statement to the following:</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.AlphaBlending#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#42)]  
  
 <span data-ttu-id="bb0e8-121">Následující obrázek znázorňuje výstup revidovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="bb0e8-121">The following illustration shows the output of the revised code.</span></span>  
  
 ![Diagram znázorňující tři tečky v kombinaci společně a s na pozadí.](./media/how-to-use-compositing-mode-to-control-alpha-blending/blend-ellipses-background.png)  
  
 [!code-csharp[System.Drawing.AlphaBlending#43](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#43)]
 [!code-vb[System.Drawing.AlphaBlending#43](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#43)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bb0e8-123">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="bb0e8-123">Compiling the Code</span></span>  
 <span data-ttu-id="bb0e8-124">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="bb0e8-124">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb0e8-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bb0e8-125">See also</span></span>

- <xref:System.Drawing.Color.FromArgb%2A>
- [<span data-ttu-id="bb0e8-126">Alfa míchání čar a výplní</span><span class="sxs-lookup"><span data-stu-id="bb0e8-126">Alpha Blending Lines and Fills</span></span>](alpha-blending-lines-and-fills.md)
