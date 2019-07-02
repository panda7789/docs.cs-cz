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
ms.openlocfilehash: 73a4af5fe7367e777fcb83af8c84c09be91e5b1e
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505120"
---
# <a name="using-fonts-and-text"></a>Použití písem a textu
Existuje několik tříd, které nabízí rozhraní GDI + a GDI pro kreslení textu ve Windows Forms. Rozhraní GDI + <xref:System.Drawing.Graphics> třídy víme o několika <xref:System.Drawing.Graphics.DrawString%2A> metody, které vám umožňují určit různé funkce textu, jako je poloha, ohraničující obdélník, písma a formát. Kromě toho můžete kreslit a měření textu pomocí GDI pomocí statické <xref:System.Windows.Forms.TextRenderer.DrawText%2A> a <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> metody nabízené `TextRenderer` třídy. Metody rozhraní GDI také umožňují zadat umístění, písma a formát. Pro vykreslování textu; můžete vybrat GDI nebo rozhraní GDI + rozhraní GDI však obvykle nabízí lepší výkon a přesnější měření text. Zahrnout další třídy, které přispívají k vykreslování textu `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, a `TextFormatFlags`.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Vytváření rodin písem a písem](how-to-construct-font-families-and-fonts.md)  
 Ukazuje, jak vytvořit `Font` a `FontFamily` objekty.  
  
 [Postupy: Kreslení textu v určeném umístění](how-to-draw-text-at-a-specified-location.md)  
 Popisuje způsob vykreslení textu na určité místo pomocí GDI + a GDI.  
  
 [Postupy: Kreslení zalomeného textu do obdélníku](how-to-draw-wrapped-text-in-a-rectangle.md)  
 Vysvětluje, jak kreslení textu v obdélníku pomocí GDI + a GDI.  
  
 [Postupy: Kreslení textu pomocí GDI](how-to-draw-text-with-gdi.md)  
 Ukazuje, jak se pro kreslení textu pomocí GDI.  
  
 [Postupy: Zarovnání vykresleného textu](how-to-align-drawn-text.md)  
 Ukazuje, jak formátovat text rozhraní GDI + a GDI.  
  
 [Postupy: Vytvoření svislého textu](how-to-create-vertical-text.md)  
 Popisuje, jak kreslení svisle zarovnané textu pomocí GDI +.  
  
 [Postupy: Nastavení zarážek v kresleném textu](how-to-set-tab-stops-in-drawn-text.md)  
 Ukazuje jak kreslení textu pomocí tabulátoru pomocí GDI +.  
  
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
