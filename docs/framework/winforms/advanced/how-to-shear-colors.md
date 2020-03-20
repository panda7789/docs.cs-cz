---
title: 'Postupy: Zkosení barev'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], transforming with color matrices
- colors [Windows Forms], shearing
ms.assetid: 0a424171-5b8b-45c4-afef-e9720a6c3e22
ms.openlocfilehash: 825e5a90ebb0d9df3b894ce7bd353e917b676939
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142391"
---
# <a name="how-to-shear-colors"></a><span data-ttu-id="753a8-102">Postupy: Zkosení barev</span><span class="sxs-lookup"><span data-stu-id="753a8-102">How to: Shear Colors</span></span>
<span data-ttu-id="753a8-103">Zkosení zvětšuje nebo zmenšuje barevnou složku o částku úměrnou jiné barevné složce.</span><span class="sxs-lookup"><span data-stu-id="753a8-103">Shearing increases or decreases a color component by an amount proportional to another color component.</span></span> <span data-ttu-id="753a8-104">Zvažte například transformaci, kde je červená komponenta zvýšena o polovinu hodnoty modré součásti.</span><span class="sxs-lookup"><span data-stu-id="753a8-104">For example, consider the transformation where the red component is increased by one half the value of the blue component.</span></span> <span data-ttu-id="753a8-105">Při takové transformaci by se barva (0,2, 0,5, 1) stala (0,7, 0,5, 1).</span><span class="sxs-lookup"><span data-stu-id="753a8-105">Under such a transformation, the color (0.2, 0.5, 1) would become (0.7, 0.5, 1).</span></span> <span data-ttu-id="753a8-106">Nová červená složka je 0,2 + (1/2)(1) = 0,7.</span><span class="sxs-lookup"><span data-stu-id="753a8-106">The new red component is 0.2 + (1/2)(1) = 0.7.</span></span>  
  
## <a name="example"></a><span data-ttu-id="753a8-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="753a8-107">Example</span></span>  
 <span data-ttu-id="753a8-108">Následující příklad vytvoří <xref:System.Drawing.Image> objekt ze souboru ColorBars4.bmp.</span><span class="sxs-lookup"><span data-stu-id="753a8-108">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars4.bmp.</span></span> <span data-ttu-id="753a8-109">Pak kód použije zkosení transformace popsané v předchozím odstavci na každý obrazový bod v obraze.</span><span class="sxs-lookup"><span data-stu-id="753a8-109">Then the code applies the shearing transformation described in the preceding paragraph to each pixel in the image.</span></span>  
  
 <span data-ttu-id="753a8-110">Následující obrázek znázorňuje původní obrázek vlevo a střižený obrázek vpravo:</span><span class="sxs-lookup"><span data-stu-id="753a8-110">The following illustration shows the original image on the left and the sheared image on the right:</span></span>
  
 ![Dva čtverce s barevnými pruhy vedle sebe ilustrující původní obraz a stočený obraz.](./media/how-to-shear-colors/original-image-sheared-image.png)  
  
 <span data-ttu-id="753a8-112">V následující tabulce jsou uvedeny vektory barev pro čtyři pruhy před a po transformaci zkosení.</span><span class="sxs-lookup"><span data-stu-id="753a8-112">The following table lists the color vectors for the four bars before and after the shearing transformation.</span></span>  
  
|<span data-ttu-id="753a8-113">Původní</span><span class="sxs-lookup"><span data-stu-id="753a8-113">Original</span></span>|<span data-ttu-id="753a8-114">Sazený</span><span class="sxs-lookup"><span data-stu-id="753a8-114">Sheared</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="753a8-115">(0, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="753a8-115">(0, 0, 1, 1)</span></span>|<span data-ttu-id="753a8-116">(0.5, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="753a8-116">(0.5, 0, 1, 1)</span></span>|  
|<span data-ttu-id="753a8-117">(0.5, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="753a8-117">(0.5, 1, 0.5, 1)</span></span>|<span data-ttu-id="753a8-118">(0.75, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="753a8-118">(0.75, 1, 0.5, 1)</span></span>|  
|<span data-ttu-id="753a8-119">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="753a8-119">(1, 1, 0, 1)</span></span>|<span data-ttu-id="753a8-120">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="753a8-120">(1, 1, 0, 1)</span></span>|  
|<span data-ttu-id="753a8-121">(0.4, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="753a8-121">(0.4, 0.4, 0.4, 1)</span></span>|<span data-ttu-id="753a8-122">(0.6, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="753a8-122">(0.6, 0.4, 0.4, 1)</span></span>|  
  
 [!code-csharp[System.Drawing.Misc3#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="753a8-123">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="753a8-123">Compiling the Code</span></span>  
 <span data-ttu-id="753a8-124">Předchozí příklad je určen pro použití s windows <xref:System.Windows.Forms.PaintEventArgs> `e`forms a vyžaduje <xref:System.Windows.Forms.Control.Paint> , což je parametr obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="753a8-124">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="753a8-125">Nahraďte `ColorBars.bmp` název obrázku a cestu platnou v systému.</span><span class="sxs-lookup"><span data-stu-id="753a8-125">Replace `ColorBars.bmp` with an image name and path valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="753a8-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="753a8-126">See also</span></span>

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="753a8-127">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="753a8-127">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="753a8-128">Přebarvení obrázků</span><span class="sxs-lookup"><span data-stu-id="753a8-128">Recoloring Images</span></span>](recoloring-images.md)
