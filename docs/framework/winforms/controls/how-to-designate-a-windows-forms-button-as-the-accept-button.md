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
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a>Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Přijmout
Na všechny formuláře Windows, můžete určit <xref:System.Windows.Forms.Button> ovládacího prvku tlačítko Přijmout, také známé jako výchozího tlačítka. Vždy, když uživatel stiskne klávesu ENTER, výchozí je stisknuto tlačítko bez ohledu na to, které další ovládací prvek na formuláři fokus.  
  
> [!NOTE]
>  Výjimky pro tento jsou jiné tlačítko po ovládací prvek fokus – v takovém případě bude kliknutí na tlačítko s fokusem – nebo víceřádkové textové pole, nebo vlastní ovládací prvek, který traps klávesu ENTER.  
  
### <a name="to-designate-the-accept-button"></a>K určení přijmout  
  
1.  Nastavte jeho <xref:System.Windows.Forms.Form.AcceptButton%2A> vlastnost na příslušné <xref:System.Windows.Forms.Button> ovládacího prvku.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Form.AcceptButton%2A>  
 [Přehled ovládacího prvku Button](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [Metody výběru ovládacího prvku Windows Forms Button](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [Postupy: Reakce na kliknutí na tlačítko Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Zrušit](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-cancel-button.md)  
 [Ovládací prvek Button](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
