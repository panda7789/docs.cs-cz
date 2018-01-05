---
title: "Postupy: Oříznutí a změna měřítka obrázků"
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
- images [Windows Forms], cropping
- images [Windows Forms], scaling
ms.assetid: 053e3360-bca0-4b25-9afa-0e77a6f17b03
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: de905cf70013098a4282e3f4af092ccbea16ccfd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-crop-and-scale-images"></a><span data-ttu-id="a4016-102">Postupy: Oříznutí a změna měřítka obrázků</span><span class="sxs-lookup"><span data-stu-id="a4016-102">How to: Crop and Scale Images</span></span>
<span data-ttu-id="a4016-103"><xref:System.Drawing.Graphics> Třída poskytuje několik <xref:System.Drawing.Graphics.DrawImage%2A> metody, některé z nich musí mít zdrojové a cílové parametry obdélníku, které můžete použít k oříznutí a škálování bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="a4016-103">The <xref:System.Drawing.Graphics> class provides several <xref:System.Drawing.Graphics.DrawImage%2A> methods, some of which have source and destination rectangle parameters that you can use to crop and scale images.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4016-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a4016-104">Example</span></span>  
 <span data-ttu-id="a4016-105">Následující příklad vytvoří <xref:System.Drawing.Image> objektu ze souboru disku Apple.gif.</span><span class="sxs-lookup"><span data-stu-id="a4016-105">The following example constructs an <xref:System.Drawing.Image> object from the disk file Apple.gif.</span></span> <span data-ttu-id="a4016-106">Kód nakreslí obrázek celý apple v původní velikost.</span><span class="sxs-lookup"><span data-stu-id="a4016-106">The code draws the entire apple image in its original size.</span></span> <span data-ttu-id="a4016-107">Kód pak zavolá <xref:System.Drawing.Graphics.DrawImage%2A> metodu <xref:System.Drawing.Graphics> objektu k vykreslení část apple bitové kopie v cílovém obdélníku, která je větší než původní bitové kopie apple.</span><span class="sxs-lookup"><span data-stu-id="a4016-107">The code then calls the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object to draw a portion of the apple image in a destination rectangle that is larger than the original apple image.</span></span>  
  
 <span data-ttu-id="a4016-108"><xref:System.Drawing.Graphics.DrawImage%2A> Metoda určuje, jaká část apple kreslení prohlížením rámeček zdroj, který je určený třetí, čtvrté, páté a šesté argumenty.</span><span class="sxs-lookup"><span data-stu-id="a4016-108">The <xref:System.Drawing.Graphics.DrawImage%2A> method determines which portion of the apple to draw by looking at the source rectangle, which is specified by the third, fourth, fifth, and sixth arguments.</span></span> <span data-ttu-id="a4016-109">V takovém případě apple oříznuty na 75 procent svou šířku a výšku 75 procent.</span><span class="sxs-lookup"><span data-stu-id="a4016-109">In this case, the apple is cropped to 75 percent of its width and 75 percent of its height.</span></span>  
  
 <span data-ttu-id="a4016-110"><xref:System.Drawing.Graphics.DrawImage%2A> Metoda určuje, kde k vykreslení oříznutý apple a jak velký aby oříznutý apple pohledem na cílovém obdélníku, který je určeného druhý argument.</span><span class="sxs-lookup"><span data-stu-id="a4016-110">The <xref:System.Drawing.Graphics.DrawImage%2A> method determines where to draw the cropped apple and how big to make the cropped apple by looking at the destination rectangle, which is specified by the second argument.</span></span> <span data-ttu-id="a4016-111">V takovém případě cílového rámeček je 30 procent širší a 30 procent vyšší než původní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="a4016-111">In this case, the destination rectangle is 30 percent wider and 30 percent taller than the original image.</span></span>  
  
 <span data-ttu-id="a4016-112">Následující obrázek znázorňuje původní apple a škálovat, oříznout apple.</span><span class="sxs-lookup"><span data-stu-id="a4016-112">The following illustration shows the original apple and the scaled, cropped apple.</span></span>  
  
 <span data-ttu-id="a4016-113">![Oříznutí a změna velikosti](../../../../docs/framework/winforms/advanced/media/cscropscale1.png "csCropScale1")</span><span class="sxs-lookup"><span data-stu-id="a4016-113">![Crop & Scale](../../../../docs/framework/winforms/advanced/media/cscropscale1.png "csCropScale1")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a4016-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="a4016-114">Compiling the Code</span></span>  
 <span data-ttu-id="a4016-115">V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="a4016-115">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="a4016-116">Nezapomeňte nahradit `Apple.gif` s název souboru obrázku a cestu, která jsou platné ve vašem systému.</span><span class="sxs-lookup"><span data-stu-id="a4016-116">Make sure to replace `Apple.gif` with an image file name and path that are valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4016-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4016-117">See Also</span></span>  
 [<span data-ttu-id="a4016-118">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="a4016-118">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="a4016-119">Práce s obrázky, rastrovými obrázky, ikonami a metasoubory</span><span class="sxs-lookup"><span data-stu-id="a4016-119">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
