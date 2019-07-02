---
title: Dotazy na datové sady (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: ec4ee345835294499f7ac9f665a9b79e2efc0f64
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504664"
---
# <a name="querying-datasets-linq-to-dataset"></a><span data-ttu-id="55d4b-102">Dotazy na datové sady (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="55d4b-102">Querying DataSets (LINQ to DataSet)</span></span>
<span data-ttu-id="55d4b-103">Po <xref:System.Data.DataSet> objekt naplněné daty, můžete začít ho dotazování.</span><span class="sxs-lookup"><span data-stu-id="55d4b-103">After a <xref:System.Data.DataSet> object has been populated with data, you can begin querying it.</span></span> <span data-ttu-id="55d4b-104">Formulování dotazy pomocí jazyka LINQ k datové sadě je podobný používání [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] proti jiné [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]– povolené zdroje.</span><span class="sxs-lookup"><span data-stu-id="55d4b-104">Formulating queries with LINQ to DataSet is similar to using [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] against other [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]-enabled data sources.</span></span> <span data-ttu-id="55d4b-105">Nezapomeňte však, že při použití [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] dotazuje přes <xref:System.Data.DataSet> objekt dotazujete výčet <xref:System.Data.DataRow> objekty namísto výčet vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="55d4b-105">Remember, however, that when you use [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] queries over a <xref:System.Data.DataSet> object you are querying an enumeration of <xref:System.Data.DataRow> objects, instead of an enumeration of a custom type.</span></span> <span data-ttu-id="55d4b-106">To znamená, že můžete použít některý z členů <xref:System.Data.DataRow> tříd ve vaší [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="55d4b-106">This means that you can use any of the members of the <xref:System.Data.DataRow> class in your [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="55d4b-107">Umožňuje vytvořit bohatě vybaveným a komplexní dotazy.</span><span class="sxs-lookup"><span data-stu-id="55d4b-107">This lets you to create rich, complex queries.</span></span>  
  
 <span data-ttu-id="55d4b-108">Stejně jako v jiných implementacích [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], můžete vytvoření LINQ to DataSet dotazy ve dvou různých formách: výraz syntaxe využívající dotazy a syntaxe dotazů založených na volání metody.</span><span class="sxs-lookup"><span data-stu-id="55d4b-108">As with other implementations of [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], you can create LINQ to DataSet queries in two different forms: query expression syntax and method-based query syntax.</span></span> <span data-ttu-id="55d4b-109">Můžete použít syntaxe výrazu dotazu nebo syntaxe dotazů založených na volání metody k provedení dotazů na jedné tabulky v <xref:System.Data.DataSet>, proti více tabulek v <xref:System.Data.DataSet>, nebo na tabulky v typovaného <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="55d4b-109">You can use query expression syntax or method-based query syntax to perform queries against single tables in a <xref:System.Data.DataSet>, against multiple tables in a <xref:System.Data.DataSet>, or against tables in a typed <xref:System.Data.DataSet>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="55d4b-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="55d4b-110">In This Section</span></span>  
 [<span data-ttu-id="55d4b-111">Dotazy na jednu tabulku</span><span class="sxs-lookup"><span data-stu-id="55d4b-111">Single-Table Queries</span></span>](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="55d4b-112">Popisuje, jak provádět dotazy na jednu tabulku.</span><span class="sxs-lookup"><span data-stu-id="55d4b-112">Describes how to perform single-table queries.</span></span>  
  
 [<span data-ttu-id="55d4b-113">Dotazy na křížovou tabulku</span><span class="sxs-lookup"><span data-stu-id="55d4b-113">Cross-Table Queries</span></span>](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="55d4b-114">Popisuje, jak provádět dotazy na křížovou tabulku.</span><span class="sxs-lookup"><span data-stu-id="55d4b-114">Describes how to perform cross-table queries.</span></span>  
  
 [<span data-ttu-id="55d4b-115">Dotazy na typové datové sady</span><span class="sxs-lookup"><span data-stu-id="55d4b-115">Querying Typed DataSets</span></span>](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 <span data-ttu-id="55d4b-116">Popisuje, jak provádět dotazy zadali <xref:System.Data.DataSet> objekty.</span><span class="sxs-lookup"><span data-stu-id="55d4b-116">Describes how to query typed <xref:System.Data.DataSet> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55d4b-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55d4b-117">See also</span></span>

- [<span data-ttu-id="55d4b-118">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="55d4b-118">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="55d4b-119">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="55d4b-119">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
