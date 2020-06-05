---
title: Function – příkaz
ms.date: 05/12/2018
f1_keywords:
- vb.Function
helpviewer_keywords:
- procedures [Visual Basic], creating
- Function procedures [Visual Basic], Function statement syntax
- functions [Visual Basic], function procedures
- ParamArray keyword [Visual Basic], Function statements
- Private keyword [Visual Basic], Function statements
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- Public keyword [Visual Basic], in Function statement
- ByVal keyword [Visual Basic], Function statements
- procedures [Visual Basic], recursive
- Implements keyword [Visual Basic], Function statements
- procedures [Visual Basic], returning values
- Exit statement [Visual Basic], in Function procedures
- recursive procedures
- As keyword [Visual Basic], in Function statement
- Optional keyword [Visual Basic], Function statements
- Function statement [Visual Basic]
- Visual Basic code, Function procedures
- procedures [Visual Basic], function
- ByRef keyword [Visual Basic], Function statements
- Friend keyword [Visual Basic], Function statements
- End keyword [Visual Basic], Function statements
- Handles keyword [Visual Basic], Function statements
ms.assetid: a4497077-0f46-4ede-a27f-9e8670df52b9
ms.openlocfilehash: 49cf4fead2c5594b7ac6815f82fea0dc995ea436
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404625"
---
# <a name="function-statement-visual-basic"></a><span data-ttu-id="82baa-102">Function – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82baa-102">Function Statement (Visual Basic)</span></span>

<span data-ttu-id="82baa-103">Deklaruje název, parametry a kód, které definují `Function` proceduru.</span><span class="sxs-lookup"><span data-stu-id="82baa-103">Declares the name, parameters, and code that define a `Function` procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="82baa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82baa-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Function ]
    [ statements ]
End Function
```

## <a name="parts"></a><span data-ttu-id="82baa-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="82baa-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="82baa-106">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="82baa-106">Optional.</span></span> <span data-ttu-id="82baa-107">Viz [seznam atributů](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="82baa-107">See [Attribute List](attribute-list.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="82baa-108">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="82baa-108">Optional.</span></span> <span data-ttu-id="82baa-109">Může to být jedna z následujících:</span><span class="sxs-lookup"><span data-stu-id="82baa-109">Can be one of the following:</span></span>

  - [<span data-ttu-id="82baa-110">Republik</span><span class="sxs-lookup"><span data-stu-id="82baa-110">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="82baa-111">Proti</span><span class="sxs-lookup"><span data-stu-id="82baa-111">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="82baa-112">Friend</span><span class="sxs-lookup"><span data-stu-id="82baa-112">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="82baa-113">Hlášen</span><span class="sxs-lookup"><span data-stu-id="82baa-113">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="82baa-114">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="82baa-114">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="82baa-115">Soukromé chráněné</span><span class="sxs-lookup"><span data-stu-id="82baa-115">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="82baa-116">Podívejte [se na úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="82baa-116">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `proceduremodifiers`

  <span data-ttu-id="82baa-117">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="82baa-117">Optional.</span></span> <span data-ttu-id="82baa-118">Může to být jedna z následujících:</span><span class="sxs-lookup"><span data-stu-id="82baa-118">Can be one of the following:</span></span>

  - [<span data-ttu-id="82baa-119">Přetížení</span><span class="sxs-lookup"><span data-stu-id="82baa-119">Overloads</span></span>](../modifiers/overloads.md)

  - [<span data-ttu-id="82baa-120">Přepsání</span><span class="sxs-lookup"><span data-stu-id="82baa-120">Overrides</span></span>](../modifiers/overrides.md)

  - [<span data-ttu-id="82baa-121">Overridable</span><span class="sxs-lookup"><span data-stu-id="82baa-121">Overridable</span></span>](../modifiers/overridable.md)

  - [<span data-ttu-id="82baa-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="82baa-122">NotOverridable</span></span>](../modifiers/notoverridable.md)

  - [<span data-ttu-id="82baa-123">MustOverride</span><span class="sxs-lookup"><span data-stu-id="82baa-123">MustOverride</span></span>](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="82baa-124">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="82baa-124">Optional.</span></span> <span data-ttu-id="82baa-125">Viz [Shared](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="82baa-125">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="82baa-126">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="82baa-126">Optional.</span></span> <span data-ttu-id="82baa-127">Viz [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="82baa-127">See [Shadows](../modifiers/shadows.md).</span></span>

- `Async`

  <span data-ttu-id="82baa-128">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="82baa-128">Optional.</span></span> <span data-ttu-id="82baa-129">Viz [Async](../modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="82baa-129">See [Async](../modifiers/async.md).</span></span>

- `Iterator`

  <span data-ttu-id="82baa-130">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="82baa-130">Optional.</span></span> <span data-ttu-id="82baa-131">Podívejte se na [iterátor](../modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="82baa-131">See [Iterator](../modifiers/iterator.md).</span></span>

- `name`

  <span data-ttu-id="82baa-132">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="82baa-132">Required.</span></span> <span data-ttu-id="82baa-133">Název procedury.</span><span class="sxs-lookup"><span data-stu-id="82baa-133">Name of the procedure.</span></span> <span data-ttu-id="82baa-134">Viz [deklarované názvy elementů](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="82baa-134">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `typeparamlist`

  <span data-ttu-id="82baa-135">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="82baa-135">Optional.</span></span> <span data-ttu-id="82baa-136">Seznam parametrů typu pro obecný postup</span><span class="sxs-lookup"><span data-stu-id="82baa-136">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="82baa-137">Viz [seznam typů](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="82baa-137">See [Type List](type-list.md).</span></span>

- `parameterlist`

  <span data-ttu-id="82baa-138">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="82baa-138">Optional.</span></span> <span data-ttu-id="82baa-139">Seznam názvů místních proměnných, které představují parametry tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="82baa-139">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="82baa-140">Viz [seznam parametrů](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="82baa-140">See [Parameter List](parameter-list.md).</span></span>

- `returntype`

  <span data-ttu-id="82baa-141">Požadováno v `Option Strict` případě `On` , že je.</span><span class="sxs-lookup"><span data-stu-id="82baa-141">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="82baa-142">Datový typ hodnoty vrácené tímto postupem.</span><span class="sxs-lookup"><span data-stu-id="82baa-142">Data type of the value returned by this procedure.</span></span>

- `Implements`

  <span data-ttu-id="82baa-143">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="82baa-143">Optional.</span></span> <span data-ttu-id="82baa-144">Označuje, že tento postup implementuje jeden nebo více `Function` postupů, každý z nich definovaný v rozhraní implementovaném touto procedurou obsahuje třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="82baa-144">Indicates that this procedure implements one or more `Function` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="82baa-145">Viz [příkaz Implements](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="82baa-145">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="82baa-146">Vyžaduje `Implements` se, pokud je zadaný.</span><span class="sxs-lookup"><span data-stu-id="82baa-146">Required if `Implements` is supplied.</span></span> <span data-ttu-id="82baa-147">Seznam `Function` implementovaných procedur.</span><span class="sxs-lookup"><span data-stu-id="82baa-147">List of `Function` procedures being implemented.</span></span>

  `implementedprocedure [ , implementedprocedure ... ]`

  <span data-ttu-id="82baa-148">Každá `implementedprocedure` z nich má následující syntaxi a části:</span><span class="sxs-lookup"><span data-stu-id="82baa-148">Each `implementedprocedure` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="82baa-149">Část</span><span class="sxs-lookup"><span data-stu-id="82baa-149">Part</span></span>|<span data-ttu-id="82baa-150">Description</span><span class="sxs-lookup"><span data-stu-id="82baa-150">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="82baa-151">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="82baa-151">Required.</span></span> <span data-ttu-id="82baa-152">Název rozhraní implementovaného touto procedurou obsahuje třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="82baa-152">Name of an interface implemented by this procedure's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="82baa-153">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="82baa-153">Required.</span></span> <span data-ttu-id="82baa-154">Název, podle kterého je procedura definovaná `interface` .</span><span class="sxs-lookup"><span data-stu-id="82baa-154">Name by which the procedure is defined in `interface`.</span></span>|

- `Handles`

  <span data-ttu-id="82baa-155">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="82baa-155">Optional.</span></span> <span data-ttu-id="82baa-156">Označuje, že tento postup může zpracovávat jednu nebo více konkrétních událostí.</span><span class="sxs-lookup"><span data-stu-id="82baa-156">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="82baa-157">Viz [Handles](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="82baa-157">See [Handles](handles-clause.md).</span></span>

- `eventlist`

  <span data-ttu-id="82baa-158">Vyžaduje `Handles` se, pokud je zadaný.</span><span class="sxs-lookup"><span data-stu-id="82baa-158">Required if `Handles` is supplied.</span></span> <span data-ttu-id="82baa-159">Seznam událostí, které tato procedura zpracovává</span><span class="sxs-lookup"><span data-stu-id="82baa-159">List of events this procedure handles.</span></span>

  `eventspecifier [ , eventspecifier ... ]`

  <span data-ttu-id="82baa-160">Každá `eventspecifier` z nich má následující syntaxi a části:</span><span class="sxs-lookup"><span data-stu-id="82baa-160">Each `eventspecifier` has the following syntax and parts:</span></span>

  `eventvariable.event`

  |<span data-ttu-id="82baa-161">Část</span><span class="sxs-lookup"><span data-stu-id="82baa-161">Part</span></span>|<span data-ttu-id="82baa-162">Description</span><span class="sxs-lookup"><span data-stu-id="82baa-162">Description</span></span>|
  |---|---|
  |`eventvariable`|<span data-ttu-id="82baa-163">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="82baa-163">Required.</span></span> <span data-ttu-id="82baa-164">Objektová proměnná deklarovaná s datovým typem třídy nebo struktury, která vyvolává událost.</span><span class="sxs-lookup"><span data-stu-id="82baa-164">Object variable declared with the data type of the class or structure that raises the event.</span></span>|
  |`event`|<span data-ttu-id="82baa-165">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="82baa-165">Required.</span></span> <span data-ttu-id="82baa-166">Název události, kterou tato procedura zpracovává</span><span class="sxs-lookup"><span data-stu-id="82baa-166">Name of the event this procedure handles.</span></span>|

- `statements`

  <span data-ttu-id="82baa-167">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="82baa-167">Optional.</span></span> <span data-ttu-id="82baa-168">Blok příkazů, které mají být provedeny v rámci tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="82baa-168">Block of statements to be executed within this procedure.</span></span>

- `End Function`

  <span data-ttu-id="82baa-169">Ukončí definici tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="82baa-169">Terminates the definition of this procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="82baa-170">Poznámky</span><span class="sxs-lookup"><span data-stu-id="82baa-170">Remarks</span></span>

<span data-ttu-id="82baa-171">Veškerý spustitelný kód musí být v rámci procedury.</span><span class="sxs-lookup"><span data-stu-id="82baa-171">All executable code must be inside a procedure.</span></span> <span data-ttu-id="82baa-172">Každý postup je deklarován v rámci třídy, struktury nebo modulu, který je označován jako obsahující třídu, strukturu nebo modul.</span><span class="sxs-lookup"><span data-stu-id="82baa-172">Each procedure, in turn, is declared within a class, a structure, or a module that is referred to as the containing class, structure, or module.</span></span>

<span data-ttu-id="82baa-173">Chcete-li vrátit hodnotu volajícímu kódu, použijte `Function` proceduru. v opačném případě použijte `Sub` proceduru.</span><span class="sxs-lookup"><span data-stu-id="82baa-173">To return a value to the calling code, use a `Function` procedure; otherwise, use a `Sub` procedure.</span></span>

## <a name="defining-a-function"></a><span data-ttu-id="82baa-174">Definování funkce</span><span class="sxs-lookup"><span data-stu-id="82baa-174">Defining a Function</span></span>

<span data-ttu-id="82baa-175">Můžete definovat `Function` proceduru pouze na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="82baa-175">You can define a `Function` procedure only at the module level.</span></span> <span data-ttu-id="82baa-176">Proto kontext deklarace pro funkci musí být třída, struktura, modul nebo rozhraní a nemůže se jednat o zdrojový soubor, obor názvů, proceduru nebo blok.</span><span class="sxs-lookup"><span data-stu-id="82baa-176">Therefore, the declaration context for a function must be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="82baa-177">Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="82baa-177">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="82baa-178">`Function`postupy jsou výchozí pro veřejný přístup.</span><span class="sxs-lookup"><span data-stu-id="82baa-178">`Function` procedures default to public access.</span></span> <span data-ttu-id="82baa-179">Můžete upravit jejich úrovně přístupu modifikátory přístupu.</span><span class="sxs-lookup"><span data-stu-id="82baa-179">You can adjust their access levels with the access modifiers.</span></span>

<span data-ttu-id="82baa-180">`Function`Procedura může deklarovat datový typ hodnoty, kterou procedura vrátí.</span><span class="sxs-lookup"><span data-stu-id="82baa-180">A `Function` procedure can declare the data type of the value that the procedure returns.</span></span> <span data-ttu-id="82baa-181">Můžete zadat libovolný datový typ nebo název výčtu, strukturu, třídu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="82baa-181">You can specify any data type or the name of an enumeration, a structure, a class, or an interface.</span></span> <span data-ttu-id="82baa-182">Pokud parametr nezadáte `returntype` , procedura se vrátí `Object` .</span><span class="sxs-lookup"><span data-stu-id="82baa-182">If you don't specify the `returntype` parameter, the procedure returns `Object`.</span></span>

<span data-ttu-id="82baa-183">Pokud tento postup používá `Implements` klíčové slovo, obsahující třídu nebo strukturu musí mít také `Implements` příkaz, který následuje hned za `Class` příkazem or `Structure` .</span><span class="sxs-lookup"><span data-stu-id="82baa-183">If this procedure uses the `Implements` keyword, the containing class or structure must also have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="82baa-184">`Implements`Příkaz musí zahrnovat každé rozhraní, které je určeno v `implementslist` .</span><span class="sxs-lookup"><span data-stu-id="82baa-184">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="82baa-185">Název, pomocí kterého rozhraní definuje `Function` (in), ale `definedname` nemusí odpovídat názvu této procedury (v `name` ).</span><span class="sxs-lookup"><span data-stu-id="82baa-185">However, the name by which an interface defines the `Function` (in `definedname`) doesn't need to match the name of this procedure (in `name`).</span></span>

> [!NOTE]
> <span data-ttu-id="82baa-186">Lambda výrazy můžete použít k definování vložených výrazů funkcí.</span><span class="sxs-lookup"><span data-stu-id="82baa-186">You can use lambda expressions to define function expressions inline.</span></span> <span data-ttu-id="82baa-187">Další informace naleznete v tématu [výraz Function](../operators/function-expression.md) a [lambda výrazy](../../programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="82baa-187">For more information, see [Function Expression](../operators/function-expression.md) and [Lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span></span>

## <a name="returning-from-a-function"></a><span data-ttu-id="82baa-188">Vrácení z funkce</span><span class="sxs-lookup"><span data-stu-id="82baa-188">Returning from a Function</span></span>

<span data-ttu-id="82baa-189">Když se `Function` procedura vrátí na volající kód, vykonání pokračuje příkazem, který následuje za příkazem, který se nazývá procedura.</span><span class="sxs-lookup"><span data-stu-id="82baa-189">When the `Function` procedure returns to the calling code, execution continues with the statement that follows the statement that called the procedure.</span></span>

<span data-ttu-id="82baa-190">Chcete-li vrátit hodnotu z funkce, můžete buď přiřadit hodnotu k názvu funkce nebo ji zahrnout do `Return` příkazu.</span><span class="sxs-lookup"><span data-stu-id="82baa-190">To return a value from a function, you can either assign the value to the function name or include it in a `Return` statement.</span></span>

<span data-ttu-id="82baa-191">`Return`Příkaz současně přiřadí návratovou hodnotu a ukončí funkci, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="82baa-191">The `Return` statement simultaneously assigns the return value and exits the function, as the following example shows.</span></span>

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

<span data-ttu-id="82baa-192">Následující příklad přiřadí návratovou hodnotu k názvu funkce `myFunction` a potom použije příkaz, `Exit Function` který se má vrátit.</span><span class="sxs-lookup"><span data-stu-id="82baa-192">The following example assigns the return value to the function name `myFunction` and then uses the `Exit Function` statement to return.</span></span>

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

<span data-ttu-id="82baa-193">`Exit Function`Příkazy a `Return` způsobují bezprostřední ukončení `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="82baa-193">The `Exit Function` and `Return` statements cause an immediate exit from a `Function` procedure.</span></span> <span data-ttu-id="82baa-194">Libovolný počet `Exit Function` příkazů a `Return` se může objevit kdekoli v proceduře a můžete kombinovat `Exit Function` a `Return` příkazy.</span><span class="sxs-lookup"><span data-stu-id="82baa-194">Any number of `Exit Function` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Function` and `Return` statements.</span></span>

<span data-ttu-id="82baa-195">Použijete `Exit Function` -li bez přiřazení hodnoty k `name` , procedura vrátí výchozí hodnotu datového typu, který je určen v `returntype` .</span><span class="sxs-lookup"><span data-stu-id="82baa-195">If you use `Exit Function` without assigning a value to `name`, the procedure returns the default value for the data type that's specified in `returntype`.</span></span> <span data-ttu-id="82baa-196">Pokud `returntype` není zadán, procedura vrátí `Nothing` , což je výchozí hodnota pro `Object` .</span><span class="sxs-lookup"><span data-stu-id="82baa-196">If `returntype` isn't specified, the procedure returns `Nothing`, which is the default value for `Object`.</span></span>

## <a name="calling-a-function"></a><span data-ttu-id="82baa-197">Volání funkce</span><span class="sxs-lookup"><span data-stu-id="82baa-197">Calling a Function</span></span>

<span data-ttu-id="82baa-198">Proceduru zavoláte `Function` pomocí názvu procedury následovaný seznamem argumentů v závorkách ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="82baa-198">You call a `Function` procedure by using the procedure name, followed by the argument list in parentheses, in an expression.</span></span> <span data-ttu-id="82baa-199">Závorky můžete vynechat pouze v případě, že neposkytujete žádné argumenty.</span><span class="sxs-lookup"><span data-stu-id="82baa-199">You can omit the parentheses only if you aren't supplying any arguments.</span></span> <span data-ttu-id="82baa-200">Váš kód je však čitelnější, pokud vždy zahrnete závorky.</span><span class="sxs-lookup"><span data-stu-id="82baa-200">However, your code is more readable if you always include the parentheses.</span></span>

<span data-ttu-id="82baa-201">Proceduru zavoláte `Function` stejným způsobem jako u libovolné funkce knihovny `Sqrt` , jako je například, `Cos` nebo `ChrW` .</span><span class="sxs-lookup"><span data-stu-id="82baa-201">You call a `Function` procedure the same way that you call any library function such as `Sqrt`, `Cos`, or `ChrW`.</span></span>

<span data-ttu-id="82baa-202">Funkci můžete také volat pomocí `Call` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="82baa-202">You can also call a function by using the `Call` keyword.</span></span> <span data-ttu-id="82baa-203">V takovém případě se návratová hodnota ignoruje.</span><span class="sxs-lookup"><span data-stu-id="82baa-203">In that case, the return value is ignored.</span></span> <span data-ttu-id="82baa-204">`Call`Ve většině případů se použití klíčového slova nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="82baa-204">Use of the `Call` keyword isn't recommended in most cases.</span></span> <span data-ttu-id="82baa-205">Další informace naleznete v tématu [Call Statement](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="82baa-205">For more information, see [Call Statement](call-statement.md).</span></span>

<span data-ttu-id="82baa-206">Visual Basic někdy mění uspořádání aritmetických výrazů a zvyšuje tak vnitřní efektivitu.</span><span class="sxs-lookup"><span data-stu-id="82baa-206">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="82baa-207">Z tohoto důvodu byste neměli použít `Function` proceduru v aritmetickém výrazu, pokud funkce změní hodnotu proměnných ve stejném výrazu.</span><span class="sxs-lookup"><span data-stu-id="82baa-207">For that reason, you shouldn't use a `Function` procedure in an arithmetic expression when the function changes the value of variables in the same expression.</span></span>

## <a name="async-functions"></a><span data-ttu-id="82baa-208">Asynchronní funkce</span><span class="sxs-lookup"><span data-stu-id="82baa-208">Async Functions</span></span>

<span data-ttu-id="82baa-209">*Asynchronní* funkce umožňuje vyvolat asynchronní funkce bez použití explicitního zpětného volání nebo ručního rozdělení kódu napříč více funkcemi nebo lambda výrazy.</span><span class="sxs-lookup"><span data-stu-id="82baa-209">The *Async* feature allows you to invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>

<span data-ttu-id="82baa-210">Pokud označíte funkci s modifikátorem [Async](../modifiers/async.md) , můžete použít operátor [await](../operators/await-operator.md) ve funkci.</span><span class="sxs-lookup"><span data-stu-id="82baa-210">If you mark a function with the [Async](../modifiers/async.md) modifier, you can use the [Await](../operators/await-operator.md) operator in the function.</span></span> <span data-ttu-id="82baa-211">Když ovládací prvek dosáhne `Await` výrazu ve `Async` funkci, ovládací prvek se vrátí volajícímu a průběh funkce je pozastaven, dokud se nedokončí očekávaný úkol.</span><span class="sxs-lookup"><span data-stu-id="82baa-211">When control reaches an `Await` expression in the `Async` function, control returns to the caller, and progress in the function is suspended until the awaited task completes.</span></span> <span data-ttu-id="82baa-212">Po dokončení úlohy může provádění pokračovat ve funkci.</span><span class="sxs-lookup"><span data-stu-id="82baa-212">When the task is complete, execution can resume in the function.</span></span>

> [!NOTE]
> <span data-ttu-id="82baa-213">`Async`Procedura se vrátí volajícímu, když dojde k prvnímu očekávanému objektu, který ještě nebyl dokončen, nebo se dostane na konec `Async` procedury, podle toho, co nastane dříve.</span><span class="sxs-lookup"><span data-stu-id="82baa-213">An `Async` procedure returns to the caller when either it encounters the first awaited object that’s not yet complete, or it gets to the end of the `Async` procedure, whichever occurs first.</span></span>

<span data-ttu-id="82baa-214">`Async`Funkce může mít návratový typ <xref:System.Threading.Tasks.Task%601> nebo <xref:System.Threading.Tasks.Task> .</span><span class="sxs-lookup"><span data-stu-id="82baa-214">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="82baa-215">Příklad `Async` funkce, která má návratový typ, <xref:System.Threading.Tasks.Task%601> je uveden níže.</span><span class="sxs-lookup"><span data-stu-id="82baa-215">An example of an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601> is provided below.</span></span>

<span data-ttu-id="82baa-216">`Async`Funkce nemůže deklarovat žádné parametry [ByRef](../modifiers/byref.md) .</span><span class="sxs-lookup"><span data-stu-id="82baa-216">An `Async` function cannot declare any [ByRef](../modifiers/byref.md) parameters.</span></span>

<span data-ttu-id="82baa-217">[Dílčí příkaz](sub-statement.md) lze také označit `Async` modifikátorem.</span><span class="sxs-lookup"><span data-stu-id="82baa-217">A [Sub Statement](sub-statement.md) can also be marked with the `Async` modifier.</span></span> <span data-ttu-id="82baa-218">Používá se hlavně pro obslužné rutiny událostí, kde nelze vracet hodnotu.</span><span class="sxs-lookup"><span data-stu-id="82baa-218">This is primarily used for event handlers, where a value cannot be returned.</span></span> <span data-ttu-id="82baa-219">`Async` `Sub` Procedura nemůže být očekávána a volající `Async` `Sub` procedury nemůže zachytit výjimky, které jsou vyvolány `Sub` procedurou.</span><span class="sxs-lookup"><span data-stu-id="82baa-219">An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that are thrown by the `Sub` procedure.</span></span>

<span data-ttu-id="82baa-220">Další informace o `Async` funkcích naleznete v tématu [asynchronní programování s Async a await](../../programming-guide/concepts/async/index.md), [řízení toku v asynchronních programech](../../programming-guide/concepts/async/control-flow-in-async-programs.md)a [Asynchronní návratové typy](../../programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="82baa-220">For more information about `Async` functions, see [Asynchronous Programming with Async and Await](../../programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="iterator-functions"></a><span data-ttu-id="82baa-221">Funkce iterátoru</span><span class="sxs-lookup"><span data-stu-id="82baa-221">Iterator Functions</span></span>

<span data-ttu-id="82baa-222">Funkce *iterátoru* provádí vlastní iteraci v kolekci, jako je například list nebo Array.</span><span class="sxs-lookup"><span data-stu-id="82baa-222">An *iterator* function performs a custom iteration over a collection, such as a list or array.</span></span> <span data-ttu-id="82baa-223">Funkce iterátoru používá příkaz [yield](yield-statement.md) k vrácení jednotlivých prvků po jednom.</span><span class="sxs-lookup"><span data-stu-id="82baa-223">An iterator function uses the [Yield](yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="82baa-224">Při dosažení příkazu [yield](yield-statement.md) se aktuální umístění v kódu pamatuje.</span><span class="sxs-lookup"><span data-stu-id="82baa-224">When a [Yield](yield-statement.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="82baa-225">Spuštění je restartováno z tohoto umístění při příštím volání funkce iterátoru.</span><span class="sxs-lookup"><span data-stu-id="82baa-225">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="82baa-226">Můžete zavolat iterátor z klientského kódu s použitím [pro každý... Další](for-each-next-statement.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="82baa-226">You call an iterator from client code by using a [For Each…Next](for-each-next-statement.md) statement.</span></span>

<span data-ttu-id="82baa-227">Návratový typ funkce iterátoru může být <xref:System.Collections.IEnumerable> , <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Collections.IEnumerator> nebo <xref:System.Collections.Generic.IEnumerator%601> .</span><span class="sxs-lookup"><span data-stu-id="82baa-227">The return type of an iterator function can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="82baa-228">Další informace najdete v tématu [iterátory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="82baa-228">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>

## <a name="example"></a><span data-ttu-id="82baa-229">Příklad</span><span class="sxs-lookup"><span data-stu-id="82baa-229">Example</span></span>

<span data-ttu-id="82baa-230">Následující příklad používá `Function` příkaz k deklaraci názvu, parametrů a kódu, který tvoří tělo `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="82baa-230">The following example uses the `Function` statement to declare the name, parameters, and code that form the body of a `Function` procedure.</span></span> <span data-ttu-id="82baa-231">`ParamArray`Modifikátor umožňuje funkci přijmout proměnlivý počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="82baa-231">The `ParamArray` modifier enables the function to accept a variable number of arguments.</span></span>

[!code-vb[VbVbalrStatements#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#25)]

## <a name="example"></a><span data-ttu-id="82baa-232">Příklad</span><span class="sxs-lookup"><span data-stu-id="82baa-232">Example</span></span>

<span data-ttu-id="82baa-233">Následující příklad vyvolá funkci deklarovanou v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="82baa-233">The following example invokes the function declared in the preceding example.</span></span>

[!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]

## <a name="example"></a><span data-ttu-id="82baa-234">Příklad</span><span class="sxs-lookup"><span data-stu-id="82baa-234">Example</span></span>

<span data-ttu-id="82baa-235">V následujícím příkladu je, `DelayAsync` `Async` `Function` který má návratový typ <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="82baa-235">In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="82baa-236">`DelayAsync`obsahuje `Return` příkaz, který vrací celé číslo.</span><span class="sxs-lookup"><span data-stu-id="82baa-236">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="82baa-237">Proto deklarace funkce `DelayAsync` musí mít návratový typ `Task(Of Integer)` .</span><span class="sxs-lookup"><span data-stu-id="82baa-237">Therefore the function declaration of `DelayAsync` needs to have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="82baa-238">Vzhledem k tomu, že návratový typ je `Task(Of Integer)` , vyhodnocení `Await` výrazu v `DoSomethingAsync` vytvoří celé číslo.</span><span class="sxs-lookup"><span data-stu-id="82baa-238">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer.</span></span> <span data-ttu-id="82baa-239">To je znázorněno v tomto prohlášení: `Dim result As Integer = Await delayTask` .</span><span class="sxs-lookup"><span data-stu-id="82baa-239">This is demonstrated in this statement: `Dim result As Integer = Await delayTask`.</span></span>

<span data-ttu-id="82baa-240">`startButton_Click`Procedura je příkladem `Async Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="82baa-240">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="82baa-241">Vzhledem k tomu `DoSomethingAsync` `Async` , že je funkce, úloha pro volání `DoSomethingAsync` musí být očekávána, jak ukazuje následující příkaz: `Await DoSomethingAsync()` .</span><span class="sxs-lookup"><span data-stu-id="82baa-241">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement demonstrates: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="82baa-242">`startButton_Click` `Sub` Procedura musí být definována s `Async` modifikátorem, protože má `Await` výraz.</span><span class="sxs-lookup"><span data-stu-id="82baa-242">The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="82baa-243">Viz také</span><span class="sxs-lookup"><span data-stu-id="82baa-243">See also</span></span>

- [<span data-ttu-id="82baa-244">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="82baa-244">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="82baa-245">Procedury funkcí</span><span class="sxs-lookup"><span data-stu-id="82baa-245">Function Procedures</span></span>](../../programming-guide/language-features/procedures/function-procedures.md)
- [<span data-ttu-id="82baa-246">Seznam parametrů</span><span class="sxs-lookup"><span data-stu-id="82baa-246">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="82baa-247">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="82baa-247">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="82baa-248">Call – příkaz</span><span class="sxs-lookup"><span data-stu-id="82baa-248">Call Statement</span></span>](call-statement.md)
- [<span data-ttu-id="82baa-249">Tohoto</span><span class="sxs-lookup"><span data-stu-id="82baa-249">Of</span></span>](of-clause.md)
- [<span data-ttu-id="82baa-250">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="82baa-250">Parameter Arrays</span></span>](../../programming-guide/language-features/procedures/parameter-arrays.md)
- [<span data-ttu-id="82baa-251">Postupy: Použití obecné třídy</span><span class="sxs-lookup"><span data-stu-id="82baa-251">How to: Use a Generic Class</span></span>](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="82baa-252">Řešení potíží s procedurami</span><span class="sxs-lookup"><span data-stu-id="82baa-252">Troubleshooting Procedures</span></span>](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [<span data-ttu-id="82baa-253">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="82baa-253">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="82baa-254">Výraz funkce</span><span class="sxs-lookup"><span data-stu-id="82baa-254">Function Expression</span></span>](../operators/function-expression.md)
