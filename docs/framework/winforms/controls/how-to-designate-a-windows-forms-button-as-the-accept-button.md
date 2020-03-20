---
title: Určení tlačítka jako tlačítka Přijmout
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
ms.openlocfilehash: ca5f691fb26db5c4adcb48405c9600b54827104c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142144"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a>Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Přijmout
V libovolném formuláři systému <xref:System.Windows.Forms.Button> Windows můžete určit ovládací prvek jako tlačítko přijmout, označované také jako výchozí tlačítko. Kdykoli uživatel stiskne klávesu ENTER, klepne se na výchozí tlačítko bez ohledu na to, který jiný ovládací prvek ve formuláři má fokus.  
  
> [!NOTE]
> Výjimkou jsou, když je ovládací prvek s fokusem jiné tlačítko – v takovém případě bude klepnut na tlačítko s fokusem – nebo víceřádkové textové pole nebo vlastní ovládací prvek, který vytvoří soutisk klávesy ENTER.  
  
### <a name="to-designate-the-accept-button"></a>Určení tlačítka přijmout  
  
1. Nastavte <xref:System.Windows.Forms.Form.AcceptButton%2A> vlastnost formuláře na příslušný <xref:System.Windows.Forms.Button> ovládací prvek.  
  
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

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [Přehled ovládacího prvku Tlačítko](button-control-overview-windows-forms.md)
- [Metody výběru ovládacího prvku Windows Forms Button](ways-to-select-a-windows-forms-button-control.md)
- [Postupy: Reakce na kliknutí na tlačítko Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Zrušit](how-to-designate-a-windows-forms-button-as-the-cancel-button.md)
- [Ovládací prvek Tlačítko](button-control-windows-forms.md)
