---
title: Metoda Load
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: a54eda8d96468d4506a5f7dafc342fa5ff128c2a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="the-load-method"></a>Metoda Load
Můžete použít <xref:System.Data.DataTable.Load%2A> metoda načíst <xref:System.Data.DataTable> s řádky ze zdroje dat. Toto je přetížené metody, které ve své nejjednodušší podobě přijímá jeden parametr, **DataReader –**. V tomto formuláři jednoduše načte **DataTable** s řádky. Volitelně můžete zadat **LoadOption** parametr řídit, jak přibývají data **DataTable**.  
  
 **LoadOption** parametr je zvlášť užitečné v případech, kde **DataTable** už obsahuje sloupce dat, protože popisuje, jak příchozí data ze zdroje dat bude sloučen s daty již v tabulce. Například **PreserveCurrentValues** (výchozí) určuje, že v případech, kde je označeno řádek **Added** v **DataTable**, **původní** hodnotu nebo každý sloupec je nastavit obsah odpovídající řádek z datového zdroje. **Aktuální** hodnotu zachovají hodnoty přiřazené při přidání řádku a **RowState** řádku, bude nastavena pro **změněno**.  
  
 Následující tabulka obsahuje stručný popis <xref:System.Data.LoadOption> hodnot výčtu.  
  
|Hodnota LoadOption|Popis|  
|----------------------|-----------------|  
|**OverwriteRow**|Pokud příchozí řádky mají stejné **PrimaryKey** hodnotu jako již v řádku **DataTable**, **původní** a **aktuální** hodnoty jednotlivých sloupce se nahradí hodnoty v řádku příchozí a **RowState** je nastavena na **Unchanged**.<br /><br /> Řádky ze zdroje dat, který ještě neexistují v **DataTable** přidají se **RowState** hodnotu **Unchanged**.<br /><br /> Tato možnost platí aktualizuje obsah **DataTable** tak, aby odpovídala obsah datového zdroje.|  
|**PreserveCurrentValues (výchozí)**|Pokud příchozí řádky mají stejné **PrimaryKey** hodnotu jako již v řádku **DataTable**, **původní** hodnota nastavena na obsah příchozí řádek a **Aktuální** hodnota nemění.<br /><br /> Pokud **RowState** je **Added** nebo **změněné**, je nastaven na hodnotu **změněné**.<br /><br /> Pokud **RowState** byla **odstraněné**, zůstane **odstraněné**.<br /><br /> Řádky ze zdroje dat, který ještě neexistují v **DataTable** přidají a **RowState** je nastaven na **Unchanged**.|  
|**UpdateCurrentValues**|Pokud příchozí řádky mají stejné **PrimaryKey** hodnotu jako již v řádku **DataTable**, **aktuální** hodnota je zkopírován do **původní**hodnotu a **aktuální** pak nastavena na hodnotu obsah příchozí řádku.<br /><br /> Pokud **RowState** v **DataTable** byla **Added**, **RowState** zůstává **Added**. Pro řádky označena jako **změněné** nebo **odstraněné**, **RowState** je **změněné**.<br /><br /> Řádky ze zdroje dat, který ještě neexistují v **DataTable** přidají a **RowState** je nastaven na **Added**.|  
  
 Následující ukázkové používá **zatížení** metodu pro zobrazení seznamu datum narození pro zaměstnance v **Northwind** databáze.  
  
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
 [Manipulace s daty v datové tabulce](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
