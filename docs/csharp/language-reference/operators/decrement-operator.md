---
title: -- – operátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- --_CSharpKeyword
helpviewer_keywords:
- -- operator [C#]
- decrement operator (--) [C#]
ms.assetid: 6b9cfe86-63c7-421f-9379-c9690fea8720
ms.openlocfilehash: 615b100447233856ab3740d075d69e3ae19285fd
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44037799"
---
# <a name="---operator-c-reference"></a><span data-ttu-id="1c1c1-102">-- – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="1c1c1-102">-- Operator (C# Reference)</span></span>
<span data-ttu-id="1c1c1-103">Operátor dekrementace (`--`) sníží svého operandu o 1.</span><span class="sxs-lookup"><span data-stu-id="1c1c1-103">The decrement operator (`--`) decrements its operand by 1.</span></span> <span data-ttu-id="1c1c1-104">Operátor dekrementace se může objevit před nebo po jeho operandu: `--variable` a `variable--`.</span><span class="sxs-lookup"><span data-stu-id="1c1c1-104">The decrement operator can appear before or after its operand: `--variable` and `variable--`.</span></span> <span data-ttu-id="1c1c1-105">První forma je operace dekrementace předpony.</span><span class="sxs-lookup"><span data-stu-id="1c1c1-105">The first form is a prefix decrement operation.</span></span> <span data-ttu-id="1c1c1-106">Výsledkem operace je hodnota operandu "po" byl snížen.</span><span class="sxs-lookup"><span data-stu-id="1c1c1-106">The result of the operation is the value of the operand "after" it has been decremented.</span></span> <span data-ttu-id="1c1c1-107">Druhá forma se operace dekrementace přípony.</span><span class="sxs-lookup"><span data-stu-id="1c1c1-107">The second form is a postfix decrement operation.</span></span> <span data-ttu-id="1c1c1-108">Výsledkem operace je hodnota operandu "před" byl snížen.</span><span class="sxs-lookup"><span data-stu-id="1c1c1-108">The result of the operation is the value of the operand "before" it has been decremented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c1c1-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1c1c1-109">Remarks</span></span>  
 <span data-ttu-id="1c1c1-110">Operátory snížení obsahuje předdefinované číselné a výčet typů.</span><span class="sxs-lookup"><span data-stu-id="1c1c1-110">Numeric and enumeration types have predefined decrement operators.</span></span>  
  
 <span data-ttu-id="1c1c1-111">Lze přetěžovat uživatelsky definované typy `--` – operátor (viz [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="1c1c1-111">User-defined types can overload the `--` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="1c1c1-112">Operace interních typů jsou obecně povoleny na výčet.</span><span class="sxs-lookup"><span data-stu-id="1c1c1-112">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c1c1-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="1c1c1-113">Example</span></span>  
 [!code-csharp[csRefOperators#8](../../../csharp/language-reference/operators/codesnippet/CSharp/decrement-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="1c1c1-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="1c1c1-114">See Also</span></span>

- [<span data-ttu-id="1c1c1-115">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1c1c1-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="1c1c1-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="1c1c1-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="1c1c1-117">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1c1c1-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
