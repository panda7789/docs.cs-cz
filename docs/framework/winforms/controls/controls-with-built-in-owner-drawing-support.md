---
title: Ovládací prvky s vestavěnou podporou vykreslování vlastníkem
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [Windows Forms], owner
- drawing [Windows Forms], custom
- controls [Windows Forms], changing appearance
- custom drawing
- owner drawing
ms.assetid: 3823d01e-9610-43e6-864d-99f9b7c2b351
ms.openlocfilehash: 5206289eaab1195e5314e21b0d49e4b8a5455b72
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54696305"
---
# <a name="controls-with-built-in-owner-drawing-support"></a><span data-ttu-id="15ae7-102">Ovládací prvky s vestavěnou podporou vykreslování vlastníkem</span><span class="sxs-lookup"><span data-stu-id="15ae7-102">Controls with Built-In Owner-Drawing Support</span></span>
<span data-ttu-id="15ae7-103">Vykreslení ve Windows Forms, který je také označován jako vlastní kreslení, vlastníka je postup pro změnu vizuálního vzhledu některé ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="15ae7-103">Owner drawing in Windows Forms, which is also known as custom drawing, is a technique for changing the visual appearance of certain controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15ae7-104">Slovo "control" v tomto tématu se používá k označení tříd, které jsou odvozeny z buď <xref:System.Windows.Forms.Control> nebo <xref:System.ComponentModel.Component>.</span><span class="sxs-lookup"><span data-stu-id="15ae7-104">The word "control" in this topic is used to mean classes that derive from either <xref:System.Windows.Forms.Control> or <xref:System.ComponentModel.Component>.</span></span>  
  
 <span data-ttu-id="15ae7-105">Obvykle Windows zpracovává Malování automaticky pomocí nastavení vlastností, jako <xref:System.Windows.Forms.Control.BackColor%2A> k určení vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="15ae7-105">Typically, Windows handles painting automatically by using property settings such as <xref:System.Windows.Forms.Control.BackColor%2A> to determine the appearance of a control.</span></span> <span data-ttu-id="15ae7-106">Pomocí vykreslení vlastníka můžete převzít kontrolu nad procesu Malování Změna vzhledu prvky, které nejsou k dispozici s použitím vlastností.</span><span class="sxs-lookup"><span data-stu-id="15ae7-106">With owner drawing, you take over the painting process, changing elements of appearance that are not available by using properties.</span></span> <span data-ttu-id="15ae7-107">Například mnoho ovládacích prvků můžete tak nastavit barvu textu, který se zobrazí, ale pro vás platí omezení na jednu barvu.</span><span class="sxs-lookup"><span data-stu-id="15ae7-107">For example, many controls let you set the color of the text that is displayed, but you are limited to a single color.</span></span> <span data-ttu-id="15ae7-108">Kreslení vlastníka můžete třeba zobrazit část textu v černé a část červeně.</span><span class="sxs-lookup"><span data-stu-id="15ae7-108">Owner drawing enables you to do things like display part of the text in black and part in red.</span></span>  
  
 <span data-ttu-id="15ae7-109">V praxi se podobá vykreslování grafiky ve formuláři vykreslení vlastníka.</span><span class="sxs-lookup"><span data-stu-id="15ae7-109">In practice, owner drawing is similar to drawing graphics on a form.</span></span> <span data-ttu-id="15ae7-110">Například můžete použít grafické metody v obslužné rutině pro daný formulář <xref:System.Windows.Forms.Control.Paint> událostí k emulaci `ListBox` ovládacího prvku, ale byste museli napsat vlastní kód pro zpracování všechny interakce s uživatelem.</span><span class="sxs-lookup"><span data-stu-id="15ae7-110">For example, you could use graphics methods in a handler for the form's <xref:System.Windows.Forms.Control.Paint> event to emulate a `ListBox` control, but you would have to write your own code to handle all user interaction.</span></span> <span data-ttu-id="15ae7-111">Pomocí vykreslení vlastníka ovládací prvek nakreslit jeho obsah pomocí kódu, ale jinak uchovává všechny vnitřní funkce.</span><span class="sxs-lookup"><span data-stu-id="15ae7-111">With owner drawing, the control uses your code to draw its contents but otherwise retains all its intrinsic capabilities.</span></span> <span data-ttu-id="15ae7-112">Metody grafiky můžete použít k vykreslení každou položku v ovládacím prvku nebo přizpůsobit některé aspekty každou položku, když použijete výchozí vzhled jiných aspektů každé položky.</span><span class="sxs-lookup"><span data-stu-id="15ae7-112">You can use graphics methods to draw each item in the control or to customize some aspects of each item while you use the default appearance for other aspects of each item.</span></span>  
  
## <a name="owner-drawing-in-windows-forms-controls"></a><span data-ttu-id="15ae7-113">Kreslení vlastníka ve Windows Forms ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="15ae7-113">Owner Drawing in Windows Forms Controls</span></span>  
 <span data-ttu-id="15ae7-114">K provedení vlastníka kreslení v ovládacích prvcích, které ho podporují, bude obvykle jednu vlastnost a zpracovat jeden nebo více událostí.</span><span class="sxs-lookup"><span data-stu-id="15ae7-114">To perform owner drawing in controls that support it, you will typically set one property and handle one or more events.</span></span>  
  
 <span data-ttu-id="15ae7-115">Většina ovládací prvky mají tento vlastník podporu kreslení `OwnerDraw` nebo `DrawMode` vlastnost, která označuje, zda ovládací prvek vyvolá jeho události související s kreslení nebo události, kdy ho jsou vykreslovány samotný.</span><span class="sxs-lookup"><span data-stu-id="15ae7-115">Most controls that support owner drawing have an `OwnerDraw` or `DrawMode` property that indicates whether the control will raise its drawing-related event or events when it paints itself.</span></span>  
  
 <span data-ttu-id="15ae7-116">Ovládací prvky, které nemají `OwnerDraw` nebo `DrawMode` zahrnují vlastnosti `DataGridView` ovládací prvek, který poskytuje výkresu události, které se automaticky provedou, a `ToolStrip` ovládací prvek, který je vykreslen třídu externí vykreslování, který má vlastní Kreslení související události.</span><span class="sxs-lookup"><span data-stu-id="15ae7-116">Controls that do not have an `OwnerDraw` or `DrawMode` property include the `DataGridView` control, which provides drawing events that occur automatically, and the `ToolStrip` control, which is drawn using an external rendering class that has its own drawing-related events.</span></span>  
  
 <span data-ttu-id="15ae7-117">Existuje mnoho různých druhů kreslení události, ale typické výkresu události dojde k vykreslení jednu položku v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="15ae7-117">There are many different kinds of drawing events, but a typical drawing event occurs in order to draw a single item within a control.</span></span> <span data-ttu-id="15ae7-118">Obslužná rutina události obdrží `EventArgs` objekt, který obsahuje informace o položkách, které je cílem vykreslování a nástrojích, které můžete použít k vykreslení ho.</span><span class="sxs-lookup"><span data-stu-id="15ae7-118">The event handler receives an `EventArgs` object that contains information about the item being drawn and tools you can use to draw it.</span></span> <span data-ttu-id="15ae7-119">Například tento objekt obvykle obsahuje položky číslo indexu v rámci kolekce jeho nadřazených prvků <xref:System.Drawing.Rectangle> , který určuje položky zobrazit hranice a <xref:System.Drawing.Graphics> objekt pro volání metod Malování.</span><span class="sxs-lookup"><span data-stu-id="15ae7-119">For example, this object typically contains the item's index number within its parent collection, a <xref:System.Drawing.Rectangle> that indicates the item's display boundaries, and a <xref:System.Drawing.Graphics> object for calling paint methods.</span></span> <span data-ttu-id="15ae7-120">Pro některé události `EventArgs` objekt poskytuje další informace o položky a metody, které můžete volat za účelem vykreslení některé aspekty položky ve výchozím nastavení, jako je například na pozadí nebo rámečku fokusu.</span><span class="sxs-lookup"><span data-stu-id="15ae7-120">For some events, the `EventArgs` object provides additional information about the item and methods that you can call to paint some aspects of the item by default, such as the background or a focus rectangle.</span></span>  
  
 <span data-ttu-id="15ae7-121">Vytvoření opakovaně použitelné ovládací prvek, který obsahuje vaše vlastní nastavení vykreslovaných vlastníkem, vytvořte novou třídu, která je odvozena z třídy ovládacího prvku, který podporuje vykreslení vlastníka.</span><span class="sxs-lookup"><span data-stu-id="15ae7-121">To create a reusable control that contains your owner-drawn customizations, create a new class that derives from a control class that supports owner drawing.</span></span> <span data-ttu-id="15ae7-122">Namísto zpracování událostí výkresu, zahrnout kód vykreslování vlastníkem přepsání pro odpovídající `On` *EventName* metodu nebo metody v této nové třídě.</span><span class="sxs-lookup"><span data-stu-id="15ae7-122">Rather than handling drawing events, include your owner-drawing code in overrides for the appropriate `On`*EventName* method or methods in the new class.</span></span> <span data-ttu-id="15ae7-123">Ujistěte se, že můžete volat základní třídy `On` *EventName* metodu nebo metody v tomto případě tak, aby uživatelé ovládacího prvku může zpracovávat události vykreslování vlastníkem a poskytují líp přizpůsobte.</span><span class="sxs-lookup"><span data-stu-id="15ae7-123">Make sure that you call the base class `On`*EventName* method or methods in this case so that users of your control can handle owner-drawing events and provide additional customization.</span></span>  
  
 <span data-ttu-id="15ae7-124">Následující Windows Forms – ovládací prvky podporu vlastníka kreslení ve všech verzích rozhraní .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="15ae7-124">The following Windows Forms controls support owner drawing in all versions of the .NET Framework:</span></span>  
  
-   <xref:System.Windows.Forms.ListBox>  
  
-   <xref:System.Windows.Forms.ComboBox>  
  
-   <span data-ttu-id="15ae7-125"><xref:System.Windows.Forms.MenuItem> (používají <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu>)</span><span class="sxs-lookup"><span data-stu-id="15ae7-125"><xref:System.Windows.Forms.MenuItem> (used by <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu>)</span></span>  
  
-   <xref:System.Windows.Forms.TabControl>  
  
 <span data-ttu-id="15ae7-126">Vlastník kreslení pouze v podporují následující ovládací prvky [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="15ae7-126">The following controls support owner drawing only in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:</span></span>  
  
-   <xref:System.Windows.Forms.ToolTip>  
  
-   <xref:System.Windows.Forms.ListView>  
  
-   <xref:System.Windows.Forms.TreeView>  
  
 <span data-ttu-id="15ae7-127">Následující ovládací prvky podporují kreslení vlastníka a jsou novinkou [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="15ae7-127">The following controls support owner drawing and are new in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridView>  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
 <span data-ttu-id="15ae7-128">Následující části obsahují další podrobnosti pro každou z těchto ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="15ae7-128">The following sections provide additional details for each of these controls.</span></span>  
  
### <a name="listbox-and-combobox-controls"></a><span data-ttu-id="15ae7-129">ListBox – a ovládací prvky pole se seznamem</span><span class="sxs-lookup"><span data-stu-id="15ae7-129">ListBox and ComboBox Controls</span></span>  
 <span data-ttu-id="15ae7-130"><xref:System.Windows.Forms.ListBox> a <xref:System.Windows.Forms.ComboBox> ovládací prvky umožňují nakreslete jednotlivých položek v ovládacím prvku vše na velikosti, nebo v různých velikostí.</span><span class="sxs-lookup"><span data-stu-id="15ae7-130">The <xref:System.Windows.Forms.ListBox> and <xref:System.Windows.Forms.ComboBox> controls enable you to draw individual items in the control either all in one size, or in varying sizes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15ae7-131">I když <xref:System.Windows.Forms.CheckedListBox> ovládací prvek je odvozený z <xref:System.Windows.Forms.ListBox> ovládacího prvku, a proto není podporována vykreslení vlastníka.</span><span class="sxs-lookup"><span data-stu-id="15ae7-131">Although the <xref:System.Windows.Forms.CheckedListBox> control is derived from the <xref:System.Windows.Forms.ListBox> control, it does not support owner drawing.</span></span>  
  
 <span data-ttu-id="15ae7-132">Chcete-li nakreslit každou položku se stejnou velikostí, nastavte `DrawMode` vlastnost <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> a zpracovat `DrawItem` událostí.</span><span class="sxs-lookup"><span data-stu-id="15ae7-132">To draw each item the same size, set the `DrawMode` property to <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> and handle the `DrawItem` event.</span></span>  
  
 <span data-ttu-id="15ae7-133">Chcete-li nakreslit každou položku pomocí různých velikostí, nastavte `DrawMode` vlastnost <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> a zpracovat oba `MeasureItem` a `DrawItem` události.</span><span class="sxs-lookup"><span data-stu-id="15ae7-133">To draw each item using a different size, set the `DrawMode` property to <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> and handle both the `MeasureItem` and `DrawItem` events.</span></span> <span data-ttu-id="15ae7-134">`MeasureItem` Událostí umožňuje určit velikost položky před `DrawItem` dojde k události pro danou položku.</span><span class="sxs-lookup"><span data-stu-id="15ae7-134">The `MeasureItem` event lets you indicate the size of an item before the `DrawItem` event occurs for that item.</span></span>  
  
 <span data-ttu-id="15ae7-135">Další informace, včetně příkladů kódu naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="15ae7-135">For more information, including code examples, see the following topics:</span></span>  
  
-   <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=nameWithType>  
  
-   [<span data-ttu-id="15ae7-136">Postupy: Vytvoření textu proměnlivé velikosti v ovládacím prvku ComboBox</span><span class="sxs-lookup"><span data-stu-id="15ae7-136">How to: Create Variable Sized Text in a ComboBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a><span data-ttu-id="15ae7-137">Komponenta položku nabídky</span><span class="sxs-lookup"><span data-stu-id="15ae7-137">MenuItem Component</span></span>  
 <span data-ttu-id="15ae7-138"><xref:System.Windows.Forms.MenuItem> Představuje samostatnou položku nabídky v součásti <xref:System.Windows.Forms.MainMenu> nebo <xref:System.Windows.Forms.ContextMenu> komponenty.</span><span class="sxs-lookup"><span data-stu-id="15ae7-138">The <xref:System.Windows.Forms.MenuItem> component represents a single menu item in a <xref:System.Windows.Forms.MainMenu> or <xref:System.Windows.Forms.ContextMenu> component.</span></span>  
  
 <span data-ttu-id="15ae7-139">Chcete-li nakreslit <xref:System.Windows.Forms.MenuItem>, nastavte jeho `OwnerDraw` vlastnost `true` a zpracovat jeho `DrawItem` událostí.</span><span class="sxs-lookup"><span data-stu-id="15ae7-139">To draw a <xref:System.Windows.Forms.MenuItem>, set its `OwnerDraw` property to `true` and handle its `DrawItem` event.</span></span> <span data-ttu-id="15ae7-140">Chcete-li přizpůsobit velikost položky nabídky před `DrawItem` dojde k události, zpracování položky `MeasureItem` událostí.</span><span class="sxs-lookup"><span data-stu-id="15ae7-140">To customize the size of the menu item before the `DrawItem` event occurs, handle the item's `MeasureItem` event.</span></span>  
  
 <span data-ttu-id="15ae7-141">Další informace, včetně příkladů kódu naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="15ae7-141">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=nameWithType>  
  
### <a name="tabcontrol-control"></a><span data-ttu-id="15ae7-142">TabControl – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="15ae7-142">TabControl Control</span></span>  
 <span data-ttu-id="15ae7-143"><xref:System.Windows.Forms.TabControl> Ovládací prvek umožňuje nakreslit jednotlivé karty v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="15ae7-143">The <xref:System.Windows.Forms.TabControl> control enables you to draw individual tabs in the control.</span></span> <span data-ttu-id="15ae7-144">Kreslení vlastníka má vliv pouze na karty; <xref:System.Windows.Forms.TabPage> obsah to nebude mít vliv.</span><span class="sxs-lookup"><span data-stu-id="15ae7-144">Owner drawing affects only the tabs; the <xref:System.Windows.Forms.TabPage> contents are not affected.</span></span>  
  
 <span data-ttu-id="15ae7-145">Chcete-li nakreslit každá karta <xref:System.Windows.Forms.TabControl>, nastavte `DrawMode` vlastnost <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> a zpracování `DrawItem` událostí.</span><span class="sxs-lookup"><span data-stu-id="15ae7-145">To draw each tab in a <xref:System.Windows.Forms.TabControl>, set the `DrawMode` property to <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> and handle the `DrawItem` event.</span></span> <span data-ttu-id="15ae7-146">Tato událost akce proběhne jednou pro každou kartu pouze v případě, že na kartě zobrazený v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="15ae7-146">This event occurs once for each tab only when the tab is visible in the control.</span></span>  
  
 <span data-ttu-id="15ae7-147">Další informace, včetně příkladů kódu naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="15ae7-147">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=nameWithType>  
  
### <a name="tooltip-component"></a><span data-ttu-id="15ae7-148">ToolTip – komponenta</span><span class="sxs-lookup"><span data-stu-id="15ae7-148">ToolTip Component</span></span>  
 <span data-ttu-id="15ae7-149"><xref:System.Windows.Forms.ToolTip> Komponenty umožňuje nakreslit celý popis, jakmile se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="15ae7-149">The <xref:System.Windows.Forms.ToolTip> component enables you to draw the entire ToolTip when it is displayed.</span></span>  
  
 <span data-ttu-id="15ae7-150">Chcete-li nakreslit <xref:System.Windows.Forms.ToolTip>, nastavte jeho `OwnerDraw` vlastnost `true` a zpracovat jeho `Draw` událostí.</span><span class="sxs-lookup"><span data-stu-id="15ae7-150">To draw a <xref:System.Windows.Forms.ToolTip>, set its `OwnerDraw` property to `true` and handle its `Draw` event.</span></span> <span data-ttu-id="15ae7-151">Přizpůsobit velikost <xref:System.Windows.Forms.ToolTip> před `Draw` dojde k události, zpracování `Popup` událostí a nastavte <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> vlastnost v obslužné rutině události.</span><span class="sxs-lookup"><span data-stu-id="15ae7-151">To customize the size of the <xref:System.Windows.Forms.ToolTip> before the `Draw` event occurs, handle the `Popup` event and set the <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> property in the event handler.</span></span>  
  
 <span data-ttu-id="15ae7-152">Další informace, včetně příkladů kódu naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="15ae7-152">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=nameWithType>  
  
### <a name="listview-control"></a><span data-ttu-id="15ae7-153">ListView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="15ae7-153">ListView Control</span></span>  
 <span data-ttu-id="15ae7-154"><xref:System.Windows.Forms.ListView> Ovládací prvek umožňuje nakreslit jednotlivých položek, podřízené položky a záhlaví sloupců v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="15ae7-154">The <xref:System.Windows.Forms.ListView> control enables you to draw individual items, subitems, and column headers in the control.</span></span>  
  
 <span data-ttu-id="15ae7-155">Pokud chcete povolit vlastníka výkres v ovládacím prvku, nastavte `OwnerDraw` vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="15ae7-155">To enable owner drawing in the control, set the `OwnerDraw` property to `true`.</span></span>  
  
 <span data-ttu-id="15ae7-156">Chcete-li nakreslit každou položku v ovládacím prvku, zpracovat `DrawItem` událostí.</span><span class="sxs-lookup"><span data-stu-id="15ae7-156">To draw each item in the control, handle the `DrawItem` event.</span></span>  
  
 <span data-ttu-id="15ae7-157">Chcete-li nakreslit záhlaví každého sloupce nebo podřízenou položku v ovládacím prvku při <xref:System.Windows.Forms.ListView.View%2A> je nastavena na <xref:System.Windows.Forms.View.Details>, zpracovat `DrawSubItem` a `DrawColumnHeader` události.</span><span class="sxs-lookup"><span data-stu-id="15ae7-157">To draw each subitem or column header in the control when the <xref:System.Windows.Forms.ListView.View%2A> property is set to <xref:System.Windows.Forms.View.Details>, handle the `DrawSubItem` and `DrawColumnHeader` events.</span></span>  
  
 <span data-ttu-id="15ae7-158">Další informace, včetně příkladů kódu naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="15ae7-158">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=nameWithType>  
  
### <a name="treeview-control"></a><span data-ttu-id="15ae7-159">TreeView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="15ae7-159">TreeView Control</span></span>  
 <span data-ttu-id="15ae7-160"><xref:System.Windows.Forms.TreeView> Ovládací prvek umožňuje nakreslit jednotlivé uzly v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="15ae7-160">The <xref:System.Windows.Forms.TreeView> control enables you to draw individual nodes in the control.</span></span>  
  
 <span data-ttu-id="15ae7-161">Chcete-li nakreslit pouze text zobrazený v každém uzlu, nastavte `DrawMode` vlastnost <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> a zpracovat `DrawNode` události vykreslování textu.</span><span class="sxs-lookup"><span data-stu-id="15ae7-161">To draw only the text displayed in each node, set the `DrawMode` property to <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> and handle the `DrawNode` event to draw the text.</span></span>  
  
 <span data-ttu-id="15ae7-162">Chcete-li nakreslit všechny prvky každého uzlu, nastavte `DrawMode` vlastnost <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> a zpracovat `DrawNode` událost k vykreslení elementů, podle toho, která budete potřebovat, jako například text, ikony, zaškrtněte políčka, plus a minus a čáry spojující uzly.</span><span class="sxs-lookup"><span data-stu-id="15ae7-162">To draw all elements of each node, set the `DrawMode` property to <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> and handle the `DrawNode` event to draw whichever elements you need, such as text, icons, check boxes, plus and minus signs, and lines connecting the nodes.</span></span>  
  
 <span data-ttu-id="15ae7-163">Další informace, včetně příkladů kódu naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="15ae7-163">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=nameWithType>  
  
### <a name="datagridview-control"></a><span data-ttu-id="15ae7-164">DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="15ae7-164">DataGridView Control</span></span>  
 <span data-ttu-id="15ae7-165"><xref:System.Windows.Forms.DataGridView> Ovládací prvek umožňuje nakreslit jednotlivé buňky a řádků v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="15ae7-165">The <xref:System.Windows.Forms.DataGridView> control enables you to draw individual cells and rows in the control.</span></span>  
  
 <span data-ttu-id="15ae7-166">Chcete-li nakreslit jednotlivé buňky, zpracovat `CellPainting` událostí.</span><span class="sxs-lookup"><span data-stu-id="15ae7-166">To draw individual cells, handle the `CellPainting` event.</span></span>  
  
 <span data-ttu-id="15ae7-167">Chcete-li nakreslit jednotlivé řádky nebo řádků, zpracovat jeden nebo oba `RowPrePaint` a `RowPostPaint` události.</span><span class="sxs-lookup"><span data-stu-id="15ae7-167">To draw individual rows or elements of rows, handle one or both of the `RowPrePaint` and `RowPostPaint` events.</span></span> <span data-ttu-id="15ae7-168">`RowPrePaint` Předtím, než jsou překreslit buňky v řádku, dojde k události a `RowPostPaint` po buňky jsou překreslit dojde k události.</span><span class="sxs-lookup"><span data-stu-id="15ae7-168">The `RowPrePaint` event occurs before the cells in a row are painted, and the `RowPostPaint` event occurs after the cells are painted.</span></span> <span data-ttu-id="15ae7-169">Dokáže zpracovat oba události a `CellPainting` událost k vykreslení pozadí řádku, jednotlivé buňky a řádek popředí samostatně, nebo můžete zadat konkrétní přizpůsobení, kde je potřebujete a použijte výchozí zobrazení pro další prvky řádku.</span><span class="sxs-lookup"><span data-stu-id="15ae7-169">You can handle both events and the `CellPainting` event to paint row background, individual cells, and row foreground separately, or you can provide specific customizations where you need them and use the default display for other elements of the row.</span></span>  
  
 <span data-ttu-id="15ae7-170">Další informace, včetně příkladů kódu naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="15ae7-170">For more information, including code examples, see the following topics:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
-   [<span data-ttu-id="15ae7-171">Postupy: Přizpůsobení vzhledu buněk v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="15ae7-171">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)  
  
-   [<span data-ttu-id="15ae7-172">Postupy: Přizpůsobení vzhledu řádků v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="15ae7-172">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a><span data-ttu-id="15ae7-173">ToolStrip – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="15ae7-173">ToolStrip Control</span></span>  
 <span data-ttu-id="15ae7-174"><xref:System.Windows.Forms.ToolStrip> a odvozené ovládací prvky umožňují přizpůsobit jiného aspektu jejich výskytu.</span><span class="sxs-lookup"><span data-stu-id="15ae7-174"><xref:System.Windows.Forms.ToolStrip> and derived controls enable you to customize any aspect of their appearance.</span></span>  
  
 <span data-ttu-id="15ae7-175">Poskytnout vlastní vykreslování pro <xref:System.Windows.Forms.ToolStrip> ovládací prvky, nastavit `Renderer` vlastnost <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, nebo <xref:System.Windows.Forms.ToolStripContentPanel> k `ToolStripRenderer` objektu a zpracovat jeden nebo více mnoho událostí výkresu poskytované `ToolStripRenderer` třídy.</span><span class="sxs-lookup"><span data-stu-id="15ae7-175">To provide custom rendering for <xref:System.Windows.Forms.ToolStrip> controls, set the `Renderer` property of a <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, or <xref:System.Windows.Forms.ToolStripContentPanel> to a `ToolStripRenderer` object and handle one or more of the many drawing events provided by the `ToolStripRenderer` class.</span></span> <span data-ttu-id="15ae7-176">Můžete také nastavit `Renderer` vlastnost instance vlastní třídy odvozené z `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, nebo <xref:System.Windows.Forms.ToolStripSystemRenderer> , který implementuje nebo přepíše konkrétní `On` *EventName* metody.</span><span class="sxs-lookup"><span data-stu-id="15ae7-176">Alternatively, set a `Renderer` property to an instance of your own class derived from `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, or <xref:System.Windows.Forms.ToolStripSystemRenderer> that implements or overrides specific `On`*EventName* methods.</span></span>  
  
 <span data-ttu-id="15ae7-177">Další informace, včetně příkladů kódu naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="15ae7-177">For more information, including code examples, see the following topics:</span></span>  
  
-   <xref:System.Windows.Forms.ToolStripRenderer>  
  
-   [<span data-ttu-id="15ae7-178">Postupy: Vytvoření a nastavení vlastního Rendereru pro ovládací prvek ToolStrip ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="15ae7-178">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
-   [<span data-ttu-id="15ae7-179">Postupy: Vlastní vykreslení ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="15ae7-179">How to: Custom Draw a ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a><span data-ttu-id="15ae7-180">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15ae7-180">See also</span></span>
- [<span data-ttu-id="15ae7-181">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="15ae7-181">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
