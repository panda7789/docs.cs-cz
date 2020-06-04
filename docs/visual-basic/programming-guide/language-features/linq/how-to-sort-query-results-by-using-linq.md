---
title: 'Postupy: Řazení výsledků dotazu pomocí LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- sorting query results, multiple columns
- sorting data [Visual Basic]
- sorting data [LINQ in Visual Basic]
- sorting query results [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], sorting results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 07a4584d-9fd8-4a1d-b7d9-ccf2efa5c84e
ms.openlocfilehash: c1bc6ab863f9de118d59e102d3d5d251d326f497
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404936"
---
# <a name="how-to-sort-query-results-by-using-linq-visual-basic"></a><span data-ttu-id="057e7-102">Postupy: Řazení výsledků dotazu pomocí LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="057e7-102">How to: Sort Query Results by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="057e7-103">LINQ (Language-Integrated Query) usnadňuje přístup k informacím o databázi a provádění dotazů.</span><span class="sxs-lookup"><span data-stu-id="057e7-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="057e7-104">Následující příklad ukazuje, jak vytvořit novou aplikaci, která provádí dotazy na databázi SQL Server a seřadí výsledky podle více polí pomocí `Order By` klauzule.</span><span class="sxs-lookup"><span data-stu-id="057e7-104">The following example shows how to create a new application that performs queries against a SQL Server database and sorts the results by multiple fields by using the `Order By` clause.</span></span> <span data-ttu-id="057e7-105">Pořadí řazení pro každé pole může být vzestupné nebo sestupné.</span><span class="sxs-lookup"><span data-stu-id="057e7-105">The sort order for each field can be ascending order or descending order.</span></span> <span data-ttu-id="057e7-106">Další informace najdete v tématu [ORDER by – klauzule](../../../language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="057e7-106">For more information, see [Order By Clause](../../../language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="057e7-107">V příkladech v tomto tématu se používá ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="057e7-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="057e7-108">Pokud tuto databázi ve vývojovém počítači nemáte, můžete si ji stáhnout z webu Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="057e7-108">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="057e7-109">Pokyny najdete v tématu [stažení ukázkových databází](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="057e7-109">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="057e7-110">Vytvoření připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="057e7-110">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="057e7-111">V aplikaci Visual Studio otevřete **Průzkumník serveru** / **Průzkumník databáze** kliknutím na **Průzkumník serveru** / **Průzkumník databáze** v nabídce **zobrazení** .</span><span class="sxs-lookup"><span data-stu-id="057e7-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="057e7-112">Klikněte pravým tlačítkem na **datová připojení** v **Průzkumník serveru** / **Průzkumníku databáze** a pak klikněte na **Přidat připojení**.</span><span class="sxs-lookup"><span data-stu-id="057e7-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="057e7-113">Zadejte platné připojení k ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="057e7-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="057e7-114">Přidání projektu, který obsahuje soubor LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="057e7-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="057e7-115">V aplikaci Visual Studio v nabídce **soubor** přejděte na možnost **Nový** a poté klikněte na položku **projekt**.</span><span class="sxs-lookup"><span data-stu-id="057e7-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="057e7-116">Jako typ projektu vyberte Visual Basic **model Windows Forms aplikace** .</span><span class="sxs-lookup"><span data-stu-id="057e7-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="057e7-117">V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="057e7-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="057e7-118">Vyberte šablonu položky **LINQ to SQL třídy** .</span><span class="sxs-lookup"><span data-stu-id="057e7-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="057e7-119">Pojmenujte soubor `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="057e7-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="057e7-120">Klikněte na tlačítko **Add** (Přidat).</span><span class="sxs-lookup"><span data-stu-id="057e7-120">Click **Add**.</span></span> <span data-ttu-id="057e7-121">Pro soubor Northwind. dbml je otevřen Návrhář relací objektů (O/R Designer).</span><span class="sxs-lookup"><span data-stu-id="057e7-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="057e7-122">Přidání tabulek pro dotaz do návrháře O/R</span><span class="sxs-lookup"><span data-stu-id="057e7-122">To add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="057e7-123">V **Server Explorer** / **Průzkumníku Průzkumník serveru Database**rozbalte připojení k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="057e7-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="057e7-124">Rozbalte složku **tabulky** .</span><span class="sxs-lookup"><span data-stu-id="057e7-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="057e7-125">Pokud jste návrháře pro/R zavřeli, můžete ho znovu otevřít dvojitým kliknutím na soubor Northwind. dbml, který jste přidali dříve.</span><span class="sxs-lookup"><span data-stu-id="057e7-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="057e7-126">Klikněte na tabulku Customers (zákazníci) a přetáhněte ji do levého podokna návrháře.</span><span class="sxs-lookup"><span data-stu-id="057e7-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="057e7-127">Klikněte na tabulku Orders (objednávky) a přetáhněte ji do levého podokna návrháře.</span><span class="sxs-lookup"><span data-stu-id="057e7-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="057e7-128">Návrhář vytvoří nové `Customer` objekty a `Order` pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="057e7-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="057e7-129">Všimněte si, že návrhář automaticky detekuje relace mezi tabulkami a vytváří podřízené vlastnosti pro související objekty.</span><span class="sxs-lookup"><span data-stu-id="057e7-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="057e7-130">IntelliSense například zobrazí, že `Customer` objekt má `Orders` vlastnost pro všechny objednávky související s tímto zákazníkem.</span><span class="sxs-lookup"><span data-stu-id="057e7-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3. <span data-ttu-id="057e7-131">Uložte změny a zavřete návrháře.</span><span class="sxs-lookup"><span data-stu-id="057e7-131">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="057e7-132">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="057e7-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="057e7-133">Přidání kódu pro dotazování databáze a zobrazení výsledků</span><span class="sxs-lookup"><span data-stu-id="057e7-133">To add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="057e7-134">Z **panelu nástrojů**přetáhněte <xref:System.Windows.Forms.DataGridView> ovládací prvek do výchozího formuláře Windows pro váš projekt, Form1.</span><span class="sxs-lookup"><span data-stu-id="057e7-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="057e7-135">Poklikejte na Form1 a přidejte kód do `Load` události formuláře.</span><span class="sxs-lookup"><span data-stu-id="057e7-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3. <span data-ttu-id="057e7-136">Když jste přidali tabulky do návrháře O/R, Návrhář přidal <xref:System.Data.Linq.DataContext> objekt do projektu.</span><span class="sxs-lookup"><span data-stu-id="057e7-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="057e7-137">Tento objekt obsahuje kód, který potřebujete pro přístup k těmto tabulkám, a pro přístup k jednotlivým objektům a kolekcím pro každou tabulku.</span><span class="sxs-lookup"><span data-stu-id="057e7-137">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="057e7-138"><xref:System.Data.Linq.DataContext>Objekt pro projekt je pojmenován na základě názvu souboru. dbml.</span><span class="sxs-lookup"><span data-stu-id="057e7-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="057e7-139">Pro tento projekt <xref:System.Data.Linq.DataContext> je objekt pojmenován `northwindDataContext` .</span><span class="sxs-lookup"><span data-stu-id="057e7-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="057e7-140">Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> v kódu a dotazovat se na tabulky určené návrhářem o/R.</span><span class="sxs-lookup"><span data-stu-id="057e7-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="057e7-141">Do události přidejte následující kód `Load` pro dotazování tabulek, které jsou zpřístupněny jako vlastnosti kontextu dat a seřaďte výsledky.</span><span class="sxs-lookup"><span data-stu-id="057e7-141">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context and sort the results.</span></span> <span data-ttu-id="057e7-142">Dotaz seřadí výsledky podle počtu objednávek zákazníků v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="057e7-142">The query sorts the results by the number of customer orders, in descending order.</span></span> <span data-ttu-id="057e7-143">Zákazníci, kteří mají stejný počet objednávek, jsou seřazeny podle názvu společnosti ve vzestupném pořadí (výchozí nastavení).</span><span class="sxs-lookup"><span data-stu-id="057e7-143">Customers that have the same number of orders are ordered by company name in ascending order (the default).</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form4.vb#10)]  
  
4. <span data-ttu-id="057e7-144">Stisknutím klávesy F5 spusťte projekt a zobrazte výsledky.</span><span class="sxs-lookup"><span data-stu-id="057e7-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="057e7-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="057e7-145">See also</span></span>

- [<span data-ttu-id="057e7-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="057e7-146">LINQ</span></span>](index.md)
- [<span data-ttu-id="057e7-147">Dotazy</span><span class="sxs-lookup"><span data-stu-id="057e7-147">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="057e7-148">Technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="057e7-148">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="057e7-149">Metody DataContext (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="057e7-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
