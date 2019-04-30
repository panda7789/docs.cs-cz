---
title: 'Postupy: Určení aktivního podřízeného formuláře MDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Clipboard [Windows Forms], copying data to
- MDI [Windows Forms], child windows
- child forms
- MDI [Windows Forms], activating forms
- MDI [Windows Forms], locating focus
ms.assetid: 33880ec3-0207-4c2b-a616-ff140443cc0f
ms.openlocfilehash: 9b70824670b8f47a2346135cb31ad39bd55694d1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937550"
---
# <a name="how-to-determine-the-active-mdi-child"></a><span data-ttu-id="80d10-102">Postupy: Určení aktivního podřízeného formuláře MDI</span><span class="sxs-lookup"><span data-stu-id="80d10-102">How to: Determine the Active MDI Child</span></span>
<span data-ttu-id="80d10-103">V některých případech budete chtít zadat příkaz, který funguje na ovládací prvek, který má fokus na aktuálně aktivní podřízený formulář.</span><span class="sxs-lookup"><span data-stu-id="80d10-103">On occasion, you will want to provide a command that operates on the control that has focus on the currently active child form.</span></span> <span data-ttu-id="80d10-104">Předpokládejme například, že chcete Zkopírování vybraného textu do schránky z podřízeného formuláře, textového pole.</span><span class="sxs-lookup"><span data-stu-id="80d10-104">For example, suppose you want to copy selected text from the child form's text box to the Clipboard.</span></span> <span data-ttu-id="80d10-105">Vytvoříte procedury, která zkopíruje vybraný text do schránky pomocí <xref:System.Windows.Forms.Control.Click> události položky nabídky kopírování ve standardní nabídce Úpravy.</span><span class="sxs-lookup"><span data-stu-id="80d10-105">You would create a procedure that copies selected text to the Clipboard using the <xref:System.Windows.Forms.Control.Click> event of the Copy menu item on the standard Edit menu.</span></span>  
  
 <span data-ttu-id="80d10-106">Protože aplikace MDI může mít mnoho instancí stejné podřízeného formuláře, postup je potřeba vědět, jaký tvar používat.</span><span class="sxs-lookup"><span data-stu-id="80d10-106">Because an MDI application can have many instances of the same child form, the procedure needs to know which form to use.</span></span> <span data-ttu-id="80d10-107">Chcete-li určit správný tvar, použijte <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> vlastnost, která vrací podřízeného formuláře, který má fokus nebo, který byl nedávno aktivní.</span><span class="sxs-lookup"><span data-stu-id="80d10-107">To specify the correct form, use the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, which returns the child form that has the focus or that was most recently active.</span></span>  
  
 <span data-ttu-id="80d10-108">Až budete mít několik ovládacích prvků ve formuláři, musíte také určit, který ovládací prvek je aktivní.</span><span class="sxs-lookup"><span data-stu-id="80d10-108">When you have several controls on a form, you also need to specify which control is active.</span></span> <span data-ttu-id="80d10-109">Podobně jako <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> vlastnost, <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> vrátí vlastnost ovládacího prvku se zaměřuje na aktivní podřízený formulář.</span><span class="sxs-lookup"><span data-stu-id="80d10-109">Like the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, the <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> property returns the control with the focus on the active child form.</span></span> <span data-ttu-id="80d10-110">Následující postup ukazuje kopírování procedury, která může být volána z podřízených nabídky formuláře nabídek MDI formuláře nebo tlačítko panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="80d10-110">The procedure below illustrates a copy procedure that can be called from a child form menu, a menu on the MDI form, or a toolbar button.</span></span>  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a><span data-ttu-id="80d10-111">K určení podřízeného prvku aktivního MDI (ke zkopírování textu do schránky.)</span><span class="sxs-lookup"><span data-stu-id="80d10-111">To determine the active MDI child (to copy its text to the Clipboard)</span></span>  
  
1. <span data-ttu-id="80d10-112">V rámci metody zkopírujte text aktivním ovládacím prvkem aktivní podřízený formulář do schránky.</span><span class="sxs-lookup"><span data-stu-id="80d10-112">Within a method, copy the text of the active control of the active child form to the Clipboard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="80d10-113">Tento příklad předpokládá, že je nadřazený formulář MDI (`Form1`), který má jeden nebo více podřízených oken MDI obsahující <xref:System.Windows.Forms.RichTextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="80d10-113">This example assumes there is an MDI parent form (`Form1`) that has one or more MDI child windows containing a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="80d10-114">Další informace najdete v tématu [vytváření nadřazených formulářů MDI](how-to-create-mdi-parent-forms.md).</span><span class="sxs-lookup"><span data-stu-id="80d10-114">For more information, see [Creating MDI Parent Forms](how-to-create-mdi-parent-forms.md).</span></span>  
  
    ```vb  
    Public Sub mniCopy_Click(ByVal sender As Object, _  
       ByVal e As System.EventArgs) Handles mniCopy.Click  
  
       ' Determine the active child form.  
       Dim activeChild As Form = Me.ActiveMDIChild  
  
       ' If there is an active child form, find the active control, which  
       ' in this example should be a RichTextBox.  
       If (Not activeChild Is Nothing) Then  
          Dim theBox As RichTextBox = _  
            TryCast(activeChild.ActiveControl, RichTextBox)  
  
          If (Not theBox Is Nothing) Then  
             'Put selected text on Clipboard.  
             Clipboard.SetDataObject(theBox.SelectedText)  
          Else  
             MessageBox.Show("You need to select a RichTextBox.")  
          End If  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    protected void mniCopy_Click (object sender, System.EventArgs e)  
    {  
       // Determine the active child form.  
       Form activeChild = this.ActiveMdiChild;  
  
       // If there is an active child form, find the active control, which  
       // in this example should be a RichTextBox.  
       if (activeChild != null)  
       {    
          try  
          {  
             RichTextBox theBox = (RichTextBox)activeChild.ActiveControl;  
             if (theBox != null)  
             {  
                // Put the selected text on the Clipboard.  
                Clipboard.SetDataObject(theBox.SelectedText);  
  
             }  
          }  
          catch  
          {  
             MessageBox.Show("You need to select a RichTextBox.");  
          }  
       }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="80d10-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="80d10-115">See also</span></span>

- [<span data-ttu-id="80d10-116">Aplikace MDI (Multiple-Document Interface)</span><span class="sxs-lookup"><span data-stu-id="80d10-116">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="80d10-117">Postupy: Vytváření nadřazených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="80d10-117">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="80d10-118">Postupy: Vytváření podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="80d10-118">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="80d10-119">Postupy: Odesílání dat do aktivního podřízeného MDI</span><span class="sxs-lookup"><span data-stu-id="80d10-119">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="80d10-120">Postupy: Uspořádání podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="80d10-120">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
