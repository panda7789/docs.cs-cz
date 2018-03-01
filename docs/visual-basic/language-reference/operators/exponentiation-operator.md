---
title: "^ – operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.^
helpviewer_keywords:
- raising numbers to powers
- ^ operator [Visual Basic], exponention
- square operator [Visual Basic]
- ^ operator [Visual Basic]
- exponentiation operator [Visual Basic]
- exponent
- numbers [Visual Basic], rasing
- powers
- arithmetic operators [Visual Basic], exponentiation
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9e7159f289b687055c7d75cc8da58d6f76607a83
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="c3172-102">^ – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3172-102">^ Operator (Visual Basic)</span></span>
<span data-ttu-id="c3172-103">Umocní jedno číslo na mocninu vyjádřenou druhým číslem.</span><span class="sxs-lookup"><span data-stu-id="c3172-103">Raises a number to the power of another number.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3172-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3172-104">Syntax</span></span>  
  
```  
number ^ exponent  
```  
  
## <a name="parts"></a><span data-ttu-id="c3172-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="c3172-105">Parts</span></span>  
 `number`  
 <span data-ttu-id="c3172-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="c3172-106">Required.</span></span> <span data-ttu-id="c3172-107">Jakýkoli číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="c3172-107">Any numeric expression.</span></span>  
  
 `exponent`  
 <span data-ttu-id="c3172-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="c3172-108">Required.</span></span> <span data-ttu-id="c3172-109">Jakýkoli číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="c3172-109">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="c3172-110">Výsledek</span><span class="sxs-lookup"><span data-stu-id="c3172-110">Result</span></span>  
 <span data-ttu-id="c3172-111">Výsledkem je `number` umocněné z `exponent`, vždy jako `Double` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c3172-111">The result is `number` raised to the power of `exponent`, always as a `Double` value.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="c3172-112">Podporované typy</span><span class="sxs-lookup"><span data-stu-id="c3172-112">Supported Types</span></span>  
 <span data-ttu-id="c3172-113">`Double`.</span><span class="sxs-lookup"><span data-stu-id="c3172-113">`Double`.</span></span> <span data-ttu-id="c3172-114">Operandy žádné jiného typu se převedou na `Double`.</span><span class="sxs-lookup"><span data-stu-id="c3172-114">Operands of any different type are converted to `Double`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3172-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c3172-115">Remarks</span></span>  
 <span data-ttu-id="c3172-116">Visual Basic vždy provede exponenciální zápis v [dvojitý datový typ](../../../visual-basic/language-reference/data-types/double-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="c3172-116">Visual Basic always performs exponentiation in the [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).</span></span>  
  
 <span data-ttu-id="c3172-117">Hodnota `exponent` může být zlomkové záporné nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="c3172-117">The value of `exponent` can be fractional, negative, or both.</span></span>  
  
 <span data-ttu-id="c3172-118">Pokud se více než jeden exponenciální zápis se provádí v jeden výraz `^` operátor je vyhodnocena jako jeho zjištění zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="c3172-118">When more than one exponentiation is performed in a single expression, the `^` operator is evaluated as it is encountered from left to right.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3172-119">`^` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="c3172-119">The `^` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="c3172-120">Pokud váš kód používá tento operátor na takové třídu nebo strukturu, ujistěte se, že rozumíte své Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="c3172-120">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="c3172-121">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="c3172-121">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3172-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="c3172-122">Example</span></span>  
 <span data-ttu-id="c3172-123">Následující příklad používá `^` operátor umožňuje aktivovat číslo na mocninu exponentem.</span><span class="sxs-lookup"><span data-stu-id="c3172-123">The following example uses the `^` operator to raise a number to the power of an exponent.</span></span> <span data-ttu-id="c3172-124">Výsledkem je první operand umocněné druhého.</span><span class="sxs-lookup"><span data-stu-id="c3172-124">The result is the first operand raised to the power of the second.</span></span>  
  
 [!code-vb[VbVbalrOperators#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-operator_1.vb)]  
  
 <span data-ttu-id="c3172-125">V předchozím příkladu poskytne následující výsledky:</span><span class="sxs-lookup"><span data-stu-id="c3172-125">The preceding example produces the following results:</span></span>  
  
 <span data-ttu-id="c3172-126">`exp1`je nastavena na 4 (2 spolehlivosti).</span><span class="sxs-lookup"><span data-stu-id="c3172-126">`exp1` is set to 4 (2 squared).</span></span>  
  
 <span data-ttu-id="c3172-127">`exp2`je nastavena na 19683 (na třetí, 3 pak tuto hodnotu na třetí).</span><span class="sxs-lookup"><span data-stu-id="c3172-127">`exp2` is set to 19683 (3 cubed, then that value cubed).</span></span>  
  
 <span data-ttu-id="c3172-128">`exp3`je nastavena na-125 (-5 umocněnou).</span><span class="sxs-lookup"><span data-stu-id="c3172-128">`exp3` is set to -125 (-5 cubed).</span></span>  
  
 <span data-ttu-id="c3172-129">`exp4`je nastavena na 625 (čtvrtý exponentem -5).</span><span class="sxs-lookup"><span data-stu-id="c3172-129">`exp4` is set to 625 (-5 to the fourth power).</span></span>  
  
 <span data-ttu-id="c3172-130">`exp5`je nastaven na hodnotu 2 (datové krychle kořen 8).</span><span class="sxs-lookup"><span data-stu-id="c3172-130">`exp5` is set to 2 (cube root of 8).</span></span>  
  
 <span data-ttu-id="c3172-131">`exp6`je nastavena na 0,5 (1.0 dělený kořenové datové krychle 8).</span><span class="sxs-lookup"><span data-stu-id="c3172-131">`exp6` is set to 0.5 (1.0 divided by the cube root of 8).</span></span>  
  
 <span data-ttu-id="c3172-132">Poznámka: význam závorkách ve výrazech v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c3172-132">Note the importance of the parentheses in the expressions in the preceding example.</span></span> <span data-ttu-id="c3172-133">Z důvodu *operátorů*, Visual Basic obvykle provádí `^` i unární operátor před všech ostatních `–` operátor.</span><span class="sxs-lookup"><span data-stu-id="c3172-133">Because of *operator precedence*, Visual Basic normally performs the `^` operator before any others, even the unary `–` operator.</span></span> <span data-ttu-id="c3172-134">Pokud `exp4` a `exp6` měl vypočítána bez závorek, by je tvořen následující výsledky:</span><span class="sxs-lookup"><span data-stu-id="c3172-134">If `exp4` and `exp6` had been calculated without parentheses, they would have produced the following results:</span></span>  
  
 <span data-ttu-id="c3172-135">`exp4 = -5 ^ 4`se počítá jako – (5 čtvrtý exponentem), což by způsobilo-625.</span><span class="sxs-lookup"><span data-stu-id="c3172-135">`exp4 = -5 ^ 4` would be calculated as –(5 to the fourth power), which would result in -625.</span></span>  
  
 <span data-ttu-id="c3172-136">`exp6 = 8 ^ -1.0 / 3.0`se počítá jako (8 power – 1 nebo 0,125) dělený 3.0, který by způsobilo 0.041666666666666666666666666666667.</span><span class="sxs-lookup"><span data-stu-id="c3172-136">`exp6 = 8 ^ -1.0 / 3.0` would be calculated as (8 to the –1 power, or 0.125) divided by 3.0, which would result in 0.041666666666666666666666666666667.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3172-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="c3172-137">See Also</span></span>  
 [<span data-ttu-id="c3172-138">^ = – Operátor</span><span class="sxs-lookup"><span data-stu-id="c3172-138">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)  
 [<span data-ttu-id="c3172-139">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="c3172-139">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="c3172-140">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c3172-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="c3172-141">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="c3172-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="c3172-142">Aritmetické operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c3172-142">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
