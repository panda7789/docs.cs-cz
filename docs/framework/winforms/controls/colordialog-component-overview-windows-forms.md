---
title: ColorDialog – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
ms.openlocfilehash: 9b4fb545a2ed35a9c7bad5e28c28d3ec42870860
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="colordialog-component-overview-windows-forms"></a>ColorDialog – přehled komponenty (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ColorDialog> součást je předem nakonfigurovaný dialogové okno umožňuje uživateli vybrat barvu z paletu a pro přidání do této palety vlastních barev. Je stejné, které vidíte v dalších dialogových oken aplikace pro systém Windows a vyberte barvy. Ji použijte v rámci aplikace systému Windows jako simple řešení místo dialogové okno Vlastní konfigurace.  
  
 Barva vybraná v dialogovém okně je vrácený v <xref:System.Windows.Forms.ColorDialog.Color%2A> vlastnost. Pokud <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> je nastavena na `false`, tlačítko "Definovat vlastní barvy" je zakázána a uživatel je omezen na předdefinované barvy palety. Pokud <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> je nastavena na `true`, uživatel nemůže vybrat tónovaná barvy. Pokud chcete zobrazit dialogové okno, musí volat jeho <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metoda.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ColorDialog>  
 [Komponenta ColorDialog](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)  
 [Ovládací prvky a součásti dialogového okna](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)  
 [Postupy: Změna vzhledu komponenty Windows Forms ColorDialog](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
