---
title: 'Návod: Zobrazení dat z databáze SQL Serveru v ovládacím prvku DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], displaying data from SQL Server
- controls [WPF], DataGrid
ms.assetid: 6810b048-0a23-4f86-bfa5-97f92b3cfab4
ms.openlocfilehash: 274ec2e8ef16190da53061bb197bc3b1a1fadcf8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024055"
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a><span data-ttu-id="50ea0-102">Návod: Zobrazení dat z databáze systému SQL Server v ovládacím prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="50ea0-102">Walkthrough: Display data from a SQL Server database in a DataGrid control</span></span>

<span data-ttu-id="50ea0-103">V tomto podrobném návodu, načtení dat z databáze SQL serveru a zobrazit tato data v <xref:System.Windows.Controls.DataGrid> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="50ea0-103">In this walkthrough, you retrieve data from a SQL Server database and display that data in a <xref:System.Windows.Controls.DataGrid> control.</span></span> <span data-ttu-id="50ea0-104">Použijete k vytvoření tříd entit, které představují data a zprostředkovatel LINQ slouží pro napsat dotaz, který načte zadaná data z entity třídy rozhraní ADO.NET Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="50ea0-104">You use the ADO.NET Entity Framework to create the entity classes that represent the data, and use LINQ to write a query that retrieves the specified data from an entity class.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="50ea0-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="50ea0-105">Prerequisites</span></span>

<span data-ttu-id="50ea0-106">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="50ea0-106">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="50ea0-107">Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="50ea0-107">Visual Studio.</span></span>

- <span data-ttu-id="50ea0-108">Přístup ke spuštěné instanci systému SQL Server nebo SQL Server Express, která obsahuje ukázkovou databázi AdventureWorks, který se k němu připojená.</span><span class="sxs-lookup"><span data-stu-id="50ea0-108">Access to a running instance of SQL Server or SQL Server Express that has the AdventureWorks sample database attached to it.</span></span> <span data-ttu-id="50ea0-109">Můžete stáhnout z databáze AdventureWorks [Githubu](https://github.com/Microsoft/sql-server-samples/releases).</span><span class="sxs-lookup"><span data-stu-id="50ea0-109">You can download the AdventureWorks database from the [GitHub](https://github.com/Microsoft/sql-server-samples/releases).</span></span>

## <a name="create-entity-classes"></a><span data-ttu-id="50ea0-110">Vytvoření tříd entit</span><span class="sxs-lookup"><span data-stu-id="50ea0-110">Create entity classes</span></span>

1. <span data-ttu-id="50ea0-111">Vytvoření nového projektu aplikace WPF v jazyce Visual Basic nebo C# a pojmenujte ho `DataGridSQLExample`.</span><span class="sxs-lookup"><span data-stu-id="50ea0-111">Create a new WPF Application project in Visual Basic or C#, and name it `DataGridSQLExample`.</span></span>

2. <span data-ttu-id="50ea0-112">V Průzkumníku řešení klikněte pravým tlačítkem na projekt, přejděte na **přidat**a pak vyberte **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="50ea0-112">In Solution Explorer, right-click your project, point to **Add**, and then select **New Item**.</span></span>

     <span data-ttu-id="50ea0-113">Zobrazí se dialogové okno Přidat novou položku.</span><span class="sxs-lookup"><span data-stu-id="50ea0-113">The Add New Item dialog box appears.</span></span>

3. <span data-ttu-id="50ea0-114">V podokně nainstalované šablony vyberte **Data** a v seznamu šablon vyberte **datový Model Entity ADO.NET**.</span><span class="sxs-lookup"><span data-stu-id="50ea0-114">In the Installed Templates pane, select **Data** and in the list of templates, select **ADO.NET Entity Data Model**.</span></span>

     ![Šablona položky modelu Entity Data Model ADO.NET](../../wcf/feature-details/./media/ado-net-entity-data-model-item-template.png)

4. <span data-ttu-id="50ea0-116">Název souboru `AdventureWorksModel.edmx` a potom klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="50ea0-116">Name the file `AdventureWorksModel.edmx` and then click **Add**.</span></span>

     <span data-ttu-id="50ea0-117">Zobrazí se Průvodce modelem Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="50ea0-117">The Entity Data Model Wizard appears.</span></span>

5. <span data-ttu-id="50ea0-118">Na obrazovce výběr obsahu modelu vyberte **EF designeru z databáze** a potom klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="50ea0-118">In the Choose Model Contents screen, select **EF Designer from database** and then click **Next**.</span></span>

6. <span data-ttu-id="50ea0-119">V dialogovém okně vyberte datové připojení slouží k navázání připojení k databázi AdventureWorksLT2008.</span><span class="sxs-lookup"><span data-stu-id="50ea0-119">In the Choose Your Data Connection screen, provide the connection to your AdventureWorksLT2008 database.</span></span> <span data-ttu-id="50ea0-120">Další informace najdete v tématu [zvolte si Data Connection Dialog Box](https://go.microsoft.com/fwlink/?LinkId=160190).</span><span class="sxs-lookup"><span data-stu-id="50ea0-120">For more information, see [Choose Your Data Connection Dialog Box](https://go.microsoft.com/fwlink/?LinkId=160190).</span></span>

    <span data-ttu-id="50ea0-121">Ujistěte se, zda je název `AdventureWorksLT2008Entities` a že **uložit nastavení připojení v souboru App.Config jako entity** zaškrtávací políčko zaškrtnuto a pak klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="50ea0-121">Make sure that the name is `AdventureWorksLT2008Entities` and that the **Save entity connection settings in App.Config as** check box is selected, and then click **Next**.</span></span>

7. <span data-ttu-id="50ea0-122">Na obrazovce Zvolte vaše databázové objekty, rozbalte uzel tabulky a vyberte **produktu** a **ProductCategory** tabulky.</span><span class="sxs-lookup"><span data-stu-id="50ea0-122">In the Choose Your Database Objects screen, expand the Tables node, and select the **Product** and **ProductCategory** tables.</span></span>

     <span data-ttu-id="50ea0-123">Můžete generovat třídy entity pro všechny tabulky; ale v tomto příkladu pouze načítáte data z těchto dvou tabulkách.</span><span class="sxs-lookup"><span data-stu-id="50ea0-123">You can generate entity classes for all of the tables; however, in this example you only retrieve data from those two tables.</span></span>

     <span data-ttu-id="50ea0-124">![Vyberte z tabulek Product a ProductCategory](./media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span><span class="sxs-lookup"><span data-stu-id="50ea0-124">![Select Product and ProductCategory from tables](./media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span></span>

8. <span data-ttu-id="50ea0-125">Klikněte na tlačítko **Dokončit**.</span><span class="sxs-lookup"><span data-stu-id="50ea0-125">Click **Finish**.</span></span>

     <span data-ttu-id="50ea0-126">Product a ProductCategory entity se zobrazí v návrháři entit.</span><span class="sxs-lookup"><span data-stu-id="50ea0-126">The Product and ProductCategory entities are displayed in the Entity Designer.</span></span>

     <span data-ttu-id="50ea0-127">![Modely entity Product a ProductCategory](./media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span><span class="sxs-lookup"><span data-stu-id="50ea0-127">![Product and ProductCategory entity models](./media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span></span>

## <a name="retrieve-and-present-the-data"></a><span data-ttu-id="50ea0-128">Načtení a zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="50ea0-128">Retrieve and present the data</span></span>

1. <span data-ttu-id="50ea0-129">Otevřete soubor MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="50ea0-129">Open the MainWindow.xaml file.</span></span>

2. <span data-ttu-id="50ea0-130">Nastavte <xref:System.Windows.FrameworkElement.Width%2A> vlastnost <xref:System.Windows.Window> na 450.</span><span class="sxs-lookup"><span data-stu-id="50ea0-130">Set the <xref:System.Windows.FrameworkElement.Width%2A> property on the <xref:System.Windows.Window> to 450.</span></span>

3. <span data-ttu-id="50ea0-131">V editoru XAML, přidejte následující <xref:System.Windows.Controls.DataGrid> označit mezi `<Grid>` a `</Grid>` značky se mají přidat <xref:System.Windows.Controls.DataGrid> s názvem `dataGrid1`.</span><span class="sxs-lookup"><span data-stu-id="50ea0-131">In the XAML editor, add the following <xref:System.Windows.Controls.DataGrid> tag between the `<Grid>` and `</Grid>` tags to add a <xref:System.Windows.Controls.DataGrid> named `dataGrid1`.</span></span>

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]

     <span data-ttu-id="50ea0-132">![Window with DataGrid](./media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span><span class="sxs-lookup"><span data-stu-id="50ea0-132">![Window with DataGrid](./media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span></span>

4. <span data-ttu-id="50ea0-133">Vyberte <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="50ea0-133">Select the <xref:System.Windows.Window>.</span></span>

5. <span data-ttu-id="50ea0-134">Pomocí okna vlastnosti nebo editoru XAML, vytvořit obslužnou rutinu události pro <xref:System.Windows.Window> s názvem `Window_Loaded` pro <xref:System.Windows.FrameworkElement.Loaded> událostí.</span><span class="sxs-lookup"><span data-stu-id="50ea0-134">Using the Properties window or XAML editor, create an event handler for the <xref:System.Windows.Window> named `Window_Loaded` for the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span> <span data-ttu-id="50ea0-135">Další informace najdete v tématu [jak: Vytvořte obslužnou rutinu události jednoduché](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="50ea0-135">For more information, see [How to: Create a Simple Event Handler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span></span>

     <span data-ttu-id="50ea0-136">Následuje ukázka XAML souboru mainwindow.XAML.</span><span class="sxs-lookup"><span data-stu-id="50ea0-136">The following shows the XAML for MainWindow.xaml.</span></span>

    > [!NOTE]
    > <span data-ttu-id="50ea0-137">Pokud používáte Visual Basic v prvním řádku souboru mainwindow.XAML, nahraďte `x:Class="DataGridSQLExample.MainWindow"` s `x:Class="MainWindow"`.</span><span class="sxs-lookup"><span data-stu-id="50ea0-137">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="DataGridSQLExample.MainWindow"` with `x:Class="MainWindow"`.</span></span>

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]

6. <span data-ttu-id="50ea0-138">Otevřete soubor kódu na pozadí (soubor MainWindow.xaml.vb nebo MainWindow.xaml.cs) pro <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="50ea0-138">Open the code-behind file (MainWindow.xaml.vb or MainWindow.xaml.cs) for the <xref:System.Windows.Window>.</span></span>

7. <span data-ttu-id="50ea0-139">Přidejte následující kód k načtení jenom konkrétní hodnoty z spojené tabulky a nastavit <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost <xref:System.Windows.Controls.DataGrid> do výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="50ea0-139">Add the following code to retrieve only specific values from the joined tables and set the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.DataGrid> to the results of the query.</span></span>

     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]

8. <span data-ttu-id="50ea0-140">Spustíte v příkladu.</span><span class="sxs-lookup"><span data-stu-id="50ea0-140">Run the example.</span></span>

     <span data-ttu-id="50ea0-141">Měli byste vidět <xref:System.Windows.Controls.DataGrid> , která zobrazí data.</span><span class="sxs-lookup"><span data-stu-id="50ea0-141">You should see a <xref:System.Windows.Controls.DataGrid> that displays data.</span></span>

     <span data-ttu-id="50ea0-142">![DataGrid – s daty z databáze SQL](./media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span><span class="sxs-lookup"><span data-stu-id="50ea0-142">![DataGrid with data from SQL database](./media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span></span>

## <a name="see-also"></a><span data-ttu-id="50ea0-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50ea0-143">See also</span></span>

- <xref:System.Windows.Controls.DataGrid>
- [<span data-ttu-id="50ea0-144">Postup: Začínáme s Entity Framework v aplikacích WPF?</span><span class="sxs-lookup"><span data-stu-id="50ea0-144">How Do I: Get Started with Entity Framework in WPF Applications?</span></span>](https://go.microsoft.com/fwlink/?LinkId=159868)