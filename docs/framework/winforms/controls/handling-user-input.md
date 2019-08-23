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
ms.openlocfilehash: f92b742c3f6feec72e5b3150204d7d984636281d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934096"
---
# <a name="handling-user-input"></a><span data-ttu-id="016d4-102">Zpracování uživatelského vstupu</span><span class="sxs-lookup"><span data-stu-id="016d4-102">Handling User Input</span></span>
<span data-ttu-id="016d4-103">Toto téma popisuje hlavní události klávesnice a myši, které <xref:System.Windows.Forms.Control?displayProperty=nameWithType>poskytuje.</span><span class="sxs-lookup"><span data-stu-id="016d4-103">This topic describes the main keyboard and mouse events provided by <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="016d4-104">Při zpracování události by autoři ovládacího prvku měli přepsat chráněnou `On`metodu *EventName* místo připojení delegáta události.</span><span class="sxs-lookup"><span data-stu-id="016d4-104">When handling an event, control authors should override the protected `On`*EventName* method rather than attaching a delegate to the event.</span></span> <span data-ttu-id="016d4-105">Informace o revizi událostí naleznete v tématu [vyvolání událostí ze součásti](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="016d4-105">For a review of events, see [Raising Events from a Component](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="016d4-106">Pokud nejsou k události přidružena žádná data, instance základní třídy <xref:System.EventArgs> je předána jako argument `On`metodě *EventName* .</span><span class="sxs-lookup"><span data-stu-id="016d4-106">If there is no data associated with an event, an instance of the base class <xref:System.EventArgs> is passed as an argument to the `On`*EventName* method.</span></span>  
  
## <a name="keyboard-events"></a><span data-ttu-id="016d4-107">Události klávesnice</span><span class="sxs-lookup"><span data-stu-id="016d4-107">Keyboard Events</span></span>  
 <span data-ttu-id="016d4-108">Běžné události klávesnice, které může váš ovládací prvek zpracovávat <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>jsou, <xref:System.Windows.Forms.Control.KeyUp>a.</span><span class="sxs-lookup"><span data-stu-id="016d4-108">The common keyboard events that your control can handle are <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, and <xref:System.Windows.Forms.Control.KeyUp>.</span></span>  
  
|<span data-ttu-id="016d4-109">Název události</span><span class="sxs-lookup"><span data-stu-id="016d4-109">Event Name</span></span>|<span data-ttu-id="016d4-110">Metoda, která se má přepsat</span><span class="sxs-lookup"><span data-stu-id="016d4-110">Method to Override</span></span>|<span data-ttu-id="016d4-111">Popis události</span><span class="sxs-lookup"><span data-stu-id="016d4-111">Description of Event</span></span>|  
|----------------|------------------------|--------------------------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|<span data-ttu-id="016d4-112">Vyvolá se pouze při počátečním stisknutí klávesy.</span><span class="sxs-lookup"><span data-stu-id="016d4-112">Raised only when a key is initially pressed.</span></span>|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|<span data-ttu-id="016d4-113">Vyvolá se při každém stisknutí klávesy.</span><span class="sxs-lookup"><span data-stu-id="016d4-113">Raised every time a key is pressed.</span></span> <span data-ttu-id="016d4-114">Pokud je klíč podržený, <xref:System.Windows.Forms.Control.KeyPress> vyvolá se událost na základě rychlosti opakování definované operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="016d4-114">If a key is held down, a <xref:System.Windows.Forms.Control.KeyPress> event is raised at the repeat rate defined by the operating system.</span></span>|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|<span data-ttu-id="016d4-115">Vyvolá se při uvolnění klávesy.</span><span class="sxs-lookup"><span data-stu-id="016d4-115">Raised when a key is released.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="016d4-116">Zpracování vstupu z klávesnice je podstatně složitější než přepsání událostí v předchozí tabulce a je nad rámec tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="016d4-116">Handling keyboard input is considerably more complex than overriding the events in the preceding table and is beyond the scope of this topic.</span></span> <span data-ttu-id="016d4-117">Další informace najdete v tématu [vstup uživatele v model Windows Forms](../user-input-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="016d4-117">For more information, see [User Input in Windows Forms](../user-input-in-windows-forms.md).</span></span>  
  
## <a name="mouse-events"></a><span data-ttu-id="016d4-118">Události myši</span><span class="sxs-lookup"><span data-stu-id="016d4-118">Mouse Events</span></span>  
 <span data-ttu-id="016d4-119">Události myši, které ovládací prvek může zpracovat, <xref:System.Windows.Forms.Control.MouseDown> <xref:System.Windows.Forms.Control.MouseEnter>jsou, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove>, a <xref:System.Windows.Forms.Control.MouseUp>.</span><span class="sxs-lookup"><span data-stu-id="016d4-119">The mouse events that your control can handle are <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove>, and <xref:System.Windows.Forms.Control.MouseUp>.</span></span>  
  
|<span data-ttu-id="016d4-120">Název události</span><span class="sxs-lookup"><span data-stu-id="016d4-120">Event Name</span></span>|<span data-ttu-id="016d4-121">Metoda, která se má přepsat</span><span class="sxs-lookup"><span data-stu-id="016d4-121">Method to Override</span></span>|<span data-ttu-id="016d4-122">Popis události</span><span class="sxs-lookup"><span data-stu-id="016d4-122">Description of Event</span></span>|  
|----------------|------------------------|--------------------------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|<span data-ttu-id="016d4-123">Je aktivována při stisknutí tlačítka myši, zatímco je ukazatel nad ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="016d4-123">Raised when the mouse button is pressed while the pointer is over the control.</span></span>|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|<span data-ttu-id="016d4-124">Je aktivována, když ukazatel poprvé vstoupí do oblasti ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="016d4-124">Raised when the pointer first enters the region of the control.</span></span>|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|<span data-ttu-id="016d4-125">Je aktivována, když ukazatel myši najede myší na ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="016d4-125">Raised when the pointer hovers over the control.</span></span>|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|<span data-ttu-id="016d4-126">Je aktivována, když ukazatel opustí oblast ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="016d4-126">Raised when the pointer leaves the region of the control.</span></span>|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|<span data-ttu-id="016d4-127">Je aktivována, když se ukazatel pohybuje v oblasti ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="016d4-127">Raised when the pointer moves in the region of the control.</span></span>|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|<span data-ttu-id="016d4-128">Je aktivována při uvolnění tlačítka myši, když je ukazatel nad ovládacím prvkem, nebo když ukazatel opustí oblast ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="016d4-128">Raised when the mouse button is released while the pointer is over the control or the pointer leaves the region of the control.</span></span>|  
  
 <span data-ttu-id="016d4-129">Následující fragment kódu ukazuje příklad přepsání <xref:System.Windows.Forms.Control.MouseDown> události.</span><span class="sxs-lookup"><span data-stu-id="016d4-129">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseDown> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 <span data-ttu-id="016d4-130">Následující fragment kódu ukazuje příklad přepsání <xref:System.Windows.Forms.Control.MouseMove> události.</span><span class="sxs-lookup"><span data-stu-id="016d4-130">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseMove> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 <span data-ttu-id="016d4-131">Následující fragment kódu ukazuje příklad přepsání <xref:System.Windows.Forms.Control.MouseUp> události.</span><span class="sxs-lookup"><span data-stu-id="016d4-131">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseUp> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 <span data-ttu-id="016d4-132">Úplný zdrojový kód pro `FlashTrackBar` ukázku naleznete v tématu [How to: Vytvoří ovládací prvek model Windows Forms, který zobrazuje](how-to-create-a-windows-forms-control-that-shows-progress.md)průběh.</span><span class="sxs-lookup"><span data-stu-id="016d4-132">For the complete source code for the `FlashTrackBar` sample, see [How to: Create a Windows Forms Control That Shows Progress](how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="016d4-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="016d4-133">See also</span></span>

- [<span data-ttu-id="016d4-134">Události v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="016d4-134">Events in Windows Forms Controls</span></span>](events-in-windows-forms-controls.md)
- [<span data-ttu-id="016d4-135">Definování události</span><span class="sxs-lookup"><span data-stu-id="016d4-135">Defining an Event</span></span>](defining-an-event-in-windows-forms-controls.md)
- [<span data-ttu-id="016d4-136">Události</span><span class="sxs-lookup"><span data-stu-id="016d4-136">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="016d4-137">Uživatelský vstup ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="016d4-137">User Input in Windows Forms</span></span>](../user-input-in-windows-forms.md)
