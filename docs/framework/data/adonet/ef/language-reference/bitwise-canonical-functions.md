---
title: "Bitový kanonické funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 993868ca-16e3-47b6-9915-c29cd63b0a21
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a20f9675af5a67291d95a9297b1ffa1c81a80522
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="bitwise-canonical-functions"></a><span data-ttu-id="3ea6a-102">Bitový kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="3ea6a-102">Bitwise Canonical Functions</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="3ea6a-103">zahrnuje bitové kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="3ea6a-103"> includes bitwise canonical functions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ea6a-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3ea6a-104">Remarks</span></span>  
 <span data-ttu-id="3ea6a-105">V následující tabulce jsou uvedeny bitové hodnotě [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="3ea6a-105">The following table shows the bitwise [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span> <span data-ttu-id="3ea6a-106">Vrátí tyto funkce `Null` Pokud `Null` vstup je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="3ea6a-106">These functions will return `Null` if `Null` input is provided.</span></span> <span data-ttu-id="3ea6a-107">Návratový typ funkce je stejný jako typy argumentů.</span><span class="sxs-lookup"><span data-stu-id="3ea6a-107">The return type of the functions is the same as the argument type(s).</span></span> <span data-ttu-id="3ea6a-108">Argumenty musí být stejného typu, pokud funkci trvá víc než jeden argument.</span><span class="sxs-lookup"><span data-stu-id="3ea6a-108">Arguments must be of the same type, if the function takes more than one argument.</span></span> <span data-ttu-id="3ea6a-109">K provedení bitové operace do různých typů, musíte explicitně převést do stejného typu.</span><span class="sxs-lookup"><span data-stu-id="3ea6a-109">To perform bitwise operations across different types, you need to cast to the same type explicitly.</span></span>  
  
|<span data-ttu-id="3ea6a-110">Funkce</span><span class="sxs-lookup"><span data-stu-id="3ea6a-110">Function</span></span>|<span data-ttu-id="3ea6a-111">Popis</span><span class="sxs-lookup"><span data-stu-id="3ea6a-111">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="3ea6a-112">`BitWiseAnd (` `value1` `,`  `value2` `)`</span><span class="sxs-lookup"><span data-stu-id="3ea6a-112">`BitWiseAnd (` `value1` `,`  `value2` `)`</span></span>|<span data-ttu-id="3ea6a-113">Vrátí bitové spojení z `value1` a `value2` jako typ `value1` a `value2`.</span><span class="sxs-lookup"><span data-stu-id="3ea6a-113">Returns the bitwise conjunction of `value1` and `value2` as the type of `value1` and `value2`.</span></span><br /><br /> <span data-ttu-id="3ea6a-114">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="3ea6a-114">**Arguments**</span></span><br /><br /> <span data-ttu-id="3ea6a-115">A `Byte`, `Int16`, `Int32`, a `Int64`.</span><span class="sxs-lookup"><span data-stu-id="3ea6a-115">A `Byte`, `Int16`, `Int32`, and `Int64`.</span></span><br /><br /> <span data-ttu-id="3ea6a-116">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="3ea6a-116">**Example**</span></span><br /><br /> `-- The following example returns 1.`<br /><br /> `BitWiseAnd(1,3)`|  
|<span data-ttu-id="3ea6a-117">`BitWiseNot (` `value` `)`</span><span class="sxs-lookup"><span data-stu-id="3ea6a-117">`BitWiseNot (` `value` `)`</span></span>|<span data-ttu-id="3ea6a-118">Vrátí bitovou negaci z `value`.</span><span class="sxs-lookup"><span data-stu-id="3ea6a-118">Returns the bitwise negation of `value`.</span></span><br /><br /> <span data-ttu-id="3ea6a-119">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="3ea6a-119">**Arguments**</span></span><br /><br /> <span data-ttu-id="3ea6a-120">A `Byte`, `Int16`, `Int32`, a `Int64`.</span><span class="sxs-lookup"><span data-stu-id="3ea6a-120">A `Byte`, `Int16`, `Int32`, and `Int64`.</span></span><br /><br /> <span data-ttu-id="3ea6a-121">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="3ea6a-121">**Example**</span></span><br /><br /> `-- The following example returns -4.`<br /><br /> `BitWiseNot(3)`|  
|<span data-ttu-id="3ea6a-122">`BitWiseOr (` `value1` `,`  `value2` `)`</span><span class="sxs-lookup"><span data-stu-id="3ea6a-122">`BitWiseOr (` `value1` `,`  `value2` `)`</span></span>|<span data-ttu-id="3ea6a-123">Vrátí bitovou disjunkci z `value1` a `value2` jako typ `value1` a `value2`.</span><span class="sxs-lookup"><span data-stu-id="3ea6a-123">Returns the bitwise disjunction of `value1` and `value2` as the type of `value1` and `value2`.</span></span><br /><br /> <span data-ttu-id="3ea6a-124">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="3ea6a-124">**Arguments**</span></span><br /><br /> <span data-ttu-id="3ea6a-125">A `Byte`, `Int16`, `Int32` a `Int64`.</span><span class="sxs-lookup"><span data-stu-id="3ea6a-125">A `Byte`, `Int16`, `Int32` and `Int64`.</span></span><br /><br /> <span data-ttu-id="3ea6a-126">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="3ea6a-126">**Example**</span></span><br /><br /> `-- The following example returns 3.`<br /><br /> `BitWiseOr(1,3)`|  
|<span data-ttu-id="3ea6a-127">`BitWiseXor (` `value1` `,`  `value2` `)`</span><span class="sxs-lookup"><span data-stu-id="3ea6a-127">`BitWiseXor (` `value1` `,`  `value2` `)`</span></span>|<span data-ttu-id="3ea6a-128">Vrátí bitový exkluzivní disjunkce z `value1` a `value2` jako typ `value1` a `value2`.</span><span class="sxs-lookup"><span data-stu-id="3ea6a-128">Returns the bitwise exclusive disjunction of `value1` and `value2` as the type of `value1` and `value2`.</span></span><br /><br /> <span data-ttu-id="3ea6a-129">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="3ea6a-129">**Arguments**</span></span><br /><br /> <span data-ttu-id="3ea6a-130">A `Byte`, `Int16`, `Int32` a `Int64`.</span><span class="sxs-lookup"><span data-stu-id="3ea6a-130">A `Byte`, `Int16`, `Int32` and `Int64`.</span></span><br /><br /> <span data-ttu-id="3ea6a-131">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="3ea6a-131">**Example**</span></span><br /><br /> `-- The following example returns 2.`<br /><br /> `BitWiseXor (1,3)`|  
  
## <a name="see-also"></a><span data-ttu-id="3ea6a-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="3ea6a-132">See Also</span></span>  
 [<span data-ttu-id="3ea6a-133">Kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="3ea6a-133">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
