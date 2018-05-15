---
title: Metoda Load
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: 04defffc724875e691fd7b87331c28e6b6c0cd28
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="the-load-method"></a><span data-ttu-id="8f2b1-102">Metoda Load</span><span class="sxs-lookup"><span data-stu-id="8f2b1-102">The Load Method</span></span>
<span data-ttu-id="8f2b1-103">Můžete použít <xref:System.Data.DataTable.Load%2A> metoda načíst <xref:System.Data.DataTable> s řádky ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="8f2b1-103">You can use the <xref:System.Data.DataTable.Load%2A> method to load a <xref:System.Data.DataTable> with rows from a data source.</span></span> <span data-ttu-id="8f2b1-104">Toto je přetížené metody, které ve své nejjednodušší podobě přijímá jeden parametr, **DataReader –**.</span><span class="sxs-lookup"><span data-stu-id="8f2b1-104">This is an overloaded method which, in its simplest form, accepts a single parameter, a **DataReader**.</span></span> <span data-ttu-id="8f2b1-105">V tomto formuláři jednoduše načte **DataTable** s řádky.</span><span class="sxs-lookup"><span data-stu-id="8f2b1-105">In this form, it simply loads the **DataTable** with rows.</span></span> <span data-ttu-id="8f2b1-106">Volitelně můžete zadat **LoadOption** parametr řídit, jak přibývají data **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="8f2b1-106">Optionally, you can specify the **LoadOption** parameter to control how data is added to the **DataTable**.</span></span>  
  
 <span data-ttu-id="8f2b1-107">**LoadOption** parametr je zvlášť užitečné v případech, kde **DataTable** už obsahuje sloupce dat, protože popisuje, jak příchozí data ze zdroje dat bude sloučen s daty již v tabulce.</span><span class="sxs-lookup"><span data-stu-id="8f2b1-107">The **LoadOption** parameter is particularly useful in cases where the **DataTable** already contains rows of data, because it describes how incoming data from the data source will be combined with the data already in the table.</span></span> <span data-ttu-id="8f2b1-108">Například **PreserveCurrentValues** (výchozí) určuje, že v případech, kde je označeno řádek **Added** v **DataTable**, **původní** hodnotu nebo každý sloupec je nastavit obsah odpovídající řádek z datového zdroje.</span><span class="sxs-lookup"><span data-stu-id="8f2b1-108">For example, **PreserveCurrentValues** (the default) specifies that in cases where a row is marked as **Added** in the **DataTable**, the **Original** value or each column is set to the contents of the matching row from the data source.</span></span> <span data-ttu-id="8f2b1-109">**Aktuální** hodnotu zachovají hodnoty přiřazené při přidání řádku a **RowState** řádku, bude nastavena pro **změněno**.</span><span class="sxs-lookup"><span data-stu-id="8f2b1-109">The **Current** value will retain the values assigned when the row was added, and the **RowState** of the row will be set to **Changed**.</span></span>  
  
 <span data-ttu-id="8f2b1-110">Následující tabulka obsahuje stručný popis <xref:System.Data.LoadOption> hodnot výčtu.</span><span class="sxs-lookup"><span data-stu-id="8f2b1-110">The following table gives a short description of the <xref:System.Data.LoadOption> enumeration values.</span></span>  
  
|<span data-ttu-id="8f2b1-111">Hodnota LoadOption</span><span class="sxs-lookup"><span data-stu-id="8f2b1-111">LoadOption value</span></span>|<span data-ttu-id="8f2b1-112">Popis</span><span class="sxs-lookup"><span data-stu-id="8f2b1-112">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="8f2b1-113">**OverwriteRow**</span><span class="sxs-lookup"><span data-stu-id="8f2b1-113">**OverwriteRow**</span></span>|<span data-ttu-id="8f2b1-114">Pokud příchozí řádky mají stejné **PrimaryKey** hodnotu jako již v řádku **DataTable**, **původní** a **aktuální** hodnoty jednotlivých sloupce se nahradí hodnoty v řádku příchozí a **RowState** je nastavena na **Unchanged**.</span><span class="sxs-lookup"><span data-stu-id="8f2b1-114">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** and **Current** values of each column are replaced with the values in the incoming row, and the **RowState** property is set to **Unchanged**.</span></span><br /><br /> <span data-ttu-id="8f2b1-115">Řádky ze zdroje dat, který ještě neexistují v **DataTable** přidají se **RowState** hodnotu **Unchanged**.</span><span class="sxs-lookup"><span data-stu-id="8f2b1-115">Rows from the data source that do not already exist in the **DataTable** are added with a **RowState** value of **Unchanged**.</span></span><br /><br /> <span data-ttu-id="8f2b1-116">Tato možnost platí aktualizuje obsah **DataTable** tak, aby odpovídala obsah datového zdroje.</span><span class="sxs-lookup"><span data-stu-id="8f2b1-116">This option in effect refreshes the contents of the **DataTable** so that it matches the contents of the data source.</span></span>|  
|<span data-ttu-id="8f2b1-117">**PreserveCurrentValues (výchozí)**</span><span class="sxs-lookup"><span data-stu-id="8f2b1-117">**PreserveCurrentValues (default)**</span></span>|<span data-ttu-id="8f2b1-118">Pokud příchozí řádky mají stejné **PrimaryKey** hodnotu jako již v řádku **DataTable**, **původní** hodnota nastavena na obsah příchozí řádek a **Aktuální** hodnota nemění.</span><span class="sxs-lookup"><span data-stu-id="8f2b1-118">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** value is set to the contents of the incoming row, and the **Current** value is not changed.</span></span><br /><br /> <span data-ttu-id="8f2b1-119">Pokud **RowState** je **Added** nebo **změněné**, je nastaven na hodnotu **změněné**.</span><span class="sxs-lookup"><span data-stu-id="8f2b1-119">If the **RowState** is **Added** or **Modified**, it is set to **Modified**.</span></span><br /><br /> <span data-ttu-id="8f2b1-120">Pokud **RowState** byla **odstraněné**, zůstane **odstraněné**.</span><span class="sxs-lookup"><span data-stu-id="8f2b1-120">If the **RowState** was **Deleted**, it remains **Deleted**.</span></span><br /><br /> <span data-ttu-id="8f2b1-121">Řádky ze zdroje dat, který ještě neexistují v **DataTable** přidají a **RowState** je nastaven na **Unchanged**.</span><span class="sxs-lookup"><span data-stu-id="8f2b1-121">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Unchanged**.</span></span>|  
|<span data-ttu-id="8f2b1-122">**UpdateCurrentValues**</span><span class="sxs-lookup"><span data-stu-id="8f2b1-122">**UpdateCurrentValues**</span></span>|<span data-ttu-id="8f2b1-123">Pokud příchozí řádky mají stejné **PrimaryKey** hodnotu jako již v řádku **DataTable**, **aktuální** hodnota je zkopírován do **původní**hodnotu a **aktuální** pak nastavena na hodnotu obsah příchozí řádku.</span><span class="sxs-lookup"><span data-stu-id="8f2b1-123">If incoming rows have the same **PrimaryKey** value as the row already in the **DataTable**, the **Current** value is copied to the **Original** value, and the **Current** value is then set to the contents of the incoming row.</span></span><br /><br /> <span data-ttu-id="8f2b1-124">Pokud **RowState** v **DataTable** byla **Added**, **RowState** zůstává **Added**.</span><span class="sxs-lookup"><span data-stu-id="8f2b1-124">If the **RowState** in the **DataTable** was **Added**, the **RowState** remains **Added**.</span></span> <span data-ttu-id="8f2b1-125">Pro řádky označena jako **změněné** nebo **odstraněné**, **RowState** je **změněné**.</span><span class="sxs-lookup"><span data-stu-id="8f2b1-125">For rows marked as **Modified** or **Deleted**, the **RowState** is **Modified**.</span></span><br /><br /> <span data-ttu-id="8f2b1-126">Řádky ze zdroje dat, který ještě neexistují v **DataTable** přidají a **RowState** je nastaven na **Added**.</span><span class="sxs-lookup"><span data-stu-id="8f2b1-126">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Added**.</span></span>|  
  
 <span data-ttu-id="8f2b1-127">Následující ukázkové používá **zatížení** metodu pro zobrazení seznamu datum narození pro zaměstnance v **Northwind** databáze.</span><span class="sxs-lookup"><span data-stu-id="8f2b1-127">The following sample uses the **Load** method to display a list of birthdays for the employees in the **Northwind** database.</span></span>  
  
```vb  
Private Sub LoadBirthdays(ByVal connectionString As String)  
    ' Assumes that connectionString is a valid connection string  
    ' to the Northwind database on SQL Server.  
    Dim queryString As String = _  
    "SELECT LastName, FirstName, BirthDate " & _  
      " FROM dbo.Employees " & _  
      "ORDER BY BirthDate, LastName, FirstName"  
  
    ' Open and fill a DataSet.   
    Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
        queryString, connectionString)  
    Dim employees As New DataSet  
    adapter.Fill(employees, "Employees")  
  
    ' Create a SqlDataReader for use with the Load Method.  
    Dim reader As DataTableReader = employees.GetDataReader()  
  
    ' Create an instance of DataTable and assign the first  
    ' DataTable in the DataSet.Tables collection to it.  
    Dim dataTableEmp As DataTable = employees.Tables(0)  
  
    ' Fill the DataTable with data by calling Load and  
    ' passing the SqlDataReader.  
    dataTableEmp.Load(reader, LoadOption.OverwriteRow)  
  
    ' Loop through the rows collection and display the values  
    ' in the console window.  
    Dim employeeRow As DataRow  
    For Each employeeRow In dataTableEmp.Rows  
        Console.WriteLine("{0:MM\\dd\\yyyy}" & ControlChars.Tab & _  
          "{1}, {2}", _  
          employeeRow("BirthDate"), _  
          employeeRow("LastName"), _  
          employeeRow("FirstName"))  
    Next employeeRow  
  
    ' Keep the window opened to view the contents.  
    Console.ReadLine()  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="8f2b1-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="8f2b1-128">See Also</span></span>  
 [<span data-ttu-id="8f2b1-129">Manipulace s daty v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="8f2b1-129">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="8f2b1-130">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="8f2b1-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
