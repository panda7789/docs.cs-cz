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
ms.openlocfilehash: a84ab2e66b4e373591fc9365b1c17d0bb0c66713
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738279"
---
# <a name="wpf-content-model"></a><span data-ttu-id="78ba9-102">Model obsahu WPF</span><span class="sxs-lookup"><span data-stu-id="78ba9-102">WPF Content Model</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="78ba9-103">je prezentační platforma, která poskytuje mnoho ovládacích prvků a typů podobných ovládacím prvkům, jejichž hlavním účelem je zobrazení různých typů obsahu.</span><span class="sxs-lookup"><span data-stu-id="78ba9-103">is a presentation platform that provides many controls and control-like types whose primary purpose is to display different types of content.</span></span> <span data-ttu-id="78ba9-104">Chcete-li určit, který ovládací prvek použít nebo který ovládací prvek odvodit z, je vhodné pochopit druhy objektů, které může konkrétní ovládací prvek nejlépe zobrazit.</span><span class="sxs-lookup"><span data-stu-id="78ba9-104">To determine which control to use or which control to derive from, you should understand the kinds of objects a particular control can best display.</span></span>  
  
 <span data-ttu-id="78ba9-105">Toto téma shrnuje model obsahu pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] typy ovládacích prvků a ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="78ba9-105">This topic summarizes the content model for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] control and control-like types.</span></span> <span data-ttu-id="78ba9-106">Model obsahu popisuje, který obsah lze použít v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="78ba9-106">The content model describes what content can be used in a control.</span></span> <span data-ttu-id="78ba9-107">Toto téma obsahuje také seznam vlastností obsahu pro každý model obsahu.</span><span class="sxs-lookup"><span data-stu-id="78ba9-107">This topic also lists the content properties for each content model.</span></span> <span data-ttu-id="78ba9-108">Vlastnost obsahu je vlastnost, která se používá k uložení obsahu objektu.</span><span class="sxs-lookup"><span data-stu-id="78ba9-108">A content property is a property that is used to store the content of the object.</span></span>  

<a name="classes_that_contain_arbitrary_content"></a>   
## <a name="classes-that-contain-arbitrary-content"></a><span data-ttu-id="78ba9-109">Třídy, které obsahují libovolný obsah</span><span class="sxs-lookup"><span data-stu-id="78ba9-109">Classes That Contain Arbitrary Content</span></span>  
 <span data-ttu-id="78ba9-110">Některé ovládací prvky mohou obsahovat objekt libovolného typu, jako je například řetězec, objekt <xref:System.DateTime> nebo <xref:System.Windows.UIElement>, který je kontejnerem pro další položky.</span><span class="sxs-lookup"><span data-stu-id="78ba9-110">Some controls can contain an object of any type, such as a string, a <xref:System.DateTime> object, or a <xref:System.Windows.UIElement> that is a container for additional items.</span></span> <span data-ttu-id="78ba9-111"><xref:System.Windows.Controls.Button> například může obsahovat obrázek a nějaký text; nebo <xref:System.Windows.Controls.CheckBox> může obsahovat hodnotu <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="78ba9-111">For example, a <xref:System.Windows.Controls.Button> can contain an image and some text; or a <xref:System.Windows.Controls.CheckBox> can contain the value of <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.</span></span>  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="78ba9-112">má čtyři třídy, které mohou obsahovat libovolný obsah.</span><span class="sxs-lookup"><span data-stu-id="78ba9-112">has four classes that can contain arbitrary content.</span></span> <span data-ttu-id="78ba9-113">V následující tabulce jsou uvedeny třídy, které dědí z <xref:System.Windows.Controls.Control>.</span><span class="sxs-lookup"><span data-stu-id="78ba9-113">The following table lists the classes, which inherit from <xref:System.Windows.Controls.Control>.</span></span>  
  
|<span data-ttu-id="78ba9-114">Třída, která obsahuje libovolný obsah</span><span class="sxs-lookup"><span data-stu-id="78ba9-114">Class that contains arbitrary content</span></span>|<span data-ttu-id="78ba9-115">Obsah</span><span class="sxs-lookup"><span data-stu-id="78ba9-115">Content</span></span>|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="78ba9-116">Jeden libovolný objekt.</span><span class="sxs-lookup"><span data-stu-id="78ba9-116">A single arbitrary object.</span></span>|  
|<xref:System.Windows.Controls.HeaderedContentControl>|<span data-ttu-id="78ba9-117">Záhlaví a jedna položka, z nichž obě jsou libovolné objekty.</span><span class="sxs-lookup"><span data-stu-id="78ba9-117">A header and a single item, both of which are arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.ItemsControl>|<span data-ttu-id="78ba9-118">Kolekce libovolných objektů.</span><span class="sxs-lookup"><span data-stu-id="78ba9-118">A collection of arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|<span data-ttu-id="78ba9-119">Záhlaví a kolekce položek, všechny, které jsou libovolnými objekty.</span><span class="sxs-lookup"><span data-stu-id="78ba9-119">A header and a collection of items, all of which are arbitrary objects.</span></span>|  
  
 <span data-ttu-id="78ba9-120">Ovládací prvky, které dědí z těchto tříd, mohou obsahovat stejný typ obsahu a zpracovávat obsah stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="78ba9-120">Controls that inherit from these classes can contain the same type of content and treat the content in the same way.</span></span> <span data-ttu-id="78ba9-121">Následující ilustrace znázorňuje jeden ovládací prvek z každého modelu obsahu, který obsahuje obrázek a nějaký text:</span><span class="sxs-lookup"><span data-stu-id="78ba9-121">The following illustration shows one control from each content model that contains an image and some text:</span></span>  
  
 ![Snímek obrazovky zobrazující čtyři různé ovládací prvky, jeden z každého modelu obsahu.](./media/wpf-content-model/control-content-model-image-text.png)  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a><span data-ttu-id="78ba9-123">Ovládací prvky, které obsahují jediný libovolný objekt</span><span class="sxs-lookup"><span data-stu-id="78ba9-123">Controls That Contain a Single Arbitrary Object</span></span>  
 <span data-ttu-id="78ba9-124">Třída <xref:System.Windows.Controls.ContentControl> obsahuje jednu část libovolného obsahu.</span><span class="sxs-lookup"><span data-stu-id="78ba9-124">The <xref:System.Windows.Controls.ContentControl> class contains a single piece of arbitrary content.</span></span> <span data-ttu-id="78ba9-125">Vlastnost obsahu je <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="78ba9-125">Its content property is <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="78ba9-126">Následující ovládací prvky dědí z <xref:System.Windows.Controls.ContentControl> a používají svůj model obsahu:</span><span class="sxs-lookup"><span data-stu-id="78ba9-126">The following controls inherit from <xref:System.Windows.Controls.ContentControl> and use its content model:</span></span>  
  
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
  
 <span data-ttu-id="78ba9-127">Následující ilustrace znázorňuje čtyři tlačítka, jejichž <xref:System.Windows.Controls.ContentControl.Content%2A> je nastavené na řetězec, <xref:System.DateTime> objekt, <xref:System.Windows.Shapes.Rectangle>a <xref:System.Windows.Controls.Panel> obsahující <xref:System.Windows.Shapes.Ellipse> a <xref:System.Windows.Controls.TextBlock>:</span><span class="sxs-lookup"><span data-stu-id="78ba9-127">The following illustration shows four buttons whose <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a string, a <xref:System.DateTime> object, a <xref:System.Windows.Shapes.Rectangle>, and a <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>:</span></span>  
  
 ![Snímek obrazovky, který zobrazuje čtyři tlačítka s různými typy obsahu.](./media/wpf-content-model/control-content-model-buttons.png)  
  
 <span data-ttu-id="78ba9-129">Příklad nastavení vlastnosti <xref:System.Windows.Controls.ContentControl.Content%2A> naleznete v tématu <xref:System.Windows.Controls.ContentControl>.</span><span class="sxs-lookup"><span data-stu-id="78ba9-129">For an example of how to set the <xref:System.Windows.Controls.ContentControl.Content%2A> property, see <xref:System.Windows.Controls.ContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a><span data-ttu-id="78ba9-130">Ovládací prvky, které obsahují záhlaví a jeden libovolný objekt</span><span class="sxs-lookup"><span data-stu-id="78ba9-130">Controls That Contain a Header and a Single Arbitrary Object</span></span>  
 <span data-ttu-id="78ba9-131">Třída <xref:System.Windows.Controls.HeaderedContentControl> dědí z <xref:System.Windows.Controls.ContentControl> a zobrazí obsah s hlavičkou.</span><span class="sxs-lookup"><span data-stu-id="78ba9-131">The <xref:System.Windows.Controls.HeaderedContentControl> class inherits from <xref:System.Windows.Controls.ContentControl> and displays content with a header.</span></span> <span data-ttu-id="78ba9-132">Dědí vlastnost obsahu, <xref:System.Windows.Controls.ContentControl.Content%2A>, z <xref:System.Windows.Controls.ContentControl> a definuje vlastnost <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>, která je typu <xref:System.Object>; Proto obojí může být libovolný objekt.</span><span class="sxs-lookup"><span data-stu-id="78ba9-132">It inherits the content property, <xref:System.Windows.Controls.ContentControl.Content%2A>, from <xref:System.Windows.Controls.ContentControl> and defines the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> property that is of type <xref:System.Object>; therefore, both can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="78ba9-133">Následující ovládací prvky dědí z <xref:System.Windows.Controls.HeaderedContentControl> a používají svůj model obsahu:</span><span class="sxs-lookup"><span data-stu-id="78ba9-133">The following controls inherit from <xref:System.Windows.Controls.HeaderedContentControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.Expander>  
  
- <xref:System.Windows.Controls.GroupBox>  
  
- <xref:System.Windows.Controls.TabItem>  
  
 <span data-ttu-id="78ba9-134">Následující ilustrace znázorňuje dva objekty <xref:System.Windows.Controls.TabItem>.</span><span class="sxs-lookup"><span data-stu-id="78ba9-134">The following illustration shows two <xref:System.Windows.Controls.TabItem> objects.</span></span> <span data-ttu-id="78ba9-135">První <xref:System.Windows.Controls.TabItem> má <xref:System.Windows.UIElement> objekty jako <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> a <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="78ba9-135">The first <xref:System.Windows.Controls.TabItem> has <xref:System.Windows.UIElement> objects as the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="78ba9-136"><xref:System.Windows.Controls.HeaderedContentControl.Header%2A> je nastaveno na <xref:System.Windows.Controls.StackPanel> obsahující <xref:System.Windows.Shapes.Ellipse> a <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="78ba9-136">The <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="78ba9-137"><xref:System.Windows.Controls.ContentControl.Content%2A> je nastaveno na <xref:System.Windows.Controls.StackPanel> obsahující <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="78ba9-137">The <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains a <xref:System.Windows.Controls.TextBlock> and a <xref:System.Windows.Controls.Label>.</span></span> <span data-ttu-id="78ba9-138">Druhý <xref:System.Windows.Controls.TabItem> obsahuje řetězec v <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> a <xref:System.Windows.Controls.TextBlock> v <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="78ba9-138">The second <xref:System.Windows.Controls.TabItem> has a string in the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and a <xref:System.Windows.Controls.TextBlock> in the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span>  
  
 ![TabControl, který ve vlastnosti Header používá jiné typy.](./media/wpf-content-model/control-content-model-tab.png)  
  
 <span data-ttu-id="78ba9-140">Příklad vytváření <xref:System.Windows.Controls.TabItem> objektů naleznete v tématu <xref:System.Windows.Controls.HeaderedContentControl>.</span><span class="sxs-lookup"><span data-stu-id="78ba9-140">For an example of how to create <xref:System.Windows.Controls.TabItem> objects, see <xref:System.Windows.Controls.HeaderedContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a><span data-ttu-id="78ba9-141">Ovládací prvky, které obsahují kolekci libovolných objektů</span><span class="sxs-lookup"><span data-stu-id="78ba9-141">Controls That Contain a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="78ba9-142">Třída <xref:System.Windows.Controls.ItemsControl> dědí z <xref:System.Windows.Controls.Control> a může obsahovat více položek, jako jsou například řetězce, objekty nebo jiné prvky.</span><span class="sxs-lookup"><span data-stu-id="78ba9-142">The <xref:System.Windows.Controls.ItemsControl> class inherits from <xref:System.Windows.Controls.Control> and can contain multiple items, such as strings, objects, or other elements.</span></span> <span data-ttu-id="78ba9-143">Vlastnosti obsahu jsou <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> a <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span><span class="sxs-lookup"><span data-stu-id="78ba9-143">Its content properties are <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> and <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span></span> <span data-ttu-id="78ba9-144"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> se obvykle používá k naplnění <xref:System.Windows.Controls.ItemsControl> kolekcí dat.</span><span class="sxs-lookup"><span data-stu-id="78ba9-144"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> is typically used to populate the <xref:System.Windows.Controls.ItemsControl> with a data collection.</span></span> <span data-ttu-id="78ba9-145">Pokud nechcete použít kolekci k naplnění <xref:System.Windows.Controls.ItemsControl>, můžete přidat položky pomocí vlastnosti <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span><span class="sxs-lookup"><span data-stu-id="78ba9-145">If you do not want to use a collection to populate the <xref:System.Windows.Controls.ItemsControl>, you can add items by using the <xref:System.Windows.Controls.ItemsControl.Items%2A> property.</span></span>  
  
 <span data-ttu-id="78ba9-146">Následující ovládací prvky dědí z <xref:System.Windows.Controls.ItemsControl> a používají svůj model obsahu:</span><span class="sxs-lookup"><span data-stu-id="78ba9-146">The following controls inherit from <xref:System.Windows.Controls.ItemsControl> and use its content model:</span></span>  
  
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
  
 <span data-ttu-id="78ba9-147">Následující obrázek ukazuje <xref:System.Windows.Controls.ListBox>, který obsahuje tyto typy položek:</span><span class="sxs-lookup"><span data-stu-id="78ba9-147">The following illustration shows a <xref:System.Windows.Controls.ListBox> that contains these types of items:</span></span>  
  
- <span data-ttu-id="78ba9-148">Řetězec.</span><span class="sxs-lookup"><span data-stu-id="78ba9-148">A string.</span></span>  
  
- <span data-ttu-id="78ba9-149">A <xref:System.DateTime> objektu.</span><span class="sxs-lookup"><span data-stu-id="78ba9-149">A <xref:System.DateTime> object.</span></span>  
  
- <span data-ttu-id="78ba9-150">A <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="78ba9-150">A <xref:System.Windows.UIElement>.</span></span>  
  
- <span data-ttu-id="78ba9-151"><xref:System.Windows.Controls.Panel> obsahující <xref:System.Windows.Shapes.Ellipse> a <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="78ba9-151">A <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 ![Snímek obrazovky, který zobrazuje seznam se čtyřmi typy obsahu.](./media/wpf-content-model/control-content-model-listbox.png)  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a><span data-ttu-id="78ba9-153">Ovládací prvky, které obsahují záhlaví a kolekci libovolných objektů</span><span class="sxs-lookup"><span data-stu-id="78ba9-153">Controls That Contain a Header and a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="78ba9-154">Třída <xref:System.Windows.Controls.HeaderedItemsControl> dědí z <xref:System.Windows.Controls.ItemsControl> a může obsahovat více položek, jako jsou například řetězce, objekty nebo jiné prvky a záhlaví.</span><span class="sxs-lookup"><span data-stu-id="78ba9-154">The <xref:System.Windows.Controls.HeaderedItemsControl> class inherits from <xref:System.Windows.Controls.ItemsControl> and can contain multiple items, such as strings, objects, or other elements, and a header.</span></span> <span data-ttu-id="78ba9-155">Zdědí <xref:System.Windows.Controls.ItemsControl> vlastnosti obsahu, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>a <xref:System.Windows.Controls.ItemsControl.Items%2A>a definuje vlastnost <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>, která může být libovolný objekt.</span><span class="sxs-lookup"><span data-stu-id="78ba9-155">It inherits the <xref:System.Windows.Controls.ItemsControl> content properties, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, and <xref:System.Windows.Controls.ItemsControl.Items%2A>, and it defines the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property that can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="78ba9-156">Následující ovládací prvky dědí z <xref:System.Windows.Controls.HeaderedItemsControl> a používají svůj model obsahu:</span><span class="sxs-lookup"><span data-stu-id="78ba9-156">The following controls inherit from <xref:System.Windows.Controls.HeaderedItemsControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.MenuItem>  
  
- <xref:System.Windows.Controls.ToolBar>  
  
- <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>   
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a><span data-ttu-id="78ba9-157">Třídy, které obsahují kolekci objektů UIElement</span><span class="sxs-lookup"><span data-stu-id="78ba9-157">Classes That Contain a Collection of UIElement Objects</span></span>  
 <span data-ttu-id="78ba9-158">Třída <xref:System.Windows.Controls.Panel> umisťuje a uspořádá podřízené objekty <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="78ba9-158">The <xref:System.Windows.Controls.Panel> class positions and arranges child <xref:System.Windows.UIElement> objects.</span></span> <span data-ttu-id="78ba9-159">Vlastnost obsahu je <xref:System.Windows.Controls.Panel.Children%2A>.</span><span class="sxs-lookup"><span data-stu-id="78ba9-159">Its content property is <xref:System.Windows.Controls.Panel.Children%2A>.</span></span>  
  
 <span data-ttu-id="78ba9-160">Následující třídy dědí z třídy <xref:System.Windows.Controls.Panel> a používají svůj obsahový model:</span><span class="sxs-lookup"><span data-stu-id="78ba9-160">The following classes inherit from the <xref:System.Windows.Controls.Panel> class and use its content model:</span></span>  
  
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
  
 <span data-ttu-id="78ba9-161">Další informace najdete v tématu [Přehled panelů](panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="78ba9-161">For more information, see [Panels Overview](panels-overview.md).</span></span>  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>   
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a><span data-ttu-id="78ba9-162">Třídy, které mají vliv na vzhled prvku UIElement</span><span class="sxs-lookup"><span data-stu-id="78ba9-162">Classes That Affect the Appearance of a UIElement</span></span>  
 <span data-ttu-id="78ba9-163">Třída <xref:System.Windows.Controls.Decorator> aplikuje vizuální efekty na nebo kolem jedné podřízené <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="78ba9-163">The <xref:System.Windows.Controls.Decorator> class applies visual effects onto or around a single child <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="78ba9-164">Vlastnost obsahu je <xref:System.Windows.Controls.Decorator.Child%2A>.</span><span class="sxs-lookup"><span data-stu-id="78ba9-164">Its content property is <xref:System.Windows.Controls.Decorator.Child%2A>.</span></span> <span data-ttu-id="78ba9-165">Následující třídy dědí z <xref:System.Windows.Controls.Decorator> a používají svůj obsahový model:</span><span class="sxs-lookup"><span data-stu-id="78ba9-165">The following classes inherit from <xref:System.Windows.Controls.Decorator> and use its content model:</span></span>  
  
- <xref:System.Windows.Documents.AdornerDecorator>  
  
- <xref:System.Windows.Controls.Border>  
  
- <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
- <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
- <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
- <xref:System.Windows.Controls.InkPresenter>  
  
- <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
- <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
- <xref:System.Windows.Controls.Viewbox>  
  
 <span data-ttu-id="78ba9-166">Následující obrázek ukazuje <xref:System.Windows.Controls.TextBox>, který má (je upravený s) <xref:System.Windows.Controls.Border> kolem něj.</span><span class="sxs-lookup"><span data-stu-id="78ba9-166">The following illustration shows a <xref:System.Windows.Controls.TextBox> that has (is decorated with) a <xref:System.Windows.Controls.Border> around it.</span></span>  
  
 <span data-ttu-id="78ba9-167">![Textové pole s černým ohraničením](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span><span class="sxs-lookup"><span data-stu-id="78ba9-167">![TextBox with black border](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span></span>  
<span data-ttu-id="78ba9-168">TextBlock s ohraničením</span><span class="sxs-lookup"><span data-stu-id="78ba9-168">TextBlock that has a Border</span></span>  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>   
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a><span data-ttu-id="78ba9-169">Třídy, které poskytují vizuální zpětnou vazbu k prvku UIElement</span><span class="sxs-lookup"><span data-stu-id="78ba9-169">Classes That Provide Visual Feedback About a UIElement</span></span>  
 <span data-ttu-id="78ba9-170">Třída <xref:System.Windows.Documents.Adorner> poskytuje uživatelům vizuální pomůcky.</span><span class="sxs-lookup"><span data-stu-id="78ba9-170">The <xref:System.Windows.Documents.Adorner> class provides visual cues to a user.</span></span> <span data-ttu-id="78ba9-171">Například použijte <xref:System.Windows.Documents.Adorner> k přidání funkčních obslužných rutin do prvků nebo poskytnutí informací o stavu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="78ba9-171">For example, use an <xref:System.Windows.Documents.Adorner> to add functional handles to elements or provide state information about a control.</span></span> <span data-ttu-id="78ba9-172">Třída <xref:System.Windows.Documents.Adorner> poskytuje rozhraní, abyste mohli vytvářet vlastní doplňky.</span><span class="sxs-lookup"><span data-stu-id="78ba9-172">The <xref:System.Windows.Documents.Adorner> class provides a framework so that you can create your own adorners.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="78ba9-173">neposkytuje žádné implementované doplňky.</span><span class="sxs-lookup"><span data-stu-id="78ba9-173">does not provide any implemented adorners.</span></span> <span data-ttu-id="78ba9-174">Další informace najdete v tématu [Přehled doplňků](adorners-overview.md).</span><span class="sxs-lookup"><span data-stu-id="78ba9-174">For more information, see [Adorners Overview](adorners-overview.md).</span></span>  
  
<a name="classes_that_enable_users_to_enter_text"></a>   
## <a name="classes-that-enable-users-to-enter-text"></a><span data-ttu-id="78ba9-175">Třídy, které umožňují uživatelům zadat text</span><span class="sxs-lookup"><span data-stu-id="78ba9-175">Classes That Enable Users to Enter Text</span></span>  
 <span data-ttu-id="78ba9-176">WPF poskytuje tři primární ovládací prvky, které umožňují uživatelům zadat text.</span><span class="sxs-lookup"><span data-stu-id="78ba9-176">WPF provides three primary controls that enable users to enter text.</span></span> <span data-ttu-id="78ba9-177">Každý ovládací prvek zobrazuje text odlišně.</span><span class="sxs-lookup"><span data-stu-id="78ba9-177">Each control displays the text differently.</span></span> <span data-ttu-id="78ba9-178">Následující tabulka uvádí tyto tři ovládací prvky související s textem, jejich možnosti, když zobrazují text a jejich vlastnosti, které obsahují text ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="78ba9-178">The following table lists these three text-related controls, their capabilities when they display text, and their properties that contain the control's text.</span></span>  
  
|<span data-ttu-id="78ba9-179">Control</span><span class="sxs-lookup"><span data-stu-id="78ba9-179">Control</span></span>|<span data-ttu-id="78ba9-180">Text se zobrazí jako</span><span class="sxs-lookup"><span data-stu-id="78ba9-180">Text is displayed as</span></span>|<span data-ttu-id="78ba9-181">Vlastnost obsahu</span><span class="sxs-lookup"><span data-stu-id="78ba9-181">Content property</span></span>|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|<span data-ttu-id="78ba9-182">Prostý text</span><span class="sxs-lookup"><span data-stu-id="78ba9-182">Plain text</span></span>|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|<span data-ttu-id="78ba9-183">Formátovaný text</span><span class="sxs-lookup"><span data-stu-id="78ba9-183">Formatted text</span></span>|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|<span data-ttu-id="78ba9-184">Skrytý text (znaky jsou maskovány)</span><span class="sxs-lookup"><span data-stu-id="78ba9-184">Hidden text (characters are masked)</span></span>|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>   
## <a name="classes-that-display-your-text"></a><span data-ttu-id="78ba9-185">Třídy, které zobrazují váš text</span><span class="sxs-lookup"><span data-stu-id="78ba9-185">Classes That Display Your Text</span></span>  
 <span data-ttu-id="78ba9-186">K zobrazení prostého nebo formátovaného textu lze použít několik tříd.</span><span class="sxs-lookup"><span data-stu-id="78ba9-186">Several classes can be used to display plain or formatted text.</span></span> <span data-ttu-id="78ba9-187">K zobrazení malých objemů textu můžete použít <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="78ba9-187">You can use <xref:System.Windows.Controls.TextBlock> to display small amounts of text.</span></span> <span data-ttu-id="78ba9-188">Chcete-li zobrazit velké množství textu, použijte ovládací prvky <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>nebo <xref:System.Windows.Controls.FlowDocumentScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="78ba9-188">If you want to display large amounts of text, use the <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, or <xref:System.Windows.Controls.FlowDocumentScrollViewer> controls.</span></span>  
  
 <span data-ttu-id="78ba9-189"><xref:System.Windows.Controls.TextBlock> má dvě vlastnosti obsahu: <xref:System.Windows.Controls.TextBlock.Text%2A> a <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span><span class="sxs-lookup"><span data-stu-id="78ba9-189">The <xref:System.Windows.Controls.TextBlock> has two content properties: <xref:System.Windows.Controls.TextBlock.Text%2A> and <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span></span> <span data-ttu-id="78ba9-190">Pokud chcete zobrazit text, který používá konzistentní formátování, je často nejlepší volbou vlastnost <xref:System.Windows.Controls.TextBlock.Text%2A>.</span><span class="sxs-lookup"><span data-stu-id="78ba9-190">When you want to display text that uses consistent formatting, the <xref:System.Windows.Controls.TextBlock.Text%2A> property is often your best choice.</span></span> <span data-ttu-id="78ba9-191">Pokud plánujete použít jiné formátování v celém textu, použijte vlastnost <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span><span class="sxs-lookup"><span data-stu-id="78ba9-191">If you plan to use different formatting throughout the text, use the <xref:System.Windows.Controls.TextBlock.Inlines%2A> property.</span></span> <span data-ttu-id="78ba9-192">Vlastnost <xref:System.Windows.Controls.TextBlock.Inlines%2A> je kolekcí objektů <xref:System.Windows.Documents.Inline>, které určují způsob formátování textu.</span><span class="sxs-lookup"><span data-stu-id="78ba9-192">The <xref:System.Windows.Controls.TextBlock.Inlines%2A> property is a collection of <xref:System.Windows.Documents.Inline> objects, which specify how to format text.</span></span>  
  
 <span data-ttu-id="78ba9-193">V následující tabulce je uveden seznam vlastností obsahu pro třídy <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>a <xref:System.Windows.Controls.FlowDocumentScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="78ba9-193">The following table lists the content property for <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, and <xref:System.Windows.Controls.FlowDocumentScrollViewer> classes.</span></span>  
  
|<span data-ttu-id="78ba9-194">Control</span><span class="sxs-lookup"><span data-stu-id="78ba9-194">Control</span></span>|<span data-ttu-id="78ba9-195">Vlastnost obsahu</span><span class="sxs-lookup"><span data-stu-id="78ba9-195">Content property</span></span>|<span data-ttu-id="78ba9-196">Typ vlastnosti obsahu</span><span class="sxs-lookup"><span data-stu-id="78ba9-196">Content property type</span></span>|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|<span data-ttu-id="78ba9-197">Dokument</span><span class="sxs-lookup"><span data-stu-id="78ba9-197">Document</span></span>|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|<span data-ttu-id="78ba9-198">Dokument</span><span class="sxs-lookup"><span data-stu-id="78ba9-198">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|<span data-ttu-id="78ba9-199">Dokument</span><span class="sxs-lookup"><span data-stu-id="78ba9-199">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
  
 <span data-ttu-id="78ba9-200"><xref:System.Windows.Documents.FlowDocument> implementuje rozhraní <xref:System.Windows.Documents.IDocumentPaginatorSource>; Proto všechny tři třídy mohou přijmout <xref:System.Windows.Documents.FlowDocument> jako obsah.</span><span class="sxs-lookup"><span data-stu-id="78ba9-200">The <xref:System.Windows.Documents.FlowDocument> implements the <xref:System.Windows.Documents.IDocumentPaginatorSource> interface; therefore, all three classes can take a <xref:System.Windows.Documents.FlowDocument> as content.</span></span>  
  
<a name="classes_that_format_text"></a>   
## <a name="classes-that-format-your-text"></a><span data-ttu-id="78ba9-201">Třídy, které naformátují text</span><span class="sxs-lookup"><span data-stu-id="78ba9-201">Classes That Format Your Text</span></span>  
 <span data-ttu-id="78ba9-202"><xref:System.Windows.Documents.TextElement> a související třídy umožňují formátovat text.</span><span class="sxs-lookup"><span data-stu-id="78ba9-202"><xref:System.Windows.Documents.TextElement> and its related classes allow you to format text.</span></span> <span data-ttu-id="78ba9-203"><xref:System.Windows.Documents.TextElement> objekty obsahují a naformátují text v objektech <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="78ba9-203"><xref:System.Windows.Documents.TextElement> objects contain and format text in <xref:System.Windows.Controls.TextBlock> and <xref:System.Windows.Documents.FlowDocument> objects.</span></span> <span data-ttu-id="78ba9-204">Dva primární typy objektů <xref:System.Windows.Documents.TextElement> jsou <xref:System.Windows.Documents.Block> elementy a prvky <xref:System.Windows.Documents.Inline>.</span><span class="sxs-lookup"><span data-stu-id="78ba9-204">The two primary types of <xref:System.Windows.Documents.TextElement> objects are <xref:System.Windows.Documents.Block> elements and <xref:System.Windows.Documents.Inline> elements.</span></span> <span data-ttu-id="78ba9-205">Element <xref:System.Windows.Documents.Block> představuje blok textu, jako je například odstavec nebo seznam.</span><span class="sxs-lookup"><span data-stu-id="78ba9-205">A <xref:System.Windows.Documents.Block> element represents a block of text, such as a paragraph or list.</span></span> <span data-ttu-id="78ba9-206">Element <xref:System.Windows.Documents.Inline> představuje část textu v bloku.</span><span class="sxs-lookup"><span data-stu-id="78ba9-206">An <xref:System.Windows.Documents.Inline> element represents a portion of text in a block.</span></span> <span data-ttu-id="78ba9-207">Mnoho tříd <xref:System.Windows.Documents.Inline> určuje formátování textu, na který jsou aplikovány.</span><span class="sxs-lookup"><span data-stu-id="78ba9-207">Many <xref:System.Windows.Documents.Inline> classes specify formatting for the text to which they are applied.</span></span> <span data-ttu-id="78ba9-208">Každý <xref:System.Windows.Documents.TextElement> má svůj vlastní model obsahu.</span><span class="sxs-lookup"><span data-stu-id="78ba9-208">Each <xref:System.Windows.Documents.TextElement> has its own content model.</span></span> <span data-ttu-id="78ba9-209">Další informace najdete v tématu [Přehled modelu obsahu TextElement](../advanced/textelement-content-model-overview.md).</span><span class="sxs-lookup"><span data-stu-id="78ba9-209">For more information, see the [TextElement Content Model Overview](../advanced/textelement-content-model-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78ba9-210">Viz také:</span><span class="sxs-lookup"><span data-stu-id="78ba9-210">See also</span></span>

- [<span data-ttu-id="78ba9-211">Pokročilé</span><span class="sxs-lookup"><span data-stu-id="78ba9-211">Advanced</span></span>](../advanced/index.md)
