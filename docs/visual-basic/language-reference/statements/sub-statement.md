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
ms.openlocfilehash: 08be38cdbec82914b567ab5b86eed71181efcf57
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34234173"
---
# <a name="sub-statement-visual-basic"></a><span data-ttu-id="213e3-102">Sub – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="213e3-102">Sub Statement (Visual Basic)</span></span>
<span data-ttu-id="213e3-103">Deklaruje název, parametry a kód, který definovat `Sub` postupu.</span><span class="sxs-lookup"><span data-stu-id="213e3-103">Declares the name, parameters, and code that define a `Sub` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="213e3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="213e3-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]  
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Sub ]  
    [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="213e3-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="213e3-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="213e3-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="213e3-106">Optional.</span></span> <span data-ttu-id="213e3-107">V tématu [seznam atributů](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="213e3-107">See [Attribute List](attribute-list.md).</span></span>  
  
-   `Partial`  
  
     <span data-ttu-id="213e3-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="213e3-108">Optional.</span></span> <span data-ttu-id="213e3-109">Určuje definici částečné metody.</span><span class="sxs-lookup"><span data-stu-id="213e3-109">Indicates definition of a partial method.</span></span> <span data-ttu-id="213e3-110">V tématu [částečné metody](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="213e3-110">See [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="213e3-111">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="213e3-111">Optional.</span></span> <span data-ttu-id="213e3-112">Může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="213e3-112">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="213e3-113">Public</span><span class="sxs-lookup"><span data-stu-id="213e3-113">Public</span></span>](../modifiers/public.md)  
  
    -   [<span data-ttu-id="213e3-114">Protected</span><span class="sxs-lookup"><span data-stu-id="213e3-114">Protected</span></span>](../modifiers/protected.md)  
  
    -   [<span data-ttu-id="213e3-115">Friend</span><span class="sxs-lookup"><span data-stu-id="213e3-115">Friend</span></span>](../modifiers/friend.md)  
  
    -   [<span data-ttu-id="213e3-116">Private</span><span class="sxs-lookup"><span data-stu-id="213e3-116">Private</span></span>](../modifiers/private.md)  
  
    - [<span data-ttu-id="213e3-117">Chráněné Friend</span><span class="sxs-lookup"><span data-stu-id="213e3-117">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)

    - [<span data-ttu-id="213e3-118">Privátní chráněný</span><span class="sxs-lookup"><span data-stu-id="213e3-118">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)
  
     <span data-ttu-id="213e3-119">V tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="213e3-119">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `proceduremodifiers`  
  
     <span data-ttu-id="213e3-120">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="213e3-120">Optional.</span></span> <span data-ttu-id="213e3-121">Může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="213e3-121">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="213e3-122">Overloads</span><span class="sxs-lookup"><span data-stu-id="213e3-122">Overloads</span></span>](../modifiers/overloads.md)  
  
    -   [<span data-ttu-id="213e3-123">Overrides</span><span class="sxs-lookup"><span data-stu-id="213e3-123">Overrides</span></span>](../modifiers/overrides.md)  
  
    -   [<span data-ttu-id="213e3-124">Overridable</span><span class="sxs-lookup"><span data-stu-id="213e3-124">Overridable</span></span>](../modifiers/overridable.md)  
  
    -   [<span data-ttu-id="213e3-125">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="213e3-125">NotOverridable</span></span>](../modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="213e3-126">MustOverride</span><span class="sxs-lookup"><span data-stu-id="213e3-126">MustOverride</span></span>](../modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="213e3-127">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="213e3-127">Optional.</span></span> <span data-ttu-id="213e3-128">V tématu [sdílené](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="213e3-128">See [Shared](../modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="213e3-129">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="213e3-129">Optional.</span></span> <span data-ttu-id="213e3-130">V tématu [stínů](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="213e3-130">See [Shadows](../modifiers/shadows.md).</span></span>  
  
-   `Async`  
  
     <span data-ttu-id="213e3-131">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="213e3-131">Optional.</span></span> <span data-ttu-id="213e3-132">V tématu [asynchronní](../modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="213e3-132">See [Async](../modifiers/async.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="213e3-133">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="213e3-133">Required.</span></span> <span data-ttu-id="213e3-134">Název procedury.</span><span class="sxs-lookup"><span data-stu-id="213e3-134">Name of the procedure.</span></span> <span data-ttu-id="213e3-135">V tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="213e3-135">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span> <span data-ttu-id="213e3-136">Chcete-li vytvořit proceduru konstruktor pro třídu, nastavte název `Sub` postup `New` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="213e3-136">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="213e3-137">Další informace najdete v tématu [doba života objektu: jak jsou objekty vytvořen a Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="213e3-137">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
-   `typeparamlist`  
  
     <span data-ttu-id="213e3-138">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="213e3-138">Optional.</span></span> <span data-ttu-id="213e3-139">Seznam parametrů typu pro obecný postup.</span><span class="sxs-lookup"><span data-stu-id="213e3-139">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="213e3-140">V tématu [zadejte seznam](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="213e3-140">See [Type List](type-list.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="213e3-141">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="213e3-141">Optional.</span></span> <span data-ttu-id="213e3-142">Seznam místní názvy proměnných představující parametry tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="213e3-142">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="213e3-143">V tématu [seznam parametrů](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="213e3-143">See [Parameter List](parameter-list.md).</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="213e3-144">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="213e3-144">Optional.</span></span> <span data-ttu-id="213e3-145">Označuje, že tento postup implementuje jeden nebo více `Sub` postupy, každé z nich definované v rozhraní implementované obsahující třídu nebo strukturu tento postup.</span><span class="sxs-lookup"><span data-stu-id="213e3-145">Indicates that this procedure implements one or more `Sub` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="213e3-146">V tématu [implementuje příkaz](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="213e3-146">See [Implements Statement](implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="213e3-147">Požadováno pokud `Implements` pochází.</span><span class="sxs-lookup"><span data-stu-id="213e3-147">Required if `Implements` is supplied.</span></span> <span data-ttu-id="213e3-148">Seznam `Sub` postupy se implementuje.</span><span class="sxs-lookup"><span data-stu-id="213e3-148">List of `Sub` procedures being implemented.</span></span>  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     <span data-ttu-id="213e3-149">Každý `implementedprocedure` má následující syntaxe a částí:</span><span class="sxs-lookup"><span data-stu-id="213e3-149">Each `implementedprocedure` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="213e3-150">Část</span><span class="sxs-lookup"><span data-stu-id="213e3-150">Part</span></span>|<span data-ttu-id="213e3-151">Popis</span><span class="sxs-lookup"><span data-stu-id="213e3-151">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="213e3-152">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="213e3-152">Required.</span></span> <span data-ttu-id="213e3-153">Název rozhraní implementované tento postup obsahující třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="213e3-153">Name of an interface implemented by this procedure's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="213e3-154">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="213e3-154">Required.</span></span> <span data-ttu-id="213e3-155">Název, podle kterého postupu je definována v `interface`.</span><span class="sxs-lookup"><span data-stu-id="213e3-155">Name by which the procedure is defined in `interface`.</span></span>|  
  
-   `Handles`  
  
     <span data-ttu-id="213e3-156">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="213e3-156">Optional.</span></span> <span data-ttu-id="213e3-157">Označuje, že tento postup může zpracovat jeden nebo více konkrétní události.</span><span class="sxs-lookup"><span data-stu-id="213e3-157">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="213e3-158">V tématu [zpracovává](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="213e3-158">See [Handles](handles-clause.md).</span></span>  
  
-   `eventlist`  
  
     <span data-ttu-id="213e3-159">Požadováno pokud `Handles` pochází.</span><span class="sxs-lookup"><span data-stu-id="213e3-159">Required if `Handles` is supplied.</span></span> <span data-ttu-id="213e3-160">Seznam událostí, který zpracovává tento postup.</span><span class="sxs-lookup"><span data-stu-id="213e3-160">List of events this procedure handles.</span></span>  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     <span data-ttu-id="213e3-161">Každý `eventspecifier` má následující syntaxe a částí:</span><span class="sxs-lookup"><span data-stu-id="213e3-161">Each `eventspecifier` has the following syntax and parts:</span></span>  
  
     `eventvariable.event`  
  
    |<span data-ttu-id="213e3-162">Část</span><span class="sxs-lookup"><span data-stu-id="213e3-162">Part</span></span>|<span data-ttu-id="213e3-163">Popis</span><span class="sxs-lookup"><span data-stu-id="213e3-163">Description</span></span>|  
    |---|---|  
    |`eventvariable`|<span data-ttu-id="213e3-164">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="213e3-164">Required.</span></span> <span data-ttu-id="213e3-165">Objektová proměnná deklarovat s datový typ třídu nebo strukturu, která vyvolává událost.</span><span class="sxs-lookup"><span data-stu-id="213e3-165">Object variable declared with the data type of the class or structure that raises the event.</span></span>|  
    |`event`|<span data-ttu-id="213e3-166">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="213e3-166">Required.</span></span> <span data-ttu-id="213e3-167">Název události, který zpracovává tento postup.</span><span class="sxs-lookup"><span data-stu-id="213e3-167">Name of the event this procedure handles.</span></span>|  
  
-   `statements`  
  
     <span data-ttu-id="213e3-168">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="213e3-168">Optional.</span></span> <span data-ttu-id="213e3-169">Blok příkazů ke spuštění v rámci tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="213e3-169">Block of statements to run within this procedure.</span></span>  
  
-   `End Sub`  
  
     <span data-ttu-id="213e3-170">Ukončí definici tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="213e3-170">Terminates the definition of this procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="213e3-171">Poznámky</span><span class="sxs-lookup"><span data-stu-id="213e3-171">Remarks</span></span>  
 <span data-ttu-id="213e3-172">Všechny spustitelný kód musí být uvnitř procedury.</span><span class="sxs-lookup"><span data-stu-id="213e3-172">All executable code must be inside a procedure.</span></span> <span data-ttu-id="213e3-173">Použití `Sub` procedury při nechcete vrátit hodnotu volání kódu.</span><span class="sxs-lookup"><span data-stu-id="213e3-173">Use a `Sub` procedure when you don't want to return a value to the calling code.</span></span> <span data-ttu-id="213e3-174">Použití `Function` postup, pokud chcete vrátit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="213e3-174">Use a `Function` procedure when you want to return a value.</span></span>  
  
## <a name="defining-a-sub-procedure"></a><span data-ttu-id="213e3-175">Definování Sub – procedury</span><span class="sxs-lookup"><span data-stu-id="213e3-175">Defining a Sub Procedure</span></span>  
 <span data-ttu-id="213e3-176">Můžete definovat `Sub` postup jenom na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="213e3-176">You can define a `Sub` procedure only at the module level.</span></span> <span data-ttu-id="213e3-177">Kontext deklarace pro proceduru sub proto musí být třídy, struktury, modul nebo rozhraní a nemůže být zdrojový soubor, obor názvů, procedury nebo blok.</span><span class="sxs-lookup"><span data-stu-id="213e3-177">The declaration context for a sub procedure must, therefore, be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="213e3-178">Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="213e3-178">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="213e3-179">`Sub` Výchozí nastavení postupy veřejný přístup.</span><span class="sxs-lookup"><span data-stu-id="213e3-179">`Sub` procedures default to public access.</span></span> <span data-ttu-id="213e3-180">Jejich úrovně přístupu můžete upravit pomocí modifikátory přístupu.</span><span class="sxs-lookup"><span data-stu-id="213e3-180">You can adjust their access levels by using the access modifiers.</span></span>  
  
 <span data-ttu-id="213e3-181">Pokud postup používá `Implements` – klíčové slovo, obsahující třídu nebo strukturu, musíte mít `Implements` příkaz, který následuje jeho `Class` nebo `Structure` příkaz.</span><span class="sxs-lookup"><span data-stu-id="213e3-181">If the procedure uses the `Implements` keyword, the containing class or structure must have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="213e3-182">`Implements` Příkaz musí zahrnovat každé rozhraní, který je uveden v `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="213e3-182">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="213e3-183">Ale název, podle kterého rozhraní definuje `Sub` (v `definedname`) nemusí odpovídat názvu tohoto postupu (v `name`).</span><span class="sxs-lookup"><span data-stu-id="213e3-183">However, the name by which an interface defines the `Sub` (in `definedname`) doesn't have to match the name of this procedure (in `name`).</span></span>  
  
## <a name="returning-from-a-sub-procedure"></a><span data-ttu-id="213e3-184">Vrácení z Sub – procedury</span><span class="sxs-lookup"><span data-stu-id="213e3-184">Returning from a Sub Procedure</span></span>  
 <span data-ttu-id="213e3-185">Když `Sub` postup vrátí kód volání, pokračuje provádění příkaz po příkazu, která je volána.</span><span class="sxs-lookup"><span data-stu-id="213e3-185">When a `Sub` procedure returns to the calling code, execution continues with the statement after the statement that called it.</span></span>  
  
 <span data-ttu-id="213e3-186">Následující příklad ukazuje vrátit z `Sub` postupu.</span><span class="sxs-lookup"><span data-stu-id="213e3-186">The following example shows a return from a `Sub` procedure.</span></span>  
  
```vb  
Sub mySub(ByVal q As String)  
    Return  
End Sub   
```  
  
 <span data-ttu-id="213e3-187">`Exit Sub` a `Return` příkazy způsobit okamžitou výstupu z `Sub` postupu.</span><span class="sxs-lookup"><span data-stu-id="213e3-187">The `Exit Sub` and `Return` statements cause an immediate exit from a `Sub` procedure.</span></span> <span data-ttu-id="213e3-188">Libovolný počet `Exit Sub` a `Return` příkazy může vyskytovat kdekoli v postupu, a je možné kombinovat `Exit Sub` a `Return` příkazy.</span><span class="sxs-lookup"><span data-stu-id="213e3-188">Any number of `Exit Sub` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Sub` and `Return` statements.</span></span>  
  
## <a name="calling-a-sub-procedure"></a><span data-ttu-id="213e3-189">Volání metody Sub – procedury</span><span class="sxs-lookup"><span data-stu-id="213e3-189">Calling a Sub Procedure</span></span>  
 <span data-ttu-id="213e3-190">Volání `Sub` postup s využitím název procedury v příkazu a potom následující tento název s jeho seznam argumentů v závorkách.</span><span class="sxs-lookup"><span data-stu-id="213e3-190">You call a `Sub` procedure by using the procedure name in a statement and then following that name with its argument list in parentheses.</span></span> <span data-ttu-id="213e3-191">Závorky můžete vynechat, pouze v případě, že jste zadali žádné argumenty.</span><span class="sxs-lookup"><span data-stu-id="213e3-191">You can omit the parentheses only if you don't supply any arguments.</span></span> <span data-ttu-id="213e3-192">Váš kód je však lépe čitelný, pokud vždy zahrnovat závorkách.</span><span class="sxs-lookup"><span data-stu-id="213e3-192">However, your code is more readable if you always include the parentheses.</span></span>  
  
 <span data-ttu-id="213e3-193">A `Sub` postupu a `Function` postupu můžete mít parametry a provádět řadu příkazů.</span><span class="sxs-lookup"><span data-stu-id="213e3-193">A `Sub` procedure and a `Function` procedure  can have parameters and perform a series of statements.</span></span> <span data-ttu-id="213e3-194">Ale `Function` postup vrátí hodnotu a `Sub` postup není.</span><span class="sxs-lookup"><span data-stu-id="213e3-194">However, a `Function` procedure returns a value, and a `Sub` procedure doesn't.</span></span> <span data-ttu-id="213e3-195">Proto nelze použít `Sub` postup ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="213e3-195">Therefore, you can't use a `Sub` procedure in an expression.</span></span>  
  
 <span data-ttu-id="213e3-196">Můžete použít `Call` – klíčové slovo při volání `Sub` postup, ale že – klíčové slovo není vhodná pro většinu používá.</span><span class="sxs-lookup"><span data-stu-id="213e3-196">You can use the `Call` keyword when you call a `Sub` procedure, but that keyword isn't recommended for most uses.</span></span> <span data-ttu-id="213e3-197">Další informace najdete v tématu [volání příkazu](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="213e3-197">For more information, see [Call Statement](call-statement.md).</span></span>  
  
 <span data-ttu-id="213e3-198">Visual Basic někdy Přeuspořádá aritmetických výrazech ke zvýšení efektivity interní.</span><span class="sxs-lookup"><span data-stu-id="213e3-198">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="213e3-199">Z tohoto důvodu Pokud váš argument seznam obsahuje výrazy, které volají další postupy, budete by neměl předpokládat, že bude volán tyto výrazy v určitém pořadí.</span><span class="sxs-lookup"><span data-stu-id="213e3-199">For that reason, if your argument list includes expressions that call other procedures, you shouldn't assume that those expressions will be called in a particular order.</span></span>  
  
## <a name="async-sub-procedures"></a><span data-ttu-id="213e3-200">Asynchronní Sub – procedury</span><span class="sxs-lookup"><span data-stu-id="213e3-200">Async Sub Procedures</span></span>  
 <span data-ttu-id="213e3-201">Pomocí funkce asynchronní můžete vyvolat asynchronní funkce bez použití explicitní zpětná volání nebo Ruční rozdělení kódu napříč více funkcí nebo výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="213e3-201">By using the Async feature, you can invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>  
  
 <span data-ttu-id="213e3-202">Pokud označíte procedura se [asynchronní](../modifiers/async.md) modifikátor, můžete použít [Await](../../../visual-basic/language-reference/operators/await-operator.md) operátor v postupu.</span><span class="sxs-lookup"><span data-stu-id="213e3-202">If you mark a procedure with the [Async](../modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the procedure.</span></span> <span data-ttu-id="213e3-203">Při řízení dosáhnou `Await` výrazu v `Async` postupu řízení vrátí volajícímu a průběh v postupu je pozastaveno, dokud dokončení awaited úlohy.</span><span class="sxs-lookup"><span data-stu-id="213e3-203">When control reaches an `Await` expression in the `Async` procedure, control returns to the caller, and progress in the procedure is suspended until the awaited task completes.</span></span> <span data-ttu-id="213e3-204">Po dokončení úlohy provádění může pokračovat v postupu.</span><span class="sxs-lookup"><span data-stu-id="213e3-204">When the task is complete, execution can resume in the procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="213e3-205">`Async` Postup vrátí volajícího, když je zjištěna buď první awaited objekt, který ještě není dokončena nebo konci `Async` postup je dosaženo, cokoliv nastane dříve.</span><span class="sxs-lookup"><span data-stu-id="213e3-205">An `Async` procedure returns to the caller when either the first awaited object that’s not yet complete is encountered or the end of the `Async` procedure is reached, whichever occurs first.</span></span>  
  
 <span data-ttu-id="213e3-206">Můžete také označit [funkce příkaz](function-statement.md) s `Async` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="213e3-206">You can also mark a [Function Statement](function-statement.md) with the `Async` modifier.</span></span> <span data-ttu-id="213e3-207">`Async` Funkce může mít návratový typ <xref:System.Threading.Tasks.Task%601> nebo <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="213e3-207">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="213e3-208">Příklad později v tomto tématu je uveden `Async` funkce, která má návratový typ <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="213e3-208">An example later in this topic shows an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
 <span data-ttu-id="213e3-209">`Async` `Sub` postupy se primárně používají pro obslužné rutiny událostí, kde nejde vrátit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="213e3-209">`Async` `Sub` procedures are primarily used for event handlers, where a value can't be returned.</span></span> <span data-ttu-id="213e3-210">`Async``Sub` Procedury nelze očekáváno a volající `Async``Sub` procedury nelze zachytit výjimky, `Sub` postup vyvolává.</span><span class="sxs-lookup"><span data-stu-id="213e3-210">An `Async``Sub` procedure can't be awaited, and the caller of an `Async``Sub` procedure can't catch exceptions that the `Sub` procedure throws.</span></span>  
  
 <span data-ttu-id="213e3-211">`Async` Procedury nelze deklarovat všechny [ByRef](../modifiers/byref.md) parametry.</span><span class="sxs-lookup"><span data-stu-id="213e3-211">An `Async` procedure can't declare any [ByRef](../modifiers/byref.md) parameters.</span></span>  
  
 <span data-ttu-id="213e3-212">Další informace o `Async` postupech najdete v [asynchronní programování s Async a Await](../../../visual-basic/programming-guide/concepts/async/index.md), [řízení toku v asynchronních programech](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), a [asynchronní vrátit typy](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="213e3-212">For more information about `Async` procedures, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="213e3-213">Příklad</span><span class="sxs-lookup"><span data-stu-id="213e3-213">Example</span></span>  
 <span data-ttu-id="213e3-214">Následující příklad používá `Sub` příkaz zadat název, parametry a kód, který vytvoří text `Sub` postupu.</span><span class="sxs-lookup"><span data-stu-id="213e3-214">The following example uses the `Sub` statement to define the name, parameters, and code that form the body of a `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#58](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/sub-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="213e3-215">Příklad</span><span class="sxs-lookup"><span data-stu-id="213e3-215">Example</span></span>  
 <span data-ttu-id="213e3-216">V následujícím příkladu `DelayAsync` je `Async``Function` s návratovým typem <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="213e3-216">In the following example, `DelayAsync` is an `Async``Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="213e3-217">`DelayAsync` má `Return` příkaz, který vrátí celé číslo.</span><span class="sxs-lookup"><span data-stu-id="213e3-217">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="213e3-218">Proto funkce deklaraci `DelayAsync` musí mít návratový typ `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="213e3-218">Therefore, the function declaration of `DelayAsync` must have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="213e3-219">Vzhledem k tomu, že je návratový typ `Task(Of Integer)`, vyhodnocení `Await` výrazu v `DoSomethingAsync` vytváří celé číslo, jak ukazuje následující příkaz: `Dim result As Integer = Await delayTask`.</span><span class="sxs-lookup"><span data-stu-id="213e3-219">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer, as the following statement shows: `Dim result As Integer = Await delayTask`.</span></span>  
  
 <span data-ttu-id="213e3-220">`startButton_Click` Postup je příklad `Async Sub` postupu.</span><span class="sxs-lookup"><span data-stu-id="213e3-220">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="213e3-221">Protože `DoSomethingAsync` je `Async` funkce, úlohy pro volání `DoSomethingAsync` musí být očekáváno, jak ukazuje následující příkaz: `Await DoSomethingAsync()`.</span><span class="sxs-lookup"><span data-stu-id="213e3-221">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="213e3-222">`startButton_Click``Sub` Postupu musí být definovány se `Async` modifikátor vzhledem k tomu, že má `Await` výrazu.</span><span class="sxs-lookup"><span data-stu-id="213e3-222">The `startButton_Click``Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/sub-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="213e3-223">Viz také</span><span class="sxs-lookup"><span data-stu-id="213e3-223">See Also</span></span>  
 [<span data-ttu-id="213e3-224">Příkaz Implements</span><span class="sxs-lookup"><span data-stu-id="213e3-224">Implements Statement</span></span>](implements-statement.md)  
 [<span data-ttu-id="213e3-225">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="213e3-225">Function Statement</span></span>](function-statement.md)  
 [<span data-ttu-id="213e3-226">Seznam parametrů</span><span class="sxs-lookup"><span data-stu-id="213e3-226">Parameter List</span></span>](parameter-list.md)  
 [<span data-ttu-id="213e3-227">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="213e3-227">Dim Statement</span></span>](dim-statement.md)  
 [<span data-ttu-id="213e3-228">Příkaz Call</span><span class="sxs-lookup"><span data-stu-id="213e3-228">Call Statement</span></span>](call-statement.md)  
 [<span data-ttu-id="213e3-229">z</span><span class="sxs-lookup"><span data-stu-id="213e3-229">Of</span></span>](of-clause.md)  
 [<span data-ttu-id="213e3-230">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="213e3-230">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)  
 [<span data-ttu-id="213e3-231">Postupy: Použití obecné třídy</span><span class="sxs-lookup"><span data-stu-id="213e3-231">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [<span data-ttu-id="213e3-232">Řešení potíží s procedurami</span><span class="sxs-lookup"><span data-stu-id="213e3-232">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)  
 [<span data-ttu-id="213e3-233">Částečné metody</span><span class="sxs-lookup"><span data-stu-id="213e3-233">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
