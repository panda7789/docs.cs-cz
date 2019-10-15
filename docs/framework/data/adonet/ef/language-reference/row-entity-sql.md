---
title: ŘÁDEK (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 06da96e8-55d7-486c-991a-4e514d837ff9
ms.openlocfilehash: 4fb16fe0072066580bff36ac0879ff38217f1e34
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319378"
---
# <a name="row-entity-sql"></a><span data-ttu-id="3e1ac-102">ŘÁDEK (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3e1ac-102">ROW (Entity SQL)</span></span>
<span data-ttu-id="3e1ac-103">Vytvoří anonymní, strukturální záznamy typu z jedné nebo více hodnot.</span><span class="sxs-lookup"><span data-stu-id="3e1ac-103">Constructs anonymous, structurally typed records from one or more values.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e1ac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e1ac-104">Syntax</span></span>  
  
```sql  
ROW ( expression [ AS alias ] [,...] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="3e1ac-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3e1ac-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="3e1ac-106">Libovolný platný výraz dotazu, který vrací hodnotu pro sestavení typu řádku.</span><span class="sxs-lookup"><span data-stu-id="3e1ac-106">Any valid query expression that returns a value to construct in a row type.</span></span>  
  
 `alias`  
 <span data-ttu-id="3e1ac-107">Určuje alias pro hodnotu zadanou v typu řádku.</span><span class="sxs-lookup"><span data-stu-id="3e1ac-107">Specifies an alias for the value specified in a row type.</span></span> <span data-ttu-id="3e1ac-108">Pokud alias není k dispozici, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] se pokusí vygenerovat alias na základě pravidel generování aliasů [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3e1ac-108">If an alias is not provided, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate an alias based on the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] alias generation rules.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3e1ac-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3e1ac-109">Return Value</span></span>  
 <span data-ttu-id="3e1ac-110">Typ řádku.</span><span class="sxs-lookup"><span data-stu-id="3e1ac-110">A row type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e1ac-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3e1ac-111">Remarks</span></span>  
 <span data-ttu-id="3e1ac-112">Konstruktory řádků v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] slouží k vytváření anonymních strukturně typových záznamů z jedné nebo více hodnot.</span><span class="sxs-lookup"><span data-stu-id="3e1ac-112">You use row constructors in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to construct anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="3e1ac-113">Typ výsledku konstruktoru řádku je typ řádku, jehož typy polí odpovídají typům hodnot, které byly použity k vytvoření řádku.</span><span class="sxs-lookup"><span data-stu-id="3e1ac-113">The result type of a row constructor is a row type whose field types correspond to the types of the values that were used to construct the row.</span></span> <span data-ttu-id="3e1ac-114">Například následující výraz vytvoří hodnotu typu `Record(a int, b string, c int)`.</span><span class="sxs-lookup"><span data-stu-id="3e1ac-114">For example, the following expression constructs a value of type `Record(a int, b string, c int)`.</span></span>  
  
```sql  
ROW(1 AS a, "abc" AS b, a+34 AS c)  
```  
  
 <span data-ttu-id="3e1ac-115">Pokud neposkytnete alias pro výraz v konstruktoru řádku, Entity Framework se pokusí jednu vygenerovat.</span><span class="sxs-lookup"><span data-stu-id="3e1ac-115">If you do not provide an alias for an expression in a row constructor, the Entity Framework will try to generate one.</span></span> <span data-ttu-id="3e1ac-116">Další informace najdete v části pravidla aliasing v tématu [identifikátory](identifiers-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="3e1ac-116">For more information, see the "Aliasing Rules" section of the [Identifiers](identifiers-entity-sql.md) topic.</span></span>  
  
 <span data-ttu-id="3e1ac-117">Následující pravidla platí pro aliasy výrazů v konstruktoru řádku:</span><span class="sxs-lookup"><span data-stu-id="3e1ac-117">The following rules apply to expression aliasing in a row constructor:</span></span>  
  
- <span data-ttu-id="3e1ac-118">Výrazy v konstruktoru řádku nemůžou odkazovat na jiné aliasy ve stejném konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="3e1ac-118">Expressions in a row constructor cannot refer to other aliases in the same constructor.</span></span>  
  
- <span data-ttu-id="3e1ac-119">Dva výrazy v konstruktoru stejného řádku nemohou mít stejný alias.</span><span class="sxs-lookup"><span data-stu-id="3e1ac-119">Two expressions in the same row constructor cannot have the same alias.</span></span>  
  
 <span data-ttu-id="3e1ac-120">Další informace o konstruktorech dotazů naleznete v tématu [sestavování typů](constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="3e1ac-120">For more information about query constructors, see [Constructing Types](constructing-types-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e1ac-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="3e1ac-121">Example</span></span>  
 <span data-ttu-id="3e1ac-122">Následující Entity SQL dotaz používá operátor řádku k vytvoření anonymních strukturovaných záznamů typu.</span><span class="sxs-lookup"><span data-stu-id="3e1ac-122">The following Entity SQL query uses the ROW operator to construct anonymous, structurally typed records.</span></span> <span data-ttu-id="3e1ac-123">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="3e1ac-123">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3e1ac-124">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="3e1ac-124">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="3e1ac-125">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="3e1ac-125">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="3e1ac-126">Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="3e1ac-126">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#ROW](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#row)]  
  
## <a name="see-also"></a><span data-ttu-id="3e1ac-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3e1ac-127">See also</span></span>

- [<span data-ttu-id="3e1ac-128">Vytváření typů</span><span class="sxs-lookup"><span data-stu-id="3e1ac-128">Constructing Types</span></span>](constructing-types-entity-sql.md)
- [<span data-ttu-id="3e1ac-129">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="3e1ac-129">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="3e1ac-130">Definice typů</span><span class="sxs-lookup"><span data-stu-id="3e1ac-130">Type Definitions</span></span>](type-definitions-entity-sql.md)
