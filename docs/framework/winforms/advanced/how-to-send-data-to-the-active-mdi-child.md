---
title: 'Postupy: Odesílání dat do aktivního podřízeného MDI'
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
ms.openlocfilehash: dab72d64cdd013125ae7c302ccf297ecdc0c98b3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589909"
---
# <a name="how-to-send-data-to-the-active-mdi-child"></a><span data-ttu-id="adad5-102">Postupy: Odesílání dat do aktivního podřízeného MDI</span><span class="sxs-lookup"><span data-stu-id="adad5-102">How to: Send Data to the Active MDI Child</span></span>
<span data-ttu-id="adad5-103">Často, v rámci kontextu [aplikace rozhraní více dokumentů (MDI)](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md), budete muset odeslat data na aktivní podřízené okno, například když uživatel vloží dat ze schránky do aplikace MDI.</span><span class="sxs-lookup"><span data-stu-id="adad5-103">Often, within the context of [Multiple-Document Interface (MDI) Applications](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md), you will need to send data to the active child window, such as when the user pastes data from the Clipboard into an MDI application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="adad5-104">Informace o ověření, které podřízené okno má fokus a odesílat její obsah do schránky, naleznete v tématu [určení podřízeného prvku aktivního MDI](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md).</span><span class="sxs-lookup"><span data-stu-id="adad5-104">For information about verifying which child window has focus and sending its contents to the Clipboard, see [Determining the Active MDI Child](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md).</span></span>  
  
### <a name="to-send-data-to-the-active-mdi-child-window-from-the-clipboard"></a><span data-ttu-id="adad5-105">K odesílání dat na aktivní podřízené okno MDI ze schránky</span><span class="sxs-lookup"><span data-stu-id="adad5-105">To send data to the active MDI child window from the Clipboard</span></span>  
  
1.  <span data-ttu-id="adad5-106">V rámci metody zkopírujte text do schránky k aktivním ovládacím prvkem aktivní podřízený formulář.</span><span class="sxs-lookup"><span data-stu-id="adad5-106">Within a method, copy the text on the Clipboard to the active control of the active child form.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="adad5-107">Tento příklad předpokládá, že je nadřazený formulář MDI (`Form1`), který má jeden nebo více podřízených oken MDI obsahující <xref:System.Windows.Forms.RichTextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="adad5-107">This example assumes there is an MDI parent form (`Form1`) that has one or more MDI child windows containing a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="adad5-108">Další informace najdete v tématu [vytváření nadřazených formulářů MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md).</span><span class="sxs-lookup"><span data-stu-id="adad5-108">For more information, see [Creating MDI Parent Forms](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="adad5-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="adad5-109">See also</span></span>
- [<span data-ttu-id="adad5-110">Aplikace MDI (Multiple-Document Interface)</span><span class="sxs-lookup"><span data-stu-id="adad5-110">Multiple-Document Interface (MDI) Applications</span></span>](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="adad5-111">Postupy: Vytváření nadřazených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="adad5-111">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="adad5-112">Postupy: Vytváření podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="adad5-112">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="adad5-113">Postupy: Určení podřízeného prvku aktivního MDI</span><span class="sxs-lookup"><span data-stu-id="adad5-113">How to: Determine the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="adad5-114">Postupy: Uspořádání podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="adad5-114">How to: Arrange MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
