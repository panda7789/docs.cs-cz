---
title: ZPRACOVÁVÁ se (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
ms.openlocfilehash: 38099fa83ed78b40d46faeb5e617157f7aa7c1a1
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319266"
---
# <a name="treat-entity-sql"></a><span data-ttu-id="f962c-102">ZPRACOVÁVÁ se (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f962c-102">TREAT (Entity SQL)</span></span>
<span data-ttu-id="f962c-103">Zpracovává objekt určitého základního typu jako objekt zadaného odvozeného typu.</span><span class="sxs-lookup"><span data-stu-id="f962c-103">Treats an object of a particular base type as an object of the specified derived type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f962c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f962c-104">Syntax</span></span>  
  
```sql  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a><span data-ttu-id="f962c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="f962c-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="f962c-106">Libovolný platný výraz dotazu, který vrací entitu.</span><span class="sxs-lookup"><span data-stu-id="f962c-106">Any valid query expression that returns an entity.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f962c-107">Typ zadaného výrazu musí být podtyp zadaného datového typu nebo musí být datový typ podtypem typu výrazu.</span><span class="sxs-lookup"><span data-stu-id="f962c-107">The type of the specified expression must be a subtype of the specified data type, or the data type must be a subtype of the type of expression.</span></span>  
  
 `type`  
 <span data-ttu-id="f962c-108">Typ entity.</span><span class="sxs-lookup"><span data-stu-id="f962c-108">An entity type.</span></span> <span data-ttu-id="f962c-109">Typ musí být kvalifikován oborem názvů.</span><span class="sxs-lookup"><span data-stu-id="f962c-109">The type must be qualified by a namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f962c-110">Zadaný výraz musí být podtypem zadaného datového typu nebo musí být datový typ podtypem výrazu.</span><span class="sxs-lookup"><span data-stu-id="f962c-110">The specified expression must be a subtype of the specified data type, or the data type must be a subtype of the expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f962c-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f962c-111">Return Value</span></span>  
 <span data-ttu-id="f962c-112">Hodnota zadaného datového typu.</span><span class="sxs-lookup"><span data-stu-id="f962c-112">A value of the specified data type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f962c-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f962c-113">Remarks</span></span>  
 <span data-ttu-id="f962c-114">K provádění přetypování mezi souvisejícími třídami se používá zpracování.</span><span class="sxs-lookup"><span data-stu-id="f962c-114">TREAT is used to perform upcasting between related classes.</span></span> <span data-ttu-id="f962c-115">Například pokud `Employee` je odvozeno z `Person` a p je typu `Person`, `TREAT(p AS NamespaceName.Employee)` přetypování obecné instance `Person` na `Employee`; To znamená, že vám umožní považovat p za `Employee`.</span><span class="sxs-lookup"><span data-stu-id="f962c-115">For example, if `Employee` derives from `Person` and p is of type `Person`, `TREAT(p AS NamespaceName.Employee)` upcasts a generic `Person` instance to `Employee`; that is, it allows you to treat p as `Employee`.</span></span>  
  
 <span data-ttu-id="f962c-116">Použití se používá ve scénářích dědičnosti, kde můžete provádět dotaz podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="f962c-116">TREAT is used in inheritance scenarios where you can do a query like the following:</span></span>  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)   
```  
  
 <span data-ttu-id="f962c-117">Tento dotaz přetypování entit `Person` na typ `Employee`.</span><span class="sxs-lookup"><span data-stu-id="f962c-117">This query upcasts `Person` entities to the `Employee` type.</span></span> <span data-ttu-id="f962c-118">Pokud hodnota p není ve skutečnosti typu `Employee`, výraz vrací hodnotu `null`.</span><span class="sxs-lookup"><span data-stu-id="f962c-118">If the value of p is not actually of type `Employee`, the expression yields the value `null`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f962c-119">Zadaný výraz `Employee` musí být podtypem zadaného datového typu `Person` nebo datový typ musí být podtypem výrazu.</span><span class="sxs-lookup"><span data-stu-id="f962c-119">The specified expression `Employee` must be a subtype of the specified data type `Person`, or the data type must be a subtype of the expression.</span></span> <span data-ttu-id="f962c-120">V opačném případě výraz způsobí chybu při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="f962c-120">Otherwise, the expression will result in a compile-time error.</span></span>  
  
 <span data-ttu-id="f962c-121">V následující tabulce je uvedeno chování při zpracování několika typických vzorů a některých méně běžných vzorů.</span><span class="sxs-lookup"><span data-stu-id="f962c-121">The following table shows the behavior of treat over some typical patterns and some less common patterns.</span></span> <span data-ttu-id="f962c-122">Všechny výjimky jsou vyvolány na straně klienta před vyvoláním zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="f962c-122">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="f962c-123">Vzor</span><span class="sxs-lookup"><span data-stu-id="f962c-123">Pattern</span></span>|<span data-ttu-id="f962c-124">Předvídatelně</span><span class="sxs-lookup"><span data-stu-id="f962c-124">Behavior</span></span>|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|<span data-ttu-id="f962c-125">Vrátí `DbNull`.</span><span class="sxs-lookup"><span data-stu-id="f962c-125">Returns `DbNull`.</span></span>|  
|`TREAT (null AS ComplexType)`|<span data-ttu-id="f962c-126">Vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="f962c-126">Throws an exception.</span></span>|  
|`TREAT (null AS RowType)`|<span data-ttu-id="f962c-127">Vyvolá výjimku/</span><span class="sxs-lookup"><span data-stu-id="f962c-127">Throws an exception/</span></span>|  
|`TREAT (EntityType AS EntityType)`|<span data-ttu-id="f962c-128">Vrátí `EntityType` nebo `null`.</span><span class="sxs-lookup"><span data-stu-id="f962c-128">Returns `EntityType` or `null`.</span></span>|  
|`TREAT (ComplexType AS ComplexType)`|<span data-ttu-id="f962c-129">Vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="f962c-129">Throws an exception.</span></span>|  
|`TREAT (RowType AS RowType)`|<span data-ttu-id="f962c-130">Vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="f962c-130">Throws an exception.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f962c-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="f962c-131">Example</span></span>  
 <span data-ttu-id="f962c-132">Následující dotaz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] používá operátor považovat pro převod objektu typu kurzu na kolekci objektů typu OnsiteCourse.</span><span class="sxs-lookup"><span data-stu-id="f962c-132">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="f962c-133">Dotaz je založen na [školním modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f962c-133">The query is based on the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-sql[DP EntityServices Concepts#TREAT_ISOF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]  
  
## <a name="see-also"></a><span data-ttu-id="f962c-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f962c-134">See also</span></span>

- [<span data-ttu-id="f962c-135">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f962c-135">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="f962c-136">Strukturované typy s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="f962c-136">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
