---
title: TREAT (Entita SQL)
ms.date: 03/30/2017
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
ms.openlocfilehash: 06c4200434f443446e8981dcefe2baf43b1af4b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149892"
---
# <a name="treat-entity-sql"></a><span data-ttu-id="6a7ce-102">TREAT (Entita SQL)</span><span class="sxs-lookup"><span data-stu-id="6a7ce-102">TREAT (Entity SQL)</span></span>
<span data-ttu-id="6a7ce-103">Zachází s objektem určitého základního typu jako s objektem zadaného odvozeného typu.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-103">Treats an object of a particular base type as an object of the specified derived type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a7ce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a7ce-104">Syntax</span></span>  
  
```sql  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a><span data-ttu-id="6a7ce-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="6a7ce-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="6a7ce-106">Libovolný platný výraz dotazu, který vrací entitu.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-106">Any valid query expression that returns an entity.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6a7ce-107">Typ zadaného výrazu musí být podtypem zadaného datového typu nebo datový typ musí být podtypem typu výrazu.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-107">The type of the specified expression must be a subtype of the specified data type, or the data type must be a subtype of the type of expression.</span></span>  
  
 `type`  
 <span data-ttu-id="6a7ce-108">Typ entity.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-108">An entity type.</span></span> <span data-ttu-id="6a7ce-109">Typ musí být kvalifikován oborem názvů.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-109">The type must be qualified by a namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6a7ce-110">Zadaný výraz musí být podtypem zadaného datového typu nebo datový typ musí být podtypem výrazu.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-110">The specified expression must be a subtype of the specified data type, or the data type must be a subtype of the expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6a7ce-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6a7ce-111">Return Value</span></span>  
 <span data-ttu-id="6a7ce-112">Hodnota zadaného datového typu.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-112">A value of the specified data type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a7ce-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6a7ce-113">Remarks</span></span>  
 <span data-ttu-id="6a7ce-114">TREAT se používá k provádění upcasting mezi související třídy.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-114">TREAT is used to perform upcasting between related classes.</span></span> <span data-ttu-id="6a7ce-115">Například pokud `Employee` je `Person` odvozen od a `Person` `TREAT(p AS NamespaceName.Employee)` p je typu `Person` , `Employee`upcasts obecná instance ; to znamená, že vám umožní `Employee`zacházet s p jako .</span><span class="sxs-lookup"><span data-stu-id="6a7ce-115">For example, if `Employee` derives from `Person` and p is of type `Person`, `TREAT(p AS NamespaceName.Employee)` upcasts a generic `Person` instance to `Employee`; that is, it allows you to treat p as `Employee`.</span></span>  
  
 <span data-ttu-id="6a7ce-116">TREAT se používá ve scénářích dědičnosti, kde můžete provést dotaz, jako je následující:</span><span class="sxs-lookup"><span data-stu-id="6a7ce-116">TREAT is used in inheritance scenarios where you can do a query like the following:</span></span>  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)
```  
  
 <span data-ttu-id="6a7ce-117">Tento dotaz upcasts `Person` entity `Employee` typu.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-117">This query upcasts `Person` entities to the `Employee` type.</span></span> <span data-ttu-id="6a7ce-118">Pokud hodnota p není ve `Employee`skutečnosti typu , výraz `null`dává hodnotu .</span><span class="sxs-lookup"><span data-stu-id="6a7ce-118">If the value of p is not actually of type `Employee`, the expression yields the value `null`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6a7ce-119">Zadaný `Employee` výraz musí být podtypem `Person`zadaného datového typu nebo datový typ musí být podtypem výrazu.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-119">The specified expression `Employee` must be a subtype of the specified data type `Person`, or the data type must be a subtype of the expression.</span></span> <span data-ttu-id="6a7ce-120">V opačném případě výraz bude mít za následek chybu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-120">Otherwise, the expression will result in a compile-time error.</span></span>  
  
 <span data-ttu-id="6a7ce-121">V následující tabulce je uvedeno chování treat přes některé typické vzory a některé méně běžné vzory.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-121">The following table shows the behavior of treat over some typical patterns and some less common patterns.</span></span> <span data-ttu-id="6a7ce-122">Všechny výjimky jsou vyvolány ze strany klienta před zprostředkovatel získá vyvolána:</span><span class="sxs-lookup"><span data-stu-id="6a7ce-122">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="6a7ce-123">Vzor</span><span class="sxs-lookup"><span data-stu-id="6a7ce-123">Pattern</span></span>|<span data-ttu-id="6a7ce-124">Chování</span><span class="sxs-lookup"><span data-stu-id="6a7ce-124">Behavior</span></span>|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|<span data-ttu-id="6a7ce-125">Vrací objekt `DbNull`.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-125">Returns `DbNull`.</span></span>|  
|`TREAT (null AS ComplexType)`|<span data-ttu-id="6a7ce-126">Vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-126">Throws an exception.</span></span>|  
|`TREAT (null AS RowType)`|<span data-ttu-id="6a7ce-127">Vyvolá výjimku/</span><span class="sxs-lookup"><span data-stu-id="6a7ce-127">Throws an exception/</span></span>|  
|`TREAT (EntityType AS EntityType)`|<span data-ttu-id="6a7ce-128">Vrátí `EntityType` `null`nebo .</span><span class="sxs-lookup"><span data-stu-id="6a7ce-128">Returns `EntityType` or `null`.</span></span>|  
|`TREAT (ComplexType AS ComplexType)`|<span data-ttu-id="6a7ce-129">Vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-129">Throws an exception.</span></span>|  
|`TREAT (RowType AS RowType)`|<span data-ttu-id="6a7ce-130">Vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-130">Throws an exception.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6a7ce-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="6a7ce-131">Example</span></span>  
 <span data-ttu-id="6a7ce-132">Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz používá treat operátor převést objekt typu Course na kolekci objektů typu OnsiteCourse.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-132">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="6a7ce-133">Dotaz je založen na [školním modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="6a7ce-133">The query is based on the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-sql[DP EntityServices Concepts#TREAT_ISOF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]  
  
## <a name="see-also"></a><span data-ttu-id="6a7ce-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="6a7ce-134">See also</span></span>

- [<span data-ttu-id="6a7ce-135">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="6a7ce-135">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="6a7ce-136">Strukturované typy s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="6a7ce-136">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
