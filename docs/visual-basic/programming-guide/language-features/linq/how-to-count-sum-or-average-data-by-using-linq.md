---
title: 'Postupy: Počet, suma nebo průměr dat pomocí LINQ (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- average operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- queries [LINQ in Visual Basic], sum results
- Aggregate clause [Visual Basic]
- sum operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], counting results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- count operator [LINQ in Visual Basic]
ms.assetid: 51ca1f59-7770-4884-8b76-113002e54fc0
ms.openlocfilehash: 942cb889c595f8caaf86dee1c025a935bd7db1b1
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43474320"
---
# <a name="how-to-count-sum-or-average-data-by-using-linq-visual-basic"></a><span data-ttu-id="ac891-102">Postupy: Počet, suma nebo průměr dat pomocí LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac891-102">How to: Count, Sum, or Average Data by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="ac891-103">Language Integrated Query (LINQ) usnadňuje přístup k informacím o databázi a spouštění dotazů.</span><span class="sxs-lookup"><span data-stu-id="ac891-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="ac891-104">Následující příklad ukazuje, jak vytvořit novou aplikaci, která provádí dotazy na databázi serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ac891-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="ac891-105">Ukázka počítá, sečte a předběhli aktuální fázi výsledky pomocí `Aggregate` a `Group By` klauzule.</span><span class="sxs-lookup"><span data-stu-id="ac891-105">The sample counts, sums, and averages the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="ac891-106">Další informace najdete v tématu [Aggregate – klauzule](../../../../visual-basic/language-reference/queries/aggregate-clause.md) a [klauzule Group](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="ac891-106">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="ac891-107">V příkladech v tomto tématu se používá ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="ac891-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="ac891-108">Pokud tuto databázi na vašem vývojovém počítači nemáte, můžete si ho stáhnout z webu Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="ac891-108">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="ac891-109">Pokyny najdete v tématu [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="ac891-109">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="ac891-110">Chcete-li vytvořit připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="ac891-110">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="ac891-111">V sadě Visual Studio, otevřete **Průzkumníka serveru**/**Průzkumník databáze** kliknutím **Průzkumníka serveru**/**databáze Průzkumník** na **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="ac891-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="ac891-112">Klikněte pravým tlačítkem na **datová připojení** v **Průzkumníka serveru**/**Průzkumník databáze** a potom klikněte na tlačítko **přidat připojení**.</span><span class="sxs-lookup"><span data-stu-id="ac891-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="ac891-113">Zadejte platné připojení k ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="ac891-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="ac891-114">Chcete-li přidat projekt, který obsahuje souboru LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="ac891-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="ac891-115">V sadě Visual Studio na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu**.</span><span class="sxs-lookup"><span data-stu-id="ac891-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="ac891-116">Výběr jazyka Visual Basic **formulářová aplikace Windows** jako typ projektu.</span><span class="sxs-lookup"><span data-stu-id="ac891-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="ac891-117">Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="ac891-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="ac891-118">Vyberte **třídy LINQ to SQL** šablony položky.</span><span class="sxs-lookup"><span data-stu-id="ac891-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="ac891-119">Název souboru `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="ac891-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="ac891-120">Klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="ac891-120">Click **Add**.</span></span> <span data-ttu-id="ac891-121">Návrhář relací objektů (O/R Designer), je otevřené northwind.dbml souboru.</span><span class="sxs-lookup"><span data-stu-id="ac891-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="ac891-122">Přidání tabulek do dotazu do Návrháře relací objektů</span><span class="sxs-lookup"><span data-stu-id="ac891-122">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="ac891-123">V **Průzkumníka serveru**/**Průzkumník databáze**, rozbalte možnost připojení k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="ac891-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="ac891-124">Rozbalte **tabulky** složky.</span><span class="sxs-lookup"><span data-stu-id="ac891-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="ac891-125">Pokud jste zavřeli O/R Designer, můžete ho znovu otevřít poklikáním northwind.dbml soubor, který jste přidali dříve.</span><span class="sxs-lookup"><span data-stu-id="ac891-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="ac891-126">Klikněte na tabulce Zákazníci a přetáhněte ji do levého podokna v návrháři.</span><span class="sxs-lookup"><span data-stu-id="ac891-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="ac891-127">Klikněte na tabulky objednávky a přetáhněte ji do levého podokna v návrháři.</span><span class="sxs-lookup"><span data-stu-id="ac891-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="ac891-128">Návrhář vytvoří nové `Customer` a `Order` objekty pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="ac891-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="ac891-129">Všimněte si, že návrhář automaticky zjišťuje vztahy mezi tabulkami a vytvoří podřízené vlastnosti pro objekty v relaci.</span><span class="sxs-lookup"><span data-stu-id="ac891-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="ac891-130">Například technologie IntelliSense se zobrazí, který `Customer` objekt má `Orders` týkající se vlastností pro všechny objednávky daného zákazníka.</span><span class="sxs-lookup"><span data-stu-id="ac891-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="ac891-131">Uložte změny a zavřete návrháře.</span><span class="sxs-lookup"><span data-stu-id="ac891-131">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="ac891-132">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="ac891-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="ac891-133">Chcete-li přidat kód pro dotaz na databázi a zobrazení výsledků</span><span class="sxs-lookup"><span data-stu-id="ac891-133">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="ac891-134">Z **nástrojů**, přetáhněte <xref:System.Windows.Forms.DataGridView> ovládacího prvku na výchozí formulář Windows pro váš projekt Form1.</span><span class="sxs-lookup"><span data-stu-id="ac891-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="ac891-135">Dvakrát klikněte na Přidat kód pro Form1 `Load` události formuláře.</span><span class="sxs-lookup"><span data-stu-id="ac891-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="ac891-136">Při přidání tabulky do Návrháře relací objektů, přidá návrháře <xref:System.Data.Linq.DataContext> objektu pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="ac891-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="ac891-137">Tento objekt obsahuje kód, který musí mít pro přístup k těchto tabulek a pro přístup k jednotlivým objekty a kolekce pro každou tabulku.</span><span class="sxs-lookup"><span data-stu-id="ac891-137">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="ac891-138"><xref:System.Data.Linq.DataContext> Objektu pro váš projekt je s názvem podle názvu souboru .dbml.</span><span class="sxs-lookup"><span data-stu-id="ac891-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="ac891-139">Pro tento projekt <xref:System.Data.Linq.DataContext> se nazývá `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="ac891-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="ac891-140">Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> v kódu a dotazování tabulky určené Návrháře relací objektů.</span><span class="sxs-lookup"><span data-stu-id="ac891-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="ac891-141">Přidejte následující kód, který `Load` událostí k dotazování tabulky, které jsou vystaveny jako vlastnosti vaší <xref:System.Data.Linq.DataContext> a počet součet a průměr výsledky.</span><span class="sxs-lookup"><span data-stu-id="ac891-141">Add the following code to the `Load` event to query the tables that are exposed as properties of your <xref:System.Data.Linq.DataContext> and count, sum, and average the results.</span></span> <span data-ttu-id="ac891-142">Ukázka používá `Aggregate` klauzule dotazu pro jeden výsledek a `Group By` seskupené klauzule zobrazíte průměr pro výsledky.</span><span class="sxs-lookup"><span data-stu-id="ac891-142">The sample uses the `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#13](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-count-sum-or-average-data-by-using-linq_1.vb)]  
  
4.  <span data-ttu-id="ac891-143">Stisknutím klávesy F5 spusťte váš projekt a prohlédněte si výsledky.</span><span class="sxs-lookup"><span data-stu-id="ac891-143">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac891-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="ac891-144">See Also</span></span>  
 [<span data-ttu-id="ac891-145">LINQ</span><span class="sxs-lookup"><span data-stu-id="ac891-145">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="ac891-146">Dotazy</span><span class="sxs-lookup"><span data-stu-id="ac891-146">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)  
 [<span data-ttu-id="ac891-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="ac891-147">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="ac891-148">Metody DataContext (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="ac891-148">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [<span data-ttu-id="ac891-149">Klauzule Aggregate</span><span class="sxs-lookup"><span data-stu-id="ac891-149">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="ac891-150">Klauzule Group By</span><span class="sxs-lookup"><span data-stu-id="ac891-150">Group By Clause</span></span>](../../../../visual-basic/language-reference/queries/group-by-clause.md)
