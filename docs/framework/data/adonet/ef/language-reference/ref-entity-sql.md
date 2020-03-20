---
title: REF (Entita SQL)
ms.date: 03/30/2017
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
ms.openlocfilehash: 40a5afd7eb99dba7cae8fe14ed0a45213fda94a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149944"
---
# <a name="ref-entity-sql"></a><span data-ttu-id="b5b2d-102">REF (Entita SQL)</span><span class="sxs-lookup"><span data-stu-id="b5b2d-102">REF (Entity SQL)</span></span>
<span data-ttu-id="b5b2d-103">Vrátí odkaz na instanci entity.</span><span class="sxs-lookup"><span data-stu-id="b5b2d-103">Returns a reference to an entity instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5b2d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5b2d-104">Syntax</span></span>  
  
```sql  
REF( expression )
```  
  
## <a name="arguments"></a><span data-ttu-id="b5b2d-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="b5b2d-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="b5b2d-106">Libovolný platný výraz, který poskytuje instanci typu entity.</span><span class="sxs-lookup"><span data-stu-id="b5b2d-106">Any valid expression that yields an instance of an entity type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b5b2d-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b5b2d-107">Return Value</span></span>  
 <span data-ttu-id="b5b2d-108">Odkaz na zadanou instanci entity.</span><span class="sxs-lookup"><span data-stu-id="b5b2d-108">A reference to the specified entity instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5b2d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b5b2d-109">Remarks</span></span>  
 <span data-ttu-id="b5b2d-110">Odkaz na entitu se skládá z klíče entity a názvu sady entit.</span><span class="sxs-lookup"><span data-stu-id="b5b2d-110">An entity reference consists of the entity key and an entity set name.</span></span> <span data-ttu-id="b5b2d-111">Vzhledem k tomu, že různé sady entit mohou být založeny na stejném typu entity, může se určitý klíč entity zobrazit ve více sadách entit.</span><span class="sxs-lookup"><span data-stu-id="b5b2d-111">Because different entity sets can be based on the same entity type, a particular entity key can appear in multiple entity sets.</span></span> <span data-ttu-id="b5b2d-112">Odkaz na entitu je však vždy jedinečný.</span><span class="sxs-lookup"><span data-stu-id="b5b2d-112">However, an entity reference is always unique.</span></span> <span data-ttu-id="b5b2d-113">Pokud vstupní výraz představuje trvalou entitu, bude vrácen odkaz na tuto entitu.</span><span class="sxs-lookup"><span data-stu-id="b5b2d-113">If the input expression represents a persisted entity, a reference to this entity will be returned.</span></span> <span data-ttu-id="b5b2d-114">Pokud vstupní výraz není trvalá entita, bude vrácen nulový odkaz.</span><span class="sxs-lookup"><span data-stu-id="b5b2d-114">If the input expression is not a persisted entity, a null reference will be returned.</span></span>  
  
 <span data-ttu-id="b5b2d-115">Pokud operátor extrakce vlastnosti (.) se používá pro přístup k vlastnosti entity, odkaz je automaticky dereferenced.</span><span class="sxs-lookup"><span data-stu-id="b5b2d-115">If the property extraction operator (.) is used to access a property of an entity, the reference is automatically dereferenced.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5b2d-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="b5b2d-116">Example</span></span>  
 <span data-ttu-id="b5b2d-117">Následující dotaz ENTITY SQL používá operátor REF k vrácení odkazu pro argument vstupní entity.</span><span class="sxs-lookup"><span data-stu-id="b5b2d-117">The following Entity SQL query uses the REF operator to return the reference for an input entity argument.</span></span> <span data-ttu-id="b5b2d-118">Stejný dotaz dereferences odkaz, protože používáme operace extrakce vlastnosti (.) pro přístup k vlastnosti Product entity.</span><span class="sxs-lookup"><span data-stu-id="b5b2d-118">The same query dereferences the reference because we are using a property extraction operation (.) to access a property of the Product entity.</span></span> <span data-ttu-id="b5b2d-119">Dotaz je založen na adventureworks prodejní model.</span><span class="sxs-lookup"><span data-stu-id="b5b2d-119">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b5b2d-120">Chcete-li tento dotaz zkompilovat a spustit, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="b5b2d-120">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="b5b2d-121">Postupujte podle postupu v [části Postup: Spusťte dotaz, který vrací výsledky typu PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="b5b2d-121">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="b5b2d-122">Předat následující dotaz jako argument `ExecutePrimitiveTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="b5b2d-122">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#REF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#ref)]  
  
## <a name="see-also"></a><span data-ttu-id="b5b2d-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5b2d-123">See also</span></span>

- [<span data-ttu-id="b5b2d-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="b5b2d-124">DEREF</span></span>](deref-entity-sql.md)
- [<span data-ttu-id="b5b2d-125">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="b5b2d-125">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="b5b2d-126">Klíč</span><span class="sxs-lookup"><span data-stu-id="b5b2d-126">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="b5b2d-127">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b5b2d-127">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="b5b2d-128">Definice typů</span><span class="sxs-lookup"><span data-stu-id="b5b2d-128">Type Definitions</span></span>](type-definitions-entity-sql.md)
