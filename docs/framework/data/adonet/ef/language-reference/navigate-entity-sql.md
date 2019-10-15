---
title: NAVIGACE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: 09128a367a02e1f9b206a9cc068987166c76381b
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319545"
---
# <a name="navigate-entity-sql"></a><span data-ttu-id="f1544-102">NAVIGACE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f1544-102">NAVIGATE (Entity SQL)</span></span>

<span data-ttu-id="f1544-103">Přejde přes vztah navázaný mezi entitami.</span><span class="sxs-lookup"><span data-stu-id="f1544-103">Navigates over the relationship established between entities.</span></span>

## <a name="syntax"></a><span data-ttu-id="f1544-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1544-104">Syntax</span></span>

```sql
navigate(instance-expression, [relationship-type], [to-end [, from-end] ])
```

## <a name="arguments"></a><span data-ttu-id="f1544-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="f1544-105">Arguments</span></span>

<span data-ttu-id="f1544-106">`instance-expression` instance entity.</span><span class="sxs-lookup"><span data-stu-id="f1544-106">`instance-expression` An instance of an entity.</span></span>

<span data-ttu-id="f1544-107">`relationship-type` název typu relace ze souboru CSDL (konceptuální schéma Definition Language).</span><span class="sxs-lookup"><span data-stu-id="f1544-107">`relationship-type` The type name of the relationship, from the conceptual schema definition language (CSDL) file.</span></span> <span data-ttu-id="f1544-108">@No__t-0 je kvalifikován jako \<namespace >. název typu \<relationship >.</span><span class="sxs-lookup"><span data-stu-id="f1544-108">The `relationship-type` is qualified as \<namespace>.\<relationship type name>.</span></span>

<span data-ttu-id="f1544-109">`to` konci relace.</span><span class="sxs-lookup"><span data-stu-id="f1544-109">`to` The end of the relationship.</span></span>

<span data-ttu-id="f1544-110">@no__t – 0 začátku relace.</span><span class="sxs-lookup"><span data-stu-id="f1544-110">`from` The beginning of the relationship.</span></span>

## <a name="return-value"></a><span data-ttu-id="f1544-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f1544-111">Return Value</span></span>

<span data-ttu-id="f1544-112">Pokud mohutnost pro končí 1, návratová hodnota bude `Ref<T>`.</span><span class="sxs-lookup"><span data-stu-id="f1544-112">If the cardinality of the to end is 1, the return value will be `Ref<T>`.</span></span> <span data-ttu-id="f1544-113">Pokud mohutnost, která má končit, je n, návratová hodnota bude `Collection<Ref<T>>`.</span><span class="sxs-lookup"><span data-stu-id="f1544-113">If the cardinality of the to end is n, the return value will be `Collection<Ref<T>>`.</span></span>

## <a name="remarks"></a><span data-ttu-id="f1544-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f1544-114">Remarks</span></span>

<span data-ttu-id="f1544-115">Relace jsou konstrukce první třídy v model EDM (Entity Data Model) (EDM).</span><span class="sxs-lookup"><span data-stu-id="f1544-115">Relationships are first-class constructs in the Entity Data Model (EDM).</span></span> <span data-ttu-id="f1544-116">Vztahy lze navázat mezi dvěma nebo více typy entit a uživatelé mohou procházet relaci z jednoho elementu end (entity) na jiný.</span><span class="sxs-lookup"><span data-stu-id="f1544-116">Relationships can be established between two or more entity types, and users can navigate over the relationship from one end (entity) to another.</span></span> <span data-ttu-id="f1544-117">`from` a `to` jsou podmíněně volitelné, pokud v rámci vztahu nedochází k nejednoznačnosti v překladu názvů.</span><span class="sxs-lookup"><span data-stu-id="f1544-117">`from` and `to` are conditionally optional when there is no ambiguity in name resolution within the relationship.</span></span>

<span data-ttu-id="f1544-118">NAVIGACE je platná v prostoru O a C.</span><span class="sxs-lookup"><span data-stu-id="f1544-118">NAVIGATE is valid in O and C space.</span></span>

<span data-ttu-id="f1544-119">Obecná forma pro navigační konstrukce je následující:</span><span class="sxs-lookup"><span data-stu-id="f1544-119">The general form of a navigation construct is the following:</span></span>

<span data-ttu-id="f1544-120">Navigate (`instance-expression`, `relationship-type`, [`to-end` [, `from-end`]])</span><span class="sxs-lookup"><span data-stu-id="f1544-120">navigate(`instance-expression`, `relationship-type`, [ `to-end` [, `from-end` ] ] )</span></span>

<span data-ttu-id="f1544-121">Příklad:</span><span class="sxs-lookup"><span data-stu-id="f1544-121">For example:</span></span>

```sql
Select o.Id, navigate(o, OrderCustomer, Customer, Order)
From LOB.Orders as o
```

<span data-ttu-id="f1544-122">Kde OrderCustomer je `relationship` a zákazník a objednávka jsou `to-end` (zákazník) a `from-end` (objednávka) vztahu.</span><span class="sxs-lookup"><span data-stu-id="f1544-122">Where OrderCustomer is the `relationship`, and Customer and Order are the `to-end` (customer) and `from-end` (order) of the relationship.</span></span> <span data-ttu-id="f1544-123">Pokud OrderCustomer byl vztah n:1, pak je výsledný typ výrazu Navigate ref @ no__t-0Customer >.</span><span class="sxs-lookup"><span data-stu-id="f1544-123">If OrderCustomer was a n:1 relationship, then the result type of the navigate expression is Ref\<Customer>.</span></span>

<span data-ttu-id="f1544-124">Jednodušší tvar tohoto výrazu je následující:</span><span class="sxs-lookup"><span data-stu-id="f1544-124">The simpler form of this expression is the following:</span></span>

```sql
Select o.Id, navigate(o, OrderCustomer)
From LOB.Orders as o
```

<span data-ttu-id="f1544-125">Podobně v dotazu následujícího formuláře by výraz Navigate vytvořil kolekci < ref @ no__t-0Order > >.</span><span class="sxs-lookup"><span data-stu-id="f1544-125">Similarly, in a query of the following form, The navigate expression would produce a Collection<Ref\<Order>>.</span></span>

```sql
Select c.Id, navigate(c, OrderCustomer, Order, Customer)
From LOB.Customers as c
```

<span data-ttu-id="f1544-126">Výrazem instance musí být typ entity nebo ref.</span><span class="sxs-lookup"><span data-stu-id="f1544-126">The instance-expression must be an entity/ref type.</span></span>

## <a name="example"></a><span data-ttu-id="f1544-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="f1544-127">Example</span></span>

<span data-ttu-id="f1544-128">Následující Entity SQL dotaz používá operátor navigace k přechodu mezi vztahem vytvořeným mezi typy entit adresa a SalesOrderHeader.</span><span class="sxs-lookup"><span data-stu-id="f1544-128">The following Entity SQL query uses the NAVIGATE operator to navigate over the relationship established between Address and SalesOrderHeader entity types.</span></span> <span data-ttu-id="f1544-129">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="f1544-129">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="f1544-130">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="f1544-130">To compile and run this query, follow these steps:</span></span>

1. <span data-ttu-id="f1544-131">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="f1544-131">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>

2. <span data-ttu-id="f1544-132">Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="f1544-132">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>

 [!code-sql[DP EntityServices Concepts#NAVIGATE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#navigate)]

## <a name="see-also"></a><span data-ttu-id="f1544-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f1544-133">See also</span></span>

- [<span data-ttu-id="f1544-134">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f1544-134">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="f1544-135">Postupy: procházení vztahů pomocí operátoru navigace</span><span class="sxs-lookup"><span data-stu-id="f1544-135">How to: Navigate Relationships with Navigate Operator</span></span>](navigate-entity-sql.md)
