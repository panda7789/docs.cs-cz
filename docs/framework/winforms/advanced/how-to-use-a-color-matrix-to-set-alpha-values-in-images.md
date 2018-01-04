---
title: "Postupy: Použití matice barev k nastavení alfa hodnot v obrázcích"
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
- images [Windows Forms], using color matrices for semi-transparent
- transparency [Windows Forms], color matrices
- matrices [Windows Forms], alpha values
- bitmaps [Windows Forms], using color matrices for semi-transparent
ms.assetid: a27121e6-f7e9-4c09-84e2-f05aa9d2a1bb
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5dde9417782e4404237a995364d65058f023c3e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-color-matrix-to-set-alpha-values-in-images"></a><span data-ttu-id="d6953-102">Postupy: Použití matice barev k nastavení alfa hodnot v obrázcích</span><span class="sxs-lookup"><span data-stu-id="d6953-102">How to: Use a Color Matrix to Set Alpha Values in Images</span></span>
<span data-ttu-id="d6953-103"><xref:System.Drawing.Bitmap> – Třída (který dědí z <xref:System.Drawing.Image> třída) a <xref:System.Drawing.Imaging.ImageAttributes> třída poskytovat funkce pro načtení a nastavení hodnoty pixelů.</span><span class="sxs-lookup"><span data-stu-id="d6953-103">The <xref:System.Drawing.Bitmap> class (which inherits from the <xref:System.Drawing.Image> class) and the <xref:System.Drawing.Imaging.ImageAttributes> class provide functionality for getting and setting pixel values.</span></span> <span data-ttu-id="d6953-104">Můžete použít <xref:System.Drawing.Imaging.ImageAttributes> třída změnit alpha hodnoty celého obrázku, nebo můžete volat <xref:System.Drawing.Bitmap.SetPixel%2A> metodu <xref:System.Drawing.Bitmap> třídy upravte hodnoty jednotlivých pixelů.</span><span class="sxs-lookup"><span data-stu-id="d6953-104">You can use the <xref:System.Drawing.Imaging.ImageAttributes> class to modify the alpha values for an entire image, or you can call the <xref:System.Drawing.Bitmap.SetPixel%2A> method of the <xref:System.Drawing.Bitmap> class to modify individual pixel values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6953-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6953-105">Example</span></span>  
 <span data-ttu-id="d6953-106"><xref:System.Drawing.Imaging.ImageAttributes> Třída má mnoho vlastností, které můžete použít k úpravě bitové kopie během vykreslování.</span><span class="sxs-lookup"><span data-stu-id="d6953-106">The <xref:System.Drawing.Imaging.ImageAttributes> class has many properties that you can use to modify images during rendering.</span></span> <span data-ttu-id="d6953-107">V následujícím příkladu se <xref:System.Drawing.Imaging.ImageAttributes> objekt se používá k nastavení alfa hodnot až 80 procent jaké byly.</span><span class="sxs-lookup"><span data-stu-id="d6953-107">In the following example, an <xref:System.Drawing.Imaging.ImageAttributes> object is used to set all the alpha values to 80 percent of what they were.</span></span> <span data-ttu-id="d6953-108">To se provádí inicializace matice barev a nastavit alpha hodnotu v matici 0,8 změny velikosti.</span><span class="sxs-lookup"><span data-stu-id="d6953-108">This is done by initializing a color matrix and setting the alpha scaling value in the matrix to 0.8.</span></span> <span data-ttu-id="d6953-109">Je předán na adresu matice barev <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> metodu <xref:System.Drawing.Imaging.ImageAttributes> objekt a <xref:System.Drawing.Imaging.ImageAttributes> je předán objekt <xref:System.Drawing.Graphics.DrawString%2A> metodu <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="d6953-109">The address of the color matrix is passed to the <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> method of the <xref:System.Drawing.Imaging.ImageAttributes> object, and the <xref:System.Drawing.Imaging.ImageAttributes> object is passed to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> object.</span></span>  
  
 <span data-ttu-id="d6953-110">Při vykreslování, jsou až 80 procent jaké byly převést alfa hodnot v souboru bitové mapy.</span><span class="sxs-lookup"><span data-stu-id="d6953-110">During rendering, the alpha values in the bitmap are converted to 80 percent of what they were.</span></span> <span data-ttu-id="d6953-111">Výsledkem je obrázek, který je smíšený s na pozadí.</span><span class="sxs-lookup"><span data-stu-id="d6953-111">This results in an image that is blended with the background.</span></span> <span data-ttu-id="d6953-112">Jak ukazuje následující obrázek, rastrový obrázek vypadá transparentní; můžete zobrazit plná černá čára přes něj.</span><span class="sxs-lookup"><span data-stu-id="d6953-112">As the following illustration shows, the bitmap image looks transparent; you can see the solid black line through it.</span></span>  
  
 <span data-ttu-id="d6953-113">![Alfa míchání pomocí matice](../../../../docs/framework/winforms/advanced/media/image2.png "obrázek 2")</span><span class="sxs-lookup"><span data-stu-id="d6953-113">![Alpha Blending Using a Matrix](../../../../docs/framework/winforms/advanced/media/image2.png "image2")</span></span>  
  
 <span data-ttu-id="d6953-114">Kde je bitová kopie je přes části bílé pozadí, má byla smíšené bitovou kopii s bílé barvy.</span><span class="sxs-lookup"><span data-stu-id="d6953-114">Where the image is over the white portion of the background, the image has been blended with the color white.</span></span> <span data-ttu-id="d6953-115">Kde bitovou kopii protne černá čára bitovou kopii je smíšený s černé barvy.</span><span class="sxs-lookup"><span data-stu-id="d6953-115">Where the image crosses the black line, the image is blended with the color black.</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d6953-116">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="d6953-116">Compiling the Code</span></span>  
 <span data-ttu-id="d6953-117">V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="d6953-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6953-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6953-118">See Also</span></span>  
 [<span data-ttu-id="d6953-119">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d6953-119">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="d6953-120">Alfa míchání čar a výplní</span><span class="sxs-lookup"><span data-stu-id="d6953-120">Alpha Blending Lines and Fills</span></span>](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)
