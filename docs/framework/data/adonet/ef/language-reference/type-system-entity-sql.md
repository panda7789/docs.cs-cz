---
title: Typový systém (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 818a505b-a196-41dd-aaac-2ccd5f7a2f1a
ms.openlocfilehash: b8b721aff5b7886fdb897ecaa3dcc163ec94ae79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149828"
---
# <a name="type-system-entity-sql"></a><span data-ttu-id="82d93-102">Typový systém (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="82d93-102">Type System (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="82d93-103">podporuje řadu typů:</span><span class="sxs-lookup"><span data-stu-id="82d93-103">supports a number of types:</span></span>  
  
- <span data-ttu-id="82d93-104">Primitivní (jednoduché) typy, jako `Int32` jsou`String.`</span><span class="sxs-lookup"><span data-stu-id="82d93-104">Primitive (simple) types such as `Int32` and `String.`</span></span>  
  
- <span data-ttu-id="82d93-105">Nominální typy, které jsou definovány ve <xref:System.Data.Metadata.Edm.EntityType>schématu, například , <xref:System.Data.Metadata.Edm.ComplexType>a <xref:System.Data.Metadata.Edm.RelationshipType>.</span><span class="sxs-lookup"><span data-stu-id="82d93-105">Nominal types that are defined in the schema, such as <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType>, and <xref:System.Data.Metadata.Edm.RelationshipType>.</span></span>  
  
- <span data-ttu-id="82d93-106">Anonymní typy, které nejsou definovány ve <xref:System.Data.Metadata.Edm.CollectionType>schématu explicitně: , <xref:System.Data.Metadata.Edm.RowType>a <xref:System.Data.Metadata.Edm.RefType>.</span><span class="sxs-lookup"><span data-stu-id="82d93-106">Anonymous types that are not defined in the schema explicitly: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType>, and <xref:System.Data.Metadata.Edm.RefType>.</span></span>  
  
 <span data-ttu-id="82d93-107">Tato část popisuje anonymní typy, které nejsou definovány ve schématu explicitně, ale jsou podporovány entity SQL.</span><span class="sxs-lookup"><span data-stu-id="82d93-107">This section discusses the anonymous types that are not defined in the schema explicitly but are supported by Entity SQL.</span></span> <span data-ttu-id="82d93-108">Informace o primitivních a nominálních typech naleznete v [tématu Conceptual Model Types (CSDL).](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)</span><span class="sxs-lookup"><span data-stu-id="82d93-108">For information on primitive and nominal types, see [Conceptual Model Types (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl).</span></span>  
  
## <a name="rows"></a><span data-ttu-id="82d93-109">Řádky</span><span class="sxs-lookup"><span data-stu-id="82d93-109">Rows</span></span>  
 <span data-ttu-id="82d93-110">Struktura řádku závisí na pořadí zadali a pojmenované členy, které řádek se skládá z.</span><span class="sxs-lookup"><span data-stu-id="82d93-110">The structure of a row depends on the sequence of typed and named members that the row consists of.</span></span> <span data-ttu-id="82d93-111">Typ řádku nemá žádnou identitu a nelze z ní zdědit.</span><span class="sxs-lookup"><span data-stu-id="82d93-111">A row type has no identity and cannot be inherited from.</span></span> <span data-ttu-id="82d93-112">Instance stejného typu řádku jsou ekvivalentní, pokud jsou členy ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="82d93-112">Instances of the same row type are equivalent if the members are respectively equivalent.</span></span> <span data-ttu-id="82d93-113">Řádky nemají žádné chování mimo jejich strukturální ekvivalence a nemají žádný ekvivalent v běžném jazyku runtime.</span><span class="sxs-lookup"><span data-stu-id="82d93-113">Rows have no behavior beyond their structural equivalence and have no equivalent in the common language runtime.</span></span> <span data-ttu-id="82d93-114">Dotazy může mít za následek struktury, které obsahují řádky nebo kolekce řádků.</span><span class="sxs-lookup"><span data-stu-id="82d93-114">Queries can result in structures that contain rows or collections of rows.</span></span> <span data-ttu-id="82d93-115">Vazba rozhraní [!INCLUDE[esql](../../../../../../includes/esql-md.md)] API mezi dotazy a jazyk hostitele definuje, jak jsou řádky realizovány v dotazu, který vytvořil výsledek.</span><span class="sxs-lookup"><span data-stu-id="82d93-115">The API binding between the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries and the host language defines how rows are realized in the query that produced the result.</span></span> <span data-ttu-id="82d93-116">Informace o tom, jak vytvořit instanci řádku, naleznete v [tématu Vytváření typů](constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="82d93-116">For information on how to construct a row instance, see [Constructing Types](constructing-types-entity-sql.md).</span></span>  
  
## <a name="collections"></a><span data-ttu-id="82d93-117">Kolekce</span><span class="sxs-lookup"><span data-stu-id="82d93-117">Collections</span></span>  
 <span data-ttu-id="82d93-118">Kolekce typy představují nula nebo více instancí jiných objektů.</span><span class="sxs-lookup"><span data-stu-id="82d93-118">Collection types represent zero or more instances of other objects.</span></span> <span data-ttu-id="82d93-119">Informace o tom, jak vytvořit kolekci, naleznete [v tématu Vytváření typů](constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="82d93-119">For information on how to construct collection, see [Constructing Types](constructing-types-entity-sql.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="82d93-120">Odkazy</span><span class="sxs-lookup"><span data-stu-id="82d93-120">References</span></span>  
 <span data-ttu-id="82d93-121">Odkaz je logický ukazatel na určitou entitu v určité sadě entit.</span><span class="sxs-lookup"><span data-stu-id="82d93-121">A reference is a logical pointer to a specific entity in a specific entity set.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="82d93-122">podporuje následující operátory k vytvoření, dekonstrukci a procházení odkazů:</span><span class="sxs-lookup"><span data-stu-id="82d93-122">supports the following operators to construct, deconstruct, and navigate through references:</span></span>  
  
- [<span data-ttu-id="82d93-123">Ref</span><span class="sxs-lookup"><span data-stu-id="82d93-123">REF</span></span>](ref-entity-sql.md)  
  
- [<span data-ttu-id="82d93-124">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="82d93-124">CREATEREF</span></span>](createref-entity-sql.md)  
  
- [<span data-ttu-id="82d93-125">Klíč</span><span class="sxs-lookup"><span data-stu-id="82d93-125">KEY</span></span>](key-entity-sql.md)  
  
- [<span data-ttu-id="82d93-126">DEREF</span><span class="sxs-lookup"><span data-stu-id="82d93-126">DEREF</span></span>](deref-entity-sql.md)  
  
 <span data-ttu-id="82d93-127">Můžete procházet odkaz pomocí operátoru přístup u člena`.`(tečka) ( ).</span><span class="sxs-lookup"><span data-stu-id="82d93-127">You can navigate through a reference by using the member access (dot) operator(`.`).</span></span> <span data-ttu-id="82d93-128">Následující úryvek extrahuje Id vlastnost (Order) procházením r (reference) vlastnost.</span><span class="sxs-lookup"><span data-stu-id="82d93-128">The following snippet extracts the Id property (of Order) by navigating through the r (reference) property.</span></span>  
  
```sql  
select o2.r.Id
from (select ref(o) as r from LOB.Orders as o) as o2
```  
  
 <span data-ttu-id="82d93-129">Pokud je hodnota odkazu null nebo pokud cíl odkazu neexistuje, výsledek je null.</span><span class="sxs-lookup"><span data-stu-id="82d93-129">If the reference value is null, or if the target of the reference does not exist, the result is null.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82d93-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="82d93-130">See also</span></span>

- [<span data-ttu-id="82d93-131">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="82d93-131">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="82d93-132">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="82d93-132">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="82d93-133">CAST</span><span class="sxs-lookup"><span data-stu-id="82d93-133">CAST</span></span>](cast-entity-sql.md)
- [<span data-ttu-id="82d93-134">Specifikace CSDL, SSDL a MSL</span><span class="sxs-lookup"><span data-stu-id="82d93-134">CSDL, SSDL, and MSL Specifications</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
