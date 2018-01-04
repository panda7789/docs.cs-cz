---
title: "Postupy: Řízení bodu pro vkládání v ovládacím prvku Windows Forms TextBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], insertion point
- insertion points [Windows Forms], TextBox controls
- text boxes [Windows Forms], controlling insertion point
ms.assetid: 5bee7d34-5121-429e-ab1f-d8ff67bc74c1
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c8de64ac28fe57e3c448c671859053fad4aae3b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-control-the-insertion-point-in-a-windows-forms-textbox-control"></a>Postupy: Řízení bodu pro vkládání v ovládacím prvku Windows Forms TextBox
Když Windows Forms <xref:System.Windows.Forms.TextBox> řízení nejprve obdrží fokus, výchozí vložení v rámci textového pole je nalevo od existujícího textu. Kurzor s klávesnici nebo myš, může uživatel přesunout. Pokud textového pole ztratí a pak znovu získal fokus, bude bod vložení kdekoli uživatele poslední ho umístili.  
  
 V některých případech může být toto chování zneklidňovat uživateli. V textovém editoru aplikace, může uživatel očekávat nové znaků, než se objeví po existujícího textu. V aplikaci vstupní data může uživatel očekávat všechny stávající položku nahradit novou znaků. <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> a <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> vlastnosti umožňují změnit chování tak, aby vyhovovala vaší účel.  
  
### <a name="to-control-the-insertion-point-in-a-textbox-control"></a>K řízení bodu vložení v ovládacím prvku TextBox  
  
1.  Nastavte <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> vlastnost na odpovídající hodnotu. Nula umístí kurzor vlevo prvního znaku.  
  
2.  (Volitelné) Nastavte <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> vlastnost, která má délku textu, kterou chcete vybrat.  
  
     Následující kód vždy vrátí kurzor na hodnotu 0. `TextBox1_Enter` Obslužné rutiny události musí být vázána k ovládacímu prvku; další informace naleznete v tématu [vytváření obslužných rutin událostí v systému Windows Forms](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md).  
  
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
  
## <a name="making-the-insertion-point-visible-by-default"></a>Ve výchozím nastavení viditelnosti kurzoru  
 <xref:System.Windows.Forms.TextBox> Je standardně viditelné v nové jenom Pokud formuláře kurzor <xref:System.Windows.Forms.TextBox> řízení je první v pořadí. V opačném kurzoru se zobrazí pouze v případě, že přidělíte <xref:System.Windows.Forms.TextBox> fokus klávesnice nebo myš.  
  
#### <a name="to-make-the-text-box-insertion-point-visible-by-default-on-a-new-form"></a>Ke zviditelnění bodu vložení textové pole na nový formulář ve výchozím nastavení  
  
-   Nastavte <xref:System.Windows.Forms.TextBox> ovládacího prvku <xref:System.Windows.Forms.Control.TabIndex%2A> vlastnost `0`.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.TextBox>  
 [Přehled ovládacího prvku TextBox](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [Postupy: Vytvoření textového pole určeného jen pro čtení](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [Postupy: Vkládání uvozovek do řetězce](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [Ovládací prvek TextBox](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
