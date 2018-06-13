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
ms.openlocfilehash: 3cc5ee303efe6c703a61eef6c7448979b487f6bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524206"
---
# <a name="how-to-obtain-font-metrics"></a>Postupy: Získání metriky písma
<xref:System.Drawing.FontFamily> Třída poskytuje následující metody, které načíst různé metriky pro konkrétní rodiny/styl kombinace:  
  
-   <xref:System.Drawing.FontFamily.GetEmHeight%2A>(FontStyle)  
  
-   <xref:System.Drawing.FontFamily.GetCellAscent%2A>(FontStyle)  
  
-   <xref:System.Drawing.FontFamily.GetCellDescent%2A>(FontStyle)  
  
-   <xref:System.Drawing.FontFamily.GetLineSpacing%2A>(FontStyle)  
  
 Hodnoty vrácené tyto metody jsou v jednotkách návrhu písma, proto jsou nezávislé na velikost a jednotky konkrétní <xref:System.Drawing.Font> objektu.  
  
 Následující obrázek ukazuje různé metriky.  
  
 ![Text písem](../../../../docs/framework/winforms/advanced/media/fontstext7a.png "fontstext7A")  
  
## <a name="example"></a>Příklad  
 Následující příklad zobrazí metriky pro regulární styl typu Arial. Kód také vytvoří <xref:System.Drawing.Font> objektu (podle Arial rodiny) s 16 pixelů velikost a zobrazí metriky (v pixelech) pro tuto konkrétní <xref:System.Drawing.Font> objektu.  
  
 Následující obrázek znázorňuje výstup ukázkový kód.  
  
 ![Text písem](../../../../docs/framework/winforms/advanced/media/csfontstext8.png "csFontsText8")  
  
 Všimněte si výstupu v předchozí ilustraci první dva řádky. <xref:System.Drawing.Font> Objekt vrátí velikost 16 a <xref:System.Drawing.FontFamily> em výška 2 048 vrátí objekt. Tato dvě čísla (16 a 2 048) jsou klíčem k převod mezi písma návrhu jednotky a jednotek (v pixelech tento případu) <xref:System.Drawing.Font> objektu.  
  
 Například můžete převést stoupání z návrhu jednotek pixelů následujícím způsobem:  
  
 ![Text písem](../../../../docs/framework/winforms/advanced/media/fontstext9.png "FontsText9")  
  
 Následující kód umisťuje textu ve svislém směru nastavením <xref:System.Drawing.PointF.Y%2A> data členem <xref:System.Drawing.PointF> objektu. Souřadnice y je zvýšen `font.Height` u každého nového řádku textu. <xref:System.Drawing.Font.Height%2A> Vlastnost <xref:System.Drawing.Font> objekt vrátí mezery mezi řádky (v pixelech) pro tuto konkrétní <xref:System.Drawing.Font> objektu. V tomto příkladu počet vrácených <xref:System.Drawing.Font.Height%2A> je 19. Všimněte si, že toto je stejné jako číslo (zaokrouhlený nahoru na celé číslo) získala při převodu metrika mezery mezi řádky na pixelů.  
  
 Všimněte si, Výška em (také nazývané velikost velikost nebo em) není součet výstup a klesání. Součet výstup a klesání nazývá výška buňky. Výška buňky minus interní úvodní výšce em rovná. Výška buňky plus externí úvodního se rovná mezery mezi řádky.  
  
 [!code-csharp[System.Drawing.FontsAndText#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.FontsAndText#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také  
 [Grafika a kreslení v modelu Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Použití písem a textu](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
