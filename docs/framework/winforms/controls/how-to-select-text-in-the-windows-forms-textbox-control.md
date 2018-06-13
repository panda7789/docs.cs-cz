---
title: 'Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], selecting text programmatically
- text boxes [Windows Forms], selecting text programmatically
- text [Windows Forms], selecting in text boxes programmatically
ms.assetid: 8c591546-6a01-45c7-8e03-f78431f903b1
ms.openlocfilehash: 8fd1cfb0764d16b86cd639d8266d1cceff874932
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536690"
---
# <a name="how-to-select-text-in-the-windows-forms-textbox-control"></a>Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox
Můžete vybrat text prostřednictvím kódu programu v systému Windows Forms <xref:System.Windows.Forms.TextBox> ovládacího prvku. Například pokud vytvoříte funkci, která hledá text pro určitý řetězec, můžete vybrat text, který má vizuální upozornění čtečky nalezen řetězec pozici.  
  
### <a name="to-select-text-programmatically"></a>Výběr textu prostřednictvím kódu programu  
  
1.  Nastavte <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> vlastnost na začátek textu, který chcete vybrat.  
  
     <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> Vlastnost je číslo, které určuje bod vložení v rámci textový řetězec, se 0 znamená pozici nejvíce vlevo. Pokud <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> je nastavena na hodnotu rovna nebo větší než počet znaků v textovém poli, za poslední znak je umístěn kurzor.  
  
2.  Nastavte <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> vlastnost, která má délku textu, kterou chcete vybrat.  
  
     <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> Vlastnost je číselnou hodnotu, která nastaví šířku kurzoru. Nastavení <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> na číslo větší než 0 způsobí, že tento počet znaků, který má být vybrán, od aktuální kurzor.  
  
3.  (Volitelné) Přístup k vybraný text prostřednictvím <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> vlastnost.  
  
     Kód pod vybere obsahu textového pole, kdy ovládacího prvku <xref:System.Windows.Forms.Control.Enter> dojde k události. Tento příklad zkontroluje, zda textového pole má hodnotu <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost, která není `null` nebo prázdný řetězec. Když bude vybrán, textového pole, je vybrána aktuální text v textovém poli. `TextBox1_Enter` Obslužné rutiny události musí být vázána k ovládacímu prvku; další informace naleznete v tématu [postupy: vytváření obslužných rutin událostí spustit čas pro Windows Forms](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
     K testování v tomto příkladu, stiskněte klávesu Tabulátor, dokud textové pole je aktivní. Pokud kliknete na tlačítko do textového pole, je text nezaškrtnuté.  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       If (Not String.IsNullOrEmpty(TextBox1.Text)) Then  
          TextBox1.SelectionStart = 0  
          TextBox1.SelectionLength = TextBox1.Text.Length  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_Enter(object sender, System.EventArgs e){  
       if (!String.IsNullOrEmpty(textBox1.Text))  
       {  
          textBox1.SelectionStart = 0;  
          textBox1.SelectionLength = textBox1.Text.Length;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^ sender,  
          System::EventArgs ^ e) {  
       if (!System::String::IsNullOrEmpty(textBox1->Text))  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = textBox1->Text->Length;  
       }  
    }  
    ```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.TextBox>  
 [Přehled ovládacího prvku TextBox](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [Postupy: Vytvoření textového pole určeného jen pro čtení](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [Postupy: Vkládání uvozovek do řetězce](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [Ovládací prvek TextBox](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
