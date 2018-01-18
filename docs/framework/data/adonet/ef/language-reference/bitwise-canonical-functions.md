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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1d703b2467d508324f3eb39b822c239484ac1c6e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="bitwise-canonical-functions"></a><span data-ttu-id="2c571-102">Bitový kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="2c571-102">Bitwise Canonical Functions</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2c571-103">zahrnuje bitové kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="2c571-103"> includes bitwise canonical functions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c571-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2c571-104">Remarks</span></span>  
 <span data-ttu-id="2c571-105">V následující tabulce jsou uvedeny bitové hodnotě [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="2c571-105">The following table shows the bitwise [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span> <span data-ttu-id="2c571-106">Vrátí tyto funkce `Null` Pokud `Null` vstup je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="2c571-106">These functions will return `Null` if `Null` input is provided.</span></span> <span data-ttu-id="2c571-107">Návratový typ funkce je stejný jako typy argumentů.</span><span class="sxs-lookup"><span data-stu-id="2c571-107">The return type of the functions is the same as the argument type(s).</span></span> <span data-ttu-id="2c571-108">Argumenty musí být stejného typu, pokud funkci trvá víc než jeden argument.</span><span class="sxs-lookup"><span data-stu-id="2c571-108">Arguments must be of the same type, if the function takes more than one argument.</span></span> <span data-ttu-id="2c571-109">K provedení bitové operace do různých typů, musíte explicitně převést do stejného typu.</span><span class="sxs-lookup"><span data-stu-id="2c571-109">To perform bitwise operations across different types, you need to cast to the same type explicitly.</span></span>  
  
|<span data-ttu-id="2c571-110">Funkce</span><span class="sxs-lookup"><span data-stu-id="2c571-110">Function</span></span>|<span data-ttu-id="2c571-111">Popis</span><span class="sxs-lookup"><span data-stu-id="2c571-111">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="2c571-112">`BitWiseAnd (` `value1` `,`  `value2` `)`</span><span class="sxs-lookup"><span data-stu-id="2c571-112">`BitWiseAnd (` `value1` `,`  `value2` `)`</span></span>|<span data-ttu-id="2c571-113">Vrátí bitové spojení z `value1` a `value2` jako typ `value1` a `value2`.</span><span class="sxs-lookup"><span data-stu-id="2c571-113">Returns the bitwise conjunction of `value1` and `value2` as the type of `value1` and `value2`.</span></span><br /><br /> <span data-ttu-id="2c571-114">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="2c571-114">**Arguments**</span></span><br /><br /> <span data-ttu-id="2c571-115">A `Byte`, `Int16`, `Int32`, a `Int64`.</span><span class="sxs-lookup"><span data-stu-id="2c571-115">A `Byte`, `Int16`, `Int32`, and `Int64`.</span></span><br /><br /> <span data-ttu-id="2c571-116">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="2c571-116">**Example**</span></span><br /><br /> `-- The following example returns 1.`<br /><br /> `BitWiseAnd(1,3)`|  
|<span data-ttu-id="2c571-117">`BitWiseNot (` `value` `)`</span><span class="sxs-lookup"><span data-stu-id="2c571-117">`BitWiseNot (` `value` `)`</span></span>|<span data-ttu-id="2c571-118">Vrátí bitovou negaci z `value`.</span><span class="sxs-lookup"><span data-stu-id="2c571-118">Returns the bitwise negation of `value`.</span></span><br /><br /> <span data-ttu-id="2c571-119">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="2c571-119">**Arguments**</span></span><br /><br /> <span data-ttu-id="2c571-120">A `Byte`, `Int16`, `Int32`, a `Int64`.</span><span class="sxs-lookup"><span data-stu-id="2c571-120">A `Byte`, `Int16`, `Int32`, and `Int64`.</span></span><br /><br /> <span data-ttu-id="2c571-121">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="2c571-121">**Example**</span></span><br /><br /> `-- The following example returns -4.`<br /><br /> `BitWiseNot(3)`|  
|<span data-ttu-id="2c571-122">`BitWiseOr (` `value1` `,`  `value2` `)`</span><span class="sxs-lookup"><span data-stu-id="2c571-122">`BitWiseOr (` `value1` `,`  `value2` `)`</span></span>|<span data-ttu-id="2c571-123">Vrátí bitovou disjunkci z `value1` a `value2` jako typ `value1` a `value2`.</span><span class="sxs-lookup"><span data-stu-id="2c571-123">Returns the bitwise disjunction of `value1` and `value2` as the type of `value1` and `value2`.</span></span><br /><br /> <span data-ttu-id="2c571-124">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="2c571-124">**Arguments**</span></span><br /><br /> <span data-ttu-id="2c571-125">A `Byte`, `Int16`, `Int32` a `Int64`.</span><span class="sxs-lookup"><span data-stu-id="2c571-125">A `Byte`, `Int16`, `Int32` and `Int64`.</span></span><br /><br /> <span data-ttu-id="2c571-126">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="2c571-126">**Example**</span></span><br /><br /> `-- The following example returns 3.`<br /><br /> `BitWiseOr(1,3)`|  
|<span data-ttu-id="2c571-127">`BitWiseXor (` `value1` `,`  `value2` `)`</span><span class="sxs-lookup"><span data-stu-id="2c571-127">`BitWiseXor (` `value1` `,`  `value2` `)`</span></span>|<span data-ttu-id="2c571-128">Vrátí bitový exkluzivní disjunkce z `value1` a `value2` jako typ `value1` a `value2`.</span><span class="sxs-lookup"><span data-stu-id="2c571-128">Returns the bitwise exclusive disjunction of `value1` and `value2` as the type of `value1` and `value2`.</span></span><br /><br /> <span data-ttu-id="2c571-129">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="2c571-129">**Arguments**</span></span><br /><br /> <span data-ttu-id="2c571-130">A `Byte`, `Int16`, `Int32` a `Int64`.</span><span class="sxs-lookup"><span data-stu-id="2c571-130">A `Byte`, `Int16`, `Int32` and `Int64`.</span></span><br /><br /> <span data-ttu-id="2c571-131">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="2c571-131">**Example**</span></span><br /><br /> `-- The following example returns 2.`<br /><br /> `BitWiseXor (1,3)`|  
  
## <a name="see-also"></a><span data-ttu-id="2c571-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="2c571-132">See Also</span></span>  
 [<span data-ttu-id="2c571-133">Kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="2c571-133">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
