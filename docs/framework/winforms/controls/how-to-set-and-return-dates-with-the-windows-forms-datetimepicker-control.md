---
title: Nastavení a vrácení dat pomocí ovládacího prvku DateTimePicker
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
ms.openlocfilehash: 1e0aa58e98748ccde9411f0f4871adbae3a5f14d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747111"
---
# <a name="how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control"></a>Postupy: Nastavení a vracení kalendářních dat pomocí ovládacího prvku Windows Forms DateTimePicker
Aktuálně vybrané datum nebo čas v ovládacím prvku model Windows Forms <xref:System.Windows.Forms.DateTimePicker> určuje vlastnost <xref:System.Windows.Forms.DateTimePicker.Value%2A>. Vlastnost <xref:System.Windows.Forms.DateTimePicker.Value%2A> lze nastavit před zobrazením ovládacího prvku (například v době návrhu nebo v události <xref:System.Windows.Forms.Form.Load> formuláře) k určení, které datum bude na ovládacím prvku původně vybráno. Ve výchozím nastavení je <xref:System.Windows.Forms.DateTimePicker.Value%2A> ovládacího prvku nastaven na aktuální datum. Změníte-li <xref:System.Windows.Forms.DateTimePicker.Value%2A> ovládacího prvku v kódu, bude ovládací prvek automaticky aktualizován ve formuláři tak, aby odrážel nové nastavení.  
  
 Vlastnost <xref:System.Windows.Forms.DateTimePicker.Value%2A> vrací strukturu <xref:System.DateTime> jako hodnotu. Existuje několik vlastností <xref:System.DateTime> struktury, které vracejí konkrétní informace o zobrazeném datu. Tyto vlastnosti lze použít pouze k vrácení hodnoty; Nepoužívejte je k nastavení hodnoty.  
  
- Pro hodnoty kalendářních dat vrátí <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>a <xref:System.DateTime.Year%2A> vlastnosti celočíselné hodnoty pro tyto časové jednotky vybraného data. Vlastnost <xref:System.DateTime.DayOfWeek%2A> vrací hodnotu udávající vybraný den v týdnu (možné hodnoty jsou uvedeny v <xref:System.DayOfWeek> výčtu).  
  
- Pro časové hodnoty vrací <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>a <xref:System.DateTime.Millisecond%2A> vlastnosti pro tyto časové jednotky celočíselné hodnoty. Chcete-li nakonfigurovat ovládací prvek tak, aby zobrazoval časy, přečtěte si téma [Postup: zobrazení času pomocí ovládacího prvku DateTimePicker](how-to-display-time-with-the-datetimepicker-control.md).  
  
### <a name="to-set-the-date-and-time-value-of-the-control"></a>Nastavení hodnoty data a času ovládacího prvku  
  
- Vlastnost <xref:System.Windows.Forms.DateTimePicker.Value%2A> nastavte na hodnotu datum nebo čas.  
  
    ```vb  
    DateTimePicker1.Value = New DateTime(2001, 10, 20)  
    ```  
  
    ```csharp  
    dateTimePicker1.Value = new DateTime(2001, 10, 20);  
    ```  
  
    ```cpp  
    dateTimePicker1->Value = DateTime(2001, 10, 20);  
    ```  
  
### <a name="to-return-the-date-and-time-value"></a>Vrácení hodnoty data a času  
  
- Voláním vlastnosti <xref:System.Windows.Forms.DateTimePicker.Text%2A> vrátíte celou hodnotu formátovanou v ovládacím prvku nebo zavolejte příslušnou metodu vlastnosti <xref:System.Windows.Forms.DateTimePicker.Value%2A>, která vrátí část hodnoty. Pomocí <xref:System.Windows.Forms.DateTimePicker.ToString%2A> převeďte informace na řetězec, který se může zobrazit uživateli.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Ovládací prvek DateTimePicker](datetimepicker-control-windows-forms.md)
- [Postupy: Zobrazení data ve vlastním formátu pomocí ovládacího prvku Windows Forms DateTimePicker](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)
