---
title: Nastavit a vrátit data s ovládacím prvkem DateTimePicker
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- dates [Windows Forms], setting in DateTimePicker
- DateTimePicker control [Windows Forms], setting and returning dates
- examples [Windows Forms], DateTimePicker control
ms.assetid: a8a48d68-e4b5-426e-9764-51230fc9acd2
ms.openlocfilehash: f958097640316715b38828e72107ab5bdb9389aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141910"
---
# <a name="how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control"></a>Postupy: Nastavení a vracení kalendářních dat pomocí ovládacího prvku Windows Forms DateTimePicker
Aktuálně vybrané datum nebo čas v <xref:System.Windows.Forms.DateTimePicker> ovládacím prvku <xref:System.Windows.Forms.DateTimePicker.Value%2A> Windows Forms je určena vlastností. Vlastnost můžete <xref:System.Windows.Forms.DateTimePicker.Value%2A> nastavit před zobrazením ovládacího prvku (například v době <xref:System.Windows.Forms.Form.Load> návrhu nebo v události formuláře) a určit, které datum bude v ovládacím prvku původně vybráno. Ve výchozím nastavení <xref:System.Windows.Forms.DateTimePicker.Value%2A> je ovládací prvek nastaven na aktuální datum. Pokud změníte ovládací <xref:System.Windows.Forms.DateTimePicker.Value%2A> prvek v kódu, ovládací prvek se automaticky aktualizuje ve formuláři tak, aby odrážel nové nastavení.  
  
 Vlastnost <xref:System.Windows.Forms.DateTimePicker.Value%2A> vrátí <xref:System.DateTime> strukturu jako jeho hodnotu. Existuje několik vlastností <xref:System.DateTime> struktury, které vracejí určité informace o zobrazeném datu. Tyto vlastnosti lze použít pouze k vrácení hodnoty; nepoužívejte je k nastavení hodnoty.  
  
- Pro hodnoty kalendářních <xref:System.DateTime.Day%2A>dat <xref:System.DateTime.Year%2A> vrátí <xref:System.DateTime.Month%2A>hodnoty , a vlastnosti celé hodnoty pro tyto časové jednotky vybraného data. Vlastnost <xref:System.DateTime.DayOfWeek%2A> vrátí hodnotu označující vybraný den v týdnu (možné hodnoty jsou uvedeny ve výčtu). <xref:System.DayOfWeek>  
  
- Pro časové hodnoty <xref:System.DateTime.Hour%2A> <xref:System.DateTime.Minute%2A>vrátí <xref:System.DateTime.Second%2A>hodnoty <xref:System.DateTime.Millisecond%2A> , , a vlastnosti celé hodnoty pro tyto časové jednotky. Chcete-li nakonfigurovat ovládací prvek tak, aby zobrazoval časy, [přečtěte si informace: Zobrazení času pomocí ovládacího prvku DateTimePicker](how-to-display-time-with-the-datetimepicker-control.md).  
  
### <a name="to-set-the-date-and-time-value-of-the-control"></a>Nastavení hodnoty data a času ovládacího prvku  
  
- Nastavte <xref:System.Windows.Forms.DateTimePicker.Value%2A> vlastnost na hodnotu data nebo času.  
  
    ```vb  
    DateTimePicker1.Value = New DateTime(2001, 10, 20)  
    ```  
  
    ```csharp  
    dateTimePicker1.Value = new DateTime(2001, 10, 20);  
    ```  
  
    ```cpp  
    dateTimePicker1->Value = DateTime(2001, 10, 20);  
    ```  
  
### <a name="to-return-the-date-and-time-value"></a>Chcete-li vrátit hodnotu data a času  
  
- Volání <xref:System.Windows.Forms.DateTimePicker.Text%2A> vlastnost vrátit celou hodnotu ve formátu v ovládacím prvku <xref:System.Windows.Forms.DateTimePicker.Value%2A> nebo volání příslušné metody vlastnost vrátit část hodnoty. Slouží <xref:System.Windows.Forms.DateTimePicker.ToString%2A> k převodu informací na řetězec, který lze zobrazit uživateli.  
  
    ```vb  
    MessageBox.Show("The selected value is ", DateTimePicker1.Text)  
    MessageBox.Show("The day of the week is ",
       DateTimePicker1.Value.DayOfWeek.ToString)  
    MessageBox.Show("Millisecond is: ",
       DateTimePicker1.Value.Millisecond.ToString)  
    ```  
  
    ```csharp  
    MessageBox.Show ("The selected value is " +
       dateTimePicker1.Text);  
    MessageBox.Show ("The day of the week is " +
       dateTimePicker1.Value.DayOfWeek.ToString());  
    MessageBox.Show("Millisecond is: " +
       dateTimePicker1.Value.Millisecond.ToString());  
    ```  
  
    ```cpp  
    MessageBox::Show (String::Concat("The selected value is ",  
       dateTimePicker1->Text));  
    MessageBox::Show (String::Concat("The day of the week is ",  
       dateTimePicker1->Value.DayOfWeek.ToString()));  
    MessageBox::Show(String::Concat("Millisecond is: ",  
       dateTimePicker1->Value.Millisecond.ToString()));  
    ```  
  
## <a name="see-also"></a>Viz také

- [DateTimePicker – ovládací prvek](datetimepicker-control-windows-forms.md)
- [Postupy: Zobrazení data ve vlastním formátu pomocí ovládacího prvku Windows Forms DateTimePicker](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)
