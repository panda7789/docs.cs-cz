---
title: 'Postupy: Translate Image Colors'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [Windows Forms], changing colors
- images [Windows Forms], changing colors
- image colors [Windows Forms]
ms.assetid: 2106fb9a-4d60-4dcf-9220-9f189a6c4d19
ms.openlocfilehash: 81aecddb28903649ff2d59e80fc90368df5e2db4
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703020"
---
# <a name="how-to-translate-image-colors"></a><span data-ttu-id="00695-102">Postupy: Translate Image Colors</span><span class="sxs-lookup"><span data-stu-id="00695-102">How to: Translate Image Colors</span></span>
<span data-ttu-id="00695-103">Překlad přidá hodnotu na jeden nebo více součástí čtyři barvy.</span><span class="sxs-lookup"><span data-stu-id="00695-103">A translation adds a value to one or more of the four color components.</span></span> <span data-ttu-id="00695-104">Matice položek barev, které představují překlady jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="00695-104">The color matrix entries that represent translations are given in the following table.</span></span>  
  
|<span data-ttu-id="00695-105">Součást, kterou přeložit</span><span class="sxs-lookup"><span data-stu-id="00695-105">Component to be translated</span></span>|<span data-ttu-id="00695-106">Přehled vstupu</span><span class="sxs-lookup"><span data-stu-id="00695-106">Matrix entry</span></span>|  
|--------------------------------|------------------|  
|<span data-ttu-id="00695-107">Červená</span><span class="sxs-lookup"><span data-stu-id="00695-107">Red</span></span>|<span data-ttu-id="00695-108">[4][0]</span><span class="sxs-lookup"><span data-stu-id="00695-108">[4][0]</span></span>|  
|<span data-ttu-id="00695-109">Zelená</span><span class="sxs-lookup"><span data-stu-id="00695-109">Green</span></span>|<span data-ttu-id="00695-110">[4][1]</span><span class="sxs-lookup"><span data-stu-id="00695-110">[4][1]</span></span>|  
|<span data-ttu-id="00695-111">Modrá</span><span class="sxs-lookup"><span data-stu-id="00695-111">Blue</span></span>|<span data-ttu-id="00695-112">[4][2]</span><span class="sxs-lookup"><span data-stu-id="00695-112">[4][2]</span></span>|  
|<span data-ttu-id="00695-113">Alpha</span><span class="sxs-lookup"><span data-stu-id="00695-113">Alpha</span></span>|<span data-ttu-id="00695-114">[4][3]</span><span class="sxs-lookup"><span data-stu-id="00695-114">[4][3]</span></span>|  
  
## <a name="example"></a><span data-ttu-id="00695-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="00695-115">Example</span></span>  
 <span data-ttu-id="00695-116">Následující příklad vytvoří <xref:System.Drawing.Image> objekt ze souboru ColorBars.bmp.</span><span class="sxs-lookup"><span data-stu-id="00695-116">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars.bmp.</span></span> <span data-ttu-id="00695-117">Potom kód přidá 0,75 červené každý pixel na obrázku.</span><span class="sxs-lookup"><span data-stu-id="00695-117">Then the code adds 0.75 to the red component of each pixel in the image.</span></span> <span data-ttu-id="00695-118">Původní bitové kopie nakreslen spolu s transformovaný bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="00695-118">The original image is drawn alongside the transformed image.</span></span>  
  
 <span data-ttu-id="00695-119">Následující obrázek znázorňuje původní obrázek na levé straně a transformovaná image na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="00695-119">The following illustration shows the original image on the left and the transformed image on the right.</span></span>  
  
 <span data-ttu-id="00695-120">![Translate Colors](./media/colortrans2.png "colortrans2")</span><span class="sxs-lookup"><span data-stu-id="00695-120">![Translate Colors](./media/colortrans2.png "colortrans2")</span></span>  
  
 <span data-ttu-id="00695-121">Následující tabulka uvádí vektory barvu pro čtyři pruhy před a po červenou překladu.</span><span class="sxs-lookup"><span data-stu-id="00695-121">The following table lists the color vectors for the four bars before and after the red translation.</span></span> <span data-ttu-id="00695-122">Mějte na paměti, protože maximální hodnota složky barvy je 1, červené ve druhém řádku nezmění.</span><span class="sxs-lookup"><span data-stu-id="00695-122">Note that because the maximum value for a color component is 1, the red component in the second row does not change.</span></span> <span data-ttu-id="00695-123">(Podobně, minimální hodnota složky barvy je 0.)</span><span class="sxs-lookup"><span data-stu-id="00695-123">(Similarly, the minimum value for a color component is 0.)</span></span>  
  
|<span data-ttu-id="00695-124">Původní</span><span class="sxs-lookup"><span data-stu-id="00695-124">Original</span></span>|<span data-ttu-id="00695-125">Přeložit</span><span class="sxs-lookup"><span data-stu-id="00695-125">Translated</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="00695-126">Černé (0, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="00695-126">Black (0, 0, 0, 1)</span></span>|<span data-ttu-id="00695-127">(0.75, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="00695-127">(0.75, 0, 0, 1)</span></span>|  
|<span data-ttu-id="00695-128">Červená (1, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="00695-128">Red (1, 0, 0, 1)</span></span>|<span data-ttu-id="00695-129">(1, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="00695-129">(1, 0, 0, 1)</span></span>|  
|<span data-ttu-id="00695-130">Zelená (0, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="00695-130">Green (0, 1, 0, 1)</span></span>|<span data-ttu-id="00695-131">(0.75, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="00695-131">(0.75, 1, 0, 1)</span></span>|  
|<span data-ttu-id="00695-132">Modré (0, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="00695-132">Blue (0, 0, 1, 1)</span></span>|<span data-ttu-id="00695-133">(0.75, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="00695-133">(0.75, 0, 1, 1)</span></span>|  
  
 [!code-csharp[System.Drawing.RecoloringImages#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.RecoloringImages#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="00695-134">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="00695-134">Compiling the Code</span></span>  
 <span data-ttu-id="00695-135">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="00695-135">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="00695-136">Nahraďte `ColorBars.bmp` název souboru bitové kopie a cestu, která jsou platné ve vašem systému.</span><span class="sxs-lookup"><span data-stu-id="00695-136">Replace `ColorBars.bmp` with an image file name and path that are valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00695-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="00695-137">See also</span></span>
- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="00695-138">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="00695-138">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="00695-139">Přebarvení obrázků</span><span class="sxs-lookup"><span data-stu-id="00695-139">Recoloring Images</span></span>](recoloring-images.md)
