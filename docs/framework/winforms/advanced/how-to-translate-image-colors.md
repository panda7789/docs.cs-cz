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
ms.openlocfilehash: 48f506f76ff6e9ca648822d073b6f6a852b9ca8e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522533"
---
# <a name="how-to-translate-image-colors"></a><span data-ttu-id="f2a39-102">Postupy: Překlad barev obrázků</span><span class="sxs-lookup"><span data-stu-id="f2a39-102">How to: Translate Image Colors</span></span>
<span data-ttu-id="f2a39-103">Překlad přidá hodnotu na jeden nebo více součástí čtyři barev.</span><span class="sxs-lookup"><span data-stu-id="f2a39-103">A translation adds a value to one or more of the four color components.</span></span> <span data-ttu-id="f2a39-104">V následující tabulce jsou uvedeny položek matice barev, které představují překladů.</span><span class="sxs-lookup"><span data-stu-id="f2a39-104">The color matrix entries that represent translations are given in the following table.</span></span>  
  
|<span data-ttu-id="f2a39-105">Součásti, které mají být převedeny</span><span class="sxs-lookup"><span data-stu-id="f2a39-105">Component to be translated</span></span>|<span data-ttu-id="f2a39-106">Položka matice</span><span class="sxs-lookup"><span data-stu-id="f2a39-106">Matrix entry</span></span>|  
|--------------------------------|------------------|  
|<span data-ttu-id="f2a39-107">červená</span><span class="sxs-lookup"><span data-stu-id="f2a39-107">Red</span></span>|<span data-ttu-id="f2a39-108">[4][0]</span><span class="sxs-lookup"><span data-stu-id="f2a39-108">[4][0]</span></span>|  
|<span data-ttu-id="f2a39-109">zelená</span><span class="sxs-lookup"><span data-stu-id="f2a39-109">Green</span></span>|<span data-ttu-id="f2a39-110">[4][1]</span><span class="sxs-lookup"><span data-stu-id="f2a39-110">[4][1]</span></span>|  
|<span data-ttu-id="f2a39-111">modrá</span><span class="sxs-lookup"><span data-stu-id="f2a39-111">Blue</span></span>|<span data-ttu-id="f2a39-112">[4][2]</span><span class="sxs-lookup"><span data-stu-id="f2a39-112">[4][2]</span></span>|  
|<span data-ttu-id="f2a39-113">Alpha</span><span class="sxs-lookup"><span data-stu-id="f2a39-113">Alpha</span></span>|<span data-ttu-id="f2a39-114">[4][3]</span><span class="sxs-lookup"><span data-stu-id="f2a39-114">[4][3]</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f2a39-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="f2a39-115">Example</span></span>  
 <span data-ttu-id="f2a39-116">Následující příklad vytvoří <xref:System.Drawing.Image> objektu ze souboru ColorBars.bmp.</span><span class="sxs-lookup"><span data-stu-id="f2a39-116">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars.bmp.</span></span> <span data-ttu-id="f2a39-117">Potom kód přidá 0,75 red součást každý pixelů v bitové kopii.</span><span class="sxs-lookup"><span data-stu-id="f2a39-117">Then the code adds 0.75 to the red component of each pixel in the image.</span></span> <span data-ttu-id="f2a39-118">Původní bitové kopie vykreslením spolu s transformovaných bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="f2a39-118">The original image is drawn alongside the transformed image.</span></span>  
  
 <span data-ttu-id="f2a39-119">Následující obrázek znázorňuje původní bitové kopie na levé straně a bitovou kopii transformovaných na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="f2a39-119">The following illustration shows the original image on the left and the transformed image on the right.</span></span>  
  
 <span data-ttu-id="f2a39-120">![Převede barvy](../../../../docs/framework/winforms/advanced/media/colortrans2.png "colortrans2")</span><span class="sxs-lookup"><span data-stu-id="f2a39-120">![Translate Colors](../../../../docs/framework/winforms/advanced/media/colortrans2.png "colortrans2")</span></span>  
  
 <span data-ttu-id="f2a39-121">Následující tabulka uvádí vektory barvu pro pruhy čtyři před a po red překlad.</span><span class="sxs-lookup"><span data-stu-id="f2a39-121">The following table lists the color vectors for the four bars before and after the red translation.</span></span> <span data-ttu-id="f2a39-122">Všimněte si, že vzhledem k tomu, že pro složku barvy maximální hodnota je 1, komponentu red ve druhém řádku nezmění.</span><span class="sxs-lookup"><span data-stu-id="f2a39-122">Note that because the maximum value for a color component is 1, the red component in the second row does not change.</span></span> <span data-ttu-id="f2a39-123">(Podobně, minimální hodnota pro součást barva je 0.)</span><span class="sxs-lookup"><span data-stu-id="f2a39-123">(Similarly, the minimum value for a color component is 0.)</span></span>  
  
|<span data-ttu-id="f2a39-124">Původní</span><span class="sxs-lookup"><span data-stu-id="f2a39-124">Original</span></span>|<span data-ttu-id="f2a39-125">Přeložit</span><span class="sxs-lookup"><span data-stu-id="f2a39-125">Translated</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="f2a39-126">Černé (0, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="f2a39-126">Black (0, 0, 0, 1)</span></span>|<span data-ttu-id="f2a39-127">(0.75, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="f2a39-127">(0.75, 0, 0, 1)</span></span>|  
|<span data-ttu-id="f2a39-128">Červený (1, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="f2a39-128">Red (1, 0, 0, 1)</span></span>|<span data-ttu-id="f2a39-129">(1, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="f2a39-129">(1, 0, 0, 1)</span></span>|  
|<span data-ttu-id="f2a39-130">Zelený (0, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="f2a39-130">Green (0, 1, 0, 1)</span></span>|<span data-ttu-id="f2a39-131">(0.75, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="f2a39-131">(0.75, 1, 0, 1)</span></span>|  
|<span data-ttu-id="f2a39-132">Modrá (0, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="f2a39-132">Blue (0, 0, 1, 1)</span></span>|<span data-ttu-id="f2a39-133">(0.75, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="f2a39-133">(0.75, 0, 1, 1)</span></span>|  
  
 [!code-csharp[System.Drawing.RecoloringImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.RecoloringImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f2a39-134">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f2a39-134">Compiling the Code</span></span>  
 <span data-ttu-id="f2a39-135">V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="f2a39-135">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="f2a39-136">Nahraďte `ColorBars.bmp` s název souboru obrázku a cestu, která jsou platné ve vašem systému.</span><span class="sxs-lookup"><span data-stu-id="f2a39-136">Replace `ColorBars.bmp` with an image file name and path that are valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2a39-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2a39-137">See Also</span></span>  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [<span data-ttu-id="f2a39-138">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f2a39-138">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="f2a39-139">Přebarvení obrázků</span><span class="sxs-lookup"><span data-stu-id="f2a39-139">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)
