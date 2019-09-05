---
title: Přetypování (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 07b6d750-dfd4-48a9-b86c-3badcbba6f70
ms.openlocfilehash: 385f9a8057ea6aa3637f7fae6fec79154ac625ba
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251235"
---
# <a name="cast-entity-sql"></a><span data-ttu-id="4429c-102">Přetypování (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4429c-102">CAST (Entity SQL)</span></span>
<span data-ttu-id="4429c-103">Převede výraz jednoho datového typu na jiný.</span><span class="sxs-lookup"><span data-stu-id="4429c-103">Converts an expression of one data type to another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4429c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4429c-104">Syntax</span></span>  
  
```  
CAST ( expression AS data_type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="4429c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="4429c-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="4429c-106">Libovolný platný výraz, který lze převést `data_type`na.</span><span class="sxs-lookup"><span data-stu-id="4429c-106">Any valid expression that is convertible to `data_type`.</span></span>  
  
 `data_type`  
 <span data-ttu-id="4429c-107">Cílový datový typ zadaný systémem.</span><span class="sxs-lookup"><span data-stu-id="4429c-107">The target system-supplied data type.</span></span> <span data-ttu-id="4429c-108">Musí se jednat o primitivní (skalární) typ.</span><span class="sxs-lookup"><span data-stu-id="4429c-108">It must be a primitive (scalar) type.</span></span> <span data-ttu-id="4429c-109">`data_type` Použitá velikost závisí na prostoru dotazu.</span><span class="sxs-lookup"><span data-stu-id="4429c-109">The `data_type` used depends on the query space.</span></span> <span data-ttu-id="4429c-110">Pokud je dotaz spuštěn s <xref:System.Data.EntityClient.EntityCommand>, datový typ je typ definovaný v koncepčním modelu.</span><span class="sxs-lookup"><span data-stu-id="4429c-110">If a query is executed with the <xref:System.Data.EntityClient.EntityCommand>, the data type is a type defined in the conceptual model.</span></span> <span data-ttu-id="4429c-111">Další informace najdete v tématu [specifikace CSDL](csdl-specification.md).</span><span class="sxs-lookup"><span data-stu-id="4429c-111">For more information, see [CSDL Specification](csdl-specification.md).</span></span> <span data-ttu-id="4429c-112">Pokud je spuštěn dotaz s <xref:System.Data.Objects.ObjectQuery%601>, datový typ je typ modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="4429c-112">If a query is executed with <xref:System.Data.Objects.ObjectQuery%601>, the data type is a common language runtime (CLR) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4429c-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4429c-113">Return Value</span></span>  
 <span data-ttu-id="4429c-114">Vrací stejnou hodnotu jako `data_type`.</span><span class="sxs-lookup"><span data-stu-id="4429c-114">Returns the same value as `data_type`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4429c-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4429c-115">Remarks</span></span>  
 <span data-ttu-id="4429c-116">Výraz přetypování má podobnou sémantiku jako výraz převodu Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="4429c-116">The cast expression has similar semantics to the Transact-SQL CONVERT expression.</span></span> <span data-ttu-id="4429c-117">Výraz přetypování se používá k převodu hodnoty jednoho typu na hodnotu jiného typu.</span><span class="sxs-lookup"><span data-stu-id="4429c-117">The cast expression is used to convert a value of one type into a value of another type.</span></span>  
  
```  
CAST( e as T )  
```  
  
 <span data-ttu-id="4429c-118">Pokud je e v některém typu, a je převoditelné na T, pak je výše uvedený výraz platným výrazem přetypování.</span><span class="sxs-lookup"><span data-stu-id="4429c-118">If e is of some type S, and S is convertible to T, then the above expression is a valid cast expression.</span></span> <span data-ttu-id="4429c-119">T musí být primitivní (skalární) typ.</span><span class="sxs-lookup"><span data-stu-id="4429c-119">T must be a primitive (scalar) type.</span></span>  
  
 <span data-ttu-id="4429c-120">Hodnoty omezujících vlastností Precision a Scale mohou být volitelně poskytnuty při přetypování do `Edm.Decimal`.</span><span class="sxs-lookup"><span data-stu-id="4429c-120">Values for the precision and scale facets may optionally be provided when casting to `Edm.Decimal`.</span></span> <span data-ttu-id="4429c-121">Pokud explicitně neposkytnete, výchozí hodnoty pro přesnost a měřítko jsou 18 a 0 v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="4429c-121">If not explicitly provided, the default values for precision and scale are 18 and 0, respectively.</span></span> <span data-ttu-id="4429c-122">Konkrétně jsou podporována následující přetížení pro `Decimal`:</span><span class="sxs-lookup"><span data-stu-id="4429c-122">Specifically, the following overloads are supported for `Decimal`:</span></span>  
  
- `CAST( d as Edm.Decimal );`  
  
- `CAST( d as Edm.Decimal(precision) );`  
  
- `CAST( d as Edm.Decimal(precision, scale) );`  
  
 <span data-ttu-id="4429c-123">Použití výrazu přetypování je považováno za explicitní převod.</span><span class="sxs-lookup"><span data-stu-id="4429c-123">The use of a cast expression is considered an explicit conversion.</span></span> <span data-ttu-id="4429c-124">Explicitní převody mohou zkrátit data nebo ztratit přesnost.</span><span class="sxs-lookup"><span data-stu-id="4429c-124">Explicit conversions might truncate data or lose precision.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4429c-125">Funkce CAST je podporována pouze u primitivních typů a typů členů výčtu.</span><span class="sxs-lookup"><span data-stu-id="4429c-125">CAST is only supported over primitive types and enumeration member types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4429c-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="4429c-126">Example</span></span>  
 <span data-ttu-id="4429c-127">Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz používá operátor přetypování k přetypování výrazu jednoho datového typu na jiný.</span><span class="sxs-lookup"><span data-stu-id="4429c-127">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the CAST operator to cast an expression of one data type to another.</span></span> <span data-ttu-id="4429c-128">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="4429c-128">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="4429c-129">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="4429c-129">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="4429c-130">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-primitivetype-results.md)PrimitiveType.</span><span class="sxs-lookup"><span data-stu-id="4429c-130">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="4429c-131">Předat následující dotaz jako argument `ExecutePrimitiveTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="4429c-131">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CAST](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#cast)]  
  
## <a name="see-also"></a><span data-ttu-id="4429c-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4429c-132">See also</span></span>

- [<span data-ttu-id="4429c-133">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4429c-133">Entity SQL Reference</span></span>](entity-sql-reference.md)
