---
title: Dotazování na datové sady (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: bb64abcffdbbcd46dfb11b2564619c565e461436
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634778"
---
# <a name="querying-datasets-linq-to-dataset"></a><span data-ttu-id="cf431-102">Dotazování na datové sady (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="cf431-102">Querying DataSets (LINQ to DataSet)</span></span>
<span data-ttu-id="cf431-103">Po naplnění <xref:System.Data.DataSet> objektu daty můžete začít dotazovat se na něj.</span><span class="sxs-lookup"><span data-stu-id="cf431-103">After a <xref:System.Data.DataSet> object has been populated with data, you can begin querying it.</span></span> <span data-ttu-id="cf431-104">Formulace dotazů pomocí LINQ to DataSet je podobná použití LINQ (Language-Integrated Query) pro jiné zdroje dat s podporou LINQ.</span><span class="sxs-lookup"><span data-stu-id="cf431-104">Formulating queries with LINQ to DataSet is similar to using Language-Integrated Query (LINQ) against other LINQ-enabled data sources.</span></span> <span data-ttu-id="cf431-105">Nezapomeňte však, že pokud používáte dotazy LINQ přes objekt <xref:System.Data.DataSet>, dotazuje se na výčet objektů <xref:System.Data.DataRow> namísto výčtu vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="cf431-105">Remember, however, that when you use LINQ queries over a <xref:System.Data.DataSet> object, you're querying an enumeration of <xref:System.Data.DataRow> objects instead of an enumeration of a custom type.</span></span> <span data-ttu-id="cf431-106">To znamená, že můžete použít kterýkoli z členů třídy <xref:System.Data.DataRow> ve svých dotazech LINQ.</span><span class="sxs-lookup"><span data-stu-id="cf431-106">This means that you can use any of the members of the <xref:System.Data.DataRow> class in your LINQ queries.</span></span> <span data-ttu-id="cf431-107">To vám umožní vytvářet bohatě komplexní dotazy.</span><span class="sxs-lookup"><span data-stu-id="cf431-107">This lets you create rich, complex queries.</span></span>  
  
 <span data-ttu-id="cf431-108">Stejně jako u jiných implementací technologie LINQ můžete vytvářet LINQ to DataSet dotazy ve dvou různých formulářích: Syntaxe výrazů dotazů a syntaxe dotazů založených na metodách.</span><span class="sxs-lookup"><span data-stu-id="cf431-108">As with other implementations of LINQ, you can create LINQ to DataSet queries in two different forms: query expression syntax and method-based query syntax.</span></span> <span data-ttu-id="cf431-109">Pomocí syntaxe výrazu dotazu nebo syntaxe dotazu založeného na metodách můžete provádět dotazy na jednotlivé tabulky v <xref:System.Data.DataSet>, proti několika tabulkám v <xref:System.Data.DataSet>nebo k tabulkám ve typované <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="cf431-109">You can use query expression syntax or method-based query syntax to perform queries against single tables in a <xref:System.Data.DataSet>, against multiple tables in a <xref:System.Data.DataSet>, or against tables in a typed <xref:System.Data.DataSet>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cf431-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="cf431-110">In This Section</span></span>  
 [<span data-ttu-id="cf431-111">Dotazy na jednu tabulku</span><span class="sxs-lookup"><span data-stu-id="cf431-111">Single-Table Queries</span></span>](single-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="cf431-112">Popisuje, jak provádět dotazy na jednu tabulku.</span><span class="sxs-lookup"><span data-stu-id="cf431-112">Describes how to perform single-table queries.</span></span>  
  
 [<span data-ttu-id="cf431-113">Dotazy na křížovou tabulku</span><span class="sxs-lookup"><span data-stu-id="cf431-113">Cross-Table Queries</span></span>](cross-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="cf431-114">Popisuje postup provádění dotazů mezi tabulkami.</span><span class="sxs-lookup"><span data-stu-id="cf431-114">Describes how to perform cross-table queries.</span></span>  
  
 [<span data-ttu-id="cf431-115">Dotazy na typové datové sady</span><span class="sxs-lookup"><span data-stu-id="cf431-115">Querying Typed DataSets</span></span>](querying-typed-datasets.md)  
 <span data-ttu-id="cf431-116">Popisuje způsob dotazování typu <xref:System.Data.DataSet> objektů.</span><span class="sxs-lookup"><span data-stu-id="cf431-116">Describes how to query typed <xref:System.Data.DataSet> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf431-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cf431-117">See also</span></span>

- [<span data-ttu-id="cf431-118">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="cf431-118">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="cf431-119">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="cf431-119">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
