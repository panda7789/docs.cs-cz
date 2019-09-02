---
title: Metoda Load
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: b704deeffcd06bca09b6c26d60a66218b46fc55c
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203166"
---
# <a name="the-load-method"></a>Metoda Load
Pomocí <xref:System.Data.DataTable.Load%2A> metody lze <xref:System.Data.DataTable> načíst řádky ze zdroje dat. Toto je přetížená metoda, která v nejjednodušším tvaru přijímá jeden parametr, objekt DataReader. V tomto formuláři jednoduše načte **objekt DataTable** s řádky. Volitelně můžete zadat parametr **LoadOption** pro řízení způsobu přidání dat do **objektu DataTable**.  
  
 Parametr **LoadOption** je zvláště užitečný v případech, kdy **objekt DataTable** již obsahuje řádky dat, protože popisuje, jak budou příchozí data ze zdroje dat kombinována s daty, která jsou již v tabulce. Například **PreserveCurrentValues** (výchozí) určuje, že v případech, kde je řádek označen jako přidaný v **objektu DataTable**, je **původní** hodnota nebo každý sloupec nastaven na obsah odpovídajícího řádku ze zdroje dat. **Aktuální** hodnota zachová hodnoty přiřazené při přidání řádku a **RowState** řádku se nastaví na hodnotu **změněno**.  
  
 Následující tabulka obsahuje stručný popis <xref:System.Data.LoadOption> hodnot výčtu.  
  
|Hodnota LoadOption|Popis|  
|----------------------|-----------------|  
|**OverwriteRow**|Pokud mají vstupní řádky stejnou hodnotu **PrimaryKey** jako řádek, který už je v **objektu DataTable**, nahradí se **původní** a **aktuální** hodnota každého sloupce hodnotami v poli příchozí řádek a vlastnost **RowState** je nastavena na hodnotu **Beze změny**.<br /><br /> Řádky ze zdroje dat, které ještě neexistují v **objektu DataTable** , jsou přidány s hodnotou **RowState** **beze změny**.<br /><br /> Tato možnost v důsledku toho aktualizuje obsah **objektu DataTable** tak, aby odpovídal obsahu zdroje dat.|  
|**PreserveCurrentValues (výchozí)**|Pokud mají vstupní řádky stejnou hodnotu **PrimaryKey** jako řádek, který je již v **objektu DataTable**, je **původní** hodnota nastavena na obsah příchozího řádku a **aktuální** hodnota se nemění.<br /><br /> Pokud je **RowState** **přidáno** nebo **upraveno**, je nastaveno na hodnotu **změněno**.<br /><br /> Pokud se **RowState** **odstranil**, zůstane **Odstraněný**.<br /><br /> Řádky ze zdroje dat, které ještě neexistují v **objektu DataTable** , jsou přidány a vlastnost **RowState** je nastavena na hodnotuUnchanged.|  
|**UpdateCurrentValues**|Pokud mají vstupní řádky stejnou hodnotu **PrimaryKey** jako řádek, který je již v **objektu DataTable**, je **aktuální** hodnota zkopírována do **původní** hodnoty a **aktuální** hodnota je poté nastavena na obsah příchozího řádku.<br /><br /> Pokud byl **přidán** **RowState** v **objektu DataTable** , **RowState** zůstane **přidán**. Pro řádky označené jako **upravené** neboodstraněné se **změní** **RowState** .<br /><br /> Řádky ze zdroje dat, které ještě neexistují v **objektu DataTable** , jsou přidány a **RowState** je nastaven na hodnotu **přidáno**.|  
  
 Následující příklad používá metodu **Load** k zobrazení seznamu narozenin pro zaměstnance v databázi **Northwind** .  
  
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

- [Manipulace s daty v datové tabulce](manipulating-data-in-a-datatable.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
