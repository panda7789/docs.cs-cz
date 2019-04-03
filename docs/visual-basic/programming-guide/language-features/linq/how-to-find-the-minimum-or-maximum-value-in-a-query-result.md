---
title: 'Postupy: Hledání minimální nebo maximální hodnoty ve výsledku dotazu pomocí LINQ (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- max operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- minimum values [LINQ in Visual Basic]
- min operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], minimum and maximum values
- Max property
- maximum values [LINQ in Visual Basic]
- Aggregate clause [Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 238b763b-7dcd-4b14-8050-b65500a4f71c
ms.openlocfilehash: 311ba2d9c4be75e77cf134bf44dc96eab957736d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838167"
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a><span data-ttu-id="f8f46-102">Postupy: Hledání minimální nebo maximální hodnoty ve výsledku dotazu pomocí LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8f46-102">How to: Find the Minimum or Maximum Value in a Query Result by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="f8f46-103">Language Integrated Query (LINQ) usnadňuje přístup k informacím o databázi a spouštění dotazů.</span><span class="sxs-lookup"><span data-stu-id="f8f46-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="f8f46-104">Následující příklad ukazuje, jak vytvořit novou aplikaci, která provádí dotazy na databázi serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f8f46-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="f8f46-105">Ukázka Určuje minimální a maximální hodnoty výsledků pomocí `Aggregate` a `Group By` klauzule.</span><span class="sxs-lookup"><span data-stu-id="f8f46-105">The sample determines the minimum and maximum values for the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="f8f46-106">Další informace najdete v tématu [Aggregate – klauzule](../../../../visual-basic/language-reference/queries/aggregate-clause.md) a [klauzule Group](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="f8f46-106">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="f8f46-107">V příkladech v tomto tématu se používá ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="f8f46-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="f8f46-108">Pokud tuto databázi na vašem vývojovém počítači nemáte, můžete si ho stáhnout z webu Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="f8f46-108">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="f8f46-109">Pokyny najdete v tématu [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="f8f46-109">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="f8f46-110">Chcete-li vytvořit připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="f8f46-110">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="f8f46-111">V sadě Visual Studio, otevřete **Průzkumníka serveru**/**Průzkumník databáze** kliknutím **Průzkumníka serveru**/**databáze Průzkumník** na **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="f8f46-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="f8f46-112">Klikněte pravým tlačítkem na **datová připojení** v **Průzkumníka serveru**/**Průzkumník databáze** a potom klikněte na tlačítko **přidat připojení**.</span><span class="sxs-lookup"><span data-stu-id="f8f46-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="f8f46-113">Zadejte platné připojení k ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="f8f46-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="f8f46-114">Chcete-li přidat projekt, který obsahuje souboru LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="f8f46-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="f8f46-115">V sadě Visual Studio na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu**.</span><span class="sxs-lookup"><span data-stu-id="f8f46-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="f8f46-116">Výběr jazyka Visual Basic **formulářová aplikace Windows** jako typ projektu.</span><span class="sxs-lookup"><span data-stu-id="f8f46-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="f8f46-117">Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="f8f46-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="f8f46-118">Vyberte **třídy LINQ to SQL** šablony položky.</span><span class="sxs-lookup"><span data-stu-id="f8f46-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="f8f46-119">Pojmenujte soubor `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="f8f46-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="f8f46-120">Klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="f8f46-120">Click **Add**.</span></span> <span data-ttu-id="f8f46-121">Návrhář relací objektů (O/R Designer), je otevřené northwind.dbml souboru.</span><span class="sxs-lookup"><span data-stu-id="f8f46-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="f8f46-122">Přidání tabulek do dotazu do Návrháře relací objektů</span><span class="sxs-lookup"><span data-stu-id="f8f46-122">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="f8f46-123">V **Průzkumníka serveru**/**Průzkumník databáze**, rozbalte možnost připojení k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="f8f46-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="f8f46-124">Rozbalte **tabulky** složky.</span><span class="sxs-lookup"><span data-stu-id="f8f46-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="f8f46-125">Pokud jste zavřeli O/R Designer, můžete ho znovu otevřít poklikáním northwind.dbml soubor, který jste přidali dříve.</span><span class="sxs-lookup"><span data-stu-id="f8f46-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="f8f46-126">Klikněte na tabulce Zákazníci a přetáhněte ji do levého podokna v návrháři.</span><span class="sxs-lookup"><span data-stu-id="f8f46-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="f8f46-127">Klikněte na tabulky objednávky a přetáhněte ji do levého podokna v návrháři.</span><span class="sxs-lookup"><span data-stu-id="f8f46-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="f8f46-128">Návrhář vytvoří nové `Customer` a `Order` objekty pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="f8f46-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="f8f46-129">Všimněte si, že návrhář automaticky zjišťuje vztahy mezi tabulkami a vytvoří podřízené vlastnosti pro objekty v relaci.</span><span class="sxs-lookup"><span data-stu-id="f8f46-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="f8f46-130">Například technologie IntelliSense se zobrazí, který `Customer` objekt má `Orders` týkající se vlastností pro všechny objednávky daného zákazníka.</span><span class="sxs-lookup"><span data-stu-id="f8f46-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="f8f46-131">Uložte změny a zavřete návrháře.</span><span class="sxs-lookup"><span data-stu-id="f8f46-131">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="f8f46-132">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="f8f46-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="f8f46-133">Chcete-li přidat kód pro dotaz na databázi a zobrazení výsledků</span><span class="sxs-lookup"><span data-stu-id="f8f46-133">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="f8f46-134">Z **nástrojů**, přetáhněte <xref:System.Windows.Forms.DataGridView> ovládacího prvku na výchozí formulář Windows pro váš projekt Form1.</span><span class="sxs-lookup"><span data-stu-id="f8f46-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="f8f46-135">Dvakrát klikněte na Přidat kód pro Form1 `Load` události formuláře.</span><span class="sxs-lookup"><span data-stu-id="f8f46-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="f8f46-136">Při přidání tabulky do Návrháře relací objektů, přidá návrháře <xref:System.Data.Linq.DataContext> objektu pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="f8f46-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="f8f46-137">Tento objekt obsahuje kód, který musí mít pro přístup k těmto tabulky, vedle jednotlivých objektů a kolekcí pro každou tabulku.</span><span class="sxs-lookup"><span data-stu-id="f8f46-137">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="f8f46-138"><xref:System.Data.Linq.DataContext> Objektu pro váš projekt je s názvem podle názvu souboru .dbml.</span><span class="sxs-lookup"><span data-stu-id="f8f46-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="f8f46-139">Pro tento projekt <xref:System.Data.Linq.DataContext> se nazývá `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="f8f46-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="f8f46-140">Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> v kódu a dotazování tabulky určené Návrháře relací objektů.</span><span class="sxs-lookup"><span data-stu-id="f8f46-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="f8f46-141">Přidejte následující kód, který `Load` událostí.</span><span class="sxs-lookup"><span data-stu-id="f8f46-141">Add the following code to the `Load` event.</span></span> <span data-ttu-id="f8f46-142">Tento kód se dotazuje tabulky, které jsou vystaveny jako vlastnosti kontextu dat a určuje minimální a maximální hodnoty výsledků.</span><span class="sxs-lookup"><span data-stu-id="f8f46-142">This code queries the tables that are exposed as properties of your data context and determines the minimum and maximum values for the results.</span></span> <span data-ttu-id="f8f46-143">Ukázka používá mu `Aggregate` klauzule dotazu pro jeden výsledek a `Group By` seskupené klauzule zobrazíte průměr pro výsledky.</span><span class="sxs-lookup"><span data-stu-id="f8f46-143">The sample uses he `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form7.vb#14)]  
  
4.  <span data-ttu-id="f8f46-144">Stisknutím klávesy F5 spusťte váš projekt a prohlédněte si výsledky.</span><span class="sxs-lookup"><span data-stu-id="f8f46-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8f46-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8f46-145">See also</span></span>

- [<span data-ttu-id="f8f46-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="f8f46-146">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="f8f46-147">Dotazy</span><span class="sxs-lookup"><span data-stu-id="f8f46-147">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="f8f46-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="f8f46-148">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="f8f46-149">Metody DataContext (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="f8f46-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
