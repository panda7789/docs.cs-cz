---
title: Grafika a kreslení v rozhraní Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: e110203605c31f90f71c949f81c18ebf464d52eb
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505541"
---
# <a name="graphics-and-drawing-in-windows-forms"></a>Grafika a kreslení v rozhraní Windows Forms
Modul common language runtime používá pokročilé implementace systému Windows rozhraní GDI (Graphics Device) volá rozhraní GDI +. Pomocí GDI + můžete vytvořit grafiky, kreslení textu a manipulaci s grafické obrázky jako objekty. Rozhraní GDI + je určená k výkonu a snadnost použití. Můžete použijete GDI + k vykreslení grafické obrázky ve Windows Forms a ovládacích prvků. I když nelze použijete GDI + přímo na webové formuláře, můžete zobrazit grafické obrázky prostřednictvím ovládacího prvku obrázek Webový Server.  
  
 V této části najdete témata, která představí základy programování v rozhraní GDI +. I když nemají být komplexní referenční informace, tato část obsahuje informace o <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, a <xref:System.Drawing.Color> objekty a vysvětluje, jak provádět úkoly, jako je kreslení tvarů, textu, kreslení nebo zobrazení obrázků. Další informace najdete v tématu [referenční dokumentace rozhraní GDI +](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).  
  
 Pokud byste chtěli přidejte se k nám a rovnou začít, najdete v článku [Začínáme s programováním grafiky](getting-started-with-graphics-programming.md). Obsahuje témata o tom, jak použít kód kreslení čar, tvary, text a informace o Windows forms.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled grafiky](graphics-overview-windows-forms.md)  
 Poskytuje úvod ke spravovaným třídám související grafiky.  
  
 [Informace o spravovaném kódu GDI+](about-gdi-managed-code.md)  
 Poskytuje informace o spravovaných třídách rozhraní GDI +.  
  
 [Použití spravovaných grafických tříd](using-managed-graphics-classes.md)  
 Ukazuje, jak na kompletní širokou škálu úloh s použitím rozhraní GDI + spravované třídy.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Drawing>  
 Poskytuje přístup k základní grafické funkce rozhraní GDI +.  
  
 <xref:System.Drawing.Drawing2D>  
 Poskytuje vyspělé 2D a vektorové grafické funkce.  
  
 <xref:System.Drawing.Imaging>  
 Poskytuje pokročilé rozhraní GDI + funkce pro zpracování obrázků.  
  
 <xref:System.Drawing.Text>  
 Poskytuje pokročilé funkce Typografie rozhraní GDI +. Třídy v tomto oboru názvů lze použít k vytvoření a použití kolekce písem.  
  
 <xref:System.Drawing.Printing>  
 Poskytuje funkce tisku.  
  
## <a name="related-sections"></a>Související oddíly  
 [Malování a vykreslování vlastního ovládacího prvku](../controls/custom-control-painting-and-rendering.md)  
 Podrobně popisuje, jak poskytnout kód pro vykreslování ovládacích prvků.
