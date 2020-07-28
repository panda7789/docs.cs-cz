---
title: 'Návod: Zobrazení dat z databáze SQL Serveru v ovládacím prvku DataGrid'
description: Naučte se, jak získat data z databáze SQL Server a zobrazit ji v Windows Presentation Foundation ovládacím prvku DataGrid pomocí tohoto návodu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], displaying data from SQL Server
- controls [WPF], DataGrid
ms.assetid: 6810b048-0a23-4f86-bfa5-97f92b3cfab4
ms.openlocfilehash: cc41979c869021c9c363f3f68ce590d4702e068c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167553"
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a><span data-ttu-id="3a6db-103">Návod: zobrazení dat z databáze SQL Server v ovládacím prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="3a6db-103">Walkthrough: Display data from a SQL Server database in a DataGrid control</span></span>

<span data-ttu-id="3a6db-104">V tomto návodu načtete data z databáze SQL Server a zobrazíte je v <xref:System.Windows.Controls.DataGrid> ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="3a6db-104">In this walkthrough, you retrieve data from a SQL Server database and display that data in a <xref:System.Windows.Controls.DataGrid> control.</span></span> <span data-ttu-id="3a6db-105">Použijte Entity Framework ADO.NET k vytvoření tříd entit, které reprezentují data, a použijte LINQ k zápisu dotazu, který načte zadaná data z třídy entity.</span><span class="sxs-lookup"><span data-stu-id="3a6db-105">You use the ADO.NET Entity Framework to create the entity classes that represent the data, and use LINQ to write a query that retrieves the specified data from an entity class.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3a6db-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3a6db-106">Prerequisites</span></span>

<span data-ttu-id="3a6db-107">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="3a6db-107">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="3a6db-108">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3a6db-108">Visual Studio.</span></span>

- <span data-ttu-id="3a6db-109">Přístup ke spuštěné instanci SQL Server nebo SQL Server Express s připojenou ukázkovou databází AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="3a6db-109">Access to a running instance of SQL Server or SQL Server Express that has the AdventureWorks sample database attached to it.</span></span> <span data-ttu-id="3a6db-110">Databázi AdventureWorks si můžete stáhnout z [GitHubu](https://github.com/Microsoft/sql-server-samples/releases).</span><span class="sxs-lookup"><span data-stu-id="3a6db-110">You can download the AdventureWorks database from the [GitHub](https://github.com/Microsoft/sql-server-samples/releases).</span></span>

## <a name="create-entity-classes"></a><span data-ttu-id="3a6db-111">Vytváření tříd entit</span><span class="sxs-lookup"><span data-stu-id="3a6db-111">Create entity classes</span></span>

1. <span data-ttu-id="3a6db-112">Vytvořte nový projekt aplikace WPF v Visual Basic nebo C# a pojmenujte ho `DataGridSQLExample` .</span><span class="sxs-lookup"><span data-stu-id="3a6db-112">Create a new WPF Application project in Visual Basic or C#, and name it `DataGridSQLExample`.</span></span>

2. <span data-ttu-id="3a6db-113">V Průzkumník řešení klikněte pravým tlačítkem myši na projekt, přejděte na **Přidat**a pak vyberte **Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="3a6db-113">In Solution Explorer, right-click your project, point to **Add**, and then select **New Item**.</span></span>

     <span data-ttu-id="3a6db-114">Zobrazí se dialogové okno Přidat novou položku.</span><span class="sxs-lookup"><span data-stu-id="3a6db-114">The Add New Item dialog box appears.</span></span>

3. <span data-ttu-id="3a6db-115">V podokně nainstalované šablony vyberte **data** a v seznamu šablon vyberte **ADO.NET model EDM (Entity Data Model)**.</span><span class="sxs-lookup"><span data-stu-id="3a6db-115">In the Installed Templates pane, select **Data** and in the list of templates, select **ADO.NET Entity Data Model**.</span></span>

     ![Šablona položky model EDM (Entity Data Model) ADO.NET](../../wcf/feature-details/media/ado-net-entity-data-model-item-template.png)

4. <span data-ttu-id="3a6db-117">Zadejte název souboru `AdventureWorksModel.edmx` a pak klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="3a6db-117">Name the file `AdventureWorksModel.edmx` and then click **Add**.</span></span>

     <span data-ttu-id="3a6db-118">Zobrazí se Průvodce modelem Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="3a6db-118">The Entity Data Model Wizard appears.</span></span>

5. <span data-ttu-id="3a6db-119">Na obrazovce zvolit obsah modelu vyberte **z databáze EF Designer** a pak klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="3a6db-119">In the Choose Model Contents screen, select **EF Designer from database** and then click **Next**.</span></span>

6. <span data-ttu-id="3a6db-120">Na obrazovce vybrat datové připojení zadejte připojení k databázi AdventureWorksLT2008.</span><span class="sxs-lookup"><span data-stu-id="3a6db-120">In the Choose Your Data Connection screen, provide the connection to your AdventureWorksLT2008 database.</span></span> <span data-ttu-id="3a6db-121">Další informace najdete v [dialogovém okně Výběr datového připojení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399244(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="3a6db-121">For more information, see [Choose Your Data Connection Dialog Box](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399244(v=vs.100)).</span></span>

    <span data-ttu-id="3a6db-122">Ujistěte se, že je název `AdventureWorksLT2008Entities` a že je zaškrtnuté políčko **Uložit nastavení připojení entity v App.Config jako** , a pak klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="3a6db-122">Make sure that the name is `AdventureWorksLT2008Entities` and that the **Save entity connection settings in App.Config as** check box is selected, and then click **Next**.</span></span>

7. <span data-ttu-id="3a6db-123">Na obrazovce zvolte vaše databázové objekty rozbalte uzel tabulky a vyberte tabulky **produkt** a **ProductCategory** .</span><span class="sxs-lookup"><span data-stu-id="3a6db-123">In the Choose Your Database Objects screen, expand the Tables node, and select the **Product** and **ProductCategory** tables.</span></span>

     <span data-ttu-id="3a6db-124">Třídy entit můžete vygenerovat pro všechny tabulky. v tomto příkladu se ale načítají jenom data z těchto dvou tabulek.</span><span class="sxs-lookup"><span data-stu-id="3a6db-124">You can generate entity classes for all of the tables; however, in this example you only retrieve data from those two tables.</span></span>

     <span data-ttu-id="3a6db-125">![Výběr produktu a ProductCategory z tabulek](./media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span><span class="sxs-lookup"><span data-stu-id="3a6db-125">![Select Product and ProductCategory from tables](./media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span></span>

8. <span data-ttu-id="3a6db-126">Klikněte na **Finish** (Dokončit).</span><span class="sxs-lookup"><span data-stu-id="3a6db-126">Click **Finish**.</span></span>

     <span data-ttu-id="3a6db-127">Entity produkt a ProductCategory se zobrazí v Entity Designer.</span><span class="sxs-lookup"><span data-stu-id="3a6db-127">The Product and ProductCategory entities are displayed in the Entity Designer.</span></span>

     <span data-ttu-id="3a6db-128">![Modely entit produktů a ProductCategory](./media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span><span class="sxs-lookup"><span data-stu-id="3a6db-128">![Product and ProductCategory entity models](./media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span></span>

## <a name="retrieve-and-present-the-data"></a><span data-ttu-id="3a6db-129">Načtení a prezentace dat</span><span class="sxs-lookup"><span data-stu-id="3a6db-129">Retrieve and present the data</span></span>

1. <span data-ttu-id="3a6db-130">Otevřete soubor MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="3a6db-130">Open the MainWindow.xaml file.</span></span>

2. <span data-ttu-id="3a6db-131">Nastavte <xref:System.Windows.FrameworkElement.Width%2A> vlastnost na hodnotu <xref:System.Windows.Window> až 450.</span><span class="sxs-lookup"><span data-stu-id="3a6db-131">Set the <xref:System.Windows.FrameworkElement.Width%2A> property on the <xref:System.Windows.Window> to 450.</span></span>

3. <span data-ttu-id="3a6db-132">V editoru XAML přidejte následující <xref:System.Windows.Controls.DataGrid> značku mezi `<Grid>` `</Grid>` značky a pro přidání <xref:System.Windows.Controls.DataGrid> pojmenovaného `dataGrid1` .</span><span class="sxs-lookup"><span data-stu-id="3a6db-132">In the XAML editor, add the following <xref:System.Windows.Controls.DataGrid> tag between the `<Grid>` and `</Grid>` tags to add a <xref:System.Windows.Controls.DataGrid> named `dataGrid1`.</span></span>

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]

     <span data-ttu-id="3a6db-133">![Okno s ovládacím panelem DataGrid](./media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span><span class="sxs-lookup"><span data-stu-id="3a6db-133">![Window with DataGrid](./media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span></span>

4. <span data-ttu-id="3a6db-134">Vyberte <xref:System.Windows.Window> .</span><span class="sxs-lookup"><span data-stu-id="3a6db-134">Select the <xref:System.Windows.Window>.</span></span>

5. <span data-ttu-id="3a6db-135">Pomocí editoru okno Vlastnosti nebo XAML vytvořte obslužnou rutinu události pro <xref:System.Windows.Window> pojmenovaný `Window_Loaded` pro <xref:System.Windows.FrameworkElement.Loaded> událost.</span><span class="sxs-lookup"><span data-stu-id="3a6db-135">Using the Properties window or XAML editor, create an event handler for the <xref:System.Windows.Window> named `Window_Loaded` for the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span> <span data-ttu-id="3a6db-136">Další informace najdete v tématu [Postup: Vytvoření jednoduché obslužné rutiny události](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="3a6db-136">For more information, see [How to: Create a Simple Event Handler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span></span>

     <span data-ttu-id="3a6db-137">Následující příklad ukazuje XAML pro MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="3a6db-137">The following shows the XAML for MainWindow.xaml.</span></span>

    > [!NOTE]
    > <span data-ttu-id="3a6db-138">Pokud používáte Visual Basic, nahraďte v prvním řádku souboru MainWindow. XAML parametrem `x:Class="DataGridSQLExample.MainWindow"` `x:Class="MainWindow"` .</span><span class="sxs-lookup"><span data-stu-id="3a6db-138">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="DataGridSQLExample.MainWindow"` with `x:Class="MainWindow"`.</span></span>

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]

6. <span data-ttu-id="3a6db-139">Otevřete soubor kódu na pozadí (MainWindow. XAML. vb nebo MainWindow.xaml.cs) pro <xref:System.Windows.Window> .</span><span class="sxs-lookup"><span data-stu-id="3a6db-139">Open the code-behind file (MainWindow.xaml.vb or MainWindow.xaml.cs) for the <xref:System.Windows.Window>.</span></span>

7. <span data-ttu-id="3a6db-140">Přidejte následující kód pro načtení specifických hodnot z spojených tabulek a nastavte <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost na <xref:System.Windows.Controls.DataGrid> výsledky dotazu.</span><span class="sxs-lookup"><span data-stu-id="3a6db-140">Add the following code to retrieve only specific values from the joined tables and set the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.DataGrid> to the results of the query.</span></span>

     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]

8. <span data-ttu-id="3a6db-141">Spusťte příklad.</span><span class="sxs-lookup"><span data-stu-id="3a6db-141">Run the example.</span></span>

     <span data-ttu-id="3a6db-142">Měli byste vidět <xref:System.Windows.Controls.DataGrid> , že se zobrazí data.</span><span class="sxs-lookup"><span data-stu-id="3a6db-142">You should see a <xref:System.Windows.Controls.DataGrid> that displays data.</span></span>

     <span data-ttu-id="3a6db-143">![Datová mřížka s daty z SQL Database](./media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span><span class="sxs-lookup"><span data-stu-id="3a6db-143">![DataGrid with data from SQL database](./media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span></span>

## <a name="see-also"></a><span data-ttu-id="3a6db-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a6db-144">See also</span></span>

- <xref:System.Windows.Controls.DataGrid>
