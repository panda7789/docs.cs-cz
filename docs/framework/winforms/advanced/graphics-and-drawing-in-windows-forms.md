---
title: Grafika a kreslení
description: Přečtěte si o objektech grafiky, pera, štětce a barvě a o tom, jak provádět takové úkoly jako kreslení tvarů, kreslení textu nebo zobrazování obrázků v model Windows Forms.
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: 58d8cde6aa102225cf9e3c342efe37218c818307
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618399"
---
# <a name="graphics-and-drawing-in-windows-forms"></a>Grafika a kreslení v rozhraní Windows Forms
Modul CLR (Common Language Runtime) používá pokročilou implementaci Windows GDI (GDI) s názvem GDI+. Pomocí nástroje GDI+ můžete vytvářet grafiky, kreslit text a manipulovat s grafickými obrázky jako objekty. GDI+ je navržený tak, aby poskytoval výkon a snadné použití. Pomocí rozhraní GDI+ můžete vykreslit grafické obrázky na model Windows Forms a ovládací prvky. I když nemůžete použít rozhraní GDI+ přímo na webových formulářích, můžete zobrazit grafické obrázky pomocí ovládacího prvku webového serveru imagí.  
  
 V této části najdete témata, která zavádějí základy programování v rozhraní GDI+. I když není zamýšlen jako vyčerpávající odkaz, Tato část obsahuje informace o <xref:System.Drawing.Graphics> <xref:System.Drawing.Pen> objektech,, <xref:System.Drawing.Brush> a a <xref:System.Drawing.Color> vysvětluje, jak provádět takové úkoly jako vykreslování tvarů, kreslení textu nebo zobrazování obrázků. Další informace najdete v tématu [Reference k rozhraní GDI+](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).  
  
 Pokud byste chtěli přejít na začátek a hned začít, přečtěte si téma [Začínáme with Graphics Programming](getting-started-with-graphics-programming.md). Obsahuje témata týkající se použití kódu k vykreslování čar, tvarů, textu a dalších v modelu Windows Forms.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled grafiky](graphics-overview-windows-forms.md)  
 Poskytuje Úvod do spravovaných tříd souvisejících s grafikou.  
  
 [Informace o spravovaném kódu GDI+](about-gdi-managed-code.md)  
 Poskytuje informace o spravovaných třídách rozhraní GDI+.  
  
 [Použití spravovaných grafických tříd](using-managed-graphics-classes.md)  
 Ukazuje, jak provést různé úlohy pomocí spravovaných tříd rozhraní GDI+.  
  
## <a name="reference"></a>Referenční informace  
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
