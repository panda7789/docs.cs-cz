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
ms.openlocfilehash: 12c14b3be0562a31470ddbd2d5489ccdbdf3b62b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350293"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="6fbde-102">+ – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6fbde-102">+ Operator (Visual Basic)</span></span>
<span data-ttu-id="6fbde-103">Přidá dvě čísla nebo vrátí kladnou hodnotu číselného výrazu.</span><span class="sxs-lookup"><span data-stu-id="6fbde-103">Adds two numbers or returns the positive value of a numeric expression.</span></span> <span data-ttu-id="6fbde-104">Lze také použít ke zřetězení dvou řetězcových výrazů.</span><span class="sxs-lookup"><span data-stu-id="6fbde-104">Can also be used to concatenate two string expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fbde-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6fbde-105">Syntax</span></span>  
  
```vb
expression1 + expression2
```
  
<span data-ttu-id="6fbde-106">nebo</span><span class="sxs-lookup"><span data-stu-id="6fbde-106">or</span></span>

```vb  
+expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="6fbde-107">Součásti</span><span class="sxs-lookup"><span data-stu-id="6fbde-107">Parts</span></span>  
  
|<span data-ttu-id="6fbde-108">Termín</span><span class="sxs-lookup"><span data-stu-id="6fbde-108">Term</span></span>|<span data-ttu-id="6fbde-109">Definice</span><span class="sxs-lookup"><span data-stu-id="6fbde-109">Definition</span></span>|  
|---|---|  
|`expression1`|<span data-ttu-id="6fbde-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="6fbde-110">Required.</span></span> <span data-ttu-id="6fbde-111">Libovolný numerický nebo řetězcový výraz.</span><span class="sxs-lookup"><span data-stu-id="6fbde-111">Any numeric or string expression.</span></span>|  
|`expression2`|<span data-ttu-id="6fbde-112">Povinné, pokud operátor `+` nevypočítá zápornou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6fbde-112">Required unless the `+` operator is calculating a negative value.</span></span> <span data-ttu-id="6fbde-113">Libovolný numerický nebo řetězcový výraz.</span><span class="sxs-lookup"><span data-stu-id="6fbde-113">Any numeric or string expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="6fbde-114">Výsledek</span><span class="sxs-lookup"><span data-stu-id="6fbde-114">Result</span></span>  
 <span data-ttu-id="6fbde-115">Pokud jsou `expression1` a `expression2` číselné, výsledkem je aritmetický součet.</span><span class="sxs-lookup"><span data-stu-id="6fbde-115">If `expression1` and `expression2` are both numeric, the result is their arithmetic sum.</span></span>  
  
 <span data-ttu-id="6fbde-116">Pokud `expression2` chybí, operátor `+` je *unárním* operátorem identity pro nezměněnou hodnotu výrazu.</span><span class="sxs-lookup"><span data-stu-id="6fbde-116">If `expression2` is absent, the `+` operator is the *unary* identity operator for the unchanged value of an expression.</span></span> <span data-ttu-id="6fbde-117">V tomto smyslu se operace skládá z zachování `expression1`, takže výsledek je záporný, pokud `expression1` záporné.</span><span class="sxs-lookup"><span data-stu-id="6fbde-117">In this sense, the operation consists of retaining the sign of `expression1`, so the result is negative if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="6fbde-118">Pokud `expression1` a `expression2` jsou oba řetězce, je výsledkem zřetězení jejich hodnot.</span><span class="sxs-lookup"><span data-stu-id="6fbde-118">If `expression1` and `expression2` are both strings, the result is the concatenation of their values.</span></span>  
  
 <span data-ttu-id="6fbde-119">Pokud `expression1` a `expression2` jsou smíšených typů, akce provedena závisí na jejich typech, jejich obsahu a nastavení [příkazu Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6fbde-119">If `expression1` and `expression2` are of mixed types, the action taken depends on their types, their contents, and the setting of the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span> <span data-ttu-id="6fbde-120">Další informace najdete v tabulkách v části "poznámky".</span><span class="sxs-lookup"><span data-stu-id="6fbde-120">For more information, see the tables in "Remarks."</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="6fbde-121">Podporované typy</span><span class="sxs-lookup"><span data-stu-id="6fbde-121">Supported Types</span></span>  
 <span data-ttu-id="6fbde-122">Všechny číselné typy, včetně typů bez znaménka a plovoucí desetinné čárky a `Decimal`a `String`.</span><span class="sxs-lookup"><span data-stu-id="6fbde-122">All numeric types, including the unsigned and floating-point types and `Decimal`, and `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6fbde-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6fbde-123">Remarks</span></span>  
 <span data-ttu-id="6fbde-124">Obecně `+` provádí aritmetické přidávání, pokud je to možné, a zřetězení pouze v případě, že oba výrazy jsou řetězce.</span><span class="sxs-lookup"><span data-stu-id="6fbde-124">In general, `+` performs arithmetic addition when possible, and concatenates only when both expressions are strings.</span></span>  
  
 <span data-ttu-id="6fbde-125">Pokud žádný výraz není `Object`, Visual Basic provede následující akce.</span><span class="sxs-lookup"><span data-stu-id="6fbde-125">If neither expression is an `Object`, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="6fbde-126">Datové typy výrazů</span><span class="sxs-lookup"><span data-stu-id="6fbde-126">Data types of expressions</span></span>|<span data-ttu-id="6fbde-127">Akce podle kompilátoru</span><span class="sxs-lookup"><span data-stu-id="6fbde-127">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="6fbde-128">Oba výrazy jsou číselné datové typy (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`nebo `Double`).</span><span class="sxs-lookup"><span data-stu-id="6fbde-128">Both expressions are numeric data types (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`)</span></span>|<span data-ttu-id="6fbde-129">Přidávání.</span><span class="sxs-lookup"><span data-stu-id="6fbde-129">Add.</span></span> <span data-ttu-id="6fbde-130">Výsledný datový typ je číselný typ, který je vhodný pro datové typy `expression1` a `expression2`.</span><span class="sxs-lookup"><span data-stu-id="6fbde-130">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="6fbde-131">Podívejte se na tabulky "celočíselné aritmetické" v [datových typech výsledků operátoru](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="6fbde-131">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="6fbde-132">Oba výrazy jsou typu `String`</span><span class="sxs-lookup"><span data-stu-id="6fbde-132">Both expressions are of type `String`</span></span>|<span data-ttu-id="6fbde-133">Zřetězit.</span><span class="sxs-lookup"><span data-stu-id="6fbde-133">Concatenate.</span></span>|  
|<span data-ttu-id="6fbde-134">Jeden výraz je číselný datový typ a druhý je řetězec.</span><span class="sxs-lookup"><span data-stu-id="6fbde-134">One expression is a numeric data type and the other is a string</span></span>|<span data-ttu-id="6fbde-135">Pokud je `Option Strict` `On`, vygenerujte chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="6fbde-135">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="6fbde-136">Pokud je `Option Strict` `Off`, implicitně převeďte `String` na `Double` a přidat.</span><span class="sxs-lookup"><span data-stu-id="6fbde-136">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="6fbde-137">Pokud `String` nelze převést na `Double`, vyvolejte výjimku <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="6fbde-137">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="6fbde-138">Jeden výraz je numerický datový typ a druhý není [nic](../../../visual-basic/language-reference/nothing.md)</span><span class="sxs-lookup"><span data-stu-id="6fbde-138">One expression is a numeric data type, and the other is [Nothing](../../../visual-basic/language-reference/nothing.md)</span></span>|<span data-ttu-id="6fbde-139">Přidejte, s `Nothing` hodnotou nula.</span><span class="sxs-lookup"><span data-stu-id="6fbde-139">Add, with `Nothing` valued as zero.</span></span>|  
|<span data-ttu-id="6fbde-140">Jeden výraz je řetězec a druhý je `Nothing`</span><span class="sxs-lookup"><span data-stu-id="6fbde-140">One expression is a string, and the other is `Nothing`</span></span>|<span data-ttu-id="6fbde-141">CONCATENATE s `Nothing` se oceňuje jako "".</span><span class="sxs-lookup"><span data-stu-id="6fbde-141">Concatenate, with `Nothing` valued as "".</span></span>|  
  
 <span data-ttu-id="6fbde-142">Pokud je jedním výrazem výraz `Object`, Visual Basic provede následující akce.</span><span class="sxs-lookup"><span data-stu-id="6fbde-142">If one expression is an `Object` expression, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="6fbde-143">Datové typy výrazů</span><span class="sxs-lookup"><span data-stu-id="6fbde-143">Data types of expressions</span></span>|<span data-ttu-id="6fbde-144">Akce podle kompilátoru</span><span class="sxs-lookup"><span data-stu-id="6fbde-144">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="6fbde-145">výraz `Object` má číselnou hodnotu a druhý je numerický datový typ.</span><span class="sxs-lookup"><span data-stu-id="6fbde-145">`Object` expression holds a numeric value and the other is a numeric data type</span></span>|<span data-ttu-id="6fbde-146">Pokud je `Option Strict` `On`, vygenerujte chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="6fbde-146">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="6fbde-147">Pokud je `Option Strict` `Off`, přidejte.</span><span class="sxs-lookup"><span data-stu-id="6fbde-147">If `Option Strict` is `Off`, then add.</span></span>|  
|<span data-ttu-id="6fbde-148">výraz `Object` má číselnou hodnotu a druhý je typu `String`</span><span class="sxs-lookup"><span data-stu-id="6fbde-148">`Object` expression holds a numeric value and the other is of type `String`</span></span>|<span data-ttu-id="6fbde-149">Pokud je `Option Strict` `On`, vygenerujte chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="6fbde-149">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="6fbde-150">Pokud je `Option Strict` `Off`, implicitně převeďte `String` na `Double` a přidat.</span><span class="sxs-lookup"><span data-stu-id="6fbde-150">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="6fbde-151">Pokud `String` nelze převést na `Double`, vyvolejte výjimku <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="6fbde-151">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="6fbde-152">výraz `Object` obsahuje řetězec a druhý je číselný datový typ.</span><span class="sxs-lookup"><span data-stu-id="6fbde-152">`Object` expression holds a string and the other is a numeric data type</span></span>|<span data-ttu-id="6fbde-153">Pokud je `Option Strict` `On`, vygenerujte chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="6fbde-153">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="6fbde-154">Pokud je `Option Strict` `Off`, pak implicitně převeďte řetězec `Object` na `Double` a přidat.</span><span class="sxs-lookup"><span data-stu-id="6fbde-154">If `Option Strict` is `Off`, then implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="6fbde-155">Pokud `Object` řetězec nelze převést na `Double`, vyvolejte výjimku <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="6fbde-155">If the string `Object` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="6fbde-156">výraz `Object` obsahuje řetězec a druhý je typu `String`</span><span class="sxs-lookup"><span data-stu-id="6fbde-156">`Object` expression holds a string and the other is of type `String`</span></span>|<span data-ttu-id="6fbde-157">Pokud je `Option Strict` `On`, vygenerujte chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="6fbde-157">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="6fbde-158">Pokud je `Option Strict` `Off`, implicitně převeďte `Object` na `String` a zřetězit.</span><span class="sxs-lookup"><span data-stu-id="6fbde-158">If `Option Strict` is `Off`, then implicitly convert `Object` to `String` and concatenate.</span></span>|  
  
 <span data-ttu-id="6fbde-159">Pokud jsou oba výrazy `Object` výrazy, Visual Basic provádí následující akce (pouze`Option Strict Off`).</span><span class="sxs-lookup"><span data-stu-id="6fbde-159">If both expressions are `Object` expressions, Visual Basic takes the following actions (`Option Strict Off` only).</span></span>  
  
|<span data-ttu-id="6fbde-160">Datové typy výrazů</span><span class="sxs-lookup"><span data-stu-id="6fbde-160">Data types of expressions</span></span>|<span data-ttu-id="6fbde-161">Akce podle kompilátoru</span><span class="sxs-lookup"><span data-stu-id="6fbde-161">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="6fbde-162">Oba `Object` výrazy uchovávají číselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6fbde-162">Both `Object` expressions hold numeric values</span></span>|<span data-ttu-id="6fbde-163">Přidávání.</span><span class="sxs-lookup"><span data-stu-id="6fbde-163">Add.</span></span>|  
|<span data-ttu-id="6fbde-164">Oba `Object` výrazy jsou typu `String`</span><span class="sxs-lookup"><span data-stu-id="6fbde-164">Both `Object` expressions are of type `String`</span></span>|<span data-ttu-id="6fbde-165">Zřetězit.</span><span class="sxs-lookup"><span data-stu-id="6fbde-165">Concatenate.</span></span>|  
|<span data-ttu-id="6fbde-166">Jeden `Object` výraz obsahuje číselnou hodnotu a druhý obsahuje řetězec.</span><span class="sxs-lookup"><span data-stu-id="6fbde-166">One `Object` expression holds a numeric value and the other holds a string</span></span>|<span data-ttu-id="6fbde-167">Implicitně převeďte řetězec `Object` na `Double` a přidat.</span><span class="sxs-lookup"><span data-stu-id="6fbde-167">Implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="6fbde-168">Pokud řetězec `Object` nelze převést na číselnou hodnotu, vyvolejte výjimku <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="6fbde-168">If the string `Object` cannot be converted to a numeric value, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
  
 <span data-ttu-id="6fbde-169">Pokud je výraz `Object` vyhodnocen jako [Nothing](../../../visual-basic/language-reference/nothing.md) nebo <xref:System.DBNull>, operátor `+` ho považuje za `String` s hodnotou "".</span><span class="sxs-lookup"><span data-stu-id="6fbde-169">If either `Object` expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md) or <xref:System.DBNull>, the `+` operator treats it as a `String` with a value of "".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6fbde-170">Když použijete operátor `+`, možná nebudete moci určit, zda dojde k přidání nebo zřetězení řetězců.</span><span class="sxs-lookup"><span data-stu-id="6fbde-170">When you use the `+` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="6fbde-171">Použijte operátor `&` pro zřetězení k eliminaci nejednoznačnosti a k poskytnutí kódu pro osobní dokument.</span><span class="sxs-lookup"><span data-stu-id="6fbde-171">Use the `&` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="6fbde-172">Přetížení</span><span class="sxs-lookup"><span data-stu-id="6fbde-172">Overloading</span></span>  
 <span data-ttu-id="6fbde-173">Operátor `+` lze přetížit, což znamená, že třída nebo struktura může předefinovat své *chování, pokud*má operand typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="6fbde-173">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="6fbde-174">Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="6fbde-174">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="6fbde-175">Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="6fbde-175">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fbde-176">Příklad</span><span class="sxs-lookup"><span data-stu-id="6fbde-176">Example</span></span>  
 <span data-ttu-id="6fbde-177">Následující příklad používá operátor `+` pro přidání čísel.</span><span class="sxs-lookup"><span data-stu-id="6fbde-177">The following example uses the `+` operator to add numbers.</span></span> <span data-ttu-id="6fbde-178">Pokud jsou operandy číselné, Visual Basic vypočítá aritmetický výsledek.</span><span class="sxs-lookup"><span data-stu-id="6fbde-178">If the operands are both numeric, Visual Basic computes the arithmetic result.</span></span> <span data-ttu-id="6fbde-179">Aritmetický výsledek představuje součet dvou operandů.</span><span class="sxs-lookup"><span data-stu-id="6fbde-179">The arithmetic result represents the sum of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#6)]  
  
 <span data-ttu-id="6fbde-180">K zřetězení řetězců lze také použít operátor `+`.</span><span class="sxs-lookup"><span data-stu-id="6fbde-180">You can also use the `+` operator to concatenate strings.</span></span> <span data-ttu-id="6fbde-181">Pokud jsou operandy řetězcem, Visual Basic je zřetězí.</span><span class="sxs-lookup"><span data-stu-id="6fbde-181">If the operands are both strings, Visual Basic concatenates them.</span></span> <span data-ttu-id="6fbde-182">Výsledek zřetězení představuje jeden řetězec skládající se z obsahu dvou operandů jednoho po druhém.</span><span class="sxs-lookup"><span data-stu-id="6fbde-182">The concatenation result represents a single string consisting of the contents of the two operands one after the other.</span></span>  
  
 <span data-ttu-id="6fbde-183">Pokud jsou operandy smíšeného typu, výsledek závisí na nastavení [příkazu Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6fbde-183">If the operands are of mixed types, the result depends on the setting of the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span> <span data-ttu-id="6fbde-184">Následující příklad ilustruje výsledek při `On``Option Strict`.</span><span class="sxs-lookup"><span data-stu-id="6fbde-184">The following example illustrates the result when `Option Strict` is `On`.</span></span>  
  
 [!code-vb[VbVbalrOperators#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class3.vb#53)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#51)]  
  
 <span data-ttu-id="6fbde-185">Následující příklad ilustruje výsledek při `Off``Option Strict`.</span><span class="sxs-lookup"><span data-stu-id="6fbde-185">The following example illustrates the result when `Option Strict` is `Off`.</span></span>  
  
 [!code-vb[VbVbalrOperators#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#54)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#52)]  
  
 <span data-ttu-id="6fbde-186">Chcete-li odstranit nejednoznačnost, měli byste použít operátor `&` místo `+` pro zřetězení.</span><span class="sxs-lookup"><span data-stu-id="6fbde-186">To eliminate ambiguity, you should use the `&` operator instead of `+` for concatenation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fbde-187">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6fbde-187">See also</span></span>

- [<span data-ttu-id="6fbde-188">& – operátor</span><span class="sxs-lookup"><span data-stu-id="6fbde-188">& Operator</span></span>](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [<span data-ttu-id="6fbde-189">Operátory zřetězení</span><span class="sxs-lookup"><span data-stu-id="6fbde-189">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="6fbde-190">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="6fbde-190">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="6fbde-191">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="6fbde-191">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="6fbde-192">Priorita operátorů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6fbde-192">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="6fbde-193">Aritmetické operátory v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6fbde-193">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="6fbde-194">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="6fbde-194">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
