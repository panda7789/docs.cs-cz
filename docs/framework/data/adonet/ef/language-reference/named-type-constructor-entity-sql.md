---
title: Konstruktor pojmenovaného typu (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
ms.openlocfilehash: f95f0dcb92068675b2efff0af7e97b349976bf42
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59329463"
---
# <a name="named-type-constructor-entity-sql"></a><span data-ttu-id="9a003-102">Konstruktor pojmenovaného typu (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="9a003-102">Named Type Constructor (Entity SQL)</span></span>
<span data-ttu-id="9a003-103">Použít k vytvoření instance nominální typy konceptuálních modelů, jako je například Entity nebo komplexní typy.</span><span class="sxs-lookup"><span data-stu-id="9a003-103">Used to create instances of conceptual model nominal types such as Entity or Complex types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a003-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a003-104">Syntax</span></span>  
  
```  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="9a003-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="9a003-105">Arguments</span></span>  
 `identifier`  
 <span data-ttu-id="9a003-106">Hodnota, která je v uvozovkách nebo jednoduchý identifikátor.</span><span class="sxs-lookup"><span data-stu-id="9a003-106">Value that is a simple or quoted identifier.</span></span> <span data-ttu-id="9a003-107">Další informace najdete v tématu [identifikátory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)</span><span class="sxs-lookup"><span data-stu-id="9a003-107">For more information see, [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)</span></span>  
  
 `expression`  
 <span data-ttu-id="9a003-108">Atributy typu, které jsou považovány za umístěné ve stejném pořadí, jak se objeví v deklaraci typu.</span><span class="sxs-lookup"><span data-stu-id="9a003-108">Attributes of the type that are assumed to be in the same order as they appear in the declaration of the type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9a003-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9a003-109">Return Value</span></span>  
 <span data-ttu-id="9a003-110">Instance s názvem komplexní typy a typy entit.</span><span class="sxs-lookup"><span data-stu-id="9a003-110">Instances of named complex types and entity types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a003-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9a003-111">Remarks</span></span>  
 <span data-ttu-id="9a003-112">Následující příklady ukazují, jak vytvořit nominální a komplexní typy:</span><span class="sxs-lookup"><span data-stu-id="9a003-112">The following examples show how to construct nominal and complex types:</span></span>  
  
 <span data-ttu-id="9a003-113">Výraz níže vytvoří instanci `Person` typu:</span><span class="sxs-lookup"><span data-stu-id="9a003-113">The expression below creates an instance of a `Person` type:</span></span>  
  
 `Person("abc", 12)`  
  
 <span data-ttu-id="9a003-114">Výraz níže vytvoří instanci komplexní typ:</span><span class="sxs-lookup"><span data-stu-id="9a003-114">The expression below creates an instance of a complex type:</span></span>  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 <span data-ttu-id="9a003-115">Výraz níže vytvoří instanci vnořené komplexní typ:</span><span class="sxs-lookup"><span data-stu-id="9a003-115">The expression below creates an instance of a nested complex type:</span></span>  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 <span data-ttu-id="9a003-116">Výraz níže vytvoří instanci entity s vnořené komplexní typ:</span><span class="sxs-lookup"><span data-stu-id="9a003-116">The expression below creates an instance of an entity with a nested complex type:</span></span>  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 <span data-ttu-id="9a003-117">Následující příklad ukazuje způsob inicializace vlastností komplexního typu na hodnotu null:</span><span class="sxs-lookup"><span data-stu-id="9a003-117">The following example shows how to initialize a property of a complex type to null:</span></span>`MyModel.ZipCode(‘98118’, null)`  
  
## <a name="example"></a><span data-ttu-id="9a003-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="9a003-118">Example</span></span>  
 <span data-ttu-id="9a003-119">Následující dotaz Entity SQL používá konstruktor pojmenovaného typu k vytvoření instance typu koncepčního modelu.</span><span class="sxs-lookup"><span data-stu-id="9a003-119">The following Entity SQL query uses the named type constructor to create an instance of a conceptual model type.</span></span> <span data-ttu-id="9a003-120">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="9a003-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="9a003-121">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="9a003-121">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="9a003-122">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="9a003-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="9a003-123">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="9a003-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NAMED_TYPE_CONSTRUCTOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#named_type_constructor)]  
  
## <a name="see-also"></a><span data-ttu-id="9a003-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9a003-124">See also</span></span>

- [<span data-ttu-id="9a003-125">Vytváření typů</span><span class="sxs-lookup"><span data-stu-id="9a003-125">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)
- [<span data-ttu-id="9a003-126">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="9a003-126">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
