---
title: 'Postupy: Nastavení a vracení kalendářních dat pomocí ovládacího prvku Windows Forms DateTimePicker'
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
ms.openlocfilehash: 12b3147e19868a1ad742fe6ddc49ffc152ecf991
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638137"
---
# <a name="how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control"></a>Postupy: Nastavení a vracení kalendářních dat pomocí ovládacího prvku Windows Forms DateTimePicker
Aktuálně vybrané datum a čas ve Windows Forms <xref:System.Windows.Forms.DateTimePicker> ovládací prvek závisí <xref:System.Windows.Forms.DateTimePicker.Value%2A> vlastnost. Můžete nastavit <xref:System.Windows.Forms.DateTimePicker.Value%2A> vlastnost předtím, než se zobrazí ovládací prvek (například v době návrhu nebo v formuláře <xref:System.Windows.Forms.Form.Load> událostí) k určení, která data se původně výběr v ovládacím prvku. Ve výchozím nastavení, ovládací prvek na <xref:System.Windows.Forms.DateTimePicker.Value%2A> je nastavena na aktuální datum. Pokud změníte ovládacího prvku <xref:System.Windows.Forms.DateTimePicker.Value%2A> v kódu, se automaticky aktualizuje ovládací prvek na formuláři tak, aby odrážela nové nastavení.  
  
 <xref:System.Windows.Forms.DateTimePicker.Value%2A> Vrátí vlastnost <xref:System.DateTime> strukturu jako jeho hodnotu. Existuje několik vlastností <xref:System.DateTime> struktura, která vrátí konkrétní informace o zobrazené datum. Tyto vlastnosti lze použít pouze k vrácení hodnoty; Nepoužívejte je pro nastavení hodnoty.  
  
- Pro hodnoty data <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>, a <xref:System.DateTime.Year%2A> vlastnosti vrací celočíselných hodnot pro tyto časové jednotky vybraným datem. <xref:System.DateTime.DayOfWeek%2A> Vlastnost vrací hodnotu, která vybraný den v týdnu (možné hodnoty jsou uvedeny v <xref:System.DayOfWeek> výčet).  
  
- Pro časové hodnoty <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>, a <xref:System.DateTime.Millisecond%2A> vlastnosti vrací celočíselných hodnot pro tyto časové jednotky. Pokud chcete nakonfigurovat ovládací prvek pro zobrazení doby, najdete v článku [jak: Zobrazení času pomocí ovládacího prvku DateTimePicker](how-to-display-time-with-the-datetimepicker-control.md).  
  
### <a name="to-set-the-date-and-time-value-of-the-control"></a>Chcete-li nastavit hodnoty data a času ovládacího prvku  
  
- Nastavte <xref:System.Windows.Forms.DateTimePicker.Value%2A> vlastnost na hodnotu data a času.  
  
    ```vb  
    DateTimePicker1.Value = New DateTime(2001, 10, 20)  
    ```  
  
    ```csharp  
    dateTimePicker1.Value = new DateTime(2001, 10, 20);  
    ```  
  
    ```cpp  
    dateTimePicker1->Value = DateTime(2001, 10, 20);  
    ```  
  
### <a name="to-return-the-date-and-time-value"></a>K vrácení hodnoty data a času  
  
- Volání <xref:System.Windows.Forms.DateTimePicker.Text%2A> vlastnost vrátí celou hodnotu jako ve formátu v ovládacím prvku nebo volání metody odpovídající <xref:System.Windows.Forms.DateTimePicker.Value%2A> vlastnost vrátí část hodnoty. Použití <xref:System.Windows.Forms.DateTimePicker.ToString%2A> informace převést na řetězec, který je možné zobrazit uživateli.  
  
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
