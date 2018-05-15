---
title: Model obsahu WPF
ms.date: 03/30/2017
helpviewer_keywords:
- UIElement class [WPF], displaying content
- content model [WPF], controls
- controls [WPF], displaying text
- content display [WPF], controls
- controls [WPF], formatting text
- displaying content [WPF]
- arbitrary content classes [WPF], content model
- ContentControl class [WPF], displaying content
ms.assetid: 214da5ef-547a-4cf8-9b07-4aa8a0e52cdd
ms.openlocfilehash: 48e96b04a3459aa18a52624758d5fa2347570fcf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="wpf-content-model"></a><span data-ttu-id="7e1c0-102">Model obsahu WPF</span><span class="sxs-lookup"><span data-stu-id="7e1c0-102">WPF Content Model</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="7e1c0-103"> je prezentace platforma, která poskytuje mnoho ovládací prvky a typy jako ovládací prvek, jehož primárním účelem je zobrazit různé typy obsahu.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-103"> is a presentation platform that provides many controls and control-like types whose primary purpose is to display different types of content.</span></span> <span data-ttu-id="7e1c0-104">Pokud chcete zjistit, který ovládací prvek použít nebo který ovládací prvek odvození od, byste měli porozumět typy objektů, které nejlépe můžete zobrazit konkrétní ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-104">To determine which control to use or which control to derive from, you should understand the kinds of objects a particular control can best display.</span></span>  
  
 <span data-ttu-id="7e1c0-105">Toto téma shrnuje modelu obsahu pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] řízení a řízení typů.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-105">This topic summarizes the content model for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] control and control-like types.</span></span> <span data-ttu-id="7e1c0-106">Model obsahu popisuje, jaké obsahu lze v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-106">The content model describes what content can be used in a control.</span></span> <span data-ttu-id="7e1c0-107">Toto téma obsahuje také obsahu vlastnosti pro každý model obsahu.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-107">This topic also lists the content properties for each content model.</span></span> <span data-ttu-id="7e1c0-108">Vlastnost obsahu je vlastnost, která se používá k uložení obsahu objektu.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-108">A content property is a property that is used to store the content of the object.</span></span>  
  
 
  
<a name="classes_that_contain_arbitrary_content"></a>   
## <a name="classes-that-contain-arbitrary-content"></a><span data-ttu-id="7e1c0-109">Třídy, které obsahují libovolný obsah</span><span class="sxs-lookup"><span data-stu-id="7e1c0-109">Classes That Contain Arbitrary Content</span></span>  
 <span data-ttu-id="7e1c0-110">Některé ovládací prvky může obsahovat objekt jakéhokoli typu, například řetězec, <xref:System.DateTime> objekt, nebo <xref:System.Windows.UIElement> který je kontejner pro další položky.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-110">Some controls can contain an object of any type, such as a string, a <xref:System.DateTime> object, or a <xref:System.Windows.UIElement> that is a container for additional items.</span></span> <span data-ttu-id="7e1c0-111">Například <xref:System.Windows.Controls.Button> může obsahovat bitovou kopii a text; nebo <xref:System.Windows.Controls.CheckBox> může obsahovat hodnotu <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-111">For example, a <xref:System.Windows.Controls.Button> can contain an image and some text; or a <xref:System.Windows.Controls.CheckBox> can contain the value of <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.</span></span>  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="7e1c0-112"> má čtyři tříd, které může obsahovat libovolný obsah.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-112"> has four classes that can contain arbitrary content.</span></span> <span data-ttu-id="7e1c0-113">Následující tabulka uvádí třídy, které dědí <xref:System.Windows.Controls.Control>.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-113">The following table lists the classes, which inherit from <xref:System.Windows.Controls.Control>.</span></span>  
  
|<span data-ttu-id="7e1c0-114">Třída, která obsahuje libovolné obsahu</span><span class="sxs-lookup"><span data-stu-id="7e1c0-114">Class that contains arbitrary content</span></span>|<span data-ttu-id="7e1c0-115">Obsah</span><span class="sxs-lookup"><span data-stu-id="7e1c0-115">Content</span></span>|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="7e1c0-116">Jeden libovolný objekt.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-116">A single arbitrary object.</span></span>|  
|<xref:System.Windows.Controls.HeaderedContentControl>|<span data-ttu-id="7e1c0-117">Záhlaví a jednu položku, obě tyto položky jsou libovolné objekty.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-117">A header and a single item, both of which are arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.ItemsControl>|<span data-ttu-id="7e1c0-118">Kolekce libovolné objekty.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-118">A collection of arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|<span data-ttu-id="7e1c0-119">Záhlaví a kolekce položek, které jsou libovolné objekty.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-119">A header and a collection of items, all of which are arbitrary objects.</span></span>|  
  
 <span data-ttu-id="7e1c0-120">Ovládací prvky, které dědí od tyto třídy může obsahovat stejného typu obsahu a považovat obsah stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-120">Controls that inherit from these classes can contain the same type of content and treat the content in the same way.</span></span> <span data-ttu-id="7e1c0-121">Následující obrázek znázorňuje jeden ovládací prvek z každé obsahu model, který obsahuje bitovou kopii a text.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-121">The following illustration shows one control from each content model that contains an image and some text.</span></span>  
  
 <span data-ttu-id="7e1c0-122">![Tlačítko, GroupBox, Listbax, TreeViewItem](../../../../docs/framework/wpf/controls/media/controlcontentmodelimagetextinto.PNG "ControlContentModelImageTextInto")</span><span class="sxs-lookup"><span data-stu-id="7e1c0-122">![Button, GroupBox, Listbax, TreeViewItem](../../../../docs/framework/wpf/controls/media/controlcontentmodelimagetextinto.PNG "ControlContentModelImageTextInto")</span></span>  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a><span data-ttu-id="7e1c0-123">Ovládací prvky, které obsahují jeden libovolný objekt</span><span class="sxs-lookup"><span data-stu-id="7e1c0-123">Controls That Contain a Single Arbitrary Object</span></span>  
 <span data-ttu-id="7e1c0-124"><xref:System.Windows.Controls.ContentControl> Třída obsahuje jediný libovolný obsah.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-124">The <xref:System.Windows.Controls.ContentControl> class contains a single piece of arbitrary content.</span></span> <span data-ttu-id="7e1c0-125">Vlastnost jeho obsahu je <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-125">Its content property is <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="7e1c0-126">Ovládací prvky dědí <xref:System.Windows.Controls.ContentControl> a použít jeho modelu obsahu:</span><span class="sxs-lookup"><span data-stu-id="7e1c0-126">The following controls inherit from <xref:System.Windows.Controls.ContentControl> and use its content model:</span></span>  
  
-   <xref:System.Windows.Controls.Button>  
  
-   <xref:System.Windows.Controls.Primitives.ButtonBase>  
  
-   <xref:System.Windows.Controls.CheckBox>  
  
-   <xref:System.Windows.Controls.ComboBoxItem>  
  
-   <xref:System.Windows.Controls.ContentControl>  
  
-   <xref:System.Windows.Controls.Frame>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeader>  
  
-   <xref:System.Windows.Controls.GroupItem>  
  
-   <xref:System.Windows.Controls.Label>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.ListViewItem>  
  
-   <xref:System.Windows.Navigation.NavigationWindow>  
  
-   <xref:System.Windows.Controls.RadioButton>  
  
-   <xref:System.Windows.Controls.Primitives.RepeatButton>  
  
-   <xref:System.Windows.Controls.ScrollViewer>  
  
-   <xref:System.Windows.Controls.Primitives.StatusBarItem>  
  
-   <xref:System.Windows.Controls.Primitives.ToggleButton>  
  
-   <xref:System.Windows.Controls.ToolTip>  
  
-   <xref:System.Windows.Controls.UserControl>  
  
-   <xref:System.Windows.Window>  
  
 <span data-ttu-id="7e1c0-127">Následující ilustrace znázorňuje čtyři tlačítka, jehož <xref:System.Windows.Controls.ContentControl.Content%2A> je nastaven na řetězec, <xref:System.DateTime> objekt, <xref:System.Windows.Shapes.Rectangle>a <xref:System.Windows.Controls.Panel> obsahující <xref:System.Windows.Shapes.Ellipse> a <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-127">The following illustration shows four buttons whose <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a string, a <xref:System.DateTime> object, a <xref:System.Windows.Shapes.Rectangle>, and a <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 <span data-ttu-id="7e1c0-128">![Čtyři tlačítka](../../../../docs/framework/wpf/controls/media/controlcontentmodelbuttons.PNG "ControlContentModelButtons")</span><span class="sxs-lookup"><span data-stu-id="7e1c0-128">![Four buttons](../../../../docs/framework/wpf/controls/media/controlcontentmodelbuttons.PNG "ControlContentModelButtons")</span></span>  
<span data-ttu-id="7e1c0-129">Čtyři tlačítka, které mají různé typy obsahu</span><span class="sxs-lookup"><span data-stu-id="7e1c0-129">Four buttons that have different types of content</span></span>  
  
 <span data-ttu-id="7e1c0-130">Příklad toho, jak nastavit <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost, najdete v části <xref:System.Windows.Controls.ContentControl>.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-130">For an example of how to set the <xref:System.Windows.Controls.ContentControl.Content%2A> property, see <xref:System.Windows.Controls.ContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a><span data-ttu-id="7e1c0-131">Ovládací prvky, které obsahují záhlaví a jeden libovolný objekt</span><span class="sxs-lookup"><span data-stu-id="7e1c0-131">Controls That Contain a Header and a Single Arbitrary Object</span></span>  
 <span data-ttu-id="7e1c0-132"><xref:System.Windows.Controls.HeaderedContentControl> Třída dědí z <xref:System.Windows.Controls.ContentControl> a zobrazí obsah s hlavičku.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-132">The <xref:System.Windows.Controls.HeaderedContentControl> class inherits from <xref:System.Windows.Controls.ContentControl> and displays content with a header.</span></span> <span data-ttu-id="7e1c0-133">Dědí vlastnost obsahu <xref:System.Windows.Controls.ContentControl.Content%2A>, z <xref:System.Windows.Controls.ContentControl> a definuje <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> vlastnost, která je typu <xref:System.Object>; proto může být libovolný objekt.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-133">It inherits the content property, <xref:System.Windows.Controls.ContentControl.Content%2A>, from <xref:System.Windows.Controls.ContentControl> and defines the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> property that is of type <xref:System.Object>; therefore, both can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="7e1c0-134">Ovládací prvky dědí <xref:System.Windows.Controls.HeaderedContentControl> a použít jeho modelu obsahu:</span><span class="sxs-lookup"><span data-stu-id="7e1c0-134">The following controls inherit from <xref:System.Windows.Controls.HeaderedContentControl> and use its content model:</span></span>  
  
-   <xref:System.Windows.Controls.Expander>  
  
-   <xref:System.Windows.Controls.GroupBox>  
  
-   <xref:System.Windows.Controls.TabItem>  
  
 <span data-ttu-id="7e1c0-135">Následující obrázek ukazuje dva <xref:System.Windows.Controls.TabItem> objekty.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-135">The following illustration shows two <xref:System.Windows.Controls.TabItem> objects.</span></span> <span data-ttu-id="7e1c0-136">První <xref:System.Windows.Controls.TabItem> má <xref:System.Windows.UIElement> objekty, jako <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> a <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-136">The first <xref:System.Windows.Controls.TabItem> has <xref:System.Windows.UIElement> objects as the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="7e1c0-137"><xref:System.Windows.Controls.HeaderedContentControl.Header%2A> Je nastaven na <xref:System.Windows.Controls.StackPanel> obsahující <xref:System.Windows.Shapes.Ellipse> a <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-137">The <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="7e1c0-138"><xref:System.Windows.Controls.ContentControl.Content%2A> Je nastaven na <xref:System.Windows.Controls.StackPanel> obsahující <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-138">The <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains a <xref:System.Windows.Controls.TextBlock> and a <xref:System.Windows.Controls.Label>.</span></span> <span data-ttu-id="7e1c0-139">Druhý <xref:System.Windows.Controls.TabItem> má řetězec <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> a <xref:System.Windows.Controls.TextBlock> v <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-139">The second <xref:System.Windows.Controls.TabItem> has a string in the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and a <xref:System.Windows.Controls.TextBlock> in the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span>  
  
 <span data-ttu-id="7e1c0-140">![TabControl](../../../../docs/framework/wpf/controls/media/controlcontentmodelteabitem.PNG "ControlContentModelTeabItem")</span><span class="sxs-lookup"><span data-stu-id="7e1c0-140">![TabControl](../../../../docs/framework/wpf/controls/media/controlcontentmodelteabitem.PNG "ControlContentModelTeabItem")</span></span>  
<span data-ttu-id="7e1c0-141">TabControl používající různé typy ve vlastnosti záhlaví</span><span class="sxs-lookup"><span data-stu-id="7e1c0-141">TabControl that uses different types in the Header property</span></span>  
  
 <span data-ttu-id="7e1c0-142">Příklad vytvoření <xref:System.Windows.Controls.TabItem> objekty, najdete v části <xref:System.Windows.Controls.HeaderedContentControl>.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-142">For an example of how to create <xref:System.Windows.Controls.TabItem> objects, see <xref:System.Windows.Controls.HeaderedContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a><span data-ttu-id="7e1c0-143">Ovládací prvky, které obsahují skupiny libovolný objekty</span><span class="sxs-lookup"><span data-stu-id="7e1c0-143">Controls That Contain a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="7e1c0-144"><xref:System.Windows.Controls.ItemsControl> Třída dědí z <xref:System.Windows.Controls.Control> a může obsahovat více položek, jako je například řetězce, objekty nebo jiných prvků.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-144">The <xref:System.Windows.Controls.ItemsControl> class inherits from <xref:System.Windows.Controls.Control> and can contain multiple items, such as strings, objects, or other elements.</span></span> <span data-ttu-id="7e1c0-145">Jeho obsahu vlastnosti jsou <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> a <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-145">Its content properties are <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> and <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span></span> <span data-ttu-id="7e1c0-146"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> Obvykle se používá k naplnění <xref:System.Windows.Controls.ItemsControl> se shromažďováním dat.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-146"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> is typically used to populate the <xref:System.Windows.Controls.ItemsControl> with a data collection.</span></span> <span data-ttu-id="7e1c0-147">Pokud nechcete použít kolekci k naplnění <xref:System.Windows.Controls.ItemsControl>, můžete přidat položky pomocí <xref:System.Windows.Controls.ItemsControl.Items%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-147">If you do not want to use a collection to populate the <xref:System.Windows.Controls.ItemsControl>, you can add items by using the <xref:System.Windows.Controls.ItemsControl.Items%2A> property.</span></span>  
  
 <span data-ttu-id="7e1c0-148">Ovládací prvky dědí <xref:System.Windows.Controls.ItemsControl> a použít jeho modelu obsahu:</span><span class="sxs-lookup"><span data-stu-id="7e1c0-148">The following controls inherit from <xref:System.Windows.Controls.ItemsControl> and use its content model:</span></span>  
  
-   <xref:System.Windows.Controls.Menu>  
  
-   <xref:System.Windows.Controls.Primitives.MenuBase>  
  
-   <xref:System.Windows.Controls.ContextMenu>  
  
-   <xref:System.Windows.Controls.ComboBox>  
  
-   <xref:System.Windows.Controls.ItemsControl>  
  
-   <xref:System.Windows.Controls.ListBox>  
  
-   <xref:System.Windows.Controls.ListView>  
  
-   <xref:System.Windows.Controls.TabControl>  
  
-   <xref:System.Windows.Controls.TreeView>  
  
-   <xref:System.Windows.Controls.Primitives.Selector>  
  
-   <xref:System.Windows.Controls.Primitives.StatusBar>  
  
 <span data-ttu-id="7e1c0-149">Následující obrázek znázorňuje <xref:System.Windows.Controls.ListBox> obsahující tyto typy položek:</span><span class="sxs-lookup"><span data-stu-id="7e1c0-149">The following illustration shows a <xref:System.Windows.Controls.ListBox> that contains these types of items:</span></span>  
  
-   <span data-ttu-id="7e1c0-150">Řetězec.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-150">A string.</span></span>  
  
-   <span data-ttu-id="7e1c0-151">A <xref:System.DateTime> objektu.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-151">A <xref:System.DateTime> object.</span></span>  
  
-   <span data-ttu-id="7e1c0-152">A <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-152">A <xref:System.Windows.UIElement>.</span></span>  
  
-   <span data-ttu-id="7e1c0-153">A <xref:System.Windows.Controls.Panel> obsahující <xref:System.Windows.Shapes.Ellipse> a <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-153">A <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 <span data-ttu-id="7e1c0-154">![ListBox – s čtyři typy obsahu](../../../../docs/framework/wpf/controls/media/controlcontentmodellistbox2.PNG "ControlContentModelListBox2")</span><span class="sxs-lookup"><span data-stu-id="7e1c0-154">![ListBox with four types of content](../../../../docs/framework/wpf/controls/media/controlcontentmodellistbox2.PNG "ControlContentModelListBox2")</span></span>  
<span data-ttu-id="7e1c0-155">ListBox –, který obsahuje více typů objektů</span><span class="sxs-lookup"><span data-stu-id="7e1c0-155">ListBox that contains multiple types of objects</span></span>  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a><span data-ttu-id="7e1c0-156">Ovládací prvky záhlaví a kolekce libovolný objektů</span><span class="sxs-lookup"><span data-stu-id="7e1c0-156">Controls That Contain a Header and a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="7e1c0-157"><xref:System.Windows.Controls.HeaderedItemsControl> Třída dědí z <xref:System.Windows.Controls.ItemsControl> a může obsahovat více položek, jako je například řetězce, objekty, nebo další prvky a hlavičku.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-157">The <xref:System.Windows.Controls.HeaderedItemsControl> class inherits from <xref:System.Windows.Controls.ItemsControl> and can contain multiple items, such as strings, objects, or other elements, and a header.</span></span> <span data-ttu-id="7e1c0-158">Zdědil <xref:System.Windows.Controls.ItemsControl> obsahu vlastnosti, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, a <xref:System.Windows.Controls.ItemsControl.Items%2A>, a definuje, <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> vlastnost, která může být libovolný objekt.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-158">It inherits the <xref:System.Windows.Controls.ItemsControl> content properties, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, and <xref:System.Windows.Controls.ItemsControl.Items%2A>, and it defines the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property that can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="7e1c0-159">Ovládací prvky dědí <xref:System.Windows.Controls.HeaderedItemsControl> a použít jeho modelu obsahu:</span><span class="sxs-lookup"><span data-stu-id="7e1c0-159">The following controls inherit from <xref:System.Windows.Controls.HeaderedItemsControl> and use its content model:</span></span>  
  
-   <xref:System.Windows.Controls.MenuItem>  
  
-   <xref:System.Windows.Controls.ToolBar>  
  
-   <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>   
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a><span data-ttu-id="7e1c0-160">Třídy, které obsahují kolekce objektů prvků uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="7e1c0-160">Classes That Contain a Collection of UIElement Objects</span></span>  
 <span data-ttu-id="7e1c0-161"><xref:System.Windows.Controls.Panel> Třídy umisťuje a uspořádá podřízené <xref:System.Windows.UIElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-161">The <xref:System.Windows.Controls.Panel> class positions and arranges child <xref:System.Windows.UIElement> objects.</span></span> <span data-ttu-id="7e1c0-162">Vlastnost jeho obsahu je <xref:System.Windows.Controls.Panel.Children%2A>.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-162">Its content property is <xref:System.Windows.Controls.Panel.Children%2A>.</span></span>  
  
 <span data-ttu-id="7e1c0-163">Následující třídy dědí <xref:System.Windows.Controls.Panel> třídy a použít jeho modelu obsahu:</span><span class="sxs-lookup"><span data-stu-id="7e1c0-163">The following classes inherit from the <xref:System.Windows.Controls.Panel> class and use its content model:</span></span>  
  
-   <xref:System.Windows.Controls.Canvas>  
  
-   <xref:System.Windows.Controls.DockPanel>  
  
-   <xref:System.Windows.Controls.Grid>  
  
-   <xref:System.Windows.Controls.Primitives.TabPanel>  
  
-   <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
  
-   <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
  
-   <xref:System.Windows.Controls.Primitives.UniformGrid>  
  
-   <xref:System.Windows.Controls.StackPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
-   <xref:System.Windows.Controls.WrapPanel>  
  
 <span data-ttu-id="7e1c0-164">Další informace najdete v tématu [přehled panelů](../../../../docs/framework/wpf/controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7e1c0-164">For more information, see [Panels Overview](../../../../docs/framework/wpf/controls/panels-overview.md).</span></span>  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>   
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a><span data-ttu-id="7e1c0-165">Třídy, které ovlivňují vzhled prvků uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="7e1c0-165">Classes That Affect the Appearance of a UIElement</span></span>  
 <span data-ttu-id="7e1c0-166"><xref:System.Windows.Controls.Decorator> Třída platí vizuálních efektů na nebo kolem jednu podřízenou <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-166">The <xref:System.Windows.Controls.Decorator> class applies visual effects onto or around a single child <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="7e1c0-167">Vlastnost jeho obsahu je <xref:System.Windows.Controls.Decorator.Child%2A>.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-167">Its content property is <xref:System.Windows.Controls.Decorator.Child%2A>.</span></span> <span data-ttu-id="7e1c0-168">Následující třídy dědí <xref:System.Windows.Controls.Decorator> a použít jeho modelu obsahu:</span><span class="sxs-lookup"><span data-stu-id="7e1c0-168">The following classes inherit from <xref:System.Windows.Controls.Decorator> and use its content model:</span></span>  
  
-   <xref:System.Windows.Documents.AdornerDecorator>  
  
-   <xref:System.Windows.Controls.Border>  
  
-   <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
-   <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
-   <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
-   <xref:System.Windows.Controls.InkPresenter>  
  
-   <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
-   <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
-   <xref:System.Windows.Controls.Viewbox>  
  
 <span data-ttu-id="7e1c0-169">Následující obrázek znázorňuje <xref:System.Windows.Controls.TextBox> má (opatřen s) <xref:System.Windows.Controls.Border> kolem něj.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-169">The following illustration shows a <xref:System.Windows.Controls.TextBox> that has (is decorated with) a <xref:System.Windows.Controls.Border> around it.</span></span>  
  
 <span data-ttu-id="7e1c0-170">![Textové pole s černým ohraničení](../../../../docs/framework/wpf/controls/media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span><span class="sxs-lookup"><span data-stu-id="7e1c0-170">![TextBox with black border](../../../../docs/framework/wpf/controls/media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span></span>  
<span data-ttu-id="7e1c0-171">TextBlock, který má ohraničení</span><span class="sxs-lookup"><span data-stu-id="7e1c0-171">TextBlock that has a Border</span></span>  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>   
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a><span data-ttu-id="7e1c0-172">Třídy, které poskytují vizuální zpětnou vazbu o prvků uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="7e1c0-172">Classes That Provide Visual Feedback About a UIElement</span></span>  
 <span data-ttu-id="7e1c0-173"><xref:System.Windows.Documents.Adorner> Třída poskytuje vizuální upozornění na uživatele.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-173">The <xref:System.Windows.Documents.Adorner> class provides visual cues to a user.</span></span> <span data-ttu-id="7e1c0-174">Například použít <xref:System.Windows.Documents.Adorner> přidat funkční obslužné rutiny na elementy nebo zadejte informace o prvku stavu.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-174">For example, use an <xref:System.Windows.Documents.Adorner> to add functional handles to elements or provide state information about a control.</span></span> <span data-ttu-id="7e1c0-175"><xref:System.Windows.Documents.Adorner> Třída poskytuje rozhraní, takže můžete vytvořit vlastní ozdobného prvku.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-175">The <xref:System.Windows.Documents.Adorner> class provides a framework so that you can create your own adorners.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="7e1c0-176"> neposkytuje žádné implementovaná ozdobného prvku.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-176"> does not provide any implemented adorners.</span></span> <span data-ttu-id="7e1c0-177">Další informace najdete v tématu [ozdobného prvku přehled](../../../../docs/framework/wpf/controls/adorners-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7e1c0-177">For more information, see [Adorners Overview](../../../../docs/framework/wpf/controls/adorners-overview.md).</span></span>  
  
<a name="classes_that_enable_users_to_enter_text"></a>   
## <a name="classes-that-enable-users-to-enter-text"></a><span data-ttu-id="7e1c0-178">Třídy, které umožňují uživatelům zadávat Text</span><span class="sxs-lookup"><span data-stu-id="7e1c0-178">Classes That Enable Users to Enter Text</span></span>  
 <span data-ttu-id="7e1c0-179">WPF poskytuje tři primární ovládací prvky, které umožňují uživatelům zadávat text.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-179">WPF provides three primary controls that enable users to enter text.</span></span> <span data-ttu-id="7e1c0-180">Každý ovládací prvek zobrazí text jinak.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-180">Each control displays the text differently.</span></span> <span data-ttu-id="7e1c0-181">Následující tabulka uvádí tyto tři související s textem ovládací prvky, jejich schopnosti, při které se zobrazuje text a jejich vlastnosti, které obsahují text ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-181">The following table lists these three text-related controls, their capabilities when they display text, and their properties that contain the control's text.</span></span>  
  
|<span data-ttu-id="7e1c0-182">Ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="7e1c0-182">Control</span></span>|<span data-ttu-id="7e1c0-183">Text se zobrazuje jako</span><span class="sxs-lookup"><span data-stu-id="7e1c0-183">Text is displayed as</span></span>|<span data-ttu-id="7e1c0-184">Vlastnost obsahu</span><span class="sxs-lookup"><span data-stu-id="7e1c0-184">Content property</span></span>|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|<span data-ttu-id="7e1c0-185">Prostý text</span><span class="sxs-lookup"><span data-stu-id="7e1c0-185">Plain text</span></span>|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|<span data-ttu-id="7e1c0-186">Formátovaný text</span><span class="sxs-lookup"><span data-stu-id="7e1c0-186">Formatted text</span></span>|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|<span data-ttu-id="7e1c0-187">Skrytý text (znaky jsou maskována)</span><span class="sxs-lookup"><span data-stu-id="7e1c0-187">Hidden text (characters are masked)</span></span>|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>   
## <a name="classes-that-display-your-text"></a><span data-ttu-id="7e1c0-188">Třídy, které zobrazí Text</span><span class="sxs-lookup"><span data-stu-id="7e1c0-188">Classes That Display Your Text</span></span>  
 <span data-ttu-id="7e1c0-189">Několik tříd lze zobrazit prostý nebo formátovaný text.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-189">Several classes can be used to display plain or formatted text.</span></span> <span data-ttu-id="7e1c0-190">Můžete použít <xref:System.Windows.Controls.TextBlock> zobrazíte malé množství textu.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-190">You can use <xref:System.Windows.Controls.TextBlock> to display small amounts of text.</span></span> <span data-ttu-id="7e1c0-191">Pokud chcete zobrazit velké množství textu, použijte <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, nebo <xref:System.Windows.Controls.FlowDocumentScrollViewer> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-191">If you want to display large amounts of text, use the <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, or <xref:System.Windows.Controls.FlowDocumentScrollViewer> controls.</span></span>  
  
 <span data-ttu-id="7e1c0-192"><xref:System.Windows.Controls.TextBlock> Má dvě vlastnosti obsahu: <xref:System.Windows.Controls.TextBlock.Text%2A> a <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-192">The <xref:System.Windows.Controls.TextBlock> has two content properties: <xref:System.Windows.Controls.TextBlock.Text%2A> and <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span></span> <span data-ttu-id="7e1c0-193">Pokud chcete zobrazit text, který používá konzistentní formátování <xref:System.Windows.Controls.TextBlock.Text%2A> vlastnost je často nejlepší volbou.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-193">When you want to display text that uses consistent formatting, the <xref:System.Windows.Controls.TextBlock.Text%2A> property is often your best choice.</span></span> <span data-ttu-id="7e1c0-194">Pokud budete chtít použít jiné formátování v celém textu, použijte <xref:System.Windows.Controls.TextBlock.Inlines%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-194">If you plan to use different formatting throughout the text, use the <xref:System.Windows.Controls.TextBlock.Inlines%2A> property.</span></span> <span data-ttu-id="7e1c0-195"><xref:System.Windows.Controls.TextBlock.Inlines%2A> Vlastnost je kolekce <xref:System.Windows.Documents.Inline> objekty, které určují způsob formátování textu.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-195">The <xref:System.Windows.Controls.TextBlock.Inlines%2A> property is a collection of <xref:System.Windows.Documents.Inline> objects, which specify how to format text.</span></span>  
  
 <span data-ttu-id="7e1c0-196">Následující tabulka uvádí vlastnost obsahu pro <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, a <xref:System.Windows.Controls.FlowDocumentScrollViewer> třídy.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-196">The following table lists the content property for <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, and <xref:System.Windows.Controls.FlowDocumentScrollViewer> classes.</span></span>  
  
|<span data-ttu-id="7e1c0-197">Ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="7e1c0-197">Control</span></span>|<span data-ttu-id="7e1c0-198">Vlastnost obsahu</span><span class="sxs-lookup"><span data-stu-id="7e1c0-198">Content property</span></span>|<span data-ttu-id="7e1c0-199">Typ obsahu vlastnosti</span><span class="sxs-lookup"><span data-stu-id="7e1c0-199">Content property type</span></span>|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|<span data-ttu-id="7e1c0-200">Dokument</span><span class="sxs-lookup"><span data-stu-id="7e1c0-200">Document</span></span>|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|<span data-ttu-id="7e1c0-201">Dokument</span><span class="sxs-lookup"><span data-stu-id="7e1c0-201">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|<span data-ttu-id="7e1c0-202">Dokument</span><span class="sxs-lookup"><span data-stu-id="7e1c0-202">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
  
 <span data-ttu-id="7e1c0-203"><xref:System.Windows.Documents.FlowDocument> Implementuje <xref:System.Windows.Documents.IDocumentPaginatorSource> rozhraní; proto může trvat všechny tři třídy <xref:System.Windows.Documents.FlowDocument> jako obsah.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-203">The <xref:System.Windows.Documents.FlowDocument> implements the <xref:System.Windows.Documents.IDocumentPaginatorSource> interface; therefore, all three classes can take a <xref:System.Windows.Documents.FlowDocument> as content.</span></span>  
  
<a name="classes_that_format_text"></a>   
## <a name="classes-that-format-your-text"></a><span data-ttu-id="7e1c0-204">Třídy, které formátování textu</span><span class="sxs-lookup"><span data-stu-id="7e1c0-204">Classes That Format Your Text</span></span>  
 <span data-ttu-id="7e1c0-205"><xref:System.Windows.Documents.TextElement> a jeho souvisejících tříd umožňují formátování textu.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-205"><xref:System.Windows.Documents.TextElement> and its related classes allow you to format text.</span></span> <span data-ttu-id="7e1c0-206"><xref:System.Windows.Documents.TextElement> objekty obsahovat a formátování textu v <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Documents.FlowDocument> objekty.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-206"><xref:System.Windows.Documents.TextElement> objects contain and format text in <xref:System.Windows.Controls.TextBlock> and <xref:System.Windows.Documents.FlowDocument> objects.</span></span> <span data-ttu-id="7e1c0-207">Oba typy primární <xref:System.Windows.Documents.TextElement> objekty jsou <xref:System.Windows.Documents.Block> elementy a <xref:System.Windows.Documents.Inline> elementy.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-207">The two primary types of <xref:System.Windows.Documents.TextElement> objects are <xref:System.Windows.Documents.Block> elements and <xref:System.Windows.Documents.Inline> elements.</span></span> <span data-ttu-id="7e1c0-208">A <xref:System.Windows.Documents.Block> element reprezentuje blok textu, například odstavce nebo seznamu.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-208">A <xref:System.Windows.Documents.Block> element represents a block of text, such as a paragraph or list.</span></span> <span data-ttu-id="7e1c0-209"><xref:System.Windows.Documents.Inline> Element reprezentuje část textu v bloku.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-209">An <xref:System.Windows.Documents.Inline> element represents a portion of text in a block.</span></span> <span data-ttu-id="7e1c0-210">Mnoho <xref:System.Windows.Documents.Inline> třídy zadejte formátování textu, do které se použijí.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-210">Many <xref:System.Windows.Documents.Inline> classes specify formatting for the text to which they are applied.</span></span> <span data-ttu-id="7e1c0-211">Každý <xref:System.Windows.Documents.TextElement> má svou vlastní modelu obsahu.</span><span class="sxs-lookup"><span data-stu-id="7e1c0-211">Each <xref:System.Windows.Documents.TextElement> has its own content model.</span></span> <span data-ttu-id="7e1c0-212">Další informace najdete v tématu [přehled modelu obsahu TextElement](../../../../docs/framework/wpf/advanced/textelement-content-model-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7e1c0-212">For more information, see the [TextElement Content Model Overview](../../../../docs/framework/wpf/advanced/textelement-content-model-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e1c0-213">Viz také</span><span class="sxs-lookup"><span data-stu-id="7e1c0-213">See Also</span></span>  
 [<span data-ttu-id="7e1c0-214">Pokročilé</span><span class="sxs-lookup"><span data-stu-id="7e1c0-214">Advanced</span></span>](../../../../docs/framework/wpf/advanced/index.md)
