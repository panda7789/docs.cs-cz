---
title: Přidání sloupců do datové tabulky
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
ms.openlocfilehash: 105537a5fccef6de7266407c78cc915f8c5d8678
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204056"
---
# <a name="adding-columns-to-a-datatable"></a>Přidání sloupců do datové tabulky
Obsahuje kolekci objektů, na které odkazuje vlastnost Columns v tabulce. <xref:System.Data.DataTable> <xref:System.Data.DataColumn> Tato kolekce sloupců, spolu s omezeními, definuje schéma nebo strukturu tabulky.  
  
 Objekty **DataColumn** lze vytvořit v tabulce pomocí konstruktoru DataColumn nebo voláním metody **Add** vlastnosti Columns tabulky, která je <xref:System.Data.DataColumnCollection>. Metoda **Add** akceptuje volitelné argumenty **ColumnName**, **DataType**a **Expression** a vytvoří nový datový **sloupec** jako člena kolekce. Přijímá také existující objekt **DataColumn** a přidává ho do kolekce a v případě potřeby vrátí odkaz na přidaný DataColumn . Vzhledem k tomu, že objekty **DataTable** nejsou specifické pro žádný zdroj dat, .NET Framework typy se používají při zadávání datového typu **DataColumn**.  
  
 Následující příklad přidá čtyři sloupce do **objektu DataTable**.  
  
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
  
 V příkladu si všimněte, že vlastnosti pro sloupec **custid** jsou nastaveny tak, aby nepovolovaly hodnoty **DBNull** a omezily hodnoty tak, aby byly jedinečné. Pokud však definujete sloupec **custid** jako sloupec primárního klíče tabulky, vlastnost **AllowDBNull** bude automaticky nastavena na **hodnotu false** a vlastnost **Unique** bude automaticky nastavena na **hodnotu true**. Další informace najdete v tématu [Definování primárních klíčů](defining-primary-keys.md).  
  
> [!CAUTION]
> Pokud pro sloupec není zadán název sloupce, sloupec má při přidání do objektu DataColumnCollection přírůstkový výchozí název sloupce*N,* který začíná na "Sloupec1". Doporučujeme vyhnout se konvenci pojmenování "Column*N*" při zadání názvu sloupce, protože zadané jméno může být v konfliktu s existujícím výchozím názvem sloupce v objektu DataColumnCollection. Pokud zadaný název již existuje, je vyvolána výjimka.  
  
 Pokud používáte <xref:System.Xml.Linq.XElement> <xref:System.Data.DataColumn.DataType%2A> jako<xref:System.Data.DataColumn> v ,<xref:System.Data.DataTable>serializace XML nebude při čtení dat fungovat. Například pokud napíšete <xref:System.Xml.XmlDocument> `DataTable.WriteXml` metodu pomocí metody, po serializaci do XML je <xref:System.Xml.Linq.XElement>další nadřazený uzel v. Chcete-li tento problém obejít, <xref:System.Data.SqlTypes.SqlXml> použijte typ <xref:System.Xml.Linq.XElement>místo. `ReadXml`a `WriteXml` funguje správně s <xref:System.Data.SqlTypes.SqlXml>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataTable>
- [Definice schématu datové tabulky](datatable-schema-definition.md)
- [Datové tabulky](datatables.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
