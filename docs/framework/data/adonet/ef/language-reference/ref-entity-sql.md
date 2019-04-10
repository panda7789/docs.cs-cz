---
title: REF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
ms.openlocfilehash: 05e687f951930d92797a863410181585278b067d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330659"
---
# <a name="ref-entity-sql"></a><span data-ttu-id="132f9-102">REF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="132f9-102">REF (Entity SQL)</span></span>
<span data-ttu-id="132f9-103">Vrátí odkaz na instanci entity.</span><span class="sxs-lookup"><span data-stu-id="132f9-103">Returns a reference to an entity instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="132f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="132f9-104">Syntax</span></span>  
  
```  
REF( expression )   
```  
  
## <a name="arguments"></a><span data-ttu-id="132f9-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="132f9-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="132f9-106">Libovolný platný výraz, který vrací instanci typu entity.</span><span class="sxs-lookup"><span data-stu-id="132f9-106">Any valid expression that yields an instance of an entity type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="132f9-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="132f9-107">Return Value</span></span>  
 <span data-ttu-id="132f9-108">Odkaz na zadané zapisovanou instanci entity.</span><span class="sxs-lookup"><span data-stu-id="132f9-108">A reference to the specified entity instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="132f9-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="132f9-109">Remarks</span></span>  
 <span data-ttu-id="132f9-110">Odkaz na entitu se skládá z klíče entity a nastavte název entity.</span><span class="sxs-lookup"><span data-stu-id="132f9-110">An entity reference consists of the entity key and an entity set name.</span></span> <span data-ttu-id="132f9-111">Protože sady různých entit může být založen na stejný typ entity, klíč konkrétní entity mohou objevit v několika sady entit.</span><span class="sxs-lookup"><span data-stu-id="132f9-111">Because different entity sets can be based on the same entity type, a particular entity key can appear in multiple entity sets.</span></span> <span data-ttu-id="132f9-112">Odkaz na entitu je však vždy jedinečná.</span><span class="sxs-lookup"><span data-stu-id="132f9-112">However, an entity reference is always unique.</span></span> <span data-ttu-id="132f9-113">Pokud vstupní výraz představuje trvalou entitu, vrátí se odkaz na tuto entitu.</span><span class="sxs-lookup"><span data-stu-id="132f9-113">If the input expression represents a persisted entity, a reference to this entity will be returned.</span></span> <span data-ttu-id="132f9-114">Pokud vstupní výraz není trvalý entity, vrátí se odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="132f9-114">If the input expression is not a persisted entity, a null reference will be returned.</span></span>  
  
 <span data-ttu-id="132f9-115">Pokud vlastnost extrakce – operátor (.) se používá pro přístup k vlastnosti entity, odkaz je automaticky přes ukazatel.</span><span class="sxs-lookup"><span data-stu-id="132f9-115">If the property extraction operator (.) is used to access a property of an entity, the reference is automatically dereferenced.</span></span>  
  
## <a name="example"></a><span data-ttu-id="132f9-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="132f9-116">Example</span></span>  
 <span data-ttu-id="132f9-117">Následující dotaz Entity SQL používá operátor REF vrací odkaz pro entity vstupní argument.</span><span class="sxs-lookup"><span data-stu-id="132f9-117">The following Entity SQL query uses the REF operator to return the reference for an input entity argument.</span></span> <span data-ttu-id="132f9-118">Stejný dotaz přístupů přes ukazatel, odkaz vzhledem k tomu, že používáme operaci extrakce vlastnosti (.) pro přístup k vlastnosti entitou produkt.</span><span class="sxs-lookup"><span data-stu-id="132f9-118">The same query dereferences the reference because we are using a property extraction operation (.) to access a property of the Product entity.</span></span> <span data-ttu-id="132f9-119">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="132f9-119">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="132f9-120">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="132f9-120">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="132f9-121">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="132f9-121">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="132f9-122">Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="132f9-122">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#REF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref)]  
  
## <a name="see-also"></a><span data-ttu-id="132f9-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="132f9-123">See also</span></span>

- [<span data-ttu-id="132f9-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="132f9-124">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
- [<span data-ttu-id="132f9-125">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="132f9-125">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)
- [<span data-ttu-id="132f9-126">KEY</span><span class="sxs-lookup"><span data-stu-id="132f9-126">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)
- [<span data-ttu-id="132f9-127">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="132f9-127">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="132f9-128">Definice typů</span><span class="sxs-lookup"><span data-stu-id="132f9-128">Type Definitions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)
