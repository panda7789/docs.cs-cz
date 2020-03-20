---
title: Model obsahu
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
ms.openlocfilehash: ec4e96c0883489135b77f09a3c19f144cb4d30bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187396"
---
# <a name="wpf-content-model"></a><span data-ttu-id="7d070-102">Model obsahu WPF</span><span class="sxs-lookup"><span data-stu-id="7d070-102">WPF Content Model</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="7d070-103">je prezentační platforma, která poskytuje mnoho ovládacích prvků a typů podobných ovládacím prvkům, jejichž primárním účelem je zobrazení různých typů obsahu.</span><span class="sxs-lookup"><span data-stu-id="7d070-103">is a presentation platform that provides many controls and control-like types whose primary purpose is to display different types of content.</span></span> <span data-ttu-id="7d070-104">Chcete-li zjistit, který ovládací prvek použít nebo který ovládací prvek odvodit z, měli byste pochopit druhy objektů, které může konkrétní ovládací prvek nejlépe zobrazit.</span><span class="sxs-lookup"><span data-stu-id="7d070-104">To determine which control to use or which control to derive from, you should understand the kinds of objects a particular control can best display.</span></span>  
  
 <span data-ttu-id="7d070-105">Toto téma shrnuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] model obsahu pro typy ovládacích prvku a ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7d070-105">This topic summarizes the content model for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] control and control-like types.</span></span> <span data-ttu-id="7d070-106">Model obsahu popisuje, jaký obsah lze použít v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="7d070-106">The content model describes what content can be used in a control.</span></span> <span data-ttu-id="7d070-107">Toto téma také uvádí vlastnosti obsahu pro každý model obsahu.</span><span class="sxs-lookup"><span data-stu-id="7d070-107">This topic also lists the content properties for each content model.</span></span> <span data-ttu-id="7d070-108">Vlastnost content je vlastnost, která se používá k ukládání obsahu objektu.</span><span class="sxs-lookup"><span data-stu-id="7d070-108">A content property is a property that is used to store the content of the object.</span></span>  

<a name="classes_that_contain_arbitrary_content"></a>
## <a name="classes-that-contain-arbitrary-content"></a><span data-ttu-id="7d070-109">Třídy, které obsahují libovolný obsah</span><span class="sxs-lookup"><span data-stu-id="7d070-109">Classes That Contain Arbitrary Content</span></span>  
 <span data-ttu-id="7d070-110">Některé ovládací prvky mohou obsahovat objekt libovolného <xref:System.DateTime> typu, <xref:System.Windows.UIElement> například řetězec, objekt nebo kontejner, který je kontejnerem pro další položky.</span><span class="sxs-lookup"><span data-stu-id="7d070-110">Some controls can contain an object of any type, such as a string, a <xref:System.DateTime> object, or a <xref:System.Windows.UIElement> that is a container for additional items.</span></span> <span data-ttu-id="7d070-111">Může například <xref:System.Windows.Controls.Button> obsahovat obrázek a nějaký text; nebo <xref:System.Windows.Controls.CheckBox> může obsahovat <xref:System.DateTime.Now%2A?displayProperty=nameWithType>hodnotu .</span><span class="sxs-lookup"><span data-stu-id="7d070-111">For example, a <xref:System.Windows.Controls.Button> can contain an image and some text; or a <xref:System.Windows.Controls.CheckBox> can contain the value of <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.</span></span>  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="7d070-112">má čtyři třídy, které mohou obsahovat libovolný obsah.</span><span class="sxs-lookup"><span data-stu-id="7d070-112">has four classes that can contain arbitrary content.</span></span> <span data-ttu-id="7d070-113">V následující tabulce jsou uvedeny <xref:System.Windows.Controls.Control>třídy, které dědí z .</span><span class="sxs-lookup"><span data-stu-id="7d070-113">The following table lists the classes, which inherit from <xref:System.Windows.Controls.Control>.</span></span>  
  
|<span data-ttu-id="7d070-114">Třída, která obsahuje libovolný obsah</span><span class="sxs-lookup"><span data-stu-id="7d070-114">Class that contains arbitrary content</span></span>|<span data-ttu-id="7d070-115">Obsah</span><span class="sxs-lookup"><span data-stu-id="7d070-115">Content</span></span>|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="7d070-116">Jeden libovolný objekt.</span><span class="sxs-lookup"><span data-stu-id="7d070-116">A single arbitrary object.</span></span>|  
|<xref:System.Windows.Controls.HeaderedContentControl>|<span data-ttu-id="7d070-117">Záhlaví a jedna položka, které jsou libovolné objekty.</span><span class="sxs-lookup"><span data-stu-id="7d070-117">A header and a single item, both of which are arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.ItemsControl>|<span data-ttu-id="7d070-118">Kolekce libovolných objektů.</span><span class="sxs-lookup"><span data-stu-id="7d070-118">A collection of arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|<span data-ttu-id="7d070-119">Záhlaví a kolekce položek, z nichž všechny jsou libovolné objekty.</span><span class="sxs-lookup"><span data-stu-id="7d070-119">A header and a collection of items, all of which are arbitrary objects.</span></span>|  
  
 <span data-ttu-id="7d070-120">Ovládací prvky, které dědí z těchto tříd, mohou obsahovat stejný typ obsahu a zacházet s obsahem stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="7d070-120">Controls that inherit from these classes can contain the same type of content and treat the content in the same way.</span></span> <span data-ttu-id="7d070-121">Následující obrázek znázorňuje jeden ovládací prvek z každého modelu obsahu, který obsahuje obrázek a některý text:</span><span class="sxs-lookup"><span data-stu-id="7d070-121">The following illustration shows one control from each content model that contains an image and some text:</span></span>  
  
 ![Snímek obrazovky, který zobrazuje čtyři různé ovládací prvky, jeden z každého modelu obsahu.](./media/wpf-content-model/control-content-model-image-text.png)  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a><span data-ttu-id="7d070-123">Ovládací prvky, které obsahují jeden libovolný objekt</span><span class="sxs-lookup"><span data-stu-id="7d070-123">Controls That Contain a Single Arbitrary Object</span></span>  
 <span data-ttu-id="7d070-124">Třída <xref:System.Windows.Controls.ContentControl> obsahuje jeden kus libovolného obsahu.</span><span class="sxs-lookup"><span data-stu-id="7d070-124">The <xref:System.Windows.Controls.ContentControl> class contains a single piece of arbitrary content.</span></span> <span data-ttu-id="7d070-125">Jeho vlastnost <xref:System.Windows.Controls.ContentControl.Content%2A>obsahu je .</span><span class="sxs-lookup"><span data-stu-id="7d070-125">Its content property is <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="7d070-126">Následující ovládací prvky dědí z <xref:System.Windows.Controls.ContentControl> a používají jeho model obsahu:</span><span class="sxs-lookup"><span data-stu-id="7d070-126">The following controls inherit from <xref:System.Windows.Controls.ContentControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.Button>  
  
- <xref:System.Windows.Controls.Primitives.ButtonBase>  
  
- <xref:System.Windows.Controls.CheckBox>  
  
- <xref:System.Windows.Controls.ComboBoxItem>  
  
- <xref:System.Windows.Controls.ContentControl>  
  
- <xref:System.Windows.Controls.Frame>  
  
- <xref:System.Windows.Controls.GridViewColumnHeader>  
  
- <xref:System.Windows.Controls.GroupItem>  
  
- <xref:System.Windows.Controls.Label>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Navigation.NavigationWindow>  
  
- <xref:System.Windows.Controls.RadioButton>  
  
- <xref:System.Windows.Controls.Primitives.RepeatButton>  
  
- <xref:System.Windows.Controls.ScrollViewer>  
  
- <xref:System.Windows.Controls.Primitives.StatusBarItem>  
  
- <xref:System.Windows.Controls.Primitives.ToggleButton>  
  
- <xref:System.Windows.Controls.ToolTip>  
  
- <xref:System.Windows.Controls.UserControl>  
  
- <xref:System.Windows.Window>  
  
 <span data-ttu-id="7d070-127">Následující obrázek znázorňuje čtyři <xref:System.Windows.Controls.ContentControl.Content%2A> tlačítka, <xref:System.DateTime> jejichž je <xref:System.Windows.Shapes.Rectangle>nastavena na řetězec, objekt, a , <xref:System.Windows.Controls.Panel> a, který obsahuje <xref:System.Windows.Shapes.Ellipse> a a : <xref:System.Windows.Controls.TextBlock></span><span class="sxs-lookup"><span data-stu-id="7d070-127">The following illustration shows four buttons whose <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a string, a <xref:System.DateTime> object, a <xref:System.Windows.Shapes.Rectangle>, and a <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>:</span></span>  
  
 ![Snímek obrazovky, který zobrazuje čtyři tlačítka s různými typy obsahu.](./media/wpf-content-model/control-content-model-buttons.png)  
  
 <span data-ttu-id="7d070-129">Příklad nastavení vlastnosti naleznete <xref:System.Windows.Controls.ContentControl.Content%2A> v <xref:System.Windows.Controls.ContentControl>tématu .</span><span class="sxs-lookup"><span data-stu-id="7d070-129">For an example of how to set the <xref:System.Windows.Controls.ContentControl.Content%2A> property, see <xref:System.Windows.Controls.ContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a><span data-ttu-id="7d070-130">Ovládací prvky, které obsahují záhlaví a jeden libovolný objekt</span><span class="sxs-lookup"><span data-stu-id="7d070-130">Controls That Contain a Header and a Single Arbitrary Object</span></span>  
 <span data-ttu-id="7d070-131">Třída <xref:System.Windows.Controls.HeaderedContentControl> dědí <xref:System.Windows.Controls.ContentControl> a zobrazuje obsah s hlavičkou.</span><span class="sxs-lookup"><span data-stu-id="7d070-131">The <xref:System.Windows.Controls.HeaderedContentControl> class inherits from <xref:System.Windows.Controls.ContentControl> and displays content with a header.</span></span> <span data-ttu-id="7d070-132">Dědí vlastnost content <xref:System.Windows.Controls.ContentControl.Content%2A>, <xref:System.Windows.Controls.ContentControl> z a <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> definuje vlastnost, <xref:System.Object>která je typu ; proto oba může být libovolný objekt.</span><span class="sxs-lookup"><span data-stu-id="7d070-132">It inherits the content property, <xref:System.Windows.Controls.ContentControl.Content%2A>, from <xref:System.Windows.Controls.ContentControl> and defines the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> property that is of type <xref:System.Object>; therefore, both can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="7d070-133">Následující ovládací prvky dědí z <xref:System.Windows.Controls.HeaderedContentControl> a používají jeho model obsahu:</span><span class="sxs-lookup"><span data-stu-id="7d070-133">The following controls inherit from <xref:System.Windows.Controls.HeaderedContentControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.Expander>  
  
- <xref:System.Windows.Controls.GroupBox>  
  
- <xref:System.Windows.Controls.TabItem>  
  
 <span data-ttu-id="7d070-134">Následující obrázek <xref:System.Windows.Controls.TabItem> znázorňuje dva objekty.</span><span class="sxs-lookup"><span data-stu-id="7d070-134">The following illustration shows two <xref:System.Windows.Controls.TabItem> objects.</span></span> <span data-ttu-id="7d070-135">První <xref:System.Windows.Controls.TabItem> má <xref:System.Windows.UIElement> objekty <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> jako <xref:System.Windows.Controls.ContentControl.Content%2A>a .</span><span class="sxs-lookup"><span data-stu-id="7d070-135">The first <xref:System.Windows.Controls.TabItem> has <xref:System.Windows.UIElement> objects as the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="7d070-136">Je <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> nastavena <xref:System.Windows.Controls.StackPanel> na, <xref:System.Windows.Shapes.Ellipse> která <xref:System.Windows.Controls.TextBlock>obsahuje a .</span><span class="sxs-lookup"><span data-stu-id="7d070-136">The <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="7d070-137">Je <xref:System.Windows.Controls.ContentControl.Content%2A> nastavena <xref:System.Windows.Controls.StackPanel> na, <xref:System.Windows.Controls.TextBlock> která <xref:System.Windows.Controls.Label>obsahuje a .</span><span class="sxs-lookup"><span data-stu-id="7d070-137">The <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains a <xref:System.Windows.Controls.TextBlock> and a <xref:System.Windows.Controls.Label>.</span></span> <span data-ttu-id="7d070-138">Druhý <xref:System.Windows.Controls.TabItem> má řetězec v <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> a <xref:System.Windows.Controls.TextBlock> v <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="7d070-138">The second <xref:System.Windows.Controls.TabItem> has a string in the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and a <xref:System.Windows.Controls.TextBlock> in the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span>  
  
 ![TabControl, který používá různé typy v Header vlastnost.](./media/wpf-content-model/control-content-model-tab.png)  
  
 <span data-ttu-id="7d070-140">Příklad vytváření <xref:System.Windows.Controls.TabItem> objektů naleznete v <xref:System.Windows.Controls.HeaderedContentControl>tématu .</span><span class="sxs-lookup"><span data-stu-id="7d070-140">For an example of how to create <xref:System.Windows.Controls.TabItem> objects, see <xref:System.Windows.Controls.HeaderedContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a><span data-ttu-id="7d070-141">Ovládací prvky, které obsahují kolekci libovolných objektů</span><span class="sxs-lookup"><span data-stu-id="7d070-141">Controls That Contain a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="7d070-142">Třída <xref:System.Windows.Controls.ItemsControl> dědí <xref:System.Windows.Controls.Control> z a může obsahovat více položek, jako jsou řetězce, objekty nebo jiné prvky.</span><span class="sxs-lookup"><span data-stu-id="7d070-142">The <xref:System.Windows.Controls.ItemsControl> class inherits from <xref:System.Windows.Controls.Control> and can contain multiple items, such as strings, objects, or other elements.</span></span> <span data-ttu-id="7d070-143">Jeho vlastnosti <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ItemsControl.Items%2A>obsahu jsou a .</span><span class="sxs-lookup"><span data-stu-id="7d070-143">Its content properties are <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> and <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span></span> <span data-ttu-id="7d070-144"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>se obvykle používá k <xref:System.Windows.Controls.ItemsControl> naplnění shromažďování dat.</span><span class="sxs-lookup"><span data-stu-id="7d070-144"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> is typically used to populate the <xref:System.Windows.Controls.ItemsControl> with a data collection.</span></span> <span data-ttu-id="7d070-145">Pokud nechcete použít kolekci k <xref:System.Windows.Controls.ItemsControl>naplnění , můžete přidat <xref:System.Windows.Controls.ItemsControl.Items%2A> položky pomocí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7d070-145">If you do not want to use a collection to populate the <xref:System.Windows.Controls.ItemsControl>, you can add items by using the <xref:System.Windows.Controls.ItemsControl.Items%2A> property.</span></span>  
  
 <span data-ttu-id="7d070-146">Následující ovládací prvky dědí z <xref:System.Windows.Controls.ItemsControl> a používají jeho model obsahu:</span><span class="sxs-lookup"><span data-stu-id="7d070-146">The following controls inherit from <xref:System.Windows.Controls.ItemsControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.Menu>  
  
- <xref:System.Windows.Controls.Primitives.MenuBase>  
  
- <xref:System.Windows.Controls.ContextMenu>  
  
- <xref:System.Windows.Controls.ComboBox>  
  
- <xref:System.Windows.Controls.ItemsControl>  
  
- <xref:System.Windows.Controls.ListBox>  
  
- <xref:System.Windows.Controls.ListView>  
  
- <xref:System.Windows.Controls.TabControl>  
  
- <xref:System.Windows.Controls.TreeView>  
  
- <xref:System.Windows.Controls.Primitives.Selector>  
  
- <xref:System.Windows.Controls.Primitives.StatusBar>  
  
 <span data-ttu-id="7d070-147">Následující obrázek <xref:System.Windows.Controls.ListBox> znázorňuje, který obsahuje tyto typy položek:</span><span class="sxs-lookup"><span data-stu-id="7d070-147">The following illustration shows a <xref:System.Windows.Controls.ListBox> that contains these types of items:</span></span>  
  
- <span data-ttu-id="7d070-148">Řetězec.</span><span class="sxs-lookup"><span data-stu-id="7d070-148">A string.</span></span>  
  
- <span data-ttu-id="7d070-149">Objekt. <xref:System.DateTime></span><span class="sxs-lookup"><span data-stu-id="7d070-149">A <xref:System.DateTime> object.</span></span>  
  
- <span data-ttu-id="7d070-150">Úloha <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="7d070-150">A <xref:System.Windows.UIElement>.</span></span>  
  
- <span data-ttu-id="7d070-151">A, <xref:System.Windows.Controls.Panel> který <xref:System.Windows.Shapes.Ellipse> obsahuje <xref:System.Windows.Controls.TextBlock>a .</span><span class="sxs-lookup"><span data-stu-id="7d070-151">A <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 ![Snímek obrazovky, který zobrazuje listbox se čtyřmi typy obsahu.](./media/wpf-content-model/control-content-model-listbox.png)  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a><span data-ttu-id="7d070-153">Ovládací prvky, které obsahují záhlaví a kolekce libovolných objektů</span><span class="sxs-lookup"><span data-stu-id="7d070-153">Controls That Contain a Header and a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="7d070-154">Třída <xref:System.Windows.Controls.HeaderedItemsControl> dědí <xref:System.Windows.Controls.ItemsControl> z a může obsahovat více položek, jako jsou řetězce, objekty nebo jiné prvky a záhlaví.</span><span class="sxs-lookup"><span data-stu-id="7d070-154">The <xref:System.Windows.Controls.HeaderedItemsControl> class inherits from <xref:System.Windows.Controls.ItemsControl> and can contain multiple items, such as strings, objects, or other elements, and a header.</span></span> <span data-ttu-id="7d070-155">Zdědí <xref:System.Windows.Controls.ItemsControl> vlastnosti <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>obsahu <xref:System.Windows.Controls.ItemsControl.Items%2A>, a , <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> a definuje vlastnost, která může být libovolný objekt.</span><span class="sxs-lookup"><span data-stu-id="7d070-155">It inherits the <xref:System.Windows.Controls.ItemsControl> content properties, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, and <xref:System.Windows.Controls.ItemsControl.Items%2A>, and it defines the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property that can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="7d070-156">Následující ovládací prvky dědí z <xref:System.Windows.Controls.HeaderedItemsControl> a používají jeho model obsahu:</span><span class="sxs-lookup"><span data-stu-id="7d070-156">The following controls inherit from <xref:System.Windows.Controls.HeaderedItemsControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.MenuItem>  
  
- <xref:System.Windows.Controls.ToolBar>  
  
- <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a><span data-ttu-id="7d070-157">Třídy, které obsahují kolekci objektů UIElement</span><span class="sxs-lookup"><span data-stu-id="7d070-157">Classes That Contain a Collection of UIElement Objects</span></span>  
 <span data-ttu-id="7d070-158">Třída <xref:System.Windows.Controls.Panel> umístí a uspořádá podřízené <xref:System.Windows.UIElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="7d070-158">The <xref:System.Windows.Controls.Panel> class positions and arranges child <xref:System.Windows.UIElement> objects.</span></span> <span data-ttu-id="7d070-159">Jeho vlastnost <xref:System.Windows.Controls.Panel.Children%2A>obsahu je .</span><span class="sxs-lookup"><span data-stu-id="7d070-159">Its content property is <xref:System.Windows.Controls.Panel.Children%2A>.</span></span>  
  
 <span data-ttu-id="7d070-160">Následující třídy dědí z <xref:System.Windows.Controls.Panel> třídy a používají její model obsahu:</span><span class="sxs-lookup"><span data-stu-id="7d070-160">The following classes inherit from the <xref:System.Windows.Controls.Panel> class and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.Canvas>  
  
- <xref:System.Windows.Controls.DockPanel>  
  
- <xref:System.Windows.Controls.Grid>  
  
- <xref:System.Windows.Controls.Primitives.TabPanel>  
  
- <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
  
- <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
  
- <xref:System.Windows.Controls.Primitives.UniformGrid>  
  
- <xref:System.Windows.Controls.StackPanel>  
  
- <xref:System.Windows.Controls.VirtualizingPanel>  
  
- <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
- <xref:System.Windows.Controls.WrapPanel>  
  
 <span data-ttu-id="7d070-161">Další informace naleznete v [tématu Přehled panelů](panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7d070-161">For more information, see [Panels Overview](panels-overview.md).</span></span>  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a><span data-ttu-id="7d070-162">Třídy, které ovlivňují vzhled prvku UIElement</span><span class="sxs-lookup"><span data-stu-id="7d070-162">Classes That Affect the Appearance of a UIElement</span></span>  
 <span data-ttu-id="7d070-163">Třída <xref:System.Windows.Controls.Decorator> aplikuje vizuální efekty na jedno <xref:System.Windows.UIElement>dítě nebo kolem jednoho dítěte .</span><span class="sxs-lookup"><span data-stu-id="7d070-163">The <xref:System.Windows.Controls.Decorator> class applies visual effects onto or around a single child <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="7d070-164">Jeho vlastnost <xref:System.Windows.Controls.Decorator.Child%2A>obsahu je .</span><span class="sxs-lookup"><span data-stu-id="7d070-164">Its content property is <xref:System.Windows.Controls.Decorator.Child%2A>.</span></span> <span data-ttu-id="7d070-165">Následující třídy <xref:System.Windows.Controls.Decorator> dědí z a používat jeho model obsahu:</span><span class="sxs-lookup"><span data-stu-id="7d070-165">The following classes inherit from <xref:System.Windows.Controls.Decorator> and use its content model:</span></span>  
  
- <xref:System.Windows.Documents.AdornerDecorator>  
  
- <xref:System.Windows.Controls.Border>  
  
- <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
- <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
- <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
- <xref:System.Windows.Controls.InkPresenter>  
  
- <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
- <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
- <xref:System.Windows.Controls.Viewbox>  
  
 <span data-ttu-id="7d070-166">Následující obrázek <xref:System.Windows.Controls.TextBox> znázorňuje, který má <xref:System.Windows.Controls.Border> (je zdoben) kolem něj.</span><span class="sxs-lookup"><span data-stu-id="7d070-166">The following illustration shows a <xref:System.Windows.Controls.TextBox> that has (is decorated with) a <xref:System.Windows.Controls.Border> around it.</span></span>  
  
 <span data-ttu-id="7d070-167">![Textbox s černým ohraničením](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span><span class="sxs-lookup"><span data-stu-id="7d070-167">![TextBox with black border](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span></span>  
<span data-ttu-id="7d070-168">TextBlock, který má ohraničení</span><span class="sxs-lookup"><span data-stu-id="7d070-168">TextBlock that has a Border</span></span>  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a><span data-ttu-id="7d070-169">Třídy, které poskytují vizuální zpětnou vazbu o Prvku UI</span><span class="sxs-lookup"><span data-stu-id="7d070-169">Classes That Provide Visual Feedback About a UIElement</span></span>  
 <span data-ttu-id="7d070-170">Třída <xref:System.Windows.Documents.Adorner> poskytuje vizuální podněty pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="7d070-170">The <xref:System.Windows.Documents.Adorner> class provides visual cues to a user.</span></span> <span data-ttu-id="7d070-171">Například použijte <xref:System.Windows.Documents.Adorner> přidat funkční popisovače prvků nebo poskytnout informace o stavu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7d070-171">For example, use an <xref:System.Windows.Documents.Adorner> to add functional handles to elements or provide state information about a control.</span></span> <span data-ttu-id="7d070-172">Třída <xref:System.Windows.Documents.Adorner> poskytuje rámec, takže můžete vytvořit vlastní adorners.</span><span class="sxs-lookup"><span data-stu-id="7d070-172">The <xref:System.Windows.Documents.Adorner> class provides a framework so that you can create your own adorners.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="7d070-173">neposkytuje žádné implementované adorners.</span><span class="sxs-lookup"><span data-stu-id="7d070-173">does not provide any implemented adorners.</span></span> <span data-ttu-id="7d070-174">Další informace naleznete v tématu [Adorners Overview](adorners-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7d070-174">For more information, see [Adorners Overview](adorners-overview.md).</span></span>  
  
<a name="classes_that_enable_users_to_enter_text"></a>
## <a name="classes-that-enable-users-to-enter-text"></a><span data-ttu-id="7d070-175">Třídy, které umožňují uživatelům zadávat text</span><span class="sxs-lookup"><span data-stu-id="7d070-175">Classes That Enable Users to Enter Text</span></span>  
 <span data-ttu-id="7d070-176">WPF poskytuje tři primární ovládací prvky, které umožňují uživatelům zadávat text.</span><span class="sxs-lookup"><span data-stu-id="7d070-176">WPF provides three primary controls that enable users to enter text.</span></span> <span data-ttu-id="7d070-177">Každý ovládací prvek zobrazí text jinak.</span><span class="sxs-lookup"><span data-stu-id="7d070-177">Each control displays the text differently.</span></span> <span data-ttu-id="7d070-178">V následující tabulce jsou uvedeny tyto tři ovládací prvky související s textem, jejich možnosti při zobrazení textu a jejich vlastnosti, které obsahují text ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7d070-178">The following table lists these three text-related controls, their capabilities when they display text, and their properties that contain the control's text.</span></span>  
  
|<span data-ttu-id="7d070-179">Řízení</span><span class="sxs-lookup"><span data-stu-id="7d070-179">Control</span></span>|<span data-ttu-id="7d070-180">Text je zobrazen jako</span><span class="sxs-lookup"><span data-stu-id="7d070-180">Text is displayed as</span></span>|<span data-ttu-id="7d070-181">Vlastnost obsahu</span><span class="sxs-lookup"><span data-stu-id="7d070-181">Content property</span></span>|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|<span data-ttu-id="7d070-182">Prostý text</span><span class="sxs-lookup"><span data-stu-id="7d070-182">Plain text</span></span>|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|<span data-ttu-id="7d070-183">Formátovaný text</span><span class="sxs-lookup"><span data-stu-id="7d070-183">Formatted text</span></span>|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|<span data-ttu-id="7d070-184">Skrytý text (znaky jsou maskované)</span><span class="sxs-lookup"><span data-stu-id="7d070-184">Hidden text (characters are masked)</span></span>|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>
## <a name="classes-that-display-your-text"></a><span data-ttu-id="7d070-185">Třídy, které zobrazují váš text</span><span class="sxs-lookup"><span data-stu-id="7d070-185">Classes That Display Your Text</span></span>  
 <span data-ttu-id="7d070-186">K zobrazení prostého nebo formátovaného textu lze použít několik tříd.</span><span class="sxs-lookup"><span data-stu-id="7d070-186">Several classes can be used to display plain or formatted text.</span></span> <span data-ttu-id="7d070-187">Můžete použít <xref:System.Windows.Controls.TextBlock> k zobrazení malého množství textu.</span><span class="sxs-lookup"><span data-stu-id="7d070-187">You can use <xref:System.Windows.Controls.TextBlock> to display small amounts of text.</span></span> <span data-ttu-id="7d070-188">Chcete-li zobrazit velké množství textu, <xref:System.Windows.Controls.FlowDocumentReader> <xref:System.Windows.Controls.FlowDocumentPageViewer>použijte <xref:System.Windows.Controls.FlowDocumentScrollViewer> ovládací prvky , nebo .</span><span class="sxs-lookup"><span data-stu-id="7d070-188">If you want to display large amounts of text, use the <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, or <xref:System.Windows.Controls.FlowDocumentScrollViewer> controls.</span></span>  
  
 <span data-ttu-id="7d070-189">Má <xref:System.Windows.Controls.TextBlock> dvě vlastnosti <xref:System.Windows.Controls.TextBlock.Text%2A> <xref:System.Windows.Controls.TextBlock.Inlines%2A>obsahu: a .</span><span class="sxs-lookup"><span data-stu-id="7d070-189">The <xref:System.Windows.Controls.TextBlock> has two content properties: <xref:System.Windows.Controls.TextBlock.Text%2A> and <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span></span> <span data-ttu-id="7d070-190">Pokud chcete zobrazit text, který používá konzistentní <xref:System.Windows.Controls.TextBlock.Text%2A> formátování, vlastnost je často nejlepší volbou.</span><span class="sxs-lookup"><span data-stu-id="7d070-190">When you want to display text that uses consistent formatting, the <xref:System.Windows.Controls.TextBlock.Text%2A> property is often your best choice.</span></span> <span data-ttu-id="7d070-191">Pokud plánujete v celém textu používat jiné <xref:System.Windows.Controls.TextBlock.Inlines%2A> formátování, použijte vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7d070-191">If you plan to use different formatting throughout the text, use the <xref:System.Windows.Controls.TextBlock.Inlines%2A> property.</span></span> <span data-ttu-id="7d070-192">Vlastnost <xref:System.Windows.Controls.TextBlock.Inlines%2A> je kolekce <xref:System.Windows.Documents.Inline> objektů, které určují, jak formátovat text.</span><span class="sxs-lookup"><span data-stu-id="7d070-192">The <xref:System.Windows.Controls.TextBlock.Inlines%2A> property is a collection of <xref:System.Windows.Documents.Inline> objects, which specify how to format text.</span></span>  
  
 <span data-ttu-id="7d070-193">V následující tabulce je <xref:System.Windows.Controls.FlowDocumentReader>uvedena <xref:System.Windows.Controls.FlowDocumentPageViewer>vlastnost <xref:System.Windows.Controls.FlowDocumentScrollViewer> obsahu pro , a třídy.</span><span class="sxs-lookup"><span data-stu-id="7d070-193">The following table lists the content property for <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, and <xref:System.Windows.Controls.FlowDocumentScrollViewer> classes.</span></span>  
  
|<span data-ttu-id="7d070-194">Řízení</span><span class="sxs-lookup"><span data-stu-id="7d070-194">Control</span></span>|<span data-ttu-id="7d070-195">Vlastnost obsahu</span><span class="sxs-lookup"><span data-stu-id="7d070-195">Content property</span></span>|<span data-ttu-id="7d070-196">Typ vlastnosti obsahu</span><span class="sxs-lookup"><span data-stu-id="7d070-196">Content property type</span></span>|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|<span data-ttu-id="7d070-197">Dokument</span><span class="sxs-lookup"><span data-stu-id="7d070-197">Document</span></span>|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|<span data-ttu-id="7d070-198">Dokument</span><span class="sxs-lookup"><span data-stu-id="7d070-198">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|<span data-ttu-id="7d070-199">Dokument</span><span class="sxs-lookup"><span data-stu-id="7d070-199">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
  
 <span data-ttu-id="7d070-200">Implementuje <xref:System.Windows.Documents.FlowDocument> <xref:System.Windows.Documents.IDocumentPaginatorSource> rozhraní; proto všechny tři třídy <xref:System.Windows.Documents.FlowDocument> může trvat jako obsah.</span><span class="sxs-lookup"><span data-stu-id="7d070-200">The <xref:System.Windows.Documents.FlowDocument> implements the <xref:System.Windows.Documents.IDocumentPaginatorSource> interface; therefore, all three classes can take a <xref:System.Windows.Documents.FlowDocument> as content.</span></span>  
  
<a name="classes_that_format_text"></a>
## <a name="classes-that-format-your-text"></a><span data-ttu-id="7d070-201">Třídy, které formátují text</span><span class="sxs-lookup"><span data-stu-id="7d070-201">Classes That Format Your Text</span></span>  
 <span data-ttu-id="7d070-202"><xref:System.Windows.Documents.TextElement>a jeho související třídy umožňují formátovat text.</span><span class="sxs-lookup"><span data-stu-id="7d070-202"><xref:System.Windows.Documents.TextElement> and its related classes allow you to format text.</span></span> <span data-ttu-id="7d070-203"><xref:System.Windows.Documents.TextElement>objekty obsahují a <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Documents.FlowDocument> formátují text a objekty.</span><span class="sxs-lookup"><span data-stu-id="7d070-203"><xref:System.Windows.Documents.TextElement> objects contain and format text in <xref:System.Windows.Controls.TextBlock> and <xref:System.Windows.Documents.FlowDocument> objects.</span></span> <span data-ttu-id="7d070-204">Dva primární typy <xref:System.Windows.Documents.TextElement> objektů <xref:System.Windows.Documents.Block> jsou <xref:System.Windows.Documents.Inline> prvky a prvky.</span><span class="sxs-lookup"><span data-stu-id="7d070-204">The two primary types of <xref:System.Windows.Documents.TextElement> objects are <xref:System.Windows.Documents.Block> elements and <xref:System.Windows.Documents.Inline> elements.</span></span> <span data-ttu-id="7d070-205">Prvek <xref:System.Windows.Documents.Block> představuje blok textu, například odstavec nebo seznam.</span><span class="sxs-lookup"><span data-stu-id="7d070-205">A <xref:System.Windows.Documents.Block> element represents a block of text, such as a paragraph or list.</span></span> <span data-ttu-id="7d070-206">Prvek <xref:System.Windows.Documents.Inline> představuje část textu v bloku.</span><span class="sxs-lookup"><span data-stu-id="7d070-206">An <xref:System.Windows.Documents.Inline> element represents a portion of text in a block.</span></span> <span data-ttu-id="7d070-207">Mnoho <xref:System.Windows.Documents.Inline> tříd určuje formátování textu, na který jsou použity.</span><span class="sxs-lookup"><span data-stu-id="7d070-207">Many <xref:System.Windows.Documents.Inline> classes specify formatting for the text to which they are applied.</span></span> <span data-ttu-id="7d070-208">Každý <xref:System.Windows.Documents.TextElement> z nich má svůj vlastní model obsahu.</span><span class="sxs-lookup"><span data-stu-id="7d070-208">Each <xref:System.Windows.Documents.TextElement> has its own content model.</span></span> <span data-ttu-id="7d070-209">Další informace naleznete v tématu [Přehled modelu obsahu TextElement](../advanced/textelement-content-model-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7d070-209">For more information, see the [TextElement Content Model Overview](../advanced/textelement-content-model-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d070-210">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d070-210">See also</span></span>

- [<span data-ttu-id="7d070-211">Pokročilé</span><span class="sxs-lookup"><span data-stu-id="7d070-211">Advanced</span></span>](../advanced/index.md)
