---
title: "Postupy: Určení podřízeného prvku aktivního MDI"
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
helpviewer_keywords:
- Clipboard [Windows Forms], copying data to
- MDI [Windows Forms], child windows
- child forms
- MDI [Windows Forms], activating forms
- MDI [Windows Forms], locating focus
ms.assetid: 33880ec3-0207-4c2b-a616-ff140443cc0f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c026df631c2ac033594ea86887bb8440a6aa240a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-the-active-mdi-child"></a><span data-ttu-id="11d91-102">Postupy: Určení podřízeného prvku aktivního MDI</span><span class="sxs-lookup"><span data-stu-id="11d91-102">How to: Determine the Active MDI Child</span></span>
<span data-ttu-id="11d91-103">V některých případech budete chtít zadat příkaz, který funguje na ovládací prvek, který má právě fokus na formuláři aktuálně aktivních podřízených.</span><span class="sxs-lookup"><span data-stu-id="11d91-103">On occasion, you will want to provide a command that operates on the control that has focus on the currently active child form.</span></span> <span data-ttu-id="11d91-104">Předpokládejme například, že chcete kopírovat vybraný text z textového pole podřízené formuláře do schránky.</span><span class="sxs-lookup"><span data-stu-id="11d91-104">For example, suppose you want to copy selected text from the child form's text box to the Clipboard.</span></span> <span data-ttu-id="11d91-105">By vytvoření procedury, která zkopíruje vybraný text do schránky pomocí <xref:System.Windows.Forms.Control.Click> událostí kopírovat položky nabídky v nabídce standardní upravit.</span><span class="sxs-lookup"><span data-stu-id="11d91-105">You would create a procedure that copies selected text to the Clipboard using the <xref:System.Windows.Forms.Control.Click> event of the Copy menu item on the standard Edit menu.</span></span>  
  
 <span data-ttu-id="11d91-106">Vzhledem k tomu, že aplikace MDI může mít velký počet instancí stejného formuláře podřízené, postup je potřeba vědět, jaký typ používat.</span><span class="sxs-lookup"><span data-stu-id="11d91-106">Because an MDI application can have many instances of the same child form, the procedure needs to know which form to use.</span></span> <span data-ttu-id="11d91-107">Pokud chcete zadat správném tvaru, použijte <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> vlastnost, která vrací podřízené formuláře v aktivním nebo který byl nedávno aktivní.</span><span class="sxs-lookup"><span data-stu-id="11d91-107">To specify the correct form, use the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, which returns the child form that has the focus or that was most recently active.</span></span>  
  
 <span data-ttu-id="11d91-108">Pokud máte několik ovládací prvky ve formuláři, musíte také určit, které řízení je aktivní.</span><span class="sxs-lookup"><span data-stu-id="11d91-108">When you have several controls on a form, you also need to specify which control is active.</span></span> <span data-ttu-id="11d91-109">Podobně jako <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> vlastnost, <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> vlastnost vrací s fokusem ovládacího prvku na formuláři aktivních podřízených.</span><span class="sxs-lookup"><span data-stu-id="11d91-109">Like the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, the <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> property returns the control with the focus on the active child form.</span></span> <span data-ttu-id="11d91-110">Následující postup ukazuje postup kopírování, kterou lze volat z podřízené formuláře nabídky, nabídky na formuláře MDI nebo tlačítka panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="11d91-110">The procedure below illustrates a copy procedure that can be called from a child form menu, a menu on the MDI form, or a toolbar button.</span></span>  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a><span data-ttu-id="11d91-111">K určení aktivního podřízeného MDI (Chcete-li do schránky zkopírujte jeho text)</span><span class="sxs-lookup"><span data-stu-id="11d91-111">To determine the active MDI child (to copy its text to the Clipboard)</span></span>  
  
1.  <span data-ttu-id="11d91-112">V rámci metodu zkopírujte text active ovládacího prvku formuláře aktivních podřízených do schránky.</span><span class="sxs-lookup"><span data-stu-id="11d91-112">Within a method, copy the text of the active control of the active child form to the Clipboard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="11d91-113">Příklad předpokládá, že je nadřazené formuláře MDI (`Form1`) má jednu nebo více podřízených oken MDI obsahující <xref:System.Windows.Forms.RichTextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="11d91-113">This example assumes there is an MDI parent form (`Form1`) that has one or more MDI child windows containing a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="11d91-114">Další informace najdete v tématu [vytváření nadřazených formulářů MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md).</span><span class="sxs-lookup"><span data-stu-id="11d91-114">For more information, see [Creating MDI Parent Forms](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="11d91-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="11d91-115">See Also</span></span>  
 [<span data-ttu-id="11d91-116">Aplikace MDI (Multiple-Document Interface)</span><span class="sxs-lookup"><span data-stu-id="11d91-116">Multiple-Document Interface (MDI) Applications</span></span>](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [<span data-ttu-id="11d91-117">Postupy: Vytváření nadřazených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="11d91-117">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="11d91-118">Postupy: Vytváření podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="11d91-118">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="11d91-119">Postupy: Odesílání dat do aktivního podřízeného MDI</span><span class="sxs-lookup"><span data-stu-id="11d91-119">How to: Send Data to the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 [<span data-ttu-id="11d91-120">Postupy: Uspořádání podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="11d91-120">How to: Arrange MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
