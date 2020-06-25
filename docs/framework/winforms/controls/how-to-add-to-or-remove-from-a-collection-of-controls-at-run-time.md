---
title: 'Postupy: Přidávání ovládacích prvků do kolekce a odebírání ovládacích prvků z kolekce za běhu'
description: Naučte se, jak přidat ovládací prvky do a odebrat ovládací prvky z libovolného ovládacího prvku kontejneru ve formulářích, jako je například panel nebo ovládací prvek skupinový rámeček, nebo dokonce samotný formulář.
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
ms.openlocfilehash: 6c3f2d1f42b130de4d808871265b50510cfb8f47
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325872"
---
# <a name="how-to-add-to-or-remove-from-a-collection-of-controls-at-run-time"></a>Postupy: Přidávání ovládacích prvků do kolekce a odebírání ovládacích prvků z kolekce za běhu
Běžné úlohy při vývoji aplikací přidávají ovládací prvky do a odebírání ovládacích prvků z libovolného ovládacího prvku kontejner ve formulářích (například <xref:System.Windows.Forms.Panel> <xref:System.Windows.Forms.GroupBox> ovládacího prvku nebo nebo i formuláře samotného). V době návrhu lze ovládací prvky přetahovat přímo do panelu nebo skupinového pole. V době běhu tyto ovládací prvky udržují `Controls` kolekci, která uchovává přehled o tom, které ovládací prvky jsou na ně umístěny.  
  
> [!NOTE]
> Následující příklad kódu se vztahuje na jakýkoli ovládací prvek, který udržuje kolekci ovládacích prvků v rámci něj.  
  
### <a name="to-add-a-control-to-a-collection-programmatically"></a>Postup přidání ovládacího prvku do kolekce prostřednictvím kódu programu  
  
1. Vytvořte instanci ovládacího prvku, který chcete přidat.  
  
2. Nastavte vlastnosti nového ovládacího prvku.  
  
3. Přidejte ovládací prvek do `Controls` kolekce nadřazeného ovládacího prvku.  
  
     Následující příklad kódu ukazuje, jak vytvořit instanci <xref:System.Windows.Forms.Button> ovládacího prvku. Vyžaduje formulář s <xref:System.Windows.Forms.Panel> ovládacím prvkem a, že metoda zpracování událostí pro tlačítko, která je vytvořena, `NewPanelButton_Click` již existuje.  
  
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
  
### <a name="to-remove-controls-from-a-collection-programmatically"></a>Postup při odebírání ovládacích prvků z kolekce prostřednictvím kódu programu  
  
1. Odeberte obslužnou rutinu události z události. V Visual Basic použijte klíčové slovo [příkaz removeHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md) ; v jazyce C# použijte [operátor-=](../../../csharp/language-reference/operators/subtraction-operator.md).  
  
2. Použijte `Remove` metodu k odstranění požadovaného ovládacího prvku z `Controls` kolekce panelu.  
  
3. Zavolejte <xref:System.Windows.Forms.Control.Dispose%2A> metodu pro uvolnění všech prostředků, které ovládací prvek používá.  
  
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
