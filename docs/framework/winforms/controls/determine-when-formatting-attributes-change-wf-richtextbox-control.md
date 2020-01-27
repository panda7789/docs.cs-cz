---
title: Určení, kdy se mění atributy formátování v ovládacím prvku RichTextBox
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
ms.openlocfilehash: f9b2a1028f79059ec7d4d6bf3683100455bb5dea
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746046"
---
# <a name="how-to-determine-when-formatting-attributes-change-in-the-windows-forms-richtextbox-control"></a>Postupy: Určení momentu změny atributů formátování v ovládacím prvku Windows Forms RichTextBox
Běžné použití ovládacího prvku model Windows Forms <xref:System.Windows.Forms.RichTextBox> formátuje text s atributy, jako jsou možnosti písma nebo Odstavcové styly. Vaše aplikace může potřebovat sledovat všechny změny formátování textu pro účely zobrazení panelu nástrojů, stejně jako v mnoha aplikacích pro zpracování textu.  
  
### <a name="to-respond-to-changes-in-formatting-attributes"></a>Reakce na změny atributů formátování  
  
1. Napište kód v obslužné rutině události <xref:System.Windows.Forms.RichTextBox.SelectionChanged> k provedení příslušné akce v závislosti na hodnotě atributu. Následující příklad změní vzhled tlačítka panelu nástrojů v závislosti na hodnotě vlastnosti <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A>. Tlačítko panelu nástrojů bude aktualizováno pouze v případě, že je v ovládacím prvku přesunut kurzor.  
  
     Následující příklad předpokládá, že formulář obsahuje ovládací prvek <xref:System.Windows.Forms.RichTextBox> a ovládací prvek <xref:System.Windows.Forms.ToolBar>, který obsahuje tlačítko panelu nástrojů. Další informace o panelech nástrojů a tlačítkách panelu nástrojů naleznete v tématu [How to: Add Buttons on a Toolbar Control](how-to-add-buttons-to-a-toolbar-control.md).  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.RichTextBox.SelectionChanged>
- <xref:System.Windows.Forms.RichTextBox>
- [Ovládací prvek RichTextBox](richtextbox-control-windows-forms.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
