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
ms.openlocfilehash: 4db414e1907d42071f7251c390077d4020fa577c
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559674"
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a><span data-ttu-id="a071d-102">Postupy: Přidání podrobností řádku do ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="a071d-102">How to: Add Row Details to a DataGrid Control</span></span>
<span data-ttu-id="a071d-103">Při použití ovládacího prvku <xref:System.Windows.Controls.DataGrid> můžete přizpůsobit prezentaci dat přidáním části Podrobnosti řádku.</span><span class="sxs-lookup"><span data-stu-id="a071d-103">When using the <xref:System.Windows.Controls.DataGrid> control, you can customize the data presentation by adding a row details section.</span></span> <span data-ttu-id="a071d-104">Přidáním části Podrobnosti řádku můžete seskupit některá data do šablony, která je volitelně viditelná nebo sbalená.</span><span class="sxs-lookup"><span data-stu-id="a071d-104">Adding a row details section enables you to group some data in a template that is optionally visible or collapsed.</span></span> <span data-ttu-id="a071d-105">Například můžete přidat podrobnosti řádku do <xref:System.Windows.Controls.DataGrid>, který prezentuje pouze souhrn dat pro každý řádek v <xref:System.Windows.Controls.DataGrid>, ale prezentuje více datových polí, když uživatel vybere řádek.</span><span class="sxs-lookup"><span data-stu-id="a071d-105">For example, you can add row details to a <xref:System.Windows.Controls.DataGrid> that presents only a summary of the data for each row in the <xref:System.Windows.Controls.DataGrid>, but presents more data fields when the user selects a row.</span></span> <span data-ttu-id="a071d-106">Šablonu můžete definovat pro oddíl podrobnosti řádku ve vlastnosti <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>.</span><span class="sxs-lookup"><span data-stu-id="a071d-106">You define the template for the row details section in the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property.</span></span> <span data-ttu-id="a071d-107">Následující ilustrace znázorňuje příklad oddílu podrobností řádku.</span><span class="sxs-lookup"><span data-stu-id="a071d-107">The following illustration shows an example of a row details section.</span></span>  
  
 <span data-ttu-id="a071d-108">![DataGrid zobrazená s podrobnostmi řádku](./media/ndp-rowdetails.png "NDP_RowDetails")</span><span class="sxs-lookup"><span data-stu-id="a071d-108">![DataGrid shown with row details](./media/ndp-rowdetails.png "NDP_RowDetails")</span></span>  
  
 <span data-ttu-id="a071d-109">Šablonu podrobností řádku můžete definovat buď jako vložený kód XAML, nebo jako prostředek.</span><span class="sxs-lookup"><span data-stu-id="a071d-109">You define the row details template as either inline XAML or as a resource.</span></span> <span data-ttu-id="a071d-110">Oba přístupy jsou uvedené v následujících postupech.</span><span class="sxs-lookup"><span data-stu-id="a071d-110">Both approaches are shown in the following procedures.</span></span> <span data-ttu-id="a071d-111">Šablona dat, která je přidána jako prostředek, může být použita v celém projektu, aniž by bylo nutné šablonu znovu vytvořit.</span><span class="sxs-lookup"><span data-stu-id="a071d-111">A data template that is added as a resource can be used throughout the project without re-creating the template.</span></span> <span data-ttu-id="a071d-112">Šablona dat, která je přidána jako vložený kód XAML, je přístupná pouze z ovládacího prvku, kde je definována.</span><span class="sxs-lookup"><span data-stu-id="a071d-112">A data template that is added as inline XAML is only accessible from the control where it is defined.</span></span>  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a><span data-ttu-id="a071d-113">Zobrazení podrobností o řádku pomocí vloženého kódu XAML</span><span class="sxs-lookup"><span data-stu-id="a071d-113">To display row details by using inline XAML</span></span>  
  
1. <span data-ttu-id="a071d-114">Vytvoří <xref:System.Windows.Controls.DataGrid>, který zobrazí data ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="a071d-114">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2. <span data-ttu-id="a071d-115">V <xref:System.Windows.Controls.DataGrid> elementu, přidejte <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> elementu.</span><span class="sxs-lookup"><span data-stu-id="a071d-115">In the <xref:System.Windows.Controls.DataGrid> element, add a <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> element.</span></span>  
  
3. <span data-ttu-id="a071d-116">Vytvořte <xref:System.Windows.DataTemplate> definující vzhled oddílu podrobností řádku.</span><span class="sxs-lookup"><span data-stu-id="a071d-116">Create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="a071d-117">Následující XAML ukazuje <xref:System.Windows.Controls.DataGrid> a jak definovat <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> inline.</span><span class="sxs-lookup"><span data-stu-id="a071d-117">The following XAML shows the <xref:System.Windows.Controls.DataGrid> and how to define the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> inline.</span></span> <span data-ttu-id="a071d-118"><xref:System.Windows.Controls.DataGrid> zobrazí tři hodnoty v každém řádku a tři další hodnoty, když je vybrán řádek.</span><span class="sxs-lookup"><span data-stu-id="a071d-118">The <xref:System.Windows.Controls.DataGrid> displays three values in each row and three more values when the row is selected.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#1](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     <span data-ttu-id="a071d-119">Následující kód ukazuje dotaz, který se používá k výběru dat zobrazených v <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="a071d-119">The following code shows the query that is used to select the data that is displayed in the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="a071d-120">V tomto příkladu dotaz vybírá data z entity, která obsahuje informace o zákaznících.</span><span class="sxs-lookup"><span data-stu-id="a071d-120">In this example, the query selects data from an entity that contains customer information.</span></span>  
  
     [!code-csharp[DataGrid_RowDetails#2](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a><span data-ttu-id="a071d-121">Zobrazení podrobností o řádku pomocí prostředku</span><span class="sxs-lookup"><span data-stu-id="a071d-121">To display row details by using a resource</span></span>  
  
1. <span data-ttu-id="a071d-122">Vytvoří <xref:System.Windows.Controls.DataGrid>, který zobrazí data ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="a071d-122">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2. <span data-ttu-id="a071d-123">Přidejte <xref:System.Windows.FrameworkElement.Resources%2A> element do kořenového prvku, jako je například ovládací prvek <xref:System.Windows.Window> nebo ovládací prvek <xref:System.Windows.Controls.Page>, nebo přidejte <xref:System.Windows.Application.Resources%2A> element do třídy <xref:System.Windows.Application> v souboru App. XAML (nebo Application. XAML).</span><span class="sxs-lookup"><span data-stu-id="a071d-123">Add a <xref:System.Windows.FrameworkElement.Resources%2A> element to the root element, such as a <xref:System.Windows.Window> control or a <xref:System.Windows.Controls.Page> control, or add a <xref:System.Windows.Application.Resources%2A> element to the <xref:System.Windows.Application> class in the App.xaml (or Application.xaml) file.</span></span>  
  
3. <span data-ttu-id="a071d-124">V elementu Resources vytvořte <xref:System.Windows.DataTemplate> definující vzhled oddílu podrobností řádku.</span><span class="sxs-lookup"><span data-stu-id="a071d-124">In the resources element, create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="a071d-125">Následující kód XAML ukazuje <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> definované ve třídě <xref:System.Windows.Application>.</span><span class="sxs-lookup"><span data-stu-id="a071d-125">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> defined in the <xref:System.Windows.Application> class.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#3](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4. <span data-ttu-id="a071d-126">V <xref:System.Windows.DataTemplate>nastavte [direktivu x:Key –](../../../desktop-wpf/xaml-services/xkey-directive.md) na hodnotu, která jedinečně identifikuje šablonu dat.</span><span class="sxs-lookup"><span data-stu-id="a071d-126">On the <xref:System.Windows.DataTemplate>, set the [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) to a value that uniquely identifies the data template.</span></span>  
  
5. <span data-ttu-id="a071d-127">V prvku <xref:System.Windows.Controls.DataGrid> nastavte vlastnost <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> na prostředek definovaný v předchozích krocích.</span><span class="sxs-lookup"><span data-stu-id="a071d-127">In the <xref:System.Windows.Controls.DataGrid> element, set the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property to the resource defined in the previous steps.</span></span> <span data-ttu-id="a071d-128">Přiřaďte prostředek jako statický prostředek.</span><span class="sxs-lookup"><span data-stu-id="a071d-128">Assign the resource as a static resource.</span></span>  
  
     <span data-ttu-id="a071d-129">Následující kód XAML ukazuje vlastnost <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> nastavenou na prostředek z předchozího příkladu.</span><span class="sxs-lookup"><span data-stu-id="a071d-129">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property set to the resource from the previous example.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#4](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a><span data-ttu-id="a071d-130">Nastavení viditelnosti a prevence horizontálního posouvání podrobností řádku</span><span class="sxs-lookup"><span data-stu-id="a071d-130">To set visibility and prevent horizontal scrolling for row details</span></span>  
  
1. <span data-ttu-id="a071d-131">V případě potřeby nastavte vlastnost <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> na hodnotu <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode>.</span><span class="sxs-lookup"><span data-stu-id="a071d-131">If needed, set the <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> property to a <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> value.</span></span>  
  
     <span data-ttu-id="a071d-132">Ve výchozím nastavení je hodnota nastavena na <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>.</span><span class="sxs-lookup"><span data-stu-id="a071d-132">By default, the value is set to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>.</span></span> <span data-ttu-id="a071d-133">Můžete nastavit, aby se zobrazily <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> pro zobrazení podrobností o všech řádcích nebo <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> pro skrytí podrobností pro všechny řádky.</span><span class="sxs-lookup"><span data-stu-id="a071d-133">You can set it to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> to show the details for all of the rows or <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> to hide the details for all rows.</span></span>  
  
2. <span data-ttu-id="a071d-134">V případě potřeby nastavte vlastnost <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> na `true`, aby se zabránilo vodorovnému posouvání oddílu podrobností řádku.</span><span class="sxs-lookup"><span data-stu-id="a071d-134">If needed, set the <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> property to `true` to prevent the row details section from scrolling horizontally.</span></span>
