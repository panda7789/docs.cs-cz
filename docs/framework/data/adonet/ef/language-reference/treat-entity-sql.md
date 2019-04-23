---
title: TREAT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
ms.openlocfilehash: e1382c4daa513477011a1d1c2132840dfae84de0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59077339"
---
# <a name="treat-entity-sql"></a><span data-ttu-id="14924-102">TREAT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="14924-102">TREAT (Entity SQL)</span></span>
<span data-ttu-id="14924-103">Zpracovává konkrétní základního typu objektu jako objekt zadaného typu odvozené.</span><span class="sxs-lookup"><span data-stu-id="14924-103">Treats an object of a particular base type as an object of the specified derived type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14924-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14924-104">Syntax</span></span>  
  
```  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a><span data-ttu-id="14924-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="14924-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="14924-106">Libovolný platný dotaz výraz, který vrátí entity.</span><span class="sxs-lookup"><span data-stu-id="14924-106">Any valid query expression that returns an entity.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14924-107">Typ zadaného výrazu musí být podtypem typu zadaného datového typu nebo datový typ musí být podtypem typu výrazu.</span><span class="sxs-lookup"><span data-stu-id="14924-107">The type of the specified expression must be a subtype of the specified data type, or the data type must be a subtype of the type of expression.</span></span>  
  
 `type`  
 <span data-ttu-id="14924-108">Typ entity.</span><span class="sxs-lookup"><span data-stu-id="14924-108">An entity type.</span></span> <span data-ttu-id="14924-109">Typ musí být kvalifikován oborem názvů.</span><span class="sxs-lookup"><span data-stu-id="14924-109">The type must be qualified by a namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14924-110">Zadaný výraz musí být podtypem typu zadaného datového typu nebo datový typ musí být podtypem typu výrazu.</span><span class="sxs-lookup"><span data-stu-id="14924-110">The specified expression must be a subtype of the specified data type, or the data type must be a subtype of the expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="14924-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="14924-111">Return Value</span></span>  
 <span data-ttu-id="14924-112">Hodnota zadaného datového typu.</span><span class="sxs-lookup"><span data-stu-id="14924-112">A value of the specified data type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14924-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="14924-113">Remarks</span></span>  
 <span data-ttu-id="14924-114">NAKLÁDÁNÍ se používá k provedení upcasting mezi souvisejícími třídami.</span><span class="sxs-lookup"><span data-stu-id="14924-114">TREAT is used to perform upcasting between related classes.</span></span> <span data-ttu-id="14924-115">Například pokud `Employee` je odvozena z `Person` a p je typu `Person`, `TREAT(p AS NamespaceName.Employee)` upcasts a Obecné `Person` instance na `Employee`; to znamená, je možné považovat za p `Employee`.</span><span class="sxs-lookup"><span data-stu-id="14924-115">For example, if `Employee` derives from `Person` and p is of type `Person`, `TREAT(p AS NamespaceName.Employee)` upcasts a generic `Person` instance to `Employee`; that is, it allows you to treat p as `Employee`.</span></span>  
  
 <span data-ttu-id="14924-116">NAKLÁDÁNÍ se používá ve scénářích dědičnosti, kde lze dotaz podobný tomuto:</span><span class="sxs-lookup"><span data-stu-id="14924-116">TREAT is used in inheritance scenarios where you can do a query like the following:</span></span>  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)   
```  
  
 <span data-ttu-id="14924-117">Tento dotaz upcasts `Person` entity, které `Employee` typu.</span><span class="sxs-lookup"><span data-stu-id="14924-117">This query upcasts `Person` entities to the `Employee` type.</span></span> <span data-ttu-id="14924-118">Pokud hodnota p není ve skutečnosti je typu `Employee`, výraz vrací hodnotu `null`.</span><span class="sxs-lookup"><span data-stu-id="14924-118">If the value of p is not actually of type `Employee`, the expression yields the value `null`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14924-119">Zadaný výraz `Employee` musí být podtypem typu zadaného datového typu `Person`, nebo datový typ musí být podtypem typu výrazu.</span><span class="sxs-lookup"><span data-stu-id="14924-119">The specified expression `Employee` must be a subtype of the specified data type `Person`, or the data type must be a subtype of the expression.</span></span> <span data-ttu-id="14924-120">V opačném případě výraz způsobí chybu kompilace.</span><span class="sxs-lookup"><span data-stu-id="14924-120">Otherwise, the expression will result in a compile-time error.</span></span>  
  
 <span data-ttu-id="14924-121">Následující tabulka uvádí chování považovat za některé typické vzory a některé méně běžné vzory.</span><span class="sxs-lookup"><span data-stu-id="14924-121">The following table shows the behavior of treat over some typical patterns and some less common patterns.</span></span> <span data-ttu-id="14924-122">Všechny výjimky jsou vyvolány ze strany klienta předtím, než je volán za zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="14924-122">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="14924-123">Vzor</span><span class="sxs-lookup"><span data-stu-id="14924-123">Pattern</span></span>|<span data-ttu-id="14924-124">Chování</span><span class="sxs-lookup"><span data-stu-id="14924-124">Behavior</span></span>|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|<span data-ttu-id="14924-125">Vrátí `DbNull`.</span><span class="sxs-lookup"><span data-stu-id="14924-125">Returns `DbNull`.</span></span>|  
|`TREAT (null AS ComplexType)`|<span data-ttu-id="14924-126">Vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="14924-126">Throws an exception.</span></span>|  
|`TREAT (null AS RowType)`|<span data-ttu-id="14924-127">Vyvolá výjimku /</span><span class="sxs-lookup"><span data-stu-id="14924-127">Throws an exception/</span></span>|  
|`TREAT (EntityType AS EntityType)`|<span data-ttu-id="14924-128">Vrátí `EntityType` nebo `null`.</span><span class="sxs-lookup"><span data-stu-id="14924-128">Returns `EntityType` or `null`.</span></span>|  
|`TREAT (ComplexType AS ComplexType)`|<span data-ttu-id="14924-129">Vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="14924-129">Throws an exception.</span></span>|  
|`TREAT (RowType AS RowType)`|<span data-ttu-id="14924-130">Vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="14924-130">Throws an exception.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="14924-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="14924-131">Example</span></span>  
 <span data-ttu-id="14924-132">Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazu používá operátor POVAŽOVAT převést objekt typu kurzu ke kolekci objektů typu OnsiteCourse.</span><span class="sxs-lookup"><span data-stu-id="14924-132">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="14924-133">Dotaz je založen na [školní modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="14924-133">The query is based on the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a><span data-ttu-id="14924-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14924-134">See also</span></span>

- [<span data-ttu-id="14924-135">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="14924-135">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="14924-136">Strukturované typy s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="14924-136">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
