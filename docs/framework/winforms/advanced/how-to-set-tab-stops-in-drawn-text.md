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
ms.openlocfilehash: 8e8f1bf193a41530a19e1046e3907b4c926b779f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64637036"
---
# <a name="how-to-set-tab-stops-in-drawn-text"></a>Postupy: Nastavení zarážek v kresleném textu
Tabulátoru pro text můžete nastavit pomocí volání <xref:System.Drawing.StringFormat.SetTabStops%2A> metodu <xref:System.Drawing.StringFormat> objektu a následné předání, který <xref:System.Drawing.StringFormat> objektu <xref:System.Drawing.Graphics.DrawString%2A> metodu <xref:System.Drawing.Graphics> třídy.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType> Fakturuje se nepodporuje přidání zarážky kresleném textu, i když rozšiřujete existující kartu přestane používat <xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType> příznak.  
  
## <a name="example"></a>Příklad  
 Následující příklad nastaví zarážek na 150, 250 a 350. Potom kód zobrazí seznam s kartami názvy a skóre v testech.  
  
 Následující obrázek znázorňuje následující text:  
  
 ![Snímek obrazovky zobrazující seznam s kartami názvy a skóre.](./media/how-to-set-tab-stops-in-drawn-text/tab-list-names-test-scores.png)  
  
 Následující kód předá dva argumenty <xref:System.Drawing.StringFormat.SetTabStops%2A> metody. Druhý argument je pole, která obsahuje kartu posunů. První argument předaný metodě <xref:System.Drawing.StringFormat.SetTabStops%2A> je 0, což znamená, že první posunutí v poli se měří z pozice 0, je levý okraj ohraničující obdélník.  
  
 [!code-csharp[System.Drawing.FontsAndText#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.FontsAndText#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také:

- [Použití písem a textu](using-fonts-and-text.md)
- [Postupy: Kreslení textu pomocí GDI](how-to-draw-text-with-gdi.md)
