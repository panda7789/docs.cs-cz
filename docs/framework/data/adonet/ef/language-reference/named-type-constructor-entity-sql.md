---
title: Konstruktor typu s názvem (entita SQL)
ms.date: 03/30/2017
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
ms.openlocfilehash: 9ffaf55ed54e8479a56e6f9fc4d7a5efe47f8e2a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="named-type-constructor-entity-sql"></a><span data-ttu-id="83f51-102">Konstruktor typu s názvem (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="83f51-102">Named Type Constructor (Entity SQL)</span></span>
<span data-ttu-id="83f51-103">Použít k vytvoření instance konceptuálního modelu nominální například Entity nebo komplexní typy.</span><span class="sxs-lookup"><span data-stu-id="83f51-103">Used to create instances of conceptual model nominal types such as Entity or Complex types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83f51-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83f51-104">Syntax</span></span>  
  
```  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="83f51-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="83f51-105">Arguments</span></span>  
 `identifier`  
 <span data-ttu-id="83f51-106">Hodnota, která je identifikátor jednoduchý nebo uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="83f51-106">Value that is a simple or quoted identifier.</span></span> <span data-ttu-id="83f51-107">Další informace najdete v tématu [identifikátory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)</span><span class="sxs-lookup"><span data-stu-id="83f51-107">For more information see, [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)</span></span>  
  
 `expression`  
 <span data-ttu-id="83f51-108">Atributy typu, které se předpokládá, že se ve stejném pořadí, jak se zobrazují v deklaraci typu.</span><span class="sxs-lookup"><span data-stu-id="83f51-108">Attributes of the type that are assumed to be in the same order as they appear in the declaration of the type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83f51-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="83f51-109">Return Value</span></span>  
 <span data-ttu-id="83f51-110">Instance s názvem komplexní typy a typy entit.</span><span class="sxs-lookup"><span data-stu-id="83f51-110">Instances of named complex types and entity types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83f51-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="83f51-111">Remarks</span></span>  
 <span data-ttu-id="83f51-112">Následující příklady ukazují, jak vytvořit nominální a komplexní typy:</span><span class="sxs-lookup"><span data-stu-id="83f51-112">The following examples show how to construct nominal and complex types:</span></span>  
  
 <span data-ttu-id="83f51-113">Následující výraz vytvoří instanci `Person` typu:</span><span class="sxs-lookup"><span data-stu-id="83f51-113">The expression below creates an instance of a `Person` type:</span></span>  
  
 `Person("abc", 12)`  
  
 <span data-ttu-id="83f51-114">Následující výraz vytvoří instanci komplexního typu:</span><span class="sxs-lookup"><span data-stu-id="83f51-114">The expression below creates an instance of a complex type:</span></span>  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 <span data-ttu-id="83f51-115">Následující výraz vytvoří instanci vnořené komplexního typu:</span><span class="sxs-lookup"><span data-stu-id="83f51-115">The expression below creates an instance of a nested complex type:</span></span>  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 <span data-ttu-id="83f51-116">Následující výraz vytvoří instanci entity s vnořené komplexního typu:</span><span class="sxs-lookup"><span data-stu-id="83f51-116">The expression below creates an instance of an entity with a nested complex type:</span></span>  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 <span data-ttu-id="83f51-117">Následující příklad ukazuje, jak k chybě při inicializaci vlastnosti pro komplexní typ na hodnotu null:`MyModel.ZipCode(‘98118’, null)`</span><span class="sxs-lookup"><span data-stu-id="83f51-117">The following example shows how to initialize a property of a complex type to null:`MyModel.ZipCode(‘98118’, null)`</span></span>  
  
## <a name="example"></a><span data-ttu-id="83f51-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="83f51-118">Example</span></span>  
 <span data-ttu-id="83f51-119">Následující dotaz Entity SQL konstruktor s názvem typu používá k vytvoření instance typu koncepčního modelu.</span><span class="sxs-lookup"><span data-stu-id="83f51-119">The following Entity SQL query uses the named type constructor to create an instance of a conceptual model type.</span></span> <span data-ttu-id="83f51-120">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="83f51-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="83f51-121">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="83f51-121">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="83f51-122">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="83f51-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="83f51-123">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="83f51-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NAMED_TYPE_CONSTRUCTOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#named_type_constructor)]  
  
## <a name="see-also"></a><span data-ttu-id="83f51-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="83f51-124">See Also</span></span>  
 [<span data-ttu-id="83f51-125">Vytváření typů</span><span class="sxs-lookup"><span data-stu-id="83f51-125">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
 [<span data-ttu-id="83f51-126">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="83f51-126">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
