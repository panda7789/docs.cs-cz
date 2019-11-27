---
title: 'Postupy: počítání, suma nebo průměr dat pomocí LINQ'
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
ms.openlocfilehash: 7e105c75653f979f53567ef49f1f4cdeafaa4d0f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345013"
---
# <a name="how-to-count-sum-or-average-data-by-using-linq-visual-basic"></a><span data-ttu-id="13e3c-102">Postupy: Počet, suma nebo průměr dat pomocí LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13e3c-102">How to: Count, Sum, or Average Data by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="13e3c-103">LINQ (Language-Integrated Query) usnadňuje přístup k informacím o databázi a provádění dotazů.</span><span class="sxs-lookup"><span data-stu-id="13e3c-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="13e3c-104">Následující příklad ukazuje, jak vytvořit novou aplikaci, která provádí dotazy na databázi SQL Server.</span><span class="sxs-lookup"><span data-stu-id="13e3c-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="13e3c-105">Počet vzorků, součty a průměrují výsledky pomocí klauzulí `Aggregate` a `Group By`.</span><span class="sxs-lookup"><span data-stu-id="13e3c-105">The sample counts, sums, and averages the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="13e3c-106">Další informace naleznete v tématu [klauzule Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md) a [klauzule GROUP by](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="13e3c-106">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="13e3c-107">V příkladech v tomto tématu se používá ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="13e3c-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="13e3c-108">Pokud tuto databázi ve vývojovém počítači nemáte, můžete si ji stáhnout z webu Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="13e3c-108">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="13e3c-109">Pokyny najdete v tématu [stažení ukázkových databází](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="13e3c-109">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="13e3c-110">Vytvoření připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="13e3c-110">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="13e3c-111">V aplikaci Visual Studio otevřete **Průzkumník serveru**/**Database explorer** kliknutím na **Průzkumník serveru**/**Průzkumník databáze** v nabídce **zobrazení** .</span><span class="sxs-lookup"><span data-stu-id="13e3c-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="13e3c-112">Klikněte pravým tlačítkem na **datová připojení** v **Průzkumník serveru**/**Průzkumníku databáze** a pak klikněte na **Přidat připojení**.</span><span class="sxs-lookup"><span data-stu-id="13e3c-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="13e3c-113">Zadejte platné připojení k ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="13e3c-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="13e3c-114">Přidání projektu, který obsahuje soubor LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="13e3c-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="13e3c-115">V aplikaci Visual Studio v nabídce **soubor** přejděte na možnost **Nový** a poté klikněte na položku **projekt**.</span><span class="sxs-lookup"><span data-stu-id="13e3c-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="13e3c-116">Jako typ projektu vyberte Visual Basic **model Windows Forms aplikace** .</span><span class="sxs-lookup"><span data-stu-id="13e3c-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="13e3c-117">V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="13e3c-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="13e3c-118">Vyberte šablonu položky **LINQ to SQL třídy** .</span><span class="sxs-lookup"><span data-stu-id="13e3c-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="13e3c-119">Pojmenujte soubor `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="13e3c-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="13e3c-120">Klikněte na tlačítko **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="13e3c-120">Click **Add**.</span></span> <span data-ttu-id="13e3c-121">Pro soubor Northwind. dbml je otevřen Návrhář relací objektů (O/R Designer).</span><span class="sxs-lookup"><span data-stu-id="13e3c-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="13e3c-122">Přidání tabulek pro dotaz do návrháře O/R</span><span class="sxs-lookup"><span data-stu-id="13e3c-122">To add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="13e3c-123">V **Průzkumník serveru**/**Průzkumníku databáze**rozbalte připojení k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="13e3c-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="13e3c-124">Rozbalte složku **tabulky** .</span><span class="sxs-lookup"><span data-stu-id="13e3c-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="13e3c-125">Pokud jste návrháře pro/R zavřeli, můžete ho znovu otevřít dvojitým kliknutím na soubor Northwind. dbml, který jste přidali dříve.</span><span class="sxs-lookup"><span data-stu-id="13e3c-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="13e3c-126">Klikněte na tabulku Customers (zákazníci) a přetáhněte ji do levého podokna návrháře.</span><span class="sxs-lookup"><span data-stu-id="13e3c-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="13e3c-127">Klikněte na tabulku Orders (objednávky) a přetáhněte ji do levého podokna návrháře.</span><span class="sxs-lookup"><span data-stu-id="13e3c-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="13e3c-128">Návrhář vytvoří nový objekt `Customer` a objekty `Order` pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="13e3c-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="13e3c-129">Všimněte si, že návrhář automaticky detekuje relace mezi tabulkami a vytváří podřízené vlastnosti pro související objekty.</span><span class="sxs-lookup"><span data-stu-id="13e3c-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="13e3c-130">IntelliSense například zobrazí, že objekt `Customer` má vlastnost `Orders` pro všechny objednávky související s tímto zákazníkem.</span><span class="sxs-lookup"><span data-stu-id="13e3c-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3. <span data-ttu-id="13e3c-131">Uložte změny a zavřete návrháře.</span><span class="sxs-lookup"><span data-stu-id="13e3c-131">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="13e3c-132">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="13e3c-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="13e3c-133">Přidání kódu pro dotazování databáze a zobrazení výsledků</span><span class="sxs-lookup"><span data-stu-id="13e3c-133">To add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="13e3c-134">Z **panelu nástrojů**přetáhněte ovládací prvek <xref:System.Windows.Forms.DataGridView> do výchozího formuláře Windows pro váš projekt, Form1.</span><span class="sxs-lookup"><span data-stu-id="13e3c-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="13e3c-135">Poklikejte na Form1 a přidejte kód do události `Load` formuláře.</span><span class="sxs-lookup"><span data-stu-id="13e3c-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3. <span data-ttu-id="13e3c-136">Když jste přidali tabulky do návrháře pro/R, Návrhář přidal objekt <xref:System.Data.Linq.DataContext> pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="13e3c-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="13e3c-137">Tento objekt obsahuje kód, který potřebujete pro přístup k těmto tabulkám, a pro přístup k jednotlivým objektům a kolekcím pro každou tabulku.</span><span class="sxs-lookup"><span data-stu-id="13e3c-137">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="13e3c-138">Objekt <xref:System.Data.Linq.DataContext> pro projekt je pojmenován na základě názvu souboru. dbml.</span><span class="sxs-lookup"><span data-stu-id="13e3c-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="13e3c-139">Pro tento projekt má objekt <xref:System.Data.Linq.DataContext> název `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="13e3c-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="13e3c-140">Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> ve vašem kódu a dotazovat tabulky určené návrhářem O/R.</span><span class="sxs-lookup"><span data-stu-id="13e3c-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="13e3c-141">Přidejte následující kód do události `Load` pro dotazování tabulek, které jsou zpřístupněny jako vlastnosti <xref:System.Data.Linq.DataContext> a počet, součet a průměr výsledků.</span><span class="sxs-lookup"><span data-stu-id="13e3c-141">Add the following code to the `Load` event to query the tables that are exposed as properties of your <xref:System.Data.Linq.DataContext> and count, sum, and average the results.</span></span> <span data-ttu-id="13e3c-142">Ukázka používá klauzuli `Aggregate` pro dotazování na jeden výsledek a klauzuli `Group By` pro zobrazení průměru pro seskupené výsledky.</span><span class="sxs-lookup"><span data-stu-id="13e3c-142">The sample uses the `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form6.vb#13)]  
  
4. <span data-ttu-id="13e3c-143">Stisknutím klávesy F5 spusťte projekt a zobrazte výsledky.</span><span class="sxs-lookup"><span data-stu-id="13e3c-143">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13e3c-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="13e3c-144">See also</span></span>

- [<span data-ttu-id="13e3c-145">LINQ</span><span class="sxs-lookup"><span data-stu-id="13e3c-145">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="13e3c-146">Dotazy</span><span class="sxs-lookup"><span data-stu-id="13e3c-146">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="13e3c-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="13e3c-147">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="13e3c-148">Metody DataContext (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="13e3c-148">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="13e3c-149">Klauzule Aggregate</span><span class="sxs-lookup"><span data-stu-id="13e3c-149">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="13e3c-150">Klauzule Group By</span><span class="sxs-lookup"><span data-stu-id="13e3c-150">Group By Clause</span></span>](../../../../visual-basic/language-reference/queries/group-by-clause.md)
