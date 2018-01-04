---
title: "Postupy: Hledání minimální nebo maximální hodnoty ve výsledku dotazu pomocí LINQ (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6a9555a86914f2352bc1a07bd92a839181355c9d
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a><span data-ttu-id="a2283-102">Postupy: Hledání minimální nebo maximální hodnoty ve výsledku dotazu pomocí LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2283-102">How to: Find the Minimum or Maximum Value in a Query Result by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="a2283-103">Language-Integrated Query (LINQ) usnadňuje přístup k informacím databáze a spouštět dotazy.</span><span class="sxs-lookup"><span data-stu-id="a2283-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="a2283-104">Následující příklad ukazuje, jak vytvořit novou aplikaci, která provádí dotazy na databázi systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a2283-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="a2283-105">Ukázka Určuje minimální a maximální hodnoty výsledků pomocí `Aggregate` a `Group By` klauzule.</span><span class="sxs-lookup"><span data-stu-id="a2283-105">The sample determines the minimum and maximum values for the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="a2283-106">Další informace najdete v tématu [Aggregate – klauzule](../../../../visual-basic/language-reference/queries/aggregate-clause.md) a [skupiny pomocí klauzule](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="a2283-106">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="a2283-107">V příkladech v tomto tématu použijte ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="a2283-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="a2283-108">Pokud ve svém vývojovém počítači nemáte ukázková databáze Northwind, si můžete stáhnout z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) webu.</span><span class="sxs-lookup"><span data-stu-id="a2283-108">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="a2283-109">Pokyny najdete v tématu [stažení ukázkové databáze](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="a2283-109">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="a2283-110">Chcete-li vytvořit připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="a2283-110">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="a2283-111">V sadě Visual Studio otevřete **Průzkumníka serveru**/**Průzkumník databáze** kliknutím **Průzkumníka serveru**/**databáze Průzkumník** na **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="a2283-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="a2283-112">Klikněte pravým tlačítkem na **připojení dat** v **Průzkumníka serveru**/**Průzkumník databáze** a pak klikněte na **přidat připojení**.</span><span class="sxs-lookup"><span data-stu-id="a2283-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="a2283-113">Zadejte platné připojení k ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="a2283-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="a2283-114">Chcete-li přidat projekt, který obsahuje LINQ to SQL souboru</span><span class="sxs-lookup"><span data-stu-id="a2283-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="a2283-115">V sadě Visual Studio na **soubor** nabídky, přejděte na příkaz **nový** a pak klikněte na **projektu**.</span><span class="sxs-lookup"><span data-stu-id="a2283-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="a2283-116">Vyberte jazyka Visual Basic **formulářové aplikace Windows** jako typ projektu.</span><span class="sxs-lookup"><span data-stu-id="a2283-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="a2283-117">Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="a2283-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="a2283-118">Vyberte **třídy LINQ to SQL** šablony položky.</span><span class="sxs-lookup"><span data-stu-id="a2283-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="a2283-119">Název souboru `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="a2283-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="a2283-120">Klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="a2283-120">Click **Add**.</span></span> <span data-ttu-id="a2283-121">Návrhář relací objektů (Návrhář relací objektů), je otevřené northwind.dbml souboru.</span><span class="sxs-lookup"><span data-stu-id="a2283-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="a2283-122">Chcete-li přidat tabulky k dotazování na Návrhář relací objektů</span><span class="sxs-lookup"><span data-stu-id="a2283-122">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="a2283-123">V **Průzkumníka serveru**/**Průzkumník databáze**, rozbalte možnost připojení k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="a2283-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="a2283-124">Rozbalte **tabulky** složky.</span><span class="sxs-lookup"><span data-stu-id="a2283-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="a2283-125">Pokud jste zavřeli Návrhář relací objektů, můžete ho znovu otevřít dvojitým kliknutím na soubor northwind.dbml, které jste přidali dříve.</span><span class="sxs-lookup"><span data-stu-id="a2283-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="a2283-126">Klikněte na tabulku zákazníků a přetáhněte ji do levého podokna návrháře.</span><span class="sxs-lookup"><span data-stu-id="a2283-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="a2283-127">Klikněte na tabulku objednávky a přetáhněte ji do levého podokna návrháře.</span><span class="sxs-lookup"><span data-stu-id="a2283-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="a2283-128">Návrhář vytvoří nové `Customer` a `Order` objekty pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="a2283-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="a2283-129">Všimněte si, že návrháře automaticky zjišťuje vztahy mezi tabulkami a vytvoří podřízené vlastnosti pro objekty v relaci.</span><span class="sxs-lookup"><span data-stu-id="a2283-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="a2283-130">Například, IntelliSense se ukazují, že `Customer` objekt má `Orders` vlastnost pro všechny objednávky týkající se tohoto zákazníka.</span><span class="sxs-lookup"><span data-stu-id="a2283-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="a2283-131">Uložte změny a zavřít návrháře.</span><span class="sxs-lookup"><span data-stu-id="a2283-131">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="a2283-132">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="a2283-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="a2283-133">Chcete-li přidat kód pro dotazování databáze a zobrazit výsledky</span><span class="sxs-lookup"><span data-stu-id="a2283-133">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="a2283-134">Z **sada nástrojů**, přetáhněte ji <xref:System.Windows.Forms.DataGridView> na výchozí formuláře Windows pro svůj projekt Form1 ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="a2283-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="a2283-135">Dvakrát klikněte na Form1 k přidejte kód, který `Load` události formuláře.</span><span class="sxs-lookup"><span data-stu-id="a2283-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="a2283-136">Při přidání tabulky do Návrhář relací objektů návrháře přidat <xref:System.Data.Linq.DataContext> objekt pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="a2283-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="a2283-137">Tento objekt obsahuje kód, který musí mít přístup k těchto tabulkách, kromě jednotlivých objektů a kolekcí pro každou tabulku.</span><span class="sxs-lookup"><span data-stu-id="a2283-137">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="a2283-138"><xref:System.Data.Linq.DataContext> Objekt pro je s názvem projektu na základě názvu souboru DBML.</span><span class="sxs-lookup"><span data-stu-id="a2283-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="a2283-139">Pro tento projekt <xref:System.Data.Linq.DataContext> názvem objektu `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="a2283-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="a2283-140">Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> v kódu a dotazování tabulky určeného Návrhář relací objektů.</span><span class="sxs-lookup"><span data-stu-id="a2283-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="a2283-141">Přidejte následující kód, který `Load` událostí.</span><span class="sxs-lookup"><span data-stu-id="a2283-141">Add the following code to the `Load` event.</span></span> <span data-ttu-id="a2283-142">Tento kód se dotazuje tabulky, které jsou zveřejněné jako vlastnosti vaše data kontextu a určuje minimální a maximální hodnoty výsledků.</span><span class="sxs-lookup"><span data-stu-id="a2283-142">This code queries the tables that are exposed as properties of your data context and determines the minimum and maximum values for the results.</span></span> <span data-ttu-id="a2283-143">Příklad používá mu `Aggregate` klauzule dotazu pro jeden výsledek a `Group By` klauzule zobrazíte v průměru pro seskupené výsledky.</span><span class="sxs-lookup"><span data-stu-id="a2283-143">The sample uses he `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#14](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-find-the-minimum-or-maximum-value-in-a-query-result_1.vb)]  
  
4.  <span data-ttu-id="a2283-144">Stisknutím klávesy F5 spusťte projekt a zobrazit výsledky.</span><span class="sxs-lookup"><span data-stu-id="a2283-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2283-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="a2283-145">See Also</span></span>  
 [<span data-ttu-id="a2283-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="a2283-146">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="a2283-147">Dotazy</span><span class="sxs-lookup"><span data-stu-id="a2283-147">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="a2283-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="a2283-148">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="a2283-149">Metody DataContext (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="a2283-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
