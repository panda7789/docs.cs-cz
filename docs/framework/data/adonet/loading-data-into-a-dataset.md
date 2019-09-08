---
title: Načtení dat do datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
ms.openlocfilehash: 53f0f5a589a0033c9612f0465dff090ab04e3fc4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794953"
---
# <a name="loading-data-into-a-dataset"></a><span data-ttu-id="06e80-102">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="06e80-102">Loading Data Into a DataSet</span></span>
<span data-ttu-id="06e80-103">Předtím, než bude možné dotazovat na LINQ to DataSet, musí být objektnejprvevyplněn.<xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="06e80-103">A <xref:System.Data.DataSet> object must first be populated before you can query over it with LINQ to DataSet.</span></span> <span data-ttu-id="06e80-104">Existuje několik různých způsobů, jak naplnit <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="06e80-104">There are several different ways to populate the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="06e80-105">Například můžete použít [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] k dotazování databáze a načtení výsledků <xref:System.Data.DataSet>do.</span><span class="sxs-lookup"><span data-stu-id="06e80-105">For example, you can use [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] to query the database and load the results into the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="06e80-106">Další informace najdete v tématu [LINQ to SQL](./sql/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="06e80-106">For more information, see [LINQ to SQL](./sql/linq/index.md).</span></span>  
  
 <span data-ttu-id="06e80-107">Dalším běžným způsobem načtení dat do <xref:System.Data.DataSet> je <xref:System.Data.Common.DataAdapter> použít třídu k načtení dat z databáze.</span><span class="sxs-lookup"><span data-stu-id="06e80-107">Another common way to load data into a <xref:System.Data.DataSet> is to use the <xref:System.Data.Common.DataAdapter> class to retrieve data from the database.</span></span> <span data-ttu-id="06e80-108">To je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="06e80-108">This is illustrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06e80-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="06e80-109">Example</span></span>  
 <span data-ttu-id="06e80-110">V tomto příkladu se <xref:System.Data.Common.DataAdapter> používá k dotazování databáze AdventureWorks na informace o prodeji z roku 2002 a výsledky se načítají <xref:System.Data.DataSet>do.</span><span class="sxs-lookup"><span data-stu-id="06e80-110">This example uses a <xref:System.Data.Common.DataAdapter> to query the AdventureWorks database for sales information from the year 2002, and loads the results into a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="06e80-111">Po naplnění můžete do <xref:System.Data.DataSet> něj zapisovat dotazy pomocí LINQ to DataSet.</span><span class="sxs-lookup"><span data-stu-id="06e80-111">After the <xref:System.Data.DataSet> has been populated, you can write queries against it by using LINQ to DataSet.</span></span> <span data-ttu-id="06e80-112">Metoda v tomto příkladu se používá v příkladech dotazů v [LINQ to DataSetch příkladech.](linq-to-dataset-examples.md) `FillDataSet`</span><span class="sxs-lookup"><span data-stu-id="06e80-112">The `FillDataSet` method in this example is used in the example queries in [LINQ to DataSet Examples](linq-to-dataset-examples.md).</span></span> <span data-ttu-id="06e80-113">Další informace najdete v tématu [dotazování na datové sady](querying-datasets-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="06e80-113">For more information, see [Querying DataSets](querying-datasets-linq-to-dataset.md).</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a><span data-ttu-id="06e80-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="06e80-114">See also</span></span>

- [<span data-ttu-id="06e80-115">Přehled LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="06e80-115">LINQ to DataSet Overview</span></span>](linq-to-dataset-overview.md)
- [<span data-ttu-id="06e80-116">Dotazy na datové sady</span><span class="sxs-lookup"><span data-stu-id="06e80-116">Querying DataSets</span></span>](querying-datasets-linq-to-dataset.md)
- [<span data-ttu-id="06e80-117">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="06e80-117">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
