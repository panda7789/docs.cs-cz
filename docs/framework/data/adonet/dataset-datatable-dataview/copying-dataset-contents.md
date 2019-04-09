---
title: Kopírování obsahu datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: cb2a172ac4e6a0ce4852f4c7cf7044583d9ab6c4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077757"
---
# <a name="copying-dataset-contents"></a>Kopírování obsahu datové sady
Můžete vytvořit kopii <xref:System.Data.DataSet> tak, aby můžete pracovat s daty, aniž by to ovlivnilo původní data ani pracovní obsahující jenom určitou podmnožinu dat z **datovou sadu**. Při kopírování **datovou sadu**, můžete:  
  
-   Vytvoření přesnou kopii **datovou sadu**, včetně schéma, data, informace o stavu řádků a verze řádků.  
  
-   Vytvoření **datovou sadu** , která obsahuje schéma z existujícího **datovou sadu**, ale pouze řádky, které byly změněny. Vrátí všechny řádky, které byly změněny, nebo zadat konkrétní **hodnotou DataRowState**. Další informace o stavy řádků, naleznete v tématu [stavy řádků a verze řádků](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
-   Kopie schématu nebo relační struktury **datovou sadu** pouze, bez kopírování žádné řádky. Řádky se dají importovat do existující <xref:System.Data.DataTable> pomocí <xref:System.Data.DataTable.ImportRow%2A>.  
  
 K vytvoření přesnou kopii **datovou sadu** , který obsahuje schéma a data, použijte <xref:System.Data.DataSet.Copy%2A> metodu **datovou sadu**. Následující příklad kódu ukazuje, jak vytvořit přesnou kopii **datovou sadu**.  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 Chcete-li vytvořit kopii **datovou sadu** , který obsahuje schéma a pouze na data představující **přidané**, **změněné**, nebo **odstraněné** řádků, použijte <xref:System.Data.DataSet.GetChanges%2A> metodu **datovou sadu**. Můžete také použít **GetChanges –** vrátit pouze řádky se stavem zadaný řádek tím, že předáte **hodnotou DataRowState** hodnotu při volání metody **GetChanges –**. Následující příklad kódu ukazuje, jak předat **hodnotou DataRowState** při volání metody **GetChanges –**.  
  
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
  
 Chcete-li vytvořit kopii **datovou sadu** , který obsahuje pouze schéma, použijte <xref:System.Data.DataSet.Clone%2A> metodu **datovou sadu**. Můžete také přidat existující řádky do klonované **datovou sadu** pomocí **ImportRow** metodu **DataTable**. **ImportRow** přidá do zadané tabulky dat, stavu řádků a informace o verzi řádku. Hodnoty sloupce jsou přidány, pouze pokud odpovídá názvu sloupce a data typ není kompatibilní.  
  
 Následující příklad kódu vytvoří klon **datovou sadu** a pak přidá řádky z původní **datovou sadu** k **zákazníkům** tabulku v **datové sady**  klonování pro zákazníky, kde **země** sloupec má hodnotu "Germany".  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
