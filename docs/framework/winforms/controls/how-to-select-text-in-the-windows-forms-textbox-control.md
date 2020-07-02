---
title: Výběr textu v ovládacím prvku TextBox
description: Naučte se, jak vybrat text programově v ovládacím prvku model Windows Forms TextBox. Také se dozvíte, jak vizuálně upozornit čtenáře pozice nalezeného řetězce.
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
ms.openlocfilehash: b8fdaff76461c4d6766dfc6afaef5e814d982834
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621558"
---
# <a name="how-to-select-text-in-the-windows-forms-textbox-control"></a>Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox
Text můžete v ovládacím prvku model Windows Forms vybrat programově <xref:System.Windows.Forms.TextBox> . Například pokud vytvoříte funkci, která vyhledává text konkrétního řetězce, můžete vybrat text, který vizuálně upozorní čtenáře nalezené pozice řetězce.  
  
### <a name="to-select-text-programmatically"></a>Výběr textu prostřednictvím kódu programu  
  
1. Nastavte <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> vlastnost na začátek textu, který chcete vybrat.  
  
     <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A>Vlastnost je číslo, které označuje pozici kurzoru v řetězci textu, přičemž 0 je největší pozice vlevo. Pokud <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> je vlastnost nastavena na hodnotu větší nebo rovna počtu znaků v textovém poli, je kurzor umístěn za posledním znakem.  
  
2. Nastavte <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> vlastnost na délku textu, který chcete vybrat.  
  
     <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A>Vlastnost je číselná hodnota, která nastavuje šířku bodu vložení. Nastavení <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> na číslo větší než 0 způsobí, že počet znaků, který má být vybrán, počínaje aktuálním místem vložení.  
  
3. Volitelné Přístup k vybranému textu prostřednictvím <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> Vlastnosti.  
  
     Následující kód vybírá obsah textového pole, když dojde k události ovládacího prvku <xref:System.Windows.Forms.Control.Enter> . Tento příklad kontroluje, zda textové pole má hodnotu pro <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost, která není nebo je `null` prázdným řetězcem. Když textové pole dostane fokus, je vybrán aktuální text v textovém poli. `TextBox1_Enter`Obslužná rutina události musí být svázána s ovládacím prvkem. Další informace naleznete v tématu [How to: Create event handlers za běhu pro model Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
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
- [TextBox – ovládací prvek](textbox-control-windows-forms.md)
