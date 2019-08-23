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
ms.openlocfilehash: 181d01f6e688b94876f77155bf598aba129e9fbf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949915"
---
# <a name="mouse-events-in-windows-forms"></a><span data-ttu-id="85abc-102">Události myši ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="85abc-102">Mouse Events in Windows Forms</span></span>

<span data-ttu-id="85abc-103">Při zpracování vstupu myši obvykle chcete znát polohu ukazatele myši a stavu tlačítek myši.</span><span class="sxs-lookup"><span data-stu-id="85abc-103">When you handle mouse input, you usually want to know the location of the mouse pointer and the state of the mouse buttons.</span></span> <span data-ttu-id="85abc-104">Toto téma obsahuje podrobné informace o tom, jak tyto informace z událostí myši získat a vysvětluje pořadí, ve kterém jsou události kliknutí myší vyvolány v ovládacích prvcích model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="85abc-104">This topic provides details on how to get this information from mouse events, and explains the order in which mouse click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="85abc-105">Seznam a popis všech událostí myši najdete [v tématu Jak funguje vstup myši v model Windows Forms](how-mouse-input-works-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="85abc-105">For a list and description of all of the mouse events, see [How Mouse Input Works in Windows Forms](how-mouse-input-works-in-windows-forms.md).</span></span>  <span data-ttu-id="85abc-106">Viz také přehled [obslužných rutin událostí (model Windows Forms)](event-handlers-overview-windows-forms.md) a [přehled událostí (model Windows Forms)](events-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="85abc-106">Also see [Event Handlers Overview (Windows Forms)](event-handlers-overview-windows-forms.md) and [Events Overview (Windows Forms)](events-overview-windows-forms.md).</span></span>

## <a name="mouse-information"></a><span data-ttu-id="85abc-107">Informace o myši</span><span class="sxs-lookup"><span data-stu-id="85abc-107">Mouse Information</span></span>

<span data-ttu-id="85abc-108">A <xref:System.Windows.Forms.MouseEventArgs> se pošle obslužným rutinám událostí myši souvisejících s kliknutím na tlačítko myši a sledováním pohybu myši.</span><span class="sxs-lookup"><span data-stu-id="85abc-108">A <xref:System.Windows.Forms.MouseEventArgs> is sent to the handlers of mouse events related to clicking a mouse button and tracking mouse movements.</span></span> <span data-ttu-id="85abc-109"><xref:System.Windows.Forms.MouseEventArgs>obsahuje informace o aktuálním stavu myši, včetně umístění ukazatele myši v souřadnicích klienta, stisknutých tlačítek myši a o tom, zda bylo kolečko myši posunuto.</span><span class="sxs-lookup"><span data-stu-id="85abc-109"><xref:System.Windows.Forms.MouseEventArgs> provides information about the current state of the mouse, including the location of the mouse pointer in client coordinates, which mouse buttons are pressed, and whether the mouse wheel has scrolled.</span></span> <span data-ttu-id="85abc-110">Několik událostí myši, jako jsou například ty, které jednoduše upozorňují, když ukazatel myši zadáte nebo opustí hranice ovládacího prvku, pošle <xref:System.EventArgs> obslužné rutině události žádné další informace.</span><span class="sxs-lookup"><span data-stu-id="85abc-110">Several mouse events, such as those that simply notify when the mouse pointer has entered or left the bounds of a control, send an <xref:System.EventArgs> to the event handler with no further information.</span></span>

<span data-ttu-id="85abc-111">Chcete-li znát aktuální stav tlačítek myši nebo umístění ukazatele myši a chcete se vyhnout manipulaci s událostí myši, můžete také použít <xref:System.Windows.Forms.Control.MouseButtons%2A> vlastnosti <xref:System.Windows.Forms.Control> a <xref:System.Windows.Forms.Control.MousePosition%2A> třídy.</span><span class="sxs-lookup"><span data-stu-id="85abc-111">If you want to know the current state of the mouse buttons or the location of the mouse pointer, and you want to avoid handling a mouse event, you can also use the <xref:System.Windows.Forms.Control.MouseButtons%2A> and <xref:System.Windows.Forms.Control.MousePosition%2A> properties of the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="85abc-112"><xref:System.Windows.Forms.Control.MouseButtons%2A>Vrátí informace o tom, která tlačítka myši jsou právě stisknutá.</span><span class="sxs-lookup"><span data-stu-id="85abc-112"><xref:System.Windows.Forms.Control.MouseButtons%2A> returns information about which mouse buttons are currently pressed.</span></span> <span data-ttu-id="85abc-113">Vrátí souřadnice obrazovky ukazatele myši a je ekvivalentní hodnotě <xref:System.Windows.Forms.Cursor.Position%2A>vrácené hodnotou. <xref:System.Windows.Forms.Control.MousePosition%2A></span><span class="sxs-lookup"><span data-stu-id="85abc-113">The <xref:System.Windows.Forms.Control.MousePosition%2A> returns the screen coordinates of the mouse pointer and is equivalent to the value returned by <xref:System.Windows.Forms.Cursor.Position%2A>.</span></span>

## <a name="converting-between-screen-and-client-coordinates"></a><span data-ttu-id="85abc-114">Převod mezi souřadnicemi obrazovky a klienta</span><span class="sxs-lookup"><span data-stu-id="85abc-114">Converting Between Screen and Client Coordinates</span></span>

<span data-ttu-id="85abc-115">Vzhledem k tomu, že některé informace o umístění myši jsou v souřadnicích klienta a některé jsou v souřadnicích obrazovky, možná budete muset převést bod z jednoho systému souřadnic na druhý.</span><span class="sxs-lookup"><span data-stu-id="85abc-115">Because some mouse location information is in client coordinates and some is in screen coordinates, you may need to convert a point from one coordinate system to the other.</span></span> <span data-ttu-id="85abc-116">To lze provést snadno pomocí <xref:System.Windows.Forms.Control.PointToClient%2A> metod a <xref:System.Windows.Forms.Control.PointToScreen%2A> dostupných ve <xref:System.Windows.Forms.Control> třídě.</span><span class="sxs-lookup"><span data-stu-id="85abc-116">You can do this easily by using the <xref:System.Windows.Forms.Control.PointToClient%2A> and <xref:System.Windows.Forms.Control.PointToScreen%2A> methods available on the <xref:System.Windows.Forms.Control> class.</span></span>

## <a name="standard-click-event-behavior"></a><span data-ttu-id="85abc-117">Standardní chování události kliknutí</span><span class="sxs-lookup"><span data-stu-id="85abc-117">Standard Click Event Behavior</span></span>

<span data-ttu-id="85abc-118">Pokud chcete zpracovávat události kliknutí myší ve správném pořadí, musíte znát pořadí, ve kterém jsou události kliknutí vyvolány v ovládacích prvcích model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="85abc-118">If you want to handle mouse click events in the proper order, you need to know the order in which click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="85abc-119">Všechny model Windows Forms ovládací prvky vyvolávají události Click ve stejném pořadí při stisknutí a uvolnění tlačítka myši (bez ohledu na to, které tlačítko myši), s výjimkou těch, které jsou uvedeny v následujícím seznamu pro jednotlivé ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="85abc-119">All Windows Forms controls raise click events in the same order when a mouse button is pressed and released (regardless of which mouse button), except where noted in the following list for individual controls.</span></span> <span data-ttu-id="85abc-120">Následující seznam zobrazuje pořadí událostí vyvolaných jedním kliknutím myši na tlačítko:</span><span class="sxs-lookup"><span data-stu-id="85abc-120">The following list shows the order of events raised for a single mouse-button click:</span></span>

1. <span data-ttu-id="85abc-121"><xref:System.Windows.Forms.Control.MouseDown>událostí.</span><span class="sxs-lookup"><span data-stu-id="85abc-121"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

2. <span data-ttu-id="85abc-122"><xref:System.Windows.Forms.Control.Click>událostí.</span><span class="sxs-lookup"><span data-stu-id="85abc-122"><xref:System.Windows.Forms.Control.Click> event.</span></span>

3. <span data-ttu-id="85abc-123"><xref:System.Windows.Forms.Control.MouseClick>událostí.</span><span class="sxs-lookup"><span data-stu-id="85abc-123"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>

4. <span data-ttu-id="85abc-124"><xref:System.Windows.Forms.Control.MouseUp>událostí.</span><span class="sxs-lookup"><span data-stu-id="85abc-124"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

<span data-ttu-id="85abc-125">Následuje pořadí událostí vyvolaných pro dvojité kliknutí myší:</span><span class="sxs-lookup"><span data-stu-id="85abc-125">Following is the order of events raised for a double mouse-button click:</span></span>

1. <span data-ttu-id="85abc-126"><xref:System.Windows.Forms.Control.MouseDown>událostí.</span><span class="sxs-lookup"><span data-stu-id="85abc-126"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

2. <span data-ttu-id="85abc-127"><xref:System.Windows.Forms.Control.Click>událostí.</span><span class="sxs-lookup"><span data-stu-id="85abc-127"><xref:System.Windows.Forms.Control.Click> event.</span></span>

3. <span data-ttu-id="85abc-128"><xref:System.Windows.Forms.Control.MouseClick>událostí.</span><span class="sxs-lookup"><span data-stu-id="85abc-128"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>

4. <span data-ttu-id="85abc-129"><xref:System.Windows.Forms.Control.MouseUp>událostí.</span><span class="sxs-lookup"><span data-stu-id="85abc-129"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

5. <span data-ttu-id="85abc-130"><xref:System.Windows.Forms.Control.MouseDown>událostí.</span><span class="sxs-lookup"><span data-stu-id="85abc-130"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

6. <span data-ttu-id="85abc-131"><xref:System.Windows.Forms.Control.DoubleClick>událostí.</span><span class="sxs-lookup"><span data-stu-id="85abc-131"><xref:System.Windows.Forms.Control.DoubleClick> event.</span></span> <span data-ttu-id="85abc-132">(To se může lišit v závislosti na tom, zda má <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> ovládací prvek nastaven bit stylu na. `true`</span><span class="sxs-lookup"><span data-stu-id="85abc-132">(This can vary, depending on whether the control in question has the <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> style bit set to `true`.</span></span> <span data-ttu-id="85abc-133">Další informace o nastavení <xref:System.Windows.Forms.ControlStyles> bitu <xref:System.Windows.Forms.Control.SetStyle%2A> naleznete v metodě.)</span><span class="sxs-lookup"><span data-stu-id="85abc-133">For more information about how to set a <xref:System.Windows.Forms.ControlStyles> bit, see the <xref:System.Windows.Forms.Control.SetStyle%2A> method.)</span></span>

7. <span data-ttu-id="85abc-134"><xref:System.Windows.Forms.Control.MouseDoubleClick>událostí.</span><span class="sxs-lookup"><span data-stu-id="85abc-134"><xref:System.Windows.Forms.Control.MouseDoubleClick> event.</span></span>

8. <span data-ttu-id="85abc-135"><xref:System.Windows.Forms.Control.MouseUp>událostí.</span><span class="sxs-lookup"><span data-stu-id="85abc-135"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

<span data-ttu-id="85abc-136">Příklad kódu, který ukazuje pořadí událostí kliknutí myší, naleznete v tématu [How to: Zpracování událostí vstupu uživatele v ovládacích prvcích](how-to-handle-user-input-events-in-windows-forms-controls.md)model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="85abc-136">For a code example that demonstrates the order of the mouse click events, see [How to: Handle User Input Events in Windows Forms Controls](how-to-handle-user-input-events-in-windows-forms-controls.md).</span></span>

### <a name="individual-controls"></a><span data-ttu-id="85abc-137">Jednotlivé ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="85abc-137">Individual Controls</span></span>

<span data-ttu-id="85abc-138">Následující ovládací prvky neodpovídají standardnímu chování události kliknutí myší:</span><span class="sxs-lookup"><span data-stu-id="85abc-138">The following controls do not conform to the standard mouse click event behavior:</span></span>

- <span data-ttu-id="85abc-139"><xref:System.Windows.Forms.Button>ovládací <xref:System.Windows.Forms.CheckBox>prvky <xref:System.Windows.Forms.ComboBox>,, <xref:System.Windows.Forms.RadioButton> a</span><span class="sxs-lookup"><span data-stu-id="85abc-139"><xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.ComboBox>, and <xref:System.Windows.Forms.RadioButton> controls</span></span>

  > [!NOTE]
  > <span data-ttu-id="85abc-140">V případě <xref:System.Windows.Forms.ComboBox> ovládacího prvku se k chování události podrobná později dojde, když uživatel klikne na pole upravit, tlačítko nebo na položku v seznamu.</span><span class="sxs-lookup"><span data-stu-id="85abc-140">For the <xref:System.Windows.Forms.ComboBox> control, the event behavior detailed later occurs if the user clicks on the edit field, the button, or on an item within the list.</span></span>

  - <span data-ttu-id="85abc-141">Klikněte levým na <xref:System.Windows.Forms.Control.Click>:,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="85abc-141">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="85abc-142">Klikněte pravým tlačítkem myši: Nebyly vyvolány žádné události kliknutí.</span><span class="sxs-lookup"><span data-stu-id="85abc-142">Right click: No click events raised</span></span>

  - <span data-ttu-id="85abc-143">Dvakrát klikněte levým na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="85abc-143">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="85abc-144">Klikněte dvakrát na tlačítko: Nebyly vyvolány žádné události kliknutí.</span><span class="sxs-lookup"><span data-stu-id="85abc-144">Right double-click: No click events raised</span></span>

- <span data-ttu-id="85abc-145"><xref:System.Windows.Forms.TextBox>ovládací <xref:System.Windows.Forms.RichTextBox>prvky <xref:System.Windows.Forms.ListBox>, ,<xref:System.Windows.Forms.MaskedTextBox>, a<xref:System.Windows.Forms.CheckedListBox></span><span class="sxs-lookup"><span data-stu-id="85abc-145"><xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox>, and <xref:System.Windows.Forms.CheckedListBox> controls</span></span>

  > [!NOTE]
  > <span data-ttu-id="85abc-146">K chování události později dojde, když uživatel klikne kamkoli v rámci těchto ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="85abc-146">The event behavior detailed later occurs when the user clicks anywhere within these controls.</span></span>

  - <span data-ttu-id="85abc-147">Klikněte levým na <xref:System.Windows.Forms.Control.Click>:,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="85abc-147">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="85abc-148">Klikněte pravým tlačítkem myši: Nebyly vyvolány žádné události kliknutí.</span><span class="sxs-lookup"><span data-stu-id="85abc-148">Right click: No click events raised</span></span>

  - <span data-ttu-id="85abc-149">Dvakrát klikněte levým na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="85abc-149">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="85abc-150">Klikněte dvakrát na tlačítko: Nebyly vyvolány žádné události kliknutí.</span><span class="sxs-lookup"><span data-stu-id="85abc-150">Right double-click: No click events raised</span></span>

- <span data-ttu-id="85abc-151"><xref:System.Windows.Forms.ListView>nad</span><span class="sxs-lookup"><span data-stu-id="85abc-151"><xref:System.Windows.Forms.ListView> control</span></span>

  > [!NOTE]
  > <span data-ttu-id="85abc-152">K chování události později dochází pouze v případě, že uživatel klikne na položky v <xref:System.Windows.Forms.ListView> ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="85abc-152">The event behavior detailed later occurs only when the user clicks on the items in the <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="85abc-153">Pro kliknutí jinde v ovládacím prvku nejsou vyvolány žádné události.</span><span class="sxs-lookup"><span data-stu-id="85abc-153">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="85abc-154">Kromě událostí popsaných dále jsou <xref:System.Windows.Forms.ListView.BeforeLabelEdit> k dispozici události a <xref:System.Windows.Forms.ListView.AfterLabelEdit> , které vás mohou zajímat, pokud chcete použít ověřování s <xref:System.Windows.Forms.ListView> ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="85abc-154">In addition to the events described later, there are the <xref:System.Windows.Forms.ListView.BeforeLabelEdit> and <xref:System.Windows.Forms.ListView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.ListView> control.</span></span>

  - <span data-ttu-id="85abc-155">Klikněte levým na <xref:System.Windows.Forms.Control.Click>:,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="85abc-155">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="85abc-156">Klikněte pravým <xref:System.Windows.Forms.Control.Click>tlačítkem myši:,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="85abc-156">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="85abc-157">Dvakrát klikněte levým na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="85abc-157">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="85abc-158">Klikněte dvakrát na tlačítko: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="85abc-158">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

- <span data-ttu-id="85abc-159"><xref:System.Windows.Forms.TreeView>nad</span><span class="sxs-lookup"><span data-stu-id="85abc-159"><xref:System.Windows.Forms.TreeView> control</span></span>

  > [!NOTE]
  > <span data-ttu-id="85abc-160">K chování události později dochází pouze v případě, že uživatel klikne na samotné položky nebo napravo od položek v <xref:System.Windows.Forms.TreeView> ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="85abc-160">The event behavior detailed later occurs only when the user clicks on the items themselves or to the right of the items in the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="85abc-161">Pro kliknutí jinde v ovládacím prvku nejsou vyvolány žádné události.</span><span class="sxs-lookup"><span data-stu-id="85abc-161">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="85abc-162">Kromě těch, které jsou <xref:System.Windows.Forms.TreeView.BeforeCheck>popsány později, existují <xref:System.Windows.Forms.TreeView.BeforeSelect> <xref:System.Windows.Forms.TreeView.AfterCheck> <xref:System.Windows.Forms.TreeView.AfterLabelEdit> <xref:System.Windows.Forms.TreeView.BeforeLabelEdit> události,<xref:System.Windows.Forms.TreeView.AfterSelect>,,, a, které vás mohou zajímat, pokud chcete použít ověřování s ovládacímprvkem<xref:System.Windows.Forms.TreeView> .</span><span class="sxs-lookup"><span data-stu-id="85abc-162">In addition to those described later, there are the <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck>, and <xref:System.Windows.Forms.TreeView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.TreeView> control.</span></span>

  - <span data-ttu-id="85abc-163">Klikněte levým na <xref:System.Windows.Forms.Control.Click>:,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="85abc-163">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="85abc-164">Klikněte pravým <xref:System.Windows.Forms.Control.Click>tlačítkem myši:,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="85abc-164">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="85abc-165">Dvakrát klikněte levým na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="85abc-165">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="85abc-166">Klikněte dvakrát na tlačítko: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="85abc-166">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

### <a name="painting-behavior-of-toggle-controls"></a><span data-ttu-id="85abc-167">Chování při malování pro přepínací ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="85abc-167">Painting Behavior of Toggle Controls</span></span>

<span data-ttu-id="85abc-168">Přepínací ovládací prvky, jako jsou například ovládací prvky odvozené <xref:System.Windows.Forms.ButtonBase> od třídy, mají následující chování při malování v kombinaci s událostmi kliknutí myší:</span><span class="sxs-lookup"><span data-stu-id="85abc-168">Toggle controls, such as the controls deriving from the <xref:System.Windows.Forms.ButtonBase> class, have the following distinctive painting behavior in combination with mouse click events:</span></span>

1. <span data-ttu-id="85abc-169">Uživatel stiskne tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="85abc-169">The user presses the mouse button.</span></span>

2. <span data-ttu-id="85abc-170">Ovládací prvky vykreslí ve stisknutém stavu.</span><span class="sxs-lookup"><span data-stu-id="85abc-170">The control paints in the pressed state.</span></span>

3. <span data-ttu-id="85abc-171"><xref:System.Windows.Forms.Control.MouseDown> Událost je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="85abc-171">The <xref:System.Windows.Forms.Control.MouseDown> event is raised.</span></span>

4. <span data-ttu-id="85abc-172">Uživatel uvolní tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="85abc-172">The user releases the mouse button.</span></span>

5. <span data-ttu-id="85abc-173">Ovládací prvky se vykreslí do vystouplého stavu.</span><span class="sxs-lookup"><span data-stu-id="85abc-173">The control paints in the raised state.</span></span>

6. <span data-ttu-id="85abc-174"><xref:System.Windows.Forms.Control.Click> Událost je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="85abc-174">The <xref:System.Windows.Forms.Control.Click> event is raised.</span></span>

7. <span data-ttu-id="85abc-175"><xref:System.Windows.Forms.Control.MouseClick> Událost je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="85abc-175">The <xref:System.Windows.Forms.Control.MouseClick> event is raised.</span></span>

8. <span data-ttu-id="85abc-176"><xref:System.Windows.Forms.Control.MouseUp> Událost je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="85abc-176">The <xref:System.Windows.Forms.Control.MouseUp> event is raised.</span></span>

    > [!NOTE]
    > <span data-ttu-id="85abc-177">Pokud uživatel přesune ukazatel myši na ovládací prvek přepínacího tlačítka, když je tlačítko myši vypnuté (například přesunutí myši <xref:System.Windows.Forms.Button> nad ovládací prvek během jeho stisknutí), ovládací prvek přepínacího tlačítka se vykreslí ve vystouplém stavu a dojde k výskytu <xref:System.Windows.Forms.Control.MouseUp> pouze události.</span><span class="sxs-lookup"><span data-stu-id="85abc-177">If the user moves the pointer out of the toggle control while the mouse button is down (such as moving the mouse off the <xref:System.Windows.Forms.Button> control while it is pressed), the toggle control will paint in the raised state and only the <xref:System.Windows.Forms.Control.MouseUp> event occurs.</span></span> <span data-ttu-id="85abc-178">Události <xref:System.Windows.Forms.Control.Click> nebo<xref:System.Windows.Forms.Control.MouseClick> se v této situaci neobjeví.</span><span class="sxs-lookup"><span data-stu-id="85abc-178">The <xref:System.Windows.Forms.Control.Click> or <xref:System.Windows.Forms.Control.MouseClick> events will not occur in this situation.</span></span>

## <a name="see-also"></a><span data-ttu-id="85abc-179">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85abc-179">See also</span></span>

- [<span data-ttu-id="85abc-180">Vstup z myši v aplikaci Windows Forms</span><span class="sxs-lookup"><span data-stu-id="85abc-180">Mouse Input in a Windows Forms Application</span></span>](mouse-input-in-a-windows-forms-application.md)
