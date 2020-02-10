---
title: 'Návod: Připojení k datům v hybridních aplikacích'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- data binding [WPF interoperability]
ms.assetid: 18997e71-745a-4425-9c69-2cbce1d8669e
ms.openlocfilehash: 0d1e66a1277e6a04d2f49ac91691160f70fb56e4
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095070"
---
# <a name="walkthrough-binding-to-data-in-hybrid-applications"></a><span data-ttu-id="28b35-102">Návod: Připojení k datům v hybridních aplikacích</span><span class="sxs-lookup"><span data-stu-id="28b35-102">Walkthrough: Binding to Data in Hybrid Applications</span></span>

<span data-ttu-id="28b35-103">Vytvoření vazby zdroje dat k ovládacímu prvku je nezbytné pro poskytování přístupu uživatelům s přístupem k podkladovým datům, ať už používáte model Windows Forms nebo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="28b35-103">Binding a data source to a control is essential for providing users with access to underlying data, whether you are using Windows Forms or [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="28b35-104">Tento návod ukazuje, jak můžete použít datovou vazbu v hybridních aplikacích, které zahrnují ovládací prvky model Windows Forms i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="28b35-104">This walkthrough shows how you can use data binding in hybrid applications that include both Windows Forms and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controls.</span></span>

<span data-ttu-id="28b35-105">Úlohy, které jsou znázorněné v tomto návodu, zahrnují:</span><span class="sxs-lookup"><span data-stu-id="28b35-105">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="28b35-106">Vytváří se projekt.</span><span class="sxs-lookup"><span data-stu-id="28b35-106">Creating the project.</span></span>

- <span data-ttu-id="28b35-107">Definování šablony dat.</span><span class="sxs-lookup"><span data-stu-id="28b35-107">Defining the data template.</span></span>

- <span data-ttu-id="28b35-108">Určení rozložení formuláře</span><span class="sxs-lookup"><span data-stu-id="28b35-108">Specifying the form layout.</span></span>

- <span data-ttu-id="28b35-109">Zadání datových vazeb.</span><span class="sxs-lookup"><span data-stu-id="28b35-109">Specifying data bindings.</span></span>

- <span data-ttu-id="28b35-110">Zobrazení dat pomocí meziprovozu.</span><span class="sxs-lookup"><span data-stu-id="28b35-110">Displaying data by using interoperation.</span></span>

- <span data-ttu-id="28b35-111">Přidání zdroje dat do projektu.</span><span class="sxs-lookup"><span data-stu-id="28b35-111">Adding the data source to the project.</span></span>

- <span data-ttu-id="28b35-112">Vazba na zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="28b35-112">Binding to the data source.</span></span>

<span data-ttu-id="28b35-113">Úplný výpis kódu úloh, které jsou znázorněné v tomto návodu, najdete v tématu [Ukázka datových vazeb v hybridních aplikacích](https://github.com/microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFWithWFAndDatabinding).</span><span class="sxs-lookup"><span data-stu-id="28b35-113">For a complete code listing of the tasks illustrated in this walkthrough, see [Data Binding in Hybrid Applications Sample](https://github.com/microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFWithWFAndDatabinding).</span></span>

<span data-ttu-id="28b35-114">Až budete hotovi, budete obeznámeni s funkcemi datových vazeb v hybridních aplikacích.</span><span class="sxs-lookup"><span data-stu-id="28b35-114">When you are finished, you will have an understanding of data binding features in hybrid applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="28b35-115">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="28b35-115">Prerequisites</span></span>

<span data-ttu-id="28b35-116">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="28b35-116">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="28b35-117">Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="28b35-117">Visual Studio.</span></span>

- <span data-ttu-id="28b35-118">Přístup k ukázkové databázi Northwind běžící na Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="28b35-118">Access to the Northwind sample database running on Microsoft SQL Server.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="28b35-119">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="28b35-119">Creating the Project</span></span>

### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="28b35-120">Vytvoření a nastavení projektu</span><span class="sxs-lookup"><span data-stu-id="28b35-120">To create and set up the project</span></span>

1. <span data-ttu-id="28b35-121">Vytvořte projekt aplikace WPF s názvem `WPFWithWFAndDatabinding`.</span><span class="sxs-lookup"><span data-stu-id="28b35-121">Create a WPF Application project named `WPFWithWFAndDatabinding`.</span></span>

2. <span data-ttu-id="28b35-122">V Průzkumník řešení přidejte odkazy na následující sestavení.</span><span class="sxs-lookup"><span data-stu-id="28b35-122">In Solution Explorer, add references to the following assemblies.</span></span>

    - <span data-ttu-id="28b35-123">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="28b35-123">WindowsFormsIntegration</span></span>

    - <span data-ttu-id="28b35-124">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="28b35-124">System.Windows.Forms</span></span>

3. <span data-ttu-id="28b35-125">Otevřete MainWindow. XAML v Návrháři WPF.</span><span class="sxs-lookup"><span data-stu-id="28b35-125">Open MainWindow.xaml in the WPF Designer.</span></span>

4. <span data-ttu-id="28b35-126">V elementu <xref:System.Windows.Window> přidejte následující mapování model Windows Forms obory názvů.</span><span class="sxs-lookup"><span data-stu-id="28b35-126">In the <xref:System.Windows.Window> element, add the following Windows Forms namespaces mapping.</span></span>

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. <span data-ttu-id="28b35-127">Pojmenujte výchozí <xref:System.Windows.Controls.Grid> element `mainGrid` přiřazením vlastnosti <xref:System.Windows.FrameworkElement.Name%2A>.</span><span class="sxs-lookup"><span data-stu-id="28b35-127">Name the default <xref:System.Windows.Controls.Grid> element `mainGrid` by assigning the <xref:System.Windows.FrameworkElement.Name%2A> property.</span></span>

     [!code-xaml[WPFWithWFAndDatabinding#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]

## <a name="defining-the-data-template"></a><span data-ttu-id="28b35-128">Definování šablony dat</span><span class="sxs-lookup"><span data-stu-id="28b35-128">Defining the Data Template</span></span>

<span data-ttu-id="28b35-129">Hlavní seznam zákazníků se zobrazí v ovládacím prvku <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="28b35-129">The master list of customers is displayed in a <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="28b35-130">Následující příklad kódu definuje objekt <xref:System.Windows.DataTemplate> s názvem `ListItemsTemplate`, který ovládá vizuální strom ovládacího prvku <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="28b35-130">The following code example defines a <xref:System.Windows.DataTemplate> object named `ListItemsTemplate` that controls the visual tree of the <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="28b35-131">Tato <xref:System.Windows.DataTemplate> je přiřazena k vlastnosti <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> ovládacího prvku <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="28b35-131">This <xref:System.Windows.DataTemplate> is assigned to the <xref:System.Windows.Controls.ListBox> control's <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> property.</span></span>

### <a name="to-define-the-data-template"></a><span data-ttu-id="28b35-132">Definování šablony dat</span><span class="sxs-lookup"><span data-stu-id="28b35-132">To define the data template</span></span>

- <span data-ttu-id="28b35-133">Zkopírujte následující kód XAML do deklarace <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="28b35-133">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>

     [!code-xaml[WPFWithWFAndDatabinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]

## <a name="specifying-the-form-layout"></a><span data-ttu-id="28b35-134">Určení rozložení formuláře</span><span class="sxs-lookup"><span data-stu-id="28b35-134">Specifying the Form Layout</span></span>

<span data-ttu-id="28b35-135">Rozložení formuláře je definováno mřížkou, která má tři řádky a tři sloupce.</span><span class="sxs-lookup"><span data-stu-id="28b35-135">The layout of the form is defined by a grid with three rows and three columns.</span></span> <span data-ttu-id="28b35-136">pro identifikaci každého sloupce v tabulce Customers jsou k dispozici <xref:System.Windows.Controls.Label> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="28b35-136"><xref:System.Windows.Controls.Label> controls are provided to identify each column in the Customers table.</span></span>

### <a name="to-set-up-the-grid-layout"></a><span data-ttu-id="28b35-137">Nastavení rozložení mřížky</span><span class="sxs-lookup"><span data-stu-id="28b35-137">To set up the Grid layout</span></span>

- <span data-ttu-id="28b35-138">Zkopírujte následující kód XAML do deklarace <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="28b35-138">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>

     [!code-xaml[WPFWithWFAndDatabinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]

### <a name="to-set-up-the-label-controls"></a><span data-ttu-id="28b35-139">Nastavení ovládacích prvků popisek</span><span class="sxs-lookup"><span data-stu-id="28b35-139">To set up the Label controls</span></span>

- <span data-ttu-id="28b35-140">Zkopírujte následující kód XAML do deklarace <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="28b35-140">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>

     [!code-xaml[WPFWithWFAndDatabinding#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]

## <a name="specifying-data-bindings"></a><span data-ttu-id="28b35-141">Určení datových vazeb</span><span class="sxs-lookup"><span data-stu-id="28b35-141">Specifying Data Bindings</span></span>

<span data-ttu-id="28b35-142">Hlavní seznam zákazníků se zobrazí v ovládacím prvku <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="28b35-142">The master list of customers is displayed in a <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="28b35-143">Připojené `ListItemsTemplate` váže ovládací prvek <xref:System.Windows.Controls.TextBlock> k poli `ContactName` z databáze.</span><span class="sxs-lookup"><span data-stu-id="28b35-143">The attached `ListItemsTemplate` binds a <xref:System.Windows.Controls.TextBlock> control to the `ContactName` field from the database.</span></span>

<span data-ttu-id="28b35-144">Podrobnosti o jednotlivých záznamech zákazníka se zobrazí v několika ovládacích prvcích <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="28b35-144">The details of each customer record are displayed in several <xref:System.Windows.Controls.TextBox> controls.</span></span>

### <a name="to-specify-data-bindings"></a><span data-ttu-id="28b35-145">Určení datových vazeb</span><span class="sxs-lookup"><span data-stu-id="28b35-145">To specify data bindings</span></span>

- <span data-ttu-id="28b35-146">Zkopírujte následující kód XAML do deklarace <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="28b35-146">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>

     <span data-ttu-id="28b35-147">Třída <xref:System.Windows.Data.Binding> váže ovládací prvky <xref:System.Windows.Controls.TextBox> k příslušným polím v databázi.</span><span class="sxs-lookup"><span data-stu-id="28b35-147">The <xref:System.Windows.Data.Binding> class binds the <xref:System.Windows.Controls.TextBox> controls to the appropriate fields in the database.</span></span>

     [!code-xaml[WPFWithWFAndDatabinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]

## <a name="displaying-data-by-using-interoperation"></a><span data-ttu-id="28b35-148">Zobrazení dat pomocí spolupráce</span><span class="sxs-lookup"><span data-stu-id="28b35-148">Displaying Data by Using Interoperation</span></span>

<span data-ttu-id="28b35-149">Objednávky odpovídající vybranému zákazníkovi se zobrazí v ovládacím prvku <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="28b35-149">The orders corresponding to the selected customer are displayed in a <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> control named `dataGridView1`.</span></span> <span data-ttu-id="28b35-150">`dataGridView1` ovládací prvek je svázán se zdrojem dat v souboru kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="28b35-150">The `dataGridView1` control is bound to the data source in the code-behind file.</span></span> <span data-ttu-id="28b35-151">Ovládací prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost> je nadřazeným prvkem tohoto model Windows Formsho ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="28b35-151">A <xref:System.Windows.Forms.Integration.WindowsFormsHost> control is the parent of this Windows Forms control.</span></span>

### <a name="to-display-data-in-the-datagridview-control"></a><span data-ttu-id="28b35-152">Zobrazení dat v ovládacím prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="28b35-152">To display data in the DataGridView control</span></span>

- <span data-ttu-id="28b35-153">Zkopírujte následující kód XAML do deklarace <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="28b35-153">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>

     [!code-xaml[WPFWithWFAndDatabinding#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]

## <a name="adding-the-data-source-to-the-project"></a><span data-ttu-id="28b35-154">Přidání zdroje dat do projektu</span><span class="sxs-lookup"><span data-stu-id="28b35-154">Adding the Data Source to the Project</span></span>

<span data-ttu-id="28b35-155">Se sadou Visual Studio můžete snadno přidat zdroj dat do projektu.</span><span class="sxs-lookup"><span data-stu-id="28b35-155">With Visual Studio, you can easily add a data source to your project.</span></span> <span data-ttu-id="28b35-156">Tento postup přidá do projektu datovou sadu silného typu.</span><span class="sxs-lookup"><span data-stu-id="28b35-156">This procedure adds a strongly typed data set to your project.</span></span> <span data-ttu-id="28b35-157">Přidávají se také některé další třídy podpory, například adaptéry pro tabulky pro každou z vybraných tabulek.</span><span class="sxs-lookup"><span data-stu-id="28b35-157">Several other support classes, such as table adapters for each of the chosen tables, are also added.</span></span>

### <a name="to-add-the-data-source"></a><span data-ttu-id="28b35-158">Přidání zdroje dat</span><span class="sxs-lookup"><span data-stu-id="28b35-158">To add the data source</span></span>

1. <span data-ttu-id="28b35-159">V nabídce **data** vyberte **Přidat nový zdroj dat**.</span><span class="sxs-lookup"><span data-stu-id="28b35-159">From the **Data** menu, select **Add New Data Source**.</span></span>

2. <span data-ttu-id="28b35-160">V **Průvodci konfigurací zdroje dat**vytvořte připojení k databázi Northwind pomocí datové sady.</span><span class="sxs-lookup"><span data-stu-id="28b35-160">In the **Data Source Configuration Wizard**, create a connection to the Northwind database by using a dataset.</span></span> <span data-ttu-id="28b35-161">Další informace najdete v tématu [Postup: připojení k datům v databázi](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="28b35-161">For more information, see [How to: Connect to Data in a Database](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120)).</span></span>

3. <span data-ttu-id="28b35-162">Po zobrazení výzvy **Průvodce konfigurací zdroje dat**uložte připojovací řetězec jako `NorthwindConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="28b35-162">When you are prompted by the **Data Source Configuration Wizard**, save the connection string as `NorthwindConnectionString`.</span></span>

4. <span data-ttu-id="28b35-163">Když se zobrazí výzva k výběru databázových objektů, vyberte tabulky `Customers` a `Orders` a pojmenujte vygenerovanou sadu dat `NorthwindDataSet`.</span><span class="sxs-lookup"><span data-stu-id="28b35-163">When you are prompted to choose your database objects, select the `Customers` and `Orders` tables, and name the generated data set `NorthwindDataSet`.</span></span>

## <a name="binding-to-the-data-source"></a><span data-ttu-id="28b35-164">Vazba na zdroj dat</span><span class="sxs-lookup"><span data-stu-id="28b35-164">Binding to the Data Source</span></span>

<span data-ttu-id="28b35-165">Komponenta <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> poskytuje jednotné rozhraní pro zdroj dat aplikace.</span><span class="sxs-lookup"><span data-stu-id="28b35-165">The <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> component provides a uniform interface for the application's data source.</span></span> <span data-ttu-id="28b35-166">Vazba na zdroj dat je implementována v souboru kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="28b35-166">Binding to the data source is implemented in the code-behind file.</span></span>

### <a name="to-bind-to-the-data-source"></a><span data-ttu-id="28b35-167">Vytvoření vazby na zdroj dat</span><span class="sxs-lookup"><span data-stu-id="28b35-167">To bind to the data source</span></span>

1. <span data-ttu-id="28b35-168">Otevřete soubor kódu na pozadí, který má název MainWindow. XAML. vb nebo MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="28b35-168">Open the code-behind file, which is named MainWindow.xaml.vb or MainWindow.xaml.cs.</span></span>

2. <span data-ttu-id="28b35-169">Zkopírujte následující kód do definice třídy `MainWindow`.</span><span class="sxs-lookup"><span data-stu-id="28b35-169">Copy the following code into the `MainWindow` class definition.</span></span>

     <span data-ttu-id="28b35-170">Tento kód deklaruje komponentu <xref:System.Windows.Forms.BindingSource> a přidružené pomocné třídy, které se připojují k databázi.</span><span class="sxs-lookup"><span data-stu-id="28b35-170">This code declares the <xref:System.Windows.Forms.BindingSource> component and associated helper classes that connect to the database.</span></span>

     [!code-csharp[WPFWithWFAndDatabinding#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]

3. <span data-ttu-id="28b35-171">Zkopírujte následující kód do konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="28b35-171">Copy the following code into the constructor.</span></span>

     <span data-ttu-id="28b35-172">Tento kód vytvoří a inicializuje komponentu <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="28b35-172">This code creates and initializes the <xref:System.Windows.Forms.BindingSource> component.</span></span>

     [!code-csharp[WPFWithWFAndDatabinding#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]

4. <span data-ttu-id="28b35-173">Otevřete MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="28b35-173">Open MainWindow.xaml.</span></span>

5. <span data-ttu-id="28b35-174">V zobrazení zobrazení Návrh nebo XAML vyberte prvek <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="28b35-174">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>

6. <span data-ttu-id="28b35-175">V okno Vlastnosti klikněte na kartu **události** .</span><span class="sxs-lookup"><span data-stu-id="28b35-175">In the Properties window, click the **Events** tab.</span></span>

7. <span data-ttu-id="28b35-176">Dvakrát klikněte na událost <xref:System.Windows.FrameworkElement.Loaded>.</span><span class="sxs-lookup"><span data-stu-id="28b35-176">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

8. <span data-ttu-id="28b35-177">Zkopírujte následující kód do obslužné rutiny události <xref:System.Windows.FrameworkElement.Loaded>.</span><span class="sxs-lookup"><span data-stu-id="28b35-177">Copy the following code into the <xref:System.Windows.FrameworkElement.Loaded> event handler.</span></span>

     <span data-ttu-id="28b35-178">Tento kód přiřadí komponentu <xref:System.Windows.Forms.BindingSource> jako kontext dat a naplní `Customers` a `Orders` objekty adaptéru.</span><span class="sxs-lookup"><span data-stu-id="28b35-178">This code assigns the <xref:System.Windows.Forms.BindingSource> component as the data context and populates the `Customers` and `Orders` adapter objects.</span></span>

     [!code-csharp[WPFWithWFAndDatabinding#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]

9. <span data-ttu-id="28b35-179">Zkopírujte následující kód do definice třídy `MainWindow`.</span><span class="sxs-lookup"><span data-stu-id="28b35-179">Copy the following code into the `MainWindow` class definition.</span></span>

     <span data-ttu-id="28b35-180">Tato metoda zpracovává událost <xref:System.Windows.Data.CollectionView.CurrentChanged> a aktualizuje aktuální položku datové vazby.</span><span class="sxs-lookup"><span data-stu-id="28b35-180">This method handles the <xref:System.Windows.Data.CollectionView.CurrentChanged> event and updates the current item of the data binding.</span></span>

     [!code-csharp[WPFWithWFAndDatabinding#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]

10. <span data-ttu-id="28b35-181">Stisknutím klávesy F5 aplikaci sestavíte a spustíte.</span><span class="sxs-lookup"><span data-stu-id="28b35-181">Press F5 to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="28b35-182">Viz také</span><span class="sxs-lookup"><span data-stu-id="28b35-182">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="28b35-183">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="28b35-183">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="28b35-184">Ukázka datových vazeb v hybridních aplikacích</span><span class="sxs-lookup"><span data-stu-id="28b35-184">Data Binding in Hybrid Applications Sample</span></span>](https://github.com/microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFWithWFAndDatabinding)
- [<span data-ttu-id="28b35-185">Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="28b35-185">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="28b35-186">Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="28b35-186">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
