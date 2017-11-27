---
title: "++ – operátor (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6deb2f772fefc93020e7eaaed6be35e48b11df7a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="73998-102">++ – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="73998-102">++ Operator (C# Reference)</span></span>
<span data-ttu-id="73998-103">Operátor přírůstku (`++`) jeho operand zvýší o 1.</span><span class="sxs-lookup"><span data-stu-id="73998-103">The increment operator (`++`) increments its operand by 1.</span></span> <span data-ttu-id="73998-104">Operátor přírůstku může vyskytovat před nebo po jeho operand: `++variable` a `variable++`.</span><span class="sxs-lookup"><span data-stu-id="73998-104">The increment operator can appear before or after its operand: `++variable` and `variable++`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73998-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="73998-105">Remarks</span></span>  
 <span data-ttu-id="73998-106">První formulář je předpona přírůstek operace.</span><span class="sxs-lookup"><span data-stu-id="73998-106">The first form is a prefix increment operation.</span></span> <span data-ttu-id="73998-107">Výsledkem operace je hodnota operand po byla zvýšena.</span><span class="sxs-lookup"><span data-stu-id="73998-107">The result of the operation is the value of the operand after it has been incremented.</span></span>  
  
 <span data-ttu-id="73998-108">Druhý formulář je operace operátory přírůstku.</span><span class="sxs-lookup"><span data-stu-id="73998-108">The second form is a postfix increment operation.</span></span> <span data-ttu-id="73998-109">Výsledkem operace je hodnota operand předtím, než byla zvýšena.</span><span class="sxs-lookup"><span data-stu-id="73998-109">The result of the operation is the value of the operand before it has been incremented.</span></span>  
  
 <span data-ttu-id="73998-110">Operátory přírůstku obsahuje předdefinované číselné a výčtové typy.</span><span class="sxs-lookup"><span data-stu-id="73998-110">Numeric and enumeration types have predefined increment operators.</span></span> <span data-ttu-id="73998-111">Uživatelem definované typy může přetížit `++` operátor.</span><span class="sxs-lookup"><span data-stu-id="73998-111">User-defined types can overload the `++` operator.</span></span> <span data-ttu-id="73998-112">Operace u celočíselných typů jsou obecně povoleny na výčtu.</span><span class="sxs-lookup"><span data-stu-id="73998-112">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73998-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="73998-113">Example</span></span>  
 [!code-csharp[csRefOperators#3](../../../csharp/language-reference/operators/codesnippet/CSharp/increment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="73998-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="73998-114">See Also</span></span>  
 [<span data-ttu-id="73998-115">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="73998-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="73998-116">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="73998-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="73998-117">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="73998-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
