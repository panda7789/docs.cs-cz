---
title: 'Postupy: Seskupení, řazení a filtrování dat v ovládacím prvku DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], sort
- DataGrid [WPF], group
- DataGrid [WPF], filter
ms.assetid: 03345e85-89e3-4aec-9ed0-3b80759df770
ms.openlocfilehash: f0f80afd982092248bc52590e072c92784dbcbce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54650454"
---
# <a name="how-to-group-sort-and-filter-data-in-the-datagrid-control"></a><span data-ttu-id="f8d1c-102">Postupy: Seskupení, řazení a filtrování dat v ovládacím prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="f8d1c-102">How to: Group, sort, and filter data in the DataGrid control</span></span>

<span data-ttu-id="f8d1c-103">Často je užitečné, chcete-li zobrazit data <xref:System.Windows.Controls.DataGrid> seskupení, řazení a filtrování dat různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-103">It is often useful to view data in a <xref:System.Windows.Controls.DataGrid> in different ways by grouping, sorting, and filtering the data.</span></span> <span data-ttu-id="f8d1c-104">Seskupení, řazení a filtrování dat v <xref:System.Windows.Controls.DataGrid>, umožňuje vytvořit vazbu <xref:System.Windows.Data.CollectionView> , který podporuje tyto funkce.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-104">To group, sort, and filter the data in a <xref:System.Windows.Controls.DataGrid>, you bind it to a <xref:System.Windows.Data.CollectionView> that supports these functions.</span></span> <span data-ttu-id="f8d1c-105">Pak můžete pracovat s daty v <xref:System.Windows.Data.CollectionView> bez ovlivnění základního zdrojová data.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-105">You can then work with the data in the <xref:System.Windows.Data.CollectionView> without affecting the underlying source data.</span></span> <span data-ttu-id="f8d1c-106">V zobrazení kolekce se projeví v <xref:System.Windows.Controls.DataGrid> uživatelského rozhraní (UI).</span><span class="sxs-lookup"><span data-stu-id="f8d1c-106">The changes in the collection view are reflected in the <xref:System.Windows.Controls.DataGrid> user interface (UI).</span></span>

<span data-ttu-id="f8d1c-107"><xref:System.Windows.Data.CollectionView> Třída poskytuje seskupování a řazení funkce pro zdroj dat, která implementuje <xref:System.Collections.IEnumerable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-107">The <xref:System.Windows.Data.CollectionView> class provides grouping and sorting functionality for a data source that implements the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="f8d1c-108"><xref:System.Windows.Data.CollectionViewSource> Třída umožňuje nastavit vlastnosti <xref:System.Windows.Data.CollectionView> z XAML.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-108">The <xref:System.Windows.Data.CollectionViewSource> class enables you to set the properties of a <xref:System.Windows.Data.CollectionView> from XAML.</span></span>

<span data-ttu-id="f8d1c-109">V tomto příkladu kolekce `Task` objektům svázaným s <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-109">In this example, a collection of `Task` objects is bound to a <xref:System.Windows.Data.CollectionViewSource>.</span></span> <span data-ttu-id="f8d1c-110"><xref:System.Windows.Data.CollectionViewSource> Slouží jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pro <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-110">The <xref:System.Windows.Data.CollectionViewSource> is used as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="f8d1c-111">Seskupení, řazení a filtrování se provádí na <xref:System.Windows.Data.CollectionViewSource> a jsou zobrazeny v <xref:System.Windows.Controls.DataGrid> uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-111">Grouping, sorting, and filtering are performed on the <xref:System.Windows.Data.CollectionViewSource> and are displayed in the <xref:System.Windows.Controls.DataGrid> UI.</span></span>

<span data-ttu-id="f8d1c-112">![Seskupená data do ovládacího prvku DataGrid](./media/wpf-datagridgroups.png "WPF_DataGridGroups") seskupená data do ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="f8d1c-112">![Grouped data in a DataGrid](./media/wpf-datagridgroups.png "WPF_DataGridGroups") Grouped data in a DataGrid</span></span>

## <a name="using-a-collectionviewsource-as-an-itemssource"></a><span data-ttu-id="f8d1c-113">Pomocí kolekce CollectionViewSource jako vlastnost ItemsSource.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-113">Using a CollectionViewSource as an ItemsSource</span></span>

<span data-ttu-id="f8d1c-114">Pro seskupení, řazení a filtrování dat v <xref:System.Windows.Controls.DataGrid> ovládacího prvku, je vytvořit vazbu <xref:System.Windows.Controls.DataGrid> k <xref:System.Windows.Data.CollectionView> , který podporuje tyto funkce.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-114">To group, sort, and filter data in a <xref:System.Windows.Controls.DataGrid> control, you bind the <xref:System.Windows.Controls.DataGrid> to a <xref:System.Windows.Data.CollectionView> that supports these functions.</span></span> <span data-ttu-id="f8d1c-115">V tomto příkladu <xref:System.Windows.Controls.DataGrid> je vázán na <xref:System.Windows.Data.CollectionViewSource> , který poskytuje tyto funkce pro <xref:System.Collections.Generic.List%601> z `Task` objekty.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-115">In this example, the <xref:System.Windows.Controls.DataGrid> is bound to a <xref:System.Windows.Data.CollectionViewSource> that provides these functions for a <xref:System.Collections.Generic.List%601> of `Task` objects.</span></span>

### <a name="to-bind-a-datagrid-to-a-collectionviewsource"></a><span data-ttu-id="f8d1c-116">Kolekce CollectionViewSource vytvořit vazbu ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="f8d1c-116">To bind a DataGrid to a CollectionViewSource</span></span>

1. <span data-ttu-id="f8d1c-117">Vytvořit kolekci dat, která implementuje <xref:System.Collections.IEnumerable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-117">Create a data collection that implements the <xref:System.Collections.IEnumerable> interface.</span></span>

    <span data-ttu-id="f8d1c-118">Pokud používáte <xref:System.Collections.Generic.List%601> k vytvoření kolekce, měli byste vytvořit novou třídu, která dědí z <xref:System.Collections.Generic.List%601> namísto vytvoření instance instance <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-118">If you use <xref:System.Collections.Generic.List%601> to create your collection, you should create a new class that inherits from <xref:System.Collections.Generic.List%601> instead of instantiating an instance of <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="f8d1c-119">To vám umožní vytvořit vazbu na data do kolekce v XAML.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-119">This enables you to data bind to the collection in XAML.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f8d1c-120">Objekty v kolekci musí implementovat <xref:System.ComponentModel.INotifyPropertyChanged> změněné rozhraní a <xref:System.ComponentModel.IEditableObject> rozhraní, aby <xref:System.Windows.Controls.DataGrid> správně reagovat na změny vlastností a úpravy.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-120">The objects in the collection must implement the <xref:System.ComponentModel.INotifyPropertyChanged> changed interface and the <xref:System.ComponentModel.IEditableObject> interface in order for the <xref:System.Windows.Controls.DataGrid> to respond correctly to property changes and edits.</span></span> <span data-ttu-id="f8d1c-121">Další informace najdete v tématu [implementace oznámení změn vlastností](../data/how-to-implement-property-change-notification.md).</span><span class="sxs-lookup"><span data-stu-id="f8d1c-121">For more information, see [Implement Property Change Notification](../data/how-to-implement-property-change-notification.md).</span></span>

    [!code-csharp[DataGrid_GroupSortFilter#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#101)]
    [!code-vb[DataGrid_GroupSortFilter#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#101)]

2. <span data-ttu-id="f8d1c-122">V XAML, vytvoření instance třídy kolekce a nastavte [x: Key – direktiva](../../../../docs/framework/xaml-services/x-key-directive.md).</span><span class="sxs-lookup"><span data-stu-id="f8d1c-122">In XAML, create an instance of the collection class and set the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md).</span></span>

3. <span data-ttu-id="f8d1c-123">V XAML, vytvořte instanci <xref:System.Windows.Data.CollectionViewSource> třídy, nastavte [x: Key – direktiva](../../../../docs/framework/xaml-services/x-key-directive.md)a nastavte instance třídy kolekce jako <xref:System.Windows.Data.CollectionViewSource.Source%2A>.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-123">In XAML, create an instance of the <xref:System.Windows.Data.CollectionViewSource> class, set the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md), and set the instance of your collection class as the <xref:System.Windows.Data.CollectionViewSource.Source%2A>.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#201](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml#201)]

4. <span data-ttu-id="f8d1c-124">Vytvoření instance <xref:System.Windows.Controls.DataGrid> třídy a nastavit <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-124">Create an instance of the <xref:System.Windows.Controls.DataGrid> class, and set the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property to the <xref:System.Windows.Data.CollectionViewSource>.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#002](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#002)]

5. <span data-ttu-id="f8d1c-125">Pro přístup <xref:System.Windows.Data.CollectionViewSource> z vašeho kódu, použijte <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> metodu k získání odkazu na <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-125">To access the <xref:System.Windows.Data.CollectionViewSource> from your code, use the <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> method to get a reference to the <xref:System.Windows.Data.CollectionViewSource>.</span></span>

    [!code-csharp[DataGrid_GroupSortFilter#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#102)]
    [!code-vb[DataGrid_GroupSortFilter#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#102)]

## <a name="grouping-items-in-a-datagrid"></a><span data-ttu-id="f8d1c-126">Seskupení položek do ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="f8d1c-126">Grouping items in a DataGrid</span></span>

<span data-ttu-id="f8d1c-127">K určení způsobu seskupení položek v <xref:System.Windows.Controls.DataGrid>, je použít <xref:System.Windows.Data.PropertyGroupDescription> typ seskupení položek v zobrazení zdroje.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-127">To specify how items are grouped in a <xref:System.Windows.Controls.DataGrid>, you use the <xref:System.Windows.Data.PropertyGroupDescription> type to group the items in the source view.</span></span>

### <a name="to-group-items-in-a-datagrid-using-xaml"></a><span data-ttu-id="f8d1c-128">Seskupit položky v DataGrid pomocí XAML</span><span class="sxs-lookup"><span data-stu-id="f8d1c-128">To group items in a DataGrid using XAML</span></span>

1. <span data-ttu-id="f8d1c-129">Vytvoření <xref:System.Windows.Data.PropertyGroupDescription> , který určuje vlastnost, která má Seskupit podle.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-129">Create a <xref:System.Windows.Data.PropertyGroupDescription> that specifies the property to group by.</span></span> <span data-ttu-id="f8d1c-130">V XAML nebo v kódu, můžete zadat vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-130">You can specify the property in XAML or in code.</span></span>

   1. <span data-ttu-id="f8d1c-131">V XAML, nastavte <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> na název vlastnosti, které chcete seskupit podle.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-131">In XAML, set the <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> to the name of the property to group by.</span></span>

   2. <span data-ttu-id="f8d1c-132">V kódu předejte název vlastnosti Seskupit podle do konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-132">In code, pass the name of the property to group by to the constructor.</span></span>

2. <span data-ttu-id="f8d1c-133">Přidat <xref:System.Windows.Data.PropertyGroupDescription> k <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> kolekce.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-133">Add the <xref:System.Windows.Data.PropertyGroupDescription> to the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> collection.</span></span>

3. <span data-ttu-id="f8d1c-134">Přidat další instance <xref:System.Windows.Data.PropertyGroupDescription> k <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> kolekce přidejte další úrovně seskupení.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-134">Add additional instances of <xref:System.Windows.Data.PropertyGroupDescription> to the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection to add more levels of grouping.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#012](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#012)]
    [!code-csharp[DataGrid_GroupSortFilter#112](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#112)]
    [!code-vb[DataGrid_GroupSortFilter#112](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#112)]

4. <span data-ttu-id="f8d1c-135">Chcete-li odebrat skupinu, odeberte <xref:System.Windows.Data.PropertyGroupDescription> z <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-135">To remove a group, remove the <xref:System.Windows.Data.PropertyGroupDescription> from the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection.</span></span>

5. <span data-ttu-id="f8d1c-136">Chcete-li odebrat všechny skupiny, zavolejte <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> metodu <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-136">To remove all groups, call the <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> method of the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection.</span></span>

    [!code-csharp[DataGrid_GroupSortFilter#114](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#114)]
    [!code-vb[DataGrid_GroupSortFilter#114](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#114)]

<span data-ttu-id="f8d1c-137">Po seskupení položek v <xref:System.Windows.Controls.DataGrid>, můžete definovat <xref:System.Windows.Controls.GroupStyle> , který určuje vzhled každou skupinu.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-137">When items are grouped in the <xref:System.Windows.Controls.DataGrid>, you can define a <xref:System.Windows.Controls.GroupStyle> that specifies the appearance of each group.</span></span> <span data-ttu-id="f8d1c-138">Můžete použít <xref:System.Windows.Controls.GroupStyle> tak, že ji přidáte <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> kolekce v prvku DataGrid.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-138">You apply the <xref:System.Windows.Controls.GroupStyle> by adding it to the <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> collection of the DataGrid.</span></span> <span data-ttu-id="f8d1c-139">Pokud máte více úrovní seskupení můžete použít různé styly pro každou úroveň skupiny.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-139">If you have multiple levels of grouping, you can apply different styles to each group level.</span></span> <span data-ttu-id="f8d1c-140">Styly použijí v pořadí, ve kterém jsou definovány.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-140">Styles are applied in the order in which they are defined.</span></span> <span data-ttu-id="f8d1c-141">Například pokud definujete dvě styly, první se použije u skupin nejvyšší úrovně řádku.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-141">For example, if you define two styles, the first will be applied to top level row groups.</span></span> <span data-ttu-id="f8d1c-142">Druhý styl bude platí pro všechny skupiny řádku na druhé úrovni a nižší.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-142">The second style will be applied to all row groups at the second level and lower.</span></span> <span data-ttu-id="f8d1c-143"><xref:System.Windows.FrameworkElement.DataContext%2A> z <xref:System.Windows.Controls.GroupStyle> je <xref:System.Windows.Data.CollectionViewGroup> , který představuje skupiny.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-143">The <xref:System.Windows.FrameworkElement.DataContext%2A> of the <xref:System.Windows.Controls.GroupStyle> is the <xref:System.Windows.Data.CollectionViewGroup> that the group represents.</span></span>

### <a name="to-change-the-appearance-of-row-group-headers"></a><span data-ttu-id="f8d1c-144">Chcete-li změnit vzhled hlaviček skupiny řádků</span><span class="sxs-lookup"><span data-stu-id="f8d1c-144">To change the appearance of row group headers</span></span>

1. <span data-ttu-id="f8d1c-145">Vytvoření <xref:System.Windows.Controls.GroupStyle> , která definuje vzhled elementů skupinu řádků.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-145">Create a <xref:System.Windows.Controls.GroupStyle> that defines the appearance of the row group.</span></span>

2. <span data-ttu-id="f8d1c-146">Vložit <xref:System.Windows.Controls.GroupStyle> uvnitř `<DataGrid.GroupStyle>` značky.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-146">Put the <xref:System.Windows.Controls.GroupStyle> inside the `<DataGrid.GroupStyle>` tags.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#003](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#003)]

## <a name="sorting-items-in-a-datagrid"></a><span data-ttu-id="f8d1c-147">Řazení položek do ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="f8d1c-147">Sorting items in a DataGrid</span></span>

<span data-ttu-id="f8d1c-148">Chcete-li určit, jak jsou položky seřazeny v <xref:System.Windows.Controls.DataGrid>, použijete <xref:System.ComponentModel.SortDescription> typ řazení položek v zobrazení zdroje.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-148">To specify how items are sorted in a <xref:System.Windows.Controls.DataGrid>, you use the <xref:System.ComponentModel.SortDescription> type to sort the items in the source view.</span></span>

### <a name="to-sort-items-in-a-datagrid"></a><span data-ttu-id="f8d1c-149">Chcete-li seřadit položky ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="f8d1c-149">To sort items in a DataGrid</span></span>

1. <span data-ttu-id="f8d1c-150">Vytvoření <xref:System.ComponentModel.SortDescription> , který určuje vlastnost, která má řadit.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-150">Create a <xref:System.ComponentModel.SortDescription> that specifies the property to sort by.</span></span> <span data-ttu-id="f8d1c-151">V XAML nebo v kódu, můžete zadat vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-151">You can specify the property in XAML or in code.</span></span>

    1. <span data-ttu-id="f8d1c-152">V XAML, nastavte <xref:System.ComponentModel.SortDescription.PropertyName%2A> název vlastnosti, která má řadit.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-152">In XAML, set the <xref:System.ComponentModel.SortDescription.PropertyName%2A> to the name of the property to sort by.</span></span>

    2. <span data-ttu-id="f8d1c-153">V kódu, předejte název vlastnosti seřadit podle a <xref:System.ComponentModel.ListSortDirection> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-153">In code, pass the name of the property to sort by and the <xref:System.ComponentModel.ListSortDirection> to the constructor.</span></span>

2. <span data-ttu-id="f8d1c-154">Přidat <xref:System.ComponentModel.SortDescription> k <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> kolekce.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-154">Add the <xref:System.ComponentModel.SortDescription> to the <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> collection.</span></span>

3. <span data-ttu-id="f8d1c-155">Přidat další instance <xref:System.ComponentModel.SortDescription> k <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> kolekce seřadíte položky podle další vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-155">Add additional instances of <xref:System.ComponentModel.SortDescription> to the <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> collection to sort by additional properties.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#011](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#011)]
    [!code-csharp[DataGrid_GroupSortFilter#211](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml.cs#211)]
    [!code-vb[DataGrid_GroupSortFilter#211](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#211)]

## <a name="filtering-items-in-a-datagrid"></a><span data-ttu-id="f8d1c-156">Filtrování položek do ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="f8d1c-156">Filtering items in a DataGrid</span></span>

<span data-ttu-id="f8d1c-157">Pro filtrování položek v <xref:System.Windows.Controls.DataGrid> pomocí <xref:System.Windows.Data.CollectionViewSource>, poskytuje logiku filtrování v obslužné rutině <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> událostí.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-157">To filter items in a <xref:System.Windows.Controls.DataGrid> using a <xref:System.Windows.Data.CollectionViewSource>, you provide the filtering logic in the handler for the <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> event.</span></span>

### <a name="to-filter-items-in-a-datagrid"></a><span data-ttu-id="f8d1c-158">K filtrování položek do ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="f8d1c-158">To filter items in a DataGrid</span></span>

1. <span data-ttu-id="f8d1c-159">Přidání obslužné rutiny <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> událostí.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-159">Add a handler for the <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> event.</span></span>

2. <span data-ttu-id="f8d1c-160">V <xref:System.Windows.Data.CollectionViewSource.Filter> obslužná rutina události definujte logiku filtrování.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-160">In the <xref:System.Windows.Data.CollectionViewSource.Filter> event handler, define the filtering logic.</span></span>

    <span data-ttu-id="f8d1c-161">Filtr se použijí pokaždé, když je zobrazení aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-161">The filter will be applied every time the view is refreshed.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#013](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#013)]
    [!code-csharp[DataGrid_GroupSortFilter#113](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#113)]
    [!code-vb[DataGrid_GroupSortFilter#113](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#113)]

<span data-ttu-id="f8d1c-162">Alternativně můžete filtrovat položky v <xref:System.Windows.Controls.DataGrid> vytvořením metodu, která poskytuje logiku filtrování a nastavení <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> vlastnosti použijte filtr.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-162">Alternatively, you can filter items in a <xref:System.Windows.Controls.DataGrid> by creating a method that provides the filtering logic and setting the <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> property to apply the filter.</span></span> <span data-ttu-id="f8d1c-163">Příklad této metody naleznete v tématu [filtrování dat v zobrazení](../data/how-to-filter-data-in-a-view.md).</span><span class="sxs-lookup"><span data-stu-id="f8d1c-163">To see an example of this method, see [Filter Data in a View](../data/how-to-filter-data-in-a-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f8d1c-164">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8d1c-164">Example</span></span>

<span data-ttu-id="f8d1c-165">Následující příklad ukazuje seskupení, řazení a filtrování `Task` data v <xref:System.Windows.Data.CollectionViewSource> a zobrazení skupinových, seřazený a filtrovaný `Task` data v <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-165">The following example demonstrates grouping, sorting, and filtering `Task` data in a <xref:System.Windows.Data.CollectionViewSource> and displaying the grouped, sorted, and filtered `Task` data in a <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="f8d1c-166"><xref:System.Windows.Data.CollectionViewSource> Slouží jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pro <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-166">The <xref:System.Windows.Data.CollectionViewSource> is used as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="f8d1c-167">Seskupení, řazení a filtrování se provádí na <xref:System.Windows.Data.CollectionViewSource> a jsou zobrazeny v <xref:System.Windows.Controls.DataGrid> uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-167">Grouping, sorting, and filtering are performed on the <xref:System.Windows.Data.CollectionViewSource> and are displayed in the <xref:System.Windows.Controls.DataGrid> UI.</span></span>

<span data-ttu-id="f8d1c-168">K otestování v tomto příkladu, je potřeba upravit název DGGroupSortFilterExample tak, aby odpovídaly název vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-168">To test this example, you will need to adjust the DGGroupSortFilterExample name to match your project name.</span></span> <span data-ttu-id="f8d1c-169">Pokud používáte Visual Basic, bude nutné změnit název třídy pro <xref:System.Windows.Window> následující.</span><span class="sxs-lookup"><span data-stu-id="f8d1c-169">If you are using Visual Basic, you will need to change the class name for <xref:System.Windows.Window> to the following.</span></span>

`<Window x:Class="MainWindow"`

[!code-xaml[DataGrid_GroupSortFilter#000](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#000)]
[!code-csharp[DataGrid_GroupSortFilter#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#100)]
[!code-vb[DataGrid_GroupSortFilter#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#100)]

## <a name="see-also"></a><span data-ttu-id="f8d1c-170">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8d1c-170">See also</span></span>

- [<span data-ttu-id="f8d1c-171">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="f8d1c-171">Data Binding Overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="f8d1c-172">Vytvoření a vytvoření vazby ke kolekci ObservableCollection</span><span class="sxs-lookup"><span data-stu-id="f8d1c-172">Create and Bind to an ObservableCollection</span></span>](../data/how-to-create-and-bind-to-an-observablecollection.md)
- [<span data-ttu-id="f8d1c-173">Filtrování dat v zobrazení</span><span class="sxs-lookup"><span data-stu-id="f8d1c-173">Filter Data in a View</span></span>](../data/how-to-filter-data-in-a-view.md)
- [<span data-ttu-id="f8d1c-174">Řazení dat v zobrazení</span><span class="sxs-lookup"><span data-stu-id="f8d1c-174">Sort Data in a View</span></span>](../data/how-to-sort-data-in-a-view.md)
- [<span data-ttu-id="f8d1c-175">Řazení a seskupení dat pomocí zobrazení XAML</span><span class="sxs-lookup"><span data-stu-id="f8d1c-175">Sort and Group Data Using a View in XAML</span></span>](../data/how-to-sort-and-group-data-using-a-view-in-xaml.md)
