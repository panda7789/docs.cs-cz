---
title: 'Postupy: Překlad barev obrázků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [Windows Forms], changing colors
- images [Windows Forms], changing colors
- image colors [Windows Forms]
ms.assetid: 2106fb9a-4d60-4dcf-9220-9f189a6c4d19
ms.openlocfilehash: 04e61383ef79b17ea6e1523588cd9593ec9b082c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132636"
---
# <a name="how-to-translate-image-colors"></a><span data-ttu-id="5acfa-102">Postupy: Překlad barev obrázků</span><span class="sxs-lookup"><span data-stu-id="5acfa-102">How to: Translate Image Colors</span></span>
<span data-ttu-id="5acfa-103">Překlad přidá hodnotu na jeden nebo více součástí čtyři barvy.</span><span class="sxs-lookup"><span data-stu-id="5acfa-103">A translation adds a value to one or more of the four color components.</span></span> <span data-ttu-id="5acfa-104">Matice položek barev, které představují překlady jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="5acfa-104">The color matrix entries that represent translations are given in the following table.</span></span>  
  
|<span data-ttu-id="5acfa-105">Součást, kterou přeložit</span><span class="sxs-lookup"><span data-stu-id="5acfa-105">Component to be translated</span></span>|<span data-ttu-id="5acfa-106">Přehled vstupu</span><span class="sxs-lookup"><span data-stu-id="5acfa-106">Matrix entry</span></span>|  
|--------------------------------|------------------|  
|<span data-ttu-id="5acfa-107">Červená</span><span class="sxs-lookup"><span data-stu-id="5acfa-107">Red</span></span>|<span data-ttu-id="5acfa-108">[4][0]</span><span class="sxs-lookup"><span data-stu-id="5acfa-108">[4][0]</span></span>|  
|<span data-ttu-id="5acfa-109">Zelená</span><span class="sxs-lookup"><span data-stu-id="5acfa-109">Green</span></span>|<span data-ttu-id="5acfa-110">[4][1]</span><span class="sxs-lookup"><span data-stu-id="5acfa-110">[4][1]</span></span>|  
|<span data-ttu-id="5acfa-111">Modrá</span><span class="sxs-lookup"><span data-stu-id="5acfa-111">Blue</span></span>|<span data-ttu-id="5acfa-112">[4][2]</span><span class="sxs-lookup"><span data-stu-id="5acfa-112">[4][2]</span></span>|  
|<span data-ttu-id="5acfa-113">Alpha</span><span class="sxs-lookup"><span data-stu-id="5acfa-113">Alpha</span></span>|<span data-ttu-id="5acfa-114">[4][3]</span><span class="sxs-lookup"><span data-stu-id="5acfa-114">[4][3]</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5acfa-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="5acfa-115">Example</span></span>  
 <span data-ttu-id="5acfa-116">Následující příklad vytvoří <xref:System.Drawing.Image> objekt ze souboru ColorBars.bmp.</span><span class="sxs-lookup"><span data-stu-id="5acfa-116">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars.bmp.</span></span> <span data-ttu-id="5acfa-117">Potom kód přidá 0,75 červené každý pixel na obrázku.</span><span class="sxs-lookup"><span data-stu-id="5acfa-117">Then the code adds 0.75 to the red component of each pixel in the image.</span></span> <span data-ttu-id="5acfa-118">Původní bitové kopie nakreslen spolu s transformovaný bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="5acfa-118">The original image is drawn alongside the transformed image.</span></span>  
  
 <span data-ttu-id="5acfa-119">Následující obrázek znázorňuje původní obrázek na levé straně a transformovaná image na pravé straně:</span><span class="sxs-lookup"><span data-stu-id="5acfa-119">The following illustration shows the original image on the left and the transformed image on the right:</span></span>  
  
 ![Snímek obrazovky s původní a transformovaná image.](./media/how-to-translate-image-colors/original-image-translate-colors.png)  
  
 <span data-ttu-id="5acfa-121">Následující tabulka uvádí vektory barvu pro čtyři pruhy před a po červenou překladu.</span><span class="sxs-lookup"><span data-stu-id="5acfa-121">The following table lists the color vectors for the four bars before and after the red translation.</span></span> <span data-ttu-id="5acfa-122">Mějte na paměti, protože maximální hodnota složky barvy je 1, červené ve druhém řádku nezmění.</span><span class="sxs-lookup"><span data-stu-id="5acfa-122">Note that because the maximum value for a color component is 1, the red component in the second row does not change.</span></span> <span data-ttu-id="5acfa-123">(Podobně, minimální hodnota složky barvy je 0.)</span><span class="sxs-lookup"><span data-stu-id="5acfa-123">(Similarly, the minimum value for a color component is 0.)</span></span>  
  
|<span data-ttu-id="5acfa-124">Původní</span><span class="sxs-lookup"><span data-stu-id="5acfa-124">Original</span></span>|<span data-ttu-id="5acfa-125">Přeložit</span><span class="sxs-lookup"><span data-stu-id="5acfa-125">Translated</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="5acfa-126">Černé (0, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="5acfa-126">Black (0, 0, 0, 1)</span></span>|<span data-ttu-id="5acfa-127">(0.75, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="5acfa-127">(0.75, 0, 0, 1)</span></span>|  
|<span data-ttu-id="5acfa-128">Červená (1, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="5acfa-128">Red (1, 0, 0, 1)</span></span>|<span data-ttu-id="5acfa-129">(1, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="5acfa-129">(1, 0, 0, 1)</span></span>|  
|<span data-ttu-id="5acfa-130">Zelená (0, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="5acfa-130">Green (0, 1, 0, 1)</span></span>|<span data-ttu-id="5acfa-131">(0.75, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="5acfa-131">(0.75, 1, 0, 1)</span></span>|  
|<span data-ttu-id="5acfa-132">Modré (0, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="5acfa-132">Blue (0, 0, 1, 1)</span></span>|<span data-ttu-id="5acfa-133">(0.75, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="5acfa-133">(0.75, 0, 1, 1)</span></span>|  
  
 [!code-csharp[System.Drawing.RecoloringImages#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.RecoloringImages#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5acfa-134">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="5acfa-134">Compiling the Code</span></span>  
 <span data-ttu-id="5acfa-135">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs>`e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="5acfa-135">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="5acfa-136">Nahraďte `ColorBars.bmp` název souboru bitové kopie a cestu, která jsou platné ve vašem systému.</span><span class="sxs-lookup"><span data-stu-id="5acfa-136">Replace `ColorBars.bmp` with an image file name and path that are valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5acfa-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5acfa-137">See also</span></span>

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="5acfa-138">Grafika a kreslení v rozhraní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5acfa-138">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="5acfa-139">Přebarvení obrázků</span><span class="sxs-lookup"><span data-stu-id="5acfa-139">Recoloring Images</span></span>](recoloring-images.md)
