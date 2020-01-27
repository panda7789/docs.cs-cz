---
title: Změna vzhledu součásti ColorDialog
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ColorDialog component [Windows Forms], examples
- ColorDialog component [Windows Forms], formatting appearance
- color dialog box [Windows Forms], configuring appearance
ms.assetid: bba4e262-1cd7-4f63-89cf-330a36f7b539
ms.openlocfilehash: 0402d7f3c03a0771512a03ac54e1b093c9fe6e9b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746637"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-colordialog-component"></a>Postupy: Změna vzhledu součásti Windows Forms ColorDialog
Můžete nakonfigurovat vzhled součásti model Windows Forms <xref:System.Windows.Forms.ColorDialog> s řadou vlastností. Dialogové okno obsahuje dvě části, které zobrazují základní barvy a jeden, který uživateli umožňuje definovat vlastní barvy.  
  
 Většina vlastností omezuje barvy, které uživatel může vybrat z dialogového okna. Pokud je vlastnost <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> nastavena na hodnotu `true`, uživatel může definovat vlastní barvy. Vlastnost <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> je `true`, pokud je dialogové okno rozbaleno pro definování vlastních barev; v opačném případě musí uživatel kliknout na tlačítko "definovat vlastní barvy". Pokud je vlastnost <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> nastavena na hodnotu `true`, dialogové okno zobrazí všechny dostupné barvy v sadě základních barev. Pokud je vlastnost <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> nastavena na hodnotu `true`, uživatel nemůže vybrat rozdané barvy; pro výběr jsou k dispozici pouze plné barvy.  
  
 Pokud je vlastnost <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> nastavena na hodnotu `true`, zobrazí se v dialogovém okně tlačítko Help. Když uživatel klikne na tlačítko Help, vyvolá se událost <xref:System.Windows.Forms.CommonDialog.HelpRequest> <xref:System.Windows.Forms.ColorDialog> komponenty.  
  
### <a name="to-configure-the-appearance-of-the-color-dialog-box"></a>Konfigurace vzhledu dialogového okna Barva  
  
1. Nastavte vlastnosti <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>a <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> na požadované hodnoty.  
  
    ```vb  
    ColorDialog1.AllowFullOpen = True  
    ColorDialog1.AnyColor = True  
    ColorDialog1.SolidColorOnly = False  
    ColorDialog1.ShowHelp = True  
    ```  
  
    ```csharp  
    colorDialog1.AllowFullOpen = true;  
    colorDialog1.AnyColor = true;  
    colorDialog1.SolidColorOnly = false;  
    colorDialog1.ShowHelp = true;  
    ```  
  
    ```cpp  
    colorDialog1->AllowFullOpen = true;  
    colorDialog1->AnyColor = true;  
    colorDialog1->SolidColorOnly = false;  
    colorDialog1->ShowHelp = true;  
    ```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ColorDialog>
- [Komponenta ColorDialog](colordialog-component-windows-forms.md)
- [Přehled komponenty ColorDialog](colordialog-component-overview-windows-forms.md)
