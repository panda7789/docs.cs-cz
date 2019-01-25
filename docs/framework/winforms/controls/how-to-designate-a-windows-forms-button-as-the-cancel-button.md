---
title: 'Postupy: Určení tlačítka Windows Forms jako tlačítko Storno'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 252f0834-e54b-44d9-96f7-ee5f50e94f2c
ms.openlocfilehash: 74d025677682735fc7f1c68116b2364887f0519c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701466"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a>Postupy: Určení tlačítka Windows Forms jako tlačítko Storno
Na formuláři Windows, můžete určit <xref:System.Windows.Forms.Button> ovládacího prvku tlačítko Storno. Pokaždé, když uživatel stiskne klávesu ESC, bez ohledu na to, který má jiný ovládací prvek ve formuláři fokus, je kliknutí na tlačítko Storno. Toto tlačítko je obvykle naprogramovaný tak, aby uživateli umožňuje rychle operaci ukončit bez potvrzení na každou akci.  
  
### <a name="to-designate-the-cancel-button"></a>Chcete-li určit tlačítka Storno  
  
1.  Vlastnost formuláře <xref:System.Windows.Forms.Form.CancelButton%2A> vlastnosti na příslušné <xref:System.Windows.Forms.Button> ovládacího prvku.  
  
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
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [Přehled ovládacího prvku Button](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)
- [Metody výběru ovládacího prvku Windows Forms Button](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)
- [Postupy: Reakce na kliknutí na tlačítko Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)
- [Postupy: Určení tlačítka Windows Forms pro funkci tlačítka přijmout](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-accept-button.md)
- [Ovládací prvek Button](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
