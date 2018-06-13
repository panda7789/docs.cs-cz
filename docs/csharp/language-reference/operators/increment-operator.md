---
title: ++ – operátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
ms.openlocfilehash: 0fe1150ca7267d02feeab33168eab7f79734c2a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275061"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="f1b1c-102">++ – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="f1b1c-102">++ Operator (C# Reference)</span></span>
<span data-ttu-id="f1b1c-103">Operátor přírůstku (`++`) jeho operand zvýší o 1.</span><span class="sxs-lookup"><span data-stu-id="f1b1c-103">The increment operator (`++`) increments its operand by 1.</span></span> <span data-ttu-id="f1b1c-104">Operátor přírůstku může vyskytovat před nebo po jeho operand: `++variable` a `variable++`.</span><span class="sxs-lookup"><span data-stu-id="f1b1c-104">The increment operator can appear before or after its operand: `++variable` and `variable++`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1b1c-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f1b1c-105">Remarks</span></span>  
 <span data-ttu-id="f1b1c-106">První formulář je předpona přírůstek operace.</span><span class="sxs-lookup"><span data-stu-id="f1b1c-106">The first form is a prefix increment operation.</span></span> <span data-ttu-id="f1b1c-107">Výsledkem operace je hodnota operand po byla zvýšena.</span><span class="sxs-lookup"><span data-stu-id="f1b1c-107">The result of the operation is the value of the operand after it has been incremented.</span></span>  
  
 <span data-ttu-id="f1b1c-108">Druhý formulář je operace operátory přírůstku.</span><span class="sxs-lookup"><span data-stu-id="f1b1c-108">The second form is a postfix increment operation.</span></span> <span data-ttu-id="f1b1c-109">Výsledkem operace je hodnota operand předtím, než byla zvýšena.</span><span class="sxs-lookup"><span data-stu-id="f1b1c-109">The result of the operation is the value of the operand before it has been incremented.</span></span>  
  
 <span data-ttu-id="f1b1c-110">Operátory přírůstku obsahuje předdefinované číselné a výčtové typy.</span><span class="sxs-lookup"><span data-stu-id="f1b1c-110">Numeric and enumeration types have predefined increment operators.</span></span> <span data-ttu-id="f1b1c-111">Uživatelem definované typy může přetížit `++` operátor.</span><span class="sxs-lookup"><span data-stu-id="f1b1c-111">User-defined types can overload the `++` operator.</span></span> <span data-ttu-id="f1b1c-112">Operace u celočíselných typů jsou obecně povoleny na výčtu.</span><span class="sxs-lookup"><span data-stu-id="f1b1c-112">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1b1c-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="f1b1c-113">Example</span></span>  
 [!code-csharp[csRefOperators#3](../../../csharp/language-reference/operators/codesnippet/CSharp/increment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f1b1c-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="f1b1c-114">See Also</span></span>  
 [<span data-ttu-id="f1b1c-115">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f1b1c-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f1b1c-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="f1b1c-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f1b1c-117">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f1b1c-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
