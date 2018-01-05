---
title: "Postupy: Vyplnění obrazce pomocí textury"
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
- images [Windows Forms], using with brushes
- bitmaps [Windows Forms], using texture
- shapes [Windows Forms], filling with images
ms.assetid: 508da5a6-2433-4d2b-9680-eaeae4e96e3b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7b5ef87762b08daa973237e7b3da1068640e08bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-fill-a-shape-with-an-image-texture"></a><span data-ttu-id="463fd-102">Postupy: Vyplnění obrazce pomocí textury</span><span class="sxs-lookup"><span data-stu-id="463fd-102">How to: Fill a Shape with an Image Texture</span></span>
<span data-ttu-id="463fd-103">Můžete vyplnit uzavřený obrazec texturou pomocí <xref:System.Drawing.Image> třídy a <xref:System.Drawing.TextureBrush> třídy.</span><span class="sxs-lookup"><span data-stu-id="463fd-103">You can fill a closed shape with a texture by using the <xref:System.Drawing.Image> class and the <xref:System.Drawing.TextureBrush> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="463fd-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="463fd-104">Example</span></span>  
 <span data-ttu-id="463fd-105">Následující příklad doplní elipsy s bitovou kopií.</span><span class="sxs-lookup"><span data-stu-id="463fd-105">The following example fills an ellipse with an image.</span></span> <span data-ttu-id="463fd-106">Kód vytvoří <xref:System.Drawing.Image> objektu a pak předá adresu této <xref:System.Drawing.Image> jako argument pro objekt <xref:System.Drawing.TextureBrush.%23ctor%2A> konstruktor.</span><span class="sxs-lookup"><span data-stu-id="463fd-106">The code constructs an <xref:System.Drawing.Image> object, and then passes the address of that <xref:System.Drawing.Image> object as an argument to a <xref:System.Drawing.TextureBrush.%23ctor%2A> constructor.</span></span> <span data-ttu-id="463fd-107">Třetí příkaz škáluje bitovou kopii a čtvrtý příkaz výplní se třemi tečkami s opakovaných kopie škálovat bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="463fd-107">The third statement scales the image, and the fourth statement fills the ellipse with repeated copies of the scaled image.</span></span>  
  
 <span data-ttu-id="463fd-108">V následujícím kódu <xref:System.Drawing.TextureBrush.Transform%2A> vlastnost obsahuje transformace, která je použita pro obrázek předtím, než se nevykreslí.</span><span class="sxs-lookup"><span data-stu-id="463fd-108">In the following code, the <xref:System.Drawing.TextureBrush.Transform%2A> property contains the transformation that is applied to the image before it is drawn.</span></span> <span data-ttu-id="463fd-109">Předpokládejme, že původní bitové kopie má 640 pixelů šířka a výška 480 pixelů.</span><span class="sxs-lookup"><span data-stu-id="463fd-109">Assume that the original image has a width of 640 pixels and a height of 480 pixels.</span></span> <span data-ttu-id="463fd-110">Transformovat zmenší bitovou kopii na 75 × 75 nastavením hodnoty vodorovného a svislého škálování.</span><span class="sxs-lookup"><span data-stu-id="463fd-110">The transform shrinks the image to 75×75 by setting the horizontal and vertical scaling values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="463fd-111">V následujícím příkladu velikost image je 75 × 75 a velikost elipsy je 150 × 250.</span><span class="sxs-lookup"><span data-stu-id="463fd-111">In the following example, the image size is 75×75, and the ellipse size is 150×250.</span></span> <span data-ttu-id="463fd-112">Vzhledem k tomu, že bitová kopie je menší, než se třemi tečkami, které je naplnění, se třemi tečkami je rozložen formou dlaždic s bitovou kopií.</span><span class="sxs-lookup"><span data-stu-id="463fd-112">Because the image is smaller than the ellipse it is filling, the ellipse is tiled with the image.</span></span> <span data-ttu-id="463fd-113">Je dosaženo dlaždice znamená, že obrázek se opakuje vodorovně a svisle dokud hranice tvaru.</span><span class="sxs-lookup"><span data-stu-id="463fd-113">Tiling means that the image is repeated horizontally and vertically until the boundary of the shape is reached.</span></span> <span data-ttu-id="463fd-114">Další informace o dlaždice najdete v tématu [postupy: dlaždicové vyplnění obrazce pomocí obrázku](../../../../docs/framework/winforms/advanced/how-to-tile-a-shape-with-an-image.md).</span><span class="sxs-lookup"><span data-stu-id="463fd-114">For more information about tiling, see [How to: Tile a Shape with an Image](../../../../docs/framework/winforms/advanced/how-to-tile-a-shape-with-an-image.md).</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="463fd-115">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="463fd-115">Compiling the Code</span></span>  
 <span data-ttu-id="463fd-116">V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="463fd-116">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="463fd-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="463fd-117">See Also</span></span>  
 [<span data-ttu-id="463fd-118">Použití štětce k vyplnění obrazců</span><span class="sxs-lookup"><span data-stu-id="463fd-118">Using a Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
