---
title: Operace Join (C#)
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
no-loc:
- Join
- GroupJoin
ms.openlocfilehash: d4bf9fe76238d8824c5255df8910c1000503dcdf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746966"
---
# <a name="opno-locjoin-operations-c"></a><span data-ttu-id="7c268-102">Operace [!OP.NO-LOC(Join)] (C#)</span><span class="sxs-lookup"><span data-stu-id="7c268-102">[!OP.NO-LOC(Join)] Operations (C#)</span></span>
<span data-ttu-id="7c268-103">*Spojení* dvou zdrojů dat je přidružení objektů v jednom zdroji dat s objekty, které sdílejí společný atribut v jiném zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="7c268-103">A *join* of two data sources is the association of objects in one data source with objects that share a common attribute in another data source.</span></span>  
  
 <span data-ttu-id="7c268-104">Spojování je důležitou operací v dotazech, které cílí na zdroje dat, u kterých vzájemně vztazích nemůžete přímo následovat.</span><span class="sxs-lookup"><span data-stu-id="7c268-104">Joining is an important operation in queries that target data sources whose relationships to each other cannot be followed directly.</span></span> <span data-ttu-id="7c268-105">V objektově orientovaném programování může to znamenat korelaci mezi objekty, které nejsou modelovány, jako je například zpětný směr jednosměrné relace.</span><span class="sxs-lookup"><span data-stu-id="7c268-105">In object-oriented programming, this could mean a correlation between objects that is not modeled, such as the backwards direction of a one-way relationship.</span></span> <span data-ttu-id="7c268-106">Příkladem jednosměrného vztahu je třída zákazníka, která má vlastnost typu City, ale třída City nemá vlastnost, která je kolekcí zákaznických objektů.</span><span class="sxs-lookup"><span data-stu-id="7c268-106">An example of a one-way relationship is a Customer class that has a property of type City, but the City class does not have a property that is a collection of Customer objects.</span></span> <span data-ttu-id="7c268-107">Pokud máte seznam objektů City a chcete najít všechny zákazníky v jednotlivých městech, můžete je najít pomocí operace JOIN.</span><span class="sxs-lookup"><span data-stu-id="7c268-107">If you have a list of City objects and you want to find all the customers in each city, you could use a join operation to find them.</span></span>  
  
 <span data-ttu-id="7c268-108">Metody join poskytované v rozhraní LINQ Framework jsou <xref:System.Linq.Enumerable.[!OP.NO-LOC(Join)]%2A> a <xref:System.Linq.Enumerable.[!OP.NO-LOC(GroupJoin)]%2A>.</span><span class="sxs-lookup"><span data-stu-id="7c268-108">The join methods provided in the LINQ framework are <xref:System.Linq.Enumerable.[!OP.NO-LOC(Join)]%2A> and <xref:System.Linq.Enumerable.[!OP.NO-LOC(GroupJoin)]%2A>.</span></span> <span data-ttu-id="7c268-109">Tyto metody provádějí equijoins nebo spojení, které odpovídají dvěma zdrojům dat na základě rovnosti jejich klíčů.</span><span class="sxs-lookup"><span data-stu-id="7c268-109">These methods perform equijoins, or joins that match two data sources based on equality of their keys.</span></span> <span data-ttu-id="7c268-110">(Pro porovnání jazyk Transact-SQL podporuje operátory JOIN jiné než Equals, například operátor "menší než".) V rámci podmínek relační databáze <xref:System.Linq.Enumerable.[!OP.NO-LOC(Join)]%2A> implementuje vnitřní spojení, což je typ spojení, ve kterém jsou vráceny pouze objekty, které mají shodu v jiné sadě dat.</span><span class="sxs-lookup"><span data-stu-id="7c268-110">(For comparison, Transact-SQL supports join operators other than 'equals', for example the 'less than' operator.) In relational database terms, <xref:System.Linq.Enumerable.[!OP.NO-LOC(Join)]%2A> implements an inner join, a type of join in which only those objects that have a match in the other data set are returned.</span></span> <span data-ttu-id="7c268-111">Metoda <xref:System.Linq.Enumerable.[!OP.NO-LOC(GroupJoin)]%2A> nemá žádný přímý ekvivalent v rámci podmínek relační databáze, ale implementuje nadmnožinu vnitřních spojení a levé vnější spojení.</span><span class="sxs-lookup"><span data-stu-id="7c268-111">The <xref:System.Linq.Enumerable.[!OP.NO-LOC(GroupJoin)]%2A> method has no direct equivalent in relational database terms, but it implements a superset of inner joins and left outer joins.</span></span> <span data-ttu-id="7c268-112">Levé vnější spojení je spojení, které vrátí každý prvek prvního (levého) zdroje dat, a to i v případě, že nemá žádné korelační prvky v jiném zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="7c268-112">A left outer join is a join that returns each element of the first (left) data source, even if it has no correlated elements in the other data source.</span></span>  
  
 <span data-ttu-id="7c268-113">Následující ilustrace znázorňuje koncepční zobrazení dvou sad a prvků v rámci těchto sad, které jsou zahrnuty buď pomocí vnitřního spojení, nebo levého vnějšího spojení.</span><span class="sxs-lookup"><span data-stu-id="7c268-113">The following illustration shows a conceptual view of two sets and the elements within those sets that are included in either an inner join or a left outer join.</span></span>  
  
 ![Dva překrývající se kružnice ukazující vnitřní&#47;vnější.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a><span data-ttu-id="7c268-115">Metody</span><span class="sxs-lookup"><span data-stu-id="7c268-115">Methods</span></span>  
  
|<span data-ttu-id="7c268-116">Název metody</span><span class="sxs-lookup"><span data-stu-id="7c268-116">Method Name</span></span>|<span data-ttu-id="7c268-117">Popis</span><span class="sxs-lookup"><span data-stu-id="7c268-117">Description</span></span>|<span data-ttu-id="7c268-118">C#Syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="7c268-118">C# Query Expression Syntax</span></span>|<span data-ttu-id="7c268-119">Další informace</span><span class="sxs-lookup"><span data-stu-id="7c268-119">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Join|<span data-ttu-id="7c268-120">Spojí dvě sekvence na základě funkcí selektoru klíčů a extrahuje páry hodnot.</span><span class="sxs-lookup"><span data-stu-id="7c268-120">Joins two sequences based on key selector functions and extracts pairs of values.</span></span>|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|<span data-ttu-id="7c268-121">Spojí dvě sekvence na základě funkcí selektoru klíčů a seskupí výsledné shody pro každý prvek.</span><span class="sxs-lookup"><span data-stu-id="7c268-121">Joins two sequences based on key selector functions and groups the resulting matches for each element.</span></span>|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="7c268-122">Příklady syntaxe výrazů dotazů</span><span class="sxs-lookup"><span data-stu-id="7c268-122">Query expression syntax examples</span></span>
  
### Join  
  
<span data-ttu-id="7c268-123">Následující příklad používá klauzuli `join … in … on … equals …` pro spojení dvou sekvencí na základě konkrétní hodnoty:</span><span class="sxs-lookup"><span data-stu-id="7c268-123">The following example uses the `join … in … on … equals …` clause to join two sequences based on specific value:</span></span>
  
[!code-csharp[Join](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQJoin/CS/JoinOperation.cs#Join)]  

### GroupJoin  

<span data-ttu-id="7c268-124">Následující příklad používá klauzuli `join … in … on … equals … into …` pro spojení dvou sekvencí založených na konkrétní hodnotě a seskupení výsledných shod pro každý prvek:</span><span class="sxs-lookup"><span data-stu-id="7c268-124">The following example uses the `join … in … on … equals … into …` clause to join two sequences based on specific value and groups the resulting matches for each element:</span></span>
  
[!code-csharp[GroupJoin](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQJoin/CS/JoinOperation.cs#GroupJoin)]  
  
## <a name="see-also"></a><span data-ttu-id="7c268-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7c268-125">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="7c268-126">Přehled standardních operátorů dotazůC#()</span><span class="sxs-lookup"><span data-stu-id="7c268-126">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="7c268-127">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="7c268-127">Anonymous Types</span></span>](../../classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="7c268-128">Formulování spojení a dotazů napříč produkty</span><span class="sxs-lookup"><span data-stu-id="7c268-128">Formulate Joins and Cross-Product Queries</span></span>](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [<span data-ttu-id="7c268-129">join – klauzule</span><span class="sxs-lookup"><span data-stu-id="7c268-129">join clause</span></span>](../../../language-reference/keywords/join-clause.md)
- <span data-ttu-id="7c268-130">[Join pomocí složených klíčů](../../../linq/join-by-using-composite-keys.md)</span><span class="sxs-lookup"><span data-stu-id="7c268-130">[Join by using composite keys](../../../linq/join-by-using-composite-keys.md)</span></span>
- [<span data-ttu-id="7c268-131">Postup připojení obsahu z nepodobných souborů (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="7c268-131">How to join content from dissimilar files (LINQ) (C#)</span></span>](./how-to-join-content-from-dissimilar-files-linq.md)
- [<span data-ttu-id="7c268-132">Řazení výsledků klauzule join</span><span class="sxs-lookup"><span data-stu-id="7c268-132">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="7c268-133">Provádění vlastních operací spojování</span><span class="sxs-lookup"><span data-stu-id="7c268-133">Perform custom join operations</span></span>](../../../linq/perform-custom-join-operations.md)
- [<span data-ttu-id="7c268-134">Provádění seskupených spojení</span><span class="sxs-lookup"><span data-stu-id="7c268-134">Perform grouped joins</span></span>](../../../linq/perform-grouped-joins.md)
- [<span data-ttu-id="7c268-135">Provádění vnitřních spojení</span><span class="sxs-lookup"><span data-stu-id="7c268-135">Perform inner joins</span></span>](../../../linq/perform-inner-joins.md)
- [<span data-ttu-id="7c268-136">Provedení levých vnějších spojení</span><span class="sxs-lookup"><span data-stu-id="7c268-136">Perform left outer joins</span></span>](../../../linq/perform-left-outer-joins.md)
- [<span data-ttu-id="7c268-137">Jak naplnit kolekce objektů z více zdrojů (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="7c268-137">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](./how-to-populate-object-collections-from-multiple-sources-linq.md)
