---
title: "TextBox – přehled ovládacího prvku (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4d7312246c43157ca9cd6c7b41d2b110586721c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="textbox-control-overview-windows-forms"></a>TextBox – přehled ovládacího prvku (Windows Forms)
Windows Forms textová pole se používají k získání vstup od uživatele nebo k zobrazení textu. <xref:System.Windows.Forms.TextBox> Řízení se obecně používají pro upravovat text, i když ho můžete také provést jen pro čtení. Textová pole můžete zobrazit více řádků, zalomení textu velikosti ovládacího prvku a přidat základní formátování. <xref:System.Windows.Forms.TextBox> Řízení poskytuje jeden formát styl textu zobrazuje nebo je zadán do ovládacího prvku. Chcete-li zobrazit více typů formátovaný text, použijte <xref:System.Windows.Forms.RichTextBox> ovládacího prvku. Další informace najdete v tématu [– Přehled ovládacího prvku RichTextBox](../../../../docs/framework/winforms/controls/richtextbox-control-overview-windows-forms.md).  
  
## <a name="working-with-the-textbox-control"></a>Práce s ovládacím prvku TextBox  
 Je součástí textu zobrazovaného ovládacím prvkem <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost. Ve výchozím nastavení můžete zadat až 2048 znaků v textovém poli. Pokud nastavíte <xref:System.Windows.Forms.TextBox.Multiline%2A> vlastnost `true`, můžete zadat až 32 KB textu. <xref:System.Windows.Forms.TextBox.Text%2A> Vlastnost lze nastavit v době návrhu pomocí okna vlastností v době běhu v kódu, nebo uživatelského vstupu v době běhu. Aktuální obsahu textového pole můžete získat v době běhu čtením <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost.  
  
 Následující příklad kódu nastaví text v ovládacím prvku za běhu. `InitializeMyControl` Postup nebude automaticky spustit; musí být volána.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.TextBox>  
 [Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [Postupy: Vytvoření textového pole určeného jen pro čtení](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [Postupy: Vkládání uvozovek do řetězce](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [Ovládací prvek TextBox](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
