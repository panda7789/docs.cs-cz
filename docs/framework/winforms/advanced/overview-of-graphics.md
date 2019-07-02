---
title: Přehled grafiky
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using managed interface
- graphics [Windows Forms], about graphics
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
ms.openlocfilehash: f0e2fd9dcf31e5fdce16b5a3b6fd21eab6eab66a
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505319"
---
# <a name="overview-of-graphics"></a>Přehled grafiky
Rozhraní GDI + je aplikační programovací rozhraní (API), která tvoří subsystému operačního systému Microsoft Windows. Rozhraní GDI + je zodpovědná za zobrazení informací na obrazovkách a tiskárny. Jak název napovídá, rozhraní GDI + je nástupcem GDI Graphics Device Interface zahrnuté ve starších verzích Windows.  
  
## <a name="managed-class-interface"></a>Spravované třídy rozhraní  
 Rozhraní API je přístupný prostřednictvím sady tříd nasadit jako spravovaný kód. Tato sada třídy se nazývá *spravovanou třídu rozhraní* do rozhraní GDI +. Následující obory názvů tvoří rozhraní spravovanou třídu:  
  
- <xref:System.Drawing>  
  
- <xref:System.Drawing.Drawing2D>  
  
- <xref:System.Drawing.Imaging>  
  
- <xref:System.Drawing.Text>  
  
- <xref:System.Drawing.Printing>  
  
 S Graphics Device Interface, jako je například rozhraní GDI + můžete zobrazit informace na obrazovce nebo tiskárny, nemusíte mít obavy o podrobnostech konkrétní zobrazovací zařízení. Programátor volá metody poskytované objektem třídy rozhraní GDI +. Tyto metody zase volání odpovídající ovladače pro konkrétní zařízení. Rozhraní GDI + insulates aplikace od hardwaru grafiky. Je tato izolace, která umožňuje programátorem na vytvoření aplikace nezávislých na zařízení.  
  
## <a name="see-also"></a>Viz také:

- [Přehled grafiky](graphics-overview-windows-forms.md)
