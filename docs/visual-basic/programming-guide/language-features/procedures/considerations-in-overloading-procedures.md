---
title: "Aspekty přetížení procedur (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3c9a9a4759d4ec2dd87778c49c4fd82a08c081a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a><span data-ttu-id="3699c-102">Aspekty přetížení procedur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3699c-102">Considerations in Overloading Procedures (Visual Basic)</span></span>
<span data-ttu-id="3699c-103">Pokud jste přetížení procedury, je nutné použít jiné *podpis* pro každou přetížené verzi.</span><span class="sxs-lookup"><span data-stu-id="3699c-103">When you overload a procedure, you must use a different *signature* for each overloaded version.</span></span> <span data-ttu-id="3699c-104">To obvykle znamená, že každou verzi musíte zadat seznam různých parametrů.</span><span class="sxs-lookup"><span data-stu-id="3699c-104">This usually means each version must specify a different parameter list.</span></span> <span data-ttu-id="3699c-105">Další informace najdete v tématu "Jiný podpis" v [přetížení procedury](./procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="3699c-105">For more information, see "Different Signature" in [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
 <span data-ttu-id="3699c-106">Můžete použít přetížení `Function` procedura s `Sub` postupu a naopak a poskytuje mají různé podpisy.</span><span class="sxs-lookup"><span data-stu-id="3699c-106">You can overload a `Function` procedure with a `Sub` procedure, and vice versa, provided they have different signatures.</span></span> <span data-ttu-id="3699c-107">Dvě přetížení nemůže se liší pouze v tom jeden má návratovou hodnotu a druhý není.</span><span class="sxs-lookup"><span data-stu-id="3699c-107">Two overloads cannot differ only in that one has a return value and the other does not.</span></span>  
  
 <span data-ttu-id="3699c-108">Můžete použít přetížení vlastnost stejným způsobem jako přetížení procedury a s stejná omezení.</span><span class="sxs-lookup"><span data-stu-id="3699c-108">You can overload a property the same way you overload a procedure, and with the same restrictions.</span></span> <span data-ttu-id="3699c-109">Nelze však přetížení procedury, vlastnost nebo naopak.</span><span class="sxs-lookup"><span data-stu-id="3699c-109">However, you cannot overload a procedure with a property, or vice versa.</span></span>  
  
## <a name="alternatives-to-overloaded-versions"></a><span data-ttu-id="3699c-110">Alternativy k přetížené verze</span><span class="sxs-lookup"><span data-stu-id="3699c-110">Alternatives to Overloaded Versions</span></span>  
 <span data-ttu-id="3699c-111">Někdy máte alternativy přetížené verze, zvláště pokud přítomnost argumentů je volitelné nebo jejich počet proměnné.</span><span class="sxs-lookup"><span data-stu-id="3699c-111">You sometimes have alternatives to overloaded versions, particularly when the presence of arguments is optional or their number is variable.</span></span>  
  
 <span data-ttu-id="3699c-112">Mějte na paměti, která volitelné argumenty nejsou nezbytně nepodporuje všechny jazyky a pole parametrů jsou omezené na [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3699c-112">Keep in mind that optional arguments are not necessarily supported by all languages, and parameter arrays are limited to [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="3699c-113">Pokud píšete procedury, která je pravděpodobné, která se má volat z kódu napsaného v některém z několika různými jazyky, přetížený nabídka verze nejvyšší flexibilitu.</span><span class="sxs-lookup"><span data-stu-id="3699c-113">If you are writing a procedure that is likely to be called from code written in any of several different languages, overloaded versions offer the greatest flexibility.</span></span>  
  
### <a name="overloads-and-optional-arguments"></a><span data-ttu-id="3699c-114">Přetížení a nepovinné argumenty</span><span class="sxs-lookup"><span data-stu-id="3699c-114">Overloads and Optional Arguments</span></span>  
 <span data-ttu-id="3699c-115">Při volání kód můžete volitelně zadat nebo vynechat jeden nebo více argumentů, můžete definovat několik verzí přetížené nebo použít volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="3699c-115">When the calling code can optionally supply or omit one or more arguments, you can define multiple overloaded versions or use optional parameters.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="3699c-116">Při použití přetížených verzí</span><span class="sxs-lookup"><span data-stu-id="3699c-116">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="3699c-117">Můžete zvážit definování řadu přetížené verze v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="3699c-117">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
-   <span data-ttu-id="3699c-118">Logika kód postup se výrazně liší v závislosti na tom, zda kód volání poskytuje nepovinný argument, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="3699c-118">The logic in the procedure code is significantly different depending on whether the calling code supplies an optional argument or not.</span></span>  
  
-   <span data-ttu-id="3699c-119">Kód procedury nelze spolehlivě otestovat, zda kód volání dodal za volitelným argumentem.</span><span class="sxs-lookup"><span data-stu-id="3699c-119">The procedure code cannot reliably test whether the calling code has supplied an optional argument.</span></span> <span data-ttu-id="3699c-120">Ano, například pokud není žádná možné kandidáta pro výchozí hodnotu, která kód volání nebylo se předpokládá, že zadat.</span><span class="sxs-lookup"><span data-stu-id="3699c-120">This is the case, for example, if there is no possible candidate for a default value that the calling code could not be expected to supply.</span></span>  
  
#### <a name="when-to-use-optional-parameters"></a><span data-ttu-id="3699c-121">Kdy použít volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="3699c-121">When to Use Optional Parameters</span></span>  
 <span data-ttu-id="3699c-122">Možná budete chtít jeden nebo více volitelné parametry v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="3699c-122">You might prefer one or more optional parameters in the following cases:</span></span>  
  
-   <span data-ttu-id="3699c-123">Pouze požadované akce při volání kód neposkytuje nepovinný argument je nastavit parametr na výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3699c-123">The only required action when the calling code does not supply an optional argument is to set the parameter to a default value.</span></span> <span data-ttu-id="3699c-124">V takovém případě může být méně složitý kód postup při definování jedna verze s jedním nebo více `Optional` parametry.</span><span class="sxs-lookup"><span data-stu-id="3699c-124">In such a case, the procedure code can be less complicated if you define a single version with one or more `Optional` parameters.</span></span>  
  
 <span data-ttu-id="3699c-125">Další informace najdete v tématu [volitelné parametry](./optional-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="3699c-125">For more information, see [Optional Parameters](./optional-parameters.md).</span></span>  
  
### <a name="overloads-and-paramarrays"></a><span data-ttu-id="3699c-126">Přetížení a ParamArrays</span><span class="sxs-lookup"><span data-stu-id="3699c-126">Overloads and ParamArrays</span></span>  
 <span data-ttu-id="3699c-127">Při volání kód předat proměnný počet argumentů, můžete definovat několik verzí přetížené nebo použít pole parametrů.</span><span class="sxs-lookup"><span data-stu-id="3699c-127">When the calling code can pass a variable number of arguments, you can define multiple overloaded versions or use a parameter array.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="3699c-128">Při použití přetížených verzí</span><span class="sxs-lookup"><span data-stu-id="3699c-128">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="3699c-129">Můžete zvážit definování řadu přetížené verze v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="3699c-129">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
-   <span data-ttu-id="3699c-130">Víte, že kód volání nikdy předá více než malý počet hodnot pole parametrů.</span><span class="sxs-lookup"><span data-stu-id="3699c-130">You know that the calling code never passes more than a small number of values to the parameter array.</span></span>  
  
-   <span data-ttu-id="3699c-131">Logika v postupu kódu je výrazně liší v závislosti na tom, kolik hodnot předá volání kódu.</span><span class="sxs-lookup"><span data-stu-id="3699c-131">The logic in the procedure code is significantly different depending on how many values the calling code passes.</span></span>  
  
-   <span data-ttu-id="3699c-132">Volání kódu můžete předat hodnoty různých datových typů.</span><span class="sxs-lookup"><span data-stu-id="3699c-132">The calling code can pass values of different data types.</span></span>  
  
#### <a name="when-to-use-a-parameter-array"></a><span data-ttu-id="3699c-133">Kdy použít pole parametrů</span><span class="sxs-lookup"><span data-stu-id="3699c-133">When to Use a Parameter Array</span></span>  
 <span data-ttu-id="3699c-134">Můžete se lépe vyhovovat `ParamArray` parametr v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="3699c-134">You are better served by a `ParamArray` parameter in the following cases:</span></span>  
  
-   <span data-ttu-id="3699c-135">Nemůžete k předpovědi kolik hodnot volající kód můžete předat pole parametrů a může být velký počet.</span><span class="sxs-lookup"><span data-stu-id="3699c-135">You are not able to predict how many values the calling code can pass to the parameter array, and it could be a large number.</span></span>  
  
-   <span data-ttu-id="3699c-136">Postup logiku různě iterace v rámci všech hodnot kód volání úspěšně projde, provádění v podstatě stejné operace v každé hodnotě.</span><span class="sxs-lookup"><span data-stu-id="3699c-136">The procedure logic lends itself to iterating through all the values the calling code passes, performing essentially the same operations on every value.</span></span>  
  
 <span data-ttu-id="3699c-137">Další informace najdete v tématu [pole parametrů](./parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="3699c-137">For more information, see [Parameter Arrays](./parameter-arrays.md).</span></span>  
  
## <a name="implicit-overloads-for-optional-parameters"></a><span data-ttu-id="3699c-138">Implicitní přetížení pro volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="3699c-138">Implicit Overloads for Optional Parameters</span></span>  
 <span data-ttu-id="3699c-139">Procedura se [volitelné](../../../../visual-basic/language-reference/modifiers/optional.md) je ekvivalentní přetížené dva postupy, jeden s volitelný parametr a jeden bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="3699c-139">A procedure with an [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameter is equivalent to two overloaded procedures, one with the optional parameter and one without it.</span></span> <span data-ttu-id="3699c-140">Tento postup nelze přetížení s seznam parametrů odpovídající buď na kteroukoli z nich.</span><span class="sxs-lookup"><span data-stu-id="3699c-140">You cannot overload such a procedure with a parameter list corresponding to either of these.</span></span> <span data-ttu-id="3699c-141">Následující deklarace znázornění.</span><span class="sxs-lookup"><span data-stu-id="3699c-141">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#58](./codesnippet/VisualBasic/considerations-in-overloading-procedures_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#60](./codesnippet/VisualBasic/considerations-in-overloading-procedures_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#61](./codesnippet/VisualBasic/considerations-in-overloading-procedures_3.vb)]  
  
 <span data-ttu-id="3699c-142">Pro proceduru s více než jeden volitelný parametr je sada implicitní přetížení, které byly přijaty logikou podobné jako v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="3699c-142">For a procedure with more than one optional parameter, there is a set of implicit overloads, arrived at by logic similar to that in the preceding example.</span></span>  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a><span data-ttu-id="3699c-143">Implicitní přetížení pro ParamArray parametr</span><span class="sxs-lookup"><span data-stu-id="3699c-143">Implicit Overloads for a ParamArray Parameter</span></span>  
 <span data-ttu-id="3699c-144">Kompilátor zvažuje procedura se [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametr mít libovolný počet přetížení, které se liší od sebe navzájem v co volací kód předá parametr pole, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="3699c-144">The compiler considers a procedure with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter to have an infinite number of overloads, differing from each other in what the calling code passes to the parameter array, as follows:</span></span>  
  
-   <span data-ttu-id="3699c-145">Jednomu přetížení pro při volání kód neposkytuje argumentu`ParamArray`</span><span class="sxs-lookup"><span data-stu-id="3699c-145">One overload for when the calling code does not supply an argument to the `ParamArray`</span></span>  
  
-   <span data-ttu-id="3699c-146">Jednomu přetížení pro při volání kód poskytuje jednorozměrného pole `ParamArray` typ elementu</span><span class="sxs-lookup"><span data-stu-id="3699c-146">One overload for when the calling code supplies a one-dimensional array of the `ParamArray` element type</span></span>  
  
-   <span data-ttu-id="3699c-147">Pro každý kladné celé číslo, jeden přetížení pro při volání kód poskytuje tento počet argumentů, každý z `ParamArray` typ elementu</span><span class="sxs-lookup"><span data-stu-id="3699c-147">For every positive integer, one overload for when the calling code supplies that number of arguments, each of the `ParamArray` element type</span></span>  
  
 <span data-ttu-id="3699c-148">Následující deklarace znázorňují tyto implicitní přetížení.</span><span class="sxs-lookup"><span data-stu-id="3699c-148">The following declarations illustrate these implicit overloads.</span></span>  
  
 [!code-vb[VbVbcnProcedures#68](./codesnippet/VisualBasic/considerations-in-overloading-procedures_4.vb)]  
  
 [!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/considerations-in-overloading-procedures_5.vb)]  
  
 <span data-ttu-id="3699c-149">Tento postup se seznam parametrů, která přebírá jednorozměrné pole pro parametr pole nelze přetížení.</span><span class="sxs-lookup"><span data-stu-id="3699c-149">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="3699c-150">Můžete však použít signatur implicitní přetížení.</span><span class="sxs-lookup"><span data-stu-id="3699c-150">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="3699c-151">Následující deklarace znázornění.</span><span class="sxs-lookup"><span data-stu-id="3699c-151">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/considerations-in-overloading-procedures_6.vb)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a><span data-ttu-id="3699c-152">Programování bez psaní jako alternativu k přetížení</span><span class="sxs-lookup"><span data-stu-id="3699c-152">Typeless Programming as an Alternative to Overloading</span></span>  
 <span data-ttu-id="3699c-153">Pokud chcete povolit volání kódu pro různé datové typy předat parametru, je alternativní způsob programování bez psaní.</span><span class="sxs-lookup"><span data-stu-id="3699c-153">If you want to allow the calling code to pass different data types to a parameter, an alternative approach is typeless programming.</span></span> <span data-ttu-id="3699c-154">Můžete nastavit typ kontroly přepínač tak, aby `Off` s buď [Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md) nebo [/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="3699c-154">You can set the type checking switch to `Off` with either the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) or the [/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) compiler option.</span></span> <span data-ttu-id="3699c-155">Pak nemáte deklarovat datový typ parametru.</span><span class="sxs-lookup"><span data-stu-id="3699c-155">Then you do not have to declare the parameter's data type.</span></span> <span data-ttu-id="3699c-156">Tento přístup má ale tyto nevýhody ve srovnání s přetížení:</span><span class="sxs-lookup"><span data-stu-id="3699c-156">However, this approach has the following disadvantages compared to overloading:</span></span>  
  
-   <span data-ttu-id="3699c-157">Programování bez psaní vytvoří méně efektivní provádění kódu.</span><span class="sxs-lookup"><span data-stu-id="3699c-157">Typeless programming produces less efficient execution code.</span></span>  
  
-   <span data-ttu-id="3699c-158">Postup, musíte otestovat pro každý typ dat je připravená na předávány.</span><span class="sxs-lookup"><span data-stu-id="3699c-158">The procedure must test for every data type it anticipates being passed.</span></span>  
  
-   <span data-ttu-id="3699c-159">Kompilátor nelze signál chybu, pokud kód volání předá datový typ, který postup nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="3699c-159">The compiler cannot signal an error if the calling code passes a data type that the procedure does not support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3699c-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="3699c-160">See Also</span></span>  
 [<span data-ttu-id="3699c-161">Postupy</span><span class="sxs-lookup"><span data-stu-id="3699c-161">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="3699c-162">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="3699c-162">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="3699c-163">Řešení potíží s procedurami</span><span class="sxs-lookup"><span data-stu-id="3699c-163">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="3699c-164">Postupy: definice více verzí procedury</span><span class="sxs-lookup"><span data-stu-id="3699c-164">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)  
 [<span data-ttu-id="3699c-165">Postupy: volání přetížené procedury</span><span class="sxs-lookup"><span data-stu-id="3699c-165">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)  
 [<span data-ttu-id="3699c-166">Postupy: přetížení procedury, která přebírá volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="3699c-166">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [<span data-ttu-id="3699c-167">Postupy: přetížení procedury, která přebírá nekonečný počet parametrů</span><span class="sxs-lookup"><span data-stu-id="3699c-167">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [<span data-ttu-id="3699c-168">Řešení přetížení</span><span class="sxs-lookup"><span data-stu-id="3699c-168">Overload Resolution</span></span>](./overload-resolution.md)  
 [<span data-ttu-id="3699c-169">Přetížení</span><span class="sxs-lookup"><span data-stu-id="3699c-169">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
