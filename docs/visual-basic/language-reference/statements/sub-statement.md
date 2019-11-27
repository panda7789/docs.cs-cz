---
title: Sub – příkaz
ms.date: 05/12/2018
f1_keywords:
- vb.Sub
helpviewer_keywords:
- Public keyword [Visual Basic], Sub statements
- procedures [Visual Basic], creating
- declaring procedures [Visual Basic], Sub statement
- arguments [Visual Basic], Sub procedures
- As keyword [Visual Basic], Sub statements
- Optional keyword [Visual Basic], Sub statements
- declarations [Visual Basic], procedures
- Sub keyword [Visual Basic]
- Handles keyword [Visual Basic], Sub statements
- Protected Friend keyword [Visual Basic]
- ParamArray keyword [Visual Basic], Sub statements
- Implements keyword [Visual Basic], Sub statements
- Sub statement [Visual Basic]
- subroutines
- ByRef keyword [Visual Basic], Sub statements
- Sub procedures [Visual Basic], Sub statement
- recursive procedures
- Private keyword [Visual Basic], Sub statements
- Friend keyword [Visual Basic], Sub statements
- Exit statement [Visual Basic], Sub statements
- procedures [Visual Basic], Sub
- End keyword [Visual Basic], Sub statements
- ByVal keyword [Visual Basic], Sub statements
- Visual Basic code, Sub procedures
ms.assetid: e347d700-d06c-405b-b302-e9b1edb57dfc
ms.openlocfilehash: da498a5e0a3633eb98882aaed145fcd21ab169fd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346443"
---
# <a name="sub-statement-visual-basic"></a><span data-ttu-id="0c716-102">Sub – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c716-102">Sub Statement (Visual Basic)</span></span>

<span data-ttu-id="0c716-103">Deklaruje název, parametry a kód, které definují proceduru `Sub`.</span><span class="sxs-lookup"><span data-stu-id="0c716-103">Declares the name, parameters, and code that define a `Sub` procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="0c716-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c716-104">Syntax</span></span>

```vb
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Sub ]
    [ statements ]
End Sub
```

## <a name="parts"></a><span data-ttu-id="0c716-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="0c716-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="0c716-106">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="0c716-106">Optional.</span></span> <span data-ttu-id="0c716-107">Viz [seznam atributů](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="0c716-107">See [Attribute List](attribute-list.md).</span></span>

- `Partial`

  <span data-ttu-id="0c716-108">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="0c716-108">Optional.</span></span> <span data-ttu-id="0c716-109">Označuje definici částečné metody.</span><span class="sxs-lookup"><span data-stu-id="0c716-109">Indicates definition of a partial method.</span></span> <span data-ttu-id="0c716-110">Viz [částečné metody](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="0c716-110">See [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="0c716-111">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="0c716-111">Optional.</span></span> <span data-ttu-id="0c716-112">Může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="0c716-112">Can be one of the following:</span></span>

  - [<span data-ttu-id="0c716-113">Public</span><span class="sxs-lookup"><span data-stu-id="0c716-113">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="0c716-114">Protected</span><span class="sxs-lookup"><span data-stu-id="0c716-114">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="0c716-115">Friend</span><span class="sxs-lookup"><span data-stu-id="0c716-115">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="0c716-116">Private</span><span class="sxs-lookup"><span data-stu-id="0c716-116">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="0c716-117">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="0c716-117">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)

  - [<span data-ttu-id="0c716-118">Private Protected</span><span class="sxs-lookup"><span data-stu-id="0c716-118">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)

  <span data-ttu-id="0c716-119">Podívejte [se na úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="0c716-119">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `proceduremodifiers`

  <span data-ttu-id="0c716-120">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="0c716-120">Optional.</span></span> <span data-ttu-id="0c716-121">Může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="0c716-121">Can be one of the following:</span></span>

  - [<span data-ttu-id="0c716-122">Overloads</span><span class="sxs-lookup"><span data-stu-id="0c716-122">Overloads</span></span>](../modifiers/overloads.md)

  - [<span data-ttu-id="0c716-123">Overrides</span><span class="sxs-lookup"><span data-stu-id="0c716-123">Overrides</span></span>](../modifiers/overrides.md)

  - [<span data-ttu-id="0c716-124">Overridable</span><span class="sxs-lookup"><span data-stu-id="0c716-124">Overridable</span></span>](../modifiers/overridable.md)

  - [<span data-ttu-id="0c716-125">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="0c716-125">NotOverridable</span></span>](../modifiers/notoverridable.md)

  - [<span data-ttu-id="0c716-126">MustOverride</span><span class="sxs-lookup"><span data-stu-id="0c716-126">MustOverride</span></span>](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="0c716-127">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="0c716-127">Optional.</span></span> <span data-ttu-id="0c716-128">Viz [Shared](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="0c716-128">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="0c716-129">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="0c716-129">Optional.</span></span> <span data-ttu-id="0c716-130">Viz [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="0c716-130">See [Shadows](../modifiers/shadows.md).</span></span>

- `Async`

  <span data-ttu-id="0c716-131">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="0c716-131">Optional.</span></span> <span data-ttu-id="0c716-132">Viz [Async](../modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="0c716-132">See [Async](../modifiers/async.md).</span></span>

- `name`

  <span data-ttu-id="0c716-133">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="0c716-133">Required.</span></span> <span data-ttu-id="0c716-134">Název procedury.</span><span class="sxs-lookup"><span data-stu-id="0c716-134">Name of the procedure.</span></span> <span data-ttu-id="0c716-135">Viz [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="0c716-135">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span> <span data-ttu-id="0c716-136">Chcete-li vytvořit proceduru konstruktoru pro třídu, nastavte název `Sub` procedury na klíčové slovo `New`.</span><span class="sxs-lookup"><span data-stu-id="0c716-136">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="0c716-137">Další informace naleznete v tématu [Doba života objektu: vytváření a zničení objektů](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="0c716-137">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

- `typeparamlist`

  <span data-ttu-id="0c716-138">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="0c716-138">Optional.</span></span> <span data-ttu-id="0c716-139">Seznam parametrů typu pro obecný postup</span><span class="sxs-lookup"><span data-stu-id="0c716-139">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="0c716-140">Viz [seznam typů](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="0c716-140">See [Type List](type-list.md).</span></span>

- `parameterlist`

  <span data-ttu-id="0c716-141">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="0c716-141">Optional.</span></span> <span data-ttu-id="0c716-142">Seznam názvů místních proměnných, které představují parametry tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="0c716-142">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="0c716-143">Viz [seznam parametrů](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="0c716-143">See [Parameter List](parameter-list.md).</span></span>

- `Implements`

  <span data-ttu-id="0c716-144">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="0c716-144">Optional.</span></span> <span data-ttu-id="0c716-145">Označuje, že tento postup implementuje jeden nebo více `Sub` procedur, každý z nich definovaný v rozhraní implementovaném touto procedurou obsahuje třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="0c716-145">Indicates that this procedure implements one or more `Sub` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="0c716-146">Viz [příkaz Implements](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0c716-146">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="0c716-147">Vyžaduje se, pokud je dodána `Implements`.</span><span class="sxs-lookup"><span data-stu-id="0c716-147">Required if `Implements` is supplied.</span></span> <span data-ttu-id="0c716-148">Seznam `Sub`ch procedur, které jsou implementovány.</span><span class="sxs-lookup"><span data-stu-id="0c716-148">List of `Sub` procedures being implemented.</span></span>

  `implementedprocedure [ , implementedprocedure ... ]`

  <span data-ttu-id="0c716-149">Každý `implementedprocedure` má následující syntaxi a části:</span><span class="sxs-lookup"><span data-stu-id="0c716-149">Each `implementedprocedure` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="0c716-150">Částí</span><span class="sxs-lookup"><span data-stu-id="0c716-150">Part</span></span>|<span data-ttu-id="0c716-151">Popis</span><span class="sxs-lookup"><span data-stu-id="0c716-151">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="0c716-152">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="0c716-152">Required.</span></span> <span data-ttu-id="0c716-153">Název rozhraní implementovaného touto procedurou obsahuje třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="0c716-153">Name of an interface implemented by this procedure's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="0c716-154">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="0c716-154">Required.</span></span> <span data-ttu-id="0c716-155">Název, podle kterého je procedura definovaná v `interface`.</span><span class="sxs-lookup"><span data-stu-id="0c716-155">Name by which the procedure is defined in `interface`.</span></span>|

- `Handles`

  <span data-ttu-id="0c716-156">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="0c716-156">Optional.</span></span> <span data-ttu-id="0c716-157">Označuje, že tento postup může zpracovávat jednu nebo více konkrétních událostí.</span><span class="sxs-lookup"><span data-stu-id="0c716-157">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="0c716-158">Viz [Handles](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="0c716-158">See [Handles](handles-clause.md).</span></span>

- `eventlist`

  <span data-ttu-id="0c716-159">Vyžaduje se, pokud je dodána `Handles`.</span><span class="sxs-lookup"><span data-stu-id="0c716-159">Required if `Handles` is supplied.</span></span> <span data-ttu-id="0c716-160">Seznam událostí, které tato procedura zpracovává</span><span class="sxs-lookup"><span data-stu-id="0c716-160">List of events this procedure handles.</span></span>

  `eventspecifier [ , eventspecifier ... ]`

  <span data-ttu-id="0c716-161">Každý `eventspecifier` má následující syntaxi a části:</span><span class="sxs-lookup"><span data-stu-id="0c716-161">Each `eventspecifier` has the following syntax and parts:</span></span>

  `eventvariable.event`

  |<span data-ttu-id="0c716-162">Částí</span><span class="sxs-lookup"><span data-stu-id="0c716-162">Part</span></span>|<span data-ttu-id="0c716-163">Popis</span><span class="sxs-lookup"><span data-stu-id="0c716-163">Description</span></span>|
  |---|---|
  |`eventvariable`|<span data-ttu-id="0c716-164">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="0c716-164">Required.</span></span> <span data-ttu-id="0c716-165">Objektová proměnná deklarovaná s datovým typem třídy nebo struktury, která vyvolává událost.</span><span class="sxs-lookup"><span data-stu-id="0c716-165">Object variable declared with the data type of the class or structure that raises the event.</span></span>|
  |`event`|<span data-ttu-id="0c716-166">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="0c716-166">Required.</span></span> <span data-ttu-id="0c716-167">Název události, kterou tato procedura zpracovává</span><span class="sxs-lookup"><span data-stu-id="0c716-167">Name of the event this procedure handles.</span></span>|

- `statements`

  <span data-ttu-id="0c716-168">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="0c716-168">Optional.</span></span> <span data-ttu-id="0c716-169">Blok příkazů, které mají být spuštěny v rámci tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="0c716-169">Block of statements to run within this procedure.</span></span>

- `End Sub`

  <span data-ttu-id="0c716-170">Ukončí definici tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="0c716-170">Terminates the definition of this procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="0c716-171">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0c716-171">Remarks</span></span>

<span data-ttu-id="0c716-172">Veškerý spustitelný kód musí být v rámci procedury.</span><span class="sxs-lookup"><span data-stu-id="0c716-172">All executable code must be inside a procedure.</span></span> <span data-ttu-id="0c716-173">Pokud nechcete vracet hodnotu volajícímu kódu, použijte `Sub` proceduru.</span><span class="sxs-lookup"><span data-stu-id="0c716-173">Use a `Sub` procedure when you don't want to return a value to the calling code.</span></span> <span data-ttu-id="0c716-174">Pokud chcete vrátit hodnotu, použijte `Function` proceduru.</span><span class="sxs-lookup"><span data-stu-id="0c716-174">Use a `Function` procedure when you want to return a value.</span></span>

## <a name="defining-a-sub-procedure"></a><span data-ttu-id="0c716-175">Definování procedury Sub</span><span class="sxs-lookup"><span data-stu-id="0c716-175">Defining a Sub Procedure</span></span>

<span data-ttu-id="0c716-176">Můžete definovat `Sub` proceduru pouze na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="0c716-176">You can define a `Sub` procedure only at the module level.</span></span> <span data-ttu-id="0c716-177">Kontext deklarace pro proceduru Sub musí tedy být třída, struktura, modul nebo rozhraní a nemůže se jednat o zdrojový soubor, obor názvů, proceduru nebo blok.</span><span class="sxs-lookup"><span data-stu-id="0c716-177">The declaration context for a sub procedure must, therefore, be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="0c716-178">Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="0c716-178">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="0c716-179">výchozími postupy `Sub` jsou veřejné přístupy.</span><span class="sxs-lookup"><span data-stu-id="0c716-179">`Sub` procedures default to public access.</span></span> <span data-ttu-id="0c716-180">Úrovně přístupu můžete upravit pomocí modifikátorů přístupu.</span><span class="sxs-lookup"><span data-stu-id="0c716-180">You can adjust their access levels by using the access modifiers.</span></span>

<span data-ttu-id="0c716-181">Pokud procedura používá klíčové slovo `Implements`, obsahující třídu nebo strukturu musí mít příkaz `Implements`, který následuje bezprostředně za `Class` nebo `Structure` příkaz.</span><span class="sxs-lookup"><span data-stu-id="0c716-181">If the procedure uses the `Implements` keyword, the containing class or structure must have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="0c716-182">Příkaz `Implements` musí zahrnovat každé rozhraní, které je určeno v `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="0c716-182">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="0c716-183">Název, kterým rozhraní definuje `Sub` (v `definedname`), ale nemusí odpovídat názvu tohoto postupu (v `name`).</span><span class="sxs-lookup"><span data-stu-id="0c716-183">However, the name by which an interface defines the `Sub` (in `definedname`) doesn't have to match the name of this procedure (in `name`).</span></span>

## <a name="returning-from-a-sub-procedure"></a><span data-ttu-id="0c716-184">Vrácení z procedury Sub</span><span class="sxs-lookup"><span data-stu-id="0c716-184">Returning from a Sub Procedure</span></span>

<span data-ttu-id="0c716-185">Když se `Sub` procedura vrátí k volajícímu kódu, provádění pokračuje příkazem po příkazu, který ho volal.</span><span class="sxs-lookup"><span data-stu-id="0c716-185">When a `Sub` procedure returns to the calling code, execution continues with the statement after the statement that called it.</span></span>

<span data-ttu-id="0c716-186">Následující příklad ukazuje návrat z `Sub` proceduře.</span><span class="sxs-lookup"><span data-stu-id="0c716-186">The following example shows a return from a `Sub` procedure.</span></span>

```vb
Sub mySub(ByVal q As String)
    Return
End Sub
```

<span data-ttu-id="0c716-187">Příkazy `Exit Sub` a `Return` způsobují bezprostřední ukončení `Sub`ho postupu.</span><span class="sxs-lookup"><span data-stu-id="0c716-187">The `Exit Sub` and `Return` statements cause an immediate exit from a `Sub` procedure.</span></span> <span data-ttu-id="0c716-188">Libovolný počet `Exit Sub` a `Return` příkazů se může objevit kdekoli v proceduře a můžete kombinovat `Exit Sub` a `Return` příkazy.</span><span class="sxs-lookup"><span data-stu-id="0c716-188">Any number of `Exit Sub` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Sub` and `Return` statements.</span></span>

## <a name="calling-a-sub-procedure"></a><span data-ttu-id="0c716-189">Volání procedury Sub</span><span class="sxs-lookup"><span data-stu-id="0c716-189">Calling a Sub Procedure</span></span>

<span data-ttu-id="0c716-190">Proceduru `Sub` zavoláte pomocí názvu procedury v příkazu a potom následujícím názvem se seznamem argumentů v závorkách.</span><span class="sxs-lookup"><span data-stu-id="0c716-190">You call a `Sub` procedure by using the procedure name in a statement and then following that name with its argument list in parentheses.</span></span> <span data-ttu-id="0c716-191">Závorky můžete vynechat pouze v případě, že nezadáte žádné argumenty.</span><span class="sxs-lookup"><span data-stu-id="0c716-191">You can omit the parentheses only if you don't supply any arguments.</span></span> <span data-ttu-id="0c716-192">Váš kód je však čitelnější, pokud vždy zahrnete závorky.</span><span class="sxs-lookup"><span data-stu-id="0c716-192">However, your code is more readable if you always include the parentheses.</span></span>

<span data-ttu-id="0c716-193">Procedura `Sub` a procedura `Function` mohou mít parametry a provádět sérii příkazů.</span><span class="sxs-lookup"><span data-stu-id="0c716-193">A `Sub` procedure and a `Function` procedure  can have parameters and perform a series of statements.</span></span> <span data-ttu-id="0c716-194">Nicméně procedura `Function` vrátí hodnotu a `Sub` procedura ne.</span><span class="sxs-lookup"><span data-stu-id="0c716-194">However, a `Function` procedure returns a value, and a `Sub` procedure doesn't.</span></span> <span data-ttu-id="0c716-195">Proto nemůžete ve výrazu použít `Sub` proceduru.</span><span class="sxs-lookup"><span data-stu-id="0c716-195">Therefore, you can't use a `Sub` procedure in an expression.</span></span>

<span data-ttu-id="0c716-196">Klíčové slovo `Call` můžete použít při volání `Sub` procedury, ale toto klíčové slovo se pro většinu použití nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="0c716-196">You can use the `Call` keyword when you call a `Sub` procedure, but that keyword isn't recommended for most uses.</span></span> <span data-ttu-id="0c716-197">Další informace naleznete v tématu [Call Statement](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0c716-197">For more information, see [Call Statement](call-statement.md).</span></span>

<span data-ttu-id="0c716-198">Visual Basic někdy mění uspořádání aritmetických výrazů a zvyšuje tak vnitřní efektivitu.</span><span class="sxs-lookup"><span data-stu-id="0c716-198">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="0c716-199">Z tohoto důvodu, pokud seznam argumentů obsahuje výrazy, které volají jiné procedury, neměli byste předpokládat, že tyto výrazy budou volány v určitém pořadí.</span><span class="sxs-lookup"><span data-stu-id="0c716-199">For that reason, if your argument list includes expressions that call other procedures, you shouldn't assume that those expressions will be called in a particular order.</span></span>

## <a name="async-sub-procedures"></a><span data-ttu-id="0c716-200">Asynchronní procedury Sub</span><span class="sxs-lookup"><span data-stu-id="0c716-200">Async Sub Procedures</span></span>

<span data-ttu-id="0c716-201">Pomocí asynchronní funkce můžete vyvolat asynchronní funkce bez použití explicitního zpětného volání nebo ruční rozdělení kódu napříč více funkcemi nebo lambda výrazy.</span><span class="sxs-lookup"><span data-stu-id="0c716-201">By using the Async feature, you can invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>

<span data-ttu-id="0c716-202">Pokud označíte proceduru modifikátorem [Async](../modifiers/async.md) , můžete použít operátor [await](../../../visual-basic/language-reference/operators/await-operator.md) v proceduře.</span><span class="sxs-lookup"><span data-stu-id="0c716-202">If you mark a procedure with the [Async](../modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the procedure.</span></span> <span data-ttu-id="0c716-203">Když ovládací prvek dosáhne `Await` výraz v proceduře `Async`, ovládací prvek se vrátí volajícímu a průběh procedury je pozastaven, dokud se nedokončí očekávaný úkol.</span><span class="sxs-lookup"><span data-stu-id="0c716-203">When control reaches an `Await` expression in the `Async` procedure, control returns to the caller, and progress in the procedure is suspended until the awaited task completes.</span></span> <span data-ttu-id="0c716-204">Po dokončení úlohy může provádění pokračovat postupem.</span><span class="sxs-lookup"><span data-stu-id="0c716-204">When the task is complete, execution can resume in the procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="0c716-205">`Async` procedura se vrátí volajícímu, když buď dojde k prvnímu očekávanému objektu, který ještě nebyl dokončen, nebo je dosaženo konce `Async` postupu, podle toho, co nastane dříve.</span><span class="sxs-lookup"><span data-stu-id="0c716-205">An `Async` procedure returns to the caller when either the first awaited object that’s not yet complete is encountered or the end of the `Async` procedure is reached, whichever occurs first.</span></span>

<span data-ttu-id="0c716-206">Můžete také označit [příkaz funkce](function-statement.md) pomocí modifikátoru `Async`.</span><span class="sxs-lookup"><span data-stu-id="0c716-206">You can also mark a [Function Statement](function-statement.md) with the `Async` modifier.</span></span> <span data-ttu-id="0c716-207">`Async` funkce může mít návratový typ <xref:System.Threading.Tasks.Task%601> nebo <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="0c716-207">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="0c716-208">Příklad dále v tomto tématu ukazuje funkci `Async`, která má návratový typ <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="0c716-208">An example later in this topic shows an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span>

<span data-ttu-id="0c716-209">procedury `Async` `Sub` jsou primárně používány pro obslužné rutiny událostí, kde nelze vrátit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0c716-209">`Async` `Sub` procedures are primarily used for event handlers, where a value can't be returned.</span></span> <span data-ttu-id="0c716-210">Procedura `Async` `Sub` nemůže být očekávána a volající procedury `Async` `Sub` nemůže zachytit výjimky, které vyvolá procedura `Sub`.</span><span class="sxs-lookup"><span data-stu-id="0c716-210">An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that the `Sub` procedure throws.</span></span>

<span data-ttu-id="0c716-211">Procedura `Async` nemůže deklarovat žádné parametry [ByRef](../modifiers/byref.md) .</span><span class="sxs-lookup"><span data-stu-id="0c716-211">An `Async` procedure can't declare any [ByRef](../modifiers/byref.md) parameters.</span></span>

<span data-ttu-id="0c716-212">Další informace o `Async` postupy naleznete v tématu [asynchronní programování s modifikátorem Async a await](../../../visual-basic/programming-guide/concepts/async/index.md), [řízení toku v asynchronních programech](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)a [Asynchronní návratové typy](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="0c716-212">For more information about `Async` procedures, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="example"></a><span data-ttu-id="0c716-213">Příklad</span><span class="sxs-lookup"><span data-stu-id="0c716-213">Example</span></span>

<span data-ttu-id="0c716-214">Následující příklad používá příkaz `Sub` k definování názvu, parametrů a kódu, který tvoří tělo `Sub`ho postupu.</span><span class="sxs-lookup"><span data-stu-id="0c716-214">The following example uses the `Sub` statement to define the name, parameters, and code that form the body of a `Sub` procedure.</span></span>

[!code-vb[VbVbalrStatements#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#58)]

## <a name="example"></a><span data-ttu-id="0c716-215">Příklad</span><span class="sxs-lookup"><span data-stu-id="0c716-215">Example</span></span>

<span data-ttu-id="0c716-216">V následujícím příkladu je `DelayAsync` `Async` `Function`, který má návratový typ <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="0c716-216">In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="0c716-217">`DelayAsync` má příkaz `Return`, který vrací celé číslo.</span><span class="sxs-lookup"><span data-stu-id="0c716-217">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="0c716-218">Proto deklarace funkce `DelayAsync` musí mít návratový typ `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="0c716-218">Therefore, the function declaration of `DelayAsync` must have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="0c716-219">Vzhledem k tomu, že návratový typ je `Task(Of Integer)`, vyhodnocení výrazu `Await` v `DoSomethingAsync` vytvoří celé číslo, jak ukazuje následující příkaz: `Dim result As Integer = Await delayTask`.</span><span class="sxs-lookup"><span data-stu-id="0c716-219">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer, as the following statement shows: `Dim result As Integer = Await delayTask`.</span></span>

<span data-ttu-id="0c716-220">Procedura `startButton_Click` je příkladem `Async Sub` postupu.</span><span class="sxs-lookup"><span data-stu-id="0c716-220">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="0c716-221">Vzhledem k tomu, že `DoSomethingAsync` je `Async` funkce, musí být úkol pro volání `DoSomethingAsync` očekáván, jak ukazuje následující příkaz: `Await DoSomethingAsync()`.</span><span class="sxs-lookup"><span data-stu-id="0c716-221">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="0c716-222">Procedura `startButton_Click` `Sub` musí být definována s modifikátorem `Async`, protože obsahuje výraz `Await`.</span><span class="sxs-lookup"><span data-stu-id="0c716-222">The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="0c716-223">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0c716-223">See also</span></span>

- [<span data-ttu-id="0c716-224">Příkaz Implements</span><span class="sxs-lookup"><span data-stu-id="0c716-224">Implements Statement</span></span>](implements-statement.md)
- [<span data-ttu-id="0c716-225">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="0c716-225">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="0c716-226">Seznam parametrů</span><span class="sxs-lookup"><span data-stu-id="0c716-226">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="0c716-227">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="0c716-227">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="0c716-228">Příkaz Call</span><span class="sxs-lookup"><span data-stu-id="0c716-228">Call Statement</span></span>](call-statement.md)
- [<span data-ttu-id="0c716-229">Tohoto</span><span class="sxs-lookup"><span data-stu-id="0c716-229">Of</span></span>](of-clause.md)
- [<span data-ttu-id="0c716-230">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="0c716-230">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [<span data-ttu-id="0c716-231">Postupy: Použití obecné třídy</span><span class="sxs-lookup"><span data-stu-id="0c716-231">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="0c716-232">Řešení potíží s procedurami</span><span class="sxs-lookup"><span data-stu-id="0c716-232">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [<span data-ttu-id="0c716-233">Částečné metody</span><span class="sxs-lookup"><span data-stu-id="0c716-233">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
