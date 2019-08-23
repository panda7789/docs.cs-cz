---
title: 'Postupy: Nastavení zarážek v kresleném textu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing with tab stops
- tabs [Windows Forms], drawn text
ms.assetid: 64878f98-39ba-4303-b63f-0859ab682eeb
ms.openlocfilehash: 8821f6170b8ba588e3197ef54eab14c2719a6cc3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947823"
---
# <a name="how-to-set-tab-stops-in-drawn-text"></a>Postupy: Nastavení zarážek v kresleném textu
Můžete nastavit zarážky tabulátoru pro text voláním <xref:System.Drawing.StringFormat.SetTabStops%2A> metody <xref:System.Drawing.StringFormat> objektu a následným <xref:System.Drawing.Graphics.DrawString%2A> předáním tohoto <xref:System.Drawing.StringFormat> objektu metodě <xref:System.Drawing.Graphics> třídy.  
  
> [!NOTE]
> Nepodporuje přidání zarážek tabulátoru do vykresleného textu, i když můžete rozbalit existující zarážku tabulátoru <xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType> pomocí příznaku. <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType>  
  
## <a name="example"></a>Příklad  
 Následující příklad nastaví zarážky tabulátoru na 150, 250 a 350. Kód pak zobrazuje seznam názvů a hodnocení testů s kartami.  
  
 Následující ilustrace znázorňuje text s kartami:  
  
 ![Snímek obrazovky zobrazující seznam názvů a skóre s kartami](./media/how-to-set-tab-stops-in-drawn-text/tab-list-names-test-scores.png)  
  
 Následující kód předá do <xref:System.Drawing.StringFormat.SetTabStops%2A> metody dva argumenty. Druhým argumentem je pole, které obsahuje posuny tabulátoru. První argument předaný do <xref:System.Drawing.StringFormat.SetTabStops%2A> je 0, což znamená, že první posun v poli je měřen od pozice 0, levého okraje ohraničovacího rámečku.  
  
 [!code-csharp[System.Drawing.FontsAndText#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.FontsAndText#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Předchozí příklad je navržen pro použití s model Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, <xref:System.Windows.Forms.PaintEventHandler>což je parametr.  
  
## <a name="see-also"></a>Viz také:

- [Použití písem a textu](using-fonts-and-text.md)
- [Postupy: Nakreslit text pomocí GDI](how-to-draw-text-with-gdi.md)
