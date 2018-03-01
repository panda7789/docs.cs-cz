---
title: "-- – operátor (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- --_CSharpKeyword
helpviewer_keywords:
- -- operator [C#]
- decrement operator (--) [C#]
ms.assetid: 6b9cfe86-63c7-421f-9379-c9690fea8720
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4eb68143103d44defeac7191e7c4ce7d1ee90e9b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="---operator-c-reference"></a><span data-ttu-id="f5e1b-102">-- – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="f5e1b-102">-- Operator (C# Reference)</span></span>
<span data-ttu-id="f5e1b-103">Operátor snížení (`--`) snižuje jeho operand o 1.</span><span class="sxs-lookup"><span data-stu-id="f5e1b-103">The decrement operator (`--`) decrements its operand by 1.</span></span> <span data-ttu-id="f5e1b-104">Operátor snížení může vyskytovat před nebo po jeho operand: `--variable` a `variable--`.</span><span class="sxs-lookup"><span data-stu-id="f5e1b-104">The decrement operator can appear before or after its operand: `--variable` and `variable--`.</span></span> <span data-ttu-id="f5e1b-105">První formulář je operace snížení předpony.</span><span class="sxs-lookup"><span data-stu-id="f5e1b-105">The first form is a prefix decrement operation.</span></span> <span data-ttu-id="f5e1b-106">Výsledkem operace je hodnota operand "po" byla odečte.</span><span class="sxs-lookup"><span data-stu-id="f5e1b-106">The result of the operation is the value of the operand "after" it has been decremented.</span></span> <span data-ttu-id="f5e1b-107">Druhý formulář je operátory snížení operace.</span><span class="sxs-lookup"><span data-stu-id="f5e1b-107">The second form is a postfix decrement operation.</span></span> <span data-ttu-id="f5e1b-108">Výsledkem operace je hodnota operand "před" jeho odečte.</span><span class="sxs-lookup"><span data-stu-id="f5e1b-108">The result of the operation is the value of the operand "before" it has been decremented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5e1b-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f5e1b-109">Remarks</span></span>  
 <span data-ttu-id="f5e1b-110">Operátory snížení obsahuje předdefinované číselné a výčtové typy.</span><span class="sxs-lookup"><span data-stu-id="f5e1b-110">Numeric and enumeration types have predefined decrement operators.</span></span>  
  
 <span data-ttu-id="f5e1b-111">Uživatelem definované typy může přetížit `--` – operátor (najdete v části [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="f5e1b-111">User-defined types can overload the `--` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="f5e1b-112">Operace u celočíselných typů jsou obecně povoleny na výčtu.</span><span class="sxs-lookup"><span data-stu-id="f5e1b-112">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5e1b-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5e1b-113">Example</span></span>  
 [!code-csharp[csRefOperators#8](../../../csharp/language-reference/operators/codesnippet/CSharp/decrement-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f5e1b-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5e1b-114">See Also</span></span>  
 [<span data-ttu-id="f5e1b-115">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f5e1b-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f5e1b-116">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="f5e1b-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f5e1b-117">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f5e1b-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
