---
title: FontDialog – přehled komponenty
ms.date: 03/30/2017
f1_keywords:
- FontDialog
helpviewer_keywords:
- Font dialog box [Windows Forms], Windows Forms
- Font dialog box
- FontDialog component [Windows Forms], about FontDialog component
ms.assetid: daf46e57-1b4b-4b7a-bad0-b50ca7ba75dc
ms.openlocfilehash: 664b756dc068ca283e4f43edbdd0f3266f5d1142
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745701"
---
# <a name="fontdialog-component-overview-windows-forms"></a>FontDialog – přehled komponenty (Windows Forms)
Komponenta model Windows Forms <xref:System.Windows.Forms.FontDialog> je předem nakonfigurovaným dialogovým oknem, které je standardním dialogovým oknem **písma** systému Windows, které slouží k vystavení písem, která jsou aktuálně nainstalována v systému. Použijte ho v rámci aplikace pro Windows jako jednoduché řešení pro výběr písem namísto konfigurace vlastního dialogového okna.  
  
 Ve výchozím nastavení se v dialogovém okně zobrazují pole pro písmo, styl písma a velikost; zaškrtávací políčka pro efekty jako přeškrtnutí a podtržení; rozevírací seznam pro skript; a ukázku, jak se písmo zobrazí. (Skript odkazuje na jiné znakové skripty, které jsou k dispozici pro dané písmo, například hebrejština nebo japonština.) Chcete-li zobrazit dialogové okno písmo, zavolejte metodu <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>.  
  
## <a name="key-properties"></a>Klíčové vlastnosti  
 Komponenta má několik vlastností, které konfigurují její vzhled. Vlastnosti, které nastavují výběry dialogových oken, jsou <xref:System.Windows.Forms.FontDialog.Font%2A> a <xref:System.Windows.Forms.FontDialog.Color%2A>. Vlastnost <xref:System.Windows.Forms.FontDialog.Font%2A> nastaví písmo, styl, velikost, skript a efekty; například `Arial, 10pt, style=Italic, Strikeout`.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.FontDialog>
- [Komponenta FontDialog](fontdialog-component-windows-forms.md)
