---
title: 'Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Přijmout'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: 22cc9da6-b913-4e04-9554-dee443ac5c3a
ms.openlocfilehash: a69964b83e9948a844483725616a150234a38c97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531937"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a><span data-ttu-id="59863-102">Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Přijmout</span><span class="sxs-lookup"><span data-stu-id="59863-102">How to: Designate a Windows Forms Button as the Accept Button</span></span>
<span data-ttu-id="59863-103">Na všechny formuláře Windows, můžete určit <xref:System.Windows.Forms.Button> ovládacího prvku tlačítko Přijmout, také známé jako výchozího tlačítka.</span><span class="sxs-lookup"><span data-stu-id="59863-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the accept button, also known as the default button.</span></span> <span data-ttu-id="59863-104">Vždy, když uživatel stiskne klávesu ENTER, výchozí je stisknuto tlačítko bez ohledu na to, které další ovládací prvek na formuláři fokus.</span><span class="sxs-lookup"><span data-stu-id="59863-104">Whenever the user presses the ENTER key, the default button is clicked regardless of which other control on the form has the focus.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59863-105">Výjimky pro tento jsou jiné tlačítko po ovládací prvek fokus – v takovém případě bude kliknutí na tlačítko s fokusem – nebo víceřádkové textové pole, nebo vlastní ovládací prvek, který traps klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="59863-105">The exceptions to this are when the control with focus is another button — in that case, the button with the focus will be clicked — or a multiline text box, or a custom control that traps the ENTER key.</span></span>  
  
### <a name="to-designate-the-accept-button"></a><span data-ttu-id="59863-106">K určení přijmout</span><span class="sxs-lookup"><span data-stu-id="59863-106">To designate the accept button</span></span>  
  
1.  <span data-ttu-id="59863-107">Nastavte jeho <xref:System.Windows.Forms.Form.AcceptButton%2A> vlastnost na příslušné <xref:System.Windows.Forms.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="59863-107">Set the form's <xref:System.Windows.Forms.Form.AcceptButton%2A> property to the appropriate <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub SetDefault(ByVal myDefaultBtn As Button)  
      Me.AcceptButton = myDefaultBtn   
    End Sub  
    ```  
  
    ```csharp  
    private void SetDefault(Button myDefaultBtn)  
    {  
       this.AcceptButton = myDefaultBtn;  
    }  
    ```  
  
    ```cpp  
    private:  
       void SetDefault(Button ^ myDefaultBtn)  
       {  
          this->AcceptButton = myDefaultBtn;  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="59863-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="59863-108">See Also</span></span>  
 <xref:System.Windows.Forms.Form.AcceptButton%2A>  
 [<span data-ttu-id="59863-109">Přehled ovládacího prvku Button</span><span class="sxs-lookup"><span data-stu-id="59863-109">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [<span data-ttu-id="59863-110">Metody výběru ovládacího prvku Windows Forms Button</span><span class="sxs-lookup"><span data-stu-id="59863-110">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [<span data-ttu-id="59863-111">Postupy: Reakce na kliknutí na tlačítko Windows Forms</span><span class="sxs-lookup"><span data-stu-id="59863-111">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="59863-112">Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Zrušit</span><span class="sxs-lookup"><span data-stu-id="59863-112">How to: Designate a Windows Forms Button as the Cancel Button</span></span>](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-cancel-button.md)  
 [<span data-ttu-id="59863-113">Ovládací prvek Button</span><span class="sxs-lookup"><span data-stu-id="59863-113">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
