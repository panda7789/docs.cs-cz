---
title: Metoda Load
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: f1c819333225c22efb85946001a1fc8340d57989
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150724"
---
# <a name="the-load-method"></a><span data-ttu-id="09b98-102">Metoda Load</span><span class="sxs-lookup"><span data-stu-id="09b98-102">The Load Method</span></span>
<span data-ttu-id="09b98-103">Metodu <xref:System.Data.DataTable.Load%2A> můžete použít k <xref:System.Data.DataTable> načtení řádků s ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="09b98-103">You can use the <xref:System.Data.DataTable.Load%2A> method to load a <xref:System.Data.DataTable> with rows from a data source.</span></span> <span data-ttu-id="09b98-104">Jedná se o přetíženou metodu, která ve své nejjednodušší podobě přijímá jeden parametr, **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="09b98-104">This is an overloaded method which, in its simplest form, accepts a single parameter, a **DataReader**.</span></span> <span data-ttu-id="09b98-105">V tomto formuláři jednoduše načte **DataTable** s řádky.</span><span class="sxs-lookup"><span data-stu-id="09b98-105">In this form, it simply loads the **DataTable** with rows.</span></span> <span data-ttu-id="09b98-106">Volitelně můžete určit **parametr LoadOption,** který určuje, jak budou data přidána do **datatable**.</span><span class="sxs-lookup"><span data-stu-id="09b98-106">Optionally, you can specify the **LoadOption** parameter to control how data is added to the **DataTable**.</span></span>  
  
 <span data-ttu-id="09b98-107">**LoadOption** Parametr je zvláště užitečné v případech, kdy **DataTable** již obsahuje řádky dat, protože popisuje, jak příchozí data ze zdroje dat budou kombinovány s daty již v tabulce.</span><span class="sxs-lookup"><span data-stu-id="09b98-107">The **LoadOption** parameter is particularly useful in cases where the **DataTable** already contains rows of data, because it describes how incoming data from the data source will be combined with the data already in the table.</span></span> <span data-ttu-id="09b98-108">Například **PreserveCurrentValues** (výchozí) určuje, že v případech, kdy je řádek označen jako **Přidáno** v **DataTable**, **původní** hodnota nebo každý sloupec je nastavena na obsah odpovídající řádek ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="09b98-108">For example, **PreserveCurrentValues** (the default) specifies that in cases where a row is marked as **Added** in the **DataTable**, the **Original** value or each column is set to the contents of the matching row from the data source.</span></span> <span data-ttu-id="09b98-109">**Aktuální** hodnota zachová hodnoty přiřazené při přidání řádku a **RowState** řádku bude nastavena na **Changed**.</span><span class="sxs-lookup"><span data-stu-id="09b98-109">The **Current** value will retain the values assigned when the row was added, and the **RowState** of the row will be set to **Changed**.</span></span>  
  
 <span data-ttu-id="09b98-110">V následující tabulce je uveden <xref:System.Data.LoadOption> krátký popis hodnot výčtu.</span><span class="sxs-lookup"><span data-stu-id="09b98-110">The following table gives a short description of the <xref:System.Data.LoadOption> enumeration values.</span></span>  
  
|<span data-ttu-id="09b98-111">Hodnota LoadOption</span><span class="sxs-lookup"><span data-stu-id="09b98-111">LoadOption value</span></span>|<span data-ttu-id="09b98-112">Popis</span><span class="sxs-lookup"><span data-stu-id="09b98-112">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="09b98-113">**Přepsat řádek**</span><span class="sxs-lookup"><span data-stu-id="09b98-113">**OverwriteRow**</span></span>|<span data-ttu-id="09b98-114">Pokud příchozí řádky mají stejnou hodnotu **PrimaryKey** jako řádek již v **DataTable**, **původní** a **aktuální** hodnoty každého sloupce jsou nahrazeny hodnotami v příchozím řádku a **RowState** vlastnost je nastavena na **nezměněné**.</span><span class="sxs-lookup"><span data-stu-id="09b98-114">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** and **Current** values of each column are replaced with the values in the incoming row, and the **RowState** property is set to **Unchanged**.</span></span><br /><br /> <span data-ttu-id="09b98-115">Řádky ze zdroje dat, které ještě neexistují v **DataTable** jsou přidány s **RowState** hodnotu **Beze změny**.</span><span class="sxs-lookup"><span data-stu-id="09b98-115">Rows from the data source that do not already exist in the **DataTable** are added with a **RowState** value of **Unchanged**.</span></span><br /><br /> <span data-ttu-id="09b98-116">Tato možnost ve skutečnosti aktualizuje obsah **DataTable** tak, aby odpovídala obsahu zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="09b98-116">This option in effect refreshes the contents of the **DataTable** so that it matches the contents of the data source.</span></span>|  
|<span data-ttu-id="09b98-117">**Zachovat hodnoty proudu (výchozí)**</span><span class="sxs-lookup"><span data-stu-id="09b98-117">**PreserveCurrentValues (default)**</span></span>|<span data-ttu-id="09b98-118">Pokud příchozí řádky mají stejnou hodnotu **PrimaryKey** jako řádek již v **DataTable**, **původní** hodnota je nastavena na obsah příchozí řádek a **aktuální** hodnota se nezmění.</span><span class="sxs-lookup"><span data-stu-id="09b98-118">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** value is set to the contents of the incoming row, and the **Current** value is not changed.</span></span><br /><br /> <span data-ttu-id="09b98-119">Pokud **je Stav řádku** **přidán** nebo **změněn**, je nastaven na **změnit**.</span><span class="sxs-lookup"><span data-stu-id="09b98-119">If the **RowState** is **Added** or **Modified**, it is set to **Modified**.</span></span><br /><br /> <span data-ttu-id="09b98-120">Pokud **rowState** byl **odstraněn**, zůstane **Odstraněno**.</span><span class="sxs-lookup"><span data-stu-id="09b98-120">If the **RowState** was **Deleted**, it remains **Deleted**.</span></span><br /><br /> <span data-ttu-id="09b98-121">Řádky ze zdroje dat, které ještě neexistují v **DataTable** jsou přidány a **RowState** je nastavena na **beze změny**.</span><span class="sxs-lookup"><span data-stu-id="09b98-121">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Unchanged**.</span></span>|  
|<span data-ttu-id="09b98-122">**AktualizovatCurrentValues**</span><span class="sxs-lookup"><span data-stu-id="09b98-122">**UpdateCurrentValues**</span></span>|<span data-ttu-id="09b98-123">Pokud mají příchozí řádky stejnou hodnotu **PrimaryKey** jako řádek již v **tabulce DataTable**, je hodnota **Current** zkopírována na **hodnotu Original** a hodnota **Current** je pak nastavena na obsah příchozího řádku.</span><span class="sxs-lookup"><span data-stu-id="09b98-123">If incoming rows have the same **PrimaryKey** value as the row already in the **DataTable**, the **Current** value is copied to the **Original** value, and the **Current** value is then set to the contents of the incoming row.</span></span><br /><br /> <span data-ttu-id="09b98-124">Pokud byl **přidán** **stav RowState** v **tabulce DataTable** , **zůstane Stav řádku** **Přidáno**.</span><span class="sxs-lookup"><span data-stu-id="09b98-124">If the **RowState** in the **DataTable** was **Added**, the **RowState** remains **Added**.</span></span> <span data-ttu-id="09b98-125">U řádků označených jako **Změněno** nebo **Odstraněno**je **stav řádku** **změněn**.</span><span class="sxs-lookup"><span data-stu-id="09b98-125">For rows marked as **Modified** or **Deleted**, the **RowState** is **Modified**.</span></span><br /><br /> <span data-ttu-id="09b98-126">Řádky ze zdroje dat, které ještě neexistují v **DataTable** jsou přidány a **RowState** je nastavena na **Přidáno**.</span><span class="sxs-lookup"><span data-stu-id="09b98-126">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Added**.</span></span>|  
  
 <span data-ttu-id="09b98-127">Následující ukázka používá **Load** metoda zobrazit seznam narozenin pro zaměstnance v databázi **Northwind.**</span><span class="sxs-lookup"><span data-stu-id="09b98-127">The following sample uses the **Load** method to display a list of birthdays for the employees in the **Northwind** database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="09b98-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="09b98-128">See also</span></span>

- [<span data-ttu-id="09b98-129">Manipulace s daty v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="09b98-129">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="09b98-130">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="09b98-130">ADO.NET Overview</span></span>](../ado-net-overview.md)
