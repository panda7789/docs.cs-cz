---
title: 'Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], insertion point
- insertion points [Windows Forms], TextBox controls
- text boxes [Windows Forms], controlling insertion point
ms.assetid: 5bee7d34-5121-429e-ab1f-d8ff67bc74c1
ms.openlocfilehash: 1fa6e8a3642086f81d0a62502d801ec6ade9b3d1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110713"
---
# <a name="how-to-control-the-insertion-point-in-a-windows-forms-textbox-control"></a>Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox
Když prvku Windows Forms <xref:System.Windows.Forms.TextBox> ovládací prvek nejprve dostane fokus, je výchozí kurzor v textovém poli na levé straně jakýkoli existující text. Uživatel může přesunout kurzor pomocí klávesnice nebo myši. Pokud textové pole ztratí a potom získá fokus, kurzor se všude, kde uživatel naposledy vložili.  
  
 V některých případech může být toto chování zneklidňovat uživateli. V textovém editoru aplikace, uživatel může očekávat, že znaky nového objevovat po jakýkoli existující text. V aplikaci vstupní data uživatel může očekávat znaky nového nahradit všechny existující položky. <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> a <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> vlastnosti umožňují změnit chování při vyhovovaly vašim konkrétním potřebám.  
  
### <a name="to-control-the-insertion-point-in-a-textbox-control"></a>K řízení místa vložení v ovládacím prvku TextBox  
  
1.  Nastavte <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> vlastnost na odpovídající hodnotu. Nula umístí kurzor bezprostředně nalevo od prvního znaku.  
  
2.  (Volitelné) Nastavte <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> vlastnost Délka textu, kterou chcete vybrat.  
  
     Následující kód vždy vrátí kurzor na hodnotu 0. `TextBox1_Enter` Obslužné rutiny události musí být vázán na ovládací prvek; další informace naleznete v tématu [vytváření obslužných rutin událostí ve Windows Forms](../creating-event-handlers-in-windows-forms.md).  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       TextBox1.SelectionStart = 0  
       TextBox1.SelectionLength = 0  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_Enter(Object sender, System.EventArgs e) {  
       textBox1.SelectionStart = 0;  
       textBox1.SelectionLength = 0;  
    }  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = 0;  
       }  
    ```  
  
## <a name="making-the-insertion-point-visible-by-default"></a>Ve výchozím nastavení zviditelnění kurzor  
 <xref:System.Windows.Forms.TextBox> Viditelné ve výchozím nastavení nového formuláře pouze tehdy, pokud je kurzor <xref:System.Windows.Forms.TextBox> ovládací prvek je první v pořadí. V opačném případě se zobrazí kurzor pouze v případě, že přidělíte <xref:System.Windows.Forms.TextBox> fokusu pomocí klávesnice nebo myši.  
  
#### <a name="to-make-the-text-box-insertion-point-visible-by-default-on-a-new-form"></a>Ke zviditelnění pole kurzor text ve výchozím nastavení nový formulář  
  
-   Nastavte <xref:System.Windows.Forms.TextBox> ovládacího prvku <xref:System.Windows.Forms.Control.TabIndex%2A> vlastnost `0`.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.TextBox>
- [Přehled ovládacího prvku TextBox](textbox-control-overview-windows-forms.md)
- [Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Postupy: Vytvoření textového pole určeného jen pro čtení](how-to-create-a-read-only-text-box-windows-forms.md)
- [Postupy: Vkládání uvozovek do řetězce](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [Ovládací prvek TextBox](textbox-control-windows-forms.md)
