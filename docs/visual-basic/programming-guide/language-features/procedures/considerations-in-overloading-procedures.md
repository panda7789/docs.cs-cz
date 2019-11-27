---
title: Aspekty přetížení procedur
ms.date: 07/20/2015
helpviewer_keywords:
- signatures [Visual Basic], ParamArray arguments
- ParamArray keyword [Visual Basic], parameter arrays
- ParamArray keyword [Visual Basic], arguments and signatures
- function overloading [Visual Basic], implicit overloads for ParamArray
- ParamArray keyword [Visual Basic], signatures
- Visual Basic code, procedures
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], overloading
- parameters [Visual Basic], lists
- function overloading [Visual Basic], typeless programming
- typeless programming
- function overloading [Visual Basic], restrictions
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], overloading
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- parameter arrays [Visual Basic], overloading arguments
- Visual Basic code, parameter lists
- procedure overloading [Visual Basic], considerations
- Option Explicit statement [Visual Basic]
- restrictions [Visual Basic], overloading procedures
- procedures [Visual Basic], parameter lists
ms.assetid: a2001248-10d0-42c5-b0ce-eeedc987319f
ms.openlocfilehash: 4a0cfe176a59b3f90f5850ae8b4e34784c400c6b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351001"
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a><span data-ttu-id="cec0e-102">Aspekty přetížení procedur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cec0e-102">Considerations in Overloading Procedures (Visual Basic)</span></span>
<span data-ttu-id="cec0e-103">Pokud převedete proceduru, musíte pro každou přetíženou verzi použít jiný *podpis* .</span><span class="sxs-lookup"><span data-stu-id="cec0e-103">When you overload a procedure, you must use a different *signature* for each overloaded version.</span></span> <span data-ttu-id="cec0e-104">To obvykle znamená, že každá verze musí určovat jiný seznam parametrů.</span><span class="sxs-lookup"><span data-stu-id="cec0e-104">This usually means each version must specify a different parameter list.</span></span> <span data-ttu-id="cec0e-105">Další informace naleznete v části "různé signatury" v tématu [Process Overloads](./procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="cec0e-105">For more information, see "Different Signature" in [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
 <span data-ttu-id="cec0e-106">Můžete přetížit `Function` proceduru pomocí `Sub` procedury a naopak, pokud mají různé signatury.</span><span class="sxs-lookup"><span data-stu-id="cec0e-106">You can overload a `Function` procedure with a `Sub` procedure, and vice versa, provided they have different signatures.</span></span> <span data-ttu-id="cec0e-107">Dvě přetížení se nemohou lišit pouze v tom, že jedna má návratovou hodnotu a druhá ne.</span><span class="sxs-lookup"><span data-stu-id="cec0e-107">Two overloads cannot differ only in that one has a return value and the other does not.</span></span>  
  
 <span data-ttu-id="cec0e-108">Můžete přetížit vlastnost stejným způsobem jako procedura přetížení a se stejnými omezeními.</span><span class="sxs-lookup"><span data-stu-id="cec0e-108">You can overload a property the same way you overload a procedure, and with the same restrictions.</span></span> <span data-ttu-id="cec0e-109">Nemůžete však přetížit proceduru s vlastností, ani naopak.</span><span class="sxs-lookup"><span data-stu-id="cec0e-109">However, you cannot overload a procedure with a property, or vice versa.</span></span>  
  
## <a name="alternatives-to-overloaded-versions"></a><span data-ttu-id="cec0e-110">Alternativy k přetíženým verzím</span><span class="sxs-lookup"><span data-stu-id="cec0e-110">Alternatives to Overloaded Versions</span></span>  
 <span data-ttu-id="cec0e-111">Někdy máte alternativu k přetíženým verzím, zejména v případě, že je přítomnost argumentů volitelná nebo jejich počet je proměnná.</span><span class="sxs-lookup"><span data-stu-id="cec0e-111">You sometimes have alternatives to overloaded versions, particularly when the presence of arguments is optional or their number is variable.</span></span>  
  
 <span data-ttu-id="cec0e-112">Mějte na paměti, že volitelné argumenty nejsou nutně podporovány všemi jazyky a pole parametrů jsou omezeny na Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cec0e-112">Keep in mind that optional arguments are not necessarily supported by all languages, and parameter arrays are limited to Visual Basic.</span></span> <span data-ttu-id="cec0e-113">Pokud píšete proceduru, která je pravděpodobně volána z kódu napsaného v některém z několika různých jazyků, přetížené verze nabízejí největší flexibilitu.</span><span class="sxs-lookup"><span data-stu-id="cec0e-113">If you are writing a procedure that is likely to be called from code written in any of several different languages, overloaded versions offer the greatest flexibility.</span></span>  
  
### <a name="overloads-and-optional-arguments"></a><span data-ttu-id="cec0e-114">Přetížení a volitelné argumenty</span><span class="sxs-lookup"><span data-stu-id="cec0e-114">Overloads and Optional Arguments</span></span>  
 <span data-ttu-id="cec0e-115">Když volající kód může volitelně zadat nebo vynechat jeden nebo více argumentů, můžete definovat více přetížených verzí nebo použít volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="cec0e-115">When the calling code can optionally supply or omit one or more arguments, you can define multiple overloaded versions or use optional parameters.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="cec0e-116">Kdy použít přetížené verze</span><span class="sxs-lookup"><span data-stu-id="cec0e-116">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="cec0e-117">Můžete zvážit definování řady přetížených verzí v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="cec0e-117">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
- <span data-ttu-id="cec0e-118">Logika v kódu procedury je výrazně odlišná v závislosti na tom, zda volající kód dodává nepovinný argument nebo ne.</span><span class="sxs-lookup"><span data-stu-id="cec0e-118">The logic in the procedure code is significantly different depending on whether the calling code supplies an optional argument or not.</span></span>  
  
- <span data-ttu-id="cec0e-119">Kód procedury nemůže spolehlivě testovat, zda volající kód zadal volitelný argument.</span><span class="sxs-lookup"><span data-stu-id="cec0e-119">The procedure code cannot reliably test whether the calling code has supplied an optional argument.</span></span> <span data-ttu-id="cec0e-120">Jedná se například o případ, kdy není možný kandidát na výchozí hodnotu, kterou by volající kód nemohl dodat.</span><span class="sxs-lookup"><span data-stu-id="cec0e-120">This is the case, for example, if there is no possible candidate for a default value that the calling code could not be expected to supply.</span></span>  
  
#### <a name="when-to-use-optional-parameters"></a><span data-ttu-id="cec0e-121">Kdy použít volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="cec0e-121">When to Use Optional Parameters</span></span>  
 <span data-ttu-id="cec0e-122">V následujících případech můžete preferovat jeden nebo více volitelných parametrů:</span><span class="sxs-lookup"><span data-stu-id="cec0e-122">You might prefer one or more optional parameters in the following cases:</span></span>  
  
- <span data-ttu-id="cec0e-123">Jediná požadovaná akce, když volající kód neposkytne volitelný argument, je nastavit parametr na výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cec0e-123">The only required action when the calling code does not supply an optional argument is to set the parameter to a default value.</span></span> <span data-ttu-id="cec0e-124">V takovém případě může být kód procedury méně komplikovaný, pokud definujete jednu verzi s jedním nebo více `Optional` parametry.</span><span class="sxs-lookup"><span data-stu-id="cec0e-124">In such a case, the procedure code can be less complicated if you define a single version with one or more `Optional` parameters.</span></span>  
  
 <span data-ttu-id="cec0e-125">Další informace najdete v tématu [volitelné parametry](./optional-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="cec0e-125">For more information, see [Optional Parameters](./optional-parameters.md).</span></span>  
  
### <a name="overloads-and-paramarrays"></a><span data-ttu-id="cec0e-126">Přetížení a ParamArray</span><span class="sxs-lookup"><span data-stu-id="cec0e-126">Overloads and ParamArrays</span></span>  
 <span data-ttu-id="cec0e-127">Když volající kód může předat proměnný počet argumentů, můžete definovat více přetížených verzí nebo použít pole parametrů.</span><span class="sxs-lookup"><span data-stu-id="cec0e-127">When the calling code can pass a variable number of arguments, you can define multiple overloaded versions or use a parameter array.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="cec0e-128">Kdy použít přetížené verze</span><span class="sxs-lookup"><span data-stu-id="cec0e-128">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="cec0e-129">Můžete zvážit definování řady přetížených verzí v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="cec0e-129">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
- <span data-ttu-id="cec0e-130">Víte, že volající kód nikdy nepředává více než malý počet hodnot do pole parametrů.</span><span class="sxs-lookup"><span data-stu-id="cec0e-130">You know that the calling code never passes more than a small number of values to the parameter array.</span></span>  
  
- <span data-ttu-id="cec0e-131">Logika v kódu procedury je výrazně odlišná v závislosti na tom, kolik hodnot volající kód předává.</span><span class="sxs-lookup"><span data-stu-id="cec0e-131">The logic in the procedure code is significantly different depending on how many values the calling code passes.</span></span>  
  
- <span data-ttu-id="cec0e-132">Volající kód může předat hodnoty různých datových typů.</span><span class="sxs-lookup"><span data-stu-id="cec0e-132">The calling code can pass values of different data types.</span></span>  
  
#### <a name="when-to-use-a-parameter-array"></a><span data-ttu-id="cec0e-133">Kdy použít pole parametrů</span><span class="sxs-lookup"><span data-stu-id="cec0e-133">When to Use a Parameter Array</span></span>  
 <span data-ttu-id="cec0e-134">V následujících případech je lepší obsluhou `ParamArray` parametrem:</span><span class="sxs-lookup"><span data-stu-id="cec0e-134">You are better served by a `ParamArray` parameter in the following cases:</span></span>  
  
- <span data-ttu-id="cec0e-135">Nemůžete odhadnout, kolik hodnot může volající kód předat poli parametrů, a může to být velké číslo.</span><span class="sxs-lookup"><span data-stu-id="cec0e-135">You are not able to predict how many values the calling code can pass to the parameter array, and it could be a large number.</span></span>  
  
- <span data-ttu-id="cec0e-136">Procedura procedury je sama o sobě k iterování všech hodnot, které volající kód projde, a provádí v podstatě stejné operace na každé hodnotě.</span><span class="sxs-lookup"><span data-stu-id="cec0e-136">The procedure logic lends itself to iterating through all the values the calling code passes, performing essentially the same operations on every value.</span></span>  
  
 <span data-ttu-id="cec0e-137">Další informace naleznete v tématu [pole parametrů](./parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="cec0e-137">For more information, see [Parameter Arrays](./parameter-arrays.md).</span></span>  
  
## <a name="implicit-overloads-for-optional-parameters"></a><span data-ttu-id="cec0e-138">Implicitní přetížení pro volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="cec0e-138">Implicit Overloads for Optional Parameters</span></span>  
 <span data-ttu-id="cec0e-139">Procedura s [volitelným](../../../../visual-basic/language-reference/modifiers/optional.md) parametrem je ekvivalentní dvou přetíženým procedurám, jeden s volitelným parametrem a druhý bez něj.</span><span class="sxs-lookup"><span data-stu-id="cec0e-139">A procedure with an [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameter is equivalent to two overloaded procedures, one with the optional parameter and one without it.</span></span> <span data-ttu-id="cec0e-140">Taková procedura se nedá přetížit se seznamem parametrů, který odpovídá některé z nich.</span><span class="sxs-lookup"><span data-stu-id="cec0e-140">You cannot overload such a procedure with a parameter list corresponding to either of these.</span></span> <span data-ttu-id="cec0e-141">Tuto ilustraci ilustrují následující deklarace.</span><span class="sxs-lookup"><span data-stu-id="cec0e-141">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#58)]  
  
 [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
 [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
 <span data-ttu-id="cec0e-142">Pro proceduru s více než jedním volitelným parametrem je množina implicitních přetížení, kterou dorazila v logice podobně jako v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="cec0e-142">For a procedure with more than one optional parameter, there is a set of implicit overloads, arrived at by logic similar to that in the preceding example.</span></span>  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a><span data-ttu-id="cec0e-143">Implicitní přetížení parametru ParamArray</span><span class="sxs-lookup"><span data-stu-id="cec0e-143">Implicit Overloads for a ParamArray Parameter</span></span>  
 <span data-ttu-id="cec0e-144">Kompilátor považuje proceduru s parametrem [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) za nekonečný počet přetížení a liší se od sebe v tom, co volající kód předává do pole parametrů, následovně:</span><span class="sxs-lookup"><span data-stu-id="cec0e-144">The compiler considers a procedure with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter to have an infinite number of overloads, differing from each other in what the calling code passes to the parameter array, as follows:</span></span>  
  
- <span data-ttu-id="cec0e-145">Jedno přetížení pro, když volající kód nedodá argument pro `ParamArray`</span><span class="sxs-lookup"><span data-stu-id="cec0e-145">One overload for when the calling code does not supply an argument to the `ParamArray`</span></span>  
  
- <span data-ttu-id="cec0e-146">Jedno přetížení pro, když volající kód dodá jednorozměrné pole typu elementu `ParamArray`.</span><span class="sxs-lookup"><span data-stu-id="cec0e-146">One overload for when the calling code supplies a one-dimensional array of the `ParamArray` element type</span></span>  
  
- <span data-ttu-id="cec0e-147">Pro každé kladné celé číslo jedno přetížení pro, když volající kód dodá tento počet argumentů, každý z `ParamArray` typ elementu.</span><span class="sxs-lookup"><span data-stu-id="cec0e-147">For every positive integer, one overload for when the calling code supplies that number of arguments, each of the `ParamArray` element type</span></span>  
  
 <span data-ttu-id="cec0e-148">Následující deklarace ilustrují tato implicitní přetížení.</span><span class="sxs-lookup"><span data-stu-id="cec0e-148">The following declarations illustrate these implicit overloads.</span></span>  
  
 [!code-vb[VbVbcnProcedures#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#68)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 <span data-ttu-id="cec0e-149">Taková procedura se nedá přetížit se seznamem parametrů, který přebírá jednorozměrné pole pro pole parametrů.</span><span class="sxs-lookup"><span data-stu-id="cec0e-149">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="cec0e-150">Můžete však použít signatury dalších implicitních přetížení.</span><span class="sxs-lookup"><span data-stu-id="cec0e-150">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="cec0e-151">Tuto ilustraci ilustrují následující deklarace.</span><span class="sxs-lookup"><span data-stu-id="cec0e-151">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a><span data-ttu-id="cec0e-152">Programování jako alternativa k přetížení</span><span class="sxs-lookup"><span data-stu-id="cec0e-152">Typeless Programming as an Alternative to Overloading</span></span>  
 <span data-ttu-id="cec0e-153">Pokud chcete, aby volající kód předával jiné datové typy parametru, alternativním přístupem je beztyp programování.</span><span class="sxs-lookup"><span data-stu-id="cec0e-153">If you want to allow the calling code to pass different data types to a parameter, an alternative approach is typeless programming.</span></span> <span data-ttu-id="cec0e-154">Můžete nastavit přepínač pro kontrolu typu na `Off` s použitím [příkazu Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) nebo pomocí možnosti kompilátoru [-OptionStrict –](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) .</span><span class="sxs-lookup"><span data-stu-id="cec0e-154">You can set the type checking switch to `Off` with either the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) or the [-optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) compiler option.</span></span> <span data-ttu-id="cec0e-155">Pak nemusíte deklarovat datový typ parametru.</span><span class="sxs-lookup"><span data-stu-id="cec0e-155">Then you do not have to declare the parameter's data type.</span></span> <span data-ttu-id="cec0e-156">Tento přístup ale má v porovnání s přetížením následující nevýhody:</span><span class="sxs-lookup"><span data-stu-id="cec0e-156">However, this approach has the following disadvantages compared to overloading:</span></span>  
  
- <span data-ttu-id="cec0e-157">Programování bez typů produkuje méně efektivní kód spuštění.</span><span class="sxs-lookup"><span data-stu-id="cec0e-157">Typeless programming produces less efficient execution code.</span></span>  
  
- <span data-ttu-id="cec0e-158">Procedura musí být testována pro každý datový typ, který předpokládá předání.</span><span class="sxs-lookup"><span data-stu-id="cec0e-158">The procedure must test for every data type it anticipates being passed.</span></span>  
  
- <span data-ttu-id="cec0e-159">Kompilátor nemůže signalizovat chybu, pokud volající kód předává datový typ, který procedura nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="cec0e-159">The compiler cannot signal an error if the calling code passes a data type that the procedure does not support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cec0e-160">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cec0e-160">See also</span></span>

- [<span data-ttu-id="cec0e-161">Procedury</span><span class="sxs-lookup"><span data-stu-id="cec0e-161">Procedures</span></span>](./index.md)
- [<span data-ttu-id="cec0e-162">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="cec0e-162">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="cec0e-163">Řešení potíží s procedurami</span><span class="sxs-lookup"><span data-stu-id="cec0e-163">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="cec0e-164">Postupy: Definice více verzí procedury</span><span class="sxs-lookup"><span data-stu-id="cec0e-164">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="cec0e-165">Postupy: Volání přetížené procedury</span><span class="sxs-lookup"><span data-stu-id="cec0e-165">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="cec0e-166">Postupy: Přetížení procedury, která přebírá nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="cec0e-166">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="cec0e-167">Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů</span><span class="sxs-lookup"><span data-stu-id="cec0e-167">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="cec0e-168">Řešení přetížení</span><span class="sxs-lookup"><span data-stu-id="cec0e-168">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="cec0e-169">Overloads</span><span class="sxs-lookup"><span data-stu-id="cec0e-169">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
