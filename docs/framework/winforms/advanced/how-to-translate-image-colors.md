---
title: "Postupy: Překlad barev obrázků"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [Windows Forms], changing colors
- images [Windows Forms], changing colors
- image colors [Windows Forms]
ms.assetid: 2106fb9a-4d60-4dcf-9220-9f189a6c4d19
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4c21d20b631d8e0cf68e370dd43b3f5e92144b09
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-translate-image-colors"></a><span data-ttu-id="fd174-102">Postupy: Překlad barev obrázků</span><span class="sxs-lookup"><span data-stu-id="fd174-102">How to: Translate Image Colors</span></span>
<span data-ttu-id="fd174-103">Překlad přidá hodnotu na jeden nebo více součástí čtyři barev.</span><span class="sxs-lookup"><span data-stu-id="fd174-103">A translation adds a value to one or more of the four color components.</span></span> <span data-ttu-id="fd174-104">V následující tabulce jsou uvedeny položek matice barev, které představují překladů.</span><span class="sxs-lookup"><span data-stu-id="fd174-104">The color matrix entries that represent translations are given in the following table.</span></span>  
  
|<span data-ttu-id="fd174-105">Součásti, které mají být převedeny</span><span class="sxs-lookup"><span data-stu-id="fd174-105">Component to be translated</span></span>|<span data-ttu-id="fd174-106">Položka matice</span><span class="sxs-lookup"><span data-stu-id="fd174-106">Matrix entry</span></span>|  
|--------------------------------|------------------|  
|<span data-ttu-id="fd174-107">červená</span><span class="sxs-lookup"><span data-stu-id="fd174-107">Red</span></span>|<span data-ttu-id="fd174-108">[4][0]</span><span class="sxs-lookup"><span data-stu-id="fd174-108">[4][0]</span></span>|  
|<span data-ttu-id="fd174-109">zelená</span><span class="sxs-lookup"><span data-stu-id="fd174-109">Green</span></span>|<span data-ttu-id="fd174-110">[4][1]</span><span class="sxs-lookup"><span data-stu-id="fd174-110">[4][1]</span></span>|  
|<span data-ttu-id="fd174-111">modrá</span><span class="sxs-lookup"><span data-stu-id="fd174-111">Blue</span></span>|<span data-ttu-id="fd174-112">[4][2]</span><span class="sxs-lookup"><span data-stu-id="fd174-112">[4][2]</span></span>|  
|<span data-ttu-id="fd174-113">Alpha</span><span class="sxs-lookup"><span data-stu-id="fd174-113">Alpha</span></span>|<span data-ttu-id="fd174-114">[4][3]</span><span class="sxs-lookup"><span data-stu-id="fd174-114">[4][3]</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fd174-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="fd174-115">Example</span></span>  
 <span data-ttu-id="fd174-116">Následující příklad vytvoří <xref:System.Drawing.Image> objektu ze souboru ColorBars.bmp.</span><span class="sxs-lookup"><span data-stu-id="fd174-116">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars.bmp.</span></span> <span data-ttu-id="fd174-117">Potom kód přidá 0,75 red součást každý pixelů v bitové kopii.</span><span class="sxs-lookup"><span data-stu-id="fd174-117">Then the code adds 0.75 to the red component of each pixel in the image.</span></span> <span data-ttu-id="fd174-118">Původní bitové kopie vykreslením spolu s transformovaných bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="fd174-118">The original image is drawn alongside the transformed image.</span></span>  
  
 <span data-ttu-id="fd174-119">Následující obrázek znázorňuje původní bitové kopie na levé straně a bitovou kopii transformovaných na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="fd174-119">The following illustration shows the original image on the left and the transformed image on the right.</span></span>  
  
 <span data-ttu-id="fd174-120">![Převede barvy](../../../../docs/framework/winforms/advanced/media/colortrans2.png "colortrans2")</span><span class="sxs-lookup"><span data-stu-id="fd174-120">![Translate Colors](../../../../docs/framework/winforms/advanced/media/colortrans2.png "colortrans2")</span></span>  
  
 <span data-ttu-id="fd174-121">Následující tabulka uvádí vektory barvu pro pruhy čtyři před a po red překlad.</span><span class="sxs-lookup"><span data-stu-id="fd174-121">The following table lists the color vectors for the four bars before and after the red translation.</span></span> <span data-ttu-id="fd174-122">Všimněte si, že vzhledem k tomu, že pro složku barvy maximální hodnota je 1, komponentu red ve druhém řádku nezmění.</span><span class="sxs-lookup"><span data-stu-id="fd174-122">Note that because the maximum value for a color component is 1, the red component in the second row does not change.</span></span> <span data-ttu-id="fd174-123">(Podobně, minimální hodnota pro součást barva je 0.)</span><span class="sxs-lookup"><span data-stu-id="fd174-123">(Similarly, the minimum value for a color component is 0.)</span></span>  
  
|<span data-ttu-id="fd174-124">Původní</span><span class="sxs-lookup"><span data-stu-id="fd174-124">Original</span></span>|<span data-ttu-id="fd174-125">Přeložit</span><span class="sxs-lookup"><span data-stu-id="fd174-125">Translated</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="fd174-126">Černé (0, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="fd174-126">Black (0, 0, 0, 1)</span></span>|<span data-ttu-id="fd174-127">(0.75, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="fd174-127">(0.75, 0, 0, 1)</span></span>|  
|<span data-ttu-id="fd174-128">Červený (1, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="fd174-128">Red (1, 0, 0, 1)</span></span>|<span data-ttu-id="fd174-129">(1, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="fd174-129">(1, 0, 0, 1)</span></span>|  
|<span data-ttu-id="fd174-130">Zelený (0, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="fd174-130">Green (0, 1, 0, 1)</span></span>|<span data-ttu-id="fd174-131">(0.75, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="fd174-131">(0.75, 1, 0, 1)</span></span>|  
|<span data-ttu-id="fd174-132">Modrá (0, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="fd174-132">Blue (0, 0, 1, 1)</span></span>|<span data-ttu-id="fd174-133">(0.75, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="fd174-133">(0.75, 0, 1, 1)</span></span>|  
  
 [!code-csharp[System.Drawing.RecoloringImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.RecoloringImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fd174-134">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="fd174-134">Compiling the Code</span></span>  
 <span data-ttu-id="fd174-135">V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="fd174-135">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="fd174-136">Nahraďte `ColorBars.bmp` s název souboru obrázku a cestu, která jsou platné ve vašem systému.</span><span class="sxs-lookup"><span data-stu-id="fd174-136">Replace `ColorBars.bmp` with an image file name and path that are valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd174-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="fd174-137">See Also</span></span>  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [<span data-ttu-id="fd174-138">Grafika a kreslení v systému Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fd174-138">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="fd174-139">Přebarvení obrázků</span><span class="sxs-lookup"><span data-stu-id="fd174-139">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)
