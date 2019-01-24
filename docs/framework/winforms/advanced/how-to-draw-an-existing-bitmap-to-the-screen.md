---
title: 'Postupy: Nakreslení existujícího rastrového obrázku na obrazovku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [Windows Forms], displaying in Windows Forms
- bitmaps [Windows Forms], loading in Windows Forms applications
- images [Windows Forms], displaying on Windows Forms
ms.assetid: 5bc558d7-b326-4050-a834-b8600da0de95
ms.openlocfilehash: d8c118d9561c0fe993228cb6bd8cebcd156d411d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54586719"
---
# <a name="how-to-draw-an-existing-bitmap-to-the-screen"></a><span data-ttu-id="4b67e-102">Postupy: Nakreslení existujícího rastrového obrázku na obrazovku</span><span class="sxs-lookup"><span data-stu-id="4b67e-102">How to: Draw an Existing Bitmap to the Screen</span></span>
<span data-ttu-id="4b67e-103">Snadno můžete nakreslit stávající bitovou kopii na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="4b67e-103">You can easily draw an existing image on the screen.</span></span> <span data-ttu-id="4b67e-104">Nejdřív je potřeba vytvořit <xref:System.Drawing.Bitmap> objektu pomocí konstruktoru rastrový obrázek, který vezme název souboru, <xref:System.Drawing.Bitmap.%23ctor%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="4b67e-104">First you need to create a <xref:System.Drawing.Bitmap> object by using the bitmap constructor that takes a file name, <xref:System.Drawing.Bitmap.%23ctor%28System.String%29>.</span></span> <span data-ttu-id="4b67e-105">Tento konstruktor přijímá imagí v několika různých formátech, včetně BMP, GIF, JPEG, PNG a TIFF.</span><span class="sxs-lookup"><span data-stu-id="4b67e-105">This constructor accepts images with several different file formats, including BMP, GIF, JPEG, PNG, and TIFF.</span></span> <span data-ttu-id="4b67e-106">Po vytvoření <xref:System.Drawing.Bitmap> objektu, který předat <xref:System.Drawing.Bitmap> objektu <xref:System.Drawing.Graphics.DrawImage%2A> metodu <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="4b67e-106">After you have created the <xref:System.Drawing.Bitmap> object, pass that <xref:System.Drawing.Bitmap> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b67e-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b67e-107">Example</span></span>  
 <span data-ttu-id="4b67e-108">Tento příklad vytvoří <xref:System.Drawing.Bitmap> objekt ze souboru JPEG a pak vykreslí pomocí jeho levého horního rohu na (60, 10).</span><span class="sxs-lookup"><span data-stu-id="4b67e-108">This example creates a <xref:System.Drawing.Bitmap> object from a JPEG file and then draws the bitmap with its upper-left corner at (60, 10).</span></span>  
  
 <span data-ttu-id="4b67e-109">Následující obrázek znázorňuje rastrového obrázku vykreslena v zadaném umístění.</span><span class="sxs-lookup"><span data-stu-id="4b67e-109">The following illustration shows the bitmap drawn at the specified location.</span></span>  
  
 <span data-ttu-id="4b67e-110">![Obrázek pozice](../../../../docs/framework/winforms/advanced/media/csimageposition1.png "csimageposition1")</span><span class="sxs-lookup"><span data-stu-id="4b67e-110">![Image Position](../../../../docs/framework/winforms/advanced/media/csimageposition1.png "csimageposition1")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.WorkingWithImages#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4b67e-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="4b67e-111">Compiling the Code</span></span>  
 <span data-ttu-id="4b67e-112">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="4b67e-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b67e-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4b67e-113">See also</span></span>
- [<span data-ttu-id="4b67e-114">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4b67e-114">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="4b67e-115">Práce s obrázky, rastrovými obrázky, ikonami a metasoubory</span><span class="sxs-lookup"><span data-stu-id="4b67e-115">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
