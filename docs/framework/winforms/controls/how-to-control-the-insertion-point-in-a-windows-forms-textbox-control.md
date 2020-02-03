---
title: Řízení bodu vložení v ovládacím prvku TextBox
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
ms.openlocfilehash: fd4803820921f0c922a4ce885f809abee8fd4c6c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742204"
---
# <a name="how-to-control-the-insertion-point-in-a-windows-forms-textbox-control"></a>Postupy: Řízení bodu pro vkládání v ovládacím prvku Windows Forms TextBox
Když ovládací prvek model Windows Forms <xref:System.Windows.Forms.TextBox> první dostane fokus, výchozí vložení v textovém poli je nalevo od existujícího textu. Uživatel může přesunout bod vložení pomocí klávesnice nebo myši. Pokud textové pole ztratí a pak znovu získá fokus, bude kurzor místo, kde ho uživatel naposledy umístil.  
  
 V některých případech může být toto chování ve vzájemném objednání uživatele. V aplikaci pro zpracování textu může uživatel očekávat, že se nové znaky objeví po jakémkoli existujícím textu. V aplikaci pro zadávání dat může uživatel očekávat, že nové znaky nahradí existující položku. Vlastnosti <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> a <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> umožňují upravit chování tak, aby vyhovovalo vašemu účelu.  
  
### <a name="to-control-the-insertion-point-in-a-textbox-control"></a>Řízení bodu vložení v ovládacím prvku TextBox  
  
1. Vlastnost <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> nastavte na odpovídající hodnotu. Nula umístí kurzor hned nalevo od prvního znaku.  
  
2. Volitelné Vlastnost <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> nastavte na délku textu, který chcete vybrat.  
  
     Následující kód vždy vrátí kurzor na hodnotu 0. Obslužná rutina události `TextBox1_Enter` musí být svázána s ovládacím prvkem. Další informace naleznete v tématu [vytváření obslužných rutin událostí v model Windows Forms](../creating-event-handlers-in-windows-forms.md).  
  
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
  
## <a name="making-the-insertion-point-visible-by-default"></a>Zpřístupnění bodu vložení ve výchozím nastavení  
 <xref:System.Windows.Forms.TextBox> vkládání je ve výchozím nastavení viditelné pouze v případě, že je ovládací prvek <xref:System.Windows.Forms.TextBox> nejprve v pořadí prvků. V opačném případě se místo vložení zobrazí pouze v případě, že <xref:System.Windows.Forms.TextBox> fokus poskytnete buď pomocí klávesnice, nebo pomocí myši.  
  
#### <a name="to-make-the-text-box-insertion-point-visible-by-default-on-a-new-form"></a>Chcete-li, aby byl textový rámeček ve výchozím nastavení viditelný v novém formuláři  
  
- Nastavte vlastnost <xref:System.Windows.Forms.Control.TabIndex%2A> <xref:System.Windows.Forms.TextBox>ho ovládacího prvku na hodnotu `0`.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.TextBox>
- [Přehled ovládacího prvku TextBox](textbox-control-overview-windows-forms.md)
- [Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Postupy: Vytvoření textového pole určeného jen pro čtení](how-to-create-a-read-only-text-box-windows-forms.md)
- [Postupy: Vkládání uvozovek do řetězce](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [Ovládací prvek TextBox](textbox-control-windows-forms.md)
