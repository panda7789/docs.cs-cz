---
title: 'Postupy: Načtení a zobrazení metasouborů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], metafiles
- metafiles [Windows Forms], displaying
ms.assetid: 60af1714-f148-4d85-a739-0557965ffa73
ms.openlocfilehash: d0835d7f2c5ffea44f22661a765ab16b1d0130c5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54619555"
---
# <a name="how-to-load-and-display-metafiles"></a><span data-ttu-id="891ca-102">Postupy: Načtení a zobrazení metasouborů</span><span class="sxs-lookup"><span data-stu-id="891ca-102">How to: Load and Display Metafiles</span></span>
<span data-ttu-id="891ca-103"><xref:System.Drawing.Imaging.Metafile> Třída, která dědí z <xref:System.Drawing.Image> třídy, poskytuje metody pro nahrávání, zobrazování a zkoumání vektorové obrázky.</span><span class="sxs-lookup"><span data-stu-id="891ca-103">The <xref:System.Drawing.Imaging.Metafile> class, which inherits from the <xref:System.Drawing.Image> class, provides methods for recording, displaying, and examining vector images.</span></span>  
  
## <a name="example"></a><span data-ttu-id="891ca-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="891ca-104">Example</span></span>  
 <span data-ttu-id="891ca-105">K zobrazení bitovou kopii vektoru (metafile) na obrazovce, je nutné <xref:System.Drawing.Imaging.Metafile> objektu a <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="891ca-105">To display a vector image (metafile) on the screen, you need a <xref:System.Drawing.Imaging.Metafile> object and a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="891ca-106">Předat název souboru (nebo datový proud) <xref:System.Drawing.Imaging.Metafile> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="891ca-106">Pass the name of a file (or a stream) to a <xref:System.Drawing.Imaging.Metafile> constructor.</span></span> <span data-ttu-id="891ca-107">Po vytvoření <xref:System.Drawing.Imaging.Metafile> objektu, který předat <xref:System.Drawing.Imaging.Metafile> objektu <xref:System.Drawing.Graphics.DrawImage%2A> metodu <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="891ca-107">After you have created a <xref:System.Drawing.Imaging.Metafile> object, pass that <xref:System.Drawing.Imaging.Metafile> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 <span data-ttu-id="891ca-108">V příkladu se vytvoří <xref:System.Drawing.Imaging.Metafile> objekt ze souboru EMF (rozšířený metasoubor) a potom nakreslí obrázek s jeho levého horního rohu na (60, 10).</span><span class="sxs-lookup"><span data-stu-id="891ca-108">The example creates a <xref:System.Drawing.Imaging.Metafile> object from an EMF (enhanced metafile) file and then draws the image with its upper-left corner at (60, 10).</span></span>  
  
 <span data-ttu-id="891ca-109">Následující obrázek znázorňuje tento metasoubor vykreslen v zadaném umístění.</span><span class="sxs-lookup"><span data-stu-id="891ca-109">The following illustration shows the metafile drawn at the specified location.</span></span>  
  
 <span data-ttu-id="891ca-110">![Obrázek pozice](../../../../docs/framework/winforms/advanced/media/imageposition2.png "imageposition2")</span><span class="sxs-lookup"><span data-stu-id="891ca-110">![Image Position](../../../../docs/framework/winforms/advanced/media/imageposition2.png "imageposition2")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="891ca-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="891ca-111">Compiling the Code</span></span>  
 <span data-ttu-id="891ca-112">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="891ca-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="891ca-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="891ca-113">See also</span></span>
- [<span data-ttu-id="891ca-114">Práce s obrázky, rastrovými obrázky, ikonami a metasoubory</span><span class="sxs-lookup"><span data-stu-id="891ca-114">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
