---
title: 'Postupy: volání uložené procedury pomocí LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
ms.openlocfilehash: f91ccda1842887b3785ce304fd41bdd020a55479
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345024"
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a><span data-ttu-id="673fc-102">Postupy: Volání uložené procedury pomocí LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="673fc-102">How to: Call a Stored Procedure by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="673fc-103">LINQ (Language-Integrated Query) usnadňuje přístup k informacím o databázi, včetně databázových objektů, jako jsou například uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="673fc-103">Language-Integrated Query (LINQ) makes it easy to access database information, including database objects such as stored procedures.</span></span>  
  
 <span data-ttu-id="673fc-104">Následující příklad ukazuje, jak vytvořit aplikaci, která volá uloženou proceduru v databázi SQL Server.</span><span class="sxs-lookup"><span data-stu-id="673fc-104">The following example shows how to create an application that calls a stored procedure in a SQL Server database.</span></span> <span data-ttu-id="673fc-105">Ukázka ukazuje, jak volat dva různé uložené procedury v databázi.</span><span class="sxs-lookup"><span data-stu-id="673fc-105">The sample shows how to call two different stored procedures in the database.</span></span> <span data-ttu-id="673fc-106">Každý postup vrátí výsledky dotazu.</span><span class="sxs-lookup"><span data-stu-id="673fc-106">Each procedure returns the results of a query.</span></span> <span data-ttu-id="673fc-107">Jeden postup přebírá vstupní parametry a druhý postup nepřijímá parametry.</span><span class="sxs-lookup"><span data-stu-id="673fc-107">One procedure takes input parameters, and the other procedure does not take parameters.</span></span>  
  
 <span data-ttu-id="673fc-108">V příkladech v tomto tématu se používá ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="673fc-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="673fc-109">Pokud tuto databázi ve vývojovém počítači nemáte, můžete si ji stáhnout z webu Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="673fc-109">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="673fc-110">Pokyny najdete v tématu [stažení ukázkových databází](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="673fc-110">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="673fc-111">Vytvoření připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="673fc-111">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="673fc-112">V aplikaci Visual Studio otevřete **Průzkumník serveru**/**Database explorer** kliknutím na **Průzkumník serveru**/**Průzkumník databáze** v nabídce **zobrazení** .</span><span class="sxs-lookup"><span data-stu-id="673fc-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="673fc-113">Klikněte pravým tlačítkem na **datová připojení** v **Průzkumník serveru**/**Průzkumníku databáze** a pak klikněte na **Přidat připojení**.</span><span class="sxs-lookup"><span data-stu-id="673fc-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="673fc-114">Zadejte platné připojení k ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="673fc-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="673fc-115">Přidání projektu, který obsahuje soubor LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="673fc-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="673fc-116">V aplikaci Visual Studio v nabídce **soubor** přejděte na možnost **Nový** a poté klikněte na položku **projekt**.</span><span class="sxs-lookup"><span data-stu-id="673fc-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="673fc-117">Jako typ projektu vyberte Visual Basic **model Windows Forms aplikace** .</span><span class="sxs-lookup"><span data-stu-id="673fc-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="673fc-118">V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="673fc-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="673fc-119">Vyberte šablonu položky **LINQ to SQL třídy** .</span><span class="sxs-lookup"><span data-stu-id="673fc-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="673fc-120">Pojmenujte soubor `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="673fc-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="673fc-121">Klikněte na tlačítko **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="673fc-121">Click **Add**.</span></span> <span data-ttu-id="673fc-122">Pro soubor Northwind. dbml je otevřen Návrhář relací objektů (O/R Designer).</span><span class="sxs-lookup"><span data-stu-id="673fc-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a><span data-ttu-id="673fc-123">Přidání uložených procedur do návrháře relací výstupů</span><span class="sxs-lookup"><span data-stu-id="673fc-123">To add stored procedures to the O/R Designer</span></span>  
  
1. <span data-ttu-id="673fc-124">V **Průzkumník serveru**/**Průzkumníku databáze**rozbalte připojení k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="673fc-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="673fc-125">Rozbalte složku **uložené procedury** .</span><span class="sxs-lookup"><span data-stu-id="673fc-125">Expand the **Stored Procedures** folder.</span></span>  
  
     <span data-ttu-id="673fc-126">Pokud jste návrháře pro/R zavřeli, můžete ho znovu otevřít dvojitým kliknutím na soubor Northwind. dbml, který jste přidali dříve.</span><span class="sxs-lookup"><span data-stu-id="673fc-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="673fc-127">Klikněte na uloženou proceduru **prodej podle roku** a přetáhněte ji do pravého podokna návrháře.</span><span class="sxs-lookup"><span data-stu-id="673fc-127">Click the **Sales by Year** stored procedure and drag it to the right pane of the designer.</span></span> <span data-ttu-id="673fc-128">Klikněte na **desítkovou** uloženou proceduru, kterou si můžete přetáhnout do pravého podokna návrháře.</span><span class="sxs-lookup"><span data-stu-id="673fc-128">Click the **Ten Most Expensive Products** stored procedure drag it to the right pane of the designer.</span></span>  
  
3. <span data-ttu-id="673fc-129">Uložte změny a zavřete návrháře.</span><span class="sxs-lookup"><span data-stu-id="673fc-129">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="673fc-130">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="673fc-130">Save your project.</span></span>  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a><span data-ttu-id="673fc-131">Chcete-li přidat kód pro zobrazení výsledků uložených procedur</span><span class="sxs-lookup"><span data-stu-id="673fc-131">To add code to display the results of the stored procedures</span></span>  
  
1. <span data-ttu-id="673fc-132">Z **panelu nástrojů**přetáhněte ovládací prvek <xref:System.Windows.Forms.DataGridView> do výchozího formuláře Windows pro váš projekt, Form1.</span><span class="sxs-lookup"><span data-stu-id="673fc-132">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="673fc-133">Poklikejte na Form1 a přidejte do události `Load` kód.</span><span class="sxs-lookup"><span data-stu-id="673fc-133">Double-click Form1 to add code to its `Load` event.</span></span>  
  
3. <span data-ttu-id="673fc-134">Když jste přidali uložené procedury do návrháře O/R, Návrhář přidal objekt <xref:System.Data.Linq.DataContext> pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="673fc-134">When you added stored procedures to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="673fc-135">Tento objekt obsahuje kód, který musíte mít pro přístup k těmto postupům.</span><span class="sxs-lookup"><span data-stu-id="673fc-135">This object contains the code that you must have to access those procedures.</span></span> <span data-ttu-id="673fc-136">Objekt <xref:System.Data.Linq.DataContext> pro projekt je pojmenován na základě názvu souboru. dbml.</span><span class="sxs-lookup"><span data-stu-id="673fc-136">The <xref:System.Data.Linq.DataContext> object for the project is named based on the name of the .dbml file.</span></span> <span data-ttu-id="673fc-137">Pro tento projekt má objekt <xref:System.Data.Linq.DataContext> název `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="673fc-137">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="673fc-138">Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> v kódu a volat metody uložené procedury určené návrhářem O/R.</span><span class="sxs-lookup"><span data-stu-id="673fc-138">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and call the stored procedure methods specified by the O/R Designer.</span></span> <span data-ttu-id="673fc-139">Chcete-li vytvořit propojení s objektem <xref:System.Windows.Forms.DataGridView>, bude pravděpodobně nutné vynutit okamžité provedení dotazu voláním metody <xref:System.Linq.Enumerable.ToList%2A> u výsledků uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="673fc-139">To bind to the <xref:System.Windows.Forms.DataGridView> object, you may have to force the query to execute immediately by calling the <xref:System.Linq.Enumerable.ToList%2A> method on the results of the stored procedure.</span></span>  
  
     <span data-ttu-id="673fc-140">Do události `Load` přidejte následující kód, který zavolá jeden z uložených procedur vystavených jako metody pro váš datový kontext.</span><span class="sxs-lookup"><span data-stu-id="673fc-140">Add the following code to the `Load` event to call either of the stored procedures exposed as methods for your data context.</span></span>  
  
     [!code-vb[VbLINQtoSQLHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#1)]  
    [!code-vb[VbLINQtoSQLHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#2)]  
  
4. <span data-ttu-id="673fc-141">Stisknutím klávesy F5 spusťte projekt a zobrazte výsledky.</span><span class="sxs-lookup"><span data-stu-id="673fc-141">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="673fc-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="673fc-142">See also</span></span>

- [<span data-ttu-id="673fc-143">LINQ</span><span class="sxs-lookup"><span data-stu-id="673fc-143">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="673fc-144">Dotazy</span><span class="sxs-lookup"><span data-stu-id="673fc-144">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="673fc-145">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="673fc-145">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="673fc-146">Metody DataContext (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="673fc-146">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="673fc-147">Postupy: Přiřazení uložených procedur za účelem aktualizací, vkládání a odstraňování (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="673fc-147">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
