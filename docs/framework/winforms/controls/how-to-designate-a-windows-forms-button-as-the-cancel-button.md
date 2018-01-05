---
title: "Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Storno"
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
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 252f0834-e54b-44d9-96f7-ee5f50e94f2c
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f3f61828b4c8b65ae984685610d6d8609953376a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a>Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Storno
Na všechny formuláře Windows, můžete určit <xref:System.Windows.Forms.Button> ovládacího prvku tlačítko Zrušit. Vždy, když uživatel stisknutím klávesy ESC, bez ohledu na to, které další ovládací prvek na formuláři fokus, po kliknutí na tlačítko Storno. Toto tlačítko je obvykle naprogramovaný tak, aby uživatelům umožnit rychle operaci ukončit bez potvrzení na každou akci.  
  
### <a name="to-designate-the-cancel-button"></a>Chcete-li určit tlačítko Zrušit  
  
1.  Nastavte jeho <xref:System.Windows.Forms.Form.CancelButton%2A> vlastnost na příslušné <xref:System.Windows.Forms.Button> ovládacího prvku.  
  
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
 <xref:System.Windows.Forms.Form.CancelButton%2A>  
 [Přehled ovládacího prvku Button](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [Metody výběru ovládacího prvku Windows Forms Button](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [Postupy: Reakce na kliknutí na tlačítko Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Přijmout](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-accept-button.md)  
 [Ovládací prvek Button](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
