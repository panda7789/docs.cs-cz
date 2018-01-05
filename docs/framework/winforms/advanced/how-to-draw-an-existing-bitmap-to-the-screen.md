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
ms.workload: dotnet
ms.openlocfilehash: 7b3c8aef4aee74fbcdcc80301f5d5c1020883341
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-an-existing-bitmap-to-the-screen"></a>Postupy: Nakreslení existujícího rastrového obrázku na obrazovku
Na obrazovce můžete snadno nakreslit stávající image. Nejprve je nutné vytvořit <xref:System.Drawing.Bitmap> objekt pomocí konstruktor rastrový obrázek, který přebírá název souboru, <xref:System.Drawing.Bitmap.%23ctor%28System.String%29>. Tento konstruktor přijímá obrázků pomocí několika různých formátech souborů, včetně BMP, GIF, JPEG, PNG a TIFF. Po vytvoření <xref:System.Drawing.Bitmap> objektu, který předat <xref:System.Drawing.Bitmap> do objektu <xref:System.Drawing.Graphics.DrawImage%2A> metodu <xref:System.Drawing.Graphics> objektu.  
  
## <a name="example"></a>Příklad  
 Tento příklad vytvoří <xref:System.Drawing.Bitmap> objekt ze souboru JPEG a pak nevykresluje bitmap s jeho levého horního rohu v (60, 10).  
  
 Následující obrázek znázorňuje rastrový obrázek vykreslovat v zadaném umístění.  
  
 ![Obrázek pozice](../../../../docs/framework/winforms/advanced/media/csimageposition1.png "csimageposition1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.WorkingWithImages#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také  
 [Grafika a kreslení v modelu Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Práce s obrázky, rastrovými obrázky, ikonami a metasoubory](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
