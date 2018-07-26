---
title: 'Postupy: Filtrování výsledků dotazu pomocí LINQ (Visual Basic)'
ms.date: 07/20/2015
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
ms.openlocfilehash: 8e051d583cdaeb04190e4499834a052fa41d1c48
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2018
ms.locfileid: "39243972"
---
# <a name="how-to-filter-query-results-by-using-linq-visual-basic"></a><span data-ttu-id="1e7dc-102">Postupy: Filtrování výsledků dotazu pomocí LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e7dc-102">How to: Filter Query Results by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="1e7dc-103">Language Integrated Query (LINQ) usnadňuje přístup k informacím o databázi a spouštění dotazů.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="1e7dc-104">Následující příklad ukazuje, jak vytvořit novou aplikaci, která provádí dotazy na databázi serveru SQL Server a filtruje výsledky podle konkrétní hodnoty pomocí `Where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-104">The following example shows how to create a new application that performs queries against a SQL Server database and filters the results by a particular value by using the `Where` clause.</span></span> <span data-ttu-id="1e7dc-105">Další informace najdete v tématu [klauzule Where](../../../../visual-basic/language-reference/queries/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="1e7dc-105">For more information, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>  
  
 <span data-ttu-id="1e7dc-106">V příkladech v tomto tématu se používá ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-106">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="1e7dc-107">Pokud tuto databázi na vašem vývojovém počítači nemáte, můžete si ho stáhnout z webu Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-107">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="1e7dc-108">Pokyny najdete v tématu [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="1e7dc-108">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="1e7dc-109">Chcete-li vytvořit připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="1e7dc-109">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="1e7dc-110">V sadě Visual Studio, otevřete **Průzkumníka serveru**/**Průzkumník databáze** kliknutím **Průzkumníka serveru**/**databáze Průzkumník** na **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-110">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="1e7dc-111">Klikněte pravým tlačítkem na **datová připojení** v **Průzkumníka serveru**/**Průzkumník databáze** a potom klikněte na tlačítko **přidat připojení**.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-111">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="1e7dc-112">Zadejte platné připojení k ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-112">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="1e7dc-113">Chcete-li přidat projekt, který obsahuje souboru LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="1e7dc-113">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="1e7dc-114">V sadě Visual Studio na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu**.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-114">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="1e7dc-115">Výběr jazyka Visual Basic **formulářová aplikace Windows** jako typ projektu.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-115">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="1e7dc-116">Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-116">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="1e7dc-117">Vyberte **třídy LINQ to SQL** šablony položky.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-117">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="1e7dc-118">Název souboru `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-118">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="1e7dc-119">Klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-119">Click **Add**.</span></span> <span data-ttu-id="1e7dc-120">Pro soubor northwind.dbml otevře se Návrhář relací objektů (O/R Designer).</span><span class="sxs-lookup"><span data-stu-id="1e7dc-120">The Object Relational Designer (O/R Designer) opens for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="1e7dc-121">Přidání tabulek do dotazu do Návrháře relací objektů</span><span class="sxs-lookup"><span data-stu-id="1e7dc-121">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="1e7dc-122">V **Průzkumníka serveru**/**Průzkumník databáze**, rozbalte možnost připojení k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-122">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="1e7dc-123">Rozbalte **tabulky** složky.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-123">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="1e7dc-124">Pokud jste zavřeli O/R Designer, můžete ho znovu otevřít poklikáním northwind.dbml soubor, který jste přidali dříve.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-124">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="1e7dc-125">Klikněte na tabulce Zákazníci a přetáhněte ji do levého podokna v návrháři.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-125">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="1e7dc-126">Klikněte na tabulky objednávky a přetáhněte ji do levého podokna v návrháři.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-126">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="1e7dc-127">Návrhář vytvoří nové `Customer` a `Order` objekty pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-127">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="1e7dc-128">Všimněte si, že návrhář automaticky zjišťuje vztahy mezi tabulkami a vytvoří podřízené vlastnosti pro objekty v relaci.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-128">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="1e7dc-129">Například technologie IntelliSense se zobrazí, který `Customer` objekt má `Orders` týkající se vlastností pro všechny objednávky daného zákazníka.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-129">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="1e7dc-130">Uložte změny a zavřete návrháře.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-130">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="1e7dc-131">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-131">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="1e7dc-132">Chcete-li přidat kód pro dotaz na databázi a zobrazení výsledků</span><span class="sxs-lookup"><span data-stu-id="1e7dc-132">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="1e7dc-133">Z **nástrojů**, přetáhněte <xref:System.Windows.Forms.DataGridView> ovládacího prvku na výchozí formulář Windows pro váš projekt Form1.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-133">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="1e7dc-134">Dvakrát klikněte na Přidat kód pro Form1 `Load` události formuláře.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-134">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="1e7dc-135">Při přidání tabulky do Návrháře relací objektů, přidá návrháře <xref:System.Data.Linq.DataContext> objektu pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-135">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="1e7dc-136">Tento objekt obsahuje kód, který musí mít pro přístup k těmto tabulky, vedle jednotlivých objektů a kolekcí pro každou tabulku.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-136">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="1e7dc-137"><xref:System.Data.Linq.DataContext> Objektu pro váš projekt je s názvem podle názvu souboru .dbml.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-137">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="1e7dc-138">Pro tento projekt <xref:System.Data.Linq.DataContext> se nazývá `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-138">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="1e7dc-139">Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> v kódu a dotazování tabulky určené Návrháře relací objektů.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-139">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="1e7dc-140">Přidejte následující kód, který `Load` událostí k dotazování tabulky, které jsou vystaveny jako vlastnosti datového kontextu.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-140">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="1e7dc-141">Dotaz vyfiltruje výsledky a vrátí pouze zákazníci, kteří se nacházejí v `London`.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-141">The query filters the results and returns only customers that are located in `London`.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#11](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-filter-query-results-by-using-linq_1.vb)]  
  
4.  <span data-ttu-id="1e7dc-142">Stisknutím klávesy F5 spusťte váš projekt a prohlédněte si výsledky.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-142">Press F5 to run your project and view the results.</span></span>  
  
5.  <span data-ttu-id="1e7dc-143">Toto jsou některé filtry, které můžete vyzkoušet.</span><span class="sxs-lookup"><span data-stu-id="1e7dc-143">Following are some other filters that you can try.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#12](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-filter-query-results-by-using-linq_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1e7dc-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="1e7dc-144">See Also</span></span>  
 [<span data-ttu-id="1e7dc-145">LINQ</span><span class="sxs-lookup"><span data-stu-id="1e7dc-145">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="1e7dc-146">Dotazy</span><span class="sxs-lookup"><span data-stu-id="1e7dc-146">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="1e7dc-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="1e7dc-147">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="1e7dc-148">Metody DataContext (O/R Designer)</span><span class="sxs-lookup"><span data-stu-id="1e7dc-148">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
