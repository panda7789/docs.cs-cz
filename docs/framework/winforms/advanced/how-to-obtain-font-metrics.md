---
title: 'Postupy: Získání metriky písma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [Windows Forms], obtaining metrics
- font metrics [Windows Forms], obtaining
ms.assetid: ff7c0616-67f7-4fa2-84ee-b8d642f2b09b
ms.openlocfilehash: 24cada3962339cae0608bbe01e070a0b8e256e73
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119051"
---
# <a name="how-to-obtain-font-metrics"></a>Postupy: Získání metriky písma
<xref:System.Drawing.FontFamily> Třída poskytuje následující metody, které načítají různé metriky pro konkrétní řady a styl kombinace:  
  
-   <xref:System.Drawing.FontFamily.GetEmHeight%2A>(FontStyle)  
  
-   <xref:System.Drawing.FontFamily.GetCellAscent%2A>(FontStyle)  
  
-   <xref:System.Drawing.FontFamily.GetCellDescent%2A>(FontStyle)  
  
-   <xref:System.Drawing.FontFamily.GetLineSpacing%2A>(FontStyle)  
  
 Hodnoty vrácené z těchto metod jsou v písma návrhu jednotek, takže se platí bez ohledu na velikost a jednotek určitého <xref:System.Drawing.Font> objektu.  
  
 Následující obrázek znázorňuje různé metriky.  
  
 ![Písma textu](./media/fontstext7a.png "fontstext7A")  
  
## <a name="example"></a>Příklad  
 Následující příklad zobrazuje metriky pro pravidelné styl řady Arial písmo. Kód vytvoří také <xref:System.Drawing.Font> objektu (podle Arial řady) s velikost 16 pixelů a zobrazení metrik (v pixelech) o tomto konkrétním <xref:System.Drawing.Font> objektu.  
  
 Následující obrázek znázorňuje výstup tohoto ukázkového kódu.  
  
 ![Fonts Text](./media/csfontstext8.png "csFontsText8")  
  
 Poznámka: první dva řádky výstupního předchozím obrázku. <xref:System.Drawing.Font> o velikosti 16, vrátí objekt a <xref:System.Drawing.FontFamily> objekt vrátí výšku em 2 048. Tyto dvě čísla (16 a 2 048) jsou klíčem k převodu mezi písma návrhu jednotky a jednotek (v tomto případu pixelů) <xref:System.Drawing.Font> objektu.  
  
 Například můžete převedete ascent z návrhu jednotek na pixelech následujícím způsobem:  
  
 ![Písma textu](./media/fontstext9.png "FontsText9")  
  
 Následující kód umístí text svisle tak, že nastavíte <xref:System.Drawing.PointF.Y%2A> datový člen třídy <xref:System.Drawing.PointF> objektu. Souřadnice y prodloužen o `font.Height` pro každého nového řádku textu. <xref:System.Drawing.Font.Height%2A> Vlastnost <xref:System.Drawing.Font> objekt vrátí řádkování (v pixelech) o tomto konkrétním <xref:System.Drawing.Font> objektu. V tomto příkladu číslo vrácen podle <xref:System.Drawing.Font.Height%2A> je 19. Všimněte si, že toto je stejné jako číslo (zaokrouhleno na celé číslo) získala při převodu řádkování metrika na pixelech.  
  
 Všimněte si, že výška em (také nazývané velikost nebo em velikost) není součet ascent a sestup. Součet hodnot ascent a sestup se nazývá výška buňky. Výška buňky minus interní úvodního rovná Výška em. Výška buňky a externí úvodního rovná řádkování.  
  
 [!code-csharp[System.Drawing.FontsAndText#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.FontsAndText#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také:

- [Grafika a kreslení v rozhraní Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Použití písem a textu](using-fonts-and-text.md)
