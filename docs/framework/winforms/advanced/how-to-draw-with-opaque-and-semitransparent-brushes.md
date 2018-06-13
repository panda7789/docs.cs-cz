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
ms.openlocfilehash: 91aa3e89e2ff6d20432dbc5e988f2877059b4cdd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523605"
---
# <a name="how-to-draw-with-opaque-and-semitransparent-brushes"></a><span data-ttu-id="34718-102">Postupy: Kreslení pomocí neprůhledných a poloprůhledných štětců</span><span class="sxs-lookup"><span data-stu-id="34718-102">How to: Draw with Opaque and Semitransparent Brushes</span></span>
<span data-ttu-id="34718-103">Po vyplnění obrazce, je nutné předat <xref:System.Drawing.Brush> objektu na jednu z metod výplně <xref:System.Drawing.Graphics> třídy.</span><span class="sxs-lookup"><span data-stu-id="34718-103">When you fill a shape, you must pass a <xref:System.Drawing.Brush> object to one of the fill methods of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="34718-104">Jeden parametr <xref:System.Drawing.SolidBrush.%23ctor%2A> konstruktor je <xref:System.Drawing.Color> objektu.</span><span class="sxs-lookup"><span data-stu-id="34718-104">The one parameter of the <xref:System.Drawing.SolidBrush.%23ctor%2A> constructor is a <xref:System.Drawing.Color> object.</span></span> <span data-ttu-id="34718-105">K vyplnění neprůhledného tvaru, nastavte komponentu alfa barvy na 255.</span><span class="sxs-lookup"><span data-stu-id="34718-105">To fill an opaque shape, set the alpha component of the color to 255.</span></span> <span data-ttu-id="34718-106">K vyplnění obrazce poloprůhledných, nastavte na jakoukoli hodnotu od 1 do 254 komponentu alfa.</span><span class="sxs-lookup"><span data-stu-id="34718-106">To fill a semitransparent shape, set the alpha component to any value from 1 through 254.</span></span>  
  
 <span data-ttu-id="34718-107">Jakmile zadáte poloprůhledných obrazce, barva obrazce je smíšený s barvy pozadí.</span><span class="sxs-lookup"><span data-stu-id="34718-107">When you fill a semitransparent shape, the color of the shape is blended with the colors of the background.</span></span> <span data-ttu-id="34718-108">Komponentu alfa Určuje, jak jsou kombinované barvy tvar a pozadí; hodnoty alfa téměř 0 umístěte další váhy barvy pozadí a hodnoty alfa téměř 255 umístit další váhy na barvou obrazce.</span><span class="sxs-lookup"><span data-stu-id="34718-108">The alpha component specifies how the shape and background colors are mixed; alpha values near 0 place more weight on the background colors, and alpha values near 255 place more weight on the shape color.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34718-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="34718-109">Example</span></span>  
 <span data-ttu-id="34718-110">Následující příklad nevykresluje rastrový obrázek a pak vyplní tři výpustky, které se překrývají bitové mapy.</span><span class="sxs-lookup"><span data-stu-id="34718-110">The following example draws a bitmap and then fills three ellipses that overlap the bitmap.</span></span> <span data-ttu-id="34718-111">První elipsy používá alfa součást 255, takže je plné krytí.</span><span class="sxs-lookup"><span data-stu-id="34718-111">The first ellipse uses an alpha component of 255, so it is opaque.</span></span> <span data-ttu-id="34718-112">Druhý a třetí výpustky použít alfa součást 128, tak, aby byly poloprůhledných; Zobrazí se obrázek pozadí prostřednictvím na symbol tří teček.</span><span class="sxs-lookup"><span data-stu-id="34718-112">The second and third ellipses use an alpha component of 128, so they are semitransparent; you can see the background image through the ellipses.</span></span> <span data-ttu-id="34718-113">Volání, které se nastaví <xref:System.Drawing.Graphics.CompositingQuality%2A> vlastnost způsobí, že prolnutí pro třetí elipsy provést ve spojení s korekce gama.</span><span class="sxs-lookup"><span data-stu-id="34718-113">The call that sets the <xref:System.Drawing.Graphics.CompositingQuality%2A> property causes the blending for the third ellipse to be done in conjunction with gamma correction.</span></span>  
  
 <span data-ttu-id="34718-114">Následující obrázek znázorňuje výstup následující kód.</span><span class="sxs-lookup"><span data-stu-id="34718-114">The following illustration shows the output of the following code.</span></span>  
  
 <span data-ttu-id="34718-115">![Neprůhledných a poloprůhledných](../../../../docs/framework/winforms/advanced/media/compqualellipse.png "compqualellipse")</span><span class="sxs-lookup"><span data-stu-id="34718-115">![Opaque and Semitransparent](../../../../docs/framework/winforms/advanced/media/compqualellipse.png "compqualellipse")</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.AlphaBlending#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="34718-116">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="34718-116">Compiling the Code</span></span>  
 <span data-ttu-id="34718-117">V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="34718-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34718-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="34718-118">See Also</span></span>  
 [<span data-ttu-id="34718-119">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="34718-119">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="34718-120">Alfa míchání čar a výplní</span><span class="sxs-lookup"><span data-stu-id="34718-120">Alpha Blending Lines and Fills</span></span>](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)  
 [<span data-ttu-id="34718-121">Postupy: Zajištění průhledného pozadí pro vlastní ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="34718-121">How to: Give Your Control a Transparent Background</span></span>](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 [<span data-ttu-id="34718-122">Postupy: Kreslení neprůhledných a poloprůhledných čar</span><span class="sxs-lookup"><span data-stu-id="34718-122">How to: Draw Opaque and Semitransparent Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)
