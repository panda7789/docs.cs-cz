---
title: 'Postupy: Použití tabulky přemapování barev'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- color tables [Windows Forms], remapping colors with
- custom colors [Windows Forms], creating with color remap table
- color remap tables [Windows Forms], using
ms.assetid: 977df1ce-8665-42d4-9fb1-ef7f0ff63419
ms.openlocfilehash: 619eee8e5c08d24f2c7c485dfdc43331f5d64e9f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080056"
---
# <a name="how-to-use-a-color-remap-table"></a><span data-ttu-id="11b4b-102">Postupy: Použití tabulky přemapování barev</span><span class="sxs-lookup"><span data-stu-id="11b4b-102">How to: Use a Color Remap Table</span></span>
<span data-ttu-id="11b4b-103">Přemapování je proces převodu barvy v bitovou kopii podle tabulky přemapování barev.</span><span class="sxs-lookup"><span data-stu-id="11b4b-103">Remapping is the process of converting the colors in an image according to a color remap table.</span></span> <span data-ttu-id="11b4b-104">Tabulky přemapování barev je pole <xref:System.Drawing.Imaging.ColorMap> objekty.</span><span class="sxs-lookup"><span data-stu-id="11b4b-104">The color remap table is an array of <xref:System.Drawing.Imaging.ColorMap> objects.</span></span> <span data-ttu-id="11b4b-105">Každý <xref:System.Drawing.Imaging.ColorMap> objekt pole má <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> vlastnost a <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="11b4b-105">Each <xref:System.Drawing.Imaging.ColorMap> object in the array has an <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> property and a <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> property.</span></span>  
  
 <span data-ttu-id="11b4b-106">Když [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] nakreslí obrázek, každý pixel na obrázku je ve srovnání s poli staré barvy.</span><span class="sxs-lookup"><span data-stu-id="11b4b-106">When [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] draws an image, each pixel of the image is compared to the array of old colors.</span></span> <span data-ttu-id="11b4b-107">Pokud jeden bod barva odpovídá stará barva, jeho barva se změní na odpovídající novou barvu.</span><span class="sxs-lookup"><span data-stu-id="11b4b-107">If a pixel's color matches an old color, its color is changed to the corresponding new color.</span></span> <span data-ttu-id="11b4b-108">Barvy se změní pouze pro vykreslování – hodnoty barev samotné (uložené v <xref:System.Drawing.Image> nebo <xref:System.Drawing.Bitmap> objektu) se nezmění.</span><span class="sxs-lookup"><span data-stu-id="11b4b-108">The colors are changed only for rendering — the color values of the image itself (stored in an <xref:System.Drawing.Image> or <xref:System.Drawing.Bitmap> object) are not changed.</span></span>  
  
 <span data-ttu-id="11b4b-109">Chcete-li nakreslit změnu mapování bitové kopie, inicializovat pole <xref:System.Drawing.Imaging.ColorMap> objekty.</span><span class="sxs-lookup"><span data-stu-id="11b4b-109">To draw a remapped image, initialize an array of <xref:System.Drawing.Imaging.ColorMap> objects.</span></span> <span data-ttu-id="11b4b-110">Předejte toto pole na <xref:System.Drawing.Imaging.ImageAttributes.SetRemapTable%2A> metodu <xref:System.Drawing.Imaging.ImageAttributes> objektu a pak předejte <xref:System.Drawing.Imaging.ImageAttributes> objektu <xref:System.Drawing.Graphics.DrawImage%2A> metodu <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="11b4b-110">Pass that array to the <xref:System.Drawing.Imaging.ImageAttributes.SetRemapTable%2A> method of an <xref:System.Drawing.Imaging.ImageAttributes> object, and then pass the <xref:System.Drawing.Imaging.ImageAttributes> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11b4b-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="11b4b-111">Example</span></span>  
 <span data-ttu-id="11b4b-112">Následující příklad vytvoří <xref:System.Drawing.Image> objekt ze souboru RemapInput.bmp.</span><span class="sxs-lookup"><span data-stu-id="11b4b-112">The following example creates an <xref:System.Drawing.Image> object from the file RemapInput.bmp.</span></span> <span data-ttu-id="11b4b-113">Vytvoří kód, který se skládá z jedné tabulky přemapování barev <xref:System.Drawing.Imaging.ColorMap> objektu.</span><span class="sxs-lookup"><span data-stu-id="11b4b-113">The code creates a color remap table that consists of a single <xref:System.Drawing.Imaging.ColorMap> object.</span></span> <span data-ttu-id="11b4b-114"><xref:System.Drawing.Imaging.ColorMap.OldColor%2A> Vlastnost `ColorRemap` červená, je objekt a <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> vlastnost je modrá.</span><span class="sxs-lookup"><span data-stu-id="11b4b-114">The <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> property of the `ColorRemap` object is red, and the <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> property is blue.</span></span> <span data-ttu-id="11b4b-115">Na obrázku je bez přemapování vykresleného jednou a jednou pro přemapování.</span><span class="sxs-lookup"><span data-stu-id="11b4b-115">The image is drawn once without remapping and once with remapping.</span></span> <span data-ttu-id="11b4b-116">Přemapování proces pouze změní všechny red pixelů na modrou.</span><span class="sxs-lookup"><span data-stu-id="11b4b-116">The remapping process changes all the red pixels to blue.</span></span>  
  
 <span data-ttu-id="11b4b-117">Následující obrázek znázorňuje původní obrázek na levé straně a změnu mapování image na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="11b4b-117">The following illustration shows the original image on the left and the remapped image on the right.</span></span>  
  
 ![Snímek obrazovky zobrazující původní bitové kopie a změnu mapování bitové kopie.](./media/how-to-use-a-color-remap-table/original-image-remap-colors.png)  
  
 [!code-csharp[System.Drawing.RecoloringImages#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.RecoloringImages#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="11b4b-119">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="11b4b-119">Compiling the Code</span></span>  
 <span data-ttu-id="11b4b-120">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="11b4b-120">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11b4b-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="11b4b-121">See also</span></span>

- [<span data-ttu-id="11b4b-122">Přebarvení obrázků</span><span class="sxs-lookup"><span data-stu-id="11b4b-122">Recoloring Images</span></span>](recoloring-images.md)
- [<span data-ttu-id="11b4b-123">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="11b4b-123">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
