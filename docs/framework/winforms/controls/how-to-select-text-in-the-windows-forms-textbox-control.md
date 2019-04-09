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
ms.openlocfilehash: f96ac69f16eefb5bf4a0625ff83e207c289a105b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111433"
---
# <a name="how-to-select-text-in-the-windows-forms-textbox-control"></a>Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox
Text můžete vybrat programově v rozhraní Windows Forms <xref:System.Windows.Forms.TextBox> ovládacího prvku. Pokud vytvoříte funkci, která hledá text pro určitý řetězec, můžete vybrat text, který má vizuální upozornění čtečky nalezený řetězec pozici.  
  
### <a name="to-select-text-programmatically"></a>Chcete-li vybrat text prostřednictvím kódu programu  
  
1.  Nastavte <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> vlastnost na začátek textu, který chcete vybrat.  
  
     <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> Vlastnost je číslo, které označuje kurzor do textového řetězce, s 0 se pozice nejvíce vlevo. Pokud <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> je nastavena na hodnotu roven nebo větší než počet znaků v textovém poli, kurzor je umístěn za posledním znakem.  
  
2.  Nastavte <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> vlastnost Délka textu, kterou chcete vybrat.  
  
     <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> Vlastnost má číselnou hodnotu, která nastavuje šířku kurzor. Nastavení <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> na číslo větší než 0 způsobí, že se tento počet znaků, které mají být vybrán, od z do aktuálního místa vložení.  
  
3.  (Volitelné) Přístup prostřednictvím vybraný text <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> vlastnost.  
  
     Kód uvedený níže vybere obsah textového pole, když ovládací prvek <xref:System.Windows.Forms.Control.Enter> dojde k události. Tento příklad kontroluje, jestli do textového pole má hodnotu <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost, která není `null` nebo prázdný řetězec. Když bude vybrán, do textového pole, je vybrána aktuální text v textovém poli. `TextBox1_Enter` Obslužné rutiny události musí být vázán na ovládací prvek; další informace naleznete v tématu [jak: Vytváření obslužných rutin událostí pro Windows Forms v době běhu](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
     K otestování v tomto příkladu, stiskněte klávesu Tab, dokud do textového pole má fokus. Pokud kliknete do textového pole, text byl zrušen výběr cesty.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.TextBox>
- [Přehled ovládacího prvku TextBox](textbox-control-overview-windows-forms.md)
- [Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Postupy: Vytvoření textového pole určeného jen pro čtení](how-to-create-a-read-only-text-box-windows-forms.md)
- [Postupy: Vkládání uvozovek do řetězce](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [Ovládací prvek TextBox](textbox-control-windows-forms.md)
