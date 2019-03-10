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
ms.openlocfilehash: 121f285a95d0169db79bdc302d80dba03b3b40c2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720040"
---
# <a name="how-to-load-and-display-metafiles"></a><span data-ttu-id="aa743-102">Postupy: Načtení a zobrazení metasouborů</span><span class="sxs-lookup"><span data-stu-id="aa743-102">How to: Load and Display Metafiles</span></span>
<span data-ttu-id="aa743-103"><xref:System.Drawing.Imaging.Metafile> Třída, která dědí z <xref:System.Drawing.Image> třídy, poskytuje metody pro nahrávání, zobrazování a zkoumání vektorové obrázky.</span><span class="sxs-lookup"><span data-stu-id="aa743-103">The <xref:System.Drawing.Imaging.Metafile> class, which inherits from the <xref:System.Drawing.Image> class, provides methods for recording, displaying, and examining vector images.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa743-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="aa743-104">Example</span></span>  
 <span data-ttu-id="aa743-105">K zobrazení bitovou kopii vektoru (metafile) na obrazovce, je nutné <xref:System.Drawing.Imaging.Metafile> objektu a <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="aa743-105">To display a vector image (metafile) on the screen, you need a <xref:System.Drawing.Imaging.Metafile> object and a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="aa743-106">Předat název souboru (nebo datový proud) <xref:System.Drawing.Imaging.Metafile> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="aa743-106">Pass the name of a file (or a stream) to a <xref:System.Drawing.Imaging.Metafile> constructor.</span></span> <span data-ttu-id="aa743-107">Po vytvoření <xref:System.Drawing.Imaging.Metafile> objektu, který předat <xref:System.Drawing.Imaging.Metafile> objektu <xref:System.Drawing.Graphics.DrawImage%2A> metodu <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="aa743-107">After you have created a <xref:System.Drawing.Imaging.Metafile> object, pass that <xref:System.Drawing.Imaging.Metafile> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 <span data-ttu-id="aa743-108">V příkladu se vytvoří <xref:System.Drawing.Imaging.Metafile> objekt ze souboru EMF (rozšířený metasoubor) a potom nakreslí obrázek s jeho levého horního rohu na (60, 10).</span><span class="sxs-lookup"><span data-stu-id="aa743-108">The example creates a <xref:System.Drawing.Imaging.Metafile> object from an EMF (enhanced metafile) file and then draws the image with its upper-left corner at (60, 10).</span></span>  
  
 <span data-ttu-id="aa743-109">Následující obrázek znázorňuje tento metasoubor vykreslen v zadaném umístění.</span><span class="sxs-lookup"><span data-stu-id="aa743-109">The following illustration shows the metafile drawn at the specified location.</span></span>  
  
 <span data-ttu-id="aa743-110">![Obrázek pozice](./media/imageposition2.png "imageposition2")</span><span class="sxs-lookup"><span data-stu-id="aa743-110">![Image Position](./media/imageposition2.png "imageposition2")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="aa743-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="aa743-111">Compiling the Code</span></span>  
 <span data-ttu-id="aa743-112">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="aa743-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa743-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa743-113">See also</span></span>
- [<span data-ttu-id="aa743-114">Práce s obrázky, rastrovými obrázky, ikonami a metasoubory</span><span class="sxs-lookup"><span data-stu-id="aa743-114">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
