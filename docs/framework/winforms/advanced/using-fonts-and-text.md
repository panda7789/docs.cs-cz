---
title: Použití písem a textu
ms.date: 03/30/2017
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing in Windows Forms
- examples [Windows Forms], fonts and text
- fonts [Windows Forms], using in Windows Forms
- strings [Windows Forms], drawing in Windows Forms
ms.assetid: d43640f3-da94-4df2-a29d-a9d021a1c069
ms.openlocfilehash: d157b51e24009d847dede9ea6a9f81c8898c5b06
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-fonts-and-text"></a>Použití písem a textu
Existuje několik tříd, které nabízí [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] a [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] pro kreslení textu v rozhraní Windows Forms. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> Třída obsahuje několik <xref:System.Drawing.Graphics.DrawString%2A> metody, které vám umožní určit různé funkce textu, jako je například umístění, ohraničujícího rámečku, písma a formát. Kromě toho můžete kreslení a měřit textu s [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] pomocí statické <xref:System.Windows.Forms.TextRenderer.DrawText%2A> a <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> metody nabízené `TextRenderer` třídy. [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] Metody taky umožňují určit umístění, písma a formát. Můžete buď [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] nebo [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] pro vykreslování textu; však [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] obecně nabízí lepší výkon a přesnější měření text. Zahrnout další třídy, které přispívají k vykreslování textu `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, a `TextFormatFlags`.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Vytváření rodin písem a písem](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 Ukazuje, jak vytvořit `Font` a `FontFamily` objekty.  
  
 [Postupy: Kreslení textu v určeném umístění](../../../../docs/framework/winforms/advanced/how-to-draw-text-at-a-specified-location.md)  
 Popisuje, jak kreslení textu v určitých umístění pomocí [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] a [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
 [Postupy: Kreslení zalomeného textu do obdélníku](../../../../docs/framework/winforms/advanced/how-to-draw-wrapped-text-in-a-rectangle.md)  
 Vysvětluje, jak kreslení textu v obdélníku pomocí [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] a [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
 [Postupy: Kreslení textu pomocí GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 Ukazuje, jak používat [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] pro kreslení textu.  
  
 [Postupy: Zarovnání vykresleného textu](../../../../docs/framework/winforms/advanced/how-to-align-drawn-text.md)  
 Ukazuje, jak k formátování [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] a [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] text.  
  
 [Postupy: Vytvoření svislého textu](../../../../docs/framework/winforms/advanced/how-to-create-vertical-text.md)  
 Popisuje, jak kreslení svisle zarovnaný textu s [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
 [Postupy: Nastavení zarážek v kresleném textu](../../../../docs/framework/winforms/advanced/how-to-set-tab-stops-in-drawn-text.md)  
 Ukazuje, jak kreslení textu pomocí zarážek tabulátoru s [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
 [Postupy: Výčet instalovaných písem](../../../../docs/framework/winforms/advanced/how-to-enumerate-installed-fonts.md)  
 Vysvětluje, jak zobrazit názvy instalovaných písem.  
  
 [Postupy: Vytvoření soukromé kolekce písem](../../../../docs/framework/winforms/advanced/how-to-create-a-private-font-collection.md)  
 Popisuje postup vytvoření <xref:System.Drawing.Text.PrivateFontCollection> objektu.  
  
 [Postupy: Získání metriky písma](../../../../docs/framework/winforms/advanced/how-to-obtain-font-metrics.md)  
 Ukazuje, jak získat metriky písma, jako je například výstup buňky a klesání.  
  
 [Postupy: Použití vyhlazení u textu](../../../../docs/framework/winforms/advanced/how-to-use-antialiasing-with-text.md)  
 Tento článek vysvětluje použití vyhlazení při kreslení textu.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Drawing.Font>  
 Tato třída popisuje a obsahuje odkazy na všechny její členy.  
  
 <xref:System.Drawing.FontFamily>  
 Tato třída popisuje a obsahuje odkazy na všechny její členy.  
  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 Tato třída popisuje a obsahuje odkazy na všechny její členy.  
  
 <xref:System.Windows.Forms.TextRenderer>  
 Tato třída popisuje a obsahuje odkazy na všechny její členy.  
  
 <xref:System.Windows.Forms.TextFormatFlags>  
 Tato třída popisuje a obsahuje odkazy na všechny její členy.
