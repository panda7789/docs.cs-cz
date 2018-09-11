---
title: '% – operátor (Referenční dokumentace jazyka C#)'
ms.date: 09/04/2018
f1_keywords:
- '%_CSharpKeyword'
helpviewer_keywords:
- remainder operator [C#]
- '% operator [C#]'
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
ms.openlocfilehash: 9cd2f7ad3856feb34667686979c942ecb21887c2
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44266693"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="84530-102">% – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="84530-102">% Operator (C# Reference)</span></span>

<span data-ttu-id="84530-103">Operátor zbytku `%` vypočítá zbytek po dělení svůj první operand tak svým druhým operandem.</span><span class="sxs-lookup"><span data-stu-id="84530-103">The remainder operator `%` computes the remainder after dividing its first operand by its second operand.</span></span> <span data-ttu-id="84530-104">Uživatelem definované typy lze [přetížení](../keywords/operator.md) `%` operátor.</span><span class="sxs-lookup"><span data-stu-id="84530-104">User-defined types can [overload](../keywords/operator.md) the `%` operator.</span></span> <span data-ttu-id="84530-105">Když `%` je přetížena, [operátor přiřazení zbytku](remainder-assignment-operator.md) `%=` je také implicitně přetížená.</span><span class="sxs-lookup"><span data-stu-id="84530-105">When the `%` is overloaded, the [remainder assignment operator](remainder-assignment-operator.md) `%=` is also implicitly overloaded.</span></span>

<span data-ttu-id="84530-106">Všechny číselné typy podporují operátor zbytku.</span><span class="sxs-lookup"><span data-stu-id="84530-106">All numeric types support the remainder operator.</span></span>

## <a name="integer-remainder"></a><span data-ttu-id="84530-107">Zbývající celé číslo</span><span class="sxs-lookup"><span data-stu-id="84530-107">Integer remainder</span></span>
  
<span data-ttu-id="84530-108">Pro celočíselné operandy, výsledek `a % b` hodnota vytvořil `a - (a / b) * b`.</span><span class="sxs-lookup"><span data-stu-id="84530-108">For the integer operands, the result of `a % b` is the value produced by `a - (a / b) * b`.</span></span> <span data-ttu-id="84530-109">Znaménko nenulové zbývající je stejný jako první operand, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="84530-109">The sign of the non-zero remainder is the same as that of the first operand, as the following example shows:</span></span>

[!code-csharp-interactive[integer remainder](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#1)]

## <a name="floating-point-remainder"></a><span data-ttu-id="84530-110">Zbytek s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="84530-110">Floating-point remainder</span></span>

<span data-ttu-id="84530-111">Pro [float](../keywords/float.md) a [double](../keywords/double.md) operandy, výsledek `x % y` pro omezenou `x` a `y` je hodnota `z` tak, aby</span><span class="sxs-lookup"><span data-stu-id="84530-111">For the [float](../keywords/float.md) and [double](../keywords/double.md) operands, the result of `x % y` for the finite `x` and `y` is the value `z` such that</span></span>

- <span data-ttu-id="84530-112">znaménko `z`nenulová, pokud je stejný jako znaménko `x`;</span><span class="sxs-lookup"><span data-stu-id="84530-112">the sign of `z`, if non-zero, is the same as the sign of `x`;</span></span>
- <span data-ttu-id="84530-113">absolutní hodnota `z` hodnota vytvořil `|x| - n * |y|` kde `n` je největší možné číslo, které je menší než nebo rovna hodnotě `|x| / |y|` a `|x|` a `|y|` jsou absolutní hodnoty `x` a `y`v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="84530-113">the absolute value of `z` is the value produced by `|x| - n * |y|` where `n` is the largest possible integer that is less than or equal to `|x| / |y|` and `|x|` and `|y|` are the absolute values of `x` and `y`, respectively.</span></span>

<span data-ttu-id="84530-114">Informace o chování `%` operátor v případě nekonečnou operandy, najdete v článku [operátor zbytku](/dotnet/csharp/language-reference/language-specification/expressions#remainder-operator) část [specifikace jazyka C#](/dotnet/csharp/language-reference/language-specification/index).</span><span class="sxs-lookup"><span data-stu-id="84530-114">For information about behavior of the `%` operator in case of non-finite operands, see the [Remainder operator](/dotnet/csharp/language-reference/language-specification/expressions#remainder-operator) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/index).</span></span>

> [!NOTE]
> <span data-ttu-id="84530-115">Tato metoda výpočetních zbytek je obdobou, který používá pro celočíselné operandy, ale se liší od IEEE 754.</span><span class="sxs-lookup"><span data-stu-id="84530-115">This method of computing the remainder is analogous to that used for integer operands, but differs from the IEEE 754.</span></span> <span data-ttu-id="84530-116">Pokud potřebujete zbývající operace, která splňuje IEEE 754, použijte <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="84530-116">If you need the remainder operation that complies with the IEEE 754, use the <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="84530-117">Následující příklad ukazuje chování operátor zbytku pro `float` a `double` operandy:</span><span class="sxs-lookup"><span data-stu-id="84530-117">The following example demonstrates the behavior of the remainder operator for `float` and `double` operands:</span></span>

[!code-csharp-interactive[float and double remainder](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#2)]

<span data-ttu-id="84530-118">Všimněte si zaokrouhlovací chyby, které mohou být spojeny s typy s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="84530-118">Note the round-off errors that can be associated with the floating-point types.</span></span>

<span data-ttu-id="84530-119">Pro [desítkové](../keywords/decimal.md) operandy, operátor zbytku `%` odpovídá [operátor zbytku](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) z <xref:System.Decimal?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="84530-119">For the [decimal](../keywords/decimal.md) operands, the remainder operator `%` is equivalent to the [remainder operator](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) of the <xref:System.Decimal?displayProperty=nameWithType> type.</span></span>

## <a name="see-also"></a><span data-ttu-id="84530-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="84530-120">See also</span></span>

- [<span data-ttu-id="84530-121">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="84530-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="84530-122">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="84530-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="84530-123">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="84530-123">C# Operators</span></span>](index.md)
- <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType>
- <xref:System.Math.DivRem%2A?displayProperty=nameWithType>
