---
title: 'Postupy: Volání uložené procedury pomocí LINQ (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
ms.openlocfilehash: 2d05d43ae8f9b93fd3e5e405bb7ff0d59832e830
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823347"
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a><span data-ttu-id="26312-102">Postupy: Volání uložené procedury pomocí LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26312-102">How to: Call a Stored Procedure by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="26312-103">Language Integrated Query (LINQ) usnadňuje přístup k informacím o databáze, včetně databázové objekty, jako uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="26312-103">Language-Integrated Query (LINQ) makes it easy to access database information, including database objects such as stored procedures.</span></span>  
  
 <span data-ttu-id="26312-104">Následující příklad ukazuje, jak vytvořit aplikaci, která volá uloženou proceduru v databázi serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="26312-104">The following example shows how to create an application that calls a stored procedure in a SQL Server database.</span></span> <span data-ttu-id="26312-105">Vzorek ukazuje, jak volat dvě různé uložené procedury v databázi.</span><span class="sxs-lookup"><span data-stu-id="26312-105">The sample shows how to call two different stored procedures in the database.</span></span> <span data-ttu-id="26312-106">Každý postup vrátí výsledky dotazu.</span><span class="sxs-lookup"><span data-stu-id="26312-106">Each procedure returns the results of a query.</span></span> <span data-ttu-id="26312-107">Jeden procedura používá vstupní parametry a další postup nepřijímá parametry.</span><span class="sxs-lookup"><span data-stu-id="26312-107">One procedure takes input parameters, and the other procedure does not take parameters.</span></span>  
  
 <span data-ttu-id="26312-108">V příkladech v tomto tématu se používá ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="26312-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="26312-109">Pokud tuto databázi na vašem vývojovém počítači nemáte, můžete si ho stáhnout z webu Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="26312-109">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="26312-110">Pokyny najdete v tématu [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="26312-110">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="26312-111">Chcete-li vytvořit připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="26312-111">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="26312-112">V sadě Visual Studio, otevřete **Průzkumníka serveru**/**Průzkumník databáze** kliknutím **Průzkumníka serveru**/**databáze Průzkumník** na **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="26312-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="26312-113">Klikněte pravým tlačítkem na **datová připojení** v **Průzkumníka serveru**/**Průzkumník databáze** a potom klikněte na tlačítko **přidat připojení**.</span><span class="sxs-lookup"><span data-stu-id="26312-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="26312-114">Zadejte platné připojení k ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="26312-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="26312-115">Chcete-li přidat projekt, který obsahuje souboru LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="26312-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="26312-116">V sadě Visual Studio na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu**.</span><span class="sxs-lookup"><span data-stu-id="26312-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="26312-117">Výběr jazyka Visual Basic **formulářová aplikace Windows** jako typ projektu.</span><span class="sxs-lookup"><span data-stu-id="26312-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="26312-118">Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="26312-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="26312-119">Vyberte **třídy LINQ to SQL** šablony položky.</span><span class="sxs-lookup"><span data-stu-id="26312-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="26312-120">Pojmenujte soubor `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="26312-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="26312-121">Klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="26312-121">Click **Add**.</span></span> <span data-ttu-id="26312-122">Návrhář relací objektů (O/R Designer), je otevřené northwind.dbml souboru.</span><span class="sxs-lookup"><span data-stu-id="26312-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a><span data-ttu-id="26312-123">Chcete-li přidat úložné procedury do Návrháře relací objektů</span><span class="sxs-lookup"><span data-stu-id="26312-123">To add stored procedures to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="26312-124">V **Průzkumníka serveru**/**Průzkumník databáze**, rozbalte možnost připojení k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="26312-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="26312-125">Rozbalte **uložené procedury** složky.</span><span class="sxs-lookup"><span data-stu-id="26312-125">Expand the **Stored Procedures** folder.</span></span>  
  
     <span data-ttu-id="26312-126">Pokud jste zavřeli O/R Designer, můžete ho znovu otevřít poklikáním northwind.dbml soubor, který jste přidali dříve.</span><span class="sxs-lookup"><span data-stu-id="26312-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="26312-127">Klikněte na tlačítko **prodeje podle roku** uložené procedury a přetáhněte ho do pravého podokna návrháře.</span><span class="sxs-lookup"><span data-stu-id="26312-127">Click the **Sales by Year** stored procedure and drag it to the right pane of the designer.</span></span> <span data-ttu-id="26312-128">Klikněte na tlačítko **deset nejvíce nákladné produktů** uložené procedury, přetáhněte ho do pravého podokna návrháře.</span><span class="sxs-lookup"><span data-stu-id="26312-128">Click the **Ten Most Expensive Products** stored procedure drag it to the right pane of the designer.</span></span>  
  
3.  <span data-ttu-id="26312-129">Uložte změny a zavřete návrháře.</span><span class="sxs-lookup"><span data-stu-id="26312-129">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="26312-130">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="26312-130">Save your project.</span></span>  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a><span data-ttu-id="26312-131">Chcete-li přidat kód pro zobrazení výsledků uložených procedur</span><span class="sxs-lookup"><span data-stu-id="26312-131">To add code to display the results of the stored procedures</span></span>  
  
1.  <span data-ttu-id="26312-132">Z **nástrojů**, přetáhněte <xref:System.Windows.Forms.DataGridView> ovládacího prvku na výchozí formulář Windows pro váš projekt Form1.</span><span class="sxs-lookup"><span data-stu-id="26312-132">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="26312-133">Klikněte dvakrát na Form1 přidat kód pro jeho `Load` událostí.</span><span class="sxs-lookup"><span data-stu-id="26312-133">Double-click Form1 to add code to its `Load` event.</span></span>  
  
3.  <span data-ttu-id="26312-134">Když jste přidali do Návrháře relací objektů uložených procedur, přidá návrháře <xref:System.Data.Linq.DataContext> objektu pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="26312-134">When you added stored procedures to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="26312-135">Tento objekt obsahuje kód, který musí mít pro přístup k těmto postupy.</span><span class="sxs-lookup"><span data-stu-id="26312-135">This object contains the code that you must have to access those procedures.</span></span> <span data-ttu-id="26312-136"><xref:System.Data.Linq.DataContext> Objektu pro projekt je s názvem podle názvu souboru .dbml.</span><span class="sxs-lookup"><span data-stu-id="26312-136">The <xref:System.Data.Linq.DataContext> object for the project is named based on the name of the .dbml file.</span></span> <span data-ttu-id="26312-137">Pro tento projekt <xref:System.Data.Linq.DataContext> se nazývá `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="26312-137">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="26312-138">Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> v kódu a volání určené metody uloženou proceduru Návrháře relací objektů.</span><span class="sxs-lookup"><span data-stu-id="26312-138">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and call the stored procedure methods specified by the O/R Designer.</span></span> <span data-ttu-id="26312-139">K vytvoření vazby <xref:System.Windows.Forms.DataGridView> objektu, možná budete muset vynutit dotaz tak, aby okamžitě je spouštějte voláním <xref:System.Linq.Enumerable.ToList%2A> metodu na výsledky uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="26312-139">To bind to the <xref:System.Windows.Forms.DataGridView> object, you may have to force the query to execute immediately by calling the <xref:System.Linq.Enumerable.ToList%2A> method on the results of the stored procedure.</span></span>  
  
     <span data-ttu-id="26312-140">Přidejte následující kód, který `Load` události a volání buď uložené procedury jako metody pro datový kontext.</span><span class="sxs-lookup"><span data-stu-id="26312-140">Add the following code to the `Load` event to call either of the stored procedures exposed as methods for your data context.</span></span>  
  
     [!code-vb[VbLINQtoSQLHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#1)]  
    [!code-vb[VbLINQtoSQLHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#2)]  
  
4.  <span data-ttu-id="26312-141">Stisknutím klávesy F5 spusťte váš projekt a prohlédněte si výsledky.</span><span class="sxs-lookup"><span data-stu-id="26312-141">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26312-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="26312-142">See also</span></span>

- [<span data-ttu-id="26312-143">LINQ</span><span class="sxs-lookup"><span data-stu-id="26312-143">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="26312-144">Dotazy</span><span class="sxs-lookup"><span data-stu-id="26312-144">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="26312-145">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="26312-145">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="26312-146">Metody DataContext (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="26312-146">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="26312-147">Postupy: Přiřazení uložených procedur za účelem aktualizací, vkládání a odstraňování (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="26312-147">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
