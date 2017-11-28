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
ms.openlocfilehash: 3bbdf2ec4f2353662f1077b9d95966e0a2ebd316
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Přehled ovládacího prvku tlačítko](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [Metody výběru ovládacího prvku Windows Forms Button](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [Postupy: reakce na kliknutí na tlačítko Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Postupy: určení tlačítka Windows Forms tlačítka přijmout](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-accept-button.md)  
 [Tlačítko – ovládací prvek](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
