---
title: 'Postupy: Změna dat v databázi pomocí LINQ'
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
ms.openlocfilehash: eb076d9156fa66858f2e560422eef0dc61ba22b5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403482"
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a><span data-ttu-id="b2d74-102">Postupy: Změna dat v databázi pomocí LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2d74-102">How to: Modify Data in a Database by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="b2d74-103">Dotazy LINQ (Language-Integrated Query) usnadňují přístup k informacím o databázi a upravují hodnoty v databázi.</span><span class="sxs-lookup"><span data-stu-id="b2d74-103">Language-Integrated Query (LINQ) queries make it easy to access database information and modify values in the database.</span></span>

<span data-ttu-id="b2d74-104">Následující příklad ukazuje, jak vytvořit novou aplikaci, která načte a aktualizuje informace v databázi SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b2d74-104">The following example shows how to create a new application that retrieves and updates information in a SQL Server database.</span></span>

<span data-ttu-id="b2d74-105">V příkladech v tomto tématu se používá ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="b2d74-105">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="b2d74-106">Pokud tuto databázi ve vývojovém počítači nemáte, můžete si ji stáhnout z webu Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="b2d74-106">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="b2d74-107">Pokyny najdete v tématu [stažení ukázkových databází](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="b2d74-107">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>

### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="b2d74-108">Vytvoření připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="b2d74-108">To create a connection to a database</span></span>

1. <span data-ttu-id="b2d74-109">V aplikaci Visual Studio otevřete **Průzkumník serveru** / **Průzkumník databáze** kliknutím na nabídku **zobrazení** a pak vyberte **Průzkumník serveru** / **Průzkumník databáze**.</span><span class="sxs-lookup"><span data-stu-id="b2d74-109">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking the **View** menu, and then select **Server Explorer**/**Database Explorer**.</span></span>

2. <span data-ttu-id="b2d74-110">Klikněte pravým tlačítkem na **datová připojení** v **Průzkumník serveru** / **Průzkumníku databáze**a klikněte na **Přidat připojení**.</span><span class="sxs-lookup"><span data-stu-id="b2d74-110">Right-click **Data Connections** in **Server Explorer**/**Database Explorer**, and click **Add Connection**.</span></span>

3. <span data-ttu-id="b2d74-111">Zadejte platné připojení k ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="b2d74-111">Specify a valid connection to the Northwind sample database.</span></span>

### <a name="to-add-a-project-with-a-linq-to-sql-file"></a><span data-ttu-id="b2d74-112">Přidání projektu se souborem LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b2d74-112">To add a Project with a LINQ to SQL file</span></span>

1. <span data-ttu-id="b2d74-113">V aplikaci Visual Studio v nabídce **soubor** přejděte na možnost **Nový** a poté klikněte na položku **projekt**.</span><span class="sxs-lookup"><span data-stu-id="b2d74-113">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="b2d74-114">Jako typ projektu vyberte Visual Basic **model Windows Forms aplikace** .</span><span class="sxs-lookup"><span data-stu-id="b2d74-114">Select Visual Basic **Windows Forms Application** as the project type.</span></span>

2. <span data-ttu-id="b2d74-115">V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="b2d74-115">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="b2d74-116">Vyberte šablonu položky **LINQ to SQL třídy** .</span><span class="sxs-lookup"><span data-stu-id="b2d74-116">Select the **LINQ to SQL Classes** item template.</span></span>

3. <span data-ttu-id="b2d74-117">Pojmenujte soubor `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="b2d74-117">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="b2d74-118">Klikněte na tlačítko **Add** (Přidat).</span><span class="sxs-lookup"><span data-stu-id="b2d74-118">Click **Add**.</span></span> <span data-ttu-id="b2d74-119">Pro soubor je otevřen Návrhář relací objektů (Návrhář O/R) `northwind.dbml` .</span><span class="sxs-lookup"><span data-stu-id="b2d74-119">The Object Relational Designer (O/R Designer) is opened for the `northwind.dbml` file.</span></span>

### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a><span data-ttu-id="b2d74-120">Přidání tabulek pro dotazování a úpravy v Návrháři</span><span class="sxs-lookup"><span data-stu-id="b2d74-120">To add tables to query and modify to the designer</span></span>

1. <span data-ttu-id="b2d74-121">V **Server Explorer** / **Průzkumníku Průzkumník serveru Database**rozbalte připojení k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="b2d74-121">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="b2d74-122">Rozbalte složku **tabulky** .</span><span class="sxs-lookup"><span data-stu-id="b2d74-122">Expand the **Tables** folder.</span></span>

     <span data-ttu-id="b2d74-123">Pokud jste návrháře pro/R zavřeli, můžete ho znovu otevřít dvojitým kliknutím na `northwind.dbml` soubor, který jste přidali dříve.</span><span class="sxs-lookup"><span data-stu-id="b2d74-123">If you have closed the O/R Designer, you can reopen it by double-clicking the `northwind.dbml` file that you added earlier.</span></span>

2. <span data-ttu-id="b2d74-124">Klikněte na tabulku Customers (zákazníci) a přetáhněte ji do levého podokna návrháře.</span><span class="sxs-lookup"><span data-stu-id="b2d74-124">Click the Customers table and drag it to the left pane of the designer.</span></span>

     <span data-ttu-id="b2d74-125">Návrhář vytvoří nový objekt zákazníka pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="b2d74-125">The designer creates a new Customer object for your project.</span></span>

3. <span data-ttu-id="b2d74-126">Uložte změny a zavřete návrháře.</span><span class="sxs-lookup"><span data-stu-id="b2d74-126">Save your changes and close the designer.</span></span>

4. <span data-ttu-id="b2d74-127">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="b2d74-127">Save your project.</span></span>

### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a><span data-ttu-id="b2d74-128">Přidání kódu pro úpravu databáze a zobrazení výsledků</span><span class="sxs-lookup"><span data-stu-id="b2d74-128">To add code to modify the database and display the results</span></span>

1. <span data-ttu-id="b2d74-129">Z **panelu nástrojů**přetáhněte <xref:System.Windows.Forms.DataGridView> ovládací prvek do výchozího formuláře Windows pro váš projekt, Form1.</span><span class="sxs-lookup"><span data-stu-id="b2d74-129">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>

2. <span data-ttu-id="b2d74-130">Když jste přidali tabulky do návrháře O/R, Návrhář přidal <xref:System.Data.Linq.DataContext> objekt do projektu.</span><span class="sxs-lookup"><span data-stu-id="b2d74-130">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="b2d74-131">Tento objekt obsahuje kód, který můžete použít pro přístup k tabulce Customers.</span><span class="sxs-lookup"><span data-stu-id="b2d74-131">This object contains code that you can use to access the Customers table.</span></span> <span data-ttu-id="b2d74-132">Obsahuje také kód, který definuje místní objekt zákazníka a kolekci Customers pro tabulku.</span><span class="sxs-lookup"><span data-stu-id="b2d74-132">It also contains code that defines  a local Customer object and a Customers collection for the table.</span></span> <span data-ttu-id="b2d74-133"><xref:System.Data.Linq.DataContext>Objekt pro projekt je pojmenován na základě názvu souboru. dbml.</span><span class="sxs-lookup"><span data-stu-id="b2d74-133">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="b2d74-134">Pro tento projekt <xref:System.Data.Linq.DataContext> je objekt pojmenován `northwindDataContext` .</span><span class="sxs-lookup"><span data-stu-id="b2d74-134">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>

     <span data-ttu-id="b2d74-135">Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> objektu v kódu a dotazovat a upravit kolekci Customers, kterou určuje Návrhář relací O/R.</span><span class="sxs-lookup"><span data-stu-id="b2d74-135">You can create an instance of the <xref:System.Data.Linq.DataContext> object in your code and query and modify the Customers collection specified by the O/R Designer.</span></span> <span data-ttu-id="b2d74-136">Změny, které provedete v kolekci Customers, se v databázi neprojeví, dokud je neodešlete voláním <xref:System.Data.Linq.DataContext.SubmitChanges%2A> metody <xref:System.Data.Linq.DataContext> objektu.</span><span class="sxs-lookup"><span data-stu-id="b2d74-136">Changes that you make to the Customers collection are not reflected in the database until you submit them by calling the <xref:System.Data.Linq.DataContext.SubmitChanges%2A> method of the <xref:System.Data.Linq.DataContext> object.</span></span>

     <span data-ttu-id="b2d74-137">Poklikejte na formulář Windows, Form1 a přidejte do události kód pro <xref:System.Windows.Forms.Form.Load> dotazování tabulky Customers, která je vystavena jako vlastnost vaší <xref:System.Data.Linq.DataContext> .</span><span class="sxs-lookup"><span data-stu-id="b2d74-137">Double-click the Windows Form, Form1, to add code to the <xref:System.Windows.Forms.Form.Load> event to query the Customers table that is exposed as a property of your <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="b2d74-138">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="b2d74-138">Add the following code:</span></span>

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

3. <span data-ttu-id="b2d74-139">Z **panelu nástrojů**přetáhněte do <xref:System.Windows.Forms.Button> formuláře tři ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="b2d74-139">From the **Toolbox**, drag three <xref:System.Windows.Forms.Button> controls onto the form.</span></span> <span data-ttu-id="b2d74-140">Vyberte první `Button` ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="b2d74-140">Select the first `Button` control.</span></span> <span data-ttu-id="b2d74-141">V okně **vlastnosti** nastavte `Name` `Button` ovládací prvek na `AddButton` a na `Text` `Add` .</span><span class="sxs-lookup"><span data-stu-id="b2d74-141">In the **Properties** window, set the `Name` of the `Button` control to `AddButton` and the `Text` to `Add`.</span></span> <span data-ttu-id="b2d74-142">Vyberte druhé tlačítko a nastavte `Name` vlastnost na hodnotu `UpdateButton` a vlastnost na `Text` `Update` .</span><span class="sxs-lookup"><span data-stu-id="b2d74-142">Select the second button and set the `Name` property to `UpdateButton` and the `Text` property to `Update`.</span></span> <span data-ttu-id="b2d74-143">Vyberte třetí tlačítko a nastavte `Name` vlastnost na hodnotu `DeleteButton` a `Text` vlastnost na hodnotu `Delete` .</span><span class="sxs-lookup"><span data-stu-id="b2d74-143">Select the third button and set the `Name` property to `DeleteButton` and the `Text` property to `Delete`.</span></span>

4. <span data-ttu-id="b2d74-144">Dvojím kliknutím na tlačítko **Přidat** přidejte kód k `Click` události.</span><span class="sxs-lookup"><span data-stu-id="b2d74-144">Double-click the **Add** button to add code to its `Click` event.</span></span> <span data-ttu-id="b2d74-145">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="b2d74-145">Add the following code:</span></span>

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

5. <span data-ttu-id="b2d74-146">Dvojím kliknutím na tlačítko **aktualizovat** přidejte kód k `Click` události.</span><span class="sxs-lookup"><span data-stu-id="b2d74-146">Double-click the **Update** button to add code to its `Click` event.</span></span> <span data-ttu-id="b2d74-147">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="b2d74-147">Add the following code:</span></span>

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

6. <span data-ttu-id="b2d74-148">Dvojím kliknutím na tlačítko **Odstranit** přidejte kód k `Click` události.</span><span class="sxs-lookup"><span data-stu-id="b2d74-148">Double-click the **Delete** button to add code to its `Click` event.</span></span> <span data-ttu-id="b2d74-149">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="b2d74-149">Add the following code:</span></span>

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

7. <span data-ttu-id="b2d74-150">Stisknutím klávesy F5 spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="b2d74-150">Press F5 to run your project.</span></span> <span data-ttu-id="b2d74-151">Kliknutím na tlačítko **Přidat** přidejte nový záznam.</span><span class="sxs-lookup"><span data-stu-id="b2d74-151">Click **Add** to add a new record.</span></span> <span data-ttu-id="b2d74-152">Kliknutím na **aktualizovat** upravíte nový záznam.</span><span class="sxs-lookup"><span data-stu-id="b2d74-152">Click **Update** to modify the new record.</span></span> <span data-ttu-id="b2d74-153">Kliknutím na **Odstranit** odstraňte nový záznam.</span><span class="sxs-lookup"><span data-stu-id="b2d74-153">Click **Delete** to delete the new record.</span></span>

## <a name="see-also"></a><span data-ttu-id="b2d74-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2d74-154">See also</span></span>

- [<span data-ttu-id="b2d74-155">LINQ</span><span class="sxs-lookup"><span data-stu-id="b2d74-155">LINQ</span></span>](index.md)
- [<span data-ttu-id="b2d74-156">Dotazy</span><span class="sxs-lookup"><span data-stu-id="b2d74-156">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="b2d74-157">Technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b2d74-157">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="b2d74-158">Metody DataContext (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="b2d74-158">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="b2d74-159">Postupy: Přiřazení uložených procedur za účelem aktualizací, vkládání a odstraňování (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="b2d74-159">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
