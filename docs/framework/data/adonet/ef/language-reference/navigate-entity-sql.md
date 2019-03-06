---
title: NAVIGATE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: 993c07b824d30c89773c5cfea90c7c194c6b3869
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356874"
---
# <a name="navigate-entity-sql"></a><span data-ttu-id="736d9-102">NAVIGATE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="736d9-102">NAVIGATE (Entity SQL)</span></span>

<span data-ttu-id="736d9-103">Přejde přes vztahu mezi entitami.</span><span class="sxs-lookup"><span data-stu-id="736d9-103">Navigates over the relationship established between entities.</span></span>

## <a name="syntax"></a><span data-ttu-id="736d9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="736d9-104">Syntax</span></span>

```
navigate(instance-expression, [relationship-type], [to-end [, from-end] ])
```

## <a name="arguments"></a><span data-ttu-id="736d9-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="736d9-105">Arguments</span></span>

<span data-ttu-id="736d9-106">`instance-expression` Instance entity.</span><span class="sxs-lookup"><span data-stu-id="736d9-106">`instance-expression` An instance of an entity.</span></span>

<span data-ttu-id="736d9-107">`relationship-type` Název typu relace ze souboru Konceptuální schéma definici jazyka (CSDL).</span><span class="sxs-lookup"><span data-stu-id="736d9-107">`relationship-type` The type name of the relationship, from the conceptual schema definition language (CSDL) file.</span></span> <span data-ttu-id="736d9-108">`relationship-type` Je kvalifikovány jako \<oboru názvů >.\< Název typu vztahu >.</span><span class="sxs-lookup"><span data-stu-id="736d9-108">The `relationship-type` is qualified as \<namespace>.\<relationship type name>.</span></span>

<span data-ttu-id="736d9-109">`to` Konci vztahu.</span><span class="sxs-lookup"><span data-stu-id="736d9-109">`to` The end of the relationship.</span></span>

<span data-ttu-id="736d9-110">`from` Začátek relace.</span><span class="sxs-lookup"><span data-stu-id="736d9-110">`from` The beginning of the relationship.</span></span>

## <a name="return-value"></a><span data-ttu-id="736d9-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="736d9-111">Return Value</span></span>

<span data-ttu-id="736d9-112">Pokud Kardinalita do konce je 1, bude návratovou hodnotou `Ref<T>`.</span><span class="sxs-lookup"><span data-stu-id="736d9-112">If the cardinality of the to end is 1, the return value will be `Ref<T>`.</span></span> <span data-ttu-id="736d9-113">Pokud se Kardinalita ukončení je n, bude návratovou hodnotou `Collection<Ref<T>>`.</span><span class="sxs-lookup"><span data-stu-id="736d9-113">If the cardinality of the to end is n, the return value will be `Collection<Ref<T>>`.</span></span>

## <a name="remarks"></a><span data-ttu-id="736d9-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="736d9-114">Remarks</span></span>

<span data-ttu-id="736d9-115">Relace jsou prvotřídní konstrukce v [!INCLUDE[adonet_edm](../../../../../../includes/adonet-edm-md.md)] (EDM).</span><span class="sxs-lookup"><span data-stu-id="736d9-115">Relationships are first-class constructs in the [!INCLUDE[adonet_edm](../../../../../../includes/adonet-edm-md.md)] (EDM).</span></span> <span data-ttu-id="736d9-116">Vztah lze navázat mezi dva nebo více typů entit a uživatelé mohou přejít přes vztah konce (entita).</span><span class="sxs-lookup"><span data-stu-id="736d9-116">Relationships can be established between two or more entity types, and users can navigate over the relationship from one end (entity) to another.</span></span> <span data-ttu-id="736d9-117">`from` a `to` jsou podmíněně volitelné, pokud nedochází k nejednoznačnosti v překlad v rámci relace.</span><span class="sxs-lookup"><span data-stu-id="736d9-117">`from` and `to` are conditionally optional when there is no ambiguity in name resolution within the relationship.</span></span>

<span data-ttu-id="736d9-118">NAVIGOVAT je platný v prostoru O a C.</span><span class="sxs-lookup"><span data-stu-id="736d9-118">NAVIGATE is valid in O and C space.</span></span>

<span data-ttu-id="736d9-119">Obecný tvar konstrukci navigace je následující:</span><span class="sxs-lookup"><span data-stu-id="736d9-119">The general form of a navigation construct is the following:</span></span>

<span data-ttu-id="736d9-120">přejděte (`instance-expression`, `relationship-type`, [ `to-end` [, `from-end` ]])</span><span class="sxs-lookup"><span data-stu-id="736d9-120">navigate(`instance-expression`, `relationship-type`, [ `to-end` [, `from-end` ] ] )</span></span>

<span data-ttu-id="736d9-121">Příklad:</span><span class="sxs-lookup"><span data-stu-id="736d9-121">For example:</span></span>

```sql
Select o.Id, navigate(o, OrderCustomer, Customer, Order)
From LOB.Orders as o
```

<span data-ttu-id="736d9-122">Kde je OrderCustomer `relationship`, a odběratele a objednávky `to-end` (zákazníka) a `from-end` (pořadí) vztahu.</span><span class="sxs-lookup"><span data-stu-id="736d9-122">Where OrderCustomer is the `relationship`, and Customer and Order are the `to-end` (customer) and `from-end` (order) of the relationship.</span></span> <span data-ttu-id="736d9-123">Pokud byl OrderCustomer relaci n: 1, je výsledný typ výraz navigate Ref\<zákazníků >.</span><span class="sxs-lookup"><span data-stu-id="736d9-123">If OrderCustomer was a n:1 relationship, then the result type of the navigate expression is Ref\<Customer>.</span></span>

<span data-ttu-id="736d9-124">Jednodušší formu tento výraz je následující:</span><span class="sxs-lookup"><span data-stu-id="736d9-124">The simpler form of this expression is the following:</span></span>

```sql
Select o.Id, navigate(o, OrderCustomer)
From LOB.Orders as o
```

<span data-ttu-id="736d9-125">Podobně v dotazu má následující formu, výraz navigate byste mohli vytvořit kolekci < Ref\<pořadí >>.</span><span class="sxs-lookup"><span data-stu-id="736d9-125">Similarly, in a query of the following form, The navigate expression would produce a Collection<Ref\<Order>>.</span></span>

```sql
Select c.Id, navigate(c, OrderCustomer, Order, Customer)
From LOB.Customers as c
```

<span data-ttu-id="736d9-126">Výraz instance musí být typu entity nebo ref.</span><span class="sxs-lookup"><span data-stu-id="736d9-126">The instance-expression must be an entity/ref type.</span></span>

## <a name="example"></a><span data-ttu-id="736d9-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="736d9-127">Example</span></span>

<span data-ttu-id="736d9-128">Následující dotaz Entity SQL používá operátor NAVIGOVAT přejít přes vztahu mezi adresu a SalesOrderHeader typy entit.</span><span class="sxs-lookup"><span data-stu-id="736d9-128">The following Entity SQL query uses the NAVIGATE operator to navigate over the relationship established between Address and SalesOrderHeader entity types.</span></span> <span data-ttu-id="736d9-129">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="736d9-129">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="736d9-130">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="736d9-130">To compile and run this query, follow these steps:</span></span>

1. <span data-ttu-id="736d9-131">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="736d9-131">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>

2. <span data-ttu-id="736d9-132">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="736d9-132">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>

 [!code-csharp[DP EntityServices Concepts 2#NAVIGATE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#navigate)]

## <a name="see-also"></a><span data-ttu-id="736d9-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="736d9-133">See also</span></span>

- [<span data-ttu-id="736d9-134">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="736d9-134">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="736d9-135">Postupy: Procházení relací pomocí navigačního operátoru</span><span class="sxs-lookup"><span data-stu-id="736d9-135">How to: Navigate Relationships with Navigate Operator</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)
