---
title: 'Postupy: Určení momentu změny atributů formátování v ovládacím prvku Windows Forms RichTextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], text boxes
- RichTextBox control [Windows Forms], determining font changes
- text boxes [Windows Forms], determining font changes
- SelChange event
ms.assetid: bdfed015-f77a-41e5-b38f-f8629b2fa166
ms.openlocfilehash: 789a0a25c65185b101ef427ff62871fa490c7f1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-determine-when-formatting-attributes-change-in-the-windows-forms-richtextbox-control"></a>Postupy: Určení momentu změny atributů formátování v ovládacím prvku Windows Forms RichTextBox
Běžně se používají Windows Forms <xref:System.Windows.Forms.RichTextBox> ovládací prvek je formátování textu s atributy, jako je například možnosti písma nebo styly odstavce. Aplikace může vyžadovat můžete sledovat všechny změny v textu formátování pro účely zobrazení panelu nástrojů, jako v mnoha aplikacích pro zpracování textu.  
  
### <a name="to-respond-to-changes-in-formatting-attributes"></a>Reakce na změny atributů formátování  
  
1.  Psaní kódu <xref:System.Windows.Forms.RichTextBox.SelectionChanged> obslužné rutiny události k provedení příslušné akce v závislosti na hodnotě atributu. Následující příklad změní vzhled tlačítka panelu nástrojů v závislosti na hodnotě <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> vlastnost. Tlačítka panelu nástrojů budou aktualizováni, pouze pokud je přesunut bod vložení v ovládacím prvku.  
  
     Následující příklad předpokládá formulář s <xref:System.Windows.Forms.RichTextBox> řízení a <xref:System.Windows.Forms.ToolBar> ovládací prvek, který obsahuje tlačítka panelu nástrojů. Další informace o panelech nástrojů a tlačítka panelu nástrojů najdete v tématu [postupy: přidání tlačítek do ovládacího prvku panel nástrojů](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md).  
  
    ```vb  
    ' The following code assumes the existence of a toolbar control  
    ' with at least one toolbar button.  
    Private Sub RichTextBox1_SelectionChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles RichTextBox1.SelectionChanged  
       If RichTextBox1.SelectionBullet = True Then  
          ' Bullet button on toolbar should appear pressed  
          ToolBarButton1.Pushed = True  
       Else  
           ' Bullet button on toolbar should appear unpressed  
           ToolBarButton1.Pushed = False  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    // The following code assumes the existence of a toolbar control  
    // with at least one toolbar button.  
    private void richTextBox1_SelectionChanged(object sender,  
    System.EventArgs e)  
    {  
       if (richTextBox1.SelectionBullet == true)   
       {  
          // Bullet button on toolbar should appear pressed  
          toolBarButton1.Pushed = true;  
       }  
       else   
       {  
          // Bullet button on toolbar should appear unpressed  
          toolBarButton1.Pushed = false;  
       }  
    }  
    ```  
  
    ```cpp  
    // The following code assumes the existence of a toolbar control  
    // with at least one toolbar button.  
    private:  
       System::Void richTextBox1_SelectionChanged(  
          System::Object ^  sender, System::EventArgs ^  e)  
       {  
          if (richTextBox1->SelectionBullet == true)  
          {  
             // Bullet button on toolbar should appear pressed  
             toolBarButton1->Pushed = true;  
          }  
          else  
          {  
             // Bullet button on toolbar should appear unpressed  
             toolBarButton1->Pushed = false;  
          }  
       }  
    ```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.RichTextBox.SelectionChanged>  
 <xref:System.Windows.Forms.RichTextBox>  
 [Ovládací prvek RichTextBox](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Ovládací prvky používané ve Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
