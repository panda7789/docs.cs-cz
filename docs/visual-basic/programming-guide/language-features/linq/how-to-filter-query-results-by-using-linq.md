---
title: "Postupy: Filtrování výsledků dotazu pomocí LINQ (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- filtering [Visual Basic]
- filtering data [LINQ in Visual Basic]
- filtering [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], filtering results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- filtering data [Visual Basic]
ms.assetid: ef103092-9bed-4134-97f4-2db696e83c12
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 09f2eb65858853fd759ae033f749151b348c124d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-filter-query-results-by-using-linq-visual-basic"></a><span data-ttu-id="093a7-102">Postupy: Filtrování výsledků dotazu pomocí LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="093a7-102">How to: Filter Query Results by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="093a7-103">Language-Integrated Query (LINQ) usnadňuje přístup k informacím databáze a spouštět dotazy.</span><span class="sxs-lookup"><span data-stu-id="093a7-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="093a7-104">Následující příklad ukazuje, jak vytvořit novou aplikaci, která provádí dotazy na databázi systému SQL Server a filtruje výsledky podle konkrétní hodnoty pomocí `Where` klauzule.</span><span class="sxs-lookup"><span data-stu-id="093a7-104">The following example shows how to create a new application that performs queries against a SQL Server database and filters the results by a particular value by using the `Where` clause.</span></span> <span data-ttu-id="093a7-105">Další informace najdete v tématu [klauzule Where](../../../../visual-basic/language-reference/queries/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="093a7-105">For more information, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>  
  
 <span data-ttu-id="093a7-106">V příkladech v tomto tématu použijte ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="093a7-106">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="093a7-107">Pokud ve svém vývojovém počítači nemáte ukázková databáze Northwind, si můžete stáhnout z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) webu.</span><span class="sxs-lookup"><span data-stu-id="093a7-107">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="093a7-108">Pokyny najdete v tématu [stažení ukázkové databáze](https://msdn.microsoft.com/library/bb399411).</span><span class="sxs-lookup"><span data-stu-id="093a7-108">For instructions, see [Downloading Sample Databases](https://msdn.microsoft.com/library/bb399411).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="093a7-109">Chcete-li vytvořit připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="093a7-109">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="093a7-110">V sadě Visual Studio otevřete **Průzkumníka serveru**/**Průzkumník databáze** kliknutím **Průzkumníka serveru**/**databáze Průzkumník** na **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="093a7-110">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="093a7-111">Klikněte pravým tlačítkem na **připojení dat** v **Průzkumníka serveru**/**Průzkumník databáze** a pak klikněte na **přidat připojení**.</span><span class="sxs-lookup"><span data-stu-id="093a7-111">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="093a7-112">Zadejte platné připojení k ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="093a7-112">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="093a7-113">Chcete-li přidat projekt, který obsahuje LINQ to SQL souboru</span><span class="sxs-lookup"><span data-stu-id="093a7-113">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="093a7-114">V sadě Visual Studio na **soubor** nabídky, přejděte na příkaz **nový** a pak klikněte na **projektu**.</span><span class="sxs-lookup"><span data-stu-id="093a7-114">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="093a7-115">Vyberte jazyka Visual Basic **formulářové aplikace Windows** jako typ projektu.</span><span class="sxs-lookup"><span data-stu-id="093a7-115">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="093a7-116">Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="093a7-116">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="093a7-117">Vyberte **třídy LINQ to SQL** šablony položky.</span><span class="sxs-lookup"><span data-stu-id="093a7-117">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="093a7-118">Název souboru `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="093a7-118">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="093a7-119">Klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="093a7-119">Click **Add**.</span></span> <span data-ttu-id="093a7-120">Otevře se soubor northwind.dbml Návrhář relací objektů (Návrhář relací objektů).</span><span class="sxs-lookup"><span data-stu-id="093a7-120">The Object Relational Designer (O/R Designer) opens for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="093a7-121">Chcete-li přidat tabulky k dotazování na Návrhář relací objektů</span><span class="sxs-lookup"><span data-stu-id="093a7-121">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="093a7-122">V **Průzkumníka serveru**/**Průzkumník databáze**, rozbalte možnost připojení k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="093a7-122">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="093a7-123">Rozbalte **tabulky** složky.</span><span class="sxs-lookup"><span data-stu-id="093a7-123">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="093a7-124">Pokud jste zavřeli Návrhář relací objektů, můžete ho znovu otevřít dvojitým kliknutím na soubor northwind.dbml, které jste přidali dříve.</span><span class="sxs-lookup"><span data-stu-id="093a7-124">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="093a7-125">Klikněte na tabulku zákazníků a přetáhněte ji do levého podokna návrháře.</span><span class="sxs-lookup"><span data-stu-id="093a7-125">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="093a7-126">Klikněte na tabulku objednávky a přetáhněte ji do levého podokna návrháře.</span><span class="sxs-lookup"><span data-stu-id="093a7-126">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="093a7-127">Návrhář vytvoří nové `Customer` a `Order` objekty pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="093a7-127">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="093a7-128">Všimněte si, že návrháře automaticky zjišťuje vztahy mezi tabulkami a vytvoří podřízené vlastnosti pro objekty v relaci.</span><span class="sxs-lookup"><span data-stu-id="093a7-128">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="093a7-129">Například, IntelliSense se ukazují, že `Customer` objekt má `Orders` vlastnost pro všechny objednávky týkající se tohoto zákazníka.</span><span class="sxs-lookup"><span data-stu-id="093a7-129">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="093a7-130">Uložte změny a zavřít návrháře.</span><span class="sxs-lookup"><span data-stu-id="093a7-130">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="093a7-131">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="093a7-131">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="093a7-132">Chcete-li přidat kód pro dotazování databáze a zobrazit výsledky</span><span class="sxs-lookup"><span data-stu-id="093a7-132">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="093a7-133">Z **sada nástrojů**, přetáhněte ji <xref:System.Windows.Forms.DataGridView> na výchozí formuláře Windows pro svůj projekt Form1 ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="093a7-133">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="093a7-134">Dvakrát klikněte na Form1 k přidejte kód, který `Load` události formuláře.</span><span class="sxs-lookup"><span data-stu-id="093a7-134">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="093a7-135">Při přidání tabulky do Návrhář relací objektů návrháře přidat <xref:System.Data.Linq.DataContext> objekt pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="093a7-135">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="093a7-136">Tento objekt obsahuje kód, který musí mít přístup k těchto tabulkách, kromě jednotlivých objektů a kolekcí pro každou tabulku.</span><span class="sxs-lookup"><span data-stu-id="093a7-136">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="093a7-137"><xref:System.Data.Linq.DataContext> Objekt pro je s názvem projektu na základě názvu souboru DBML.</span><span class="sxs-lookup"><span data-stu-id="093a7-137">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="093a7-138">Pro tento projekt <xref:System.Data.Linq.DataContext> názvem objektu `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="093a7-138">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="093a7-139">Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> v kódu a dotazování tabulky určeného Návrhář relací objektů.</span><span class="sxs-lookup"><span data-stu-id="093a7-139">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="093a7-140">Přidejte následující kód, který `Load` události při dotazování tabulky, které jsou zveřejněné jako vlastnosti vaše data kontextu.</span><span class="sxs-lookup"><span data-stu-id="093a7-140">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="093a7-141">Dotaz vyfiltruje výsledky a vrátí pouze uživatelé, kteří se nacházejí v `London`.</span><span class="sxs-lookup"><span data-stu-id="093a7-141">The query filters the results and returns only customers that are located in `London`.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#11](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-filter-query-results-by-using-linq_1.vb)]  
  
4.  <span data-ttu-id="093a7-142">Stisknutím klávesy F5 spusťte projekt a zobrazit výsledky.</span><span class="sxs-lookup"><span data-stu-id="093a7-142">Press F5 to run your project and view the results.</span></span>  
  
5.  <span data-ttu-id="093a7-143">Toto jsou některé filtry, které můžete vyzkoušet.</span><span class="sxs-lookup"><span data-stu-id="093a7-143">Following are some other filters that you can try.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#12](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-filter-query-results-by-using-linq_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="093a7-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="093a7-144">See Also</span></span>  
 [<span data-ttu-id="093a7-145">LINQ</span><span class="sxs-lookup"><span data-stu-id="093a7-145">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="093a7-146">Dotazy</span><span class="sxs-lookup"><span data-stu-id="093a7-146">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="093a7-147">Technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="093a7-147">LINQ to SQL</span></span>](https://msdn.microsoft.com/library/bb386976)  
 [<span data-ttu-id="093a7-148">Metody DataContext (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="093a7-148">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
