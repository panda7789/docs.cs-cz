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
ms.openlocfilehash: 4f866e0366a7781c287b3ebae7b668c2b296a5cc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134587"
---
# <a name="wpf-content-model"></a><span data-ttu-id="8c523-102">Model obsahu WPF</span><span class="sxs-lookup"><span data-stu-id="8c523-102">WPF Content Model</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="8c523-103">je prezentační platforma, která nabízí mnoho ovládacích prvků a typů ovládacího prvku, jejichž primárním účelem je zobrazit různé typy obsahu.</span><span class="sxs-lookup"><span data-stu-id="8c523-103">is a presentation platform that provides many controls and control-like types whose primary purpose is to display different types of content.</span></span> <span data-ttu-id="8c523-104">Pokud chcete zjistit, který ovládací prvek použít nebo který ovládací prvek k odvození z, měli byste porozumět typy objektů, které nejlépe můžete zobrazit konkrétní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="8c523-104">To determine which control to use or which control to derive from, you should understand the kinds of objects a particular control can best display.</span></span>  
  
 <span data-ttu-id="8c523-105">Toto téma obsahuje souhrn obsahu modelu pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacího prvku a typů ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8c523-105">This topic summarizes the content model for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] control and control-like types.</span></span> <span data-ttu-id="8c523-106">Model obsahu popisuje, jaký obsah je možné v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="8c523-106">The content model describes what content can be used in a control.</span></span> <span data-ttu-id="8c523-107">Toto téma obsahuje také seznam obsahu vlastnosti pro každý model obsahu.</span><span class="sxs-lookup"><span data-stu-id="8c523-107">This topic also lists the content properties for each content model.</span></span> <span data-ttu-id="8c523-108">Vlastnost obsahu má vlastnost, která se používá k ukládání obsahu objektu.</span><span class="sxs-lookup"><span data-stu-id="8c523-108">A content property is a property that is used to store the content of the object.</span></span>  

<a name="classes_that_contain_arbitrary_content"></a>   
## <a name="classes-that-contain-arbitrary-content"></a><span data-ttu-id="8c523-109">Třídy, které obsahují libovolný obsah</span><span class="sxs-lookup"><span data-stu-id="8c523-109">Classes That Contain Arbitrary Content</span></span>  
 <span data-ttu-id="8c523-110">Některé ovládací prvky mohou obsahovat objekt typu, jako je řetězec, <xref:System.DateTime> objektu, nebo <xref:System.Windows.UIElement> , který je kontejnerem pro další položky.</span><span class="sxs-lookup"><span data-stu-id="8c523-110">Some controls can contain an object of any type, such as a string, a <xref:System.DateTime> object, or a <xref:System.Windows.UIElement> that is a container for additional items.</span></span> <span data-ttu-id="8c523-111">Například <xref:System.Windows.Controls.Button> může obsahovat obrázek a text; nebo <xref:System.Windows.Controls.CheckBox> může obsahovat hodnotu <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8c523-111">For example, a <xref:System.Windows.Controls.Button> can contain an image and some text; or a <xref:System.Windows.Controls.CheckBox> can contain the value of <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.</span></span>  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="8c523-112">má čtyři třídy, které mohou obsahovat libovolný obsah.</span><span class="sxs-lookup"><span data-stu-id="8c523-112">has four classes that can contain arbitrary content.</span></span> <span data-ttu-id="8c523-113">V následující tabulce jsou uvedeny třídy, které dědí nastavení z <xref:System.Windows.Controls.Control>.</span><span class="sxs-lookup"><span data-stu-id="8c523-113">The following table lists the classes, which inherit from <xref:System.Windows.Controls.Control>.</span></span>  
  
|<span data-ttu-id="8c523-114">Třída, která obsahuje libovolný obsah</span><span class="sxs-lookup"><span data-stu-id="8c523-114">Class that contains arbitrary content</span></span>|<span data-ttu-id="8c523-115">Obsah</span><span class="sxs-lookup"><span data-stu-id="8c523-115">Content</span></span>|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="8c523-116">Jeden libovolný objekt.</span><span class="sxs-lookup"><span data-stu-id="8c523-116">A single arbitrary object.</span></span>|  
|<xref:System.Windows.Controls.HeaderedContentControl>|<span data-ttu-id="8c523-117">Záhlaví a jednu položku, které jsou libovolné objekty.</span><span class="sxs-lookup"><span data-stu-id="8c523-117">A header and a single item, both of which are arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.ItemsControl>|<span data-ttu-id="8c523-118">Kolekci libovolného objektů.</span><span class="sxs-lookup"><span data-stu-id="8c523-118">A collection of arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|<span data-ttu-id="8c523-119">Záhlaví a kolekci položek, z nichž všechny jsou libovolné objekty.</span><span class="sxs-lookup"><span data-stu-id="8c523-119">A header and a collection of items, all of which are arbitrary objects.</span></span>|  
  
 <span data-ttu-id="8c523-120">Ovládací prvky, které dědí z těchto tříd může obsahovat stejné typu obsahu a zpracovávat obsah stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="8c523-120">Controls that inherit from these classes can contain the same type of content and treat the content in the same way.</span></span> <span data-ttu-id="8c523-121">Následující obrázek znázorňuje jeden ovládací prvek z každý model obsahu, který obsahuje obrázek a text:</span><span class="sxs-lookup"><span data-stu-id="8c523-121">The following illustration shows one control from each content model that contains an image and some text:</span></span>  
  
 ![Snímek obrazovky zobrazující čtyři různé ovládací prvky, jeden z každé obsahu modelu.](./media/wpf-content-model/control-content-model-image-text.png)  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a><span data-ttu-id="8c523-123">Ovládací prvky, které obsahují jednoho libovolného objektu</span><span class="sxs-lookup"><span data-stu-id="8c523-123">Controls That Contain a Single Arbitrary Object</span></span>  
 <span data-ttu-id="8c523-124"><xref:System.Windows.Controls.ContentControl> Třída obsahuje jediný libovolný obsah.</span><span class="sxs-lookup"><span data-stu-id="8c523-124">The <xref:System.Windows.Controls.ContentControl> class contains a single piece of arbitrary content.</span></span> <span data-ttu-id="8c523-125">Jeho vlastnost obsahu má <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="8c523-125">Its content property is <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="8c523-126">Následující ovládací prvky automaticky dědí z <xref:System.Windows.Controls.ContentControl> a použijte svůj model obsahu:</span><span class="sxs-lookup"><span data-stu-id="8c523-126">The following controls inherit from <xref:System.Windows.Controls.ContentControl> and use its content model:</span></span>  
  
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
  
 <span data-ttu-id="8c523-127">Následující obrázek znázorňuje čtyři tlačítka, jehož <xref:System.Windows.Controls.ContentControl.Content%2A> nastavený na řetězec, <xref:System.DateTime> objektu, <xref:System.Windows.Shapes.Rectangle>a <xref:System.Windows.Controls.Panel> , který obsahuje <xref:System.Windows.Shapes.Ellipse> a <xref:System.Windows.Controls.TextBlock>:</span><span class="sxs-lookup"><span data-stu-id="8c523-127">The following illustration shows four buttons whose <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a string, a <xref:System.DateTime> object, a <xref:System.Windows.Shapes.Rectangle>, and a <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>:</span></span>  
  
 ![Snímek obrazovky zobrazující čtyři tlačítka s různými typy obsahu.](./media/wpf-content-model/control-content-model-buttons.png)  
  
 <span data-ttu-id="8c523-129">Příklad toho, jak nastavit <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost, naleznete v tématu <xref:System.Windows.Controls.ContentControl>.</span><span class="sxs-lookup"><span data-stu-id="8c523-129">For an example of how to set the <xref:System.Windows.Controls.ContentControl.Content%2A> property, see <xref:System.Windows.Controls.ContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a><span data-ttu-id="8c523-130">Ovládací prvky, které obsahují záhlaví a jednoho libovolného objektu</span><span class="sxs-lookup"><span data-stu-id="8c523-130">Controls That Contain a Header and a Single Arbitrary Object</span></span>  
 <span data-ttu-id="8c523-131"><xref:System.Windows.Controls.HeaderedContentControl> Třída dědí z <xref:System.Windows.Controls.ContentControl> a zobrazí obsah s hlavičkou.</span><span class="sxs-lookup"><span data-stu-id="8c523-131">The <xref:System.Windows.Controls.HeaderedContentControl> class inherits from <xref:System.Windows.Controls.ContentControl> and displays content with a header.</span></span> <span data-ttu-id="8c523-132">Dědí vlastnost obsahu <xref:System.Windows.Controls.ContentControl.Content%2A>, z <xref:System.Windows.Controls.ContentControl> a definuje <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> vlastnost, která je typu <xref:System.Object>, proto může být libovolný objekt.</span><span class="sxs-lookup"><span data-stu-id="8c523-132">It inherits the content property, <xref:System.Windows.Controls.ContentControl.Content%2A>, from <xref:System.Windows.Controls.ContentControl> and defines the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> property that is of type <xref:System.Object>; therefore, both can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="8c523-133">Následující ovládací prvky automaticky dědí z <xref:System.Windows.Controls.HeaderedContentControl> a použijte svůj model obsahu:</span><span class="sxs-lookup"><span data-stu-id="8c523-133">The following controls inherit from <xref:System.Windows.Controls.HeaderedContentControl> and use its content model:</span></span>  
  
-   <xref:System.Windows.Controls.Expander>  
  
-   <xref:System.Windows.Controls.GroupBox>  
  
-   <xref:System.Windows.Controls.TabItem>  
  
 <span data-ttu-id="8c523-134">Následující obrázek ukazuje dva <xref:System.Windows.Controls.TabItem> objekty.</span><span class="sxs-lookup"><span data-stu-id="8c523-134">The following illustration shows two <xref:System.Windows.Controls.TabItem> objects.</span></span> <span data-ttu-id="8c523-135">První <xref:System.Windows.Controls.TabItem> má <xref:System.Windows.UIElement> objektů, jako <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> a <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="8c523-135">The first <xref:System.Windows.Controls.TabItem> has <xref:System.Windows.UIElement> objects as the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="8c523-136"><xref:System.Windows.Controls.HeaderedContentControl.Header%2A> Je nastavena na <xref:System.Windows.Controls.StackPanel> , který obsahuje <xref:System.Windows.Shapes.Ellipse> a <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="8c523-136">The <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="8c523-137"><xref:System.Windows.Controls.ContentControl.Content%2A> Je nastavena na <xref:System.Windows.Controls.StackPanel> , která obsahuje <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="8c523-137">The <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains a <xref:System.Windows.Controls.TextBlock> and a <xref:System.Windows.Controls.Label>.</span></span> <span data-ttu-id="8c523-138">Druhá <xref:System.Windows.Controls.TabItem> má řetězec <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> a <xref:System.Windows.Controls.TextBlock> v <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="8c523-138">The second <xref:System.Windows.Controls.TabItem> has a string in the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and a <xref:System.Windows.Controls.TextBlock> in the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span>  
  
 ![TabControl –, který používá různé typy ve vlastnosti záhlaví.](./media/wpf-content-model/control-content-model-tab.png)  
  
 <span data-ttu-id="8c523-140">Příklad toho, jak vytvořit <xref:System.Windows.Controls.TabItem> objekty, najdete <xref:System.Windows.Controls.HeaderedContentControl>.</span><span class="sxs-lookup"><span data-stu-id="8c523-140">For an example of how to create <xref:System.Windows.Controls.TabItem> objects, see <xref:System.Windows.Controls.HeaderedContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a><span data-ttu-id="8c523-141">Ovládací prvky, které obsahují kolekci libovolného objektů</span><span class="sxs-lookup"><span data-stu-id="8c523-141">Controls That Contain a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="8c523-142"><xref:System.Windows.Controls.ItemsControl> Třída dědí z <xref:System.Windows.Controls.Control> a může obsahovat několik položek, jako je například řetězce, objekty nebo další prvky.</span><span class="sxs-lookup"><span data-stu-id="8c523-142">The <xref:System.Windows.Controls.ItemsControl> class inherits from <xref:System.Windows.Controls.Control> and can contain multiple items, such as strings, objects, or other elements.</span></span> <span data-ttu-id="8c523-143">Jsou jeho vlastnosti obsahu <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> a <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span><span class="sxs-lookup"><span data-stu-id="8c523-143">Its content properties are <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> and <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span></span> <span data-ttu-id="8c523-144"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> Obvykle se používá k naplnění <xref:System.Windows.Controls.ItemsControl> se shromažďováním dat.</span><span class="sxs-lookup"><span data-stu-id="8c523-144"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> is typically used to populate the <xref:System.Windows.Controls.ItemsControl> with a data collection.</span></span> <span data-ttu-id="8c523-145">Pokud nechcete používat kolekce k naplnění <xref:System.Windows.Controls.ItemsControl>, můžete přidat položky pomocí <xref:System.Windows.Controls.ItemsControl.Items%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8c523-145">If you do not want to use a collection to populate the <xref:System.Windows.Controls.ItemsControl>, you can add items by using the <xref:System.Windows.Controls.ItemsControl.Items%2A> property.</span></span>  
  
 <span data-ttu-id="8c523-146">Následující ovládací prvky automaticky dědí z <xref:System.Windows.Controls.ItemsControl> a použijte svůj model obsahu:</span><span class="sxs-lookup"><span data-stu-id="8c523-146">The following controls inherit from <xref:System.Windows.Controls.ItemsControl> and use its content model:</span></span>  
  
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
  
 <span data-ttu-id="8c523-147">Následující ilustrace ukazuje <xref:System.Windows.Controls.ListBox> , která obsahuje tyto typy položek:</span><span class="sxs-lookup"><span data-stu-id="8c523-147">The following illustration shows a <xref:System.Windows.Controls.ListBox> that contains these types of items:</span></span>  
  
-   <span data-ttu-id="8c523-148">Řetězec.</span><span class="sxs-lookup"><span data-stu-id="8c523-148">A string.</span></span>  
  
-   <span data-ttu-id="8c523-149">A <xref:System.DateTime> objektu.</span><span class="sxs-lookup"><span data-stu-id="8c523-149">A <xref:System.DateTime> object.</span></span>  
  
-   <span data-ttu-id="8c523-150">A <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="8c523-150">A <xref:System.Windows.UIElement>.</span></span>  
  
-   <span data-ttu-id="8c523-151">A <xref:System.Windows.Controls.Panel> , který obsahuje <xref:System.Windows.Shapes.Ellipse> a <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="8c523-151">A <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 ![Snímek obrazovky zobrazující prvku ListBox s čtyři typy obsahu.](./media/wpf-content-model/control-content-model-listbox.png)  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a><span data-ttu-id="8c523-153">Ovládací prvky, které obsahují záhlaví a kolekce objektů libovolného</span><span class="sxs-lookup"><span data-stu-id="8c523-153">Controls That Contain a Header and a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="8c523-154"><xref:System.Windows.Controls.HeaderedItemsControl> Třída dědí z <xref:System.Windows.Controls.ItemsControl> a může obsahovat několik položek, jako jsou řetězce, objekty, nebo další prvky a záhlaví.</span><span class="sxs-lookup"><span data-stu-id="8c523-154">The <xref:System.Windows.Controls.HeaderedItemsControl> class inherits from <xref:System.Windows.Controls.ItemsControl> and can contain multiple items, such as strings, objects, or other elements, and a header.</span></span> <span data-ttu-id="8c523-155">Dědí <xref:System.Windows.Controls.ItemsControl> obsah vlastnosti <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, a <xref:System.Windows.Controls.ItemsControl.Items%2A>, a definuje <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> vlastnost, která může být libovolný objekt.</span><span class="sxs-lookup"><span data-stu-id="8c523-155">It inherits the <xref:System.Windows.Controls.ItemsControl> content properties, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, and <xref:System.Windows.Controls.ItemsControl.Items%2A>, and it defines the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property that can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="8c523-156">Následující ovládací prvky automaticky dědí z <xref:System.Windows.Controls.HeaderedItemsControl> a použijte svůj model obsahu:</span><span class="sxs-lookup"><span data-stu-id="8c523-156">The following controls inherit from <xref:System.Windows.Controls.HeaderedItemsControl> and use its content model:</span></span>  
  
-   <xref:System.Windows.Controls.MenuItem>  
  
-   <xref:System.Windows.Controls.ToolBar>  
  
-   <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>   
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a><span data-ttu-id="8c523-157">Třídy, které obsahují kolekci objektů UIElement</span><span class="sxs-lookup"><span data-stu-id="8c523-157">Classes That Contain a Collection of UIElement Objects</span></span>  
 <span data-ttu-id="8c523-158"><xref:System.Windows.Controls.Panel> Třídy umístění a uspořádá podřízené <xref:System.Windows.UIElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="8c523-158">The <xref:System.Windows.Controls.Panel> class positions and arranges child <xref:System.Windows.UIElement> objects.</span></span> <span data-ttu-id="8c523-159">Jeho vlastnost obsahu má <xref:System.Windows.Controls.Panel.Children%2A>.</span><span class="sxs-lookup"><span data-stu-id="8c523-159">Its content property is <xref:System.Windows.Controls.Panel.Children%2A>.</span></span>  
  
 <span data-ttu-id="8c523-160">Následující třídy dědí <xref:System.Windows.Controls.Panel> třídy a použijte svůj model obsahu:</span><span class="sxs-lookup"><span data-stu-id="8c523-160">The following classes inherit from the <xref:System.Windows.Controls.Panel> class and use its content model:</span></span>  
  
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
  
 <span data-ttu-id="8c523-161">Další informace najdete v tématu [přehled panelů](panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8c523-161">For more information, see [Panels Overview](panels-overview.md).</span></span>  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>   
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a><span data-ttu-id="8c523-162">Třídy, které mají vliv na vzhled elementu UIElement</span><span class="sxs-lookup"><span data-stu-id="8c523-162">Classes That Affect the Appearance of a UIElement</span></span>  
 <span data-ttu-id="8c523-163"><xref:System.Windows.Controls.Decorator> Použije vizuální efekty na nebo okolo jednu podřízenou třídu <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="8c523-163">The <xref:System.Windows.Controls.Decorator> class applies visual effects onto or around a single child <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="8c523-164">Jeho vlastnost obsahu má <xref:System.Windows.Controls.Decorator.Child%2A>.</span><span class="sxs-lookup"><span data-stu-id="8c523-164">Its content property is <xref:System.Windows.Controls.Decorator.Child%2A>.</span></span> <span data-ttu-id="8c523-165">Následující třídy dědí <xref:System.Windows.Controls.Decorator> a použijte svůj model obsahu:</span><span class="sxs-lookup"><span data-stu-id="8c523-165">The following classes inherit from <xref:System.Windows.Controls.Decorator> and use its content model:</span></span>  
  
-   <xref:System.Windows.Documents.AdornerDecorator>  
  
-   <xref:System.Windows.Controls.Border>  
  
-   <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
-   <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
-   <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
-   <xref:System.Windows.Controls.InkPresenter>  
  
-   <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
-   <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
-   <xref:System.Windows.Controls.Viewbox>  
  
 <span data-ttu-id="8c523-166">Následující ilustrace ukazuje <xref:System.Windows.Controls.TextBox> , který má (je doplněn) <xref:System.Windows.Controls.Border> kolem něj.</span><span class="sxs-lookup"><span data-stu-id="8c523-166">The following illustration shows a <xref:System.Windows.Controls.TextBox> that has (is decorated with) a <xref:System.Windows.Controls.Border> around it.</span></span>  
  
 <span data-ttu-id="8c523-167">![Textové pole s černým ohraničením](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span><span class="sxs-lookup"><span data-stu-id="8c523-167">![TextBox with black border](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span></span>  
<span data-ttu-id="8c523-168">TextBlock –, který má ohraničení</span><span class="sxs-lookup"><span data-stu-id="8c523-168">TextBlock that has a Border</span></span>  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>   
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a><span data-ttu-id="8c523-169">Třídy, které poskytují vizuální zpětnou vazbu o prvku UIElement</span><span class="sxs-lookup"><span data-stu-id="8c523-169">Classes That Provide Visual Feedback About a UIElement</span></span>  
 <span data-ttu-id="8c523-170"><xref:System.Windows.Documents.Adorner> Třída poskytuje vizuální upozornění na uživatele.</span><span class="sxs-lookup"><span data-stu-id="8c523-170">The <xref:System.Windows.Documents.Adorner> class provides visual cues to a user.</span></span> <span data-ttu-id="8c523-171">Například použít <xref:System.Windows.Documents.Adorner> přidat funkční zpracovává na prvky nebo poskytují informace o ovládací prvek stavu.</span><span class="sxs-lookup"><span data-stu-id="8c523-171">For example, use an <xref:System.Windows.Documents.Adorner> to add functional handles to elements or provide state information about a control.</span></span> <span data-ttu-id="8c523-172"><xref:System.Windows.Documents.Adorner> Třída poskytuje rozhraní, takže můžete vytvářet vlastní doplňky pro úpravy.</span><span class="sxs-lookup"><span data-stu-id="8c523-172">The <xref:System.Windows.Documents.Adorner> class provides a framework so that you can create your own adorners.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="8c523-173">neposkytuje žádné implementované doplňků pro úpravy.</span><span class="sxs-lookup"><span data-stu-id="8c523-173">does not provide any implemented adorners.</span></span> <span data-ttu-id="8c523-174">Další informace najdete v tématu [přehled doplňků pro úpravy](adorners-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8c523-174">For more information, see [Adorners Overview](adorners-overview.md).</span></span>  
  
<a name="classes_that_enable_users_to_enter_text"></a>   
## <a name="classes-that-enable-users-to-enter-text"></a><span data-ttu-id="8c523-175">Třídy, které umožňují uživatelům zadávat Text</span><span class="sxs-lookup"><span data-stu-id="8c523-175">Classes That Enable Users to Enter Text</span></span>  
 <span data-ttu-id="8c523-176">WPF poskytuje tři primární ovládací prvky, které umožňují uživatelům zadávat text.</span><span class="sxs-lookup"><span data-stu-id="8c523-176">WPF provides three primary controls that enable users to enter text.</span></span> <span data-ttu-id="8c523-177">Každý ovládací prvek zobrazí text jiným způsobem.</span><span class="sxs-lookup"><span data-stu-id="8c523-177">Each control displays the text differently.</span></span> <span data-ttu-id="8c523-178">V následující tabulce jsou uvedeny tyto tři text související ovládací prvky, jejich možnosti při jejich zobrazení textu a jejich vlastností, které obsahují text ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8c523-178">The following table lists these three text-related controls, their capabilities when they display text, and their properties that contain the control's text.</span></span>  
  
|<span data-ttu-id="8c523-179">Control</span><span class="sxs-lookup"><span data-stu-id="8c523-179">Control</span></span>|<span data-ttu-id="8c523-180">Text se zobrazí jako</span><span class="sxs-lookup"><span data-stu-id="8c523-180">Text is displayed as</span></span>|<span data-ttu-id="8c523-181">Vlastnost obsahu</span><span class="sxs-lookup"><span data-stu-id="8c523-181">Content property</span></span>|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|<span data-ttu-id="8c523-182">Prostý text</span><span class="sxs-lookup"><span data-stu-id="8c523-182">Plain text</span></span>|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|<span data-ttu-id="8c523-183">Formátovaný text</span><span class="sxs-lookup"><span data-stu-id="8c523-183">Formatted text</span></span>|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|<span data-ttu-id="8c523-184">Skrytý text (znaky jsou maskována)</span><span class="sxs-lookup"><span data-stu-id="8c523-184">Hidden text (characters are masked)</span></span>|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>   
## <a name="classes-that-display-your-text"></a><span data-ttu-id="8c523-185">Třídy, které se zobrazí váš Text</span><span class="sxs-lookup"><span data-stu-id="8c523-185">Classes That Display Your Text</span></span>  
 <span data-ttu-id="8c523-186">Několik tříd lze použít k zobrazení prostý nebo formátovaný text.</span><span class="sxs-lookup"><span data-stu-id="8c523-186">Several classes can be used to display plain or formatted text.</span></span> <span data-ttu-id="8c523-187">Můžete použít <xref:System.Windows.Controls.TextBlock> zobrazíte malé množství textu.</span><span class="sxs-lookup"><span data-stu-id="8c523-187">You can use <xref:System.Windows.Controls.TextBlock> to display small amounts of text.</span></span> <span data-ttu-id="8c523-188">Pokud chcete pro zobrazení velkého množství textu, použijte <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, nebo <xref:System.Windows.Controls.FlowDocumentScrollViewer> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="8c523-188">If you want to display large amounts of text, use the <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, or <xref:System.Windows.Controls.FlowDocumentScrollViewer> controls.</span></span>  
  
 <span data-ttu-id="8c523-189"><xref:System.Windows.Controls.TextBlock> Má dvě vlastnosti obsahu: <xref:System.Windows.Controls.TextBlock.Text%2A> a <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span><span class="sxs-lookup"><span data-stu-id="8c523-189">The <xref:System.Windows.Controls.TextBlock> has two content properties: <xref:System.Windows.Controls.TextBlock.Text%2A> and <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span></span> <span data-ttu-id="8c523-190">Pokud chcete zobrazit text, který používá formátování konzistentní vzhledem k aplikacím <xref:System.Windows.Controls.TextBlock.Text%2A> vlastnost je často nejlepší volbou.</span><span class="sxs-lookup"><span data-stu-id="8c523-190">When you want to display text that uses consistent formatting, the <xref:System.Windows.Controls.TextBlock.Text%2A> property is often your best choice.</span></span> <span data-ttu-id="8c523-191">Pokud budete chtít použít odlišné formátování všude v textu, použijte <xref:System.Windows.Controls.TextBlock.Inlines%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8c523-191">If you plan to use different formatting throughout the text, use the <xref:System.Windows.Controls.TextBlock.Inlines%2A> property.</span></span> <span data-ttu-id="8c523-192"><xref:System.Windows.Controls.TextBlock.Inlines%2A> Vlastnost je kolekce <xref:System.Windows.Documents.Inline> objekty, které určují způsob formátování textu.</span><span class="sxs-lookup"><span data-stu-id="8c523-192">The <xref:System.Windows.Controls.TextBlock.Inlines%2A> property is a collection of <xref:System.Windows.Documents.Inline> objects, which specify how to format text.</span></span>  
  
 <span data-ttu-id="8c523-193">V následující tabulce jsou uvedeny vlastnost obsahu pro <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, a <xref:System.Windows.Controls.FlowDocumentScrollViewer> třídy.</span><span class="sxs-lookup"><span data-stu-id="8c523-193">The following table lists the content property for <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, and <xref:System.Windows.Controls.FlowDocumentScrollViewer> classes.</span></span>  
  
|<span data-ttu-id="8c523-194">Control</span><span class="sxs-lookup"><span data-stu-id="8c523-194">Control</span></span>|<span data-ttu-id="8c523-195">Vlastnost obsahu</span><span class="sxs-lookup"><span data-stu-id="8c523-195">Content property</span></span>|<span data-ttu-id="8c523-196">Typ obsahu vlastnosti</span><span class="sxs-lookup"><span data-stu-id="8c523-196">Content property type</span></span>|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|<span data-ttu-id="8c523-197">Dokument</span><span class="sxs-lookup"><span data-stu-id="8c523-197">Document</span></span>|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|<span data-ttu-id="8c523-198">Dokument</span><span class="sxs-lookup"><span data-stu-id="8c523-198">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|<span data-ttu-id="8c523-199">Dokument</span><span class="sxs-lookup"><span data-stu-id="8c523-199">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
  
 <span data-ttu-id="8c523-200"><xref:System.Windows.Documents.FlowDocument> Implementuje <xref:System.Windows.Documents.IDocumentPaginatorSource> rozhraní; proto můžete provést všechny třídy <xref:System.Windows.Documents.FlowDocument> jako obsah.</span><span class="sxs-lookup"><span data-stu-id="8c523-200">The <xref:System.Windows.Documents.FlowDocument> implements the <xref:System.Windows.Documents.IDocumentPaginatorSource> interface; therefore, all three classes can take a <xref:System.Windows.Documents.FlowDocument> as content.</span></span>  
  
<a name="classes_that_format_text"></a>   
## <a name="classes-that-format-your-text"></a><span data-ttu-id="8c523-201">Třídy, které formátování textu</span><span class="sxs-lookup"><span data-stu-id="8c523-201">Classes That Format Your Text</span></span>  
 <span data-ttu-id="8c523-202"><xref:System.Windows.Documents.TextElement> a její související třídy umožňují formátování textu.</span><span class="sxs-lookup"><span data-stu-id="8c523-202"><xref:System.Windows.Documents.TextElement> and its related classes allow you to format text.</span></span> <span data-ttu-id="8c523-203"><xref:System.Windows.Documents.TextElement> objekty obsahují a formátování textu v <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Documents.FlowDocument> objekty.</span><span class="sxs-lookup"><span data-stu-id="8c523-203"><xref:System.Windows.Documents.TextElement> objects contain and format text in <xref:System.Windows.Controls.TextBlock> and <xref:System.Windows.Documents.FlowDocument> objects.</span></span> <span data-ttu-id="8c523-204">Dva hlavní typy <xref:System.Windows.Documents.TextElement> objekty jsou <xref:System.Windows.Documents.Block> elementy a <xref:System.Windows.Documents.Inline> elementy.</span><span class="sxs-lookup"><span data-stu-id="8c523-204">The two primary types of <xref:System.Windows.Documents.TextElement> objects are <xref:System.Windows.Documents.Block> elements and <xref:System.Windows.Documents.Inline> elements.</span></span> <span data-ttu-id="8c523-205">A <xref:System.Windows.Documents.Block> element reprezentuje blok textu, jako jsou odstavce nebo seznamu.</span><span class="sxs-lookup"><span data-stu-id="8c523-205">A <xref:System.Windows.Documents.Block> element represents a block of text, such as a paragraph or list.</span></span> <span data-ttu-id="8c523-206"><xref:System.Windows.Documents.Inline> Element reprezentuje část textu v bloku.</span><span class="sxs-lookup"><span data-stu-id="8c523-206">An <xref:System.Windows.Documents.Inline> element represents a portion of text in a block.</span></span> <span data-ttu-id="8c523-207">Mnoho <xref:System.Windows.Documents.Inline> třídy určit formátování textu, do které se použijí.</span><span class="sxs-lookup"><span data-stu-id="8c523-207">Many <xref:System.Windows.Documents.Inline> classes specify formatting for the text to which they are applied.</span></span> <span data-ttu-id="8c523-208">Každý <xref:System.Windows.Documents.TextElement> má svůj vlastní model obsahu.</span><span class="sxs-lookup"><span data-stu-id="8c523-208">Each <xref:System.Windows.Documents.TextElement> has its own content model.</span></span> <span data-ttu-id="8c523-209">Další informace najdete v tématu [přehled modelu obsahu TextElement](../advanced/textelement-content-model-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8c523-209">For more information, see the [TextElement Content Model Overview](../advanced/textelement-content-model-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c523-210">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c523-210">See also</span></span>

- [<span data-ttu-id="8c523-211">Pokročilé</span><span class="sxs-lookup"><span data-stu-id="8c523-211">Advanced</span></span>](../advanced/index.md)
