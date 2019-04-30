---
title: Sub – příkaz (Visual Basic)
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
ms.openlocfilehash: ab94865f4881b40b38f67eb40d2f9fa2e1982af8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783835"
---
# <a name="sub-statement-visual-basic"></a><span data-ttu-id="284b6-102">Sub – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="284b6-102">Sub Statement (Visual Basic)</span></span>

<span data-ttu-id="284b6-103">Deklaruje název, parametry a kód, které definují `Sub` postup.</span><span class="sxs-lookup"><span data-stu-id="284b6-103">Declares the name, parameters, and code that define a `Sub` procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="284b6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="284b6-104">Syntax</span></span>

```
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Sub ]
    [ statements ]
End Sub
```

## <a name="parts"></a><span data-ttu-id="284b6-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="284b6-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="284b6-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="284b6-106">Optional.</span></span> <span data-ttu-id="284b6-107">Zobrazit [seznam atributů](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="284b6-107">See [Attribute List](attribute-list.md).</span></span>

- `Partial`

  <span data-ttu-id="284b6-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="284b6-108">Optional.</span></span> <span data-ttu-id="284b6-109">Určuje definici dílčí metody.</span><span class="sxs-lookup"><span data-stu-id="284b6-109">Indicates definition of a partial method.</span></span> <span data-ttu-id="284b6-110">Zobrazit [částečné metody](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="284b6-110">See [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="284b6-111">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="284b6-111">Optional.</span></span> <span data-ttu-id="284b6-112">Může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="284b6-112">Can be one of the following:</span></span>

  - [<span data-ttu-id="284b6-113">Public</span><span class="sxs-lookup"><span data-stu-id="284b6-113">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="284b6-114">Protected</span><span class="sxs-lookup"><span data-stu-id="284b6-114">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="284b6-115">Friend</span><span class="sxs-lookup"><span data-stu-id="284b6-115">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="284b6-116">Private</span><span class="sxs-lookup"><span data-stu-id="284b6-116">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="284b6-117">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="284b6-117">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)

  - [<span data-ttu-id="284b6-118">Private Protected</span><span class="sxs-lookup"><span data-stu-id="284b6-118">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)

  <span data-ttu-id="284b6-119">Zobrazit [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="284b6-119">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `proceduremodifiers`

  <span data-ttu-id="284b6-120">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="284b6-120">Optional.</span></span> <span data-ttu-id="284b6-121">Může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="284b6-121">Can be one of the following:</span></span>

  - [<span data-ttu-id="284b6-122">Overloads</span><span class="sxs-lookup"><span data-stu-id="284b6-122">Overloads</span></span>](../modifiers/overloads.md)

  - [<span data-ttu-id="284b6-123">Overrides</span><span class="sxs-lookup"><span data-stu-id="284b6-123">Overrides</span></span>](../modifiers/overrides.md)

  - [<span data-ttu-id="284b6-124">Overridable</span><span class="sxs-lookup"><span data-stu-id="284b6-124">Overridable</span></span>](../modifiers/overridable.md)

  - [<span data-ttu-id="284b6-125">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="284b6-125">NotOverridable</span></span>](../modifiers/notoverridable.md)

  - [<span data-ttu-id="284b6-126">MustOverride</span><span class="sxs-lookup"><span data-stu-id="284b6-126">MustOverride</span></span>](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="284b6-127">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="284b6-127">Optional.</span></span> <span data-ttu-id="284b6-128">Zobrazit [sdílené](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="284b6-128">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="284b6-129">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="284b6-129">Optional.</span></span> <span data-ttu-id="284b6-130">Zobrazit [stíny](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="284b6-130">See [Shadows](../modifiers/shadows.md).</span></span>

- `Async`

  <span data-ttu-id="284b6-131">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="284b6-131">Optional.</span></span> <span data-ttu-id="284b6-132">Zobrazit [asynchronní](../modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="284b6-132">See [Async](../modifiers/async.md).</span></span>

- `name`

  <span data-ttu-id="284b6-133">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="284b6-133">Required.</span></span> <span data-ttu-id="284b6-134">Název procedury.</span><span class="sxs-lookup"><span data-stu-id="284b6-134">Name of the procedure.</span></span> <span data-ttu-id="284b6-135">Zobrazit [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="284b6-135">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span> <span data-ttu-id="284b6-136">Chcete-li vytvořit proceduru konstruktor pro třídu, nastavte název `Sub` postup `New` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="284b6-136">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="284b6-137">Další informace najdete v tématu [doba života objektu: Způsob vytváření a zničení objektů](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="284b6-137">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

- `typeparamlist`

  <span data-ttu-id="284b6-138">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="284b6-138">Optional.</span></span> <span data-ttu-id="284b6-139">Seznam parametrů typu pro obecný postup.</span><span class="sxs-lookup"><span data-stu-id="284b6-139">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="284b6-140">Zobrazit [seznamu](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="284b6-140">See [Type List](type-list.md).</span></span>

- `parameterlist`

  <span data-ttu-id="284b6-141">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="284b6-141">Optional.</span></span> <span data-ttu-id="284b6-142">Seznam místní názvy proměnných představující parametry tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="284b6-142">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="284b6-143">Zobrazit [seznam parametrů](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="284b6-143">See [Parameter List](parameter-list.md).</span></span>

- `Implements`

  <span data-ttu-id="284b6-144">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="284b6-144">Optional.</span></span> <span data-ttu-id="284b6-145">Označuje, že tento postup implementuje jednu nebo více `Sub` postupy, každý z nich definované v rozhraní implementované obsahující třídu nebo strukturu, tento postup.</span><span class="sxs-lookup"><span data-stu-id="284b6-145">Indicates that this procedure implements one or more `Sub` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="284b6-146">Zobrazit [implementuje příkaz](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="284b6-146">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="284b6-147">Požadováno pokud `Implements` pochází.</span><span class="sxs-lookup"><span data-stu-id="284b6-147">Required if `Implements` is supplied.</span></span> <span data-ttu-id="284b6-148">Seznam `Sub` postupy se implementuje.</span><span class="sxs-lookup"><span data-stu-id="284b6-148">List of `Sub` procedures being implemented.</span></span>

  `implementedprocedure [ , implementedprocedure ... ]`

  <span data-ttu-id="284b6-149">Každý `implementedprocedure` má následující syntaxi a části:</span><span class="sxs-lookup"><span data-stu-id="284b6-149">Each `implementedprocedure` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="284b6-150">Část</span><span class="sxs-lookup"><span data-stu-id="284b6-150">Part</span></span>|<span data-ttu-id="284b6-151">Popis</span><span class="sxs-lookup"><span data-stu-id="284b6-151">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="284b6-152">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="284b6-152">Required.</span></span> <span data-ttu-id="284b6-153">Název rozhraní implementovaných tímto postupem obsahující třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="284b6-153">Name of an interface implemented by this procedure's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="284b6-154">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="284b6-154">Required.</span></span> <span data-ttu-id="284b6-155">Název, podle kterého postupu je definován v `interface`.</span><span class="sxs-lookup"><span data-stu-id="284b6-155">Name by which the procedure is defined in `interface`.</span></span>|

- `Handles`

  <span data-ttu-id="284b6-156">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="284b6-156">Optional.</span></span> <span data-ttu-id="284b6-157">Označuje, že tento postup může zpracovat jeden nebo více konkrétních událostí.</span><span class="sxs-lookup"><span data-stu-id="284b6-157">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="284b6-158">Zobrazit [zpracovává](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="284b6-158">See [Handles](handles-clause.md).</span></span>

- `eventlist`

  <span data-ttu-id="284b6-159">Požadováno pokud `Handles` pochází.</span><span class="sxs-lookup"><span data-stu-id="284b6-159">Required if `Handles` is supplied.</span></span> <span data-ttu-id="284b6-160">Seznam událostí, který zpracovává tento postup.</span><span class="sxs-lookup"><span data-stu-id="284b6-160">List of events this procedure handles.</span></span>

  `eventspecifier [ , eventspecifier ... ]`

  <span data-ttu-id="284b6-161">Každý `eventspecifier` má následující syntaxi a části:</span><span class="sxs-lookup"><span data-stu-id="284b6-161">Each `eventspecifier` has the following syntax and parts:</span></span>

  `eventvariable.event`

  |<span data-ttu-id="284b6-162">Část</span><span class="sxs-lookup"><span data-stu-id="284b6-162">Part</span></span>|<span data-ttu-id="284b6-163">Popis</span><span class="sxs-lookup"><span data-stu-id="284b6-163">Description</span></span>|
  |---|---|
  |`eventvariable`|<span data-ttu-id="284b6-164">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="284b6-164">Required.</span></span> <span data-ttu-id="284b6-165">Objektová proměnná deklarovaná s datovým typem třídy nebo struktury, která vyvolává událost.</span><span class="sxs-lookup"><span data-stu-id="284b6-165">Object variable declared with the data type of the class or structure that raises the event.</span></span>|
  |`event`|<span data-ttu-id="284b6-166">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="284b6-166">Required.</span></span> <span data-ttu-id="284b6-167">Název události, které zpracovává tento postup.</span><span class="sxs-lookup"><span data-stu-id="284b6-167">Name of the event this procedure handles.</span></span>|

- `statements`

  <span data-ttu-id="284b6-168">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="284b6-168">Optional.</span></span> <span data-ttu-id="284b6-169">Blok příkazů ke spuštění v rámci tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="284b6-169">Block of statements to run within this procedure.</span></span>

- `End Sub`

  <span data-ttu-id="284b6-170">Ukončí definici tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="284b6-170">Terminates the definition of this procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="284b6-171">Poznámky</span><span class="sxs-lookup"><span data-stu-id="284b6-171">Remarks</span></span>

<span data-ttu-id="284b6-172">Všechny spustitelný kód musí být uvnitř procedury.</span><span class="sxs-lookup"><span data-stu-id="284b6-172">All executable code must be inside a procedure.</span></span> <span data-ttu-id="284b6-173">Použití `Sub` procedury při nechcete vracet hodnotu volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="284b6-173">Use a `Sub` procedure when you don't want to return a value to the calling code.</span></span> <span data-ttu-id="284b6-174">Použití `Function` postup, pokud chcete vracet hodnotu.</span><span class="sxs-lookup"><span data-stu-id="284b6-174">Use a `Function` procedure when you want to return a value.</span></span>

## <a name="defining-a-sub-procedure"></a><span data-ttu-id="284b6-175">Definuje proceduru Sub</span><span class="sxs-lookup"><span data-stu-id="284b6-175">Defining a Sub Procedure</span></span>

<span data-ttu-id="284b6-176">Můžete definovat `Sub` postup pouze na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="284b6-176">You can define a `Sub` procedure only at the module level.</span></span> <span data-ttu-id="284b6-177">Kontext deklarace pro proceduru sub, proto musí třída, struktura, modul nebo rozhraní a nemůže být zdrojový soubor, obor názvů, procedura nebo blok.</span><span class="sxs-lookup"><span data-stu-id="284b6-177">The declaration context for a sub procedure must, therefore, be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="284b6-178">Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="284b6-178">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="284b6-179">`Sub` postupy výchozí veřejný přístup.</span><span class="sxs-lookup"><span data-stu-id="284b6-179">`Sub` procedures default to public access.</span></span> <span data-ttu-id="284b6-180">Můžete nastavit jejich úrovně přístupu pomocí přístupu modifikátory přístupu.</span><span class="sxs-lookup"><span data-stu-id="284b6-180">You can adjust their access levels by using the access modifiers.</span></span>

<span data-ttu-id="284b6-181">Pokud postup používá `Implements` – klíčové slovo, obsahuje třídu nebo strukturu, musíte mít `Implements` příkaz, který bezprostředně následuje po jeho `Class` nebo `Structure` příkazu.</span><span class="sxs-lookup"><span data-stu-id="284b6-181">If the procedure uses the `Implements` keyword, the containing class or structure must have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="284b6-182">`Implements` Příkazu musí obsahovat každé rozhraní, které je zadáno v `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="284b6-182">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="284b6-183">Ale název, pomocí kterého rozhraní definuje `Sub` (v `definedname`) nemusí odpovídat názvu tohoto postupu (v `name`).</span><span class="sxs-lookup"><span data-stu-id="284b6-183">However, the name by which an interface defines the `Sub` (in `definedname`) doesn't have to match the name of this procedure (in `name`).</span></span>

## <a name="returning-from-a-sub-procedure"></a><span data-ttu-id="284b6-184">Návrat z proceduru Sub</span><span class="sxs-lookup"><span data-stu-id="284b6-184">Returning from a Sub Procedure</span></span>

<span data-ttu-id="284b6-185">Když `Sub` postup vrátí volajícímu kódu, provádění pokračuje s příkazu následujícímu po prohlášení, která ji zavolala.</span><span class="sxs-lookup"><span data-stu-id="284b6-185">When a `Sub` procedure returns to the calling code, execution continues with the statement after the statement that called it.</span></span>

<span data-ttu-id="284b6-186">Následující příklad ukazuje návrat z `Sub` postup.</span><span class="sxs-lookup"><span data-stu-id="284b6-186">The following example shows a return from a `Sub` procedure.</span></span>

```vb
Sub mySub(ByVal q As String)
    Return
End Sub
```

<span data-ttu-id="284b6-187">`Exit Sub` a `Return` příkazy způsobit okamžité ukončení `Sub` postup.</span><span class="sxs-lookup"><span data-stu-id="284b6-187">The `Exit Sub` and `Return` statements cause an immediate exit from a `Sub` procedure.</span></span> <span data-ttu-id="284b6-188">Libovolný počet `Exit Sub` a `Return` příkazů může vyskytovat kdekoli v postupu, a je možné kombinovat `Exit Sub` a `Return` příkazy.</span><span class="sxs-lookup"><span data-stu-id="284b6-188">Any number of `Exit Sub` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Sub` and `Return` statements.</span></span>

## <a name="calling-a-sub-procedure"></a><span data-ttu-id="284b6-189">Volání procedury Sub</span><span class="sxs-lookup"><span data-stu-id="284b6-189">Calling a Sub Procedure</span></span>

<span data-ttu-id="284b6-190">Volání `Sub` postup pomocí název procedury v příkazu a budete postupovat tímto názvem s jeho seznamem argumentů v závorkách.</span><span class="sxs-lookup"><span data-stu-id="284b6-190">You call a `Sub` procedure by using the procedure name in a statement and then following that name with its argument list in parentheses.</span></span> <span data-ttu-id="284b6-191">Závorky lze vynechat pouze tehdy, pokud nezadáte žádné argumenty.</span><span class="sxs-lookup"><span data-stu-id="284b6-191">You can omit the parentheses only if you don't supply any arguments.</span></span> <span data-ttu-id="284b6-192">Váš kód je však čitelnější, pokud vždy závorek.</span><span class="sxs-lookup"><span data-stu-id="284b6-192">However, your code is more readable if you always include the parentheses.</span></span>

<span data-ttu-id="284b6-193">A `Sub` postup a `Function` procedury mohou mít parametry a provádět řadu příkazů.</span><span class="sxs-lookup"><span data-stu-id="284b6-193">A `Sub` procedure and a `Function` procedure  can have parameters and perform a series of statements.</span></span> <span data-ttu-id="284b6-194">Ale `Function` postup vrátí hodnotu a s `Sub` není procedura.</span><span class="sxs-lookup"><span data-stu-id="284b6-194">However, a `Function` procedure returns a value, and a `Sub` procedure doesn't.</span></span> <span data-ttu-id="284b6-195">Proto je nelze použít `Sub` postup ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="284b6-195">Therefore, you can't use a `Sub` procedure in an expression.</span></span>

<span data-ttu-id="284b6-196">Můžete použít `Call` – klíčové slovo při volání `Sub` postup, ale toto klíčové slovo se nedoporučuje pro většinu použití.</span><span class="sxs-lookup"><span data-stu-id="284b6-196">You can use the `Call` keyword when you call a `Sub` procedure, but that keyword isn't recommended for most uses.</span></span> <span data-ttu-id="284b6-197">Další informace najdete v tématu [zavolat příkaz](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="284b6-197">For more information, see [Call Statement](call-statement.md).</span></span>

<span data-ttu-id="284b6-198">Visual Basic někdy znovu uspořádá aritmetických výrazů ke zvýšení účinnosti interní.</span><span class="sxs-lookup"><span data-stu-id="284b6-198">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="284b6-199">Z tohoto důvodu Pokud váš seznam argumentů obsahuje výrazy, které vyžadují další postupy budete by neměl předpokládat, že tyto výrazy se nazývají v určitém pořadí.</span><span class="sxs-lookup"><span data-stu-id="284b6-199">For that reason, if your argument list includes expressions that call other procedures, you shouldn't assume that those expressions will be called in a particular order.</span></span>

## <a name="async-sub-procedures"></a><span data-ttu-id="284b6-200">Async Sub – procedury</span><span class="sxs-lookup"><span data-stu-id="284b6-200">Async Sub Procedures</span></span>

<span data-ttu-id="284b6-201">Při použití asynchronní funkce, se dají vyvolat asynchronní funkce bez použití explicitní zpětná volání nebo Ruční rozdělení kódu mezi více funkcí nebo výrazů lambda.</span><span class="sxs-lookup"><span data-stu-id="284b6-201">By using the Async feature, you can invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>

<span data-ttu-id="284b6-202">Pokud označíte procedura se [asynchronní](../modifiers/async.md) modifikátor, můžete použít [Await](../../../visual-basic/language-reference/operators/await-operator.md) operátor v postupu.</span><span class="sxs-lookup"><span data-stu-id="284b6-202">If you mark a procedure with the [Async](../modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the procedure.</span></span> <span data-ttu-id="284b6-203">Když ovládací prvek dosáhne `Await` výrazu v `Async` postupu ovládací prvek vrátí volajícímu a průběh v postupu je pozastaveno, dokud očekávaná úloha dokončí.</span><span class="sxs-lookup"><span data-stu-id="284b6-203">When control reaches an `Await` expression in the `Async` procedure, control returns to the caller, and progress in the procedure is suspended until the awaited task completes.</span></span> <span data-ttu-id="284b6-204">Po dokončení úlohy se provádění může pokračovat v postupu.</span><span class="sxs-lookup"><span data-stu-id="284b6-204">When the task is complete, execution can resume in the procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="284b6-205">`Async` Postup vrátí volajícímu vyskytne buď první očekávaný objekt, který ještě není dokončeno nebo konec `Async` postup je dosaženo, podle toho, co nastane dříve.</span><span class="sxs-lookup"><span data-stu-id="284b6-205">An `Async` procedure returns to the caller when either the first awaited object that’s not yet complete is encountered or the end of the `Async` procedure is reached, whichever occurs first.</span></span>

<span data-ttu-id="284b6-206">Můžete také označit [Function – příkaz](function-statement.md) s `Async` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="284b6-206">You can also mark a [Function Statement](function-statement.md) with the `Async` modifier.</span></span> <span data-ttu-id="284b6-207">`Async` Funkce může mít návratový typ <xref:System.Threading.Tasks.Task%601> nebo <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="284b6-207">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="284b6-208">Příklad dále v tomto tématu si ukážeme `Async` funkci, která má návratový typ <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="284b6-208">An example later in this topic shows an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span>

<span data-ttu-id="284b6-209">`Async` `Sub` postupy jsou primárně určené pro obslužné rutiny událostí, ve kterém nejde vrátit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="284b6-209">`Async` `Sub` procedures are primarily used for event handlers, where a value can't be returned.</span></span> <span data-ttu-id="284b6-210">`Async` `Sub` Nemůže být očekávána proceduru a volající `Async` `Sub` postup zaznamenat tak výjimky, která `Sub` postup vyvolá.</span><span class="sxs-lookup"><span data-stu-id="284b6-210">An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that the `Sub` procedure throws.</span></span>

<span data-ttu-id="284b6-211">`Async` Procedura nemůže deklarovat všechny [ByRef](../modifiers/byref.md) parametry.</span><span class="sxs-lookup"><span data-stu-id="284b6-211">An `Async` procedure can't declare any [ByRef](../modifiers/byref.md) parameters.</span></span>

<span data-ttu-id="284b6-212">Další informace o `Async` postupy, najdete v článku [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [tok řízení v asynchronních programech](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), a [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="284b6-212">For more information about `Async` procedures, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="example"></a><span data-ttu-id="284b6-213">Příklad</span><span class="sxs-lookup"><span data-stu-id="284b6-213">Example</span></span>

<span data-ttu-id="284b6-214">V následujícím příkladu `Sub` příkazu zadat název, parametry a kód, který tvoří text `Sub` postup.</span><span class="sxs-lookup"><span data-stu-id="284b6-214">The following example uses the `Sub` statement to define the name, parameters, and code that form the body of a `Sub` procedure.</span></span>

[!code-vb[VbVbalrStatements#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#58)]

## <a name="example"></a><span data-ttu-id="284b6-215">Příklad</span><span class="sxs-lookup"><span data-stu-id="284b6-215">Example</span></span>

<span data-ttu-id="284b6-216">V následujícím příkladu `DelayAsync` je `Async` `Function` , která má návratový typ <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="284b6-216">In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="284b6-217">`DelayAsync` má `Return` příkaz, který vrátí celé číslo.</span><span class="sxs-lookup"><span data-stu-id="284b6-217">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="284b6-218">Proto se funkce deklarace `DelayAsync` musí mít typ vrácené hodnoty `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="284b6-218">Therefore, the function declaration of `DelayAsync` must have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="284b6-219">Vzhledem k tomu, že je návratový typ `Task(Of Integer)`, vyhodnocení `Await` výrazu v `DoSomethingAsync` vytváří celé číslo, jak ukazuje následující příkaz: `Dim result As Integer = Await delayTask`.</span><span class="sxs-lookup"><span data-stu-id="284b6-219">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer, as the following statement shows: `Dim result As Integer = Await delayTask`.</span></span>

<span data-ttu-id="284b6-220">`startButton_Click` Postup je příkladem `Async Sub` postup.</span><span class="sxs-lookup"><span data-stu-id="284b6-220">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="284b6-221">Protože `DoSomethingAsync` je `Async` funkce, úkol pro volání `DoSomethingAsync` musí ní použít operátor await, jak ukazuje následující příkaz: `Await DoSomethingAsync()`.</span><span class="sxs-lookup"><span data-stu-id="284b6-221">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="284b6-222">`startButton_Click` `Sub` Postupu musí být definované s `Async` modifikátor vzhledem k tomu, že má `Await` výrazu.</span><span class="sxs-lookup"><span data-stu-id="284b6-222">The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="284b6-223">Viz také:</span><span class="sxs-lookup"><span data-stu-id="284b6-223">See also</span></span>

- [<span data-ttu-id="284b6-224">Příkaz Implements</span><span class="sxs-lookup"><span data-stu-id="284b6-224">Implements Statement</span></span>](implements-statement.md)
- [<span data-ttu-id="284b6-225">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="284b6-225">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="284b6-226">Seznam parametrů</span><span class="sxs-lookup"><span data-stu-id="284b6-226">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="284b6-227">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="284b6-227">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="284b6-228">Příkaz Call</span><span class="sxs-lookup"><span data-stu-id="284b6-228">Call Statement</span></span>](call-statement.md)
- [<span data-ttu-id="284b6-229">z</span><span class="sxs-lookup"><span data-stu-id="284b6-229">Of</span></span>](of-clause.md)
- [<span data-ttu-id="284b6-230">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="284b6-230">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [<span data-ttu-id="284b6-231">Postupy: Použití obecné třídy</span><span class="sxs-lookup"><span data-stu-id="284b6-231">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="284b6-232">Řešení potíží s procedurami</span><span class="sxs-lookup"><span data-stu-id="284b6-232">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [<span data-ttu-id="284b6-233">Částečné metody</span><span class="sxs-lookup"><span data-stu-id="284b6-233">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
