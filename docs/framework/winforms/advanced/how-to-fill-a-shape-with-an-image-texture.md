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
ms.openlocfilehash: 42c456137f84c6fa657ba5a09727eae052a45376
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911679"
---
# <a name="how-to-fill-a-shape-with-an-image-texture"></a><span data-ttu-id="a17ee-102">Postupy: Vyplnění obrazce pomocí textury</span><span class="sxs-lookup"><span data-stu-id="a17ee-102">How to: Fill a Shape with an Image Texture</span></span>
<span data-ttu-id="a17ee-103">Uzavřený tvar můžete vyplnit texturou pomocí <xref:System.Drawing.Image> třídy <xref:System.Drawing.TextureBrush> a třídy.</span><span class="sxs-lookup"><span data-stu-id="a17ee-103">You can fill a closed shape with a texture by using the <xref:System.Drawing.Image> class and the <xref:System.Drawing.TextureBrush> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a17ee-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a17ee-104">Example</span></span>  
 <span data-ttu-id="a17ee-105">Následující příklad vyplní elipsu obrázkem.</span><span class="sxs-lookup"><span data-stu-id="a17ee-105">The following example fills an ellipse with an image.</span></span> <span data-ttu-id="a17ee-106">Kód vytvoří <xref:System.Drawing.Image> objekt a poté předá adresu <xref:System.Drawing.Image> tohoto objektu <xref:System.Drawing.TextureBrush.%23ctor%2A> jako argument konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="a17ee-106">The code constructs an <xref:System.Drawing.Image> object, and then passes the address of that <xref:System.Drawing.Image> object as an argument to a <xref:System.Drawing.TextureBrush.%23ctor%2A> constructor.</span></span> <span data-ttu-id="a17ee-107">Třetí příkaz škáluje obrázek a čtvrtý příkaz vyplní elipsu opakovanými kopiemi obrázku s měřítkem.</span><span class="sxs-lookup"><span data-stu-id="a17ee-107">The third statement scales the image, and the fourth statement fills the ellipse with repeated copies of the scaled image.</span></span>  
  
 <span data-ttu-id="a17ee-108">V následujícím kódu <xref:System.Drawing.TextureBrush.Transform%2A> vlastnost obsahuje transformaci, která je použita na obrázek před vykreslením.</span><span class="sxs-lookup"><span data-stu-id="a17ee-108">In the following code, the <xref:System.Drawing.TextureBrush.Transform%2A> property contains the transformation that is applied to the image before it is drawn.</span></span> <span data-ttu-id="a17ee-109">Předpokládat, že původní obrázek má šířku 640 pixelů a výšku 480 pixelů.</span><span class="sxs-lookup"><span data-stu-id="a17ee-109">Assume that the original image has a width of 640 pixels and a height of 480 pixels.</span></span> <span data-ttu-id="a17ee-110">Transformace zmenší obrázek na 75 × 75 nastavením hodnot horizontálního a svislého měřítka.</span><span class="sxs-lookup"><span data-stu-id="a17ee-110">The transform shrinks the image to 75×75 by setting the horizontal and vertical scaling values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a17ee-111">V následujícím příkladu je velikost obrázku 75 × 75 a velikost elipsy je 150 × 250.</span><span class="sxs-lookup"><span data-stu-id="a17ee-111">In the following example, the image size is 75×75, and the ellipse size is 150×250.</span></span> <span data-ttu-id="a17ee-112">Vzhledem k tomu, že je obrázek menší než elipsa, která je vyplňuje, je elipsa v dlaždici s obrázkem.</span><span class="sxs-lookup"><span data-stu-id="a17ee-112">Because the image is smaller than the ellipse it is filling, the ellipse is tiled with the image.</span></span> <span data-ttu-id="a17ee-113">Dláždění znamená, že se obrázek opakuje vodorovně a svisle, dokud nedosáhne hranice tvaru.</span><span class="sxs-lookup"><span data-stu-id="a17ee-113">Tiling means that the image is repeated horizontally and vertically until the boundary of the shape is reached.</span></span> <span data-ttu-id="a17ee-114">Další informace o dlaždicích naleznete v [tématu How to: Dlaždici tvar s obrázkem](how-to-tile-a-shape-with-an-image.md)</span><span class="sxs-lookup"><span data-stu-id="a17ee-114">For more information about tiling, see [How to: Tile a Shape with an Image](how-to-tile-a-shape-with-an-image.md).</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a17ee-115">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="a17ee-115">Compiling the Code</span></span>  
 <span data-ttu-id="a17ee-116">Předchozí příklad je navržen pro použití s model Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což <xref:System.Windows.Forms.Control.Paint> je parametr obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="a17ee-116">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a17ee-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a17ee-117">See also</span></span>

- [<span data-ttu-id="a17ee-118">Použití štětce k vyplnění obrazců</span><span class="sxs-lookup"><span data-stu-id="a17ee-118">Using a Brush to Fill Shapes</span></span>](using-a-brush-to-fill-shapes.md)
