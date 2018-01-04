---
title: "Přidávání sloupců do DataTable"
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
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 423b9ed389a5a3750c8e9b0339e0887d6b650741
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="adding-columns-to-a-datatable"></a>Přidávání sloupců do DataTable
A <xref:System.Data.DataTable> obsahuje kolekci <xref:System.Data.DataColumn> objekty odkazuje **sloupce** vlastnosti tabulky. Tato kolekce sloupců, společně s omezeními, definuje schéma a struktura tabulky.  
  
 Vytvoříte **DataColumn** objektů v rámci tabulky pomocí **DataColumn** konstruktoru, nebo voláním **přidat** metodu **sloupce**vlastnost tabulky, který je <xref:System.Data.DataColumnCollection>. **Přidat** metoda přijímá volitelný **ColumnName**, **datový typ**, a **výraz** argumenty a vytvoří novou  **DataColumn** jako člena kolekce. Také přijímá existující **DataColumn** objektu a přidá do kolekce a vrátí odkaz na přidaném **DataColumn** Pokud požadovaný. Protože **DataTable** objekty nejsou specifické pro libovolný zdroj dat, typy rozhraní .NET Framework se používají při zadávání datový typ **DataColumn**.  
  
 Následující příklad přidá čtyři sloupce, abyste **DataTable**.  
  
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
  
 V příkladu, Všimněte si, že vlastnosti **CustID** není povolena nastavení sloupec **DBNull** hodnoty a omezit hodnoty, které mají být jedinečné. Ale pokud definujete **CustID** sloupec jako sloupec primárního klíče tabulky **AllowDBNull** vlastnost bude automaticky nastavena **false** a **Jedinečný** vlastnost bude automaticky nastavena **true**. Další informace najdete v tématu [definování primárních klíčů](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
> [!CAUTION]
>  Pokud je název sloupce není zadaný pro sloupec, sloupec je uveden přírůstkové výchozí název sloupce*N,* počínaje "Column1", když je přidán do **DataColumnCollection**. Doporučujeme, abyste se zabránilo pojmenovávací konvenci "sloupec*N*" Pokud zadáte název sloupce, protože název zadáte může dojít ke konfliktu s existujícím názvem sloupce výchozí v **DataColumnCollection**. Pokud se zadaným názvem již existuje, je vyvolána výjimka.  
  
 Pokud používáte <xref:System.Xml.Linq.XElement> jako <xref:System.Data.DataColumn.DataType%2A> z <xref:System.Data.DataColumn> v <xref:System.Data.DataTable>, serializace XML nebude fungovat při čtení v datech. Například, pokud je zapsat <xref:System.Xml.XmlDocument> pomocí `DataTable.WriteXml` metoda při serializaci do formátu XML je další nadřazený uzel v <xref:System.Xml.Linq.XElement>. Chcete-li tento problém obejít, použijte <xref:System.Data.SqlTypes.SqlXml> zadejte místo <xref:System.Xml.Linq.XElement>. `ReadXml`a `WriteXml` pracovní správně s <xref:System.Data.SqlTypes.SqlXml>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Data.DataColumn>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataTable>  
 [Definice schématu datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [Datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
