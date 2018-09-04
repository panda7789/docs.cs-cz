---
title: SqlTypes a datová sada
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
ms.openlocfilehash: fe00e669449d40320a2038697976423db83ade5b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43511544"
---
# <a name="sqltypes-and-the-dataset"></a><span data-ttu-id="ad992-102">SqlTypes a datová sada</span><span class="sxs-lookup"><span data-stu-id="ad992-102">SqlTypes and the DataSet</span></span>
<span data-ttu-id="ad992-103">ADO.NET 2.0 zavedené rozšířenou podporu typu `DataSet` prostřednictvím <xref:System.Data.SqlTypes> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ad992-103">ADO.NET 2.0 introduced enhanced type support for the `DataSet` through the  <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="ad992-104">Typy v <xref:System.Data.SqlTypes> poskytují datové typy jako typy dat v databázi serveru SQL Server pomocí stejné sémantiky a přesnosti.</span><span class="sxs-lookup"><span data-stu-id="ad992-104">The types in <xref:System.Data.SqlTypes> are designed to provide data types with the same semantics and precision as the data types in a SQL Server database.</span></span> <span data-ttu-id="ad992-105">Každý datový typ ve <xref:System.Data.SqlTypes> má odpovídající datový typ v systému SQL Server se stejnou reprezentaci podkladová data.</span><span class="sxs-lookup"><span data-stu-id="ad992-105">Each data type in <xref:System.Data.SqlTypes> has an equivalent data type in SQL Server, with the same underlying data representation.</span></span>  
  
 <span data-ttu-id="ad992-106">Pomocí <xref:System.Data.SqlTypes> přímo <xref:System.Data.DataSet> při práci s datovými typy SQL serveru poskytuje několik výhod.</span><span class="sxs-lookup"><span data-stu-id="ad992-106">Using <xref:System.Data.SqlTypes> directly in a <xref:System.Data.DataSet> confers several benefits when working with SQL Server data types.</span></span> <span data-ttu-id="ad992-107"><xref:System.Data.SqlTypes> podporuje stejnou sémantiku jako nativní datové typy serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ad992-107"><xref:System.Data.SqlTypes> supports the same semantics as SQL Server native data types.</span></span> <span data-ttu-id="ad992-108">Zadáním jednoho z <xref:System.Data.SqlTypes> v definici <xref:System.Data.DataColumn> eliminuje ztrátou přesnosti, která může dojít, pokud převod desítkový nebo číselný datový typy na jeden z common language runtime (CLR) datové typy.</span><span class="sxs-lookup"><span data-stu-id="ad992-108">Specifying one of the <xref:System.Data.SqlTypes> in the definition of a <xref:System.Data.DataColumn> eliminates the loss of precision that can occur when converting decimal or numeric data types to one of the common language runtime (CLR) data types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad992-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="ad992-109">Example</span></span>  
 <span data-ttu-id="ad992-110">Následující příklad vytvoří <xref:System.Data.DataTable> objekt explicitně definovat <xref:System.Data.DataColumn> datové typy s použitím <xref:System.Data.SqlTypes> místo typů CLR.</span><span class="sxs-lookup"><span data-stu-id="ad992-110">The following example creates a <xref:System.Data.DataTable> object, explicitly defining the <xref:System.Data.DataColumn> data types by using <xref:System.Data.SqlTypes> instead of CLR types.</span></span> <span data-ttu-id="ad992-111">Vloží kód <xref:System.Data.DataTable> s daty z tabulky Sales.SalesOrderDetail databáze AdventureWorks v systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ad992-111">The code fills the <xref:System.Data.DataTable> with data from the Sales.SalesOrderDetail table in the AdventureWorks database in SQL Server.</span></span> <span data-ttu-id="ad992-112">Výstup zobrazí v okně konzoly se zobrazí typ dat každého sloupce a hodnoty získány z SQL serveru.</span><span class="sxs-lookup"><span data-stu-id="ad992-112">The output displayed in the console window shows the data type of each column, and the values retrieved from SQL Server.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ad992-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="ad992-113">See Also</span></span>  
 [<span data-ttu-id="ad992-114">Mapování datových typů SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="ad992-114">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [<span data-ttu-id="ad992-115">Konfigurace parametrů a datové typy parametrů</span><span class="sxs-lookup"><span data-stu-id="ad992-115">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [<span data-ttu-id="ad992-116">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="ad992-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
