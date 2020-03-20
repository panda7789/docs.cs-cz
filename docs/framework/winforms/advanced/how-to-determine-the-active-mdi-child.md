---
title: 'Postupy: Určení podřízeného prvku aktivního MDI'
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
ms.openlocfilehash: 57491faa10c182630d41565ba236d65e393929b3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182549"
---
# <a name="how-to-determine-the-active-mdi-child"></a><span data-ttu-id="ec2f3-102">Postupy: Určení podřízeného prvku aktivního MDI</span><span class="sxs-lookup"><span data-stu-id="ec2f3-102">How to: Determine the Active MDI Child</span></span>
<span data-ttu-id="ec2f3-103">V některých případech budete chtít poskytnout příkaz, který pracuje na ovládací prvek, který má fokus na aktuálně aktivní podřízený formulář.</span><span class="sxs-lookup"><span data-stu-id="ec2f3-103">On occasion, you will want to provide a command that operates on the control that has focus on the currently active child form.</span></span> <span data-ttu-id="ec2f3-104">Předpokládejme například, že chcete zkopírovat vybraný text z textového pole podřízeného formuláře do schránky.</span><span class="sxs-lookup"><span data-stu-id="ec2f3-104">For example, suppose you want to copy selected text from the child form's text box to the Clipboard.</span></span> <span data-ttu-id="ec2f3-105">Vytvořili byste proceduru, která zkopíruje vybraný <xref:System.Windows.Forms.Control.Click> text do schránky pomocí události položky nabídky Kopírovat ve standardní nabídce Úpravy.</span><span class="sxs-lookup"><span data-stu-id="ec2f3-105">You would create a procedure that copies selected text to the Clipboard using the <xref:System.Windows.Forms.Control.Click> event of the Copy menu item on the standard Edit menu.</span></span>  
  
 <span data-ttu-id="ec2f3-106">Vzhledem k tomu, že aplikace MDI může mít mnoho instancí stejnépodřízené ho formuláře, postup potřebuje vědět, který formulář použít.</span><span class="sxs-lookup"><span data-stu-id="ec2f3-106">Because an MDI application can have many instances of the same child form, the procedure needs to know which form to use.</span></span> <span data-ttu-id="ec2f3-107">Chcete-li zadat správný <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> formulář, použijte vlastnost, která vrátí podřízený formulář, který má fokus nebo který byl naposledy aktivní.</span><span class="sxs-lookup"><span data-stu-id="ec2f3-107">To specify the correct form, use the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, which returns the child form that has the focus or that was most recently active.</span></span>  
  
 <span data-ttu-id="ec2f3-108">Pokud máte ve formuláři několik ovládacích prvků, musíte také určit, který ovládací prvek je aktivní.</span><span class="sxs-lookup"><span data-stu-id="ec2f3-108">When you have several controls on a form, you also need to specify which control is active.</span></span> <span data-ttu-id="ec2f3-109">Stejně <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> jako <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> vlastnost, vlastnost vrátí ovládací prvek se zaměřením na aktivní podřízený formulář.</span><span class="sxs-lookup"><span data-stu-id="ec2f3-109">Like the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, the <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> property returns the control with the focus on the active child form.</span></span> <span data-ttu-id="ec2f3-110">Následující postup ilustruje postup kopírování, který lze volat z nabídky podřízeného formuláře, nabídky ve formuláři MDI nebo tlačítka panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="ec2f3-110">The procedure below illustrates a copy procedure that can be called from a child form menu, a menu on the MDI form, or a toolbar button.</span></span>  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a><span data-ttu-id="ec2f3-111">Chcete-li zjistit aktivní podřízenou položku MDI (zkopírovat jeho text do schránky)</span><span class="sxs-lookup"><span data-stu-id="ec2f3-111">To determine the active MDI child (to copy its text to the Clipboard)</span></span>  
  
1. <span data-ttu-id="ec2f3-112">V rámci metody zkopírujte text aktivního ovládacího prvku aktivního podřízeného formuláře do schránky.</span><span class="sxs-lookup"><span data-stu-id="ec2f3-112">Within a method, copy the text of the active control of the active child form to the Clipboard.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ec2f3-113">Tento příklad předpokládá, že existuje nadřazený formulář MDI (`Form1`), <xref:System.Windows.Forms.RichTextBox> který má jedno nebo více podřízených oken MDI obsahující chod ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ec2f3-113">This example assumes there is an MDI parent form (`Form1`) that has one or more MDI child windows containing a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="ec2f3-114">Další informace naleznete v [tématu Vytváření nadřazených formulářů MDI](how-to-create-mdi-parent-forms.md).</span><span class="sxs-lookup"><span data-stu-id="ec2f3-114">For more information, see [Creating MDI Parent Forms](how-to-create-mdi-parent-forms.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ec2f3-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="ec2f3-115">See also</span></span>

- [<span data-ttu-id="ec2f3-116">Aplikace MDI (Multiple-Document Interface)</span><span class="sxs-lookup"><span data-stu-id="ec2f3-116">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="ec2f3-117">Postupy: Vytváření nadřazených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="ec2f3-117">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="ec2f3-118">Postupy: Vytváření podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="ec2f3-118">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="ec2f3-119">Postupy: Odesílání dat do aktivního podřízeného MDI</span><span class="sxs-lookup"><span data-stu-id="ec2f3-119">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="ec2f3-120">Postupy: Uspořádání podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="ec2f3-120">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
