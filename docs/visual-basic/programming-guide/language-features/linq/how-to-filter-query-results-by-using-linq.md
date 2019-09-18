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
ms.openlocfilehash: 1250f2fe0ccd7661b9bc1986000143ec4a15a9f0
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053279"
---
# <a name="how-to-filter-query-results-by-using-linq-visual-basic"></a><span data-ttu-id="8a468-102">Postupy: Filtrování výsledků dotazu pomocí LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a468-102">How to: Filter Query Results by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="8a468-103">LINQ (Language-Integrated Query) usnadňuje přístup k informacím o databázi a provádění dotazů.</span><span class="sxs-lookup"><span data-stu-id="8a468-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>

<span data-ttu-id="8a468-104">Následující příklad ukazuje, jak vytvořit novou aplikaci, která provádí dotazy na databázi SQL Server a filtruje výsledky podle konkrétní hodnoty pomocí `Where` klauzule.</span><span class="sxs-lookup"><span data-stu-id="8a468-104">The following example shows how to create a new application that performs queries against a SQL Server database and filters the results by a particular value by using the `Where` clause.</span></span> <span data-ttu-id="8a468-105">Další informace naleznete v tématu [Where klauzule](../../../../visual-basic/language-reference/queries/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="8a468-105">For more information, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>

<span data-ttu-id="8a468-106">V příkladech v tomto tématu se používá ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="8a468-106">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="8a468-107">Pokud tuto databázi ve vývojovém počítači nemáte, můžete si ji stáhnout z webu Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="8a468-107">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="8a468-108">Pokyny najdete v tématu [stažení ukázkových databází](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="8a468-108">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="8a468-109">Vytvoření připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="8a468-109">To create a connection to a database</span></span>

1. <span data-ttu-id="8a468-110">V aplikaci Visual Studio otevřete **Průzkumník serveru**/**Průzkumník databáze** kliknutím na **Průzkumník serveru**/**Průzkumník databáze** v nabídce **zobrazení** .</span><span class="sxs-lookup"><span data-stu-id="8a468-110">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>

2. <span data-ttu-id="8a468-111">Klikněte pravým tlačítkem na **datová připojení** v **Průzkumník serveru**/**Průzkumníku databáze** a pak klikněte na **Přidat připojení**.</span><span class="sxs-lookup"><span data-stu-id="8a468-111">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>

3. <span data-ttu-id="8a468-112">Zadejte platné připojení k ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="8a468-112">Specify a valid connection to the Northwind sample database.</span></span>

## <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="8a468-113">Přidání projektu, který obsahuje soubor LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="8a468-113">To add a project that contains a LINQ to SQL file</span></span>

1. <span data-ttu-id="8a468-114">V sadě Visual Studio na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu**.</span><span class="sxs-lookup"><span data-stu-id="8a468-114">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="8a468-115">Jako typ projektu vyberte Visual Basic **model Windows Forms aplikace** .</span><span class="sxs-lookup"><span data-stu-id="8a468-115">Select Visual Basic **Windows Forms Application** as the project type.</span></span>

2. <span data-ttu-id="8a468-116">V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="8a468-116">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="8a468-117">Vyberte šablonu položky **LINQ to SQL třídy** .</span><span class="sxs-lookup"><span data-stu-id="8a468-117">Select the **LINQ to SQL Classes** item template.</span></span>

3. <span data-ttu-id="8a468-118">Pojmenujte soubor `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="8a468-118">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="8a468-119">Klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="8a468-119">Click **Add**.</span></span> <span data-ttu-id="8a468-120">Otevře se Návrhář relací objektů (O/R Designer) pro soubor Northwind. dbml.</span><span class="sxs-lookup"><span data-stu-id="8a468-120">The Object Relational Designer (O/R Designer) opens for the northwind.dbml file.</span></span>

## <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="8a468-121">Přidání tabulek pro dotaz do návrháře O/R</span><span class="sxs-lookup"><span data-stu-id="8a468-121">To add tables to query to the O/R Designer</span></span>

1. <span data-ttu-id="8a468-122">V Průzkumníku **Průzkumník serveru**/**Database**rozbalte připojení k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="8a468-122">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="8a468-123">Rozbalte složku **tabulky** .</span><span class="sxs-lookup"><span data-stu-id="8a468-123">Expand the **Tables** folder.</span></span>

     <span data-ttu-id="8a468-124">Pokud jste návrháře pro/R zavřeli, můžete ho znovu otevřít dvojitým kliknutím na soubor Northwind. dbml, který jste přidali dříve.</span><span class="sxs-lookup"><span data-stu-id="8a468-124">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>

2. <span data-ttu-id="8a468-125">Klikněte na tabulku Customers (zákazníci) a přetáhněte ji do levého podokna návrháře.</span><span class="sxs-lookup"><span data-stu-id="8a468-125">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="8a468-126">Klikněte na tabulku Orders (objednávky) a přetáhněte ji do levého podokna návrháře.</span><span class="sxs-lookup"><span data-stu-id="8a468-126">Click the Orders table and drag it to the left pane of the designer.</span></span>

     <span data-ttu-id="8a468-127">Návrhář vytvoří nové `Customer` objekty a `Order` pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="8a468-127">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="8a468-128">Všimněte si, že návrhář automaticky detekuje relace mezi tabulkami a vytváří podřízené vlastnosti pro související objekty.</span><span class="sxs-lookup"><span data-stu-id="8a468-128">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="8a468-129">IntelliSense například zobrazí, že `Customer` objekt `Orders` má vlastnost pro všechny objednávky související s tímto zákazníkem.</span><span class="sxs-lookup"><span data-stu-id="8a468-129">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>

3. <span data-ttu-id="8a468-130">Uložte změny a zavřete návrháře.</span><span class="sxs-lookup"><span data-stu-id="8a468-130">Save your changes and close the designer.</span></span>

4. <span data-ttu-id="8a468-131">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="8a468-131">Save your project.</span></span>

## <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="8a468-132">Přidání kódu pro dotazování databáze a zobrazení výsledků</span><span class="sxs-lookup"><span data-stu-id="8a468-132">To add code to query the database and display the results</span></span>

1. <span data-ttu-id="8a468-133">Z **panelu nástrojů**přetáhněte <xref:System.Windows.Forms.DataGridView> ovládací prvek do výchozího formuláře Windows pro váš projekt, Form1.</span><span class="sxs-lookup"><span data-stu-id="8a468-133">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>

2. <span data-ttu-id="8a468-134">Poklikejte na Form1 a přidejte kód do `Load` události formuláře.</span><span class="sxs-lookup"><span data-stu-id="8a468-134">Double-click Form1 to add code to the `Load` event of the form.</span></span>

3. <span data-ttu-id="8a468-135">Když jste přidali tabulky do návrháře o/R, Návrhář přidal <xref:System.Data.Linq.DataContext> objekt pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="8a468-135">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="8a468-136">Tento objekt obsahuje kód, který potřebujete pro přístup k těmto tabulkám, kromě jednotlivých objektů a kolekcí pro každou tabulku.</span><span class="sxs-lookup"><span data-stu-id="8a468-136">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="8a468-137"><xref:System.Data.Linq.DataContext> Objekt pro projekt je pojmenován na základě názvu souboru. dbml.</span><span class="sxs-lookup"><span data-stu-id="8a468-137">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="8a468-138">Pro tento projekt <xref:System.Data.Linq.DataContext> je objekt pojmenován `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="8a468-138">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>

    <span data-ttu-id="8a468-139">Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> v kódu a dotazovat se na tabulky určené návrhářem o/R.</span><span class="sxs-lookup"><span data-stu-id="8a468-139">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>

    <span data-ttu-id="8a468-140">Do `Load` události přidejte následující kód pro dotazování tabulek, které jsou zpřístupněny jako vlastnosti vašeho kontextu dat.</span><span class="sxs-lookup"><span data-stu-id="8a468-140">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="8a468-141">Dotaz vyfiltruje výsledky a vrátí pouze zákazníky nacházející se v `London`.</span><span class="sxs-lookup"><span data-stu-id="8a468-141">The query filters the results and returns only customers that are located in `London`.</span></span>

    [!code-vb[VbLINQToSQLHowTos#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#11)]

4. <span data-ttu-id="8a468-142">Stisknutím klávesy F5 spusťte projekt a zobrazte výsledky.</span><span class="sxs-lookup"><span data-stu-id="8a468-142">Press F5 to run your project and view the results.</span></span>

5. <span data-ttu-id="8a468-143">Níže jsou uvedeny některé další filtry, které můžete vyzkoušet.</span><span class="sxs-lookup"><span data-stu-id="8a468-143">Following are some other filters that you can try.</span></span>

    [!code-vb[VbLINQToSQLHowTos#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#12)]

## <a name="see-also"></a><span data-ttu-id="8a468-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8a468-144">See also</span></span>

- [<span data-ttu-id="8a468-145">LINQ</span><span class="sxs-lookup"><span data-stu-id="8a468-145">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="8a468-146">Dotazy</span><span class="sxs-lookup"><span data-stu-id="8a468-146">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="8a468-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="8a468-147">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="8a468-148">Metody DataContext (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="8a468-148">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
