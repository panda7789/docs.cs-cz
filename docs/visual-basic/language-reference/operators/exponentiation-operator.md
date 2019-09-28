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
ms.openlocfilehash: 8cdfbec917608211e19c39eb37bd12dbc7c4d33f
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592213"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="a3d79-102">^ – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3d79-102">^ Operator (Visual Basic)</span></span>

<span data-ttu-id="a3d79-103">Umocní číslo na mocninu jiného čísla.</span><span class="sxs-lookup"><span data-stu-id="a3d79-103">Raises a number to the power of another number.</span></span>

## <a name="syntax"></a><span data-ttu-id="a3d79-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3d79-104">Syntax</span></span>

```vb
number ^ exponent
```

## <a name="parts"></a><span data-ttu-id="a3d79-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="a3d79-105">Parts</span></span>

`number`\
<span data-ttu-id="a3d79-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="a3d79-106">Required.</span></span> <span data-ttu-id="a3d79-107">Libovolný číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="a3d79-107">Any numeric expression.</span></span>

`exponent`\
<span data-ttu-id="a3d79-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="a3d79-108">Required.</span></span> <span data-ttu-id="a3d79-109">Libovolný číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="a3d79-109">Any numeric expression.</span></span>

## <a name="result"></a><span data-ttu-id="a3d79-110">Výsledek</span><span class="sxs-lookup"><span data-stu-id="a3d79-110">Result</span></span>

<span data-ttu-id="a3d79-111">Výsledek je `number` umocněn na mocninu `exponent`, vždy jako hodnota `Double`.</span><span class="sxs-lookup"><span data-stu-id="a3d79-111">The result is `number` raised to the power of `exponent`, always as a `Double` value.</span></span>

## <a name="supported-types"></a><span data-ttu-id="a3d79-112">Podporované typy</span><span class="sxs-lookup"><span data-stu-id="a3d79-112">Supported Types</span></span>

<span data-ttu-id="a3d79-113">`Double`.</span><span class="sxs-lookup"><span data-stu-id="a3d79-113">`Double`.</span></span> <span data-ttu-id="a3d79-114">Operandy jiného typu jsou převedeny na `Double`.</span><span class="sxs-lookup"><span data-stu-id="a3d79-114">Operands of any different type are converted to `Double`.</span></span>

## <a name="remarks"></a><span data-ttu-id="a3d79-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a3d79-115">Remarks</span></span>

<span data-ttu-id="a3d79-116">Visual Basic vždy provádí umocnění v [datovém typu Double](../../../visual-basic/language-reference/data-types/double-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="a3d79-116">Visual Basic always performs exponentiation in the [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).</span></span>

<span data-ttu-id="a3d79-117">Hodnota `exponent` může být zlomková, záporná nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="a3d79-117">The value of `exponent` can be fractional, negative, or both.</span></span>

<span data-ttu-id="a3d79-118">Je-li v jednom výrazu proveden více než jeden umocnění, je operátor `^` vyhodnocen tak, jak byl zjištěn zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="a3d79-118">When more than one exponentiation is performed in a single expression, the `^` operator is evaluated as it is encountered from left to right.</span></span>

> [!NOTE]
> <span data-ttu-id="a3d79-119">Operátor `^` lze přetížit, což znamená, že třída nebo struktura může předefinovat *chování, pokud*operand má typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="a3d79-119">The `^` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="a3d79-120">Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="a3d79-120">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="a3d79-121">Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="a3d79-121">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="example"></a><span data-ttu-id="a3d79-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="a3d79-122">Example</span></span>

<span data-ttu-id="a3d79-123">Následující příklad používá operátor `^` k vyvolání čísla mocninou exponentu.</span><span class="sxs-lookup"><span data-stu-id="a3d79-123">The following example uses the `^` operator to raise a number to the power of an exponent.</span></span> <span data-ttu-id="a3d79-124">Výsledkem je první operand vyvolaný mocninou sekundy.</span><span class="sxs-lookup"><span data-stu-id="a3d79-124">The result is the first operand raised to the power of the second.</span></span>

[!code-vb[VbVbalrOperators#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#20)]

<span data-ttu-id="a3d79-125">Předchozí příklad vytvoří následující výsledky:</span><span class="sxs-lookup"><span data-stu-id="a3d79-125">The preceding example produces the following results:</span></span>

<span data-ttu-id="a3d79-126">`exp1` je nastavené na 4 (2 čtvercové).</span><span class="sxs-lookup"><span data-stu-id="a3d79-126">`exp1` is set to 4 (2 squared).</span></span>

<span data-ttu-id="a3d79-127">hodnota `exp2` je nastavená na 19683 (3 na třetí straně a pak na třetí).</span><span class="sxs-lookup"><span data-stu-id="a3d79-127">`exp2` is set to 19683 (3 cubed, then that value cubed).</span></span>

<span data-ttu-id="a3d79-128">hodnota `exp3` je nastavena na-125 (-5 na třetí).</span><span class="sxs-lookup"><span data-stu-id="a3d79-128">`exp3` is set to -125 (-5 cubed).</span></span>

<span data-ttu-id="a3d79-129">hodnota `exp4` je nastavená na 625 (-5 až čtvrtého výkonu).</span><span class="sxs-lookup"><span data-stu-id="a3d79-129">`exp4` is set to 625 (-5 to the fourth power).</span></span>

<span data-ttu-id="a3d79-130">hodnota `exp5` je nastavena na hodnotu 2 (kořenová hodnota datové krychle 8).</span><span class="sxs-lookup"><span data-stu-id="a3d79-130">`exp5` is set to 2 (cube root of 8).</span></span>

<span data-ttu-id="a3d79-131">hodnota `exp6` je nastavena na 0,5 (1,0 děleno kořenem datové krychle 8).</span><span class="sxs-lookup"><span data-stu-id="a3d79-131">`exp6` is set to 0.5 (1.0 divided by the cube root of 8).</span></span>

<span data-ttu-id="a3d79-132">Všimněte si důležitosti závorek ve výrazech v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a3d79-132">Note the importance of the parentheses in the expressions in the preceding example.</span></span> <span data-ttu-id="a3d79-133">Z důvodu *přednosti operátoru*Visual Basic obvykle provádí operátor `^` před všemi ostatními, a to i unární operátor `–`.</span><span class="sxs-lookup"><span data-stu-id="a3d79-133">Because of *operator precedence*, Visual Basic normally performs the `^` operator before any others, even the unary `–` operator.</span></span> <span data-ttu-id="a3d79-134">Pokud byla vypočítána hodnota `exp4` a `exp6` bez závorek, byly vytvořeny následující výsledky:</span><span class="sxs-lookup"><span data-stu-id="a3d79-134">If `exp4` and `exp6` had been calculated without parentheses, they would have produced the following results:</span></span>

<span data-ttu-id="a3d79-135">`exp4 = -5 ^ 4` se vypočítá jako – (5 až čtvrtého výkonu), což by vedlo k-625.</span><span class="sxs-lookup"><span data-stu-id="a3d79-135">`exp4 = -5 ^ 4` would be calculated as –(5 to the fourth power), which would result in -625.</span></span>

<span data-ttu-id="a3d79-136">`exp6 = 8 ^ -1.0 / 3.0` by se vypočítalo jako (8 na-1 výkon nebo 0,125) dělené 3,0, což by vedlo k 0.041666666666666666666666666666667.</span><span class="sxs-lookup"><span data-stu-id="a3d79-136">`exp6 = 8 ^ -1.0 / 3.0` would be calculated as (8 to the –1 power, or 0.125) divided by 3.0, which would result in 0.041666666666666666666666666666667.</span></span>

## <a name="see-also"></a><span data-ttu-id="a3d79-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a3d79-137">See also</span></span>

- [<span data-ttu-id="a3d79-138">^= – operátor</span><span class="sxs-lookup"><span data-stu-id="a3d79-138">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [<span data-ttu-id="a3d79-139">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="a3d79-139">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="a3d79-140">Priorita operátorů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a3d79-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="a3d79-141">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="a3d79-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="a3d79-142">Aritmetické operátory v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a3d79-142">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
