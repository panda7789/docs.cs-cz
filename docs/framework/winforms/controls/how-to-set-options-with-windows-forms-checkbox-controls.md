---
title: 'Postupy: Nastavení možností pomocí ovládacích prvků Windows Forms CheckBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- checked
helpviewer_keywords:
- CheckBox control [Windows Forms], checked state
- check boxes [Windows Forms], using to set options
- CheckBox control [Windows Forms], using to set options
ms.assetid: 2ac70498-7e3e-4e07-8901-ccabaeb5fd3e
ms.openlocfilehash: 881996563acef36a1981ca6236c155b8fc56ef0a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013202"
---
# <a name="how-to-set-options-with-windows-forms-checkbox-controls"></a><span data-ttu-id="6c95f-102">Postupy: Nastavení možností pomocí ovládacích prvků Windows Forms CheckBox</span><span class="sxs-lookup"><span data-stu-id="6c95f-102">How to: Set Options with Windows Forms CheckBox Controls</span></span>
<span data-ttu-id="6c95f-103">Windows Forms <xref:System.Windows.Forms.CheckBox> ovládacího prvku se používá k uživatelům True/False nebo možnosti Ano nebo ne.</span><span class="sxs-lookup"><span data-stu-id="6c95f-103">A Windows Forms <xref:System.Windows.Forms.CheckBox> control is used to give users True/False or Yes/No options.</span></span> <span data-ttu-id="6c95f-104">Ovládací prvek zobrazí zaškrtávací políčko, pokud je vybrána.</span><span class="sxs-lookup"><span data-stu-id="6c95f-104">The control displays a check mark when it is selected.</span></span>  
  
### <a name="to-set-options-with-checkbox-controls"></a><span data-ttu-id="6c95f-105">Nastavení možností pomocí ovládacích prvků CheckBox</span><span class="sxs-lookup"><span data-stu-id="6c95f-105">To set options with CheckBox controls</span></span>  
  
1. <span data-ttu-id="6c95f-106">Zkoumat hodnoty <xref:System.Windows.Forms.CheckBox.Checked%2A> vlastnosti k určení stavu a tuto hodnotu můžete nastavit možnost.</span><span class="sxs-lookup"><span data-stu-id="6c95f-106">Examine the value of the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine its state, and use that value to set an option.</span></span>  
  
     <span data-ttu-id="6c95f-107">Ve vzorovém kódu níže, kdy <xref:System.Windows.Forms.CheckBox> ovládacího prvku <xref:System.Windows.Forms.CheckBox.CheckedChanged> událost se vyvolá, formuláře <xref:System.Windows.Forms.Control.AllowDrop%2A> je nastavena na `false` Pokud je zaškrtnuto zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="6c95f-107">In the code sample below, when the <xref:System.Windows.Forms.CheckBox> control's <xref:System.Windows.Forms.CheckBox.CheckedChanged> event is raised, the form's <xref:System.Windows.Forms.Control.AllowDrop%2A> property is set to `false` if the check box is checked.</span></span> <span data-ttu-id="6c95f-108">To je užitečné v situacích, ve které chcete omezit interakci s uživatelem.</span><span class="sxs-lookup"><span data-stu-id="6c95f-108">This is useful for situations where you want to restrict user interaction.</span></span>  
  
    ```vb  
    Private Sub CheckBox1_CheckedChanged(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles CheckBox1.CheckedChanged  
       ' Determine the CheckState of the check box.  
       If CheckBox1.CheckState = CheckState.Checked Then  
          ' If checked, do not allow items to be dragged onto the form.  
          Me.AllowDrop = False  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void checkBox1_CheckedChanged(object sender, System.EventArgs e)  
    {  
       // Determine the CheckState of the check box.  
       if (checkBox1.CheckState == CheckState.Checked)   
       {  
          // If checked, do not allow items to be dragged onto the form.  
          this.AllowDrop = false;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Determine the CheckState of the check box.  
          if (checkBox1->CheckState == CheckState::Checked)   
          {  
             // If checked, do not allow items to be dragged onto the form.  
             this->AllowDrop = false;  
          }  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6c95f-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6c95f-109">See also</span></span>

- <xref:System.Windows.Forms.CheckBox>
- [<span data-ttu-id="6c95f-110">Přehled ovládacího prvku CheckBox</span><span class="sxs-lookup"><span data-stu-id="6c95f-110">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="6c95f-111">Postupy: Reakce na Windows Forms kliknutí na zaškrtávací políčko</span><span class="sxs-lookup"><span data-stu-id="6c95f-111">How to: Respond to Windows Forms CheckBox Clicks</span></span>](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [<span data-ttu-id="6c95f-112">Ovládací prvek CheckBox</span><span class="sxs-lookup"><span data-stu-id="6c95f-112">CheckBox Control</span></span>](checkbox-control-windows-forms.md)
