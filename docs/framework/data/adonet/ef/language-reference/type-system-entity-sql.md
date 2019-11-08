---
title: Systém typů (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 818a505b-a196-41dd-aaac-2ccd5f7a2f1a
ms.openlocfilehash: f99d63bd526981c4a9f079c25851dc9bbd89cf7c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738459"
---
# <a name="type-system-entity-sql"></a><span data-ttu-id="087ae-102">Systém typů (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="087ae-102">Type System (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="087ae-103">podporuje několik typů:</span><span class="sxs-lookup"><span data-stu-id="087ae-103">supports a number of types:</span></span>  
  
- <span data-ttu-id="087ae-104">Primitivní (jednoduché) typy jako `Int32` a `String.`</span><span class="sxs-lookup"><span data-stu-id="087ae-104">Primitive (simple) types such as `Int32` and `String.`</span></span>  
  
- <span data-ttu-id="087ae-105">Nominální typy, které jsou definovány ve schématu, například <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType> a <xref:System.Data.Metadata.Edm.RelationshipType>.</span><span class="sxs-lookup"><span data-stu-id="087ae-105">Nominal types that are defined in the schema, such as <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType>, and <xref:System.Data.Metadata.Edm.RelationshipType>.</span></span>  
  
- <span data-ttu-id="087ae-106">Anonymní typy, které nejsou definovány ve schématu explicitně: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType> a <xref:System.Data.Metadata.Edm.RefType>.</span><span class="sxs-lookup"><span data-stu-id="087ae-106">Anonymous types that are not defined in the schema explicitly: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType>, and <xref:System.Data.Metadata.Edm.RefType>.</span></span>  
  
 <span data-ttu-id="087ae-107">Tato část popisuje anonymní typy, které nejsou explicitně definovány ve schématu, ale jsou podporovány Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="087ae-107">This section discusses the anonymous types that are not defined in the schema explicitly but are supported by Entity SQL.</span></span> <span data-ttu-id="087ae-108">Informace o primitivních a nominálních typech naleznete v tématu [typy konceptuálních modelů (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl).</span><span class="sxs-lookup"><span data-stu-id="087ae-108">For information on primitive and nominal types, see [Conceptual Model Types (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl).</span></span>  
  
## <a name="rows"></a><span data-ttu-id="087ae-109">tabulky</span><span class="sxs-lookup"><span data-stu-id="087ae-109">Rows</span></span>  
 <span data-ttu-id="087ae-110">Struktura řádku závisí na sekvenci typovaného a pojmenovaného člena, ze kterého se řádek skládá.</span><span class="sxs-lookup"><span data-stu-id="087ae-110">The structure of a row depends on the sequence of typed and named members that the row consists of.</span></span> <span data-ttu-id="087ae-111">Typ řádku nemá žádnou identitu a nedá se dědit z.</span><span class="sxs-lookup"><span data-stu-id="087ae-111">A row type has no identity and cannot be inherited from.</span></span> <span data-ttu-id="087ae-112">Instance stejného typu řádku jsou ekvivalentní, pokud jsou členy ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="087ae-112">Instances of the same row type are equivalent if the members are respectively equivalent.</span></span> <span data-ttu-id="087ae-113">Řádky nemají žádné chování nad jejich strukturální rovnocennost a nemají ekvivalent v modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="087ae-113">Rows have no behavior beyond their structural equivalence and have no equivalent in the common language runtime.</span></span> <span data-ttu-id="087ae-114">Dotazy mohou mít za následek struktury, které obsahují řádky nebo kolekce řádků.</span><span class="sxs-lookup"><span data-stu-id="087ae-114">Queries can result in structures that contain rows or collections of rows.</span></span> <span data-ttu-id="087ae-115">Vazba rozhraní API mezi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazy a jazykem hostitele definuje způsob, jakým jsou řádky realizovány v dotazu, který vytvořil výsledek.</span><span class="sxs-lookup"><span data-stu-id="087ae-115">The API binding between the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries and the host language defines how rows are realized in the query that produced the result.</span></span> <span data-ttu-id="087ae-116">Informace o tom, jak vytvořit instanci řádku, naleznete v tématu [sestavování typů](constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="087ae-116">For information on how to construct a row instance, see [Constructing Types](constructing-types-entity-sql.md).</span></span>  
  
## <a name="collections"></a><span data-ttu-id="087ae-117">Kolekce</span><span class="sxs-lookup"><span data-stu-id="087ae-117">Collections</span></span>  
 <span data-ttu-id="087ae-118">Typy kolekce reprezentují nula nebo více instancí jiných objektů.</span><span class="sxs-lookup"><span data-stu-id="087ae-118">Collection types represent zero or more instances of other objects.</span></span> <span data-ttu-id="087ae-119">Informace o tom, jak sestavit kolekci, naleznete v tématu [konstrukce typů](constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="087ae-119">For information on how to construct collection, see [Constructing Types](constructing-types-entity-sql.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="087ae-120">Odkazy</span><span class="sxs-lookup"><span data-stu-id="087ae-120">References</span></span>  
 <span data-ttu-id="087ae-121">Odkaz je logický ukazatel na konkrétní entitu v konkrétní sadě entit.</span><span class="sxs-lookup"><span data-stu-id="087ae-121">A reference is a logical pointer to a specific entity in a specific entity set.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="087ae-122">podporuje následující operátory pro konstrukci, dekonstrukci a navigaci prostřednictvím odkazů:</span><span class="sxs-lookup"><span data-stu-id="087ae-122">supports the following operators to construct, deconstruct, and navigate through references:</span></span>  
  
- [<span data-ttu-id="087ae-123">REF</span><span class="sxs-lookup"><span data-stu-id="087ae-123">REF</span></span>](ref-entity-sql.md)  
  
- [<span data-ttu-id="087ae-124">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="087ae-124">CREATEREF</span></span>](createref-entity-sql.md)  
  
- [<span data-ttu-id="087ae-125">KEY</span><span class="sxs-lookup"><span data-stu-id="087ae-125">KEY</span></span>](key-entity-sql.md)  
  
- [<span data-ttu-id="087ae-126">DEREF</span><span class="sxs-lookup"><span data-stu-id="087ae-126">DEREF</span></span>](deref-entity-sql.md)  
  
 <span data-ttu-id="087ae-127">Můžete procházet odkazem pomocí operátoru přístupu ke členu (tečka) (`.`).</span><span class="sxs-lookup"><span data-stu-id="087ae-127">You can navigate through a reference by using the member access (dot) operator(`.`).</span></span> <span data-ttu-id="087ae-128">Následující fragment kódu extrahuje vlastnost ID (z pořadí) přechodem na vlastnost r (Reference).</span><span class="sxs-lookup"><span data-stu-id="087ae-128">The following snippet extracts the Id property (of Order) by navigating through the r (reference) property.</span></span>  
  
```sql  
select o2.r.Id   
from (select ref(o) as r from LOB.Orders as o) as o2   
```  
  
 <span data-ttu-id="087ae-129">Pokud má referenční hodnota hodnotu null nebo pokud cíl odkazu neexistuje, výsledek je null.</span><span class="sxs-lookup"><span data-stu-id="087ae-129">If the reference value is null, or if the target of the reference does not exist, the result is null.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="087ae-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="087ae-130">See also</span></span>

- [<span data-ttu-id="087ae-131">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="087ae-131">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="087ae-132">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="087ae-132">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="087ae-133">CAST</span><span class="sxs-lookup"><span data-stu-id="087ae-133">CAST</span></span>](cast-entity-sql.md)
- [<span data-ttu-id="087ae-134">Specifikace CSDL, SSDL a MSL</span><span class="sxs-lookup"><span data-stu-id="087ae-134">CSDL, SSDL, and MSL Specifications</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
