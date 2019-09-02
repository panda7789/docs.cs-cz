---
title: Kopírování obsahu datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: f60ef817773b6234b19856bfc0727eedb67e113e
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205173"
---
# <a name="copying-dataset-contents"></a>Kopírování obsahu datové sady
Můžete vytvořit kopii <xref:System.Data.DataSet> , abyste mohli pracovat s daty bez ovlivnění původních dat nebo pracovat s podmnožinou dat z **datové sady**. Když kopírujete **datovou sadu**, můžete:  
  
- Vytvořte přesnou kopii **datové sady**, včetně schématu, dat, informací o stavu řádku a verze řádků.  
  
- Vytvořte **datovou sadu** , která obsahuje schéma existující **datové sady**, ale pouze řádky, které byly změněny. Můžete vrátit všechny řádky, které byly změněny, nebo zadat konkrétní **nezměněnou DataRowState**. Další informace o stavech řádků najdete v tématu [stavy řádků a verze řádků](row-states-and-row-versions.md).  
  
- Zkopírujte schéma nebo relační strukturu pouze pro **datovou sadu** bez kopírování řádků. Řádky lze importovat do existujícího <xref:System.Data.DataTable> objektu using. <xref:System.Data.DataTable.ImportRow%2A>  
  
 Chcete-li vytvořit přesnou kopii **datové sady** , která obsahuje schéma i data, použijte <xref:System.Data.DataSet.Copy%2A> metodu **DataSet**. Následující příklad kódu ukazuje, jak vytvořit přesnou kopii **datové sady**.  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 Chcete-li vytvořit kopii **datové sady** , která obsahuje schéma a pouze data představující **přidané**, **upravené**nebo odstraněné řádky, použijte <xref:System.Data.DataSet.GetChanges%2A> metodu **DataSet**. Pomocí GetChanges můžete také vracet pouze řádky se zadaným stavem řádku předáním hodnoty **nezměněnou DataRowState** při volání metody GetChanges. Následující příklad kódu ukazuje, jak předat **nezměněnou DataRowState** při volání metody GetChanges.  
  
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
  
 Chcete-li vytvořit kopii **datové sady** , která obsahuje pouze schéma, použijte <xref:System.Data.DataSet.Clone%2A> metodu **DataSet**. Můžete také přidat existující řádky do klonované **datové sady** pomocí metody **ImportRow** **objektu DataTable**. **ImportRow** přidá informace o datech, stavu řádků a verzi řádku do zadané tabulky. Hodnoty sloupců jsou přidány pouze tam, kde se shodují název sloupce a datový typ je kompatibilní.  
  
 Následující příklad kódu vytvoří klon **datové sady** a potom přidá řádky z původní **datové sady** do tabulky Customers ( **zákazníci** ) ve klonu **datové sady** pro zákazníky, kde sloupec **země** má hodnotu "Německo". ".  
  
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
- [Datové sady, datové tabulky a datová zobrazení](index.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
