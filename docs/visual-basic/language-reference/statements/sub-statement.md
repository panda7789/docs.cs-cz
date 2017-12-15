---
title: "Sub – příkaz (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Sub
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
caps.latest.revision: "52"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0a2d0d5ffdca857a3a5ca58cd38b0930f254526f
ms.sourcegitcommit: 8ed4ebc15b5ef89d06a7507dc9d5e306e30accf7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/14/2017
---
# <a name="sub-statement-visual-basic"></a><span data-ttu-id="b25bf-102">Sub – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b25bf-102">Sub Statement (Visual Basic)</span></span>
<span data-ttu-id="b25bf-103">Deklaruje název, parametry a kód, který definovat `Sub` postupu.</span><span class="sxs-lookup"><span data-stu-id="b25bf-103">Declares the name, parameters, and code that define a `Sub` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b25bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b25bf-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]  
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Sub ]  
    [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="b25bf-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="b25bf-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="b25bf-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="b25bf-106">Optional.</span></span> <span data-ttu-id="b25bf-107">V tématu [seznam atributů](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="b25bf-107">See [Attribute List](attribute-list.md).</span></span>  
  
-   `Partial`  
  
     <span data-ttu-id="b25bf-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="b25bf-108">Optional.</span></span> <span data-ttu-id="b25bf-109">Určuje definici částečné metody.</span><span class="sxs-lookup"><span data-stu-id="b25bf-109">Indicates definition of a partial method.</span></span> <span data-ttu-id="b25bf-110">V tématu [částečné metody](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="b25bf-110">See [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="b25bf-111">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="b25bf-111">Optional.</span></span> <span data-ttu-id="b25bf-112">Může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="b25bf-112">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="b25bf-113">Public</span><span class="sxs-lookup"><span data-stu-id="b25bf-113">Public</span></span>](../modifiers/public.md)  
  
    -   [<span data-ttu-id="b25bf-114">Protected</span><span class="sxs-lookup"><span data-stu-id="b25bf-114">Protected</span></span>](../modifiers/protected.md)  
  
    -   [<span data-ttu-id="b25bf-115">Friend</span><span class="sxs-lookup"><span data-stu-id="b25bf-115">Friend</span></span>](../modifiers/friend.md)  
  
    -   [<span data-ttu-id="b25bf-116">Private</span><span class="sxs-lookup"><span data-stu-id="b25bf-116">Private</span></span>](../modifiers/private.md)  
  
    -   `Protected Friend`  
  
     <span data-ttu-id="b25bf-117">V tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="b25bf-117">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `proceduremodifiers`  
  
     <span data-ttu-id="b25bf-118">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="b25bf-118">Optional.</span></span> <span data-ttu-id="b25bf-119">Může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="b25bf-119">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="b25bf-120">Overloads</span><span class="sxs-lookup"><span data-stu-id="b25bf-120">Overloads</span></span>](../modifiers/overloads.md)  
  
    -   [<span data-ttu-id="b25bf-121">Overrides</span><span class="sxs-lookup"><span data-stu-id="b25bf-121">Overrides</span></span>](../modifiers/overrides.md)  
  
    -   [<span data-ttu-id="b25bf-122">Overridable</span><span class="sxs-lookup"><span data-stu-id="b25bf-122">Overridable</span></span>](../modifiers/overridable.md)  
  
    -   [<span data-ttu-id="b25bf-123">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="b25bf-123">NotOverridable</span></span>](../modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="b25bf-124">MustOverride</span><span class="sxs-lookup"><span data-stu-id="b25bf-124">MustOverride</span></span>](../modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="b25bf-125">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="b25bf-125">Optional.</span></span> <span data-ttu-id="b25bf-126">V tématu [sdílené](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="b25bf-126">See [Shared](../modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="b25bf-127">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="b25bf-127">Optional.</span></span> <span data-ttu-id="b25bf-128">V tématu [stínů](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="b25bf-128">See [Shadows](../modifiers/shadows.md).</span></span>  
  
-   `Async`  
  
     <span data-ttu-id="b25bf-129">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="b25bf-129">Optional.</span></span> <span data-ttu-id="b25bf-130">V tématu [asynchronní](../modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="b25bf-130">See [Async](../modifiers/async.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="b25bf-131">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="b25bf-131">Required.</span></span> <span data-ttu-id="b25bf-132">Název procedury.</span><span class="sxs-lookup"><span data-stu-id="b25bf-132">Name of the procedure.</span></span> <span data-ttu-id="b25bf-133">V tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="b25bf-133">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span> <span data-ttu-id="b25bf-134">Chcete-li vytvořit proceduru konstruktor pro třídu, nastavte název `Sub` postup `New` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="b25bf-134">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="b25bf-135">Další informace najdete v tématu [doba života objektu: jak jsou objekty vytvořen a Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="b25bf-135">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
-   `typeparamlist`  
  
     <span data-ttu-id="b25bf-136">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="b25bf-136">Optional.</span></span> <span data-ttu-id="b25bf-137">Seznam parametrů typu pro obecný postup.</span><span class="sxs-lookup"><span data-stu-id="b25bf-137">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="b25bf-138">V tématu [zadejte seznam](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="b25bf-138">See [Type List](type-list.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="b25bf-139">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="b25bf-139">Optional.</span></span> <span data-ttu-id="b25bf-140">Seznam místní názvy proměnných představující parametry tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="b25bf-140">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="b25bf-141">V tématu [seznam parametrů](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="b25bf-141">See [Parameter List](parameter-list.md).</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="b25bf-142">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="b25bf-142">Optional.</span></span> <span data-ttu-id="b25bf-143">Označuje, že tento postup implementuje jeden nebo více `Sub` postupy, každé z nich definované v rozhraní implementované obsahující třídu nebo strukturu tento postup.</span><span class="sxs-lookup"><span data-stu-id="b25bf-143">Indicates that this procedure implements one or more `Sub` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="b25bf-144">V tématu [implementuje příkaz](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b25bf-144">See [Implements Statement](implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="b25bf-145">Požadováno pokud `Implements` pochází.</span><span class="sxs-lookup"><span data-stu-id="b25bf-145">Required if `Implements` is supplied.</span></span> <span data-ttu-id="b25bf-146">Seznam `Sub` postupy se implementuje.</span><span class="sxs-lookup"><span data-stu-id="b25bf-146">List of `Sub` procedures being implemented.</span></span>  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     <span data-ttu-id="b25bf-147">Každý `implementedprocedure` má následující syntaxe a částí:</span><span class="sxs-lookup"><span data-stu-id="b25bf-147">Each `implementedprocedure` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="b25bf-148">Část</span><span class="sxs-lookup"><span data-stu-id="b25bf-148">Part</span></span>|<span data-ttu-id="b25bf-149">Popis</span><span class="sxs-lookup"><span data-stu-id="b25bf-149">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="b25bf-150">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="b25bf-150">Required.</span></span> <span data-ttu-id="b25bf-151">Název rozhraní implementované tento postup obsahující třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="b25bf-151">Name of an interface implemented by this procedure's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="b25bf-152">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="b25bf-152">Required.</span></span> <span data-ttu-id="b25bf-153">Název, podle kterého postupu je definována v `interface`.</span><span class="sxs-lookup"><span data-stu-id="b25bf-153">Name by which the procedure is defined in `interface`.</span></span>|  
  
-   `Handles`  
  
     <span data-ttu-id="b25bf-154">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="b25bf-154">Optional.</span></span> <span data-ttu-id="b25bf-155">Označuje, že tento postup může zpracovat jeden nebo více konkrétní události.</span><span class="sxs-lookup"><span data-stu-id="b25bf-155">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="b25bf-156">V tématu [zpracovává](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="b25bf-156">See [Handles](handles-clause.md).</span></span>  
  
-   `eventlist`  
  
     <span data-ttu-id="b25bf-157">Požadováno pokud `Handles` pochází.</span><span class="sxs-lookup"><span data-stu-id="b25bf-157">Required if `Handles` is supplied.</span></span> <span data-ttu-id="b25bf-158">Seznam událostí, který zpracovává tento postup.</span><span class="sxs-lookup"><span data-stu-id="b25bf-158">List of events this procedure handles.</span></span>  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     <span data-ttu-id="b25bf-159">Každý `eventspecifier` má následující syntaxe a částí:</span><span class="sxs-lookup"><span data-stu-id="b25bf-159">Each `eventspecifier` has the following syntax and parts:</span></span>  
  
     `eventvariable.event`  
  
    |<span data-ttu-id="b25bf-160">Část</span><span class="sxs-lookup"><span data-stu-id="b25bf-160">Part</span></span>|<span data-ttu-id="b25bf-161">Popis</span><span class="sxs-lookup"><span data-stu-id="b25bf-161">Description</span></span>|  
    |---|---|  
    |`eventvariable`|<span data-ttu-id="b25bf-162">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="b25bf-162">Required.</span></span> <span data-ttu-id="b25bf-163">Objektová proměnná deklarovat s datový typ třídu nebo strukturu, která vyvolává událost.</span><span class="sxs-lookup"><span data-stu-id="b25bf-163">Object variable declared with the data type of the class or structure that raises the event.</span></span>|  
    |`event`|<span data-ttu-id="b25bf-164">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="b25bf-164">Required.</span></span> <span data-ttu-id="b25bf-165">Název události, který zpracovává tento postup.</span><span class="sxs-lookup"><span data-stu-id="b25bf-165">Name of the event this procedure handles.</span></span>|  
  
-   `statements`  
  
     <span data-ttu-id="b25bf-166">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="b25bf-166">Optional.</span></span> <span data-ttu-id="b25bf-167">Blok příkazů ke spuštění v rámci tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="b25bf-167">Block of statements to run within this procedure.</span></span>  
  
-   `End Sub`  
  
     <span data-ttu-id="b25bf-168">Ukončí definici tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="b25bf-168">Terminates the definition of this procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b25bf-169">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b25bf-169">Remarks</span></span>  
 <span data-ttu-id="b25bf-170">Všechny spustitelný kód musí být uvnitř procedury.</span><span class="sxs-lookup"><span data-stu-id="b25bf-170">All executable code must be inside a procedure.</span></span> <span data-ttu-id="b25bf-171">Použití `Sub` procedury při nechcete vrátit hodnotu volání kódu.</span><span class="sxs-lookup"><span data-stu-id="b25bf-171">Use a `Sub` procedure when you don't want to return a value to the calling code.</span></span> <span data-ttu-id="b25bf-172">Použití `Function` postup, pokud chcete vrátit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b25bf-172">Use a `Function` procedure when you want to return a value.</span></span>  
  
## <a name="defining-a-sub-procedure"></a><span data-ttu-id="b25bf-173">Definování Sub – procedury</span><span class="sxs-lookup"><span data-stu-id="b25bf-173">Defining a Sub Procedure</span></span>  
 <span data-ttu-id="b25bf-174">Můžete definovat `Sub` postup jenom na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="b25bf-174">You can define a `Sub` procedure only at the module level.</span></span> <span data-ttu-id="b25bf-175">Kontext deklarace pro proceduru sub proto musí být třídy, struktury, modul nebo rozhraní a nemůže být zdrojový soubor, obor názvů, procedury nebo blok.</span><span class="sxs-lookup"><span data-stu-id="b25bf-175">The declaration context for a sub procedure must, therefore, be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="b25bf-176">Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="b25bf-176">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="b25bf-177">`Sub`Výchozí nastavení postupy veřejný přístup.</span><span class="sxs-lookup"><span data-stu-id="b25bf-177">`Sub` procedures default to public access.</span></span> <span data-ttu-id="b25bf-178">Jejich úrovně přístupu můžete upravit pomocí modifikátory přístupu.</span><span class="sxs-lookup"><span data-stu-id="b25bf-178">You can adjust their access levels by using the access modifiers.</span></span>  
  
 <span data-ttu-id="b25bf-179">Pokud postup používá `Implements` – klíčové slovo, obsahující třídu nebo strukturu, musíte mít `Implements` příkaz, který následuje jeho `Class` nebo `Structure` příkaz.</span><span class="sxs-lookup"><span data-stu-id="b25bf-179">If the procedure uses the `Implements` keyword, the containing class or structure must have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="b25bf-180">`Implements` Příkaz musí zahrnovat každé rozhraní, který je uveden v `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="b25bf-180">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="b25bf-181">Ale název, podle kterého rozhraní definuje `Sub` (v `definedname`) nemusí odpovídat názvu tohoto postupu (v `name`).</span><span class="sxs-lookup"><span data-stu-id="b25bf-181">However, the name by which an interface defines the `Sub` (in `definedname`) doesn't have to match the name of this procedure (in `name`).</span></span>  
  
## <a name="returning-from-a-sub-procedure"></a><span data-ttu-id="b25bf-182">Vrácení z Sub – procedury</span><span class="sxs-lookup"><span data-stu-id="b25bf-182">Returning from a Sub Procedure</span></span>  
 <span data-ttu-id="b25bf-183">Když `Sub` postup vrátí kód volání, pokračuje provádění příkaz po příkazu, která je volána.</span><span class="sxs-lookup"><span data-stu-id="b25bf-183">When a `Sub` procedure returns to the calling code, execution continues with the statement after the statement that called it.</span></span>  
  
 <span data-ttu-id="b25bf-184">Následující příklad ukazuje vrátit z `Sub` postupu.</span><span class="sxs-lookup"><span data-stu-id="b25bf-184">The following example shows a return from a `Sub` procedure.</span></span>  
  
```vb  
Sub mySub(ByVal q As String)  
    Return  
End Sub   
```  
  
 <span data-ttu-id="b25bf-185">`Exit Sub` a `Return` příkazy způsobit okamžitou výstupu z `Sub` postupu.</span><span class="sxs-lookup"><span data-stu-id="b25bf-185">The `Exit Sub` and `Return` statements cause an immediate exit from a `Sub` procedure.</span></span> <span data-ttu-id="b25bf-186">Libovolný počet `Exit Sub` a `Return` příkazy může vyskytovat kdekoli v postupu, a je možné kombinovat `Exit Sub` a `Return` příkazy.</span><span class="sxs-lookup"><span data-stu-id="b25bf-186">Any number of `Exit Sub` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Sub` and `Return` statements.</span></span>  
  
## <a name="calling-a-sub-procedure"></a><span data-ttu-id="b25bf-187">Volání metody Sub – procedury</span><span class="sxs-lookup"><span data-stu-id="b25bf-187">Calling a Sub Procedure</span></span>  
 <span data-ttu-id="b25bf-188">Volání `Sub` postup s využitím název procedury v příkazu a potom následující tento název s jeho seznam argumentů v závorkách.</span><span class="sxs-lookup"><span data-stu-id="b25bf-188">You call a `Sub` procedure by using the procedure name in a statement and then following that name with its argument list in parentheses.</span></span> <span data-ttu-id="b25bf-189">Závorky můžete vynechat, pouze v případě, že jste zadali žádné argumenty.</span><span class="sxs-lookup"><span data-stu-id="b25bf-189">You can omit the parentheses only if you don't supply any arguments.</span></span> <span data-ttu-id="b25bf-190">Váš kód je však lépe čitelný, pokud vždy zahrnovat závorkách.</span><span class="sxs-lookup"><span data-stu-id="b25bf-190">However, your code is more readable if you always include the parentheses.</span></span>  
  
 <span data-ttu-id="b25bf-191">A `Sub` postupu a `Function` postupu můžete mít parametry a provádět řadu příkazů.</span><span class="sxs-lookup"><span data-stu-id="b25bf-191">A `Sub` procedure and a `Function` procedure  can have parameters and perform a series of statements.</span></span> <span data-ttu-id="b25bf-192">Ale `Function` postup vrátí hodnotu a `Sub` postup není.</span><span class="sxs-lookup"><span data-stu-id="b25bf-192">However, a `Function` procedure returns a value, and a `Sub` procedure doesn't.</span></span> <span data-ttu-id="b25bf-193">Proto nelze použít `Sub` postup ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="b25bf-193">Therefore, you can't use a `Sub` procedure in an expression.</span></span>  
  
 <span data-ttu-id="b25bf-194">Můžete použít `Call` – klíčové slovo při volání `Sub` postup, ale že – klíčové slovo není vhodná pro většinu používá.</span><span class="sxs-lookup"><span data-stu-id="b25bf-194">You can use the `Call` keyword when you call a `Sub` procedure, but that keyword isn't recommended for most uses.</span></span> <span data-ttu-id="b25bf-195">Další informace najdete v tématu [volání příkazu](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b25bf-195">For more information, see [Call Statement](call-statement.md).</span></span>  
  
 <span data-ttu-id="b25bf-196">Visual Basic někdy Přeuspořádá aritmetických výrazech ke zvýšení efektivity interní.</span><span class="sxs-lookup"><span data-stu-id="b25bf-196">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="b25bf-197">Z tohoto důvodu Pokud váš argument seznam obsahuje výrazy, které volají další postupy, budete by neměl předpokládat, že bude volán tyto výrazy v určitém pořadí.</span><span class="sxs-lookup"><span data-stu-id="b25bf-197">For that reason, if your argument list includes expressions that call other procedures, you shouldn't assume that those expressions will be called in a particular order.</span></span>  
  
## <a name="async-sub-procedures"></a><span data-ttu-id="b25bf-198">Asynchronní Sub – procedury</span><span class="sxs-lookup"><span data-stu-id="b25bf-198">Async Sub Procedures</span></span>  
 <span data-ttu-id="b25bf-199">Pomocí funkce asynchronní můžete vyvolat asynchronní funkce bez použití explicitní zpětná volání nebo Ruční rozdělení kódu napříč více funkcí nebo výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="b25bf-199">By using the Async feature, you can invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>  
  
 <span data-ttu-id="b25bf-200">Pokud označíte procedura se [asynchronní](../modifiers/async.md) modifikátor, můžete použít [Await](../../../visual-basic/language-reference/operators/await-operator.md) operátor v postupu.</span><span class="sxs-lookup"><span data-stu-id="b25bf-200">If you mark a procedure with the [Async](../modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the procedure.</span></span> <span data-ttu-id="b25bf-201">Při řízení dosáhnou `Await` výrazu v `Async` postupu řízení vrátí volajícímu a průběh v postupu je pozastaveno, dokud dokončení awaited úlohy.</span><span class="sxs-lookup"><span data-stu-id="b25bf-201">When control reaches an `Await` expression in the `Async` procedure, control returns to the caller, and progress in the procedure is suspended until the awaited task completes.</span></span> <span data-ttu-id="b25bf-202">Po dokončení úlohy provádění může pokračovat v postupu.</span><span class="sxs-lookup"><span data-stu-id="b25bf-202">When the task is complete, execution can resume in the procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b25bf-203">`Async` Postup vrátí volajícího, když je zjištěna buď první awaited objekt, který ještě není dokončena nebo konci `Async` postup je dosaženo, cokoliv nastane dříve.</span><span class="sxs-lookup"><span data-stu-id="b25bf-203">An `Async` procedure returns to the caller when either the first awaited object that’s not yet complete is encountered or the end of the `Async` procedure is reached, whichever occurs first.</span></span>  
  
 <span data-ttu-id="b25bf-204">Můžete také označit [funkce příkaz](function-statement.md) s `Async` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="b25bf-204">You can also mark a [Function Statement](function-statement.md) with the `Async` modifier.</span></span> <span data-ttu-id="b25bf-205">`Async` Funkce může mít návratový typ <xref:System.Threading.Tasks.Task%601> nebo <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="b25bf-205">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="b25bf-206">Příklad později v tomto tématu je uveden `Async` funkce, která má návratový typ <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="b25bf-206">An example later in this topic shows an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
 <span data-ttu-id="b25bf-207">`Async``Sub` postupy se primárně používají pro obslužné rutiny událostí, kde nejde vrátit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b25bf-207">`Async` `Sub` procedures are primarily used for event handlers, where a value can't be returned.</span></span> <span data-ttu-id="b25bf-208">`Async``Sub` Procedury nelze očekáváno a volající `Async``Sub` procedury nelze zachytit výjimky, `Sub` postup vyvolává.</span><span class="sxs-lookup"><span data-stu-id="b25bf-208">An `Async``Sub` procedure can't be awaited, and the caller of an `Async``Sub` procedure can't catch exceptions that the `Sub` procedure throws.</span></span>  
  
 <span data-ttu-id="b25bf-209">`Async` Procedury nelze deklarovat všechny [ByRef](../modifiers/byref.md) parametry.</span><span class="sxs-lookup"><span data-stu-id="b25bf-209">An `Async` procedure can't declare any [ByRef](../modifiers/byref.md) parameters.</span></span>  
  
 <span data-ttu-id="b25bf-210">Další informace o `Async` postupech najdete v [asynchronní programování s Async a Await](../../../visual-basic/programming-guide/concepts/async/index.md), [řízení toku v asynchronních programech](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), a [asynchronní vrátit typy](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="b25bf-210">For more information about `Async` procedures, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b25bf-211">Příklad</span><span class="sxs-lookup"><span data-stu-id="b25bf-211">Example</span></span>  
 <span data-ttu-id="b25bf-212">Následující příklad používá `Sub` příkaz zadat název, parametry a kód, který vytvoří text `Sub` postupu.</span><span class="sxs-lookup"><span data-stu-id="b25bf-212">The following example uses the `Sub` statement to define the name, parameters, and code that form the body of a `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#58](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/sub-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="b25bf-213">Příklad</span><span class="sxs-lookup"><span data-stu-id="b25bf-213">Example</span></span>  
 <span data-ttu-id="b25bf-214">V následujícím příkladu `DelayAsync` je `Async``Function` s návratovým typem <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="b25bf-214">In the following example, `DelayAsync` is an `Async``Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="b25bf-215">`DelayAsync`má `Return` příkaz, který vrátí celé číslo.</span><span class="sxs-lookup"><span data-stu-id="b25bf-215">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="b25bf-216">Proto funkce deklaraci `DelayAsync` musí mít návratový typ `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="b25bf-216">Therefore, the function declaration of `DelayAsync` must have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="b25bf-217">Vzhledem k tomu, že je návratový typ `Task(Of Integer)`, vyhodnocení `Await` výrazu v `DoSomethingAsync` vytváří celé číslo, jak ukazuje následující příkaz: `Dim result As Integer = Await delayTask`.</span><span class="sxs-lookup"><span data-stu-id="b25bf-217">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer, as the following statement shows: `Dim result As Integer = Await delayTask`.</span></span>  
  
 <span data-ttu-id="b25bf-218">`startButton_Click` Postup je příklad `Async Sub` postupu.</span><span class="sxs-lookup"><span data-stu-id="b25bf-218">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="b25bf-219">Protože `DoSomethingAsync` je `Async` funkce, úlohy pro volání `DoSomethingAsync` musí být očekáváno, jak ukazuje následující příkaz: `Await DoSomethingAsync()`.</span><span class="sxs-lookup"><span data-stu-id="b25bf-219">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="b25bf-220">`startButton_Click``Sub` Postupu musí být definovány se `Async` modifikátor vzhledem k tomu, že má `Await` výrazu.</span><span class="sxs-lookup"><span data-stu-id="b25bf-220">The `startButton_Click``Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/sub-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b25bf-221">Viz také</span><span class="sxs-lookup"><span data-stu-id="b25bf-221">See Also</span></span>  
 [<span data-ttu-id="b25bf-222">Příkaz Implements</span><span class="sxs-lookup"><span data-stu-id="b25bf-222">Implements Statement</span></span>](implements-statement.md)  
 [<span data-ttu-id="b25bf-223">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="b25bf-223">Function Statement</span></span>](function-statement.md)  
 [<span data-ttu-id="b25bf-224">Seznam parametrů</span><span class="sxs-lookup"><span data-stu-id="b25bf-224">Parameter List</span></span>](parameter-list.md)  
 [<span data-ttu-id="b25bf-225">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="b25bf-225">Dim Statement</span></span>](dim-statement.md)  
 [<span data-ttu-id="b25bf-226">Příkaz Call</span><span class="sxs-lookup"><span data-stu-id="b25bf-226">Call Statement</span></span>](call-statement.md)  
 [<span data-ttu-id="b25bf-227">Z</span><span class="sxs-lookup"><span data-stu-id="b25bf-227">Of</span></span>](of-clause.md)  
 [<span data-ttu-id="b25bf-228">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="b25bf-228">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)  
 [<span data-ttu-id="b25bf-229">Postupy: Použití obecné třídy</span><span class="sxs-lookup"><span data-stu-id="b25bf-229">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [<span data-ttu-id="b25bf-230">Řešení potíží s procedurami</span><span class="sxs-lookup"><span data-stu-id="b25bf-230">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)  
 [<span data-ttu-id="b25bf-231">Částečné metody</span><span class="sxs-lookup"><span data-stu-id="b25bf-231">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
