---
title: Kopírování obsahu datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: de13e07eb5c19b8beffa724fec4a128c418a4fed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151361"
---
# <a name="copying-dataset-contents"></a>Kopírování obsahu datové sady
Můžete vytvořit kopii, <xref:System.Data.DataSet> takže můžete pracovat s daty bez ovlivnění původních dat, nebo pracovat s podmnožinou dat z **datové sady**. Při kopírování **datové sady**můžete:  
  
- Vytvořte přesnou kopii **dataset**, včetně schématu, data, informace o stavu řádku a verze řádků.  
  
- Vytvořte **datovou sadu,** která obsahuje schéma existující **dataset**, ale pouze řádky, které byly změněny. Můžete vrátit všechny řádky, které byly změněny, nebo zadat konkrétní **DataRowState**. Další informace o stavech řádků naleznete v [tématu Stavy řádků a Verze řádků](row-states-and-row-versions.md).  
  
- Zkopírujte schéma nebo relační strukturu pouze **DataSet,** bez kopírování řádků. Řádky lze importovat do <xref:System.Data.DataTable> <xref:System.Data.DataTable.ImportRow%2A>existující pomocí .  
  
 Chcete-li vytvořit přesnou kopii **dataset,** který obsahuje schéma <xref:System.Data.DataSet.Copy%2A> a data, použijte metodu **DataSet**. Následující příklad kódu ukazuje, jak vytvořit přesnou kopii **DataSet**.  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 Chcete-li vytvořit kopii **datové sady,** která obsahuje schéma a pouze data představující řádky <xref:System.Data.DataSet.GetChanges%2A> **Přidané**, **Změněno**nebo **Odstraněno,** použijte metodu **DataSet**. Můžete také použít **GetChanges** vrátit pouze řádky se zadaným stavem řádku předáním **DataRowState** hodnotu při volání **GetChanges**. Následující příklad kódu ukazuje, jak předat **DataRowState** při volání **GetChanges**.  
  
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
  
 Chcete-li vytvořit kopii **dataset,** který obsahuje pouze <xref:System.Data.DataSet.Clone%2A> schéma, použijte metodu **DataSet**. Existující řádky můžete také přidat do klonované **datové sady** pomocí metody **ImportRow** **datatable**. **ImportRow** přidá data, stav řádku a informace o verzi řádku do zadané tabulky. Hodnoty sloupců jsou přidány pouze tam, kde se název sloupce shoduje a datový typ je kompatibilní.  
  
 Následující příklad kódu vytvoří klon **DataSet** a potom přidá řádky z původní **dataset** do tabulky **Zákazníci** v **dataset** klon pro zákazníky, kde sloupec **Země** má hodnotu "Německo".  
  
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

- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [Datové sady, datové tabulky a datová zobrazení](index.md)
- [Přehled ADO.NET](../ado-net-overview.md)
