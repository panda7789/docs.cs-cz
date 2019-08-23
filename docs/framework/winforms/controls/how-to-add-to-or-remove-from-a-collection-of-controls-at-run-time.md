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
ms.openlocfilehash: 87ad4c957ac5b99438684d398a0c5ad7d126c406
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925048"
---
# <a name="how-to-add-to-or-remove-from-a-collection-of-controls-at-run-time"></a><span data-ttu-id="e3602-102">Postupy: Přidávání ovládacích prvků do kolekce a odebírání ovládacích prvků z kolekce za běhu</span><span class="sxs-lookup"><span data-stu-id="e3602-102">How to: Add to or Remove from a Collection of Controls at Run Time</span></span>
<span data-ttu-id="e3602-103">Běžné úlohy při vývoji aplikací přidávají ovládací prvky do a odebírání ovládacích prvků z libovolného ovládacího prvku kontejner ve formulářích (například <xref:System.Windows.Forms.Panel> ovládacího <xref:System.Windows.Forms.GroupBox> prvku nebo nebo i formuláře samotného).</span><span class="sxs-lookup"><span data-stu-id="e3602-103">Common tasks in application development are adding controls to and removing controls from any container control on your forms (such as the <xref:System.Windows.Forms.Panel> or <xref:System.Windows.Forms.GroupBox> control, or even the form itself).</span></span> <span data-ttu-id="e3602-104">V době návrhu lze ovládací prvky přetahovat přímo do panelu nebo skupinového pole.</span><span class="sxs-lookup"><span data-stu-id="e3602-104">At design time, controls can be dragged directly onto a panel or group box.</span></span> <span data-ttu-id="e3602-105">V době běhu tyto ovládací prvky udržují `Controls` kolekci, která uchovává přehled o tom, které ovládací prvky jsou na ně umístěny.</span><span class="sxs-lookup"><span data-stu-id="e3602-105">At run time, these controls maintain a `Controls` collection, which keeps track of what controls are placed on them.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e3602-106">Následující příklad kódu se vztahuje na jakýkoli ovládací prvek, který udržuje kolekci ovládacích prvků v rámci něj.</span><span class="sxs-lookup"><span data-stu-id="e3602-106">The following code example applies to any control that maintains a collection of controls within it.</span></span>  
  
### <a name="to-add-a-control-to-a-collection-programmatically"></a><span data-ttu-id="e3602-107">Postup přidání ovládacího prvku do kolekce prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="e3602-107">To add a control to a collection programmatically</span></span>  
  
1. <span data-ttu-id="e3602-108">Vytvořte instanci ovládacího prvku, který chcete přidat.</span><span class="sxs-lookup"><span data-stu-id="e3602-108">Create an instance of the control to be added.</span></span>  
  
2. <span data-ttu-id="e3602-109">Nastavte vlastnosti nového ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e3602-109">Set properties of the new control.</span></span>  
  
3. <span data-ttu-id="e3602-110">Přidejte ovládací prvek do `Controls` kolekce nadřazeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e3602-110">Add the control to the `Controls` collection of the parent control.</span></span>  
  
     <span data-ttu-id="e3602-111">Následující příklad kódu ukazuje, jak vytvořit instanci <xref:System.Windows.Forms.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e3602-111">The following code example shows how to create an instance of the <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="e3602-112">Vyžaduje formulář s <xref:System.Windows.Forms.Panel> ovládacím prvkem a, že metoda zpracování událostí pro tlačítko, která je vytvořena, `NewPanelButton_Click`již existuje.</span><span class="sxs-lookup"><span data-stu-id="e3602-112">It requires a form with a <xref:System.Windows.Forms.Panel> control and that the event-handling method for the button being created, `NewPanelButton_Click`, already exists.</span></span>  
  
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
  
### <a name="to-remove-controls-from-a-collection-programmatically"></a><span data-ttu-id="e3602-113">Postup při odebírání ovládacích prvků z kolekce prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="e3602-113">To remove controls from a collection programmatically</span></span>  
  
1. <span data-ttu-id="e3602-114">Odeberte obslužnou rutinu události z události.</span><span class="sxs-lookup"><span data-stu-id="e3602-114">Remove the event handler from the event.</span></span> <span data-ttu-id="e3602-115">V Visual Basic použijte klíčové slovo [příkaz removeHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md) ; v C#použijte [operátor-=](../../../csharp/language-reference/operators/subtraction-operator.md).</span><span class="sxs-lookup"><span data-stu-id="e3602-115">In Visual Basic, use the [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md) keyword; in C#, use the [-= operator](../../../csharp/language-reference/operators/subtraction-operator.md).</span></span>  
  
2. <span data-ttu-id="e3602-116">Použijte metodu k odstranění požadovaného ovládacího prvku z `Controls` kolekce panelu. `Remove`</span><span class="sxs-lookup"><span data-stu-id="e3602-116">Use the `Remove` method to delete the desired control from the panel's `Controls` collection.</span></span>  
  
3. <span data-ttu-id="e3602-117"><xref:System.Windows.Forms.Control.Dispose%2A> Zavolejte metodu pro uvolnění všech prostředků, které ovládací prvek používá.</span><span class="sxs-lookup"><span data-stu-id="e3602-117">Call the <xref:System.Windows.Forms.Control.Dispose%2A> method to release all the resources used by the control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e3602-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e3602-118">See also</span></span>

- <xref:System.Windows.Forms.Panel>
- [<span data-ttu-id="e3602-119">Ovládací prvek Panel</span><span class="sxs-lookup"><span data-stu-id="e3602-119">Panel Control</span></span>](panel-control-windows-forms.md)
