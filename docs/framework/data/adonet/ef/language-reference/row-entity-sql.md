---
title: ŘÁDEK (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 06da96e8-55d7-486c-991a-4e514d837ff9
ms.openlocfilehash: dfd0031f49cbdf41797cecf21c149fafde4d7a8c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249251"
---
# <a name="row-entity-sql"></a><span data-ttu-id="b37ec-102">ŘÁDEK (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="b37ec-102">ROW (Entity SQL)</span></span>
<span data-ttu-id="b37ec-103">Vytvoří anonymní, strukturální záznamy typu z jedné nebo více hodnot.</span><span class="sxs-lookup"><span data-stu-id="b37ec-103">Constructs anonymous, structurally typed records from one or more values.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b37ec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b37ec-104">Syntax</span></span>  
  
```  
ROW ( expression [ AS alias ] [,...] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="b37ec-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b37ec-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="b37ec-106">Libovolný platný výraz dotazu, který vrací hodnotu pro sestavení typu řádku.</span><span class="sxs-lookup"><span data-stu-id="b37ec-106">Any valid query expression that returns a value to construct in a row type.</span></span>  
  
 `alias`  
 <span data-ttu-id="b37ec-107">Určuje alias pro hodnotu zadanou v typu řádku.</span><span class="sxs-lookup"><span data-stu-id="b37ec-107">Specifies an alias for the value specified in a row type.</span></span> <span data-ttu-id="b37ec-108">Pokud alias není k dispozici, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nástroj se pokusí vygenerovat alias na základě [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pravidel generování aliasů.</span><span class="sxs-lookup"><span data-stu-id="b37ec-108">If an alias is not provided, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate an alias based on the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] alias generation rules.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b37ec-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b37ec-109">Return Value</span></span>  
 <span data-ttu-id="b37ec-110">Typ řádku.</span><span class="sxs-lookup"><span data-stu-id="b37ec-110">A row type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b37ec-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b37ec-111">Remarks</span></span>  
 <span data-ttu-id="b37ec-112">Použijete konstruktory řádků v rozhraní [!INCLUDE[esql](../../../../../../includes/esql-md.md)] k sestavení anonymních strukturovaných typů záznamů z jedné nebo více hodnot.</span><span class="sxs-lookup"><span data-stu-id="b37ec-112">You use row constructors in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to construct anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="b37ec-113">Typ výsledku konstruktoru řádku je typ řádku, jehož typy polí odpovídají typům hodnot, které byly použity k vytvoření řádku.</span><span class="sxs-lookup"><span data-stu-id="b37ec-113">The result type of a row constructor is a row type whose field types correspond to the types of the values that were used to construct the row.</span></span> <span data-ttu-id="b37ec-114">Například následující výraz vytvoří hodnotu typu `Record(a int, b string, c int)`.</span><span class="sxs-lookup"><span data-stu-id="b37ec-114">For example, the following expression constructs a value of type `Record(a int, b string, c int)`.</span></span>  
  
```  
ROW(1 AS a, "abc" AS b, a+34 AS c)  
```  
  
 <span data-ttu-id="b37ec-115">Pokud neposkytnete alias pro výraz v konstruktoru řádku, Entity Framework se pokusí jednu vygenerovat.</span><span class="sxs-lookup"><span data-stu-id="b37ec-115">If you do not provide an alias for an expression in a row constructor, the Entity Framework will try to generate one.</span></span> <span data-ttu-id="b37ec-116">Další informace najdete v části pravidla aliasing v tématu [identifikátory](identifiers-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="b37ec-116">For more information, see the "Aliasing Rules" section of the [Identifiers](identifiers-entity-sql.md) topic.</span></span>  
  
 <span data-ttu-id="b37ec-117">Následující pravidla platí pro aliasy výrazů v konstruktoru řádku:</span><span class="sxs-lookup"><span data-stu-id="b37ec-117">The following rules apply to expression aliasing in a row constructor:</span></span>  
  
- <span data-ttu-id="b37ec-118">Výrazy v konstruktoru řádku nemůžou odkazovat na jiné aliasy ve stejném konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="b37ec-118">Expressions in a row constructor cannot refer to other aliases in the same constructor.</span></span>  
  
- <span data-ttu-id="b37ec-119">Dva výrazy v konstruktoru stejného řádku nemohou mít stejný alias.</span><span class="sxs-lookup"><span data-stu-id="b37ec-119">Two expressions in the same row constructor cannot have the same alias.</span></span>  
  
 <span data-ttu-id="b37ec-120">Další informace o konstruktorech dotazů naleznete v tématu [sestavování typů](constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="b37ec-120">For more information about query constructors, see [Constructing Types](constructing-types-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b37ec-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="b37ec-121">Example</span></span>  
 <span data-ttu-id="b37ec-122">Následující Entity SQL dotaz používá operátor řádku k vytvoření anonymních strukturovaných záznamů typu.</span><span class="sxs-lookup"><span data-stu-id="b37ec-122">The following Entity SQL query uses the ROW operator to construct anonymous, structurally typed records.</span></span> <span data-ttu-id="b37ec-123">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="b37ec-123">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b37ec-124">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="b37ec-124">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="b37ec-125">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="b37ec-125">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="b37ec-126">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="b37ec-126">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ROW](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#row)]  
  
## <a name="see-also"></a><span data-ttu-id="b37ec-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b37ec-127">See also</span></span>

- [<span data-ttu-id="b37ec-128">Vytváření typů</span><span class="sxs-lookup"><span data-stu-id="b37ec-128">Constructing Types</span></span>](constructing-types-entity-sql.md)
- [<span data-ttu-id="b37ec-129">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b37ec-129">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="b37ec-130">Definice typů</span><span class="sxs-lookup"><span data-stu-id="b37ec-130">Type Definitions</span></span>](type-definitions-entity-sql.md)
