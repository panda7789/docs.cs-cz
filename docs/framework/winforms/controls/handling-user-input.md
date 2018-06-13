---
title: Zpracování uživatelského vstupu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], user input using code
- custom controls [Windows Forms], keyboard events using code
- custom controls [Windows Forms], mouse events using code
ms.assetid: d9b12787-86f6-4022-8e0f-e12d312c4af2
ms.openlocfilehash: a230611bfbb0a7f21a96de22674377887cc93c2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527797"
---
# <a name="handling-user-input"></a><span data-ttu-id="3f49f-102">Zpracování uživatelského vstupu</span><span class="sxs-lookup"><span data-stu-id="3f49f-102">Handling User Input</span></span>
<span data-ttu-id="3f49f-103">Toto téma popisuje hlavní události klávesnice a myši poskytované <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3f49f-103">This topic describes the main keyboard and mouse events provided by <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3f49f-104">Při zpracování události, by měly přepsat autoři řízení chráněného `On` *EventName* metoda místo připojení delegáta k události.</span><span class="sxs-lookup"><span data-stu-id="3f49f-104">When handling an event, control authors should override the protected `On`*EventName* method rather than attaching a delegate to the event.</span></span> <span data-ttu-id="3f49f-105">Ke kontrole událostí, najdete v části [vyvolání události ze součásti](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).</span><span class="sxs-lookup"><span data-stu-id="3f49f-105">For a review of events, see [Raising Events from a Component](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3f49f-106">Pokud nejsou žádná data přidružená události instance základní třídy <xref:System.EventArgs> je předat jako argument k `On` *EventName* metoda.</span><span class="sxs-lookup"><span data-stu-id="3f49f-106">If there is no data associated with an event, an instance of the base class <xref:System.EventArgs> is passed as an argument to the `On`*EventName* method.</span></span>  
  
## <a name="keyboard-events"></a><span data-ttu-id="3f49f-107">Události klávesnice</span><span class="sxs-lookup"><span data-stu-id="3f49f-107">Keyboard Events</span></span>  
 <span data-ttu-id="3f49f-108">Jsou běžné události klávesnice, které může zpracovat vlastního ovládacího prvku <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, a <xref:System.Windows.Forms.Control.KeyUp>.</span><span class="sxs-lookup"><span data-stu-id="3f49f-108">The common keyboard events that your control can handle are <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, and <xref:System.Windows.Forms.Control.KeyUp>.</span></span>  
  
|<span data-ttu-id="3f49f-109">Název události</span><span class="sxs-lookup"><span data-stu-id="3f49f-109">Event Name</span></span>|<span data-ttu-id="3f49f-110">Metoda k přepsání</span><span class="sxs-lookup"><span data-stu-id="3f49f-110">Method to Override</span></span>|<span data-ttu-id="3f49f-111">Popis události</span><span class="sxs-lookup"><span data-stu-id="3f49f-111">Description of Event</span></span>|  
|----------------|------------------------|--------------------------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|<span data-ttu-id="3f49f-112">Vyvolána, pouze pokud původně stisknutí klávesy.</span><span class="sxs-lookup"><span data-stu-id="3f49f-112">Raised only when a key is initially pressed.</span></span>|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|<span data-ttu-id="3f49f-113">Vyvolá se pokaždé, když stisknutí klávesy.</span><span class="sxs-lookup"><span data-stu-id="3f49f-113">Raised every time a key is pressed.</span></span> <span data-ttu-id="3f49f-114">Pokud je klávesa stisknuta, <xref:System.Windows.Forms.Control.KeyPress> událost se vyvolá při opakovaném míry definované v operačním systému.</span><span class="sxs-lookup"><span data-stu-id="3f49f-114">If a key is held down, a <xref:System.Windows.Forms.Control.KeyPress> event is raised at the repeat rate defined by the operating system.</span></span>|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|<span data-ttu-id="3f49f-115">Vyvolá, když uvolnění klávesy.</span><span class="sxs-lookup"><span data-stu-id="3f49f-115">Raised when a key is released.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="3f49f-116">Zpracování vstupu klávesnice je podstatně složitější než přepsání události v předchozí tabulce a je nad rámec tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="3f49f-116">Handling keyboard input is considerably more complex than overriding the events in the preceding table and is beyond the scope of this topic.</span></span> <span data-ttu-id="3f49f-117">Další informace najdete v tématu [uživatelský vstup ve Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="3f49f-117">For more information, see [User Input in Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md).</span></span>  
  
## <a name="mouse-events"></a><span data-ttu-id="3f49f-118">Události myši</span><span class="sxs-lookup"><span data-stu-id="3f49f-118">Mouse Events</span></span>  
 <span data-ttu-id="3f49f-119">Události myši, které může zpracovat vlastního ovládacího prvku jsou <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove>, a <xref:System.Windows.Forms.Control.MouseUp>.</span><span class="sxs-lookup"><span data-stu-id="3f49f-119">The mouse events that your control can handle are <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove>, and <xref:System.Windows.Forms.Control.MouseUp>.</span></span>  
  
|<span data-ttu-id="3f49f-120">Název události</span><span class="sxs-lookup"><span data-stu-id="3f49f-120">Event Name</span></span>|<span data-ttu-id="3f49f-121">Metoda k přepsání</span><span class="sxs-lookup"><span data-stu-id="3f49f-121">Method to Override</span></span>|<span data-ttu-id="3f49f-122">Popis události</span><span class="sxs-lookup"><span data-stu-id="3f49f-122">Description of Event</span></span>|  
|----------------|------------------------|--------------------------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|<span data-ttu-id="3f49f-123">Vyvolána při stisknutí tlačítka myši při ukazatel myši nad ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="3f49f-123">Raised when the mouse button is pressed while the pointer is over the control.</span></span>|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|<span data-ttu-id="3f49f-124">Vyvolá, když ukazatel vstoupí nejprve oblast ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3f49f-124">Raised when the pointer first enters the region of the control.</span></span>|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|<span data-ttu-id="3f49f-125">Vyvolá, když ukazatelem myši ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="3f49f-125">Raised when the pointer hovers over the control.</span></span>|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|<span data-ttu-id="3f49f-126">Vyvolá, když ukazatel opustí oblast ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3f49f-126">Raised when the pointer leaves the region of the control.</span></span>|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|<span data-ttu-id="3f49f-127">Vyvolána při umístění ukazatele v oblasti řízení.</span><span class="sxs-lookup"><span data-stu-id="3f49f-127">Raised when the pointer moves in the region of the control.</span></span>|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|<span data-ttu-id="3f49f-128">Vyvolá, když je uvolnění tlačítka myši, když je ukazatel myši nad ovládací prvek nebo když ukazatel opustí oblast ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3f49f-128">Raised when the mouse button is released while the pointer is over the control or the pointer leaves the region of the control.</span></span>|  
  
 <span data-ttu-id="3f49f-129">Následující fragment kódu ukazuje příklad přepsání <xref:System.Windows.Forms.Control.MouseDown> událostí.</span><span class="sxs-lookup"><span data-stu-id="3f49f-129">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseDown> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 <span data-ttu-id="3f49f-130">Následující fragment kódu ukazuje příklad přepsání <xref:System.Windows.Forms.Control.MouseMove> událostí.</span><span class="sxs-lookup"><span data-stu-id="3f49f-130">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseMove> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 <span data-ttu-id="3f49f-131">Následující fragment kódu ukazuje příklad přepsání <xref:System.Windows.Forms.Control.MouseUp> událostí.</span><span class="sxs-lookup"><span data-stu-id="3f49f-131">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseUp> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 <span data-ttu-id="3f49f-132">Pro úplný zdrojový kód `FlashTrackBar` ukázkové najdete v tématu [postupy: vytvoření Windows Forms ovládací prvek, zobrazuje průběh](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span><span class="sxs-lookup"><span data-stu-id="3f49f-132">For the complete source code for the `FlashTrackBar` sample, see [How to: Create a Windows Forms Control That Shows Progress](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f49f-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f49f-133">See Also</span></span>  
 [<span data-ttu-id="3f49f-134">Události v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3f49f-134">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 [<span data-ttu-id="3f49f-135">Definování události</span><span class="sxs-lookup"><span data-stu-id="3f49f-135">Defining an Event</span></span>](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)  
 [<span data-ttu-id="3f49f-136">Události</span><span class="sxs-lookup"><span data-stu-id="3f49f-136">Events</span></span>](../../../../docs/standard/events/index.md)  
 [<span data-ttu-id="3f49f-137">Uživatelský vstup ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3f49f-137">User Input in Windows Forms</span></span>](../../../../docs/framework/winforms/user-input-in-windows-forms.md)
