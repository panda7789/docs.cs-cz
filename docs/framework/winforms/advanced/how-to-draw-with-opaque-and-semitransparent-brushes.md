---
title: 'Postupy: Kreslení pomocí neprůhledných a poloprůhledných štětců'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- semi-transparent shapes [Windows Forms], drawing
- transparency [Windows Forms], semi-transparent shapes
- alpha blending [Windows Forms], brush
- brushes [Windows Forms], using semi-transparent
ms.assetid: a4f6f6b8-3bc8-440a-84af-d62ef0f8ff40
ms.openlocfilehash: 1e48bbd563f6377380848949325962b568fa432c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142404"
---
# <a name="how-to-draw-with-opaque-and-semitransparent-brushes"></a><span data-ttu-id="ac577-102">Postupy: Kreslení pomocí neprůhledných a poloprůhledných štětců</span><span class="sxs-lookup"><span data-stu-id="ac577-102">How to: Draw with Opaque and Semitransparent Brushes</span></span>
<span data-ttu-id="ac577-103">Při vyplňování tvaru je nutné <xref:System.Drawing.Brush> předat objekt jedné z <xref:System.Drawing.Graphics> metod výplně třídy.</span><span class="sxs-lookup"><span data-stu-id="ac577-103">When you fill a shape, you must pass a <xref:System.Drawing.Brush> object to one of the fill methods of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="ac577-104">Jeden parametr konstruktoru <xref:System.Drawing.SolidBrush.%23ctor%2A> <xref:System.Drawing.Color> je objekt.</span><span class="sxs-lookup"><span data-stu-id="ac577-104">The one parameter of the <xref:System.Drawing.SolidBrush.%23ctor%2A> constructor is a <xref:System.Drawing.Color> object.</span></span> <span data-ttu-id="ac577-105">Chcete-li vyplnit neprůhledný tvar, nastavte alfa složku barvy na 255.</span><span class="sxs-lookup"><span data-stu-id="ac577-105">To fill an opaque shape, set the alpha component of the color to 255.</span></span> <span data-ttu-id="ac577-106">Chcete-li vyplnit poloprůhledný tvar, nastavte komponentu alfa na libovolnou hodnotu od 1 do 254.</span><span class="sxs-lookup"><span data-stu-id="ac577-106">To fill a semitransparent shape, set the alpha component to any value from 1 through 254.</span></span>  
  
 <span data-ttu-id="ac577-107">Když vyplníte poloprůhledný tvar, barva tvaru se prolne s barvami pozadí.</span><span class="sxs-lookup"><span data-stu-id="ac577-107">When you fill a semitransparent shape, the color of the shape is blended with the colors of the background.</span></span> <span data-ttu-id="ac577-108">Komponenta alfa určuje, jak se smíchají barvy tvaru a pozadí; Hodnoty alfa v blízkosti 0 kladou větší váhu na barvy pozadí a hodnoty alfa poblíž 255 kladou větší váhu na barvu tvaru.</span><span class="sxs-lookup"><span data-stu-id="ac577-108">The alpha component specifies how the shape and background colors are mixed; alpha values near 0 place more weight on the background colors, and alpha values near 255 place more weight on the shape color.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac577-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="ac577-109">Example</span></span>  
 <span data-ttu-id="ac577-110">Následující příklad nakreslí bitmapu a pak vyplní tři elipsy, které rastrový obrázek překrývají.</span><span class="sxs-lookup"><span data-stu-id="ac577-110">The following example draws a bitmap and then fills three ellipses that overlap the bitmap.</span></span> <span data-ttu-id="ac577-111">První elipsa používá alfa součást 255, takže je neprůhledná.</span><span class="sxs-lookup"><span data-stu-id="ac577-111">The first ellipse uses an alpha component of 255, so it is opaque.</span></span> <span data-ttu-id="ac577-112">Druhá a třetí elipsy používají alfa součást 128, takže jsou poloprůhledné; můžete vidět obrázek na pozadí přes elipsy.</span><span class="sxs-lookup"><span data-stu-id="ac577-112">The second and third ellipses use an alpha component of 128, so they are semitransparent; you can see the background image through the ellipses.</span></span> <span data-ttu-id="ac577-113">Volání, které <xref:System.Drawing.Graphics.CompositingQuality%2A> nastaví vlastnost způsobí prolnutí pro třetí elipsy, které mají být provedeny ve spojení s korekcí gama.</span><span class="sxs-lookup"><span data-stu-id="ac577-113">The call that sets the <xref:System.Drawing.Graphics.CompositingQuality%2A> property causes the blending for the third ellipse to be done in conjunction with gamma correction.</span></span>  

 [!code-csharp[System.Drawing.AlphaBlending#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.AlphaBlending#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#31)]  

 <span data-ttu-id="ac577-114">Následující obrázek znázorňuje výstup následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="ac577-114">The following illustration shows the output of the following code:</span></span>
  
 ![Obrázek znázorňuje neprůhledný a poloprůhledný výstup.](./media/how-to-draw-with-opaque-and-semitransparent-brushes/compositingquality-ellipse-semitransparent.png)  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ac577-116">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ac577-116">Compiling the Code</span></span>  
 <span data-ttu-id="ac577-117">Předchozí příklad je určen pro použití s windows <xref:System.Windows.Forms.PaintEventArgs> `e`forms a vyžaduje <xref:System.Windows.Forms.PaintEventHandler>, což je parametr .</span><span class="sxs-lookup"><span data-stu-id="ac577-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac577-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="ac577-118">See also</span></span>

- [<span data-ttu-id="ac577-119">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ac577-119">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="ac577-120">Alfa míchání čar a výplní</span><span class="sxs-lookup"><span data-stu-id="ac577-120">Alpha Blending Lines and Fills</span></span>](alpha-blending-lines-and-fills.md)
- [<span data-ttu-id="ac577-121">Postupy: Zajištění průhledného pozadí pro vlastní ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="ac577-121">How to: Give Your Control a Transparent Background</span></span>](../controls/how-to-give-your-control-a-transparent-background.md)
- [<span data-ttu-id="ac577-122">Postupy: Kreslení neprůhledných a poloprůhledných čar</span><span class="sxs-lookup"><span data-stu-id="ac577-122">How to: Draw Opaque and Semitransparent Lines</span></span>](how-to-draw-opaque-and-semitransparent-lines.md)
