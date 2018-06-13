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
ms.openlocfilehash: a5cbdc733a2f1cda3e708ceaae8604297f8da58a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529244"
---
# <a name="controls-with-built-in-owner-drawing-support"></a><span data-ttu-id="9e47e-102">Ovládací prvky s vestavěnou podporou vykreslování vlastníkem</span><span class="sxs-lookup"><span data-stu-id="9e47e-102">Controls with Built-In Owner-Drawing Support</span></span>
<span data-ttu-id="9e47e-103">Kreslení v systému Windows Forms, který je také označován jako vlastní kreslení, vlastníka je technika pro změnu vzhled určitých ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="9e47e-103">Owner drawing in Windows Forms, which is also known as custom drawing, is a technique for changing the visual appearance of certain controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e47e-104">Slovo "řízení" v tomto tématu se používá k označení třídy, které jsou odvozeny od buď <xref:System.Windows.Forms.Control> nebo <xref:System.ComponentModel.Component>.</span><span class="sxs-lookup"><span data-stu-id="9e47e-104">The word "control" in this topic is used to mean classes that derive from either <xref:System.Windows.Forms.Control> or <xref:System.ComponentModel.Component>.</span></span>  
  
 <span data-ttu-id="9e47e-105">Obvykle Windows zpracovává Malování automaticky pomocí nastavení vlastností, jako <xref:System.Windows.Forms.Control.BackColor%2A> k určení vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9e47e-105">Typically, Windows handles painting automatically by using property settings such as <xref:System.Windows.Forms.Control.BackColor%2A> to determine the appearance of a control.</span></span> <span data-ttu-id="9e47e-106">Kreslení vlastníka můžete provést nad tímto procesem Malování Změna vzhledu prvky, které nejsou k dispozici pomocí vlastností.</span><span class="sxs-lookup"><span data-stu-id="9e47e-106">With owner drawing, you take over the painting process, changing elements of appearance that are not available by using properties.</span></span> <span data-ttu-id="9e47e-107">Například mnoho ovládací prvky umožňují nastavit barvu textu, který se zobrazí, ale jste omezeni na jedné barvy.</span><span class="sxs-lookup"><span data-stu-id="9e47e-107">For example, many controls let you set the color of the text that is displayed, but you are limited to a single color.</span></span> <span data-ttu-id="9e47e-108">Kreslení vlastníka můžete například zobrazit část textu v černé a část červeně.</span><span class="sxs-lookup"><span data-stu-id="9e47e-108">Owner drawing enables you to do things like display part of the text in black and part in red.</span></span>  
  
 <span data-ttu-id="9e47e-109">V praxi je podobný jako při kreslení grafiky ve formuláři kreslení vlastníka.</span><span class="sxs-lookup"><span data-stu-id="9e47e-109">In practice, owner drawing is similar to drawing graphics on a form.</span></span> <span data-ttu-id="9e47e-110">Například můžete použít metody grafiky v obslužnou rutinu pro daný formulář <xref:System.Windows.Forms.Control.Paint> událostí emulovat `ListBox` řízení, ale muset napsat vlastní kód pro zpracování všechny interakce s uživatelem.</span><span class="sxs-lookup"><span data-stu-id="9e47e-110">For example, you could use graphics methods in a handler for the form's <xref:System.Windows.Forms.Control.Paint> event to emulate a `ListBox` control, but you would have to write your own code to handle all user interaction.</span></span> <span data-ttu-id="9e47e-111">S kreslení vlastníka ovládacího prvku používá kódu kreslení její obsah, ale jinak uchovává všechny vlastní možnosti.</span><span class="sxs-lookup"><span data-stu-id="9e47e-111">With owner drawing, the control uses your code to draw its contents but otherwise retains all its intrinsic capabilities.</span></span> <span data-ttu-id="9e47e-112">Grafické metody můžete použít k vykreslení jednotlivých položek v ovládacím prvku nebo chcete-li přizpůsobit některé aspekty každé položky při používat výchozí vzhled pro další aspekty každé položky.</span><span class="sxs-lookup"><span data-stu-id="9e47e-112">You can use graphics methods to draw each item in the control or to customize some aspects of each item while you use the default appearance for other aspects of each item.</span></span>  
  
## <a name="owner-drawing-in-windows-forms-controls"></a><span data-ttu-id="9e47e-113">Kreslení vlastníka ve Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="9e47e-113">Owner Drawing in Windows Forms Controls</span></span>  
 <span data-ttu-id="9e47e-114">K provedení vlastníka kreslení v ovládacích prvcích, které ji podporují, se obvykle nastavit jednu vlastnost a zpracovat jeden nebo více událostí.</span><span class="sxs-lookup"><span data-stu-id="9e47e-114">To perform owner drawing in controls that support it, you will typically set one property and handle one or more events.</span></span>  
  
 <span data-ttu-id="9e47e-115">Většina ovládacích prvků kreslení vlastníka tohoto podporu má `OwnerDraw` nebo `DrawMode` vlastnost, která určuje, zda bude ovládací prvek zvýšit jeho kreslení související události nebo událostí v případě, že ho vybarví sám sebe.</span><span class="sxs-lookup"><span data-stu-id="9e47e-115">Most controls that support owner drawing have an `OwnerDraw` or `DrawMode` property that indicates whether the control will raise its drawing-related event or events when it paints itself.</span></span>  
  
 <span data-ttu-id="9e47e-116">Ovládací prvky, které nemají `OwnerDraw` nebo `DrawMode` vlastnost, zahrnout `DataGridView` řízení, které poskytuje kreslení události, které se automaticky provedou, a `ToolStrip` řízení, které je vykresleno pomocí třídu externí vykreslování, který má svou vlastní Kreslení související události.</span><span class="sxs-lookup"><span data-stu-id="9e47e-116">Controls that do not have an `OwnerDraw` or `DrawMode` property include the `DataGridView` control, which provides drawing events that occur automatically, and the `ToolStrip` control, which is drawn using an external rendering class that has its own drawing-related events.</span></span>  
  
 <span data-ttu-id="9e47e-117">Existuje mnoho různých druhů kreslení události, avšak typické kreslení události dojde k vykreslení jednu položku v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="9e47e-117">There are many different kinds of drawing events, but a typical drawing event occurs in order to draw a single item within a control.</span></span> <span data-ttu-id="9e47e-118">Obslužné rutiny události obdrží `EventArgs` objekt, který obsahuje informace o položce přitahuje a nástroje, které můžete použít k vykreslení ho.</span><span class="sxs-lookup"><span data-stu-id="9e47e-118">The event handler receives an `EventArgs` object that contains information about the item being drawn and tools you can use to draw it.</span></span> <span data-ttu-id="9e47e-119">Například tento objekt obsahuje obvykle číslo indexu položky v rámci jeho kolekce nadřazených <xref:System.Drawing.Rectangle> určující položky zobrazit hranice a <xref:System.Drawing.Graphics> objekt pro volání metod Malování.</span><span class="sxs-lookup"><span data-stu-id="9e47e-119">For example, this object typically contains the item's index number within its parent collection, a <xref:System.Drawing.Rectangle> that indicates the item's display boundaries, and a <xref:System.Drawing.Graphics> object for calling paint methods.</span></span> <span data-ttu-id="9e47e-120">Pro některé události `EventArgs` objekt poskytuje další informace o položky a metody, které můžete volat k vyplnění některé aspekty položky ve výchozím nastavení, jako je například na pozadí nebo rámečku fokusu.</span><span class="sxs-lookup"><span data-stu-id="9e47e-120">For some events, the `EventArgs` object provides additional information about the item and methods that you can call to paint some aspects of the item by default, such as the background or a focus rectangle.</span></span>  
  
 <span data-ttu-id="9e47e-121">Pokud chcete vytvořit opakovaně použitelný ovládací prvek, který obsahuje vlastní nastavení vykreslovaných vlastníkem, vytvořte novou třídu odvozenou z ovládacího prvku třídu, která podporuje kreslení vlastníka.</span><span class="sxs-lookup"><span data-stu-id="9e47e-121">To create a reusable control that contains your owner-drawn customizations, create a new class that derives from a control class that supports owner drawing.</span></span> <span data-ttu-id="9e47e-122">Místo zpracování kreslení událostí, zahrnout kódu vykreslování vlastníkem přepsání pro příslušné `On` *EventName* metodu nebo metody ve třídě nové.</span><span class="sxs-lookup"><span data-stu-id="9e47e-122">Rather than handling drawing events, include your owner-drawing code in overrides for the appropriate `On`*EventName* method or methods in the new class.</span></span> <span data-ttu-id="9e47e-123">Ujistěte se, že zavoláte základní třídy `On` *EventName* metodu nebo metody v tomto případě tak, aby uživatelé ovládacího prvku zpracování vykreslování vlastníkem událostí a poskytnout další přizpůsobení.</span><span class="sxs-lookup"><span data-stu-id="9e47e-123">Make sure that you call the base class `On`*EventName* method or methods in this case so that users of your control can handle owner-drawing events and provide additional customization.</span></span>  
  
 <span data-ttu-id="9e47e-124">Následující Windows Forms – ovládací prvky kreslení ve všech verzích rozhraní .NET Framework vlastníka podpory:</span><span class="sxs-lookup"><span data-stu-id="9e47e-124">The following Windows Forms controls support owner drawing in all versions of the .NET Framework:</span></span>  
  
-   <xref:System.Windows.Forms.ListBox>  
  
-   <xref:System.Windows.Forms.ComboBox>  
  
-   <span data-ttu-id="9e47e-125"><xref:System.Windows.Forms.MenuItem> (používané <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu>)</span><span class="sxs-lookup"><span data-stu-id="9e47e-125"><xref:System.Windows.Forms.MenuItem> (used by <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu>)</span></span>  
  
-   <xref:System.Windows.Forms.TabControl>  
  
 <span data-ttu-id="9e47e-126">Ovládací prvky podporují pouze v kreslení vlastníka [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="9e47e-126">The following controls support owner drawing only in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:</span></span>  
  
-   <xref:System.Windows.Forms.ToolTip>  
  
-   <xref:System.Windows.Forms.ListView>  
  
-   <xref:System.Windows.Forms.TreeView>  
  
 <span data-ttu-id="9e47e-127">Ovládací prvky podporují kreslení vlastníka a jsou v nové [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="9e47e-127">The following controls support owner drawing and are new in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridView>  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
 <span data-ttu-id="9e47e-128">Následující části obsahují další podrobnosti pro každou z těchto ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="9e47e-128">The following sections provide additional details for each of these controls.</span></span>  
  
### <a name="listbox-and-combobox-controls"></a><span data-ttu-id="9e47e-129">ListBox – a ComboBox – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="9e47e-129">ListBox and ComboBox Controls</span></span>  
 <span data-ttu-id="9e47e-130"><xref:System.Windows.Forms.ListBox> a <xref:System.Windows.Forms.ComboBox> ovládací prvky umožňují kreslení jednotlivé položky v ovládacím prvku všechno ve velikosti nebo v různou velikost.</span><span class="sxs-lookup"><span data-stu-id="9e47e-130">The <xref:System.Windows.Forms.ListBox> and <xref:System.Windows.Forms.ComboBox> controls enable you to draw individual items in the control either all in one size, or in varying sizes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e47e-131">I když <xref:System.Windows.Forms.CheckedListBox> ovládací prvek je odvozený od <xref:System.Windows.Forms.ListBox> řízení, nepodporuje kreslení vlastníka.</span><span class="sxs-lookup"><span data-stu-id="9e47e-131">Although the <xref:System.Windows.Forms.CheckedListBox> control is derived from the <xref:System.Windows.Forms.ListBox> control, it does not support owner drawing.</span></span>  
  
 <span data-ttu-id="9e47e-132">Kreslení každou položku stejnou velikost, nastavte `DrawMode` vlastnost, která má <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> a zpracovat `DrawItem` událostí.</span><span class="sxs-lookup"><span data-stu-id="9e47e-132">To draw each item the same size, set the `DrawMode` property to <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> and handle the `DrawItem` event.</span></span>  
  
 <span data-ttu-id="9e47e-133">Kreslení každou položku pomocí různých velikostí, nastavte `DrawMode` vlastnost <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> a zpracovat oba `MeasureItem` a `DrawItem` události.</span><span class="sxs-lookup"><span data-stu-id="9e47e-133">To draw each item using a different size, set the `DrawMode` property to <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> and handle both the `MeasureItem` and `DrawItem` events.</span></span> <span data-ttu-id="9e47e-134">`MeasureItem` Událostí umožňuje určit velikost položky před `DrawItem` této položky dojde k události.</span><span class="sxs-lookup"><span data-stu-id="9e47e-134">The `MeasureItem` event lets you indicate the size of an item before the `DrawItem` event occurs for that item.</span></span>  
  
 <span data-ttu-id="9e47e-135">Další informace, včetně příkladů kódu naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="9e47e-135">For more information, including code examples, see the following topics:</span></span>  
  
-   <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=nameWithType>  
  
-   [<span data-ttu-id="9e47e-136">Postupy: Vytvoření textu proměnlivé velikosti v ovládacím prvku ComboBox</span><span class="sxs-lookup"><span data-stu-id="9e47e-136">How to: Create Variable Sized Text in a ComboBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a><span data-ttu-id="9e47e-137">Součást MenuItem</span><span class="sxs-lookup"><span data-stu-id="9e47e-137">MenuItem Component</span></span>  
 <span data-ttu-id="9e47e-138"><xref:System.Windows.Forms.MenuItem> Představuje samostatnou položku nabídky v součásti <xref:System.Windows.Forms.MainMenu> nebo <xref:System.Windows.Forms.ContextMenu> součásti.</span><span class="sxs-lookup"><span data-stu-id="9e47e-138">The <xref:System.Windows.Forms.MenuItem> component represents a single menu item in a <xref:System.Windows.Forms.MainMenu> or <xref:System.Windows.Forms.ContextMenu> component.</span></span>  
  
 <span data-ttu-id="9e47e-139">Kreslení <xref:System.Windows.Forms.MenuItem>, nastavte jeho `OwnerDraw` vlastnost `true` a zpracovat jeho `DrawItem` událostí.</span><span class="sxs-lookup"><span data-stu-id="9e47e-139">To draw a <xref:System.Windows.Forms.MenuItem>, set its `OwnerDraw` property to `true` and handle its `DrawItem` event.</span></span> <span data-ttu-id="9e47e-140">Chcete-li přizpůsobit velikost položky nabídky před `DrawItem` události dojde, zpracování položky `MeasureItem` událostí.</span><span class="sxs-lookup"><span data-stu-id="9e47e-140">To customize the size of the menu item before the `DrawItem` event occurs, handle the item's `MeasureItem` event.</span></span>  
  
 <span data-ttu-id="9e47e-141">Další informace, včetně příkladů kódu najdete v těchto tématech:</span><span class="sxs-lookup"><span data-stu-id="9e47e-141">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=nameWithType>  
  
### <a name="tabcontrol-control"></a><span data-ttu-id="9e47e-142">TabControl – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="9e47e-142">TabControl Control</span></span>  
 <span data-ttu-id="9e47e-143"><xref:System.Windows.Forms.TabControl> Řízení umožňuje kreslení jednotlivé karty v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="9e47e-143">The <xref:System.Windows.Forms.TabControl> control enables you to draw individual tabs in the control.</span></span> <span data-ttu-id="9e47e-144">Kreslení vlastníka ovlivňuje pouze karty; <xref:System.Windows.Forms.TabPage> obsah neovlivní.</span><span class="sxs-lookup"><span data-stu-id="9e47e-144">Owner drawing affects only the tabs; the <xref:System.Windows.Forms.TabPage> contents are not affected.</span></span>  
  
 <span data-ttu-id="9e47e-145">Kreslení každé kartě <xref:System.Windows.Forms.TabControl>, nastavte `DrawMode` vlastnost, která má <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> a zpracovat `DrawItem` událostí.</span><span class="sxs-lookup"><span data-stu-id="9e47e-145">To draw each tab in a <xref:System.Windows.Forms.TabControl>, set the `DrawMode` property to <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> and handle the `DrawItem` event.</span></span> <span data-ttu-id="9e47e-146">Tato událost nastane jednou pro každé kartě jenom v případě, že je na kartě viditelné v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="9e47e-146">This event occurs once for each tab only when the tab is visible in the control.</span></span>  
  
 <span data-ttu-id="9e47e-147">Další informace, včetně příkladů kódu najdete v těchto tématech:</span><span class="sxs-lookup"><span data-stu-id="9e47e-147">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=nameWithType>  
  
### <a name="tooltip-component"></a><span data-ttu-id="9e47e-148">ToolTip – komponenta</span><span class="sxs-lookup"><span data-stu-id="9e47e-148">ToolTip Component</span></span>  
 <span data-ttu-id="9e47e-149"><xref:System.Windows.Forms.ToolTip> Součást umožňuje kreslení celý popisek, jakmile se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="9e47e-149">The <xref:System.Windows.Forms.ToolTip> component enables you to draw the entire ToolTip when it is displayed.</span></span>  
  
 <span data-ttu-id="9e47e-150">Kreslení <xref:System.Windows.Forms.ToolTip>, nastavte jeho `OwnerDraw` vlastnost `true` a zpracovat jeho `Draw` událostí.</span><span class="sxs-lookup"><span data-stu-id="9e47e-150">To draw a <xref:System.Windows.Forms.ToolTip>, set its `OwnerDraw` property to `true` and handle its `Draw` event.</span></span> <span data-ttu-id="9e47e-151">Chcete-li přizpůsobit velikost <xref:System.Windows.Forms.ToolTip> před `Draw` události dojde, zpracování `Popup` událostí a sady <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> vlastnost v obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="9e47e-151">To customize the size of the <xref:System.Windows.Forms.ToolTip> before the `Draw` event occurs, handle the `Popup` event and set the <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> property in the event handler.</span></span>  
  
 <span data-ttu-id="9e47e-152">Další informace, včetně příkladů kódu najdete v těchto tématech:</span><span class="sxs-lookup"><span data-stu-id="9e47e-152">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=nameWithType>  
  
### <a name="listview-control"></a><span data-ttu-id="9e47e-153">ListView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="9e47e-153">ListView Control</span></span>  
 <span data-ttu-id="9e47e-154"><xref:System.Windows.Forms.ListView> Řízení umožňuje kreslení jednotlivé položky, podřízených položek a záhlaví sloupců v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="9e47e-154">The <xref:System.Windows.Forms.ListView> control enables you to draw individual items, subitems, and column headers in the control.</span></span>  
  
 <span data-ttu-id="9e47e-155">Chcete-li povolit kreslení v ovládacím prvku vlastníka, nastavte `OwnerDraw` vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="9e47e-155">To enable owner drawing in the control, set the `OwnerDraw` property to `true`.</span></span>  
  
 <span data-ttu-id="9e47e-156">Kreslení jednotlivých položek v ovládacím prvku, zpracování `DrawItem` událostí.</span><span class="sxs-lookup"><span data-stu-id="9e47e-156">To draw each item in the control, handle the `DrawItem` event.</span></span>  
  
 <span data-ttu-id="9e47e-157">Kreslení každý záhlaví sloupce či podřízenou položku v ovládacím prvku při <xref:System.Windows.Forms.ListView.View%2A> je nastavena na <xref:System.Windows.Forms.View.Details>, zpracování `DrawSubItem` a `DrawColumnHeader` události.</span><span class="sxs-lookup"><span data-stu-id="9e47e-157">To draw each subitem or column header in the control when the <xref:System.Windows.Forms.ListView.View%2A> property is set to <xref:System.Windows.Forms.View.Details>, handle the `DrawSubItem` and `DrawColumnHeader` events.</span></span>  
  
 <span data-ttu-id="9e47e-158">Další informace, včetně příkladů kódu najdete v těchto tématech:</span><span class="sxs-lookup"><span data-stu-id="9e47e-158">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=nameWithType>  
  
### <a name="treeview-control"></a><span data-ttu-id="9e47e-159">TreeView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="9e47e-159">TreeView Control</span></span>  
 <span data-ttu-id="9e47e-160"><xref:System.Windows.Forms.TreeView> Řízení umožňuje kreslení jednotlivé uzly v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="9e47e-160">The <xref:System.Windows.Forms.TreeView> control enables you to draw individual nodes in the control.</span></span>  
  
 <span data-ttu-id="9e47e-161">Kreslení pouze text zobrazovaný v každém uzlu, nastavte `DrawMode` vlastnost <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> a zpracovat `DrawNode` událost, která má nakreslit text.</span><span class="sxs-lookup"><span data-stu-id="9e47e-161">To draw only the text displayed in each node, set the `DrawMode` property to <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> and handle the `DrawNode` event to draw the text.</span></span>  
  
 <span data-ttu-id="9e47e-162">Kreslení všechny elementy každého uzlu, nastavte `DrawMode` vlastnost <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> a zpracovat `DrawNode` událostí k vykreslení elementů, podle toho, která budete potřebovat, jako například textu, ikony, zaškrtněte políčka, plus a minus a čáry propojující uzly.</span><span class="sxs-lookup"><span data-stu-id="9e47e-162">To draw all elements of each node, set the `DrawMode` property to <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> and handle the `DrawNode` event to draw whichever elements you need, such as text, icons, check boxes, plus and minus signs, and lines connecting the nodes.</span></span>  
  
 <span data-ttu-id="9e47e-163">Další informace, včetně příkladů kódu najdete v těchto tématech:</span><span class="sxs-lookup"><span data-stu-id="9e47e-163">For more information, including code examples, see the following reference topics:</span></span>  
  
-   <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=nameWithType>  
  
### <a name="datagridview-control"></a><span data-ttu-id="9e47e-164">DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="9e47e-164">DataGridView Control</span></span>  
 <span data-ttu-id="9e47e-165"><xref:System.Windows.Forms.DataGridView> Řízení umožňuje kreslení jednotlivých buněk a řádků v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="9e47e-165">The <xref:System.Windows.Forms.DataGridView> control enables you to draw individual cells and rows in the control.</span></span>  
  
 <span data-ttu-id="9e47e-166">Kreslení jednotlivých buněk, zpracování `CellPainting` událostí.</span><span class="sxs-lookup"><span data-stu-id="9e47e-166">To draw individual cells, handle the `CellPainting` event.</span></span>  
  
 <span data-ttu-id="9e47e-167">K vykreslení elementů řádků nebo jednotlivých řádků, zpracovat jeden nebo oba `RowPrePaint` a `RowPostPaint` události.</span><span class="sxs-lookup"><span data-stu-id="9e47e-167">To draw individual rows or elements of rows, handle one or both of the `RowPrePaint` and `RowPostPaint` events.</span></span> <span data-ttu-id="9e47e-168">`RowPrePaint` Předtím, než se vykresluje v buňkách v řádku, dojde k události a `RowPostPaint` po buněk se vykresluje dojde k události.</span><span class="sxs-lookup"><span data-stu-id="9e47e-168">The `RowPrePaint` event occurs before the cells in a row are painted, and the `RowPostPaint` event occurs after the cells are painted.</span></span> <span data-ttu-id="9e47e-169">Dokáže zpracovat oba události a `CellPainting` událost Malování řádek pozadí, jednotlivých buněk a řádek popředí samostatně, nebo můžete zadat konkrétní přizpůsobení, kde je potřebujete a použít výchozí zobrazení pro další prvky řádek.</span><span class="sxs-lookup"><span data-stu-id="9e47e-169">You can handle both events and the `CellPainting` event to paint row background, individual cells, and row foreground separately, or you can provide specific customizations where you need them and use the default display for other elements of the row.</span></span>  
  
 <span data-ttu-id="9e47e-170">Další informace, včetně příkladů kódu naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="9e47e-170">For more information, including code examples, see the following topics:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
-   [<span data-ttu-id="9e47e-171">Postupy: Přizpůsobení vzhledu buněk v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="9e47e-171">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)  
  
-   [<span data-ttu-id="9e47e-172">Postupy: Přizpůsobení vzhledu řádků v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="9e47e-172">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a><span data-ttu-id="9e47e-173">ToolStrip – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="9e47e-173">ToolStrip Control</span></span>  
 <span data-ttu-id="9e47e-174"><xref:System.Windows.Forms.ToolStrip> a odvozené ovládací prvky umožňují přizpůsobit kteréhokoli aspektu jejich vzhled.</span><span class="sxs-lookup"><span data-stu-id="9e47e-174"><xref:System.Windows.Forms.ToolStrip> and derived controls enable you to customize any aspect of their appearance.</span></span>  
  
 <span data-ttu-id="9e47e-175">Poskytnout vlastní vykreslení pro <xref:System.Windows.Forms.ToolStrip> ovládací prvky, nastavení `Renderer` vlastnost <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, nebo <xref:System.Windows.Forms.ToolStripContentPanel> k `ToolStripRenderer` objektu a zpracovat jeden nebo více mnoho kreslení událostí poskytované `ToolStripRenderer` třídy.</span><span class="sxs-lookup"><span data-stu-id="9e47e-175">To provide custom rendering for <xref:System.Windows.Forms.ToolStrip> controls, set the `Renderer` property of a <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, or <xref:System.Windows.Forms.ToolStripContentPanel> to a `ToolStripRenderer` object and handle one or more of the many drawing events provided by the `ToolStripRenderer` class.</span></span> <span data-ttu-id="9e47e-176">Alternativně nastavte `Renderer` vlastnost, která má instance vlastní třídy odvozené od `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, nebo <xref:System.Windows.Forms.ToolStripSystemRenderer> implementuje nebo přepsání konkrétní `On` *EventName* metody.</span><span class="sxs-lookup"><span data-stu-id="9e47e-176">Alternatively, set a `Renderer` property to an instance of your own class derived from `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, or <xref:System.Windows.Forms.ToolStripSystemRenderer> that implements or overrides specific `On`*EventName* methods.</span></span>  
  
 <span data-ttu-id="9e47e-177">Další informace, včetně příkladů kódu naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="9e47e-177">For more information, including code examples, see the following topics:</span></span>  
  
-   <xref:System.Windows.Forms.ToolStripRenderer>  
  
-   [<span data-ttu-id="9e47e-178">Postupy: Vytvoření a nastavení vlastního rendereru pro ovládací prvek ToolStrip ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9e47e-178">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
-   [<span data-ttu-id="9e47e-179">Postupy: Vlastní vykreslení ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="9e47e-179">How to: Custom Draw a ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a><span data-ttu-id="9e47e-180">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e47e-180">See Also</span></span>  
 [<span data-ttu-id="9e47e-181">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9e47e-181">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
