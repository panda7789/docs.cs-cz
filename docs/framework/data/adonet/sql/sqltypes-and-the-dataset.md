---
title: SqlTypes a datová sada
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
ms.openlocfilehash: a218a8e0fe3d2c17a0f09a40645c7b3ad26fb5ed
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072698"
---
# <a name="sqltypes-and-the-dataset"></a>SqlTypes a datová sada
ADO.NET 2.0 zavedené rozšířenou podporu typu `DataSet` prostřednictvím <xref:System.Data.SqlTypes> oboru názvů. Typy v <xref:System.Data.SqlTypes> poskytují datové typy jako typy dat v databázi serveru SQL Server pomocí stejné sémantiky a přesnosti. Každý datový typ ve <xref:System.Data.SqlTypes> má odpovídající datový typ v systému SQL Server se stejnou reprezentaci podkladová data.  
  
 Pomocí <xref:System.Data.SqlTypes> přímo <xref:System.Data.DataSet> při práci s datovými typy SQL serveru poskytuje několik výhod. <xref:System.Data.SqlTypes> podporuje stejnou sémantiku jako nativní datové typy serveru SQL Server. Zadáním jednoho z <xref:System.Data.SqlTypes> v definici <xref:System.Data.DataColumn> eliminuje ztrátou přesnosti, která může dojít, pokud převod desítkový nebo číselný datový typy na jeden z common language runtime (CLR) datové typy.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Data.DataTable> objekt explicitně definovat <xref:System.Data.DataColumn> datové typy s použitím <xref:System.Data.SqlTypes> místo typů CLR. Vloží kód <xref:System.Data.DataTable> s daty z tabulky Sales.SalesOrderDetail databáze AdventureWorks v systému SQL Server. Výstup zobrazí v okně konzoly se zobrazí typ dat každého sloupce a hodnoty získány z SQL serveru.  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Mapování datových typů SQL Serveru](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)
- [Konfigurace parametrů a datové typy parametrů](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
