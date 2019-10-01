---
title: + – Operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.+
helpviewer_keywords:
- arithmetic operators [Visual Basic], addition
- + operator
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
- sum operator [Visual Basic]
ms.assetid: 5694778f-0a2c-4539-8009-f66f318fb46d
ms.openlocfilehash: 3187551afb7d25470f48dad894188766a811bb0a
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701002"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="0b47c-102">+ – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b47c-102">+ Operator (Visual Basic)</span></span>
<span data-ttu-id="0b47c-103">Přidá dvě čísla nebo vrátí kladnou hodnotu číselného výrazu.</span><span class="sxs-lookup"><span data-stu-id="0b47c-103">Adds two numbers or returns the positive value of a numeric expression.</span></span> <span data-ttu-id="0b47c-104">Lze také použít ke zřetězení dvou řetězcových výrazů.</span><span class="sxs-lookup"><span data-stu-id="0b47c-104">Can also be used to concatenate two string expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b47c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b47c-105">Syntax</span></span>  
  
```vb
expression1 + expression2
```
  
<span data-ttu-id="0b47c-106">or</span><span class="sxs-lookup"><span data-stu-id="0b47c-106">or</span></span>

```vb  
+expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="0b47c-107">Součásti</span><span class="sxs-lookup"><span data-stu-id="0b47c-107">Parts</span></span>  
  
|<span data-ttu-id="0b47c-108">Termín</span><span class="sxs-lookup"><span data-stu-id="0b47c-108">Term</span></span>|<span data-ttu-id="0b47c-109">Definice</span><span class="sxs-lookup"><span data-stu-id="0b47c-109">Definition</span></span>|  
|---|---|  
|`expression1`|<span data-ttu-id="0b47c-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="0b47c-110">Required.</span></span> <span data-ttu-id="0b47c-111">Libovolný numerický nebo řetězcový výraz.</span><span class="sxs-lookup"><span data-stu-id="0b47c-111">Any numeric or string expression.</span></span>|  
|`expression2`|<span data-ttu-id="0b47c-112">Povinné, pokud operátor `+` nepočítá zápornou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0b47c-112">Required unless the `+` operator is calculating a negative value.</span></span> <span data-ttu-id="0b47c-113">Libovolný numerický nebo řetězcový výraz.</span><span class="sxs-lookup"><span data-stu-id="0b47c-113">Any numeric or string expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="0b47c-114">Výsledek</span><span class="sxs-lookup"><span data-stu-id="0b47c-114">Result</span></span>  
 <span data-ttu-id="0b47c-115">Pokud `expression1` a `expression2` jsou číselné, výsledkem je aritmetický součet.</span><span class="sxs-lookup"><span data-stu-id="0b47c-115">If `expression1` and `expression2` are both numeric, the result is their arithmetic sum.</span></span>  
  
 <span data-ttu-id="0b47c-116">Pokud chybí `expression2`, operátor `+` je *unárním* operátorem identity pro nezměněnou hodnotu výrazu.</span><span class="sxs-lookup"><span data-stu-id="0b47c-116">If `expression2` is absent, the `+` operator is the *unary* identity operator for the unchanged value of an expression.</span></span> <span data-ttu-id="0b47c-117">V tomto smyslu se operace skládá z uchování znaménka `expression1`, takže výsledek je negativní, pokud je `expression1` záporný.</span><span class="sxs-lookup"><span data-stu-id="0b47c-117">In this sense, the operation consists of retaining the sign of `expression1`, so the result is negative if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="0b47c-118">Pokud `expression1` a `expression2` jsou oba řetězce, je výsledkem zřetězení jejich hodnot.</span><span class="sxs-lookup"><span data-stu-id="0b47c-118">If `expression1` and `expression2` are both strings, the result is the concatenation of their values.</span></span>  
  
 <span data-ttu-id="0b47c-119">Pokud `expression1` a `expression2` jsou smíšené typy, akce provedena závisí na jejich typech, jejich obsahu a nastavení [příkazu Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0b47c-119">If `expression1` and `expression2` are of mixed types, the action taken depends on their types, their contents, and the setting of the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span> <span data-ttu-id="0b47c-120">Další informace najdete v tabulkách v části "poznámky".</span><span class="sxs-lookup"><span data-stu-id="0b47c-120">For more information, see the tables in "Remarks."</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="0b47c-121">Podporované typy</span><span class="sxs-lookup"><span data-stu-id="0b47c-121">Supported Types</span></span>  
 <span data-ttu-id="0b47c-122">Všechny číselné typy, včetně typů unsigned a float-Point a `Decimal` a `String`.</span><span class="sxs-lookup"><span data-stu-id="0b47c-122">All numeric types, including the unsigned and floating-point types and `Decimal`, and `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b47c-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b47c-123">Remarks</span></span>  
 <span data-ttu-id="0b47c-124">Obecně platí, `+` provede aritmetické přidávání, pokud je to možné, a zřetězí se pouze v případě, že jsou oba výrazy řetězce.</span><span class="sxs-lookup"><span data-stu-id="0b47c-124">In general, `+` performs arithmetic addition when possible, and concatenates only when both expressions are strings.</span></span>  
  
 <span data-ttu-id="0b47c-125">Pokud žádný výraz není `Object`, Visual Basic provede následující akce.</span><span class="sxs-lookup"><span data-stu-id="0b47c-125">If neither expression is an `Object`, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="0b47c-126">Datové typy výrazů</span><span class="sxs-lookup"><span data-stu-id="0b47c-126">Data types of expressions</span></span>|<span data-ttu-id="0b47c-127">Akce podle kompilátoru</span><span class="sxs-lookup"><span data-stu-id="0b47c-127">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="0b47c-128">Oba výrazy jsou číselné datové typy (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single` nebo 0).</span><span class="sxs-lookup"><span data-stu-id="0b47c-128">Both expressions are numeric data types (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`)</span></span>|<span data-ttu-id="0b47c-129">Přidávání.</span><span class="sxs-lookup"><span data-stu-id="0b47c-129">Add.</span></span> <span data-ttu-id="0b47c-130">Výsledný datový typ je číselný typ, který je vhodný pro datové typy `expression1` a `expression2`.</span><span class="sxs-lookup"><span data-stu-id="0b47c-130">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="0b47c-131">Podívejte se na tabulky "celočíselné aritmetické" v [datových typech výsledků operátoru](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="0b47c-131">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="0b47c-132">Oba výrazy jsou typu `String`.</span><span class="sxs-lookup"><span data-stu-id="0b47c-132">Both expressions are of type `String`</span></span>|<span data-ttu-id="0b47c-133">Zřetězit.</span><span class="sxs-lookup"><span data-stu-id="0b47c-133">Concatenate.</span></span>|  
|<span data-ttu-id="0b47c-134">Jeden výraz je číselný datový typ a druhý je řetězec.</span><span class="sxs-lookup"><span data-stu-id="0b47c-134">One expression is a numeric data type and the other is a string</span></span>|<span data-ttu-id="0b47c-135">Pokud je `Option Strict` `On`, vygenerujte chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="0b47c-135">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="0b47c-136">Pokud je `Option Strict` `Off`, implicitně převeďte `String` na `Double` a přidejte.</span><span class="sxs-lookup"><span data-stu-id="0b47c-136">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="0b47c-137">Pokud `String` nelze převést na `Double`, vyvolejte výjimku <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="0b47c-137">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="0b47c-138">Jeden výraz je numerický datový typ a druhý není [nic](../../../visual-basic/language-reference/nothing.md)</span><span class="sxs-lookup"><span data-stu-id="0b47c-138">One expression is a numeric data type, and the other is [Nothing](../../../visual-basic/language-reference/nothing.md)</span></span>|<span data-ttu-id="0b47c-139">Přidejte s @no__t hodnotou 0, která se vyhodnotí jako nula.</span><span class="sxs-lookup"><span data-stu-id="0b47c-139">Add, with `Nothing` valued as zero.</span></span>|  
|<span data-ttu-id="0b47c-140">Jeden výraz je řetězec a druhý je `Nothing`</span><span class="sxs-lookup"><span data-stu-id="0b47c-140">One expression is a string, and the other is `Nothing`</span></span>|<span data-ttu-id="0b47c-141">Zřetězte s @no__t hodnotou 0, která se vyhodnotí jako "".</span><span class="sxs-lookup"><span data-stu-id="0b47c-141">Concatenate, with `Nothing` valued as "".</span></span>|  
  
 <span data-ttu-id="0b47c-142">Pokud je jeden výraz výraz `Object`, Visual Basic provede následující akce.</span><span class="sxs-lookup"><span data-stu-id="0b47c-142">If one expression is an `Object` expression, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="0b47c-143">Datové typy výrazů</span><span class="sxs-lookup"><span data-stu-id="0b47c-143">Data types of expressions</span></span>|<span data-ttu-id="0b47c-144">Akce podle kompilátoru</span><span class="sxs-lookup"><span data-stu-id="0b47c-144">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="0b47c-145">výraz `Object` obsahuje číselnou hodnotu a druhý je číselný datový typ.</span><span class="sxs-lookup"><span data-stu-id="0b47c-145">`Object` expression holds a numeric value and the other is a numeric data type</span></span>|<span data-ttu-id="0b47c-146">Pokud je `Option Strict` `On`, vygenerujte chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="0b47c-146">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="0b47c-147">Pokud je `Option Strict` `Off`, pak přidejte.</span><span class="sxs-lookup"><span data-stu-id="0b47c-147">If `Option Strict` is `Off`, then add.</span></span>|  
|<span data-ttu-id="0b47c-148">výraz `Object` obsahuje číselnou hodnotu a druhá je typu `String`.</span><span class="sxs-lookup"><span data-stu-id="0b47c-148">`Object` expression holds a numeric value and the other is of type `String`</span></span>|<span data-ttu-id="0b47c-149">Pokud je `Option Strict` `On`, vygenerujte chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="0b47c-149">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="0b47c-150">Pokud je `Option Strict` `Off`, implicitně převeďte `String` na `Double` a přidejte.</span><span class="sxs-lookup"><span data-stu-id="0b47c-150">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="0b47c-151">Pokud `String` nelze převést na `Double`, vyvolejte výjimku <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="0b47c-151">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="0b47c-152">výraz `Object` obsahuje řetězec a druhý je číselný datový typ.</span><span class="sxs-lookup"><span data-stu-id="0b47c-152">`Object` expression holds a string and the other is a numeric data type</span></span>|<span data-ttu-id="0b47c-153">Pokud je `Option Strict` `On`, vygenerujte chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="0b47c-153">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="0b47c-154">Pokud je `Option Strict` `Off`, implicitně převeďte řetězec `Object` na `Double` a přidejte.</span><span class="sxs-lookup"><span data-stu-id="0b47c-154">If `Option Strict` is `Off`, then implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="0b47c-155">Pokud řetězec `Object` nelze převést na `Double`, vyvolejte výjimku <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="0b47c-155">If the string `Object` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="0b47c-156">výraz `Object` obsahuje řetězec a druhý je typu `String`.</span><span class="sxs-lookup"><span data-stu-id="0b47c-156">`Object` expression holds a string and the other is of type `String`</span></span>|<span data-ttu-id="0b47c-157">Pokud je `Option Strict` `On`, vygenerujte chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="0b47c-157">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="0b47c-158">Pokud je `Option Strict` `Off`, implicitně převede `Object` na `String` a zřetězení.</span><span class="sxs-lookup"><span data-stu-id="0b47c-158">If `Option Strict` is `Off`, then implicitly convert `Object` to `String` and concatenate.</span></span>|  
  
 <span data-ttu-id="0b47c-159">Pokud jsou oba výrazy @no__t výrazy-0, Visual Basic provede následující akce (pouze `Option Strict Off`).</span><span class="sxs-lookup"><span data-stu-id="0b47c-159">If both expressions are `Object` expressions, Visual Basic takes the following actions (`Option Strict Off` only).</span></span>  
  
|<span data-ttu-id="0b47c-160">Datové typy výrazů</span><span class="sxs-lookup"><span data-stu-id="0b47c-160">Data types of expressions</span></span>|<span data-ttu-id="0b47c-161">Akce podle kompilátoru</span><span class="sxs-lookup"><span data-stu-id="0b47c-161">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="0b47c-162">Oba výrazy `Object` uchovávají číselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0b47c-162">Both `Object` expressions hold numeric values</span></span>|<span data-ttu-id="0b47c-163">Přidávání.</span><span class="sxs-lookup"><span data-stu-id="0b47c-163">Add.</span></span>|  
|<span data-ttu-id="0b47c-164">Výrazy `Object` jsou typu `String`.</span><span class="sxs-lookup"><span data-stu-id="0b47c-164">Both `Object` expressions are of type `String`</span></span>|<span data-ttu-id="0b47c-165">Zřetězit.</span><span class="sxs-lookup"><span data-stu-id="0b47c-165">Concatenate.</span></span>|  
|<span data-ttu-id="0b47c-166">Jeden výraz `Object` obsahuje číselnou hodnotu a druhý obsahuje řetězec.</span><span class="sxs-lookup"><span data-stu-id="0b47c-166">One `Object` expression holds a numeric value and the other holds a string</span></span>|<span data-ttu-id="0b47c-167">Implicitně převeďte řetězec `Object` na `Double` a přidat.</span><span class="sxs-lookup"><span data-stu-id="0b47c-167">Implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="0b47c-168">Pokud řetězec `Object` nelze převést na číselnou hodnotu, vyvolejte výjimku <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="0b47c-168">If the string `Object` cannot be converted to a numeric value, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
  
 <span data-ttu-id="0b47c-169">Pokud je výraz `Object` vyhodnocen jako [Nothing](../../../visual-basic/language-reference/nothing.md) nebo <xref:System.DBNull>, operátor `+` ho považuje za `String` s hodnotou "".</span><span class="sxs-lookup"><span data-stu-id="0b47c-169">If either `Object` expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md) or <xref:System.DBNull>, the `+` operator treats it as a `String` with a value of "".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0b47c-170">Pokud použijete operátor `+`, možná nebudete moci určit, zda dojde k přidání nebo zřetězení řetězců.</span><span class="sxs-lookup"><span data-stu-id="0b47c-170">When you use the `+` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="0b47c-171">Pomocí operátoru `&` pro zřetězení Eliminujte nejednoznačnosti a poskytněte kód pro samoobslužný dokument.</span><span class="sxs-lookup"><span data-stu-id="0b47c-171">Use the `&` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="0b47c-172">Přetížení</span><span class="sxs-lookup"><span data-stu-id="0b47c-172">Overloading</span></span>  
 <span data-ttu-id="0b47c-173">Operátor `+` lze přetížit, což znamená, že třída nebo struktura může předefinovat *chování, pokud*operand má typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="0b47c-173">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="0b47c-174">Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="0b47c-174">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="0b47c-175">Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="0b47c-175">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b47c-176">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b47c-176">Example</span></span>  
 <span data-ttu-id="0b47c-177">Následující příklad používá operátor `+` pro přidání čísel.</span><span class="sxs-lookup"><span data-stu-id="0b47c-177">The following example uses the `+` operator to add numbers.</span></span> <span data-ttu-id="0b47c-178">Pokud jsou operandy číselné, Visual Basic vypočítá aritmetický výsledek.</span><span class="sxs-lookup"><span data-stu-id="0b47c-178">If the operands are both numeric, Visual Basic computes the arithmetic result.</span></span> <span data-ttu-id="0b47c-179">Aritmetický výsledek představuje součet dvou operandů.</span><span class="sxs-lookup"><span data-stu-id="0b47c-179">The arithmetic result represents the sum of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#6)]  
  
 <span data-ttu-id="0b47c-180">K zřetězení řetězců můžete použít také operátor `+`.</span><span class="sxs-lookup"><span data-stu-id="0b47c-180">You can also use the `+` operator to concatenate strings.</span></span> <span data-ttu-id="0b47c-181">Pokud jsou operandy řetězcem, Visual Basic je zřetězí.</span><span class="sxs-lookup"><span data-stu-id="0b47c-181">If the operands are both strings, Visual Basic concatenates them.</span></span> <span data-ttu-id="0b47c-182">Výsledek zřetězení představuje jeden řetězec skládající se z obsahu dvou operandů jednoho po druhém.</span><span class="sxs-lookup"><span data-stu-id="0b47c-182">The concatenation result represents a single string consisting of the contents of the two operands one after the other.</span></span>  
  
 <span data-ttu-id="0b47c-183">Pokud jsou operandy smíšeného typu, výsledek závisí na nastavení [příkazu Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0b47c-183">If the operands are of mixed types, the result depends on the setting of the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span> <span data-ttu-id="0b47c-184">Následující příklad ilustruje výsledek, pokud je `Option Strict` `On`.</span><span class="sxs-lookup"><span data-stu-id="0b47c-184">The following example illustrates the result when `Option Strict` is `On`.</span></span>  
  
 [!code-vb[VbVbalrOperators#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class3.vb#53)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#51)]  
  
 <span data-ttu-id="0b47c-185">Následující příklad ilustruje výsledek, pokud je `Option Strict` `Off`.</span><span class="sxs-lookup"><span data-stu-id="0b47c-185">The following example illustrates the result when `Option Strict` is `Off`.</span></span>  
  
 [!code-vb[VbVbalrOperators#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#54)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#52)]  
  
 <span data-ttu-id="0b47c-186">Chcete-li odstranit nejednoznačnost, měli byste použít operátor `&` namísto `+` pro zřetězení.</span><span class="sxs-lookup"><span data-stu-id="0b47c-186">To eliminate ambiguity, you should use the `&` operator instead of `+` for concatenation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b47c-187">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0b47c-187">See also</span></span>

- [<span data-ttu-id="0b47c-188">Operátor &</span><span class="sxs-lookup"><span data-stu-id="0b47c-188">& Operator</span></span>](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [<span data-ttu-id="0b47c-189">Operátory řetězení</span><span class="sxs-lookup"><span data-stu-id="0b47c-189">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="0b47c-190">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="0b47c-190">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="0b47c-191">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="0b47c-191">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="0b47c-192">Priorita operátorů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0b47c-192">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="0b47c-193">Aritmetické operátory v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0b47c-193">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="0b47c-194">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="0b47c-194">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
