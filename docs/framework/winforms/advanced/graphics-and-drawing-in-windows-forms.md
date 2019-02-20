---
title: Grafika a kreslení v rozhraní Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: e6d3c395a2d5b8ae885114a53b230d7265102bc8
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2019
ms.locfileid: "56441161"
---
# <a name="graphics-and-drawing-in-windows-forms"></a>Grafika a kreslení v rozhraní Windows Forms
Modul common language runtime používá pokročilé provádění Windows Graphics Device Interface ([!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]) volá [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]. S [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] můžete vytvořit grafiky, kreslení textu a manipulaci s grafické obrázky jako objekty. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] je určená k výkonu a snadnost použití. Můžete použít [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] k vykreslení grafické obrázky ve Windows Forms a ovládacích prvků. I když [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] přímo na webové formuláře, můžete zobrazit grafické obrázky prostřednictvím ovládacího prvku obrázek Webový Server.  
  
 V této části najdete témata, která představují základní informace o [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] programování. I když nemají být komplexní referenční informace, tato část obsahuje informace o <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, a <xref:System.Drawing.Color> objekty a vysvětluje, jak provádět úkoly, jako je kreslení tvarů, textu, kreslení nebo zobrazení obrázků. Další informace najdete v tématu [referenční dokumentace rozhraní GDI +](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).  
  
 Pokud byste chtěli přidejte se k nám a rovnou začít, najdete v článku [Začínáme s programováním grafiky](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md). Obsahuje témata o tom, jak použít kód kreslení čar, tvary, text a informace o Windows forms.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled grafiky](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 Poskytuje úvod ke spravovaným třídám související grafiky.  
  
 [Informace o spravovaném kódu GDI+](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 Poskytuje informace o managed [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] třídy.  
  
 [Použití spravovaných grafických tříd](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)  
 Ukazuje, jak k provádění různých úloh s použitím [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] spravovaných tříd.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Drawing>  
 Poskytuje přístup k [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] základní grafické funkce.  
  
 <xref:System.Drawing.Drawing2D>  
 Poskytuje vyspělé 2D a vektorové grafické funkce.  
  
 <xref:System.Drawing.Imaging>  
 Poskytuje pokročilé [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] funkce pro zpracování obrázků.  
  
 <xref:System.Drawing.Text>  
 Poskytuje pokročilé [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Typografie funkce. Třídy v tomto oboru názvů lze použít k vytvoření a použití kolekce písem.  
  
 <xref:System.Drawing.Printing>  
 Poskytuje funkce tisku.  
  
## <a name="related-sections"></a>Související oddíly  
 [Malování a vykreslování vlastního ovládacího prvku](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)  
 Podrobně popisuje, jak poskytnout kód pro vykreslování ovládacích prvků.
