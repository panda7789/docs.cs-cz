---
title: "Události myši ve Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 803f2daab5b8f6e216effe4a9ae9f34752d24e70
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="mouse-events-in-windows-forms"></a><span data-ttu-id="79710-102">Události myši ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="79710-102">Mouse Events in Windows Forms</span></span>
<span data-ttu-id="79710-103">Pokud zpracováváte vstup z myši, obvykle chcete znát umístění myši ukazatel a stav tlačítka myši.</span><span class="sxs-lookup"><span data-stu-id="79710-103">When you handle mouse input, you usually want to know the location of the mouse pointer and the state of the mouse buttons.</span></span> <span data-ttu-id="79710-104">Toto téma obsahuje podrobné informace o tom, jak získat tyto informace z událostí myši a vysvětluje pořadí, ve které klikněte na tlačítko myši události jsou vyvolány v ovládacích prvcích Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="79710-104">This topic provides details on how to get this information from mouse events, and explains the order in which mouse click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="79710-105">Seznam a popis všech událostí myši najdete v tématu [jak funguje vstup myši Windows Forms](../../../docs/framework/winforms/how-mouse-input-works-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="79710-105">For a list and description of all of the mouse events, see [How Mouse Input Works in Windows Forms](../../../docs/framework/winforms/how-mouse-input-works-in-windows-forms.md).</span></span>  <span data-ttu-id="79710-106">Viz také [Přehled obslužných rutin událostí (Windows Forms)](http://msdn.microsoft.com/library/be6fx1bb\(v=vs.110\)), [Přehled událostí (Windows Forms)](http://msdn.microsoft.com/library/1h12f09z\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="79710-106">Also see [Event Handlers Overview (Windows Forms)](http://msdn.microsoft.com/library/be6fx1bb\(v=vs.110\)), [Events Overview (Windows Forms)](http://msdn.microsoft.com/library/1h12f09z\(v=vs.110\))</span></span>  
  
## <a name="mouse-information"></a><span data-ttu-id="79710-107">Informace o myši</span><span class="sxs-lookup"><span data-stu-id="79710-107">Mouse Information</span></span>  
 <span data-ttu-id="79710-108">A <xref:System.Windows.Forms.MouseEventArgs> posílá obslužných rutin událostí myši související s kliknutím na tlačítko myši a sledováním pohybů myši.</span><span class="sxs-lookup"><span data-stu-id="79710-108">A <xref:System.Windows.Forms.MouseEventArgs> is sent to the handlers of mouse events related to clicking a mouse button and tracking mouse movements.</span></span> <span data-ttu-id="79710-109"><xref:System.Windows.Forms.MouseEventArgs>poskytuje informace o aktuálním stavu myš, včetně umístění ukazatele myši v souřadnicích klienta, které jsou stisknutí tlačítka myši a zda má přešli kolečko myši.</span><span class="sxs-lookup"><span data-stu-id="79710-109"><xref:System.Windows.Forms.MouseEventArgs> provides information about the current state of the mouse, including the location of the mouse pointer in client coordinates, which mouse buttons are pressed, and whether the mouse wheel has scrolled.</span></span> <span data-ttu-id="79710-110">Několik myši události, jako jsou ty, které jednoduše Upozornit při zpracování má ukazatel myši zadali nebo ponecháno hranice ovládacího prvku, odeslání <xref:System.EventArgs> k obslužné rutině událostí s žádné další informace.</span><span class="sxs-lookup"><span data-stu-id="79710-110">Several mouse events, such as those that simply notify when the mouse pointer has entered or left the bounds of a control, send an <xref:System.EventArgs> to the event handler with no further information.</span></span>  
  
 <span data-ttu-id="79710-111">Pokud chcete zjistit aktuální stav tlačítka myši nebo umístění ukazatele myši a budete chtít vyhnout zpracování události myši, můžete použít také <xref:System.Windows.Forms.Control.MouseButtons%2A> a <xref:System.Windows.Forms.Control.MousePosition%2A> vlastnosti <xref:System.Windows.Forms.Control> třídy.</span><span class="sxs-lookup"><span data-stu-id="79710-111">If you want to know the current state of the mouse buttons or the location of the mouse pointer, and you want to avoid handling a mouse event, you can also use the <xref:System.Windows.Forms.Control.MouseButtons%2A> and <xref:System.Windows.Forms.Control.MousePosition%2A> properties of the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="79710-112"><xref:System.Windows.Forms.Control.MouseButtons%2A>vrací informace o tom, které jsou aktuálně stisknutí tlačítka myši.</span><span class="sxs-lookup"><span data-stu-id="79710-112"><xref:System.Windows.Forms.Control.MouseButtons%2A> returns information about which mouse buttons are currently pressed.</span></span> <span data-ttu-id="79710-113"><xref:System.Windows.Forms.Control.MousePosition%2A> Vrátí souřadnice obrazovky ukazatele myši a je ekvivalentem hodnoty vrácené <xref:System.Windows.Forms.Cursor.Position%2A>.</span><span class="sxs-lookup"><span data-stu-id="79710-113">The <xref:System.Windows.Forms.Control.MousePosition%2A> returns the screen coordinates of the mouse pointer and is equivalent to the value returned by <xref:System.Windows.Forms.Cursor.Position%2A>.</span></span>  
  
## <a name="converting-between-screen-and-client-coordinates"></a><span data-ttu-id="79710-114">Převod mezi obrazovky a klienta koordinuje</span><span class="sxs-lookup"><span data-stu-id="79710-114">Converting Between Screen and Client Coordinates</span></span>  
 <span data-ttu-id="79710-115">Protože některé informace o umístění myši v souřadnicích klienta a některé v souřadnice obrazovky, musíte převést bod souřadnicový systém.</span><span class="sxs-lookup"><span data-stu-id="79710-115">Because some mouse location information is in client coordinates and some is in screen coordinates, you may need to convert a point from one coordinate system to the other.</span></span> <span data-ttu-id="79710-116">Můžete k tomu snadno pomocí <xref:System.Windows.Forms.Control.PointToClient%2A> a <xref:System.Windows.Forms.Control.PointToScreen%2A> metody, které jsou k dispozici na <xref:System.Windows.Forms.Control> třídy.</span><span class="sxs-lookup"><span data-stu-id="79710-116">You can do this easily by using the <xref:System.Windows.Forms.Control.PointToClient%2A> and <xref:System.Windows.Forms.Control.PointToScreen%2A> methods available on the <xref:System.Windows.Forms.Control> class.</span></span>  
  
## <a name="standard-click-event-behavior"></a><span data-ttu-id="79710-117">Standardní chování události, klikněte na tlačítko</span><span class="sxs-lookup"><span data-stu-id="79710-117">Standard Click Event Behavior</span></span>  
 <span data-ttu-id="79710-118">Pokud chcete zpracovávat myši klikněte na události ve správném pořadí, je nutné znát pořadí, ve které klikněte na tlačítko akce jsou vyvolány ve Windows Forms – ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="79710-118">If you want to handle mouse click events in the proper order, you need to know the order in which click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="79710-119">Až tlačítko myši po stisknutí a uvolnění (bez ohledu na které tlačítko myši), s výjimkou uvedeno v následujícím seznamu u jednotlivých ovládacích prvků, klikněte na všechny formuláře Windows, které vyvolávají události ve stejném pořadí.</span><span class="sxs-lookup"><span data-stu-id="79710-119">All Windows Forms controls raise click events in the same order when a mouse button is pressed and released (regardless of which mouse button), except where noted in the following list for individual controls.</span></span> <span data-ttu-id="79710-120">V následujícím seznamu jsou pořadí událostí vyvolaných pro klikněte na tlačítko myši v jednom:</span><span class="sxs-lookup"><span data-stu-id="79710-120">The following list shows the order of events raised for a single mouse-button click:</span></span>  
  
1.  <span data-ttu-id="79710-121"><xref:System.Windows.Forms.Control.MouseDown>událost.</span><span class="sxs-lookup"><span data-stu-id="79710-121"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>  
  
2.  <span data-ttu-id="79710-122"><xref:System.Windows.Forms.Control.Click>událost.</span><span class="sxs-lookup"><span data-stu-id="79710-122"><xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
3.  <span data-ttu-id="79710-123"><xref:System.Windows.Forms.Control.MouseClick>událost.</span><span class="sxs-lookup"><span data-stu-id="79710-123"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>  
  
4.  <span data-ttu-id="79710-124"><xref:System.Windows.Forms.Control.MouseUp>událost.</span><span class="sxs-lookup"><span data-stu-id="79710-124"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>  
  
 <span data-ttu-id="79710-125">Toto je pořadí událostí vyvolaných pro tlačítko myši dvojité kliknutí:</span><span class="sxs-lookup"><span data-stu-id="79710-125">Following is the order of events raised for a double mouse-button click:</span></span>  
  
1.  <span data-ttu-id="79710-126"><xref:System.Windows.Forms.Control.MouseDown>událost.</span><span class="sxs-lookup"><span data-stu-id="79710-126"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>  
  
2.  <span data-ttu-id="79710-127"><xref:System.Windows.Forms.Control.Click>událost.</span><span class="sxs-lookup"><span data-stu-id="79710-127"><xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
3.  <span data-ttu-id="79710-128"><xref:System.Windows.Forms.Control.MouseClick>událost.</span><span class="sxs-lookup"><span data-stu-id="79710-128"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>  
  
4.  <span data-ttu-id="79710-129"><xref:System.Windows.Forms.Control.MouseUp>událost.</span><span class="sxs-lookup"><span data-stu-id="79710-129"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>  
  
5.  <span data-ttu-id="79710-130"><xref:System.Windows.Forms.Control.MouseDown>událost.</span><span class="sxs-lookup"><span data-stu-id="79710-130"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>  
  
6.  <span data-ttu-id="79710-131"><xref:System.Windows.Forms.Control.DoubleClick>událost.</span><span class="sxs-lookup"><span data-stu-id="79710-131"><xref:System.Windows.Forms.Control.DoubleClick> event.</span></span> <span data-ttu-id="79710-132">(To se může lišit, v závislosti na tom, jestli se má ovládací prvek v <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> k nastaven bit stylu `true`.</span><span class="sxs-lookup"><span data-stu-id="79710-132">(This can vary, depending on whether the control in question has the <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> style bit set to `true`.</span></span> <span data-ttu-id="79710-133">Další informace o tom, jak nastavit <xref:System.Windows.Forms.ControlStyles> bit, najdete v článku <xref:System.Windows.Forms.Control.SetStyle%2A> metoda.)</span><span class="sxs-lookup"><span data-stu-id="79710-133">For more information about how to set a <xref:System.Windows.Forms.ControlStyles> bit, see the <xref:System.Windows.Forms.Control.SetStyle%2A> method.)</span></span>  
  
7.  <span data-ttu-id="79710-134"><xref:System.Windows.Forms.Control.MouseDoubleClick>událost.</span><span class="sxs-lookup"><span data-stu-id="79710-134"><xref:System.Windows.Forms.Control.MouseDoubleClick> event.</span></span>  
  
8.  <span data-ttu-id="79710-135"><xref:System.Windows.Forms.Control.MouseUp>událost.</span><span class="sxs-lookup"><span data-stu-id="79710-135"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>  
  
 <span data-ttu-id="79710-136">Příklad kódu, který ukazuje pořadí myši klikněte na události, najdete v části [postupy: zpracování událostí vstup uživatele v ovládacích prvcích Windows Forms](../../../docs/framework/winforms/how-to-handle-user-input-events-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="79710-136">For a code example that demonstrates the order of the mouse click events, see [How to: Handle User Input Events in Windows Forms Controls](../../../docs/framework/winforms/how-to-handle-user-input-events-in-windows-forms-controls.md).</span></span>  
  
### <a name="individual-controls"></a><span data-ttu-id="79710-137">Jednotlivých ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="79710-137">Individual Controls</span></span>  
 <span data-ttu-id="79710-138">Ovládací prvky nejsou v souladu s standardní myši klikněte na tlačítko chování události:</span><span class="sxs-lookup"><span data-stu-id="79710-138">The following controls do not conform to the standard mouse click event behavior:</span></span>  
  
-   <span data-ttu-id="79710-139"><xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.ComboBox>, a <xref:System.Windows.Forms.RadioButton> ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="79710-139"><xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.ComboBox>, and <xref:System.Windows.Forms.RadioButton> controls</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="79710-140">Pro <xref:System.Windows.Forms.ComboBox> dojde chování události, které jsou podrobně popsané ovládací prvek, pokud uživatel klikne na pole upravit tlačítko, nebo na položku v seznamu.</span><span class="sxs-lookup"><span data-stu-id="79710-140">For the <xref:System.Windows.Forms.ComboBox> control, the event behavior detailed later occurs if the user clicks on the edit field, the button, or on an item within the list.</span></span>  
  
    -   <span data-ttu-id="79710-141">Ikona kliknutí levým tlačítkem: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="79710-141">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>  
  
    -   <span data-ttu-id="79710-142">Klikněte pravým tlačítkem: žádné události kliknutí na vyvolána</span><span class="sxs-lookup"><span data-stu-id="79710-142">Right click: No click events raised</span></span>  
  
    -   <span data-ttu-id="79710-143">Levé poklikejte na soubor: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="79710-143">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>  
  
    -   <span data-ttu-id="79710-144">Právo dvakrát klikněte na: žádné události kliknutí na vyvolána</span><span class="sxs-lookup"><span data-stu-id="79710-144">Right double-click: No click events raised</span></span>  
  
-   <span data-ttu-id="79710-145"><xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox>, a <xref:System.Windows.Forms.CheckedListBox> ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="79710-145"><xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox>, and <xref:System.Windows.Forms.CheckedListBox> controls</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="79710-146">Chování události, které jsou podrobně popsané nastane, když uživatel klikne kdekoli v rámci těchto ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="79710-146">The event behavior detailed later occurs when the user clicks anywhere within these controls.</span></span>  
  
    -   <span data-ttu-id="79710-147">Ikona kliknutí levým tlačítkem: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="79710-147">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>  
  
    -   <span data-ttu-id="79710-148">Klikněte pravým tlačítkem: žádné události kliknutí na vyvolána</span><span class="sxs-lookup"><span data-stu-id="79710-148">Right click: No click events raised</span></span>  
  
    -   <span data-ttu-id="79710-149">Levé poklikejte na soubor: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="79710-149">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>  
  
    -   <span data-ttu-id="79710-150">Právo dvakrát klikněte na: žádné události kliknutí na vyvolána</span><span class="sxs-lookup"><span data-stu-id="79710-150">Right double-click: No click events raised</span></span>  
  
-   <span data-ttu-id="79710-151"><xref:System.Windows.Forms.ListView>ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="79710-151"><xref:System.Windows.Forms.ListView> control</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="79710-152">Podrobně popsané chování události dojde, pouze když uživatel klikne na položky v <xref:System.Windows.Forms.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="79710-152">The event behavior detailed later occurs only when the user clicks on the items in the <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="79710-153">Žádné události jsou vyvolány pro klikne na ovládací prvek někde jinde.</span><span class="sxs-lookup"><span data-stu-id="79710-153">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="79710-154">Kromě události popsané dál, jsou k dispozici <xref:System.Windows.Forms.ListView.BeforeLabelEdit> a <xref:System.Windows.Forms.ListView.AfterLabelEdit> události, které můžou být vás zajímají, pokud chcete použít ověřování pomocí <xref:System.Windows.Forms.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="79710-154">In addition to the events described later, there are the <xref:System.Windows.Forms.ListView.BeforeLabelEdit> and <xref:System.Windows.Forms.ListView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
    -   <span data-ttu-id="79710-155">Ikona kliknutí levým tlačítkem: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="79710-155">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>  
  
    -   <span data-ttu-id="79710-156">Klikněte pravým tlačítkem: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="79710-156">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>  
  
    -   <span data-ttu-id="79710-157">Levé poklikejte na soubor: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="79710-157">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>  
  
    -   <span data-ttu-id="79710-158">Právo dvakrát klikněte na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="79710-158">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>  
  
-   <span data-ttu-id="79710-159"><xref:System.Windows.Forms.TreeView>ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="79710-159"><xref:System.Windows.Forms.TreeView> control</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="79710-160">Podrobně popsané chování události dojde, pouze když uživatel klikne na položky sami nebo napravo od položky v <xref:System.Windows.Forms.TreeView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="79710-160">The event behavior detailed later occurs only when the user clicks on the items themselves or to the right of the items in the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="79710-161">Žádné události jsou vyvolány pro klikne na ovládací prvek někde jinde.</span><span class="sxs-lookup"><span data-stu-id="79710-161">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="79710-162">Kromě těch, které popsané dál, jsou k dispozici <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck>, a <xref:System.Windows.Forms.TreeView.AfterLabelEdit> události, které můžou být vás zajímají, pokud chcete použít ověřování pomocí <xref:System.Windows.Forms.TreeView> ovládací prvek .</span><span class="sxs-lookup"><span data-stu-id="79710-162">In addition to those described later, there are the <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck>, and <xref:System.Windows.Forms.TreeView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.TreeView> control.</span></span>  
  
    -   <span data-ttu-id="79710-163">Ikona kliknutí levým tlačítkem: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="79710-163">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>  
  
    -   <span data-ttu-id="79710-164">Klikněte pravým tlačítkem: <xref:System.Windows.Forms.Control.Click>,<xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="79710-164">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>  
  
    -   <span data-ttu-id="79710-165">Levé poklikejte na soubor: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="79710-165">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>  
  
    -   <span data-ttu-id="79710-166">Právo dvakrát klikněte na: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>,<xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="79710-166">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>  
  
### <a name="painting-behavior-of-toggle-controls"></a><span data-ttu-id="79710-167">Vykreslování chování ovládacích prvků přepínání</span><span class="sxs-lookup"><span data-stu-id="79710-167">Painting Behavior of Toggle Controls</span></span>  
 <span data-ttu-id="79710-168">Ovládací prvky, jako je například odvozování z ovládacích prvků přepínání <xref:System.Windows.Forms.ButtonBase> třídy, máte následující chování rozlišovací malování v kombinaci s myši, klikněte na události:</span><span class="sxs-lookup"><span data-stu-id="79710-168">Toggle controls, such as the controls deriving from the <xref:System.Windows.Forms.ButtonBase> class, have the following distinctive painting behavior in combination with mouse click events:</span></span>  
  
1.  <span data-ttu-id="79710-169">Uživatel tlačítka myši.</span><span class="sxs-lookup"><span data-stu-id="79710-169">The user presses the mouse button.</span></span>  
  
2.  <span data-ttu-id="79710-170">Ovládací prvek vybarví ve stavu při stisknutí tlačítka.</span><span class="sxs-lookup"><span data-stu-id="79710-170">The control paints in the pressed state.</span></span>  
  
3.  <span data-ttu-id="79710-171"><xref:System.Windows.Forms.Control.MouseDown> Událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="79710-171">The <xref:System.Windows.Forms.Control.MouseDown> event is raised.</span></span>  
  
4.  <span data-ttu-id="79710-172">Uživatel uvolní tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="79710-172">The user releases the mouse button.</span></span>  
  
5.  <span data-ttu-id="79710-173">Ovládací prvek vybarví v vyvolané stavu.</span><span class="sxs-lookup"><span data-stu-id="79710-173">The control paints in the raised state.</span></span>  
  
6.  <span data-ttu-id="79710-174"><xref:System.Windows.Forms.Control.Click> Událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="79710-174">The <xref:System.Windows.Forms.Control.Click> event is raised.</span></span>  
  
7.  <span data-ttu-id="79710-175"><xref:System.Windows.Forms.Control.MouseClick> Událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="79710-175">The <xref:System.Windows.Forms.Control.MouseClick> event is raised.</span></span>  
  
8.  <span data-ttu-id="79710-176"><xref:System.Windows.Forms.Control.MouseUp> Událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="79710-176">The <xref:System.Windows.Forms.Control.MouseUp> event is raised.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="79710-177">Pokud se uživatel přesune ukazatel mimo ovládací prvek přepínač, zatímco je tlačítko myši směrem dolů (například pohyb myši <xref:System.Windows.Forms.Button> řízení při stisknutí), bude malovat vyvolané ovládací prvek přepínač stavu a to pouze <xref:System.Windows.Forms.Control.MouseUp> dojde k události.</span><span class="sxs-lookup"><span data-stu-id="79710-177">If the user moves the pointer out of the toggle control while the mouse button is down (such as moving the mouse off the <xref:System.Windows.Forms.Button> control while it is pressed), the toggle control will paint in the raised state and only the <xref:System.Windows.Forms.Control.MouseUp> event occurs.</span></span> <span data-ttu-id="79710-178"><xref:System.Windows.Forms.Control.Click> Nebo <xref:System.Windows.Forms.Control.MouseClick> nebude v této situaci dojde k událostem.</span><span class="sxs-lookup"><span data-stu-id="79710-178">The <xref:System.Windows.Forms.Control.Click> or <xref:System.Windows.Forms.Control.MouseClick> events will not occur in this situation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79710-179">Viz také</span><span class="sxs-lookup"><span data-stu-id="79710-179">See Also</span></span>  
 [<span data-ttu-id="79710-180">Vstup z myši ve Windows Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="79710-180">Mouse Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
