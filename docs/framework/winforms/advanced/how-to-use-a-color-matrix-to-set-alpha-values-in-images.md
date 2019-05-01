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
ms.openlocfilehash: 79937f0801a790d4ff1ab327aaaf45ef1b881827
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954534"
---
# <a name="how-to-use-a-color-matrix-to-set-alpha-values-in-images"></a><span data-ttu-id="544b3-102">Postupy: Použití matice barev k nastavení alfa hodnot v obrázcích</span><span class="sxs-lookup"><span data-stu-id="544b3-102">How to: Use a Color Matrix to Set Alpha Values in Images</span></span>
<span data-ttu-id="544b3-103"><xref:System.Drawing.Bitmap> Třídy (který dědí z <xref:System.Drawing.Image> třídy) a <xref:System.Drawing.Imaging.ImageAttributes> třídy poskytují funkce pro získání a nastavení hodnoty pixelů.</span><span class="sxs-lookup"><span data-stu-id="544b3-103">The <xref:System.Drawing.Bitmap> class (which inherits from the <xref:System.Drawing.Image> class) and the <xref:System.Drawing.Imaging.ImageAttributes> class provide functionality for getting and setting pixel values.</span></span> <span data-ttu-id="544b3-104">Můžete použít <xref:System.Drawing.Imaging.ImageAttributes> třídy k úpravě alfa hodnoty celého obrázku, nebo můžete volat <xref:System.Drawing.Bitmap.SetPixel%2A> metodu <xref:System.Drawing.Bitmap> třídy k úpravě jednotlivých obrazových bodů.</span><span class="sxs-lookup"><span data-stu-id="544b3-104">You can use the <xref:System.Drawing.Imaging.ImageAttributes> class to modify the alpha values for an entire image, or you can call the <xref:System.Drawing.Bitmap.SetPixel%2A> method of the <xref:System.Drawing.Bitmap> class to modify individual pixel values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="544b3-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="544b3-105">Example</span></span>  
 <span data-ttu-id="544b3-106"><xref:System.Drawing.Imaging.ImageAttributes> Třída má mnoho vlastností, které vám umožní upravit obrázky při vykreslování.</span><span class="sxs-lookup"><span data-stu-id="544b3-106">The <xref:System.Drawing.Imaging.ImageAttributes> class has many properties that you can use to modify images during rendering.</span></span> <span data-ttu-id="544b3-107">V následujícím příkladu <xref:System.Drawing.Imaging.ImageAttributes> objektu se používá k nastavení alfa hodnot až 80 procent, co bylo.</span><span class="sxs-lookup"><span data-stu-id="544b3-107">In the following example, an <xref:System.Drawing.Imaging.ImageAttributes> object is used to set all the alpha values to 80 percent of what they were.</span></span> <span data-ttu-id="544b3-108">To se provádí inicializace matice barev a alfa škálování hodnoty v matici 0,8 nastavením.</span><span class="sxs-lookup"><span data-stu-id="544b3-108">This is done by initializing a color matrix and setting the alpha scaling value in the matrix to 0.8.</span></span> <span data-ttu-id="544b3-109">Adresa matice barev je předána <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> metodu <xref:System.Drawing.Imaging.ImageAttributes> objektu a <xref:System.Drawing.Imaging.ImageAttributes> objekt je předán do <xref:System.Drawing.Graphics.DrawString%2A> metodu <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="544b3-109">The address of the color matrix is passed to the <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> method of the <xref:System.Drawing.Imaging.ImageAttributes> object, and the <xref:System.Drawing.Imaging.ImageAttributes> object is passed to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> object.</span></span>  
  
 <span data-ttu-id="544b3-110">Během vykreslování, jsou převedeny alfa hodnot rastrového obrázku nastaven na 80 procent, co bylo.</span><span class="sxs-lookup"><span data-stu-id="544b3-110">During rendering, the alpha values in the bitmap are converted to 80 percent of what they were.</span></span> <span data-ttu-id="544b3-111">Výsledkem je obrázek, který je v kombinaci s na pozadí.</span><span class="sxs-lookup"><span data-stu-id="544b3-111">This results in an image that is blended with the background.</span></span> <span data-ttu-id="544b3-112">Jak ukazuje následující obrázek, vypadá průhledné; rastrový obrázek Zobrazí se plná čára černé přes něj.</span><span class="sxs-lookup"><span data-stu-id="544b3-112">As the following illustration shows, the bitmap image looks transparent; you can see the solid black line through it.</span></span>  
  
 <span data-ttu-id="544b3-113">![Alfa míchání pomocí matice](./media/image2.png "obrazek2")</span><span class="sxs-lookup"><span data-stu-id="544b3-113">![Alpha Blending Using a Matrix](./media/image2.png "image2")</span></span>  
  
 <span data-ttu-id="544b3-114">Kde je bitová kopie je přes bílé části na pozadí, má byla image v kombinaci s bílou barvu.</span><span class="sxs-lookup"><span data-stu-id="544b3-114">Where the image is over the white portion of the background, the image has been blended with the color white.</span></span> <span data-ttu-id="544b3-115">Kde image protíná černá čára na obrázku je v kombinaci s černá barva.</span><span class="sxs-lookup"><span data-stu-id="544b3-115">Where the image crosses the black line, the image is blended with the color black.</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="544b3-116">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="544b3-116">Compiling the Code</span></span>  
 <span data-ttu-id="544b3-117">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="544b3-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="544b3-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="544b3-118">See also</span></span>

- [<span data-ttu-id="544b3-119">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="544b3-119">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="544b3-120">Alfa míchání čar a výplní</span><span class="sxs-lookup"><span data-stu-id="544b3-120">Alpha Blending Lines and Fills</span></span>](alpha-blending-lines-and-fills.md)
