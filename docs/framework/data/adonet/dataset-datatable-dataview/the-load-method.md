---
title: Metoda Load
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: 82f840ab7dd26a4888ebf024d696f2c70701eb18
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59173287"
---
# <a name="the-load-method"></a>Metoda Load
Můžete použít <xref:System.Data.DataTable.Load%2A> metodu pro načtení <xref:System.Data.DataTable> s řádky ze zdroje dat. Toto je přetěžované metody, které ve své nejjednodušší podobě přijímá jeden parametr, **DataReader**. V tomto formuláři jednoduše načte **DataTable** s řádky. Volitelně můžete zadat **LoadOption** parametr řídit, jak data je přidána do **DataTable**.  
  
 **LoadOption** parametr je zvlášť užitečné v případech, kde **DataTable** již obsahuje řádky dat, protože popisuje, jak příchozí data ze zdroje dat se zkombinuje s daty už v tabulce. Například **PreserveCurrentValues** (výchozí) určuje, že v případech, kde je řádek označený jako **přidané** v **DataTable**, **původní** hodnotu nebo jednotlivé sloupce je nastavena na odpovídající řádek obsah ze zdroje dat. **Aktuální** hodnotu zachová hodnoty přiřazené při přidání řádku a **RowState** řádku, který bude nastavena na **změněné**.  
  
 Následující tabulka obsahuje stručný popis <xref:System.Data.LoadOption> hodnot výčtu.  
  
|Hodnota LoadOption|Popis|  
|----------------------|-----------------|  
|**OverwriteRow**|Pokud příchozí řádků mají stejné **PrimaryKey** hodnotu jako již v řádku **DataTable**, **původní** a **aktuální** hodnoty sloupce se nahradí hodnotami v řádku příchozí a **RowState** je nastavena na **Unchanged**.<br /><br /> Řádků ze zdroje dat, které už neexistují v **DataTable** se přidají **RowState** hodnotu **Unchanged**.<br /><br /> Tato možnost platit aktualizuje obsah **DataTable** tak, aby odpovídalo obsah datového zdroje.|  
|**PreserveCurrentValues (výchozí)**|Pokud příchozí řádků mají stejné **PrimaryKey** hodnotu jako již v řádku **DataTable**, **původní** je hodnota nastavená na obsah z příchozího řádku a **Aktuální** hodnota se nezmění.<br /><br /> Pokud **RowState** je **přidané** nebo **změněné**, je nastaven na hodnotu **změněné**.<br /><br /> Pokud **RowState** byl **odstraněné**, zůstane **odstraněné**.<br /><br /> Řádků ze zdroje dat, které už neexistují v **DataTable** jsou přidány a **RowState** je nastavena na **Unchanged**.|  
|**UpdateCurrentValues**|Pokud příchozí řádků mají stejné **PrimaryKey** hodnotu jako již v řádku **DataTable**, **aktuální** zkopírování hodnoty do **původní**hodnotu a **aktuální** hodnota je nastaven na obsah z příchozího řádku.<br /><br /> Pokud **RowState** v **DataTable** byl **přidané**, **RowState** zůstává **přidané**. Pro řádky jsou označeny jako **změněné** nebo **odstraněné**, **RowState** je **změněné**.<br /><br /> Řádků ze zdroje dat, které už neexistují v **DataTable** jsou přidány a **RowState** je nastavena na **přidané**.|  
  
 Následující ukázkový používá **zatížení** metodu pro zobrazení seznamu datum narození pro zaměstnance v **Northwind** databáze.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Manipulace s daty v datové tabulce](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
