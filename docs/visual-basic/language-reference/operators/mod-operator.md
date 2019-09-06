---
title: Mod – operátor (Visual Basic)
ms.date: 04/24/2018
f1_keywords:
- vb.Mod
helpviewer_keywords:
- remainder (Mod operator)
- division operator [Visual Basic], Mod operator
- modulus operator [Visual Basic], Visual Basic
- Mod operator [Visual Basic]
- operators [Visual Basic], division
- arithmetic operators [Visual Basic], Mod
- math operators [Visual Basic]
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
ms.openlocfilehash: dc1e866836bb7420ffe17210b5be7a5e1d4048d0
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374492"
---
# <a name="mod-operator-visual-basic"></a><span data-ttu-id="67306-102">Mod – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="67306-102">Mod operator (Visual Basic)</span></span>

<span data-ttu-id="67306-103">Vydělí dvě čísla a vrátí pouze zbytek.</span><span class="sxs-lookup"><span data-stu-id="67306-103">Divides two numbers and returns only the remainder.</span></span>

## <a name="syntax"></a><span data-ttu-id="67306-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67306-104">Syntax</span></span>

```vb
result = number1 Mod number2
```

## <a name="parts"></a><span data-ttu-id="67306-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="67306-105">Parts</span></span>

`result` \
<span data-ttu-id="67306-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="67306-106">Required.</span></span> <span data-ttu-id="67306-107">Jakákoli číselná proměnná nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="67306-107">Any numeric variable or property.</span></span>

`number1` \
<span data-ttu-id="67306-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="67306-108">Required.</span></span> <span data-ttu-id="67306-109">Libovolný číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="67306-109">Any numeric expression.</span></span>

`number2` \
<span data-ttu-id="67306-110">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="67306-110">Required.</span></span> <span data-ttu-id="67306-111">Libovolný číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="67306-111">Any numeric expression.</span></span>

## <a name="supported-types"></a><span data-ttu-id="67306-112">Podporované typy</span><span class="sxs-lookup"><span data-stu-id="67306-112">Supported types</span></span>

<span data-ttu-id="67306-113">Všechny číselné typy.</span><span class="sxs-lookup"><span data-stu-id="67306-113">All numeric types.</span></span> <span data-ttu-id="67306-114">To zahrnuje typy unsigned a float-Point a `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="67306-114">This includes the unsigned and floating-point types and `Decimal`.</span></span>

## <a name="result"></a><span data-ttu-id="67306-115">Výsledek</span><span class="sxs-lookup"><span data-stu-id="67306-115">Result</span></span>

<span data-ttu-id="67306-116">Výsledek je zbytek po `number1` `number2`dělení.</span><span class="sxs-lookup"><span data-stu-id="67306-116">The result is the remainder after `number1` is divided by `number2`.</span></span> <span data-ttu-id="67306-117">Například výraz `14 Mod 4` se vyhodnotí jako 2.</span><span class="sxs-lookup"><span data-stu-id="67306-117">For example, the expression `14 Mod 4` evaluates to 2.</span></span>

> [!NOTE]
> <span data-ttu-id="67306-118">Existuje rozdíl mezi *zbytkem* a *modulem* v matematice s různými výsledky pro záporná čísla.</span><span class="sxs-lookup"><span data-stu-id="67306-118">There is a difference between *remainder* and *modulus* in mathematics, with different results for negative numbers.</span></span> <span data-ttu-id="67306-119">Operátor v Visual Basic, operátor .NET Framework `op_Modulus` a podkladová instrukce [rem](<xref:System.Reflection.Emit.OpCodes.Rem>) Il provádí zbývající operaci. `Mod`</span><span class="sxs-lookup"><span data-stu-id="67306-119">The `Mod` operator in Visual Basic, the .NET Framework `op_Modulus` operator, and the underlying [rem](<xref:System.Reflection.Emit.OpCodes.Rem>) IL instruction all perform a remainder operation.</span></span>

<span data-ttu-id="67306-120">Výsledkem `Mod` operace zůstane znaménko dividendy, `number1`, a tak může být kladné nebo záporné.</span><span class="sxs-lookup"><span data-stu-id="67306-120">The result of a `Mod` operation retains the sign of the dividend, `number1`, and so it may be positive or negative.</span></span> <span data-ttu-id="67306-121">Výsledek je vždy v rozsahu (-`number2`, `number2`), exkluzivní.</span><span class="sxs-lookup"><span data-stu-id="67306-121">The result is always in the range (-`number2`, `number2`), exclusive.</span></span> <span data-ttu-id="67306-122">Příklad:</span><span class="sxs-lookup"><span data-stu-id="67306-122">For example:</span></span>

```vb
Public Module Example
   Public Sub Main()
      Console.WriteLine($" 8 Mod  3 = {8 Mod 3}")
      Console.WriteLine($"-8 Mod  3 = {-8 Mod 3}")
      Console.WriteLine($" 8 Mod -3 = {8 Mod -3}")
      Console.WriteLine($"-8 Mod -3 = {-8 Mod -3}")
   End Sub
End Module
' The example displays the following output:
'       8 Mod  3 = 2
'      -8 Mod  3 = -2
'       8 Mod -3 = 2
'      -8 Mod -3 = -2
```

## <a name="remarks"></a><span data-ttu-id="67306-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="67306-123">Remarks</span></span>

<span data-ttu-id="67306-124">Pokud buď `number1` nebo `number2` je hodnota s plovoucí desetinnou čárkou, vrátí zbytek dělení plovoucí desetinné čárky.</span><span class="sxs-lookup"><span data-stu-id="67306-124">If either `number1` or `number2` is a floating-point value, the floating-point remainder of the division is returned.</span></span> <span data-ttu-id="67306-125">Datový typ výsledku je nejmenší datový typ, který může uchovávat všechny možné hodnoty, které jsou výsledkem dělení s datovými typy `number1` a. `number2`</span><span class="sxs-lookup"><span data-stu-id="67306-125">The data type of the result is the smallest data type that can hold all possible values that result from division with the data types of `number1` and `number2`.</span></span>

<span data-ttu-id="67306-126">Pokud `number1` je `number2` nebo se vyhodnotí jako [Nothing](../../../visual-basic/language-reference/nothing.md), bude se zacházet jako nula.</span><span class="sxs-lookup"><span data-stu-id="67306-126">If `number1` or `number2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>

<span data-ttu-id="67306-127">Mezi související operátory patří následující:</span><span class="sxs-lookup"><span data-stu-id="67306-127">Related operators include the following:</span></span>

- <span data-ttu-id="67306-128">[Operátor \ (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) vrátí celočíselnou podíl dělení.</span><span class="sxs-lookup"><span data-stu-id="67306-128">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient of a division.</span></span> <span data-ttu-id="67306-129">Například výraz `14 \ 4` se vyhodnotí jako 3.</span><span class="sxs-lookup"><span data-stu-id="67306-129">For example, the expression `14 \ 4` evaluates to 3.</span></span>

- <span data-ttu-id="67306-130">[Operátor/(Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) vrátí úplný podíl včetně zbytku jako čísla s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="67306-130">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) returns the full quotient, including the remainder, as a floating-point number.</span></span> <span data-ttu-id="67306-131">Například výraz `14 / 4` se vyhodnotí jako 3,5.</span><span class="sxs-lookup"><span data-stu-id="67306-131">For example, the expression `14 / 4` evaluates to 3.5.</span></span>

## <a name="attempted-division-by-zero"></a><span data-ttu-id="67306-132">Došlo k pokusu o dělení nulou.</span><span class="sxs-lookup"><span data-stu-id="67306-132">Attempted division by zero</span></span>

<span data-ttu-id="67306-133">Pokud `number2` je hodnota vyhodnocena jako nula, chování `Mod` operátoru závisí na datovém typu operandů:</span><span class="sxs-lookup"><span data-stu-id="67306-133">If `number2` evaluates to zero, the behavior of the `Mod` operator depends on the data type of the operands:</span></span>
- <span data-ttu-id="67306-134">Celočíselné dělení vyvolá <xref:System.DivideByZeroException> výjimku, pokud `number2` nelze určit v době kompilace a generuje chybu `BC30542 Division by zero occurred while evaluating this expression` při kompilaci, pokud `number2` je v době kompilace vyhodnocena jako nula.</span><span class="sxs-lookup"><span data-stu-id="67306-134">An integral division throws a <xref:System.DivideByZeroException> exception if `number2` cannot be determined in compile-time and generates a compile-time error `BC30542 Division by zero occurred while evaluating this expression` if `number2` is evaluated to zero at compile-time.</span></span>
- <span data-ttu-id="67306-135">Dělení s plovoucí desetinnou čárkou se vrátí <xref:System.Double.NaN?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="67306-135">A floating-point division returns <xref:System.Double.NaN?displayProperty=nameWithType>.</span></span>

## <a name="equivalent-formula"></a><span data-ttu-id="67306-136">Ekvivalentní vzorec</span><span class="sxs-lookup"><span data-stu-id="67306-136">Equivalent formula</span></span>

<span data-ttu-id="67306-137">Výraz `a Mod b` je ekvivalentem některého z následujících vzorců:</span><span class="sxs-lookup"><span data-stu-id="67306-137">The expression `a Mod b` is equivalent to either of the following formulas:</span></span>

`a - (b * (a \ b))`

`a - (b * Fix(a / b))`

## <a name="floating-point-imprecision"></a><span data-ttu-id="67306-138">Nepřesnost plovoucí desetinné čárky</span><span class="sxs-lookup"><span data-stu-id="67306-138">Floating-point imprecision</span></span>

<span data-ttu-id="67306-139">Když pracujete s čísly s plovoucí desetinnou čárkou, mějte na paměti, že v paměti nemají vždy přesné desetinné vyjádření.</span><span class="sxs-lookup"><span data-stu-id="67306-139">When you work with floating-point numbers, remember that they do not always have a precise decimal representation in memory.</span></span> <span data-ttu-id="67306-140">To může vést k neočekávaným výsledkům z určitých operací, jako je například `Mod` porovnání hodnot a operátor.</span><span class="sxs-lookup"><span data-stu-id="67306-140">This can lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="67306-141">Další informace najdete v tématu [řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="67306-141">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

## <a name="overloading"></a><span data-ttu-id="67306-142">Přetížení</span><span class="sxs-lookup"><span data-stu-id="67306-142">Overloading</span></span>

<span data-ttu-id="67306-143">Operátor může být přetížen, což znamená, že třída nebo struktura může změnit své chování. `Mod`</span><span class="sxs-lookup"><span data-stu-id="67306-143">The `Mod` operator can be *overloaded*, which means that a class or structure can redefine its behavior.</span></span> <span data-ttu-id="67306-144">Pokud se váš kód `Mod` vztahuje na instanci třídy nebo struktury, která obsahuje takové přetížení, ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="67306-144">If your code applies `Mod` to an instance of a class or structure that includes such an overload, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="67306-145">Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="67306-145">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="example"></a><span data-ttu-id="67306-146">Příklad</span><span class="sxs-lookup"><span data-stu-id="67306-146">Example</span></span>

<span data-ttu-id="67306-147">Následující příklad používá `Mod` operátor k rozdělení dvou čísel a vrácení pouze zbytku.</span><span class="sxs-lookup"><span data-stu-id="67306-147">The following example uses the `Mod` operator to divide two numbers and return only the remainder.</span></span> <span data-ttu-id="67306-148">Pokud je jedno číslo číslo s plovoucí desetinnou čárkou, výsledkem je číslo s plovoucí desetinnou čárkou, které představuje zbytek.</span><span class="sxs-lookup"><span data-stu-id="67306-148">If either number is a floating-point number, the result is a floating-point number that represents the remainder.</span></span>

[!code-vb[VbVbalrOperators#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#31)]

## <a name="example"></a><span data-ttu-id="67306-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="67306-149">Example</span></span>

<span data-ttu-id="67306-150">Následující příklad ukazuje potenciální nepřesnost operandů s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="67306-150">The following example demonstrates the potential imprecision of floating-point operands.</span></span> <span data-ttu-id="67306-151">V prvním příkazu jsou `Double`operandy a 0,2 nekonečně opakující se binární zlomek s uloženou hodnotou 0.20000000000000001.</span><span class="sxs-lookup"><span data-stu-id="67306-151">In the first statement, the operands are `Double`, and 0.2 is an infinitely repeating binary fraction with a stored value of 0.20000000000000001.</span></span> <span data-ttu-id="67306-152">Ve druhém příkazu vynucuje znak `D` typu literálu oba operandy `Decimal`a 0,2 má přesnou reprezentaci.</span><span class="sxs-lookup"><span data-stu-id="67306-152">In the second statement, the literal type character `D` forces both operands to `Decimal`, and 0.2 has a precise representation.</span></span>

[!code-vb[VbVbalrOperators#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#32)]

## <a name="see-also"></a><span data-ttu-id="67306-153">Viz také:</span><span class="sxs-lookup"><span data-stu-id="67306-153">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- [<span data-ttu-id="67306-154">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="67306-154">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="67306-155">Priorita operátorů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="67306-155">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="67306-156">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="67306-156">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="67306-157">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="67306-157">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="67306-158">Aritmetické operátory v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="67306-158">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="67306-159">\ – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="67306-159">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
