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
ms.openlocfilehash: c9fe16752223203806c7d3828f632aad0cab0c28
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703362"
---
# <a name="using-fonts-and-text"></a>Použití písem a textu
Existuje několik tříd, které nabízí [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] a [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] pro kreslení textu ve Windows Forms. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> Třídy víme o několika <xref:System.Drawing.Graphics.DrawString%2A> metody, které vám umožňují určit různé funkce textu, jako je poloha, ohraničující obdélník, písma a formát. Kromě toho můžete kreslit a měření text s [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] pomocí statické <xref:System.Windows.Forms.TextRenderer.DrawText%2A> a <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> metody nabízené `TextRenderer` třídy. [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] Metody lze také zadat umístění, písma a formát. Můžete použít buď [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] nebo [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] pro vykreslování textu; však [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] obecně nabízí vyšší výkon a přesnější měření text. Zahrnout další třídy, které přispívají k vykreslování textu `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, a `TextFormatFlags`.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Vytváření rodin písem a písem](how-to-construct-font-families-and-fonts.md)  
 Ukazuje, jak vytvořit `Font` a `FontFamily` objekty.  
  
 [Postupy: Kreslení textu v určeném umístění](how-to-draw-text-at-a-specified-location.md)  
 Popisuje, jak kreslení textu v určitých umístění pomocí [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] a [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
 [Postupy: Kreslení zalomeného textu do obdélníku](how-to-draw-wrapped-text-in-a-rectangle.md)  
 Vysvětluje, jak kreslení textu v obdélníku pomocí [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] a [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
 [Postupy: Kreslení textu pomocí GDI](how-to-draw-text-with-gdi.md)  
 Ukazuje, jak používat [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] pro kreslení textu.  
  
 [Postupy: Zarovnání vykresleného textu](how-to-align-drawn-text.md)  
 Ukazuje, jak formátovat [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] a [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] text.  
  
 [Postupy: Vytvoření svislého textu](how-to-create-vertical-text.md)  
 Popisuje, jak kreslení svisle zarovnané textu pomocí [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
 [Postupy: Nastavení zarážek v kresleném textu](how-to-set-tab-stops-in-drawn-text.md)  
 Ukazuje, jak kreslení textu pomocí zarážek s [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
 [Postupy: Výčet instalovaných písem](how-to-enumerate-installed-fonts.md)  
 Vysvětluje, jak zobrazit jména instalovaných písem.  
  
 [Postupy: Vytvoření soukromé kolekce písem](how-to-create-a-private-font-collection.md)  
 Popisuje, jak vytvořit <xref:System.Drawing.Text.PrivateFontCollection> objektu.  
  
 [Postupy: Získání metriky písma](how-to-obtain-font-metrics.md)  
 Ukazuje, jak získání metriky písma, jako je například ascent buňky a sestup.  
  
 [Postupy: Použití vyhlazení s textem](how-to-use-antialiasing-with-text.md)  
 Vysvětluje způsob použití vyhlazení při kreslení textu.  
  
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
