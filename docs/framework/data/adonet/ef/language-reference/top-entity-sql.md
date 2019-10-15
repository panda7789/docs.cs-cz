---
title: HORNÍ (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
ms.openlocfilehash: 16be25336bac386c993eae7527c9377be1073d1e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319278"
---
# <a name="top-entity-sql"></a><span data-ttu-id="6c76e-102">HORNÍ (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6c76e-102">TOP (Entity SQL)</span></span>

<span data-ttu-id="6c76e-103">Klauzule SELECT může mít volitelnou klauzuli TOP sub podle volitelného modifikátoru ALL/DISTINCT.</span><span class="sxs-lookup"><span data-stu-id="6c76e-103">The SELECT clause can have an optional TOP sub-clause following the optional ALL/DISTINCT modifier.</span></span> <span data-ttu-id="6c76e-104">Dílčí klauzule TOP určuje, že z výsledku dotazu bude vrácena pouze první sada řádků.</span><span class="sxs-lookup"><span data-stu-id="6c76e-104">The TOP sub-clause specifies that only the first set of rows will be returned from the query result.</span></span>

## <a name="syntax"></a><span data-ttu-id="6c76e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c76e-105">Syntax</span></span>

```sql
[ TOP (n) ]
```

## <a name="arguments"></a><span data-ttu-id="6c76e-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="6c76e-106">Arguments</span></span>

<span data-ttu-id="6c76e-107">`n` číselný výraz, který určuje počet vrácených řádků.</span><span class="sxs-lookup"><span data-stu-id="6c76e-107">`n` The numeric expression that specifies the number of rows to be returned.</span></span> <span data-ttu-id="6c76e-108">`n` může být jeden numerický literál nebo jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="6c76e-108">`n` could be a single numeric literal or a single parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="6c76e-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6c76e-109">Remarks</span></span>

<span data-ttu-id="6c76e-110">Výraz TOP musí být buď jeden numerický literál, nebo jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="6c76e-110">The TOP expression must be either a single numeric literal or a single parameter.</span></span> <span data-ttu-id="6c76e-111">Je-li použit konstantní literál, musí být literální typ implicitně propagačním objektem EDM. Int64 (Byte, Int16, Int32 nebo Int64 nebo libovolný typ poskytovatele, který je namapován na typ, který je možné použít na EDM. Int64) a jeho hodnota musí být větší než nebo rovna nule.</span><span class="sxs-lookup"><span data-stu-id="6c76e-111">If a constant literal is used, the literal type must be implicitly promotable to Edm.Int64 (byte, int16, int32 or int64 or any provider type that maps to a type that is promotable to Edm.Int64) and its value must be greater than or equal to zero.</span></span> <span data-ttu-id="6c76e-112">V opačném případě bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="6c76e-112">Otherwise an exception will be raised.</span></span> <span data-ttu-id="6c76e-113">Pokud je parametr použit jako výraz, musí být typ parametru také implicitně propagačním objektem EDM. Int64, ale během kompilace nebude nijak ověřována skutečná hodnota parametru, protože hodnoty parametrů jsou zpožděny.</span><span class="sxs-lookup"><span data-stu-id="6c76e-113">If a parameter is used as an expression, the parameter type must also be implicitly promotable to Edm.Int64, but there will be no validation of the actual parameter value during compilation because the parameter values are late bounded.</span></span>

<span data-ttu-id="6c76e-114">Následuje příklad konstantního výrazu TOP:</span><span class="sxs-lookup"><span data-stu-id="6c76e-114">The following is an example of constant TOP expression:</span></span>

```sql
select distinct top(10) c.a1, c.a2 from T as a
```

<span data-ttu-id="6c76e-115">Následuje příklad parametrizovaného HORNÍho výrazu:</span><span class="sxs-lookup"><span data-stu-id="6c76e-115">The following is an example of parameterized TOP expression:</span></span>

```sql
select distinct top(@topParam) c.a1, c.a2 from T as a
```

<span data-ttu-id="6c76e-116">Klauzule TOP není deterministické, pokud dotaz není seřazen.</span><span class="sxs-lookup"><span data-stu-id="6c76e-116">TOP is non-deterministic unless the query is sorted.</span></span> <span data-ttu-id="6c76e-117">Pokud vyžadujete deterministický výsledek, použijte dílčí klauzule [Skip](skip-entity-sql.md) a [limit](limit-entity-sql.md) v klauzuli [ORDER by](order-by-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="6c76e-117">If you require a deterministic result, use the [SKIP](skip-entity-sql.md) and [LIMIT](limit-entity-sql.md) sub-clauses in the [ORDER BY](order-by-entity-sql.md) clause.</span></span> <span data-ttu-id="6c76e-118">Klauzule TOP a SKIP a LIMIT se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="6c76e-118">The TOP and SKIP/LIMIT are mutually exclusive.</span></span>

## <a name="example"></a><span data-ttu-id="6c76e-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="6c76e-119">Example</span></span>

<span data-ttu-id="6c76e-120">Následující dotaz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] používá začátek k určení horního řádku, který se má vrátit z výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="6c76e-120">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TOP to specify the top one row to be returned from the query result.</span></span> <span data-ttu-id="6c76e-121">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="6c76e-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6c76e-122">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="6c76e-122">To compile and run this query, follow these steps:</span></span>

1. <span data-ttu-id="6c76e-123">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="6c76e-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>

2. <span data-ttu-id="6c76e-124">Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="6c76e-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>

    [!code-sql[DP EntityServices Concepts#TOP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#top)]

## <a name="see-also"></a><span data-ttu-id="6c76e-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6c76e-125">See also</span></span>

- [<span data-ttu-id="6c76e-126">SELECT</span><span class="sxs-lookup"><span data-stu-id="6c76e-126">SELECT</span></span>](select-entity-sql.md)
- [<span data-ttu-id="6c76e-127">SKIP</span><span class="sxs-lookup"><span data-stu-id="6c76e-127">SKIP</span></span>](skip-entity-sql.md)
- [<span data-ttu-id="6c76e-128">LIMIT</span><span class="sxs-lookup"><span data-stu-id="6c76e-128">LIMIT</span></span>](limit-entity-sql.md)
- [<span data-ttu-id="6c76e-129">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="6c76e-129">ORDER BY</span></span>](order-by-entity-sql.md)
- [<span data-ttu-id="6c76e-130">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="6c76e-130">Entity SQL Reference</span></span>](entity-sql-reference.md)
