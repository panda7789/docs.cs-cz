---
title: Předávání argumentů podle pozice a názvu (Visual Basic)
ms.date: 02/01/2018
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
ms.openlocfilehash: bdaa0351e288b85a3e35818c0f53ef4d772932e5
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53151305"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a><span data-ttu-id="6d9aa-102">Předávání argumentů podle pozice a názvu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d9aa-102">Passing Arguments by Position and by Name (Visual Basic)</span></span>
<span data-ttu-id="6d9aa-103">Při volání `Sub` nebo `Function` postup, můžete předat argumenty *umístěním* – v pořadí, v jakém jsou uvedeny v definici procedury – nebo můžete předat je *podle názvu*, bez ohledem na pozici.</span><span class="sxs-lookup"><span data-stu-id="6d9aa-103">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span></span>  
  
 <span data-ttu-id="6d9aa-104">Při předání argumentu podle názvu, můžete zadat argument deklarován název následovaný dvojtečkou a znaménko rovná se (`:=`) následovaný hodnotu argumentu.</span><span class="sxs-lookup"><span data-stu-id="6d9aa-104">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span></span> <span data-ttu-id="6d9aa-105">Můžete zadat pojmenované argumenty v libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="6d9aa-105">You can supply named arguments in any order.</span></span>  
  
 <span data-ttu-id="6d9aa-106">Například následující `Sub` procedura má tři argumenty:</span><span class="sxs-lookup"><span data-stu-id="6d9aa-106">For example, the following `Sub` procedure takes three arguments:</span></span>  
  
 [!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]  
  
 <span data-ttu-id="6d9aa-107">Při volání tohoto postupu můžete zadat argumentů podle pozice, podle názvu nebo s použitím kombinaci obou.</span><span class="sxs-lookup"><span data-stu-id="6d9aa-107">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span></span>  
  
## <a name="passing-arguments-by-position"></a><span data-ttu-id="6d9aa-108">Předávání argumentů podle pozice</span><span class="sxs-lookup"><span data-stu-id="6d9aa-108">Passing Arguments by Position</span></span>  
 <span data-ttu-id="6d9aa-109">Můžete volat `Display` metoda s argumenty předány podle pozice a oddělených čárkami, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="6d9aa-109">You can call the `Display` method with its arguments passed by position and delimited by commas, as shown in the following example:</span></span>  
  
[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)] 
  
 <span data-ttu-id="6d9aa-110">Pokud volitelný argument v seznamu poziční argument vynecháte, je třeba držet místo něj čárkou.</span><span class="sxs-lookup"><span data-stu-id="6d9aa-110">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span></span> <span data-ttu-id="6d9aa-111">Následující příklad volá `Display` metody bez `age` argument:</span><span class="sxs-lookup"><span data-stu-id="6d9aa-111">The following example calls the `Display` method without the `age` argument:</span></span>  
  
[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)] 
  
## <a name="passing-arguments-by-name"></a><span data-ttu-id="6d9aa-112">Předávání argumentů podle názvu</span><span class="sxs-lookup"><span data-stu-id="6d9aa-112">Passing Arguments by Name</span></span>  
 <span data-ttu-id="6d9aa-113">Alternativně můžete volat `Display` s argumenty předány podle názvu, také oddělených čárkami, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="6d9aa-113">Alternatively, you can call `Display` with the arguments passed by name, also delimited by commas, as shown in the following example:</span></span>  
  
[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)] 

 <span data-ttu-id="6d9aa-114">Předávání argumentů podle názvu tímto způsobem je užitečné zejména při volání procedury, která má více než jeden volitelný argument.</span><span class="sxs-lookup"><span data-stu-id="6d9aa-114">Passing arguments by name in this way is especially useful when you call a procedure that has more than one optional argument.</span></span> <span data-ttu-id="6d9aa-115">Pokud zadáte argumenty podle názvu, není nutné používat po sobě jdoucích čárek k označení chybí poziční argumenty.</span><span class="sxs-lookup"><span data-stu-id="6d9aa-115">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span></span> <span data-ttu-id="6d9aa-116">Předávání argumentů podle názvu také usnadňuje sledovat, které argumenty předáváte a ty, které se vynechá.</span><span class="sxs-lookup"><span data-stu-id="6d9aa-116">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span></span>  
  
## <a name="mixing-arguments-by-position-and-by-name"></a><span data-ttu-id="6d9aa-117">Kombinace argumentů podle pozice a názvu</span><span class="sxs-lookup"><span data-stu-id="6d9aa-117">Mixing Arguments by Position and by Name</span></span>  

<span data-ttu-id="6d9aa-118">Můžete zadat argumentů podle pozice a podle názvu ve volání jedné postupem, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="6d9aa-118">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span></span>  
  
[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)] 
  
 <span data-ttu-id="6d9aa-119">V předchozím příkladu je nezbytné k uložení místo vynechaný žádné další čárka `age` argument, protože `birth` je předán podle názvu.</span><span class="sxs-lookup"><span data-stu-id="6d9aa-119">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span></span>  
  
<span data-ttu-id="6d9aa-120">Ve verzích jazyka Visual Basic před 15.5 Pokud dodání argumentů podle pozice a názvu, poziční argumenty kombinaci musí všechny být první.</span><span class="sxs-lookup"><span data-stu-id="6d9aa-120">In versions of Visual Basic before 15.5, when you supply arguments by a mixture of position and name, the positional arguments must all come first.</span></span> <span data-ttu-id="6d9aa-121">Jakmile zadáte argument podle názvu, všechny zbývající argumenty musí všechny předávat podle názvu.</span><span class="sxs-lookup"><span data-stu-id="6d9aa-121">Once you supply an argument by name, any remaining arguments must all be passed by name.</span></span>  <span data-ttu-id="6d9aa-122">Například následující volání `Display` metoda zobrazí chyba kompilátoru [BC30241: Očekával se pojmenovaný argument](../../../misc/bc30241.md).</span><span class="sxs-lookup"><span data-stu-id="6d9aa-122">For example, the following call to the `Display` method displays compiler error [BC30241: Named argument expected](../../../misc/bc30241.md).</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)] 

<span data-ttu-id="6d9aa-123">Od verze 15.5 jazyka Visual Basic, poziční argumenty lze použít pojmenované argumenty v případě koncové poziční argumenty nejsou ve správné pozici.</span><span class="sxs-lookup"><span data-stu-id="6d9aa-123">Starting with Visual Basic 15.5, positional arguments can follow named arguments if the ending positional arguments are in the correct position.</span></span> <span data-ttu-id="6d9aa-124">Je-li zkompilovat v rámci jazyka Visual Basic 15.5, předchozího volání `Display` metoda se zkompiluje úspěšně a už vygeneruje Chyba kompilátoru [BC30241](../../../misc/bc30241.md).</span><span class="sxs-lookup"><span data-stu-id="6d9aa-124">If compiled under Visual Basic 15.5, the previous call to the `Display` method compiles successfully and no longer generates compiler error [BC30241](../../../misc/bc30241.md).</span></span>  

<span data-ttu-id="6d9aa-125">Tato schopnost kombinovat a párovat s názvem a poziční argumenty v libovolném pořadí je zvlášť užitečné, pokud chcete použít pojmenovaný argument, aby váš kód lépe čitelný.</span><span class="sxs-lookup"><span data-stu-id="6d9aa-125">This ability to mix and match named and positional arguments in any order is particularly useful when you want to use a named argument to make your code more readable.</span></span> <span data-ttu-id="6d9aa-126">Například následující `Person` konstruktoru třídy vyžaduje dva argumenty typu `Person`, které může být `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="6d9aa-126">For example, the following `Person` class constructor requires two arguments of type `Person`, both of which can be `Nothing`.</span></span> 

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)] 

<span data-ttu-id="6d9aa-127">Smíšené pojmenované a poziční argumenty, které pomáhá provádět záměru kódu vymazat při použití hodnoty `father` a `mother` argumenty `Nothing`:</span><span class="sxs-lookup"><span data-stu-id="6d9aa-127">Using mixed named and positional arguments helps to make the intent of the code clear when the value of the `father` and `mother` arguments is `Nothing`:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)] 

<span data-ttu-id="6d9aa-128">Pro použít poziční argumenty s pojmenovanými argumenty, je nutné přidat následující prvek do projektu jazyka Visual Basic (\*.vbproj) souboru:</span><span class="sxs-lookup"><span data-stu-id="6d9aa-128">To follow positional arguments with named arguments, you must add the following element to your Visual Basic project (\*.vbproj) file:</span></span>

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="6d9aa-129">Další informace najdete v části [nastavení verze jazyka Visual Basic](../../../language-reference/configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="6d9aa-129">For more information see [setting the Visual Basic language version](../../../language-reference/configure-language-version.md).</span></span>

## <a name="restrictions-on-supplying-arguments-by-name"></a><span data-ttu-id="6d9aa-130">Omezení pro poskytnutí argumentů podle názvu</span><span class="sxs-lookup"><span data-stu-id="6d9aa-130">Restrictions on Supplying Arguments by Name</span></span>  

<span data-ttu-id="6d9aa-131">Argumenty nelze předávat podle názvu myslet povinnými argumenty.</span><span class="sxs-lookup"><span data-stu-id="6d9aa-131">You cannot pass arguments by name to avoid entering required arguments.</span></span> <span data-ttu-id="6d9aa-132">Vynechat jenom volitelné argumenty.</span><span class="sxs-lookup"><span data-stu-id="6d9aa-132">You can omit only the optional arguments.</span></span>  
  
<span data-ttu-id="6d9aa-133">Pole parametrů nelze předat podle názvu.</span><span class="sxs-lookup"><span data-stu-id="6d9aa-133">You cannot pass a parameter array by name.</span></span> <span data-ttu-id="6d9aa-134">Je to proto, že při volání postupu zadáte nekonečný počet oddělovači argumentů pole parametrů a kompilátor nelze přidružit k více než jeden argument jeden název.</span><span class="sxs-lookup"><span data-stu-id="6d9aa-134">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d9aa-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d9aa-135">See Also</span></span>  
 [<span data-ttu-id="6d9aa-136">Procedury</span><span class="sxs-lookup"><span data-stu-id="6d9aa-136">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="6d9aa-137">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="6d9aa-137">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="6d9aa-138">Jak: Předání argumentů proceduře</span><span class="sxs-lookup"><span data-stu-id="6d9aa-138">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="6d9aa-139">Předávání argumentů podle hodnoty a reference</span><span class="sxs-lookup"><span data-stu-id="6d9aa-139">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="6d9aa-140">Nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="6d9aa-140">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="6d9aa-141">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="6d9aa-141">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="6d9aa-142">Optional</span><span class="sxs-lookup"><span data-stu-id="6d9aa-142">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [<span data-ttu-id="6d9aa-143">ParamArray</span><span class="sxs-lookup"><span data-stu-id="6d9aa-143">ParamArray</span></span>](../../../../visual-basic/language-reference/modifiers/paramarray.md)
