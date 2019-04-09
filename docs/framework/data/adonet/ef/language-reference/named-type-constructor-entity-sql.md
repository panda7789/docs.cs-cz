---
title: Konstruktor pojmenovaného typu (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
ms.openlocfilehash: 26fb2839f0cc7d645f6ce6daea2d27e35868b63c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168789"
---
# <a name="named-type-constructor-entity-sql"></a><span data-ttu-id="4ed85-102">Konstruktor pojmenovaného typu (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4ed85-102">Named Type Constructor (Entity SQL)</span></span>
<span data-ttu-id="4ed85-103">Použít k vytvoření instance nominální typy konceptuálních modelů, jako je například Entity nebo komplexní typy.</span><span class="sxs-lookup"><span data-stu-id="4ed85-103">Used to create instances of conceptual model nominal types such as Entity or Complex types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ed85-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ed85-104">Syntax</span></span>  
  
```  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="4ed85-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="4ed85-105">Arguments</span></span>  
 `identifier`  
 <span data-ttu-id="4ed85-106">Hodnota, která je v uvozovkách nebo jednoduchý identifikátor.</span><span class="sxs-lookup"><span data-stu-id="4ed85-106">Value that is a simple or quoted identifier.</span></span> <span data-ttu-id="4ed85-107">Další informace najdete v tématu [identifikátory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)</span><span class="sxs-lookup"><span data-stu-id="4ed85-107">For more information see, [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)</span></span>  
  
 `expression`  
 <span data-ttu-id="4ed85-108">Atributy typu, které jsou považovány za umístěné ve stejném pořadí, jak se objeví v deklaraci typu.</span><span class="sxs-lookup"><span data-stu-id="4ed85-108">Attributes of the type that are assumed to be in the same order as they appear in the declaration of the type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ed85-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4ed85-109">Return Value</span></span>  
 <span data-ttu-id="4ed85-110">Instance s názvem komplexní typy a typy entit.</span><span class="sxs-lookup"><span data-stu-id="4ed85-110">Instances of named complex types and entity types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ed85-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4ed85-111">Remarks</span></span>  
 <span data-ttu-id="4ed85-112">Následující příklady ukazují, jak vytvořit nominální a komplexní typy:</span><span class="sxs-lookup"><span data-stu-id="4ed85-112">The following examples show how to construct nominal and complex types:</span></span>  
  
 <span data-ttu-id="4ed85-113">Výraz níže vytvoří instanci `Person` typu:</span><span class="sxs-lookup"><span data-stu-id="4ed85-113">The expression below creates an instance of a `Person` type:</span></span>  
  
 `Person("abc", 12)`  
  
 <span data-ttu-id="4ed85-114">Výraz níže vytvoří instanci komplexní typ:</span><span class="sxs-lookup"><span data-stu-id="4ed85-114">The expression below creates an instance of a complex type:</span></span>  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 <span data-ttu-id="4ed85-115">Výraz níže vytvoří instanci vnořené komplexní typ:</span><span class="sxs-lookup"><span data-stu-id="4ed85-115">The expression below creates an instance of a nested complex type:</span></span>  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 <span data-ttu-id="4ed85-116">Výraz níže vytvoří instanci entity s vnořené komplexní typ:</span><span class="sxs-lookup"><span data-stu-id="4ed85-116">The expression below creates an instance of an entity with a nested complex type:</span></span>  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 <span data-ttu-id="4ed85-117">Následující příklad ukazuje způsob inicializace vlastností komplexního typu na hodnotu null:</span><span class="sxs-lookup"><span data-stu-id="4ed85-117">The following example shows how to initialize a property of a complex type to null:</span></span>`MyModel.ZipCode(‘98118’, null)`  
  
## <a name="example"></a><span data-ttu-id="4ed85-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="4ed85-118">Example</span></span>  
 <span data-ttu-id="4ed85-119">Následující dotaz Entity SQL používá konstruktor pojmenovaného typu k vytvoření instance typu koncepčního modelu.</span><span class="sxs-lookup"><span data-stu-id="4ed85-119">The following Entity SQL query uses the named type constructor to create an instance of a conceptual model type.</span></span> <span data-ttu-id="4ed85-120">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="4ed85-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="4ed85-121">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="4ed85-121">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="4ed85-122">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="4ed85-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="4ed85-123">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="4ed85-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NAMED_TYPE_CONSTRUCTOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#named_type_constructor)]  
  
## <a name="see-also"></a><span data-ttu-id="4ed85-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ed85-124">See also</span></span>

- [<span data-ttu-id="4ed85-125">Vytváření typů</span><span class="sxs-lookup"><span data-stu-id="4ed85-125">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)
- [<span data-ttu-id="4ed85-126">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4ed85-126">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
