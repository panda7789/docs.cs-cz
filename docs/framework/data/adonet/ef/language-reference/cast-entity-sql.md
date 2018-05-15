---
title: PŘETYPOVÁNÍ (entita SQL)
ms.date: 03/30/2017
ms.assetid: 07b6d750-dfd4-48a9-b86c-3badcbba6f70
ms.openlocfilehash: b3ebd4a7fe9d9e1324210d9f4d1265115bd8617f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="cast-entity-sql"></a><span data-ttu-id="e8ff4-102">PŘETYPOVÁNÍ (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="e8ff4-102">CAST (Entity SQL)</span></span>
<span data-ttu-id="e8ff4-103">Převod výrazu jednoho datového typu.</span><span class="sxs-lookup"><span data-stu-id="e8ff4-103">Converts an expression of one data type to another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8ff4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8ff4-104">Syntax</span></span>  
  
```  
CAST ( expression AS data_type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="e8ff4-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e8ff4-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="e8ff4-106">Libovolný platný výraz, který je převést na `data_type`.</span><span class="sxs-lookup"><span data-stu-id="e8ff4-106">Any valid expression that is convertible to `data_type`.</span></span>  
  
 `data_type`  
 <span data-ttu-id="e8ff4-107">Cíl poskytnuté systémem datového typu.</span><span class="sxs-lookup"><span data-stu-id="e8ff4-107">The target system-supplied data type.</span></span> <span data-ttu-id="e8ff4-108">Musí být primitivního typu (skalární).</span><span class="sxs-lookup"><span data-stu-id="e8ff4-108">It must be a primitive (scalar) type.</span></span> <span data-ttu-id="e8ff4-109">`data_type` Používá závisí na obor dotazu.</span><span class="sxs-lookup"><span data-stu-id="e8ff4-109">The `data_type` used depends on the query space.</span></span> <span data-ttu-id="e8ff4-110">Pokud je dotaz proveden s <xref:System.Data.EntityClient.EntityCommand>, datový typ je typ definovanou v konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="e8ff4-110">If a query is executed with the <xref:System.Data.EntityClient.EntityCommand>, the data type is a type defined in the conceptual model.</span></span> <span data-ttu-id="e8ff4-111">Další informace najdete v tématu [CSDL specifikace](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md).</span><span class="sxs-lookup"><span data-stu-id="e8ff4-111">For more information, see [CSDL Specification](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md).</span></span> <span data-ttu-id="e8ff4-112">Pokud je dotaz proveden s <xref:System.Data.Objects.ObjectQuery%601>, datový typ je stejného typu language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="e8ff4-112">If a query is executed with <xref:System.Data.Objects.ObjectQuery%601>, the data type is a common language runtime (CLR) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8ff4-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e8ff4-113">Return Value</span></span>  
 <span data-ttu-id="e8ff4-114">Vrací stejnou hodnotu jako `data_type`.</span><span class="sxs-lookup"><span data-stu-id="e8ff4-114">Returns the same value as `data_type`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8ff4-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e8ff4-115">Remarks</span></span>  
 <span data-ttu-id="e8ff4-116">Výraz cast má podobnou sémantiku [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] převést výraz.</span><span class="sxs-lookup"><span data-stu-id="e8ff4-116">The cast expression has similar semantics to the [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] CONVERT expression.</span></span> <span data-ttu-id="e8ff4-117">Výraz cast je použít k převodu hodnoty jednoho typu do hodnoty jiného typu.</span><span class="sxs-lookup"><span data-stu-id="e8ff4-117">The cast expression is used to convert a value of one type into a value of another type.</span></span>  
  
```  
CAST( e as T )  
```  
  
 <span data-ttu-id="e8ff4-118">Pokud e je typu je převést na T S a S a potom ve výše uvedené výrazu je výrazem platnou přetypování.</span><span class="sxs-lookup"><span data-stu-id="e8ff4-118">If e is of some type S, and S is convertible to T, then the above expression is a valid cast expression.</span></span> <span data-ttu-id="e8ff4-119">T musí být typu primitivní (skalární).</span><span class="sxs-lookup"><span data-stu-id="e8ff4-119">T must be a primitive (scalar) type.</span></span>  
  
 <span data-ttu-id="e8ff4-120">Hodnoty pro omezující vlastnosti přesnost a měřítko může volitelně zadaný při přetypování na `Edm.Decimal`.</span><span class="sxs-lookup"><span data-stu-id="e8ff4-120">Values for the precision and scale facets may optionally be provided when casting to `Edm.Decimal`.</span></span> <span data-ttu-id="e8ff4-121">Pokud není explicitně k dispozici, výchozí hodnoty pro přesnost a měřítko jsou 18 a 0.</span><span class="sxs-lookup"><span data-stu-id="e8ff4-121">If not explicitly provided, the default values for precision and scale are 18 and 0, respectively.</span></span> <span data-ttu-id="e8ff4-122">Konkrétně, jsou podporovány následující přetížení pro `Decimal`:</span><span class="sxs-lookup"><span data-stu-id="e8ff4-122">Specifically, the following overloads are supported for `Decimal`:</span></span>  
  
-   `CAST( d as Edm.Decimal );`  
  
-   `CAST( d as Edm.Decimal(precision) );`  
  
-   `CAST( d as Edm.Decimal(precision, scale) );`  
  
 <span data-ttu-id="e8ff4-123">Použití výraz cast je považován za explicitní převod.</span><span class="sxs-lookup"><span data-stu-id="e8ff4-123">The use of a cast expression is considered an explicit conversion.</span></span> <span data-ttu-id="e8ff4-124">Explicitní převody může zkrátit dat nebo ztratit přesnost.</span><span class="sxs-lookup"><span data-stu-id="e8ff4-124">Explicit conversions might truncate data or lose precision.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e8ff4-125">PŘETYPOVÁNÍ je podporována pouze přes primitivní typy a typy členů výčtu.</span><span class="sxs-lookup"><span data-stu-id="e8ff4-125">CAST is only supported over primitive types and enumeration member types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8ff4-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8ff4-126">Example</span></span>  
 <span data-ttu-id="e8ff4-127">Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz používá operátor PŘETYPOVÁNÍ k přetypování výrazu jednoho datového typu na jiný.</span><span class="sxs-lookup"><span data-stu-id="e8ff4-127">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the CAST operator to cast an expression of one data type to another.</span></span> <span data-ttu-id="e8ff4-128">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e8ff4-128">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e8ff4-129">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="e8ff4-129">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="e8ff4-130">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="e8ff4-130">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="e8ff4-131">Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="e8ff4-131">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CAST](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#cast)]  
  
## <a name="see-also"></a><span data-ttu-id="e8ff4-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="e8ff4-132">See Also</span></span>  
 [<span data-ttu-id="e8ff4-133">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e8ff4-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
