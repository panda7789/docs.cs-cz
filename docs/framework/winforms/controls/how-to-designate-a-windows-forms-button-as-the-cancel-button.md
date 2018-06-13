---
title: 'Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Storno'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 252f0834-e54b-44d9-96f7-ee5f50e94f2c
ms.openlocfilehash: efe68ec8e5c34607bb8f865b5d0c7919a0377ab8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530868"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a><span data-ttu-id="1fc01-102">Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Storno</span><span class="sxs-lookup"><span data-stu-id="1fc01-102">How to: Designate a Windows Forms Button as the Cancel Button</span></span>
<span data-ttu-id="1fc01-103">Na všechny formuláře Windows, můžete určit <xref:System.Windows.Forms.Button> ovládacího prvku tlačítko Zrušit.</span><span class="sxs-lookup"><span data-stu-id="1fc01-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the cancel button.</span></span> <span data-ttu-id="1fc01-104">Vždy, když uživatel stisknutím klávesy ESC, bez ohledu na to, které další ovládací prvek na formuláři fokus, po kliknutí na tlačítko Storno.</span><span class="sxs-lookup"><span data-stu-id="1fc01-104">A cancel button is clicked whenever the user presses the ESC key, regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="1fc01-105">Toto tlačítko je obvykle naprogramovaný tak, aby uživatelům umožnit rychle operaci ukončit bez potvrzení na každou akci.</span><span class="sxs-lookup"><span data-stu-id="1fc01-105">Such a button is usually programmed to enable the user to quickly exit an operation without committing to any action.</span></span>  
  
### <a name="to-designate-the-cancel-button"></a><span data-ttu-id="1fc01-106">Chcete-li určit tlačítko Zrušit</span><span class="sxs-lookup"><span data-stu-id="1fc01-106">To designate the cancel button</span></span>  
  
1.  <span data-ttu-id="1fc01-107">Nastavte jeho <xref:System.Windows.Forms.Form.CancelButton%2A> vlastnost na příslušné <xref:System.Windows.Forms.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1fc01-107">Set the form's <xref:System.Windows.Forms.Form.CancelButton%2A> property to the appropriate <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub SetCancelButton(ByVal myCancelBtn As Button)  
       Me.CancelButton = myCancelBtn  
    End Sub  
    ```  
  
    ```csharp  
    private void SetCancelButton(Button myCancelBtn)  
    {  
       this.CancelButton = myCancelBtn;  
    }  
    ```  
  
    ```cpp  
    private:  
       void SetCancelButton(Button ^ myCancelBtn)  
       {  
          this->CancelButton = myCancelBtn;  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1fc01-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="1fc01-108">See Also</span></span>  
 <xref:System.Windows.Forms.Form.CancelButton%2A>  
 [<span data-ttu-id="1fc01-109">Přehled ovládacího prvku Button</span><span class="sxs-lookup"><span data-stu-id="1fc01-109">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [<span data-ttu-id="1fc01-110">Metody výběru ovládacího prvku Windows Forms Button</span><span class="sxs-lookup"><span data-stu-id="1fc01-110">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [<span data-ttu-id="1fc01-111">Postupy: Reakce na kliknutí na tlačítko Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1fc01-111">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="1fc01-112">Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Přijmout</span><span class="sxs-lookup"><span data-stu-id="1fc01-112">How to: Designate a Windows Forms Button as the Accept Button</span></span>](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-accept-button.md)  
 [<span data-ttu-id="1fc01-113">Ovládací prvek Button</span><span class="sxs-lookup"><span data-stu-id="1fc01-113">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
