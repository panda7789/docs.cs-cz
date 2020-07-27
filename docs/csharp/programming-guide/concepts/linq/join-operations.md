---
title: :::no-loc(Join):::Operace (C#)
description: Spojení dvou zdrojů dat přidruží objekty k objektům, které sdílejí atribut napříč zdroji dat. Přečtěte si informace o metodách JOIN v rozhraní LINQ Framework v jazyce C#.
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
no-loc:
- ':::no-loc(Join):::'
- ':::no-loc(GroupJoin):::'
ms.openlocfilehash: 1b453f1752edf0cc126f8e27dbdd9e91ad9143f3
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165686"
---
# <a name="no-locjoin-operations-c"></a><span data-ttu-id="1411a-104">:::no-loc(Join):::Operace (C#)</span><span class="sxs-lookup"><span data-stu-id="1411a-104">:::no-loc(Join)::: Operations (C#)</span></span>

<span data-ttu-id="1411a-105">*Spojení* dvou zdrojů dat je přidružení objektů v jednom zdroji dat s objekty, které sdílejí společný atribut v jiném zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="1411a-105">A *join* of two data sources is the association of objects in one data source with objects that share a common attribute in another data source.</span></span>  
  
 <span data-ttu-id="1411a-106">:::no-loc(Join):::důležité operace v dotazech, které cílí na zdroje dat, u kterých se vzájemně vzájemně nevztahují, nemůžou následovat přímo.</span><span class="sxs-lookup"><span data-stu-id="1411a-106">:::no-loc(Join):::ing is an important operation in queries that target data sources whose relationships to each other cannot be followed directly.</span></span> <span data-ttu-id="1411a-107">V objektově orientovaném programování může to znamenat korelaci mezi objekty, které nejsou modelovány, jako je například zpětný směr jednosměrné relace.</span><span class="sxs-lookup"><span data-stu-id="1411a-107">In object-oriented programming, this could mean a correlation between objects that is not modeled, such as the backwards direction of a one-way relationship.</span></span> <span data-ttu-id="1411a-108">Příkladem jednosměrného vztahu je třída zákazníka, která má vlastnost typu City, ale třída City nemá vlastnost, která je kolekcí zákaznických objektů.</span><span class="sxs-lookup"><span data-stu-id="1411a-108">An example of a one-way relationship is a Customer class that has a property of type City, but the City class does not have a property that is a collection of Customer objects.</span></span> <span data-ttu-id="1411a-109">Pokud máte seznam objektů City a chcete najít všechny zákazníky v jednotlivých městech, můžete je najít pomocí operace JOIN.</span><span class="sxs-lookup"><span data-stu-id="1411a-109">If you have a list of City objects and you want to find all the customers in each city, you could use a join operation to find them.</span></span>  
  
 <span data-ttu-id="1411a-110">Metody join, které jsou k dispozici v rozhraní LINQ Framework, jsou <xref:System.Linq.Enumerable.:::no-loc(Join):::%2A> a <xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A> .</span><span class="sxs-lookup"><span data-stu-id="1411a-110">The join methods provided in the LINQ framework are <xref:System.Linq.Enumerable.:::no-loc(Join):::%2A> and <xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A>.</span></span> <span data-ttu-id="1411a-111">Tyto metody provádějí equijoins nebo spojení, které odpovídají dvěma zdrojům dat na základě rovnosti jejich klíčů.</span><span class="sxs-lookup"><span data-stu-id="1411a-111">These methods perform equijoins, or joins that match two data sources based on equality of their keys.</span></span> <span data-ttu-id="1411a-112">(Pro porovnání jazyk Transact-SQL podporuje operátory JOIN jiné než Equals, například operátor "menší než".) V terminologii relačních databází <xref:System.Linq.Enumerable.:::no-loc(Join):::%2A> implementuje interní spojení typ spojení, ve kterém jsou vráceny pouze objekty, které mají shodu v jiné sadě dat.</span><span class="sxs-lookup"><span data-stu-id="1411a-112">(For comparison, Transact-SQL supports join operators other than 'equals', for example the 'less than' operator.) In relational database terms, <xref:System.Linq.Enumerable.:::no-loc(Join):::%2A> implements an inner join, a type of join in which only those objects that have a match in the other data set are returned.</span></span> <span data-ttu-id="1411a-113">Tato <xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A> metoda nemá žádný přímý ekvivalent v rámci podmínek relační databáze, ale implementuje nadmnožinu vnitřních spojení a levé vnější spojení.</span><span class="sxs-lookup"><span data-stu-id="1411a-113">The <xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A> method has no direct equivalent in relational database terms, but it implements a superset of inner joins and left outer joins.</span></span> <span data-ttu-id="1411a-114">Levé vnější spojení je spojení, které vrátí každý prvek prvního (levého) zdroje dat, a to i v případě, že nemá žádné korelační prvky v jiném zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="1411a-114">A left outer join is a join that returns each element of the first (left) data source, even if it has no correlated elements in the other data source.</span></span>  
  
 <span data-ttu-id="1411a-115">Následující ilustrace znázorňuje koncepční zobrazení dvou sad a prvků v rámci těchto sad, které jsou zahrnuty buď pomocí vnitřního spojení, nebo levého vnějšího spojení.</span><span class="sxs-lookup"><span data-stu-id="1411a-115">The following illustration shows a conceptual view of two sets and the elements within those sets that are included in either an inner join or a left outer join.</span></span>  
  
 ![Dva překrývající se kružnice ukazující vnitřní&#47;vnější.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a><span data-ttu-id="1411a-117">Metody</span><span class="sxs-lookup"><span data-stu-id="1411a-117">Methods</span></span>  
  
|<span data-ttu-id="1411a-118">Název metody</span><span class="sxs-lookup"><span data-stu-id="1411a-118">Method Name</span></span>|<span data-ttu-id="1411a-119">Popis</span><span class="sxs-lookup"><span data-stu-id="1411a-119">Description</span></span>|<span data-ttu-id="1411a-120">Syntaxe výrazu dotazu v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="1411a-120">C# Query Expression Syntax</span></span>|<span data-ttu-id="1411a-121">Další informace</span><span class="sxs-lookup"><span data-stu-id="1411a-121">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|:::no-loc(Join):::|<span data-ttu-id="1411a-122">:::no-loc(Join):::s dvě sekvence na základě funkcí selektoru klíčů a extrahují páry hodnot.</span><span class="sxs-lookup"><span data-stu-id="1411a-122">:::no-loc(Join):::s two sequences based on key selector functions and extracts pairs of values.</span></span>|`join … in … on … equals …`|<xref:System.Linq.Enumerable.:::no-loc(Join):::%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.:::no-loc(Join):::%2A?displayProperty=nameWithType>|  
|:::no-loc(GroupJoin):::|<span data-ttu-id="1411a-123">:::no-loc(Join):::s dvě sekvence založené na funkcích selektoru klíčů a seskupují výsledné shody pro každý prvek.</span><span class="sxs-lookup"><span data-stu-id="1411a-123">:::no-loc(Join):::s two sequences based on key selector functions and groups the resulting matches for each element.</span></span>|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.:::no-loc(GroupJoin):::%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="1411a-124">Příklady syntaxe výrazů dotazů</span><span class="sxs-lookup"><span data-stu-id="1411a-124">Query expression syntax examples</span></span>
  
### :::no-loc(Join):::  
  
<span data-ttu-id="1411a-125">Následující příklad používá `join … in … on … equals …` klauzuli pro spojení dvou sekvencí na základě konkrétní hodnoty:</span><span class="sxs-lookup"><span data-stu-id="1411a-125">The following example uses the `join … in … on … equals …` clause to join two sequences based on specific value:</span></span>
  
[!code-csharp[:::no-loc(Join):::](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQ:::no-loc(Join):::Operation/CS/:::no-loc(Join):::Operation.cs#:::no-loc(Join):::)]  

### :::no-loc(GroupJoin):::  

<span data-ttu-id="1411a-126">Následující příklad používá `join … in … on … equals … into …` klauzuli pro spojení dvou sekvencí založených na konkrétní hodnotě a seskupení výsledných shod pro každý prvek:</span><span class="sxs-lookup"><span data-stu-id="1411a-126">The following example uses the `join … in … on … equals … into …` clause to join two sequences based on specific value and groups the resulting matches for each element:</span></span>
  
[!code-csharp[:::no-loc(GroupJoin):::](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQ:::no-loc(Join):::Operation/CS/:::no-loc(Join):::Operation.cs#:::no-loc(GroupJoin):::)]  
  
## <a name="see-also"></a><span data-ttu-id="1411a-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="1411a-127">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="1411a-128">Přehled standardních operátorů dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="1411a-128">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="1411a-129">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="1411a-129">Anonymous Types</span></span>](../../classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="1411a-130">Formulace :::no-loc(Join)::: s a dotazy na více produktů</span><span class="sxs-lookup"><span data-stu-id="1411a-130">Formulate :::no-loc(Join):::s and Cross-Product Queries</span></span>](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [<span data-ttu-id="1411a-131">join – klauzule</span><span class="sxs-lookup"><span data-stu-id="1411a-131">join clause</span></span>](../../../language-reference/keywords/join-clause.md)
- [<span data-ttu-id="1411a-132">:::no-loc(Join):::pomocí složených klíčů</span><span class="sxs-lookup"><span data-stu-id="1411a-132">:::no-loc(Join)::: by using composite keys</span></span>](../../../linq/join-by-using-composite-keys.md)
- [<span data-ttu-id="1411a-133">Postup připojení obsahu z nepodobných souborů (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="1411a-133">How to join content from dissimilar files (LINQ) (C#)</span></span>](./how-to-join-content-from-dissimilar-files-linq.md)
- [<span data-ttu-id="1411a-134">Řazení výsledků klauzule join</span><span class="sxs-lookup"><span data-stu-id="1411a-134">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="1411a-135">Provádění vlastních operací spojování</span><span class="sxs-lookup"><span data-stu-id="1411a-135">Perform custom join operations</span></span>](../../../linq/perform-custom-join-operations.md)
- [<span data-ttu-id="1411a-136">Provádění seskupených spojení</span><span class="sxs-lookup"><span data-stu-id="1411a-136">Perform grouped joins</span></span>](../../../linq/perform-grouped-joins.md)
- [<span data-ttu-id="1411a-137">Provádění vnitřních spojení</span><span class="sxs-lookup"><span data-stu-id="1411a-137">Perform inner joins</span></span>](../../../linq/perform-inner-joins.md)
- [<span data-ttu-id="1411a-138">Provedení levých vnějších spojení</span><span class="sxs-lookup"><span data-stu-id="1411a-138">Perform left outer joins</span></span>](../../../linq/perform-left-outer-joins.md)
- [<span data-ttu-id="1411a-139">Jak naplnit kolekce objektů z více zdrojů (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="1411a-139">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](./how-to-populate-object-collections-from-multiple-sources-linq.md)
