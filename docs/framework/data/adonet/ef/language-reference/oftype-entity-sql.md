---
title: OFTYPE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
ms.openlocfilehash: f1dd5ba92c7b1eaf7117c9732a78e04e5d5a317a
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319459"
---
# <a name="oftype-entity-sql"></a><span data-ttu-id="f23e3-102">OFTYPE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f23e3-102">OFTYPE (Entity SQL)</span></span>
<span data-ttu-id="f23e3-103">Vrátí kolekci objektů z výrazu dotazu, který je určitého typu.</span><span class="sxs-lookup"><span data-stu-id="f23e3-103">Returns a collection of objects from a query expression that is of a specific type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f23e3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f23e3-104">Syntax</span></span>  
  
```sql  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="f23e3-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="f23e3-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="f23e3-106">Libovolný platný výraz dotazu, který vrací kolekci objektů.</span><span class="sxs-lookup"><span data-stu-id="f23e3-106">Any valid query expression that returns a collection of objects.</span></span>  
  
 `test_type`  
 <span data-ttu-id="f23e3-107">Typ pro otestování všech objektů vrácených `expression` proti.</span><span class="sxs-lookup"><span data-stu-id="f23e3-107">The type to test each object returned by `expression` against.</span></span> <span data-ttu-id="f23e3-108">Typ musí být kvalifikován oborem názvů.</span><span class="sxs-lookup"><span data-stu-id="f23e3-108">The type must be qualified by a namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f23e3-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f23e3-109">Return Value</span></span>  
 <span data-ttu-id="f23e3-110">Kolekce objektů, které jsou typu `test_type` nebo základní typ nebo odvozený typ `test_type`.</span><span class="sxs-lookup"><span data-stu-id="f23e3-110">A collection of objects that are of type `test_type`, or a base type or derived type of `test_type`.</span></span> <span data-ttu-id="f23e3-111">Pokud je zadáno pouze, budou vráceny pouze instance `test_type` nebo prázdné kolekce.</span><span class="sxs-lookup"><span data-stu-id="f23e3-111">If ONLY is specified, only instances of the `test_type` or an empty collection will be returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f23e3-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f23e3-112">Remarks</span></span>  
 <span data-ttu-id="f23e3-113">Výraz `OFTYPE` určuje výraz typu, který je vystaven pro provedení testu typu proti jednotlivým prvkům kolekce.</span><span class="sxs-lookup"><span data-stu-id="f23e3-113">An `OFTYPE` expression specifies a type expression that is issued to perform a type test against each element of a collection.</span></span>  <span data-ttu-id="f23e3-114">Výraz `OFTYPE` vytvoří novou kolekci zadaného typu obsahující pouze prvky, které byly buď ekvivalentní tomuto typu, nebo dílčímu typu.</span><span class="sxs-lookup"><span data-stu-id="f23e3-114">The `OFTYPE` expression produces a new collection of the specified type containing only those elements that were either equivalent to that type or a sub-type of it.</span></span>  
  
 <span data-ttu-id="f23e3-115">Výraz `OFTYPE` je zkratkou následujícího výrazu dotazu:</span><span class="sxs-lookup"><span data-stu-id="f23e3-115">An `OFTYPE` expression is an abbreviation of the following query expression:</span></span>  
  
```sql  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 <span data-ttu-id="f23e3-116">Vzhledem k tom, že manažer je podtypu zaměstnance, vytvoří následující výraz kolekci pouze správců z kolekce zaměstnanců:</span><span class="sxs-lookup"><span data-stu-id="f23e3-116">Given that a Manager is a subtype of Employee, the following expression produces a collection of only managers from a collection of employees:</span></span>  
  
```sql  
OfType(employees, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="f23e3-117">Je také možné přetypování kolekce pomocí filtru typů:</span><span class="sxs-lookup"><span data-stu-id="f23e3-117">It is also possible to up cast a collection using the type filter:</span></span>  
  
```sql
OfType(executives, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="f23e3-118">Vzhledem k tomu, že všichni vedoucí pracovníci jsou manažeři, výsledná kolekce stále obsahuje všechny původní vedoucí pracovníky, i když je kolekce teď zadaná jako kolekce manažerů.</span><span class="sxs-lookup"><span data-stu-id="f23e3-118">Since all executives are managers, the resulting collection still contains all the original executives, though the collection is now typed as a collection of managers.</span></span>  
  
 <span data-ttu-id="f23e3-119">Následující tabulka ukazuje chování operátoru `OFTYPE` v některých vzorcích.</span><span class="sxs-lookup"><span data-stu-id="f23e3-119">The following table shows the behavior of the `OFTYPE` operator over some patterns.</span></span> <span data-ttu-id="f23e3-120">Všechny výjimky jsou vyvolány na straně klienta před vyvoláním poskytovatele:</span><span class="sxs-lookup"><span data-stu-id="f23e3-120">All exceptions are thrown from the client side before the provider is invoked:</span></span>  
  
|<span data-ttu-id="f23e3-121">Vzor</span><span class="sxs-lookup"><span data-stu-id="f23e3-121">Pattern</span></span>|<span data-ttu-id="f23e3-122">Předvídatelně</span><span class="sxs-lookup"><span data-stu-id="f23e3-122">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="f23e3-123">OFTYPE (EntityType), EntityType)</span><span class="sxs-lookup"><span data-stu-id="f23e3-123">OFTYPE(Collection(EntityType), EntityType)</span></span>|<span data-ttu-id="f23e3-124">Kolekce (EntityType)</span><span class="sxs-lookup"><span data-stu-id="f23e3-124">Collection(EntityType)</span></span>|  
|<span data-ttu-id="f23e3-125">OFTYPE (Collection), ComplexType)</span><span class="sxs-lookup"><span data-stu-id="f23e3-125">OFTYPE(Collection(ComplexType), ComplexType)</span></span>|<span data-ttu-id="f23e3-126">Vyvolá</span><span class="sxs-lookup"><span data-stu-id="f23e3-126">Throws</span></span>|  
|<span data-ttu-id="f23e3-127">OFTYPE (Collection (RowType); RowType)</span><span class="sxs-lookup"><span data-stu-id="f23e3-127">OFTYPE(Collection(RowType), RowType)</span></span>|<span data-ttu-id="f23e3-128">Vyvolá</span><span class="sxs-lookup"><span data-stu-id="f23e3-128">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f23e3-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="f23e3-129">Example</span></span>  
 <span data-ttu-id="f23e3-130">Následující dotaz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] používá operátor OFTYPE k vrácení kolekce objektů OnsiteCourse z kolekce objektů kurzu.</span><span class="sxs-lookup"><span data-stu-id="f23e3-130">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the OFTYPE operator to return a collection of OnsiteCourse objects from a collection of Course objects.</span></span> <span data-ttu-id="f23e3-131">Dotaz je založen na [školním modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f23e3-131">The query is based on the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-sql[DP EntityServices Concepts#OFTYPE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#oftype)]  
  
## <a name="see-also"></a><span data-ttu-id="f23e3-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f23e3-132">See also</span></span>

- [<span data-ttu-id="f23e3-133">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f23e3-133">Entity SQL Reference</span></span>](entity-sql-reference.md)
