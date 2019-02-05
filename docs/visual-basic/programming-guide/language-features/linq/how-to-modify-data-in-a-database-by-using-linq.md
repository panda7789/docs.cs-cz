---
title: 'Postupy: Změna dat v databázi pomocí LINQ (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inserting rows [LINQ to SQL]
- deleting rows [LINQ to SQL]
- updating rows [LINQ to SQL]
- inserting data [Visual Basic]
- deleting data
- data [Visual Basic], updating
- updating data [LINQ]
- queries [LINQ in Visual Basic], data changes in database
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: cf52635f-0c1b-46c3-aff1-bdf181cf19b1
ms.openlocfilehash: 88597e5cfa1db46e147b829c8ffc634697cecc7e
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/05/2019
ms.locfileid: "55739485"
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a><span data-ttu-id="69219-102">Postupy: Změna dat v databázi pomocí LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69219-102">How to: Modify Data in a Database by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="69219-103">Language-Integrated Query (LINQ) dotazy umožňují snadno přistupovat k informací o databázi a hodnot v databázi.</span><span class="sxs-lookup"><span data-stu-id="69219-103">Language-Integrated Query (LINQ) queries make it easy to access database information and modify values in the database.</span></span>  
  
 <span data-ttu-id="69219-104">Následující příklad ukazuje, jak vytvořit novou aplikaci, která načte a informací o aktualizacích v databázi serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="69219-104">The following example shows how to create a new application that retrieves and updates information in a SQL Server database.</span></span>  
  
 <span data-ttu-id="69219-105">V příkladech v tomto tématu se používá ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="69219-105">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="69219-106">Pokud tuto databázi na vašem vývojovém počítači nemáte, můžete si ho stáhnout z webu Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="69219-106">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="69219-107">Pokyny najdete v tématu [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="69219-107">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="69219-108">Chcete-li vytvořit připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="69219-108">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="69219-109">V sadě Visual Studio, otevřete **Průzkumníka serveru**/**Průzkumník databáze** kliknutím **zobrazení** nabídky a pak vyberte **Průzkumníka serveru** / **Databázového Průzkumníka**.</span><span class="sxs-lookup"><span data-stu-id="69219-109">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking the **View** menu, and then select **Server Explorer**/**Database Explorer**.</span></span>  
  
2.  <span data-ttu-id="69219-110">Klikněte pravým tlačítkem na **datová připojení** v **Průzkumníka serveru**/**Průzkumník databáze**a klikněte na tlačítko **přidat připojení**.</span><span class="sxs-lookup"><span data-stu-id="69219-110">Right-click **Data Connections** in **Server Explorer**/**Database Explorer**, and click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="69219-111">Zadejte platné připojení k ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="69219-111">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-with-a-linq-to-sql-file"></a><span data-ttu-id="69219-112">Přidání projektu s LINQ na soubor SQL</span><span class="sxs-lookup"><span data-stu-id="69219-112">To add a Project with a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="69219-113">V sadě Visual Studio na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu**.</span><span class="sxs-lookup"><span data-stu-id="69219-113">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="69219-114">Výběr jazyka Visual Basic **formulářová aplikace Windows** jako typ projektu.</span><span class="sxs-lookup"><span data-stu-id="69219-114">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="69219-115">Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="69219-115">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="69219-116">Vyberte **třídy LINQ to SQL** šablony položky.</span><span class="sxs-lookup"><span data-stu-id="69219-116">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="69219-117">Pojmenujte soubor `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="69219-117">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="69219-118">Klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="69219-118">Click **Add**.</span></span> <span data-ttu-id="69219-119">Návrhář relací objektů (O/R Designer), je otevřené `northwind.dbml` souboru.</span><span class="sxs-lookup"><span data-stu-id="69219-119">The Object Relational Designer (O/R Designer) is opened for the `northwind.dbml` file.</span></span>  
  
### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a><span data-ttu-id="69219-120">Chcete-li přidat tabulky k dotazování a modifikaci do návrháře</span><span class="sxs-lookup"><span data-stu-id="69219-120">To add tables to query and modify to the designer</span></span>  
  
1.  <span data-ttu-id="69219-121">V **Průzkumníka serveru**/**Průzkumník databáze**, rozbalte možnost připojení k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="69219-121">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="69219-122">Rozbalte **tabulky** složky.</span><span class="sxs-lookup"><span data-stu-id="69219-122">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="69219-123">Pokud jste zavřeli O/R Designer, můžete znovu otevřít jej dvojitým kliknutím `northwind.dbml` soubor, který jste přidali dříve.</span><span class="sxs-lookup"><span data-stu-id="69219-123">If you have closed the O/R Designer, you can reopen it by double-clicking the `northwind.dbml` file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="69219-124">Klikněte na tabulce Zákazníci a přetáhněte ji do levého podokna v návrháři.</span><span class="sxs-lookup"><span data-stu-id="69219-124">Click the Customers table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="69219-125">Návrhář vytvoří nový objekt zákazníka pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="69219-125">The designer creates a new Customer object for your project.</span></span>  
  
3.  <span data-ttu-id="69219-126">Uložte změny a zavřete návrháře.</span><span class="sxs-lookup"><span data-stu-id="69219-126">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="69219-127">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="69219-127">Save your project.</span></span>  
  
### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a><span data-ttu-id="69219-128">Přidání kódu k úpravám databáze a zobrazení výsledků</span><span class="sxs-lookup"><span data-stu-id="69219-128">To add code to modify the database and display the results</span></span>  
  
1.  <span data-ttu-id="69219-129">Z **nástrojů**, přetáhněte <xref:System.Windows.Forms.DataGridView> ovládacího prvku na výchozí formulář Windows pro váš projekt Form1.</span><span class="sxs-lookup"><span data-stu-id="69219-129">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="69219-130">Při přidání tabulky do Návrháře relací objektů, přidá návrháře <xref:System.Data.Linq.DataContext> objektu do projektu.</span><span class="sxs-lookup"><span data-stu-id="69219-130">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="69219-131">Tento objekt obsahuje kód, který můžete použít pro přístup k tabulce Zákazníci.</span><span class="sxs-lookup"><span data-stu-id="69219-131">This object contains code that you can use to access the Customers table.</span></span> <span data-ttu-id="69219-132">Také obsahuje kód, který definuje místní objekt zákazníka a kolekci zákazníků pro tabulku.</span><span class="sxs-lookup"><span data-stu-id="69219-132">It also contains code that defines  a local Customer object and a Customers collection for the table.</span></span> <span data-ttu-id="69219-133"><xref:System.Data.Linq.DataContext> Objektu pro váš projekt je s názvem podle názvu souboru .dbml.</span><span class="sxs-lookup"><span data-stu-id="69219-133">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="69219-134">Pro tento projekt <xref:System.Data.Linq.DataContext> se nazývá `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="69219-134">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="69219-135">Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> objekt v kódu a dotazování a úprava zákazníkům kolekci specifikované souborem Návrháře relací objektů.</span><span class="sxs-lookup"><span data-stu-id="69219-135">You can create an instance of the <xref:System.Data.Linq.DataContext> object in your code and query and modify the Customers collection specified by the O/R Designer.</span></span> <span data-ttu-id="69219-136">Změny provedené ke kolekci zákazníků se neprojeví v databázi, dokud odeslání je voláním <xref:System.Data.Linq.DataContext.SubmitChanges%2A> metodu <xref:System.Data.Linq.DataContext> objektu.</span><span class="sxs-lookup"><span data-stu-id="69219-136">Changes that you make to the Customers collection are not reflected in the database until you submit them by calling the <xref:System.Data.Linq.DataContext.SubmitChanges%2A> method of the <xref:System.Data.Linq.DataContext> object.</span></span>  
  
     <span data-ttu-id="69219-137">Klikněte dvakrát na Windows formuláři Form1, přidat kód pro <xref:System.Windows.Forms.Form.Load> událost dotaz Zákazníci tabulku, která je vystavena jako vlastnost vaše <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="69219-137">Double-click the Windows Form, Form1, to add code to the <xref:System.Windows.Forms.Form.Load> event to query the Customers table that is exposed as a property of your <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="69219-138">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="69219-138">Add the following code:</span></span>  
  
    ```vb  
    Private db As northwindDataContext  
  
    Private Sub Form1_Load(ByVal sender As System.Object,   
                           ByVal e As System.EventArgs  
                          ) Handles MyBase.Load  
      db = New northwindDataContext()  
  
      RefreshData()  
    End Sub  
  
    Private Sub RefreshData()  
      Dim customers = From cust In db.Customers   
                      Where cust.City(0) = "W"   
                      Select cust  
  
      DataGridView1.DataSource = customers  
    End Sub  
    ```  
  
3.  <span data-ttu-id="69219-139">Z **nástrojů**, přetáhněte tři <xref:System.Windows.Forms.Button> ovládací prvky na formuláři.</span><span class="sxs-lookup"><span data-stu-id="69219-139">From the **Toolbox**, drag three <xref:System.Windows.Forms.Button> controls onto the form.</span></span> <span data-ttu-id="69219-140">Vyberte první `Button` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="69219-140">Select the first `Button` control.</span></span> <span data-ttu-id="69219-141">V **vlastnosti** okno, nastaveno `Name` z `Button` ovládací prvek `AddButton` a `Text` k `Add`.</span><span class="sxs-lookup"><span data-stu-id="69219-141">In the **Properties** window, set the `Name` of the `Button` control to `AddButton` and the `Text` to `Add`.</span></span> <span data-ttu-id="69219-142">Vyberte druhé tlačítko a nastavte `Name` vlastnost `UpdateButton` a `Text` vlastnost `Update`.</span><span class="sxs-lookup"><span data-stu-id="69219-142">Select the second button and set the `Name` property to `UpdateButton` and the `Text` property to `Update`.</span></span> <span data-ttu-id="69219-143">Vyberte třetí tlačítko a nastavte `Name` vlastnost `DeleteButton` a `Text` vlastnost `Delete`.</span><span class="sxs-lookup"><span data-stu-id="69219-143">Select the third button and set the `Name` property to `DeleteButton` and the `Text` property to `Delete`.</span></span>  
  
4.  <span data-ttu-id="69219-144">Dvakrát klikněte **přidat** tlačítko Přidat kód pro jeho `Click` událostí.</span><span class="sxs-lookup"><span data-stu-id="69219-144">Double-click the **Add** button to add code to its `Click` event.</span></span> <span data-ttu-id="69219-145">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="69219-145">Add the following code:</span></span>  
  
    ```vb  
    Private Sub AddButton_Click(ByVal sender As System.Object,   
                                ByVal e As System.EventArgs  
                               ) Handles AddButton.Click  
      Dim cust As New Customer With {   
        .City = "Wellington",   
        .CompanyName = "Blue Yonder Airlines",   
        .ContactName = "Jill Frank",   
        .Country = "New Zealand",   
        .CustomerID = "JILLF"}  
  
      db.Customers.InsertOnSubmit(cust)  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
5.  <span data-ttu-id="69219-146">Dvakrát klikněte **aktualizace** tlačítko Přidat kód pro jeho `Click` událostí.</span><span class="sxs-lookup"><span data-stu-id="69219-146">Double-click the **Update** button to add code to its `Click` event.</span></span> <span data-ttu-id="69219-147">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="69219-147">Add the following code:</span></span>  
  
    ```vb  
    Private Sub UpdateButton_Click(ByVal sender As System.Object, _  
                                   ByVal e As System.EventArgs  
                                  ) Handles UpdateButton.Click  
      Dim updateCust = (From cust In db.Customers   
                        Where cust.CustomerID = "JILLF").ToList()(0)  
  
      updateCust.ContactName = "Jill Shrader"
      updateCust.Country = "Wales"
      updateCust.CompanyName = "Red Yonder Airlines"
      updateCust.City = "Cardiff"
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
6.  <span data-ttu-id="69219-148">Dvakrát klikněte **odstranit** tlačítko Přidat kód pro jeho `Click` událostí.</span><span class="sxs-lookup"><span data-stu-id="69219-148">Double-click the **Delete** button to add code to its `Click` event.</span></span> <span data-ttu-id="69219-149">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="69219-149">Add the following code:</span></span>  
  
    ```vb  
    Private Sub DeleteButton_Click(ByVal sender As System.Object, _  
                                   ByVal e As System.EventArgs  
                                  ) Handles DeleteButton.Click  
      Dim deleteCust = (From cust In db.Customers   
                        Where cust.CustomerID = "JILLF").ToList()(0)  
  
      db.Customers.DeleteOnSubmit(deleteCust)  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
7.  <span data-ttu-id="69219-150">Stisknutím klávesy F5 spusťte váš projekt.</span><span class="sxs-lookup"><span data-stu-id="69219-150">Press F5 to run your project.</span></span> <span data-ttu-id="69219-151">Klikněte na tlačítko **přidat** přidáte nový záznam.</span><span class="sxs-lookup"><span data-stu-id="69219-151">Click **Add** to add a new record.</span></span> <span data-ttu-id="69219-152">Klikněte na tlačítko **aktualizace** Upravit nový záznam.</span><span class="sxs-lookup"><span data-stu-id="69219-152">Click **Update** to modify the new record.</span></span> <span data-ttu-id="69219-153">Klikněte na tlačítko **odstranit** nový záznam odstranit.</span><span class="sxs-lookup"><span data-stu-id="69219-153">Click **Delete** to delete the new record.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69219-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69219-154">See also</span></span>
- [<span data-ttu-id="69219-155">LINQ</span><span class="sxs-lookup"><span data-stu-id="69219-155">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="69219-156">Dotazy</span><span class="sxs-lookup"><span data-stu-id="69219-156">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="69219-157">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="69219-157">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="69219-158">Metody DataContext (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="69219-158">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="69219-159">Postupy: Přiřazení uložených procedur za účelem aktualizací, vkládání a odstraňování (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="69219-159">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
