---
title: 'Postupy: připojení více událostí k jedné obslužné rutině události'
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
ms.openlocfilehash: 0591291522ab1da04fef90bf1c0a73cf33ba0518
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739605"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a><span data-ttu-id="a6cf9-102">Postupy: Připojení více událostí k jedné obslužné rutině událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a6cf9-102">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>
<span data-ttu-id="a6cf9-103">V návrhu aplikace může být nutné použít jednu obslužnou rutinu události pro více událostí nebo mít více událostí stejný postup.</span><span class="sxs-lookup"><span data-stu-id="a6cf9-103">In your application design, you may find it necessary to use a single event handler for multiple events or have multiple events perform the same procedure.</span></span> <span data-ttu-id="a6cf9-104">Například je často účinný časový okamžik, který má příkaz nabídky vyvolat stejnou událost jako tlačítko na formuláři, pokud vystavuje stejné funkce.</span><span class="sxs-lookup"><span data-stu-id="a6cf9-104">For example, it is often a powerful time-saver to have a menu command raise the same event as a button on your form does if they expose the same functionality.</span></span> <span data-ttu-id="a6cf9-105">To lze provést pomocí zobrazení událostí okno Vlastnosti v C# nebo pomocí klíčového slova `Handles` a rozevíracího seznamu název **třídy** a **názvu metody** v editoru kódu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a6cf9-105">You can do this by using the Events view of the Properties window in C# or using the `Handles` keyword and the **Class Name** and **Method Name** drop-down boxes in the Visual Basic Code Editor.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a><span data-ttu-id="a6cf9-106">Připojení více událostí k jedné obslužné rutině události v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a6cf9-106">To connect multiple events to a single event handler in Visual Basic</span></span>  
  
1. <span data-ttu-id="a6cf9-107">Klikněte pravým tlačítkem na formulář a vyberte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="a6cf9-107">Right-click the form and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="a6cf9-108">Z rozevíracího seznamu **název třídy** vyberte jeden z ovládacích prvků, u kterých chcete obslužnou rutinu události zpracovat.</span><span class="sxs-lookup"><span data-stu-id="a6cf9-108">From the **Class Name** drop-down box, select one of the controls that you want to have the event handler handle.</span></span>  
  
3. <span data-ttu-id="a6cf9-109">V rozevíracím seznamu **název metody** vyberte jednu z událostí, které má obslužná rutina události zpracovat.</span><span class="sxs-lookup"><span data-stu-id="a6cf9-109">From the **Method Name** drop-down box, select one of the events that you want the event handler to handle.</span></span>  
  
4. <span data-ttu-id="a6cf9-110">Editor kódu vloží příslušnou obslužnou rutinu události a umístí kurzor do metody.</span><span class="sxs-lookup"><span data-stu-id="a6cf9-110">The Code Editor inserts the appropriate event handler and positions the insertion point within the method.</span></span> <span data-ttu-id="a6cf9-111">V následujícím příkladu je to událost <xref:System.Windows.Forms.Control.Click> pro ovládací prvek <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="a6cf9-111">In the example below, it is the <xref:System.Windows.Forms.Control.Click> event for the <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5. <span data-ttu-id="a6cf9-112">Přidejte další události, které chcete zpracovat, do klauzule `Handles`.</span><span class="sxs-lookup"><span data-stu-id="a6cf9-112">Append the other events you would like handled to the `Handles` clause.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6. <span data-ttu-id="a6cf9-113">Přidejte příslušný kód do obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="a6cf9-113">Add the appropriate code to the event handler.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a><span data-ttu-id="a6cf9-114">Připojení více událostí k jedné obslužné rutině události v jazyce C\#</span><span class="sxs-lookup"><span data-stu-id="a6cf9-114">To connect multiple events to a single event handler in C\#</span></span>
  
1. <span data-ttu-id="a6cf9-115">Vyberte ovládací prvek, ke kterému chcete připojit obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="a6cf9-115">Select the control to which you want to connect an event handler.</span></span>  
  
2. <span data-ttu-id="a6cf9-116">V okno Vlastnosti klikněte na tlačítko **události** (![tlačítko události](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span><span class="sxs-lookup"><span data-stu-id="a6cf9-116">In the Properties window, click the **Events** button (![Events Button](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span></span>  
  
3. <span data-ttu-id="a6cf9-117">Klikněte na název události, kterou chcete zpracovat.</span><span class="sxs-lookup"><span data-stu-id="a6cf9-117">Click the name of the event that you want to handle.</span></span>  
  
4. <span data-ttu-id="a6cf9-118">V části hodnota vedle názvu události klikněte na tlačítko rozevíracího seznamu a zobrazí se seznam existujících obslužných rutin událostí, které odpovídají podpisu metody události, kterou chcete zpracovat.</span><span class="sxs-lookup"><span data-stu-id="a6cf9-118">In the value section next to the event name, click the drop-down button to display a list of existing event handlers that match the method signature of the event you want to handle.</span></span>  
  
5. <span data-ttu-id="a6cf9-119">V seznamu vyberte příslušnou obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="a6cf9-119">Select the appropriate event handler from the list.</span></span>  
  
     <span data-ttu-id="a6cf9-120">Kód se přidá do formuláře, aby se událost navázala na existující obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="a6cf9-120">Code will be added to the form to bind the event to the existing event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6cf9-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="a6cf9-121">See also</span></span>

- [<span data-ttu-id="a6cf9-122">Vytváření obslužných rutin událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a6cf9-122">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="a6cf9-123">Přehled obslužných rutin událostí</span><span class="sxs-lookup"><span data-stu-id="a6cf9-123">Event Handlers Overview</span></span>](event-handlers-overview-windows-forms.md)
