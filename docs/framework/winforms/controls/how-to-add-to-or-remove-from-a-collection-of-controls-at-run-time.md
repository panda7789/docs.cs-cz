---
title: 'Postupy: Přidat nebo odebrat z kolekce ovládacích prvků za běhu'
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
ms.openlocfilehash: 6ec4e41f5a3bee6302996f21afa81f2b5eeb9568
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720888"
---
# <a name="how-to-add-to-or-remove-from-a-collection-of-controls-at-run-time"></a>Postupy: Přidat nebo odebrat z kolekce ovládacích prvků za běhu
Běžné úlohy při vývoji aplikace se přidání ovládacích prvků pro a odebírání ovládacích prvků z kontejneru ovládacích prvků ve formulářích (například <xref:System.Windows.Forms.Panel> nebo <xref:System.Windows.Forms.GroupBox> ovládací prvek nebo dokonce i samotný formulář). V době návrhu můžete přetáhnout ovládací prvky přímo na panelu nebo skupiny. V době běhu, udržovat tyto ovládací prvky `Controls` kolekce, která uchovává informace o jaké ovládací prvky jsou umístěny na ně.  
  
> [!NOTE]
>  Následující příklad kódu se vztahuje na libovolný ovládací prvek, který udržuje sadu ovládacích prvků na ní.  
  
### <a name="to-add-a-control-to-a-collection-programmatically"></a>Přidání ovládacího prvku do kolekce prostřednictvím kódu programu  
  
1.  Vytvořte instanci ovládacího prvku na Přidat.  
  
2.  Nastavení vlastností nového ovládacího prvku.  
  
3.  Přidejte ovládací prvek `Controls` kolekce nadřazeného ovládacího prvku.  
  
     Následující příklad kódu ukazuje, jak vytvořit instanci <xref:System.Windows.Forms.Button> ovládacího prvku. Vyžaduje formulář s <xref:System.Windows.Forms.Panel> ovládací prvek a zda vytvořena metoda zpracování událostí na tlačítku pro `NewPanelButton_Click`, již existuje.  
  
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
  
### <a name="to-remove-controls-from-a-collection-programmatically"></a>Odebrání ovládacích prvků z kolekce prostřednictvím kódu programu  
  
1.  Odeberte obslužnou rutinu události z události. V jazyce Visual Basic použijte [RemoveHandler – příkaz](~/docs/visual-basic/language-reference/statements/removehandler-statement.md) – klíčové slovo; ve Vizuálu C#, použijte [-= – operátor (C# odkaz)](~/docs/csharp/language-reference/operators/subtraction-assignment-operator.md).  
  
2.  Použití `Remove` metoda odstranit požadovaný ovládací prvek z panelu `Controls` kolekce.  
  
3.  Volání <xref:System.Windows.Forms.Control.Dispose%2A> metoda a uvolnit tak prostředky používané ovládací prvek.  
  
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
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.Panel>
- [Ovládací prvek Panel](panel-control-windows-forms.md)
