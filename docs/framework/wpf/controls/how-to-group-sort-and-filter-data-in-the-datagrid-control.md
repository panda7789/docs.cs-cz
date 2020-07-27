---
title: 'Postupy: seskupení, řazení a filtrování dat v ovládacím prvku DataGrid'
description: Naučte se navazovat Windows Presentation Foundation ovládací prvek DataGrid na CollectionView, který podporuje seskupení, řazení a filtrování dat v zobrazeních.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], sort
- DataGrid [WPF], group
- DataGrid [WPF], filter
ms.assetid: 03345e85-89e3-4aec-9ed0-3b80759df770
ms.openlocfilehash: 072e5a104a91faa40bb54f2a3fc4ed6188e1112e
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167668"
---
# <a name="how-to-group-sort-and-filter-data-in-the-datagrid-control"></a><span data-ttu-id="85460-103">Postupy: seskupení, řazení a filtrování dat v ovládacím prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="85460-103">How to: Group, sort, and filter data in the DataGrid control</span></span>

<span data-ttu-id="85460-104">Často je užitečné zobrazovat data <xref:System.Windows.Controls.DataGrid> různými způsoby seskupením, řazením a filtrováním dat.</span><span class="sxs-lookup"><span data-stu-id="85460-104">It is often useful to view data in a <xref:System.Windows.Controls.DataGrid> in different ways by grouping, sorting, and filtering the data.</span></span> <span data-ttu-id="85460-105">Chcete-li seskupit, seřadit a filtrovat data v <xref:System.Windows.Controls.DataGrid> , navážete ji na a <xref:System.Windows.Data.CollectionView> podporující tyto funkce.</span><span class="sxs-lookup"><span data-stu-id="85460-105">To group, sort, and filter the data in a <xref:System.Windows.Controls.DataGrid>, you bind it to a <xref:System.Windows.Data.CollectionView> that supports these functions.</span></span> <span data-ttu-id="85460-106">Pak můžete pracovat s daty v, <xref:System.Windows.Data.CollectionView> aniž by to mělo vliv na podkladová zdrojová data.</span><span class="sxs-lookup"><span data-stu-id="85460-106">You can then work with the data in the <xref:System.Windows.Data.CollectionView> without affecting the underlying source data.</span></span> <span data-ttu-id="85460-107">Změny v zobrazení kolekce se projeví v <xref:System.Windows.Controls.DataGrid> uživatelském rozhraní (UI).</span><span class="sxs-lookup"><span data-stu-id="85460-107">The changes in the collection view are reflected in the <xref:System.Windows.Controls.DataGrid> user interface (UI).</span></span>

<span data-ttu-id="85460-108"><xref:System.Windows.Data.CollectionView>Třída poskytuje funkce seskupování a řazení pro zdroj dat, který implementuje <xref:System.Collections.IEnumerable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="85460-108">The <xref:System.Windows.Data.CollectionView> class provides grouping and sorting functionality for a data source that implements the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="85460-109"><xref:System.Windows.Data.CollectionViewSource>Třída umožňuje nastavit vlastnosti <xref:System.Windows.Data.CollectionView> z XAML.</span><span class="sxs-lookup"><span data-stu-id="85460-109">The <xref:System.Windows.Data.CollectionViewSource> class enables you to set the properties of a <xref:System.Windows.Data.CollectionView> from XAML.</span></span>

<span data-ttu-id="85460-110">V tomto příkladu `Task` je kolekce objektů svázána s <xref:System.Windows.Data.CollectionViewSource> .</span><span class="sxs-lookup"><span data-stu-id="85460-110">In this example, a collection of `Task` objects is bound to a <xref:System.Windows.Data.CollectionViewSource>.</span></span> <span data-ttu-id="85460-111"><xref:System.Windows.Data.CollectionViewSource>Slouží jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pro <xref:System.Windows.Controls.DataGrid> .</span><span class="sxs-lookup"><span data-stu-id="85460-111">The <xref:System.Windows.Data.CollectionViewSource> is used as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="85460-112">Seskupení, řazení a filtrování se provádí v <xref:System.Windows.Data.CollectionViewSource> a se zobrazí v <xref:System.Windows.Controls.DataGrid> uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="85460-112">Grouping, sorting, and filtering are performed on the <xref:System.Windows.Data.CollectionViewSource> and are displayed in the <xref:System.Windows.Controls.DataGrid> UI.</span></span>

<span data-ttu-id="85460-113">![Seskupená data v objektu DataGrid](././media/wpf-datagridgroups.png "WPF_DataGridGroups") Seskupená data v objektu DataGrid</span><span class="sxs-lookup"><span data-stu-id="85460-113">![Grouped data in a DataGrid](././media/wpf-datagridgroups.png "WPF_DataGridGroups") Grouped data in a DataGrid</span></span>

## <a name="using-a-collectionviewsource-as-an-itemssource"></a><span data-ttu-id="85460-114">Použití CollectionViewSource jako ItemsSource</span><span class="sxs-lookup"><span data-stu-id="85460-114">Using a CollectionViewSource as an ItemsSource</span></span>

<span data-ttu-id="85460-115">Chcete-li seskupovat, řadit a filtrovat data v <xref:System.Windows.Controls.DataGrid> ovládacím prvku, navážete na <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Data.CollectionView> , který podporuje tyto funkce.</span><span class="sxs-lookup"><span data-stu-id="85460-115">To group, sort, and filter data in a <xref:System.Windows.Controls.DataGrid> control, you bind the <xref:System.Windows.Controls.DataGrid> to a <xref:System.Windows.Data.CollectionView> that supports these functions.</span></span> <span data-ttu-id="85460-116">V tomto příkladu <xref:System.Windows.Controls.DataGrid> je svázána s objektem <xref:System.Windows.Data.CollectionViewSource> , který poskytuje tyto funkce pro <xref:System.Collections.Generic.List%601> `Task` objekty.</span><span class="sxs-lookup"><span data-stu-id="85460-116">In this example, the <xref:System.Windows.Controls.DataGrid> is bound to a <xref:System.Windows.Data.CollectionViewSource> that provides these functions for a <xref:System.Collections.Generic.List%601> of `Task` objects.</span></span>

### <a name="to-bind-a-datagrid-to-a-collectionviewsource"></a><span data-ttu-id="85460-117">Svázání prvku DataGrid s CollectionViewSource</span><span class="sxs-lookup"><span data-stu-id="85460-117">To bind a DataGrid to a CollectionViewSource</span></span>

1. <span data-ttu-id="85460-118">Vytvořte kolekci dat, která implementuje <xref:System.Collections.IEnumerable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="85460-118">Create a data collection that implements the <xref:System.Collections.IEnumerable> interface.</span></span>

    <span data-ttu-id="85460-119">Použijete <xref:System.Collections.Generic.List%601> -li k vytvoření kolekce, měli byste vytvořit novou třídu, která dědí z <xref:System.Collections.Generic.List%601> namísto instance instance <xref:System.Collections.Generic.List%601> .</span><span class="sxs-lookup"><span data-stu-id="85460-119">If you use <xref:System.Collections.Generic.List%601> to create your collection, you should create a new class that inherits from <xref:System.Collections.Generic.List%601> instead of instantiating an instance of <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="85460-120">To umožňuje vytvořit datovou vazby ke kolekci v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="85460-120">This enables you to data bind to the collection in XAML.</span></span>

    > [!NOTE]
    > <span data-ttu-id="85460-121">Objekty v kolekci musí implementovat <xref:System.ComponentModel.INotifyPropertyChanged> změněné rozhraní a rozhraní, aby <xref:System.ComponentModel.IEditableObject> <xref:System.Windows.Controls.DataGrid> správně odpovídaly změnám a úpravám vlastností.</span><span class="sxs-lookup"><span data-stu-id="85460-121">The objects in the collection must implement the <xref:System.ComponentModel.INotifyPropertyChanged> changed interface and the <xref:System.ComponentModel.IEditableObject> interface in order for the <xref:System.Windows.Controls.DataGrid> to respond correctly to property changes and edits.</span></span> <span data-ttu-id="85460-122">Další informace najdete v tématu [implementace oznámení změny vlastností](../data/how-to-implement-property-change-notification.md).</span><span class="sxs-lookup"><span data-stu-id="85460-122">For more information, see [Implement Property Change Notification](../data/how-to-implement-property-change-notification.md).</span></span>

    [!code-csharp[DataGrid_GroupSortFilter#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#101)]
    [!code-vb[DataGrid_GroupSortFilter#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#101)]

2. <span data-ttu-id="85460-123">V jazyce XAML vytvořte instanci třídy kolekce a nastavte [direktivu x:Key –](../../../desktop-wpf/xaml-services/xkey-directive.md).</span><span class="sxs-lookup"><span data-stu-id="85460-123">In XAML, create an instance of the collection class and set the [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md).</span></span>

3. <span data-ttu-id="85460-124">V jazyce XAML vytvořte instanci <xref:System.Windows.Data.CollectionViewSource> třídy, nastavte [direktivu x:Key –](../../../desktop-wpf/xaml-services/xkey-directive.md)a nastavte instanci třídy kolekce jako <xref:System.Windows.Data.CollectionViewSource.Source%2A> .</span><span class="sxs-lookup"><span data-stu-id="85460-124">In XAML, create an instance of the <xref:System.Windows.Data.CollectionViewSource> class, set the [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md), and set the instance of your collection class as the <xref:System.Windows.Data.CollectionViewSource.Source%2A>.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#201](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml#201)]

4. <span data-ttu-id="85460-125">Vytvořte instanci <xref:System.Windows.Controls.DataGrid> třídy a nastavte <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost na <xref:System.Windows.Data.CollectionViewSource> .</span><span class="sxs-lookup"><span data-stu-id="85460-125">Create an instance of the <xref:System.Windows.Controls.DataGrid> class, and set the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property to the <xref:System.Windows.Data.CollectionViewSource>.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#002](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#002)]

5. <span data-ttu-id="85460-126">Chcete-li získat přístup k <xref:System.Windows.Data.CollectionViewSource> z kódu, použijte <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> metodu pro získání odkazu na <xref:System.Windows.Data.CollectionViewSource> .</span><span class="sxs-lookup"><span data-stu-id="85460-126">To access the <xref:System.Windows.Data.CollectionViewSource> from your code, use the <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> method to get a reference to the <xref:System.Windows.Data.CollectionViewSource>.</span></span>

    [!code-csharp[DataGrid_GroupSortFilter#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#102)]
    [!code-vb[DataGrid_GroupSortFilter#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#102)]

## <a name="grouping-items-in-a-datagrid"></a><span data-ttu-id="85460-127">Seskupení položek v objektu DataGrid</span><span class="sxs-lookup"><span data-stu-id="85460-127">Grouping items in a DataGrid</span></span>

<span data-ttu-id="85460-128">Chcete-li určit, jak jsou položky seskupeny v <xref:System.Windows.Controls.DataGrid> , použijte <xref:System.Windows.Data.PropertyGroupDescription> typ k seskupení položek v zobrazení zdroje.</span><span class="sxs-lookup"><span data-stu-id="85460-128">To specify how items are grouped in a <xref:System.Windows.Controls.DataGrid>, you use the <xref:System.Windows.Data.PropertyGroupDescription> type to group the items in the source view.</span></span>

### <a name="to-group-items-in-a-datagrid-using-xaml"></a><span data-ttu-id="85460-129">Seskupení položek v prvku DataGrid pomocí jazyka XAML</span><span class="sxs-lookup"><span data-stu-id="85460-129">To group items in a DataGrid using XAML</span></span>

1. <span data-ttu-id="85460-130">Vytvořte <xref:System.Windows.Data.PropertyGroupDescription> , který určuje vlastnost, podle které se má seskupit.</span><span class="sxs-lookup"><span data-stu-id="85460-130">Create a <xref:System.Windows.Data.PropertyGroupDescription> that specifies the property to group by.</span></span> <span data-ttu-id="85460-131">Můžete zadat vlastnost v jazyce XAML nebo v kódu.</span><span class="sxs-lookup"><span data-stu-id="85460-131">You can specify the property in XAML or in code.</span></span>

   1. <span data-ttu-id="85460-132">V jazyce XAML nastavte na <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> název vlastnosti, podle které chcete seskupit.</span><span class="sxs-lookup"><span data-stu-id="85460-132">In XAML, set the <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> to the name of the property to group by.</span></span>

   2. <span data-ttu-id="85460-133">V kódu předejte název vlastnosti k seskupení podle konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="85460-133">In code, pass the name of the property to group by to the constructor.</span></span>

2. <span data-ttu-id="85460-134">Přidejte <xref:System.Windows.Data.PropertyGroupDescription> do <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> kolekce.</span><span class="sxs-lookup"><span data-stu-id="85460-134">Add the <xref:System.Windows.Data.PropertyGroupDescription> to the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> collection.</span></span>

3. <span data-ttu-id="85460-135">Přidejte další instance <xref:System.Windows.Data.PropertyGroupDescription> do <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> kolekce, abyste mohli přidat další úrovně seskupení.</span><span class="sxs-lookup"><span data-stu-id="85460-135">Add additional instances of <xref:System.Windows.Data.PropertyGroupDescription> to the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection to add more levels of grouping.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#012](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#012)]
    [!code-csharp[DataGrid_GroupSortFilter#112](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#112)]
    [!code-vb[DataGrid_GroupSortFilter#112](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#112)]

4. <span data-ttu-id="85460-136">Pokud chcete skupinu odebrat, odeberte <xref:System.Windows.Data.PropertyGroupDescription> z <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="85460-136">To remove a group, remove the <xref:System.Windows.Data.PropertyGroupDescription> from the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection.</span></span>

5. <span data-ttu-id="85460-137">Chcete-li odebrat všechny skupiny, zavolejte <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> metodu <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="85460-137">To remove all groups, call the <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> method of the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection.</span></span>

    [!code-csharp[DataGrid_GroupSortFilter#114](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#114)]
    [!code-vb[DataGrid_GroupSortFilter#114](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#114)]

<span data-ttu-id="85460-138">Když jsou položky seskupeny v <xref:System.Windows.Controls.DataGrid> , můžete definovat <xref:System.Windows.Controls.GroupStyle> , který určuje vzhled každé skupiny.</span><span class="sxs-lookup"><span data-stu-id="85460-138">When items are grouped in the <xref:System.Windows.Controls.DataGrid>, you can define a <xref:System.Windows.Controls.GroupStyle> that specifies the appearance of each group.</span></span> <span data-ttu-id="85460-139">Použijete <xref:System.Windows.Controls.GroupStyle> ho přidáním do <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> kolekce DataGrid.</span><span class="sxs-lookup"><span data-stu-id="85460-139">You apply the <xref:System.Windows.Controls.GroupStyle> by adding it to the <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> collection of the DataGrid.</span></span> <span data-ttu-id="85460-140">Pokud máte více úrovní seskupení, můžete pro každou úroveň skupiny použít různé styly.</span><span class="sxs-lookup"><span data-stu-id="85460-140">If you have multiple levels of grouping, you can apply different styles to each group level.</span></span> <span data-ttu-id="85460-141">Styly jsou aplikovány v pořadí, ve kterém jsou definovány.</span><span class="sxs-lookup"><span data-stu-id="85460-141">Styles are applied in the order in which they are defined.</span></span> <span data-ttu-id="85460-142">Například pokud definujete dva styly, použije se jako první na nejvyšší úrovni skupiny řádků.</span><span class="sxs-lookup"><span data-stu-id="85460-142">For example, if you define two styles, the first will be applied to top level row groups.</span></span> <span data-ttu-id="85460-143">Druhý styl bude použit pro všechny skupiny řádků na druhé úrovni a nižší.</span><span class="sxs-lookup"><span data-stu-id="85460-143">The second style will be applied to all row groups at the second level and lower.</span></span> <span data-ttu-id="85460-144"><xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Controls.GroupStyle> Je <xref:System.Windows.Data.CollectionViewGroup> , který skupina představuje.</span><span class="sxs-lookup"><span data-stu-id="85460-144">The <xref:System.Windows.FrameworkElement.DataContext%2A> of the <xref:System.Windows.Controls.GroupStyle> is the <xref:System.Windows.Data.CollectionViewGroup> that the group represents.</span></span>

### <a name="to-change-the-appearance-of-row-group-headers"></a><span data-ttu-id="85460-145">Změna vzhledu záhlaví skupin řádků</span><span class="sxs-lookup"><span data-stu-id="85460-145">To change the appearance of row group headers</span></span>

1. <span data-ttu-id="85460-146">Vytvořte <xref:System.Windows.Controls.GroupStyle> , který definuje vzhled skupiny řádků.</span><span class="sxs-lookup"><span data-stu-id="85460-146">Create a <xref:System.Windows.Controls.GroupStyle> that defines the appearance of the row group.</span></span>

2. <span data-ttu-id="85460-147">Vložte <xref:System.Windows.Controls.GroupStyle> dovnitř `<DataGrid.GroupStyle>` značek.</span><span class="sxs-lookup"><span data-stu-id="85460-147">Put the <xref:System.Windows.Controls.GroupStyle> inside the `<DataGrid.GroupStyle>` tags.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#003](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#003)]

## <a name="sorting-items-in-a-datagrid"></a><span data-ttu-id="85460-148">Řazení položek v objektu DataGrid</span><span class="sxs-lookup"><span data-stu-id="85460-148">Sorting items in a DataGrid</span></span>

<span data-ttu-id="85460-149">Chcete-li určit, jak jsou položky seřazeny v <xref:System.Windows.Controls.DataGrid> , použijte <xref:System.ComponentModel.SortDescription> typ k seřazení položek v zobrazení zdroje.</span><span class="sxs-lookup"><span data-stu-id="85460-149">To specify how items are sorted in a <xref:System.Windows.Controls.DataGrid>, you use the <xref:System.ComponentModel.SortDescription> type to sort the items in the source view.</span></span>

### <a name="to-sort-items-in-a-datagrid"></a><span data-ttu-id="85460-150">Řazení položek v objektu DataGrid</span><span class="sxs-lookup"><span data-stu-id="85460-150">To sort items in a DataGrid</span></span>

1. <span data-ttu-id="85460-151">Vytvořte <xref:System.ComponentModel.SortDescription> , který určuje vlastnost, podle které se má řadit.</span><span class="sxs-lookup"><span data-stu-id="85460-151">Create a <xref:System.ComponentModel.SortDescription> that specifies the property to sort by.</span></span> <span data-ttu-id="85460-152">Můžete zadat vlastnost v jazyce XAML nebo v kódu.</span><span class="sxs-lookup"><span data-stu-id="85460-152">You can specify the property in XAML or in code.</span></span>

    1. <span data-ttu-id="85460-153">V jazyce XAML nastavte na <xref:System.ComponentModel.SortDescription.PropertyName%2A> název vlastnosti, podle které chcete řadit.</span><span class="sxs-lookup"><span data-stu-id="85460-153">In XAML, set the <xref:System.ComponentModel.SortDescription.PropertyName%2A> to the name of the property to sort by.</span></span>

    2. <span data-ttu-id="85460-154">V kódu předejte název vlastnosti k řazení podle a <xref:System.ComponentModel.ListSortDirection> do konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="85460-154">In code, pass the name of the property to sort by and the <xref:System.ComponentModel.ListSortDirection> to the constructor.</span></span>

2. <span data-ttu-id="85460-155">Přidejte <xref:System.ComponentModel.SortDescription> do <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> kolekce.</span><span class="sxs-lookup"><span data-stu-id="85460-155">Add the <xref:System.ComponentModel.SortDescription> to the <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> collection.</span></span>

3. <span data-ttu-id="85460-156">Přidejte další instance <xref:System.ComponentModel.SortDescription> do <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> kolekce, abyste je mohli seřadit podle dalších vlastností.</span><span class="sxs-lookup"><span data-stu-id="85460-156">Add additional instances of <xref:System.ComponentModel.SortDescription> to the <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> collection to sort by additional properties.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#011](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#011)]
    [!code-csharp[DataGrid_GroupSortFilter#211](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml.cs#211)]
    [!code-vb[DataGrid_GroupSortFilter#211](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#211)]

## <a name="filtering-items-in-a-datagrid"></a><span data-ttu-id="85460-157">Filtrování položek v objektu DataGrid</span><span class="sxs-lookup"><span data-stu-id="85460-157">Filtering items in a DataGrid</span></span>

<span data-ttu-id="85460-158">Chcete-li filtrovat položky v rámci <xref:System.Windows.Controls.DataGrid> pomocí <xref:System.Windows.Data.CollectionViewSource> , zadáte logiku filtrování v obslužné rutině <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> události.</span><span class="sxs-lookup"><span data-stu-id="85460-158">To filter items in a <xref:System.Windows.Controls.DataGrid> using a <xref:System.Windows.Data.CollectionViewSource>, you provide the filtering logic in the handler for the <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> event.</span></span>

### <a name="to-filter-items-in-a-datagrid"></a><span data-ttu-id="85460-159">Filtrování položek v prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="85460-159">To filter items in a DataGrid</span></span>

1. <span data-ttu-id="85460-160">Přidejte obslužnou rutinu pro <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> událost.</span><span class="sxs-lookup"><span data-stu-id="85460-160">Add a handler for the <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> event.</span></span>

2. <span data-ttu-id="85460-161">V <xref:System.Windows.Data.CollectionViewSource.Filter> obslužné rutině události definujte logiku filtrování.</span><span class="sxs-lookup"><span data-stu-id="85460-161">In the <xref:System.Windows.Data.CollectionViewSource.Filter> event handler, define the filtering logic.</span></span>

    <span data-ttu-id="85460-162">Filtr bude použit při každém obnovení zobrazení.</span><span class="sxs-lookup"><span data-stu-id="85460-162">The filter will be applied every time the view is refreshed.</span></span>

    [!code-xaml[DataGrid_GroupSortFilter#013](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#013)]
    [!code-csharp[DataGrid_GroupSortFilter#113](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#113)]
    [!code-vb[DataGrid_GroupSortFilter#113](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#113)]

<span data-ttu-id="85460-163">Alternativně můžete filtrovat položky v a <xref:System.Windows.Controls.DataGrid> vytvořením metody, která poskytuje logiku filtrování a nastavením <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> vlastnosti pro použití filtru.</span><span class="sxs-lookup"><span data-stu-id="85460-163">Alternatively, you can filter items in a <xref:System.Windows.Controls.DataGrid> by creating a method that provides the filtering logic and setting the <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> property to apply the filter.</span></span> <span data-ttu-id="85460-164">Příklad této metody najdete v tématu [filtrování dat v zobrazení](../data/how-to-filter-data-in-a-view.md).</span><span class="sxs-lookup"><span data-stu-id="85460-164">To see an example of this method, see [Filter Data in a View](../data/how-to-filter-data-in-a-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="85460-165">Příklad</span><span class="sxs-lookup"><span data-stu-id="85460-165">Example</span></span>

<span data-ttu-id="85460-166">Následující příklad znázorňuje seskupení, řazení a filtrování `Task` dat v <xref:System.Windows.Data.CollectionViewSource> a zobrazení seskupených, seřazených a filtrovaných `Task` dat v <xref:System.Windows.Controls.DataGrid> .</span><span class="sxs-lookup"><span data-stu-id="85460-166">The following example demonstrates grouping, sorting, and filtering `Task` data in a <xref:System.Windows.Data.CollectionViewSource> and displaying the grouped, sorted, and filtered `Task` data in a <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="85460-167"><xref:System.Windows.Data.CollectionViewSource>Slouží jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pro <xref:System.Windows.Controls.DataGrid> .</span><span class="sxs-lookup"><span data-stu-id="85460-167">The <xref:System.Windows.Data.CollectionViewSource> is used as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="85460-168">Seskupení, řazení a filtrování se provádí v <xref:System.Windows.Data.CollectionViewSource> a se zobrazí v <xref:System.Windows.Controls.DataGrid> uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="85460-168">Grouping, sorting, and filtering are performed on the <xref:System.Windows.Data.CollectionViewSource> and are displayed in the <xref:System.Windows.Controls.DataGrid> UI.</span></span>

<span data-ttu-id="85460-169">Chcete-li otestovat tento příklad, budete muset upravit DGGroupSortFilterExample název tak, aby odpovídal názvu projektu.</span><span class="sxs-lookup"><span data-stu-id="85460-169">To test this example, you will need to adjust the DGGroupSortFilterExample name to match your project name.</span></span> <span data-ttu-id="85460-170">Pokud používáte Visual Basic, budete muset změnit název třídy <xref:System.Windows.Window> na následující.</span><span class="sxs-lookup"><span data-stu-id="85460-170">If you are using Visual Basic, you will need to change the class name for <xref:System.Windows.Window> to the following.</span></span>

`<Window x:Class="MainWindow"`

[!code-xaml[DataGrid_GroupSortFilter#000](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#000)]
[!code-csharp[DataGrid_GroupSortFilter#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#100)]
[!code-vb[DataGrid_GroupSortFilter#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#100)]

## <a name="see-also"></a><span data-ttu-id="85460-171">Viz také</span><span class="sxs-lookup"><span data-stu-id="85460-171">See also</span></span>

- [<span data-ttu-id="85460-172">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="85460-172">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="85460-173">Vytvoření a vazba na kolekci ObservableCollection</span><span class="sxs-lookup"><span data-stu-id="85460-173">Create and Bind to an ObservableCollection</span></span>](../data/how-to-create-and-bind-to-an-observablecollection.md)
- [<span data-ttu-id="85460-174">Filtrování dat v zobrazení</span><span class="sxs-lookup"><span data-stu-id="85460-174">Filter Data in a View</span></span>](../data/how-to-filter-data-in-a-view.md)
- [<span data-ttu-id="85460-175">Řazení dat v zobrazení</span><span class="sxs-lookup"><span data-stu-id="85460-175">Sort Data in a View</span></span>](../data/how-to-sort-data-in-a-view.md)
- [<span data-ttu-id="85460-176">Řazení a seskupení dat pomocí zobrazení v jazyce XAML</span><span class="sxs-lookup"><span data-stu-id="85460-176">Sort and Group Data Using a View in XAML</span></span>](../data/how-to-sort-and-group-data-using-a-view-in-xaml.md)
