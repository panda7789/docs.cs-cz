---
title: REF (entita SQL)
ms.date: 03/30/2017
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
ms.openlocfilehash: fdad27e52f3cdc366415ed585d4bd80542a6915f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762101"
---
# <a name="ref-entity-sql"></a><span data-ttu-id="e6b5c-102">REF (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="e6b5c-102">REF (Entity SQL)</span></span>
<span data-ttu-id="e6b5c-103">Vrátí odkaz na instanci entity.</span><span class="sxs-lookup"><span data-stu-id="e6b5c-103">Returns a reference to an entity instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6b5c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6b5c-104">Syntax</span></span>  
  
```  
REF( expression )   
```  
  
## <a name="arguments"></a><span data-ttu-id="e6b5c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e6b5c-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="e6b5c-106">Jakýkoli platný výraz, který poskytne instanci typu entity.</span><span class="sxs-lookup"><span data-stu-id="e6b5c-106">Any valid expression that yields an instance of an entity type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6b5c-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e6b5c-107">Return Value</span></span>  
 <span data-ttu-id="e6b5c-108">Odkaz na instanci zadané entity.</span><span class="sxs-lookup"><span data-stu-id="e6b5c-108">A reference to the specified entity instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6b5c-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e6b5c-109">Remarks</span></span>  
 <span data-ttu-id="e6b5c-110">Odkaz na entitu se skládá z klíče entity a nastavte název entity.</span><span class="sxs-lookup"><span data-stu-id="e6b5c-110">An entity reference consists of the entity key and an entity set name.</span></span> <span data-ttu-id="e6b5c-111">Protože sad různých entit může být založen na stejný typ entity, se může zobrazit klíč konkrétní entity ve víc sadách entit.</span><span class="sxs-lookup"><span data-stu-id="e6b5c-111">Because different entity sets can be based on the same entity type, a particular entity key can appear in multiple entity sets.</span></span> <span data-ttu-id="e6b5c-112">Odkaz na entitu je však vždy jedinečný.</span><span class="sxs-lookup"><span data-stu-id="e6b5c-112">However, an entity reference is always unique.</span></span> <span data-ttu-id="e6b5c-113">Pokud vstupní výraz představuje trvalou entity, se vrátí odkaz na tuto entitu.</span><span class="sxs-lookup"><span data-stu-id="e6b5c-113">If the input expression represents a persisted entity, a reference to this entity will be returned.</span></span> <span data-ttu-id="e6b5c-114">Pokud vstupní výraz není trvalý entity, bude vrácen odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="e6b5c-114">If the input expression is not a persisted entity, a null reference will be returned.</span></span>  
  
 <span data-ttu-id="e6b5c-115">Pokud je vlastnost extrakce – operátor (.) se používá pro přístup k vlastnosti entity, je automaticky dereferenced odkaz.</span><span class="sxs-lookup"><span data-stu-id="e6b5c-115">If the property extraction operator (.) is used to access a property of an entity, the reference is automatically dereferenced.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6b5c-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="e6b5c-116">Example</span></span>  
 <span data-ttu-id="e6b5c-117">Následující dotaz Entity SQL pomocí operátoru REF vrací odkaz pro argument vstupní entity.</span><span class="sxs-lookup"><span data-stu-id="e6b5c-117">The following Entity SQL query uses the REF operator to return the reference for an input entity argument.</span></span> <span data-ttu-id="e6b5c-118">Stejný dotaz dereferences odkaz, protože jsme se o přístup k vlastnosti entity produktu pomocí operace extrakce vlastnost (.).</span><span class="sxs-lookup"><span data-stu-id="e6b5c-118">The same query dereferences the reference because we are using a property extraction operation (.) to access a property of the Product entity.</span></span> <span data-ttu-id="e6b5c-119">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e6b5c-119">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e6b5c-120">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="e6b5c-120">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="e6b5c-121">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="e6b5c-121">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="e6b5c-122">Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="e6b5c-122">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#REF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref)]  
  
## <a name="see-also"></a><span data-ttu-id="e6b5c-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6b5c-123">See Also</span></span>  
 [<span data-ttu-id="e6b5c-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="e6b5c-124">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
 [<span data-ttu-id="e6b5c-125">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="e6b5c-125">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [<span data-ttu-id="e6b5c-126">KEY</span><span class="sxs-lookup"><span data-stu-id="e6b5c-126">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
 [<span data-ttu-id="e6b5c-127">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e6b5c-127">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="e6b5c-128">Definice typů</span><span class="sxs-lookup"><span data-stu-id="e6b5c-128">Type Definitions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)
