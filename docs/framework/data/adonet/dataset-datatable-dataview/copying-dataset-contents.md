---
title: "Kopírování obsahu datové sady"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: d8f9eac80d7a6679e7b3717446e79caf54a5fed3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="copying-dataset-contents"></a>Kopírování obsahu datové sady
Můžete vytvořit kopii <xref:System.Data.DataSet> , mohli pracovat s daty, aniž by to ovlivnilo původní data nebo pracovat s podmnožinu dat z **datovou sadu**. Při kopírování **datovou sadu**, můžete:  
  
-   Vytvořit přesnou kopii **datovou sadu**, včetně schéma, data, informace o stavu řádku a verze řádku.  
  
-   Vytvoření **datovou sadu** obsahující schéma z existující **datovou sadu**, ale pouze řádky, které byly upraveny. Vrátí všechny řádky, které byly upraveny, nebo zadat konkrétní **DataRowState**. Další informace o stavy řádků najdete v tématu [stavy řádků a verze řádku](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
-   Zkopírujte schéma nebo relační struktura z **datovou sadu** pouze bez kopírování žádné řádky. Řádky se dají importovat do existující <xref:System.Data.DataTable> pomocí <xref:System.Data.DataTable.ImportRow%2A>.  
  
 Chcete-li vytvořit přesný kopii **datovou sadu** zahrnující schéma a data, použijte <xref:System.Data.DataSet.Copy%2A> metodu **datovou sadu**. Následující příklad kódu ukazuje, jak vytvořit přesnou kopii **datovou sadu**.  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 Vytvořit kopii **datovou sadu** schéma a pouze na data představující, který obsahuje **Added**, **změněné**, nebo **odstraněné** řádky, použijte <xref:System.Data.DataSet.GetChanges%2A> metodu **datovou sadu**. Můžete také použít **GetChanges –** vrátit pouze sloupce se stavem zadaný řádek předáním **DataRowState** hodnota při volání metody **GetChanges –**. Následující příklad kódu ukazuje, jak předat **DataRowState** při volání metody **GetChanges –**.  
  
```vb  
' Copy all changes.  
Dim changeDataSet As DataSet = customerDataSet.GetChanges()  
' Copy only new rows.  
Dim addedDataSetAs DataSet = _  
    customerDataSet.GetChanges(DataRowState.Added)  
```  
  
```csharp  
// Copy all changes.  
DataSet changeDataSet = customerDataSet.GetChanges();  
// Copy only new rows.  
DataSet addedDataSet= customerDataSet.GetChanges(DataRowState.Added);  
```  
  
 Vytvořit kopii **datovou sadu** zahrnující schéma, použijte <xref:System.Data.DataSet.Clone%2A> metodu **datovou sadu**. Můžete také přidat existující řádky do klonované **datovou sadu** pomocí **ImportRow** metodu **DataTable**. **ImportRow** přidá data, stav řádku a informace o verzi řádek zadané tabulky. Hodnoty ve sloupcích se přidají jenom kde odpovídá názvu sloupce a data typ je kompatibilní.  
  
 Následující příklad kódu vytvoří klon **datovou sadu** a potom přidá řádky z původní **datovou sadu** k **zákazníci** tabulky v **datové sady**  klon pro zákazníky, kde **země** sloupec obsahuje hodnotu "Německo".  
  
```vb  
Dim customerDataSet As New DataSet  
        customerDataSet.Tables.Add(New DataTable("Customers"))  
        customerDataSet.Tables("Customers").Columns.Add("Name", GetType(String))  
        customerDataSet.Tables("Customers").Columns.Add("CountryRegion", GetType(String))  
        customerDataSet.Tables("Customers").Rows.Add("Juan", "Spain")  
        customerDataSet.Tables("Customers").Rows.Add("Johann", "Germany")  
        customerDataSet.Tables("Customers").Rows.Add("John", "UK")  
  
Dim germanyCustomers As DataSet = customerDataSet.Clone()  
  
Dim copyRows() As DataRow = _  
  customerDataSet.Tables("Customers").Select("CountryRegion = 'Germany'")  
  
Dim customerTable As DataTable = germanyCustomers.Tables("Customers")  
Dim copyRow As DataRow  
  
For Each copyRow In copyRows  
  customerTable.ImportRow(copyRow)  
Next  
```  
  
```csharp  
DataSet customerDataSet = new DataSet();  
customerDataSet.Tables.Add(new DataTable("Customers"));  
customerDataSet.Tables["Customers"].Columns.Add("Name", typeof(string));  
customerDataSet.Tables["Customers"].Columns.Add("CountryRegion", typeof(string));  
customerDataSet.Tables["Customers"].Rows.Add("Juan", "Spain");  
customerDataSet.Tables["Customers"].Rows.Add("Johann", "Germany");  
customerDataSet.Tables["Customers"].Rows.Add("John", "UK");  
  
DataSet germanyCustomers = customerDataSet.Clone();  
  
DataRow[] copyRows =   
  customerDataSet.Tables["Customers"].Select("CountryRegion = 'Germany'");  
  
DataTable customerTable = germanyCustomers.Tables["Customers"];  
  
foreach (DataRow copyRow in copyRows)  
  customerTable.ImportRow(copyRow);  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
