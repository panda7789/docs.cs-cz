---
title: "Návod: Zobrazení dat z databáze serveru SQL Server v ovládacím prvku DataGrid"
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
- DataGrid [WPF], displaying data from SQL Server
- controls [WPF], DataGrid
ms.assetid: 6810b048-0a23-4f86-bfa5-97f92b3cfab4
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0397206a05ef47a7fc9b130fbd13fa19a0d766fa
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a><span data-ttu-id="7bb09-102">Návod: Zobrazení dat z databáze serveru SQL Server v ovládacím prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="7bb09-102">Walkthrough: Display Data from a SQL Server Database in a DataGrid Control</span></span>
<span data-ttu-id="7bb09-103">V tomto návodu načtení dat z databáze serveru SQL a zobrazit tato data v <xref:System.Windows.Controls.DataGrid> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7bb09-103">In this walkthrough, you retrieve data from a SQL Server database and display that data in a <xref:System.Windows.Controls.DataGrid> control.</span></span> <span data-ttu-id="7bb09-104">Použijete k vytvoření tříd entit, které představují data a pomocí LINQ vytvořit dotaz, který načte zadaná data z třídu entity ADO.NET Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="7bb09-104">You use the ADO.NET Entity Framework to create the entity classes that represent the data, and use LINQ to write a query that retrieves the specified data from an entity class.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7bb09-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7bb09-105">Prerequisites</span></span>  
 <span data-ttu-id="7bb09-106">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="7bb09-106">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="7bb09-107">.</span><span class="sxs-lookup"><span data-stu-id="7bb09-107">.</span></span>  
  
-   <span data-ttu-id="7bb09-108">Přístup k spuštěnou instanci systému SQL Server nebo SQL Server Express, která obsahuje ukázkovou databázi AdventureWorks k němu připojen.</span><span class="sxs-lookup"><span data-stu-id="7bb09-108">Access to a running instance of SQL Server or SQL Server Express that has the AdventureWorks sample database attached to it.</span></span> <span data-ttu-id="7bb09-109">Si můžete stáhnout databázi AdventureWorks z [Githubu](https://github.com/Microsoft/sql-server-samples/releases).</span><span class="sxs-lookup"><span data-stu-id="7bb09-109">You can download the AdventureWorks database from the [GitHub](https://github.com/Microsoft/sql-server-samples/releases).</span></span>  
  
### <a name="to-create-entity-classes"></a><span data-ttu-id="7bb09-110">Chcete-li vytvořit tříd entit</span><span class="sxs-lookup"><span data-stu-id="7bb09-110">To create entity classes</span></span>  
  
1.  <span data-ttu-id="7bb09-111">Vytvořte nový projekt aplikace WPF v jazyce Visual Basic nebo C# a pojmenujte ji `DataGridSQLExample`.</span><span class="sxs-lookup"><span data-stu-id="7bb09-111">Create a new WPF Application project in Visual Basic or C#, and name it `DataGridSQLExample`.</span></span>  
  
2.  <span data-ttu-id="7bb09-112">V Průzkumníku řešení klikněte pravým tlačítkem na projekt, přejděte na **přidat**a potom vyberte **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="7bb09-112">In Solution Explorer, right-click your project, point to **Add**, and then select **New Item**.</span></span>  
  
     <span data-ttu-id="7bb09-113">Zobrazí se dialogové okno Přidat novou položku.</span><span class="sxs-lookup"><span data-stu-id="7bb09-113">The Add New Item dialog box appears.</span></span>  
  
3.  <span data-ttu-id="7bb09-114">V podokně nainstalovaných šablonách vyberte **Data** a v seznamu šablon, vyberte **ADO.NET Entity Data režimu**l.</span><span class="sxs-lookup"><span data-stu-id="7bb09-114">In the Installed Templates pane, select **Data** and in the list of templates, select **ADO.NET Entity Data Mode**l.</span></span>  
  
     <span data-ttu-id="7bb09-115">![Vyberte model ADO.NET Entity Data Model](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step1.png "DataGrid_SQL_EF_Step1")</span><span class="sxs-lookup"><span data-stu-id="7bb09-115">![Select ADO.NET Entity Data Model](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step1.png "DataGrid_SQL_EF_Step1")</span></span>  
  
4.  <span data-ttu-id="7bb09-116">Název souboru `AdventureWorksModel.edmx` a pak klikněte na **přidat**.</span><span class="sxs-lookup"><span data-stu-id="7bb09-116">Name the file `AdventureWorksModel.edmx` and then click **Add**.</span></span>  
  
     <span data-ttu-id="7bb09-117">Zobrazí se Průvodce modelem Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="7bb09-117">The Entity Data Model Wizard appears.</span></span>  
  
5.  <span data-ttu-id="7bb09-118">V dialogovém okně Zvolte obsah modelu vyberte **generování z databáze** a pak klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="7bb09-118">In the Choose Model Contents screen, select **Generate from database** and then click **Next**.</span></span>  
  
     <span data-ttu-id="7bb09-119">![Vyberte možnost databáze generování](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step2.png "DataGrid_SQL_EF_Step2")</span><span class="sxs-lookup"><span data-stu-id="7bb09-119">![Select Generate from database option](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step2.png "DataGrid_SQL_EF_Step2")</span></span>  
  
6.  <span data-ttu-id="7bb09-120">V dialogovém okně Vybrat datové připojení slouží k navázání připojení k vaší databázi AdventureWorksLT2008.</span><span class="sxs-lookup"><span data-stu-id="7bb09-120">In the Choose Your Data Connection screen, provide the connection to your AdventureWorksLT2008 database.</span></span> <span data-ttu-id="7bb09-121">Další informace najdete v tématu [zvolte vaše Data dialogové okno připojení](http://go.microsoft.com/fwlink/?LinkId=160190).</span><span class="sxs-lookup"><span data-stu-id="7bb09-121">For more information, see [Choose Your Data Connection Dialog Box](http://go.microsoft.com/fwlink/?LinkId=160190).</span></span>  
  
     <span data-ttu-id="7bb09-122">![Zadejte připojení k databázi](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step3.png "DataGrid_SQL_EF_Step3")</span><span class="sxs-lookup"><span data-stu-id="7bb09-122">![Provide connection to database](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step3.png "DataGrid_SQL_EF_Step3")</span></span>  
  
7.  <span data-ttu-id="7bb09-123">Ujistěte se, zda je název `AdventureWorksLT2008Entities` a že **uložit nastavení připojení entity v souboru App.Config jako** zaškrtávací políčko je vybraná a pak klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="7bb09-123">Make sure that the name is `AdventureWorksLT2008Entities` and that the **Save entity connection settings in App.Config as** check box is selected, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="7bb09-124">V dialogovém okně zvolte si databázové objekty, rozbalte uzel tabulky a vyberte **produktu** a **ProductCategory** tabulky.</span><span class="sxs-lookup"><span data-stu-id="7bb09-124">In the Choose Your Database Objects screen, expand the Tables node, and select the **Product** and **ProductCategory** tables.</span></span>  
  
     <span data-ttu-id="7bb09-125">Můžete vygenerovat třídy entity pro všechny tabulky; ale v tomto příkladu pouze data načítat z těchto dvou tabulek.</span><span class="sxs-lookup"><span data-stu-id="7bb09-125">You can generate entity classes for all of the tables; however, in this example you only retrieve data from those two tables.</span></span>  
  
     <span data-ttu-id="7bb09-126">![Vyberte produktu a ProductCategory z tabulek](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span><span class="sxs-lookup"><span data-stu-id="7bb09-126">![Select Product and ProductCategory from tables](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span></span>  
  
9. <span data-ttu-id="7bb09-127">Klikněte na tlačítko **Dokončit**.</span><span class="sxs-lookup"><span data-stu-id="7bb09-127">Click **Finish**.</span></span>  
  
     <span data-ttu-id="7bb09-128">Entity produktu a ProductCategory jsou zobrazeny v Entity designeru.</span><span class="sxs-lookup"><span data-stu-id="7bb09-128">The Product and ProductCategory entities are displayed in the Entity Designer.</span></span>  
  
     <span data-ttu-id="7bb09-129">![Modely entity produktu a ProductCategory](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span><span class="sxs-lookup"><span data-stu-id="7bb09-129">![Product and ProductCategory entity models](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span></span>  
  
### <a name="to-retrieve-and-present-the-data"></a><span data-ttu-id="7bb09-130">Načtení a prezentovat data</span><span class="sxs-lookup"><span data-stu-id="7bb09-130">To retrieve and present the data</span></span>  
  
1.  <span data-ttu-id="7bb09-131">Otevřete soubor MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="7bb09-131">Open the MainWindow.xaml file.</span></span>  
  
2.  <span data-ttu-id="7bb09-132">Nastavte <xref:System.Windows.FrameworkElement.Width%2A> vlastnost <xref:System.Windows.Window> na 450.</span><span class="sxs-lookup"><span data-stu-id="7bb09-132">Set the <xref:System.Windows.FrameworkElement.Width%2A> property on the <xref:System.Windows.Window> to 450.</span></span>  
  
3.  <span data-ttu-id="7bb09-133">V editoru XAML, přidejte následující <xref:System.Windows.Controls.DataGrid> značky mezi `<Grid>` a `</Grid>` značky se mají přidat <xref:System.Windows.Controls.DataGrid> s názvem `dataGrid1`.</span><span class="sxs-lookup"><span data-stu-id="7bb09-133">In the XAML editor, add the following <xref:System.Windows.Controls.DataGrid> tag between the `<Grid>` and `</Grid>` tags to add a <xref:System.Windows.Controls.DataGrid> named `dataGrid1`.</span></span>  
  
     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]  
  
     <span data-ttu-id="7bb09-134">![Okno s DataGrid](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span><span class="sxs-lookup"><span data-stu-id="7bb09-134">![Window with DataGrid](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span></span>  
  
4.  <span data-ttu-id="7bb09-135">Vyberte <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="7bb09-135">Select the <xref:System.Windows.Window>.</span></span>  
  
5.  <span data-ttu-id="7bb09-136">Pomocí vlastnosti – okno nebo editoru XAML, vytvořte obslužnou rutinu události pro <xref:System.Windows.Window> s názvem `Window_Loaded` pro <xref:System.Windows.FrameworkElement.Loaded> událostí.</span><span class="sxs-lookup"><span data-stu-id="7bb09-136">Using the Properties window or XAML editor, create an event handler for the <xref:System.Windows.Window> named `Window_Loaded` for the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span> <span data-ttu-id="7bb09-137">Další informace najdete v tématu [postupy: vytvoření jednoduché obslužné rutiny události](http://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480).</span><span class="sxs-lookup"><span data-stu-id="7bb09-137">For more information, see [How to: Create a Simple Event Handler](http://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480).</span></span>  
  
     <span data-ttu-id="7bb09-138">Následující ukazuje XAML pro MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="7bb09-138">The following shows the XAML for MainWindow.xaml.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7bb09-139">Pokud používáte Visual Basic, v prvním řádku MainWindow.xaml, nahraďte `x:Class="DataGridSQLExample.MainWindow"` s `x:Class="MainWindow"`.</span><span class="sxs-lookup"><span data-stu-id="7bb09-139">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="DataGridSQLExample.MainWindow"` with `x:Class="MainWindow"`.</span></span>  
  
     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]  
  
6.  <span data-ttu-id="7bb09-140">Pro otevření souboru kódu na pozadí (MainWindow.xaml.vb nebo MainWindow.xaml.cs) <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="7bb09-140">Open the code-behind file (MainWindow.xaml.vb or MainWindow.xaml.cs) for the <xref:System.Windows.Window>.</span></span>  
  
7.  <span data-ttu-id="7bb09-141">Přidejte následující kód k načtení jenom konkrétní hodnoty z spojené tabulky a nastavení <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost <xref:System.Windows.Controls.DataGrid> do výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="7bb09-141">Add the following code to retrieve only specific values from the joined tables and set the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.DataGrid> to the results of the query.</span></span>  
  
     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]  
  
8.  <span data-ttu-id="7bb09-142">Spusťte v příkladu.</span><span class="sxs-lookup"><span data-stu-id="7bb09-142">Run the example.</span></span>  
  
     <span data-ttu-id="7bb09-143">Měli byste vidět <xref:System.Windows.Controls.DataGrid> , zobrazí data.</span><span class="sxs-lookup"><span data-stu-id="7bb09-143">You should see a <xref:System.Windows.Controls.DataGrid> that displays data.</span></span>  
  
     <span data-ttu-id="7bb09-144">![DataGrid – s daty z databáze SQL](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span><span class="sxs-lookup"><span data-stu-id="7bb09-144">![DataGrid with data from SQL database](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="7bb09-145">Další kroky</span><span class="sxs-lookup"><span data-stu-id="7bb09-145">Next Steps</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bb09-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="7bb09-146">See Also</span></span>  
 <xref:System.Windows.Controls.DataGrid>  
 [<span data-ttu-id="7bb09-147">Jak I: začít pracovat s platformou Entity Framework v aplikacích WPF?</span><span class="sxs-lookup"><span data-stu-id="7bb09-147">How Do I: Get Started with Entity Framework in WPF Applications?</span></span>](http://go.microsoft.com/fwlink/?LinkId=159868)
