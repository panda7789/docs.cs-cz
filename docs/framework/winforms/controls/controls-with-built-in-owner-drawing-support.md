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
ms.openlocfilehash: f0d4b99f9ee0134fc7334a941dd5ef4fd7ba3df3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930196"
---
# <a name="controls-with-built-in-owner-drawing-support"></a><span data-ttu-id="183df-102">Ovládací prvky s vestavěnou podporou vykreslování vlastníkem</span><span class="sxs-lookup"><span data-stu-id="183df-102">Controls with Built-In Owner-Drawing Support</span></span>
<span data-ttu-id="183df-103">Vlastní kreslení v model Windows Forms, který se také označuje jako vlastní kreslení, je technika pro změnu vzhledu některých ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="183df-103">Owner drawing in Windows Forms, which is also known as custom drawing, is a technique for changing the visual appearance of certain controls.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="183df-104">Slovo "ovládací prvek" v tomto tématu se používá jako třídy, které jsou odvozeny <xref:System.Windows.Forms.Control> z <xref:System.ComponentModel.Component>buď nebo.</span><span class="sxs-lookup"><span data-stu-id="183df-104">The word "control" in this topic is used to mean classes that derive from either <xref:System.Windows.Forms.Control> or <xref:System.ComponentModel.Component>.</span></span>  
  
 <span data-ttu-id="183df-105">Systém Windows obvykle zpracovává automatické malování pomocí nastavení vlastností, jako je <xref:System.Windows.Forms.Control.BackColor%2A> například k určení vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="183df-105">Typically, Windows handles painting automatically by using property settings such as <xref:System.Windows.Forms.Control.BackColor%2A> to determine the appearance of a control.</span></span> <span data-ttu-id="183df-106">Při kreslení vlastníka převezmete proces Malování a změníte prvky vzhledu, které nejsou k dispozici pomocí vlastností.</span><span class="sxs-lookup"><span data-stu-id="183df-106">With owner drawing, you take over the painting process, changing elements of appearance that are not available by using properties.</span></span> <span data-ttu-id="183df-107">Mnoho ovládacích prvků například umožňuje nastavit barvu zobrazeného textu, ale budete omezeni na jednu barvu.</span><span class="sxs-lookup"><span data-stu-id="183df-107">For example, many controls let you set the color of the text that is displayed, but you are limited to a single color.</span></span> <span data-ttu-id="183df-108">Vlastní vykreslování umožňuje provádět akce, jako je například zobrazení části textu černě a částečně.</span><span class="sxs-lookup"><span data-stu-id="183df-108">Owner drawing enables you to do things like display part of the text in black and part in red.</span></span>  
  
 <span data-ttu-id="183df-109">V praxi je kreslení vlastníka podobné kreslení grafik na formuláři.</span><span class="sxs-lookup"><span data-stu-id="183df-109">In practice, owner drawing is similar to drawing graphics on a form.</span></span> <span data-ttu-id="183df-110">Například můžete použít grafické metody v obslužné rutině pro <xref:System.Windows.Forms.Control.Paint> událost formuláře k emulaci `ListBox` ovládacího prvku, ale budete muset napsat vlastní kód pro zpracování interakce všech uživatelů.</span><span class="sxs-lookup"><span data-stu-id="183df-110">For example, you could use graphics methods in a handler for the form's <xref:System.Windows.Forms.Control.Paint> event to emulate a `ListBox` control, but you would have to write your own code to handle all user interaction.</span></span> <span data-ttu-id="183df-111">Při kreslení vlastníka používá ovládací prvek váš kód k nakreslení jeho obsahu, ale jinak uchovává všechny jeho vnitřní funkce.</span><span class="sxs-lookup"><span data-stu-id="183df-111">With owner drawing, the control uses your code to draw its contents but otherwise retains all its intrinsic capabilities.</span></span> <span data-ttu-id="183df-112">Můžete použít grafické metody pro vykreslení každé položky v ovládacím prvku nebo pro přizpůsobení některých aspektů každé položky, zatímco používáte výchozí vzhled pro jiné aspekty každé položky.</span><span class="sxs-lookup"><span data-stu-id="183df-112">You can use graphics methods to draw each item in the control or to customize some aspects of each item while you use the default appearance for other aspects of each item.</span></span>  
  
## <a name="owner-drawing-in-windows-forms-controls"></a><span data-ttu-id="183df-113">Vlastní kreslení v ovládacích prvcích model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="183df-113">Owner Drawing in Windows Forms Controls</span></span>  
 <span data-ttu-id="183df-114">Chcete-li provést vykreslování vlastníka v ovládacích prvcích, které ho podporují, obvykle nastavíte jednu vlastnost a zpracujete jednu nebo více událostí.</span><span class="sxs-lookup"><span data-stu-id="183df-114">To perform owner drawing in controls that support it, you will typically set one property and handle one or more events.</span></span>  
  
 <span data-ttu-id="183df-115">Většina ovládacích prvků, které podporují kreslení vlastníka `OwnerDraw` , `DrawMode` mají vlastnost nebo, která označuje, zda ovládací prvek při malování sám vyvolá událost související s kreslením nebo události.</span><span class="sxs-lookup"><span data-stu-id="183df-115">Most controls that support owner drawing have an `OwnerDraw` or `DrawMode` property that indicates whether the control will raise its drawing-related event or events when it paints itself.</span></span>  
  
 <span data-ttu-id="183df-116">`OwnerDraw` Ovládací prvky, které nemají vlastnost nebo `DrawMode` , obsahují `DataGridView` ovládací prvek, který poskytuje události `ToolStrip` kreslení, ke kterým dochází automaticky, a ovládací prvek, který je vykreslen pomocí externí třídy vykreslování, která má vlastní. události související s vykreslováním.</span><span class="sxs-lookup"><span data-stu-id="183df-116">Controls that do not have an `OwnerDraw` or `DrawMode` property include the `DataGridView` control, which provides drawing events that occur automatically, and the `ToolStrip` control, which is drawn using an external rendering class that has its own drawing-related events.</span></span>  
  
 <span data-ttu-id="183df-117">Existuje mnoho různých typů událostí kreslení, ale k typické události kreslení dojde, pokud chcete nakreslit jednu položku v rámci ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="183df-117">There are many different kinds of drawing events, but a typical drawing event occurs in order to draw a single item within a control.</span></span> <span data-ttu-id="183df-118">Obslužná rutina události obdrží `EventArgs` objekt, který obsahuje informace o vykreslené položce a o nástrojích, které můžete použít k vykreslení.</span><span class="sxs-lookup"><span data-stu-id="183df-118">The event handler receives an `EventArgs` object that contains information about the item being drawn and tools you can use to draw it.</span></span> <span data-ttu-id="183df-119">Například tento objekt obvykle obsahuje číslo indexu položky v rámci své nadřazené kolekce, <xref:System.Drawing.Rectangle> která označuje hranice zobrazení položky <xref:System.Drawing.Graphics> a objekt pro volání metod vybarvení.</span><span class="sxs-lookup"><span data-stu-id="183df-119">For example, this object typically contains the item's index number within its parent collection, a <xref:System.Drawing.Rectangle> that indicates the item's display boundaries, and a <xref:System.Drawing.Graphics> object for calling paint methods.</span></span> <span data-ttu-id="183df-120">U některých událostí `EventArgs` objekt poskytuje další informace o položce a metodách, které lze volat k malování některých aspektů položky ve výchozím nastavení, jako je například pozadí nebo obdélník výběru.</span><span class="sxs-lookup"><span data-stu-id="183df-120">For some events, the `EventArgs` object provides additional information about the item and methods that you can call to paint some aspects of the item by default, such as the background or a focus rectangle.</span></span>  
  
 <span data-ttu-id="183df-121">Chcete-li vytvořit opakovaně použitelný ovládací prvek, který obsahuje vlastní nastavení vykreslené uživatelem, vytvořte novou třídu, která je odvozena z třídy ovládacího prvku, která podporuje vykreslování vlastníka.</span><span class="sxs-lookup"><span data-stu-id="183df-121">To create a reusable control that contains your owner-drawn customizations, create a new class that derives from a control class that supports owner drawing.</span></span> <span data-ttu-id="183df-122">Místo zpracování událostí vykreslování zahrňte do přepsání kód pro vykreslení vlastníka pro příslušnou `On`metodu nebo metody *EventName* v nové třídě.</span><span class="sxs-lookup"><span data-stu-id="183df-122">Rather than handling drawing events, include your owner-drawing code in overrides for the appropriate `On`*EventName* method or methods in the new class.</span></span> <span data-ttu-id="183df-123">Ujistěte se, že v tomto případě zavoláte metodu nebo metody `On` *EventName* základní třídy, aby uživatelé vašeho ovládacího prvku mohli zpracovávat události vykreslování vlastníka a poskytnout další přizpůsobení.</span><span class="sxs-lookup"><span data-stu-id="183df-123">Make sure that you call the base class `On`*EventName* method or methods in this case so that users of your control can handle owner-drawing events and provide additional customization.</span></span>  
  
 <span data-ttu-id="183df-124">Následující model Windows Forms řídí vykreslování vlastníků ve všech verzích .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="183df-124">The following Windows Forms controls support owner drawing in all versions of the .NET Framework:</span></span>  
  
- <xref:System.Windows.Forms.ListBox>  
  
- <xref:System.Windows.Forms.ComboBox>  
  
- <span data-ttu-id="183df-125"><xref:System.Windows.Forms.MenuItem>(používá se <xref:System.Windows.Forms.MainMenu> v <xref:System.Windows.Forms.ContextMenu>a)</span><span class="sxs-lookup"><span data-stu-id="183df-125"><xref:System.Windows.Forms.MenuItem> (used by <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu>)</span></span>  
  
- <xref:System.Windows.Forms.TabControl>  
  
 <span data-ttu-id="183df-126">Následující ovládací prvky podporují kreslení vlastníka pouze v .NET Framework 2,0:</span><span class="sxs-lookup"><span data-stu-id="183df-126">The following controls support owner drawing only in .NET Framework 2.0:</span></span>  
  
- <xref:System.Windows.Forms.ToolTip>  
  
- <xref:System.Windows.Forms.ListView>  
  
- <xref:System.Windows.Forms.TreeView>  
  
 <span data-ttu-id="183df-127">Následující ovládací prvky podporují kreslení vlastníka a jsou v .NET Framework 2,0 nové:</span><span class="sxs-lookup"><span data-stu-id="183df-127">The following controls support owner drawing and are new in .NET Framework 2.0:</span></span>  
  
- <xref:System.Windows.Forms.DataGridView>  
  
- <xref:System.Windows.Forms.ToolStrip>  
  
 <span data-ttu-id="183df-128">Následující části obsahují další podrobnosti o každém z těchto ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="183df-128">The following sections provide additional details for each of these controls.</span></span>  
  
### <a name="listbox-and-combobox-controls"></a><span data-ttu-id="183df-129">Ovládací prvky ListBox a ComboBox</span><span class="sxs-lookup"><span data-stu-id="183df-129">ListBox and ComboBox Controls</span></span>  
 <span data-ttu-id="183df-130">Ovládací prvky <xref:System.Windows.Forms.ComboBox> a umožňují kreslit jednotlivé položky v ovládacím prvku buď v jedné velikosti, nebo v různých velikostech. <xref:System.Windows.Forms.ListBox></span><span class="sxs-lookup"><span data-stu-id="183df-130">The <xref:System.Windows.Forms.ListBox> and <xref:System.Windows.Forms.ComboBox> controls enable you to draw individual items in the control either all in one size, or in varying sizes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="183df-131">I když je <xref:System.Windows.Forms.ListBox> ovládací prvek odvozen z ovládacího prvku, nepodporuje vykreslování vlastníka. <xref:System.Windows.Forms.CheckedListBox></span><span class="sxs-lookup"><span data-stu-id="183df-131">Although the <xref:System.Windows.Forms.CheckedListBox> control is derived from the <xref:System.Windows.Forms.ListBox> control, it does not support owner drawing.</span></span>  
  
 <span data-ttu-id="183df-132">Chcete-li každou položku nakreslit na stejnou velikost `DrawMode` , nastavte <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> vlastnost na a `DrawItem` zpracujte událost.</span><span class="sxs-lookup"><span data-stu-id="183df-132">To draw each item the same size, set the `DrawMode` property to <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> and handle the `DrawItem` event.</span></span>  
  
 <span data-ttu-id="183df-133">Pro vykreslení každé položky pomocí `DrawMode` jiné velikosti nastavte vlastnost na <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> a zpracujte `MeasureItem` události a `DrawItem` .</span><span class="sxs-lookup"><span data-stu-id="183df-133">To draw each item using a different size, set the `DrawMode` property to <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> and handle both the `MeasureItem` and `DrawItem` events.</span></span> <span data-ttu-id="183df-134">Událost umožňuje určit velikost položky `DrawItem` před tím, než dojde k události pro tuto položku. `MeasureItem`</span><span class="sxs-lookup"><span data-stu-id="183df-134">The `MeasureItem` event lets you indicate the size of an item before the `DrawItem` event occurs for that item.</span></span>  
  
 <span data-ttu-id="183df-135">Další informace, včetně příkladů kódu, najdete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="183df-135">For more information, including code examples, see the following topics:</span></span>  
  
- <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=nameWithType>  
  
- [<span data-ttu-id="183df-136">Postupy: Vytvoření textu proměnlivé velikosti v ovládacím prvku ComboBox</span><span class="sxs-lookup"><span data-stu-id="183df-136">How to: Create Variable Sized Text in a ComboBox Control</span></span>](how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a><span data-ttu-id="183df-137">Komponenta MenuItem</span><span class="sxs-lookup"><span data-stu-id="183df-137">MenuItem Component</span></span>  
 <span data-ttu-id="183df-138">Komponenta představuje jednu položku nabídky <xref:System.Windows.Forms.MainMenu> v součásti nebo <xref:System.Windows.Forms.ContextMenu>. <xref:System.Windows.Forms.MenuItem></span><span class="sxs-lookup"><span data-stu-id="183df-138">The <xref:System.Windows.Forms.MenuItem> component represents a single menu item in a <xref:System.Windows.Forms.MainMenu> or <xref:System.Windows.Forms.ContextMenu> component.</span></span>  
  
 <span data-ttu-id="183df-139">Chcete-li <xref:System.Windows.Forms.MenuItem>nakreslit, `OwnerDraw` nastavte jeho `true` vlastnost na a `DrawItem` zpracujte její událost.</span><span class="sxs-lookup"><span data-stu-id="183df-139">To draw a <xref:System.Windows.Forms.MenuItem>, set its `OwnerDraw` property to `true` and handle its `DrawItem` event.</span></span> <span data-ttu-id="183df-140">Chcete-li přizpůsobit velikost položky nabídky před `DrawItem` výskytem události, zpracujte `MeasureItem` událost položky.</span><span class="sxs-lookup"><span data-stu-id="183df-140">To customize the size of the menu item before the `DrawItem` event occurs, handle the item's `MeasureItem` event.</span></span>  
  
 <span data-ttu-id="183df-141">Další informace, včetně příkladů kódu, najdete v následujících referenčních tématech:</span><span class="sxs-lookup"><span data-stu-id="183df-141">For more information, including code examples, see the following reference topics:</span></span>  
  
- <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=nameWithType>  
  
### <a name="tabcontrol-control"></a><span data-ttu-id="183df-142">TabControl – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="183df-142">TabControl Control</span></span>  
 <span data-ttu-id="183df-143"><xref:System.Windows.Forms.TabControl> Ovládací prvek umožňuje kreslit jednotlivé karty v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="183df-143">The <xref:System.Windows.Forms.TabControl> control enables you to draw individual tabs in the control.</span></span> <span data-ttu-id="183df-144">Vlastní kresba má vliv pouze na karty; <xref:System.Windows.Forms.TabPage> obsah není ovlivněn.</span><span class="sxs-lookup"><span data-stu-id="183df-144">Owner drawing affects only the tabs; the <xref:System.Windows.Forms.TabPage> contents are not affected.</span></span>  
  
 <span data-ttu-id="183df-145">Chcete-li nakreslit každou <xref:System.Windows.Forms.TabControl>kartu v, `DrawMode` nastavte `DrawItem` vlastnost <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> na a zpracujte událost.</span><span class="sxs-lookup"><span data-stu-id="183df-145">To draw each tab in a <xref:System.Windows.Forms.TabControl>, set the `DrawMode` property to <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> and handle the `DrawItem` event.</span></span> <span data-ttu-id="183df-146">Tato událost nastane jednou pro každou kartu pouze v případě, že je karta viditelná v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="183df-146">This event occurs once for each tab only when the tab is visible in the control.</span></span>  
  
 <span data-ttu-id="183df-147">Další informace, včetně příkladů kódu, najdete v následujících referenčních tématech:</span><span class="sxs-lookup"><span data-stu-id="183df-147">For more information, including code examples, see the following reference topics:</span></span>  
  
- <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=nameWithType>  
  
### <a name="tooltip-component"></a><span data-ttu-id="183df-148">ToolTip – komponenta</span><span class="sxs-lookup"><span data-stu-id="183df-148">ToolTip Component</span></span>  
 <span data-ttu-id="183df-149"><xref:System.Windows.Forms.ToolTip> Komponenta umožňuje při zobrazení zobrazit celý popis tlačítka.</span><span class="sxs-lookup"><span data-stu-id="183df-149">The <xref:System.Windows.Forms.ToolTip> component enables you to draw the entire ToolTip when it is displayed.</span></span>  
  
 <span data-ttu-id="183df-150">Chcete-li <xref:System.Windows.Forms.ToolTip>nakreslit, `OwnerDraw` nastavte jeho `true` vlastnost na a `Draw` zpracujte její událost.</span><span class="sxs-lookup"><span data-stu-id="183df-150">To draw a <xref:System.Windows.Forms.ToolTip>, set its `OwnerDraw` property to `true` and handle its `Draw` event.</span></span> <span data-ttu-id="183df-151">Chcete-li přizpůsobit <xref:System.Windows.Forms.ToolTip> velikost, `Draw` než dojde k `Popup` události, zpracujte událost a nastavte <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> vlastnost v obslužné rutině události.</span><span class="sxs-lookup"><span data-stu-id="183df-151">To customize the size of the <xref:System.Windows.Forms.ToolTip> before the `Draw` event occurs, handle the `Popup` event and set the <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> property in the event handler.</span></span>  
  
 <span data-ttu-id="183df-152">Další informace, včetně příkladů kódu, najdete v následujících referenčních tématech:</span><span class="sxs-lookup"><span data-stu-id="183df-152">For more information, including code examples, see the following reference topics:</span></span>  
  
- <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=nameWithType>  
  
### <a name="listview-control"></a><span data-ttu-id="183df-153">ListView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="183df-153">ListView Control</span></span>  
 <span data-ttu-id="183df-154"><xref:System.Windows.Forms.ListView> Ovládací prvek umožňuje v ovládacím prvku nakreslit jednotlivé položky, podpoložky a záhlaví sloupců.</span><span class="sxs-lookup"><span data-stu-id="183df-154">The <xref:System.Windows.Forms.ListView> control enables you to draw individual items, subitems, and column headers in the control.</span></span>  
  
 <span data-ttu-id="183df-155">Chcete-li povolit vykreslování vlastníka v ovládacím prvku, `OwnerDraw` nastavte vlastnost `true`na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="183df-155">To enable owner drawing in the control, set the `OwnerDraw` property to `true`.</span></span>  
  
 <span data-ttu-id="183df-156">Chcete-li nakreslit každou položku v ovládacím prvku `DrawItem` , zpracujte událost.</span><span class="sxs-lookup"><span data-stu-id="183df-156">To draw each item in the control, handle the `DrawItem` event.</span></span>  
  
 <span data-ttu-id="183df-157">Chcete-li v ovládacím prvku nakreslit jednotlivá záhlaví podpoložky nebo <xref:System.Windows.Forms.ListView.View%2A> sloupce, když je <xref:System.Windows.Forms.View.Details>vlastnost nastavena na `DrawSubItem` , `DrawColumnHeader` zpracujte události a.</span><span class="sxs-lookup"><span data-stu-id="183df-157">To draw each subitem or column header in the control when the <xref:System.Windows.Forms.ListView.View%2A> property is set to <xref:System.Windows.Forms.View.Details>, handle the `DrawSubItem` and `DrawColumnHeader` events.</span></span>  
  
 <span data-ttu-id="183df-158">Další informace, včetně příkladů kódu, najdete v následujících referenčních tématech:</span><span class="sxs-lookup"><span data-stu-id="183df-158">For more information, including code examples, see the following reference topics:</span></span>  
  
- <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=nameWithType>  
  
### <a name="treeview-control"></a><span data-ttu-id="183df-159">TreeView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="183df-159">TreeView Control</span></span>  
 <span data-ttu-id="183df-160"><xref:System.Windows.Forms.TreeView> Ovládací prvek umožňuje kreslit jednotlivé uzly v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="183df-160">The <xref:System.Windows.Forms.TreeView> control enables you to draw individual nodes in the control.</span></span>  
  
 <span data-ttu-id="183df-161">Chcete-li nakreslit pouze text zobrazený v každém uzlu `DrawMode` , nastavte <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> vlastnost na a `DrawNode` zpracujte událost pro vykreslení textu.</span><span class="sxs-lookup"><span data-stu-id="183df-161">To draw only the text displayed in each node, set the `DrawMode` property to <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> and handle the `DrawNode` event to draw the text.</span></span>  
  
 <span data-ttu-id="183df-162">Chcete-li nakreslit všechny prvky každého uzlu, `DrawMode` nastavte vlastnost <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> na a zpracujte `DrawNode` událost pro vykreslení všech potřebných prvků, jako jsou text, ikony, zaškrtávací políčka, znaménka plus a mínus a čáry připojující uzly.</span><span class="sxs-lookup"><span data-stu-id="183df-162">To draw all elements of each node, set the `DrawMode` property to <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> and handle the `DrawNode` event to draw whichever elements you need, such as text, icons, check boxes, plus and minus signs, and lines connecting the nodes.</span></span>  
  
 <span data-ttu-id="183df-163">Další informace, včetně příkladů kódu, najdete v následujících referenčních tématech:</span><span class="sxs-lookup"><span data-stu-id="183df-163">For more information, including code examples, see the following reference topics:</span></span>  
  
- <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=nameWithType>  
  
### <a name="datagridview-control"></a><span data-ttu-id="183df-164">DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="183df-164">DataGridView Control</span></span>  
 <span data-ttu-id="183df-165"><xref:System.Windows.Forms.DataGridView> Ovládací prvek umožňuje kreslit jednotlivé buňky a řádky v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="183df-165">The <xref:System.Windows.Forms.DataGridView> control enables you to draw individual cells and rows in the control.</span></span>  
  
 <span data-ttu-id="183df-166">Chcete-li nakreslit jednotlivé buňky `CellPainting` , zpracujte událost.</span><span class="sxs-lookup"><span data-stu-id="183df-166">To draw individual cells, handle the `CellPainting` event.</span></span>  
  
 <span data-ttu-id="183df-167">Chcete-li nakreslit jednotlivé řádky nebo prvky řádků, zpracujte jednu nebo obě `RowPrePaint` události `RowPostPaint` a.</span><span class="sxs-lookup"><span data-stu-id="183df-167">To draw individual rows or elements of rows, handle one or both of the `RowPrePaint` and `RowPostPaint` events.</span></span> <span data-ttu-id="183df-168">K události dojde před vykreslením buněk v řádku `RowPostPaint` a událost nastane po vykreslení buněk. `RowPrePaint`</span><span class="sxs-lookup"><span data-stu-id="183df-168">The `RowPrePaint` event occurs before the cells in a row are painted, and the `RowPostPaint` event occurs after the cells are painted.</span></span> <span data-ttu-id="183df-169">Můžete zpracovávat obě události a `CellPainting` událost pro malování pozadí řádku, jednotlivé buňky a popředí řádku samostatně nebo můžete zadat konkrétní vlastní nastavení, kde je potřebujete, a použít výchozí zobrazení pro jiné prvky řádku.</span><span class="sxs-lookup"><span data-stu-id="183df-169">You can handle both events and the `CellPainting` event to paint row background, individual cells, and row foreground separately, or you can provide specific customizations where you need them and use the default display for other elements of the row.</span></span>  
  
 <span data-ttu-id="183df-170">Další informace, včetně příkladů kódu, najdete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="183df-170">For more information, including code examples, see the following topics:</span></span>  
  
- <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
- <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
- <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
- [<span data-ttu-id="183df-171">Postupy: Přizpůsobení vzhledu buněk v ovládacím prvku DataGridView model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="183df-171">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>](customize-the-appearance-of-cells-in-the-datagrid.md)  
  
- [<span data-ttu-id="183df-172">Postupy: Přizpůsobení vzhledu řádků v ovládacím prvku DataGridView model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="183df-172">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>](customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a><span data-ttu-id="183df-173">ToolStrip – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="183df-173">ToolStrip Control</span></span>  
 <span data-ttu-id="183df-174"><xref:System.Windows.Forms.ToolStrip>a odvozené ovládací prvky umožňují přizpůsobit libovolný aspekt jejich vzhledu.</span><span class="sxs-lookup"><span data-stu-id="183df-174"><xref:System.Windows.Forms.ToolStrip> and derived controls enable you to customize any aspect of their appearance.</span></span>  
  
 <span data-ttu-id="183df-175">Chcete-li poskytnout vlastní <xref:System.Windows.Forms.ToolStrip> vykreslování pro ovládací prvky `Renderer` , nastavte <xref:System.Windows.Forms.ToolStripPanel>vlastnost <xref:System.Windows.Forms.ToolStrip> `ToolStripRenderer` objektu <xref:System.Windows.Forms.ToolStripManager>,, nebo <xref:System.Windows.Forms.ToolStripContentPanel> na objekt a zpracujte jednu nebo více mnoha událostí kreslení poskytovaných `ToolStripRenderer` třída.</span><span class="sxs-lookup"><span data-stu-id="183df-175">To provide custom rendering for <xref:System.Windows.Forms.ToolStrip> controls, set the `Renderer` property of a <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, or <xref:System.Windows.Forms.ToolStripContentPanel> to a `ToolStripRenderer` object and handle one or more of the many drawing events provided by the `ToolStripRenderer` class.</span></span> <span data-ttu-id="183df-176">Případně můžete `Renderer` nastavit vlastnost na instanci vaší vlastní třídy odvozené z `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>nebo <xref:System.Windows.Forms.ToolStripSystemRenderer> , která implementuje nebo Přepisuje konkrétní `On`metody *EventName* .</span><span class="sxs-lookup"><span data-stu-id="183df-176">Alternatively, set a `Renderer` property to an instance of your own class derived from `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, or <xref:System.Windows.Forms.ToolStripSystemRenderer> that implements or overrides specific `On`*EventName* methods.</span></span>  
  
 <span data-ttu-id="183df-177">Další informace, včetně příkladů kódu, najdete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="183df-177">For more information, including code examples, see the following topics:</span></span>  
  
- <xref:System.Windows.Forms.ToolStripRenderer>  
  
- [<span data-ttu-id="183df-178">Postupy: Vytvoření a nastavení vlastního zobrazovací jednotky pro ovládací prvek ToolStrip v model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="183df-178">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
- [<span data-ttu-id="183df-179">Postupy: Vlastní vykreslení ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="183df-179">How to: Custom Draw a ToolStrip Control</span></span>](how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a><span data-ttu-id="183df-180">Viz také:</span><span class="sxs-lookup"><span data-stu-id="183df-180">See also</span></span>

- [<span data-ttu-id="183df-181">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="183df-181">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
