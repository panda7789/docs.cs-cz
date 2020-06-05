---
title: + Operátor
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
ms.openlocfilehash: 6ae3feae6ecb63b82426f2aa69359625bbffcec8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372113"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="02241-102">+ – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="02241-102">+ Operator (Visual Basic)</span></span>
<span data-ttu-id="02241-103">Přidá dvě čísla nebo vrátí kladnou hodnotu číselného výrazu.</span><span class="sxs-lookup"><span data-stu-id="02241-103">Adds two numbers or returns the positive value of a numeric expression.</span></span> <span data-ttu-id="02241-104">Lze také použít ke zřetězení dvou řetězcových výrazů.</span><span class="sxs-lookup"><span data-stu-id="02241-104">Can also be used to concatenate two string expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02241-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02241-105">Syntax</span></span>  
  
```vb
expression1 + expression2
```
  
<span data-ttu-id="02241-106">nebo</span><span class="sxs-lookup"><span data-stu-id="02241-106">or</span></span>

```vb  
+expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="02241-107">Součásti</span><span class="sxs-lookup"><span data-stu-id="02241-107">Parts</span></span>  
  
|<span data-ttu-id="02241-108">Pojem</span><span class="sxs-lookup"><span data-stu-id="02241-108">Term</span></span>|<span data-ttu-id="02241-109">Definice</span><span class="sxs-lookup"><span data-stu-id="02241-109">Definition</span></span>|  
|---|---|  
|`expression1`|<span data-ttu-id="02241-110">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="02241-110">Required.</span></span> <span data-ttu-id="02241-111">Libovolný numerický nebo řetězcový výraz.</span><span class="sxs-lookup"><span data-stu-id="02241-111">Any numeric or string expression.</span></span>|  
|`expression2`|<span data-ttu-id="02241-112">Povinné, pokud `+` operátor nevypočítá zápornou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="02241-112">Required unless the `+` operator is calculating a negative value.</span></span> <span data-ttu-id="02241-113">Libovolný numerický nebo řetězcový výraz.</span><span class="sxs-lookup"><span data-stu-id="02241-113">Any numeric or string expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="02241-114">Výsledek</span><span class="sxs-lookup"><span data-stu-id="02241-114">Result</span></span>  
 <span data-ttu-id="02241-115">Pokud `expression1` a `expression2` jsou oba číselné, výsledek je aritmetický součet.</span><span class="sxs-lookup"><span data-stu-id="02241-115">If `expression1` and `expression2` are both numeric, the result is their arithmetic sum.</span></span>  
  
 <span data-ttu-id="02241-116">Pokud `expression2` chybí, `+` operátor je *unární* operátor identity pro nezměněnou hodnotu výrazu.</span><span class="sxs-lookup"><span data-stu-id="02241-116">If `expression2` is absent, the `+` operator is the *unary* identity operator for the unchanged value of an expression.</span></span> <span data-ttu-id="02241-117">V tomto smyslu se operace skládá z zachování znaménka `expression1` , takže výsledek je záporný, pokud `expression1` je záporná.</span><span class="sxs-lookup"><span data-stu-id="02241-117">In this sense, the operation consists of retaining the sign of `expression1`, so the result is negative if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="02241-118">Pokud `expression1` a `expression2` jsou oba řetězce, je výsledkem zřetězení jejich hodnot.</span><span class="sxs-lookup"><span data-stu-id="02241-118">If `expression1` and `expression2` are both strings, the result is the concatenation of their values.</span></span>  
  
 <span data-ttu-id="02241-119">`expression1`V případě `expression2` smíšených typů závisí akce prováděná na jejich typech, jejich obsahu a nastavení [příkazu Option Strict](../statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="02241-119">If `expression1` and `expression2` are of mixed types, the action taken depends on their types, their contents, and the setting of the [Option Strict Statement](../statements/option-strict-statement.md).</span></span> <span data-ttu-id="02241-120">Další informace najdete v tabulkách v části "poznámky".</span><span class="sxs-lookup"><span data-stu-id="02241-120">For more information, see the tables in "Remarks."</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="02241-121">Podporované typy</span><span class="sxs-lookup"><span data-stu-id="02241-121">Supported Types</span></span>  
 <span data-ttu-id="02241-122">Všechny číselné typy, včetně typů unsigned a float-Point a `Decimal` a `String` .</span><span class="sxs-lookup"><span data-stu-id="02241-122">All numeric types, including the unsigned and floating-point types and `Decimal`, and `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02241-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="02241-123">Remarks</span></span>  
 <span data-ttu-id="02241-124">Obecně `+` provádí aritmetické sčítání, pokud je to možné, a zřetězení pouze v případě, že oba výrazy jsou řetězce.</span><span class="sxs-lookup"><span data-stu-id="02241-124">In general, `+` performs arithmetic addition when possible, and concatenates only when both expressions are strings.</span></span>  
  
 <span data-ttu-id="02241-125">Pokud žádný výraz není `Object` , Visual Basic provede následující akce.</span><span class="sxs-lookup"><span data-stu-id="02241-125">If neither expression is an `Object`, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="02241-126">Datové typy výrazů</span><span class="sxs-lookup"><span data-stu-id="02241-126">Data types of expressions</span></span>|<span data-ttu-id="02241-127">Akce podle kompilátoru</span><span class="sxs-lookup"><span data-stu-id="02241-127">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="02241-128">Oba výrazy jsou číselné datové typy ( `SByte` , `Byte` , `Short` , `UShort` , `Integer` , `UInteger` , `Long` , `ULong` , `Decimal` , `Single` , nebo `Double` ).</span><span class="sxs-lookup"><span data-stu-id="02241-128">Both expressions are numeric data types (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`)</span></span>|<span data-ttu-id="02241-129">Přidat</span><span class="sxs-lookup"><span data-stu-id="02241-129">Add.</span></span> <span data-ttu-id="02241-130">Výsledný datový typ je číselný typ odpovídající datovým typům `expression1` a `expression2` .</span><span class="sxs-lookup"><span data-stu-id="02241-130">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="02241-131">Podívejte se na tabulky "celočíselné aritmetické" v [datových typech výsledků operátoru](data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="02241-131">See the "Integer Arithmetic" tables in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="02241-132">Oba výrazy jsou typu`String`</span><span class="sxs-lookup"><span data-stu-id="02241-132">Both expressions are of type `String`</span></span>|<span data-ttu-id="02241-133">Zřetězit.</span><span class="sxs-lookup"><span data-stu-id="02241-133">Concatenate.</span></span>|  
|<span data-ttu-id="02241-134">Jeden výraz je číselný datový typ a druhý je řetězec.</span><span class="sxs-lookup"><span data-stu-id="02241-134">One expression is a numeric data type and the other is a string</span></span>|<span data-ttu-id="02241-135">Pokud `Option Strict` je `On` , vygenerujte chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="02241-135">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="02241-136">Pokud `Option Strict` je `Off` , pak implicitně převeďte `String` na `Double` a přidat.</span><span class="sxs-lookup"><span data-stu-id="02241-136">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="02241-137">Pokud `String` nelze převést na `Double` , vyvolejte <xref:System.InvalidCastException> výjimku.</span><span class="sxs-lookup"><span data-stu-id="02241-137">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="02241-138">Jeden výraz je numerický datový typ a druhý není [nic](../nothing.md)</span><span class="sxs-lookup"><span data-stu-id="02241-138">One expression is a numeric data type, and the other is [Nothing](../nothing.md)</span></span>|<span data-ttu-id="02241-139">Přidejte s `Nothing` hodnotou nula.</span><span class="sxs-lookup"><span data-stu-id="02241-139">Add, with `Nothing` valued as zero.</span></span>|  
|<span data-ttu-id="02241-140">Jeden výraz je řetězec a druhý je`Nothing`</span><span class="sxs-lookup"><span data-stu-id="02241-140">One expression is a string, and the other is `Nothing`</span></span>|<span data-ttu-id="02241-141">CONCATENATE s hodnotou " `Nothing` ".</span><span class="sxs-lookup"><span data-stu-id="02241-141">Concatenate, with `Nothing` valued as "".</span></span>|  
  
 <span data-ttu-id="02241-142">Pokud je jedním výrazem výraz `Object` , Visual Basic provede následující akce.</span><span class="sxs-lookup"><span data-stu-id="02241-142">If one expression is an `Object` expression, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="02241-143">Datové typy výrazů</span><span class="sxs-lookup"><span data-stu-id="02241-143">Data types of expressions</span></span>|<span data-ttu-id="02241-144">Akce podle kompilátoru</span><span class="sxs-lookup"><span data-stu-id="02241-144">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="02241-145">`Object`výraz obsahuje číselnou hodnotu a druhý je číselný datový typ.</span><span class="sxs-lookup"><span data-stu-id="02241-145">`Object` expression holds a numeric value and the other is a numeric data type</span></span>|<span data-ttu-id="02241-146">Pokud `Option Strict` je `On` , vygenerujte chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="02241-146">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="02241-147">Pokud `Option Strict` je `Off` , přidejte.</span><span class="sxs-lookup"><span data-stu-id="02241-147">If `Option Strict` is `Off`, then add.</span></span>|  
|<span data-ttu-id="02241-148">`Object`výraz obsahuje číselnou hodnotu a druhý je typu.`String`</span><span class="sxs-lookup"><span data-stu-id="02241-148">`Object` expression holds a numeric value and the other is of type `String`</span></span>|<span data-ttu-id="02241-149">Pokud `Option Strict` je `On` , vygenerujte chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="02241-149">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="02241-150">Pokud `Option Strict` je `Off` , pak implicitně převeďte `String` na `Double` a přidat.</span><span class="sxs-lookup"><span data-stu-id="02241-150">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="02241-151">Pokud `String` nelze převést na `Double` , vyvolejte <xref:System.InvalidCastException> výjimku.</span><span class="sxs-lookup"><span data-stu-id="02241-151">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="02241-152">`Object`výraz obsahuje řetězec a druhý je číselný datový typ.</span><span class="sxs-lookup"><span data-stu-id="02241-152">`Object` expression holds a string and the other is a numeric data type</span></span>|<span data-ttu-id="02241-153">Pokud `Option Strict` je `On` , vygenerujte chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="02241-153">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="02241-154">Pokud `Option Strict` je `Off` , pak implicitně převeďte řetězec `Object` na `Double` a přidat.</span><span class="sxs-lookup"><span data-stu-id="02241-154">If `Option Strict` is `Off`, then implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="02241-155">Pokud řetězec `Object` nelze převést na `Double` , vyvolejte <xref:System.InvalidCastException> výjimku.</span><span class="sxs-lookup"><span data-stu-id="02241-155">If the string `Object` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="02241-156">`Object`výraz obsahuje řetězec a druhý je typu`String`</span><span class="sxs-lookup"><span data-stu-id="02241-156">`Object` expression holds a string and the other is of type `String`</span></span>|<span data-ttu-id="02241-157">Pokud `Option Strict` je `On` , vygenerujte chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="02241-157">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="02241-158">Pokud `Option Strict` je `Off` , pak implicitní převod `Object` na `String` a zřetězení.</span><span class="sxs-lookup"><span data-stu-id="02241-158">If `Option Strict` is `Off`, then implicitly convert `Object` to `String` and concatenate.</span></span>|  
  
 <span data-ttu-id="02241-159">Pokud jsou oba výrazy `Object` výrazy, Visual Basic provádí následující akce ( `Option Strict Off` pouze).</span><span class="sxs-lookup"><span data-stu-id="02241-159">If both expressions are `Object` expressions, Visual Basic takes the following actions (`Option Strict Off` only).</span></span>  
  
|<span data-ttu-id="02241-160">Datové typy výrazů</span><span class="sxs-lookup"><span data-stu-id="02241-160">Data types of expressions</span></span>|<span data-ttu-id="02241-161">Akce podle kompilátoru</span><span class="sxs-lookup"><span data-stu-id="02241-161">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="02241-162">Oba `Object` výrazy uchovávají číselné hodnoty</span><span class="sxs-lookup"><span data-stu-id="02241-162">Both `Object` expressions hold numeric values</span></span>|<span data-ttu-id="02241-163">Přidat</span><span class="sxs-lookup"><span data-stu-id="02241-163">Add.</span></span>|  
|<span data-ttu-id="02241-164">Oba `Object` výrazy jsou typu`String`</span><span class="sxs-lookup"><span data-stu-id="02241-164">Both `Object` expressions are of type `String`</span></span>|<span data-ttu-id="02241-165">Zřetězit.</span><span class="sxs-lookup"><span data-stu-id="02241-165">Concatenate.</span></span>|  
|<span data-ttu-id="02241-166">Jeden `Object` výraz obsahuje číselnou hodnotu a druhý obsahuje řetězec.</span><span class="sxs-lookup"><span data-stu-id="02241-166">One `Object` expression holds a numeric value and the other holds a string</span></span>|<span data-ttu-id="02241-167">Implicitně převeďte řetězec `Object` na `Double` a přidat.</span><span class="sxs-lookup"><span data-stu-id="02241-167">Implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="02241-168">Pokud řetězec `Object` nelze převést na číselnou hodnotu, vyvolejte <xref:System.InvalidCastException> výjimku.</span><span class="sxs-lookup"><span data-stu-id="02241-168">If the string `Object` cannot be converted to a numeric value, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
  
 <span data-ttu-id="02241-169">Pokud se některý `Object` výraz vyhodnotí jako [Nothing](../nothing.md) nebo <xref:System.DBNull> , `+` operátor ho považuje za `String` s hodnotou "".</span><span class="sxs-lookup"><span data-stu-id="02241-169">If either `Object` expression evaluates to [Nothing](../nothing.md) or <xref:System.DBNull>, the `+` operator treats it as a `String` with a value of "".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="02241-170">Při použití `+` operátoru nemusí být možné určit, zda dojde k přidání nebo zřetězení řetězců.</span><span class="sxs-lookup"><span data-stu-id="02241-170">When you use the `+` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="02241-171">Použijte `&` operátor pro zřetězení k eliminaci nejednoznačnosti a k poskytnutí kódu pro samoobslužné dokumenty.</span><span class="sxs-lookup"><span data-stu-id="02241-171">Use the `&` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="02241-172">Přetížení</span><span class="sxs-lookup"><span data-stu-id="02241-172">Overloading</span></span>  
 <span data-ttu-id="02241-173">`+`Operátor může být *přetížen*, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="02241-173">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="02241-174">Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="02241-174">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="02241-175">Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="02241-175">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="02241-176">Příklad</span><span class="sxs-lookup"><span data-stu-id="02241-176">Example</span></span>  
 <span data-ttu-id="02241-177">Následující příklad používá `+` operátor pro přidání čísel.</span><span class="sxs-lookup"><span data-stu-id="02241-177">The following example uses the `+` operator to add numbers.</span></span> <span data-ttu-id="02241-178">Pokud jsou operandy číselné, Visual Basic vypočítá aritmetický výsledek.</span><span class="sxs-lookup"><span data-stu-id="02241-178">If the operands are both numeric, Visual Basic computes the arithmetic result.</span></span> <span data-ttu-id="02241-179">Aritmetický výsledek představuje součet dvou operandů.</span><span class="sxs-lookup"><span data-stu-id="02241-179">The arithmetic result represents the sum of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#6)]  
  
 <span data-ttu-id="02241-180">Operátor můžete také použít `+` k zřetězení řetězců.</span><span class="sxs-lookup"><span data-stu-id="02241-180">You can also use the `+` operator to concatenate strings.</span></span> <span data-ttu-id="02241-181">Pokud jsou operandy řetězcem, Visual Basic je zřetězí.</span><span class="sxs-lookup"><span data-stu-id="02241-181">If the operands are both strings, Visual Basic concatenates them.</span></span> <span data-ttu-id="02241-182">Výsledek zřetězení představuje jeden řetězec skládající se z obsahu dvou operandů jednoho po druhém.</span><span class="sxs-lookup"><span data-stu-id="02241-182">The concatenation result represents a single string consisting of the contents of the two operands one after the other.</span></span>  
  
 <span data-ttu-id="02241-183">Pokud jsou operandy smíšeného typu, výsledek závisí na nastavení [příkazu Option Strict](../statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="02241-183">If the operands are of mixed types, the result depends on the setting of the [Option Strict Statement](../statements/option-strict-statement.md).</span></span> <span data-ttu-id="02241-184">Následující příklad ilustruje výsledek, pokud `Option Strict` je `On` .</span><span class="sxs-lookup"><span data-stu-id="02241-184">The following example illustrates the result when `Option Strict` is `On`.</span></span>  
  
 [!code-vb[VbVbalrOperators#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class3.vb#53)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#51)]  
  
 <span data-ttu-id="02241-185">Následující příklad ilustruje výsledek, pokud `Option Strict` je `Off` .</span><span class="sxs-lookup"><span data-stu-id="02241-185">The following example illustrates the result when `Option Strict` is `Off`.</span></span>  
  
 [!code-vb[VbVbalrOperators#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#54)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#52)]  
  
 <span data-ttu-id="02241-186">Chcete-li eliminovat nejednoznačnost, použijte `&` místo `+` pro zřetězení operátor.</span><span class="sxs-lookup"><span data-stu-id="02241-186">To eliminate ambiguity, you should use the `&` operator instead of `+` for concatenation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02241-187">Viz také</span><span class="sxs-lookup"><span data-stu-id="02241-187">See also</span></span>

- [<span data-ttu-id="02241-188">Operátor&</span><span class="sxs-lookup"><span data-stu-id="02241-188">& Operator</span></span>](concatenation-operator.md)
- [<span data-ttu-id="02241-189">Operátory řetězení</span><span class="sxs-lookup"><span data-stu-id="02241-189">Concatenation Operators</span></span>](concatenation-operators.md)
- [<span data-ttu-id="02241-190">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="02241-190">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="02241-191">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="02241-191">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="02241-192">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="02241-192">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="02241-193">Aritmetické operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="02241-193">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="02241-194">Option Strict – příkaz</span><span class="sxs-lookup"><span data-stu-id="02241-194">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
