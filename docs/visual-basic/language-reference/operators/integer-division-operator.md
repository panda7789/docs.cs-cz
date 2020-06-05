---
title: '\ – operátor'
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
ms.openlocfilehash: 1f8095afc5f096928b946607adc715af49827022
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370879"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="ab267-102">\ – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab267-102">\ Operator (Visual Basic)</span></span>
<span data-ttu-id="ab267-103">Vydělí dvě čísla a vrátí celočíselný výsledek.</span><span class="sxs-lookup"><span data-stu-id="ab267-103">Divides two numbers and returns an integer result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab267-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab267-104">Syntax</span></span>  
  
```vb  
expression1 \ expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="ab267-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="ab267-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="ab267-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="ab267-106">Required.</span></span> <span data-ttu-id="ab267-107">Libovolný číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="ab267-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="ab267-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="ab267-108">Required.</span></span> <span data-ttu-id="ab267-109">Libovolný číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="ab267-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="ab267-110">Podporované typy</span><span class="sxs-lookup"><span data-stu-id="ab267-110">Supported Types</span></span>  
 <span data-ttu-id="ab267-111">Všechny číselné typy, včetně typů unsigned a float-Point a `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="ab267-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="ab267-112">Výsledek</span><span class="sxs-lookup"><span data-stu-id="ab267-112">Result</span></span>  
 <span data-ttu-id="ab267-113">Výsledkem je celočíselný podíl `expression1` dělený pomocí `expression2` , který zahodí všechny zbývající a uchová pouze celočíselnou část.</span><span class="sxs-lookup"><span data-stu-id="ab267-113">The result is the integer quotient of `expression1` divided by `expression2`, which discards any remainder and retains only the integer portion.</span></span> <span data-ttu-id="ab267-114">Toto se říká *zkrácení*.</span><span class="sxs-lookup"><span data-stu-id="ab267-114">This is known as *truncation*.</span></span>  
  
 <span data-ttu-id="ab267-115">Výsledný datový typ je číselný typ odpovídající datovým typům `expression1` a `expression2` .</span><span class="sxs-lookup"><span data-stu-id="ab267-115">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="ab267-116">Podívejte se na tabulky "celočíselné aritmetické" v [datových typech výsledků operátoru](data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="ab267-116">See the "Integer Arithmetic" tables in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>  
  
 <span data-ttu-id="ab267-117">[Operátor/(Visual Basic)](floating-point-division-operator.md) vrátí úplný podíl, který zachová zbytek ve zlomkové části.</span><span class="sxs-lookup"><span data-stu-id="ab267-117">The [/ Operator (Visual Basic)](floating-point-division-operator.md) returns the full quotient, which retains the remainder in the fractional portion.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab267-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ab267-118">Remarks</span></span>  
 <span data-ttu-id="ab267-119">Před provedením dělení Visual Basic pokusy o převod libovolného číselného výrazu s plovoucí desetinnou čárkou na `Long` .</span><span class="sxs-lookup"><span data-stu-id="ab267-119">Before performing the division, Visual Basic attempts to convert any floating-point numeric expression to `Long`.</span></span> <span data-ttu-id="ab267-120">V `Option Strict` `On` takovém případě dojde k chybě kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="ab267-120">If `Option Strict` is `On`, a compiler error occurs.</span></span> <span data-ttu-id="ab267-121">Pokud `Option Strict` je `Off` , je možné, že je <xref:System.OverflowException> hodnota mimo rozsah [dlouhého datového typu](../data-types/long-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="ab267-121">If `Option Strict` is `Off`, an <xref:System.OverflowException> is possible if the value is outside the range of the [Long Data Type](../data-types/long-data-type.md).</span></span> <span data-ttu-id="ab267-122">Převod na `Long` je také předmětem *zaokrouhlování bank*.</span><span class="sxs-lookup"><span data-stu-id="ab267-122">The conversion to `Long` is also subject to *banker's rounding*.</span></span> <span data-ttu-id="ab267-123">Další informace naleznete v části "zlomkové části" v tématu [funkce pro převod typů](../functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="ab267-123">For more information, see "Fractional Parts" in [Type Conversion Functions](../functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="ab267-124">Pokud `expression1` je nebo se `expression2` vyhodnotí jako [Nothing](../nothing.md), bude se zacházet jako nula.</span><span class="sxs-lookup"><span data-stu-id="ab267-124">If `expression1` or `expression2` evaluates to [Nothing](../nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="ab267-125">Došlo k pokusu o dělení nulou.</span><span class="sxs-lookup"><span data-stu-id="ab267-125">Attempted Division by Zero</span></span>  
 <span data-ttu-id="ab267-126">Pokud je `expression2` hodnota vyhodnocena jako nula, `\` operátor vyvolá <xref:System.DivideByZeroException> výjimku.</span><span class="sxs-lookup"><span data-stu-id="ab267-126">If `expression2` evaluates to zero, the `\` operator throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="ab267-127">To platí pro všechny číselné datové typy operandů.</span><span class="sxs-lookup"><span data-stu-id="ab267-127">This is true for all numeric data types of the operands.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ab267-128">`\`Operátor může být *přetížen*, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="ab267-128">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="ab267-129">Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="ab267-129">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="ab267-130">Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="ab267-130">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab267-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="ab267-131">Example</span></span>  
 <span data-ttu-id="ab267-132">Následující příklad používá `\` operátor k provedení dělení celého čísla.</span><span class="sxs-lookup"><span data-stu-id="ab267-132">The following example uses the `\` operator to perform integer division.</span></span> <span data-ttu-id="ab267-133">Výsledkem je celé číslo, které představuje celočíselný podíl dvou operandů a zbytek byl zahozen.</span><span class="sxs-lookup"><span data-stu-id="ab267-133">The result is an integer that represents the integer quotient of the two operands, with the remainder discarded.</span></span>  
  
 [!code-vb[VbVbalrOperators#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#18)]  
  
 <span data-ttu-id="ab267-134">Výrazy v předchozím příkladu vrací hodnoty 2, 3, 33 a-22 v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ab267-134">The expressions in the preceding example return values of 2, 3, 33, and -22, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab267-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab267-135">See also</span></span>

- [<span data-ttu-id="ab267-136">\\= – Operátor</span><span class="sxs-lookup"><span data-stu-id="ab267-136">\\= Operator</span></span>](integer-division-assignment-operator.md)
- [<span data-ttu-id="ab267-137">/– Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab267-137">/ Operator (Visual Basic)</span></span>](floating-point-division-operator.md)
- [<span data-ttu-id="ab267-138">Option Strict – příkaz</span><span class="sxs-lookup"><span data-stu-id="ab267-138">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
- [<span data-ttu-id="ab267-139">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="ab267-139">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="ab267-140">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ab267-140">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="ab267-141">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="ab267-141">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="ab267-142">Aritmetické operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ab267-142">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
