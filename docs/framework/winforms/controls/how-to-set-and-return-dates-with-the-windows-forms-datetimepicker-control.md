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
ms.openlocfilehash: 017224aa493bfe0cd519df482a4d00e16f889a1a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535666"
---
# <a name="how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control"></a>Postupy: Nastavení a vracení kalendářních dat pomocí ovládacího prvku Windows Forms DateTimePicker
Aktuálně vybrané data a času v systému Windows Forms <xref:System.Windows.Forms.DateTimePicker> je dáno ovládacího prvku <xref:System.Windows.Forms.DateTimePicker.Value%2A> vlastnost. Můžete nastavit <xref:System.Windows.Forms.DateTimePicker.Value%2A> předtím, než se zobrazí ovládací prvek (například v době návrhu nebo formuláře <xref:System.Windows.Forms.Form.Load> událostí) k určení, datum, pro které bude zpočátku vybrali v ovládacím prvku. Ve výchozím nastavení, ovládacího prvku na <xref:System.Windows.Forms.DateTimePicker.Value%2A> nastavena na aktuální datum. Pokud změníte ovládacího prvku <xref:System.Windows.Forms.DateTimePicker.Value%2A> v kódu, se automaticky aktualizuje ovládací prvek na formuláři, aby odrážela nové nastavení.  
  
 <xref:System.Windows.Forms.DateTimePicker.Value%2A> Vlastnost vrátí <xref:System.DateTime> struktura jako jeho hodnotu. Existuje několik vlastností, které <xref:System.DateTime> struktura, která vrátí konkrétní informace o zobrazené datum. Tyto vlastnosti slouží pouze k vrácení hodnoty; Nepoužívejte je nastavte hodnotu.  
  
-   Pro hodnoty data <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>, a <xref:System.DateTime.Year%2A> vlastnosti, vrátí celé číslo hodnoty pro tyto časové jednotky vybraným datem. <xref:System.DateTime.DayOfWeek%2A> Vlastnost vrací hodnotu, která určuje vybraný den v týdnu (možné hodnoty jsou uvedeny v <xref:System.DayOfWeek> výčet).  
  
-   Pro hodnoty času <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>, a <xref:System.DateTime.Millisecond%2A> vlastnosti vrátí celé číslo hodnoty těchto časových jednotek. Konfigurovat ovládací prvek zobrazí dobu, najdete v tématu [postupy: zobrazení času pomocí ovládacího prvku DateTimePicker](../../../../docs/framework/winforms/controls/how-to-display-time-with-the-datetimepicker-control.md).  
  
### <a name="to-set-the-date-and-time-value-of-the-control"></a>Chcete-li nastavit hodnoty data a času ovládacího prvku  
  
-   Nastavte <xref:System.Windows.Forms.DateTimePicker.Value%2A> vlastnost na hodnotu data a času.  
  
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
  
-   Volání <xref:System.Windows.Forms.DateTimePicker.Text%2A> vlastnost, která má vrátit celou hodnotu jako formátované v ovládacím prvku nebo volejte příslušnou metodu <xref:System.Windows.Forms.DateTimePicker.Value%2A> vlastnost vrátit část hodnoty. Použití <xref:System.Windows.Forms.DateTimePicker.ToString%2A> informace převést na řetězec, který lze zobrazit uživateli.  
  
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
 [Ovládací prvek DateTimePicker](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)  
 [Postupy: Zobrazení data ve vlastním formátu pomocí ovládacího prvku Windows Forms DateTimePicker](../../../../docs/framework/winforms/controls/display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)
