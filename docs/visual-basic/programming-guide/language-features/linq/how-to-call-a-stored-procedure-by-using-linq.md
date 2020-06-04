---
title: 'Postupy: Volání uložené procedury pomocí LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
ms.openlocfilehash: b451642a16f36c4f7fd19c853fdfd2282f5bede5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405027"
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a><span data-ttu-id="341a4-102">Postupy: Volání uložené procedury pomocí LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="341a4-102">How to: Call a Stored Procedure by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="341a4-103">LINQ (Language-Integrated Query) usnadňuje přístup k informacím o databázi, včetně databázových objektů, jako jsou například uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="341a4-103">Language-Integrated Query (LINQ) makes it easy to access database information, including database objects such as stored procedures.</span></span>  
  
 <span data-ttu-id="341a4-104">Následující příklad ukazuje, jak vytvořit aplikaci, která volá uloženou proceduru v databázi SQL Server.</span><span class="sxs-lookup"><span data-stu-id="341a4-104">The following example shows how to create an application that calls a stored procedure in a SQL Server database.</span></span> <span data-ttu-id="341a4-105">Ukázka ukazuje, jak volat dva různé uložené procedury v databázi.</span><span class="sxs-lookup"><span data-stu-id="341a4-105">The sample shows how to call two different stored procedures in the database.</span></span> <span data-ttu-id="341a4-106">Každý postup vrátí výsledky dotazu.</span><span class="sxs-lookup"><span data-stu-id="341a4-106">Each procedure returns the results of a query.</span></span> <span data-ttu-id="341a4-107">Jeden postup přebírá vstupní parametry a druhý postup nepřijímá parametry.</span><span class="sxs-lookup"><span data-stu-id="341a4-107">One procedure takes input parameters, and the other procedure does not take parameters.</span></span>  
  
 <span data-ttu-id="341a4-108">V příkladech v tomto tématu se používá ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="341a4-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="341a4-109">Pokud tuto databázi ve vývojovém počítači nemáte, můžete si ji stáhnout z webu Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="341a4-109">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="341a4-110">Pokyny najdete v tématu [stažení ukázkových databází](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="341a4-110">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="341a4-111">Vytvoření připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="341a4-111">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="341a4-112">V aplikaci Visual Studio otevřete **Průzkumník serveru** / **Průzkumník databáze** kliknutím na **Průzkumník serveru** / **Průzkumník databáze** v nabídce **zobrazení** .</span><span class="sxs-lookup"><span data-stu-id="341a4-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="341a4-113">Klikněte pravým tlačítkem na **datová připojení** v **Průzkumník serveru** / **Průzkumníku databáze** a pak klikněte na **Přidat připojení**.</span><span class="sxs-lookup"><span data-stu-id="341a4-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="341a4-114">Zadejte platné připojení k ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="341a4-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="341a4-115">Přidání projektu, který obsahuje soubor LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="341a4-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="341a4-116">V aplikaci Visual Studio v nabídce **soubor** přejděte na možnost **Nový** a poté klikněte na položku **projekt**.</span><span class="sxs-lookup"><span data-stu-id="341a4-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="341a4-117">Jako typ projektu vyberte Visual Basic **model Windows Forms aplikace** .</span><span class="sxs-lookup"><span data-stu-id="341a4-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="341a4-118">V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="341a4-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="341a4-119">Vyberte šablonu položky **LINQ to SQL třídy** .</span><span class="sxs-lookup"><span data-stu-id="341a4-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="341a4-120">Pojmenujte soubor `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="341a4-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="341a4-121">Klikněte na tlačítko **Add** (Přidat).</span><span class="sxs-lookup"><span data-stu-id="341a4-121">Click **Add**.</span></span> <span data-ttu-id="341a4-122">Pro soubor Northwind. dbml je otevřen Návrhář relací objektů (O/R Designer).</span><span class="sxs-lookup"><span data-stu-id="341a4-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a><span data-ttu-id="341a4-123">Přidání uložených procedur do návrháře relací výstupů</span><span class="sxs-lookup"><span data-stu-id="341a4-123">To add stored procedures to the O/R Designer</span></span>  
  
1. <span data-ttu-id="341a4-124">V **Server Explorer** / **Průzkumníku Průzkumník serveru Database**rozbalte připojení k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="341a4-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="341a4-125">Rozbalte složku **uložené procedury** .</span><span class="sxs-lookup"><span data-stu-id="341a4-125">Expand the **Stored Procedures** folder.</span></span>  
  
     <span data-ttu-id="341a4-126">Pokud jste návrháře pro/R zavřeli, můžete ho znovu otevřít dvojitým kliknutím na soubor Northwind. dbml, který jste přidali dříve.</span><span class="sxs-lookup"><span data-stu-id="341a4-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="341a4-127">Klikněte na uloženou proceduru **prodej podle roku** a přetáhněte ji do pravého podokna návrháře.</span><span class="sxs-lookup"><span data-stu-id="341a4-127">Click the **Sales by Year** stored procedure and drag it to the right pane of the designer.</span></span> <span data-ttu-id="341a4-128">Klikněte na **desítkovou** uloženou proceduru, kterou si můžete přetáhnout do pravého podokna návrháře.</span><span class="sxs-lookup"><span data-stu-id="341a4-128">Click the **Ten Most Expensive Products** stored procedure drag it to the right pane of the designer.</span></span>  
  
3. <span data-ttu-id="341a4-129">Uložte změny a zavřete návrháře.</span><span class="sxs-lookup"><span data-stu-id="341a4-129">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="341a4-130">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="341a4-130">Save your project.</span></span>  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a><span data-ttu-id="341a4-131">Chcete-li přidat kód pro zobrazení výsledků uložených procedur</span><span class="sxs-lookup"><span data-stu-id="341a4-131">To add code to display the results of the stored procedures</span></span>  
  
1. <span data-ttu-id="341a4-132">Z **panelu nástrojů**přetáhněte <xref:System.Windows.Forms.DataGridView> ovládací prvek do výchozího formuláře Windows pro váš projekt, Form1.</span><span class="sxs-lookup"><span data-stu-id="341a4-132">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="341a4-133">Poklikejte na Form1 a přidejte do jeho události kód `Load` .</span><span class="sxs-lookup"><span data-stu-id="341a4-133">Double-click Form1 to add code to its `Load` event.</span></span>  
  
3. <span data-ttu-id="341a4-134">Když jste přidali uložené procedury do návrháře O/R, Návrhář přidal <xref:System.Data.Linq.DataContext> objekt pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="341a4-134">When you added stored procedures to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="341a4-135">Tento objekt obsahuje kód, který musíte mít pro přístup k těmto postupům.</span><span class="sxs-lookup"><span data-stu-id="341a4-135">This object contains the code that you must have to access those procedures.</span></span> <span data-ttu-id="341a4-136"><xref:System.Data.Linq.DataContext>Objekt pro projekt je pojmenován na základě názvu souboru. dbml.</span><span class="sxs-lookup"><span data-stu-id="341a4-136">The <xref:System.Data.Linq.DataContext> object for the project is named based on the name of the .dbml file.</span></span> <span data-ttu-id="341a4-137">Pro tento projekt <xref:System.Data.Linq.DataContext> je objekt pojmenován `northwindDataContext` .</span><span class="sxs-lookup"><span data-stu-id="341a4-137">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="341a4-138">Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> v kódu a volat metody uložené procedury určené návrhářem o/R.</span><span class="sxs-lookup"><span data-stu-id="341a4-138">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and call the stored procedure methods specified by the O/R Designer.</span></span> <span data-ttu-id="341a4-139">Chcete-li vytvořit svázání s <xref:System.Windows.Forms.DataGridView> objektem, může být nutné vynutit okamžité provedení dotazu voláním <xref:System.Linq.Enumerable.ToList%2A> metody u výsledků uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="341a4-139">To bind to the <xref:System.Windows.Forms.DataGridView> object, you may have to force the query to execute immediately by calling the <xref:System.Linq.Enumerable.ToList%2A> method on the results of the stored procedure.</span></span>  
  
     <span data-ttu-id="341a4-140">Přidejte následující kód do `Load` události pro volání některého z uložených procedur vystavených jako metody pro váš kontext dat.</span><span class="sxs-lookup"><span data-stu-id="341a4-140">Add the following code to the `Load` event to call either of the stored procedures exposed as methods for your data context.</span></span>  
  
     [!code-vb[VbLINQtoSQLHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#1)]  
    [!code-vb[VbLINQtoSQLHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#2)]  
  
4. <span data-ttu-id="341a4-141">Stisknutím klávesy F5 spusťte projekt a zobrazte výsledky.</span><span class="sxs-lookup"><span data-stu-id="341a4-141">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="341a4-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="341a4-142">See also</span></span>

- [<span data-ttu-id="341a4-143">LINQ</span><span class="sxs-lookup"><span data-stu-id="341a4-143">LINQ</span></span>](index.md)
- [<span data-ttu-id="341a4-144">Dotazy</span><span class="sxs-lookup"><span data-stu-id="341a4-144">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="341a4-145">Technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="341a4-145">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="341a4-146">Metody DataContext (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="341a4-146">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="341a4-147">Postupy: Přiřazení uložených procedur za účelem aktualizací, vkládání a odstraňování (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="341a4-147">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
