---
title: "Postupy: Vrácení výsledku dotazu LINQ jako specifického typu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- queries [LINQ in Visual Basic], specific type returned
- projection [LINQ in Visual Basic]
- anonymous types [Visual Basic]
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3c46799dea71a727b47a79f9fc108d676b253513
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a><span data-ttu-id="9974b-102">Postupy: Vrácení výsledku dotazu LINQ jako specifického typu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9974b-102">How to: Return a LINQ Query Result as a Specific Type (Visual Basic)</span></span>
<span data-ttu-id="9974b-103">Language-Integrated Query (LINQ) usnadňuje přístup k informacím databáze a spouštět dotazy.</span><span class="sxs-lookup"><span data-stu-id="9974b-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span> <span data-ttu-id="9974b-104">Ve výchozím nastavení dotazů LINQ vrátí seznam objektů jako anonymní typ.</span><span class="sxs-lookup"><span data-stu-id="9974b-104">By default, LINQ queries return a list of objects as an anonymous type.</span></span> <span data-ttu-id="9974b-105">Můžete také určit, že dotaz vrátí seznam konkrétního typu pomocí `Select` klauzule.</span><span class="sxs-lookup"><span data-stu-id="9974b-105">You can also specify that a query return a list of a specific type by using the `Select` clause.</span></span>  
  
 <span data-ttu-id="9974b-106">Následující příklad ukazuje, jak vytvořit novou aplikaci, která provádí dotazy na databázi systému SQL Server a projekty výsledky jako specifického typu s názvem.</span><span class="sxs-lookup"><span data-stu-id="9974b-106">The following example shows how to create a new application that performs queries against a SQL Server database and projects the results as a specific named type.</span></span> <span data-ttu-id="9974b-107">Další informace najdete v tématu [anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) a [klauzule Select](../../../../visual-basic/language-reference/queries/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="9974b-107">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) and [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span></span>  
  
 <span data-ttu-id="9974b-108">V příkladech v tomto tématu použijte ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="9974b-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="9974b-109">Pokud ve svém vývojovém počítači nemáte ukázková databáze Northwind, si můžete stáhnout z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) webu.</span><span class="sxs-lookup"><span data-stu-id="9974b-109">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="9974b-110">Pokyny najdete v tématu [stažení ukázkové databáze](../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="9974b-110">For instructions, see [Downloading Sample Databases](../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="9974b-111">Chcete-li vytvořit připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="9974b-111">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="9974b-112">V sadě Visual Studio otevřete **Průzkumníka serveru**/**Průzkumník databáze** kliknutím **Průzkumníka serveru**/**databáze Průzkumník** na **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="9974b-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="9974b-113">Klikněte pravým tlačítkem na **připojení dat** v **Průzkumníka serveru**/**Průzkumník databáze** a pak klikněte na **přidat připojení**.</span><span class="sxs-lookup"><span data-stu-id="9974b-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="9974b-114">Zadejte platné připojení k ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="9974b-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="9974b-115">Chcete-li přidat projekt, který obsahuje LINQ to SQL souboru</span><span class="sxs-lookup"><span data-stu-id="9974b-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="9974b-116">V sadě Visual Studio na **soubor** nabídky, přejděte na příkaz **nový** a pak klikněte na **projektu**.</span><span class="sxs-lookup"><span data-stu-id="9974b-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="9974b-117">Vyberte jazyka Visual Basic **formulářové aplikace Windows** jako typ projektu.</span><span class="sxs-lookup"><span data-stu-id="9974b-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="9974b-118">Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="9974b-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="9974b-119">Vyberte **třídy LINQ to SQL** šablony položky.</span><span class="sxs-lookup"><span data-stu-id="9974b-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="9974b-120">Název souboru `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="9974b-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="9974b-121">Klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="9974b-121">Click **Add**.</span></span> <span data-ttu-id="9974b-122">Návrhář relací objektů (Návrhář relací objektů), je otevřené northwind.dbml souboru.</span><span class="sxs-lookup"><span data-stu-id="9974b-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="9974b-123">Chcete-li přidat tabulky k dotazování na Návrhář relací objektů</span><span class="sxs-lookup"><span data-stu-id="9974b-123">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="9974b-124">V **Průzkumníka serveru**/**Průzkumník databáze**, rozbalte možnost připojení k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="9974b-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="9974b-125">Rozbalte **tabulky** složky.</span><span class="sxs-lookup"><span data-stu-id="9974b-125">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="9974b-126">Pokud jste zavřeli Návrhář relací objektů, můžete ho znovu otevřít dvojitým kliknutím na soubor northwind.dbml, které jste přidali dříve.</span><span class="sxs-lookup"><span data-stu-id="9974b-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="9974b-127">Klikněte na tabulku zákazníků a přetáhněte ji do levého podokna návrháře.</span><span class="sxs-lookup"><span data-stu-id="9974b-127">Click the Customers table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="9974b-128">Vytvoří novou návrháře `Customer` objekt pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="9974b-128">The designer creates a new `Customer` object for your project.</span></span> <span data-ttu-id="9974b-129">Výsledek dotazu jako můžete promítnout `Customer` typu nebo jako typ, který vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="9974b-129">You can project a query result as the `Customer` type or as a type that you create.</span></span> <span data-ttu-id="9974b-130">Tato ukázka vytvoříte nový typ v pozdějším postupu a výsledek dotazu jako tento typ projektu.</span><span class="sxs-lookup"><span data-stu-id="9974b-130">This sample will create a new type in a later procedure and project a query result as that type.</span></span>  
  
3.  <span data-ttu-id="9974b-131">Uložte změny a zavřít návrháře.</span><span class="sxs-lookup"><span data-stu-id="9974b-131">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="9974b-132">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="9974b-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="9974b-133">Chcete-li přidat kód pro dotazování databáze a zobrazit výsledky</span><span class="sxs-lookup"><span data-stu-id="9974b-133">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="9974b-134">Z **sada nástrojů**, přetáhněte ji <xref:System.Windows.Forms.DataGridView> na výchozí formuláře Windows pro svůj projekt Form1 ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="9974b-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="9974b-135">Dvakrát klikněte na Form1 k úpravě Form1 třídy.</span><span class="sxs-lookup"><span data-stu-id="9974b-135">Double-click Form1 to modify the Form1 class.</span></span>  
  
3.  <span data-ttu-id="9974b-136">Po `End Class` příkaz Form1 třídy, přidejte následující kód k vytvoření `CustomerInfo` typ k ukládání výsledků dotazu pro tuto ukázku.</span><span class="sxs-lookup"><span data-stu-id="9974b-136">After the `End Class` statement of the Form1 class, add the following code to create a `CustomerInfo` type to hold the query results for this sample.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#16](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_1.vb)]  
  
4.  <span data-ttu-id="9974b-137">Při přidání tabulky do Návrhář relací objektů návrháře přidat <xref:System.Data.Linq.DataContext> objektu do projektu.</span><span class="sxs-lookup"><span data-stu-id="9974b-137">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="9974b-138">Tento objekt obsahuje kód, který musíte mít přístup k těchto tabulek a pro přístup k jednotlivých objektů a kolekcí pro každou tabulku.</span><span class="sxs-lookup"><span data-stu-id="9974b-138">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="9974b-139"><xref:System.Data.Linq.DataContext> Objekt pro je s názvem projektu na základě názvu souboru DBML.</span><span class="sxs-lookup"><span data-stu-id="9974b-139">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="9974b-140">Pro tento projekt <xref:System.Data.Linq.DataContext> názvem objektu `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="9974b-140">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="9974b-141">Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> v kódu a dotazování tabulky určeného Návrhář relací objektů.</span><span class="sxs-lookup"><span data-stu-id="9974b-141">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="9974b-142">V `Load` událostí Form1 třídy, přidejte následující kód k dotazování tabulky, které jsou zveřejněné jako vlastnosti vaše data kontextu.</span><span class="sxs-lookup"><span data-stu-id="9974b-142">In the `Load` event of the Form1 class, add the following code to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="9974b-143">`Select` Klauzuli dotazu se vytvoří nové `CustomerInfo` typ místo anonymní typ pro každou položku výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="9974b-143">The `Select` clause of the query will create a new `CustomerInfo` type instead of an anonymous type for each item of the query result.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#15](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_2.vb)]  
  
5.  <span data-ttu-id="9974b-144">Stisknutím klávesy F5 spusťte projekt a zobrazit výsledky.</span><span class="sxs-lookup"><span data-stu-id="9974b-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9974b-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="9974b-145">See Also</span></span>  
 [<span data-ttu-id="9974b-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="9974b-146">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="9974b-147">Dotazy</span><span class="sxs-lookup"><span data-stu-id="9974b-147">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="9974b-148">Technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="9974b-148">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="9974b-149">Metody DataContext (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="9974b-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
