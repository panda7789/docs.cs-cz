---
title: 'Postupy: hledání minimální nebo maximální hodnoty ve výsledku dotazu pomocí LINQ'
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
ms.openlocfilehash: bddb90baa0b01fd9d724583b472af9f9fa7569e5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344968"
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a><span data-ttu-id="85a84-102">Postupy: Hledání minimální nebo maximální hodnoty ve výsledku dotazu pomocí LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85a84-102">How to: Find the Minimum or Maximum Value in a Query Result by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="85a84-103">LINQ (Language-Integrated Query) usnadňuje přístup k informacím o databázi a provádění dotazů.</span><span class="sxs-lookup"><span data-stu-id="85a84-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="85a84-104">Následující příklad ukazuje, jak vytvořit novou aplikaci, která provádí dotazy na databázi SQL Server.</span><span class="sxs-lookup"><span data-stu-id="85a84-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="85a84-105">Ukázka určuje minimální a maximální hodnoty pro výsledky pomocí klauzulí `Aggregate` a `Group By`.</span><span class="sxs-lookup"><span data-stu-id="85a84-105">The sample determines the minimum and maximum values for the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="85a84-106">Další informace naleznete v tématu [klauzule Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md) a [klauzule GROUP by](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="85a84-106">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="85a84-107">V příkladech v tomto tématu se používá ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="85a84-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="85a84-108">Pokud tuto databázi ve vývojovém počítači nemáte, můžete si ji stáhnout z webu Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="85a84-108">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="85a84-109">Pokyny najdete v tématu [stažení ukázkových databází](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="85a84-109">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="85a84-110">Vytvoření připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="85a84-110">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="85a84-111">V aplikaci Visual Studio otevřete **Průzkumník serveru**/**Database explorer** kliknutím na **Průzkumník serveru**/**Průzkumník databáze** v nabídce **zobrazení** .</span><span class="sxs-lookup"><span data-stu-id="85a84-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="85a84-112">Klikněte pravým tlačítkem na **datová připojení** v **Průzkumník serveru**/**Průzkumníku databáze** a pak klikněte na **Přidat připojení**.</span><span class="sxs-lookup"><span data-stu-id="85a84-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="85a84-113">Zadejte platné připojení k ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="85a84-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="85a84-114">Přidání projektu, který obsahuje soubor LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="85a84-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="85a84-115">V aplikaci Visual Studio v nabídce **soubor** přejděte na možnost **Nový** a poté klikněte na položku **projekt**.</span><span class="sxs-lookup"><span data-stu-id="85a84-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="85a84-116">Jako typ projektu vyberte Visual Basic **model Windows Forms aplikace** .</span><span class="sxs-lookup"><span data-stu-id="85a84-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="85a84-117">V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="85a84-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="85a84-118">Vyberte šablonu položky **LINQ to SQL třídy** .</span><span class="sxs-lookup"><span data-stu-id="85a84-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="85a84-119">Pojmenujte soubor `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="85a84-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="85a84-120">Klikněte na tlačítko **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="85a84-120">Click **Add**.</span></span> <span data-ttu-id="85a84-121">Pro soubor Northwind. dbml je otevřen Návrhář relací objektů (O/R Designer).</span><span class="sxs-lookup"><span data-stu-id="85a84-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="85a84-122">Přidání tabulek pro dotaz do návrháře O/R</span><span class="sxs-lookup"><span data-stu-id="85a84-122">To add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="85a84-123">V **Průzkumník serveru**/**Průzkumníku databáze**rozbalte připojení k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="85a84-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="85a84-124">Rozbalte složku **tabulky** .</span><span class="sxs-lookup"><span data-stu-id="85a84-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="85a84-125">Pokud jste návrháře pro/R zavřeli, můžete ho znovu otevřít dvojitým kliknutím na soubor Northwind. dbml, který jste přidali dříve.</span><span class="sxs-lookup"><span data-stu-id="85a84-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="85a84-126">Klikněte na tabulku Customers (zákazníci) a přetáhněte ji do levého podokna návrháře.</span><span class="sxs-lookup"><span data-stu-id="85a84-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="85a84-127">Klikněte na tabulku Orders (objednávky) a přetáhněte ji do levého podokna návrháře.</span><span class="sxs-lookup"><span data-stu-id="85a84-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="85a84-128">Návrhář vytvoří nový objekt `Customer` a objekty `Order` pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="85a84-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="85a84-129">Všimněte si, že návrhář automaticky detekuje relace mezi tabulkami a vytváří podřízené vlastnosti pro související objekty.</span><span class="sxs-lookup"><span data-stu-id="85a84-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="85a84-130">IntelliSense například zobrazí, že objekt `Customer` má vlastnost `Orders` pro všechny objednávky související s tímto zákazníkem.</span><span class="sxs-lookup"><span data-stu-id="85a84-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3. <span data-ttu-id="85a84-131">Uložte změny a zavřete návrháře.</span><span class="sxs-lookup"><span data-stu-id="85a84-131">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="85a84-132">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="85a84-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="85a84-133">Přidání kódu pro dotazování databáze a zobrazení výsledků</span><span class="sxs-lookup"><span data-stu-id="85a84-133">To add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="85a84-134">Z **panelu nástrojů**přetáhněte ovládací prvek <xref:System.Windows.Forms.DataGridView> do výchozího formuláře Windows pro váš projekt, Form1.</span><span class="sxs-lookup"><span data-stu-id="85a84-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="85a84-135">Poklikejte na Form1 a přidejte kód do události `Load` formuláře.</span><span class="sxs-lookup"><span data-stu-id="85a84-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3. <span data-ttu-id="85a84-136">Když jste přidali tabulky do návrháře pro/R, Návrhář přidal objekt <xref:System.Data.Linq.DataContext> pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="85a84-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="85a84-137">Tento objekt obsahuje kód, který potřebujete pro přístup k těmto tabulkám, kromě jednotlivých objektů a kolekcí pro každou tabulku.</span><span class="sxs-lookup"><span data-stu-id="85a84-137">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="85a84-138">Objekt <xref:System.Data.Linq.DataContext> pro projekt je pojmenován na základě názvu souboru. dbml.</span><span class="sxs-lookup"><span data-stu-id="85a84-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="85a84-139">Pro tento projekt má objekt <xref:System.Data.Linq.DataContext> název `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="85a84-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="85a84-140">Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> ve vašem kódu a dotazovat tabulky určené návrhářem O/R.</span><span class="sxs-lookup"><span data-stu-id="85a84-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="85a84-141">Do události `Load` přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="85a84-141">Add the following code to the `Load` event.</span></span> <span data-ttu-id="85a84-142">Tento kód se dotazuje na tabulky, které jsou přístupné jako vlastnosti kontextu dat, a určuje minimální a maximální hodnoty výsledků.</span><span class="sxs-lookup"><span data-stu-id="85a84-142">This code queries the tables that are exposed as properties of your data context and determines the minimum and maximum values for the results.</span></span> <span data-ttu-id="85a84-143">Ukázka používá `Aggregate` klauzuli pro dotaz na jeden výsledek a klauzuli `Group By` pro zobrazení průměru pro seskupené výsledky.</span><span class="sxs-lookup"><span data-stu-id="85a84-143">The sample uses he `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form7.vb#14)]  
  
4. <span data-ttu-id="85a84-144">Stisknutím klávesy F5 spusťte projekt a zobrazte výsledky.</span><span class="sxs-lookup"><span data-stu-id="85a84-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85a84-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85a84-145">See also</span></span>

- [<span data-ttu-id="85a84-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="85a84-146">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="85a84-147">Dotazy</span><span class="sxs-lookup"><span data-stu-id="85a84-147">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="85a84-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="85a84-148">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="85a84-149">Metody DataContext (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="85a84-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
