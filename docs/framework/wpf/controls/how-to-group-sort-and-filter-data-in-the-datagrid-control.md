---
title: 'Postupy: skupiny, třídění a filtrování dat v objektu DataGrid řízení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], sort
- DataGrid [WPF], group
- DataGrid [WPF], filter
ms.assetid: 03345e85-89e3-4aec-9ed0-3b80759df770
ms.openlocfilehash: 49ed0f43f0ebebe1aff7ef2f12f667ca656a774a
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37028003"
---
# <a name="how-to-group-sort-and-filter-data-in-the-datagrid-control"></a><span data-ttu-id="17cce-102">Postupy: skupina, řazení a filtrování dat v ovládacím prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="17cce-102">How to: Group, sort, and filter data in the DataGrid control</span></span>

<span data-ttu-id="17cce-103">Je často užitečné k zobrazení dat v <xref:System.Windows.Controls.DataGrid> seskupování, řazení a filtrování dat různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="17cce-103">It is often useful to view data in a <xref:System.Windows.Controls.DataGrid> in different ways by grouping, sorting, and filtering the data.</span></span> <span data-ttu-id="17cce-104">Skupina, řazení a filtrování dat v <xref:System.Windows.Controls.DataGrid>, navázat jej na <xref:System.Windows.Data.CollectionView> , která podporuje tyto funkce.</span><span class="sxs-lookup"><span data-stu-id="17cce-104">To group, sort, and filter the data in a <xref:System.Windows.Controls.DataGrid>, you bind it to a <xref:System.Windows.Data.CollectionView> that supports these functions.</span></span> <span data-ttu-id="17cce-105">Potom můžete pracovat s daty v <xref:System.Windows.Data.CollectionView> bez ovlivnění základní zdrojová data.</span><span class="sxs-lookup"><span data-stu-id="17cce-105">You can then work with the data in the <xref:System.Windows.Data.CollectionView> without affecting the underlying source data.</span></span> <span data-ttu-id="17cce-106">Změny v zobrazení kolekce se projeví v <xref:System.Windows.Controls.DataGrid> uživatelské rozhraní (UI).</span><span class="sxs-lookup"><span data-stu-id="17cce-106">The changes in the collection view are reflected in the <xref:System.Windows.Controls.DataGrid> user interface (UI).</span></span>

<span data-ttu-id="17cce-107"><xref:System.Windows.Data.CollectionView> Třída poskytuje seskupení a řazení funkce pro zdroj dat, který implementuje <xref:System.Collections.IEnumerable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="17cce-107">The <xref:System.Windows.Data.CollectionView> class provides grouping and sorting functionality for a data source that implements the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="17cce-108"><xref:System.Windows.Data.CollectionViewSource> Vám umožňuje nastavit vlastnosti <xref:System.Windows.Data.CollectionView> z XAML.</span><span class="sxs-lookup"><span data-stu-id="17cce-108">The <xref:System.Windows.Data.CollectionViewSource> class enables you to set the properties of a <xref:System.Windows.Data.CollectionView> from XAML.</span></span>

<span data-ttu-id="17cce-109">V tomto příkladu kolekce `Task` objektů je vázána <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="17cce-109">In this example, a collection of `Task` objects is bound to a <xref:System.Windows.Data.CollectionViewSource>.</span></span> <span data-ttu-id="17cce-110"><xref:System.Windows.Data.CollectionViewSource> Slouží jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pro <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="17cce-110">The <xref:System.Windows.Data.CollectionViewSource> is used as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="17cce-111">Seskupování, řazení a filtrování se provádí na <xref:System.Windows.Data.CollectionViewSource> a jsou zobrazeny v <xref:System.Windows.Controls.DataGrid> uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="17cce-111">Grouping, sorting, and filtering are performed on the <xref:System.Windows.Data.CollectionViewSource> and are displayed in the <xref:System.Windows.Controls.DataGrid> UI.</span></span>

<span data-ttu-id="17cce-112">![Seskupené data v DataGrid](./media/wpf-datagridgroups.png "WPF_DataGridGroups") seskupené data v DataGrid</span><span class="sxs-lookup"><span data-stu-id="17cce-112">![Grouped data in a DataGrid](./media/wpf-datagridgroups.png "WPF_DataGridGroups") Grouped data in a DataGrid</span></span>

## <a name="using-a-collectionviewsource-as-an-itemssource"></a><span data-ttu-id="17cce-113">Použití CollectionViewSource jako ItemsSource</span><span class="sxs-lookup"><span data-stu-id="17cce-113">Using a CollectionViewSource as an ItemsSource</span></span>

<span data-ttu-id="17cce-114">Ke skupině, řazení a filtrování dat v <xref:System.Windows.Controls.DataGrid> řízení, vytvoření vazby <xref:System.Windows.Controls.DataGrid> k <xref:System.Windows.Data.CollectionView> , která podporuje tyto funkce.</span><span class="sxs-lookup"><span data-stu-id="17cce-114">To group, sort, and filter data in a <xref:System.Windows.Controls.DataGrid> control, you bind the <xref:System.Windows.Controls.DataGrid> to a <xref:System.Windows.Data.CollectionView> that supports these functions.</span></span> <span data-ttu-id="17cce-115">V tomto příkladu <xref:System.Windows.Controls.DataGrid> je vázána <xref:System.Windows.Data.CollectionViewSource> , který poskytuje tyto funkce pro <xref:System.Collections.Generic.List%601> z `Task` objekty.</span><span class="sxs-lookup"><span data-stu-id="17cce-115">In this example, the <xref:System.Windows.Controls.DataGrid> is bound to a <xref:System.Windows.Data.CollectionViewSource> that provides these functions for a <xref:System.Collections.Generic.List%601> of `Task` objects.</span></span>

### <a name="to-bind-a-datagrid-to-a-collectionviewsource"></a><span data-ttu-id="17cce-116">K vytvoření vazby ovládacího prvku DataGrid CollectionViewSource</span><span class="sxs-lookup"><span data-stu-id="17cce-116">To bind a DataGrid to a CollectionViewSource</span></span>

1. <span data-ttu-id="17cce-117">Vytvořte kolekci dat, který implementuje <xref:System.Collections.IEnumerable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="17cce-117">Create a data collection that implements the <xref:System.Collections.IEnumerable> interface.</span></span>

    <span data-ttu-id="17cce-118">Pokud používáte <xref:System.Collections.Generic.List%601> k vytvoření kolekce, měli byste vytvořit novou třídu, která dědí z <xref:System.Collections.Generic.List%601> místo konkretizaci instance <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="17cce-118">If you use <xref:System.Collections.Generic.List%601> to create your collection, you should create a new class that inherits from <xref:System.Collections.Generic.List%601> instead of instantiating an instance of <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="17cce-119">To vám umožní k vazbě dat na kolekce v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="17cce-119">This enables you to data bind to the collection in XAML.</span></span>

    > [!NOTE]
    > <span data-ttu-id="17cce-120">Objekty v kolekci musí implementovat <xref:System.ComponentModel.INotifyPropertyChanged> změněné rozhraní a <xref:System.ComponentModel.IEditableObject> rozhraní, aby <xref:System.Windows.Controls.DataGrid> správně reakce na změny vlastností a úpravy.</span><span class="sxs-lookup"><span data-stu-id="17cce-120">The objects in the collection must implement the <xref:System.ComponentModel.INotifyPropertyChanged> changed interface and the <xref:System.ComponentModel.IEditableObject> interface in order for the <xref:System.Windows.Controls.DataGrid> to respond correctly to property changes and edits.</span></span> <span data-ttu-id="17cce-121">Další informace najdete v tématu [oznámení o změně vlastnost implementace](../data/how-to-implement-property-change-notification.md).</span><span class="sxs-lookup"><span data-stu-id="17cce-121">For more information, see [Implement Property Change Notification](../data/how-to-implement-property-change-notification.md).</span></span>

    [!code-csharp[DataGrid_GroupSortFilter#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#101)]
    [!code-vb[DataGrid_GroupSortFilter#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#101)]

2. <span data-ttu-id="17cce-122">V jazyce XAML, vytvoření instance třídy kolekce a nastavte [x: Key – direktiva](../../../../docs/framework/xaml-services/x-key-directive.md).</span><span class="sxs-lookup"><span data-stu-id="17cce-122">In XAML, create an instance of the collection class and set the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md).</span></span>

3. <span data-ttu-id="17cce-123">V jazyce XAML, vytvořte instanci <xref:System.Windows.Data.CollectionViewSource> třídy, nastavte [x: Key – direktiva](../../../../docs/framework/xaml-services/x-key-directive.md)a nastavte instance třídy kolekce jako <xref:System.Windows.Data.CollectionViewSource.Source%2A>.</span><span class="sxs-lookup"><span data-stu-id="17cce-123">In XAML, create an instance of the <xref:System.Windows.Data.CollectionViewSource> class, set the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md), and set the instance of your collection class as the <xref:System.Windows.Data.CollectionViewSource.Source%2A>.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#201](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml#201)]

4. <span data-ttu-id="17cce-124">Vytvoření instance <xref:System.Windows.Controls.DataGrid> třídy a nastavte <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost, která má <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="17cce-124">Create an instance of the <xref:System.Windows.Controls.DataGrid> class, and set the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property to the <xref:System.Windows.Data.CollectionViewSource>.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#002](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#002)]

5. <span data-ttu-id="17cce-125">Pro přístup k <xref:System.Windows.Data.CollectionViewSource> z vašeho kódu pomocí <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> metodu k získání odkazu na <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="17cce-125">To access the <xref:System.Windows.Data.CollectionViewSource> from your code, use the <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> method to get a reference to the <xref:System.Windows.Data.CollectionViewSource>.</span></span>

    [!code-csharp[DataGrid_GroupSortFilter#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#102)]
    [!code-vb[DataGrid_GroupSortFilter#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#102)]

## <a name="grouping-items-in-a-datagrid"></a><span data-ttu-id="17cce-126">Seskupení položek v DataGrid</span><span class="sxs-lookup"><span data-stu-id="17cce-126">Grouping items in a DataGrid</span></span>

<span data-ttu-id="17cce-127">Chcete-li určit způsob seskupení položek v <xref:System.Windows.Controls.DataGrid>, můžete použít <xref:System.Windows.Data.PropertyGroupDescription> typu chcete seskupit položky v zobrazení zdroje.</span><span class="sxs-lookup"><span data-stu-id="17cce-127">To specify how items are grouped in a <xref:System.Windows.Controls.DataGrid>, you use the <xref:System.Windows.Data.PropertyGroupDescription> type to group the items in the source view.</span></span>

### <a name="to-group-items-in-a-datagrid-using-xaml"></a><span data-ttu-id="17cce-128">Seskupit položky v DataGrid pomocí jazyka XAML</span><span class="sxs-lookup"><span data-stu-id="17cce-128">To group items in a DataGrid using XAML</span></span>

1. <span data-ttu-id="17cce-129">Vytvoření <xref:System.Windows.Data.PropertyGroupDescription> , určuje vlastnost do skupiny podle.</span><span class="sxs-lookup"><span data-stu-id="17cce-129">Create a <xref:System.Windows.Data.PropertyGroupDescription> that specifies the property to group by.</span></span> <span data-ttu-id="17cce-130">Vlastnost můžete zadat v jazyce XAML, nebo v kódu.</span><span class="sxs-lookup"><span data-stu-id="17cce-130">You can specify the property in XAML or in code.</span></span>

   1. <span data-ttu-id="17cce-131">V jazyce XAML, nastavte <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> na název vlastnosti, která má Seskupit podle.</span><span class="sxs-lookup"><span data-stu-id="17cce-131">In XAML, set the <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> to the name of the property to group by.</span></span>

   2. <span data-ttu-id="17cce-132">V kódu předejte název vlastnost do skupiny pomocí konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="17cce-132">In code, pass the name of the property to group by to the constructor.</span></span>

2. <span data-ttu-id="17cce-133">Přidat <xref:System.Windows.Data.PropertyGroupDescription> k <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> kolekce.</span><span class="sxs-lookup"><span data-stu-id="17cce-133">Add the <xref:System.Windows.Data.PropertyGroupDescription> to the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> collection.</span></span>

3. <span data-ttu-id="17cce-134">Přidat další instance <xref:System.Windows.Data.PropertyGroupDescription> k <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> kolekce, které chcete přidat další úrovně seskupení.</span><span class="sxs-lookup"><span data-stu-id="17cce-134">Add additional instances of <xref:System.Windows.Data.PropertyGroupDescription> to the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection to add more levels of grouping.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#012](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#012)]
    [!code-csharp[DataGrid_GroupSortFilter#112](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#112)]
    [!code-vb[DataGrid_GroupSortFilter#112](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#112)]

4. <span data-ttu-id="17cce-135">Chcete-li odebrat skupinu, odeberte <xref:System.Windows.Data.PropertyGroupDescription> z <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="17cce-135">To remove a group, remove the <xref:System.Windows.Data.PropertyGroupDescription> from the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection.</span></span>

5. <span data-ttu-id="17cce-136">Chcete-li odebrat všechny skupiny, zavolejte <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> metodu <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="17cce-136">To remove all groups, call the <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> method of the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection.</span></span>

    [!code-csharp[DataGrid_GroupSortFilter#114](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#114)]
    [!code-vb[DataGrid_GroupSortFilter#114](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#114)]

<span data-ttu-id="17cce-137">Pokud budou seskupeny položky v <xref:System.Windows.Controls.DataGrid>, můžete definovat <xref:System.Windows.Controls.GroupStyle> určující vzhled každé skupiny.</span><span class="sxs-lookup"><span data-stu-id="17cce-137">When items are grouped in the <xref:System.Windows.Controls.DataGrid>, you can define a <xref:System.Windows.Controls.GroupStyle> that specifies the appearance of each group.</span></span> <span data-ttu-id="17cce-138">Můžete použít <xref:System.Windows.Controls.GroupStyle> přidáním jeho <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> kolekci DataGrid.</span><span class="sxs-lookup"><span data-stu-id="17cce-138">You apply the <xref:System.Windows.Controls.GroupStyle> by adding it to the <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> collection of the DataGrid.</span></span> <span data-ttu-id="17cce-139">Pokud máte více úrovní seskupení, můžete použít různé styly pro každou úroveň skupiny.</span><span class="sxs-lookup"><span data-stu-id="17cce-139">If you have multiple levels of grouping, you can apply different styles to each group level.</span></span> <span data-ttu-id="17cce-140">Styly jsou použity v pořadí, ve kterém jsou definovány.</span><span class="sxs-lookup"><span data-stu-id="17cce-140">Styles are applied in the order in which they are defined.</span></span> <span data-ttu-id="17cce-141">Například pokud definujete dvě styly, první se použijí na nejvyšší úrovni řádek skupiny.</span><span class="sxs-lookup"><span data-stu-id="17cce-141">For example, if you define two styles, the first will be applied to top level row groups.</span></span> <span data-ttu-id="17cce-142">Druhý styl bude použit na všechny skupiny řádků na úrovni druhé a nižší.</span><span class="sxs-lookup"><span data-stu-id="17cce-142">The second style will be applied to all row groups at the second level and lower.</span></span> <span data-ttu-id="17cce-143"><xref:System.Windows.FrameworkElement.DataContext%2A> z <xref:System.Windows.Controls.GroupStyle> je <xref:System.Windows.Data.CollectionViewGroup> představující skupině.</span><span class="sxs-lookup"><span data-stu-id="17cce-143">The <xref:System.Windows.FrameworkElement.DataContext%2A> of the <xref:System.Windows.Controls.GroupStyle> is the <xref:System.Windows.Data.CollectionViewGroup> that the group represents.</span></span>

### <a name="to-change-the-appearance-of-row-group-headers"></a><span data-ttu-id="17cce-144">Chcete-li změnit vzhled záhlaví skupiny řádků</span><span class="sxs-lookup"><span data-stu-id="17cce-144">To change the appearance of row group headers</span></span>

1. <span data-ttu-id="17cce-145">Vytvoření <xref:System.Windows.Controls.GroupStyle> , který definuje vzhled skupiny řádků.</span><span class="sxs-lookup"><span data-stu-id="17cce-145">Create a <xref:System.Windows.Controls.GroupStyle> that defines the appearance of the row group.</span></span>

2. <span data-ttu-id="17cce-146">Umístit <xref:System.Windows.Controls.GroupStyle> uvnitř `<DataGrid.GroupStyle>` značky.</span><span class="sxs-lookup"><span data-stu-id="17cce-146">Put the <xref:System.Windows.Controls.GroupStyle> inside the `<DataGrid.GroupStyle>` tags.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#003](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#003)]

## <a name="sorting-items-in-a-datagrid"></a><span data-ttu-id="17cce-147">Řazení položek v DataGrid</span><span class="sxs-lookup"><span data-stu-id="17cce-147">Sorting items in a DataGrid</span></span>

<span data-ttu-id="17cce-148">Chcete-li určit, jak jsou položky seřazeny v <xref:System.Windows.Controls.DataGrid>, použijete <xref:System.ComponentModel.SortDescription> typ seřadíte položky v zobrazení zdroje.</span><span class="sxs-lookup"><span data-stu-id="17cce-148">To specify how items are sorted in a <xref:System.Windows.Controls.DataGrid>, you use the <xref:System.ComponentModel.SortDescription> type to sort the items in the source view.</span></span>

### <a name="to-sort-items-in-a-datagrid"></a><span data-ttu-id="17cce-149">Chcete-li řadit položky v DataGrid</span><span class="sxs-lookup"><span data-stu-id="17cce-149">To sort items in a DataGrid</span></span>

1. <span data-ttu-id="17cce-150">Vytvoření <xref:System.ComponentModel.SortDescription> , určuje vlastnost, která má seřadit.</span><span class="sxs-lookup"><span data-stu-id="17cce-150">Create a <xref:System.ComponentModel.SortDescription> that specifies the property to sort by.</span></span> <span data-ttu-id="17cce-151">Vlastnost můžete zadat v jazyce XAML, nebo v kódu.</span><span class="sxs-lookup"><span data-stu-id="17cce-151">You can specify the property in XAML or in code.</span></span>

    1. <span data-ttu-id="17cce-152">V jazyce XAML, nastavte <xref:System.ComponentModel.SortDescription.PropertyName%2A> na název vlastnosti, která má seřadit.</span><span class="sxs-lookup"><span data-stu-id="17cce-152">In XAML, set the <xref:System.ComponentModel.SortDescription.PropertyName%2A> to the name of the property to sort by.</span></span>

    2. <span data-ttu-id="17cce-153">V kódu předat název vlastnosti pro řazení podle a <xref:System.ComponentModel.ListSortDirection> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="17cce-153">In code, pass the name of the property to sort by and the <xref:System.ComponentModel.ListSortDirection> to the constructor.</span></span>

2. <span data-ttu-id="17cce-154">Přidat <xref:System.ComponentModel.SortDescription> k <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> kolekce.</span><span class="sxs-lookup"><span data-stu-id="17cce-154">Add the <xref:System.ComponentModel.SortDescription> to the <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> collection.</span></span>

3. <span data-ttu-id="17cce-155">Přidat další instance <xref:System.ComponentModel.SortDescription> k <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> kolekce seřadit podle další vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="17cce-155">Add additional instances of <xref:System.ComponentModel.SortDescription> to the <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> collection to sort by additional properties.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#011](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#011)]
    [!code-csharp[DataGrid_GroupSortFilter#211](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml.cs#211)]
    [!code-vb[DataGrid_GroupSortFilter#211](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#211)]

## <a name="filtering-items-in-a-datagrid"></a><span data-ttu-id="17cce-156">Filtrování položek v DataGrid</span><span class="sxs-lookup"><span data-stu-id="17cce-156">Filtering items in a DataGrid</span></span>

<span data-ttu-id="17cce-157">Filtrování položek v <xref:System.Windows.Controls.DataGrid> pomocí <xref:System.Windows.Data.CollectionViewSource>, poskytovat logiku filtrování obslužné rutiny pro <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> událostí.</span><span class="sxs-lookup"><span data-stu-id="17cce-157">To filter items in a <xref:System.Windows.Controls.DataGrid> using a <xref:System.Windows.Data.CollectionViewSource>, you provide the filtering logic in the handler for the <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> event.</span></span>

### <a name="to-filter-items-in-a-datagrid"></a><span data-ttu-id="17cce-158">Filtrovat položky v DataGrid</span><span class="sxs-lookup"><span data-stu-id="17cce-158">To filter items in a DataGrid</span></span>

1. <span data-ttu-id="17cce-159">Přidání obslužné rutiny <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> událostí.</span><span class="sxs-lookup"><span data-stu-id="17cce-159">Add a handler for the <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> event.</span></span>

2. <span data-ttu-id="17cce-160">V <xref:System.Windows.Data.CollectionViewSource.Filter> obslužné rutiny události, definovat filtrování logiku.</span><span class="sxs-lookup"><span data-stu-id="17cce-160">In the <xref:System.Windows.Data.CollectionViewSource.Filter> event handler, define the filtering logic.</span></span>

    <span data-ttu-id="17cce-161">Filtr se použijí pokaždé, když je zobrazení aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="17cce-161">The filter will be applied every time the view is refreshed.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#013](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#013)]
    [!code-csharp[DataGrid_GroupSortFilter#113](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#113)]
    [!code-vb[DataGrid_GroupSortFilter#113](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#113)]

<span data-ttu-id="17cce-162">Alternativně můžete filtrovat položky v <xref:System.Windows.Controls.DataGrid> vytvořením metodu, která poskytuje filtrování logiku a nastavení <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> vlastnost použít filtr.</span><span class="sxs-lookup"><span data-stu-id="17cce-162">Alternatively, you can filter items in a <xref:System.Windows.Controls.DataGrid> by creating a method that provides the filtering logic and setting the <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> property to apply the filter.</span></span> <span data-ttu-id="17cce-163">Příklad této metody naleznete v tématu [filtrování dat v zobrazení](../data/how-to-filter-data-in-a-view.md).</span><span class="sxs-lookup"><span data-stu-id="17cce-163">To see an example of this method, see [Filter Data in a View](../data/how-to-filter-data-in-a-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="17cce-164">Příklad</span><span class="sxs-lookup"><span data-stu-id="17cce-164">Example</span></span>

<span data-ttu-id="17cce-165">Následující příklad ukazuje seskupování, řazení a filtrování `Task` data v <xref:System.Windows.Data.CollectionViewSource> a zobrazování seskupené, třídění a filtrování `Task` data <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="17cce-165">The following example demonstrates grouping, sorting, and filtering `Task` data in a <xref:System.Windows.Data.CollectionViewSource> and displaying the grouped, sorted, and filtered `Task` data in a <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="17cce-166"><xref:System.Windows.Data.CollectionViewSource> Slouží jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pro <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="17cce-166">The <xref:System.Windows.Data.CollectionViewSource> is used as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="17cce-167">Seskupování, řazení a filtrování se provádí na <xref:System.Windows.Data.CollectionViewSource> a jsou zobrazeny v <xref:System.Windows.Controls.DataGrid> uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="17cce-167">Grouping, sorting, and filtering are performed on the <xref:System.Windows.Data.CollectionViewSource> and are displayed in the <xref:System.Windows.Controls.DataGrid> UI.</span></span>

<span data-ttu-id="17cce-168">K testování v tomto příkladu, musíte upravit název DGGroupSortFilterExample tak, aby odpovídaly název projektu.</span><span class="sxs-lookup"><span data-stu-id="17cce-168">To test this example, you will need to adjust the DGGroupSortFilterExample name to match your project name.</span></span> <span data-ttu-id="17cce-169">Pokud používáte Visual Basic, budete muset změnit název třídy pro <xref:System.Windows.Window> pro následující.</span><span class="sxs-lookup"><span data-stu-id="17cce-169">If you are using Visual Basic, you will need to change the class name for <xref:System.Windows.Window> to the following.</span></span>

`<Window x:Class="MainWindow"`

[!code-xaml[DataGrid_GroupSortFilter#000](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#000)]
[!code-csharp[DataGrid_GroupSortFilter#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#100)]
[!code-vb[DataGrid_GroupSortFilter#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#100)]

## <a name="see-also"></a><span data-ttu-id="17cce-170">Viz také:</span><span class="sxs-lookup"><span data-stu-id="17cce-170">See also</span></span>

[<span data-ttu-id="17cce-171">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="17cce-171">Data Binding Overview</span></span>](../data/data-binding-overview.md)  
[<span data-ttu-id="17cce-172">Vytvoření a vytvoření vazby ke kolekci ObservableCollection</span><span class="sxs-lookup"><span data-stu-id="17cce-172">Create and Bind to an ObservableCollection</span></span>](../data/how-to-create-and-bind-to-an-observablecollection.md)  
[<span data-ttu-id="17cce-173">Filtrování dat v zobrazení</span><span class="sxs-lookup"><span data-stu-id="17cce-173">Filter Data in a View</span></span>](../data/how-to-filter-data-in-a-view.md)  
[<span data-ttu-id="17cce-174">Řazení dat v zobrazení</span><span class="sxs-lookup"><span data-stu-id="17cce-174">Sort Data in a View</span></span>](../data/how-to-sort-data-in-a-view.md)  
[<span data-ttu-id="17cce-175">Řazení a seskupení dat pomocí zobrazení XAML</span><span class="sxs-lookup"><span data-stu-id="17cce-175">Sort and Group Data Using a View in XAML</span></span>](../data/how-to-sort-and-group-data-using-a-view-in-xaml.md)  