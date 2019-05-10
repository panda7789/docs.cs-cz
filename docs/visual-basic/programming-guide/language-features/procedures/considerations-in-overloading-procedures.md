---
title: Aspekty přetížení procedur (Visual Basic)
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
ms.openlocfilehash: b5a26a8b68a2f786213aa49f30247d692b3de2f7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649648"
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a><span data-ttu-id="666fa-102">Aspekty přetížení procedur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="666fa-102">Considerations in Overloading Procedures (Visual Basic)</span></span>
<span data-ttu-id="666fa-103">Když je přetížení procedury, musíte použít jiný *podpis* jednotlivých přetížených verzí.</span><span class="sxs-lookup"><span data-stu-id="666fa-103">When you overload a procedure, you must use a different *signature* for each overloaded version.</span></span> <span data-ttu-id="666fa-104">To obvykle znamená, že každá verze musíte zadat seznam různých parametrů.</span><span class="sxs-lookup"><span data-stu-id="666fa-104">This usually means each version must specify a different parameter list.</span></span> <span data-ttu-id="666fa-105">Další informace najdete v tématu "Jiný podpis" [přetížení procedury](./procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="666fa-105">For more information, see "Different Signature" in [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
 <span data-ttu-id="666fa-106">Můžete použít přetížení `Function` procedury s `Sub` postupu a naopak, pokud mají různé podpisy.</span><span class="sxs-lookup"><span data-stu-id="666fa-106">You can overload a `Function` procedure with a `Sub` procedure, and vice versa, provided they have different signatures.</span></span> <span data-ttu-id="666fa-107">Dvě přetížení nemůže se liší pouze v tom, jedna má návratovou hodnotu a druhá ne.</span><span class="sxs-lookup"><span data-stu-id="666fa-107">Two overloads cannot differ only in that one has a return value and the other does not.</span></span>  
  
 <span data-ttu-id="666fa-108">Vlastnost můžete přetížit stejným způsobem jako přetížení procedury a omezení.</span><span class="sxs-lookup"><span data-stu-id="666fa-108">You can overload a property the same way you overload a procedure, and with the same restrictions.</span></span> <span data-ttu-id="666fa-109">Nelze však přetížení procedury s vlastností nebo naopak.</span><span class="sxs-lookup"><span data-stu-id="666fa-109">However, you cannot overload a procedure with a property, or vice versa.</span></span>  
  
## <a name="alternatives-to-overloaded-versions"></a><span data-ttu-id="666fa-110">Alternativy k přetížené verze</span><span class="sxs-lookup"><span data-stu-id="666fa-110">Alternatives to Overloaded Versions</span></span>  
 <span data-ttu-id="666fa-111">Máte někdy alternativy k přetížené verze, zejména pokud přítomnost argumentů je volitelný nebo jejich počet je proměnná.</span><span class="sxs-lookup"><span data-stu-id="666fa-111">You sometimes have alternatives to overloaded versions, particularly when the presence of arguments is optional or their number is variable.</span></span>  
  
 <span data-ttu-id="666fa-112">Mějte na paměti, že volitelné argumenty nejsou nutně nepodporuje všechny jazyky a pole parametrů jsou omezené na Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="666fa-112">Keep in mind that optional arguments are not necessarily supported by all languages, and parameter arrays are limited to Visual Basic.</span></span> <span data-ttu-id="666fa-113">Pokud píšete procedury, která by mohla být volány kódem napsaným v některém z několika různých jazyků, přetížené verze nabídky nejvyšší flexibilitu.</span><span class="sxs-lookup"><span data-stu-id="666fa-113">If you are writing a procedure that is likely to be called from code written in any of several different languages, overloaded versions offer the greatest flexibility.</span></span>  
  
### <a name="overloads-and-optional-arguments"></a><span data-ttu-id="666fa-114">Přetížení a nepovinné argumenty.</span><span class="sxs-lookup"><span data-stu-id="666fa-114">Overloads and Optional Arguments</span></span>  
 <span data-ttu-id="666fa-115">Pokud volající kód může volitelně můžete zadat nebo vynechat jeden nebo více argumentů, můžete definovat více přetížené verze nebo používat volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="666fa-115">When the calling code can optionally supply or omit one or more arguments, you can define multiple overloaded versions or use optional parameters.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="666fa-116">Kdy použít přetížené verze</span><span class="sxs-lookup"><span data-stu-id="666fa-116">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="666fa-117">Můžete zvážit, definování řadu přetížené verze v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="666fa-117">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
- <span data-ttu-id="666fa-118">Logika v kódu procedury je výrazně liší v závislosti na tom, zda volající kód poskytuje volitelný argument nebo ne.</span><span class="sxs-lookup"><span data-stu-id="666fa-118">The logic in the procedure code is significantly different depending on whether the calling code supplies an optional argument or not.</span></span>  
  
- <span data-ttu-id="666fa-119">Kód procedury nelze spolehlivě otestovat, zda volající kód dodal nepovinný argument.</span><span class="sxs-lookup"><span data-stu-id="666fa-119">The procedure code cannot reliably test whether the calling code has supplied an optional argument.</span></span> <span data-ttu-id="666fa-120">To platí, například, pokud neexistuje žádný možné Release candidate pro výchozí hodnotu, která volající kód nelze očekávat, že zadat.</span><span class="sxs-lookup"><span data-stu-id="666fa-120">This is the case, for example, if there is no possible candidate for a default value that the calling code could not be expected to supply.</span></span>  
  
#### <a name="when-to-use-optional-parameters"></a><span data-ttu-id="666fa-121">Kdy použít nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="666fa-121">When to Use Optional Parameters</span></span>  
 <span data-ttu-id="666fa-122">Můžete dát přednost jeden nebo více volitelných parametrů v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="666fa-122">You might prefer one or more optional parameters in the following cases:</span></span>  
  
- <span data-ttu-id="666fa-123">Pouze požadované akce, když volající kód neposkytuje nepovinný argument je nastavena na výchozí hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="666fa-123">The only required action when the calling code does not supply an optional argument is to set the parameter to a default value.</span></span> <span data-ttu-id="666fa-124">V takovém případě může být méně složitý kód procedury definujete jednu verzi s jednou nebo více `Optional` parametry.</span><span class="sxs-lookup"><span data-stu-id="666fa-124">In such a case, the procedure code can be less complicated if you define a single version with one or more `Optional` parameters.</span></span>  
  
 <span data-ttu-id="666fa-125">Další informace najdete v tématu [volitelné parametry](./optional-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="666fa-125">For more information, see [Optional Parameters](./optional-parameters.md).</span></span>  
  
### <a name="overloads-and-paramarrays"></a><span data-ttu-id="666fa-126">Přetížení a ParamArrays</span><span class="sxs-lookup"><span data-stu-id="666fa-126">Overloads and ParamArrays</span></span>  
 <span data-ttu-id="666fa-127">Pokud volající kód může předat proměnlivý počet argumentů, můžete definovat více přetížené verze nebo použití pole parametrů.</span><span class="sxs-lookup"><span data-stu-id="666fa-127">When the calling code can pass a variable number of arguments, you can define multiple overloaded versions or use a parameter array.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="666fa-128">Kdy použít přetížené verze</span><span class="sxs-lookup"><span data-stu-id="666fa-128">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="666fa-129">Můžete zvážit, definování řadu přetížené verze v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="666fa-129">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
- <span data-ttu-id="666fa-130">Víte, že volající kód nikdy neprocházejí více než malý počet hodnot pro pole parametrů.</span><span class="sxs-lookup"><span data-stu-id="666fa-130">You know that the calling code never passes more than a small number of values to the parameter array.</span></span>  
  
- <span data-ttu-id="666fa-131">Logika v kódu procedury je výrazně liší v závislosti na tom, kolik hodnot volající kód předá.</span><span class="sxs-lookup"><span data-stu-id="666fa-131">The logic in the procedure code is significantly different depending on how many values the calling code passes.</span></span>  
  
- <span data-ttu-id="666fa-132">Volající kód může předat hodnoty z různých datových typů.</span><span class="sxs-lookup"><span data-stu-id="666fa-132">The calling code can pass values of different data types.</span></span>  
  
#### <a name="when-to-use-a-parameter-array"></a><span data-ttu-id="666fa-133">Kdy použít pole parametrů.</span><span class="sxs-lookup"><span data-stu-id="666fa-133">When to Use a Parameter Array</span></span>  
 <span data-ttu-id="666fa-134">Budete se lépe vyhovovat `ParamArray` parametr v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="666fa-134">You are better served by a `ParamArray` parameter in the following cases:</span></span>  
  
- <span data-ttu-id="666fa-135">Nejste schopni předpovědět, kolik hodnot volající kód můžete předat pole parametrů a může to být hodně.</span><span class="sxs-lookup"><span data-stu-id="666fa-135">You are not able to predict how many values the calling code can pass to the parameter array, and it could be a large number.</span></span>  
  
- <span data-ttu-id="666fa-136">Logiky postup slouží k procházení všech hodnot volající kód předá, provádí se v podstatě stejné operace v každé hodnotě.</span><span class="sxs-lookup"><span data-stu-id="666fa-136">The procedure logic lends itself to iterating through all the values the calling code passes, performing essentially the same operations on every value.</span></span>  
  
 <span data-ttu-id="666fa-137">Další informace najdete v tématu [pole parametrů](./parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="666fa-137">For more information, see [Parameter Arrays](./parameter-arrays.md).</span></span>  
  
## <a name="implicit-overloads-for-optional-parameters"></a><span data-ttu-id="666fa-138">Implicitní přetížení pro volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="666fa-138">Implicit Overloads for Optional Parameters</span></span>  
 <span data-ttu-id="666fa-139">Procedura se [volitelné](../../../../visual-basic/language-reference/modifiers/optional.md) parametr je ekvivalentní na dvě přetížení procedury, jednu s volitelným parametrem a druhou bez parametru.</span><span class="sxs-lookup"><span data-stu-id="666fa-139">A procedure with an [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameter is equivalent to two overloaded procedures, one with the optional parameter and one without it.</span></span> <span data-ttu-id="666fa-140">Tento postup nejde přetížit se seznamem parametrů odpovídá buď z nich.</span><span class="sxs-lookup"><span data-stu-id="666fa-140">You cannot overload such a procedure with a parameter list corresponding to either of these.</span></span> <span data-ttu-id="666fa-141">Následující deklarace ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="666fa-141">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#58)]  
  
 [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
 [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
 <span data-ttu-id="666fa-142">Pro proceduru s více než jeden volitelný parametr je sada implicitní přetížení, které byly přijaty logikou podobné jako v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="666fa-142">For a procedure with more than one optional parameter, there is a set of implicit overloads, arrived at by logic similar to that in the preceding example.</span></span>  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a><span data-ttu-id="666fa-143">Implicitní přetížení pro ParamArray parametr</span><span class="sxs-lookup"><span data-stu-id="666fa-143">Implicit Overloads for a ParamArray Parameter</span></span>  
 <span data-ttu-id="666fa-144">Kompilátor považuje postupu názvem [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametr mít neomezený počet přetížení lišící se od sebe navzájem co volající kód předá pole parametrů, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="666fa-144">The compiler considers a procedure with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter to have an infinite number of overloads, differing from each other in what the calling code passes to the parameter array, as follows:</span></span>  
  
- <span data-ttu-id="666fa-145">Když volající kód neposkytuje argument pro jeden přetížená metoda `ParamArray`</span><span class="sxs-lookup"><span data-stu-id="666fa-145">One overload for when the calling code does not supply an argument to the `ParamArray`</span></span>  
  
- <span data-ttu-id="666fa-146">Jedním přetížením pro když volající kód poskytuje jednorozměrné pole `ParamArray` typ elementu</span><span class="sxs-lookup"><span data-stu-id="666fa-146">One overload for when the calling code supplies a one-dimensional array of the `ParamArray` element type</span></span>  
  
- <span data-ttu-id="666fa-147">Pro každý kladné celé číslo, jeden přetížení pro když volající kód poskytuje tento počet argumentů, každý z `ParamArray` typ elementu</span><span class="sxs-lookup"><span data-stu-id="666fa-147">For every positive integer, one overload for when the calling code supplies that number of arguments, each of the `ParamArray` element type</span></span>  
  
 <span data-ttu-id="666fa-148">Následující deklarace ukazují tyto implicitní přetížení.</span><span class="sxs-lookup"><span data-stu-id="666fa-148">The following declarations illustrate these implicit overloads.</span></span>  
  
 [!code-vb[VbVbcnProcedures#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#68)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 <span data-ttu-id="666fa-149">Tento postup se seznamem parametrů, který přebírá jednorozměrné pole pro pole parametrů nelze přetížit.</span><span class="sxs-lookup"><span data-stu-id="666fa-149">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="666fa-150">Můžete však použít podpisy implicitní přetížení.</span><span class="sxs-lookup"><span data-stu-id="666fa-150">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="666fa-151">Následující deklarace ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="666fa-151">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a><span data-ttu-id="666fa-152">Programování bez psaní jako alternativu k přetížení</span><span class="sxs-lookup"><span data-stu-id="666fa-152">Typeless Programming as an Alternative to Overloading</span></span>  
 <span data-ttu-id="666fa-153">Pokud chcete povolit, aby volající kód předat parametr různé datové typy, je alternativním přístupem programování bez psaní.</span><span class="sxs-lookup"><span data-stu-id="666fa-153">If you want to allow the calling code to pass different data types to a parameter, an alternative approach is typeless programming.</span></span> <span data-ttu-id="666fa-154">Můžete nastavit typ kontroly přepínač tak, aby `Off` buď [Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md) nebo [/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="666fa-154">You can set the type checking switch to `Off` with either the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) or the [/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) compiler option.</span></span> <span data-ttu-id="666fa-155">Potom není potřeba deklarovat datový typ parametru.</span><span class="sxs-lookup"><span data-stu-id="666fa-155">Then you do not have to declare the parameter's data type.</span></span> <span data-ttu-id="666fa-156">Tento přístup má ale tyto nevýhody ve srovnání s přetížení:</span><span class="sxs-lookup"><span data-stu-id="666fa-156">However, this approach has the following disadvantages compared to overloading:</span></span>  
  
- <span data-ttu-id="666fa-157">Programování bez psaní vytvoří méně efektivní provádění kódu.</span><span class="sxs-lookup"><span data-stu-id="666fa-157">Typeless programming produces less efficient execution code.</span></span>  
  
- <span data-ttu-id="666fa-158">Postup, musíte otestovat pro každý typ dat je připraven předávaný.</span><span class="sxs-lookup"><span data-stu-id="666fa-158">The procedure must test for every data type it anticipates being passed.</span></span>  
  
- <span data-ttu-id="666fa-159">Kompilátor nemůže signalizujete chybu, pokud volající kód předá datový typ, který postup není podporován.</span><span class="sxs-lookup"><span data-stu-id="666fa-159">The compiler cannot signal an error if the calling code passes a data type that the procedure does not support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="666fa-160">Viz také:</span><span class="sxs-lookup"><span data-stu-id="666fa-160">See also</span></span>

- [<span data-ttu-id="666fa-161">Procedury</span><span class="sxs-lookup"><span data-stu-id="666fa-161">Procedures</span></span>](./index.md)
- [<span data-ttu-id="666fa-162">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="666fa-162">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="666fa-163">Řešení potíží s procedurami</span><span class="sxs-lookup"><span data-stu-id="666fa-163">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="666fa-164">Postupy: Definice více verzí procedury</span><span class="sxs-lookup"><span data-stu-id="666fa-164">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="666fa-165">Postupy: Volání přetížené procedury</span><span class="sxs-lookup"><span data-stu-id="666fa-165">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="666fa-166">Postupy: Přetížení procedury, která přebírá volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="666fa-166">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="666fa-167">Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů</span><span class="sxs-lookup"><span data-stu-id="666fa-167">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="666fa-168">Řešení přetížení</span><span class="sxs-lookup"><span data-stu-id="666fa-168">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="666fa-169">Overloads</span><span class="sxs-lookup"><span data-stu-id="666fa-169">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
