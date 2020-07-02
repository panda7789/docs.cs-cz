---
title: 'Postupy: připojení více událostí k jedné obslužné rutině události'
description: Naučte se, jak připojit více událostí k jedné obslužné rutině události v model Windows Forms pomocí zobrazení událostí okno Vlastnosti v C#.
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
ms.openlocfilehash: cca85c223b46d9a82dbc3e34e3377fb83c075959
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621883"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a><span data-ttu-id="39c88-103">Postupy: Připojení více událostí k jedné obslužné rutině událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="39c88-103">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>
<span data-ttu-id="39c88-104">V návrhu aplikace může být nutné použít jednu obslužnou rutinu události pro více událostí nebo mít více událostí stejný postup.</span><span class="sxs-lookup"><span data-stu-id="39c88-104">In your application design, you may find it necessary to use a single event handler for multiple events or have multiple events perform the same procedure.</span></span> <span data-ttu-id="39c88-105">Například je často účinný časový okamžik, který má příkaz nabídky vyvolat stejnou událost jako tlačítko na formuláři, pokud vystavuje stejné funkce.</span><span class="sxs-lookup"><span data-stu-id="39c88-105">For example, it is often a powerful time-saver to have a menu command raise the same event as a button on your form does if they expose the same functionality.</span></span> <span data-ttu-id="39c88-106">Můžete to provést pomocí zobrazení událostí okno Vlastnosti v C# nebo pomocí `Handles` rozevíracích seznamů název **třídy** a názvu **metody** v editoru kódu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="39c88-106">You can do this by using the Events view of the Properties window in C# or using the `Handles` keyword and the **Class Name** and **Method Name** drop-down boxes in the Visual Basic Code Editor.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a><span data-ttu-id="39c88-107">Připojení více událostí k jedné obslužné rutině události v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="39c88-107">To connect multiple events to a single event handler in Visual Basic</span></span>  
  
1. <span data-ttu-id="39c88-108">Klikněte pravým tlačítkem na formulář a vyberte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="39c88-108">Right-click the form and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="39c88-109">Z rozevíracího seznamu **název třídy** vyberte jeden z ovládacích prvků, u kterých chcete obslužnou rutinu události zpracovat.</span><span class="sxs-lookup"><span data-stu-id="39c88-109">From the **Class Name** drop-down box, select one of the controls that you want to have the event handler handle.</span></span>  
  
3. <span data-ttu-id="39c88-110">V rozevíracím seznamu **název metody** vyberte jednu z událostí, které má obslužná rutina události zpracovat.</span><span class="sxs-lookup"><span data-stu-id="39c88-110">From the **Method Name** drop-down box, select one of the events that you want the event handler to handle.</span></span>  
  
4. <span data-ttu-id="39c88-111">Editor kódu vloží příslušnou obslužnou rutinu události a umístí kurzor do metody.</span><span class="sxs-lookup"><span data-stu-id="39c88-111">The Code Editor inserts the appropriate event handler and positions the insertion point within the method.</span></span> <span data-ttu-id="39c88-112">V následujícím příkladu je to <xref:System.Windows.Forms.Control.Click> událost <xref:System.Windows.Forms.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="39c88-112">In the example below, it is the <xref:System.Windows.Forms.Control.Click> event for the <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5. <span data-ttu-id="39c88-113">Do klauzule přidejte další události, které byste chtěli zpracovat `Handles` .</span><span class="sxs-lookup"><span data-stu-id="39c88-113">Append the other events you would like handled to the `Handles` clause.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6. <span data-ttu-id="39c88-114">Přidejte příslušný kód do obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="39c88-114">Add the appropriate code to the event handler.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a><span data-ttu-id="39c88-115">Připojení více událostí k jedné obslužné rutině události v jazyce C\#</span><span class="sxs-lookup"><span data-stu-id="39c88-115">To connect multiple events to a single event handler in C\#</span></span>
  
1. <span data-ttu-id="39c88-116">Vyberte ovládací prvek, ke kterému chcete připojit obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="39c88-116">Select the control to which you want to connect an event handler.</span></span>  
  
2. <span data-ttu-id="39c88-117">V okno Vlastnosti klikněte na tlačítko **události** (![tlačítko události](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span><span class="sxs-lookup"><span data-stu-id="39c88-117">In the Properties window, click the **Events** button (![Events Button](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span></span>  
  
3. <span data-ttu-id="39c88-118">Klikněte na název události, kterou chcete zpracovat.</span><span class="sxs-lookup"><span data-stu-id="39c88-118">Click the name of the event that you want to handle.</span></span>  
  
4. <span data-ttu-id="39c88-119">V části hodnota vedle názvu události klikněte na tlačítko rozevíracího seznamu a zobrazí se seznam existujících obslužných rutin událostí, které odpovídají podpisu metody události, kterou chcete zpracovat.</span><span class="sxs-lookup"><span data-stu-id="39c88-119">In the value section next to the event name, click the drop-down button to display a list of existing event handlers that match the method signature of the event you want to handle.</span></span>  
  
5. <span data-ttu-id="39c88-120">V seznamu vyberte příslušnou obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="39c88-120">Select the appropriate event handler from the list.</span></span>  
  
     <span data-ttu-id="39c88-121">Kód se přidá do formuláře, aby se událost navázala na existující obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="39c88-121">Code will be added to the form to bind the event to the existing event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39c88-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="39c88-122">See also</span></span>

- [<span data-ttu-id="39c88-123">Vytváření obslužných rutin událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="39c88-123">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="39c88-124">Přehled obslužných rutin událostí</span><span class="sxs-lookup"><span data-stu-id="39c88-124">Event Handlers Overview</span></span>](event-handlers-overview-windows-forms.md)
