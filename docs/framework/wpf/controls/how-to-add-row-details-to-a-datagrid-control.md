---
title: 'Postupy: Přidání podrobností řádku do ovládacího prvku DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataTemplate [WPF], DataGrid
- row details [WPF], DataGrid
- DataGrid [WPF], row details
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
ms.openlocfilehash: d5b6539f3d379088528b9654861267988b6fc69b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59317885"
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a><span data-ttu-id="98c58-102">Postupy: Přidání podrobností řádku do ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="98c58-102">How to: Add Row Details to a DataGrid Control</span></span>
<span data-ttu-id="98c58-103">Při použití <xref:System.Windows.Controls.DataGrid> ovládacího prvku, prezentace dat můžete přizpůsobit přidáním části Podrobnosti řádků.</span><span class="sxs-lookup"><span data-stu-id="98c58-103">When using the <xref:System.Windows.Controls.DataGrid> control, you can customize the data presentation by adding a row details section.</span></span> <span data-ttu-id="98c58-104">Přidání části Podrobnosti o řádek umožňují seskupit některá data v šabloně, která je volitelně zobrazená nebo sbalená.</span><span class="sxs-lookup"><span data-stu-id="98c58-104">Adding a row details section enables you to group some data in a template that is optionally visible or collapsed.</span></span> <span data-ttu-id="98c58-105">Například může přidání podrobností řádku do <xref:System.Windows.Controls.DataGrid> , který představuje pouze souhrnné informace o data pro každý řádek <xref:System.Windows.Controls.DataGrid>, ale přináší další datová pole, když uživatel vybere řádek.</span><span class="sxs-lookup"><span data-stu-id="98c58-105">For example, you can add row details to a <xref:System.Windows.Controls.DataGrid> that presents only a summary of the data for each row in the <xref:System.Windows.Controls.DataGrid>, but presents more data fields when the user selects a row.</span></span> <span data-ttu-id="98c58-106">Definování šablony daného oddílu Podrobnosti řádku <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="98c58-106">You define the template for the row details section in the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property.</span></span> <span data-ttu-id="98c58-107">Následující obrázek znázorňuje příklad v části Podrobnosti řádků.</span><span class="sxs-lookup"><span data-stu-id="98c58-107">The following illustration shows an example of a row details section.</span></span>  
  
 <span data-ttu-id="98c58-108">![DataGrid – zobrazí se podrobnosti řádku](./media/ndp-rowdetails.png "NDP_RowDetails")</span><span class="sxs-lookup"><span data-stu-id="98c58-108">![DataGrid shown with row details](./media/ndp-rowdetails.png "NDP_RowDetails")</span></span>  
  
 <span data-ttu-id="98c58-109">Podrobnosti šablony řádku definujete, buď jako vložené XAML nebo jako prostředek.</span><span class="sxs-lookup"><span data-stu-id="98c58-109">You define the row details template as either inline XAML or as a resource.</span></span> <span data-ttu-id="98c58-110">Oba přístupy jsou uvedeny v následujících postupech.</span><span class="sxs-lookup"><span data-stu-id="98c58-110">Both approaches are shown in the following procedures.</span></span> <span data-ttu-id="98c58-111">Datové šablony, které se přidají jako prostředek je možné v celém projektu bez nutnosti znovu vytvářet šablony.</span><span class="sxs-lookup"><span data-stu-id="98c58-111">A data template that is added as a resource can be used throughout the project without re-creating the template.</span></span> <span data-ttu-id="98c58-112">Datové šablony, které se přidají jako vložený, XAML je dostupná jenom z ovládacího prvku níž byl definován.</span><span class="sxs-lookup"><span data-stu-id="98c58-112">A data template that is added as inline XAML is only accessible from the control where it is defined.</span></span>  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a><span data-ttu-id="98c58-113">Chcete-li zobrazit podrobnosti řádku s použitím vložené XAML</span><span class="sxs-lookup"><span data-stu-id="98c58-113">To display row details by using inline XAML</span></span>  
  
1. <span data-ttu-id="98c58-114">Vytvoření <xref:System.Windows.Controls.DataGrid> zobrazující data z datového zdroje.</span><span class="sxs-lookup"><span data-stu-id="98c58-114">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2. <span data-ttu-id="98c58-115">V <xref:System.Windows.Controls.DataGrid> elementu, přidejte <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> elementu.</span><span class="sxs-lookup"><span data-stu-id="98c58-115">In the <xref:System.Windows.Controls.DataGrid> element, add a <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> element.</span></span>  
  
3. <span data-ttu-id="98c58-116">Vytvoření <xref:System.Windows.DataTemplate> , která definuje vzhled elementů v části Podrobnosti řádků.</span><span class="sxs-lookup"><span data-stu-id="98c58-116">Create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="98c58-117">Zobrazí se následující XAML <xref:System.Windows.Controls.DataGrid> a tom, jak definovat <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> vložené.</span><span class="sxs-lookup"><span data-stu-id="98c58-117">The following XAML shows the <xref:System.Windows.Controls.DataGrid> and how to define the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> inline.</span></span> <span data-ttu-id="98c58-118"><xref:System.Windows.Controls.DataGrid> Zobrazí tři hodnoty v jednotlivých řádcích a tři další hodnoty při výběru řádku.</span><span class="sxs-lookup"><span data-stu-id="98c58-118">The <xref:System.Windows.Controls.DataGrid> displays three values in each row and three more values when the row is selected.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#1](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     <span data-ttu-id="98c58-119">Následující kód ukazuje dotaz, který se používá pro výběr data, která se zobrazí <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="98c58-119">The following code shows the query that is used to select the data that is displayed in the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="98c58-120">V tomto příkladu dotaz vybere data z entity, který obsahuje informace o zákaznících.</span><span class="sxs-lookup"><span data-stu-id="98c58-120">In this example, the query selects data from an entity that contains customer information.</span></span>  
  
     [!code-csharp[DataGrid_RowDetails#2](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a><span data-ttu-id="98c58-121">Chcete-li zobrazit podrobnosti řádku s použitím prostředku</span><span class="sxs-lookup"><span data-stu-id="98c58-121">To display row details by using a resource</span></span>  
  
1. <span data-ttu-id="98c58-122">Vytvoření <xref:System.Windows.Controls.DataGrid> zobrazující data z datového zdroje.</span><span class="sxs-lookup"><span data-stu-id="98c58-122">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2. <span data-ttu-id="98c58-123">Přidat <xref:System.Windows.FrameworkElement.Resources%2A> element do kořenového elementu, jako <xref:System.Windows.Window> ovládací prvek nebo <xref:System.Windows.Controls.Page> ovládací prvek, nebo přidejte <xref:System.Windows.Application.Resources%2A> element <xref:System.Windows.Application> třída v souboru App.xaml (nebo Application.xaml).</span><span class="sxs-lookup"><span data-stu-id="98c58-123">Add a <xref:System.Windows.FrameworkElement.Resources%2A> element to the root element, such as a <xref:System.Windows.Window> control or a <xref:System.Windows.Controls.Page> control, or add a <xref:System.Windows.Application.Resources%2A> element to the <xref:System.Windows.Application> class in the App.xaml (or Application.xaml) file.</span></span>  
  
3. <span data-ttu-id="98c58-124">Vytvořte v elementu resources <xref:System.Windows.DataTemplate> , která definuje vzhled elementů v části Podrobnosti řádků.</span><span class="sxs-lookup"><span data-stu-id="98c58-124">In the resources element, create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="98c58-125">Zobrazí se následující XAML <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> definované v <xref:System.Windows.Application> třídy.</span><span class="sxs-lookup"><span data-stu-id="98c58-125">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> defined in the <xref:System.Windows.Application> class.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#3](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4. <span data-ttu-id="98c58-126">Na <xref:System.Windows.DataTemplate>, nastavte [x: Key – direktiva](../../xaml-services/x-key-directive.md) na hodnotu, která jednoznačně identifikuje šablony.</span><span class="sxs-lookup"><span data-stu-id="98c58-126">On the <xref:System.Windows.DataTemplate>, set the [x:Key Directive](../../xaml-services/x-key-directive.md) to a value that uniquely identifies the data template.</span></span>  
  
5. <span data-ttu-id="98c58-127">V <xref:System.Windows.Controls.DataGrid> element, nastaven <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> vlastnost na prostředek definovaný v předchozích krocích.</span><span class="sxs-lookup"><span data-stu-id="98c58-127">In the <xref:System.Windows.Controls.DataGrid> element, set the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property to the resource defined in the previous steps.</span></span> <span data-ttu-id="98c58-128">Přiřaďte zdroje jako statický prostředek.</span><span class="sxs-lookup"><span data-stu-id="98c58-128">Assign the resource as a static resource.</span></span>  
  
     <span data-ttu-id="98c58-129">Zobrazí se následující XAML <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> nastavenou na prostředek z předchozího příkladu.</span><span class="sxs-lookup"><span data-stu-id="98c58-129">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property set to the resource from the previous example.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#4](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a><span data-ttu-id="98c58-130">Pokud chcete nastavit viditelnost a zabránit vodorovného posouvání pro podrobnosti řádku</span><span class="sxs-lookup"><span data-stu-id="98c58-130">To set visibility and prevent horizontal scrolling for row details</span></span>  
  
1. <span data-ttu-id="98c58-131">V případě potřeby nastavte <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> vlastnost <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="98c58-131">If needed, set the <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> property to a <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> value.</span></span>  
  
     <span data-ttu-id="98c58-132">Ve výchozím nastavení, je hodnota nastavena <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>.</span><span class="sxs-lookup"><span data-stu-id="98c58-132">By default, the value is set to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>.</span></span> <span data-ttu-id="98c58-133">Můžete nastavit na <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> zobrazte podrobnosti pro všechny řádky nebo <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> skrýt podrobnosti pro všechny řádky.</span><span class="sxs-lookup"><span data-stu-id="98c58-133">You can set it to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> to show the details for all of the rows or <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> to hide the details for all rows.</span></span>  
  
2. <span data-ttu-id="98c58-134">V případě potřeby nastavte <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> vlastnost `true` zabránit řádku podrobnosti v části posouvání vodorovně.</span><span class="sxs-lookup"><span data-stu-id="98c58-134">If needed, set the <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> property to `true` to prevent the row details section from scrolling horizontally.</span></span>
