---
title: Vytvoření datové tabulky
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
ms.openlocfilehash: b56d2f8cd46f3184f1001c8bd6a70dbfc4968968
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937034"
---
# <a name="creating-a-datatable"></a>Vytvoření datové tabulky
, Který představuje jednu tabulku relačních dat v paměti, lze vytvořit a použít nezávisle, nebo mohou být použity jinými .NET Framework objekty, nejčastěji jako člen <xref:System.Data.DataSet>. <xref:System.Data.DataTable>  
  
 Objekt **DataTable** lze vytvořit pomocí příslušného konstruktoru **DataTable** . Můžete ji přidat do **datové sady** pomocí metody **Add** pro její přidání do kolekce **tabulek** objektu **DataTable** .  
  
 Můžete také vytvořit objekty **DataTable** v rámci **datové sady** pomocí metod **Fill** nebo **FillSchema** objektu **DataAdapter** nebo z předdefinovaného nebo odvozeného schématu XML pomocí **ReadXml**, **ReadXmlSchema** nebo metody **InferXmlSchema** **objektu DataSet**. Všimněte si, že poté, co jste přidali **DataTable** jako člena kolekce **Tables** jedné **datové sady**, nelze ji přidat do kolekce tabulek žádné jiné **datové sady**.  
  
 Při prvním vytvoření **objektu DataTable**nemá schéma (to znamená struktury). Chcete-li definovat schéma tabulky, je nutné vytvořit a přidat <xref:System.Data.DataColumn> objekty do kolekce **Columns** v tabulce. Můžete také definovat sloupec primárního klíče pro tabulku a vytvořit a přidat objekty **omezení** do kolekce **omezení** v tabulce. Po definování schématu pro **objekt DataTable**můžete do tabulky přidat řádky dat přidáním objektů **DataRow** do kolekce **řádků** tabulky.  
  
 Při vytváření <xref:System.Data.DataTable.TableName%2A> **objektu DataTable**není nutné zadávat hodnotu vlastnosti. vlastnost lze zadat v jinou dobu nebo ji můžete ponechat prázdnou. Pokud však přidáte tabulku bez hodnoty **TableName** do **datové sady**, bude se tabulce předávat přírůstkový výchozí název tabulky*N*, počínaje "Table" pro TABLE0.  
  
> [!NOTE]
> Doporučujeme vyhnout se konvenci pojmenování tabulky*N*při zadání hodnoty **TableName** , protože název, který zadáte, může být v konfliktu s existujícím názvem výchozí tabulky v **datové sadě**. Pokud zadaný název již existuje, je vyvolána výjimka.  
  
 Následující příklad vytvoří instanci objektu **DataTable** a přiřadí mu název "Customers".  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 Následující příklad vytvoří instanci **objektu DataTable** přidáním do kolekce **Tables** **objektu DataSet**.  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.DataTable>
- <xref:System.Data.DataTableCollection>
- [Datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [Naplnění datové sady z adaptéru dat](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)
- [Načtení datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [Načtení informací o schématu datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
