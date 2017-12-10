---
title: "Postupy: Změna dat v databázi pomocí LINQ (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 69e2fc7a6860ad2ff43742d37cd35671ebe35acf
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a><span data-ttu-id="1a4d7-102">Postupy: Změna dat v databázi pomocí LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1a4d7-102">How to: Modify Data in a Database by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="1a4d7-103">Language-Integrated Query (LINQ) dotazy usnadňují přístup k informacím databáze a upravte hodnoty v databázi.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-103">Language-Integrated Query (LINQ) queries make it easy to access database information and modify values in the database.</span></span>  
  
 <span data-ttu-id="1a4d7-104">Následující příklad ukazuje, jak vytvořit novou aplikaci, která načte a informace o aktualizacích v databázi systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-104">The following example shows how to create a new application that retrieves and updates information in a SQL Server database.</span></span>  
  
 <span data-ttu-id="1a4d7-105">V příkladech v tomto tématu použijte ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-105">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="1a4d7-106">Pokud ve svém vývojovém počítači nemáte ukázková databáze Northwind, si můžete stáhnout z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) webu.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-106">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="1a4d7-107">Pokyny najdete v tématu [stažení ukázkové databáze](../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="1a4d7-107">For instructions, see [Downloading Sample Databases](../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="1a4d7-108">Chcete-li vytvořit připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="1a4d7-108">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="1a4d7-109">V sadě Visual Studio otevřete **Průzkumníka serveru**/**Průzkumník databáze** kliknutím **zobrazení** nabídce a potom vyberte **Průzkumníka serveru** / **Databáze Explorer**.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-109">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking the **View** menu, and then select **Server Explorer**/**Database Explorer**.</span></span>  
  
2.  <span data-ttu-id="1a4d7-110">Klikněte pravým tlačítkem na **připojení dat** v **Průzkumníka serveru**/**Průzkumník databáze**a klikněte na tlačítko **přidat připojení**.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-110">Right-click **Data Connections** in **Server Explorer**/**Database Explorer**, and click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="1a4d7-111">Zadejte platné připojení k ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-111">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-with-a-linq-to-sql-file"></a><span data-ttu-id="1a4d7-112">Přidat k projektu s LINQ souboru SQL</span><span class="sxs-lookup"><span data-stu-id="1a4d7-112">To add a Project with a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="1a4d7-113">V sadě Visual Studio na **soubor** nabídky, přejděte na příkaz **nový** a pak klikněte na **projektu**.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-113">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="1a4d7-114">Vyberte jazyka Visual Basic **formulářové aplikace Windows** jako typ projektu.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-114">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="1a4d7-115">Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-115">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="1a4d7-116">Vyberte **třídy LINQ to SQL** šablony položky.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-116">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="1a4d7-117">Název souboru `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-117">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="1a4d7-118">Klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-118">Click **Add**.</span></span> <span data-ttu-id="1a4d7-119">Návrhář relací objektů (Návrhář relací objektů), je otevřené `northwind.dbml` souboru.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-119">The Object Relational Designer (O/R Designer) is opened for the `northwind.dbml` file.</span></span>  
  
### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a><span data-ttu-id="1a4d7-120">Chcete-li přidat tabulky pro dotazování a upravit návrháře</span><span class="sxs-lookup"><span data-stu-id="1a4d7-120">To add tables to query and modify to the designer</span></span>  
  
1.  <span data-ttu-id="1a4d7-121">V **Průzkumníka serveru**/**Průzkumník databáze**, rozbalte možnost připojení k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-121">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="1a4d7-122">Rozbalte **tabulky** složky.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-122">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="1a4d7-123">Pokud jste zavřeli Návrhář relací objektů, můžete ho znovu otevřít dvojitým kliknutím `northwind.dbml` soubor, který jste přidali dříve.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-123">If you have closed the O/R Designer, you can reopen it by double-clicking the `northwind.dbml` file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="1a4d7-124">Klikněte na tabulku zákazníků a přetáhněte ji do levého podokna návrháře.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-124">Click the Customers table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="1a4d7-125">Návrhář vytvoří nový objekt zákazníka pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-125">The designer creates a new Customer object for your project.</span></span>  
  
3.  <span data-ttu-id="1a4d7-126">Uložte změny a zavřít návrháře.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-126">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="1a4d7-127">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-127">Save your project.</span></span>  
  
### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a><span data-ttu-id="1a4d7-128">Přidání kódu k úpravě databáze a zobrazit výsledky</span><span class="sxs-lookup"><span data-stu-id="1a4d7-128">To add code to modify the database and display the results</span></span>  
  
1.  <span data-ttu-id="1a4d7-129">Z **sada nástrojů**, přetáhněte ji <xref:System.Windows.Forms.DataGridView> na výchozí formuláře Windows pro svůj projekt Form1 ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-129">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="1a4d7-130">Při přidání tabulky do Návrhář relací objektů návrháře přidat <xref:System.Data.Linq.DataContext> objektu do projektu.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-130">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="1a4d7-131">Tento objekt obsahuje kód, který můžete použít pro přístup k tabulce zákazníků.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-131">This object contains code that you can use to access the Customers table.</span></span> <span data-ttu-id="1a4d7-132">Také obsahuje kód, který definuje objekt místní zákazníka a kolekci zákazníci pro tabulku.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-132">It also contains code that defines  a local Customer object and a Customers collection for the table.</span></span> <span data-ttu-id="1a4d7-133"><xref:System.Data.Linq.DataContext> Objekt pro je s názvem projektu na základě názvu souboru DBML.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-133">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="1a4d7-134">Pro tento projekt <xref:System.Data.Linq.DataContext> názvem objektu `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-134">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="1a4d7-135">Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> objekt v kódu a dotazů a upravit kolekci zákazníkům určit Návrhář relací objektů.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-135">You can create an instance of the <xref:System.Data.Linq.DataContext> object in your code and query and modify the Customers collection specified by the O/R Designer.</span></span> <span data-ttu-id="1a4d7-136">Změny provedené ke kolekci zákazníků se neprojeví v databázi, dokud odeslání voláním <xref:System.Data.Linq.DataContext.SubmitChanges%2A> metodu <xref:System.Data.Linq.DataContext> objektu.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-136">Changes that you make to the Customers collection are not reflected in the database until you submit them by calling the <xref:System.Data.Linq.DataContext.SubmitChanges%2A> method of the <xref:System.Data.Linq.DataContext> object.</span></span>  
  
     <span data-ttu-id="1a4d7-137">Dvakrát klikněte na Windows formuláře, formulář1, přidejte kód, který <xref:System.Windows.Forms.Form.Load> událost, která má dotaz zákazníků tabulku, která je k dispozici jako vlastnost vaší <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-137">Double-click the Windows Form, Form1, to add code to the <xref:System.Windows.Forms.Form.Load> event to query the Customers table that is exposed as a property of your <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="1a4d7-138">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="1a4d7-138">Add the following code:</span></span>  
  
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
  
3.  <span data-ttu-id="1a4d7-139">Z **sada nástrojů**, přetáhněte tři <xref:System.Windows.Forms.Button> ovládací prvky na formuláři.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-139">From the **Toolbox**, drag three <xref:System.Windows.Forms.Button> controls onto the form.</span></span> <span data-ttu-id="1a4d7-140">Vyberte první `Button` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-140">Select the first `Button` control.</span></span> <span data-ttu-id="1a4d7-141">V **vlastnosti** nastavte `Name` z `Button` řídit k `AddButton` a `Text` k `Add`.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-141">In the **Properties** window, set the `Name` of the `Button` control to `AddButton` and the `Text` to `Add`.</span></span> <span data-ttu-id="1a4d7-142">Vyberte tlačítko druhý a nastavte `Name` vlastnost `UpdateButton` a `Text` vlastnost `Update`.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-142">Select the second button and set the `Name` property to `UpdateButton` and the `Text` property to `Update`.</span></span> <span data-ttu-id="1a4d7-143">Vyberte tlačítko třetí a nastavte `Name` vlastnost `DeleteButton` a `Text` vlastnost `Delete`.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-143">Select the third button and set the `Name` property to `DeleteButton` and the `Text` property to `Delete`.</span></span>  
  
4.  <span data-ttu-id="1a4d7-144">Dvakrát klikněte **přidat** tlačítko Přidat kód pro jeho `Click` událostí.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-144">Double-click the **Add** button to add code to its `Click` event.</span></span> <span data-ttu-id="1a4d7-145">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="1a4d7-145">Add the following code:</span></span>  
  
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
  
5.  <span data-ttu-id="1a4d7-146">Dvakrát klikněte **aktualizace** tlačítko Přidat kód pro jeho `Click` událostí.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-146">Double-click the **Update** button to add code to its `Click` event.</span></span> <span data-ttu-id="1a4d7-147">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="1a4d7-147">Add the following code:</span></span>  
  
    ```vb  
    Private Sub UpdateButton_Click(ByVal sender As System.Object, _  
                                   ByVal e As System.EventArgs  
                                  ) Handles UpdateButton.Click  
      Dim updateCust = (From cust In db.Customers   
                        Where cust.CustomerID = "JILLF").ToList()(0)  
  
      updateCust.ContactName = "Jill Shrader"  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
6.  <span data-ttu-id="1a4d7-148">Dvakrát klikněte **odstranit** tlačítko Přidat kód pro jeho `Click` událostí.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-148">Double-click the **Delete** button to add code to its `Click` event.</span></span> <span data-ttu-id="1a4d7-149">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="1a4d7-149">Add the following code:</span></span>  
  
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
  
7.  <span data-ttu-id="1a4d7-150">Stisknutím klávesy F5 spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-150">Press F5 to run your project.</span></span> <span data-ttu-id="1a4d7-151">Klikněte na tlačítko **přidat** přidat nový záznam.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-151">Click **Add** to add a new record.</span></span> <span data-ttu-id="1a4d7-152">Klikněte na tlačítko **aktualizace** nový záznam upravit.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-152">Click **Update** to modify the new record.</span></span> <span data-ttu-id="1a4d7-153">Klikněte na tlačítko **odstranit** odstranit novém záznamu.</span><span class="sxs-lookup"><span data-stu-id="1a4d7-153">Click **Delete** to delete the new record.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a4d7-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="1a4d7-154">See Also</span></span>  
 [<span data-ttu-id="1a4d7-155">LINQ</span><span class="sxs-lookup"><span data-stu-id="1a4d7-155">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="1a4d7-156">Dotazy</span><span class="sxs-lookup"><span data-stu-id="1a4d7-156">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="1a4d7-157">Technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="1a4d7-157">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="1a4d7-158">Metody DataContext (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="1a4d7-158">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [<span data-ttu-id="1a4d7-159">Postupy: přiřazení uložené procedury k provedení aktualizací, vložení a odstranění (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="1a4d7-159">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)
