---
title: 'Postupy: Kreslení neprůhledných a poloprůhledných čar'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- transparency [Windows Forms], lines
- lines [Windows Forms], drawing alpha blended
- alpha blending [Windows Forms], drawing lines
ms.assetid: 8f2508af-f495-4223-b5cc-646cbbb520eb
ms.openlocfilehash: 210916bbaf437d8f71b07e8107eb0cdc0989ea42
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2019
ms.locfileid: "58465617"
---
# <a name="how-to-draw-opaque-and-semitransparent-lines"></a><span data-ttu-id="7650c-102">Postupy: Kreslení neprůhledných a poloprůhledných čar</span><span class="sxs-lookup"><span data-stu-id="7650c-102">How to: Draw Opaque and Semitransparent Lines</span></span>
<span data-ttu-id="7650c-103">Když nakreslíte čáru, je nutné předat <xref:System.Drawing.Pen> objektu <xref:System.Drawing.Graphics.DrawLine%2A> metodu <xref:System.Drawing.Graphics> třídy.</span><span class="sxs-lookup"><span data-stu-id="7650c-103">When you draw a line, you must pass a <xref:System.Drawing.Pen> object to the <xref:System.Drawing.Graphics.DrawLine%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="7650c-104">Jeden z parametrů <xref:System.Drawing.Pen.%23ctor%2A> je konstruktor <xref:System.Drawing.Color> objektu.</span><span class="sxs-lookup"><span data-stu-id="7650c-104">One of the parameters of the <xref:System.Drawing.Pen.%23ctor%2A> constructor is a <xref:System.Drawing.Color> object.</span></span> <span data-ttu-id="7650c-105">Kreslení neprůhledných čáry, nastavte hodnota alfa barvy do 255.</span><span class="sxs-lookup"><span data-stu-id="7650c-105">To draw an opaque line, set the alpha component of the color to 255.</span></span> <span data-ttu-id="7650c-106">Nakreslení poloprůhledných čáry, nastavte na libovolnou hodnotu od 1 do 254 alfa složkou.</span><span class="sxs-lookup"><span data-stu-id="7650c-106">To draw a semitransparent line, set the alpha component to any value from 1 through 254.</span></span>  
  
 <span data-ttu-id="7650c-107">Když nakreslíte čáru poloprůhledných na pozadí, Barva čáry jsou prolnuty barvy pozadí.</span><span class="sxs-lookup"><span data-stu-id="7650c-107">When you draw a semitransparent line over a background, the color of the line is blended with the colors of the background.</span></span> <span data-ttu-id="7650c-108">Hodnota alfa Určuje, jak barvy čáry a pozadí směšování; hodnoty alfa téměř 0 umístěte větší váhu na barvy pozadí a alfa hodnot v 255 umístit větší váhu na barvu čáry.</span><span class="sxs-lookup"><span data-stu-id="7650c-108">The alpha component specifies how the line and background colors are mixed; alpha values near 0 place more weight on the background colors, and alpha values near 255 place more weight on the line color.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7650c-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="7650c-109">Example</span></span>  
 <span data-ttu-id="7650c-110">V následujícím příkladu nakreslí rastrový obrázek a pak vykreslí tři řádky, které používají rastrového obrázku na pozadí.</span><span class="sxs-lookup"><span data-stu-id="7650c-110">The following example draws a bitmap and then draws three lines that use the bitmap as a background.</span></span> <span data-ttu-id="7650c-111">První řádek používá alfa složkou 255, proto je skrytá.</span><span class="sxs-lookup"><span data-stu-id="7650c-111">The first line uses an alpha component of 255, so it is opaque.</span></span> <span data-ttu-id="7650c-112">Druhý a třetí řádky použít alfa složkou 128, tak, aby byly poloprůhledných; Zobrazí se obrázek pozadí přes řádky.</span><span class="sxs-lookup"><span data-stu-id="7650c-112">The second and third lines use an alpha component of 128, so they are semitransparent; you can see the background image through the lines.</span></span> <span data-ttu-id="7650c-113">Příkaz, který nastaví <xref:System.Drawing.Graphics.CompositingQuality%2A> vlastnosti způsobí, že míchání pro udělat ve spojení s gama korekce na třetím řádku.</span><span class="sxs-lookup"><span data-stu-id="7650c-113">The statement that sets the <xref:System.Drawing.Graphics.CompositingQuality%2A> property causes the blending for the third line to be done in conjunction with gamma correction.</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.AlphaBlending#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#11)]  
  
 <span data-ttu-id="7650c-114">Následující obrázek znázorňuje výstup následující kód:</span><span class="sxs-lookup"><span data-stu-id="7650c-114">The following illustration shows the output of the following code:</span></span>  
  
 ![Obrázek, na kterém neprůhledných a poloprůhledných výstupu](./media/how-to-draw-opaque-and-semitransparent-lines/opaque-semitransparent-lines.png)  

## <a name="compiling-the-code"></a><span data-ttu-id="7650c-116">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="7650c-116">Compiling the Code</span></span>  
 <span data-ttu-id="7650c-117">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="7650c-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7650c-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7650c-118">See also</span></span>
- [<span data-ttu-id="7650c-119">Alfa míchání čar a výplní</span><span class="sxs-lookup"><span data-stu-id="7650c-119">Alpha Blending Lines and Fills</span></span>](alpha-blending-lines-and-fills.md)
- [<span data-ttu-id="7650c-120">Postupy: Zadejte svůj ovládací prvek průhledné pozadí</span><span class="sxs-lookup"><span data-stu-id="7650c-120">How to: Give Your Control a Transparent Background</span></span>](../controls/how-to-give-your-control-a-transparent-background.md)
- [<span data-ttu-id="7650c-121">Postupy: Kreslení pomocí neprůhledných a poloprůhledných štětců</span><span class="sxs-lookup"><span data-stu-id="7650c-121">How to: Draw with Opaque and Semitransparent Brushes</span></span>](how-to-draw-with-opaque-and-semitransparent-brushes.md)
