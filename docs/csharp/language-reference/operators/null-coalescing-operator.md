---
title: ?? Operator - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- coalesce operator [C#]
- ?? operator [C#]
- conditional-AND operator (&&) [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: b96fe4790aac7ff5ff5394cbaaeaddc1e334e96c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61689330"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="e3a41-103">??</span><span class="sxs-lookup"><span data-stu-id="e3a41-103">??</span></span> <span data-ttu-id="e3a41-104">operator (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e3a41-104">operator (C# Reference)</span></span>

<span data-ttu-id="e3a41-105">`??` Operátor se nazývá operátoru nulového sjednocení.</span><span class="sxs-lookup"><span data-stu-id="e3a41-105">The `??` operator is called the null-coalescing operator.</span></span>  <span data-ttu-id="e3a41-106">Vrátí levý operand, pokud hodnota operandu není null; v opačném případě vrátí pravý operand.</span><span class="sxs-lookup"><span data-stu-id="e3a41-106">It returns the left-hand operand if the operand is not null; otherwise it returns the right hand operand.</span></span>

## <a name="remarks"></a><span data-ttu-id="e3a41-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e3a41-107">Remarks</span></span>

<span data-ttu-id="e3a41-108">Typ povolené hodnoty null představuje hodnotu z domény typu, hodnotu lze také definovat (v takovém případě je hodnota null).</span><span class="sxs-lookup"><span data-stu-id="e3a41-108">A nullable type can represent a value from the type’s domain, or the value can be undefined (in which case the value is null).</span></span> <span data-ttu-id="e3a41-109">Můžete použít `??` syntaktické expresivity obsluhy se vraťte na příslušnou hodnotu (pravý operand) Pokud levý operand má typ s možnou hodnotou Null, jehož hodnota je null.</span><span class="sxs-lookup"><span data-stu-id="e3a41-109">You can use the `??` operator’s syntactic expressiveness to return an appropriate value (the right hand operand) when the left operand has a nullable type whose value is null.</span></span> <span data-ttu-id="e3a41-110">Pokud se pokusíte přiřadit typ s možnou hodnotou Null typu hodnotu Null bez použití `??` operátoru, vygeneruje chybu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="e3a41-110">If you try to assign a nullable value type to a non-nullable value type without using the `??` operator, you will generate a compile-time error.</span></span> <span data-ttu-id="e3a41-111">Pokud použijete přetypování a typ s možnou hodnotou Null není aktuálně definován `InvalidOperationException` , bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="e3a41-111">If you use a cast, and the nullable value type is currently undefined, an `InvalidOperationException` exception will be thrown.</span></span>

<span data-ttu-id="e3a41-112">Další informace najdete v tématu [typy připouštějící hodnotu Null](../../programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="e3a41-112">For more information, see [Nullable Types](../../programming-guide/nullable-types/index.md).</span></span>

<span data-ttu-id="e3a41-113">Výsledek??</span><span class="sxs-lookup"><span data-stu-id="e3a41-113">The result of a ??</span></span> <span data-ttu-id="e3a41-114">operátor není považována za konstantu, i když jsou oba argumenty konstanty.</span><span class="sxs-lookup"><span data-stu-id="e3a41-114">operator is not considered to be a constant even if both its arguments are constants.</span></span>

## <a name="example"></a><span data-ttu-id="e3a41-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="e3a41-115">Example</span></span>

[!code-csharp[csRefOperators#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#53)]

## <a name="c-language-specification"></a><span data-ttu-id="e3a41-116">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e3a41-116">C# language specification</span></span>

<span data-ttu-id="e3a41-117">Další informace najdete v tématu [null operátor sloučení](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) v [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="e3a41-117">For more information, see [The null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="e3a41-118">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="e3a41-118">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="e3a41-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e3a41-119">See also</span></span>

- [<span data-ttu-id="e3a41-120">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e3a41-120">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e3a41-121">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e3a41-121">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e3a41-122">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e3a41-122">C# operators</span></span>](index.md)
- [<span data-ttu-id="e3a41-123">Typy s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="e3a41-123">Nullable Types</span></span>](../../programming-guide/nullable-types/index.md)
- [<span data-ttu-id="e3a41-124">Co přesně se pojem "zrušeno" znamenají?</span><span class="sxs-lookup"><span data-stu-id="e3a41-124">What Exactly Does 'Lifted' mean?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)