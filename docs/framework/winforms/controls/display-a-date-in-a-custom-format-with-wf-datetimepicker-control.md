---
title: 'Postupy: Zobrazení data ve vlastním formátu pomocí ovládacího prvku Windows Forms DateTimePicker'
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
ms.openlocfilehash: 0c454580c6f3aa1fadb6e98d2ee715da948364b1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59192989"
---
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a>Postupy: Zobrazení data ve vlastním formátu pomocí ovládacího prvku Windows Forms DateTimePicker
Windows Forms <xref:System.Windows.Forms.DateTimePicker> ovládacího prvku poskytuje flexibilitu při formátování zobrazení dat a časů v ovládacím prvku. <xref:System.Windows.Forms.DateTimePicker.Format%2A> Vlastnost vám umožní vybrat z předdefinovaných formátů, uvedené v <xref:System.Windows.Forms.DateTimePickerFormat>. Pokud žádná z nich je vhodný pro vaše potřeby, můžete vytvořit vlastní styl formátování pomocí formátu znaky uvedené v <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.  
  
### <a name="to-display-a-custom-format"></a>K zobrazení vlastního formátu  
  
1.  Nastavte <xref:System.Windows.Forms.DateTimePicker.Format%2A> vlastnost `DateTimePickerFormat.Custom`.  
  
2.  Nastavte <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> nastavte na řetězec formátu.  
  
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
  
### <a name="to-add-text-to-the-formatted-value"></a>Chcete-li přidat text formátovaná hodnota  
  
1.  Pomocí jednoduchých uvozovek uzavřete libovolný znak, který není znak formátu jako "M" nebo oddělovač, jako je ":". Například řetězec formátu níže zobrazí aktuální datum ve formátu "Dnes je: 05:30:31. března pátek 02, 2012" v jazykové verze Angličtina (Spojené státy).  
  
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
  
     V závislosti na nastavení jazykové verze, nejspíš se změní všechny znaky, není uzavřen v jednoduchých uvozovkách. Například řetězec formátu výše zobrazuje aktuální datum ve formátu "Dnes je: 05:30:31. března pátek 02, 2012" v jazykové verze Angličtina (Spojené státy). Protože ale nemají být oddělovací znak je "hh: mm:", mějte na paměti, že první dvojtečku uzavřen v jednoduchých uvozovkách. V jiné jazykové verze, může být ve formátu zobrazí jako "Dnes je: 05.30.31 pátek březen 02, 2012".  
  
## <a name="see-also"></a>Viz také:

- [Ovládací prvek DateTimePicker](datetimepicker-control-windows-forms.md)
- [Postupy: Nastavení a vracení kalendářních dat pomocí ovládacího prvku Windows Forms DateTimePicker](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
