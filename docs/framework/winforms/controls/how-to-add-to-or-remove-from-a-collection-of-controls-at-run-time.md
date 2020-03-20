---
title: 'Postupy: Přidávání ovládacích prvků do kolekce a odebírání ovládacích prvků z kolekce za běhu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- run time [Windows Forms], removing controls
- controls [Windows Forms], adding using collections
- controls collections
- collections [Windows Forms], adding items
- run time [Windows Forms], adding controls
- controls [Windows Forms], removing using collections
ms.assetid: 771bf895-3d5f-469b-a324-3528f343657e
ms.openlocfilehash: 369946581847b4bdcf8bc658aeb94b14c529061c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182279"
---
# <a name="how-to-add-to-or-remove-from-a-collection-of-controls-at-run-time"></a>Postupy: Přidávání ovládacích prvků do kolekce a odebírání ovládacích prvků z kolekce za běhu
Běžné úkoly ve vývoji aplikací jsou přidání ovládacích prvků a <xref:System.Windows.Forms.Panel> odebrání <xref:System.Windows.Forms.GroupBox> ovládacích prvků z libovolného ovládacího prvku kontejneru ve formulářích (například ovládací prvek nebo dokonce samotný formulář). V době návrhu lze ovládací prvky přetáhnout přímo do panelu nebo skupinového rámečku. V době běhu tyto `Controls` ovládací prvky udržovat kolekci, která sleduje, jaké ovládací prvky jsou umístěny na ně.  
  
> [!NOTE]
> Následující příklad kódu platí pro všechny ovládací prvky, které udržuje kolekci ovládacích prvků v něm.  
  
### <a name="to-add-a-control-to-a-collection-programmatically"></a>Chcete-li přidat ovládací prvek do kolekce programově  
  
1. Vytvořte instanci ovládacího prvku, který má být přidán.  
  
2. Nastavte vlastnosti nového ovládacího prvku.  
  
3. Přidejte ovládací `Controls` prvek do kolekce nadřazeného ovládacího prvku.  
  
     Následující příklad kódu ukazuje, jak vytvořit <xref:System.Windows.Forms.Button> instanci ovládacího prvku. Vyžaduje formulář s <xref:System.Windows.Forms.Panel> ovládacím prvkem a že metoda zpracování událostí `NewPanelButton_Click`pro vytvářené tlačítko , , již existuje.  
  
    ```vb  
    Public NewPanelButton As New Button()  
  
    Public Sub AddNewControl()  
       ' The Add method will accept as a parameter any object that derives  
       ' from the Control class. In this case, it is a Button control.  
       Panel1.Controls.Add(NewPanelButton)  
       ' The event handler indicated for the Click event in the code
       ' below is used as an example. Substite the appropriate event  
       ' handler for your application.  
       AddHandler NewPanelButton.Click, AddressOf NewPanelButton_Click  
    End Sub  
    ```  
  
    ```csharp  
    public Button newPanelButton = new Button();  
  
    public void addNewControl()  
    {
       // The Add method will accept as a parameter any object that derives  
       // from the Control class. In this case, it is a Button control.  
       panel1.Controls.Add(newPanelButton);  
       // The event handler indicated for the Click event in the code
       // below is used as an example. Substitute the appropriate event  
       // handler for your application.  
       this.newPanelButton.Click += new System.EventHandler(this. NewPanelButton_Click);  
    }  
    ```  
  
### <a name="to-remove-controls-from-a-collection-programmatically"></a>Odebrání ovládacích prvků z kolekce programově  
  
1. Odeberte obslužnou rutinu události z události. V jazyce Visual Basic použijte klíčové slovo [Příkaz RemoveHandler;](../../../visual-basic/language-reference/statements/removehandler-statement.md) v c#, použijte [-= operátor](../../../csharp/language-reference/operators/subtraction-operator.md).  
  
2. Pomocí `Remove` metody odstraňte požadovaný ovládací prvek `Controls` z kolekce panelu.  
  
3. Volání <xref:System.Windows.Forms.Control.Dispose%2A> metody uvolnit všechny prostředky používané ovládacího prvku.  
  
    ```vb  
    Public Sub RemoveControl()  
    ' NOTE: The code below uses the instance of
    ' the button (NewPanelButton) from the previous example.  
       If Panel1.Controls.Contains(NewPanelButton) Then  
          RemoveHandler NewPanelButton.Click, AddressOf _
             NewPanelButton_Click  
          Panel1.Controls.Remove(NewPanelButton)  
          NewPanelButton.Dispose()  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void removeControl(object sender, System.EventArgs e)  
    {  
    // NOTE: The code below uses the instance of
    // the button (newPanelButton) from the previous example.  
       if(panel1.Controls.Contains(newPanelButton))  
       {  
          this.newPanelButton.Click -= new System.EventHandler(this.
             NewPanelButton_Click);  
          panel1.Controls.Remove(newPanelButton);  
          newPanelButton.Dispose();  
       }  
    }  
    ```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.Panel>
- [Ovládací prvek Panel](panel-control-windows-forms.md)
