---
title: 'Postupy: Použití matice barev k nastavení alfa hodnot v obrázcích'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], using color matrices for semi-transparent
- transparency [Windows Forms], color matrices
- matrices [Windows Forms], alpha values
- bitmaps [Windows Forms], using color matrices for semi-transparent
ms.assetid: a27121e6-f7e9-4c09-84e2-f05aa9d2a1bb
ms.openlocfilehash: 73e820845d040856a0ae367da8b9371ad6afa142
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423739"
---
# <a name="how-to-use-a-color-matrix-to-set-alpha-values-in-images"></a><span data-ttu-id="9dc7a-102">Postupy: Použití matice barev k nastavení alfa hodnot v obrázcích</span><span class="sxs-lookup"><span data-stu-id="9dc7a-102">How to: Use a Color Matrix to Set Alpha Values in Images</span></span>
<span data-ttu-id="9dc7a-103">Třída <xref:System.Drawing.Bitmap> (která dědí z třídy <xref:System.Drawing.Image>) a třída <xref:System.Drawing.Imaging.ImageAttributes> poskytují funkce pro získávání a nastavování hodnot pixelů.</span><span class="sxs-lookup"><span data-stu-id="9dc7a-103">The <xref:System.Drawing.Bitmap> class (which inherits from the <xref:System.Drawing.Image> class) and the <xref:System.Drawing.Imaging.ImageAttributes> class provide functionality for getting and setting pixel values.</span></span> <span data-ttu-id="9dc7a-104">Třídu <xref:System.Drawing.Imaging.ImageAttributes> lze použít k úpravě hodnot alfa pro celý obrázek, nebo můžete zavolat metodu <xref:System.Drawing.Bitmap.SetPixel%2A> třídy <xref:System.Drawing.Bitmap> pro úpravu jednotlivých hodnot pixelů.</span><span class="sxs-lookup"><span data-stu-id="9dc7a-104">You can use the <xref:System.Drawing.Imaging.ImageAttributes> class to modify the alpha values for an entire image, or you can call the <xref:System.Drawing.Bitmap.SetPixel%2A> method of the <xref:System.Drawing.Bitmap> class to modify individual pixel values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9dc7a-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="9dc7a-105">Example</span></span>  
 <span data-ttu-id="9dc7a-106">Třída <xref:System.Drawing.Imaging.ImageAttributes> má mnoho vlastností, které lze použít k úpravě obrázků během vykreslování.</span><span class="sxs-lookup"><span data-stu-id="9dc7a-106">The <xref:System.Drawing.Imaging.ImageAttributes> class has many properties that you can use to modify images during rendering.</span></span> <span data-ttu-id="9dc7a-107">V následujícím příkladu se <xref:System.Drawing.Imaging.ImageAttributes> objekt používá k nastavení všech hodnot Alpha na 80 procent z toho, co byly.</span><span class="sxs-lookup"><span data-stu-id="9dc7a-107">In the following example, an <xref:System.Drawing.Imaging.ImageAttributes> object is used to set all the alpha values to 80 percent of what they were.</span></span> <span data-ttu-id="9dc7a-108">To se provádí inicializací barevné matice a nastavením hodnoty alfa škálování v matici na 0,8.</span><span class="sxs-lookup"><span data-stu-id="9dc7a-108">This is done by initializing a color matrix and setting the alpha scaling value in the matrix to 0.8.</span></span> <span data-ttu-id="9dc7a-109">Adresa matice barev je předána metodě <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> objektu <xref:System.Drawing.Imaging.ImageAttributes> a objekt <xref:System.Drawing.Imaging.ImageAttributes> je předán metodě <xref:System.Drawing.Graphics.DrawString%2A> objektu <xref:System.Drawing.Graphics>.</span><span class="sxs-lookup"><span data-stu-id="9dc7a-109">The address of the color matrix is passed to the <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> method of the <xref:System.Drawing.Imaging.ImageAttributes> object, and the <xref:System.Drawing.Imaging.ImageAttributes> object is passed to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> object.</span></span>  
  
 <span data-ttu-id="9dc7a-110">Při vykreslování se hodnoty alfa v bitmapě převedou na 80 procent z toho, co byly.</span><span class="sxs-lookup"><span data-stu-id="9dc7a-110">During rendering, the alpha values in the bitmap are converted to 80 percent of what they were.</span></span> <span data-ttu-id="9dc7a-111">Výsledkem je obrázek, který je Blendem na pozadí.</span><span class="sxs-lookup"><span data-stu-id="9dc7a-111">This results in an image that is blended with the background.</span></span> <span data-ttu-id="9dc7a-112">Jak ukazuje následující obrázek, rastrový obrázek vypadá transparentně. můžete vidět plnou černou čáru.</span><span class="sxs-lookup"><span data-stu-id="9dc7a-112">As the following illustration shows, the bitmap image looks transparent; you can see the solid black line through it.</span></span>  
  
 <span data-ttu-id="9dc7a-113">![Snímek obrazovky s alfa prolnutím s použitím matice](./media/how-to-use-a-color-matrix-to-set-alpha-values-in-images/alpha-blending-matrix.png "Obrázek 2")</span><span class="sxs-lookup"><span data-stu-id="9dc7a-113">![Screenshot of alpha blending using a matrix.](./media/how-to-use-a-color-matrix-to-set-alpha-values-in-images/alpha-blending-matrix.png "image2")</span></span>  
  
 <span data-ttu-id="9dc7a-114">V případě, že se obrázek nachází v bílé části pozadí, obrázek byl smíchán s barvou bílá.</span><span class="sxs-lookup"><span data-stu-id="9dc7a-114">Where the image is over the white portion of the background, the image has been blended with the color white.</span></span> <span data-ttu-id="9dc7a-115">V případě, že obrázek překračuje černou čáru, je obrázek smíchán barvou černou.</span><span class="sxs-lookup"><span data-stu-id="9dc7a-115">Where the image crosses the black line, the image is blended with the color black.</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9dc7a-116">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="9dc7a-116">Compiling the Code</span></span>  
 <span data-ttu-id="9dc7a-117">Předchozí příklad je navržen pro použití s model Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="9dc7a-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dc7a-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9dc7a-118">See also</span></span>

- [<span data-ttu-id="9dc7a-119">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9dc7a-119">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="9dc7a-120">Alfa míchání čar a výplní</span><span class="sxs-lookup"><span data-stu-id="9dc7a-120">Alpha Blending Lines and Fills</span></span>](alpha-blending-lines-and-fills.md)
