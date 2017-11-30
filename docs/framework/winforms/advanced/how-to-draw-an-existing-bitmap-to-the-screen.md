---
title: "Postupy: Nakreslení existujícího rastrového obrázku na obrazovku"
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
- bitmaps [Windows Forms], displaying in Windows Forms
- bitmaps [Windows Forms], loading in Windows Forms applications
- images [Windows Forms], displaying on Windows Forms
ms.assetid: 5bc558d7-b326-4050-a834-b8600da0de95
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f435c397832e8f64b2bf911a59aae7578ffd3bdf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-an-existing-bitmap-to-the-screen"></a><span data-ttu-id="3e9b5-102">Postupy: Nakreslení existujícího rastrového obrázku na obrazovku</span><span class="sxs-lookup"><span data-stu-id="3e9b5-102">How to: Draw an Existing Bitmap to the Screen</span></span>
<span data-ttu-id="3e9b5-103">Na obrazovce můžete snadno nakreslit stávající image.</span><span class="sxs-lookup"><span data-stu-id="3e9b5-103">You can easily draw an existing image on the screen.</span></span> <span data-ttu-id="3e9b5-104">Nejprve je nutné vytvořit <xref:System.Drawing.Bitmap> objekt pomocí konstruktor rastrový obrázek, který přebírá název souboru, <xref:System.Drawing.Bitmap.%23ctor%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="3e9b5-104">First you need to create a <xref:System.Drawing.Bitmap> object by using the bitmap constructor that takes a file name, <xref:System.Drawing.Bitmap.%23ctor%28System.String%29>.</span></span> <span data-ttu-id="3e9b5-105">Tento konstruktor přijímá obrázků pomocí několika různých formátech souborů, včetně BMP, GIF, JPEG, PNG a TIFF.</span><span class="sxs-lookup"><span data-stu-id="3e9b5-105">This constructor accepts images with several different file formats, including BMP, GIF, JPEG, PNG, and TIFF.</span></span> <span data-ttu-id="3e9b5-106">Po vytvoření <xref:System.Drawing.Bitmap> objektu, který předat <xref:System.Drawing.Bitmap> do objektu <xref:System.Drawing.Graphics.DrawImage%2A> metodu <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="3e9b5-106">After you have created the <xref:System.Drawing.Bitmap> object, pass that <xref:System.Drawing.Bitmap> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e9b5-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="3e9b5-107">Example</span></span>  
 <span data-ttu-id="3e9b5-108">Tento příklad vytvoří <xref:System.Drawing.Bitmap> objekt ze souboru JPEG a pak nevykresluje bitmap s jeho levého horního rohu v (60, 10).</span><span class="sxs-lookup"><span data-stu-id="3e9b5-108">This example creates a <xref:System.Drawing.Bitmap> object from a JPEG file and then draws the bitmap with its upper-left corner at (60, 10).</span></span>  
  
 <span data-ttu-id="3e9b5-109">Následující obrázek znázorňuje rastrový obrázek vykreslovat v zadaném umístění.</span><span class="sxs-lookup"><span data-stu-id="3e9b5-109">The following illustration shows the bitmap drawn at the specified location.</span></span>  
  
 <span data-ttu-id="3e9b5-110">![Obrázek pozice](../../../../docs/framework/winforms/advanced/media/csimageposition1.png "csimageposition1")</span><span class="sxs-lookup"><span data-stu-id="3e9b5-110">![Image Position](../../../../docs/framework/winforms/advanced/media/csimageposition1.png "csimageposition1")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.WorkingWithImages#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3e9b5-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="3e9b5-111">Compiling the Code</span></span>  
 <span data-ttu-id="3e9b5-112">V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="3e9b5-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e9b5-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="3e9b5-113">See Also</span></span>  
 [<span data-ttu-id="3e9b5-114">Grafika a kreslení v systému Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3e9b5-114">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="3e9b5-115">Práce s obrázky, rastrové obrázky, ikony a metasoubory</span><span class="sxs-lookup"><span data-stu-id="3e9b5-115">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
