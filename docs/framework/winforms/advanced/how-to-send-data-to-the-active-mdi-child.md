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
# <a name="how-to-send-data-to-the-active-mdi-child"></a><span data-ttu-id="5b2ec-102">Postupy: Odesílání dat do aktivního podřízeného formuláře MDI</span><span class="sxs-lookup"><span data-stu-id="5b2ec-102">How to: Send Data to the Active MDI Child</span></span>
<span data-ttu-id="5b2ec-103">V rámci kontextu [aplikací rozhraní MDI (Multiple Document Interface)](multiple-document-interface-mdi-applications.md)je často potřeba odeslat data do aktivního podřízeného okna, například když uživatel vloží data ze schránky do aplikace MDI.</span><span class="sxs-lookup"><span data-stu-id="5b2ec-103">Often, within the context of [Multiple-Document Interface (MDI) Applications](multiple-document-interface-mdi-applications.md), you will need to send data to the active child window, such as when the user pastes data from the Clipboard into an MDI application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5b2ec-104">Informace o ověření, které podřízené okno má fokus a který odesílá obsah do schránky, naleznete v tématu [určení aktivního podřízeného prvku MDI](how-to-determine-the-active-mdi-child.md).</span><span class="sxs-lookup"><span data-stu-id="5b2ec-104">For information about verifying which child window has focus and sending its contents to the Clipboard, see [Determining the Active MDI Child](how-to-determine-the-active-mdi-child.md).</span></span>  
  
### <a name="to-send-data-to-the-active-mdi-child-window-from-the-clipboard"></a><span data-ttu-id="5b2ec-105">Odeslání dat do aktivního podřízeného okna MDI ze schránky</span><span class="sxs-lookup"><span data-stu-id="5b2ec-105">To send data to the active MDI child window from the Clipboard</span></span>  
  
1. <span data-ttu-id="5b2ec-106">V rámci metody zkopírujte text ve schránce do aktivního ovládacího prvku aktivního podřízeného formuláře.</span><span class="sxs-lookup"><span data-stu-id="5b2ec-106">Within a method, copy the text on the Clipboard to the active control of the active child form.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5b2ec-107">Tento příklad předpokládá, že existuje nadřazený formulář MDI (`Form1`), který obsahuje jeden nebo více podřízených oken MDI <xref:System.Windows.Forms.RichTextBox> obsahující ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="5b2ec-107">This example assumes there is an MDI parent form (`Form1`) that has one or more MDI child windows containing a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="5b2ec-108">Další informace najdete v tématu [Vytváření nadřazených formulářů MDI](how-to-create-mdi-parent-forms.md).</span><span class="sxs-lookup"><span data-stu-id="5b2ec-108">For more information, see [Creating MDI Parent Forms](how-to-create-mdi-parent-forms.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5b2ec-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5b2ec-109">See also</span></span>

- [<span data-ttu-id="5b2ec-110">Aplikace MDI (Multiple-Document Interface)</span><span class="sxs-lookup"><span data-stu-id="5b2ec-110">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="5b2ec-111">Postupy: Vytvoření nadřazených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="5b2ec-111">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="5b2ec-112">Postupy: Vytvořit podřízené formuláře MDI</span><span class="sxs-lookup"><span data-stu-id="5b2ec-112">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="5b2ec-113">Postupy: Zjistit aktivní podřízenou položku MDI</span><span class="sxs-lookup"><span data-stu-id="5b2ec-113">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="5b2ec-114">Postupy: Uspořádat podřízené formuláře MDI</span><span class="sxs-lookup"><span data-stu-id="5b2ec-114">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
