---
title: Předávání argumentů pozicí nebo názvem
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
ms.openlocfilehash: 686b64977f086c8128e56298a0ed8c5aa0c51efa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364029"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a><span data-ttu-id="d6261-102">Předávání argumentů podle pozice a názvu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6261-102">Passing Arguments by Position and by Name (Visual Basic)</span></span>

<span data-ttu-id="d6261-103">Při volání `Sub` `Function` procedury nebo můžete předat argumenty *podle pozice* – v pořadí, v jakém jsou uvedeny v definici procedury, nebo je můžete předat *podle názvu*bez ohledu na pozici.</span><span class="sxs-lookup"><span data-stu-id="d6261-103">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span></span>

<span data-ttu-id="d6261-104">Pokud předáte argument podle názvu, zadáte deklarovaný název argumentu následovaný dvojtečkou a symbolem rovná se ( `:=` ) následovaný hodnotou argumentu.</span><span class="sxs-lookup"><span data-stu-id="d6261-104">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span></span> <span data-ttu-id="d6261-105">Pojmenované argumenty můžete dodat v libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d6261-105">You can supply named arguments in any order.</span></span>

<span data-ttu-id="d6261-106">Například následující `Sub` procedura přijímá tři argumenty:</span><span class="sxs-lookup"><span data-stu-id="d6261-106">For example, the following `Sub` procedure takes three arguments:</span></span>

[!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]

<span data-ttu-id="d6261-107">Při volání tohoto postupu můžete dodat argumenty podle pozice, názvu nebo pomocí kombinace obou.</span><span class="sxs-lookup"><span data-stu-id="d6261-107">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span></span>

## <a name="passing-arguments-by-position"></a><span data-ttu-id="d6261-108">Předávání argumentů podle pozice</span><span class="sxs-lookup"><span data-stu-id="d6261-108">Passing Arguments by Position</span></span>

<span data-ttu-id="d6261-109">Metodu lze volat `Display` s argumenty předanými pozicí a oddělenými čárkami, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="d6261-109">You can call the `Display` method with its arguments passed by position and delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)]

<span data-ttu-id="d6261-110">Vynecháte-li volitelný argument v seznamu pozičních argumentů, je nutné umístit jeho umístění do čárky.</span><span class="sxs-lookup"><span data-stu-id="d6261-110">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span></span> <span data-ttu-id="d6261-111">V následujícím příkladu je volána `Display` Metoda bez `age` argumentu:</span><span class="sxs-lookup"><span data-stu-id="d6261-111">The following example calls the `Display` method without the `age` argument:</span></span>

[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)]

## <a name="passing-arguments-by-name"></a><span data-ttu-id="d6261-112">Předávání argumentů podle názvu</span><span class="sxs-lookup"><span data-stu-id="d6261-112">Passing Arguments by Name</span></span>

<span data-ttu-id="d6261-113">Alternativně můžete volat `Display` s argumenty předanými podle názvu, také oddělené čárkami, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="d6261-113">Alternatively, you can call `Display` with the arguments passed by name, also delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)]

<span data-ttu-id="d6261-114">Předávání argumentů podle názvu tímto způsobem je zvlášť užitečné při volání procedury, která má více než jeden volitelný argument.</span><span class="sxs-lookup"><span data-stu-id="d6261-114">Passing arguments by name in this way is especially useful when you call a procedure that has more than one optional argument.</span></span> <span data-ttu-id="d6261-115">Pokud zadáte argumenty podle názvu, nemusíte používat po sobě jdoucí čárky k označení chybějících argumentů.</span><span class="sxs-lookup"><span data-stu-id="d6261-115">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span></span> <span data-ttu-id="d6261-116">Předávání argumentů podle názvu také usnadňuje sledování předávaného argumentu a těch, které jsou vynechány.</span><span class="sxs-lookup"><span data-stu-id="d6261-116">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span></span>

## <a name="mixing-arguments-by-position-and-by-name"></a><span data-ttu-id="d6261-117">Kombinování argumentů podle pozice a názvu</span><span class="sxs-lookup"><span data-stu-id="d6261-117">Mixing Arguments by Position and by Name</span></span>

<span data-ttu-id="d6261-118">Můžete dodat argumenty podle umístění a podle názvu v rámci jednoho volání procedury, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="d6261-118">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)]

<span data-ttu-id="d6261-119">V předchozím příkladu není k dispozici žádná další čárka, která by obsahovala místo vynechaného `age` argumentu, protože `birth` je předána názvem.</span><span class="sxs-lookup"><span data-stu-id="d6261-119">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span></span>

<span data-ttu-id="d6261-120">Ve verzích Visual Basic před 15,5, pokud zadáváte argumenty podle kombinace pozice a názvu, musí být argumenty pozice napřed.</span><span class="sxs-lookup"><span data-stu-id="d6261-120">In versions of Visual Basic before 15.5, when you supply arguments by a mixture of position and name, the positional arguments must all come first.</span></span> <span data-ttu-id="d6261-121">Po zadání argumentu podle názvu musí všechny zbývající argumenty předávat název.</span><span class="sxs-lookup"><span data-stu-id="d6261-121">Once you supply an argument by name, any remaining arguments must all be passed by name.</span></span>  <span data-ttu-id="d6261-122">Například následující volání `Display` metody zobrazí chybu kompilátoru [BC30241: očekával se pojmenovaný argument](../../../misc/bc30241.md).</span><span class="sxs-lookup"><span data-stu-id="d6261-122">For example, the following call to the `Display` method displays compiler error [BC30241: Named argument expected](../../../misc/bc30241.md).</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)]

<span data-ttu-id="d6261-123">Počínaje Visual Basic 15,5 se Poziční argumenty mohou pořídit pojmenovanými argumenty, pokud jsou konečné Poziční argumenty ve správné pozici.</span><span class="sxs-lookup"><span data-stu-id="d6261-123">Starting with Visual Basic 15.5, positional arguments can follow named arguments if the ending positional arguments are in the correct position.</span></span> <span data-ttu-id="d6261-124">Pokud je kompilace v rámci Visual Basic 15,5, předchozí volání `Display` metody se úspěšně zkompiluje a již negeneruje chybu kompilátoru [BC30241](../../../misc/bc30241.md).</span><span class="sxs-lookup"><span data-stu-id="d6261-124">If compiled under Visual Basic 15.5, the previous call to the `Display` method compiles successfully and no longer generates compiler error [BC30241](../../../misc/bc30241.md).</span></span>

<span data-ttu-id="d6261-125">Tuto schopnost sloučit a porovnat pojmenované a poziční argumenty v libovolném pořadí je zvláště užitečné, pokud chcete použít pojmenovaný argument k lepšímu čitelnosti kódu.</span><span class="sxs-lookup"><span data-stu-id="d6261-125">This ability to mix and match named and positional arguments in any order is particularly useful when you want to use a named argument to make your code more readable.</span></span> <span data-ttu-id="d6261-126">Například následující `Person` konstruktor třídy vyžaduje dva argumenty typu `Person` , oba z nich mohou být `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="d6261-126">For example, the following `Person` class constructor requires two arguments of type `Person`, both of which can be `Nothing`.</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)]

<span data-ttu-id="d6261-127">Použití smíšených pojmenovaných a pozičních argumentů pomáhá zajistit, aby byl záměr kódu jasný, pokud `father` je hodnota `mother` argumentů a `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="d6261-127">Using mixed named and positional arguments helps to make the intent of the code clear when the value of the `father` and `mother` arguments is `Nothing`:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)]

<span data-ttu-id="d6261-128">Chcete-li následovat Poziční argumenty s pojmenovanými argumenty, je nutné přidat následující prvek do souboru Visual Basic projektu ( \* . vbproj):</span><span class="sxs-lookup"><span data-stu-id="d6261-128">To follow positional arguments with named arguments, you must add the following element to your Visual Basic project (\*.vbproj) file:</span></span>

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="d6261-129">Další informace najdete v tématu [nastavení jazykové verze Visual Basic](../../../language-reference/configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="d6261-129">For more information see [setting the Visual Basic language version](../../../language-reference/configure-language-version.md).</span></span>

## <a name="restrictions-on-supplying-arguments-by-name"></a><span data-ttu-id="d6261-130">Omezení pro zadání argumentů podle názvu</span><span class="sxs-lookup"><span data-stu-id="d6261-130">Restrictions on Supplying Arguments by Name</span></span>

<span data-ttu-id="d6261-131">Argumenty nelze předat podle názvu, abyste se vyhnuli zadávání požadovaných argumentů.</span><span class="sxs-lookup"><span data-stu-id="d6261-131">You cannot pass arguments by name to avoid entering required arguments.</span></span> <span data-ttu-id="d6261-132">Můžete vynechat jenom nepovinné argumenty.</span><span class="sxs-lookup"><span data-stu-id="d6261-132">You can omit only the optional arguments.</span></span>

<span data-ttu-id="d6261-133">Pole parametrů nelze předat podle názvu.</span><span class="sxs-lookup"><span data-stu-id="d6261-133">You cannot pass a parameter array by name.</span></span> <span data-ttu-id="d6261-134">Důvodem je, že při volání procedury zadáte nekonečný počet argumentů oddělených čárkou pro pole parametrů a kompilátor nemůže přidružit více než jeden argument s jediným názvem.</span><span class="sxs-lookup"><span data-stu-id="d6261-134">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span></span>

## <a name="see-also"></a><span data-ttu-id="d6261-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6261-135">See also</span></span>

- [<span data-ttu-id="d6261-136">Procedury</span><span class="sxs-lookup"><span data-stu-id="d6261-136">Procedures</span></span>](./index.md)
- [<span data-ttu-id="d6261-137">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="d6261-137">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="d6261-138">Postupy: Předání argumentů proceduře</span><span class="sxs-lookup"><span data-stu-id="d6261-138">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="d6261-139">Předávání argumentů podle hodnoty a reference</span><span class="sxs-lookup"><span data-stu-id="d6261-139">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="d6261-140">Volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="d6261-140">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="d6261-141">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="d6261-141">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="d6261-142">Volitelné</span><span class="sxs-lookup"><span data-stu-id="d6261-142">Optional</span></span>](../../../language-reference/modifiers/optional.md)
- [<span data-ttu-id="d6261-143">ParamArray</span><span class="sxs-lookup"><span data-stu-id="d6261-143">ParamArray</span></span>](../../../language-reference/modifiers/paramarray.md)
