---
title: FontDialog – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- FontDialog
helpviewer_keywords:
- Font dialog box [Windows Forms], Windows Forms
- Font dialog box
- FontDialog component [Windows Forms], about FontDialog component
ms.assetid: daf46e57-1b4b-4b7a-bad0-b50ca7ba75dc
ms.openlocfilehash: 3a4707ffe471161988d0526ce0908b37299f3e07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="fontdialog-component-overview-windows-forms"></a>FontDialog – přehled komponenty (Windows Forms)
Windows Forms <xref:System.Windows.Forms.FontDialog> součást je předem nakonfigurovaný dialogové okno, což je standardní Windows **písma** dialogové okno používá ke zveřejnění písma, které jsou aktuálně nainstalovány v systému. Použití v rámci aplikace systému Windows jako jednoduchým řešením pro výběr písma místo dialogové okno Vlastní konfigurace.  
  
 Ve výchozím nastavení, dialogové okno zobrazí seznamy pro písmo, styl písma a velikost; Zaškrtávací políčka důsledky jako přeškrtnutí a podtržení; rozevírací seznam pro skript; a ukázka vzhled písma. (Skript odkazuje jiný znak skripty, které jsou k dispozici pro dané písmo, například hebrejština nebo japonština.) Chcete-li zobrazit dialogové okno písmo, zavolejte <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metoda.  
  
## <a name="key-properties"></a>Klíčové vlastnosti  
 Součást má několik vlastností, které konfigurují její vzhled. Vlastnosti, které nastavit možnosti – dialogové okno se <xref:System.Windows.Forms.FontDialog.Font%2A> a <xref:System.Windows.Forms.FontDialog.Color%2A>. <xref:System.Windows.Forms.FontDialog.Font%2A> Vlastnost nastaví písmo, styl, velikost, skript a efekty; například `Arial, 10pt, style=Italic, Strikeout`.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.FontDialog>  
 [Komponenta FontDialog](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md)
