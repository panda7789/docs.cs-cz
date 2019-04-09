---
title: 'Postupy: Oříznutí a změna měřítka obrázků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], cropping
- images [Windows Forms], scaling
ms.assetid: 053e3360-bca0-4b25-9afa-0e77a6f17b03
ms.openlocfilehash: 4257431881565f9160f45795111d374cc680dedd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189882"
---
# <a name="how-to-crop-and-scale-images"></a><span data-ttu-id="ffe89-102">Postupy: Oříznutí a změna měřítka obrázků</span><span class="sxs-lookup"><span data-stu-id="ffe89-102">How to: Crop and Scale Images</span></span>
<span data-ttu-id="ffe89-103"><xref:System.Drawing.Graphics> Třída poskytuje několik <xref:System.Drawing.Graphics.DrawImage%2A> metody, některé z nich mají zdrojové a cílové parametry obdélníku, které slouží k oříznutí a změna měřítka obrázků.</span><span class="sxs-lookup"><span data-stu-id="ffe89-103">The <xref:System.Drawing.Graphics> class provides several <xref:System.Drawing.Graphics.DrawImage%2A> methods, some of which have source and destination rectangle parameters that you can use to crop and scale images.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ffe89-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="ffe89-104">Example</span></span>  
 <span data-ttu-id="ffe89-105">Následující příklad vytvoří <xref:System.Drawing.Image> objekt ze souboru na disku Apple.gif.</span><span class="sxs-lookup"><span data-stu-id="ffe89-105">The following example constructs an <xref:System.Drawing.Image> object from the disk file Apple.gif.</span></span> <span data-ttu-id="ffe89-106">Kód v původní velikost nakreslí obrázek celý apple.</span><span class="sxs-lookup"><span data-stu-id="ffe89-106">The code draws the entire apple image in its original size.</span></span> <span data-ttu-id="ffe89-107">Kód poté volá <xref:System.Drawing.Graphics.DrawImage%2A> metodu <xref:System.Drawing.Graphics> objektů pro kreslení část obrázku apple v cílového obdélníku, který je větší než původní obrázek apple.</span><span class="sxs-lookup"><span data-stu-id="ffe89-107">The code then calls the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object to draw a portion of the apple image in a destination rectangle that is larger than the original apple image.</span></span>  
  
 <span data-ttu-id="ffe89-108"><xref:System.Drawing.Graphics.DrawImage%2A> Metoda určuje, jaká část apple k vykreslení zobrazením zdrojového obdélníku, který je určený třetí, čtvrtý, pátý a šestý argument.</span><span class="sxs-lookup"><span data-stu-id="ffe89-108">The <xref:System.Drawing.Graphics.DrawImage%2A> method determines which portion of the apple to draw by looking at the source rectangle, which is specified by the third, fourth, fifth, and sixth arguments.</span></span> <span data-ttu-id="ffe89-109">V takovém případě je apple ořízne na 75 procent šířku a výšku 75 procent.</span><span class="sxs-lookup"><span data-stu-id="ffe89-109">In this case, the apple is cropped to 75 percent of its width and 75 percent of its height.</span></span>  
  
 <span data-ttu-id="ffe89-110"><xref:System.Drawing.Graphics.DrawImage%2A> Metoda určuje, kde stanovit oříznutý apple a jak velký aby oříznutý apple zobrazením cílového obdélníku, který je zadaný v druhém argumentu.</span><span class="sxs-lookup"><span data-stu-id="ffe89-110">The <xref:System.Drawing.Graphics.DrawImage%2A> method determines where to draw the cropped apple and how big to make the cropped apple by looking at the destination rectangle, which is specified by the second argument.</span></span> <span data-ttu-id="ffe89-111">V tomto případě cílového obdélníku je 30 procent širší a vyšší než původní obrázek 30 procent.</span><span class="sxs-lookup"><span data-stu-id="ffe89-111">In this case, the destination rectangle is 30 percent wider and 30 percent taller than the original image.</span></span>  
  
 <span data-ttu-id="ffe89-112">Následující obrázek znázorňuje původní apple a škálovanou, oříznuté apple.</span><span class="sxs-lookup"><span data-stu-id="ffe89-112">The following illustration shows the original apple and the scaled, cropped apple.</span></span>  
  
 ![Snímek obrazovky s původní bitové kopie a stejnou bitovou kopii oříznuté.](./media/how-to-crop-and-scale-images/original-image-cropped-image.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.WorkingWithImages#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ffe89-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ffe89-114">Compiling the Code</span></span>  
 <span data-ttu-id="ffe89-115">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="ffe89-115">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="ffe89-116">Nezapomeňte nahradit `Apple.gif` název souboru bitové kopie a cestu, která jsou platné ve vašem systému.</span><span class="sxs-lookup"><span data-stu-id="ffe89-116">Make sure to replace `Apple.gif` with an image file name and path that are valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffe89-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ffe89-117">See also</span></span>

- [<span data-ttu-id="ffe89-118">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="ffe89-118">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="ffe89-119">Práce s obrázky, rastrovými obrázky, ikonami a metasoubory</span><span class="sxs-lookup"><span data-stu-id="ffe89-119">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
