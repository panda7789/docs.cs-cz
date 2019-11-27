---
title: 'Postupy: Vrácení výsledku dotazu LINQ jako specifického typu'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], specific type returned
- projection [LINQ in Visual Basic]
- anonymous types [Visual Basic]
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
ms.openlocfilehash: 1084743b0c50d381375b76a3116ed7c9e6f9d769
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354202"
---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a><span data-ttu-id="c84bd-102">Postupy: Vrácení výsledku dotazu LINQ jako specifického typu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c84bd-102">How to: Return a LINQ Query Result as a Specific Type (Visual Basic)</span></span>
<span data-ttu-id="c84bd-103">LINQ (Language-Integrated Query) usnadňuje přístup k informacím o databázi a provádění dotazů.</span><span class="sxs-lookup"><span data-stu-id="c84bd-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span> <span data-ttu-id="c84bd-104">Ve výchozím nastavení dotazy LINQ vrátí seznam objektů jako anonymní typ.</span><span class="sxs-lookup"><span data-stu-id="c84bd-104">By default, LINQ queries return a list of objects as an anonymous type.</span></span> <span data-ttu-id="c84bd-105">Můžete také určit, že dotaz vrátí seznam konkrétního typu pomocí klauzule `Select`.</span><span class="sxs-lookup"><span data-stu-id="c84bd-105">You can also specify that a query return a list of a specific type by using the `Select` clause.</span></span>  
  
 <span data-ttu-id="c84bd-106">Následující příklad ukazuje, jak vytvořit novou aplikaci, která provádí dotazy na databázi SQL Server a projekty výsledky jako konkrétní pojmenovaný typ.</span><span class="sxs-lookup"><span data-stu-id="c84bd-106">The following example shows how to create a new application that performs queries against a SQL Server database and projects the results as a specific named type.</span></span> <span data-ttu-id="c84bd-107">Další informace naleznete v tématu [anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) a [klauzule SELECT](../../../../visual-basic/language-reference/queries/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="c84bd-107">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) and [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span></span>  
  
 <span data-ttu-id="c84bd-108">V příkladech v tomto tématu se používá ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="c84bd-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="c84bd-109">Pokud tuto databázi ve vývojovém počítači nemáte, můžete si ji stáhnout z webu Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="c84bd-109">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="c84bd-110">Pokyny najdete v tématu [stažení ukázkových databází](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="c84bd-110">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="c84bd-111">Vytvoření připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="c84bd-111">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="c84bd-112">V aplikaci Visual Studio otevřete **Průzkumník serveru**/**Database explorer** kliknutím na **Průzkumník serveru**/**Průzkumník databáze** v nabídce **zobrazení** .</span><span class="sxs-lookup"><span data-stu-id="c84bd-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="c84bd-113">Klikněte pravým tlačítkem na **datová připojení** v **Průzkumník serveru**/**Průzkumníku databáze** a pak klikněte na **Přidat připojení**.</span><span class="sxs-lookup"><span data-stu-id="c84bd-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="c84bd-114">Zadejte platné připojení k ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="c84bd-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="c84bd-115">Přidání projektu, který obsahuje soubor LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="c84bd-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="c84bd-116">V aplikaci Visual Studio v nabídce **soubor** přejděte na možnost **Nový** a poté klikněte na položku **projekt**.</span><span class="sxs-lookup"><span data-stu-id="c84bd-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="c84bd-117">Jako typ projektu vyberte Visual Basic **model Windows Forms aplikace** .</span><span class="sxs-lookup"><span data-stu-id="c84bd-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="c84bd-118">V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="c84bd-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="c84bd-119">Vyberte šablonu položky **LINQ to SQL třídy** .</span><span class="sxs-lookup"><span data-stu-id="c84bd-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="c84bd-120">Pojmenujte soubor `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="c84bd-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="c84bd-121">Klikněte na tlačítko **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="c84bd-121">Click **Add**.</span></span> <span data-ttu-id="c84bd-122">Pro soubor Northwind. dbml je otevřen Návrhář relací objektů (O/R Designer).</span><span class="sxs-lookup"><span data-stu-id="c84bd-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="c84bd-123">Přidání tabulek pro dotaz do návrháře O/R</span><span class="sxs-lookup"><span data-stu-id="c84bd-123">To add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="c84bd-124">V **Průzkumník serveru**/**Průzkumníku databáze**rozbalte připojení k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="c84bd-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="c84bd-125">Rozbalte složku **tabulky** .</span><span class="sxs-lookup"><span data-stu-id="c84bd-125">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="c84bd-126">Pokud jste návrháře pro/R zavřeli, můžete ho znovu otevřít dvojitým kliknutím na soubor Northwind. dbml, který jste přidali dříve.</span><span class="sxs-lookup"><span data-stu-id="c84bd-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="c84bd-127">Klikněte na tabulku Customers (zákazníci) a přetáhněte ji do levého podokna návrháře.</span><span class="sxs-lookup"><span data-stu-id="c84bd-127">Click the Customers table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="c84bd-128">Návrhář vytvoří nový objekt `Customer` pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="c84bd-128">The designer creates a new `Customer` object for your project.</span></span> <span data-ttu-id="c84bd-129">Výsledek dotazu můžete promítnout jako typ `Customer` nebo jako typ, který vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="c84bd-129">You can project a query result as the `Customer` type or as a type that you create.</span></span> <span data-ttu-id="c84bd-130">Tato ukázka vytvoří nový typ v pozdější proceduře a projekt výsledek dotazu jako tento typ.</span><span class="sxs-lookup"><span data-stu-id="c84bd-130">This sample will create a new type in a later procedure and project a query result as that type.</span></span>  
  
3. <span data-ttu-id="c84bd-131">Uložte změny a zavřete návrháře.</span><span class="sxs-lookup"><span data-stu-id="c84bd-131">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="c84bd-132">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="c84bd-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="c84bd-133">Přidání kódu pro dotazování databáze a zobrazení výsledků</span><span class="sxs-lookup"><span data-stu-id="c84bd-133">To add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="c84bd-134">Z **panelu nástrojů**přetáhněte ovládací prvek <xref:System.Windows.Forms.DataGridView> do výchozího formuláře Windows pro váš projekt, Form1.</span><span class="sxs-lookup"><span data-stu-id="c84bd-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="c84bd-135">Poklikejte na Form1 a upravte třídu Form1.</span><span class="sxs-lookup"><span data-stu-id="c84bd-135">Double-click Form1 to modify the Form1 class.</span></span>  
  
3. <span data-ttu-id="c84bd-136">Po příkazu `End Class` třídy Form1 přidejte následující kód pro vytvoření `CustomerInfo` typu pro uchování výsledků dotazu pro tuto ukázku.</span><span class="sxs-lookup"><span data-stu-id="c84bd-136">After the `End Class` statement of the Form1 class, add the following code to create a `CustomerInfo` type to hold the query results for this sample.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#16)]  
  
4. <span data-ttu-id="c84bd-137">Když jste přidali tabulky do návrháře pro/R, Návrhář přidal do projektu objekt <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="c84bd-137">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="c84bd-138">Tento objekt obsahuje kód, který potřebujete pro přístup k těmto tabulkám, a pro přístup k jednotlivým objektům a kolekcím pro každou tabulku.</span><span class="sxs-lookup"><span data-stu-id="c84bd-138">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="c84bd-139">Objekt <xref:System.Data.Linq.DataContext> pro projekt je pojmenován na základě názvu souboru. dbml.</span><span class="sxs-lookup"><span data-stu-id="c84bd-139">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="c84bd-140">Pro tento projekt má objekt <xref:System.Data.Linq.DataContext> název `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="c84bd-140">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="c84bd-141">Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> ve vašem kódu a dotazovat tabulky určené návrhářem O/R.</span><span class="sxs-lookup"><span data-stu-id="c84bd-141">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="c84bd-142">Do události `Load` třídy Form1 přidejte následující kód pro dotazování tabulek, které jsou zpřístupněny jako vlastnosti vašeho kontextu dat.</span><span class="sxs-lookup"><span data-stu-id="c84bd-142">In the `Load` event of the Form1 class, add the following code to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="c84bd-143">Klauzule `Select` dotazu vytvoří nový typ `CustomerInfo` namísto anonymního typu pro každou položku výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="c84bd-143">The `Select` clause of the query will create a new `CustomerInfo` type instead of an anonymous type for each item of the query result.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#15)]  
  
5. <span data-ttu-id="c84bd-144">Stisknutím klávesy F5 spusťte projekt a zobrazte výsledky.</span><span class="sxs-lookup"><span data-stu-id="c84bd-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c84bd-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c84bd-145">See also</span></span>

- [<span data-ttu-id="c84bd-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="c84bd-146">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="c84bd-147">Dotazy</span><span class="sxs-lookup"><span data-stu-id="c84bd-147">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="c84bd-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="c84bd-148">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="c84bd-149">Metody DataContext (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="c84bd-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
