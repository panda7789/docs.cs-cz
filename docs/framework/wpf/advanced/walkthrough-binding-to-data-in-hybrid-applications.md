---
title: 'Průvodce: Připojení k datům v hybridních aplikacích'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- data binding [WPF interoperability]
ms.assetid: 18997e71-745a-4425-9c69-2cbce1d8669e
ms.openlocfilehash: 2a20dc95467df4baedce2f4acc63f0c029f178c6
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748489"
---
# <a name="walkthrough-binding-to-data-in-hybrid-applications"></a><span data-ttu-id="d8bbf-102">Průvodce: Připojení k datům v hybridních aplikacích</span><span class="sxs-lookup"><span data-stu-id="d8bbf-102">Walkthrough: Binding to Data in Hybrid Applications</span></span>
<span data-ttu-id="d8bbf-103">Vytvoření vazby zdroje dat k ovládacímu prvku je zásadní pro zároveň uživatelům poskytují přístup k podkladová data, ať používáte [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nebo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d8bbf-103">Binding a data source to a control is essential for providing users with access to underlying data, whether you are using [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] or [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="d8bbf-104">Tento návod ukazuje, jak můžete datové vazby v hybridních aplikacích, které zahrnují oba [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-104">This walkthrough shows how you can use data binding in hybrid applications that include both [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controls.</span></span>  
  
 <span data-ttu-id="d8bbf-105">Úlohy v tomto návodu zahrnují:</span><span class="sxs-lookup"><span data-stu-id="d8bbf-105">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="d8bbf-106">Vytvoření projektu.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-106">Creating the project.</span></span>  
  
-   <span data-ttu-id="d8bbf-107">Definice šablony.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-107">Defining the data template.</span></span>  
  
-   <span data-ttu-id="d8bbf-108">Určení rozložení formuláře.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-108">Specifying the form layout.</span></span>  
  
-   <span data-ttu-id="d8bbf-109">Určení datové vazby.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-109">Specifying data bindings.</span></span>  
  
-   <span data-ttu-id="d8bbf-110">Zobrazení dat s využitím vzájemná spolupráce grafického subsystému.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-110">Displaying data by using interoperation.</span></span>  
  
-   <span data-ttu-id="d8bbf-111">Přidání zdroje dat do projektu.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-111">Adding the data source to the project.</span></span>  
  
-   <span data-ttu-id="d8bbf-112">Vytvoření vazby ke zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-112">Binding to the data source.</span></span>  
  
 <span data-ttu-id="d8bbf-113">Kompletní výpis kódu úloh v tomto návodu, naleznete v tématu [datové vazby v ukázkové aplikace hybridní](https://go.microsoft.com/fwlink/?LinkID=159983).</span><span class="sxs-lookup"><span data-stu-id="d8bbf-113">For a complete code listing of the tasks illustrated in this walkthrough, see [Data Binding in Hybrid Applications Sample](https://go.microsoft.com/fwlink/?LinkID=159983).</span></span>  
  
 <span data-ttu-id="d8bbf-114">Až budete hotovi, budete mít znalost funkcí datové vazby v hybridních aplikacích.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-114">When you are finished, you will have an understanding of data binding features in hybrid applications.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d8bbf-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d8bbf-115">Prerequisites</span></span>  
 <span data-ttu-id="d8bbf-116">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="d8bbf-116">You need the following components to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="d8bbf-117">Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-117">Visual Studio.</span></span>  
  
-   <span data-ttu-id="d8bbf-118">Přístup k ukázkové databázi Northwind a systémem Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-118">Access to the Northwind sample database running on Microsoft SQL Server.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="d8bbf-119">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="d8bbf-119">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="d8bbf-120">K vytvoření a nastavení projektu</span><span class="sxs-lookup"><span data-stu-id="d8bbf-120">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="d8bbf-121">Vytvoření projektu aplikace WPF s názvem `WPFWithWFAndDatabinding`.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-121">Create a WPF Application project named `WPFWithWFAndDatabinding`.</span></span>  
  
2.  <span data-ttu-id="d8bbf-122">V Průzkumníku řešení přidejte odkazy na následující sestavení.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-122">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="d8bbf-123">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="d8bbf-123">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="d8bbf-124">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="d8bbf-124">System.Windows.Forms</span></span>  
  
3.  <span data-ttu-id="d8bbf-125">Otevřete soubor MainWindow.xaml v [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d8bbf-125">Open MainWindow.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="d8bbf-126">V <xref:System.Windows.Window> prvku, přidejte následující [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mapování oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-126">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespaces mapping.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <span data-ttu-id="d8bbf-127">Pojmenujte výchozí <xref:System.Windows.Controls.Grid> element `mainGrid` přiřazením <xref:System.Windows.FrameworkElement.Name%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-127">Name the default <xref:System.Windows.Controls.Grid> element `mainGrid` by assigning the <xref:System.Windows.FrameworkElement.Name%2A> property.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]  
  
## <a name="defining-the-data-template"></a><span data-ttu-id="d8bbf-128">Definování šablon dat</span><span class="sxs-lookup"><span data-stu-id="d8bbf-128">Defining the Data Template</span></span>  
 <span data-ttu-id="d8bbf-129">Zobrazí se seznam zákazníků v <xref:System.Windows.Controls.ListBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-129">The master list of customers is displayed in a <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="d8bbf-130">Následující příklad kódu definuje <xref:System.Windows.DataTemplate> objekt s názvem `ListItemsTemplate` , která řídí vizuálního stromu <xref:System.Windows.Controls.ListBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-130">The following code example defines a <xref:System.Windows.DataTemplate> object named `ListItemsTemplate` that controls the visual tree of the <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="d8bbf-131">To <xref:System.Windows.DataTemplate> je přiřazen <xref:System.Windows.Controls.ListBox> ovládacího prvku <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-131">This <xref:System.Windows.DataTemplate> is assigned to the <xref:System.Windows.Controls.ListBox> control's <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> property.</span></span>  
  
#### <a name="to-define-the-data-template"></a><span data-ttu-id="d8bbf-132">Definování šablon dat</span><span class="sxs-lookup"><span data-stu-id="d8bbf-132">To define the data template</span></span>  
  
-   <span data-ttu-id="d8bbf-133">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> deklarace prvku.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-133">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]  
  
## <a name="specifying-the-form-layout"></a><span data-ttu-id="d8bbf-134">Určení rozložení formuláře</span><span class="sxs-lookup"><span data-stu-id="d8bbf-134">Specifying the Form Layout</span></span>  
 <span data-ttu-id="d8bbf-135">Rozložení formuláře je definována grid se třemi řádky a tři sloupce.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-135">The layout of the form is defined by a grid with three rows and three columns.</span></span> <span data-ttu-id="d8bbf-136"><xref:System.Windows.Controls.Label> ovládací prvky jsou k dispozici k identifikaci jednotlivých sloupců v tabulce Zákazníci.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-136"><xref:System.Windows.Controls.Label> controls are provided to identify each column in the Customers table.</span></span>  
  
#### <a name="to-set-up-the-grid-layout"></a><span data-ttu-id="d8bbf-137">Nastavit rozložení mřížky</span><span class="sxs-lookup"><span data-stu-id="d8bbf-137">To set up the Grid layout</span></span>  
  
-   <span data-ttu-id="d8bbf-138">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> deklarace prvku.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-138">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]  
  
#### <a name="to-set-up-the-label-controls"></a><span data-ttu-id="d8bbf-139">Nastavit ovládací prvky popisku</span><span class="sxs-lookup"><span data-stu-id="d8bbf-139">To set up the Label controls</span></span>  
  
-   <span data-ttu-id="d8bbf-140">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> deklarace prvku.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-140">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]  
  
## <a name="specifying-data-bindings"></a><span data-ttu-id="d8bbf-141">Určení datové vazby</span><span class="sxs-lookup"><span data-stu-id="d8bbf-141">Specifying Data Bindings</span></span>  
 <span data-ttu-id="d8bbf-142">Zobrazí se seznam zákazníků v <xref:System.Windows.Controls.ListBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-142">The master list of customers is displayed in a <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="d8bbf-143">Připojený `ListItemsTemplate` vytvoří vazbu <xref:System.Windows.Controls.TextBlock> ovládací prvek `ContactName` pole z databáze.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-143">The attached `ListItemsTemplate` binds a <xref:System.Windows.Controls.TextBlock> control to the `ContactName` field from the database.</span></span>  
  
 <span data-ttu-id="d8bbf-144">Podrobnosti o jednotlivých záznam zákazníka se zobrazují v několika <xref:System.Windows.Controls.TextBox> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-144">The details of each customer record are displayed in several <xref:System.Windows.Controls.TextBox> controls.</span></span>  
  
#### <a name="to-specify-data-bindings"></a><span data-ttu-id="d8bbf-145">Chcete-li určit datové vazby</span><span class="sxs-lookup"><span data-stu-id="d8bbf-145">To specify data bindings</span></span>  
  
-   <span data-ttu-id="d8bbf-146">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> deklarace prvku.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-146">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     <span data-ttu-id="d8bbf-147"><xref:System.Windows.Data.Binding> Třídy vytvoří vazbu <xref:System.Windows.Controls.TextBox> ovládacích prvků na odpovídající pole v databázi.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-147">The <xref:System.Windows.Data.Binding> class binds the <xref:System.Windows.Controls.TextBox> controls to the appropriate fields in the database.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]  
  
## <a name="displaying-data-by-using-interoperation"></a><span data-ttu-id="d8bbf-148">Zobrazení dat s využitím vzájemná spolupráce grafického subsystému</span><span class="sxs-lookup"><span data-stu-id="d8bbf-148">Displaying Data by Using Interoperation</span></span>  
 <span data-ttu-id="d8bbf-149">Zobrazení objednávek odpovídající k vybranému zákazníkovi v <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> ovládací prvek s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-149">The orders corresponding to the selected customer are displayed in a <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> control named `dataGridView1`.</span></span> <span data-ttu-id="d8bbf-150">`dataGridView1` Ovládací prvek vázán na zdroj dat v souboru kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-150">The `dataGridView1` control is bound to the data source in the code-behind file.</span></span> <span data-ttu-id="d8bbf-151">A <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládací prvek je nadřazeného tohoto [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-151">A <xref:System.Windows.Forms.Integration.WindowsFormsHost> control is the parent of this [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
#### <a name="to-display-data-in-the-datagridview-control"></a><span data-ttu-id="d8bbf-152">Zobrazení dat v ovládacím prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="d8bbf-152">To display data in the DataGridView control</span></span>  
  
-   <span data-ttu-id="d8bbf-153">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> deklarace prvku.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-153">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]  
  
## <a name="adding-the-data-source-to-the-project"></a><span data-ttu-id="d8bbf-154">Přidání zdroje dat do projektu</span><span class="sxs-lookup"><span data-stu-id="d8bbf-154">Adding the Data Source to the Project</span></span>  
 <span data-ttu-id="d8bbf-155">Pomocí sady Visual Studio můžete snadno přidat zdroj dat do projektu.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-155">With Visual Studio, you can easily add a data source to your project.</span></span> <span data-ttu-id="d8bbf-156">Tento postup přidá silně typované datové sady do vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-156">This procedure adds a strongly typed data set to your project.</span></span> <span data-ttu-id="d8bbf-157">Přidají také několik jiných tříd podpory, jako jsou adaptéry tabulek pro jednotlivé vybrané tabulky.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-157">Several other support classes, such as table adapters for each of the chosen tables, are also added.</span></span>  
  
#### <a name="to-add-the-data-source"></a><span data-ttu-id="d8bbf-158">Přidání zdroje dat</span><span class="sxs-lookup"><span data-stu-id="d8bbf-158">To add the data source</span></span>  
  
1.  <span data-ttu-id="d8bbf-159">Z **Data** nabídce vyberte možnost **přidat nový zdroj dat**.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-159">From the **Data** menu, select **Add New Data Source**.</span></span>  
  
2.  <span data-ttu-id="d8bbf-160">V **Průvodce konfigurací zdroje dat**, vytvořit připojení k databázi Northwind pomocí datové sady.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-160">In the **Data Source Configuration Wizard**, create a connection to the Northwind database by using a dataset.</span></span> <span data-ttu-id="d8bbf-161">Další informace najdete v tématu [jak: Připojení k datům v databázi](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="d8bbf-161">For more information, see [How to: Connect to Data in a Database](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120)).</span></span>  
  
3.  <span data-ttu-id="d8bbf-162">Po zobrazení výzvy **Průvodce konfigurací zdroje dat**, uložit připojovací řetězec jako `NorthwindConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-162">When you are prompted by the **Data Source Configuration Wizard**, save the connection string as `NorthwindConnectionString`.</span></span>  
  
4.  <span data-ttu-id="d8bbf-163">Po zobrazení výzvy zvolte vaše databázové objekty, vyberte `Customers` a `Orders` tabulky a název generovaný sady dat `NorthwindDataSet`.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-163">When you are prompted to choose your database objects, select the `Customers` and `Orders` tables, and name the generated data set `NorthwindDataSet`.</span></span>  
  
## <a name="binding-to-the-data-source"></a><span data-ttu-id="d8bbf-164">Vytvoření vazby ke zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-164">Binding to the Data Source</span></span>  
 <span data-ttu-id="d8bbf-165"><xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> Součást poskytuje jednotné rozhraní pro zdroj dat aplikace.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-165">The <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> component provides a uniform interface for the application's data source.</span></span> <span data-ttu-id="d8bbf-166">Vazby ke zdroji dat je implementováno v souboru kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-166">Binding to the data source is implemented in the code-behind file.</span></span>  
  
#### <a name="to-bind-to-the-data-source"></a><span data-ttu-id="d8bbf-167">K vytvoření vazby ke zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-167">To bind to the data source</span></span>  
  
1.  <span data-ttu-id="d8bbf-168">Otevřete soubor kódu na pozadí, který se nazývá soubor MainWindow.xaml.vb nebo MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-168">Open the code-behind file, which is named MainWindow.xaml.vb or MainWindow.xaml.cs.</span></span>  
  
2.  <span data-ttu-id="d8bbf-169">Zkopírujte následující kód do `MainWindow` definici třídy.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-169">Copy the following code into the `MainWindow` class definition.</span></span>  
  
     <span data-ttu-id="d8bbf-170">Tento kód deklaruje <xref:System.Windows.Forms.BindingSource> komponenty a přidružené pomocné třídy, které se připojují k databázi.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-170">This code declares the <xref:System.Windows.Forms.BindingSource> component and associated helper classes that connect to the database.</span></span>  
  
     [!code-csharp[WPFWithWFAndDatabinding#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]

3.  <span data-ttu-id="d8bbf-171">Zkopírujte následující kód do konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-171">Copy the following code into the constructor.</span></span>

     <span data-ttu-id="d8bbf-172">Tento kód vytvoří a inicializuje <xref:System.Windows.Forms.BindingSource> komponenty.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-172">This code creates and initializes the <xref:System.Windows.Forms.BindingSource> component.</span></span>

     [!code-csharp[WPFWithWFAndDatabinding#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]

4.  <span data-ttu-id="d8bbf-173">Open MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-173">Open MainWindow.xaml.</span></span>

5.  <span data-ttu-id="d8bbf-174">V zobrazení návrhu nebo v XAML zobrazení, vyberte <xref:System.Windows.Window> elementu.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-174">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>

6.  <span data-ttu-id="d8bbf-175">V okně Vlastnosti klikněte na tlačítko **události** kartu.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-175">In the Properties window, click the **Events** tab.</span></span>

7.  <span data-ttu-id="d8bbf-176">Dvakrát klikněte <xref:System.Windows.FrameworkElement.Loaded> událostí.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-176">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

8.  <span data-ttu-id="d8bbf-177">Zkopírujte následující kód do <xref:System.Windows.FrameworkElement.Loaded> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-177">Copy the following code into the <xref:System.Windows.FrameworkElement.Loaded> event handler.</span></span>

     <span data-ttu-id="d8bbf-178">Tento kód přiřadí <xref:System.Windows.Forms.BindingSource> komponenty jako kontext dat a naplní `Customers` a `Orders` adaptér objekty.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-178">This code assigns the <xref:System.Windows.Forms.BindingSource> component as the data context and populates the `Customers` and `Orders` adapter objects.</span></span>

     [!code-csharp[WPFWithWFAndDatabinding#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]

9. <span data-ttu-id="d8bbf-179">Zkopírujte následující kód do `MainWindow` definici třídy.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-179">Copy the following code into the `MainWindow` class definition.</span></span>

     <span data-ttu-id="d8bbf-180">Tato metoda obsluhuje <xref:System.Windows.Data.CollectionView.CurrentChanged> událostí a aktualizuje aktuální položky datové vazby.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-180">This method handles the <xref:System.Windows.Data.CollectionView.CurrentChanged> event and updates the current item of the data binding.</span></span>

     [!code-csharp[WPFWithWFAndDatabinding#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]  
  
10. <span data-ttu-id="d8bbf-181">Stisknutím klávesy F5 sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d8bbf-181">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8bbf-182">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d8bbf-182">See also</span></span>
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="d8bbf-183">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d8bbf-183">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="d8bbf-184">Datové vazby v ukázce hybridní aplikace</span><span class="sxs-lookup"><span data-stu-id="d8bbf-184">Data Binding in Hybrid Applications Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159983)
- [<span data-ttu-id="d8bbf-185">Návod: Hostování složeného ovládacího Windows Forms v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="d8bbf-185">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="d8bbf-186">Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d8bbf-186">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
