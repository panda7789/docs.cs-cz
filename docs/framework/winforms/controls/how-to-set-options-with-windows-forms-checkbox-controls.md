---
title: "Postupy: Nastavení možností pomocí ovládacích prvků Windows Forms CheckBox"
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
- cpp
f1_keywords: checked
helpviewer_keywords:
- CheckBox control [Windows Forms], checked state
- check boxes [Windows Forms], using to set options
- CheckBox control [Windows Forms], using to set options
ms.assetid: 2ac70498-7e3e-4e07-8901-ccabaeb5fd3e
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4059e3b4ad4c687234f2bc0c66c680b2c857cfe7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-options-with-windows-forms-checkbox-controls"></a><span data-ttu-id="a120e-102">Postupy: Nastavení možností pomocí ovládacích prvků Windows Forms CheckBox</span><span class="sxs-lookup"><span data-stu-id="a120e-102">How to: Set Options with Windows Forms CheckBox Controls</span></span>
<span data-ttu-id="a120e-103">Windows Forms <xref:System.Windows.Forms.CheckBox> řízení se používá k dát uživatelům True/False nebo možnosti Ano/Ne.</span><span class="sxs-lookup"><span data-stu-id="a120e-103">A Windows Forms <xref:System.Windows.Forms.CheckBox> control is used to give users True/False or Yes/No options.</span></span> <span data-ttu-id="a120e-104">Tento ovládací prvek zobrazí zaškrtnutí, pokud je vybrána.</span><span class="sxs-lookup"><span data-stu-id="a120e-104">The control displays a check mark when it is selected.</span></span>  
  
### <a name="to-set-options-with-checkbox-controls"></a><span data-ttu-id="a120e-105">Nastavení možností pomocí ovládacích prvků CheckBox</span><span class="sxs-lookup"><span data-stu-id="a120e-105">To set options with CheckBox controls</span></span>  
  
1.  <span data-ttu-id="a120e-106">Zkontrolujte hodnotu <xref:System.Windows.Forms.CheckBox.Checked%2A> vlastnost, abyste zjistili její stav a použít tuto hodnotu nastavit možnost.</span><span class="sxs-lookup"><span data-stu-id="a120e-106">Examine the value of the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine its state, and use that value to set an option.</span></span>  
  
     <span data-ttu-id="a120e-107">V ukázce kódu níže, kdy <xref:System.Windows.Forms.CheckBox> ovládacího prvku <xref:System.Windows.Forms.CheckBox.CheckedChanged> událost se vyvolá, formuláře <xref:System.Windows.Forms.Control.AllowDrop%2A> je nastavena na `false` Pokud je zaškrtnuto políčko.</span><span class="sxs-lookup"><span data-stu-id="a120e-107">In the code sample below, when the <xref:System.Windows.Forms.CheckBox> control's <xref:System.Windows.Forms.CheckBox.CheckedChanged> event is raised, the form's <xref:System.Windows.Forms.Control.AllowDrop%2A> property is set to `false` if the check box is checked.</span></span> <span data-ttu-id="a120e-108">To je užitečné v situacích, kde chcete omezit interakci s uživatelem.</span><span class="sxs-lookup"><span data-stu-id="a120e-108">This is useful for situations where you want to restrict user interaction.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a120e-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="a120e-109">See Also</span></span>  
 <xref:System.Windows.Forms.CheckBox>  
 [<span data-ttu-id="a120e-110">Přehled ovládacího prvku CheckBox</span><span class="sxs-lookup"><span data-stu-id="a120e-110">CheckBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="a120e-111">Postupy: Reakce na kliknutí na prvek Windows Forms CheckBox</span><span class="sxs-lookup"><span data-stu-id="a120e-111">How to: Respond to Windows Forms CheckBox Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-checkbox-clicks.md)  
 [<span data-ttu-id="a120e-112">Ovládací prvek CheckBox</span><span class="sxs-lookup"><span data-stu-id="a120e-112">CheckBox Control</span></span>](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)
