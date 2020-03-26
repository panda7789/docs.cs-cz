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
ms.openlocfilehash: 8d2717dd7b819e963126072279b361fda02188bc
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111332"
---
# <a name="how-to-rotate-colors"></a><span data-ttu-id="39e1b-102">Postupy: Otáčení barev</span><span class="sxs-lookup"><span data-stu-id="39e1b-102">How to: Rotate Colors</span></span>
<span data-ttu-id="39e1b-103">Rotace ve čtyřrozměrném barevném prostoru je obtížné vizualizovat.</span><span class="sxs-lookup"><span data-stu-id="39e1b-103">Rotation in a four-dimensional color space is difficult to visualize.</span></span> <span data-ttu-id="39e1b-104">Můžeme usnadnit vizualizaci rotace tím, že souhlasís tím, aby jedna z barevných složek pevné.</span><span class="sxs-lookup"><span data-stu-id="39e1b-104">We can make it easier to visualize rotation by agreeing to keep one of the color components fixed.</span></span> <span data-ttu-id="39e1b-105">Předpokládejme, že se dohodneme na zachování alfa komponenty pevné na 1 (plně neprůhledné).</span><span class="sxs-lookup"><span data-stu-id="39e1b-105">Suppose we agree to keep the alpha component fixed at 1 (fully opaque).</span></span> <span data-ttu-id="39e1b-106">Pak můžeme vizualizovat trojrozměrný barevný prostor s červenými, zelenými a modrými osami, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="39e1b-106">Then we can visualize a three-dimensional color space with red, green, and blue axes as shown in the following illustration.</span></span>  
  
 ![Obrázek znázorňovaný otočením s červenými, zelenými a modrými osami.](./media/how-to-rotate-colors/rotation-red-green-blue-axes.gif)  
  
 <span data-ttu-id="39e1b-108">Barvu lze považovat za bod ve 3D prostoru.</span><span class="sxs-lookup"><span data-stu-id="39e1b-108">A color can be thought of as a point in 3D space.</span></span> <span data-ttu-id="39e1b-109">Například bod (1, 0, 0) v prostoru představuje červenou barvu a bod (0, 1, 0) v prostoru představuje zelenou barvu.</span><span class="sxs-lookup"><span data-stu-id="39e1b-109">For example, the point (1, 0, 0) in space represents the color red, and the point (0, 1, 0) in space represents the color green.</span></span>  
  
 <span data-ttu-id="39e1b-110">Následující obrázek znázorňuje, co znamená otočit barvu (1, 0, 0) pod úhlem 60 stupňů v červenozelené rovině.</span><span class="sxs-lookup"><span data-stu-id="39e1b-110">The following illustration shows what it means to rotate the color (1, 0, 0) through an angle of 60 degrees in the Red-Green plane.</span></span> <span data-ttu-id="39e1b-111">Otočení v rovině rovnoběžné s červeno-zelenou rovinou lze považovat za rotaci kolem modré osy.</span><span class="sxs-lookup"><span data-stu-id="39e1b-111">Rotation in a plane parallel to the Red-Green plane can be thought of as rotation about the blue axis.</span></span>  
  
 ![Obrázek znázorňuje otočení kolem modré osy.](./media/how-to-rotate-colors/rotation-about-blue-axis.gif)  
  
 <span data-ttu-id="39e1b-113">Následující obrázek znázorňuje, jak inicializovat matici barev, aby se provedla rotace kolem každé ze tří os souřadnic (červená, zelená, modrá):</span><span class="sxs-lookup"><span data-stu-id="39e1b-113">The following illustration shows how to initialize a color matrix to perform rotations about each of the three coordinate axes (red, green, blue):</span></span>  
  
 ![Inicializovat matici barev, abyste provedli otočení asi tři osy.](./media/how-to-rotate-colors/rotation-about-three-axes.gif)  
  
## <a name="example"></a><span data-ttu-id="39e1b-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="39e1b-115">Example</span></span>  
 <span data-ttu-id="39e1b-116">Následující příklad přebírá obraz, který je všechny jednu barvu (1, 0, 0,6) a použije otočení o 60 stupňů kolem modré osy.</span><span class="sxs-lookup"><span data-stu-id="39e1b-116">The following example takes an image that is all one color (1, 0, 0.6) and applies a 60-degree rotation about the blue axis.</span></span> <span data-ttu-id="39e1b-117">Úhel natočení je vymet v rovině, která je rovnoběžná s červenozelenou rovinou.</span><span class="sxs-lookup"><span data-stu-id="39e1b-117">The angle of the rotation is swept out in a plane that is parallel to the red-green plane.</span></span>  
  
 <span data-ttu-id="39e1b-118">Následující obrázek znázorňuje původní obrázek vlevo a obrázek otočený o barvy vpravo:</span><span class="sxs-lookup"><span data-stu-id="39e1b-118">The following illustration shows the original image on the left and the color-rotated image on the right:</span></span>  
  
 ![Obrázek znázorňuje původní obraz a barevně otočený obraz.](./media/how-to-rotate-colors/original-color-rotated-images.png)  
  
 <span data-ttu-id="39e1b-120">Následující obrázek znázorňuje vizualizaci otáčení barev provedenou v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="39e1b-120">The following illustration shows a visualization of the color rotation performed in the following code:</span></span>
  
 ![Obrázek znázorňuje vizualizaci otáčení barev.](./media/how-to-rotate-colors/visualization-color-rotation.gif)  
  
 [!code-csharp[System.Drawing.RotateColors#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="39e1b-122">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="39e1b-122">Compiling the Code</span></span>  
 <span data-ttu-id="39e1b-123">Předchozí příklad je určen pro použití s windows <xref:System.Windows.Forms.PaintEventArgs> `e`forms a vyžaduje <xref:System.Windows.Forms.Control.Paint> , což je parametr obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="39e1b-123">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="39e1b-124">Nahraďte `RotationInput.bmp` název souboru obrázku a cestu platnou v systému.</span><span class="sxs-lookup"><span data-stu-id="39e1b-124">Replace `RotationInput.bmp` with an image file name and path valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39e1b-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="39e1b-125">See also</span></span>

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="39e1b-126">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="39e1b-126">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="39e1b-127">Přebarvení obrázků</span><span class="sxs-lookup"><span data-stu-id="39e1b-127">Recoloring Images</span></span>](recoloring-images.md)
