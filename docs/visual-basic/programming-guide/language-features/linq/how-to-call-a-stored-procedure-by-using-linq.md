---
title: "Postupy: Volání uložené procedury pomocí LINQ (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7fb2d119d56cb643ebc1b43894952a6323e5e06e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a><span data-ttu-id="7c80a-102">Postupy: Volání uložené procedury pomocí LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c80a-102">How to: Call a Stored Procedure by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="7c80a-103">Language-Integrated Query (LINQ) usnadňuje přístup k informacím databáze, včetně databázové objekty, jako uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="7c80a-103">Language-Integrated Query (LINQ) makes it easy to access database information, including database objects such as stored procedures.</span></span>  
  
 <span data-ttu-id="7c80a-104">Následující příklad ukazuje, jak vytvořit aplikaci, která volá uloženou proceduru v databázi systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7c80a-104">The following example shows how to create an application that calls a stored procedure in a SQL Server database.</span></span> <span data-ttu-id="7c80a-105">Ukázka ukazuje způsob volání dva různé postupy uložené v databázi.</span><span class="sxs-lookup"><span data-stu-id="7c80a-105">The sample shows how to call two different stored procedures in the database.</span></span> <span data-ttu-id="7c80a-106">Každý postup vrátí výsledky dotazu.</span><span class="sxs-lookup"><span data-stu-id="7c80a-106">Each procedure returns the results of a query.</span></span> <span data-ttu-id="7c80a-107">Jeden procedura používá vstupní parametry a další postup nemusí provádět žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="7c80a-107">One procedure takes input parameters, and the other procedure does not take parameters.</span></span>  
  
 <span data-ttu-id="7c80a-108">V příkladech v tomto tématu použijte ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="7c80a-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="7c80a-109">Pokud ve svém vývojovém počítači nemáte ukázková databáze Northwind, si můžete stáhnout z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) webu.</span><span class="sxs-lookup"><span data-stu-id="7c80a-109">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="7c80a-110">Pokyny najdete v tématu [stažení ukázkové databáze](https://msdn.microsoft.com/library/bb399411).</span><span class="sxs-lookup"><span data-stu-id="7c80a-110">For instructions, see [Downloading Sample Databases](https://msdn.microsoft.com/library/bb399411).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="7c80a-111">Chcete-li vytvořit připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="7c80a-111">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="7c80a-112">V sadě Visual Studio otevřete **Průzkumníka serveru**/**Průzkumník databáze** kliknutím **Průzkumníka serveru**/**databáze Průzkumník** na **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="7c80a-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="7c80a-113">Klikněte pravým tlačítkem na **připojení dat** v **Průzkumníka serveru**/**Průzkumník databáze** a pak klikněte na **přidat připojení**.</span><span class="sxs-lookup"><span data-stu-id="7c80a-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="7c80a-114">Zadejte platné připojení k ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="7c80a-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="7c80a-115">Chcete-li přidat projekt, který obsahuje LINQ to SQL souboru</span><span class="sxs-lookup"><span data-stu-id="7c80a-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="7c80a-116">V sadě Visual Studio na **soubor** nabídky, přejděte na příkaz **nový** a pak klikněte na **projektu**.</span><span class="sxs-lookup"><span data-stu-id="7c80a-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="7c80a-117">Vyberte jazyka Visual Basic **formulářové aplikace Windows** jako typ projektu.</span><span class="sxs-lookup"><span data-stu-id="7c80a-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="7c80a-118">Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="7c80a-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="7c80a-119">Vyberte **třídy LINQ to SQL** šablony položky.</span><span class="sxs-lookup"><span data-stu-id="7c80a-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="7c80a-120">Název souboru `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="7c80a-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="7c80a-121">Klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="7c80a-121">Click **Add**.</span></span> <span data-ttu-id="7c80a-122">Návrhář relací objektů (Návrhář relací objektů), je otevřené northwind.dbml souboru.</span><span class="sxs-lookup"><span data-stu-id="7c80a-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a><span data-ttu-id="7c80a-123">Chcete-li přidat uložené procedury pro Návrhář relací objektů</span><span class="sxs-lookup"><span data-stu-id="7c80a-123">To add stored procedures to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="7c80a-124">V **Průzkumníka serveru**/**Průzkumník databáze**, rozbalte možnost připojení k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="7c80a-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="7c80a-125">Rozbalte **uložené procedury** složky.</span><span class="sxs-lookup"><span data-stu-id="7c80a-125">Expand the **Stored Procedures** folder.</span></span>  
  
     <span data-ttu-id="7c80a-126">Pokud jste zavřeli Návrhář relací objektů, můžete ho znovu otevřít dvojitým kliknutím na soubor northwind.dbml, které jste přidali dříve.</span><span class="sxs-lookup"><span data-stu-id="7c80a-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="7c80a-127">Klikněte **prodeje podle roku** uložené procedury a přetáhněte ji do pravého podokna návrháře.</span><span class="sxs-lookup"><span data-stu-id="7c80a-127">Click the **Sales by Year** stored procedure and drag it to the right pane of the designer.</span></span> <span data-ttu-id="7c80a-128">Klikněte **deset nejvíce nákladné produkty** uložené procedury, přetáhněte ji do pravého podokna návrháře.</span><span class="sxs-lookup"><span data-stu-id="7c80a-128">Click the **Ten Most Expensive Products** stored procedure drag it to the right pane of the designer.</span></span>  
  
3.  <span data-ttu-id="7c80a-129">Uložte změny a zavřít návrháře.</span><span class="sxs-lookup"><span data-stu-id="7c80a-129">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="7c80a-130">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="7c80a-130">Save your project.</span></span>  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a><span data-ttu-id="7c80a-131">Chcete-li přidat kód, který zobrazí výsledky uložené procedury</span><span class="sxs-lookup"><span data-stu-id="7c80a-131">To add code to display the results of the stored procedures</span></span>  
  
1.  <span data-ttu-id="7c80a-132">Z **sada nástrojů**, přetáhněte ji <xref:System.Windows.Forms.DataGridView> na výchozí formuláře Windows pro svůj projekt Form1 ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="7c80a-132">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="7c80a-133">Dvakrát klikněte na Form1 přidání kódu k jeho `Load` událostí.</span><span class="sxs-lookup"><span data-stu-id="7c80a-133">Double-click Form1 to add code to its `Load` event.</span></span>  
  
3.  <span data-ttu-id="7c80a-134">Pokud jste přidali uložené procedury Návrhář relací objektů, návrháře přidat <xref:System.Data.Linq.DataContext> objekt pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="7c80a-134">When you added stored procedures to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="7c80a-135">Tento objekt obsahuje kód, který musí mít přístup k tyto postupy.</span><span class="sxs-lookup"><span data-stu-id="7c80a-135">This object contains the code that you must have to access those procedures.</span></span> <span data-ttu-id="7c80a-136"><xref:System.Data.Linq.DataContext> Objektu pro název projektu na základě názvu souboru DBML.</span><span class="sxs-lookup"><span data-stu-id="7c80a-136">The <xref:System.Data.Linq.DataContext> object for the project is named based on the name of the .dbml file.</span></span> <span data-ttu-id="7c80a-137">Pro tento projekt <xref:System.Data.Linq.DataContext> názvem objektu `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="7c80a-137">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="7c80a-138">Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> v kódu a volání metody uložené procedury určeného Návrhář relací objektů.</span><span class="sxs-lookup"><span data-stu-id="7c80a-138">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and call the stored procedure methods specified by the O/R Designer.</span></span> <span data-ttu-id="7c80a-139">K vytvoření vazby <xref:System.Windows.Forms.DataGridView> objektu, možná budete muset vynutit dotaz provést okamžitě voláním <xref:System.Linq.Enumerable.ToList%2A> metodu výsledky uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="7c80a-139">To bind to the <xref:System.Windows.Forms.DataGridView> object, you may have to force the query to execute immediately by calling the <xref:System.Linq.Enumerable.ToList%2A> method on the results of the stored procedure.</span></span>  
  
     <span data-ttu-id="7c80a-140">Přidejte následující kód, který `Load` události zavolat buď uložené procedury, které jsou zveřejněné jako metody pro vaše data kontextu.</span><span class="sxs-lookup"><span data-stu-id="7c80a-140">Add the following code to the `Load` event to call either of the stored procedures exposed as methods for your data context.</span></span>  
  
     [!code-vb[VbLINQtoSQLHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_1.vb)]  
    [!code-vb[VbLINQtoSQLHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_2.vb)]  
  
4.  <span data-ttu-id="7c80a-141">Stisknutím klávesy F5 spusťte projekt a zobrazit výsledky.</span><span class="sxs-lookup"><span data-stu-id="7c80a-141">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c80a-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c80a-142">See Also</span></span>  
 [<span data-ttu-id="7c80a-143">LINQ</span><span class="sxs-lookup"><span data-stu-id="7c80a-143">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="7c80a-144">Dotazy</span><span class="sxs-lookup"><span data-stu-id="7c80a-144">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="7c80a-145">Technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="7c80a-145">LINQ to SQL</span></span>](https://msdn.microsoft.com/library/bb386976)  
 [<span data-ttu-id="7c80a-146">Metody DataContext (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="7c80a-146">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [<span data-ttu-id="7c80a-147">Postupy: přiřazení uložené procedury k provedení aktualizací, vložení a odstranění (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="7c80a-147">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)
