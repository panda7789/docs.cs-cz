---
title: 'Postupy: Vrácení výsledku dotazu LINQ jako specifického typu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], specific type returned
- projection [LINQ in Visual Basic]
- anonymous types [Visual Basic]
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
ms.openlocfilehash: ba6479852f7a78fb26743a04fd08adea07c1ffff
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835866"
---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a><span data-ttu-id="815a7-102">Postupy: Vrácení výsledku dotazu LINQ jako specifického typu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="815a7-102">How to: Return a LINQ Query Result as a Specific Type (Visual Basic)</span></span>
<span data-ttu-id="815a7-103">Language Integrated Query (LINQ) usnadňuje přístup k informacím o databázi a spouštění dotazů.</span><span class="sxs-lookup"><span data-stu-id="815a7-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span> <span data-ttu-id="815a7-104">Ve výchozím nastavení dotazy LINQ vrací seznam objektů jako anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="815a7-104">By default, LINQ queries return a list of objects as an anonymous type.</span></span> <span data-ttu-id="815a7-105">Můžete také určit, že dotaz vrátí seznam určitého typu pomocí `Select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="815a7-105">You can also specify that a query return a list of a specific type by using the `Select` clause.</span></span>  
  
 <span data-ttu-id="815a7-106">Následující příklad ukazuje, jak vytvořit novou aplikaci, která provádí dotazy na databázi serveru SQL Server a projekty výsledky jako konkrétní pojmenovaného typu.</span><span class="sxs-lookup"><span data-stu-id="815a7-106">The following example shows how to create a new application that performs queries against a SQL Server database and projects the results as a specific named type.</span></span> <span data-ttu-id="815a7-107">Další informace najdete v tématu [anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) a [klauzule Select](../../../../visual-basic/language-reference/queries/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="815a7-107">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) and [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span></span>  
  
 <span data-ttu-id="815a7-108">V příkladech v tomto tématu se používá ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="815a7-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="815a7-109">Pokud tuto databázi na vašem vývojovém počítači nemáte, můžete si ho stáhnout z webu Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="815a7-109">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="815a7-110">Pokyny najdete v tématu [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="815a7-110">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="815a7-111">Chcete-li vytvořit připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="815a7-111">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="815a7-112">V sadě Visual Studio, otevřete **Průzkumníka serveru**/**Průzkumník databáze** kliknutím **Průzkumníka serveru**/**databáze Průzkumník** na **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="815a7-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="815a7-113">Klikněte pravým tlačítkem na **datová připojení** v **Průzkumníka serveru**/**Průzkumník databáze** a potom klikněte na tlačítko **přidat připojení**.</span><span class="sxs-lookup"><span data-stu-id="815a7-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="815a7-114">Zadejte platné připojení k ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="815a7-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="815a7-115">Chcete-li přidat projekt, který obsahuje souboru LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="815a7-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="815a7-116">V sadě Visual Studio na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu**.</span><span class="sxs-lookup"><span data-stu-id="815a7-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="815a7-117">Výběr jazyka Visual Basic **formulářová aplikace Windows** jako typ projektu.</span><span class="sxs-lookup"><span data-stu-id="815a7-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="815a7-118">Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="815a7-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="815a7-119">Vyberte **třídy LINQ to SQL** šablony položky.</span><span class="sxs-lookup"><span data-stu-id="815a7-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="815a7-120">Pojmenujte soubor `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="815a7-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="815a7-121">Klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="815a7-121">Click **Add**.</span></span> <span data-ttu-id="815a7-122">Návrhář relací objektů (O/R Designer), je otevřené northwind.dbml souboru.</span><span class="sxs-lookup"><span data-stu-id="815a7-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="815a7-123">Přidání tabulek do dotazu do Návrháře relací objektů</span><span class="sxs-lookup"><span data-stu-id="815a7-123">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="815a7-124">V **Průzkumníka serveru**/**Průzkumník databáze**, rozbalte možnost připojení k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="815a7-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="815a7-125">Rozbalte **tabulky** složky.</span><span class="sxs-lookup"><span data-stu-id="815a7-125">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="815a7-126">Pokud jste zavřeli O/R Designer, můžete ho znovu otevřít poklikáním northwind.dbml soubor, který jste přidali dříve.</span><span class="sxs-lookup"><span data-stu-id="815a7-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="815a7-127">Klikněte na tabulce Zákazníci a přetáhněte ji do levého podokna v návrháři.</span><span class="sxs-lookup"><span data-stu-id="815a7-127">Click the Customers table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="815a7-128">Vytvoří nový Návrhář `Customer` objektu pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="815a7-128">The designer creates a new `Customer` object for your project.</span></span> <span data-ttu-id="815a7-129">Jako výsledek dotazu můžete promítnout `Customer` typ nebo typ, který vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="815a7-129">You can project a query result as the `Customer` type or as a type that you create.</span></span> <span data-ttu-id="815a7-130">Tato ukázka vytvoří nový typ v pozdějším postupu a výsledek dotazu jako tento typ projektu.</span><span class="sxs-lookup"><span data-stu-id="815a7-130">This sample will create a new type in a later procedure and project a query result as that type.</span></span>  
  
3.  <span data-ttu-id="815a7-131">Uložte změny a zavřete návrháře.</span><span class="sxs-lookup"><span data-stu-id="815a7-131">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="815a7-132">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="815a7-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="815a7-133">Chcete-li přidat kód pro dotaz na databázi a zobrazení výsledků</span><span class="sxs-lookup"><span data-stu-id="815a7-133">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="815a7-134">Z **nástrojů**, přetáhněte <xref:System.Windows.Forms.DataGridView> ovládacího prvku na výchozí formulář Windows pro váš projekt Form1.</span><span class="sxs-lookup"><span data-stu-id="815a7-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="815a7-135">Klikněte dvakrát na Form1 upravte třídu Form1.</span><span class="sxs-lookup"><span data-stu-id="815a7-135">Double-click Form1 to modify the Form1 class.</span></span>  
  
3.  <span data-ttu-id="815a7-136">Po `End Class` příkazu Form1 třídy, přidejte následující kód k vytvoření `CustomerInfo` typu k ukládání výsledků dotazu pro tuto ukázku.</span><span class="sxs-lookup"><span data-stu-id="815a7-136">After the `End Class` statement of the Form1 class, add the following code to create a `CustomerInfo` type to hold the query results for this sample.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#16)]  
  
4.  <span data-ttu-id="815a7-137">Při přidání tabulky do Návrháře relací objektů, přidá návrháře <xref:System.Data.Linq.DataContext> objektu do projektu.</span><span class="sxs-lookup"><span data-stu-id="815a7-137">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="815a7-138">Tento objekt obsahuje kód, který musí mít pro přístup k těchto tabulek a pro přístup k jednotlivým objekty a kolekce pro každou tabulku.</span><span class="sxs-lookup"><span data-stu-id="815a7-138">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="815a7-139"><xref:System.Data.Linq.DataContext> Objektu pro váš projekt je s názvem podle názvu souboru .dbml.</span><span class="sxs-lookup"><span data-stu-id="815a7-139">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="815a7-140">Pro tento projekt <xref:System.Data.Linq.DataContext> se nazývá `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="815a7-140">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="815a7-141">Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> v kódu a dotazování tabulky určené Návrháře relací objektů.</span><span class="sxs-lookup"><span data-stu-id="815a7-141">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="815a7-142">V `Load` událost třídy Form1, přidejte následující kód k dotazování tabulky, které jsou vystaveny jako vlastnosti datového kontextu.</span><span class="sxs-lookup"><span data-stu-id="815a7-142">In the `Load` event of the Form1 class, add the following code to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="815a7-143">`Select` Klauzule dotazu se vytvoří nový `CustomerInfo` typ místo anonymního typu pro každou položku výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="815a7-143">The `Select` clause of the query will create a new `CustomerInfo` type instead of an anonymous type for each item of the query result.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#15)]  
  
5.  <span data-ttu-id="815a7-144">Stisknutím klávesy F5 spusťte váš projekt a prohlédněte si výsledky.</span><span class="sxs-lookup"><span data-stu-id="815a7-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="815a7-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="815a7-145">See also</span></span>

- [<span data-ttu-id="815a7-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="815a7-146">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="815a7-147">Dotazy</span><span class="sxs-lookup"><span data-stu-id="815a7-147">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="815a7-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="815a7-148">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="815a7-149">Metody DataContext (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="815a7-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
