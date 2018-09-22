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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 456c19fc8e28517a0662b58e338028e1c75cd8c8
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46697682"
---
# <a name="mod-operator-visual-basic"></a><span data-ttu-id="4c1c8-102">Mod – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c1c8-102">Mod operator (Visual Basic)</span></span>
<span data-ttu-id="4c1c8-103">Provede podíl dvou čísel a vrátí pouze zbytek.</span><span class="sxs-lookup"><span data-stu-id="4c1c8-103">Divides two numbers and returns only the remainder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c1c8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c1c8-104">Syntax</span></span>  
  
```  
number1 Mod number2  
```  
  
## <a name="parts"></a><span data-ttu-id="4c1c8-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="4c1c8-105">Parts</span></span>  
 `number1`  
 <span data-ttu-id="4c1c8-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="4c1c8-106">Required.</span></span> <span data-ttu-id="4c1c8-107">Jakýkoli číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="4c1c8-107">Any numeric expression.</span></span>  
  
 `number2`  
 <span data-ttu-id="4c1c8-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="4c1c8-108">Required.</span></span> <span data-ttu-id="4c1c8-109">Jakýkoli číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="4c1c8-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="4c1c8-110">Podporované typy</span><span class="sxs-lookup"><span data-stu-id="4c1c8-110">Supported types</span></span>  
 <span data-ttu-id="4c1c8-111">Všechny číselné typy.</span><span class="sxs-lookup"><span data-stu-id="4c1c8-111">All numeric types.</span></span> <span data-ttu-id="4c1c8-112">Jedná se o typy bez znaménka a s plovoucí desetinnou čárkou a `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="4c1c8-112">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="4c1c8-113">Výsledek</span><span class="sxs-lookup"><span data-stu-id="4c1c8-113">Result</span></span>

<span data-ttu-id="4c1c8-114">Výsledkem je zbytek po `number1` , je vyděleno hodnotou `number2`.</span><span class="sxs-lookup"><span data-stu-id="4c1c8-114">The result is the remainder after `number1` is divided by `number2`.</span></span> <span data-ttu-id="4c1c8-115">Například výraz `14 Mod 4` vyhodnotí na 2.</span><span class="sxs-lookup"><span data-stu-id="4c1c8-115">For example, the expression `14 Mod 4` evaluates to 2.</span></span>  

> [!NOTE]
> <span data-ttu-id="4c1c8-116">Existuje rozdíl mezi *zbývající* a *numerického zbytku* v matematice se různé výsledky pro záporná čísla.</span><span class="sxs-lookup"><span data-stu-id="4c1c8-116">There is a difference between *remainder* and *modulus* in mathematics, with different results for negative numbers.</span></span> <span data-ttu-id="4c1c8-117">`Mod` Operátor v jazyce Visual Basic, rozhraní .NET Framework `op_Modulus` operátor a základní [rem](<xref:System.Reflection.Emit.OpCodes.Rem>) provádět všechny operace remainder instrukce IL.</span><span class="sxs-lookup"><span data-stu-id="4c1c8-117">The `Mod` operator in Visual Basic, the .NET Framework `op_Modulus` operator, and the underlying [rem](<xref:System.Reflection.Emit.OpCodes.Rem>) IL instruction all perform a remainder operation.</span></span>

<span data-ttu-id="4c1c8-118">Výsledek `Mod` operace uchovává znaménko podíl, `number1`, a proto může být pozitivní nebo negativní.</span><span class="sxs-lookup"><span data-stu-id="4c1c8-118">The result of a `Mod` operation retains the sign of the dividend, `number1`, and so it may be positive or negative.</span></span> <span data-ttu-id="4c1c8-119">Výsledek je vždycky v rozsahu (-`number2`, `number2`) exkluzivní.</span><span class="sxs-lookup"><span data-stu-id="4c1c8-119">The result is always in the range (-`number2`, `number2`), exclusive.</span></span> <span data-ttu-id="4c1c8-120">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4c1c8-120">For example:</span></span>

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

## <a name="remarks"></a><span data-ttu-id="4c1c8-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4c1c8-121">Remarks</span></span>  
 <span data-ttu-id="4c1c8-122">Pokud `number1` nebo `number2` je hodnotu s plovoucí desetinnou čárkou se vrátí zbytek s plovoucí desetinnou čárkou dělení.</span><span class="sxs-lookup"><span data-stu-id="4c1c8-122">If either `number1` or `number2` is a floating-point value, the floating-point remainder of the division is returned.</span></span> <span data-ttu-id="4c1c8-123">Datový typ výsledku je nejmenší datový typ, který může uchovat všechny možné hodnoty, které jsou výsledkem dělení s datové typy `number1` a `number2`.</span><span class="sxs-lookup"><span data-stu-id="4c1c8-123">The data type of the result is the smallest data type that can hold all possible values that result from division with the data types of `number1` and `number2`.</span></span>  
  
 <span data-ttu-id="4c1c8-124">Pokud `number1` nebo `number2` vyhodnotí jako [nic](../../../visual-basic/language-reference/nothing.md), je považován za nulu.</span><span class="sxs-lookup"><span data-stu-id="4c1c8-124">If `number1` or `number2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
 <span data-ttu-id="4c1c8-125">Související operátory patří:</span><span class="sxs-lookup"><span data-stu-id="4c1c8-125">Related operators include the following:</span></span>  
  
-   <span data-ttu-id="4c1c8-126">[\ – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) vrátí podíl dělení celého čísla.</span><span class="sxs-lookup"><span data-stu-id="4c1c8-126">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient of a division.</span></span> <span data-ttu-id="4c1c8-127">Například výraz `14 \ 4` vyhodnocen jako 3.</span><span class="sxs-lookup"><span data-stu-id="4c1c8-127">For example, the expression `14 \ 4` evaluates to 3.</span></span>  
  
-   <span data-ttu-id="4c1c8-128">[/ – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) vrátí úplné podíl, včetně zbývající jako číslo s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="4c1c8-128">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) returns the full quotient, including the remainder, as a floating-point number.</span></span> <span data-ttu-id="4c1c8-129">Například výraz `14 / 4` vyhodnocen jako 3.5.</span><span class="sxs-lookup"><span data-stu-id="4c1c8-129">For example, the expression `14 / 4` evaluates to 3.5.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="4c1c8-130">Pokus o dělení nulou</span><span class="sxs-lookup"><span data-stu-id="4c1c8-130">Attempted division by zero</span></span>  
 <span data-ttu-id="4c1c8-131">Pokud `number2` vyhodnocen jako nula, chování `Mod` operátor závisí na datový typ operandu.</span><span class="sxs-lookup"><span data-stu-id="4c1c8-131">If `number2` evaluates to zero, the behavior of the `Mod` operator depends on the data type of the operands.</span></span> <span data-ttu-id="4c1c8-132">Vyvolá celočíselného dělení <xref:System.DivideByZeroException> výjimky.</span><span class="sxs-lookup"><span data-stu-id="4c1c8-132">An integral division throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="4c1c8-133">Vrátí hodnotu s plovoucí desetinnou čárkou dělení <xref:System.Double.NaN>.</span><span class="sxs-lookup"><span data-stu-id="4c1c8-133">A floating-point division returns <xref:System.Double.NaN>.</span></span>  
  
## <a name="equivalent-formula"></a><span data-ttu-id="4c1c8-134">Ekvivalentní vzorce</span><span class="sxs-lookup"><span data-stu-id="4c1c8-134">Equivalent formula</span></span>  
 <span data-ttu-id="4c1c8-135">Výraz `a Mod b` odpovídá některé z těchto vzorců:</span><span class="sxs-lookup"><span data-stu-id="4c1c8-135">The expression `a Mod b` is equivalent to either of the following formulas:</span></span>  
  
 `a - (b * (a \ b))`  
  
 `a - (b * Fix(a / b))`  
  
## <a name="floating-point-imprecision"></a><span data-ttu-id="4c1c8-136">S plovoucí desetinnou čárkou nepřesnost</span><span class="sxs-lookup"><span data-stu-id="4c1c8-136">Floating-point imprecision</span></span>  
 <span data-ttu-id="4c1c8-137">Při práci s čísly s plovoucí desetinnou čárkou, mějte na paměti, že vždy nemají reprezentaci přesné desítkové v paměti.</span><span class="sxs-lookup"><span data-stu-id="4c1c8-137">When you work with floating-point numbers, remember that they do not always have a precise decimal representation in memory.</span></span> <span data-ttu-id="4c1c8-138">To může vést k neočekávaným výsledkům z určité operace, jako je například porovnání hodnoty a `Mod` operátor.</span><span class="sxs-lookup"><span data-stu-id="4c1c8-138">This can lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="4c1c8-139">Další informace najdete v tématu [řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="4c1c8-139">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="4c1c8-140">Přetížení</span><span class="sxs-lookup"><span data-stu-id="4c1c8-140">Overloading</span></span>  
 <span data-ttu-id="4c1c8-141">`Mod` Operátor může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování.</span><span class="sxs-lookup"><span data-stu-id="4c1c8-141">The `Mod` operator can be *overloaded*, which means that a class or structure can redefine its behavior.</span></span> <span data-ttu-id="4c1c8-142">Pokud se váš kód vztahuje `Mod` být do instance třídy nebo struktury, která obsahuje tato přetížení, že rozumíte jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="4c1c8-142">If your code applies `Mod` to an instance of a class or structure that includes such an overload, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="4c1c8-143">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="4c1c8-143">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c1c8-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="4c1c8-144">Example</span></span>  
 <span data-ttu-id="4c1c8-145">V následujícím příkladu `Mod` operátor dělení dvou čísel a vrátí pouze zbytek.</span><span class="sxs-lookup"><span data-stu-id="4c1c8-145">The following example uses the `Mod` operator to divide two numbers and return only the remainder.</span></span> <span data-ttu-id="4c1c8-146">Pokud je buď číslo s plovoucí desetinnou čárkou číslo, výsledkem je číslo s plovoucí desetinnou čárkou, které představuje zbytek.</span><span class="sxs-lookup"><span data-stu-id="4c1c8-146">If either number is a floating-point number, the result is a floating-point number that represents the remainder.</span></span>  
  
 [!code-vb[VbVbalrOperators#31](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="4c1c8-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="4c1c8-147">Example</span></span>  
 <span data-ttu-id="4c1c8-148">Následující příklad ukazuje potenciál nepřesnost operandů s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="4c1c8-148">The following example demonstrates the potential imprecision of floating-point operands.</span></span> <span data-ttu-id="4c1c8-149">V prvním příkazu, jsou jako operandy `Double`, a 0.2 je neomezeně opakovaný binární zlomek s hodnotou uloženou v 0.20000000000000001.</span><span class="sxs-lookup"><span data-stu-id="4c1c8-149">In the first statement, the operands are `Double`, and 0.2 is an infinitely repeating binary fraction with a stored value of 0.20000000000000001.</span></span> <span data-ttu-id="4c1c8-150">V druhém příkazu znak typu literálu `D` vynutí oba operandy `Decimal`, a 0.2 má přesné reprezentaci.</span><span class="sxs-lookup"><span data-stu-id="4c1c8-150">In the second statement, the literal type character `D` forces both operands to `Decimal`, and 0.2 has a precise representation.</span></span>  
  
 [!code-vb[VbVbalrOperators#32](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4c1c8-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4c1c8-151">See also</span></span>  
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>  
 [<span data-ttu-id="4c1c8-152">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="4c1c8-152">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="4c1c8-153">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4c1c8-153">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="4c1c8-154">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="4c1c8-154">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="4c1c8-155">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="4c1c8-155">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="4c1c8-156">Aritmetické operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4c1c8-156">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="4c1c8-157">\ – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c1c8-157">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
