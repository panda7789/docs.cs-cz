---
title: Události myši ve Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- MouseLeave event [Windows Forms]
- events [Windows Forms], mouse
- Click event [Windows Forms], raising order
- Windows Forms controls, click events
- MouseDoubleClick event [Windows Forms]
- MouseEnter event [Windows Forms]
- MouseHover event [Windows Forms]
- MouseDown event [Windows Forms]
- MouseClick event [Windows Forms]
- MouseMove event [Windows Forms]
- mouse [Windows Forms], events
- MouseUp event
ms.assetid: 8cf0070d-793b-4876-b09e-d20d28280fab
ms.openlocfilehash: a61f4eedde611cfb7598d55465103924516e06c6
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834599"
---
# <a name="mouse-events-in-windows-forms"></a><span data-ttu-id="98e50-102">Události myši ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="98e50-102">Mouse Events in Windows Forms</span></span>

<span data-ttu-id="98e50-103">Při zpracování vstupu myši obvykle chcete znát polohu ukazatele myši a stavu tlačítek myši.</span><span class="sxs-lookup"><span data-stu-id="98e50-103">When you handle mouse input, you usually want to know the location of the mouse pointer and the state of the mouse buttons.</span></span> <span data-ttu-id="98e50-104">Toto téma obsahuje podrobné informace o tom, jak tyto informace z událostí myši získat a vysvětluje pořadí, ve kterém jsou události kliknutí myší vyvolány v ovládacích prvcích model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="98e50-104">This topic provides details on how to get this information from mouse events, and explains the order in which mouse click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="98e50-105">Seznam a popis všech událostí myši najdete [v tématu Jak funguje vstup myši v model Windows Forms](how-mouse-input-works-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="98e50-105">For a list and description of all of the mouse events, see [How Mouse Input Works in Windows Forms](how-mouse-input-works-in-windows-forms.md).</span></span>  <span data-ttu-id="98e50-106">Viz také přehled [obslužných rutin událostí (model Windows Forms)](event-handlers-overview-windows-forms.md) a [přehled událostí (model Windows Forms)](events-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="98e50-106">Also see [Event Handlers Overview (Windows Forms)](event-handlers-overview-windows-forms.md) and [Events Overview (Windows Forms)](events-overview-windows-forms.md).</span></span>

## <a name="mouse-information"></a><span data-ttu-id="98e50-107">Informace o myši</span><span class="sxs-lookup"><span data-stu-id="98e50-107">Mouse Information</span></span>

<span data-ttu-id="98e50-108">@No__t-0 se pošle obslužným rutinám událostí myši souvisejících s kliknutím na tlačítko myši a sledováním pohybu myši.</span><span class="sxs-lookup"><span data-stu-id="98e50-108">A <xref:System.Windows.Forms.MouseEventArgs> is sent to the handlers of mouse events related to clicking a mouse button and tracking mouse movements.</span></span> <span data-ttu-id="98e50-109"><xref:System.Windows.Forms.MouseEventArgs> poskytuje informace o aktuálním stavu myši, včetně umístění ukazatele myši v souřadnicích klienta, vylisovaných tlačítek myši a o tom, zda kolečko myši bylo posunuto.</span><span class="sxs-lookup"><span data-stu-id="98e50-109"><xref:System.Windows.Forms.MouseEventArgs> provides information about the current state of the mouse, including the location of the mouse pointer in client coordinates, which mouse buttons are pressed, and whether the mouse wheel has scrolled.</span></span> <span data-ttu-id="98e50-110">Několik událostí myši, například ty, které jednoduše upozorňují na zadání nebo levé hranice ovládacího prvku, odesílají <xref:System.EventArgs> do obslužné rutiny události bez dalších informací.</span><span class="sxs-lookup"><span data-stu-id="98e50-110">Several mouse events, such as those that simply notify when the mouse pointer has entered or left the bounds of a control, send an <xref:System.EventArgs> to the event handler with no further information.</span></span>

<span data-ttu-id="98e50-111">Pokud chcete zjistit aktuální stav tlačítek myši nebo umístění ukazatele myši a chcete se vyhnout manipulaci s událostí myši, můžete použít také vlastnosti <xref:System.Windows.Forms.Control.MouseButtons%2A> a <xref:System.Windows.Forms.Control.MousePosition%2A> třídy <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="98e50-111">If you want to know the current state of the mouse buttons or the location of the mouse pointer, and you want to avoid handling a mouse event, you can also use the <xref:System.Windows.Forms.Control.MouseButtons%2A> and <xref:System.Windows.Forms.Control.MousePosition%2A> properties of the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="98e50-112"><xref:System.Windows.Forms.Control.MouseButtons%2A> vrátí informace o tom, která tlačítka myši jsou právě stisknutá.</span><span class="sxs-lookup"><span data-stu-id="98e50-112"><xref:System.Windows.Forms.Control.MouseButtons%2A> returns information about which mouse buttons are currently pressed.</span></span> <span data-ttu-id="98e50-113">@No__t-0 vrátí souřadnice obrazovky ukazatele myši a je ekvivalentní hodnotě vrácené <xref:System.Windows.Forms.Cursor.Position%2A>.</span><span class="sxs-lookup"><span data-stu-id="98e50-113">The <xref:System.Windows.Forms.Control.MousePosition%2A> returns the screen coordinates of the mouse pointer and is equivalent to the value returned by <xref:System.Windows.Forms.Cursor.Position%2A>.</span></span>

## <a name="converting-between-screen-and-client-coordinates"></a><span data-ttu-id="98e50-114">Převod mezi souřadnicemi obrazovky a klienta</span><span class="sxs-lookup"><span data-stu-id="98e50-114">Converting Between Screen and Client Coordinates</span></span>

<span data-ttu-id="98e50-115">Vzhledem k tomu, že některé informace o umístění myši jsou v souřadnicích klienta a některé jsou v souřadnicích obrazovky, možná budete muset převést bod z jednoho systému souřadnic na druhý.</span><span class="sxs-lookup"><span data-stu-id="98e50-115">Because some mouse location information is in client coordinates and some is in screen coordinates, you may need to convert a point from one coordinate system to the other.</span></span> <span data-ttu-id="98e50-116">To lze provést snadno pomocí metod @no__t 0 a <xref:System.Windows.Forms.Control.PointToScreen%2A> dostupných ve třídě <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="98e50-116">You can do this easily by using the <xref:System.Windows.Forms.Control.PointToClient%2A> and <xref:System.Windows.Forms.Control.PointToScreen%2A> methods available on the <xref:System.Windows.Forms.Control> class.</span></span>

## <a name="standard-click-event-behavior"></a><span data-ttu-id="98e50-117">Standardní chování události kliknutí</span><span class="sxs-lookup"><span data-stu-id="98e50-117">Standard Click Event Behavior</span></span>

<span data-ttu-id="98e50-118">Pokud chcete zpracovávat události kliknutí myší ve správném pořadí, musíte znát pořadí, ve kterém jsou události kliknutí vyvolány v ovládacích prvcích model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="98e50-118">If you want to handle mouse click events in the proper order, you need to know the order in which click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="98e50-119">Všechny model Windows Forms ovládací prvky vyvolávají události Click ve stejném pořadí při stisknutí a uvolnění tlačítka myši (bez ohledu na to, které tlačítko myši), s výjimkou těch, které jsou uvedeny v následujícím seznamu pro jednotlivé ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="98e50-119">All Windows Forms controls raise click events in the same order when a mouse button is pressed and released (regardless of which mouse button), except where noted in the following list for individual controls.</span></span> <span data-ttu-id="98e50-120">Následující seznam zobrazuje pořadí událostí vyvolaných jedním kliknutím myši na tlačítko:</span><span class="sxs-lookup"><span data-stu-id="98e50-120">The following list shows the order of events raised for a single mouse-button click:</span></span>

1. <span data-ttu-id="98e50-121">událost <xref:System.Windows.Forms.Control.MouseDown></span><span class="sxs-lookup"><span data-stu-id="98e50-121"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

2. <span data-ttu-id="98e50-122">událost <xref:System.Windows.Forms.Control.Click></span><span class="sxs-lookup"><span data-stu-id="98e50-122"><xref:System.Windows.Forms.Control.Click> event.</span></span>

3. <span data-ttu-id="98e50-123">událost <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="98e50-123"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>

4. <span data-ttu-id="98e50-124">událost <xref:System.Windows.Forms.Control.MouseUp></span><span class="sxs-lookup"><span data-stu-id="98e50-124"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

<span data-ttu-id="98e50-125">Následuje pořadí událostí vyvolaných pro dvojité kliknutí myší:</span><span class="sxs-lookup"><span data-stu-id="98e50-125">The following is the order of events raised for a double mouse-button click:</span></span>

1. <span data-ttu-id="98e50-126">událost <xref:System.Windows.Forms.Control.MouseDown></span><span class="sxs-lookup"><span data-stu-id="98e50-126"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

2. <span data-ttu-id="98e50-127">událost <xref:System.Windows.Forms.Control.Click></span><span class="sxs-lookup"><span data-stu-id="98e50-127"><xref:System.Windows.Forms.Control.Click> event.</span></span>

3. <span data-ttu-id="98e50-128">událost <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="98e50-128"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>

4. <span data-ttu-id="98e50-129">událost <xref:System.Windows.Forms.Control.MouseUp></span><span class="sxs-lookup"><span data-stu-id="98e50-129"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

5. <span data-ttu-id="98e50-130">událost <xref:System.Windows.Forms.Control.MouseDown></span><span class="sxs-lookup"><span data-stu-id="98e50-130"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

6. <span data-ttu-id="98e50-131">událost <xref:System.Windows.Forms.Control.DoubleClick></span><span class="sxs-lookup"><span data-stu-id="98e50-131"><xref:System.Windows.Forms.Control.DoubleClick> event.</span></span> <span data-ttu-id="98e50-132">(To se může lišit v závislosti na tom, jestli má daný ovládací prvek nastaven bit stylu <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> na `true`.</span><span class="sxs-lookup"><span data-stu-id="98e50-132">(This can vary, depending on whether the control in question has the <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> style bit set to `true`.</span></span> <span data-ttu-id="98e50-133">Další informace o tom, jak nastavit bit <xref:System.Windows.Forms.ControlStyles>, naleznete v metodě <xref:System.Windows.Forms.Control.SetStyle%2A>.)</span><span class="sxs-lookup"><span data-stu-id="98e50-133">For more information about how to set a <xref:System.Windows.Forms.ControlStyles> bit, see the <xref:System.Windows.Forms.Control.SetStyle%2A> method.)</span></span>

7. <span data-ttu-id="98e50-134">událost <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="98e50-134"><xref:System.Windows.Forms.Control.MouseDoubleClick> event.</span></span>

8. <span data-ttu-id="98e50-135">událost <xref:System.Windows.Forms.Control.MouseUp></span><span class="sxs-lookup"><span data-stu-id="98e50-135"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

<span data-ttu-id="98e50-136">Příklad kódu, který ukazuje pořadí událostí kliknutí myší, naleznete v tématu [How to: Handler User Input events in model Windows Forms Controls](how-to-handle-user-input-events-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="98e50-136">For a code example that demonstrates the order of the mouse click events, see [How to: Handle User Input Events in Windows Forms Controls](how-to-handle-user-input-events-in-windows-forms-controls.md).</span></span>

### <a name="individual-controls"></a><span data-ttu-id="98e50-137">Jednotlivé ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="98e50-137">Individual Controls</span></span>

<span data-ttu-id="98e50-138">Následující ovládací prvky neodpovídají standardnímu chování události kliknutí myší:</span><span class="sxs-lookup"><span data-stu-id="98e50-138">The following controls do not conform to the standard mouse click event behavior:</span></span>

- <xref:System.Windows.Forms.Button>
- <xref:System.Windows.Forms.CheckBox>
- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.RadioButton>

  > [!NOTE]
  > <span data-ttu-id="98e50-139">V případě ovládacího prvku <xref:System.Windows.Forms.ComboBox> dojde k podrobnému chování události, pokud uživatel klikne na pole upravit, tlačítko nebo na položku v seznamu.</span><span class="sxs-lookup"><span data-stu-id="98e50-139">For the <xref:System.Windows.Forms.ComboBox> control, the event behavior detailed later occurs if the user clicks on the edit field, the button, or on an item within the list.</span></span>

  - <span data-ttu-id="98e50-140">Kliknutí levým na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="98e50-140">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="98e50-141">Kliknutí pravým tlačítkem: neaktivována událost kliknutí na události</span><span class="sxs-lookup"><span data-stu-id="98e50-141">Right click: No click events raised</span></span>

  - <span data-ttu-id="98e50-142">Dvakrát klikněte levým na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="98e50-142">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="98e50-143">Dvakrát klikněte pravým tlačítkem myši na událost žádné události kliknutí.</span><span class="sxs-lookup"><span data-stu-id="98e50-143">Right double-click: No click events raised</span></span>

- <span data-ttu-id="98e50-144"><xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox> a <xref:System.Windows.Forms.CheckedListBox> ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="98e50-144"><xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox>, and <xref:System.Windows.Forms.CheckedListBox> controls</span></span>

  > [!NOTE]
  > <span data-ttu-id="98e50-145">K chování události později dojde, když uživatel klikne kamkoli v rámci těchto ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="98e50-145">The event behavior detailed later occurs when the user clicks anywhere within these controls.</span></span>

  - <span data-ttu-id="98e50-146">Kliknutí levým na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="98e50-146">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="98e50-147">Kliknutí pravým tlačítkem: neaktivována událost kliknutí na události</span><span class="sxs-lookup"><span data-stu-id="98e50-147">Right click: No click events raised</span></span>

  - <span data-ttu-id="98e50-148">Dvakrát klikněte levým na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>.</span><span class="sxs-lookup"><span data-stu-id="98e50-148">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="98e50-149">Dvakrát klikněte pravým tlačítkem myši na událost žádné události kliknutí.</span><span class="sxs-lookup"><span data-stu-id="98e50-149">Right double-click: No click events raised</span></span>

- <span data-ttu-id="98e50-150">ovládací prvek <xref:System.Windows.Forms.ListView></span><span class="sxs-lookup"><span data-stu-id="98e50-150"><xref:System.Windows.Forms.ListView> control</span></span>

  > [!NOTE]
  > <span data-ttu-id="98e50-151">K chování události později dojde pouze v případě, že uživatel klikne na položky v ovládacím prvku <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="98e50-151">The event behavior detailed later occurs only when the user clicks on the items in the <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="98e50-152">Pro kliknutí jinde v ovládacím prvku nejsou vyvolány žádné události.</span><span class="sxs-lookup"><span data-stu-id="98e50-152">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="98e50-153">Kromě událostí popsaných dále existují události <xref:System.Windows.Forms.ListView.BeforeLabelEdit> a <xref:System.Windows.Forms.ListView.AfterLabelEdit>, které vás mohou zajímat, pokud chcete použít ověřování pomocí ovládacího prvku <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="98e50-153">In addition to the events described later, there are the <xref:System.Windows.Forms.ListView.BeforeLabelEdit> and <xref:System.Windows.Forms.ListView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.ListView> control.</span></span>

  - <span data-ttu-id="98e50-154">Kliknutí levým na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="98e50-154">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="98e50-155">Klikněte pravým tlačítkem na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>.</span><span class="sxs-lookup"><span data-stu-id="98e50-155">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="98e50-156">Dvakrát klikněte levým na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="98e50-156">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="98e50-157">Klikněte dvakrát na tlačítko: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="98e50-157">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

- <span data-ttu-id="98e50-158">ovládací prvek <xref:System.Windows.Forms.TreeView></span><span class="sxs-lookup"><span data-stu-id="98e50-158"><xref:System.Windows.Forms.TreeView> control</span></span>

  > [!NOTE]
  > <span data-ttu-id="98e50-159">K chování události později dochází pouze v případě, že uživatel klikne na samotné položky nebo napravo od položek v ovládacím prvku <xref:System.Windows.Forms.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="98e50-159">The event behavior detailed later occurs only when the user clicks on the items themselves or to the right of the items in the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="98e50-160">Pro kliknutí jinde v ovládacím prvku nejsou vyvolány žádné události.</span><span class="sxs-lookup"><span data-stu-id="98e50-160">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="98e50-161">Kromě těch popsaných později jsou k dispozici <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck> a <xref:System.Windows.Forms.TreeView.AfterLabelEdit>, které vás mohou zajímat, pokud chcete použít ověřování s ovládacím prvkem <xref:System.Windows.Forms.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="98e50-161">In addition to those described later, there are the <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck>, and <xref:System.Windows.Forms.TreeView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.TreeView> control.</span></span>

  - <span data-ttu-id="98e50-162">Kliknutí levým na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="98e50-162">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="98e50-163">Klikněte pravým tlačítkem na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>.</span><span class="sxs-lookup"><span data-stu-id="98e50-163">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="98e50-164">Dvakrát klikněte levým na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="98e50-164">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="98e50-165">Klikněte dvakrát na tlačítko: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="98e50-165">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

### <a name="painting-behavior-of-toggle-controls"></a><span data-ttu-id="98e50-166">Chování při malování pro přepínací ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="98e50-166">Painting behavior of toggle controls</span></span>

<span data-ttu-id="98e50-167">Přepínací ovládací prvky, jako jsou například ovládací prvky odvozené od třídy <xref:System.Windows.Forms.ButtonBase>, mají následující chování při rozkreslení v kombinaci s událostmi kliknutí myší:</span><span class="sxs-lookup"><span data-stu-id="98e50-167">Toggle controls, such as the controls deriving from the <xref:System.Windows.Forms.ButtonBase> class, have the following distinctive painting behavior in combination with mouse click events:</span></span>

1. <span data-ttu-id="98e50-168">Uživatel stiskne tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="98e50-168">The user presses the mouse button.</span></span>

2. <span data-ttu-id="98e50-169">Ovládací prvky vykreslí ve stisknutém stavu.</span><span class="sxs-lookup"><span data-stu-id="98e50-169">The control paints in the pressed state.</span></span>

3. <span data-ttu-id="98e50-170">Vyvolá se událost <xref:System.Windows.Forms.Control.MouseDown>.</span><span class="sxs-lookup"><span data-stu-id="98e50-170">The <xref:System.Windows.Forms.Control.MouseDown> event is raised.</span></span>

4. <span data-ttu-id="98e50-171">Uživatel uvolní tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="98e50-171">The user releases the mouse button.</span></span>

5. <span data-ttu-id="98e50-172">Ovládací prvky se vykreslí do vystouplého stavu.</span><span class="sxs-lookup"><span data-stu-id="98e50-172">The control paints in the raised state.</span></span>

6. <span data-ttu-id="98e50-173">Vyvolá se událost <xref:System.Windows.Forms.Control.Click>.</span><span class="sxs-lookup"><span data-stu-id="98e50-173">The <xref:System.Windows.Forms.Control.Click> event is raised.</span></span>

7. <span data-ttu-id="98e50-174">Vyvolá se událost <xref:System.Windows.Forms.Control.MouseClick>.</span><span class="sxs-lookup"><span data-stu-id="98e50-174">The <xref:System.Windows.Forms.Control.MouseClick> event is raised.</span></span>

8. <span data-ttu-id="98e50-175">Vyvolá se událost <xref:System.Windows.Forms.Control.MouseUp>.</span><span class="sxs-lookup"><span data-stu-id="98e50-175">The <xref:System.Windows.Forms.Control.MouseUp> event is raised.</span></span>

    > [!NOTE]
    > <span data-ttu-id="98e50-176">Pokud uživatel přesune ukazatel myši na ovládací prvek přepínacího tlačítka, když je stisknuto tlačítko myši (například přesunutím ukazatele myši nad ovládací prvek <xref:System.Windows.Forms.Button>, když je spuštěný), přepínací ovládací prvek se vykreslí do vystouplého stavu a dojde k pouze události <xref:System.Windows.Forms.Control.MouseUp>.</span><span class="sxs-lookup"><span data-stu-id="98e50-176">If the user moves the pointer out of the toggle control while the mouse button is down (such as moving the mouse off the <xref:System.Windows.Forms.Button> control while it is pressed), the toggle control will paint in the raised state and only the <xref:System.Windows.Forms.Control.MouseUp> event occurs.</span></span> <span data-ttu-id="98e50-177">V této situaci se neobjeví události <xref:System.Windows.Forms.Control.Click> nebo <xref:System.Windows.Forms.Control.MouseClick>.</span><span class="sxs-lookup"><span data-stu-id="98e50-177">The <xref:System.Windows.Forms.Control.Click> or <xref:System.Windows.Forms.Control.MouseClick> events will not occur in this situation.</span></span>

## <a name="see-also"></a><span data-ttu-id="98e50-178">Viz také:</span><span class="sxs-lookup"><span data-stu-id="98e50-178">See also</span></span>

- [<span data-ttu-id="98e50-179">Vstup z myši v aplikaci Windows Forms</span><span class="sxs-lookup"><span data-stu-id="98e50-179">Mouse Input in a Windows Forms Application</span></span>](mouse-input-in-a-windows-forms-application.md)
