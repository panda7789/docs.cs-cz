---
title: Přehled grafiky
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using managed interface
- graphics [Windows Forms], about graphics
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
ms.openlocfilehash: c569eb249a583ca9f71381210eeb11a8d10b04e5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590198"
---
# <a name="overview-of-graphics"></a>Přehled grafiky
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] je aplikační programovací rozhraní (API), která tvoří subsystému operačního systému Microsoft Windows. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] je zodpovědná za zobrazení informací na obrazovkách a tiskárny. Jak název napovídá, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] je nástupcem [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], Graphics Device Interface zahrnuté ve starších verzích Windows.  
  
## <a name="managed-class-interface"></a>Spravované třídy rozhraní  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Rozhraní API je k dispozici prostřednictvím sady tříd nasadit jako spravovaný kód. Tato sada třídy se nazývá *spravovanou třídu rozhraní* k [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]. Následující obory názvů tvoří rozhraní spravovanou třídu:  
  
-   <xref:System.Drawing>  
  
-   <xref:System.Drawing.Drawing2D>  
  
-   <xref:System.Drawing.Imaging>  
  
-   <xref:System.Drawing.Text>  
  
-   <xref:System.Drawing.Printing>  
  
 S Graphics Device Interface jako například [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], aniž byste museli mít obavy o podrobnostech konkrétní zobrazovací zařízení můžete zobrazit informace na obrazovce nebo tiskárny. Programátor provede volání do metody poskytované [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] třídy. Tyto metody zase volání odpovídající ovladače pro konkrétní zařízení. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] insulates aplikace od hardwaru grafiky. Je tato izolace, která umožňuje programátorem na vytvoření aplikace nezávislých na zařízení.  
  
## <a name="see-also"></a>Viz také:
- [Přehled grafiky](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)
