---
title: 'Postupy: Připojení více událostí k jedné obslužné rutině událostí ve Windows Forms'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- events [Windows Forms], connecting multiple to single event handler
- event handlers [Windows Forms], connecting events to
- menus [Windows Forms], event-handling methods for multiple menu items
- Windows Forms controls, events
- menu items [Windows Forms], multicasting event-handling methods
ms.assetid: 5a20749a-41b5-4acc-8eb1-9e5040b0a2c4
ms.openlocfilehash: 527a76376a4c1d5ad051f4768ca2bd42c3548b3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538577"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a><span data-ttu-id="87ba0-102">Postupy: Připojení více událostí k jedné obslužné rutině událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="87ba0-102">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>
<span data-ttu-id="87ba0-103">Při návrhu aplikace možná bude nutné použít více událostí jedné obslužné rutině událostí nebo mít více událostí, použijte stejný postup.</span><span class="sxs-lookup"><span data-stu-id="87ba0-103">In your application design, you may find it necessary to use a single event handler for multiple events or have multiple events perform the same procedure.</span></span> <span data-ttu-id="87ba0-104">Je třeba často výkonné spoustu času tak, aby měl příkaz nabídky vyvolání stejné události, jak to dělá tlačítko ve formuláři, pokud jejich zpřístupnění stejné funkce.</span><span class="sxs-lookup"><span data-stu-id="87ba0-104">For example, it is often a powerful time-saver to have a menu command raise the same event as a button on your form does if they expose the same functionality.</span></span> <span data-ttu-id="87ba0-105">Můžete to provést pomocí zobrazení událostí okna vlastnosti v jazyce C# nebo `Handles` – klíčové slovo a **název třídy** a **název metody** rozevíracího seznamu polí v editoru kódu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="87ba0-105">You can do this by using the Events view of the Properties window in C# or using the `Handles` keyword and the **Class Name** and **Method Name** drop-down boxes in the Visual Basic Code Editor.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a><span data-ttu-id="87ba0-106">Připojení více událostí k jedné obslužné rutině událostí v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="87ba0-106">To connect multiple events to a single event handler in Visual Basic</span></span>  
  
1.  <span data-ttu-id="87ba0-107">Klikněte pravým tlačítkem na formulář a zvolte **kód zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="87ba0-107">Right-click the form and choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="87ba0-108">Z **název třídy** rozevíracího seznamu vyberte jednu z ovládacích prvků, které chcete mít obslužné rutiny události zpracovat.</span><span class="sxs-lookup"><span data-stu-id="87ba0-108">From the **Class Name** drop-down box, select one of the controls that you want to have the event handler handle.</span></span>  
  
3.  <span data-ttu-id="87ba0-109">Z **název metody** rozevíracího seznamu vyberte jednu z události, které chcete obslužné rutiny události pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="87ba0-109">From the **Method Name** drop-down box, select one of the events that you want the event handler to handle.</span></span>  
  
4.  <span data-ttu-id="87ba0-110">Editor kódu vloží obslužné rutiny odpovídající události a umístění kurzoru v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="87ba0-110">The Code Editor inserts the appropriate event handler and positions the insertion point within the method.</span></span> <span data-ttu-id="87ba0-111">V následujícím příkladu je <xref:System.Windows.Forms.Control.Click> události <xref:System.Windows.Forms.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="87ba0-111">In the example below, it is the <xref:System.Windows.Forms.Control.Click> event for the <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5.  <span data-ttu-id="87ba0-112">Připojit ostatní události, které chcete využívá ke `Handles` klauzule.</span><span class="sxs-lookup"><span data-stu-id="87ba0-112">Append the other events you would like handled to the `Handles` clause.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6.  <span data-ttu-id="87ba0-113">Přidejte příslušný kód do obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="87ba0-113">Add the appropriate code to the event handler.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a><span data-ttu-id="87ba0-114">Připojení více událostí k jedné obslužné rutině událostí v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="87ba0-114">To connect multiple events to a single event handler in C#</span></span>  
  
1.  <span data-ttu-id="87ba0-115">Vyberte ovládací prvek, ke kterému se chcete připojit obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="87ba0-115">Select the control to which you want to connect an event handler.</span></span>  
  
2.  <span data-ttu-id="87ba0-116">V okně vlastností klikněte **události** tlačítko (![tlačítko události](../../../docs/framework/winforms/media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span><span class="sxs-lookup"><span data-stu-id="87ba0-116">In the Properties window, click the **Events** button (![Events Button](../../../docs/framework/winforms/media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span></span>  
  
3.  <span data-ttu-id="87ba0-117">Klikněte na název události, která chcete zpracovat.</span><span class="sxs-lookup"><span data-stu-id="87ba0-117">Click the name of the event that you want to handle.</span></span>  
  
4.  <span data-ttu-id="87ba0-118">V části hodnotu vedle názvu události klikněte na tlačítko rozevíracího seznamu můžete zobrazit seznam existujících obslužné rutiny, které odpovídají podpis metody události, kterou chcete zpracovat.</span><span class="sxs-lookup"><span data-stu-id="87ba0-118">In the value section next to the event name, click the drop-down button to display a list of existing event handlers that match the method signature of the event you want to handle.</span></span>  
  
5.  <span data-ttu-id="87ba0-119">Obslužné rutiny události odpovídající vyberte ze seznamu.</span><span class="sxs-lookup"><span data-stu-id="87ba0-119">Select the appropriate event handler from the list.</span></span>  
  
     <span data-ttu-id="87ba0-120">Kód bude přidán do formuláře pro vazbu události pro stávající obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="87ba0-120">Code will be added to the form to bind the event to the existing event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87ba0-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="87ba0-121">See Also</span></span>  
 [<span data-ttu-id="87ba0-122">Vytváření obslužných rutin událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="87ba0-122">Creating Event Handlers in Windows Forms</span></span>](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [<span data-ttu-id="87ba0-123">Přehled obslužných rutin událostí</span><span class="sxs-lookup"><span data-stu-id="87ba0-123">Event Handlers Overview</span></span>](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)
