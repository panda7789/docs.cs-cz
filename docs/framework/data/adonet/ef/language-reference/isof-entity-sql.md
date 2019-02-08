---
title: ISOF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: 87d69f58fc0c45eacb4ee63997129347f7f2a857
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827406"
---
# <a name="isof-entity-sql"></a><span data-ttu-id="61234-102">ISOF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="61234-102">ISOF (Entity SQL)</span></span>
<span data-ttu-id="61234-103">Určuje, zda je typ výrazu zadaný typ nebo některý z jeho podtypy.</span><span class="sxs-lookup"><span data-stu-id="61234-103">Determines whether the type of an expression is of the specified type or one of its subtypes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61234-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61234-104">Syntax</span></span>  
  
```  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="61234-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="61234-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="61234-106">Libovolný výraz platného dotazu k určení typu.</span><span class="sxs-lookup"><span data-stu-id="61234-106">Any valid query expression to determine the type of.</span></span>  
  
 <span data-ttu-id="61234-107">NOT</span><span class="sxs-lookup"><span data-stu-id="61234-107">NOT</span></span>  
 <span data-ttu-id="61234-108">Neguje modelu EDM. Výsledek logickou hodnotu je z.</span><span class="sxs-lookup"><span data-stu-id="61234-108">Negates the EDM.Boolean result of IS OF.</span></span>  
  
 <span data-ttu-id="61234-109">POUZE</span><span class="sxs-lookup"><span data-stu-id="61234-109">ONLY</span></span>  
 <span data-ttu-id="61234-110">Určuje, že se vrátí `true` pouze tehdy, pokud `expression` je typu `type` a nikoli jakákoliv některou jeho podtypy.</span><span class="sxs-lookup"><span data-stu-id="61234-110">Specifies that IS OF returns `true` only if `expression` is of type `type` and not any of one its subtypes.</span></span>  
  
 `type`  
 <span data-ttu-id="61234-111">Typ, který chcete testovat `expression` proti.</span><span class="sxs-lookup"><span data-stu-id="61234-111">The type to test `expression` against.</span></span> <span data-ttu-id="61234-112">Typ musí být kvalifikovaný v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="61234-112">The type must be namespace-qualified.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="61234-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="61234-113">Return Value</span></span>  
 <span data-ttu-id="61234-114">`true` Pokud `expression` je typu T a T je základní typ nebo odvozeným typem `type`; hodnota null, pokud `expression` je za běhu hodnotu null; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="61234-114">`true` if `expression` is of type T and T is either a base type, or a derived type of `type`; null if `expression` is null at runtime; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61234-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="61234-115">Remarks</span></span>  
 <span data-ttu-id="61234-116">Výrazy `expression IS NOT OF (type)` a `expression IS NOT OF (ONLY type)` syntakticky odpovídajících `NOT (expression IS OF (type))` a `NOT (expression IS OF (ONLY type))`v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="61234-116">The expressions `expression IS NOT OF (type)` and `expression IS NOT OF (ONLY type)` are syntactically equivalent to `NOT (expression IS OF (type))` and `NOT (expression IS OF (ONLY type))`, respectively.</span></span>  
  
 <span data-ttu-id="61234-117">V následující tabulce jsou uvedeny chování `IS OF` operátor přes některé typické - rohové a vzory.</span><span class="sxs-lookup"><span data-stu-id="61234-117">The following table shows the behavior of `IS OF` operator over some typical- and corner patterns.</span></span> <span data-ttu-id="61234-118">Všechny výjimky jsou vyvolány ze strany klienta předtím, než je volán za zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="61234-118">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="61234-119">Vzor</span><span class="sxs-lookup"><span data-stu-id="61234-119">Pattern</span></span>|<span data-ttu-id="61234-120">Chování</span><span class="sxs-lookup"><span data-stu-id="61234-120">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="61234-121">NULL je typu (EntityType)</span><span class="sxs-lookup"><span data-stu-id="61234-121">null IS OF (EntityType)</span></span>|<span data-ttu-id="61234-122">Vyvolá výjimku</span><span class="sxs-lookup"><span data-stu-id="61234-122">Throws</span></span>|  
|<span data-ttu-id="61234-123">NULL je typu (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="61234-123">null IS OF (ComplexType)</span></span>|<span data-ttu-id="61234-124">Vyvolá výjimku</span><span class="sxs-lookup"><span data-stu-id="61234-124">Throws</span></span>|  
|<span data-ttu-id="61234-125">NULL je z (RowType)</span><span class="sxs-lookup"><span data-stu-id="61234-125">null IS OF (RowType)</span></span>|<span data-ttu-id="61234-126">Vyvolá výjimku</span><span class="sxs-lookup"><span data-stu-id="61234-126">Throws</span></span>|  
|<span data-ttu-id="61234-127">POVAŽOVAT (třída EntityType hodnotu null jako) je typu (EntityType)</span><span class="sxs-lookup"><span data-stu-id="61234-127">TREAT (null AS EntityType) IS OF (EntityType)</span></span>|<span data-ttu-id="61234-128">Vrátí DBNull</span><span class="sxs-lookup"><span data-stu-id="61234-128">Returns DBNull</span></span>|  
|<span data-ttu-id="61234-129">POVAŽOVAT (null jako ComplexType) je typu (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="61234-129">TREAT (null AS ComplexType) IS OF (ComplexType)</span></span>|<span data-ttu-id="61234-130">Vyvolá výjimku</span><span class="sxs-lookup"><span data-stu-id="61234-130">Throws</span></span>|  
|<span data-ttu-id="61234-131">POVAŽOVAT (null jako RowType) je z (RowType)</span><span class="sxs-lookup"><span data-stu-id="61234-131">TREAT (null AS RowType) IS OF (RowType)</span></span>|<span data-ttu-id="61234-132">Vyvolá výjimku</span><span class="sxs-lookup"><span data-stu-id="61234-132">Throws</span></span>|  
|<span data-ttu-id="61234-133">JE typ entity typu (EntityType)</span><span class="sxs-lookup"><span data-stu-id="61234-133">EntityType IS OF (EntityType)</span></span>|<span data-ttu-id="61234-134">Vrátí hodnotu true nebo false</span><span class="sxs-lookup"><span data-stu-id="61234-134">Returns true/false</span></span>|  
|<span data-ttu-id="61234-135">Typ ComplexType je typu (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="61234-135">ComplexType IS OF (ComplexType)</span></span>|<span data-ttu-id="61234-136">Vyvolá výjimku</span><span class="sxs-lookup"><span data-stu-id="61234-136">Throws</span></span>|  
|<span data-ttu-id="61234-137">JE RowType z (RowType)</span><span class="sxs-lookup"><span data-stu-id="61234-137">RowType IS OF (RowType)</span></span>|<span data-ttu-id="61234-138">Vyvolá výjimku</span><span class="sxs-lookup"><span data-stu-id="61234-138">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="61234-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="61234-139">Example</span></span>  
 <span data-ttu-id="61234-140">Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazu používá operátor je určit typ výrazu dotazu a pak používá operátor POVAŽOVAT převést objekt typu kurzu ke kolekci objektů typu OnsiteCourse.</span><span class="sxs-lookup"><span data-stu-id="61234-140">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS OF operator to determine the type of a query expression, and then uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="61234-141">Dotaz je založen na [školní modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="61234-141">The query is based on the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a><span data-ttu-id="61234-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="61234-142">See also</span></span>
- [<span data-ttu-id="61234-143">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="61234-143">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
