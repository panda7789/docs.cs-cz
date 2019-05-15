---
title: 'Postupy: Otáčení barev'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], rotating
- examples [Windows Forms], rotating colors
ms.assetid: e2e4c300-159c-4f4a-9b56-103b0f7cbc05
ms.openlocfilehash: d251a223fca50eebc3a959ea694242992c4a1dbe
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65590321"
---
# <a name="how-to-rotate-colors"></a><span data-ttu-id="bc7de-102">Postupy: Otáčení barev</span><span class="sxs-lookup"><span data-stu-id="bc7de-102">How to: Rotate Colors</span></span>
<span data-ttu-id="bc7de-103">Otočení v four-dimensional barevný prostor je obtížné vizualizace.</span><span class="sxs-lookup"><span data-stu-id="bc7de-103">Rotation in a four-dimensional color space is difficult to visualize.</span></span> <span data-ttu-id="bc7de-104">Můžeme provádět to usnadňuje vizualizaci otočení souhlasit a udržovat jeden barevným opraveno.</span><span class="sxs-lookup"><span data-stu-id="bc7de-104">We can make it easier to visualize rotation by agreeing to keep one of the color components fixed.</span></span> <span data-ttu-id="bc7de-105">Předpokládejme, že jsme souhlas zachovat alfa pevně nastavena na 1 (úplně neprůhledné).</span><span class="sxs-lookup"><span data-stu-id="bc7de-105">Suppose we agree to keep the alpha component fixed at 1 (fully opaque).</span></span> <span data-ttu-id="bc7de-106">Potom jsme vizualizace trojrozměrného barevný prostor pomocí červené, zelené a modré osy, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="bc7de-106">Then we can visualize a three-dimensional color space with red, green, and blue axes as shown in the following illustration.</span></span>  
  
 ![Obrázek, na kterém otočení pomocí červené, zelené a modré osy.](./media/how-to-rotate-colors/rotation-red-green-blue-axes.gif)  
  
 <span data-ttu-id="bc7de-108">Barvu můžete představit jako bod v 3D prostoru.</span><span class="sxs-lookup"><span data-stu-id="bc7de-108">A color can be thought of as a point in 3-D space.</span></span> <span data-ttu-id="bc7de-109">Například bod (1, 0, 0) v prostoru představuje červenou barvu a bod (0, 1, 0) v prostoru představuje zelenou barvu.</span><span class="sxs-lookup"><span data-stu-id="bc7de-109">For example, the point (1, 0, 0) in space represents the color red, and the point (0, 1, 0) in space represents the color green.</span></span>  
  
 <span data-ttu-id="bc7de-110">Následující obrázek znázorňuje prostřednictvím úhel 60 stupňů v rovině červenou a zelenou význam otočení barev (1, 0, 0).</span><span class="sxs-lookup"><span data-stu-id="bc7de-110">The following illustration shows what it means to rotate the color (1, 0, 0) through an angle of 60 degrees in the Red-Green plane.</span></span> <span data-ttu-id="bc7de-111">Otočení paralelně roviny k rovině červenou a zelenou můžete představit jako otočení o modrá osu.</span><span class="sxs-lookup"><span data-stu-id="bc7de-111">Rotation in a plane parallel to the Red-Green plane can be thought of as rotation about the blue axis.</span></span>  
  
 ![Obrázek, na kterém otočení o modrá osu.](./media/how-to-rotate-colors/rotation-about-blue-axis.gif)  
  
 <span data-ttu-id="bc7de-113">Následující obrázek znázorňuje způsob inicializace matice barev k provedení rotace o každé ze tří OS souřadnic (červená, zelená, modrá):</span><span class="sxs-lookup"><span data-stu-id="bc7de-113">The following illustration shows how to initialize a color matrix to perform rotations about each of the three coordinate axes (red, green, blue):</span></span>  
  
 ![Inicializujte matice barev k provedení rotace o tři osy.](./media/how-to-rotate-colors/rotation-about-three-axes.gif)  
  
## <a name="example"></a><span data-ttu-id="bc7de-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc7de-115">Example</span></span>  
 <span data-ttu-id="bc7de-116">Následující příklad používá image, která je všechny jednu barvu (1, 0, 0.6) a platí otočení 60 stupňů o modrá osu.</span><span class="sxs-lookup"><span data-stu-id="bc7de-116">The following example takes an image that is all one color (1, 0, 0.6) and applies a 60-degree rotation about the blue axis.</span></span> <span data-ttu-id="bc7de-117">Úhel otočení je, jež navýšení kapacity v rovině, který je paralelní k rovině červenou a zelenou.</span><span class="sxs-lookup"><span data-stu-id="bc7de-117">The angle of the rotation is swept out in a plane that is parallel to the red-green plane.</span></span>  
  
 <span data-ttu-id="bc7de-118">Následující obrázek znázorňuje původní obrázek nalevo a obrázek otočí barvu na pravé straně:</span><span class="sxs-lookup"><span data-stu-id="bc7de-118">The following illustration shows the original image on the left and the color-rotated image on the right:</span></span>  
  
 ![Obrázek, který ukazuje původní image a image barva otočen.](./media/how-to-rotate-colors/original-color-rotated-images.png)  
  
 <span data-ttu-id="bc7de-120">Následující obrázek znázorňuje vizualizace otáčení barev provést v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="bc7de-120">The following illustration shows a visualization of the color rotation performed in the following code:</span></span>
  
 ![Obrázek, který zobrazuje vizualizaci otočení barev.](./media/how-to-rotate-colors/visualization-color-rotation.gif)  
  
 [!code-csharp[System.Drawing.RotateColors#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bc7de-122">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="bc7de-122">Compiling the Code</span></span>  
 <span data-ttu-id="bc7de-123">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="bc7de-123">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="bc7de-124">Nahraďte `RotationInput.bmp` název a cesta platné ve vašem systému.</span><span class="sxs-lookup"><span data-stu-id="bc7de-124">Replace `RotationInput.bmp` with an image file name and path valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc7de-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bc7de-125">See also</span></span>

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="bc7de-126">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bc7de-126">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="bc7de-127">Přebarvení obrázků</span><span class="sxs-lookup"><span data-stu-id="bc7de-127">Recoloring Images</span></span>](recoloring-images.md)
