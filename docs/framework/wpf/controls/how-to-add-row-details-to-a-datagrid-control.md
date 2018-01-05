---
title: "Postupy: Přidání podrobností řádku do ovládacího prvku DataGrid"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataTemplate [WPF], DataGrid
- row details [WPF], DataGrid
- DataGrid [WPF], row details
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f65eb9e916fad83deb1476c1d8f0def4981d08d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a><span data-ttu-id="a62b2-102">Postupy: Přidání podrobností řádku do ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="a62b2-102">How to: Add Row Details to a DataGrid Control</span></span>
<span data-ttu-id="a62b2-103">Při použití <xref:System.Windows.Controls.DataGrid> řízení, prezentace dat můžete přizpůsobit přidáním v části Podrobnosti o řádek.</span><span class="sxs-lookup"><span data-stu-id="a62b2-103">When using the <xref:System.Windows.Controls.DataGrid> control, you can customize the data presentation by adding a row details section.</span></span> <span data-ttu-id="a62b2-104">Přidání v části Podrobnosti o řádek umožňují seskupit některá data v šabloně, která je volitelně zobrazená nebo sbalená.</span><span class="sxs-lookup"><span data-stu-id="a62b2-104">Adding a row details section enables you to group some data in a template that is optionally visible or collapsed.</span></span> <span data-ttu-id="a62b2-105">Například můžete přidat podrobnosti řádku <xref:System.Windows.Controls.DataGrid> , uvede pouze souhrn dat pro každý řádek <xref:System.Windows.Controls.DataGrid>, ale přináší další datová pole, když uživatel vybere řádek.</span><span class="sxs-lookup"><span data-stu-id="a62b2-105">For example, you can add row details to a <xref:System.Windows.Controls.DataGrid> that presents only a summary of the data for each row in the <xref:System.Windows.Controls.DataGrid>, but presents more data fields when the user selects a row.</span></span> <span data-ttu-id="a62b2-106">Definovat šablonu pro v oddílu Podrobnosti řádek <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a62b2-106">You define the template for the row details section in the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property.</span></span> <span data-ttu-id="a62b2-107">Následující obrázek znázorňuje příklad v části Podrobnosti o řádek.</span><span class="sxs-lookup"><span data-stu-id="a62b2-107">The following illustration shows an example of a row details section.</span></span>  
  
 <span data-ttu-id="a62b2-108">![DataGrid – zobrazený s podrobnostmi řádků](../../../../docs/framework/wpf/controls/media/ndp-rowdetails.png "NDP_RowDetails")</span><span class="sxs-lookup"><span data-stu-id="a62b2-108">![DataGrid shown with row details](../../../../docs/framework/wpf/controls/media/ndp-rowdetails.png "NDP_RowDetails")</span></span>  
  
 <span data-ttu-id="a62b2-109">Podrobnosti šablony řádku definujete jako buď inline kód XAML nebo jako prostředek.</span><span class="sxs-lookup"><span data-stu-id="a62b2-109">You define the row details template as either inline XAML or as a resource.</span></span> <span data-ttu-id="a62b2-110">V následujících postupech se zobrazí obou přístupů.</span><span class="sxs-lookup"><span data-stu-id="a62b2-110">Both approaches are shown in the following procedures.</span></span> <span data-ttu-id="a62b2-111">Šablonu dat, který je přidán jako prostředek lze použít v rámci projektu bez nutnosti znovu vytvářet šablony.</span><span class="sxs-lookup"><span data-stu-id="a62b2-111">A data template that is added as a resource can be used throughout the project without re-creating the template.</span></span> <span data-ttu-id="a62b2-112">Šablonu data, která je přidána jako inline kód XAML je k dispozici pouze z ovládacího prvku kterých byla definována.</span><span class="sxs-lookup"><span data-stu-id="a62b2-112">A data template that is added as inline XAML is only accessible from the control where it is defined.</span></span>  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a><span data-ttu-id="a62b2-113">Zobrazit podrobnosti o řádek pomocí inline kód XAML</span><span class="sxs-lookup"><span data-stu-id="a62b2-113">To display row details by using inline XAML</span></span>  
  
1.  <span data-ttu-id="a62b2-114">Vytvoření <xref:System.Windows.Controls.DataGrid> , které zobrazuje data ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="a62b2-114">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2.  <span data-ttu-id="a62b2-115">V <xref:System.Windows.Controls.DataGrid> elementu, přidejte <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> elementu.</span><span class="sxs-lookup"><span data-stu-id="a62b2-115">In the <xref:System.Windows.Controls.DataGrid> element, add a <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> element.</span></span>  
  
3.  <span data-ttu-id="a62b2-116">Vytvoření <xref:System.Windows.DataTemplate> vzhled v části Podrobnosti o řádek, který definuje.</span><span class="sxs-lookup"><span data-stu-id="a62b2-116">Create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="a62b2-117">Následující XAML ukazuje <xref:System.Windows.Controls.DataGrid> a definování <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> vložené.</span><span class="sxs-lookup"><span data-stu-id="a62b2-117">The following XAML shows the <xref:System.Windows.Controls.DataGrid> and how to define the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> inline.</span></span> <span data-ttu-id="a62b2-118"><xref:System.Windows.Controls.DataGrid> Zobrazí tři hodnoty v každém řádku a tři další hodnoty když je vybraný řádek.</span><span class="sxs-lookup"><span data-stu-id="a62b2-118">The <xref:System.Windows.Controls.DataGrid> displays three values in each row and three more values when the row is selected.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     <span data-ttu-id="a62b2-119">Následující kód ukazuje dotaz, který slouží k výběru data, která se zobrazí v <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="a62b2-119">The following code shows the query that is used to select the data that is displayed in the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="a62b2-120">V tomto příkladu dotaz vybere data z entity, která obsahuje informace o zákazníkovi.</span><span class="sxs-lookup"><span data-stu-id="a62b2-120">In this example, the query selects data from an entity that contains customer information.</span></span>  
  
     [!code-csharp[DataGrid_RowDetails#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a><span data-ttu-id="a62b2-121">Zobrazit podrobnosti o řádek pomocí prostředku</span><span class="sxs-lookup"><span data-stu-id="a62b2-121">To display row details by using a resource</span></span>  
  
1.  <span data-ttu-id="a62b2-122">Vytvoření <xref:System.Windows.Controls.DataGrid> , které zobrazuje data ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="a62b2-122">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2.  <span data-ttu-id="a62b2-123">Přidat <xref:System.Windows.FrameworkElement.Resources%2A> element pro kořenový element například <xref:System.Windows.Window> ovládací prvek nebo <xref:System.Windows.Controls.Page> řídit, nebo přidejte <xref:System.Windows.Application.Resources%2A> elementu, který chcete <xref:System.Windows.Application> – třída v souboru App.xaml (nebo Application.xaml).</span><span class="sxs-lookup"><span data-stu-id="a62b2-123">Add a <xref:System.Windows.FrameworkElement.Resources%2A> element to the root element, such as a <xref:System.Windows.Window> control or a <xref:System.Windows.Controls.Page> control, or add a <xref:System.Windows.Application.Resources%2A> element to the <xref:System.Windows.Application> class in the App.xaml (or Application.xaml) file.</span></span>  
  
3.  <span data-ttu-id="a62b2-124">V elementu prostředky, vytvořte <xref:System.Windows.DataTemplate> vzhled v části Podrobnosti o řádek, který definuje.</span><span class="sxs-lookup"><span data-stu-id="a62b2-124">In the resources element, create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="a62b2-125">Následující XAML ukazuje <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> definované v <xref:System.Windows.Application> třídy.</span><span class="sxs-lookup"><span data-stu-id="a62b2-125">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> defined in the <xref:System.Windows.Application> class.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4.  <span data-ttu-id="a62b2-126">Na <xref:System.Windows.DataTemplate>, nastavte [x: Key – direktiva](../../../../docs/framework/xaml-services/x-key-directive.md) na hodnotu, která jednoznačně identifikuje data šablony.</span><span class="sxs-lookup"><span data-stu-id="a62b2-126">On the <xref:System.Windows.DataTemplate>, set the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) to a value that uniquely identifies the data template.</span></span>  
  
5.  <span data-ttu-id="a62b2-127">V <xref:System.Windows.Controls.DataGrid> , nastavena <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> vlastnost prostředku definované v předchozích krocích.</span><span class="sxs-lookup"><span data-stu-id="a62b2-127">In the <xref:System.Windows.Controls.DataGrid> element, set the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property to the resource defined in the previous steps.</span></span> <span data-ttu-id="a62b2-128">Přiřadíte prostředek jako statické prostředek.</span><span class="sxs-lookup"><span data-stu-id="a62b2-128">Assign the resource as a static resource.</span></span>  
  
     <span data-ttu-id="a62b2-129">Následující XAML ukazuje <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> vlastností nastavenou na prostředek z předchozího příkladu.</span><span class="sxs-lookup"><span data-stu-id="a62b2-129">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property set to the resource from the previous example.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a><span data-ttu-id="a62b2-130">Nastavit viditelnost a zabránit vodorovného posouvání podrobnosti řádek</span><span class="sxs-lookup"><span data-stu-id="a62b2-130">To set visibility and prevent horizontal scrolling for row details</span></span>  
  
1.  <span data-ttu-id="a62b2-131">V případě potřeby nastavte <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> vlastnosti <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a62b2-131">If needed, set the <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> property to a <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> value.</span></span>  
  
     <span data-ttu-id="a62b2-132">Ve výchozím nastavení, je hodnota nastavena <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>.</span><span class="sxs-lookup"><span data-stu-id="a62b2-132">By default, the value is set to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>.</span></span> <span data-ttu-id="a62b2-133">Můžete nastavit na <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> a zobrazit podrobnosti pro všechny řádky nebo <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> skrýt podrobnosti pro všechny řádky.</span><span class="sxs-lookup"><span data-stu-id="a62b2-133">You can set it to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> to show the details for all of the rows or <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> to hide the details for all rows.</span></span>  
  
2.  <span data-ttu-id="a62b2-134">V případě potřeby nastavte <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> vlastnost `true` zabránit řádek podrobnosti části posouvání vodorovně.</span><span class="sxs-lookup"><span data-stu-id="a62b2-134">If needed, set the <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> property to `true` to prevent the row details section from scrolling horizontally.</span></span>
