---
title: SqlTypes a datová sada
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
ms.openlocfilehash: dea5a2017479443cb747d31e253c1c83585ddd09
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791496"
---
# <a name="sqltypes-and-the-dataset"></a>SqlTypes a datová sada
ADO.NET 2,0 představilo rozšířenou podporu typu `DataSet` pro <xref:System.Data.SqlTypes> obor názvů. Typy v <xref:System.Data.SqlTypes> jsou navrženy tak, aby poskytovaly datové typy se stejnou sémantikou a přesností jako datové typy v databázi SQL Server. Každý datový typ v <xref:System.Data.SqlTypes> v má v SQL Server ekvivalentní datový typ se stejnou základní datovou reprezentací.  
  
 Použití <xref:System.Data.SqlTypes> přímo v rámci <xref:System.Data.DataSet> conf přináší několik výhod při práci s SQL Servermi datovými typy. <xref:System.Data.SqlTypes>podporuje stejnou sémantiku jako SQL Server nativní datové typy. Zadání jedné z <xref:System.Data.SqlTypes> z definice a <xref:System.Data.DataColumn> eliminuje ztrátu přesnosti, ke které může dojít při převodu desítkových nebo číselných datových typů na jeden z datových typů modulu CLR (Common Language Runtime).  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Data.DataTable> objekt, explicitní <xref:System.Data.DataColumn> definování datových typů pomocí <xref:System.Data.SqlTypes> typu namísto CLR. Kód vyplní <xref:System.Data.DataTable> data z tabulky Sales. SalesOrderDetail v databázi AdventureWorks v SQL Server. Výstup zobrazený v okně konzoly zobrazuje datový typ každého sloupce a hodnoty načtené z SQL Server.  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Mapování datových typů SQL Serveru](../sql-server-data-type-mappings.md)
- [Konfigurace parametrů a datové typy parametrů](../configuring-parameters-and-parameter-data-types.md)
- [Přehled ADO.NET](../ado-net-overview.md)
