---
title: "+ Operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.+
helpviewer_keywords:
- arithmetic operators [Visual Basic], addition
- + operator
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
- sum operator [Visual Basic]
ms.assetid: 5694778f-0a2c-4539-8009-f66f318fb46d
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fb0d66db2d777c046ccec69acc1f2069d21baf6c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="61cdf-102">+ – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61cdf-102">+ Operator (Visual Basic)</span></span>
<span data-ttu-id="61cdf-103">Sečte dvě čísla nebo vrátí kladnou hodnotu číselného výrazu.</span><span class="sxs-lookup"><span data-stu-id="61cdf-103">Adds two numbers or returns the positive value of a numeric expression.</span></span> <span data-ttu-id="61cdf-104">Můžete také použít ke zřetězení dvou výrazů řetězec.</span><span class="sxs-lookup"><span data-stu-id="61cdf-104">Can also be used to concatenate two string expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61cdf-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61cdf-105">Syntax</span></span>  
  
```  
      expression1 + expression2  
- or -  
+ expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="61cdf-106">Součásti</span><span class="sxs-lookup"><span data-stu-id="61cdf-106">Parts</span></span>  
  
|<span data-ttu-id="61cdf-107">Termín</span><span class="sxs-lookup"><span data-stu-id="61cdf-107">Term</span></span>|<span data-ttu-id="61cdf-108">Definice</span><span class="sxs-lookup"><span data-stu-id="61cdf-108">Definition</span></span>|  
|---|---|  
|`expression1`|<span data-ttu-id="61cdf-109">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="61cdf-109">Required.</span></span> <span data-ttu-id="61cdf-110">Číselný nebo řetězec výraz.</span><span class="sxs-lookup"><span data-stu-id="61cdf-110">Any numeric or string expression.</span></span>|  
|`expression2`|<span data-ttu-id="61cdf-111">Vyžaduje, pokud `+` operátor je výpočet zápornou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="61cdf-111">Required unless the `+` operator is calculating a negative value.</span></span> <span data-ttu-id="61cdf-112">Číselný nebo řetězec výraz.</span><span class="sxs-lookup"><span data-stu-id="61cdf-112">Any numeric or string expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="61cdf-113">Výsledek</span><span class="sxs-lookup"><span data-stu-id="61cdf-113">Result</span></span>  
 <span data-ttu-id="61cdf-114">Pokud `expression1` a `expression2` jsou obě číselné, výsledkem je jejich aritmetické součet.</span><span class="sxs-lookup"><span data-stu-id="61cdf-114">If `expression1` and `expression2` are both numeric, the result is their arithmetic sum.</span></span>  
  
 <span data-ttu-id="61cdf-115">Pokud `expression2` chybí, `+` operátor je *unární* operátor identity pro beze změny hodnotu výrazu.</span><span class="sxs-lookup"><span data-stu-id="61cdf-115">If `expression2` is absent, the `+` operator is the *unary* identity operator for the unchanged value of an expression.</span></span> <span data-ttu-id="61cdf-116">V tomto smyslu operaci se skládá z ponechá znaménko `expression1`, takže výsledek je záporný, pokud `expression1` záporné.</span><span class="sxs-lookup"><span data-stu-id="61cdf-116">In this sense, the operation consists of retaining the sign of `expression1`, so the result is negative if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="61cdf-117">Pokud `expression1` a `expression2` jsou oba řetězce, výsledkem je zřetězení jejich hodnot.</span><span class="sxs-lookup"><span data-stu-id="61cdf-117">If `expression1` and `expression2` are both strings, the result is the concatenation of their values.</span></span>  
  
 <span data-ttu-id="61cdf-118">Pokud `expression1` a `expression2` jsou smíšené typů akci prováděnou závisí na jejich typy, jejich obsah a nastavení [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="61cdf-118">If `expression1` and `expression2` are of mixed types, the action taken depends on their types, their contents, and the setting of the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span> <span data-ttu-id="61cdf-119">Další informace najdete v tématu tabulky v "Poznámky."</span><span class="sxs-lookup"><span data-stu-id="61cdf-119">For more information, see the tables in "Remarks."</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="61cdf-120">Podporované typy</span><span class="sxs-lookup"><span data-stu-id="61cdf-120">Supported Types</span></span>  
 <span data-ttu-id="61cdf-121">Všechny číselné typy, včetně typy bez znaménka a s plovoucí desetinnou čárkou a `Decimal`, a `String`.</span><span class="sxs-lookup"><span data-stu-id="61cdf-121">All numeric types, including the unsigned and floating-point types and `Decimal`, and `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61cdf-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="61cdf-122">Remarks</span></span>  
 <span data-ttu-id="61cdf-123">Obecně platí `+` provede aritmetické přidání, pokud je to možné a zřetězí, pouze pokud jsou oba výrazy řetězce.</span><span class="sxs-lookup"><span data-stu-id="61cdf-123">In general, `+` performs arithmetic addition when possible, and concatenates only when both expressions are strings.</span></span>  
  
 <span data-ttu-id="61cdf-124">Pokud ani výraz `Object`, Visual Basic provede následující akce.</span><span class="sxs-lookup"><span data-stu-id="61cdf-124">If neither expression is an `Object`, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="61cdf-125">Datové typy výrazů</span><span class="sxs-lookup"><span data-stu-id="61cdf-125">Data types of expressions</span></span>|<span data-ttu-id="61cdf-126">Akce kompilátorem</span><span class="sxs-lookup"><span data-stu-id="61cdf-126">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="61cdf-127">Číselné datové typy jsou oba výrazy (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, nebo `Double`)</span><span class="sxs-lookup"><span data-stu-id="61cdf-127">Both expressions are numeric data types (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`)</span></span>|<span data-ttu-id="61cdf-128">Přidáte.</span><span class="sxs-lookup"><span data-stu-id="61cdf-128">Add.</span></span> <span data-ttu-id="61cdf-129">Datový typ výsledků je vhodné pro datové typy číselného typu `expression1` a `expression2`.</span><span class="sxs-lookup"><span data-stu-id="61cdf-129">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="61cdf-130">Podívejte se na tabulky "Celočíselné aritmetiky" v [typy výsledků operátoru Data](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="61cdf-130">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="61cdf-131">Jsou oba výrazy typu`String`</span><span class="sxs-lookup"><span data-stu-id="61cdf-131">Both expressions are of type `String`</span></span>|<span data-ttu-id="61cdf-132">Zřetězení.</span><span class="sxs-lookup"><span data-stu-id="61cdf-132">Concatenate.</span></span>|  
|<span data-ttu-id="61cdf-133">Jeden výraz je číselný datový typ a druhá je řetězec</span><span class="sxs-lookup"><span data-stu-id="61cdf-133">One expression is a numeric data type and the other is a string</span></span>|<span data-ttu-id="61cdf-134">Pokud `Option Strict` je `On`, pak vygenerována chyba kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="61cdf-134">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="61cdf-135">Pokud `Option Strict` je `Off`, pak implicitně převést `String` k `Double` a přidejte.</span><span class="sxs-lookup"><span data-stu-id="61cdf-135">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="61cdf-136">Pokud `String` nelze převést na `Double`, pak throw <xref:System.InvalidCastException> výjimka.</span><span class="sxs-lookup"><span data-stu-id="61cdf-136">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="61cdf-137">Jeden výraz je číselný datový typ, a druhá je [nic](../../../visual-basic/language-reference/nothing.md)</span><span class="sxs-lookup"><span data-stu-id="61cdf-137">One expression is a numeric data type, and the other is [Nothing](../../../visual-basic/language-reference/nothing.md)</span></span>|<span data-ttu-id="61cdf-138">Přidat, s `Nothing` s hodnotou nula.</span><span class="sxs-lookup"><span data-stu-id="61cdf-138">Add, with `Nothing` valued as zero.</span></span>|  
|<span data-ttu-id="61cdf-139">Jeden výraz je řetězec, a druhá je`Nothing`</span><span class="sxs-lookup"><span data-stu-id="61cdf-139">One expression is a string, and the other is `Nothing`</span></span>|<span data-ttu-id="61cdf-140">Zřetězení s `Nothing` cenná jako "".</span><span class="sxs-lookup"><span data-stu-id="61cdf-140">Concatenate, with `Nothing` valued as "".</span></span>|  
  
 <span data-ttu-id="61cdf-141">Pokud je jeden výraz `Object` výrazu jazyka Visual Basic provede následující akce.</span><span class="sxs-lookup"><span data-stu-id="61cdf-141">If one expression is an `Object` expression, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="61cdf-142">Datové typy výrazů</span><span class="sxs-lookup"><span data-stu-id="61cdf-142">Data types of expressions</span></span>|<span data-ttu-id="61cdf-143">Akce kompilátorem</span><span class="sxs-lookup"><span data-stu-id="61cdf-143">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="61cdf-144">`Object`výraz obsahuje číselnou hodnotu a druhá je číselný datový typ.</span><span class="sxs-lookup"><span data-stu-id="61cdf-144">`Object` expression holds a numeric value and the other is a numeric data type</span></span>|<span data-ttu-id="61cdf-145">Pokud `Option Strict` je `On`, pak vygenerována chyba kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="61cdf-145">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="61cdf-146">Pokud `Option Strict` je `Off`, pak přidat.</span><span class="sxs-lookup"><span data-stu-id="61cdf-146">If `Option Strict` is `Off`, then add.</span></span>|  
|<span data-ttu-id="61cdf-147">`Object`výraz obsahuje číselnou hodnotu a druhá je typu`String`</span><span class="sxs-lookup"><span data-stu-id="61cdf-147">`Object` expression holds a numeric value and the other is of type `String`</span></span>|<span data-ttu-id="61cdf-148">Pokud `Option Strict` je `On`, pak vygenerována chyba kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="61cdf-148">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="61cdf-149">Pokud `Option Strict` je `Off`, pak implicitně převést `String` k `Double` a přidejte.</span><span class="sxs-lookup"><span data-stu-id="61cdf-149">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="61cdf-150">Pokud `String` nelze převést na `Double`, pak throw <xref:System.InvalidCastException> výjimka.</span><span class="sxs-lookup"><span data-stu-id="61cdf-150">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="61cdf-151">`Object`výraz obsahuje řetězec a druhá je číselný datový typ.</span><span class="sxs-lookup"><span data-stu-id="61cdf-151">`Object` expression holds a string and the other is a numeric data type</span></span>|<span data-ttu-id="61cdf-152">Pokud `Option Strict` je `On`, pak vygenerována chyba kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="61cdf-152">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="61cdf-153">Pokud `Option Strict` je `Off`, implicitně převést řetězec `Object` k `Double` a přidejte.</span><span class="sxs-lookup"><span data-stu-id="61cdf-153">If `Option Strict` is `Off`, then implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="61cdf-154">Pokud řetězec `Object` nelze převést na `Double`, pak throw <xref:System.InvalidCastException> výjimka.</span><span class="sxs-lookup"><span data-stu-id="61cdf-154">If the string `Object` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="61cdf-155">`Object`výraz obsahuje řetězec a druhá je typu`String`</span><span class="sxs-lookup"><span data-stu-id="61cdf-155">`Object` expression holds a string and the other is of type `String`</span></span>|<span data-ttu-id="61cdf-156">Pokud `Option Strict` je `On`, pak vygenerována chyba kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="61cdf-156">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="61cdf-157">Pokud `Option Strict` je `Off`, pak implicitně převést `Object` k `String` a zřetězení.</span><span class="sxs-lookup"><span data-stu-id="61cdf-157">If `Option Strict` is `Off`, then implicitly convert `Object` to `String` and concatenate.</span></span>|  
  
 <span data-ttu-id="61cdf-158">Pokud jsou oba výrazy `Object` výrazy jazyka Visual Basic provede následující akce (`Option Strict Off` pouze).</span><span class="sxs-lookup"><span data-stu-id="61cdf-158">If both expressions are `Object` expressions, Visual Basic takes the following actions (`Option Strict Off` only).</span></span>  
  
|<span data-ttu-id="61cdf-159">Datové typy výrazů</span><span class="sxs-lookup"><span data-stu-id="61cdf-159">Data types of expressions</span></span>|<span data-ttu-id="61cdf-160">Akce kompilátorem</span><span class="sxs-lookup"><span data-stu-id="61cdf-160">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="61cdf-161">Obě `Object` výrazy uložení číselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="61cdf-161">Both `Object` expressions hold numeric values</span></span>|<span data-ttu-id="61cdf-162">Přidáte.</span><span class="sxs-lookup"><span data-stu-id="61cdf-162">Add.</span></span>|  
|<span data-ttu-id="61cdf-163">Obě `Object` výrazy jsou typu`String`</span><span class="sxs-lookup"><span data-stu-id="61cdf-163">Both `Object` expressions are of type `String`</span></span>|<span data-ttu-id="61cdf-164">Zřetězení.</span><span class="sxs-lookup"><span data-stu-id="61cdf-164">Concatenate.</span></span>|  
|<span data-ttu-id="61cdf-165">Jeden `Object` výraz obsahuje číselnou hodnotu a dalších obsahuje řetězec</span><span class="sxs-lookup"><span data-stu-id="61cdf-165">One `Object` expression holds a numeric value and the other holds a string</span></span>|<span data-ttu-id="61cdf-166">Implicitně převést řetězec `Object` k `Double` a přidejte.</span><span class="sxs-lookup"><span data-stu-id="61cdf-166">Implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="61cdf-167">Pokud řetězec `Object` nelze převést na číselnou hodnotu, pak throw <xref:System.InvalidCastException> výjimka.</span><span class="sxs-lookup"><span data-stu-id="61cdf-167">If the string `Object` cannot be converted to a numeric value, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
  
 <span data-ttu-id="61cdf-168">Pokud má jedna `Object` výraz vyhodnocen jako [nic](../../../visual-basic/language-reference/nothing.md) nebo <xref:System.DBNull>, `+` operátor považuje za `String` s hodnotou "".</span><span class="sxs-lookup"><span data-stu-id="61cdf-168">If either `Object` expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md) or <xref:System.DBNull>, the `+` operator treats it as a `String` with a value of "".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="61cdf-169">Při použití `+` operátor, nemusí být schopní určit, zda dojde k přidání nebo řetězec zřetězení.</span><span class="sxs-lookup"><span data-stu-id="61cdf-169">When you use the `+` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="61cdf-170">Použití `&` operátor řetězení odstranit nejednoznačnost a k poskytování samoobslužných dokumentů kódu.</span><span class="sxs-lookup"><span data-stu-id="61cdf-170">Use the `&` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="61cdf-171">Přetížení</span><span class="sxs-lookup"><span data-stu-id="61cdf-171">Overloading</span></span>  
 <span data-ttu-id="61cdf-172">`+` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="61cdf-172">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="61cdf-173">Pokud váš kód používá tento operátor na takové třídu nebo strukturu, ujistěte se, že rozumíte své Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="61cdf-173">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="61cdf-174">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="61cdf-174">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="61cdf-175">Příklad</span><span class="sxs-lookup"><span data-stu-id="61cdf-175">Example</span></span>  
 <span data-ttu-id="61cdf-176">Následující příklad používá `+` operátor přidat čísla.</span><span class="sxs-lookup"><span data-stu-id="61cdf-176">The following example uses the `+` operator to add numbers.</span></span> <span data-ttu-id="61cdf-177">Pokud operandy číselné, Visual Basic vypočte aritmetický výsledek.</span><span class="sxs-lookup"><span data-stu-id="61cdf-177">If the operands are both numeric, Visual Basic computes the arithmetic result.</span></span> <span data-ttu-id="61cdf-178">Aritmetické výsledek představuje součet hodnot dva operandy.</span><span class="sxs-lookup"><span data-stu-id="61cdf-178">The arithmetic result represents the sum of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#6](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_1.vb)]  
  
 <span data-ttu-id="61cdf-179">Můžete také `+` operátor ke zřetězení řetězců.</span><span class="sxs-lookup"><span data-stu-id="61cdf-179">You can also use the `+` operator to concatenate strings.</span></span> <span data-ttu-id="61cdf-180">Pokud operandy oba řetězce, Visual Basic je zřetězí.</span><span class="sxs-lookup"><span data-stu-id="61cdf-180">If the operands are both strings, Visual Basic concatenates them.</span></span> <span data-ttu-id="61cdf-181">Výsledek zřetězení představuje jeden řetězec sestávající z obsah dva operandy jedna po druhé.</span><span class="sxs-lookup"><span data-stu-id="61cdf-181">The concatenation result represents a single string consisting of the contents of the two operands one after the other.</span></span>  
  
 <span data-ttu-id="61cdf-182">Pokud operandy smíšený typů, výsledek bude záviset na nastavení jazyka [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="61cdf-182">If the operands are of mixed types, the result depends on the setting of the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span> <span data-ttu-id="61cdf-183">Následující příklad ilustruje výsledek při `Option Strict` je `On`.</span><span class="sxs-lookup"><span data-stu-id="61cdf-183">The following example illustrates the result when `Option Strict` is `On`.</span></span>  
  
 [!code-vb[VbVbalrOperators#53](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_2.vb)]  
  
 [!code-vb[VbVbalrOperators#50](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]  
[!code-vb[VbVbalrOperators#51](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_4.vb)]  
  
 <span data-ttu-id="61cdf-184">Následující příklad ilustruje výsledek při `Option Strict` je `Off`.</span><span class="sxs-lookup"><span data-stu-id="61cdf-184">The following example illustrates the result when `Option Strict` is `Off`.</span></span>  
  
 [!code-vb[VbVbalrOperators#54](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_5.vb)]  
  
 [!code-vb[VbVbalrOperators#50](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]  
[!code-vb[VbVbalrOperators#52](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_6.vb)]  
  
 <span data-ttu-id="61cdf-185">Chcete-li odstranit nejednoznačnost, použijte `&` operátor místo `+` pro zřetězení.</span><span class="sxs-lookup"><span data-stu-id="61cdf-185">To eliminate ambiguity, you should use the `&` operator instead of `+` for concatenation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61cdf-186">Viz také</span><span class="sxs-lookup"><span data-stu-id="61cdf-186">See Also</span></span>  
 [<span data-ttu-id="61cdf-187">& – Operátor</span><span class="sxs-lookup"><span data-stu-id="61cdf-187">& Operator</span></span>](../../../visual-basic/language-reference/operators/concatenation-operator.md)  
 [<span data-ttu-id="61cdf-188">Operátory zřetězení</span><span class="sxs-lookup"><span data-stu-id="61cdf-188">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [<span data-ttu-id="61cdf-189">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="61cdf-189">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="61cdf-190">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="61cdf-190">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="61cdf-191">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="61cdf-191">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="61cdf-192">Aritmetické operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="61cdf-192">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="61cdf-193">Option Strict – příkaz</span><span class="sxs-lookup"><span data-stu-id="61cdf-193">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
