---
title: ISOF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: c4c4cbf74cb17cf43e79c42ff42d1e68122fd534
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319721"
---
# <a name="isof-entity-sql"></a><span data-ttu-id="d6c87-102">ISOF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d6c87-102">ISOF (Entity SQL)</span></span>
<span data-ttu-id="d6c87-103">Určuje, zda je typ výrazu zadaného typu nebo některého z jeho podtypů.</span><span class="sxs-lookup"><span data-stu-id="d6c87-103">Determines whether the type of an expression is of the specified type or one of its subtypes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6c87-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6c87-104">Syntax</span></span>  
  
```sql  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="d6c87-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d6c87-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="d6c87-106">Libovolný platný výraz dotazu pro určení typu.</span><span class="sxs-lookup"><span data-stu-id="d6c87-106">Any valid query expression to determine the type of.</span></span>  
  
 <span data-ttu-id="d6c87-107">MĚNÍ</span><span class="sxs-lookup"><span data-stu-id="d6c87-107">NOT</span></span>  
 <span data-ttu-id="d6c87-108">Negace datového modelu EDM. Logický výsledek pro je.</span><span class="sxs-lookup"><span data-stu-id="d6c87-108">Negates the EDM.Boolean result of IS OF.</span></span>  
  
 <span data-ttu-id="d6c87-109">POUZE</span><span class="sxs-lookup"><span data-stu-id="d6c87-109">ONLY</span></span>  
 <span data-ttu-id="d6c87-110">Určuje, že vrací hodnotu `true` pouze v případě, že `expression` je typu `type` a nikoli žádné z jeho podtypu.</span><span class="sxs-lookup"><span data-stu-id="d6c87-110">Specifies that IS OF returns `true` only if `expression` is of type `type` and not any of one its subtypes.</span></span>  
  
 `type`  
 <span data-ttu-id="d6c87-111">Typ pro otestování @no__t 0 proti.</span><span class="sxs-lookup"><span data-stu-id="d6c87-111">The type to test `expression` against.</span></span> <span data-ttu-id="d6c87-112">Typ musí být kvalifikovaný v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d6c87-112">The type must be namespace-qualified.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6c87-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d6c87-113">Return Value</span></span>  
 <span data-ttu-id="d6c87-114">`true`, pokud `expression` je typu T a T je buď základní typ, nebo odvozený typ `type`; null, pokud `expression` má za běhu hodnotu null; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="d6c87-114">`true` if `expression` is of type T and T is either a base type, or a derived type of `type`; null if `expression` is null at runtime; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6c87-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d6c87-115">Remarks</span></span>  
 <span data-ttu-id="d6c87-116">Výrazy `expression IS NOT OF (type)` a `expression IS NOT OF (ONLY type)` jsou syntakticky ekvivalentní `NOT (expression IS OF (type))` a `NOT (expression IS OF (ONLY type))` v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d6c87-116">The expressions `expression IS NOT OF (type)` and `expression IS NOT OF (ONLY type)` are syntactically equivalent to `NOT (expression IS OF (type))` and `NOT (expression IS OF (ONLY type))`, respectively.</span></span>  
  
 <span data-ttu-id="d6c87-117">Následující tabulka ukazuje chování operátoru `IS OF` v některých typických a rohových vzorcích.</span><span class="sxs-lookup"><span data-stu-id="d6c87-117">The following table shows the behavior of `IS OF` operator over some typical- and corner patterns.</span></span> <span data-ttu-id="d6c87-118">Všechny výjimky jsou vyvolány na straně klienta před vyvoláním zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="d6c87-118">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="d6c87-119">Vzor</span><span class="sxs-lookup"><span data-stu-id="d6c87-119">Pattern</span></span>|<span data-ttu-id="d6c87-120">Předvídatelně</span><span class="sxs-lookup"><span data-stu-id="d6c87-120">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="d6c87-121">hodnota null je typu (EntityType).</span><span class="sxs-lookup"><span data-stu-id="d6c87-121">null IS OF (EntityType)</span></span>|<span data-ttu-id="d6c87-122">Vyvolá</span><span class="sxs-lookup"><span data-stu-id="d6c87-122">Throws</span></span>|  
|<span data-ttu-id="d6c87-123">hodnota null je (ComplexType).</span><span class="sxs-lookup"><span data-stu-id="d6c87-123">null IS OF (ComplexType)</span></span>|<span data-ttu-id="d6c87-124">Vyvolá</span><span class="sxs-lookup"><span data-stu-id="d6c87-124">Throws</span></span>|  
|<span data-ttu-id="d6c87-125">hodnota null je (RowType).</span><span class="sxs-lookup"><span data-stu-id="d6c87-125">null IS OF (RowType)</span></span>|<span data-ttu-id="d6c87-126">Vyvolá</span><span class="sxs-lookup"><span data-stu-id="d6c87-126">Throws</span></span>|  
|<span data-ttu-id="d6c87-127">ZPRACOVÁVÁ se (hodnota null jako EntityType) je typu (EntityType).</span><span class="sxs-lookup"><span data-stu-id="d6c87-127">TREAT (null AS EntityType) IS OF (EntityType)</span></span>|<span data-ttu-id="d6c87-128">Vrátí hodnotu DBNull.</span><span class="sxs-lookup"><span data-stu-id="d6c87-128">Returns DBNull</span></span>|  
|<span data-ttu-id="d6c87-129">ZPRACOVÁVÁ se (hodnota null jako ComplexType) je (ComplexType).</span><span class="sxs-lookup"><span data-stu-id="d6c87-129">TREAT (null AS ComplexType) IS OF (ComplexType)</span></span>|<span data-ttu-id="d6c87-130">Vyvolá</span><span class="sxs-lookup"><span data-stu-id="d6c87-130">Throws</span></span>|  
|<span data-ttu-id="d6c87-131">ZPRACOVÁVÁ se (hodnota null jako RowType) je (RowType).</span><span class="sxs-lookup"><span data-stu-id="d6c87-131">TREAT (null AS RowType) IS OF (RowType)</span></span>|<span data-ttu-id="d6c87-132">Vyvolá</span><span class="sxs-lookup"><span data-stu-id="d6c87-132">Throws</span></span>|  
|<span data-ttu-id="d6c87-133">EntityType je typu (EntityType).</span><span class="sxs-lookup"><span data-stu-id="d6c87-133">EntityType IS OF (EntityType)</span></span>|<span data-ttu-id="d6c87-134">Vrátí hodnotu true nebo false.</span><span class="sxs-lookup"><span data-stu-id="d6c87-134">Returns true/false</span></span>|  
|<span data-ttu-id="d6c87-135">ComplexType je typu (ComplexType).</span><span class="sxs-lookup"><span data-stu-id="d6c87-135">ComplexType IS OF (ComplexType)</span></span>|<span data-ttu-id="d6c87-136">Vyvolá</span><span class="sxs-lookup"><span data-stu-id="d6c87-136">Throws</span></span>|  
|<span data-ttu-id="d6c87-137">RowType je (RowType)</span><span class="sxs-lookup"><span data-stu-id="d6c87-137">RowType IS OF (RowType)</span></span>|<span data-ttu-id="d6c87-138">Vyvolá</span><span class="sxs-lookup"><span data-stu-id="d6c87-138">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d6c87-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6c87-139">Example</span></span>  
 <span data-ttu-id="d6c87-140">Následující dotaz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] používá operátor IS OF k určení typu výrazu dotazu a poté pomocí operátoru "považovat" převést objekt typu kurzu na kolekci objektů typu OnsiteCourse.</span><span class="sxs-lookup"><span data-stu-id="d6c87-140">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS OF operator to determine the type of a query expression, and then uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="d6c87-141">Dotaz je založen na [školním modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d6c87-141">The query is based on the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 <span data-ttu-id="d6c87-142">[! Code-SQL [DP EntityServices koncepty # TREAT_ISOF] ~/samples/snippets/tsql/VS_Snippets_Data/dp EntityServices koncepty/TSQL/EntitySql. SQL # TREAT_ISOF)]</span><span class="sxs-lookup"><span data-stu-id="d6c87-142">[!code-sql[DP EntityServices Concepts#TREAT_ISOF]~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6c87-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d6c87-143">See also</span></span>

- [<span data-ttu-id="d6c87-144">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d6c87-144">Entity SQL Reference</span></span>](entity-sql-reference.md)
