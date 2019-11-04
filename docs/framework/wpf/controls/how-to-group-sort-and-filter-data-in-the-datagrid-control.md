---
title: 'Postupy: seskupení, řazení a filtrování dat v ovládacím prvku DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], sort
- DataGrid [WPF], group
- DataGrid [WPF], filter
ms.assetid: 03345e85-89e3-4aec-9ed0-3b80759df770
ms.openlocfilehash: 2632566b5b55ae641d2750e903bf94cdc681f8f8
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460235"
---
# <a name="how-to-group-sort-and-filter-data-in-the-datagrid-control"></a><span data-ttu-id="66932-102">Postupy: seskupení, řazení a filtrování dat v ovládacím prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="66932-102">How to: Group, sort, and filter data in the DataGrid control</span></span>

<span data-ttu-id="66932-103">Často je užitečné zobrazit data v <xref:System.Windows.Controls.DataGrid> různými způsoby seskupením, řazením a filtrováním dat.</span><span class="sxs-lookup"><span data-stu-id="66932-103">It is often useful to view data in a <xref:System.Windows.Controls.DataGrid> in different ways by grouping, sorting, and filtering the data.</span></span> <span data-ttu-id="66932-104">K seskupení, řazení a filtrování dat v <xref:System.Windows.Controls.DataGrid>je svážete s <xref:System.Windows.Data.CollectionView>, která tyto funkce podporuje.</span><span class="sxs-lookup"><span data-stu-id="66932-104">To group, sort, and filter the data in a <xref:System.Windows.Controls.DataGrid>, you bind it to a <xref:System.Windows.Data.CollectionView> that supports these functions.</span></span> <span data-ttu-id="66932-105">Pak můžete pracovat s daty v <xref:System.Windows.Data.CollectionView> bez vlivu na podkladová zdrojová data.</span><span class="sxs-lookup"><span data-stu-id="66932-105">You can then work with the data in the <xref:System.Windows.Data.CollectionView> without affecting the underlying source data.</span></span> <span data-ttu-id="66932-106">Změny v zobrazení kolekce se projeví v uživatelském rozhraní <xref:System.Windows.Controls.DataGrid> (UI).</span><span class="sxs-lookup"><span data-stu-id="66932-106">The changes in the collection view are reflected in the <xref:System.Windows.Controls.DataGrid> user interface (UI).</span></span>

<span data-ttu-id="66932-107">Třída <xref:System.Windows.Data.CollectionView> poskytuje funkce seskupování a řazení pro zdroj dat, který implementuje rozhraní <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="66932-107">The <xref:System.Windows.Data.CollectionView> class provides grouping and sorting functionality for a data source that implements the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="66932-108">Třída <xref:System.Windows.Data.CollectionViewSource> umožňuje nastavit vlastnosti <xref:System.Windows.Data.CollectionView> z XAML.</span><span class="sxs-lookup"><span data-stu-id="66932-108">The <xref:System.Windows.Data.CollectionViewSource> class enables you to set the properties of a <xref:System.Windows.Data.CollectionView> from XAML.</span></span>

<span data-ttu-id="66932-109">V tomto příkladu je kolekce objektů `Task` svázána s <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="66932-109">In this example, a collection of `Task` objects is bound to a <xref:System.Windows.Data.CollectionViewSource>.</span></span> <span data-ttu-id="66932-110"><xref:System.Windows.Data.CollectionViewSource> slouží jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pro <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="66932-110">The <xref:System.Windows.Data.CollectionViewSource> is used as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="66932-111">Seskupení, řazení a filtrování se provádí na <xref:System.Windows.Data.CollectionViewSource> a zobrazují se v uživatelském rozhraní <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="66932-111">Grouping, sorting, and filtering are performed on the <xref:System.Windows.Data.CollectionViewSource> and are displayed in the <xref:System.Windows.Controls.DataGrid> UI.</span></span>

<span data-ttu-id="66932-112">![Seskupená data v objektu DataGrid](././media/wpf-datagridgroups.png "WPF_DataGridGroups") Seskupená data v objektu DataGrid</span><span class="sxs-lookup"><span data-stu-id="66932-112">![Grouped data in a DataGrid](././media/wpf-datagridgroups.png "WPF_DataGridGroups") Grouped data in a DataGrid</span></span>

## <a name="using-a-collectionviewsource-as-an-itemssource"></a><span data-ttu-id="66932-113">Použití CollectionViewSource jako ItemsSource</span><span class="sxs-lookup"><span data-stu-id="66932-113">Using a CollectionViewSource as an ItemsSource</span></span>

<span data-ttu-id="66932-114">K seskupení, řazení a filtrování dat v ovládacím prvku <xref:System.Windows.Controls.DataGrid> svážete <xref:System.Windows.Controls.DataGrid> s <xref:System.Windows.Data.CollectionView>, které tyto funkce podporují.</span><span class="sxs-lookup"><span data-stu-id="66932-114">To group, sort, and filter data in a <xref:System.Windows.Controls.DataGrid> control, you bind the <xref:System.Windows.Controls.DataGrid> to a <xref:System.Windows.Data.CollectionView> that supports these functions.</span></span> <span data-ttu-id="66932-115">V tomto příkladu je <xref:System.Windows.Controls.DataGrid> svázán s <xref:System.Windows.Data.CollectionViewSource>, která poskytuje tyto funkce pro <xref:System.Collections.Generic.List%601> objektů `Task`.</span><span class="sxs-lookup"><span data-stu-id="66932-115">In this example, the <xref:System.Windows.Controls.DataGrid> is bound to a <xref:System.Windows.Data.CollectionViewSource> that provides these functions for a <xref:System.Collections.Generic.List%601> of `Task` objects.</span></span>

### <a name="to-bind-a-datagrid-to-a-collectionviewsource"></a><span data-ttu-id="66932-116">Svázání prvku DataGrid s CollectionViewSource</span><span class="sxs-lookup"><span data-stu-id="66932-116">To bind a DataGrid to a CollectionViewSource</span></span>

1. <span data-ttu-id="66932-117">Vytvořte kolekci dat, která implementuje rozhraní <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="66932-117">Create a data collection that implements the <xref:System.Collections.IEnumerable> interface.</span></span>

    <span data-ttu-id="66932-118">Použijete-li <xref:System.Collections.Generic.List%601> k vytvoření kolekce, měli byste vytvořit novou třídu, která dědí z <xref:System.Collections.Generic.List%601> namísto vytvoření instance <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="66932-118">If you use <xref:System.Collections.Generic.List%601> to create your collection, you should create a new class that inherits from <xref:System.Collections.Generic.List%601> instead of instantiating an instance of <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="66932-119">To umožňuje vytvořit datovou vazby ke kolekci v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="66932-119">This enables you to data bind to the collection in XAML.</span></span>

    > [!NOTE]
    > <span data-ttu-id="66932-120">Objekty v kolekci musí implementovat <xref:System.ComponentModel.INotifyPropertyChanged> změněné rozhraní a rozhraní <xref:System.ComponentModel.IEditableObject>, aby <xref:System.Windows.Controls.DataGrid> správně reagovala na změny a úpravy vlastností.</span><span class="sxs-lookup"><span data-stu-id="66932-120">The objects in the collection must implement the <xref:System.ComponentModel.INotifyPropertyChanged> changed interface and the <xref:System.ComponentModel.IEditableObject> interface in order for the <xref:System.Windows.Controls.DataGrid> to respond correctly to property changes and edits.</span></span> <span data-ttu-id="66932-121">Další informace najdete v tématu [implementace oznámení změny vlastností](../data/how-to-implement-property-change-notification.md).</span><span class="sxs-lookup"><span data-stu-id="66932-121">For more information, see [Implement Property Change Notification](../data/how-to-implement-property-change-notification.md).</span></span>

    [!code-csharp[DataGrid_GroupSortFilter#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#101)]
    [!code-vb[DataGrid_GroupSortFilter#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#101)]

2. <span data-ttu-id="66932-122">V jazyce XAML vytvořte instanci třídy kolekce a nastavte [direktivu x:Key –](../../xaml-services/x-key-directive.md).</span><span class="sxs-lookup"><span data-stu-id="66932-122">In XAML, create an instance of the collection class and set the [x:Key Directive](../../xaml-services/x-key-directive.md).</span></span>

3. <span data-ttu-id="66932-123">V jazyce XAML vytvořte instanci třídy <xref:System.Windows.Data.CollectionViewSource>, nastavte [direktivu x:Key –](../../xaml-services/x-key-directive.md)a nastavte instanci třídy kolekce jako <xref:System.Windows.Data.CollectionViewSource.Source%2A>.</span><span class="sxs-lookup"><span data-stu-id="66932-123">In XAML, create an instance of the <xref:System.Windows.Data.CollectionViewSource> class, set the [x:Key Directive](../../xaml-services/x-key-directive.md), and set the instance of your collection class as the <xref:System.Windows.Data.CollectionViewSource.Source%2A>.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#201](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml#201)]

4. <span data-ttu-id="66932-124">Vytvořte instanci třídy <xref:System.Windows.Controls.DataGrid> a nastavte vlastnost <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> na <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="66932-124">Create an instance of the <xref:System.Windows.Controls.DataGrid> class, and set the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property to the <xref:System.Windows.Data.CollectionViewSource>.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#002](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#002)]

5. <span data-ttu-id="66932-125">Chcete-li získat přístup k <xref:System.Windows.Data.CollectionViewSource> z kódu, použijte metodu <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> a získejte odkaz na <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="66932-125">To access the <xref:System.Windows.Data.CollectionViewSource> from your code, use the <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> method to get a reference to the <xref:System.Windows.Data.CollectionViewSource>.</span></span>

    [!code-csharp[DataGrid_GroupSortFilter#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#102)]
    [!code-vb[DataGrid_GroupSortFilter#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#102)]

## <a name="grouping-items-in-a-datagrid"></a><span data-ttu-id="66932-126">Seskupení položek v objektu DataGrid</span><span class="sxs-lookup"><span data-stu-id="66932-126">Grouping items in a DataGrid</span></span>

<span data-ttu-id="66932-127">Chcete-li určit, jak jsou položky seskupeny v <xref:System.Windows.Controls.DataGrid>, použijte typ <xref:System.Windows.Data.PropertyGroupDescription> k seskupení položek v zobrazení zdroje.</span><span class="sxs-lookup"><span data-stu-id="66932-127">To specify how items are grouped in a <xref:System.Windows.Controls.DataGrid>, you use the <xref:System.Windows.Data.PropertyGroupDescription> type to group the items in the source view.</span></span>

### <a name="to-group-items-in-a-datagrid-using-xaml"></a><span data-ttu-id="66932-128">Seskupení položek v prvku DataGrid pomocí jazyka XAML</span><span class="sxs-lookup"><span data-stu-id="66932-128">To group items in a DataGrid using XAML</span></span>

1. <span data-ttu-id="66932-129">Vytvořte <xref:System.Windows.Data.PropertyGroupDescription>, který určuje vlastnost, podle které se má seskupit.</span><span class="sxs-lookup"><span data-stu-id="66932-129">Create a <xref:System.Windows.Data.PropertyGroupDescription> that specifies the property to group by.</span></span> <span data-ttu-id="66932-130">Můžete zadat vlastnost v jazyce XAML nebo v kódu.</span><span class="sxs-lookup"><span data-stu-id="66932-130">You can specify the property in XAML or in code.</span></span>

   1. <span data-ttu-id="66932-131">V jazyce XAML nastavte <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> na název vlastnosti, podle které chcete seskupovat.</span><span class="sxs-lookup"><span data-stu-id="66932-131">In XAML, set the <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> to the name of the property to group by.</span></span>

   2. <span data-ttu-id="66932-132">V kódu předejte název vlastnosti k seskupení podle konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="66932-132">In code, pass the name of the property to group by to the constructor.</span></span>

2. <span data-ttu-id="66932-133">Přidejte <xref:System.Windows.Data.PropertyGroupDescription> do kolekce <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="66932-133">Add the <xref:System.Windows.Data.PropertyGroupDescription> to the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> collection.</span></span>

3. <span data-ttu-id="66932-134">Přidáním dalších instancí <xref:System.Windows.Data.PropertyGroupDescription> do kolekce <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> přidáte další úrovně seskupení.</span><span class="sxs-lookup"><span data-stu-id="66932-134">Add additional instances of <xref:System.Windows.Data.PropertyGroupDescription> to the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection to add more levels of grouping.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#012](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#012)]
    [!code-csharp[DataGrid_GroupSortFilter#112](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#112)]
    [!code-vb[DataGrid_GroupSortFilter#112](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#112)]

4. <span data-ttu-id="66932-135">Chcete-li odebrat skupinu, odeberte <xref:System.Windows.Data.PropertyGroupDescription> z kolekce <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A>.</span><span class="sxs-lookup"><span data-stu-id="66932-135">To remove a group, remove the <xref:System.Windows.Data.PropertyGroupDescription> from the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection.</span></span>

5. <span data-ttu-id="66932-136">Chcete-li odebrat všechny skupiny, zavolejte metodu <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> kolekce <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A>.</span><span class="sxs-lookup"><span data-stu-id="66932-136">To remove all groups, call the <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> method of the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection.</span></span>

    [!code-csharp[DataGrid_GroupSortFilter#114](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#114)]
    [!code-vb[DataGrid_GroupSortFilter#114](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#114)]

<span data-ttu-id="66932-137">Pokud jsou položky seskupeny v <xref:System.Windows.Controls.DataGrid>, můžete definovat <xref:System.Windows.Controls.GroupStyle>, která určuje vzhled každé skupiny.</span><span class="sxs-lookup"><span data-stu-id="66932-137">When items are grouped in the <xref:System.Windows.Controls.DataGrid>, you can define a <xref:System.Windows.Controls.GroupStyle> that specifies the appearance of each group.</span></span> <span data-ttu-id="66932-138"><xref:System.Windows.Controls.GroupStyle> použijete tak, že ji přidáte do kolekce <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> prvku DataGrid.</span><span class="sxs-lookup"><span data-stu-id="66932-138">You apply the <xref:System.Windows.Controls.GroupStyle> by adding it to the <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> collection of the DataGrid.</span></span> <span data-ttu-id="66932-139">Pokud máte více úrovní seskupení, můžete pro každou úroveň skupiny použít různé styly.</span><span class="sxs-lookup"><span data-stu-id="66932-139">If you have multiple levels of grouping, you can apply different styles to each group level.</span></span> <span data-ttu-id="66932-140">Styly jsou aplikovány v pořadí, ve kterém jsou definovány.</span><span class="sxs-lookup"><span data-stu-id="66932-140">Styles are applied in the order in which they are defined.</span></span> <span data-ttu-id="66932-141">Například pokud definujete dva styly, použije se jako první na nejvyšší úrovni skupiny řádků.</span><span class="sxs-lookup"><span data-stu-id="66932-141">For example, if you define two styles, the first will be applied to top level row groups.</span></span> <span data-ttu-id="66932-142">Druhý styl bude použit pro všechny skupiny řádků na druhé úrovni a nižší.</span><span class="sxs-lookup"><span data-stu-id="66932-142">The second style will be applied to all row groups at the second level and lower.</span></span> <span data-ttu-id="66932-143"><xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Controls.GroupStyle> je <xref:System.Windows.Data.CollectionViewGroup>, které skupina představuje.</span><span class="sxs-lookup"><span data-stu-id="66932-143">The <xref:System.Windows.FrameworkElement.DataContext%2A> of the <xref:System.Windows.Controls.GroupStyle> is the <xref:System.Windows.Data.CollectionViewGroup> that the group represents.</span></span>

### <a name="to-change-the-appearance-of-row-group-headers"></a><span data-ttu-id="66932-144">Změna vzhledu záhlaví skupin řádků</span><span class="sxs-lookup"><span data-stu-id="66932-144">To change the appearance of row group headers</span></span>

1. <span data-ttu-id="66932-145">Vytvořte <xref:System.Windows.Controls.GroupStyle> definující vzhled skupiny řádků.</span><span class="sxs-lookup"><span data-stu-id="66932-145">Create a <xref:System.Windows.Controls.GroupStyle> that defines the appearance of the row group.</span></span>

2. <span data-ttu-id="66932-146">Vložte <xref:System.Windows.Controls.GroupStyle> dovnitř značek `<DataGrid.GroupStyle>`.</span><span class="sxs-lookup"><span data-stu-id="66932-146">Put the <xref:System.Windows.Controls.GroupStyle> inside the `<DataGrid.GroupStyle>` tags.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#003](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#003)]

## <a name="sorting-items-in-a-datagrid"></a><span data-ttu-id="66932-147">Řazení položek v objektu DataGrid</span><span class="sxs-lookup"><span data-stu-id="66932-147">Sorting items in a DataGrid</span></span>

<span data-ttu-id="66932-148">Chcete-li určit, jak jsou položky seřazeny v <xref:System.Windows.Controls.DataGrid>, použijte typ <xref:System.ComponentModel.SortDescription> k řazení položek v zobrazení zdroje.</span><span class="sxs-lookup"><span data-stu-id="66932-148">To specify how items are sorted in a <xref:System.Windows.Controls.DataGrid>, you use the <xref:System.ComponentModel.SortDescription> type to sort the items in the source view.</span></span>

### <a name="to-sort-items-in-a-datagrid"></a><span data-ttu-id="66932-149">Řazení položek v objektu DataGrid</span><span class="sxs-lookup"><span data-stu-id="66932-149">To sort items in a DataGrid</span></span>

1. <span data-ttu-id="66932-150">Vytvořte <xref:System.ComponentModel.SortDescription>, který určuje vlastnost, podle které se má řadit.</span><span class="sxs-lookup"><span data-stu-id="66932-150">Create a <xref:System.ComponentModel.SortDescription> that specifies the property to sort by.</span></span> <span data-ttu-id="66932-151">Můžete zadat vlastnost v jazyce XAML nebo v kódu.</span><span class="sxs-lookup"><span data-stu-id="66932-151">You can specify the property in XAML or in code.</span></span>

    1. <span data-ttu-id="66932-152">V jazyce XAML nastavte <xref:System.ComponentModel.SortDescription.PropertyName%2A> na název vlastnosti, podle které chcete řadit.</span><span class="sxs-lookup"><span data-stu-id="66932-152">In XAML, set the <xref:System.ComponentModel.SortDescription.PropertyName%2A> to the name of the property to sort by.</span></span>

    2. <span data-ttu-id="66932-153">V kódu předejte název vlastnosti k řazení podle a <xref:System.ComponentModel.ListSortDirection> do konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="66932-153">In code, pass the name of the property to sort by and the <xref:System.ComponentModel.ListSortDirection> to the constructor.</span></span>

2. <span data-ttu-id="66932-154">Přidejte <xref:System.ComponentModel.SortDescription> do kolekce <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="66932-154">Add the <xref:System.ComponentModel.SortDescription> to the <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> collection.</span></span>

3. <span data-ttu-id="66932-155">Přidejte další instance <xref:System.ComponentModel.SortDescription> do kolekce <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> k seřazení podle dalších vlastností.</span><span class="sxs-lookup"><span data-stu-id="66932-155">Add additional instances of <xref:System.ComponentModel.SortDescription> to the <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> collection to sort by additional properties.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#011](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#011)]
    [!code-csharp[DataGrid_GroupSortFilter#211](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml.cs#211)]
    [!code-vb[DataGrid_GroupSortFilter#211](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#211)]

## <a name="filtering-items-in-a-datagrid"></a><span data-ttu-id="66932-156">Filtrování položek v objektu DataGrid</span><span class="sxs-lookup"><span data-stu-id="66932-156">Filtering items in a DataGrid</span></span>

<span data-ttu-id="66932-157">Chcete-li filtrovat položky v <xref:System.Windows.Controls.DataGrid> pomocí <xref:System.Windows.Data.CollectionViewSource>, zadejte logiku filtrování v obslužné rutině pro událost <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="66932-157">To filter items in a <xref:System.Windows.Controls.DataGrid> using a <xref:System.Windows.Data.CollectionViewSource>, you provide the filtering logic in the handler for the <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> event.</span></span>

### <a name="to-filter-items-in-a-datagrid"></a><span data-ttu-id="66932-158">Filtrování položek v prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="66932-158">To filter items in a DataGrid</span></span>

1. <span data-ttu-id="66932-159">Přidejte obslužnou rutinu pro událost <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="66932-159">Add a handler for the <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> event.</span></span>

2. <span data-ttu-id="66932-160">V obslužné rutině události <xref:System.Windows.Data.CollectionViewSource.Filter> definujte logiku filtrování.</span><span class="sxs-lookup"><span data-stu-id="66932-160">In the <xref:System.Windows.Data.CollectionViewSource.Filter> event handler, define the filtering logic.</span></span>

    <span data-ttu-id="66932-161">Filtr bude použit při každém obnovení zobrazení.</span><span class="sxs-lookup"><span data-stu-id="66932-161">The filter will be applied every time the view is refreshed.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#013](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#013)]
    [!code-csharp[DataGrid_GroupSortFilter#113](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#113)]
    [!code-vb[DataGrid_GroupSortFilter#113](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#113)]

<span data-ttu-id="66932-162">Alternativně můžete filtrovat položky v <xref:System.Windows.Controls.DataGrid> vytvořením metody, která poskytuje logiku filtrování a nastavením vlastnosti <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> na použití filtru.</span><span class="sxs-lookup"><span data-stu-id="66932-162">Alternatively, you can filter items in a <xref:System.Windows.Controls.DataGrid> by creating a method that provides the filtering logic and setting the <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> property to apply the filter.</span></span> <span data-ttu-id="66932-163">Příklad této metody najdete v tématu [filtrování dat v zobrazení](../data/how-to-filter-data-in-a-view.md).</span><span class="sxs-lookup"><span data-stu-id="66932-163">To see an example of this method, see [Filter Data in a View](../data/how-to-filter-data-in-a-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="66932-164">Příklad</span><span class="sxs-lookup"><span data-stu-id="66932-164">Example</span></span>

<span data-ttu-id="66932-165">Následující příklad znázorňuje seskupení, řazení a filtrování `Task` dat v <xref:System.Windows.Data.CollectionViewSource> a zobrazení seskupených, seřazených a filtrovaných `Task` dat v <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="66932-165">The following example demonstrates grouping, sorting, and filtering `Task` data in a <xref:System.Windows.Data.CollectionViewSource> and displaying the grouped, sorted, and filtered `Task` data in a <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="66932-166"><xref:System.Windows.Data.CollectionViewSource> slouží jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pro <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="66932-166">The <xref:System.Windows.Data.CollectionViewSource> is used as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="66932-167">Seskupení, řazení a filtrování se provádí na <xref:System.Windows.Data.CollectionViewSource> a zobrazují se v uživatelském rozhraní <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="66932-167">Grouping, sorting, and filtering are performed on the <xref:System.Windows.Data.CollectionViewSource> and are displayed in the <xref:System.Windows.Controls.DataGrid> UI.</span></span>

<span data-ttu-id="66932-168">Chcete-li otestovat tento příklad, budete muset upravit DGGroupSortFilterExample název tak, aby odpovídal názvu projektu.</span><span class="sxs-lookup"><span data-stu-id="66932-168">To test this example, you will need to adjust the DGGroupSortFilterExample name to match your project name.</span></span> <span data-ttu-id="66932-169">Pokud používáte Visual Basic, budete muset změnit název třídy pro <xref:System.Windows.Window> na následující.</span><span class="sxs-lookup"><span data-stu-id="66932-169">If you are using Visual Basic, you will need to change the class name for <xref:System.Windows.Window> to the following.</span></span>

`<Window x:Class="MainWindow"`

[!code-xaml[DataGrid_GroupSortFilter#000](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#000)]
[!code-csharp[DataGrid_GroupSortFilter#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#100)]
[!code-vb[DataGrid_GroupSortFilter#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#100)]

## <a name="see-also"></a><span data-ttu-id="66932-170">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66932-170">See also</span></span>

- [<span data-ttu-id="66932-171">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="66932-171">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="66932-172">Vytvoření a vytvoření vazby ke kolekci ObservableCollection</span><span class="sxs-lookup"><span data-stu-id="66932-172">Create and Bind to an ObservableCollection</span></span>](../data/how-to-create-and-bind-to-an-observablecollection.md)
- [<span data-ttu-id="66932-173">Filtrování dat v zobrazení</span><span class="sxs-lookup"><span data-stu-id="66932-173">Filter Data in a View</span></span>](../data/how-to-filter-data-in-a-view.md)
- [<span data-ttu-id="66932-174">Řazení dat v zobrazení</span><span class="sxs-lookup"><span data-stu-id="66932-174">Sort Data in a View</span></span>](../data/how-to-sort-data-in-a-view.md)
- [<span data-ttu-id="66932-175">Řazení a seskupení dat pomocí zobrazení XAML</span><span class="sxs-lookup"><span data-stu-id="66932-175">Sort and Group Data Using a View in XAML</span></span>](../data/how-to-sort-and-group-data-using-a-view-in-xaml.md)
