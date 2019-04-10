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
ms.openlocfilehash: eec6a754b885cd169e5542221caefb3233c4c8af
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59300720"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a><span data-ttu-id="3b7f5-102">Postupy: Připojení více událostí k jedné obslužné rutině událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3b7f5-102">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>
<span data-ttu-id="3b7f5-103">V návrhu aplikace možná bude nutné použít jedné obslužné rutině událostí pro více událostí nebo mít více událostí, použijte stejný postup.</span><span class="sxs-lookup"><span data-stu-id="3b7f5-103">In your application design, you may find it necessary to use a single event handler for multiple events or have multiple events perform the same procedure.</span></span> <span data-ttu-id="3b7f5-104">Je například často výkonné spoustu času mít příkaz nabídky vyvolat stejnou událost, stejně jako tlačítko na formuláři pokud zveřejňovaly stejné funkce.</span><span class="sxs-lookup"><span data-stu-id="3b7f5-104">For example, it is often a powerful time-saver to have a menu command raise the same event as a button on your form does if they expose the same functionality.</span></span> <span data-ttu-id="3b7f5-105">Můžete to provést pomocí zobrazení události v okně Vlastnosti v C# nebo pomocí `Handles` – klíčové slovo a **název třídy** a **název metody** rozevírací seznamy v editoru kódu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3b7f5-105">You can do this by using the Events view of the Properties window in C# or using the `Handles` keyword and the **Class Name** and **Method Name** drop-down boxes in the Visual Basic Code Editor.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a><span data-ttu-id="3b7f5-106">Připojení více událostí k obslužné rutině jedné události v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3b7f5-106">To connect multiple events to a single event handler in Visual Basic</span></span>  
  
1. <span data-ttu-id="3b7f5-107">Klikněte pravým tlačítkem na formuláři a zvolte **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="3b7f5-107">Right-click the form and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="3b7f5-108">Z **název třídy** rozevíracího seznamu vyberte jednu z ovládacích prvků, které chcete mít obslužná rutina události zpracovávají.</span><span class="sxs-lookup"><span data-stu-id="3b7f5-108">From the **Class Name** drop-down box, select one of the controls that you want to have the event handler handle.</span></span>  
  
3. <span data-ttu-id="3b7f5-109">Z **název metody** rozevíracího seznamu vyberte jednu z událostí, které chcete, aby obslužná rutina události pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="3b7f5-109">From the **Method Name** drop-down box, select one of the events that you want the event handler to handle.</span></span>  
  
4. <span data-ttu-id="3b7f5-110">Editor kódu vloží obslužná rutina odpovídající události a umístí kurzor do metody.</span><span class="sxs-lookup"><span data-stu-id="3b7f5-110">The Code Editor inserts the appropriate event handler and positions the insertion point within the method.</span></span> <span data-ttu-id="3b7f5-111">V následujícím příkladu je <xref:System.Windows.Forms.Control.Click> události <xref:System.Windows.Forms.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3b7f5-111">In the example below, it is the <xref:System.Windows.Forms.Control.Click> event for the <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5. <span data-ttu-id="3b7f5-112">Přidat další události byste chtěli ke zpracování `Handles` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="3b7f5-112">Append the other events you would like handled to the `Handles` clause.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6. <span data-ttu-id="3b7f5-113">Přidáte odpovídající kód do obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="3b7f5-113">Add the appropriate code to the event handler.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a><span data-ttu-id="3b7f5-114">Připojení více událostí k obslužné rutině jedné události v jazyce C\#</span><span class="sxs-lookup"><span data-stu-id="3b7f5-114">To connect multiple events to a single event handler in C\#</span></span>
  
1. <span data-ttu-id="3b7f5-115">Vyberte ovládací prvek, ke kterému chcete připojit obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="3b7f5-115">Select the control to which you want to connect an event handler.</span></span>  
  
2. <span data-ttu-id="3b7f5-116">V okně Vlastnosti klikněte na tlačítko **události** tlačítko (![tlačítko události](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span><span class="sxs-lookup"><span data-stu-id="3b7f5-116">In the Properties window, click the **Events** button (![Events Button](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span></span>  
  
3. <span data-ttu-id="3b7f5-117">Klikněte na název události, ke které chcete zpracovat.</span><span class="sxs-lookup"><span data-stu-id="3b7f5-117">Click the name of the event that you want to handle.</span></span>  
  
4. <span data-ttu-id="3b7f5-118">V části Hodnota vedle názvu události klikněte na tlačítko rozevíracího seznamu zobrazíte seznam existujících, které odpovídají podpis metody, kterou chcete zpracovat událost obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="3b7f5-118">In the value section next to the event name, click the drop-down button to display a list of existing event handlers that match the method signature of the event you want to handle.</span></span>  
  
5. <span data-ttu-id="3b7f5-119">Obslužná rutina události odpovídající vyberte ze seznamu.</span><span class="sxs-lookup"><span data-stu-id="3b7f5-119">Select the appropriate event handler from the list.</span></span>  
  
     <span data-ttu-id="3b7f5-120">Kód bude přidán do formuláře pro vazbu události do existující obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="3b7f5-120">Code will be added to the form to bind the event to the existing event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b7f5-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3b7f5-121">See also</span></span>

- [<span data-ttu-id="3b7f5-122">Vytváření obslužných rutin událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3b7f5-122">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="3b7f5-123">Přehled obslužných rutin událostí</span><span class="sxs-lookup"><span data-stu-id="3b7f5-123">Event Handlers Overview</span></span>](event-handlers-overview-windows-forms.md)
