---
title: Přidání sloupců do datové tabulky
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
ms.openlocfilehash: 2e7008f6693d7d76520a7ff6ae9172e28e4990c2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207003"
---
# <a name="adding-columns-to-a-datatable"></a>Přidání sloupců do datové tabulky
A <xref:System.Data.DataTable> obsahuje kolekci <xref:System.Data.DataColumn> objekty odkazují **sloupce** vlastnost tabulky. Tuto sadu sloupců, společně s omezeními, definuje schéma a struktura tabulky.  
  
 Vytvoříte **DataColumn** objektů v rámci tabulky pomocí **DataColumn** konstruktoru, nebo pomocí volání **přidat** metodu **sloupce**vlastnost tabulky, který je <xref:System.Data.DataColumnCollection>. **Přidat** metoda přijímá volitelný **Názevsloupce**, **datový typ**, a **výraz** argumenty a vytvoří novou  **Objekt DataColumn** jako člena kolekce. Také přijímá existující **DataColumn** objektu a přidá jej do kolekce a vrátí odkaz na přidaném **DataColumn** pokud o to požádá. Protože **DataTable** objekty nejsou specifické pro libovolný zdroj dat, typy rozhraní .NET Framework se používají při zadávání datového typu **DataColumn**.  
  
 Následující příklad přidá čtyři sloupce **DataTable**.  
  
```vb  
Dim workTable As DataTable = New DataTable("Customers")  
  
Dim workCol As DataColumn = workTable.Columns.Add( _  
    "CustID", Type.GetType("System.Int32"))  
workCol.AllowDBNull = false  
workCol.Unique = true  
  
workTable.Columns.Add("CustLName", Type.GetType("System.String"))  
workTable.Columns.Add("CustFName", Type.GetType("System.String"))  
workTable.Columns.Add("Purchases", Type.GetType("System.Double"))  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
  
DataColumn workCol = workTable.Columns.Add("CustID", typeof(Int32));  
workCol.AllowDBNull = false;  
workCol.Unique = true;  
  
workTable.Columns.Add("CustLName", typeof(String));  
workTable.Columns.Add("CustFName", typeof(String));  
workTable.Columns.Add("Purchases", typeof(Double));  
```  
  
 V příkladu, Všimněte si, že vlastnosti **CustID** sloupec je nastaven na nepovoluje **DBNull** hodnoty a k omezení hodnoty, které mají být jedinečné. Ale pokud definujete **CustID** sloupec jako sloupec primárního klíče tabulky, **AllowDBNull** vlastnost bude automaticky nastavena **false** a **Jedinečné** vlastnost bude automaticky nastavena **true**. Další informace najdete v tématu [definování primárních klíčů](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
> [!CAUTION]
>  Pokud není zadán název sloupce pro sloupec, ve sloupci je předána na přírůstkové výchozí název sloupce*N,* počínaje "Sloupec1", když se přidá do **DataColumnCollection**. Doporučujeme vám, že byste se vyhnout zásadu vytváření názvů "sloupce*N*" když zadáte název sloupce, vzhledem k tomu, že zadáte název dojít ke konfliktu s existujícím názvem sloupce výchozí v **DataColumnCollection**. Pokud zadaný název již existuje, je vyvolána výjimka.  
  
 Pokud používáte <xref:System.Xml.Linq.XElement> jako <xref:System.Data.DataColumn.DataType%2A> z <xref:System.Data.DataColumn> v <xref:System.Data.DataTable>, serializace XML nebude fungovat, pokud čtení v datech. Například, pokud je vypsat <xref:System.Xml.XmlDocument> pomocí `DataTable.WriteXml` metoda po serializace za účelem je do další nadřazeného uzlu v XML <xref:System.Xml.Linq.XElement>. Chcete-li tento problém obejít, použijte <xref:System.Data.SqlTypes.SqlXml> zadejte místo <xref:System.Xml.Linq.XElement>. `ReadXml` a `WriteXml` fungují správně s <xref:System.Data.SqlTypes.SqlXml>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataTable>
- [Definice schématu datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [Datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
