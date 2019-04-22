---
title: TextBox – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TextBox
helpviewer_keywords:
- TextBox control [Windows Forms], about TextBox controls
- text boxes [Windows Forms], adding
ms.assetid: d1a9c7f5-fa53-480a-a75c-158f8649ea2f
ms.openlocfilehash: a91b67df1071c79707bb20a68efb4d5e6f083ae0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59162134"
---
# <a name="textbox-control-overview-windows-forms"></a>TextBox – přehled ovládacího prvku (Windows Forms)
Windows Forms textová pole se používají k získání vstupy od uživatele nebo k zobrazení textu. <xref:System.Windows.Forms.TextBox> Ovládací prvek se obecně používají pro upravitelný text, i když ji můžete také nastavit jen pro čtení. Textová pole můžete zobrazit více řádků, zalamovat text, který má velikost ovládacího prvku a přidat základní formátování. <xref:System.Windows.Forms.TextBox> Řízení poskytuje jeden formát styl textu zobrazit nebo zadat do ovládacího prvku. Chcete-li zobrazit více typů formátovaný text, použijte <xref:System.Windows.Forms.RichTextBox> ovládacího prvku. Další informace najdete v tématu [RichTextBox – Přehled ovládacího prvku](richtextbox-control-overview-windows-forms.md).  
  
## <a name="working-with-the-textbox-control"></a>Práce s ovládacím prvkem textového pole  
 Text zobrazený ovládacím prvkem je součástí <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost. Ve výchozím nastavení můžete zadat maximálně 2048 znaků v textovém poli. Pokud jste nastavili <xref:System.Windows.Forms.TextBox.Multiline%2A> vlastnost `true`, můžete zadat až 32 KB textu. <xref:System.Windows.Forms.TextBox.Text%2A> Vlastnost lze nastavit v době návrhu pomocí okna vlastnosti v době běhu v kódu, nebo uživatelského vstupu v době běhu. Je možné načíst aktuální obsah textového pole za běhu v článku <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost.  
  
 Následující příklad kódu nastaví text v ovládacím prvku v době běhu. `InitializeMyControl` Postup nespustí automaticky, musí být volána.  
  
```vb  
Private Sub InitializeMyControl()  
   ' Put some text into the control first.  
   TextBox1.Text = "This is a TextBox control."  
End Sub  
```  
  
```csharp  
private void InitializeMyControl() {  
   // Put some text into the control first.  
   textBox1.Text = "This is a TextBox control.";  
}  
```  
  
```cpp  
private:  
   void InitializeMyControl()  
   {  
      // Put some text into the control first.  
      textBox1->Text = "This is a TextBox control.";  
   }  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.TextBox>
- [Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Postupy: Vytvoření pole jen pro čtení textu](how-to-create-a-read-only-text-box-windows-forms.md)
- [Postupy: Vkládání uvozovek do řetězce](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Postupy: Zobrazit více řádků v ovládacím prvku Windows Forms TextBox](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [Ovládací prvek TextBox](textbox-control-windows-forms.md)
