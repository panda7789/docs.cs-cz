---
title: "Postupy: Přidávání ovládacích prvků do kolekce a odebírání ovládacích prvků z kolekce za běhu"
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
helpviewer_keywords:
- run time [Windows Forms], removing controls
- controls [Windows Forms], adding using collections
- controls collections
- collections [Windows Forms], adding items
- run time [Windows Forms], adding controls
- controls [Windows Forms], removing using collections
ms.assetid: 771bf895-3d5f-469b-a324-3528f343657e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 548ca8d682ffea6f2afa03124719a1bb5097a2fb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-to-or-remove-from-a-collection-of-controls-at-run-time"></a>Postupy: Přidávání ovládacích prvků do kolekce a odebírání ovládacích prvků z kolekce za běhu
Běžné úlohy při vývoji aplikace jsou přidání ovládacích prvků do a z kontejneru ovládacích prvků ve formulářích odebrání ovládacích prvků (například <xref:System.Windows.Forms.Panel> nebo <xref:System.Windows.Forms.GroupBox> ovládací prvek nebo i vlastního formuláře). V době návrhu můžete být přetažen ovládací prvky přímo na panelu nebo skupiny. V době běhu udržovat tyto ovládací prvky `Controls` kolekce, která uchovává informace o jaké ovládací prvky jsou umístěny na ně.  
  
> [!NOTE]
>  Následující příklad kódu se vztahuje na libovolný ovládací prvek, která udržuje kolekci ovládacích prvků v něm.  
  
### <a name="to-add-a-control-to-a-collection-programmatically"></a>Přidání ovládacího prvku do kolekce prostřednictvím kódu programu  
  
1.  Vytvořte instanci ovládacího prvku, který se má přidat.  
  
2.  Nastavit vlastnosti nového ovládacího prvku.  
  
3.  Přidání do ovládacího prvku `Controls` kolekce nadřazeného ovládacího prvku.  
  
     Následující příklad kódu ukazuje, jak vytvořit instanci <xref:System.Windows.Forms.Button> ovládacího prvku. Vyžaduje formulář s <xref:System.Windows.Forms.Panel> řízení a která metoda zpracování událostí pro tlačítko vytváří, `NewPanelButton_Click`, již existuje.  
  
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
  
1.  Odeberte obslužné rutiny události z události. V [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], použijte [RemoveHandler – příkaz](~/docs/visual-basic/language-reference/statements/removehandler-statement.md) – klíčové slovo; v [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], použijte [-= – operátor (referenční dokumentace jazyka C#)](~/docs/csharp/language-reference/operators/subtraction-assignment-operator.md).  
  
2.  Použití `Remove` metoda odstranit požadovaný ovládací prvek z panelu `Controls` kolekce.  
  
3.  Volání <xref:System.Windows.Forms.Control.Dispose%2A> metodu pro uvolnění všechny prostředky používané ovládací prvek.  
  
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
 <xref:System.Windows.Forms.Panel>  
 [Ovládací prvek Panel](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)
