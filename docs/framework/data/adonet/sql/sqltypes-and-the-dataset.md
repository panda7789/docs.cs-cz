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
# <a name="sqltypes-and-the-dataset"></a><span data-ttu-id="a87e3-102">SqlTypes a datová sada</span><span class="sxs-lookup"><span data-stu-id="a87e3-102">SqlTypes and the DataSet</span></span>
<span data-ttu-id="a87e3-103">ADO.NET 2,0 představilo rozšířenou podporu typu `DataSet` pro <xref:System.Data.SqlTypes> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="a87e3-103">ADO.NET 2.0 introduced enhanced type support for the `DataSet` through the  <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="a87e3-104">Typy v <xref:System.Data.SqlTypes> jsou navrženy tak, aby poskytovaly datové typy se stejnou sémantikou a přesností jako datové typy v databázi SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a87e3-104">The types in <xref:System.Data.SqlTypes> are designed to provide data types with the same semantics and precision as the data types in a SQL Server database.</span></span> <span data-ttu-id="a87e3-105">Každý datový typ v <xref:System.Data.SqlTypes> v má v SQL Server ekvivalentní datový typ se stejnou základní datovou reprezentací.</span><span class="sxs-lookup"><span data-stu-id="a87e3-105">Each data type in <xref:System.Data.SqlTypes> has an equivalent data type in SQL Server, with the same underlying data representation.</span></span>  
  
 <span data-ttu-id="a87e3-106">Použití <xref:System.Data.SqlTypes> přímo v rámci <xref:System.Data.DataSet> conf přináší několik výhod při práci s SQL Servermi datovými typy.</span><span class="sxs-lookup"><span data-stu-id="a87e3-106">Using <xref:System.Data.SqlTypes> directly in a <xref:System.Data.DataSet> confers several benefits when working with SQL Server data types.</span></span> <span data-ttu-id="a87e3-107"><xref:System.Data.SqlTypes>podporuje stejnou sémantiku jako SQL Server nativní datové typy.</span><span class="sxs-lookup"><span data-stu-id="a87e3-107"><xref:System.Data.SqlTypes> supports the same semantics as SQL Server native data types.</span></span> <span data-ttu-id="a87e3-108">Zadání jedné z <xref:System.Data.SqlTypes> z definice a <xref:System.Data.DataColumn> eliminuje ztrátu přesnosti, ke které může dojít při převodu desítkových nebo číselných datových typů na jeden z datových typů modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="a87e3-108">Specifying one of the <xref:System.Data.SqlTypes> in the definition of a <xref:System.Data.DataColumn> eliminates the loss of precision that can occur when converting decimal or numeric data types to one of the common language runtime (CLR) data types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a87e3-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="a87e3-109">Example</span></span>  
 <span data-ttu-id="a87e3-110">Následující příklad vytvoří <xref:System.Data.DataTable> objekt, explicitní <xref:System.Data.DataColumn> definování datových typů pomocí <xref:System.Data.SqlTypes> typu namísto CLR.</span><span class="sxs-lookup"><span data-stu-id="a87e3-110">The following example creates a <xref:System.Data.DataTable> object, explicitly defining the <xref:System.Data.DataColumn> data types by using <xref:System.Data.SqlTypes> instead of CLR types.</span></span> <span data-ttu-id="a87e3-111">Kód vyplní <xref:System.Data.DataTable> data z tabulky Sales. SalesOrderDetail v databázi AdventureWorks v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a87e3-111">The code fills the <xref:System.Data.DataTable> with data from the Sales.SalesOrderDetail table in the AdventureWorks database in SQL Server.</span></span> <span data-ttu-id="a87e3-112">Výstup zobrazený v okně konzoly zobrazuje datový typ každého sloupce a hodnoty načtené z SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a87e3-112">The output displayed in the console window shows the data type of each column, and the values retrieved from SQL Server.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a87e3-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a87e3-113">See also</span></span>

- [<span data-ttu-id="a87e3-114">Mapování datových typů SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="a87e3-114">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="a87e3-115">Konfigurace parametrů a datové typy parametrů</span><span class="sxs-lookup"><span data-stu-id="a87e3-115">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="a87e3-116">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a87e3-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
