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
# <a name="how-to-use-a-color-matrix-to-set-alpha-values-in-images"></a>Postupy: Použití matice barev k nastavení alfa hodnot v obrázcích
<xref:System.Drawing.Bitmap> Třídy (který dědí z <xref:System.Drawing.Image> třídy) a <xref:System.Drawing.Imaging.ImageAttributes> třídy poskytují funkce pro získání a nastavení hodnoty pixelů. Můžete použít <xref:System.Drawing.Imaging.ImageAttributes> třídy k úpravě alfa hodnoty celého obrázku, nebo můžete volat <xref:System.Drawing.Bitmap.SetPixel%2A> metodu <xref:System.Drawing.Bitmap> třídy k úpravě jednotlivých obrazových bodů.  
  
## <a name="example"></a>Příklad  
 <xref:System.Drawing.Imaging.ImageAttributes> Třída má mnoho vlastností, které vám umožní upravit obrázky při vykreslování. V následujícím příkladu <xref:System.Drawing.Imaging.ImageAttributes> objektu se používá k nastavení alfa hodnot až 80 procent, co bylo. To se provádí inicializace matice barev a alfa škálování hodnoty v matici 0,8 nastavením. Adresa matice barev je předána <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> metodu <xref:System.Drawing.Imaging.ImageAttributes> objektu a <xref:System.Drawing.Imaging.ImageAttributes> objekt je předán do <xref:System.Drawing.Graphics.DrawString%2A> metodu <xref:System.Drawing.Graphics> objektu.  
  
 Během vykreslování, jsou převedeny alfa hodnot rastrového obrázku nastaven na 80 procent, co bylo. Výsledkem je obrázek, který je v kombinaci s na pozadí. Jak ukazuje následující obrázek, vypadá průhledné; rastrový obrázek Zobrazí se plná čára černé přes něj.  
  
 ![Alfa míchání pomocí matice](./media/image2.png "obrazek2")  
  
 Kde je bitová kopie je přes bílé části na pozadí, má byla image v kombinaci s bílou barvu. Kde image protíná černá čára na obrázku je v kombinaci s černá barva.  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také:

- [Grafika a kreslení v modelu Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Alfa míchání čar a výplní](alpha-blending-lines-and-fills.md)
