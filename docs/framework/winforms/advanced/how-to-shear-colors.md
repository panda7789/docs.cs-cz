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
ms.openlocfilehash: bf645cf88c4905cd5cf47c2a6c7af088fa428c8a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59076240"
---
# <a name="how-to-shear-colors"></a><span data-ttu-id="8b8f6-102">Postupy: Zkosení barev</span><span class="sxs-lookup"><span data-stu-id="8b8f6-102">How to: Shear Colors</span></span>
<span data-ttu-id="8b8f6-103">Zkosení zvyšuje nebo snižuje složku barvy podle zadaného množství úměrná jiné součásti barvy.</span><span class="sxs-lookup"><span data-stu-id="8b8f6-103">Shearing increases or decreases a color component by an amount proportional to another color component.</span></span> <span data-ttu-id="8b8f6-104">Představte si třeba transformace, kde se hodnota červené zvýší o polovinu hodnota modré.</span><span class="sxs-lookup"><span data-stu-id="8b8f6-104">For example, consider the transformation where the red component is increased by one half the value of the blue component.</span></span> <span data-ttu-id="8b8f6-105">V takové transformace barvu (0.2, 0,5, 1) by se mohla stát (0,7, 0,5, 1).</span><span class="sxs-lookup"><span data-stu-id="8b8f6-105">Under such a transformation, the color (0.2, 0.5, 1) would become (0.7, 0.5, 1).</span></span> <span data-ttu-id="8b8f6-106">Nová hodnota červené je 0.2 + (1/2)(1) = 0,7.</span><span class="sxs-lookup"><span data-stu-id="8b8f6-106">The new red component is 0.2 + (1/2)(1) = 0.7.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b8f6-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="8b8f6-107">Example</span></span>  
 <span data-ttu-id="8b8f6-108">Následující příklad vytvoří <xref:System.Drawing.Image> objekt ze souboru ColorBars4.bmp.</span><span class="sxs-lookup"><span data-stu-id="8b8f6-108">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars4.bmp.</span></span> <span data-ttu-id="8b8f6-109">Potom kód použije transformace zkosení je popsáno v předchozím odstavci každý pixel na obrázku.</span><span class="sxs-lookup"><span data-stu-id="8b8f6-109">Then the code applies the shearing transformation described in the preceding paragraph to each pixel in the image.</span></span>  
  
 <span data-ttu-id="8b8f6-110">Následující obrázek znázorňuje původní obrázek na levé straně a zkosené image na pravé straně:</span><span class="sxs-lookup"><span data-stu-id="8b8f6-110">The following illustration shows the original image on the left and the sheared image on the right:</span></span> 
  
 ![Dvě pole s barevné pruhy – souběžně ilustrující původní bitové kopie a zkosené bitové kopie.](./media/how-to-shear-colors/original-image-sheared-image.png)  
  
 <span data-ttu-id="8b8f6-112">Následující tabulka uvádí vektory barvu pro čtyři pruhy před a po transformaci zkosení.</span><span class="sxs-lookup"><span data-stu-id="8b8f6-112">The following table lists the color vectors for the four bars before and after the shearing transformation.</span></span>  
  
|<span data-ttu-id="8b8f6-113">Původní</span><span class="sxs-lookup"><span data-stu-id="8b8f6-113">Original</span></span>|<span data-ttu-id="8b8f6-114">Stříhanou</span><span class="sxs-lookup"><span data-stu-id="8b8f6-114">Sheared</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="8b8f6-115">(0, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="8b8f6-115">(0, 0, 1, 1)</span></span>|<span data-ttu-id="8b8f6-116">(0.5, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="8b8f6-116">(0.5, 0, 1, 1)</span></span>|  
|<span data-ttu-id="8b8f6-117">(0.5, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="8b8f6-117">(0.5, 1, 0.5, 1)</span></span>|<span data-ttu-id="8b8f6-118">(0.75, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="8b8f6-118">(0.75, 1, 0.5, 1)</span></span>|  
|<span data-ttu-id="8b8f6-119">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="8b8f6-119">(1, 1, 0, 1)</span></span>|<span data-ttu-id="8b8f6-120">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="8b8f6-120">(1, 1, 0, 1)</span></span>|  
|<span data-ttu-id="8b8f6-121">(0.4, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="8b8f6-121">(0.4, 0.4, 0.4, 1)</span></span>|<span data-ttu-id="8b8f6-122">(0.6, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="8b8f6-122">(0.6, 0.4, 0.4, 1)</span></span>|  
  
 [!code-csharp[System.Drawing.Misc3#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8b8f6-123">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="8b8f6-123">Compiling the Code</span></span>  
 <span data-ttu-id="8b8f6-124">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="8b8f6-124">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="8b8f6-125">Nahraďte `ColorBars.bmp` image název a cesta platné ve vašem systému.</span><span class="sxs-lookup"><span data-stu-id="8b8f6-125">Replace `ColorBars.bmp` with an image name and path valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b8f6-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b8f6-126">See also</span></span>

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="8b8f6-127">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8b8f6-127">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="8b8f6-128">Přebarvení obrázků</span><span class="sxs-lookup"><span data-stu-id="8b8f6-128">Recoloring Images</span></span>](recoloring-images.md)
