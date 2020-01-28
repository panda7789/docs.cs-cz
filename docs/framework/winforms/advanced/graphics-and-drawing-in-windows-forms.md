---
title: Grafika a kreslení
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: 10ad18d38c84f6e447601ab6c8bf1a953dabb7cf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746400"
---
# <a name="graphics-and-drawing-in-windows-forms"></a>Grafika a kreslení v rozhraní Windows Forms
Modul CLR (Common Language Runtime) používá pokročilou implementaci Windows GDI (GDI) s názvem GDI+. Pomocí nástroje GDI+ můžete vytvářet grafiky, kreslit text a manipulovat s grafickými obrázky jako objekty. GDI+ je navržený tak, aby poskytoval výkon a snadné použití. Pomocí rozhraní GDI+ můžete vykreslit grafické obrázky na model Windows Forms a ovládací prvky. I když nemůžete použít rozhraní GDI+ přímo na webových formulářích, můžete zobrazit grafické obrázky pomocí ovládacího prvku webového serveru imagí.  
  
 V této části najdete témata, která zavádějí základy programování v rozhraní GDI+. I když se nejedná o ucelený odkaz, obsahuje tato část informace o <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>a <xref:System.Drawing.Color>ch objektech a vysvětluje, jak provádět takové úkoly jako kreslení tvarů, kreslení textu nebo zobrazování obrázků. Další informace najdete v tématu [Reference k rozhraní GDI+](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).  
  
 Pokud byste chtěli přejít na začátek a hned začít, přečtěte si téma [Začínáme with Graphics Programming](getting-started-with-graphics-programming.md). Obsahuje témata týkající se použití kódu k vykreslování čar, tvarů, textu a dalších v modelu Windows Forms.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled grafiky](graphics-overview-windows-forms.md)  
 Poskytuje Úvod do spravovaných tříd souvisejících s grafikou.  
  
 [Informace o spravovaném kódu GDI+](about-gdi-managed-code.md)  
 Poskytuje informace o spravovaných třídách rozhraní GDI+.  
  
 [Použití spravovaných grafických tříd](using-managed-graphics-classes.md)  
 Ukazuje, jak provést různé úlohy pomocí spravovaných tříd rozhraní GDI+.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Drawing>  
 Poskytuje přístup k funkci GDI+ Basic Graphics.  
  
 <xref:System.Drawing.Drawing2D>  
 Poskytuje pokročilé funkce dvourozměrné a vektorové grafiky.  
  
 <xref:System.Drawing.Imaging>  
 Poskytuje pokročilé funkce pro vytváření bitových kopií rozhraní GDI+.  
  
 <xref:System.Drawing.Text>  
 Poskytuje pokročilé funkce typografie rozhraní GDI+. Třídy v tomto oboru názvů lze použít k vytvoření a použití kolekcí písem.  
  
 <xref:System.Drawing.Printing>  
 Poskytuje funkce tisku.  
  
## <a name="related-sections"></a>Související oddíly  
 [Malování a vykreslování vlastního ovládacího prvku](../controls/custom-control-painting-and-rendering.md)  
 Obsahuje podrobnosti o tom, jak poskytnout kód pro vykreslování ovládacích prvků.
