---
title: 'Postupy: Přidání podrobností řádku do ovládacího prvku DataGrid'
description: Přečtěte si, jak přizpůsobit prezentaci dat při použití ovládacího prvku Windows Presentation Foundation DataGrid přidáním části s podrobnostmi řádku.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataTemplate [WPF], DataGrid
- row details [WPF], DataGrid
- DataGrid [WPF], row details
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
ms.openlocfilehash: 8fd6b07f454681a0eed70d7a6208cfcc426dc920
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164948"
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a><span data-ttu-id="1ca36-103">Postupy: Přidání podrobností řádku do ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="1ca36-103">How to: Add Row Details to a DataGrid Control</span></span>
<span data-ttu-id="1ca36-104">Při použití <xref:System.Windows.Controls.DataGrid> ovládacího prvku můžete upravit prezentaci dat přidáním části Podrobnosti řádku.</span><span class="sxs-lookup"><span data-stu-id="1ca36-104">When using the <xref:System.Windows.Controls.DataGrid> control, you can customize the data presentation by adding a row details section.</span></span> <span data-ttu-id="1ca36-105">Přidáním části Podrobnosti řádku můžete seskupit některá data do šablony, která je volitelně viditelná nebo sbalená.</span><span class="sxs-lookup"><span data-stu-id="1ca36-105">Adding a row details section enables you to group some data in a template that is optionally visible or collapsed.</span></span> <span data-ttu-id="1ca36-106">Například můžete přidat podrobnosti řádku do a <xref:System.Windows.Controls.DataGrid> , který prezentuje pouze souhrn dat pro každý řádek v <xref:System.Windows.Controls.DataGrid> , ale prezentuje více datových polí, když uživatel vybere řádek.</span><span class="sxs-lookup"><span data-stu-id="1ca36-106">For example, you can add row details to a <xref:System.Windows.Controls.DataGrid> that presents only a summary of the data for each row in the <xref:System.Windows.Controls.DataGrid>, but presents more data fields when the user selects a row.</span></span> <span data-ttu-id="1ca36-107">V části vlastnosti definujete šablonu pro oddíl podrobnosti řádku <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> .</span><span class="sxs-lookup"><span data-stu-id="1ca36-107">You define the template for the row details section in the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property.</span></span> <span data-ttu-id="1ca36-108">Následující ilustrace znázorňuje příklad oddílu podrobností řádku.</span><span class="sxs-lookup"><span data-stu-id="1ca36-108">The following illustration shows an example of a row details section.</span></span>  
  
 <span data-ttu-id="1ca36-109">![DataGrid zobrazená s podrobnostmi řádku](./media/ndp-rowdetails.png "NDP_RowDetails")</span><span class="sxs-lookup"><span data-stu-id="1ca36-109">![DataGrid shown with row details](./media/ndp-rowdetails.png "NDP_RowDetails")</span></span>  
  
 <span data-ttu-id="1ca36-110">Šablonu podrobností řádku můžete definovat buď jako vložený kód XAML, nebo jako prostředek.</span><span class="sxs-lookup"><span data-stu-id="1ca36-110">You define the row details template as either inline XAML or as a resource.</span></span> <span data-ttu-id="1ca36-111">Oba přístupy jsou uvedené v následujících postupech.</span><span class="sxs-lookup"><span data-stu-id="1ca36-111">Both approaches are shown in the following procedures.</span></span> <span data-ttu-id="1ca36-112">Šablona dat, která je přidána jako prostředek, může být použita v celém projektu, aniž by bylo nutné šablonu znovu vytvořit.</span><span class="sxs-lookup"><span data-stu-id="1ca36-112">A data template that is added as a resource can be used throughout the project without re-creating the template.</span></span> <span data-ttu-id="1ca36-113">Šablona dat, která je přidána jako vložený kód XAML, je přístupná pouze z ovládacího prvku, kde je definována.</span><span class="sxs-lookup"><span data-stu-id="1ca36-113">A data template that is added as inline XAML is only accessible from the control where it is defined.</span></span>  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a><span data-ttu-id="1ca36-114">Zobrazení podrobností o řádku pomocí vloženého kódu XAML</span><span class="sxs-lookup"><span data-stu-id="1ca36-114">To display row details by using inline XAML</span></span>  
  
1. <span data-ttu-id="1ca36-115">Vytvoří objekt <xref:System.Windows.Controls.DataGrid> , který zobrazí data ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="1ca36-115">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2. <span data-ttu-id="1ca36-116">V <xref:System.Windows.Controls.DataGrid> elementu přidejte <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> element.</span><span class="sxs-lookup"><span data-stu-id="1ca36-116">In the <xref:System.Windows.Controls.DataGrid> element, add a <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> element.</span></span>  
  
3. <span data-ttu-id="1ca36-117">Vytvořte <xref:System.Windows.DataTemplate> , který definuje vzhled oddílu podrobností řádku.</span><span class="sxs-lookup"><span data-stu-id="1ca36-117">Create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="1ca36-118">Následující kód XAML ukazuje, <xref:System.Windows.Controls.DataGrid> jak definovat <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> vloženou.</span><span class="sxs-lookup"><span data-stu-id="1ca36-118">The following XAML shows the <xref:System.Windows.Controls.DataGrid> and how to define the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> inline.</span></span> <span data-ttu-id="1ca36-119"><xref:System.Windows.Controls.DataGrid>Zobrazí tři hodnoty v každém řádku a tři další hodnoty, když je vybrán řádek.</span><span class="sxs-lookup"><span data-stu-id="1ca36-119">The <xref:System.Windows.Controls.DataGrid> displays three values in each row and three more values when the row is selected.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#1](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     <span data-ttu-id="1ca36-120">Následující kód ukazuje dotaz, který se používá k výběru dat zobrazených v <xref:System.Windows.Controls.DataGrid> .</span><span class="sxs-lookup"><span data-stu-id="1ca36-120">The following code shows the query that is used to select the data that is displayed in the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="1ca36-121">V tomto příkladu dotaz vybírá data z entity, která obsahuje informace o zákaznících.</span><span class="sxs-lookup"><span data-stu-id="1ca36-121">In this example, the query selects data from an entity that contains customer information.</span></span>  
  
     [!code-csharp[DataGrid_RowDetails#2](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a><span data-ttu-id="1ca36-122">Zobrazení podrobností o řádku pomocí prostředku</span><span class="sxs-lookup"><span data-stu-id="1ca36-122">To display row details by using a resource</span></span>  
  
1. <span data-ttu-id="1ca36-123">Vytvoří objekt <xref:System.Windows.Controls.DataGrid> , který zobrazí data ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="1ca36-123">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2. <span data-ttu-id="1ca36-124">Přidejte <xref:System.Windows.FrameworkElement.Resources%2A> element do kořenového prvku, jako je například <xref:System.Windows.Window> ovládací prvek nebo <xref:System.Windows.Controls.Page> ovládací prvek, nebo přidejte <xref:System.Windows.Application.Resources%2A> element do <xref:System.Windows.Application> třídy v souboru App. XAML (nebo Application. XAML).</span><span class="sxs-lookup"><span data-stu-id="1ca36-124">Add a <xref:System.Windows.FrameworkElement.Resources%2A> element to the root element, such as a <xref:System.Windows.Window> control or a <xref:System.Windows.Controls.Page> control, or add a <xref:System.Windows.Application.Resources%2A> element to the <xref:System.Windows.Application> class in the App.xaml (or Application.xaml) file.</span></span>  
  
3. <span data-ttu-id="1ca36-125">V elementu Resources vytvořte objekt <xref:System.Windows.DataTemplate> , který definuje vzhled oddílu podrobností řádku.</span><span class="sxs-lookup"><span data-stu-id="1ca36-125">In the resources element, create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="1ca36-126">Následující kód XAML znázorňuje <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> definici ve <xref:System.Windows.Application> třídě.</span><span class="sxs-lookup"><span data-stu-id="1ca36-126">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> defined in the <xref:System.Windows.Application> class.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#3](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4. <span data-ttu-id="1ca36-127">Na rozhraní <xref:System.Windows.DataTemplate> nastavte [direktivu x:Key –](../../../desktop-wpf/xaml-services/xkey-directive.md) na hodnotu, která jedinečně identifikuje šablonu dat.</span><span class="sxs-lookup"><span data-stu-id="1ca36-127">On the <xref:System.Windows.DataTemplate>, set the [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) to a value that uniquely identifies the data template.</span></span>  
  
5. <span data-ttu-id="1ca36-128">V <xref:System.Windows.Controls.DataGrid> elementu nastavte <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> vlastnost na prostředek definovaný v předchozích krocích.</span><span class="sxs-lookup"><span data-stu-id="1ca36-128">In the <xref:System.Windows.Controls.DataGrid> element, set the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property to the resource defined in the previous steps.</span></span> <span data-ttu-id="1ca36-129">Přiřaďte prostředek jako statický prostředek.</span><span class="sxs-lookup"><span data-stu-id="1ca36-129">Assign the resource as a static resource.</span></span>  
  
     <span data-ttu-id="1ca36-130">Následující kód XAML ukazuje <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> vlastnost nastavenou na prostředek z předchozího příkladu.</span><span class="sxs-lookup"><span data-stu-id="1ca36-130">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property set to the resource from the previous example.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#4](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a><span data-ttu-id="1ca36-131">Nastavení viditelnosti a prevence horizontálního posouvání podrobností řádku</span><span class="sxs-lookup"><span data-stu-id="1ca36-131">To set visibility and prevent horizontal scrolling for row details</span></span>  
  
1. <span data-ttu-id="1ca36-132">V případě potřeby nastavte <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> vlastnost na <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1ca36-132">If needed, set the <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> property to a <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> value.</span></span>  
  
     <span data-ttu-id="1ca36-133">Ve výchozím nastavení je hodnota nastavena na <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected> .</span><span class="sxs-lookup"><span data-stu-id="1ca36-133">By default, the value is set to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>.</span></span> <span data-ttu-id="1ca36-134">Můžete ji nastavit tak, aby <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> zobrazovala podrobnosti pro všechny řádky nebo aby se <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> skryly podrobnosti pro všechny řádky.</span><span class="sxs-lookup"><span data-stu-id="1ca36-134">You can set it to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> to show the details for all of the rows or <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> to hide the details for all rows.</span></span>  
  
2. <span data-ttu-id="1ca36-135">V případě potřeby nastavte <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> vlastnost tak, aby `true` nedocházelo k vodorovnému posouvání oddílu podrobností řádku.</span><span class="sxs-lookup"><span data-stu-id="1ca36-135">If needed, set the <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> property to `true` to prevent the row details section from scrolling horizontally.</span></span>
