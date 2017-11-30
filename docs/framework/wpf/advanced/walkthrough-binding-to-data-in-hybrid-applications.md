---
title: "Návod: Připojení k datům v hybridních aplikacích"
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
- hybrid applications [WPF interoperability]
- data binding [WPF interoperability]
ms.assetid: 18997e71-745a-4425-9c69-2cbce1d8669e
caps.latest.revision: "39"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 957559cbc88855700471cc457f76d69ef5a296d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-binding-to-data-in-hybrid-applications"></a><span data-ttu-id="191e1-102">Návod: Připojení k datům v hybridních aplikacích</span><span class="sxs-lookup"><span data-stu-id="191e1-102">Walkthrough: Binding to Data in Hybrid Applications</span></span>
<span data-ttu-id="191e1-103">Vytvoření vazby zdroje dat k ovládacímu prvku je nezbytné pro poskytuje uživatelům přístup k základní data, zda používáte [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nebo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="191e1-103">Binding a data source to a control is essential for providing users with access to underlying data, whether you are using [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] or [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="191e1-104">Tento návod ukazuje, jak můžete pomocí datové vazby v hybridní aplikace, které zahrnují oba [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="191e1-104">This walkthrough shows how you can use data binding in hybrid applications that include both [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controls.</span></span>  
  
 <span data-ttu-id="191e1-105">Úkoly v tomto návodu zahrnují:</span><span class="sxs-lookup"><span data-stu-id="191e1-105">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="191e1-106">Vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="191e1-106">Creating the project.</span></span>  
  
-   <span data-ttu-id="191e1-107">Definování dat šablony.</span><span class="sxs-lookup"><span data-stu-id="191e1-107">Defining the data template.</span></span>  
  
-   <span data-ttu-id="191e1-108">Určení rozložení formuláře.</span><span class="sxs-lookup"><span data-stu-id="191e1-108">Specifying the form layout.</span></span>  
  
-   <span data-ttu-id="191e1-109">Zadání dat vazby.</span><span class="sxs-lookup"><span data-stu-id="191e1-109">Specifying data bindings.</span></span>  
  
-   <span data-ttu-id="191e1-110">Zobrazení dat pomocí vzájemná spolupráce.</span><span class="sxs-lookup"><span data-stu-id="191e1-110">Displaying data by using interoperation.</span></span>  
  
-   <span data-ttu-id="191e1-111">Přidání zdroje dat do projektu.</span><span class="sxs-lookup"><span data-stu-id="191e1-111">Adding the data source to the project.</span></span>  
  
-   <span data-ttu-id="191e1-112">Vazba ke zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="191e1-112">Binding to the data source.</span></span>  
  
 <span data-ttu-id="191e1-113">Kompletní kód tak seznam všech úloh v tomto návodu, najdete v části [datové vazby v ukázce hybridní aplikace](http://go.microsoft.com/fwlink/?LinkID=159983).</span><span class="sxs-lookup"><span data-stu-id="191e1-113">For a complete code listing of the tasks illustrated in this walkthrough, see [Data Binding in Hybrid Applications Sample](http://go.microsoft.com/fwlink/?LinkID=159983).</span></span>  
  
 <span data-ttu-id="191e1-114">Jakmile budete hotovi, budete mít k pochopení funkce vazby dat v hybridní aplikace.</span><span class="sxs-lookup"><span data-stu-id="191e1-114">When you are finished, you will have an understanding of data binding features in hybrid applications.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="191e1-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="191e1-115">Prerequisites</span></span>  
 <span data-ttu-id="191e1-116">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="191e1-116">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="191e1-117">.</span><span class="sxs-lookup"><span data-stu-id="191e1-117">.</span></span>  
  
-   <span data-ttu-id="191e1-118">Přístup k ukázková databáze Northwind systémem Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="191e1-118">Access to the Northwind sample database running on Microsoft SQL Server.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="191e1-119">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="191e1-119">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="191e1-120">Vytvoření a nastavení projektu</span><span class="sxs-lookup"><span data-stu-id="191e1-120">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="191e1-121">Vytvořte projekt aplikace WPF s názvem `WPFWithWFAndDatabinding`.</span><span class="sxs-lookup"><span data-stu-id="191e1-121">Create a WPF Application project named `WPFWithWFAndDatabinding`.</span></span>  
  
2.  <span data-ttu-id="191e1-122">V Průzkumníku řešení přidejte odkazy na následující sestavení.</span><span class="sxs-lookup"><span data-stu-id="191e1-122">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="191e1-123">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="191e1-123">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="191e1-124">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="191e1-124">System.Windows.Forms</span></span>  
  
3.  <span data-ttu-id="191e1-125">Otevřete MainWindow.xaml v [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="191e1-125">Open MainWindow.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="191e1-126">V <xref:System.Windows.Window> elementu, přidejte následující [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mapování obory názvů.</span><span class="sxs-lookup"><span data-stu-id="191e1-126">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespaces mapping.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <span data-ttu-id="191e1-127">Název výchozí <xref:System.Windows.Controls.Grid> element `mainGrid` přiřazením <xref:System.Windows.FrameworkElement.Name%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="191e1-127">Name the default <xref:System.Windows.Controls.Grid> element `mainGrid` by assigning the <xref:System.Windows.FrameworkElement.Name%2A> property.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]  
  
## <a name="defining-the-data-template"></a><span data-ttu-id="191e1-128">Definování dat šablony</span><span class="sxs-lookup"><span data-stu-id="191e1-128">Defining the Data Template</span></span>  
 <span data-ttu-id="191e1-129">Hlavní seznamu zákazníků se zobrazí v <xref:System.Windows.Controls.ListBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="191e1-129">The master list of customers is displayed in a <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="191e1-130">Následující příklad kódu definuje <xref:System.Windows.DataTemplate> objekt s názvem `ListItemsTemplate` která řídí stromu visual <xref:System.Windows.Controls.ListBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="191e1-130">The following code example defines a <xref:System.Windows.DataTemplate> object named `ListItemsTemplate` that controls the visual tree of the <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="191e1-131">To <xref:System.Windows.DataTemplate> je přiřazena k <xref:System.Windows.Controls.ListBox> ovládacího prvku <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="191e1-131">This <xref:System.Windows.DataTemplate> is assigned to the <xref:System.Windows.Controls.ListBox> control's <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> property.</span></span>  
  
#### <a name="to-define-the-data-template"></a><span data-ttu-id="191e1-132">Definování šablon dat</span><span class="sxs-lookup"><span data-stu-id="191e1-132">To define the data template</span></span>  
  
-   <span data-ttu-id="191e1-133">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> deklaraci elementu.</span><span class="sxs-lookup"><span data-stu-id="191e1-133">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]  
  
## <a name="specifying-the-form-layout"></a><span data-ttu-id="191e1-134">Určení rozložení formuláře</span><span class="sxs-lookup"><span data-stu-id="191e1-134">Specifying the Form Layout</span></span>  
 <span data-ttu-id="191e1-135">Rozložení formuláře je definována mřížka s tři řádky a tři sloupce.</span><span class="sxs-lookup"><span data-stu-id="191e1-135">The layout of the form is defined by a grid with three rows and three columns.</span></span> <span data-ttu-id="191e1-136"><xref:System.Windows.Controls.Label>ovládací prvky jsou k dispozici k identifikaci každý sloupec v tabulce Zákazníci.</span><span class="sxs-lookup"><span data-stu-id="191e1-136"><xref:System.Windows.Controls.Label> controls are provided to identify each column in the Customers table.</span></span>  
  
#### <a name="to-set-up-the-grid-layout"></a><span data-ttu-id="191e1-137">Nastavit rozložení mřížky</span><span class="sxs-lookup"><span data-stu-id="191e1-137">To set up the Grid layout</span></span>  
  
-   <span data-ttu-id="191e1-138">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> deklaraci elementu.</span><span class="sxs-lookup"><span data-stu-id="191e1-138">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]  
  
#### <a name="to-set-up-the-label-controls"></a><span data-ttu-id="191e1-139">Nastavit ovládací prvky popisek</span><span class="sxs-lookup"><span data-stu-id="191e1-139">To set up the Label controls</span></span>  
  
-   <span data-ttu-id="191e1-140">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> deklaraci elementu.</span><span class="sxs-lookup"><span data-stu-id="191e1-140">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]  
  
## <a name="specifying-data-bindings"></a><span data-ttu-id="191e1-141">Určení datové vazby</span><span class="sxs-lookup"><span data-stu-id="191e1-141">Specifying Data Bindings</span></span>  
 <span data-ttu-id="191e1-142">Hlavní seznamu zákazníků se zobrazí v <xref:System.Windows.Controls.ListBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="191e1-142">The master list of customers is displayed in a <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="191e1-143">Připojený `ListItemsTemplate` váže <xref:System.Windows.Controls.TextBlock> řídit k `ContactName` pole z databáze.</span><span class="sxs-lookup"><span data-stu-id="191e1-143">The attached `ListItemsTemplate` binds a <xref:System.Windows.Controls.TextBlock> control to the `ContactName` field from the database.</span></span>  
  
 <span data-ttu-id="191e1-144">Podrobnosti o všech vybraných záznamech zákazníka se zobrazují v několika <xref:System.Windows.Controls.TextBox> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="191e1-144">The details of each customer record are displayed in several <xref:System.Windows.Controls.TextBox> controls.</span></span>  
  
#### <a name="to-specify-data-bindings"></a><span data-ttu-id="191e1-145">Chcete-li určit datové vazby</span><span class="sxs-lookup"><span data-stu-id="191e1-145">To specify data bindings</span></span>  
  
-   <span data-ttu-id="191e1-146">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> deklaraci elementu.</span><span class="sxs-lookup"><span data-stu-id="191e1-146">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     <span data-ttu-id="191e1-147"><xref:System.Windows.Data.Binding> Třídy vazby <xref:System.Windows.Controls.TextBox> ovládacích prvků na odpovídající pole v databázi.</span><span class="sxs-lookup"><span data-stu-id="191e1-147">The <xref:System.Windows.Data.Binding> class binds the <xref:System.Windows.Controls.TextBox> controls to the appropriate fields in the database.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]  
  
## <a name="displaying-data-by-using-interoperation"></a><span data-ttu-id="191e1-148">Zobrazení dat pomocí vzájemná spolupráce</span><span class="sxs-lookup"><span data-stu-id="191e1-148">Displaying Data by Using Interoperation</span></span>  
 <span data-ttu-id="191e1-149">Objednávky odpovídající vybraného zákazníka se zobrazují v <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> ovládací prvek s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="191e1-149">The orders corresponding to the selected customer are displayed in a <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> control named `dataGridView1`.</span></span> <span data-ttu-id="191e1-150">`dataGridView1` Ovládací prvek vázán ke zdroji dat v souboru kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="191e1-150">The `dataGridView1` control is bound to the data source in the code-behind file.</span></span> <span data-ttu-id="191e1-151">A <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládací prvek je nadřazený tohoto [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="191e1-151">A <xref:System.Windows.Forms.Integration.WindowsFormsHost> control is the parent of this [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
#### <a name="to-display-data-in-the-datagridview-control"></a><span data-ttu-id="191e1-152">K zobrazení dat v ovládacím prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="191e1-152">To display data in the DataGridView control</span></span>  
  
-   <span data-ttu-id="191e1-153">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> deklaraci elementu.</span><span class="sxs-lookup"><span data-stu-id="191e1-153">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]  
  
## <a name="adding-the-data-source-to-the-project"></a><span data-ttu-id="191e1-154">Přidání zdroje dat do projektu</span><span class="sxs-lookup"><span data-stu-id="191e1-154">Adding the Data Source to the Project</span></span>  
 <span data-ttu-id="191e1-155">S [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], můžete snadno přidat zdroje dat do projektu.</span><span class="sxs-lookup"><span data-stu-id="191e1-155">With [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], you can easily add a data source to your project.</span></span> <span data-ttu-id="191e1-156">Tento postup přidá silného typu datové sady do projektu.</span><span class="sxs-lookup"><span data-stu-id="191e1-156">This procedure adds a strongly typed data set to your project.</span></span> <span data-ttu-id="191e1-157">Také se přidají několik jiné třídy, které podporují, jako je například adaptéry tabulek pro každou z vybrané tabulky.</span><span class="sxs-lookup"><span data-stu-id="191e1-157">Several other support classes, such as table adapters for each of the chosen tables, are also added.</span></span>  
  
#### <a name="to-add-the-data-source"></a><span data-ttu-id="191e1-158">Přidání zdroje dat</span><span class="sxs-lookup"><span data-stu-id="191e1-158">To add the data source</span></span>  
  
1.  <span data-ttu-id="191e1-159">Z **Data** nabídce vyberte možnost **přidat nový zdroj dat**.</span><span class="sxs-lookup"><span data-stu-id="191e1-159">From the **Data** menu, select **Add New Data Source**.</span></span>  
  
2.  <span data-ttu-id="191e1-160">V **Průvodce konfigurací zdroje dat**, vytvořit připojení k databázi Northwind pomocí datové sady.</span><span class="sxs-lookup"><span data-stu-id="191e1-160">In the **Data Source Configuration Wizard**, create a connection to the Northwind database by using a dataset.</span></span> <span data-ttu-id="191e1-161">Další informace najdete v tématu [postupy: připojování k datům v databázi](http://msdn.microsoft.com/library/6c56e54e-8834-4297-85aa-cc1a443ba556).</span><span class="sxs-lookup"><span data-stu-id="191e1-161">For more information, see [How to: Connect to Data in a Database](http://msdn.microsoft.com/library/6c56e54e-8834-4297-85aa-cc1a443ba556).</span></span>  
  
3.  <span data-ttu-id="191e1-162">Po zobrazení výzvy pomocí **Průvodce konfigurací zdroje dat**, uložit připojovací řetězec jako `NorthwindConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="191e1-162">When you are prompted by the **Data Source Configuration Wizard**, save the connection string as `NorthwindConnectionString`.</span></span>  
  
4.  <span data-ttu-id="191e1-163">Po zobrazení výzvy zvolte databázové objekty, vyberte `Customers` a `Orders` tabulky a název generované datové sady `NorthwindDataSet`.</span><span class="sxs-lookup"><span data-stu-id="191e1-163">When you are prompted to choose your database objects, select the `Customers` and `Orders` tables, and name the generated data set `NorthwindDataSet`.</span></span>  
  
## <a name="binding-to-the-data-source"></a><span data-ttu-id="191e1-164">Vytvoření vazby ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="191e1-164">Binding to the Data Source</span></span>  
 <span data-ttu-id="191e1-165"><xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> Součást poskytuje jednotné rozhraní pro zdroj dat aplikace.</span><span class="sxs-lookup"><span data-stu-id="191e1-165">The <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> component provides a uniform interface for the application's data source.</span></span> <span data-ttu-id="191e1-166">Vazba ke zdroji dat je implementovaná v souboru kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="191e1-166">Binding to the data source is implemented in the code-behind file.</span></span>  
  
#### <a name="to-bind-to-the-data-source"></a><span data-ttu-id="191e1-167">Při vytváření vazby ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="191e1-167">To bind to the data source</span></span>  
  
1.  <span data-ttu-id="191e1-168">Otevřete soubor kódu, který se nazývá MainWindow.xaml.vb nebo MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="191e1-168">Open the code-behind file, which is named MainWindow.xaml.vb or MainWindow.xaml.cs.</span></span>  
  
2.  <span data-ttu-id="191e1-169">Zkopírujte následující kód do `MainWindow` definici třídy.</span><span class="sxs-lookup"><span data-stu-id="191e1-169">Copy the following code into the `MainWindow` class definition.</span></span>  
  
     <span data-ttu-id="191e1-170">Tento kód deklaruje <xref:System.Windows.Forms.BindingSource> součásti a přidružené pomocných tříd, které se připojují k databázi.</span><span class="sxs-lookup"><span data-stu-id="191e1-170">This code declares the <xref:System.Windows.Forms.BindingSource> component and associated helper classes that connect to the database.</span></span>  
  
     [!code-csharp[WPFWithWFAndDatabinding#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]  
  
3.  <span data-ttu-id="191e1-171">Zkopírujte následující kód do konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="191e1-171">Copy the following code into the constructor.</span></span>  
  
     <span data-ttu-id="191e1-172">Tento kód vytvoří a inicializuje <xref:System.Windows.Forms.BindingSource> součásti.</span><span class="sxs-lookup"><span data-stu-id="191e1-172">This code creates and initializes the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
     [!code-csharp[WPFWithWFAndDatabinding#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]  
  
4.  <span data-ttu-id="191e1-173">Otevřete MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="191e1-173">Open MainWindow.xaml.</span></span>  
  
5.  <span data-ttu-id="191e1-174">V návrhovém zobrazení nebo zobrazení jazyka XAML, vyberte <xref:System.Windows.Window> elementu.</span><span class="sxs-lookup"><span data-stu-id="191e1-174">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>  
  
6.  <span data-ttu-id="191e1-175">V okně vlastností klikněte **události** kartě.</span><span class="sxs-lookup"><span data-stu-id="191e1-175">In the Properties window, click the **Events** tab.</span></span>  
  
7.  <span data-ttu-id="191e1-176">Dvakrát klikněte <xref:System.Windows.FrameworkElement.Loaded> událostí.</span><span class="sxs-lookup"><span data-stu-id="191e1-176">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
8.  <span data-ttu-id="191e1-177">Zkopírujte následující kód do <xref:System.Windows.FrameworkElement.Loaded> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="191e1-177">Copy the following code into the <xref:System.Windows.FrameworkElement.Loaded> event handler.</span></span>  
  
     <span data-ttu-id="191e1-178">Tento kód přiřadí <xref:System.Windows.Forms.BindingSource> součásti jako kontextu dat a naplní `Customers` a `Orders` adaptér objekty.</span><span class="sxs-lookup"><span data-stu-id="191e1-178">This code assigns the <xref:System.Windows.Forms.BindingSource> component as the data context and populates the `Customers` and `Orders` adapter objects.</span></span>  
  
     [!code-csharp[WPFWithWFAndDatabinding#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]  
  
9. <span data-ttu-id="191e1-179">Zkopírujte následující kód do `MainWindow` definici třídy.</span><span class="sxs-lookup"><span data-stu-id="191e1-179">Copy the following code into the `MainWindow` class definition.</span></span>  
  
     <span data-ttu-id="191e1-180">Tato metoda zpracovává <xref:System.Windows.Data.CollectionView.CurrentChanged> událostí a aktualizuje aktuální položky datové vazby.</span><span class="sxs-lookup"><span data-stu-id="191e1-180">This method handles the <xref:System.Windows.Data.CollectionView.CurrentChanged> event and updates the current item of the data binding.</span></span>  
  
     [!code-csharp[WPFWithWFAndDatabinding#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]  
  
10. <span data-ttu-id="191e1-181">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="191e1-181">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="191e1-182">Viz také</span><span class="sxs-lookup"><span data-stu-id="191e1-182">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="191e1-183">Návrhář WPF</span><span class="sxs-lookup"><span data-stu-id="191e1-183">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="191e1-184">Datové vazby v ukázce hybridní aplikace</span><span class="sxs-lookup"><span data-stu-id="191e1-184">Data Binding in Hybrid Applications Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159983)  
 [<span data-ttu-id="191e1-185">Postupy: Hostování ovládacího prvku Windows Forms složené v grafickém subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="191e1-185">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="191e1-186">Postupy: Hostování složeného ovládacího prvku WPF ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="191e1-186">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
