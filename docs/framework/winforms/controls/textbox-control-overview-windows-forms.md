---
title: TextBox – přehled ovládacího prvku
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
ms.openlocfilehash: 06ab460d720d17331881b5ba653263160eaf3cb3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742804"
---
# <a name="textbox-control-overview-windows-forms"></a>TextBox – přehled ovládacího prvku (Windows Forms)
Textová pole model Windows Forms slouží k získání vstupu od uživatele nebo k zobrazení textu. <xref:System.Windows.Forms.TextBox> ovládací prvek se obecně používá pro upravitelný text, i když ho lze také nastavit jen pro čtení. Textová pole mohou zobrazovat více řádků, zalamovat text podle velikosti ovládacího prvku a přidat základní formátování. Ovládací prvek <xref:System.Windows.Forms.TextBox> poskytuje jeden styl formátu pro text zobrazený nebo zadaný do ovládacího prvku. Chcete-li zobrazit více typů formátovaného textu, použijte ovládací prvek <xref:System.Windows.Forms.RichTextBox>. Další informace najdete v tématu [Přehled ovládacího prvku RichTextBox](richtextbox-control-overview-windows-forms.md).  
  
## <a name="working-with-the-textbox-control"></a>Práce s ovládacím prvkem TextBox  
 Text zobrazený ovládacím prvkem je obsažen ve vlastnosti <xref:System.Windows.Forms.TextBox.Text%2A>. Ve výchozím nastavení můžete do textového pole zadat až 2048 znaků. Pokud nastavíte vlastnost <xref:System.Windows.Forms.TextBox.Multiline%2A> na hodnotu `true`, můžete zadat až 32 KB textu. Vlastnost <xref:System.Windows.Forms.TextBox.Text%2A> lze nastavit v době návrhu pomocí okna vlastnosti, v době spuštění v kódu nebo uživatelským vstupem v době běhu. Aktuální obsah textového pole lze načíst za běhu načtením vlastnosti <xref:System.Windows.Forms.TextBox.Text%2A>.  
  
 Následující příklad kódu nastaví text v ovládacím prvku v době běhu. Postup `InitializeMyControl` nebude proveden automaticky; musí být volána.  
  
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
- [Postupy: Vytvoření textového pole určeného jen pro čtení](how-to-create-a-read-only-text-box-windows-forms.md)
- [Postupy: Vkládání uvozovek do řetězce](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [Ovládací prvek TextBox](textbox-control-windows-forms.md)
