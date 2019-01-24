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
ms.openlocfilehash: 922cf6f9fd506e6095d87c3e0ee9eff85f920eba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54586960"
---
# <a name="how-to-draw-with-opaque-and-semitransparent-brushes"></a><span data-ttu-id="6792c-102">Postupy: Kreslení pomocí neprůhledných a poloprůhledných štětců</span><span class="sxs-lookup"><span data-stu-id="6792c-102">How to: Draw with Opaque and Semitransparent Brushes</span></span>
<span data-ttu-id="6792c-103">Po vyplnění obrazce, je nutné předat <xref:System.Drawing.Brush> objektu do jedné z metod výplň <xref:System.Drawing.Graphics> třídy.</span><span class="sxs-lookup"><span data-stu-id="6792c-103">When you fill a shape, you must pass a <xref:System.Drawing.Brush> object to one of the fill methods of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="6792c-104">Jeden parametr <xref:System.Drawing.SolidBrush.%23ctor%2A> je konstruktor <xref:System.Drawing.Color> objektu.</span><span class="sxs-lookup"><span data-stu-id="6792c-104">The one parameter of the <xref:System.Drawing.SolidBrush.%23ctor%2A> constructor is a <xref:System.Drawing.Color> object.</span></span> <span data-ttu-id="6792c-105">K vyplnění obrazce neprůhledný, nastavte alfa barvy na 255.</span><span class="sxs-lookup"><span data-stu-id="6792c-105">To fill an opaque shape, set the alpha component of the color to 255.</span></span> <span data-ttu-id="6792c-106">K vyplnění poloprůhledných tvar, nastavte na libovolnou hodnotu od 1 do 254 alfa složkou.</span><span class="sxs-lookup"><span data-stu-id="6792c-106">To fill a semitransparent shape, set the alpha component to any value from 1 through 254.</span></span>  
  
 <span data-ttu-id="6792c-107">Po vyplnění poloprůhledných tvar, barvu tvaru jsou prolnuty barvy pozadí.</span><span class="sxs-lookup"><span data-stu-id="6792c-107">When you fill a semitransparent shape, the color of the shape is blended with the colors of the background.</span></span> <span data-ttu-id="6792c-108">Hodnota alfa Určuje, jak barvy tvar a pozadí směšování; hodnoty alfa téměř 0 umístěte větší váhu na barvy pozadí a alfa hodnot v 255 ustaví větší váhu barvou obrazce.</span><span class="sxs-lookup"><span data-stu-id="6792c-108">The alpha component specifies how the shape and background colors are mixed; alpha values near 0 place more weight on the background colors, and alpha values near 255 place more weight on the shape color.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6792c-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="6792c-109">Example</span></span>  
 <span data-ttu-id="6792c-110">V následujícím příkladu nakreslí rastrový obrázek a potom naplní tři symbol tří teček, které se překrývají rastrového obrázku.</span><span class="sxs-lookup"><span data-stu-id="6792c-110">The following example draws a bitmap and then fills three ellipses that overlap the bitmap.</span></span> <span data-ttu-id="6792c-111">První tři tečky používá alfa složkou 255, proto je skrytá.</span><span class="sxs-lookup"><span data-stu-id="6792c-111">The first ellipse uses an alpha component of 255, so it is opaque.</span></span> <span data-ttu-id="6792c-112">Druhý a třetí symbol tří teček použít alfa složkou 128, tak, aby byly poloprůhledných; Zobrazí se obrázek pozadí prostřednictvím symbol tří teček.</span><span class="sxs-lookup"><span data-stu-id="6792c-112">The second and third ellipses use an alpha component of 128, so they are semitransparent; you can see the background image through the ellipses.</span></span> <span data-ttu-id="6792c-113">Volání, které nastaví <xref:System.Drawing.Graphics.CompositingQuality%2A> vlastnosti způsobí, že míchání třetí elipsy ve spojení s gama korekce udělat.</span><span class="sxs-lookup"><span data-stu-id="6792c-113">The call that sets the <xref:System.Drawing.Graphics.CompositingQuality%2A> property causes the blending for the third ellipse to be done in conjunction with gamma correction.</span></span>  
  
 <span data-ttu-id="6792c-114">Následující obrázek znázorňuje výstup následující kód.</span><span class="sxs-lookup"><span data-stu-id="6792c-114">The following illustration shows the output of the following code.</span></span>  
  
 <span data-ttu-id="6792c-115">![Neprůhledných a poloprůhledných](../../../../docs/framework/winforms/advanced/media/compqualellipse.png "compqualellipse")</span><span class="sxs-lookup"><span data-stu-id="6792c-115">![Opaque and Semitransparent](../../../../docs/framework/winforms/advanced/media/compqualellipse.png "compqualellipse")</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.AlphaBlending#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6792c-116">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="6792c-116">Compiling the Code</span></span>  
 <span data-ttu-id="6792c-117">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="6792c-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6792c-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6792c-118">See also</span></span>
- [<span data-ttu-id="6792c-119">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6792c-119">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="6792c-120">Alfa míchání čar a výplní</span><span class="sxs-lookup"><span data-stu-id="6792c-120">Alpha Blending Lines and Fills</span></span>](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)
- [<span data-ttu-id="6792c-121">Postupy: Zadejte svůj ovládací prvek průhledné pozadí</span><span class="sxs-lookup"><span data-stu-id="6792c-121">How to: Give Your Control a Transparent Background</span></span>](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)
- [<span data-ttu-id="6792c-122">Postupy: Kreslení neprůhledných a poloprůhledných čar</span><span class="sxs-lookup"><span data-stu-id="6792c-122">How to: Draw Opaque and Semitransparent Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)
