---
title: "Předávání argumentů podle pozice a názvu (Visual Basic)"
ms.custom: 
ms.date: 02/01/2018
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13f5e5a8da6a899d4920a25b250ca88b2a21f559
ms.sourcegitcommit: 099aa20d9b6450d1b7452d782a55771a6ad8ff35
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/05/2018
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a><span data-ttu-id="bf7ab-102">Předávání argumentů podle pozice a názvu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf7ab-102">Passing Arguments by Position and by Name (Visual Basic)</span></span>
<span data-ttu-id="bf7ab-103">Při volání `Sub` nebo `Function` postupu můžete předat argumenty *umístěním* – v pořadí, ve kterém se zobrazí v postupu pro definici – nebo můžete je předat *podle názvu*, bez ohledem na pozici.</span><span class="sxs-lookup"><span data-stu-id="bf7ab-103">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span></span>  
  
 <span data-ttu-id="bf7ab-104">Při předání argumentu podle názvu, zadáte argument je deklarovaný název následovaný dvojtečkou a symbolem rovná (`:=`), za nímž následují hodnota argumentu.</span><span class="sxs-lookup"><span data-stu-id="bf7ab-104">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span></span> <span data-ttu-id="bf7ab-105">Můžete zadat pojmenované argumenty v libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="bf7ab-105">You can supply named arguments in any order.</span></span>  
  
 <span data-ttu-id="bf7ab-106">Například následující `Sub` procedura používá tři argumenty:</span><span class="sxs-lookup"><span data-stu-id="bf7ab-106">For example, the following `Sub` procedure takes three arguments:</span></span>  
  
 [!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]  
  
 <span data-ttu-id="bf7ab-107">Při volání tohoto postupu můžete zadat argumentů podle pozice, podle názvu nebo pomocí kombinaci těchto dvou možností.</span><span class="sxs-lookup"><span data-stu-id="bf7ab-107">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span></span>  
  
## <a name="passing-arguments-by-position"></a><span data-ttu-id="bf7ab-108">Předávání argumentů podle pozice</span><span class="sxs-lookup"><span data-stu-id="bf7ab-108">Passing Arguments by Position</span></span>  
 <span data-ttu-id="bf7ab-109">Můžete volat `Display` metoda s argumenty předaná pozice a oddělená čárkami, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="bf7ab-109">You can call the `Display` method with its arguments passed by position and delimited by commas, as shown in the following example:</span></span>  
  
[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)] 
  
 <span data-ttu-id="bf7ab-110">Pokud vynecháte za volitelným argumentem v seznamu poziční argument, musí obsahovat příslušné místo oddělujte čárkami.</span><span class="sxs-lookup"><span data-stu-id="bf7ab-110">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span></span> <span data-ttu-id="bf7ab-111">Následující příklad volání `Display` metoda bez `age` argument:</span><span class="sxs-lookup"><span data-stu-id="bf7ab-111">The following example calls the `Display` method without the `age` argument:</span></span>  
  
[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)] 
  
## <a name="passing-arguments-by-name"></a><span data-ttu-id="bf7ab-112">Předávání argumentů podle názvu</span><span class="sxs-lookup"><span data-stu-id="bf7ab-112">Passing Arguments by Name</span></span>  
 <span data-ttu-id="bf7ab-113">Alternativně můžete volat `Display` s argumentů předaných podle názvu, také oddělená čárkami, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="bf7ab-113">Alternatively, you can call `Display` with the arguments passed by name, also delimited by commas, as shown in the following example:</span></span>  
  
[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)] 

 <span data-ttu-id="bf7ab-114">Předávání argumentů podle názvu tímto způsobem je obzvláště užitečná při volání procedury, která má více než jeden nepovinný argument.</span><span class="sxs-lookup"><span data-stu-id="bf7ab-114">Passing arguments by name in this way is especially useful when you call a procedure that has more than one optional argument.</span></span> <span data-ttu-id="bf7ab-115">Pokud zadáte argumenty podle názvu, nemáte použít po sobě jdoucích čárkami k označení chybí poziční argumenty.</span><span class="sxs-lookup"><span data-stu-id="bf7ab-115">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span></span> <span data-ttu-id="bf7ab-116">Předávání argumentů podle názvu taky usnadní ke sledování které argumenty jsou předávání a ty, které jsou vynechá.</span><span class="sxs-lookup"><span data-stu-id="bf7ab-116">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span></span>  
  
## <a name="mixing-arguments-by-position-and-by-name"></a><span data-ttu-id="bf7ab-117">Kombinování argumentů podle pozice a názvu</span><span class="sxs-lookup"><span data-stu-id="bf7ab-117">Mixing Arguments by Position and by Name</span></span>  

<span data-ttu-id="bf7ab-118">Argumentů podle pozice a podle názvu ve volání jedinou proceduru, můžete zadat, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="bf7ab-118">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span></span>  
  
[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)] 
  
 <span data-ttu-id="bf7ab-119">V předchozím příkladu, je potřeba k umístění na místo vynechání žádné další čárkami `age` argument, protože `birth` je předán podle názvu.</span><span class="sxs-lookup"><span data-stu-id="bf7ab-119">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span></span>  
  
<span data-ttu-id="bf7ab-120">Ve verzi jazyka Visual Basic před 15,5 když zadáte argumenty podle směs pozice a názvu, poziční argumenty musí všechny nejdřív se musí uvést.</span><span class="sxs-lookup"><span data-stu-id="bf7ab-120">In versions of Visual Basic before 15.5, when you supply arguments by a mixture of position and name, the positional arguments must all come first.</span></span> <span data-ttu-id="bf7ab-121">Jakmile zadáte argument podle názvu, všechny zbývající argumenty, musí všechny být předán podle názvu.</span><span class="sxs-lookup"><span data-stu-id="bf7ab-121">Once you supply an argument by name, any remaining arguments must all be passed by name.</span></span>  <span data-ttu-id="bf7ab-122">Například následující volání do `Display` metoda zobrazí chyba kompilátoru [BC30241: argument očekávání s názvem](../../../misc/bc30241.md).</span><span class="sxs-lookup"><span data-stu-id="bf7ab-122">For example, the following call to the `Display` method displays compiler error [BC30241: Named argument expected](../../../misc/bc30241.md).</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)] 

<span data-ttu-id="bf7ab-123">Od verze Visual Basic 15,5, poziční argumenty lze použít pojmenované argumenty v případě koncová poziční argumenty jsou ve správné pozici.</span><span class="sxs-lookup"><span data-stu-id="bf7ab-123">Starting with Visual Basic 15.5, positional arguments can follow named arguments if the ending positional arguments are in the correct position.</span></span> <span data-ttu-id="bf7ab-124">Pokud zkompilovat pod 15,5 Visual Basic, předchozí volání `Display` metoda zkompiluje úspěšně a už vygeneruje Chyba kompilátoru [BC30241](../../../misc/bc30241.md).</span><span class="sxs-lookup"><span data-stu-id="bf7ab-124">If compiled under Visual Basic 15.5, the previous call to the `Display` method compiles successfully and no longer generates compiler error [BC30241](../../../misc/bc30241.md).</span></span>  

<span data-ttu-id="bf7ab-125">Tato schopnost kombinovat a párovat pojmenované a poziční argumenty v libovolném pořadí je zvláště užitečné, pokud chcete používat s názvem argument tak čitelnost kódu.</span><span class="sxs-lookup"><span data-stu-id="bf7ab-125">This ability to mix and match named and positional arguments in any order is particularly useful when you want to use a named argument to make your code more readable.</span></span> <span data-ttu-id="bf7ab-126">Například následující `Person` konstruktoru třídy vyžaduje dva argumenty typu `Person`, které může být `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="bf7ab-126">For example, the following `Person` class constructor requires two arguments of type `Person`, both of which can be `Nothing`.</span></span> 

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)] 

<span data-ttu-id="bf7ab-127">Pomocí smíšený pojmenované a poziční argumenty pomáhá, aby byl záměr kódu vymazat, když hodnota `father` a `mother` argumenty je `Nothing`:</span><span class="sxs-lookup"><span data-stu-id="bf7ab-127">Using mixed named and positional arguments helps to make the intent of the code clear when the value of the `father` and `mother` arguments is `Nothing`:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)] 

<span data-ttu-id="bf7ab-128">Chcete-li postupovat podle poziční argumenty s pojmenované argumenty, je nutné přidat následující element do projektu jazyka Visual Basic (\*.vbproj) souboru:</span><span class="sxs-lookup"><span data-stu-id="bf7ab-128">To follow positional arguments with named arguments, you must add the following element to your Visual Basic project (\*.vbproj) file:</span></span>

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

## <a name="restrictions-on-supplying-arguments-by-name"></a><span data-ttu-id="bf7ab-129">Omezení pro zadávání argumenty podle názvu</span><span class="sxs-lookup"><span data-stu-id="bf7ab-129">Restrictions on Supplying Arguments by Name</span></span>  

<span data-ttu-id="bf7ab-130">Nelze předat argumenty podle názvu, abyste nemuseli zadávat povinnými argumenty.</span><span class="sxs-lookup"><span data-stu-id="bf7ab-130">You cannot pass arguments by name to avoid entering required arguments.</span></span> <span data-ttu-id="bf7ab-131">Pouze volitelné argumenty, můžete vynechat.</span><span class="sxs-lookup"><span data-stu-id="bf7ab-131">You can omit only the optional arguments.</span></span>  
  
<span data-ttu-id="bf7ab-132">Pole parametrů nelze předat podle názvu.</span><span class="sxs-lookup"><span data-stu-id="bf7ab-132">You cannot pass a parameter array by name.</span></span> <span data-ttu-id="bf7ab-133">Je to proto, že při volání postupu zadáte nekonečný počet textový soubor s oddělovači argumenty pro parametr pole a kompilátor nelze přidružit více než jeden argument s jedním názvem.</span><span class="sxs-lookup"><span data-stu-id="bf7ab-133">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf7ab-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="bf7ab-134">See Also</span></span>  
 [<span data-ttu-id="bf7ab-135">Procedury</span><span class="sxs-lookup"><span data-stu-id="bf7ab-135">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="bf7ab-136">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="bf7ab-136">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="bf7ab-137">Postupy: Předání argumentů proceduře</span><span class="sxs-lookup"><span data-stu-id="bf7ab-137">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="bf7ab-138">Předávání argumentů podle hodnoty a reference</span><span class="sxs-lookup"><span data-stu-id="bf7ab-138">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="bf7ab-139">Nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="bf7ab-139">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="bf7ab-140">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="bf7ab-140">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="bf7ab-141">Optional</span><span class="sxs-lookup"><span data-stu-id="bf7ab-141">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [<span data-ttu-id="bf7ab-142">ParamArray</span><span class="sxs-lookup"><span data-stu-id="bf7ab-142">ParamArray</span></span>](../../../../visual-basic/language-reference/modifiers/paramarray.md)
