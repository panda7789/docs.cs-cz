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
ms.openlocfilehash: fc4d43ef9181f1a290d37c137b4fc6f7f16588b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62001023"
---
# <a name="how-to-filter-query-results-by-using-linq-visual-basic"></a><span data-ttu-id="f8eef-102">Postupy: Filtrování výsledků dotazu pomocí LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8eef-102">How to: Filter Query Results by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="f8eef-103">Language Integrated Query (LINQ) usnadňuje přístup k informacím o databázi a spouštění dotazů.</span><span class="sxs-lookup"><span data-stu-id="f8eef-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="f8eef-104">Následující příklad ukazuje, jak vytvořit novou aplikaci, která provádí dotazy na databázi serveru SQL Server a filtruje výsledky podle konkrétní hodnoty pomocí `Where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="f8eef-104">The following example shows how to create a new application that performs queries against a SQL Server database and filters the results by a particular value by using the `Where` clause.</span></span> <span data-ttu-id="f8eef-105">Další informace najdete v tématu [klauzule Where](../../../../visual-basic/language-reference/queries/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="f8eef-105">For more information, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>  
  
 <span data-ttu-id="f8eef-106">V příkladech v tomto tématu se používá ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="f8eef-106">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="f8eef-107">Pokud tuto databázi na vašem vývojovém počítači nemáte, můžete si ho stáhnout z webu Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="f8eef-107">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="f8eef-108">Pokyny najdete v tématu [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="f8eef-108">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="f8eef-109">Chcete-li vytvořit připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="f8eef-109">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="f8eef-110">V sadě Visual Studio, otevřete **Průzkumníka serveru**/**Průzkumník databáze** kliknutím **Průzkumníka serveru**/**databáze Průzkumník** na **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="f8eef-110">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="f8eef-111">Klikněte pravým tlačítkem na **datová připojení** v **Průzkumníka serveru**/**Průzkumník databáze** a potom klikněte na tlačítko **přidat připojení**.</span><span class="sxs-lookup"><span data-stu-id="f8eef-111">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="f8eef-112">Zadejte platné připojení k ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="f8eef-112">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="f8eef-113">Chcete-li přidat projekt, který obsahuje souboru LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="f8eef-113">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="f8eef-114">V sadě Visual Studio na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu**.</span><span class="sxs-lookup"><span data-stu-id="f8eef-114">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="f8eef-115">Výběr jazyka Visual Basic **formulářová aplikace Windows** jako typ projektu.</span><span class="sxs-lookup"><span data-stu-id="f8eef-115">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="f8eef-116">Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="f8eef-116">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="f8eef-117">Vyberte **třídy LINQ to SQL** šablony položky.</span><span class="sxs-lookup"><span data-stu-id="f8eef-117">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="f8eef-118">Pojmenujte soubor `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="f8eef-118">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="f8eef-119">Klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="f8eef-119">Click **Add**.</span></span> <span data-ttu-id="f8eef-120">Pro soubor northwind.dbml otevře se Návrhář relací objektů (O/R Designer).</span><span class="sxs-lookup"><span data-stu-id="f8eef-120">The Object Relational Designer (O/R Designer) opens for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="f8eef-121">Přidání tabulek do dotazu do Návrháře relací objektů</span><span class="sxs-lookup"><span data-stu-id="f8eef-121">To add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="f8eef-122">V **Průzkumníka serveru**/**Průzkumník databáze**, rozbalte možnost připojení k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="f8eef-122">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="f8eef-123">Rozbalte **tabulky** složky.</span><span class="sxs-lookup"><span data-stu-id="f8eef-123">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="f8eef-124">Pokud jste zavřeli O/R Designer, můžete ho znovu otevřít poklikáním northwind.dbml soubor, který jste přidali dříve.</span><span class="sxs-lookup"><span data-stu-id="f8eef-124">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="f8eef-125">Klikněte na tabulce Zákazníci a přetáhněte ji do levého podokna v návrháři.</span><span class="sxs-lookup"><span data-stu-id="f8eef-125">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="f8eef-126">Klikněte na tabulky objednávky a přetáhněte ji do levého podokna v návrháři.</span><span class="sxs-lookup"><span data-stu-id="f8eef-126">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="f8eef-127">Návrhář vytvoří nové `Customer` a `Order` objekty pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="f8eef-127">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="f8eef-128">Všimněte si, že návrhář automaticky zjišťuje vztahy mezi tabulkami a vytvoří podřízené vlastnosti pro objekty v relaci.</span><span class="sxs-lookup"><span data-stu-id="f8eef-128">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="f8eef-129">Například technologie IntelliSense se zobrazí, který `Customer` objekt má `Orders` týkající se vlastností pro všechny objednávky daného zákazníka.</span><span class="sxs-lookup"><span data-stu-id="f8eef-129">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3. <span data-ttu-id="f8eef-130">Uložte změny a zavřete návrháře.</span><span class="sxs-lookup"><span data-stu-id="f8eef-130">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="f8eef-131">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="f8eef-131">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="f8eef-132">Chcete-li přidat kód pro dotaz na databázi a zobrazení výsledků</span><span class="sxs-lookup"><span data-stu-id="f8eef-132">To add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="f8eef-133">Z **nástrojů**, přetáhněte <xref:System.Windows.Forms.DataGridView> ovládacího prvku na výchozí formulář Windows pro váš projekt Form1.</span><span class="sxs-lookup"><span data-stu-id="f8eef-133">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="f8eef-134">Dvakrát klikněte na Přidat kód pro Form1 `Load` události formuláře.</span><span class="sxs-lookup"><span data-stu-id="f8eef-134">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3. <span data-ttu-id="f8eef-135">Při přidání tabulky do Návrháře relací objektů, přidá návrháře <xref:System.Data.Linq.DataContext> objektu pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="f8eef-135">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="f8eef-136">Tento objekt obsahuje kód, který musí mít pro přístup k těmto tabulky, vedle jednotlivých objektů a kolekcí pro každou tabulku.</span><span class="sxs-lookup"><span data-stu-id="f8eef-136">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="f8eef-137"><xref:System.Data.Linq.DataContext> Objektu pro váš projekt je s názvem podle názvu souboru .dbml.</span><span class="sxs-lookup"><span data-stu-id="f8eef-137">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="f8eef-138">Pro tento projekt <xref:System.Data.Linq.DataContext> se nazývá `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="f8eef-138">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="f8eef-139">Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> v kódu a dotazování tabulky určené Návrháře relací objektů.</span><span class="sxs-lookup"><span data-stu-id="f8eef-139">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="f8eef-140">Přidejte následující kód, který `Load` událostí k dotazování tabulky, které jsou vystaveny jako vlastnosti datového kontextu.</span><span class="sxs-lookup"><span data-stu-id="f8eef-140">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="f8eef-141">Dotaz vyfiltruje výsledky a vrátí pouze zákazníci, kteří se nacházejí v `London`.</span><span class="sxs-lookup"><span data-stu-id="f8eef-141">The query filters the results and returns only customers that are located in `London`.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#11)]  
  
4. <span data-ttu-id="f8eef-142">Stisknutím klávesy F5 spusťte váš projekt a prohlédněte si výsledky.</span><span class="sxs-lookup"><span data-stu-id="f8eef-142">Press F5 to run your project and view the results.</span></span>  
  
5. <span data-ttu-id="f8eef-143">Toto jsou některé filtry, které můžete vyzkoušet.</span><span class="sxs-lookup"><span data-stu-id="f8eef-143">Following are some other filters that you can try.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="f8eef-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8eef-144">See also</span></span>

- [<span data-ttu-id="f8eef-145">LINQ</span><span class="sxs-lookup"><span data-stu-id="f8eef-145">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="f8eef-146">Dotazy</span><span class="sxs-lookup"><span data-stu-id="f8eef-146">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="f8eef-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="f8eef-147">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="f8eef-148">Metody DataContext (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="f8eef-148">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
