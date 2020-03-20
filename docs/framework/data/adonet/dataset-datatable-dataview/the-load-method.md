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
# <a name="the-load-method"></a>Metoda Load
Metodu <xref:System.Data.DataTable.Load%2A> můžete použít k <xref:System.Data.DataTable> načtení řádků s ze zdroje dat. Jedná se o přetíženou metodu, která ve své nejjednodušší podobě přijímá jeden parametr, **DataReader**. V tomto formuláři jednoduše načte **DataTable** s řádky. Volitelně můžete určit **parametr LoadOption,** který určuje, jak budou data přidána do **datatable**.  
  
 **LoadOption** Parametr je zvláště užitečné v případech, kdy **DataTable** již obsahuje řádky dat, protože popisuje, jak příchozí data ze zdroje dat budou kombinovány s daty již v tabulce. Například **PreserveCurrentValues** (výchozí) určuje, že v případech, kdy je řádek označen jako **Přidáno** v **DataTable**, **původní** hodnota nebo každý sloupec je nastavena na obsah odpovídající řádek ze zdroje dat. **Aktuální** hodnota zachová hodnoty přiřazené při přidání řádku a **RowState** řádku bude nastavena na **Changed**.  
  
 V následující tabulce je uveden <xref:System.Data.LoadOption> krátký popis hodnot výčtu.  
  
|Hodnota LoadOption|Popis|  
|----------------------|-----------------|  
|**Přepsat řádek**|Pokud příchozí řádky mají stejnou hodnotu **PrimaryKey** jako řádek již v **DataTable**, **původní** a **aktuální** hodnoty každého sloupce jsou nahrazeny hodnotami v příchozím řádku a **RowState** vlastnost je nastavena na **nezměněné**.<br /><br /> Řádky ze zdroje dat, které ještě neexistují v **DataTable** jsou přidány s **RowState** hodnotu **Beze změny**.<br /><br /> Tato možnost ve skutečnosti aktualizuje obsah **DataTable** tak, aby odpovídala obsahu zdroje dat.|  
|**Zachovat hodnoty proudu (výchozí)**|Pokud příchozí řádky mají stejnou hodnotu **PrimaryKey** jako řádek již v **DataTable**, **původní** hodnota je nastavena na obsah příchozí řádek a **aktuální** hodnota se nezmění.<br /><br /> Pokud **je Stav řádku** **přidán** nebo **změněn**, je nastaven na **změnit**.<br /><br /> Pokud **rowState** byl **odstraněn**, zůstane **Odstraněno**.<br /><br /> Řádky ze zdroje dat, které ještě neexistují v **DataTable** jsou přidány a **RowState** je nastavena na **beze změny**.|  
|**AktualizovatCurrentValues**|Pokud mají příchozí řádky stejnou hodnotu **PrimaryKey** jako řádek již v **tabulce DataTable**, je hodnota **Current** zkopírována na **hodnotu Original** a hodnota **Current** je pak nastavena na obsah příchozího řádku.<br /><br /> Pokud byl **přidán** **stav RowState** v **tabulce DataTable** , **zůstane Stav řádku** **Přidáno**. U řádků označených jako **Změněno** nebo **Odstraněno**je **stav řádku** **změněn**.<br /><br /> Řádky ze zdroje dat, které ještě neexistují v **DataTable** jsou přidány a **RowState** je nastavena na **Přidáno**.|  
  
 Následující ukázka používá **Load** metoda zobrazit seznam narozenin pro zaměstnance v databázi **Northwind.**  
  
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
  
## <a name="see-also"></a>Viz také

- [Manipulace s daty v datové tabulce](manipulating-data-in-a-datatable.md)
- [Přehled ADO.NET](../ado-net-overview.md)
