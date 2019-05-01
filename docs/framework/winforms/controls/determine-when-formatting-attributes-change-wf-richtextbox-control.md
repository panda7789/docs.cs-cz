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
ms.openlocfilehash: a90affde9de36f1c83d5b7c21b40580cdf53402e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972286"
---
# <a name="how-to-determine-when-formatting-attributes-change-in-the-windows-forms-richtextbox-control"></a>Postupy: Určení momentu změny atributů formátování v ovládacím prvku Windows Forms RichTextBox
Běžné použití prvku modelu Windows Forms <xref:System.Windows.Forms.RichTextBox> ovládací prvek je formátování textu s atributy, jako jsou možnosti písma nebo styly odstavce. Vaše aplikace může potřebovat udržovat přehled o všechny změny v textu formátování pro účely zobrazení panelu nástrojů, jako v mnoha aplikacích pro zpracování textu.  
  
### <a name="to-respond-to-changes-in-formatting-attributes"></a>Reakce na změny atributů formátování  
  
1. Napište kód v <xref:System.Windows.Forms.RichTextBox.SelectionChanged> obslužné rutiny události k provedení příslušné akce v závislosti na hodnotě atributu. Následující příklad změní vzhled tlačítka panelu nástrojů v závislosti na hodnotu <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> vlastnost. Tlačítko panelu nástrojů budou aktualizováni, pouze když se kurzor přesune v ovládacím prvku.  
  
     Následující příklad předpokládá formulář s <xref:System.Windows.Forms.RichTextBox> ovládacího prvku a <xref:System.Windows.Forms.ToolBar> ovládací prvek, který obsahuje tlačítka panelu nástrojů. Další informace o panelech nástrojů a tlačítka panelu nástrojů najdete v tématu [jak: Přidání tlačítek do ovládacího prvku ToolBar](how-to-add-buttons-to-a-toolbar-control.md).  
  
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
