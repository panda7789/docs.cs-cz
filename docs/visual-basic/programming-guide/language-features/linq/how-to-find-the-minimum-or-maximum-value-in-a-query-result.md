---
title: 'Postupy: Hledání minimální nebo maximální hodnoty ve výsledku dotazu pomocí LINQ'
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
ms.openlocfilehash: ef5f218cdcc7275f616486110825ad0b9df11cc3
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112359"
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a><span data-ttu-id="1d67b-102">Postupy: Hledání minimální nebo maximální hodnoty ve výsledku dotazu pomocí LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d67b-102">How to: Find the Minimum or Maximum Value in a Query Result by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="1d67b-103">Jazykově integrovaný dotaz (LINQ) usnadňuje přístup k informacím o databázi a spouštění dotazů.</span><span class="sxs-lookup"><span data-stu-id="1d67b-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="1d67b-104">Následující příklad ukazuje, jak vytvořit novou aplikaci, která provádí dotazy proti databázi serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="1d67b-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="1d67b-105">Ukázka určuje minimální a maximální hodnoty výsledků `Aggregate` pomocí `Group By` klauzule a.</span><span class="sxs-lookup"><span data-stu-id="1d67b-105">The sample determines the minimum and maximum values for the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="1d67b-106">Další informace naleznete [v tématu Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and Group By [Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="1d67b-106">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="1d67b-107">Příklady v tomto tématu používají ukázkovou databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="1d67b-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="1d67b-108">Pokud tuto databázi ve vývojovém počítači nemáte, můžete ji stáhnout ze služby Stažení softwaru.</span><span class="sxs-lookup"><span data-stu-id="1d67b-108">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="1d67b-109">Pokyny naleznete v [tématu Stahování ukázkových databází](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="1d67b-109">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="create-a-connection-to-a-database"></a><span data-ttu-id="1d67b-110">Vytvoření připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="1d67b-110">Create a connection to a database</span></span>  
  
1. <span data-ttu-id="1d67b-111">V sadě Visual Studio otevřete**Průzkumníka** **databáze**/serveru klepnutím na**Průzkumník a** **Průzkumník**/serveru v nabídce **Zobrazení.**</span><span class="sxs-lookup"><span data-stu-id="1d67b-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="1d67b-112">Klepněte pravým tlačítkem myši na **položku Datová připojení** v**Průzkumníkovi databáze** **serveru**/a potom klepněte na příkaz **Přidat připojení**.</span><span class="sxs-lookup"><span data-stu-id="1d67b-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="1d67b-113">Zadejte platné připojení k ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="1d67b-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="1d67b-114">Přidání projektu, který obsahuje soubor LINQ do souboru SQL</span><span class="sxs-lookup"><span data-stu-id="1d67b-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="1d67b-115">V sadě Visual Studio v nabídce **Soubor** přejděte na **Nový** a potom klikněte na **Project**.</span><span class="sxs-lookup"><span data-stu-id="1d67b-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="1d67b-116">Jako typ projektu vyberte aplikaci Visual Basic **Windows Forms Application.**</span><span class="sxs-lookup"><span data-stu-id="1d67b-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="1d67b-117">V nabídce **Project** klikněte na **Add New Item**.</span><span class="sxs-lookup"><span data-stu-id="1d67b-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="1d67b-118">Vyberte šablonu **položky LINQ na třídy SQL.**</span><span class="sxs-lookup"><span data-stu-id="1d67b-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="1d67b-119">Pojmenujte soubor `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="1d67b-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="1d67b-120">Klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="1d67b-120">Click **Add**.</span></span> <span data-ttu-id="1d67b-121">Objekt relační návrhář (O/R Designer) je otevřen pro soubor northwind.dbml.</span><span class="sxs-lookup"><span data-stu-id="1d67b-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
## <a name="add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="1d67b-122">Přidání tabulek do dotazu do Návrháře O/R</span><span class="sxs-lookup"><span data-stu-id="1d67b-122">Add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="1d67b-123">V**Průzkumníku databáze** **serveru**/rozbalte připojení k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="1d67b-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="1d67b-124">Rozbalte složku **Tabulky.**</span><span class="sxs-lookup"><span data-stu-id="1d67b-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="1d67b-125">Pokud jste zavřeli O/R Designer, můžete jej znovu otevřít poklepáním na soubor northwind.dbml, který jste přidali dříve.</span><span class="sxs-lookup"><span data-stu-id="1d67b-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="1d67b-126">Klikněte na tabulku Zákazníci a přetáhněte ji do levého podokna návrháře.</span><span class="sxs-lookup"><span data-stu-id="1d67b-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="1d67b-127">Klikněte na tabulku Objednávky a přetáhněte ji do levého podokna návrháře.</span><span class="sxs-lookup"><span data-stu-id="1d67b-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="1d67b-128">Návrhář vytvoří `Customer` nové `Order` a objekty pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="1d67b-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="1d67b-129">Všimněte si, že návrhář automaticky detekuje relace mezi tabulkami a vytvoří podřízené vlastnosti pro související objekty.</span><span class="sxs-lookup"><span data-stu-id="1d67b-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="1d67b-130">Technologie IntelliSense například zobrazí, `Customer` že `Orders` objekt má vlastnost pro všechny objednávky související s tímto zákazníkem.</span><span class="sxs-lookup"><span data-stu-id="1d67b-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3. <span data-ttu-id="1d67b-131">Uložte změny a zavřete návrháře.</span><span class="sxs-lookup"><span data-stu-id="1d67b-131">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="1d67b-132">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="1d67b-132">Save your project.</span></span>  
  
## <a name="add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="1d67b-133">Přidání kódu k dotazování databáze a zobrazení výsledků</span><span class="sxs-lookup"><span data-stu-id="1d67b-133">Add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="1d67b-134">Z **panelu nástrojů** <xref:System.Windows.Forms.DataGridView> přetáhněte ovládací prvek do výchozího formuláře systému Windows pro projekt Form1.</span><span class="sxs-lookup"><span data-stu-id="1d67b-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="1d67b-135">Poklepáním na formulář1 přidejte kód k `Load` události formuláře.</span><span class="sxs-lookup"><span data-stu-id="1d67b-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3. <span data-ttu-id="1d67b-136">Když jste přidali tabulky do Návrháře O/R, návrhář přidal <xref:System.Data.Linq.DataContext> objekt pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="1d67b-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="1d67b-137">Tento objekt obsahuje kód, který je nutné mít pro přístup k těmto tabulkám, kromě jednotlivých objektů a kolekcí pro každou tabulku.</span><span class="sxs-lookup"><span data-stu-id="1d67b-137">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="1d67b-138">Objekt <xref:System.Data.Linq.DataContext> projektu je pojmenován na základě názvu souboru DBML.</span><span class="sxs-lookup"><span data-stu-id="1d67b-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="1d67b-139">Pro tento projekt <xref:System.Data.Linq.DataContext> je `northwindDataContext`objekt pojmenován .</span><span class="sxs-lookup"><span data-stu-id="1d67b-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="1d67b-140">Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> v kódu a dotaz tabulky určené O/R Designer.</span><span class="sxs-lookup"><span data-stu-id="1d67b-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="1d67b-141">Přidejte následující kód `Load` k události.</span><span class="sxs-lookup"><span data-stu-id="1d67b-141">Add the following code to the `Load` event.</span></span> <span data-ttu-id="1d67b-142">Tento kód dotazuje tabulky, které jsou vystaveny jako vlastnosti kontextu dat a určuje minimální a maximální hodnoty pro výsledky.</span><span class="sxs-lookup"><span data-stu-id="1d67b-142">This code queries the tables that are exposed as properties of your data context and determines the minimum and maximum values for the results.</span></span> <span data-ttu-id="1d67b-143">Ukázka používá `Aggregate` klauzuli k dotazování na `Group By` jeden výsledek a klauzule zobrazit průměr pro seskupené výsledky.</span><span class="sxs-lookup"><span data-stu-id="1d67b-143">The sample uses the `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form7.vb#14)]  
  
4. <span data-ttu-id="1d67b-144">Stisknutím **klávesy F5** spusťte projekt a zobrazte výsledky.</span><span class="sxs-lookup"><span data-stu-id="1d67b-144">Press **F5** to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d67b-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="1d67b-145">See also</span></span>

- [<span data-ttu-id="1d67b-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="1d67b-146">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="1d67b-147">Dotazy</span><span class="sxs-lookup"><span data-stu-id="1d67b-147">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="1d67b-148">Technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="1d67b-148">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="1d67b-149">Metody DataContext (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="1d67b-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
