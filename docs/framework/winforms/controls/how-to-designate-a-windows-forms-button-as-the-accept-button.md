---
title: 'Postupy: Určení tlačítka Windows Forms pro funkci tlačítka přijmout'
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
ms.openlocfilehash: e35dbc2b66f743f5af3c405228439268590e1a5b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660200"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a><span data-ttu-id="43e71-102">Postupy: Určení tlačítka Windows Forms pro funkci tlačítka přijmout</span><span class="sxs-lookup"><span data-stu-id="43e71-102">How to: Designate a Windows Forms Button as the Accept Button</span></span>
<span data-ttu-id="43e71-103">Na formuláři Windows, můžete určit <xref:System.Windows.Forms.Button> ovládacího prvku tlačítko Přijmout, označované také jako výchozího tlačítka.</span><span class="sxs-lookup"><span data-stu-id="43e71-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the accept button, also known as the default button.</span></span> <span data-ttu-id="43e71-104">Pokaždé, když uživatel stiskne klávesu ENTER, výchozí je stisknuto tlačítko bez ohledu na to, který má jiný ovládací prvek ve formuláři fokus.</span><span class="sxs-lookup"><span data-stu-id="43e71-104">Whenever the user presses the ENTER key, the default button is clicked regardless of which other control on the form has the focus.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="43e71-105">Výjimky jsou při ovládací prvek fokus je jiný tlačítko – v takovém případě bude kliknutí na tlačítko s fokusem – nebo víceřádkovém textovém poli, nebo vlastní ovládací prvek, který zachycuje klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="43e71-105">The exceptions to this are when the control with focus is another button — in that case, the button with the focus will be clicked — or a multiline text box, or a custom control that traps the ENTER key.</span></span>  
  
### <a name="to-designate-the-accept-button"></a><span data-ttu-id="43e71-106">Chcete-li určit tlačítka přijmout</span><span class="sxs-lookup"><span data-stu-id="43e71-106">To designate the accept button</span></span>  
  
1.  <span data-ttu-id="43e71-107">Vlastnost formuláře <xref:System.Windows.Forms.Form.AcceptButton%2A> vlastnosti na příslušné <xref:System.Windows.Forms.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="43e71-107">Set the form's <xref:System.Windows.Forms.Form.AcceptButton%2A> property to the appropriate <xref:System.Windows.Forms.Button> control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="43e71-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="43e71-108">See also</span></span>
- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [<span data-ttu-id="43e71-109">Přehled ovládacího prvku Button</span><span class="sxs-lookup"><span data-stu-id="43e71-109">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)
- [<span data-ttu-id="43e71-110">Metody výběru ovládacího prvku Windows Forms Button</span><span class="sxs-lookup"><span data-stu-id="43e71-110">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="43e71-111">Postupy: Reakce na kliknutí na tlačítko Windows Forms</span><span class="sxs-lookup"><span data-stu-id="43e71-111">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="43e71-112">Postupy: Určení tlačítka Windows Forms jako tlačítko Storno</span><span class="sxs-lookup"><span data-stu-id="43e71-112">How to: Designate a Windows Forms Button as the Cancel Button</span></span>](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-cancel-button.md)
- [<span data-ttu-id="43e71-113">Ovládací prvek Button</span><span class="sxs-lookup"><span data-stu-id="43e71-113">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
