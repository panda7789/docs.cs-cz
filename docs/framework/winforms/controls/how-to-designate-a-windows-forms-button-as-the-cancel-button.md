---
title: Označit tlačítko jako tlačítko Storno
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 252f0834-e54b-44d9-96f7-ee5f50e94f2c
ms.openlocfilehash: 123b3e275065efadd24815320ea7d855808e60b9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743257"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a>Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Storno
V jakémkoli formuláři Windows můžete určit <xref:System.Windows.Forms.Button> ovládací prvek pro tlačítko Storno. Kliknutím na tlačítko Storno dojde vždy, když uživatel stiskne klávesu ESC bez ohledu na to, který jiný ovládací prvek ve formuláři má fokus. Toto tlačítko je obvykle naprogramováno, aby uživatel mohl rychle ukončit operaci bez nutnosti potvrzení akce.  
  
### <a name="to-designate-the-cancel-button"></a>Chcete-li určit tlačítko Storno  
  
1. Nastavte vlastnost <xref:System.Windows.Forms.Form.CancelButton%2A> formuláře na příslušný ovládací prvek <xref:System.Windows.Forms.Button>.  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [Přehled ovládacího prvku Button](button-control-overview-windows-forms.md)
- [Metody výběru ovládacího prvku Windows Forms Button](ways-to-select-a-windows-forms-button-control.md)
- [Postupy: Reakce na kliknutí na tlačítko Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Přijmout](how-to-designate-a-windows-forms-button-as-the-accept-button.md)
- [Ovládací prvek Button](button-control-windows-forms.md)
