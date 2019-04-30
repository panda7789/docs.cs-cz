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
ms.openlocfilehash: 671e37c7d6dc40046d6d717d7785b03b6b545c7e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61800710"
---
# <a name="mouse-events-in-windows-forms"></a><span data-ttu-id="f336a-102">Události myši ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f336a-102">Mouse Events in Windows Forms</span></span>

<span data-ttu-id="f336a-103">Při zpracování vstup z myši obvykle chtít znát umístění myši ukazatele a stav tlačítka myši.</span><span class="sxs-lookup"><span data-stu-id="f336a-103">When you handle mouse input, you usually want to know the location of the mouse pointer and the state of the mouse buttons.</span></span> <span data-ttu-id="f336a-104">Toto téma obsahuje podrobné informace o tom, jak získat tyto informace z událostí myši a vysvětluje, pořadí, ve které kliknutí myší jsou vyvolány události v ovládacích prvcích Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f336a-104">This topic provides details on how to get this information from mouse events, and explains the order in which mouse click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="f336a-105">Seznam a popis všech událostí myši najdete v tématu [jak funguje myši vstup ve Windows Forms](how-mouse-input-works-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="f336a-105">For a list and description of all of the mouse events, see [How Mouse Input Works in Windows Forms](how-mouse-input-works-in-windows-forms.md).</span></span>  <span data-ttu-id="f336a-106">Viz také [Přehled obslužných rutin událostí (Windows Forms)](event-handlers-overview-windows-forms.md) a [Přehled událostí (Windows Forms)](events-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="f336a-106">Also see [Event Handlers Overview (Windows Forms)](event-handlers-overview-windows-forms.md) and [Events Overview (Windows Forms)](events-overview-windows-forms.md).</span></span>

## <a name="mouse-information"></a><span data-ttu-id="f336a-107">Informace o myši</span><span class="sxs-lookup"><span data-stu-id="f336a-107">Mouse Information</span></span>

<span data-ttu-id="f336a-108">A <xref:System.Windows.Forms.MouseEventArgs> posílá obslužné rutiny událostí myši týkající se sledování pohybu myši a kliknutím na tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="f336a-108">A <xref:System.Windows.Forms.MouseEventArgs> is sent to the handlers of mouse events related to clicking a mouse button and tracking mouse movements.</span></span> <span data-ttu-id="f336a-109"><xref:System.Windows.Forms.MouseEventArgs> poskytuje informace o aktuálním stavu myši, včetně umístění ukazatele myši v souřadnicích klienta, které jsou stisknutí tlačítka myši, a určuje, zda se posunul kolečko myši.</span><span class="sxs-lookup"><span data-stu-id="f336a-109"><xref:System.Windows.Forms.MouseEventArgs> provides information about the current state of the mouse, including the location of the mouse pointer in client coordinates, which mouse buttons are pressed, and whether the mouse wheel has scrolled.</span></span> <span data-ttu-id="f336a-110">Několik událostí myši, jako jsou ty, které jednoduše upozornění při umístění ukazatele myši má zadaný nebo ponechat hranice ovládacího prvku, odeslání <xref:System.EventArgs> obslužné rutiny události s žádné další informace.</span><span class="sxs-lookup"><span data-stu-id="f336a-110">Several mouse events, such as those that simply notify when the mouse pointer has entered or left the bounds of a control, send an <xref:System.EventArgs> to the event handler with no further information.</span></span>

<span data-ttu-id="f336a-111">Pokud chcete zjistit aktuální stav tlačítka myši nebo na umístění ukazatele myši a chcete se vyhnout zpracování události myši, můžete použít také <xref:System.Windows.Forms.Control.MouseButtons%2A> a <xref:System.Windows.Forms.Control.MousePosition%2A> vlastnosti <xref:System.Windows.Forms.Control> třídy.</span><span class="sxs-lookup"><span data-stu-id="f336a-111">If you want to know the current state of the mouse buttons or the location of the mouse pointer, and you want to avoid handling a mouse event, you can also use the <xref:System.Windows.Forms.Control.MouseButtons%2A> and <xref:System.Windows.Forms.Control.MousePosition%2A> properties of the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="f336a-112"><xref:System.Windows.Forms.Control.MouseButtons%2A> Vrátí informace o tom, které jsou aktuálně stisknutí tlačítka myši.</span><span class="sxs-lookup"><span data-stu-id="f336a-112"><xref:System.Windows.Forms.Control.MouseButtons%2A> returns information about which mouse buttons are currently pressed.</span></span> <span data-ttu-id="f336a-113"><xref:System.Windows.Forms.Control.MousePosition%2A> Vrací souřadnice obrazovky ukazatele myši a je ekvivalentní hodnotě vrácené <xref:System.Windows.Forms.Cursor.Position%2A>.</span><span class="sxs-lookup"><span data-stu-id="f336a-113">The <xref:System.Windows.Forms.Control.MousePosition%2A> returns the screen coordinates of the mouse pointer and is equivalent to the value returned by <xref:System.Windows.Forms.Cursor.Position%2A>.</span></span>

## <a name="converting-between-screen-and-client-coordinates"></a><span data-ttu-id="f336a-114">Převod mezi obrazovky a klient koordinuje</span><span class="sxs-lookup"><span data-stu-id="f336a-114">Converting Between Screen and Client Coordinates</span></span>

<span data-ttu-id="f336a-115">Protože se některé informace o umístění myši v souřadnicích klienta a některé jsou v souřadnicovém systému obrazovky, budete muset změnit bod v jednom systému souřadnice.</span><span class="sxs-lookup"><span data-stu-id="f336a-115">Because some mouse location information is in client coordinates and some is in screen coordinates, you may need to convert a point from one coordinate system to the other.</span></span> <span data-ttu-id="f336a-116">Můžete to provést jednoduše pomocí <xref:System.Windows.Forms.Control.PointToClient%2A> a <xref:System.Windows.Forms.Control.PointToScreen%2A> metody, které jsou k dispozici na <xref:System.Windows.Forms.Control> třídy.</span><span class="sxs-lookup"><span data-stu-id="f336a-116">You can do this easily by using the <xref:System.Windows.Forms.Control.PointToClient%2A> and <xref:System.Windows.Forms.Control.PointToScreen%2A> methods available on the <xref:System.Windows.Forms.Control> class.</span></span>

## <a name="standard-click-event-behavior"></a><span data-ttu-id="f336a-117">Standardní chování události klikněte na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="f336a-117">Standard Click Event Behavior</span></span>

<span data-ttu-id="f336a-118">Pokud chcete zpracovávat události ve správném pořadí kliknutí myší, je potřeba vědět pořadí, ve které kliknutím jsou vyvolány události v ovládacích prvcích Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f336a-118">If you want to handle mouse click events in the proper order, you need to know the order in which click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="f336a-119">Po stisknutí tlačítka myši a vydány (bez ohledu na které tlačítko myši), v následujícím seznamu pro jednotlivé ovládací prvky, klikněte na všechny formuláře Windows, které vyvolávají události ve stejném pořadí.</span><span class="sxs-lookup"><span data-stu-id="f336a-119">All Windows Forms controls raise click events in the same order when a mouse button is pressed and released (regardless of which mouse button), except where noted in the following list for individual controls.</span></span> <span data-ttu-id="f336a-120">Následující seznam zobrazuje pořadí událostí vyvolaných pro klikněte na jediné tlačítko myši:</span><span class="sxs-lookup"><span data-stu-id="f336a-120">The following list shows the order of events raised for a single mouse-button click:</span></span>

1. <span data-ttu-id="f336a-121"><xref:System.Windows.Forms.Control.MouseDown> události.</span><span class="sxs-lookup"><span data-stu-id="f336a-121"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

2. <span data-ttu-id="f336a-122"><xref:System.Windows.Forms.Control.Click> události.</span><span class="sxs-lookup"><span data-stu-id="f336a-122"><xref:System.Windows.Forms.Control.Click> event.</span></span>

3. <span data-ttu-id="f336a-123"><xref:System.Windows.Forms.Control.MouseClick> události.</span><span class="sxs-lookup"><span data-stu-id="f336a-123"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>

4. <span data-ttu-id="f336a-124"><xref:System.Windows.Forms.Control.MouseUp> události.</span><span class="sxs-lookup"><span data-stu-id="f336a-124"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

<span data-ttu-id="f336a-125">Toto je pořadí událostí vyvolaných pro tlačítko myši dvojité kliknutí:</span><span class="sxs-lookup"><span data-stu-id="f336a-125">Following is the order of events raised for a double mouse-button click:</span></span>

1. <span data-ttu-id="f336a-126"><xref:System.Windows.Forms.Control.MouseDown> události.</span><span class="sxs-lookup"><span data-stu-id="f336a-126"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

2. <span data-ttu-id="f336a-127"><xref:System.Windows.Forms.Control.Click> události.</span><span class="sxs-lookup"><span data-stu-id="f336a-127"><xref:System.Windows.Forms.Control.Click> event.</span></span>

3. <span data-ttu-id="f336a-128"><xref:System.Windows.Forms.Control.MouseClick> události.</span><span class="sxs-lookup"><span data-stu-id="f336a-128"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>

4. <span data-ttu-id="f336a-129"><xref:System.Windows.Forms.Control.MouseUp> události.</span><span class="sxs-lookup"><span data-stu-id="f336a-129"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

5. <span data-ttu-id="f336a-130"><xref:System.Windows.Forms.Control.MouseDown> události.</span><span class="sxs-lookup"><span data-stu-id="f336a-130"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

6. <span data-ttu-id="f336a-131"><xref:System.Windows.Forms.Control.DoubleClick> události.</span><span class="sxs-lookup"><span data-stu-id="f336a-131"><xref:System.Windows.Forms.Control.DoubleClick> event.</span></span> <span data-ttu-id="f336a-132">(To se může lišit v závislosti na tom, zda má ovládací prvek dotyčný <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> na sadu bitů stylu `true`.</span><span class="sxs-lookup"><span data-stu-id="f336a-132">(This can vary, depending on whether the control in question has the <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> style bit set to `true`.</span></span> <span data-ttu-id="f336a-133">Další informace o tom, jak nastavit <xref:System.Windows.Forms.ControlStyles> bit, najdete v článku <xref:System.Windows.Forms.Control.SetStyle%2A> metoda.)</span><span class="sxs-lookup"><span data-stu-id="f336a-133">For more information about how to set a <xref:System.Windows.Forms.ControlStyles> bit, see the <xref:System.Windows.Forms.Control.SetStyle%2A> method.)</span></span>

7. <span data-ttu-id="f336a-134"><xref:System.Windows.Forms.Control.MouseDoubleClick> události.</span><span class="sxs-lookup"><span data-stu-id="f336a-134"><xref:System.Windows.Forms.Control.MouseDoubleClick> event.</span></span>

8. <span data-ttu-id="f336a-135"><xref:System.Windows.Forms.Control.MouseUp> události.</span><span class="sxs-lookup"><span data-stu-id="f336a-135"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

<span data-ttu-id="f336a-136">Příklad kódu, který ukazuje pořadí myši klikněte na události, najdete v článku [jak: Zpracování uživatelského vstupu událostí ve Windows Forms ovládací prvky](how-to-handle-user-input-events-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="f336a-136">For a code example that demonstrates the order of the mouse click events, see [How to: Handle User Input Events in Windows Forms Controls](how-to-handle-user-input-events-in-windows-forms-controls.md).</span></span>

### <a name="individual-controls"></a><span data-ttu-id="f336a-137">Jednotlivých ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="f336a-137">Individual Controls</span></span>

<span data-ttu-id="f336a-138">Následující ovládací prvky není v souladu s Standardní zkratky myši klikněte na tlačítko chování události:</span><span class="sxs-lookup"><span data-stu-id="f336a-138">The following controls do not conform to the standard mouse click event behavior:</span></span>

- <span data-ttu-id="f336a-139"><xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.ComboBox>, a <xref:System.Windows.Forms.RadioButton> ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="f336a-139"><xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.ComboBox>, and <xref:System.Windows.Forms.RadioButton> controls</span></span>

  > [!NOTE]
  > <span data-ttu-id="f336a-140">Pro <xref:System.Windows.Forms.ComboBox> vyvolá chování události, které jsou podrobně popsané ovládací prvek, pokud uživatel klepne na pole, tlačítko, nebo na položku v seznamu.</span><span class="sxs-lookup"><span data-stu-id="f336a-140">For the <xref:System.Windows.Forms.ComboBox> control, the event behavior detailed later occurs if the user clicks on the edit field, the button, or on an item within the list.</span></span>

  - <span data-ttu-id="f336a-141">Levé tlačítko myši: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="f336a-141">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="f336a-142">Klikněte pravým tlačítkem myši na: Žádné události kliknutí na vyvolána</span><span class="sxs-lookup"><span data-stu-id="f336a-142">Right click: No click events raised</span></span>

  - <span data-ttu-id="f336a-143">Dvakrát klikněte na levý: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="f336a-143">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="f336a-144">Vpravo klikněte dvakrát na: Žádné události kliknutí na vyvolána</span><span class="sxs-lookup"><span data-stu-id="f336a-144">Right double-click: No click events raised</span></span>

- <span data-ttu-id="f336a-145"><xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox>, a <xref:System.Windows.Forms.CheckedListBox> ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="f336a-145"><xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox>, and <xref:System.Windows.Forms.CheckedListBox> controls</span></span>

  > [!NOTE]
  > <span data-ttu-id="f336a-146">Chování události, které jsou podrobně popsané nastane, pokud uživatel klikne na tlačítko kdekoli v rámci těchto ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="f336a-146">The event behavior detailed later occurs when the user clicks anywhere within these controls.</span></span>

  - <span data-ttu-id="f336a-147">Levé tlačítko myši: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="f336a-147">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="f336a-148">Klikněte pravým tlačítkem myši na: Žádné události kliknutí na vyvolána</span><span class="sxs-lookup"><span data-stu-id="f336a-148">Right click: No click events raised</span></span>

  - <span data-ttu-id="f336a-149">Dvakrát klikněte na levý: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="f336a-149">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="f336a-150">Vpravo klikněte dvakrát na: Žádné události kliknutí na vyvolána</span><span class="sxs-lookup"><span data-stu-id="f336a-150">Right double-click: No click events raised</span></span>

- <span data-ttu-id="f336a-151"><xref:System.Windows.Forms.ListView> Ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="f336a-151"><xref:System.Windows.Forms.ListView> control</span></span>

  > [!NOTE]
  > <span data-ttu-id="f336a-152">Chování události, které jsou podrobně popsané dochází, pouze když uživatel klikne na položky v <xref:System.Windows.Forms.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f336a-152">The event behavior detailed later occurs only when the user clicks on the items in the <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="f336a-153">Žádné události se generují pro kliknutí na ovládací prvek někde jinde.</span><span class="sxs-lookup"><span data-stu-id="f336a-153">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="f336a-154">Kromě události je popsáno dále, jsou k dispozici <xref:System.Windows.Forms.ListView.BeforeLabelEdit> a <xref:System.Windows.Forms.ListView.AfterLabelEdit> události, které mohou být vás zajímají, pokud chcete použít ověřování pomocí <xref:System.Windows.Forms.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f336a-154">In addition to the events described later, there are the <xref:System.Windows.Forms.ListView.BeforeLabelEdit> and <xref:System.Windows.Forms.ListView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.ListView> control.</span></span>

  - <span data-ttu-id="f336a-155">Levé tlačítko myši: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="f336a-155">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="f336a-156">Klikněte pravým tlačítkem myši na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="f336a-156">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="f336a-157">Dvakrát klikněte na levý: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="f336a-157">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="f336a-158">Vpravo klikněte dvakrát na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="f336a-158">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

- <span data-ttu-id="f336a-159"><xref:System.Windows.Forms.TreeView> Ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="f336a-159"><xref:System.Windows.Forms.TreeView> control</span></span>

  > [!NOTE]
  > <span data-ttu-id="f336a-160">Chování události, které jsou podrobně popsané dochází, pouze pokud uživatel klikne na samotných položkách nebo napravo od položky <xref:System.Windows.Forms.TreeView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f336a-160">The event behavior detailed later occurs only when the user clicks on the items themselves or to the right of the items in the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="f336a-161">Žádné události se generují pro kliknutí na ovládací prvek někde jinde.</span><span class="sxs-lookup"><span data-stu-id="f336a-161">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="f336a-162">Kromě těch popsaných dále, jsou k dispozici <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck>, a <xref:System.Windows.Forms.TreeView.AfterLabelEdit> události, které mohou být vás zajímají, pokud chcete použít ověřování pomocí <xref:System.Windows.Forms.TreeView> ovládacího prvku .</span><span class="sxs-lookup"><span data-stu-id="f336a-162">In addition to those described later, there are the <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck>, and <xref:System.Windows.Forms.TreeView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.TreeView> control.</span></span>

  - <span data-ttu-id="f336a-163">Levé tlačítko myši: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="f336a-163">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="f336a-164">Klikněte pravým tlačítkem myši na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="f336a-164">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="f336a-165">Dvakrát klikněte na levý: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="f336a-165">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="f336a-166">Vpravo klikněte dvakrát na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="f336a-166">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

### <a name="painting-behavior-of-toggle-controls"></a><span data-ttu-id="f336a-167">Malování chování ovládacích prvků přepínání</span><span class="sxs-lookup"><span data-stu-id="f336a-167">Painting Behavior of Toggle Controls</span></span>

<span data-ttu-id="f336a-168">Přepnout ovládací prvky, jako je například ovládací prvky odvozený od <xref:System.Windows.Forms.ButtonBase> třídy, mají následující zvláštní Malování chování v kombinaci s myši klikněte na tlačítko události:</span><span class="sxs-lookup"><span data-stu-id="f336a-168">Toggle controls, such as the controls deriving from the <xref:System.Windows.Forms.ButtonBase> class, have the following distinctive painting behavior in combination with mouse click events:</span></span>

1. <span data-ttu-id="f336a-169">Uživatel stiskne tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="f336a-169">The user presses the mouse button.</span></span>

2. <span data-ttu-id="f336a-170">Při stisknutí stavu Vymaluje ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="f336a-170">The control paints in the pressed state.</span></span>

3. <span data-ttu-id="f336a-171"><xref:System.Windows.Forms.Control.MouseDown> Událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="f336a-171">The <xref:System.Windows.Forms.Control.MouseDown> event is raised.</span></span>

4. <span data-ttu-id="f336a-172">Uživatel uvolní tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="f336a-172">The user releases the mouse button.</span></span>

5. <span data-ttu-id="f336a-173">Vymaluje ovládací prvek v vyvolanou stavu.</span><span class="sxs-lookup"><span data-stu-id="f336a-173">The control paints in the raised state.</span></span>

6. <span data-ttu-id="f336a-174"><xref:System.Windows.Forms.Control.Click> Událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="f336a-174">The <xref:System.Windows.Forms.Control.Click> event is raised.</span></span>

7. <span data-ttu-id="f336a-175"><xref:System.Windows.Forms.Control.MouseClick> Událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="f336a-175">The <xref:System.Windows.Forms.Control.MouseClick> event is raised.</span></span>

8. <span data-ttu-id="f336a-176"><xref:System.Windows.Forms.Control.MouseUp> Událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="f336a-176">The <xref:System.Windows.Forms.Control.MouseUp> event is raised.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="f336a-177">Pokud se uživatel přesune ukazatel myši mimo ovládací prvek přepínací tlačítko, zatímco je stisknuto levé tlačítko myši (jako je například hýbání myší <xref:System.Windows.Forms.Button> ovládací prvek je stisknutí), bude malovat vyvolanou ovládacím prvku přepínací tlačítko stavu a pouze <xref:System.Windows.Forms.Control.MouseUp> dojde k události.</span><span class="sxs-lookup"><span data-stu-id="f336a-177">If the user moves the pointer out of the toggle control while the mouse button is down (such as moving the mouse off the <xref:System.Windows.Forms.Button> control while it is pressed), the toggle control will paint in the raised state and only the <xref:System.Windows.Forms.Control.MouseUp> event occurs.</span></span> <span data-ttu-id="f336a-178"><xref:System.Windows.Forms.Control.Click> Nebo <xref:System.Windows.Forms.Control.MouseClick> nebude v této situaci dojde k událostem.</span><span class="sxs-lookup"><span data-stu-id="f336a-178">The <xref:System.Windows.Forms.Control.Click> or <xref:System.Windows.Forms.Control.MouseClick> events will not occur in this situation.</span></span>

## <a name="see-also"></a><span data-ttu-id="f336a-179">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f336a-179">See also</span></span>

- [<span data-ttu-id="f336a-180">Vstup z myši v aplikaci Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f336a-180">Mouse Input in a Windows Forms Application</span></span>](mouse-input-in-a-windows-forms-application.md)
