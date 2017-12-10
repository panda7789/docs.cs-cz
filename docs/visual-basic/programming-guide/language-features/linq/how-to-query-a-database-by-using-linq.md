---
title: "Postupy: Dotaz databáze pomocí LINQ (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- query samples [LINQ]
- database querying [LINQ]
- queries [LINQ in Visual Basic], database querying
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: bcf5e9c3-a236-4399-9a7f-3991eca7cf56
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e59c440e5553366d27fed6e5c53c5c463172906b
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="how-to-query-a-database-by-using-linq-visual-basic"></a><span data-ttu-id="f5a2e-102">Postupy: Dotaz databáze pomocí LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5a2e-102">How to: Query a Database by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="f5a2e-103">Language-Integrated Query (LINQ) usnadňuje přístup k informacím databáze a spouštět dotazy.</span><span class="sxs-lookup"><span data-stu-id="f5a2e-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="f5a2e-104">Následující příklad ukazuje, jak vytvořit novou aplikaci, která provádí dotazy na databázi systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f5a2e-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span>  
  
 <span data-ttu-id="f5a2e-105">V příkladech v tomto tématu použijte ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="f5a2e-105">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="f5a2e-106">Pokud ve svém vývojovém počítači nemáte ukázková databáze Northwind, si můžete stáhnout z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) webu.</span><span class="sxs-lookup"><span data-stu-id="f5a2e-106">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="f5a2e-107">Pokyny najdete v tématu [stažení ukázkové databáze](../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="f5a2e-107">For instructions, see [Downloading Sample Databases](../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="f5a2e-108">Chcete-li vytvořit připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="f5a2e-108">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="f5a2e-109">V sadě Visual Studio otevřete **Průzkumníka serveru**/**Průzkumník databáze** kliknutím **Průzkumníka serveru**/**databáze Průzkumník** na **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="f5a2e-109">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="f5a2e-110">Klikněte pravým tlačítkem na **připojení dat** v **Průzkumníka serveru**/**Průzkumník databáze** a pak klikněte na **přidat připojení**.</span><span class="sxs-lookup"><span data-stu-id="f5a2e-110">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="f5a2e-111">Zadejte platné připojení k ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="f5a2e-111">Specify a valid connection to the Northwind sample database.</span></span>  
  
## <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="f5a2e-112">Chcete-li přidat projekt, který obsahuje LINQ to SQL souboru</span><span class="sxs-lookup"><span data-stu-id="f5a2e-112">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="f5a2e-113">V sadě Visual Studio na **soubor** nabídky, přejděte na příkaz **nový** a pak klikněte na **projektu**.</span><span class="sxs-lookup"><span data-stu-id="f5a2e-113">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="f5a2e-114">Vyberte jazyka Visual Basic **formulářové aplikace Windows** jako typ projektu.</span><span class="sxs-lookup"><span data-stu-id="f5a2e-114">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="f5a2e-115">Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="f5a2e-115">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="f5a2e-116">Vyberte **třídy LINQ to SQL** šablony položky.</span><span class="sxs-lookup"><span data-stu-id="f5a2e-116">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="f5a2e-117">Název souboru `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="f5a2e-117">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="f5a2e-118">Klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="f5a2e-118">Click **Add**.</span></span> <span data-ttu-id="f5a2e-119">Návrhář relací objektů (Návrhář relací objektů), je otevřené northwind.dbml souboru.</span><span class="sxs-lookup"><span data-stu-id="f5a2e-119">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
## <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="f5a2e-120">Chcete-li přidat tabulky k dotazování na Návrhář relací objektů</span><span class="sxs-lookup"><span data-stu-id="f5a2e-120">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="f5a2e-121">V **Průzkumníka serveru**/**Průzkumník databáze**, rozbalte možnost připojení k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="f5a2e-121">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="f5a2e-122">Rozbalte **tabulky** složky.</span><span class="sxs-lookup"><span data-stu-id="f5a2e-122">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="f5a2e-123">Pokud jste zavřeli Návrhář relací objektů, můžete ho znovu otevřít dvojitým kliknutím na soubor northwind.dbml, které jste přidali dříve.</span><span class="sxs-lookup"><span data-stu-id="f5a2e-123">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="f5a2e-124">Klikněte na tabulku zákazníků a přetáhněte ji do levého podokna návrháře.</span><span class="sxs-lookup"><span data-stu-id="f5a2e-124">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="f5a2e-125">Klikněte na tabulku objednávky a přetáhněte ji do levého podokna návrháře.</span><span class="sxs-lookup"><span data-stu-id="f5a2e-125">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="f5a2e-126">Návrhář vytvoří nové `Customer` a `Order` objekty pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="f5a2e-126">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="f5a2e-127">Všimněte si, že návrháře automaticky zjišťuje vztahy mezi tabulkami a vytvoří podřízené vlastnosti pro objekty v relaci.</span><span class="sxs-lookup"><span data-stu-id="f5a2e-127">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="f5a2e-128">Například, IntelliSense se ukazují, že `Customer` objekt má `Orders` vlastnost pro všechny objednávky týkající se tohoto zákazníka.</span><span class="sxs-lookup"><span data-stu-id="f5a2e-128">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="f5a2e-129">Uložte změny a zavřít návrháře.</span><span class="sxs-lookup"><span data-stu-id="f5a2e-129">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="f5a2e-130">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="f5a2e-130">Save your project.</span></span>  
  
## <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="f5a2e-131">Chcete-li přidat kód pro dotazování databáze a zobrazit výsledky</span><span class="sxs-lookup"><span data-stu-id="f5a2e-131">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="f5a2e-132">Z **sada nástrojů**, přetáhněte ji <xref:System.Windows.Forms.DataGridView> na výchozí formuláře Windows pro svůj projekt Form1 ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="f5a2e-132">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="f5a2e-133">Dvakrát klikněte na Form1 k přidejte kód, který `Load` události formuláře.</span><span class="sxs-lookup"><span data-stu-id="f5a2e-133">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="f5a2e-134">Při přidání tabulky do Návrhář relací objektů návrháře přidat <xref:System.Data.Linq.DataContext> objekt pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="f5a2e-134">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="f5a2e-135">Tento objekt obsahuje kód, který musí mít přístup k těchto tabulkách, kromě jednotlivých objektů a kolekcí pro každou tabulku.</span><span class="sxs-lookup"><span data-stu-id="f5a2e-135">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="f5a2e-136"><xref:System.Data.Linq.DataContext> Objekt pro je s názvem projektu na základě názvu souboru DBML.</span><span class="sxs-lookup"><span data-stu-id="f5a2e-136">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="f5a2e-137">Pro tento projekt <xref:System.Data.Linq.DataContext> názvem objektu `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="f5a2e-137">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="f5a2e-138">Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> v kódu a dotazování tabulky určeného Návrhář relací objektů.</span><span class="sxs-lookup"><span data-stu-id="f5a2e-138">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="f5a2e-139">Přidejte následující kód, který `Load` události při dotazování tabulky, které jsou zveřejněné jako vlastnosti vaše data kontextu.</span><span class="sxs-lookup"><span data-stu-id="f5a2e-139">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-query-a-database-by-using-linq_1.vb)]  
  
4.  <span data-ttu-id="f5a2e-140">Stisknutím klávesy F5 spusťte projekt a zobrazit výsledky.</span><span class="sxs-lookup"><span data-stu-id="f5a2e-140">Press F5 to run your project and view the results.</span></span>  
  
5.  <span data-ttu-id="f5a2e-141">Toto jsou některé další dotazy, které můžete vyzkoušet:</span><span class="sxs-lookup"><span data-stu-id="f5a2e-141">Following are some additional queries that you can try:</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-query-a-database-by-using-linq_2.vb)]  
    [!code-vb[VbLINQToSQLHowTos#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-query-a-database-by-using-linq_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f5a2e-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5a2e-142">See Also</span></span>  
 [<span data-ttu-id="f5a2e-143">LINQ</span><span class="sxs-lookup"><span data-stu-id="f5a2e-143">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="f5a2e-144">Dotazy</span><span class="sxs-lookup"><span data-stu-id="f5a2e-144">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="f5a2e-145">Technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="f5a2e-145">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="f5a2e-146">Metody DataContext (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="f5a2e-146">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
