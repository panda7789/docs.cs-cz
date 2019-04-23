---
title: ROW (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 06da96e8-55d7-486c-991a-4e514d837ff9
ms.openlocfilehash: b83020601373ba93124dfb24308dd048bfa3c6dc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59319388"
---
# <a name="row-entity-sql"></a><span data-ttu-id="24d4e-102">ROW (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="24d4e-102">ROW (Entity SQL)</span></span>
<span data-ttu-id="24d4e-103">Sestaví anonymní, strukturálně typy záznamů z jedné nebo více hodnot.</span><span class="sxs-lookup"><span data-stu-id="24d4e-103">Constructs anonymous, structurally typed records from one or more values.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24d4e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="24d4e-104">Syntax</span></span>  
  
```  
ROW ( expression [ AS alias ] [,...] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="24d4e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="24d4e-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="24d4e-106">Libovolný platný dotaz výraz, který vrací hodnotu k sestavení kompletních v typu řádku.</span><span class="sxs-lookup"><span data-stu-id="24d4e-106">Any valid query expression that returns a value to construct in a row type.</span></span>  
  
 `alias`  
 <span data-ttu-id="24d4e-107">Určuje alias pro hodnotu zadanou v typu řádku.</span><span class="sxs-lookup"><span data-stu-id="24d4e-107">Specifies an alias for the value specified in a row type.</span></span> <span data-ttu-id="24d4e-108">Pokud není k dispozici jako alias, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pokusí vygenerovat alias na základě [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pravidel pro vytvoření aliasu.</span><span class="sxs-lookup"><span data-stu-id="24d4e-108">If an alias is not provided, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate an alias based on the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] alias generation rules.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24d4e-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="24d4e-109">Return Value</span></span>  
 <span data-ttu-id="24d4e-110">Typ řádku.</span><span class="sxs-lookup"><span data-stu-id="24d4e-110">A row type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24d4e-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="24d4e-111">Remarks</span></span>  
 <span data-ttu-id="24d4e-112">Použití konstruktorů řádek v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] k sestavení kompletních anonymní, strukturálně typy záznamů z jedné nebo více hodnot.</span><span class="sxs-lookup"><span data-stu-id="24d4e-112">You use row constructors in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to construct anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="24d4e-113">Výsledný typ konstruktoru řádku je typ řádku, jejichž pole typy odpovídají typům hodnot, které byly použity k vytvoření řádku.</span><span class="sxs-lookup"><span data-stu-id="24d4e-113">The result type of a row constructor is a row type whose field types correspond to the types of the values that were used to construct the row.</span></span> <span data-ttu-id="24d4e-114">Například následující výraz vytvoří hodnotu typu `Record(a int, b string, c int)`.</span><span class="sxs-lookup"><span data-stu-id="24d4e-114">For example, the following expression constructs a value of type `Record(a int, b string, c int)`.</span></span>  
  
```  
ROW(1 AS a, "abc" AS b, a+34 AS c)  
```  
  
 <span data-ttu-id="24d4e-115">Pokud nezadáte alias pro výraz v konstruktoru row, Entity Framework se pokusí vygenerovat.</span><span class="sxs-lookup"><span data-stu-id="24d4e-115">If you do not provide an alias for an expression in a row constructor, the Entity Framework will try to generate one.</span></span> <span data-ttu-id="24d4e-116">Další informace najdete v tématu "Pravidla pro aliasy" část [identifikátory](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="24d4e-116">For more information, see the "Aliasing Rules" section of the [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md) topic.</span></span>  
  
 <span data-ttu-id="24d4e-117">Výraz aliasing v konstruktoru row platí následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="24d4e-117">The following rules apply to expression aliasing in a row constructor:</span></span>  
  
-   <span data-ttu-id="24d4e-118">Výrazy v konstruktoru row nelze odkazovat na jiné aliasy v konstruktoru stejné.</span><span class="sxs-lookup"><span data-stu-id="24d4e-118">Expressions in a row constructor cannot refer to other aliases in the same constructor.</span></span>  
  
-   <span data-ttu-id="24d4e-119">Dvou výrazů ve stejné konstruktor row nemůže mít stejný alias.</span><span class="sxs-lookup"><span data-stu-id="24d4e-119">Two expressions in the same row constructor cannot have the same alias.</span></span>  
  
 <span data-ttu-id="24d4e-120">Další informace o konstruktorech dotazu naleznete v tématu [vytváření typů](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="24d4e-120">For more information about query constructors, see [Constructing Types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="24d4e-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="24d4e-121">Example</span></span>  
 <span data-ttu-id="24d4e-122">Následující dotaz Entity SQL používá operátor řádek k vytvoření anonymní, strukturálně typy záznamů.</span><span class="sxs-lookup"><span data-stu-id="24d4e-122">The following Entity SQL query uses the ROW operator to construct anonymous, structurally typed records.</span></span> <span data-ttu-id="24d4e-123">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="24d4e-123">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="24d4e-124">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="24d4e-124">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="24d4e-125">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="24d4e-125">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="24d4e-126">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="24d4e-126">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ROW](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#row)]  
  
## <a name="see-also"></a><span data-ttu-id="24d4e-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="24d4e-127">See also</span></span>

- [<span data-ttu-id="24d4e-128">Vytváření typů</span><span class="sxs-lookup"><span data-stu-id="24d4e-128">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)
- [<span data-ttu-id="24d4e-129">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="24d4e-129">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="24d4e-130">Definice typů</span><span class="sxs-lookup"><span data-stu-id="24d4e-130">Type Definitions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)
