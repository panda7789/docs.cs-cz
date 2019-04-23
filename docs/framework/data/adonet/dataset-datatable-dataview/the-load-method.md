---
title: Metoda Load
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: 82f840ab7dd26a4888ebf024d696f2c70701eb18
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173287"
---
# <a name="the-load-method"></a><span data-ttu-id="5d341-102">Metoda Load</span><span class="sxs-lookup"><span data-stu-id="5d341-102">The Load Method</span></span>
<span data-ttu-id="5d341-103">Můžete použít <xref:System.Data.DataTable.Load%2A> metodu pro načtení <xref:System.Data.DataTable> s řádky ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="5d341-103">You can use the <xref:System.Data.DataTable.Load%2A> method to load a <xref:System.Data.DataTable> with rows from a data source.</span></span> <span data-ttu-id="5d341-104">Toto je přetěžované metody, které ve své nejjednodušší podobě přijímá jeden parametr, **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="5d341-104">This is an overloaded method which, in its simplest form, accepts a single parameter, a **DataReader**.</span></span> <span data-ttu-id="5d341-105">V tomto formuláři jednoduše načte **DataTable** s řádky.</span><span class="sxs-lookup"><span data-stu-id="5d341-105">In this form, it simply loads the **DataTable** with rows.</span></span> <span data-ttu-id="5d341-106">Volitelně můžete zadat **LoadOption** parametr řídit, jak data je přidána do **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="5d341-106">Optionally, you can specify the **LoadOption** parameter to control how data is added to the **DataTable**.</span></span>  
  
 <span data-ttu-id="5d341-107">**LoadOption** parametr je zvlášť užitečné v případech, kde **DataTable** již obsahuje řádky dat, protože popisuje, jak příchozí data ze zdroje dat se zkombinuje s daty už v tabulce.</span><span class="sxs-lookup"><span data-stu-id="5d341-107">The **LoadOption** parameter is particularly useful in cases where the **DataTable** already contains rows of data, because it describes how incoming data from the data source will be combined with the data already in the table.</span></span> <span data-ttu-id="5d341-108">Například **PreserveCurrentValues** (výchozí) určuje, že v případech, kde je řádek označený jako **přidané** v **DataTable**, **původní** hodnotu nebo jednotlivé sloupce je nastavena na odpovídající řádek obsah ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="5d341-108">For example, **PreserveCurrentValues** (the default) specifies that in cases where a row is marked as **Added** in the **DataTable**, the **Original** value or each column is set to the contents of the matching row from the data source.</span></span> <span data-ttu-id="5d341-109">**Aktuální** hodnotu zachová hodnoty přiřazené při přidání řádku a **RowState** řádku, který bude nastavena na **změněné**.</span><span class="sxs-lookup"><span data-stu-id="5d341-109">The **Current** value will retain the values assigned when the row was added, and the **RowState** of the row will be set to **Changed**.</span></span>  
  
 <span data-ttu-id="5d341-110">Následující tabulka obsahuje stručný popis <xref:System.Data.LoadOption> hodnot výčtu.</span><span class="sxs-lookup"><span data-stu-id="5d341-110">The following table gives a short description of the <xref:System.Data.LoadOption> enumeration values.</span></span>  
  
|<span data-ttu-id="5d341-111">Hodnota LoadOption</span><span class="sxs-lookup"><span data-stu-id="5d341-111">LoadOption value</span></span>|<span data-ttu-id="5d341-112">Popis</span><span class="sxs-lookup"><span data-stu-id="5d341-112">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="5d341-113">**OverwriteRow**</span><span class="sxs-lookup"><span data-stu-id="5d341-113">**OverwriteRow**</span></span>|<span data-ttu-id="5d341-114">Pokud příchozí řádků mají stejné **PrimaryKey** hodnotu jako již v řádku **DataTable**, **původní** a **aktuální** hodnoty sloupce se nahradí hodnotami v řádku příchozí a **RowState** je nastavena na **Unchanged**.</span><span class="sxs-lookup"><span data-stu-id="5d341-114">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** and **Current** values of each column are replaced with the values in the incoming row, and the **RowState** property is set to **Unchanged**.</span></span><br /><br /> <span data-ttu-id="5d341-115">Řádků ze zdroje dat, které už neexistují v **DataTable** se přidají **RowState** hodnotu **Unchanged**.</span><span class="sxs-lookup"><span data-stu-id="5d341-115">Rows from the data source that do not already exist in the **DataTable** are added with a **RowState** value of **Unchanged**.</span></span><br /><br /> <span data-ttu-id="5d341-116">Tato možnost platit aktualizuje obsah **DataTable** tak, aby odpovídalo obsah datového zdroje.</span><span class="sxs-lookup"><span data-stu-id="5d341-116">This option in effect refreshes the contents of the **DataTable** so that it matches the contents of the data source.</span></span>|  
|<span data-ttu-id="5d341-117">**PreserveCurrentValues (výchozí)**</span><span class="sxs-lookup"><span data-stu-id="5d341-117">**PreserveCurrentValues (default)**</span></span>|<span data-ttu-id="5d341-118">Pokud příchozí řádků mají stejné **PrimaryKey** hodnotu jako již v řádku **DataTable**, **původní** je hodnota nastavená na obsah z příchozího řádku a **Aktuální** hodnota se nezmění.</span><span class="sxs-lookup"><span data-stu-id="5d341-118">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** value is set to the contents of the incoming row, and the **Current** value is not changed.</span></span><br /><br /> <span data-ttu-id="5d341-119">Pokud **RowState** je **přidané** nebo **změněné**, je nastaven na hodnotu **změněné**.</span><span class="sxs-lookup"><span data-stu-id="5d341-119">If the **RowState** is **Added** or **Modified**, it is set to **Modified**.</span></span><br /><br /> <span data-ttu-id="5d341-120">Pokud **RowState** byl **odstraněné**, zůstane **odstraněné**.</span><span class="sxs-lookup"><span data-stu-id="5d341-120">If the **RowState** was **Deleted**, it remains **Deleted**.</span></span><br /><br /> <span data-ttu-id="5d341-121">Řádků ze zdroje dat, které už neexistují v **DataTable** jsou přidány a **RowState** je nastavena na **Unchanged**.</span><span class="sxs-lookup"><span data-stu-id="5d341-121">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Unchanged**.</span></span>|  
|<span data-ttu-id="5d341-122">**UpdateCurrentValues**</span><span class="sxs-lookup"><span data-stu-id="5d341-122">**UpdateCurrentValues**</span></span>|<span data-ttu-id="5d341-123">Pokud příchozí řádků mají stejné **PrimaryKey** hodnotu jako již v řádku **DataTable**, **aktuální** zkopírování hodnoty do **původní**hodnotu a **aktuální** hodnota je nastaven na obsah z příchozího řádku.</span><span class="sxs-lookup"><span data-stu-id="5d341-123">If incoming rows have the same **PrimaryKey** value as the row already in the **DataTable**, the **Current** value is copied to the **Original** value, and the **Current** value is then set to the contents of the incoming row.</span></span><br /><br /> <span data-ttu-id="5d341-124">Pokud **RowState** v **DataTable** byl **přidané**, **RowState** zůstává **přidané**.</span><span class="sxs-lookup"><span data-stu-id="5d341-124">If the **RowState** in the **DataTable** was **Added**, the **RowState** remains **Added**.</span></span> <span data-ttu-id="5d341-125">Pro řádky jsou označeny jako **změněné** nebo **odstraněné**, **RowState** je **změněné**.</span><span class="sxs-lookup"><span data-stu-id="5d341-125">For rows marked as **Modified** or **Deleted**, the **RowState** is **Modified**.</span></span><br /><br /> <span data-ttu-id="5d341-126">Řádků ze zdroje dat, které už neexistují v **DataTable** jsou přidány a **RowState** je nastavena na **přidané**.</span><span class="sxs-lookup"><span data-stu-id="5d341-126">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Added**.</span></span>|  
  
 <span data-ttu-id="5d341-127">Následující ukázkový používá **zatížení** metodu pro zobrazení seznamu datum narození pro zaměstnance v **Northwind** databáze.</span><span class="sxs-lookup"><span data-stu-id="5d341-127">The following sample uses the **Load** method to display a list of birthdays for the employees in the **Northwind** database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5d341-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d341-128">See also</span></span>

- [<span data-ttu-id="5d341-129">Manipulace s daty v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="5d341-129">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="5d341-130">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="5d341-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
