---
title: REF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
ms.openlocfilehash: 9d35306d1299e91ecaa55a7d2818ee1e2982793f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249201"
---
# <a name="ref-entity-sql"></a><span data-ttu-id="a58f0-102">REF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a58f0-102">REF (Entity SQL)</span></span>
<span data-ttu-id="a58f0-103">Vrátí odkaz na instanci entity.</span><span class="sxs-lookup"><span data-stu-id="a58f0-103">Returns a reference to an entity instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a58f0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a58f0-104">Syntax</span></span>  
  
```  
REF( expression )   
```  
  
## <a name="arguments"></a><span data-ttu-id="a58f0-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a58f0-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="a58f0-106">Libovolný platný výraz, který je výsledkem instance typu entity.</span><span class="sxs-lookup"><span data-stu-id="a58f0-106">Any valid expression that yields an instance of an entity type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a58f0-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a58f0-107">Return Value</span></span>  
 <span data-ttu-id="a58f0-108">Odkaz na zadanou instanci entity</span><span class="sxs-lookup"><span data-stu-id="a58f0-108">A reference to the specified entity instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a58f0-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a58f0-109">Remarks</span></span>  
 <span data-ttu-id="a58f0-110">Odkaz na entitu se skládá z klíče entity a názvu sady entit.</span><span class="sxs-lookup"><span data-stu-id="a58f0-110">An entity reference consists of the entity key and an entity set name.</span></span> <span data-ttu-id="a58f0-111">Vzhledem k tomu, že různé sady entit můžou být založené na stejném typu entity, může se konkrétní klíč entity objevit v několika sadách entit.</span><span class="sxs-lookup"><span data-stu-id="a58f0-111">Because different entity sets can be based on the same entity type, a particular entity key can appear in multiple entity sets.</span></span> <span data-ttu-id="a58f0-112">Odkaz na entitu je ale vždycky jedinečný.</span><span class="sxs-lookup"><span data-stu-id="a58f0-112">However, an entity reference is always unique.</span></span> <span data-ttu-id="a58f0-113">Pokud vstupní výraz představuje trvalou entitu, bude vrácena odkaz na tuto entitu.</span><span class="sxs-lookup"><span data-stu-id="a58f0-113">If the input expression represents a persisted entity, a reference to this entity will be returned.</span></span> <span data-ttu-id="a58f0-114">Pokud vstupní výraz není trvalá entita, vrátí se odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="a58f0-114">If the input expression is not a persisted entity, a null reference will be returned.</span></span>  
  
 <span data-ttu-id="a58f0-115">Pokud se k přístupu k vlastnosti entity používá operátor extrakce vlastností (.), odkaz se automaticky odkázat.</span><span class="sxs-lookup"><span data-stu-id="a58f0-115">If the property extraction operator (.) is used to access a property of an entity, the reference is automatically dereferenced.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a58f0-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="a58f0-116">Example</span></span>  
 <span data-ttu-id="a58f0-117">Následující Entity SQL dotaz pomocí operátoru REF vrátí odkaz na vstupní entitu argumentu.</span><span class="sxs-lookup"><span data-stu-id="a58f0-117">The following Entity SQL query uses the REF operator to return the reference for an input entity argument.</span></span> <span data-ttu-id="a58f0-118">Stejný dotaz odkazuje na odkaz, protože používáme operaci extrakce vlastnosti (.) pro přístup k vlastnosti entity produktu.</span><span class="sxs-lookup"><span data-stu-id="a58f0-118">The same query dereferences the reference because we are using a property extraction operation (.) to access a property of the Product entity.</span></span> <span data-ttu-id="a58f0-119">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="a58f0-119">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a58f0-120">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="a58f0-120">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="a58f0-121">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-primitivetype-results.md)PrimitiveType.</span><span class="sxs-lookup"><span data-stu-id="a58f0-121">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="a58f0-122">Předat následující dotaz jako argument `ExecutePrimitiveTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="a58f0-122">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#REF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref)]  
  
## <a name="see-also"></a><span data-ttu-id="a58f0-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a58f0-123">See also</span></span>

- [<span data-ttu-id="a58f0-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="a58f0-124">DEREF</span></span>](deref-entity-sql.md)
- [<span data-ttu-id="a58f0-125">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="a58f0-125">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="a58f0-126">KEY</span><span class="sxs-lookup"><span data-stu-id="a58f0-126">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="a58f0-127">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a58f0-127">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="a58f0-128">Definice typů</span><span class="sxs-lookup"><span data-stu-id="a58f0-128">Type Definitions</span></span>](type-definitions-entity-sql.md)
