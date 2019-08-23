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
ms.openlocfilehash: 0a7a2475891488d1fdd60f0db4a483c144a73f0d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947845"
---
# <a name="how-to-send-data-to-the-active-mdi-child"></a>Postupy: Odesílání dat do aktivního podřízeného formuláře MDI
V rámci kontextu [aplikací rozhraní MDI (Multiple Document Interface)](multiple-document-interface-mdi-applications.md)je často potřeba odeslat data do aktivního podřízeného okna, například když uživatel vloží data ze schránky do aplikace MDI.  
  
> [!NOTE]
> Informace o ověření, které podřízené okno má fokus a který odesílá obsah do schránky, naleznete v tématu [určení aktivního podřízeného prvku MDI](how-to-determine-the-active-mdi-child.md).  
  
### <a name="to-send-data-to-the-active-mdi-child-window-from-the-clipboard"></a>Odeslání dat do aktivního podřízeného okna MDI ze schránky  
  
1. V rámci metody zkopírujte text ve schránce do aktivního ovládacího prvku aktivního podřízeného formuláře.  
  
    > [!NOTE]
    > Tento příklad předpokládá, že existuje nadřazený formulář MDI (`Form1`), který obsahuje jeden nebo více podřízených oken MDI <xref:System.Windows.Forms.RichTextBox> obsahující ovládací prvek. Další informace najdete v tématu [Vytváření nadřazených formulářů MDI](how-to-create-mdi-parent-forms.md).  
  
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
- [Postupy: Vytvoření nadřazených formulářů MDI](how-to-create-mdi-parent-forms.md)
- [Postupy: Vytvořit podřízené formuláře MDI](how-to-create-mdi-child-forms.md)
- [Postupy: Zjistit aktivní podřízenou položku MDI](how-to-determine-the-active-mdi-child.md)
- [Postupy: Uspořádat podřízené formuláře MDI](how-to-arrange-mdi-child-forms.md)
