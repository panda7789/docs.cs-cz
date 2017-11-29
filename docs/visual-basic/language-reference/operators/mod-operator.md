---
title: "Mod – operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Mod
helpviewer_keywords:
- remainder (Mod operator)
- division operator [Visual Basic], Mod operator
- modulus operator [Visual Basic], Visual Basic
- Mod operator [Visual Basic]
- operators [Visual Basic], division
- arithmetic operators [Visual Basic], Mod
- math operators [Visual Basic]
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5464b57c993e5703c09529b527a7bc714e045870
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="mod-operator-visual-basic"></a><span data-ttu-id="23eb3-102">Mod – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23eb3-102">Mod Operator (Visual Basic)</span></span>
<span data-ttu-id="23eb3-103">Provede podíl dvou čísel a vrátí pouze zbytek.</span><span class="sxs-lookup"><span data-stu-id="23eb3-103">Divides two numbers and returns only the remainder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23eb3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23eb3-104">Syntax</span></span>  
  
```  
number1 Mod number2  
```  
  
## <a name="parts"></a><span data-ttu-id="23eb3-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="23eb3-105">Parts</span></span>  
 `number1`  
 <span data-ttu-id="23eb3-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="23eb3-106">Required.</span></span> <span data-ttu-id="23eb3-107">Jakýkoli číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="23eb3-107">Any numeric expression.</span></span>  
  
 `number2`  
 <span data-ttu-id="23eb3-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="23eb3-108">Required.</span></span> <span data-ttu-id="23eb3-109">Jakýkoli číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="23eb3-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="23eb3-110">Podporované typy</span><span class="sxs-lookup"><span data-stu-id="23eb3-110">Supported Types</span></span>  
 <span data-ttu-id="23eb3-111">Všechny číselné typy.</span><span class="sxs-lookup"><span data-stu-id="23eb3-111">All numeric types.</span></span> <span data-ttu-id="23eb3-112">To zahrnuje typy bez znaménka a s plovoucí desetinnou čárkou a `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="23eb3-112">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="23eb3-113">Výsledek</span><span class="sxs-lookup"><span data-stu-id="23eb3-113">Result</span></span>  
 <span data-ttu-id="23eb3-114">Výsledkem je zbývající po `number1` dělení `number2`.</span><span class="sxs-lookup"><span data-stu-id="23eb3-114">The result is the remainder after `number1` is divided by `number2`.</span></span> <span data-ttu-id="23eb3-115">Například výraz `14 Mod 4` vyhodnotí 2.</span><span class="sxs-lookup"><span data-stu-id="23eb3-115">For example, the expression `14 Mod 4` evaluates to 2.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23eb3-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="23eb3-116">Remarks</span></span>  
 <span data-ttu-id="23eb3-117">Pokud má jedna `number1` nebo `number2` je hodnota s plovoucí desetinnou čárkou se vrátí zbytek divizi s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="23eb3-117">If either `number1` or `number2` is a floating-point value, the floating-point remainder of the division is returned.</span></span> <span data-ttu-id="23eb3-118">Datový typ výsledku je nejmenší datový typ, který může obsahovat všechny možné hodnoty, které jsou výsledkem dělení s typy dat `number1` a `number2`.</span><span class="sxs-lookup"><span data-stu-id="23eb3-118">The data type of the result is the smallest data type that can hold all possible values that result from division with the data types of `number1` and `number2`.</span></span>  
  
 <span data-ttu-id="23eb3-119">Pokud `number1` nebo `number2` vyhodnotí jako [nic](../../../visual-basic/language-reference/nothing.md), je považován za nula.</span><span class="sxs-lookup"><span data-stu-id="23eb3-119">If `number1` or `number2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
 <span data-ttu-id="23eb3-120">Související operátory zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="23eb3-120">Related operators include the following:</span></span>  
  
-   <span data-ttu-id="23eb3-121">[\ – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) vrátí celočíselný koeficient dělení.</span><span class="sxs-lookup"><span data-stu-id="23eb3-121">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient of a division.</span></span> <span data-ttu-id="23eb3-122">Například výraz `14 \ 4` vyhodnocen jako 3.</span><span class="sxs-lookup"><span data-stu-id="23eb3-122">For example, the expression `14 \ 4` evaluates to 3.</span></span>  
  
-   <span data-ttu-id="23eb3-123">[/ – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) vrátí úplné podílu, včetně zbývající, jako číslo s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="23eb3-123">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) returns the full quotient, including the remainder, as a floating-point number.</span></span> <span data-ttu-id="23eb3-124">Například výraz `14 / 4` vyhodnocuje 3.5.</span><span class="sxs-lookup"><span data-stu-id="23eb3-124">For example, the expression `14 / 4` evaluates to 3.5.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="23eb3-125">Pokus o dělení nulou</span><span class="sxs-lookup"><span data-stu-id="23eb3-125">Attempted Division by Zero</span></span>  
 <span data-ttu-id="23eb3-126">Pokud `number2` vyhodnocen jako nula, chování `Mod` operátor závisí na typu dat operandy.</span><span class="sxs-lookup"><span data-stu-id="23eb3-126">If `number2` evaluates to zero, the behavior of the `Mod` operator depends on the data type of the operands.</span></span> <span data-ttu-id="23eb3-127">Vyvolá celočíselné dělení <xref:System.DivideByZeroException> výjimka.</span><span class="sxs-lookup"><span data-stu-id="23eb3-127">An integral division throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="23eb3-128">Vrátí s plovoucí desetinnou čárkou dělení <xref:System.Double.NaN>.</span><span class="sxs-lookup"><span data-stu-id="23eb3-128">A floating-point division returns <xref:System.Double.NaN>.</span></span>  
  
## <a name="equivalent-formula"></a><span data-ttu-id="23eb3-129">Ekvivalentní vzorec</span><span class="sxs-lookup"><span data-stu-id="23eb3-129">Equivalent Formula</span></span>  
 <span data-ttu-id="23eb3-130">Výraz `a Mod b` odpovídá buď následující vzorce:</span><span class="sxs-lookup"><span data-stu-id="23eb3-130">The expression `a Mod b` is equivalent to either of the following formulas:</span></span>  
  
 `a - (b * (a \ b))`  
  
 `a - (b * Fix(a / b))`  
  
## <a name="floating-point-imprecision"></a><span data-ttu-id="23eb3-131">S plovoucí desetinnou čárkou nepřesnosti</span><span class="sxs-lookup"><span data-stu-id="23eb3-131">Floating-Point Imprecision</span></span>  
 <span data-ttu-id="23eb3-132">Při práci s plovoucí desetinnou čárkou, mějte na paměti, že vždy nemají znázornění přesné v paměti.</span><span class="sxs-lookup"><span data-stu-id="23eb3-132">When you work with floating-point numbers, remember that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="23eb3-133">To může vést k neočekávaným výsledkům z určité operace, jako je například porovnání hodnoty a `Mod` operátor.</span><span class="sxs-lookup"><span data-stu-id="23eb3-133">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="23eb3-134">Další informace najdete v tématu [řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="23eb3-134">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="23eb3-135">Přetížení</span><span class="sxs-lookup"><span data-stu-id="23eb3-135">Overloading</span></span>  
 <span data-ttu-id="23eb3-136">`Mod` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování.</span><span class="sxs-lookup"><span data-stu-id="23eb3-136">The `Mod` operator can be *overloaded*, which means that a class or structure can redefine its behavior.</span></span> <span data-ttu-id="23eb3-137">Pokud se váš kód vztahuje `Mod` na instanci třídy nebo struktura, která zahrnuje tyto přetížení se rozumět své Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="23eb3-137">If your code applies `Mod` to an instance of a class or structure that includes such an overload, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="23eb3-138">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="23eb3-138">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="23eb3-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="23eb3-139">Example</span></span>  
 <span data-ttu-id="23eb3-140">Následující příklad používá `Mod` operátor dělení dvou čísel a vrátí pouze zbytek.</span><span class="sxs-lookup"><span data-stu-id="23eb3-140">The following example uses the `Mod` operator to divide two numbers and return only the remainder.</span></span> <span data-ttu-id="23eb3-141">Pokud je buď číslo s plovoucí desetinnou čárkou číslo, výsledkem je číslo s plovoucí desetinnou čárkou, které představuje zbytek.</span><span class="sxs-lookup"><span data-stu-id="23eb3-141">If either number is a floating-point number, the result is a floating-point number that represents the remainder.</span></span>  
  
 [!code-vb[VbVbalrOperators#31](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="23eb3-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="23eb3-142">Example</span></span>  
 <span data-ttu-id="23eb3-143">Následující příklad ukazuje potenciální nepřesnosti operandů s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="23eb3-143">The following example demonstrates the potential imprecision of floating-point operands.</span></span> <span data-ttu-id="23eb3-144">V prvním příkazu, jsou operandy `Double`, a 0,2 nekonečnou opakovaný binární zlomek s hodnotou uloženou 0.20000000000000001.</span><span class="sxs-lookup"><span data-stu-id="23eb3-144">In the first statement, the operands are `Double`, and 0.2 is an infinitely repeating binary fraction with a stored value of 0.20000000000000001.</span></span> <span data-ttu-id="23eb3-145">Literálové druhý příkaz, zadejte znak `D` vynutí oba operandy k `Decimal`, a 0,2 má znázornění přesné.</span><span class="sxs-lookup"><span data-stu-id="23eb3-145">In the second statement, the literal type character `D` forces both operands to `Decimal`, and 0.2 has a precise representation.</span></span>  
  
 [!code-vb[VbVbalrOperators#32](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="23eb3-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="23eb3-146">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>  
 [<span data-ttu-id="23eb3-147">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="23eb3-147">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="23eb3-148">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="23eb3-148">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="23eb3-149">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="23eb3-149">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="23eb3-150">Řešení potíží s datové typy</span><span class="sxs-lookup"><span data-stu-id="23eb3-150">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="23eb3-151">Aritmetické operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="23eb3-151">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="23eb3-152">\ – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23eb3-152">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
