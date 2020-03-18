---
title: JoinOperace (C#)
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
no-loc:
- Join
- GroupJoin
ms.openlocfilehash: 6e2ec1a0c8120f6869b7c0a196b77d118762a8dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76868002"
---
# <a name="join-operations-c"></a><span data-ttu-id="e0c57-102">Operace spojení (C#)</span><span class="sxs-lookup"><span data-stu-id="e0c57-102">Join Operations (C#)</span></span>

<span data-ttu-id="e0c57-103">*Spojení* dvou zdrojů dat je přidružení objektů v jednom zdroji dat k objektům, které sdílejí společný atribut v jiném zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="e0c57-103">A *join* of two data sources is the association of objects in one data source with objects that share a common attribute in another data source.</span></span>  
  
 <span data-ttu-id="e0c57-104">Spojení je důležitá operace v dotazech, které cílí na zdroje dat, jejichž vzájemné vztahy nelze sledovat přímo.</span><span class="sxs-lookup"><span data-stu-id="e0c57-104">Joining is an important operation in queries that target data sources whose relationships to each other cannot be followed directly.</span></span> <span data-ttu-id="e0c57-105">V objektově orientovaném programování to může znamenat korelaci mezi objekty, které nejsou modelovány, jako je například směr dozadu jednosměrného vztahu.</span><span class="sxs-lookup"><span data-stu-id="e0c57-105">In object-oriented programming, this could mean a correlation between objects that is not modeled, such as the backwards direction of a one-way relationship.</span></span> <span data-ttu-id="e0c57-106">Příkladem jednosměrného vztahu je třída Customer, která má vlastnost typu Město, ale třída Město nemá vlastnost, která je kolekcí objektů Customer.</span><span class="sxs-lookup"><span data-stu-id="e0c57-106">An example of a one-way relationship is a Customer class that has a property of type City, but the City class does not have a property that is a collection of Customer objects.</span></span> <span data-ttu-id="e0c57-107">Pokud máte seznam objektů City a chcete najít všechny zákazníky v každém městě, můžete je najít pomocí operace spojení.</span><span class="sxs-lookup"><span data-stu-id="e0c57-107">If you have a list of City objects and you want to find all the customers in each city, you could use a join operation to find them.</span></span>  
  
 <span data-ttu-id="e0c57-108">Metody spojení poskytované v rámci LINQ jsou <xref:System.Linq.Enumerable.Join%2A> a <xref:System.Linq.Enumerable.GroupJoin%2A>.</span><span class="sxs-lookup"><span data-stu-id="e0c57-108">The join methods provided in the LINQ framework are <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A>.</span></span> <span data-ttu-id="e0c57-109">Tyto metody provádět equijoins nebo spojení, které odpovídají dva zdroje dat na základě rovnosti jejich klíče.</span><span class="sxs-lookup"><span data-stu-id="e0c57-109">These methods perform equijoins, or joins that match two data sources based on equality of their keys.</span></span> <span data-ttu-id="e0c57-110">(Pro srovnání, Transact-SQL podporuje operátory spojení jiné než "rovná", například operátor "menší než".) V termínech relační databáze <xref:System.Linq.Enumerable.Join%2A> implementuje vnitřní spojení, typ spojení, ve kterém jsou vráceny pouze ty objekty, které mají shodu v jiné datové sadě.</span><span class="sxs-lookup"><span data-stu-id="e0c57-110">(For comparison, Transact-SQL supports join operators other than 'equals', for example the 'less than' operator.) In relational database terms, <xref:System.Linq.Enumerable.Join%2A> implements an inner join, a type of join in which only those objects that have a match in the other data set are returned.</span></span> <span data-ttu-id="e0c57-111">Metoda <xref:System.Linq.Enumerable.GroupJoin%2A> nemá žádný přímý ekvivalent v termínech relační databáze, ale implementuje nadmnožinu vnitřní spojení a levé vnější spojení.</span><span class="sxs-lookup"><span data-stu-id="e0c57-111">The <xref:System.Linq.Enumerable.GroupJoin%2A> method has no direct equivalent in relational database terms, but it implements a superset of inner joins and left outer joins.</span></span> <span data-ttu-id="e0c57-112">Levé vnější spojení je spojení, které vrací každý prvek prvního (levého) zdroje dat, i když nemá žádné korelované prvky v jiném zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="e0c57-112">A left outer join is a join that returns each element of the first (left) data source, even if it has no correlated elements in the other data source.</span></span>  
  
 <span data-ttu-id="e0c57-113">Následující obrázek znázorňuje koncepční zobrazení dvou sad a prvků v rámci těchto sad, které jsou zahrnuty buď v vnitřní spojení nebo levé vnější spojení.</span><span class="sxs-lookup"><span data-stu-id="e0c57-113">The following illustration shows a conceptual view of two sets and the elements within those sets that are included in either an inner join or a left outer join.</span></span>  
  
 ![Dva překrývající se kruhy zobrazující vnitřní&#47;vnější.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a><span data-ttu-id="e0c57-115">Metody</span><span class="sxs-lookup"><span data-stu-id="e0c57-115">Methods</span></span>  
  
|<span data-ttu-id="e0c57-116">Název metody</span><span class="sxs-lookup"><span data-stu-id="e0c57-116">Method Name</span></span>|<span data-ttu-id="e0c57-117">Popis</span><span class="sxs-lookup"><span data-stu-id="e0c57-117">Description</span></span>|<span data-ttu-id="e0c57-118">Syntaxe výrazu dotazu jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e0c57-118">C# Query Expression Syntax</span></span>|<span data-ttu-id="e0c57-119">Další informace</span><span class="sxs-lookup"><span data-stu-id="e0c57-119">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Join|<span data-ttu-id="e0c57-120">Spojí dvě sekvence založené na funkcích selektoru klíčů a extrahuje dvojice hodnot.</span><span class="sxs-lookup"><span data-stu-id="e0c57-120">Joins two sequences based on key selector functions and extracts pairs of values.</span></span>|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|<span data-ttu-id="e0c57-121">Spojí dvě sekvence založené na funkcích selektoru klíčů a seskupí výsledné shody pro každý prvek.</span><span class="sxs-lookup"><span data-stu-id="e0c57-121">Joins two sequences based on key selector functions and groups the resulting matches for each element.</span></span>|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="e0c57-122">Příklady syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="e0c57-122">Query expression syntax examples</span></span>
  
### Join  
  
<span data-ttu-id="e0c57-123">Následující příklad používá `join … in … on … equals …` klauzuli spojit dvě sekvence na základě určité hodnoty:</span><span class="sxs-lookup"><span data-stu-id="e0c57-123">The following example uses the `join … in … on … equals …` clause to join two sequences based on specific value:</span></span>
  
[!code-csharp[Join](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#Join)]  

### GroupJoin  

<span data-ttu-id="e0c57-124">Následující příklad používá `join … in … on … equals … into …` klauzuli spojit dvě sekvence na základě určité hodnoty a seskupí výsledné shody pro každý prvek:</span><span class="sxs-lookup"><span data-stu-id="e0c57-124">The following example uses the `join … in … on … equals … into …` clause to join two sequences based on specific value and groups the resulting matches for each element:</span></span>
  
[!code-csharp[GroupJoin](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#GroupJoin)]  
  
## <a name="see-also"></a><span data-ttu-id="e0c57-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="e0c57-125">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="e0c57-126">Standardní operátory dotazů – přehled (C#)</span><span class="sxs-lookup"><span data-stu-id="e0c57-126">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="e0c57-127">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="e0c57-127">Anonymous Types</span></span>](../../classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="e0c57-128">Formulování spojení a dotazů napříč produkty</span><span class="sxs-lookup"><span data-stu-id="e0c57-128">Formulate Joins and Cross-Product Queries</span></span>](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [<span data-ttu-id="e0c57-129">spojit klauzuli</span><span class="sxs-lookup"><span data-stu-id="e0c57-129">join clause</span></span>](../../../language-reference/keywords/join-clause.md)
- <span data-ttu-id="e0c57-130">[Joinpomocí složených klíčů](../../../linq/join-by-using-composite-keys.md)</span><span class="sxs-lookup"><span data-stu-id="e0c57-130">[Join by using composite keys](../../../linq/join-by-using-composite-keys.md)</span></span>
- [<span data-ttu-id="e0c57-131">Jak se připojit k obsahu z odlišných souborů (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e0c57-131">How to join content from dissimilar files (LINQ) (C#)</span></span>](./how-to-join-content-from-dissimilar-files-linq.md)
- [<span data-ttu-id="e0c57-132">Řazení výsledků klauzule join</span><span class="sxs-lookup"><span data-stu-id="e0c57-132">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="e0c57-133">Provádění vlastních operací spojování</span><span class="sxs-lookup"><span data-stu-id="e0c57-133">Perform custom join operations</span></span>](../../../linq/perform-custom-join-operations.md)
- [<span data-ttu-id="e0c57-134">Provádění seskupených spojení</span><span class="sxs-lookup"><span data-stu-id="e0c57-134">Perform grouped joins</span></span>](../../../linq/perform-grouped-joins.md)
- [<span data-ttu-id="e0c57-135">Provádění vnitřních spojení</span><span class="sxs-lookup"><span data-stu-id="e0c57-135">Perform inner joins</span></span>](../../../linq/perform-inner-joins.md)
- [<span data-ttu-id="e0c57-136">Provedení levých vnějších spojení</span><span class="sxs-lookup"><span data-stu-id="e0c57-136">Perform left outer joins</span></span>](../../../linq/perform-left-outer-joins.md)
- [<span data-ttu-id="e0c57-137">Jak naplnit kolekce objektů z více zdrojů (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e0c57-137">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](./how-to-populate-object-collections-from-multiple-sources-linq.md)
