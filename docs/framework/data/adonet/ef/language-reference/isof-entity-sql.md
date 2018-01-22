---
title: ISOF (entita SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 78bfcef336ad265b98069ed540f9156cf9cb65bd
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="isof-entity-sql"></a><span data-ttu-id="b3d4c-102">ISOF (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="b3d4c-102">ISOF (Entity SQL)</span></span>
<span data-ttu-id="b3d4c-103">Určuje, zda typ výrazu je zadaného typu nebo jeden z jeho podtypech.</span><span class="sxs-lookup"><span data-stu-id="b3d4c-103">Determines whether the type of an expression is of the specified type or one of its subtypes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3d4c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3d4c-104">Syntax</span></span>  
  
```  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="b3d4c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b3d4c-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="b3d4c-106">Jakýkoli platný dotaz výraz k určení typu.</span><span class="sxs-lookup"><span data-stu-id="b3d4c-106">Any valid query expression to determine the type of.</span></span>  
  
 <span data-ttu-id="b3d4c-107">NENÍ</span><span class="sxs-lookup"><span data-stu-id="b3d4c-107">NOT</span></span>  
 <span data-ttu-id="b3d4c-108">Neguje EDM. Logická hodnota výsledek je z.</span><span class="sxs-lookup"><span data-stu-id="b3d4c-108">Negates the EDM.Boolean result of IS OF.</span></span>  
  
 <span data-ttu-id="b3d4c-109">POUZE</span><span class="sxs-lookup"><span data-stu-id="b3d4c-109">ONLY</span></span>  
 <span data-ttu-id="b3d4c-110">Určuje, zda je z vrátí `true` pouze v případě `expression` je typu `type` a nikoli jakákoliv jednoho jeho podtypech.</span><span class="sxs-lookup"><span data-stu-id="b3d4c-110">Specifies that IS OF returns `true` only if `expression` is of type `type` and not any of one its subtypes.</span></span>  
  
 `type`  
 <span data-ttu-id="b3d4c-111">Typ k otestování `expression` proti.</span><span class="sxs-lookup"><span data-stu-id="b3d4c-111">The type to test `expression` against.</span></span> <span data-ttu-id="b3d4c-112">Typ musí být kvalifikovaný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="b3d4c-112">The type must be namespace-qualified.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b3d4c-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b3d4c-113">Return Value</span></span>  
 <span data-ttu-id="b3d4c-114">`true`Pokud `expression` je typu T a T je základní typ nebo odvozené typ `type`; hodnota null, pokud `expression` je null za běhu, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="b3d4c-114">`true` if `expression` is of type T and T is either a base type, or a derived type of `type`; null if `expression` is null at runtime; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3d4c-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b3d4c-115">Remarks</span></span>  
 <span data-ttu-id="b3d4c-116">Výrazy `expression IS NOT OF (type)` a `expression IS NOT OF (ONLY type)` odpovídají syntakticky `NOT (expression IS OF (type))` a `NOT (expression IS OF (ONLY type))`, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="b3d4c-116">The expressions `expression IS NOT OF (type)` and `expression IS NOT OF (ONLY type)` are syntactically equivalent to `NOT (expression IS OF (type))` and `NOT (expression IS OF (ONLY type))`, respectively.</span></span>  
  
 <span data-ttu-id="b3d4c-117">Následující tabulka uvádí chování `IS OF` operátor přes některé typické a rohu vzory.</span><span class="sxs-lookup"><span data-stu-id="b3d4c-117">The following table shows the behavior of `IS OF` operator over some typical- and corner patterns.</span></span> <span data-ttu-id="b3d4c-118">Všechny výjimky jsou vyvolány ze strany klienta předtím, než získá volá zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="b3d4c-118">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="b3d4c-119">Vzor</span><span class="sxs-lookup"><span data-stu-id="b3d4c-119">Pattern</span></span>|<span data-ttu-id="b3d4c-120">Chování</span><span class="sxs-lookup"><span data-stu-id="b3d4c-120">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="b3d4c-121">Null není pro (EntityType)</span><span class="sxs-lookup"><span data-stu-id="b3d4c-121">null IS OF (EntityType)</span></span>|<span data-ttu-id="b3d4c-122">Vyvolá</span><span class="sxs-lookup"><span data-stu-id="b3d4c-122">Throws</span></span>|  
|<span data-ttu-id="b3d4c-123">NULL je z (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="b3d4c-123">null IS OF (ComplexType)</span></span>|<span data-ttu-id="b3d4c-124">Vyvolá</span><span class="sxs-lookup"><span data-stu-id="b3d4c-124">Throws</span></span>|  
|<span data-ttu-id="b3d4c-125">NULL je z (RowType)</span><span class="sxs-lookup"><span data-stu-id="b3d4c-125">null IS OF (RowType)</span></span>|<span data-ttu-id="b3d4c-126">Vyvolá</span><span class="sxs-lookup"><span data-stu-id="b3d4c-126">Throws</span></span>|  
|<span data-ttu-id="b3d4c-127">ZPRACOVÁVAT (null AS EntityType) je pro (EntityType)</span><span class="sxs-lookup"><span data-stu-id="b3d4c-127">TREAT (null AS EntityType) IS OF (EntityType)</span></span>|<span data-ttu-id="b3d4c-128">Returns DBNull</span><span class="sxs-lookup"><span data-stu-id="b3d4c-128">Returns DBNull</span></span>|  
|<span data-ttu-id="b3d4c-129">ZPRACOVÁVAT (null AS ComplexType) je z (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="b3d4c-129">TREAT (null AS ComplexType) IS OF (ComplexType)</span></span>|<span data-ttu-id="b3d4c-130">Vyvolá</span><span class="sxs-lookup"><span data-stu-id="b3d4c-130">Throws</span></span>|  
|<span data-ttu-id="b3d4c-131">ZPRACOVÁVAT (null AS RowType) je z (RowType)</span><span class="sxs-lookup"><span data-stu-id="b3d4c-131">TREAT (null AS RowType) IS OF (RowType)</span></span>|<span data-ttu-id="b3d4c-132">Vyvolá</span><span class="sxs-lookup"><span data-stu-id="b3d4c-132">Throws</span></span>|  
|<span data-ttu-id="b3d4c-133">JE typ entity (typu ENTITYTYPE)</span><span class="sxs-lookup"><span data-stu-id="b3d4c-133">EntityType IS OF (EntityType)</span></span>|<span data-ttu-id="b3d4c-134">Vrátí hodnotu true nebo false</span><span class="sxs-lookup"><span data-stu-id="b3d4c-134">Returns true/false</span></span>|  
|<span data-ttu-id="b3d4c-135">JE ComplexType (COMPLEXTYPE)</span><span class="sxs-lookup"><span data-stu-id="b3d4c-135">ComplexType IS OF (ComplexType)</span></span>|<span data-ttu-id="b3d4c-136">Vyvolá</span><span class="sxs-lookup"><span data-stu-id="b3d4c-136">Throws</span></span>|  
|<span data-ttu-id="b3d4c-137">JE RowType z (RowType)</span><span class="sxs-lookup"><span data-stu-id="b3d4c-137">RowType IS OF (RowType)</span></span>|<span data-ttu-id="b3d4c-138">Vyvolá</span><span class="sxs-lookup"><span data-stu-id="b3d4c-138">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b3d4c-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="b3d4c-139">Example</span></span>  
 <span data-ttu-id="b3d4c-140">Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz používá operátor je z určit typ výrazu dotazu a pak operátor ZPRACOVÁVAT převést objekt typu kurzu na kolekce objektů typu OnsiteCourse.</span><span class="sxs-lookup"><span data-stu-id="b3d4c-140">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS OF operator to determine the type of a query expression, and then uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="b3d4c-141">Dotaz je na základě [školní modelu](http://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac).</span><span class="sxs-lookup"><span data-stu-id="b3d4c-141">The query is based on the [School Model](http://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac).</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a><span data-ttu-id="b3d4c-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="b3d4c-142">See Also</span></span>  
 [<span data-ttu-id="b3d4c-143">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b3d4c-143">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
