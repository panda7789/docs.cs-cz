---
title: 'Postupy: Zavedení a zobrazení metasouborů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], metafiles
- metafiles [Windows Forms], displaying
ms.assetid: 60af1714-f148-4d85-a739-0557965ffa73
ms.openlocfilehash: 6c17e0b2d023ccf80b0d32301b7ee6765edcae9f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424827"
---
# <a name="how-to-load-and-display-metafiles"></a><span data-ttu-id="a6243-102">Postupy: Zavedení a zobrazení metasouborů</span><span class="sxs-lookup"><span data-stu-id="a6243-102">How to: Load and Display Metafiles</span></span>
<span data-ttu-id="a6243-103">Třída <xref:System.Drawing.Imaging.Metafile>, která dědí z třídy <xref:System.Drawing.Image>, poskytuje metody pro zaznamenávání, zobrazování a zkoumání vektorových imagí.</span><span class="sxs-lookup"><span data-stu-id="a6243-103">The <xref:System.Drawing.Imaging.Metafile> class, which inherits from the <xref:System.Drawing.Image> class, provides methods for recording, displaying, and examining vector images.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6243-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a6243-104">Example</span></span>  
 <span data-ttu-id="a6243-105">Chcete-li na obrazovce zobrazit vektorový obraz (metasoubor), budete potřebovat objekt <xref:System.Drawing.Imaging.Metafile> a objekt <xref:System.Drawing.Graphics>.</span><span class="sxs-lookup"><span data-stu-id="a6243-105">To display a vector image (metafile) on the screen, you need a <xref:System.Drawing.Imaging.Metafile> object and a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="a6243-106">Předat název souboru (nebo datového proudu) konstruktoru <xref:System.Drawing.Imaging.Metafile>.</span><span class="sxs-lookup"><span data-stu-id="a6243-106">Pass the name of a file (or a stream) to a <xref:System.Drawing.Imaging.Metafile> constructor.</span></span> <span data-ttu-id="a6243-107">Po vytvoření objektu <xref:System.Drawing.Imaging.Metafile> předejte objekt <xref:System.Drawing.Imaging.Metafile> do metody <xref:System.Drawing.Graphics.DrawImage%2A> objektu <xref:System.Drawing.Graphics>.</span><span class="sxs-lookup"><span data-stu-id="a6243-107">After you have created a <xref:System.Drawing.Imaging.Metafile> object, pass that <xref:System.Drawing.Imaging.Metafile> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 <span data-ttu-id="a6243-108">V příkladu se vytvoří objekt <xref:System.Drawing.Imaging.Metafile> ze souboru EMF (Enhanced Metafile) a pak se obrázek vykreslí pomocí levého horního rohu v (60, 10).</span><span class="sxs-lookup"><span data-stu-id="a6243-108">The example creates a <xref:System.Drawing.Imaging.Metafile> object from an EMF (enhanced metafile) file and then draws the image with its upper-left corner at (60, 10).</span></span>  
  
 <span data-ttu-id="a6243-109">Následující ilustrace znázorňuje metasoubor nakreslený v zadaném umístění.</span><span class="sxs-lookup"><span data-stu-id="a6243-109">The following illustration shows the metafile drawn at the specified location.</span></span>  
  
 <span data-ttu-id="a6243-110">![Snímek obrazovky znázorňující umístění obrázku](./media/how-to-load-and-display-metafiles/metafile-drawn-specified-location.png "imageposition2")</span><span class="sxs-lookup"><span data-stu-id="a6243-110">![Screenshot showing image position.](./media/how-to-load-and-display-metafiles/metafile-drawn-specified-location.png "imageposition2")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a6243-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="a6243-111">Compiling the Code</span></span>  
 <span data-ttu-id="a6243-112">Předchozí příklad je navržen pro použití s model Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr obslužné rutiny události <xref:System.Windows.Forms.Control.Paint>.</span><span class="sxs-lookup"><span data-stu-id="a6243-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6243-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a6243-113">See also</span></span>

- [<span data-ttu-id="a6243-114">Práce s obrázky, rastrovými obrázky, ikonami a metasoubory</span><span class="sxs-lookup"><span data-stu-id="a6243-114">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
