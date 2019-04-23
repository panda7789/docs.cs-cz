---
title: 'Postupy: Řízení funkce alfa blending pomocí režimu skládání'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- alpha blending [Windows Forms], compositing
- colors [Windows Forms], blending
- colors [Windows Forms], controlling transparency
ms.assetid: f331df2d-b395-4b0a-95be-24fec8c9bbb5
ms.openlocfilehash: 15cb111a68cedaec011e88fa4916c292786d16b4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59210688"
---
# <a name="how-to-use-compositing-mode-to-control-alpha-blending"></a>Postupy: Řízení funkce alfa blending pomocí režimu skládání
Může nastat situace, kdy budete chtít vytvořit mimo obrazovku rastrový obrázek, který má následující vlastnosti:  
  
-   Barvy mají hodnoty alfa, které jsou kratší než 255.  
  
-   Barvy nejsou alfa prolnuty mezi sebou při vytváření rastrového obrázku.  
  
-   Když zobrazíte dokončená rastrového obrázku jsou barvy rastrového obrázku nastaven barvy pozadí na zobrazovací zařízení smíšení alfa.  
  
 Chcete-li vytvořit takové rastrový obrázek, vytvořit prázdnou hodnotu <xref:System.Drawing.Bitmap> objektu a pak vytvořit <xref:System.Drawing.Graphics> objektu podle tento rastrový obrázek. Nastavení režimu skládání <xref:System.Drawing.Graphics> objektu <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy?displayProperty=nameWithType>.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Drawing.Graphics> objektu na základě <xref:System.Drawing.Bitmap> objektu. Tento kód použije <xref:System.Drawing.Graphics> objekt spolu se dvěma poloprůhledných štětců (alfa = 160) k vykreslení na rastrový obrázek. Kód vyplní red tři tečky a zelená elipsa pomocí poloprůhledných štětců. Zelené elipsy překrývá red elipsy, ale zelené není v kombinaci s červeným protože skládání režim <xref:System.Drawing.Graphics> je nastaven na <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy>.  
  
 Kód vykreslí rastrového obrázku na obrazovce dvakrát: jednou na bílém pozadí a jakmile na barevné pozadí. Pixely rastrového obrázku nastaven, které jsou součástí dvou symbol tří teček mít alfa složkou 160, proto se tři tečky v kombinaci s barvy pozadí na obrazovce.  
  
 Následující obrázek znázorňuje výstup v příkladu kódu. Všimněte si, že jsou na symbol tří teček v kombinaci s na pozadí, ale nejsou prolnuty mezi sebou.  
  
 ![Diagram znázorňující tři tečky v kombinaci s na pozadí, ne mezi sebou.](./media/how-to-use-compositing-mode-to-control-alpha-blending/ellipses-blended-background.png)  
  
 Příklad kódu obsahuje tento příkaz:  
  
 [!code-csharp[System.Drawing.AlphaBlending#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.AlphaBlending#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#41)]  
  
 Pokud chcete na symbol tří teček, chcete-li být smíšené mezi sebou můžou mít na pozadí, změňte, který tento příkaz takto:  
  
 [!code-csharp[System.Drawing.AlphaBlending#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.AlphaBlending#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#42)]  
  
 Následující obrázek znázorňuje výstup revidovaného kódu.  
  
 ![Diagram znázorňující tři tečky v kombinaci společně a s na pozadí.](./media/how-to-use-compositing-mode-to-control-alpha-blending/blend-ellipses-background.png)  
  
 [!code-csharp[System.Drawing.AlphaBlending#43](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#43)]
 [!code-vb[System.Drawing.AlphaBlending#43](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#43)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Color.FromArgb%2A>
- [Alfa míchání čar a výplní](alpha-blending-lines-and-fills.md)
