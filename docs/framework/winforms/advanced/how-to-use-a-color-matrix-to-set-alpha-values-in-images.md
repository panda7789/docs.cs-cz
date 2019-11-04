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
ms.openlocfilehash: 73e820845d040856a0ae367da8b9371ad6afa142
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423739"
---
# <a name="how-to-use-a-color-matrix-to-set-alpha-values-in-images"></a>Postupy: Použití matice barev k nastavení alfa hodnot v obrázcích
Třída <xref:System.Drawing.Bitmap> (která dědí z třídy <xref:System.Drawing.Image>) a třída <xref:System.Drawing.Imaging.ImageAttributes> poskytují funkce pro získávání a nastavování hodnot pixelů. Třídu <xref:System.Drawing.Imaging.ImageAttributes> lze použít k úpravě hodnot alfa pro celý obrázek, nebo můžete zavolat metodu <xref:System.Drawing.Bitmap.SetPixel%2A> třídy <xref:System.Drawing.Bitmap> pro úpravu jednotlivých hodnot pixelů.  
  
## <a name="example"></a>Příklad  
 Třída <xref:System.Drawing.Imaging.ImageAttributes> má mnoho vlastností, které lze použít k úpravě obrázků během vykreslování. V následujícím příkladu se <xref:System.Drawing.Imaging.ImageAttributes> objekt používá k nastavení všech hodnot Alpha na 80 procent z toho, co byly. To se provádí inicializací barevné matice a nastavením hodnoty alfa škálování v matici na 0,8. Adresa matice barev je předána metodě <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> objektu <xref:System.Drawing.Imaging.ImageAttributes> a objekt <xref:System.Drawing.Imaging.ImageAttributes> je předán metodě <xref:System.Drawing.Graphics.DrawString%2A> objektu <xref:System.Drawing.Graphics>.  
  
 Při vykreslování se hodnoty alfa v bitmapě převedou na 80 procent z toho, co byly. Výsledkem je obrázek, který je Blendem na pozadí. Jak ukazuje následující obrázek, rastrový obrázek vypadá transparentně. můžete vidět plnou černou čáru.  
  
 ![Snímek obrazovky s alfa prolnutím s použitím matice](./media/how-to-use-a-color-matrix-to-set-alpha-values-in-images/alpha-blending-matrix.png "Obrázek 2")  
  
 V případě, že se obrázek nachází v bílé části pozadí, obrázek byl smíchán s barvou bílá. V případě, že obrázek překračuje černou čáru, je obrázek smíchán barvou černou.  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Předchozí příklad je navržen pro použití s model Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také:

- [Grafika a kreslení v modelu Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Alfa míchání čar a výplní](alpha-blending-lines-and-fills.md)
