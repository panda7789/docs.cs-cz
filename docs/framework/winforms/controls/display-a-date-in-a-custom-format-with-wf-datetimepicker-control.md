---
title: Zobrazení data ve vlastním formátu pomocí ovládacího prvku DateTimePicker
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DateTimePicker control [Windows Forms], display styles
- examples [Windows Forms], DateTimePicker control
- dates [Windows Forms], displaying in DateTimePicker control
ms.assetid: 39767691-2d2b-46b6-a663-b7901e581a6e
ms.openlocfilehash: a27dbe737b81af86c0ac50b791bcd87bafe05b4f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745930"
---
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a>Postupy: Zobrazení data ve vlastním formátu pomocí ovládacího prvku Windows Forms DateTimePicker
Ovládací prvek model Windows Forms <xref:System.Windows.Forms.DateTimePicker> poskytuje flexibilitu při formátování zobrazení dat a časů v ovládacím prvku. Vlastnost <xref:System.Windows.Forms.DateTimePicker.Format%2A> umožňuje vybrat z předdefinovaných formátů, které jsou uvedeny v <xref:System.Windows.Forms.DateTimePickerFormat>. Pokud žádný z těchto důvodů není pro vaše účely vhodný, můžete vytvořit vlastní styl formátu pomocí znaků formátu uvedených v <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.  
  
### <a name="to-display-a-custom-format"></a>Zobrazení vlastního formátu  
  
1. Vlastnost <xref:System.Windows.Forms.DateTimePicker.Format%2A> nastavte na hodnotu `DateTimePickerFormat.Custom`.  
  
2. Nastavte vlastnost <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> na řetězec formátu.  
  
    ```vb  
    DateTimePicker1.Format = DateTimePickerFormat.Custom  
    ' Display the date as "Mon 27 Feb 2012".  
    DateTimePicker1.CustomFormat = "ddd dd MMM yyyy"  
    ```  
  
    ```csharp  
    dateTimePicker1.Format = DateTimePickerFormat.Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1.CustomFormat = "ddd dd MMM yyyy";  
    ```  
  
    ```cpp  
    dateTimePicker1->Format = DateTimePickerFormat::Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1->CustomFormat = "ddd dd MMM yyyy";  
    ```  
  
### <a name="to-add-text-to-the-formatted-value"></a>Přidání textu do naformátované hodnoty  
  
1. Použijte jednoduché uvozovky k uzavření libovolného znaku, který není formátovacím znakem, jako je "M" nebo oddělovače jako ":". Například řetězec formátu níže zobrazuje aktuální datum ve formátu "dnes je: 05:30:31 pátek, v. března 2012" v jazykové verzi English (USA).  
  
    ```vb  
    DateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy"  
    ```  
  
    ```csharp  
    dateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
    ```  
  
    ```cpp  
    dateTimePicker1->CustomFormat =  
       "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
    ```  
  
     V závislosti na nastavení jazykové verze se může změnit libovolný znak, který není uzavřen v jednoduchých uvozovkách. Například řetězec formátu uvedený výše zobrazuje aktuální datum ve formátu "dnes je: 05:30:31 pátek, březen 02, 2012" v jazykové verzi anglické (USA). Všimněte si, že první dvojtečka je uzavřena v jednoduchých uvozovkách, protože není určena jako znak odložení, protože je v "hh: mm: SS". V jiné jazykové verzi se formát může zobrazit jako "dnes je: 05.30.31 pátek, březen 02, 2012".  
  
## <a name="see-also"></a>Viz také

- [Ovládací prvek DateTimePicker](datetimepicker-control-windows-forms.md)
- [Postupy: Nastavení a vracení kalendářních dat pomocí ovládacího prvku Windows Forms DateTimePicker](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
