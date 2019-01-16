---
title: '- Operator - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- -_CSharpKeyword
helpviewer_keywords:
- '- operator [C#]'
- subtraction operator (-) [C#]
ms.assetid: 4de7a4fa-c69d-48e6-aff1-3130af970b2d
ms.openlocfilehash: 8cf6e8871a88e2b37b9531ecbd616289523473c7
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333756"
---
# <a name="--operator-c-reference"></a><span data-ttu-id="3c628-102">-– operátor (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="3c628-102">- operator (C# Reference)</span></span>

<span data-ttu-id="3c628-103">`-` Operátor může fungovat jako unární nebo binární operátor.</span><span class="sxs-lookup"><span data-stu-id="3c628-103">The `-` operator can function as either a unary or a binary operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="3c628-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3c628-104">Remarks</span></span>

<span data-ttu-id="3c628-105">Unární `-` operátory jsou předdefinované pro všechny číselné typy.</span><span class="sxs-lookup"><span data-stu-id="3c628-105">Unary `-` operators are predefined for all numeric types.</span></span> <span data-ttu-id="3c628-106">Výsledek unární `-` operace na číselný typ je negaci číselného operandu.</span><span class="sxs-lookup"><span data-stu-id="3c628-106">The result of a unary `-` operation on a numeric type is the numeric negation of the operand.</span></span>

<span data-ttu-id="3c628-107">Binární `-` operátory jsou předdefinované pro všechny typy číselné a výčet odečte druhý operand od prvního.</span><span class="sxs-lookup"><span data-stu-id="3c628-107">Binary `-` operators are predefined for all numeric and enumeration types to subtract the second operand from the first.</span></span>

<span data-ttu-id="3c628-108">Typy delegátů také poskytují binární soubor `-` operátor, který provádí odebrání delegátů.</span><span class="sxs-lookup"><span data-stu-id="3c628-108">Delegate types also provide a binary `-` operator, which performs delegate removal.</span></span>

<span data-ttu-id="3c628-109">Uživatelem definované typy mohou přetížit unární `-` a binární `-` operátory.</span><span class="sxs-lookup"><span data-stu-id="3c628-109">User-defined types can overload the unary `-` and binary `-` operators.</span></span> <span data-ttu-id="3c628-110">Další informace najdete v tématu [– klíčové slovo operátoru](../keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="3c628-110">For more information, see [operator keyword](../keywords/operator.md).</span></span>

## <a name="example"></a><span data-ttu-id="3c628-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="3c628-111">Example</span></span>

[!code-csharp[csRefOperators#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#40)]

## <a name="see-also"></a><span data-ttu-id="3c628-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3c628-112">See also</span></span>

- [<span data-ttu-id="3c628-113">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3c628-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3c628-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="3c628-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3c628-115">C#operátory</span><span class="sxs-lookup"><span data-stu-id="3c628-115">C# operators</span></span>](index.md)