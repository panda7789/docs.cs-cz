---
title: "Postupy: Zkosení barev"
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
- colors [Windows Forms], transforming with color matrices
- colors [Windows Forms], shearing
ms.assetid: 0a424171-5b8b-45c4-afef-e9720a6c3e22
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 35f89bb5d87ef58c5ecda7be4cb9fb41da08e8a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-shear-colors"></a><span data-ttu-id="1b081-102">Postupy: Zkosení barev</span><span class="sxs-lookup"><span data-stu-id="1b081-102">How to: Shear Colors</span></span>
<span data-ttu-id="1b081-103">Zkosení zvyšuje nebo snižuje komponentu Barva o částku úměrná jiné barevnou složku.</span><span class="sxs-lookup"><span data-stu-id="1b081-103">Shearing increases or decreases a color component by an amount proportional to another color component.</span></span> <span data-ttu-id="1b081-104">Představte si třeba transformaci, kde komponentu red vzroste polovina hodnotou modré součásti.</span><span class="sxs-lookup"><span data-stu-id="1b081-104">For example, consider the transformation where the red component is increased by one half the value of the blue component.</span></span> <span data-ttu-id="1b081-105">V části transformace by stát barvu (0,2, 0,5, 1) (0,7, 0,5, 1).</span><span class="sxs-lookup"><span data-stu-id="1b081-105">Under such a transformation, the color (0.2, 0.5, 1) would become (0.7, 0.5, 1).</span></span> <span data-ttu-id="1b081-106">Novou red součást je 0,2 + (1/2)(1) = 0,7.</span><span class="sxs-lookup"><span data-stu-id="1b081-106">The new red component is 0.2 + (1/2)(1) = 0.7.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b081-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="1b081-107">Example</span></span>  
 <span data-ttu-id="1b081-108">Následující příklad vytvoří <xref:System.Drawing.Image> objektu ze souboru ColorBars4.bmp.</span><span class="sxs-lookup"><span data-stu-id="1b081-108">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars4.bmp.</span></span> <span data-ttu-id="1b081-109">Kód pak použije transformaci zkosení popsané v předchozím odstavci pro každý pixelů v bitové kopii.</span><span class="sxs-lookup"><span data-stu-id="1b081-109">Then the code applies the shearing transformation described in the preceding paragraph to each pixel in the image.</span></span>  
  
 <span data-ttu-id="1b081-110">Následující obrázek znázorňuje původní bitové kopie na levé straně a bitovou kopii ořezanými na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="1b081-110">The following illustration shows the original image on the left and the sheared image on the right.</span></span>  
  
 <span data-ttu-id="1b081-111">![Zkosení barev](../../../../docs/framework/winforms/advanced/media/colortrans6.png "colortrans6")</span><span class="sxs-lookup"><span data-stu-id="1b081-111">![Shear Colors](../../../../docs/framework/winforms/advanced/media/colortrans6.png "colortrans6")</span></span>  
  
 <span data-ttu-id="1b081-112">Následující tabulka uvádí vektory barvu pro pruhy čtyři před a po transformaci zkosení.</span><span class="sxs-lookup"><span data-stu-id="1b081-112">The following table lists the color vectors for the four bars before and after the shearing transformation.</span></span>  
  
|<span data-ttu-id="1b081-113">Původní</span><span class="sxs-lookup"><span data-stu-id="1b081-113">Original</span></span>|<span data-ttu-id="1b081-114">Zrcadlili</span><span class="sxs-lookup"><span data-stu-id="1b081-114">Sheared</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="1b081-115">(0, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="1b081-115">(0, 0, 1, 1)</span></span>|<span data-ttu-id="1b081-116">(0.5, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="1b081-116">(0.5, 0, 1, 1)</span></span>|  
|<span data-ttu-id="1b081-117">(0.5, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="1b081-117">(0.5, 1, 0.5, 1)</span></span>|<span data-ttu-id="1b081-118">(0.75, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="1b081-118">(0.75, 1, 0.5, 1)</span></span>|  
|<span data-ttu-id="1b081-119">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="1b081-119">(1, 1, 0, 1)</span></span>|<span data-ttu-id="1b081-120">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="1b081-120">(1, 1, 0, 1)</span></span>|  
|<span data-ttu-id="1b081-121">(0.4, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="1b081-121">(0.4, 0.4, 0.4, 1)</span></span>|<span data-ttu-id="1b081-122">(0.6, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="1b081-122">(0.6, 0.4, 0.4, 1)</span></span>|  
  
 [!code-csharp[System.Drawing.Misc3#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1b081-123">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="1b081-123">Compiling the Code</span></span>  
 <span data-ttu-id="1b081-124">V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="1b081-124">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="1b081-125">Nahraďte `ColorBars.bmp` s název bitové kopie a cesta platné ve vašem systému.</span><span class="sxs-lookup"><span data-stu-id="1b081-125">Replace `ColorBars.bmp` with an image name and path valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b081-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b081-126">See Also</span></span>  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [<span data-ttu-id="1b081-127">Grafika a kreslení v systému Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1b081-127">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="1b081-128">Přebarvení obrázků</span><span class="sxs-lookup"><span data-stu-id="1b081-128">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)
