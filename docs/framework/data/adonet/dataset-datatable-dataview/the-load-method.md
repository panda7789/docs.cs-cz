---
title: Metoda Load
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: da0695aff9447355b1fc44a033c1b4a1cc224435
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785879"
---
# <a name="the-load-method"></a><span data-ttu-id="ee35a-102">Metoda Load</span><span class="sxs-lookup"><span data-stu-id="ee35a-102">The Load Method</span></span>
<span data-ttu-id="ee35a-103">Pomocí <xref:System.Data.DataTable.Load%2A> metody lze <xref:System.Data.DataTable> načíst řádky ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="ee35a-103">You can use the <xref:System.Data.DataTable.Load%2A> method to load a <xref:System.Data.DataTable> with rows from a data source.</span></span> <span data-ttu-id="ee35a-104">Toto je přetížená metoda, která v nejjednodušším tvaru přijímá jeden parametr, objekt **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="ee35a-104">This is an overloaded method which, in its simplest form, accepts a single parameter, a **DataReader**.</span></span> <span data-ttu-id="ee35a-105">V tomto formuláři jednoduše načte **objekt DataTable** s řádky.</span><span class="sxs-lookup"><span data-stu-id="ee35a-105">In this form, it simply loads the **DataTable** with rows.</span></span> <span data-ttu-id="ee35a-106">Volitelně můžete zadat parametr **LoadOption** pro řízení způsobu přidání dat do **objektu DataTable**.</span><span class="sxs-lookup"><span data-stu-id="ee35a-106">Optionally, you can specify the **LoadOption** parameter to control how data is added to the **DataTable**.</span></span>  
  
 <span data-ttu-id="ee35a-107">Parametr **LoadOption** je zvláště užitečný v případech, kdy **objekt DataTable** již obsahuje řádky dat, protože popisuje, jak budou příchozí data ze zdroje dat kombinována s daty, která jsou již v tabulce.</span><span class="sxs-lookup"><span data-stu-id="ee35a-107">The **LoadOption** parameter is particularly useful in cases where the **DataTable** already contains rows of data, because it describes how incoming data from the data source will be combined with the data already in the table.</span></span> <span data-ttu-id="ee35a-108">Například **PreserveCurrentValues** (výchozí) určuje, že v případech, kde je řádek označen jako **přidaný** v **objektu DataTable**, je **původní** hodnota nebo každý sloupec nastaven na obsah odpovídajícího řádku ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="ee35a-108">For example, **PreserveCurrentValues** (the default) specifies that in cases where a row is marked as **Added** in the **DataTable**, the **Original** value or each column is set to the contents of the matching row from the data source.</span></span> <span data-ttu-id="ee35a-109">**Aktuální** hodnota zachová hodnoty přiřazené při přidání řádku a **RowState** řádku se nastaví na hodnotu **změněno**.</span><span class="sxs-lookup"><span data-stu-id="ee35a-109">The **Current** value will retain the values assigned when the row was added, and the **RowState** of the row will be set to **Changed**.</span></span>  
  
 <span data-ttu-id="ee35a-110">Následující tabulka obsahuje stručný popis <xref:System.Data.LoadOption> hodnot výčtu.</span><span class="sxs-lookup"><span data-stu-id="ee35a-110">The following table gives a short description of the <xref:System.Data.LoadOption> enumeration values.</span></span>  
  
|<span data-ttu-id="ee35a-111">Hodnota LoadOption</span><span class="sxs-lookup"><span data-stu-id="ee35a-111">LoadOption value</span></span>|<span data-ttu-id="ee35a-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ee35a-112">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="ee35a-113">**OverwriteRow**</span><span class="sxs-lookup"><span data-stu-id="ee35a-113">**OverwriteRow**</span></span>|<span data-ttu-id="ee35a-114">Pokud mají vstupní řádky stejnou hodnotu **PrimaryKey** jako řádek, který už je v **objektu DataTable**, nahradí se **původní** a **aktuální** hodnota každého sloupce hodnotami v poli příchozí řádek a vlastnost **RowState** je nastavena na hodnotu **Beze změny**.</span><span class="sxs-lookup"><span data-stu-id="ee35a-114">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** and **Current** values of each column are replaced with the values in the incoming row, and the **RowState** property is set to **Unchanged**.</span></span><br /><br /> <span data-ttu-id="ee35a-115">Řádky ze zdroje dat, které ještě neexistují v **objektu DataTable** , jsou přidány s hodnotou **RowState** **beze změny**.</span><span class="sxs-lookup"><span data-stu-id="ee35a-115">Rows from the data source that do not already exist in the **DataTable** are added with a **RowState** value of **Unchanged**.</span></span><br /><br /> <span data-ttu-id="ee35a-116">Tato možnost v důsledku toho aktualizuje obsah **objektu DataTable** tak, aby odpovídal obsahu zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="ee35a-116">This option in effect refreshes the contents of the **DataTable** so that it matches the contents of the data source.</span></span>|  
|<span data-ttu-id="ee35a-117">**PreserveCurrentValues (výchozí)**</span><span class="sxs-lookup"><span data-stu-id="ee35a-117">**PreserveCurrentValues (default)**</span></span>|<span data-ttu-id="ee35a-118">Pokud mají vstupní řádky stejnou hodnotu **PrimaryKey** jako řádek, který je již v **objektu DataTable**, je **původní** hodnota nastavena na obsah příchozího řádku a **aktuální** hodnota se nemění.</span><span class="sxs-lookup"><span data-stu-id="ee35a-118">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** value is set to the contents of the incoming row, and the **Current** value is not changed.</span></span><br /><br /> <span data-ttu-id="ee35a-119">Pokud je **RowState** **přidáno** nebo **upraveno**, je nastaveno na hodnotu **změněno**.</span><span class="sxs-lookup"><span data-stu-id="ee35a-119">If the **RowState** is **Added** or **Modified**, it is set to **Modified**.</span></span><br /><br /> <span data-ttu-id="ee35a-120">Pokud se **RowState** **odstranil**, zůstane **Odstraněný**.</span><span class="sxs-lookup"><span data-stu-id="ee35a-120">If the **RowState** was **Deleted**, it remains **Deleted**.</span></span><br /><br /> <span data-ttu-id="ee35a-121">Řádky ze zdroje dat, které ještě neexistují v **objektu DataTable** , jsou přidány a vlastnost **RowState** je nastavena na hodnotu **Unchanged**.</span><span class="sxs-lookup"><span data-stu-id="ee35a-121">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Unchanged**.</span></span>|  
|<span data-ttu-id="ee35a-122">**UpdateCurrentValues**</span><span class="sxs-lookup"><span data-stu-id="ee35a-122">**UpdateCurrentValues**</span></span>|<span data-ttu-id="ee35a-123">Pokud mají vstupní řádky stejnou hodnotu **PrimaryKey** jako řádek, který je již v **objektu DataTable**, je **aktuální** hodnota zkopírována do **původní** hodnoty a **aktuální** hodnota je poté nastavena na obsah příchozího řádku.</span><span class="sxs-lookup"><span data-stu-id="ee35a-123">If incoming rows have the same **PrimaryKey** value as the row already in the **DataTable**, the **Current** value is copied to the **Original** value, and the **Current** value is then set to the contents of the incoming row.</span></span><br /><br /> <span data-ttu-id="ee35a-124">Pokud byl **přidán** **RowState** v **objektu DataTable** , **RowState** zůstane **přidán**.</span><span class="sxs-lookup"><span data-stu-id="ee35a-124">If the **RowState** in the **DataTable** was **Added**, the **RowState** remains **Added**.</span></span> <span data-ttu-id="ee35a-125">Pro řádky označené jako **upravené** nebo **odstraněné**se **změní** **RowState** .</span><span class="sxs-lookup"><span data-stu-id="ee35a-125">For rows marked as **Modified** or **Deleted**, the **RowState** is **Modified**.</span></span><br /><br /> <span data-ttu-id="ee35a-126">Řádky ze zdroje dat, které ještě neexistují v **objektu DataTable** , jsou přidány a **RowState** je nastaven na hodnotu **přidáno**.</span><span class="sxs-lookup"><span data-stu-id="ee35a-126">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Added**.</span></span>|  
  
 <span data-ttu-id="ee35a-127">Následující příklad používá metodu **Load** k zobrazení seznamu narozenin pro zaměstnance v databázi **Northwind** .</span><span class="sxs-lookup"><span data-stu-id="ee35a-127">The following sample uses the **Load** method to display a list of birthdays for the employees in the **Northwind** database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ee35a-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ee35a-128">See also</span></span>

- [<span data-ttu-id="ee35a-129">Manipulace s daty v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="ee35a-129">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="ee35a-130">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ee35a-130">ADO.NET Overview</span></span>](../ado-net-overview.md)
