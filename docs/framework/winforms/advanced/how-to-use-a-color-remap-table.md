---
title: "Postupy: Použití tabulky přemapování barev"
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
- color tables [Windows Forms], remapping colors with
- custom colors [Windows Forms], creating with color remap table
- color remap tables [Windows Forms], using
ms.assetid: 977df1ce-8665-42d4-9fb1-ef7f0ff63419
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1c4399e98504a675cfbf63462b8dc964c677488e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-color-remap-table"></a><span data-ttu-id="21190-102">Postupy: Použití tabulky přemapování barev</span><span class="sxs-lookup"><span data-stu-id="21190-102">How to: Use a Color Remap Table</span></span>
<span data-ttu-id="21190-103">Přemapování je proces převodu barev v obraze podle tabulky přemapování barev.</span><span class="sxs-lookup"><span data-stu-id="21190-103">Remapping is the process of converting the colors in an image according to a color remap table.</span></span> <span data-ttu-id="21190-104">Tabulky přemapování barev je pole <xref:System.Drawing.Imaging.ColorMap> objekty.</span><span class="sxs-lookup"><span data-stu-id="21190-104">The color remap table is an array of <xref:System.Drawing.Imaging.ColorMap> objects.</span></span> <span data-ttu-id="21190-105">Každý <xref:System.Drawing.Imaging.ColorMap> objekt v poli má <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> vlastnost a <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="21190-105">Each <xref:System.Drawing.Imaging.ColorMap> object in the array has an <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> property and a <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> property.</span></span>  
  
 <span data-ttu-id="21190-106">Když [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] nakreslí na bitovou kopii, každý pixelů bitové kopie se porovnává se pole staré barvy.</span><span class="sxs-lookup"><span data-stu-id="21190-106">When [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] draws an image, each pixel of the image is compared to the array of old colors.</span></span> <span data-ttu-id="21190-107">Pokud jeden bod barva odpovídá původní barvu, jeho barva se změní na barvu odpovídající nové.</span><span class="sxs-lookup"><span data-stu-id="21190-107">If a pixel's color matches an old color, its color is changed to the corresponding new color.</span></span> <span data-ttu-id="21190-108">Barvy došlo ke změně pouze pro vykreslování – hodnoty barev samotné bitové kopie (uložené v <xref:System.Drawing.Image> nebo <xref:System.Drawing.Bitmap> objektu), nebudou změněny.</span><span class="sxs-lookup"><span data-stu-id="21190-108">The colors are changed only for rendering — the color values of the image itself (stored in an <xref:System.Drawing.Image> or <xref:System.Drawing.Bitmap> object) are not changed.</span></span>  
  
 <span data-ttu-id="21190-109">Kreslení změnu mapování bitové kopie, inicializovat pole <xref:System.Drawing.Imaging.ColorMap> objekty.</span><span class="sxs-lookup"><span data-stu-id="21190-109">To draw a remapped image, initialize an array of <xref:System.Drawing.Imaging.ColorMap> objects.</span></span> <span data-ttu-id="21190-110">Předat do tohoto pole <xref:System.Drawing.Imaging.ImageAttributes.SetRemapTable%2A> metodu <xref:System.Drawing.Imaging.ImageAttributes> objektu a pak <xref:System.Drawing.Imaging.ImageAttributes> do objektu <xref:System.Drawing.Graphics.DrawImage%2A> metodu <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="21190-110">Pass that array to the <xref:System.Drawing.Imaging.ImageAttributes.SetRemapTable%2A> method of an <xref:System.Drawing.Imaging.ImageAttributes> object, and then pass the <xref:System.Drawing.Imaging.ImageAttributes> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21190-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="21190-111">Example</span></span>  
 <span data-ttu-id="21190-112">Následující příklad vytvoří <xref:System.Drawing.Image> objektu ze souboru RemapInput.bmp.</span><span class="sxs-lookup"><span data-stu-id="21190-112">The following example creates an <xref:System.Drawing.Image> object from the file RemapInput.bmp.</span></span> <span data-ttu-id="21190-113">Kód vytvoří tabulky přemapování barev, která se skládá z jedné <xref:System.Drawing.Imaging.ColorMap> objektu.</span><span class="sxs-lookup"><span data-stu-id="21190-113">The code creates a color remap table that consists of a single <xref:System.Drawing.Imaging.ColorMap> object.</span></span> <span data-ttu-id="21190-114"><xref:System.Drawing.Imaging.ColorMap.OldColor%2A> Vlastnost `ColorRemap` objekt je červená a <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> vlastnost je modrá.</span><span class="sxs-lookup"><span data-stu-id="21190-114">The <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> property of the `ColorRemap` object is red, and the <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> property is blue.</span></span> <span data-ttu-id="21190-115">Bitová kopie je vykresleného jednou bez přemapování a jednou pro přemapování.</span><span class="sxs-lookup"><span data-stu-id="21190-115">The image is drawn once without remapping and once with remapping.</span></span> <span data-ttu-id="21190-116">Procesu přemapování změní všechny red pixelů na modrou.</span><span class="sxs-lookup"><span data-stu-id="21190-116">The remapping process changes all the red pixels to blue.</span></span>  
  
 <span data-ttu-id="21190-117">Následující obrázek znázorňuje původní bitové kopie na levé straně a bitovou kopii změnu mapování na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="21190-117">The following illustration shows the original image on the left and the remapped image on the right.</span></span>  
  
 <span data-ttu-id="21190-118">![Barva přemapování](../../../../docs/framework/winforms/advanced/media/colortrans7.png "colortrans7")</span><span class="sxs-lookup"><span data-stu-id="21190-118">![Color ReMap](../../../../docs/framework/winforms/advanced/media/colortrans7.png "colortrans7")</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.RecoloringImages#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="21190-119">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="21190-119">Compiling the Code</span></span>  
 <span data-ttu-id="21190-120">V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="21190-120">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21190-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="21190-121">See Also</span></span>  
 [<span data-ttu-id="21190-122">Přebarvení obrázků</span><span class="sxs-lookup"><span data-stu-id="21190-122">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)  
 [<span data-ttu-id="21190-123">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="21190-123">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
