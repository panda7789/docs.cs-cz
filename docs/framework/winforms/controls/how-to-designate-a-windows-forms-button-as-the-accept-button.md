---
title: Označení tlačítka jako tlačítka pro přijetí
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
ms.openlocfilehash: 1063f649768cac2c866390718b261a21e18ec4d3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743265"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a><span data-ttu-id="1a38a-102">Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Přijmout</span><span class="sxs-lookup"><span data-stu-id="1a38a-102">How to: Designate a Windows Forms Button as the Accept Button</span></span>
<span data-ttu-id="1a38a-103">V jakémkoli formuláři Windows můžete určit <xref:System.Windows.Forms.Button> ovládací prvek jako tlačítko přijmout, označované také jako výchozí tlačítko.</span><span class="sxs-lookup"><span data-stu-id="1a38a-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the accept button, also known as the default button.</span></span> <span data-ttu-id="1a38a-104">Pokaždé, když uživatel stiskne klávesu ENTER, klikne na tlačítko výchozí, a to bez ohledu na to, který jiný ovládací prvek ve formuláři má fokus.</span><span class="sxs-lookup"><span data-stu-id="1a38a-104">Whenever the user presses the ENTER key, the default button is clicked regardless of which other control on the form has the focus.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1a38a-105">Výjimkou je, když je ovládací prvek s fokusem jiný tlačítko – v takovém případě se na tlačítko s fokusem klikne – nebo na víceřádkové textové pole nebo na vlastní ovládací prvek, který zachytávání klíče ENTER.</span><span class="sxs-lookup"><span data-stu-id="1a38a-105">The exceptions to this are when the control with focus is another button — in that case, the button with the focus will be clicked — or a multiline text box, or a custom control that traps the ENTER key.</span></span>  
  
### <a name="to-designate-the-accept-button"></a><span data-ttu-id="1a38a-106">Označení tlačítka přijmout</span><span class="sxs-lookup"><span data-stu-id="1a38a-106">To designate the accept button</span></span>  
  
1. <span data-ttu-id="1a38a-107">Nastavte vlastnost <xref:System.Windows.Forms.Form.AcceptButton%2A> formuláře na příslušný ovládací prvek <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="1a38a-107">Set the form's <xref:System.Windows.Forms.Form.AcceptButton%2A> property to the appropriate <xref:System.Windows.Forms.Button> control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1a38a-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1a38a-108">See also</span></span>

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [<span data-ttu-id="1a38a-109">Přehled ovládacího prvku Button</span><span class="sxs-lookup"><span data-stu-id="1a38a-109">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="1a38a-110">Metody výběru ovládacího prvku Windows Forms Button</span><span class="sxs-lookup"><span data-stu-id="1a38a-110">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="1a38a-111">Postupy: Reakce na kliknutí na tlačítko Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1a38a-111">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="1a38a-112">Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Zrušit</span><span class="sxs-lookup"><span data-stu-id="1a38a-112">How to: Designate a Windows Forms Button as the Cancel Button</span></span>](how-to-designate-a-windows-forms-button-as-the-cancel-button.md)
- [<span data-ttu-id="1a38a-113">Ovládací prvek Button</span><span class="sxs-lookup"><span data-stu-id="1a38a-113">Button Control</span></span>](button-control-windows-forms.md)
