---
title: '\ – operátor (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.\
- '\'
helpviewer_keywords:
- division operator [Visual Basic], integer
- integer division operator [Visual Basic]
- zero, division by zero
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- backslash (\) [Visual Basic]
- '\ operator [Visual Basic]'
- integer quotient
- math operators [Visual Basic]
- quotients, integer
- truncation [Visual Basic], integer division
ms.assetid: 4b0ee347-950c-45c9-8e23-54bc85df208e
ms.openlocfilehash: d1a46f99c21be007d33361ba095a3f0c52fe906c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701149"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="bb5c1-102">\ – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb5c1-102">\ Operator (Visual Basic)</span></span>
<span data-ttu-id="bb5c1-103">Vydělí dvě čísla a vrátí celočíselný výsledek.</span><span class="sxs-lookup"><span data-stu-id="bb5c1-103">Divides two numbers and returns an integer result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb5c1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb5c1-104">Syntax</span></span>  
  
```vb  
expression1 \ expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="bb5c1-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="bb5c1-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="bb5c1-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="bb5c1-106">Required.</span></span> <span data-ttu-id="bb5c1-107">Libovolný číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="bb5c1-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="bb5c1-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="bb5c1-108">Required.</span></span> <span data-ttu-id="bb5c1-109">Libovolný číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="bb5c1-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="bb5c1-110">Podporované typy</span><span class="sxs-lookup"><span data-stu-id="bb5c1-110">Supported Types</span></span>  
 <span data-ttu-id="bb5c1-111">Všechny číselné typy, včetně typů unsigned a float-Point a `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="bb5c1-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="bb5c1-112">Výsledek</span><span class="sxs-lookup"><span data-stu-id="bb5c1-112">Result</span></span>  
 <span data-ttu-id="bb5c1-113">Výsledkem je celočíselná hodnota `expression1` dělená `expression2`, která zahodí všechny zbývající a uchová pouze celočíselnou část.</span><span class="sxs-lookup"><span data-stu-id="bb5c1-113">The result is the integer quotient of `expression1` divided by `expression2`, which discards any remainder and retains only the integer portion.</span></span> <span data-ttu-id="bb5c1-114">Toto se říká *zkrácení*.</span><span class="sxs-lookup"><span data-stu-id="bb5c1-114">This is known as *truncation*.</span></span>  
  
 <span data-ttu-id="bb5c1-115">Výsledný datový typ je číselný typ, který je vhodný pro datové typy `expression1` a `expression2`.</span><span class="sxs-lookup"><span data-stu-id="bb5c1-115">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="bb5c1-116">Podívejte se na tabulky "celočíselné aritmetické" v [datových typech výsledků operátoru](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="bb5c1-116">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
 <span data-ttu-id="bb5c1-117">[Operátor/(Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) vrátí úplný podíl, který zachová zbytek ve zlomkové části.</span><span class="sxs-lookup"><span data-stu-id="bb5c1-117">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) returns the full quotient, which retains the remainder in the fractional portion.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb5c1-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bb5c1-118">Remarks</span></span>  
 <span data-ttu-id="bb5c1-119">Před provedením dělení Visual Basic pokusí převést libovolný číselný výraz s plovoucí desetinnou čárkou na `Long`.</span><span class="sxs-lookup"><span data-stu-id="bb5c1-119">Before performing the division, Visual Basic attempts to convert any floating-point numeric expression to `Long`.</span></span> <span data-ttu-id="bb5c1-120">Pokud je `Option Strict` `On`, dojde k chybě kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="bb5c1-120">If `Option Strict` is `On`, a compiler error occurs.</span></span> <span data-ttu-id="bb5c1-121">Pokud je `Option Strict` `Off`, je <xref:System.OverflowException> možné, pokud je hodnota mimo rozsah [dlouhého datového typu](../../../visual-basic/language-reference/data-types/long-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="bb5c1-121">If `Option Strict` is `Off`, an <xref:System.OverflowException> is possible if the value is outside the range of the [Long Data Type](../../../visual-basic/language-reference/data-types/long-data-type.md).</span></span> <span data-ttu-id="bb5c1-122">Převod na `Long` je také předmětem *zaokrouhlování bank*.</span><span class="sxs-lookup"><span data-stu-id="bb5c1-122">The conversion to `Long` is also subject to *banker's rounding*.</span></span> <span data-ttu-id="bb5c1-123">Další informace naleznete v části "zlomkové části" v tématu [funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="bb5c1-123">For more information, see "Fractional Parts" in [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="bb5c1-124">Pokud je hodnota `expression1` nebo `expression2` vyhodnocena jako [žádná](../../../visual-basic/language-reference/nothing.md), bude považována za nulu.</span><span class="sxs-lookup"><span data-stu-id="bb5c1-124">If `expression1` or `expression2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="bb5c1-125">Došlo k pokusu o dělení nulou.</span><span class="sxs-lookup"><span data-stu-id="bb5c1-125">Attempted Division by Zero</span></span>  
 <span data-ttu-id="bb5c1-126">Pokud je hodnota `expression2` vyhodnocena jako nula, operátor `\` vyvolá výjimku <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="bb5c1-126">If `expression2` evaluates to zero, the `\` operator throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="bb5c1-127">To platí pro všechny číselné datové typy operandů.</span><span class="sxs-lookup"><span data-stu-id="bb5c1-127">This is true for all numeric data types of the operands.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bb5c1-128">Operátor `\` lze přetížit, což znamená, že třída nebo struktura může předefinovat *chování, pokud*operand má typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="bb5c1-128">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="bb5c1-129">Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="bb5c1-129">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="bb5c1-130">Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="bb5c1-130">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb5c1-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="bb5c1-131">Example</span></span>  
 <span data-ttu-id="bb5c1-132">Následující příklad používá operátor `\` k provedení dělení celého čísla.</span><span class="sxs-lookup"><span data-stu-id="bb5c1-132">The following example uses the `\` operator to perform integer division.</span></span> <span data-ttu-id="bb5c1-133">Výsledkem je celé číslo, které představuje celočíselný podíl dvou operandů a zbytek byl zahozen.</span><span class="sxs-lookup"><span data-stu-id="bb5c1-133">The result is an integer that represents the integer quotient of the two operands, with the remainder discarded.</span></span>  
  
 [!code-vb[VbVbalrOperators#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#18)]  
  
 <span data-ttu-id="bb5c1-134">Výrazy v předchozím příkladu vrací hodnoty 2, 3, 33 a-22 v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="bb5c1-134">The expressions in the preceding example return values of 2, 3, 33, and -22, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb5c1-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bb5c1-135">See also</span></span>

- [<span data-ttu-id="bb5c1-136">\\ = – operátor</span><span class="sxs-lookup"><span data-stu-id="bb5c1-136">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [<span data-ttu-id="bb5c1-137">/– Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb5c1-137">/ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [<span data-ttu-id="bb5c1-138">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="bb5c1-138">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="bb5c1-139">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="bb5c1-139">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="bb5c1-140">Priorita operátorů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bb5c1-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="bb5c1-141">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="bb5c1-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="bb5c1-142">Aritmetické operátory v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bb5c1-142">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
