---
title: ^ – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.^
helpviewer_keywords:
- raising numbers to powers
- ^ operator [Visual Basic], exponentiation
- square operator [Visual Basic]
- ^ operator [Visual Basic]
- exponentiation operator [Visual Basic]
- exponent
- numbers [Visual Basic], rasing
- powers
- arithmetic operators [Visual Basic], exponentiation
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
ms.openlocfilehash: 54de9c91d4e166b8ca1733952dfa9c98ebf11ffe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778492"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="b672a-102">^ – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b672a-102">^ Operator (Visual Basic)</span></span>

<span data-ttu-id="b672a-103">Umocní jedno číslo na mocninu vyjádřenou druhým číslem.</span><span class="sxs-lookup"><span data-stu-id="b672a-103">Raises a number to the power of another number.</span></span>

## <a name="syntax"></a><span data-ttu-id="b672a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b672a-104">Syntax</span></span>

```
number ^ exponent
```

## <a name="parts"></a><span data-ttu-id="b672a-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="b672a-105">Parts</span></span>

`number`\
<span data-ttu-id="b672a-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="b672a-106">Required.</span></span> <span data-ttu-id="b672a-107">Jakýkoli číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="b672a-107">Any numeric expression.</span></span>

`exponent`\
<span data-ttu-id="b672a-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="b672a-108">Required.</span></span> <span data-ttu-id="b672a-109">Jakýkoli číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="b672a-109">Any numeric expression.</span></span>

## <a name="result"></a><span data-ttu-id="b672a-110">Výsledek</span><span class="sxs-lookup"><span data-stu-id="b672a-110">Result</span></span>

<span data-ttu-id="b672a-111">Výsledkem je `number` umocněné na sílu `exponent`, vždy jako `Double` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b672a-111">The result is `number` raised to the power of `exponent`, always as a `Double` value.</span></span>

## <a name="supported-types"></a><span data-ttu-id="b672a-112">Podporované typy</span><span class="sxs-lookup"><span data-stu-id="b672a-112">Supported Types</span></span>

<span data-ttu-id="b672a-113">`Double`.</span><span class="sxs-lookup"><span data-stu-id="b672a-113">`Double`.</span></span> <span data-ttu-id="b672a-114">Jakýkoli jiný typ operandy jsou převedeny na `Double`.</span><span class="sxs-lookup"><span data-stu-id="b672a-114">Operands of any different type are converted to `Double`.</span></span>

## <a name="remarks"></a><span data-ttu-id="b672a-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b672a-115">Remarks</span></span>

<span data-ttu-id="b672a-116">Visual Basic vždy provádí umocnění v [datový typ Double](../../../visual-basic/language-reference/data-types/double-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="b672a-116">Visual Basic always performs exponentiation in the [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).</span></span>

<span data-ttu-id="b672a-117">Hodnota `exponent` může být zlomkové záporné nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="b672a-117">The value of `exponent` can be fractional, negative, or both.</span></span>

<span data-ttu-id="b672a-118">Při provádění více než jeden umocnění v jednom výrazu `^` operátor je vyhodnocovány, jak je zjištěna zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="b672a-118">When more than one exponentiation is performed in a single expression, the `^` operator is evaluated as it is encountered from left to right.</span></span>

> [!NOTE]
> <span data-ttu-id="b672a-119">`^` Operátor může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="b672a-119">The `^` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="b672a-120">Pokud váš kód používá tento operátor na takové třídy nebo struktury, ujistěte se, že rozumíte jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="b672a-120">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="b672a-121">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b672a-121">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="example"></a><span data-ttu-id="b672a-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="b672a-122">Example</span></span>

<span data-ttu-id="b672a-123">V následujícím příkladu `^` operátor se má zvýšit číslo mocninu exponent.</span><span class="sxs-lookup"><span data-stu-id="b672a-123">The following example uses the `^` operator to raise a number to the power of an exponent.</span></span> <span data-ttu-id="b672a-124">Výsledkem je první operand umocněné na druhou.</span><span class="sxs-lookup"><span data-stu-id="b672a-124">The result is the first operand raised to the power of the second.</span></span>

[!code-vb[VbVbalrOperators#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#20)]

<span data-ttu-id="b672a-125">Předchozí příklad vytváří následující výsledky:</span><span class="sxs-lookup"><span data-stu-id="b672a-125">The preceding example produces the following results:</span></span>

<span data-ttu-id="b672a-126">`exp1` je nastavena na 4 (spolehlivosti 2).</span><span class="sxs-lookup"><span data-stu-id="b672a-126">`exp1` is set to 4 (2 squared).</span></span>

<span data-ttu-id="b672a-127">`exp2` je nastaven na 19683 (umocněnou, 3 pak tuto hodnotu na třetí).</span><span class="sxs-lookup"><span data-stu-id="b672a-127">`exp2` is set to 19683 (3 cubed, then that value cubed).</span></span>

<span data-ttu-id="b672a-128">`exp3` je nastaven na-125 (-5 umocněnou).</span><span class="sxs-lookup"><span data-stu-id="b672a-128">`exp3` is set to -125 (-5 cubed).</span></span>

<span data-ttu-id="b672a-129">`exp4` je nastaven na 625 (čtvrtá exponentem -5).</span><span class="sxs-lookup"><span data-stu-id="b672a-129">`exp4` is set to 625 (-5 to the fourth power).</span></span>

<span data-ttu-id="b672a-130">`exp5` je nastavena na 2 (uživatel root datové krychle 8).</span><span class="sxs-lookup"><span data-stu-id="b672a-130">`exp5` is set to 2 (cube root of 8).</span></span>

<span data-ttu-id="b672a-131">`exp6` je nastaven na 0,5 (1.0 dělený kořenové datové krychle 8).</span><span class="sxs-lookup"><span data-stu-id="b672a-131">`exp6` is set to 0.5 (1.0 divided by the cube root of 8).</span></span>

<span data-ttu-id="b672a-132">Všimněte si důležitost závorky ve výrazech v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b672a-132">Note the importance of the parentheses in the expressions in the preceding example.</span></span> <span data-ttu-id="b672a-133">Z důvodu *priorita operátorů*, Visual Basic se obvykle provádí `^` i unární operátor před všechny ostatní `–` operátor.</span><span class="sxs-lookup"><span data-stu-id="b672a-133">Because of *operator precedence*, Visual Basic normally performs the `^` operator before any others, even the unary `–` operator.</span></span> <span data-ttu-id="b672a-134">Pokud `exp4` a `exp6` měl vypočtena bez závorek by mít vyprodukoval následující výsledky:</span><span class="sxs-lookup"><span data-stu-id="b672a-134">If `exp4` and `exp6` had been calculated without parentheses, they would have produced the following results:</span></span>

<span data-ttu-id="b672a-135">`exp4 = -5 ^ 4` se vypočítá jako – (5 a čtvrtý výkon), které způsobovaly-625.</span><span class="sxs-lookup"><span data-stu-id="b672a-135">`exp4 = -5 ^ 4` would be calculated as –(5 to the fourth power), which would result in -625.</span></span>

<span data-ttu-id="b672a-136">`exp6 = 8 ^ -1.0 / 3.0` se vypočítá jako (8 – 1 napájení nebo 0,125) 3.0, což by vytvořilo 0.041666666666666666666666666666667 dělený.</span><span class="sxs-lookup"><span data-stu-id="b672a-136">`exp6 = 8 ^ -1.0 / 3.0` would be calculated as (8 to the –1 power, or 0.125) divided by 3.0, which would result in 0.041666666666666666666666666666667.</span></span>

## <a name="see-also"></a><span data-ttu-id="b672a-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b672a-137">See also</span></span>

- [<span data-ttu-id="b672a-138">^= – operátor</span><span class="sxs-lookup"><span data-stu-id="b672a-138">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [<span data-ttu-id="b672a-139">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="b672a-139">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="b672a-140">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b672a-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="b672a-141">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="b672a-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="b672a-142">Aritmetické operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b672a-142">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
