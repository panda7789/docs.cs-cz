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
ms.openlocfilehash: b6588335f7634cc87a9fc14cbfc4ba80baad1abb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400853"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a><span data-ttu-id="03c6a-102">Předávání argumentů podle pozice a názvu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03c6a-102">Passing Arguments by Position and by Name (Visual Basic)</span></span>

<span data-ttu-id="03c6a-103">Když voláte `Sub` `Function` nebo proceduru, můžete předat argumenty *podle pozice* – v pořadí, ve kterém jsou uvedeny v definici postupu – nebo je můžete předat *podle názvu*, bez ohledu na pozici.</span><span class="sxs-lookup"><span data-stu-id="03c6a-103">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span></span>

<span data-ttu-id="03c6a-104">Když předáte argument podle názvu, zadáte deklarovaný název argumentu následovaný`:=`dvojtečkou a rovnítkem ( ), následovaným hodnotou argumentu.</span><span class="sxs-lookup"><span data-stu-id="03c6a-104">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span></span> <span data-ttu-id="03c6a-105">Pojmenované argumenty můžete zadat v libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="03c6a-105">You can supply named arguments in any order.</span></span>

<span data-ttu-id="03c6a-106">Například následující `Sub` postup trvá tři argumenty:</span><span class="sxs-lookup"><span data-stu-id="03c6a-106">For example, the following `Sub` procedure takes three arguments:</span></span>

[!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]

<span data-ttu-id="03c6a-107">Při volání tohoto postupu můžete zadat argumenty podle pozice, podle názvu nebo pomocí kombinace obou.</span><span class="sxs-lookup"><span data-stu-id="03c6a-107">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span></span>

## <a name="passing-arguments-by-position"></a><span data-ttu-id="03c6a-108">Předávání argumentů podle pozice</span><span class="sxs-lookup"><span data-stu-id="03c6a-108">Passing Arguments by Position</span></span>

<span data-ttu-id="03c6a-109">Můžete volat `Display` metodu s její argumenty předaný pozice a oddělené čárkami, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="03c6a-109">You can call the `Display` method with its arguments passed by position and delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)]

<span data-ttu-id="03c6a-110">Pokud vynechete volitelný argument v seznamu pozičních argumentů, musíte jeho místo držet čárkou.</span><span class="sxs-lookup"><span data-stu-id="03c6a-110">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span></span> <span data-ttu-id="03c6a-111">Následující příklad volá `Display` metodu `age` bez argumentu:</span><span class="sxs-lookup"><span data-stu-id="03c6a-111">The following example calls the `Display` method without the `age` argument:</span></span>

[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)]

## <a name="passing-arguments-by-name"></a><span data-ttu-id="03c6a-112">Předávání argumentů podle názvu</span><span class="sxs-lookup"><span data-stu-id="03c6a-112">Passing Arguments by Name</span></span>

<span data-ttu-id="03c6a-113">Případně můžete volat `Display` s argumenty předanými názvem, také oddělenými čárkami, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="03c6a-113">Alternatively, you can call `Display` with the arguments passed by name, also delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)]

<span data-ttu-id="03c6a-114">Předávání argumentů podle názvu tímto způsobem je zvláště užitečné při volání procedury, která má více než jeden volitelný argument.</span><span class="sxs-lookup"><span data-stu-id="03c6a-114">Passing arguments by name in this way is especially useful when you call a procedure that has more than one optional argument.</span></span> <span data-ttu-id="03c6a-115">Pokud zadáte argumenty podle názvu, není třeba k označení chybějících pozičních argumentů používat po sobě jdoucí čárky.</span><span class="sxs-lookup"><span data-stu-id="03c6a-115">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span></span> <span data-ttu-id="03c6a-116">Předávání argumentů podle názvu také usnadňuje sledování, které argumenty předáváte a které vynecháváte.</span><span class="sxs-lookup"><span data-stu-id="03c6a-116">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span></span>

## <a name="mixing-arguments-by-position-and-by-name"></a><span data-ttu-id="03c6a-117">Míchání argumentů podle pozice a názvu</span><span class="sxs-lookup"><span data-stu-id="03c6a-117">Mixing Arguments by Position and by Name</span></span>

<span data-ttu-id="03c6a-118">Argumenty můžete zadat podle pozice i názvu v jednom volání procedury, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="03c6a-118">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)]

<span data-ttu-id="03c6a-119">V předchozím příkladu žádné další čárka je nutné držet `age` místo vynechaného argumentu, since `birth` je předán podle názvu.</span><span class="sxs-lookup"><span data-stu-id="03c6a-119">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span></span>

<span data-ttu-id="03c6a-120">Ve verzích jazyka Visual Basic před 15.5 při zadání argumentů kombinací pozice a názvu musí být všechny poziční argumenty na prvním místě.</span><span class="sxs-lookup"><span data-stu-id="03c6a-120">In versions of Visual Basic before 15.5, when you supply arguments by a mixture of position and name, the positional arguments must all come first.</span></span> <span data-ttu-id="03c6a-121">Jakmile zadáte argument podle názvu, všechny zbývající argumenty musí být předány podle názvu.</span><span class="sxs-lookup"><span data-stu-id="03c6a-121">Once you supply an argument by name, any remaining arguments must all be passed by name.</span></span>  <span data-ttu-id="03c6a-122">Například následující volání metody `Display` zobrazí chybu kompilátoru [BC30241: Pojmenovaný argument byl očekáván](../../../misc/bc30241.md).</span><span class="sxs-lookup"><span data-stu-id="03c6a-122">For example, the following call to the `Display` method displays compiler error [BC30241: Named argument expected](../../../misc/bc30241.md).</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)]

<span data-ttu-id="03c6a-123">Počínaje Visual Basic 15.5, poziční argumenty mohou následovat pojmenované argumenty, pokud koncové poziční argumenty jsou ve správné poloze.</span><span class="sxs-lookup"><span data-stu-id="03c6a-123">Starting with Visual Basic 15.5, positional arguments can follow named arguments if the ending positional arguments are in the correct position.</span></span> <span data-ttu-id="03c6a-124">Pokud je zkompilován v jazyce Visual `Display` Basic 15.5, předchozí volání metody zkompiluje úspěšně a již generuje chybu kompilátoru [BC30241](../../../misc/bc30241.md).</span><span class="sxs-lookup"><span data-stu-id="03c6a-124">If compiled under Visual Basic 15.5, the previous call to the `Display` method compiles successfully and no longer generates compiler error [BC30241](../../../misc/bc30241.md).</span></span>

<span data-ttu-id="03c6a-125">Tato schopnost kombinovat pojmenované a poziční argumenty v libovolném pořadí je zvláště užitečné, pokud chcete použít pojmenovaný argument, aby váš kód čitelnější.</span><span class="sxs-lookup"><span data-stu-id="03c6a-125">This ability to mix and match named and positional arguments in any order is particularly useful when you want to use a named argument to make your code more readable.</span></span> <span data-ttu-id="03c6a-126">Například následující `Person` konstruktor třídy vyžaduje dva `Person`argumenty typu `Nothing`, které mohou být .</span><span class="sxs-lookup"><span data-stu-id="03c6a-126">For example, the following `Person` class constructor requires two arguments of type `Person`, both of which can be `Nothing`.</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)]

<span data-ttu-id="03c6a-127">Použití smíšené pojmenované a poziční argumenty pomáhá, aby záměr `father` `mother` kódu jasné, když je hodnota a argumenty `Nothing`:</span><span class="sxs-lookup"><span data-stu-id="03c6a-127">Using mixed named and positional arguments helps to make the intent of the code clear when the value of the `father` and `mother` arguments is `Nothing`:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)]

<span data-ttu-id="03c6a-128">Chcete-li sledovat poziční argumenty s pojmenovanými argumenty,\*musíte do souboru projektu jazyka Visual Basic (.vbproj) přidat následující prvek:</span><span class="sxs-lookup"><span data-stu-id="03c6a-128">To follow positional arguments with named arguments, you must add the following element to your Visual Basic project (\*.vbproj) file:</span></span>

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="03c6a-129">Další informace naleznete [v nastavení jazykové verze jazyka Jazyka](../../../language-reference/configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="03c6a-129">For more information see [setting the Visual Basic language version](../../../language-reference/configure-language-version.md).</span></span>

## <a name="restrictions-on-supplying-arguments-by-name"></a><span data-ttu-id="03c6a-130">Omezení dodávajících argumentů podle názvu</span><span class="sxs-lookup"><span data-stu-id="03c6a-130">Restrictions on Supplying Arguments by Name</span></span>

<span data-ttu-id="03c6a-131">Nelze předat argumenty podle názvu, abyste se vyhnuli zadávání požadovaných argumentů.</span><span class="sxs-lookup"><span data-stu-id="03c6a-131">You cannot pass arguments by name to avoid entering required arguments.</span></span> <span data-ttu-id="03c6a-132">Vynechat můžete pouze volitelné argumenty.</span><span class="sxs-lookup"><span data-stu-id="03c6a-132">You can omit only the optional arguments.</span></span>

<span data-ttu-id="03c6a-133">Pole parametrů nelze předat podle názvu.</span><span class="sxs-lookup"><span data-stu-id="03c6a-133">You cannot pass a parameter array by name.</span></span> <span data-ttu-id="03c6a-134">Důvodem je, že při volání procedury zadáte neurčitý počet argumentů oddělených čárkami pro pole parametrů a kompilátor nemůže přidružit více než jeden argument s jedním názvem.</span><span class="sxs-lookup"><span data-stu-id="03c6a-134">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span></span>

## <a name="see-also"></a><span data-ttu-id="03c6a-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="03c6a-135">See also</span></span>

- [<span data-ttu-id="03c6a-136">Procedury</span><span class="sxs-lookup"><span data-stu-id="03c6a-136">Procedures</span></span>](./index.md)
- [<span data-ttu-id="03c6a-137">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="03c6a-137">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="03c6a-138">Postupy: Předání argumentů proceduře</span><span class="sxs-lookup"><span data-stu-id="03c6a-138">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="03c6a-139">Předávání argumentů podle hodnoty a reference</span><span class="sxs-lookup"><span data-stu-id="03c6a-139">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="03c6a-140">Volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="03c6a-140">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="03c6a-141">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="03c6a-141">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="03c6a-142">Volitelné</span><span class="sxs-lookup"><span data-stu-id="03c6a-142">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)
- [<span data-ttu-id="03c6a-143">ParamArray</span><span class="sxs-lookup"><span data-stu-id="03c6a-143">ParamArray</span></span>](../../../../visual-basic/language-reference/modifiers/paramarray.md)
