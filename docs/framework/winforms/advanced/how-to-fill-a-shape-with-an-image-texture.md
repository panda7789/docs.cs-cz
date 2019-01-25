---
title: 'Postupy: Vyplnění obrazce pomocí textury'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], using with brushes
- bitmaps [Windows Forms], using texture
- shapes [Windows Forms], filling with images
ms.assetid: 508da5a6-2433-4d2b-9680-eaeae4e96e3b
ms.openlocfilehash: bf1e09548ff9bc4eb650048eb21a9c300f3f6405
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601776"
---
# <a name="how-to-fill-a-shape-with-an-image-texture"></a><span data-ttu-id="883c4-102">Postupy: Vyplnění obrazce pomocí textury</span><span class="sxs-lookup"><span data-stu-id="883c4-102">How to: Fill a Shape with an Image Texture</span></span>
<span data-ttu-id="883c4-103">Můžete vyplnit zavřeného tvaru textury s použitím <xref:System.Drawing.Image> třídy a <xref:System.Drawing.TextureBrush> třídy.</span><span class="sxs-lookup"><span data-stu-id="883c4-103">You can fill a closed shape with a texture by using the <xref:System.Drawing.Image> class and the <xref:System.Drawing.TextureBrush> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="883c4-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="883c4-104">Example</span></span>  
 <span data-ttu-id="883c4-105">Následující příklad zkopíruje elipsu s obrázkem.</span><span class="sxs-lookup"><span data-stu-id="883c4-105">The following example fills an ellipse with an image.</span></span> <span data-ttu-id="883c4-106">Vytvoří kód <xref:System.Drawing.Image> objektu a předá adresu, která <xref:System.Drawing.Image> jako argument pro objekt <xref:System.Drawing.TextureBrush.%23ctor%2A> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="883c4-106">The code constructs an <xref:System.Drawing.Image> object, and then passes the address of that <xref:System.Drawing.Image> object as an argument to a <xref:System.Drawing.TextureBrush.%23ctor%2A> constructor.</span></span> <span data-ttu-id="883c4-107">Třetí příkaz změní velikost obrázku, a čtvrtý příkaz vyplní elipsu s opakovaného kopírování obrazu se změněnou velikostí.</span><span class="sxs-lookup"><span data-stu-id="883c4-107">The third statement scales the image, and the fourth statement fills the ellipse with repeated copies of the scaled image.</span></span>  
  
 <span data-ttu-id="883c4-108">V následujícím kódu <xref:System.Drawing.TextureBrush.Transform%2A> vlastnost obsahuje transformace, která je u obrázku před jeho vykreslení.</span><span class="sxs-lookup"><span data-stu-id="883c4-108">In the following code, the <xref:System.Drawing.TextureBrush.Transform%2A> property contains the transformation that is applied to the image before it is drawn.</span></span> <span data-ttu-id="883c4-109">Předpokládejme, že původní obrázek obsahuje 640 pixelů šířku a výšku 480 pixelů.</span><span class="sxs-lookup"><span data-stu-id="883c4-109">Assume that the original image has a width of 640 pixels and a height of 480 pixels.</span></span> <span data-ttu-id="883c4-110">Transformace zmenší bitovou kopii na 75 × 75 nastavením hodnoty vodorovného a svislého škálování.</span><span class="sxs-lookup"><span data-stu-id="883c4-110">The transform shrinks the image to 75×75 by setting the horizontal and vertical scaling values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="883c4-111">V následujícím příkladu velikost obrázku je 75 × 75 a velikosti elipsy je 150 × 250.</span><span class="sxs-lookup"><span data-stu-id="883c4-111">In the following example, the image size is 75×75, and the ellipse size is 150×250.</span></span> <span data-ttu-id="883c4-112">Vzhledem k tomu, že na obrázku je menší než elipsy, který je naplnění, se třemi tečkami je rozložen formou dlaždic s imagí.</span><span class="sxs-lookup"><span data-stu-id="883c4-112">Because the image is smaller than the ellipse it is filling, the ellipse is tiled with the image.</span></span> <span data-ttu-id="883c4-113">Dělení na bloky znamená, že obrázek se opakuje vodorovně a svisle do hranice obrazce je dosaženo.</span><span class="sxs-lookup"><span data-stu-id="883c4-113">Tiling means that the image is repeated horizontally and vertically until the boundary of the shape is reached.</span></span> <span data-ttu-id="883c4-114">Další informace o dělení najdete v tématu [jak: Dlaždicové vyplnění obrazce pomocí obrázku](../../../../docs/framework/winforms/advanced/how-to-tile-a-shape-with-an-image.md).</span><span class="sxs-lookup"><span data-stu-id="883c4-114">For more information about tiling, see [How to: Tile a Shape with an Image](../../../../docs/framework/winforms/advanced/how-to-tile-a-shape-with-an-image.md).</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="883c4-115">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="883c4-115">Compiling the Code</span></span>  
 <span data-ttu-id="883c4-116">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="883c4-116">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="883c4-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="883c4-117">See also</span></span>
- [<span data-ttu-id="883c4-118">Použití štětce k vyplnění obrazců</span><span class="sxs-lookup"><span data-stu-id="883c4-118">Using a Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
