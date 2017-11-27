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
ms.openlocfilehash: ba7a016c96556f2719d4a247c93df7ac698b24fa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-color-matrix-to-set-alpha-values-in-images"></a>Postupy: Použití matice barev k nastavení alfa hodnot v obrázcích
<xref:System.Drawing.Bitmap> – Třída (který dědí z <xref:System.Drawing.Image> třída) a <xref:System.Drawing.Imaging.ImageAttributes> třída poskytovat funkce pro načtení a nastavení hodnoty pixelů. Můžete použít <xref:System.Drawing.Imaging.ImageAttributes> třída změnit alpha hodnoty celého obrázku, nebo můžete volat <xref:System.Drawing.Bitmap.SetPixel%2A> metodu <xref:System.Drawing.Bitmap> třídy upravte hodnoty jednotlivých pixelů.  
  
## <a name="example"></a>Příklad  
 <xref:System.Drawing.Imaging.ImageAttributes> Třída má mnoho vlastností, které můžete použít k úpravě bitové kopie během vykreslování. V následujícím příkladu se <xref:System.Drawing.Imaging.ImageAttributes> objekt se používá k nastavení alfa hodnot až 80 procent jaké byly. To se provádí inicializace matice barev a nastavit alpha hodnotu v matici 0,8 změny velikosti. Je předán na adresu matice barev <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> metodu <xref:System.Drawing.Imaging.ImageAttributes> objekt a <xref:System.Drawing.Imaging.ImageAttributes> je předán objekt <xref:System.Drawing.Graphics.DrawString%2A> metodu <xref:System.Drawing.Graphics> objektu.  
  
 Při vykreslování, jsou až 80 procent jaké byly převést alfa hodnot v souboru bitové mapy. Výsledkem je obrázek, který je smíšený s na pozadí. Jak ukazuje následující obrázek, rastrový obrázek vypadá transparentní; můžete zobrazit plná černá čára přes něj.  
  
 ![Alfa míchání pomocí matice](../../../../docs/framework/winforms/advanced/media/image2.png "obrázek 2")  
  
 Kde je bitová kopie je přes části bílé pozadí, má byla smíšené bitovou kopii s bílé barvy. Kde bitovou kopii protne černá čára bitovou kopii je smíšený s černé barvy.  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také  
 [Grafika a kreslení v systému Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Alfa míchání čar a výplní](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)
