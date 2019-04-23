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
ms.openlocfilehash: 90511adf9caffe7952e270d6fe32dd85162a29d7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089163"
---
# <a name="how-to-draw-an-existing-bitmap-to-the-screen"></a><span data-ttu-id="61857-102">Postupy: Nakreslení existujícího rastrového obrázku na obrazovku</span><span class="sxs-lookup"><span data-stu-id="61857-102">How to: Draw an Existing Bitmap to the Screen</span></span>
<span data-ttu-id="61857-103">Snadno můžete nakreslit stávající bitovou kopii na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="61857-103">You can easily draw an existing image on the screen.</span></span> <span data-ttu-id="61857-104">Nejdřív je potřeba vytvořit <xref:System.Drawing.Bitmap> objektu pomocí konstruktoru rastrový obrázek, který vezme název souboru, <xref:System.Drawing.Bitmap.%23ctor%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="61857-104">First you need to create a <xref:System.Drawing.Bitmap> object by using the bitmap constructor that takes a file name, <xref:System.Drawing.Bitmap.%23ctor%28System.String%29>.</span></span> <span data-ttu-id="61857-105">Tento konstruktor přijímá imagí v několika různých formátech, včetně BMP, GIF, JPEG, PNG a TIFF.</span><span class="sxs-lookup"><span data-stu-id="61857-105">This constructor accepts images with several different file formats, including BMP, GIF, JPEG, PNG, and TIFF.</span></span> <span data-ttu-id="61857-106">Po vytvoření <xref:System.Drawing.Bitmap> objektu, který předat <xref:System.Drawing.Bitmap> objektu <xref:System.Drawing.Graphics.DrawImage%2A> metodu <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="61857-106">After you have created the <xref:System.Drawing.Bitmap> object, pass that <xref:System.Drawing.Bitmap> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61857-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="61857-107">Example</span></span>  
 <span data-ttu-id="61857-108">Tento příklad vytvoří <xref:System.Drawing.Bitmap> objekt ze souboru JPEG a pak vykreslí pomocí jeho levého horního rohu na (60, 10).</span><span class="sxs-lookup"><span data-stu-id="61857-108">This example creates a <xref:System.Drawing.Bitmap> object from a JPEG file and then draws the bitmap with its upper-left corner at (60, 10).</span></span>  
  
 <span data-ttu-id="61857-109">Následující obrázek znázorňuje rastrového obrázku vykreslena v zadaném umístění:</span><span class="sxs-lookup"><span data-stu-id="61857-109">The following illustration shows the bitmap drawn at the specified location:</span></span>  
  
 ![Snímek obrazovky zobrazující image na určené pozici.](./media/how-to-draw-an-existing-bitmap-to-the-screen/bitmap-specified-position.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.WorkingWithImages#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="61857-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="61857-111">Compiling the Code</span></span>  
 <span data-ttu-id="61857-112">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="61857-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61857-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="61857-113">See also</span></span>

- [<span data-ttu-id="61857-114">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="61857-114">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="61857-115">Práce s obrázky, rastrovými obrázky, ikonami a metasoubory</span><span class="sxs-lookup"><span data-stu-id="61857-115">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
