---
title: ISOF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: 097d6e7d452ee62a2c8934d2c5fcfdddbeaffc73
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772369"
---
# <a name="isof-entity-sql"></a><span data-ttu-id="931d3-102">ISOF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="931d3-102">ISOF (Entity SQL)</span></span>
<span data-ttu-id="931d3-103">Určuje, zda je typ výrazu zadaný typ nebo některý z jeho podtypy.</span><span class="sxs-lookup"><span data-stu-id="931d3-103">Determines whether the type of an expression is of the specified type or one of its subtypes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="931d3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="931d3-104">Syntax</span></span>  
  
```  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="931d3-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="931d3-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="931d3-106">Libovolný výraz platného dotazu k určení typu.</span><span class="sxs-lookup"><span data-stu-id="931d3-106">Any valid query expression to determine the type of.</span></span>  
  
 <span data-ttu-id="931d3-107">NOT</span><span class="sxs-lookup"><span data-stu-id="931d3-107">NOT</span></span>  
 <span data-ttu-id="931d3-108">Neguje modelu EDM. Výsledek logickou hodnotu je z.</span><span class="sxs-lookup"><span data-stu-id="931d3-108">Negates the EDM.Boolean result of IS OF.</span></span>  
  
 <span data-ttu-id="931d3-109">POUZE</span><span class="sxs-lookup"><span data-stu-id="931d3-109">ONLY</span></span>  
 <span data-ttu-id="931d3-110">Určuje, že se vrátí `true` pouze tehdy, pokud `expression` je typu `type` a nikoli jakákoliv některou jeho podtypy.</span><span class="sxs-lookup"><span data-stu-id="931d3-110">Specifies that IS OF returns `true` only if `expression` is of type `type` and not any of one its subtypes.</span></span>  
  
 `type`  
 <span data-ttu-id="931d3-111">Typ, který chcete testovat `expression` proti.</span><span class="sxs-lookup"><span data-stu-id="931d3-111">The type to test `expression` against.</span></span> <span data-ttu-id="931d3-112">Typ musí být kvalifikovaný v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="931d3-112">The type must be namespace-qualified.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="931d3-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="931d3-113">Return Value</span></span>  
 <span data-ttu-id="931d3-114">`true` Pokud `expression` je typu T a T je základní typ nebo odvozeným typem `type`; hodnota null, pokud `expression` je za běhu hodnotu null; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="931d3-114">`true` if `expression` is of type T and T is either a base type, or a derived type of `type`; null if `expression` is null at runtime; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="931d3-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="931d3-115">Remarks</span></span>  
 <span data-ttu-id="931d3-116">Výrazy `expression IS NOT OF (type)` a `expression IS NOT OF (ONLY type)` syntakticky odpovídajících `NOT (expression IS OF (type))` a `NOT (expression IS OF (ONLY type))`v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="931d3-116">The expressions `expression IS NOT OF (type)` and `expression IS NOT OF (ONLY type)` are syntactically equivalent to `NOT (expression IS OF (type))` and `NOT (expression IS OF (ONLY type))`, respectively.</span></span>  
  
 <span data-ttu-id="931d3-117">V následující tabulce jsou uvedeny chování `IS OF` operátor přes některé typické - rohové a vzory.</span><span class="sxs-lookup"><span data-stu-id="931d3-117">The following table shows the behavior of `IS OF` operator over some typical- and corner patterns.</span></span> <span data-ttu-id="931d3-118">Všechny výjimky jsou vyvolány ze strany klienta předtím, než je volán za zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="931d3-118">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="931d3-119">Vzor</span><span class="sxs-lookup"><span data-stu-id="931d3-119">Pattern</span></span>|<span data-ttu-id="931d3-120">Chování</span><span class="sxs-lookup"><span data-stu-id="931d3-120">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="931d3-121">NULL je typu (EntityType)</span><span class="sxs-lookup"><span data-stu-id="931d3-121">null IS OF (EntityType)</span></span>|<span data-ttu-id="931d3-122">Vyvolá výjimku</span><span class="sxs-lookup"><span data-stu-id="931d3-122">Throws</span></span>|  
|<span data-ttu-id="931d3-123">NULL je typu (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="931d3-123">null IS OF (ComplexType)</span></span>|<span data-ttu-id="931d3-124">Vyvolá výjimku</span><span class="sxs-lookup"><span data-stu-id="931d3-124">Throws</span></span>|  
|<span data-ttu-id="931d3-125">NULL je z (RowType)</span><span class="sxs-lookup"><span data-stu-id="931d3-125">null IS OF (RowType)</span></span>|<span data-ttu-id="931d3-126">Vyvolá výjimku</span><span class="sxs-lookup"><span data-stu-id="931d3-126">Throws</span></span>|  
|<span data-ttu-id="931d3-127">POVAŽOVAT (třída EntityType hodnotu null jako) je typu (EntityType)</span><span class="sxs-lookup"><span data-stu-id="931d3-127">TREAT (null AS EntityType) IS OF (EntityType)</span></span>|<span data-ttu-id="931d3-128">Vrátí DBNull</span><span class="sxs-lookup"><span data-stu-id="931d3-128">Returns DBNull</span></span>|  
|<span data-ttu-id="931d3-129">POVAŽOVAT (null jako ComplexType) je typu (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="931d3-129">TREAT (null AS ComplexType) IS OF (ComplexType)</span></span>|<span data-ttu-id="931d3-130">Vyvolá výjimku</span><span class="sxs-lookup"><span data-stu-id="931d3-130">Throws</span></span>|  
|<span data-ttu-id="931d3-131">POVAŽOVAT (null jako RowType) je z (RowType)</span><span class="sxs-lookup"><span data-stu-id="931d3-131">TREAT (null AS RowType) IS OF (RowType)</span></span>|<span data-ttu-id="931d3-132">Vyvolá výjimku</span><span class="sxs-lookup"><span data-stu-id="931d3-132">Throws</span></span>|  
|<span data-ttu-id="931d3-133">JE typ entity typu (EntityType)</span><span class="sxs-lookup"><span data-stu-id="931d3-133">EntityType IS OF (EntityType)</span></span>|<span data-ttu-id="931d3-134">Vrátí hodnotu true nebo false</span><span class="sxs-lookup"><span data-stu-id="931d3-134">Returns true/false</span></span>|  
|<span data-ttu-id="931d3-135">Typ ComplexType je typu (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="931d3-135">ComplexType IS OF (ComplexType)</span></span>|<span data-ttu-id="931d3-136">Vyvolá výjimku</span><span class="sxs-lookup"><span data-stu-id="931d3-136">Throws</span></span>|  
|<span data-ttu-id="931d3-137">JE RowType z (RowType)</span><span class="sxs-lookup"><span data-stu-id="931d3-137">RowType IS OF (RowType)</span></span>|<span data-ttu-id="931d3-138">Vyvolá výjimku</span><span class="sxs-lookup"><span data-stu-id="931d3-138">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="931d3-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="931d3-139">Example</span></span>  
 <span data-ttu-id="931d3-140">Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazu používá operátor je určit typ výrazu dotazu a pak používá operátor POVAŽOVAT převést objekt typu kurzu ke kolekci objektů typu OnsiteCourse.</span><span class="sxs-lookup"><span data-stu-id="931d3-140">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS OF operator to determine the type of a query expression, and then uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="931d3-141">Dotaz je založen na [školní modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="931d3-141">The query is based on the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a><span data-ttu-id="931d3-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="931d3-142">See also</span></span>

- [<span data-ttu-id="931d3-143">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="931d3-143">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
