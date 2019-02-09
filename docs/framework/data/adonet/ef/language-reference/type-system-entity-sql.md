---
title: Systém typů (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 818a505b-a196-41dd-aaac-2ccd5f7a2f1a
ms.openlocfilehash: a2748407703b90c60d3082b0e6c0b6aa2d3fb365
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2019
ms.locfileid: "55904683"
---
# <a name="type-system-entity-sql"></a><span data-ttu-id="3136d-102">Systém typů (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3136d-102">Type System (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3136d-103">podporuje několik typů:</span><span class="sxs-lookup"><span data-stu-id="3136d-103">supports a number of types:</span></span>  
  
-   <span data-ttu-id="3136d-104">(Jednoduchý) primitivní typy, jako `Int32` a `String.`</span><span class="sxs-lookup"><span data-stu-id="3136d-104">Primitive (simple) types such as `Int32` and `String.`</span></span>  
  
-   <span data-ttu-id="3136d-105">Nominální typy, které jsou definovány ve schématu, jako například <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType>, a <xref:System.Data.Metadata.Edm.RelationshipType>.</span><span class="sxs-lookup"><span data-stu-id="3136d-105">Nominal types that are defined in the schema, such as <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType>, and <xref:System.Data.Metadata.Edm.RelationshipType>.</span></span>  
  
-   <span data-ttu-id="3136d-106">Anonymní typy, které nejsou explicitně definovány ve schématu: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType>, a <xref:System.Data.Metadata.Edm.RefType>.</span><span class="sxs-lookup"><span data-stu-id="3136d-106">Anonymous types that are not defined in the schema explicitly: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType>, and <xref:System.Data.Metadata.Edm.RefType>.</span></span>  
  
 <span data-ttu-id="3136d-107">Tato část popisuje anonymní typy, které nejsou explicitně definovány ve schématu však není podporovaná Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="3136d-107">This section discusses the anonymous types that are not defined in the schema explicitly but are supported by Entity SQL.</span></span> <span data-ttu-id="3136d-108">Informace o typech primitivní a nominální najdete v tématu [koncepční Model typy (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl).</span><span class="sxs-lookup"><span data-stu-id="3136d-108">For information on primitive and nominal types, see [Conceptual Model Types (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl).</span></span>  
  
## <a name="rows"></a><span data-ttu-id="3136d-109">Řádky</span><span class="sxs-lookup"><span data-stu-id="3136d-109">Rows</span></span>  
 <span data-ttu-id="3136d-110">Struktura řádek závisí na pořadí zadaném a pojmenované členy, které se skládá z řádku.</span><span class="sxs-lookup"><span data-stu-id="3136d-110">The structure of a row depends on the sequence of typed and named members that the row consists of.</span></span> <span data-ttu-id="3136d-111">Typ řádku nemá žádná identita a nejde ji zdědit z.</span><span class="sxs-lookup"><span data-stu-id="3136d-111">A row type has no identity and cannot be inherited from.</span></span> <span data-ttu-id="3136d-112">Instance stejného typu řádku jsou rovnocenné, pokud jsou v uvedeném pořadí ekvivalentních členy.</span><span class="sxs-lookup"><span data-stu-id="3136d-112">Instances of the same row type are equivalent if the members are respectively equivalent.</span></span> <span data-ttu-id="3136d-113">Řádky mít žádné chování, mimo jejich ekvivalence strukturální a nemají žádný ekvivalent v modulu common language runtime.</span><span class="sxs-lookup"><span data-stu-id="3136d-113">Rows have no behavior beyond their structural equivalence and have no equivalent in the common language runtime.</span></span> <span data-ttu-id="3136d-114">Struktury obsahující řádky nebo kolekce řádků může způsobit dotazů.</span><span class="sxs-lookup"><span data-stu-id="3136d-114">Queries can result in structures that contain rows or collections of rows.</span></span> <span data-ttu-id="3136d-115">Rozhraní API vazby mezi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazy a jazyk hostitelského definuje, jak jsou realizované řádků v dotazu, který vytváří výsledek.</span><span class="sxs-lookup"><span data-stu-id="3136d-115">The API binding between the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries and the host language defines how rows are realized in the query that produced the result.</span></span> <span data-ttu-id="3136d-116">Informace o tom, jak vytvořit instanci řádku najdete v tématu [vytváření typů](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="3136d-116">For information on how to construct a row instance, see [Constructing Types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span></span>  
  
## <a name="collections"></a><span data-ttu-id="3136d-117">Kolekce</span><span class="sxs-lookup"><span data-stu-id="3136d-117">Collections</span></span>  
 <span data-ttu-id="3136d-118">Typy kolekce představují nula nebo víc instancí jiné objekty.</span><span class="sxs-lookup"><span data-stu-id="3136d-118">Collection types represent zero or more instances of other objects.</span></span> <span data-ttu-id="3136d-119">Informace o tom, jak vytvořit kolekci, najdete v části [vytváření typů](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="3136d-119">For information on how to construct collection, see [Constructing Types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="3136d-120">Odkazy</span><span class="sxs-lookup"><span data-stu-id="3136d-120">References</span></span>  
 <span data-ttu-id="3136d-121">Odkaz je logický ukazatel na konkrétní entitu v sadě konkrétní entity.</span><span class="sxs-lookup"><span data-stu-id="3136d-121">A reference is a logical pointer to a specific entity in a specific entity set.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3136d-122">podporuje následující operátory sestavit, dekonstruovat a procházejte odkazy:</span><span class="sxs-lookup"><span data-stu-id="3136d-122">supports the following operators to construct, deconstruct, and navigate through references:</span></span>  
  
-   [<span data-ttu-id="3136d-123">REF</span><span class="sxs-lookup"><span data-stu-id="3136d-123">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
  
-   [<span data-ttu-id="3136d-124">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="3136d-124">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
  
-   [<span data-ttu-id="3136d-125">KEY</span><span class="sxs-lookup"><span data-stu-id="3136d-125">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
  
-   [<span data-ttu-id="3136d-126">DEREF</span><span class="sxs-lookup"><span data-stu-id="3136d-126">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
  
 <span data-ttu-id="3136d-127">Odkaz můžete procházet pomocí operátoru přístupu (tečka) člena (`.`).</span><span class="sxs-lookup"><span data-stu-id="3136d-127">You can navigate through a reference by using the member access (dot) operator(`.`).</span></span> <span data-ttu-id="3136d-128">Následující fragment kódu extrahuje Vlastnost Id (pořadí) tak, že přejdete prostřednictvím vlastnosti r (odkaz).</span><span class="sxs-lookup"><span data-stu-id="3136d-128">The following snippet extracts the Id property (of Order) by navigating through the r (reference) property.</span></span>  
  
```  
select o2.r.Id   
from (select ref(o) as r from LOB.Orders as o) as o2   
```  
  
 <span data-ttu-id="3136d-129">Pokud je hodnota odkaz null nebo cílem odkazu ještě neexistuje, výsledek je null.</span><span class="sxs-lookup"><span data-stu-id="3136d-129">If the reference value is null, or if the target of the reference does not exist, the result is null.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3136d-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3136d-130">See also</span></span>
- [<span data-ttu-id="3136d-131">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="3136d-131">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="3136d-132">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="3136d-132">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="3136d-133">CAST</span><span class="sxs-lookup"><span data-stu-id="3136d-133">CAST</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md)
- [<span data-ttu-id="3136d-134">Specifikace CSDL, SSDL a MSL</span><span class="sxs-lookup"><span data-stu-id="3136d-134">CSDL, SSDL, and MSL Specifications</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
