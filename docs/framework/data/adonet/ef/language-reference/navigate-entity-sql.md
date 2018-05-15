---
title: PŘEJDĚTE (entita SQL)
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: c374261ad3702294f5720edb7881e21ba79d85bc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="navigate-entity-sql"></a><span data-ttu-id="bf416-102">PŘEJDĚTE (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="bf416-102">NAVIGATE (Entity SQL)</span></span>
<span data-ttu-id="bf416-103">Přejde přes vztahu mezi entity.</span><span class="sxs-lookup"><span data-stu-id="bf416-103">Navigates over the relationship established between entities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf416-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf416-104">Syntax</span></span>  
  
```  
navigate(instance-expresssion, [relationship-type], [to-end [, from-end] ])  
```  
  
## <a name="arguments"></a><span data-ttu-id="bf416-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="bf416-105">Arguments</span></span>  
 `instance-expresssion`  
 <span data-ttu-id="bf416-106">Instance entity.</span><span class="sxs-lookup"><span data-stu-id="bf416-106">An instance of an entity.</span></span>  
  
 `relationship-type`  
 <span data-ttu-id="bf416-107">Název typu vztahu z soubor konceptuálního schématu definition language (CSDL).</span><span class="sxs-lookup"><span data-stu-id="bf416-107">The type name of the relationship, from the conceptual schema definition language (CSDL) file.</span></span> <span data-ttu-id="bf416-108">`relationship-type` Je kvalifikovaný jako \<obor názvů >.\< Název typu vztahu >.</span><span class="sxs-lookup"><span data-stu-id="bf416-108">The `relationship-type` is qualified as \<namespace>.\<relationship type name>.</span></span>  
  
 `to`  
 <span data-ttu-id="bf416-109">Konec relace.</span><span class="sxs-lookup"><span data-stu-id="bf416-109">The end of the relationship.</span></span>  
  
 `from`  
 <span data-ttu-id="bf416-110">Začátek relace.</span><span class="sxs-lookup"><span data-stu-id="bf416-110">The beginning of the relationship.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bf416-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bf416-111">Return Value</span></span>  
 <span data-ttu-id="bf416-112">Pokud na kardinalitu pro ukončení je 1, bude vrácenou hodnotu `Ref<T>`.</span><span class="sxs-lookup"><span data-stu-id="bf416-112">If the cardinality of the to end is 1, the return value will be `Ref<T>`.</span></span> <span data-ttu-id="bf416-113">Pokud na kardinalitu na konec n, bude vrácenou hodnotu `Collection<Ref<T>>`.</span><span class="sxs-lookup"><span data-stu-id="bf416-113">If the cardinality of the to end is n, the return value will be `Collection<Ref<T>>`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf416-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bf416-114">Remarks</span></span>  
 <span data-ttu-id="bf416-115">První třídy konstrukce v se vztahy [!INCLUDE[adonet_edm](../../../../../../includes/adonet-edm-md.md)] (EDM).</span><span class="sxs-lookup"><span data-stu-id="bf416-115">Relationships are first-class constructs in the [!INCLUDE[adonet_edm](../../../../../../includes/adonet-edm-md.md)] (EDM).</span></span> <span data-ttu-id="bf416-116">Vztahy lze navázat mezi dva nebo více typy entit a uživatelé mohou přejít přes vztah z jednoho elementu end (entita) do jiné.</span><span class="sxs-lookup"><span data-stu-id="bf416-116">Relationships can be established between two or more entity types, and users can navigate over the relationship from one end (entity) to another.</span></span> <span data-ttu-id="bf416-117">`from` a `to` jsou podmíněně volitelné při překladu názvů v rámci relace nedochází k nejednoznačnosti.</span><span class="sxs-lookup"><span data-stu-id="bf416-117">`from` and `to` are conditionally optional when there is no ambiguity in name resolution within the relationship.</span></span>  
  
 <span data-ttu-id="bf416-118">NAVIGOVAT je platná v prostoru O a C.</span><span class="sxs-lookup"><span data-stu-id="bf416-118">NAVIGATE is valid in O and C space.</span></span>  
  
 <span data-ttu-id="bf416-119">Obecná forma konstrukce navigace je následující:</span><span class="sxs-lookup"><span data-stu-id="bf416-119">The general form of a navigation construct is the following:</span></span>  
  
 <span data-ttu-id="bf416-120">přejděte (`instance-expresssion`, `relationship-type`, [ `to-end` [, `from-end` ]])</span><span class="sxs-lookup"><span data-stu-id="bf416-120">navigate(`instance-expresssion`, `relationship-type`, [ `to-end` [, `from-end` ] ] )</span></span>  
  
 <span data-ttu-id="bf416-121">Příklad:</span><span class="sxs-lookup"><span data-stu-id="bf416-121">For example:</span></span>  
  
```  
Select o.Id, navigate(o, OrderCustomer, Customer, Order)  
From LOB.Orders as o  
```  
  
 <span data-ttu-id="bf416-122">Kde je OrderCustomer `relationship`, a jsou zákazníka a pořadí `to-end` (zákazníka) a `from-end` (pořadí elementů) vztahu.</span><span class="sxs-lookup"><span data-stu-id="bf416-122">Where OrderCustomer is the `relationship`, and Customer and Order are the `to-end` (customer) and `from-end` (order) of the relationship.</span></span> <span data-ttu-id="bf416-123">Jestliže byl OrderCustomer relaci n: 1, bude výsledný typ výrazu přejděte Ref\<zákazníka >.</span><span class="sxs-lookup"><span data-stu-id="bf416-123">If OrderCustomer was a n:1 relationship, then the result type of the navigate expression is Ref\<Customer>.</span></span>  
  
 <span data-ttu-id="bf416-124">Jednodušší formu výrazu je následující:</span><span class="sxs-lookup"><span data-stu-id="bf416-124">The simpler form of this expression is the following:</span></span>  
  
```  
Select o.Id, navigate(o, OrderCustomer)  
From LOB.Orders as o  
```  
  
 <span data-ttu-id="bf416-125">Podobně v dotazu má následující formu, přejděte výraz byste mohli vytvořit kolekci < Ref\<pořadí >>.</span><span class="sxs-lookup"><span data-stu-id="bf416-125">Similarly, in a query of the following form, The navigate expression would produce a Collection<Ref\<Order>>.</span></span>  
  
```  
Select c.Id, navigate(c, OrderCustomer, Order, Customer)  
From LOB.Customers as c  
```  
  
 <span data-ttu-id="bf416-126">Instance výraz musí být typu entity nebo ref.</span><span class="sxs-lookup"><span data-stu-id="bf416-126">The instance-expression must be an entity/ref type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf416-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="bf416-127">Example</span></span>  
 <span data-ttu-id="bf416-128">Následující dotaz Entity SQL pomocí operátoru přejděte přejděte přes vztahu mezi adresu a SalesOrderHeader typy entit.</span><span class="sxs-lookup"><span data-stu-id="bf416-128">The following Entity SQL query uses the NAVIGATE operator to navigate over the relationship established between Address and SalesOrderHeader entity types.</span></span> <span data-ttu-id="bf416-129">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="bf416-129">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="bf416-130">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="bf416-130">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="bf416-131">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="bf416-131">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="bf416-132">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="bf416-132">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NAVIGATE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#navigate)]  
  
## <a name="see-also"></a><span data-ttu-id="bf416-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="bf416-133">See Also</span></span>  
 [<span data-ttu-id="bf416-134">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="bf416-134">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="bf416-135">Postupy: přejděte relace se přejděte – operátor</span><span class="sxs-lookup"><span data-stu-id="bf416-135">How to: Navigate Relationships with Navigate Operator</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)
