---
title: Události myši
description: Naučte se, jak získat polohu myši z událostí myši a pochopit pořadí, ve kterém jsou události kliknutí myší vyvolány v ovládacích prvcích model Windows Forms.
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
ms.openlocfilehash: 640448109961ea5fdf3600ef9e72d7d10e8c9e49
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174377"
---
# <a name="mouse-events-in-windows-forms"></a><span data-ttu-id="f3dd2-103">Události myši ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f3dd2-103">Mouse Events in Windows Forms</span></span>

<span data-ttu-id="f3dd2-104">Při zpracování vstupu myši obvykle chcete znát polohu ukazatele myši a stavu tlačítek myši.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-104">When you handle mouse input, you usually want to know the location of the mouse pointer and the state of the mouse buttons.</span></span> <span data-ttu-id="f3dd2-105">Toto téma obsahuje podrobné informace o tom, jak tyto informace z událostí myši získat a vysvětluje pořadí, ve kterém jsou události kliknutí myší vyvolány v ovládacích prvcích model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-105">This topic provides details on how to get this information from mouse events, and explains the order in which mouse click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="f3dd2-106">Seznam a popis všech událostí myši najdete [v tématu Jak funguje vstup myši v model Windows Forms](how-mouse-input-works-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="f3dd2-106">For a list and description of all of the mouse events, see [How Mouse Input Works in Windows Forms](how-mouse-input-works-in-windows-forms.md).</span></span>  <span data-ttu-id="f3dd2-107">Viz také přehled [obslužných rutin událostí (model Windows Forms)](event-handlers-overview-windows-forms.md) a [přehled událostí (model Windows Forms)](events-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="f3dd2-107">Also see [Event Handlers Overview (Windows Forms)](event-handlers-overview-windows-forms.md) and [Events Overview (Windows Forms)](events-overview-windows-forms.md).</span></span>

## <a name="mouse-information"></a><span data-ttu-id="f3dd2-108">Informace o myši</span><span class="sxs-lookup"><span data-stu-id="f3dd2-108">Mouse Information</span></span>

<span data-ttu-id="f3dd2-109">A <xref:System.Windows.Forms.MouseEventArgs> se pošle obslužným rutinám událostí myši souvisejících s kliknutím na tlačítko myši a sledováním pohybu myši.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-109">A <xref:System.Windows.Forms.MouseEventArgs> is sent to the handlers of mouse events related to clicking a mouse button and tracking mouse movements.</span></span> <span data-ttu-id="f3dd2-110"><xref:System.Windows.Forms.MouseEventArgs>obsahuje informace o aktuálním stavu myši, včetně umístění ukazatele myši v souřadnicích klienta, stisknutých tlačítek myši a o tom, zda bylo kolečko myši posunuto.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-110"><xref:System.Windows.Forms.MouseEventArgs> provides information about the current state of the mouse, including the location of the mouse pointer in client coordinates, which mouse buttons are pressed, and whether the mouse wheel has scrolled.</span></span> <span data-ttu-id="f3dd2-111">Několik událostí myši, jako jsou například ty, které jednoduše upozorňují, když ukazatel myši zadáte nebo opustí hranice ovládacího prvku, pošle <xref:System.EventArgs> obslužné rutině události žádné další informace.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-111">Several mouse events, such as those that simply notify when the mouse pointer has entered or left the bounds of a control, send an <xref:System.EventArgs> to the event handler with no further information.</span></span>

<span data-ttu-id="f3dd2-112">Chcete-li znát aktuální stav tlačítek myši nebo umístění ukazatele myši a chcete se vyhnout manipulaci s událostí myši, můžete také použít <xref:System.Windows.Forms.Control.MouseButtons%2A> <xref:System.Windows.Forms.Control.MousePosition%2A> vlastnosti a <xref:System.Windows.Forms.Control> třídy.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-112">If you want to know the current state of the mouse buttons or the location of the mouse pointer, and you want to avoid handling a mouse event, you can also use the <xref:System.Windows.Forms.Control.MouseButtons%2A> and <xref:System.Windows.Forms.Control.MousePosition%2A> properties of the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="f3dd2-113"><xref:System.Windows.Forms.Control.MouseButtons%2A>Vrátí informace o tom, která tlačítka myši jsou právě stisknutá.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-113"><xref:System.Windows.Forms.Control.MouseButtons%2A> returns information about which mouse buttons are currently pressed.</span></span> <span data-ttu-id="f3dd2-114"><xref:System.Windows.Forms.Control.MousePosition%2A>Vrátí souřadnice obrazovky ukazatele myši a je ekvivalentní hodnotě vrácené hodnotou <xref:System.Windows.Forms.Cursor.Position%2A> .</span><span class="sxs-lookup"><span data-stu-id="f3dd2-114">The <xref:System.Windows.Forms.Control.MousePosition%2A> returns the screen coordinates of the mouse pointer and is equivalent to the value returned by <xref:System.Windows.Forms.Cursor.Position%2A>.</span></span>

## <a name="converting-between-screen-and-client-coordinates"></a><span data-ttu-id="f3dd2-115">Převod mezi souřadnicemi obrazovky a klienta</span><span class="sxs-lookup"><span data-stu-id="f3dd2-115">Converting Between Screen and Client Coordinates</span></span>

<span data-ttu-id="f3dd2-116">Vzhledem k tomu, že některé informace o umístění myši jsou v souřadnicích klienta a některé jsou v souřadnicích obrazovky, možná budete muset převést bod z jednoho systému souřadnic na druhý.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-116">Because some mouse location information is in client coordinates and some is in screen coordinates, you may need to convert a point from one coordinate system to the other.</span></span> <span data-ttu-id="f3dd2-117">To lze provést snadno pomocí <xref:System.Windows.Forms.Control.PointToClient%2A> <xref:System.Windows.Forms.Control.PointToScreen%2A> metod a dostupných ve <xref:System.Windows.Forms.Control> třídě.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-117">You can do this easily by using the <xref:System.Windows.Forms.Control.PointToClient%2A> and <xref:System.Windows.Forms.Control.PointToScreen%2A> methods available on the <xref:System.Windows.Forms.Control> class.</span></span>

## <a name="standard-click-event-behavior"></a><span data-ttu-id="f3dd2-118">Standardní chování události kliknutí</span><span class="sxs-lookup"><span data-stu-id="f3dd2-118">Standard Click Event Behavior</span></span>

<span data-ttu-id="f3dd2-119">Pokud chcete zpracovávat události kliknutí myší ve správném pořadí, musíte znát pořadí, ve kterém jsou události kliknutí vyvolány v ovládacích prvcích model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-119">If you want to handle mouse click events in the proper order, you need to know the order in which click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="f3dd2-120">Všechny model Windows Forms ovládací prvky vyvolávají události Click ve stejném pořadí při stisknutí a uvolnění tlačítka myši (bez ohledu na to, které tlačítko myši), s výjimkou těch, které jsou uvedeny v následujícím seznamu pro jednotlivé ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-120">All Windows Forms controls raise click events in the same order when a mouse button is pressed and released (regardless of which mouse button), except where noted in the following list for individual controls.</span></span> <span data-ttu-id="f3dd2-121">Následující seznam zobrazuje pořadí událostí vyvolaných jedním kliknutím myši na tlačítko:</span><span class="sxs-lookup"><span data-stu-id="f3dd2-121">The following list shows the order of events raised for a single mouse-button click:</span></span>

1. <span data-ttu-id="f3dd2-122"><xref:System.Windows.Forms.Control.MouseDown>událostí.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-122"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

2. <span data-ttu-id="f3dd2-123"><xref:System.Windows.Forms.Control.Click>událostí.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-123"><xref:System.Windows.Forms.Control.Click> event.</span></span>

3. <span data-ttu-id="f3dd2-124"><xref:System.Windows.Forms.Control.MouseClick>událostí.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-124"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>

4. <span data-ttu-id="f3dd2-125"><xref:System.Windows.Forms.Control.MouseUp>událostí.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-125"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

<span data-ttu-id="f3dd2-126">Následuje pořadí událostí vyvolaných pro dvojité kliknutí myší:</span><span class="sxs-lookup"><span data-stu-id="f3dd2-126">The following is the order of events raised for a double mouse-button click:</span></span>

1. <span data-ttu-id="f3dd2-127"><xref:System.Windows.Forms.Control.MouseDown>událostí.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-127"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

2. <span data-ttu-id="f3dd2-128"><xref:System.Windows.Forms.Control.Click>událostí.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-128"><xref:System.Windows.Forms.Control.Click> event.</span></span>

3. <span data-ttu-id="f3dd2-129"><xref:System.Windows.Forms.Control.MouseClick>událostí.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-129"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>

4. <span data-ttu-id="f3dd2-130"><xref:System.Windows.Forms.Control.MouseUp>událostí.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-130"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

5. <span data-ttu-id="f3dd2-131"><xref:System.Windows.Forms.Control.MouseDown>událostí.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-131"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

6. <span data-ttu-id="f3dd2-132"><xref:System.Windows.Forms.Control.DoubleClick>událostí.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-132"><xref:System.Windows.Forms.Control.DoubleClick> event.</span></span> <span data-ttu-id="f3dd2-133">(To se může lišit v závislosti na tom, zda má ovládací prvek <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> nastaven bit stylu na `true` .</span><span class="sxs-lookup"><span data-stu-id="f3dd2-133">(This can vary, depending on whether the control in question has the <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> style bit set to `true`.</span></span> <span data-ttu-id="f3dd2-134">Další informace o nastavení <xref:System.Windows.Forms.ControlStyles> bitu naleznete v <xref:System.Windows.Forms.Control.SetStyle%2A> metodě.)</span><span class="sxs-lookup"><span data-stu-id="f3dd2-134">For more information about how to set a <xref:System.Windows.Forms.ControlStyles> bit, see the <xref:System.Windows.Forms.Control.SetStyle%2A> method.)</span></span>

7. <span data-ttu-id="f3dd2-135"><xref:System.Windows.Forms.Control.MouseDoubleClick>událostí.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-135"><xref:System.Windows.Forms.Control.MouseDoubleClick> event.</span></span>

8. <span data-ttu-id="f3dd2-136"><xref:System.Windows.Forms.Control.MouseUp>událostí.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-136"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

<span data-ttu-id="f3dd2-137">Příklad kódu, který ukazuje pořadí událostí kliknutí myší, naleznete v tématu [How to: Handler User Input events in model Windows Forms Controls](how-to-handle-user-input-events-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="f3dd2-137">For a code example that demonstrates the order of the mouse click events, see [How to: Handle User Input Events in Windows Forms Controls](how-to-handle-user-input-events-in-windows-forms-controls.md).</span></span>

### <a name="individual-controls"></a><span data-ttu-id="f3dd2-138">Jednotlivé ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="f3dd2-138">Individual Controls</span></span>

<span data-ttu-id="f3dd2-139">Následující ovládací prvky neodpovídají standardnímu chování události kliknutí myší:</span><span class="sxs-lookup"><span data-stu-id="f3dd2-139">The following controls do not conform to the standard mouse click event behavior:</span></span>

- <xref:System.Windows.Forms.Button>
- <xref:System.Windows.Forms.CheckBox>
- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.RadioButton>

  > [!NOTE]
  > <span data-ttu-id="f3dd2-140">V případě <xref:System.Windows.Forms.ComboBox> ovládacího prvku se k chování události podrobná později dojde, když uživatel klikne na pole upravit, tlačítko nebo na položku v seznamu.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-140">For the <xref:System.Windows.Forms.ComboBox> control, the event behavior detailed later occurs if the user clicks on the edit field, the button, or on an item within the list.</span></span>

  - <span data-ttu-id="f3dd2-141">Klikněte levým na: <xref:System.Windows.Forms.Control.Click> ,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="f3dd2-141">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="f3dd2-142">Kliknutí pravým tlačítkem: neaktivována událost kliknutí na události</span><span class="sxs-lookup"><span data-stu-id="f3dd2-142">Right click: No click events raised</span></span>

  - <span data-ttu-id="f3dd2-143">Dvakrát klikněte levým na: <xref:System.Windows.Forms.Control.Click> , <xref:System.Windows.Forms.Control.MouseClick> ; <xref:System.Windows.Forms.Control.Click> ,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="f3dd2-143">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="f3dd2-144">Dvakrát klikněte pravým tlačítkem myši na událost žádné události kliknutí.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-144">Right double-click: No click events raised</span></span>

- <span data-ttu-id="f3dd2-145"><xref:System.Windows.Forms.TextBox><xref:System.Windows.Forms.RichTextBox>ovládací prvky,,, <xref:System.Windows.Forms.ListBox> <xref:System.Windows.Forms.MaskedTextBox> a <xref:System.Windows.Forms.CheckedListBox></span><span class="sxs-lookup"><span data-stu-id="f3dd2-145"><xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox>, and <xref:System.Windows.Forms.CheckedListBox> controls</span></span>

  > [!NOTE]
  > <span data-ttu-id="f3dd2-146">K chování události později dojde, když uživatel klikne kamkoli v rámci těchto ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-146">The event behavior detailed later occurs when the user clicks anywhere within these controls.</span></span>

  - <span data-ttu-id="f3dd2-147">Klikněte levým na: <xref:System.Windows.Forms.Control.Click> ,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="f3dd2-147">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="f3dd2-148">Kliknutí pravým tlačítkem: neaktivována událost kliknutí na události</span><span class="sxs-lookup"><span data-stu-id="f3dd2-148">Right click: No click events raised</span></span>

  - <span data-ttu-id="f3dd2-149">Dvakrát klikněte levým na: <xref:System.Windows.Forms.Control.Click> , <xref:System.Windows.Forms.Control.MouseClick> , <xref:System.Windows.Forms.Control.DoubleClick> ,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="f3dd2-149">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="f3dd2-150">Dvakrát klikněte pravým tlačítkem myši na událost žádné události kliknutí.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-150">Right double-click: No click events raised</span></span>

- <span data-ttu-id="f3dd2-151"><xref:System.Windows.Forms.ListView>nad</span><span class="sxs-lookup"><span data-stu-id="f3dd2-151"><xref:System.Windows.Forms.ListView> control</span></span>

  > [!NOTE]
  > <span data-ttu-id="f3dd2-152">K chování události později dochází pouze v případě, že uživatel klikne na položky v <xref:System.Windows.Forms.ListView> ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-152">The event behavior detailed later occurs only when the user clicks on the items in the <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="f3dd2-153">Pro kliknutí jinde v ovládacím prvku nejsou vyvolány žádné události.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-153">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="f3dd2-154">Kromě událostí popsaných dále jsou k dispozici <xref:System.Windows.Forms.ListView.BeforeLabelEdit> události a <xref:System.Windows.Forms.ListView.AfterLabelEdit> , které vás mohou zajímat, pokud chcete použít ověřování s <xref:System.Windows.Forms.ListView> ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-154">In addition to the events described later, there are the <xref:System.Windows.Forms.ListView.BeforeLabelEdit> and <xref:System.Windows.Forms.ListView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.ListView> control.</span></span>

  - <span data-ttu-id="f3dd2-155">Klikněte levým na: <xref:System.Windows.Forms.Control.Click> ,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="f3dd2-155">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="f3dd2-156">Klikněte pravým tlačítkem myši: <xref:System.Windows.Forms.Control.Click> ,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="f3dd2-156">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="f3dd2-157">Dvakrát klikněte levým na: <xref:System.Windows.Forms.Control.Click> , <xref:System.Windows.Forms.Control.MouseClick> ; <xref:System.Windows.Forms.Control.DoubleClick> ,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="f3dd2-157">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="f3dd2-158">Klikněte dvakrát na tlačítko: <xref:System.Windows.Forms.Control.Click> , <xref:System.Windows.Forms.Control.MouseClick> ; <xref:System.Windows.Forms.Control.DoubleClick> ,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="f3dd2-158">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

- <span data-ttu-id="f3dd2-159"><xref:System.Windows.Forms.TreeView>nad</span><span class="sxs-lookup"><span data-stu-id="f3dd2-159"><xref:System.Windows.Forms.TreeView> control</span></span>

  > [!NOTE]
  > <span data-ttu-id="f3dd2-160">K chování události později dochází pouze v případě, že uživatel klikne na samotné položky nebo napravo od položek v <xref:System.Windows.Forms.TreeView> ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-160">The event behavior detailed later occurs only when the user clicks on the items themselves or to the right of the items in the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="f3dd2-161">Pro kliknutí jinde v ovládacím prvku nejsou vyvolány žádné události.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-161">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="f3dd2-162">Kromě těch, které jsou popsány později, <xref:System.Windows.Forms.TreeView.BeforeCheck> existují <xref:System.Windows.Forms.TreeView.BeforeSelect> události,,, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit> <xref:System.Windows.Forms.TreeView.AfterSelect> , <xref:System.Windows.Forms.TreeView.AfterCheck> a <xref:System.Windows.Forms.TreeView.AfterLabelEdit> , které vás mohou zajímat, pokud chcete použít ověřování s <xref:System.Windows.Forms.TreeView> ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-162">In addition to those described later, there are the <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck>, and <xref:System.Windows.Forms.TreeView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.TreeView> control.</span></span>

  - <span data-ttu-id="f3dd2-163">Klikněte levým na: <xref:System.Windows.Forms.Control.Click> ,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="f3dd2-163">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="f3dd2-164">Klikněte pravým tlačítkem myši: <xref:System.Windows.Forms.Control.Click> ,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="f3dd2-164">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="f3dd2-165">Dvakrát klikněte levým na: <xref:System.Windows.Forms.Control.Click> , <xref:System.Windows.Forms.Control.MouseClick> ; <xref:System.Windows.Forms.Control.DoubleClick> ,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="f3dd2-165">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="f3dd2-166">Klikněte dvakrát na tlačítko: <xref:System.Windows.Forms.Control.Click> , <xref:System.Windows.Forms.Control.MouseClick> ; <xref:System.Windows.Forms.Control.DoubleClick> ,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="f3dd2-166">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

### <a name="painting-behavior-of-toggle-controls"></a><span data-ttu-id="f3dd2-167">Chování při malování pro přepínací ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="f3dd2-167">Painting behavior of toggle controls</span></span>

<span data-ttu-id="f3dd2-168">Přepínací ovládací prvky, jako jsou například ovládací prvky odvozené od <xref:System.Windows.Forms.ButtonBase> třídy, mají následující chování při malování v kombinaci s událostmi kliknutí myší:</span><span class="sxs-lookup"><span data-stu-id="f3dd2-168">Toggle controls, such as the controls deriving from the <xref:System.Windows.Forms.ButtonBase> class, have the following distinctive painting behavior in combination with mouse click events:</span></span>

1. <span data-ttu-id="f3dd2-169">Uživatel stiskne tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-169">The user presses the mouse button.</span></span>

2. <span data-ttu-id="f3dd2-170">Ovládací prvky vykreslí ve stisknutém stavu.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-170">The control paints in the pressed state.</span></span>

3. <span data-ttu-id="f3dd2-171"><xref:System.Windows.Forms.Control.MouseDown>Událost je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-171">The <xref:System.Windows.Forms.Control.MouseDown> event is raised.</span></span>

4. <span data-ttu-id="f3dd2-172">Uživatel uvolní tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-172">The user releases the mouse button.</span></span>

5. <span data-ttu-id="f3dd2-173">Ovládací prvky se vykreslí do vystouplého stavu.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-173">The control paints in the raised state.</span></span>

6. <span data-ttu-id="f3dd2-174"><xref:System.Windows.Forms.Control.Click>Událost je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-174">The <xref:System.Windows.Forms.Control.Click> event is raised.</span></span>

7. <span data-ttu-id="f3dd2-175"><xref:System.Windows.Forms.Control.MouseClick>Událost je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-175">The <xref:System.Windows.Forms.Control.MouseClick> event is raised.</span></span>

8. <span data-ttu-id="f3dd2-176"><xref:System.Windows.Forms.Control.MouseUp>Událost je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-176">The <xref:System.Windows.Forms.Control.MouseUp> event is raised.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f3dd2-177">Pokud uživatel přesune ukazatel myši na ovládací prvek přepínacího tlačítka, když je tlačítko myši vypnuté (například přesunutí myši <xref:System.Windows.Forms.Button> nad ovládací prvek během jeho stisknutí), ovládací prvek přepínacího tlačítka se vykreslí ve vystouplém stavu a <xref:System.Windows.Forms.Control.MouseUp> dojde k výskytu pouze události.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-177">If the user moves the pointer out of the toggle control while the mouse button is down (such as moving the mouse off the <xref:System.Windows.Forms.Button> control while it is pressed), the toggle control will paint in the raised state and only the <xref:System.Windows.Forms.Control.MouseUp> event occurs.</span></span> <span data-ttu-id="f3dd2-178"><xref:System.Windows.Forms.Control.Click>Události nebo <xref:System.Windows.Forms.Control.MouseClick> se v této situaci neobjeví.</span><span class="sxs-lookup"><span data-stu-id="f3dd2-178">The <xref:System.Windows.Forms.Control.Click> or <xref:System.Windows.Forms.Control.MouseClick> events will not occur in this situation.</span></span>

## <a name="see-also"></a><span data-ttu-id="f3dd2-179">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3dd2-179">See also</span></span>

- [<span data-ttu-id="f3dd2-180">Vstup z myši v aplikaci Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f3dd2-180">Mouse Input in a Windows Forms Application</span></span>](mouse-input-in-a-windows-forms-application.md)
