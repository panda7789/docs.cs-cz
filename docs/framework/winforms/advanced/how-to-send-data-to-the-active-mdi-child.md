---
title: 'Postupy: Odesílání dat do aktivního podřízeného formuláře MDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- child forms
- MDI [Windows Forms], sending data to forms
- Clipboard [Windows Forms], pasting
- Clipboard [Windows Forms], getting data from
ms.assetid: 1047d2fe-1235-46db-aad9-563aea1d743b
ms.openlocfilehash: 0ffe87d55f7325f77bd33bdbf5d5fbab9f321f93
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203324"
---
# <a name="how-to-send-data-to-the-active-mdi-child"></a>Postupy: Odesílání dat do aktivního podřízeného formuláře MDI
Často, v rámci kontextu [aplikace rozhraní více dokumentů (MDI)](multiple-document-interface-mdi-applications.md), budete muset odeslat data na aktivní podřízené okno, například když uživatel vloží dat ze schránky do aplikace MDI.  
  
> [!NOTE]
>  Informace o ověření, které podřízené okno má fokus a odesílat její obsah do schránky, naleznete v tématu [určení podřízeného prvku aktivního MDI](how-to-determine-the-active-mdi-child.md).  
  
### <a name="to-send-data-to-the-active-mdi-child-window-from-the-clipboard"></a>K odesílání dat na aktivní podřízené okno MDI ze schránky  
  
1.  V rámci metody zkopírujte text do schránky k aktivním ovládacím prvkem aktivní podřízený formulář.  
  
    > [!NOTE]
    >  Tento příklad předpokládá, že je nadřazený formulář MDI (`Form1`), který má jeden nebo více podřízených oken MDI obsahující <xref:System.Windows.Forms.RichTextBox> ovládacího prvku. Další informace najdete v tématu [vytváření nadřazených formulářů MDI](how-to-create-mdi-parent-forms.md).  
  
    ```vb  
    Public Sub mniPaste_Click(ByVal sender As Object, _  
       ByVal e As System.EventArgs) Handles mniPaste.Click  
  
       ' Determine the active child form.  
       Dim activeChild As Form = Me.ParentForm.ActiveMDIChild  
  
       ' If there is an active child form, find the active control, which  
       ' in this example should be a RichTextBox.  
       If (Not activeChild Is Nothing) Then  
          Try  
             Dim theBox As RichTextBox = Ctype(activeChild.ActiveControl, RichTextBox)  
             If (Not theBox Is Nothing) Then  
                ' Create a new instance of the DataObject interface.  
                Dim data As IDataObject = Clipboard.GetDataObject()  
                ' If the data is text, then set the text of the   
                ' RichTextBox to the text in the clipboard.  
                If (data.GetDataPresent(DataFormats.Text)) Then  
                   theBox.SelectedText = data.GetData(DataFormats.Text).ToString()  
                End If  
             End If  
          Catch  
             MessageBox.Show("You need to select a RichTextBox.")  
          End Try  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    protected void mniPaste_Click (object sender, System.EventArgs e)  
    {  
      // Determine the active child form.  
       Form activeChild = this.ParentForm.ActiveMdiChild;  
  
       // If there is an active child form, find the active control, which  
       // in this example should be a RichTextBox.  
       if (activeChild != null)  
       {  
          try   
          {  
             RichTextBox theBox = (RichTextBox)activeChild.ActiveControl;  
             if (theBox != null)  
             {  
                // Create a new instance of the DataObject interface.  
                IDataObject data = Clipboard.GetDataObject();  
                // If the data is text, then set the text of the   
                // RichTextBox to the text in the clipboard.  
                if (data.GetDataPresent(DataFormats.Text))  
                {  
                   theBox.SelectedText = data.GetData(DataFormats.Text).ToString();                 
                }  
             }  
          }  
          catch   
          {  
             MessageBox.Show("You need to select a RichTextBox.");  
          }  
       }  
    }  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Aplikace MDI (Multiple-Document Interface)](multiple-document-interface-mdi-applications.md)
- [Postupy: Vytváření nadřazených formulářů MDI](how-to-create-mdi-parent-forms.md)
- [Postupy: Vytváření podřízených formulářů MDI](how-to-create-mdi-child-forms.md)
- [Postupy: Určení aktivního podřízeného formuláře MDI](how-to-determine-the-active-mdi-child.md)
- [Postupy: Uspořádání podřízených formulářů MDI](how-to-arrange-mdi-child-forms.md)
