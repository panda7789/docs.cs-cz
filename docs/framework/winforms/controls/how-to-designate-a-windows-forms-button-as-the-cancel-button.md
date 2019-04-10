---
title: 'Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Zrušit'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 252f0834-e54b-44d9-96f7-ee5f50e94f2c
ms.openlocfilehash: ad95a527ea72858cc106c87d8712110e018e97b2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231432"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a><span data-ttu-id="59a59-102">Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Zrušit</span><span class="sxs-lookup"><span data-stu-id="59a59-102">How to: Designate a Windows Forms Button as the Cancel Button</span></span>
<span data-ttu-id="59a59-103">Na formuláři Windows, můžete určit <xref:System.Windows.Forms.Button> ovládacího prvku tlačítko Storno.</span><span class="sxs-lookup"><span data-stu-id="59a59-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the cancel button.</span></span> <span data-ttu-id="59a59-104">Pokaždé, když uživatel stiskne klávesu ESC, bez ohledu na to, který má jiný ovládací prvek ve formuláři fokus, je kliknutí na tlačítko Storno.</span><span class="sxs-lookup"><span data-stu-id="59a59-104">A cancel button is clicked whenever the user presses the ESC key, regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="59a59-105">Toto tlačítko je obvykle naprogramovaný tak, aby uživateli umožňuje rychle operaci ukončit bez potvrzení na každou akci.</span><span class="sxs-lookup"><span data-stu-id="59a59-105">Such a button is usually programmed to enable the user to quickly exit an operation without committing to any action.</span></span>  
  
### <a name="to-designate-the-cancel-button"></a><span data-ttu-id="59a59-106">Chcete-li určit tlačítka Storno</span><span class="sxs-lookup"><span data-stu-id="59a59-106">To designate the cancel button</span></span>  
  
1.  <span data-ttu-id="59a59-107">Vlastnost formuláře <xref:System.Windows.Forms.Form.CancelButton%2A> vlastnosti na příslušné <xref:System.Windows.Forms.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="59a59-107">Set the form's <xref:System.Windows.Forms.Form.CancelButton%2A> property to the appropriate <xref:System.Windows.Forms.Button> control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="59a59-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="59a59-108">See also</span></span>

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [<span data-ttu-id="59a59-109">Přehled ovládacího prvku Button</span><span class="sxs-lookup"><span data-stu-id="59a59-109">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="59a59-110">Metody výběru ovládacího prvku Windows Forms Button</span><span class="sxs-lookup"><span data-stu-id="59a59-110">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="59a59-111">Postupy: Reakce na kliknutí na tlačítko Windows Forms</span><span class="sxs-lookup"><span data-stu-id="59a59-111">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="59a59-112">Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Přijmout</span><span class="sxs-lookup"><span data-stu-id="59a59-112">How to: Designate a Windows Forms Button as the Accept Button</span></span>](how-to-designate-a-windows-forms-button-as-the-accept-button.md)
- [<span data-ttu-id="59a59-113">Ovládací prvek Button</span><span class="sxs-lookup"><span data-stu-id="59a59-113">Button Control</span></span>](button-control-windows-forms.md)
