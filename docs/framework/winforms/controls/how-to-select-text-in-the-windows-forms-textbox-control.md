---
title: Výběr textu v ovládacím prvku TextBox
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
ms.openlocfilehash: 8a32e40f14ddae6f8ddcaa6d62337329df6fde26
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745316"
---
# <a name="how-to-select-text-in-the-windows-forms-textbox-control"></a>Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox
Můžete vybrat text programově v ovládacím prvku model Windows Forms <xref:System.Windows.Forms.TextBox>. Například pokud vytvoříte funkci, která vyhledává text konkrétního řetězce, můžete vybrat text, který vizuálně upozorní čtenáře nalezené pozice řetězce.  
  
### <a name="to-select-text-programmatically"></a>Výběr textu prostřednictvím kódu programu  
  
1. Vlastnost <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> nastavte na začátek textu, který chcete vybrat.  
  
     Vlastnost <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> je číslo, které označuje pozici kurzoru v řetězci textu, přičemž 0 je největší pozice vlevo. Pokud je vlastnost <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> nastavena na hodnotu větší nebo rovna počtu znaků v textovém poli, je kurzor umístěn za posledním znakem.  
  
2. Vlastnost <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> nastavte na délku textu, který chcete vybrat.  
  
     Vlastnost <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> je číselná hodnota, která nastavuje šířku bodu vložení. Nastavení <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> na číslo větší než 0 způsobí, že počet znaků, které mají být vybrány, počínaje aktuálním místem vložení.  
  
3. Volitelné Přístup k vybranému textu prostřednictvím vlastnosti <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A>.  
  
     Následující kód vybírá obsah textového pole, když dojde k události <xref:System.Windows.Forms.Control.Enter> ovládacího prvku. Tento příklad kontroluje, zda má textové pole hodnotu vlastnosti <xref:System.Windows.Forms.TextBox.Text%2A>, která není `null` nebo prázdný řetězec. Když textové pole dostane fokus, je vybrán aktuální text v textovém poli. Obslužná rutina události `TextBox1_Enter` musí být svázána s ovládacím prvkem. Další informace naleznete v tématu [Postupy: vytváření obslužných rutin událostí v době běhu pro model Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
     Chcete-li otestovat tento příklad, stiskněte klávesu TAB, dokud textové pole nemá fokus. Pokud kliknete na textové pole, text nebude vybrán.  
  
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
