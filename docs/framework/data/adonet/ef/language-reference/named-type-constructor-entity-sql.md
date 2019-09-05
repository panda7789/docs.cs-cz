---
title: Konstruktor pojmenovaného typu (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
ms.openlocfilehash: c7027614e5667acedb02d871a09df1ac9d799405
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250008"
---
# <a name="named-type-constructor-entity-sql"></a><span data-ttu-id="4ab7b-102">Konstruktor pojmenovaného typu (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4ab7b-102">Named Type Constructor (Entity SQL)</span></span>
<span data-ttu-id="4ab7b-103">Slouží k vytváření instancí nominálních typů konceptuálního modelu, jako je například entita nebo komplexní typy.</span><span class="sxs-lookup"><span data-stu-id="4ab7b-103">Used to create instances of conceptual model nominal types such as Entity or Complex types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ab7b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ab7b-104">Syntax</span></span>  
  
```  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="4ab7b-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="4ab7b-105">Arguments</span></span>  
 `identifier`  
 <span data-ttu-id="4ab7b-106">Hodnota, která je jednoduchý nebo v identifikátoru v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="4ab7b-106">Value that is a simple or quoted identifier.</span></span> <span data-ttu-id="4ab7b-107">Další informace najdete v tématu [identifikátory](identifiers-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="4ab7b-107">For more information see, [Identifiers](identifiers-entity-sql.md)</span></span>  
  
 `expression`  
 <span data-ttu-id="4ab7b-108">Atributy typu, které jsou považovány za stejné pořadí, jaké jsou uvedeny v deklaraci typu.</span><span class="sxs-lookup"><span data-stu-id="4ab7b-108">Attributes of the type that are assumed to be in the same order as they appear in the declaration of the type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ab7b-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4ab7b-109">Return Value</span></span>  
 <span data-ttu-id="4ab7b-110">Instance pojmenovaných komplexních typů a typů entit</span><span class="sxs-lookup"><span data-stu-id="4ab7b-110">Instances of named complex types and entity types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ab7b-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4ab7b-111">Remarks</span></span>  
 <span data-ttu-id="4ab7b-112">Následující příklady znázorňují způsob konstrukce nominálních a komplexních typů:</span><span class="sxs-lookup"><span data-stu-id="4ab7b-112">The following examples show how to construct nominal and complex types:</span></span>  
  
 <span data-ttu-id="4ab7b-113">Výraz níže vytvoří instanci `Person` typu:</span><span class="sxs-lookup"><span data-stu-id="4ab7b-113">The expression below creates an instance of a `Person` type:</span></span>  
  
 `Person("abc", 12)`  
  
 <span data-ttu-id="4ab7b-114">Výraz níže vytvoří instanci komplexního typu:</span><span class="sxs-lookup"><span data-stu-id="4ab7b-114">The expression below creates an instance of a complex type:</span></span>  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 <span data-ttu-id="4ab7b-115">Výraz níže vytvoří instanci vnořeného komplexního typu:</span><span class="sxs-lookup"><span data-stu-id="4ab7b-115">The expression below creates an instance of a nested complex type:</span></span>  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 <span data-ttu-id="4ab7b-116">Výraz níže vytvoří instanci entity s vnořeným komplexním typem:</span><span class="sxs-lookup"><span data-stu-id="4ab7b-116">The expression below creates an instance of an entity with a nested complex type:</span></span>  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 <span data-ttu-id="4ab7b-117">Následující příklad ukazuje, jak inicializovat vlastnost komplexního typu na hodnotu null:`MyModel.ZipCode(‘98118’, null)`</span><span class="sxs-lookup"><span data-stu-id="4ab7b-117">The following example shows how to initialize a property of a complex type to null:`MyModel.ZipCode(‘98118’, null)`</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ab7b-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="4ab7b-118">Example</span></span>  
 <span data-ttu-id="4ab7b-119">Následující Entity SQL dotaz používá konstruktor pojmenovaného typu k vytvoření instance typu koncepčního modelu.</span><span class="sxs-lookup"><span data-stu-id="4ab7b-119">The following Entity SQL query uses the named type constructor to create an instance of a conceptual model type.</span></span> <span data-ttu-id="4ab7b-120">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="4ab7b-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="4ab7b-121">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="4ab7b-121">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="4ab7b-122">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="4ab7b-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="4ab7b-123">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="4ab7b-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NAMED_TYPE_CONSTRUCTOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#named_type_constructor)]  
  
## <a name="see-also"></a><span data-ttu-id="4ab7b-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ab7b-124">See also</span></span>

- [<span data-ttu-id="4ab7b-125">Vytváření typů</span><span class="sxs-lookup"><span data-stu-id="4ab7b-125">Constructing Types</span></span>](constructing-types-entity-sql.md)
- [<span data-ttu-id="4ab7b-126">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4ab7b-126">Entity SQL Reference</span></span>](entity-sql-reference.md)
