---
title: "Function – příkaz (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Function
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
caps.latest.revision: "62"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 667ab7ceb54e1f339fd645883ca2686c0cbb72b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="function-statement-visual-basic"></a><span data-ttu-id="c18c2-102">Function – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c18c2-102">Function Statement (Visual Basic)</span></span>
<span data-ttu-id="c18c2-103">Deklaruje název, parametry a kód, který definovat `Function` postupu.</span><span class="sxs-lookup"><span data-stu-id="c18c2-103">Declares the name, parameters, and code that define a `Function` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c18c2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c18c2-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]  
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Function ]  
    [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="c18c2-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="c18c2-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="c18c2-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="c18c2-106">Optional.</span></span> <span data-ttu-id="c18c2-107">V tématu [seznam atributů](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="c18c2-107">See [Attribute List](attribute-list.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="c18c2-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="c18c2-108">Optional.</span></span> <span data-ttu-id="c18c2-109">Může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="c18c2-109">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="c18c2-110">Veřejné</span><span class="sxs-lookup"><span data-stu-id="c18c2-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="c18c2-111">Chráněný</span><span class="sxs-lookup"><span data-stu-id="c18c2-111">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="c18c2-112">Friend</span><span class="sxs-lookup"><span data-stu-id="c18c2-112">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="c18c2-113">Privátní</span><span class="sxs-lookup"><span data-stu-id="c18c2-113">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     <span data-ttu-id="c18c2-114">V tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="c18c2-114">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `proceduremodifiers`  
  
     <span data-ttu-id="c18c2-115">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="c18c2-115">Optional.</span></span> <span data-ttu-id="c18c2-116">Může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="c18c2-116">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="c18c2-117">Přetížení</span><span class="sxs-lookup"><span data-stu-id="c18c2-117">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [<span data-ttu-id="c18c2-118">Přepsání</span><span class="sxs-lookup"><span data-stu-id="c18c2-118">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [<span data-ttu-id="c18c2-119">Overridable</span><span class="sxs-lookup"><span data-stu-id="c18c2-119">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [<span data-ttu-id="c18c2-120">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="c18c2-120">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="c18c2-121">MustOverride</span><span class="sxs-lookup"><span data-stu-id="c18c2-121">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="c18c2-122">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="c18c2-122">Optional.</span></span> <span data-ttu-id="c18c2-123">V tématu [sdílené](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="c18c2-123">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="c18c2-124">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="c18c2-124">Optional.</span></span> <span data-ttu-id="c18c2-125">V tématu [stínů](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="c18c2-125">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `Async`  
  
     <span data-ttu-id="c18c2-126">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="c18c2-126">Optional.</span></span> <span data-ttu-id="c18c2-127">V tématu [asynchronní](../../../visual-basic/language-reference/modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="c18c2-127">See [Async](../../../visual-basic/language-reference/modifiers/async.md).</span></span>  
  
-   `Iterator`  
  
     <span data-ttu-id="c18c2-128">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="c18c2-128">Optional.</span></span> <span data-ttu-id="c18c2-129">V tématu [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="c18c2-129">See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="c18c2-130">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="c18c2-130">Required.</span></span> <span data-ttu-id="c18c2-131">Název procedury.</span><span class="sxs-lookup"><span data-stu-id="c18c2-131">Name of the procedure.</span></span> <span data-ttu-id="c18c2-132">V tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="c18c2-132">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `typeparamlist`  
  
     <span data-ttu-id="c18c2-133">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="c18c2-133">Optional.</span></span> <span data-ttu-id="c18c2-134">Seznam parametrů typu pro obecný postup.</span><span class="sxs-lookup"><span data-stu-id="c18c2-134">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="c18c2-135">V tématu [zadejte seznam](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="c18c2-135">See [Type List](type-list.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="c18c2-136">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="c18c2-136">Optional.</span></span> <span data-ttu-id="c18c2-137">Seznam místní názvy proměnných představující parametry tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="c18c2-137">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="c18c2-138">V tématu [seznam parametrů](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="c18c2-138">See [Parameter List](parameter-list.md).</span></span>  
  
-   `returntype`  
  
     <span data-ttu-id="c18c2-139">Požadováno pokud `Option Strict` je `On`.</span><span class="sxs-lookup"><span data-stu-id="c18c2-139">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="c18c2-140">Datový typ hodnoty vrácené tímto postupem.</span><span class="sxs-lookup"><span data-stu-id="c18c2-140">Data type of the value returned by this procedure.</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="c18c2-141">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="c18c2-141">Optional.</span></span> <span data-ttu-id="c18c2-142">Označuje, že tento postup implementuje jeden nebo více `Function` postupy, každé z nich definované v rozhraní implementované obsahující třídu nebo strukturu tento postup.</span><span class="sxs-lookup"><span data-stu-id="c18c2-142">Indicates that this procedure implements one or more `Function` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="c18c2-143">V tématu [implementuje příkaz](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c18c2-143">See [Implements Statement](implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="c18c2-144">Požadováno pokud `Implements` pochází.</span><span class="sxs-lookup"><span data-stu-id="c18c2-144">Required if `Implements` is supplied.</span></span> <span data-ttu-id="c18c2-145">Seznam `Function` postupy se implementuje.</span><span class="sxs-lookup"><span data-stu-id="c18c2-145">List of `Function` procedures being implemented.</span></span>  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     <span data-ttu-id="c18c2-146">Každý `implementedprocedure` má následující syntaxe a částí:</span><span class="sxs-lookup"><span data-stu-id="c18c2-146">Each `implementedprocedure` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="c18c2-147">Část</span><span class="sxs-lookup"><span data-stu-id="c18c2-147">Part</span></span>|<span data-ttu-id="c18c2-148">Popis</span><span class="sxs-lookup"><span data-stu-id="c18c2-148">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="c18c2-149">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="c18c2-149">Required.</span></span> <span data-ttu-id="c18c2-150">Název rozhraní implementované tento postup obsahující třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="c18c2-150">Name of an interface implemented by this procedure's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="c18c2-151">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="c18c2-151">Required.</span></span> <span data-ttu-id="c18c2-152">Název, podle kterého postupu je definována v `interface`.</span><span class="sxs-lookup"><span data-stu-id="c18c2-152">Name by which the procedure is defined in `interface`.</span></span>|  
  
-   `Handles`  
  
     <span data-ttu-id="c18c2-153">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="c18c2-153">Optional.</span></span> <span data-ttu-id="c18c2-154">Označuje, že tento postup může zpracovat jeden nebo více konkrétní události.</span><span class="sxs-lookup"><span data-stu-id="c18c2-154">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="c18c2-155">V tématu [zpracovává](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="c18c2-155">See [Handles](handles-clause.md).</span></span>  
  
-   `eventlist`  
  
     <span data-ttu-id="c18c2-156">Požadováno pokud `Handles` pochází.</span><span class="sxs-lookup"><span data-stu-id="c18c2-156">Required if `Handles` is supplied.</span></span> <span data-ttu-id="c18c2-157">Seznam událostí, který zpracovává tento postup.</span><span class="sxs-lookup"><span data-stu-id="c18c2-157">List of events this procedure handles.</span></span>  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     <span data-ttu-id="c18c2-158">Každý `eventspecifier` má následující syntaxe a částí:</span><span class="sxs-lookup"><span data-stu-id="c18c2-158">Each `eventspecifier` has the following syntax and parts:</span></span>  
  
     `eventvariable.event`  
  
    |<span data-ttu-id="c18c2-159">Část</span><span class="sxs-lookup"><span data-stu-id="c18c2-159">Part</span></span>|<span data-ttu-id="c18c2-160">Popis</span><span class="sxs-lookup"><span data-stu-id="c18c2-160">Description</span></span>|  
    |---|---|  
    |`eventvariable`|<span data-ttu-id="c18c2-161">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="c18c2-161">Required.</span></span> <span data-ttu-id="c18c2-162">Objektová proměnná deklarovat s datový typ třídu nebo strukturu, která vyvolává událost.</span><span class="sxs-lookup"><span data-stu-id="c18c2-162">Object variable declared with the data type of the class or structure that raises the event.</span></span>|  
    |`event`|<span data-ttu-id="c18c2-163">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="c18c2-163">Required.</span></span> <span data-ttu-id="c18c2-164">Název události, který zpracovává tento postup.</span><span class="sxs-lookup"><span data-stu-id="c18c2-164">Name of the event this procedure handles.</span></span>|  
  
-   `statements`  
  
     <span data-ttu-id="c18c2-165">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="c18c2-165">Optional.</span></span> <span data-ttu-id="c18c2-166">Blok příkazů k provedení v rámci tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="c18c2-166">Block of statements to be executed within this procedure.</span></span>  
  
-   `End Function`  
  
     <span data-ttu-id="c18c2-167">Ukončí definici tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="c18c2-167">Terminates the definition of this procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c18c2-168">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c18c2-168">Remarks</span></span>  
 <span data-ttu-id="c18c2-169">Všechny spustitelný kód musí být uvnitř procedury.</span><span class="sxs-lookup"><span data-stu-id="c18c2-169">All executable code must be inside a procedure.</span></span> <span data-ttu-id="c18c2-170">Každý postup je pak deklarované v rámci třídy, struktury nebo modul, který se označuje jako obsahující třídy, struktury nebo modul.</span><span class="sxs-lookup"><span data-stu-id="c18c2-170">Each procedure, in turn, is declared within a class, a structure, or a module that is referred to as the containing class, structure, or module.</span></span>  
  
 <span data-ttu-id="c18c2-171">Chcete-li vrátit hodnotu volání kódu, použijte `Function` postupu; jinak použijte `Sub` postup.</span><span class="sxs-lookup"><span data-stu-id="c18c2-171">To return a value to the calling code, use a `Function` procedure; otherwise, use a `Sub` procedure.</span></span>  
  
## <a name="defining-a-function"></a><span data-ttu-id="c18c2-172">Definování funkcí</span><span class="sxs-lookup"><span data-stu-id="c18c2-172">Defining a Function</span></span>  
 <span data-ttu-id="c18c2-173">Můžete definovat `Function` postup jenom na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="c18c2-173">You can define a `Function` procedure only at the module level.</span></span> <span data-ttu-id="c18c2-174">Kontext deklarace pro funkci proto musí být třídy, struktury, modul nebo rozhraní a nemůže být zdrojový soubor, obor názvů, procedury nebo blok.</span><span class="sxs-lookup"><span data-stu-id="c18c2-174">Therefore, the declaration context for a function must be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="c18c2-175">Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="c18c2-175">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="c18c2-176">`Function`Výchozí nastavení postupy veřejný přístup.</span><span class="sxs-lookup"><span data-stu-id="c18c2-176">`Function` procedures default to public access.</span></span> <span data-ttu-id="c18c2-177">Můžete nastavit jejich úrovně přístupu s modifikátory přístupu.</span><span class="sxs-lookup"><span data-stu-id="c18c2-177">You can adjust their access levels with the access modifiers.</span></span>  
  
 <span data-ttu-id="c18c2-178">A `Function` postupu můžou deklarovat datový typ hodnoty, která vrátí postupu.</span><span class="sxs-lookup"><span data-stu-id="c18c2-178">A `Function` procedure can declare the data type of the value that the procedure returns.</span></span> <span data-ttu-id="c18c2-179">Můžete zadat jakýkoli datový typ nebo název výčet, struktury, třídu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c18c2-179">You can specify any data type or the name of an enumeration, a structure, a class, or an interface.</span></span> <span data-ttu-id="c18c2-180">Pokud nezadáte `returntype` vrátí parametr postupu `Object`.</span><span class="sxs-lookup"><span data-stu-id="c18c2-180">If you don't specify the `returntype` parameter, the procedure returns `Object`.</span></span>  
  
 <span data-ttu-id="c18c2-181">Pokud tento postup používá `Implements` – klíčové slovo, obsahující třídu nebo strukturu musí také mít `Implements` příkaz, který následuje jeho `Class` nebo `Structure` příkaz.</span><span class="sxs-lookup"><span data-stu-id="c18c2-181">If this procedure uses the `Implements` keyword, the containing class or structure must also have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="c18c2-182">`Implements` Příkaz musí zahrnovat každé rozhraní, který je uveden v `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="c18c2-182">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="c18c2-183">Ale název, podle kterého rozhraní definuje `Function` (v `definedname`) nemusí odpovídat názvu tohoto postupu (v `name`).</span><span class="sxs-lookup"><span data-stu-id="c18c2-183">However, the name by which an interface defines the `Function` (in `definedname`) doesn't need to match the name of this procedure (in `name`).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c18c2-184">Lambda – výrazy můžete použít k definování vložené výrazy funkce.</span><span class="sxs-lookup"><span data-stu-id="c18c2-184">You can use lambda expressions to define function expressions inline.</span></span> <span data-ttu-id="c18c2-185">Další informace najdete v tématu [výraz funkce](../../../visual-basic/language-reference/operators/function-expression.md) a [výrazy Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="c18c2-185">For more information, see [Function Expression](../../../visual-basic/language-reference/operators/function-expression.md) and [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
## <a name="returning-from-a-function"></a><span data-ttu-id="c18c2-186">Vrácení z funkce</span><span class="sxs-lookup"><span data-stu-id="c18c2-186">Returning from a Function</span></span>  
 <span data-ttu-id="c18c2-187">Když `Function` postup vrátí kód volání, pokračuje provádění příkaz, který následuje příkaz, který volá postup.</span><span class="sxs-lookup"><span data-stu-id="c18c2-187">When the `Function` procedure returns to the calling code, execution continues with the statement that follows the statement that called the procedure.</span></span>  
  
 <span data-ttu-id="c18c2-188">Vrácení hodnoty z funkce, můžete přiřadit hodnotu název funkce nebo ji v zahrnout `Return` příkaz.</span><span class="sxs-lookup"><span data-stu-id="c18c2-188">To return a value from a function, you can either assign the value to the function name or include it in a `Return` statement.</span></span>  
  
 <span data-ttu-id="c18c2-189">`Return` Příkaz současně přiřadí návratovou hodnotu a ukončí funkce, jako ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="c18c2-189">The `Return` statement simultaneously assigns the return value and exits the function, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_1.vb)]  
  
 <span data-ttu-id="c18c2-190">Následující příklad přiřadí návratovou hodnotu pro název funkce `myFunction` a použije je `Exit Function` příkaz, který má vrátit.</span><span class="sxs-lookup"><span data-stu-id="c18c2-190">The following example assigns the return value to the function name `myFunction` and then uses the `Exit Function` statement to return.</span></span>  
  
 [!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_2.vb)]  
  
 <span data-ttu-id="c18c2-191">`Exit Function` a `Return` příkazy způsobit okamžitou výstupu z `Function` postupu.</span><span class="sxs-lookup"><span data-stu-id="c18c2-191">The `Exit Function` and `Return` statements cause an immediate exit from a `Function` procedure.</span></span> <span data-ttu-id="c18c2-192">Libovolný počet `Exit Function` a `Return` příkazy může vyskytovat kdekoli v postupu, a je možné kombinovat `Exit Function` a `Return` příkazy.</span><span class="sxs-lookup"><span data-stu-id="c18c2-192">Any number of `Exit Function` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Function` and `Return` statements.</span></span>  
  
 <span data-ttu-id="c18c2-193">Pokud používáte `Exit Function` bez přiřazení hodnoty k `name`, vrátí výchozí hodnota pro datový typ, který je uveden v postupu `returntype`.</span><span class="sxs-lookup"><span data-stu-id="c18c2-193">If you use `Exit Function` without assigning a value to `name`, the procedure returns the default value for the data type that's specified in `returntype`.</span></span> <span data-ttu-id="c18c2-194">Pokud `returntype` není zadán, vrátí postup `Nothing`, což je výchozí hodnota pro `Object`.</span><span class="sxs-lookup"><span data-stu-id="c18c2-194">If `returntype` isn't specified, the procedure returns `Nothing`, which is the default value for `Object`.</span></span>  
  
## <a name="calling-a-function"></a><span data-ttu-id="c18c2-195">Volání funkce</span><span class="sxs-lookup"><span data-stu-id="c18c2-195">Calling a Function</span></span>  
 <span data-ttu-id="c18c2-196">Volání `Function` postup pomocí název postupu, za nímž následuje seznam argumentů v závorkách ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="c18c2-196">You call a `Function` procedure by using the procedure name, followed by the argument list in parentheses, in an expression.</span></span> <span data-ttu-id="c18c2-197">Závorky můžete vynechat, pouze v případě, že nejsou zadávání žádné argumenty.</span><span class="sxs-lookup"><span data-stu-id="c18c2-197">You can omit the parentheses only if you aren't supplying any arguments.</span></span> <span data-ttu-id="c18c2-198">Váš kód je však lépe čitelný, pokud vždy zahrnovat závorkách.</span><span class="sxs-lookup"><span data-stu-id="c18c2-198">However, your code is more readable if you always include the parentheses.</span></span>  
  
 <span data-ttu-id="c18c2-199">Volání `Function` postup volat žádnou knihovnu stejným způsobem jako funkce, jako `Sqrt`, `Cos`, nebo `ChrW`.</span><span class="sxs-lookup"><span data-stu-id="c18c2-199">You call a `Function` procedure the same way that you call any library function such as `Sqrt`, `Cos`, or `ChrW`.</span></span>  
  
 <span data-ttu-id="c18c2-200">Můžete také zavolat funkci pomocí `Call` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="c18c2-200">You can also call a function by using the `Call` keyword.</span></span> <span data-ttu-id="c18c2-201">V takovém případě se ignoruje návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c18c2-201">In that case, the return value is ignored.</span></span> <span data-ttu-id="c18c2-202">Použití `Call` ve většině případů se nedoporučuje – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="c18c2-202">Use of the `Call` keyword isn't recommended in most cases.</span></span> <span data-ttu-id="c18c2-203">Další informace najdete v tématu [volání příkazu](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c18c2-203">For more information, see [Call Statement](call-statement.md).</span></span>  
  
 <span data-ttu-id="c18c2-204">Visual Basic někdy Přeuspořádá aritmetických výrazech ke zvýšení efektivity interní.</span><span class="sxs-lookup"><span data-stu-id="c18c2-204">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="c18c2-205">Z tohoto důvodu byste neměli používat `Function` postup ve výrazu aritmetické při změně hodnot proměnných ve stejném výrazu funkce.</span><span class="sxs-lookup"><span data-stu-id="c18c2-205">For that reason, you shouldn't use a `Function` procedure in an arithmetic expression when the function changes the value of variables in the same expression.</span></span>  
  
## <a name="async-functions"></a><span data-ttu-id="c18c2-206">Asynchronní funkce</span><span class="sxs-lookup"><span data-stu-id="c18c2-206">Async Functions</span></span>  
 <span data-ttu-id="c18c2-207">*Asynchronní* funkce umožňuje vyvolání asynchronní funkce bez použití explicitní zpětná volání nebo Ruční rozdělení kódu napříč více funkcí nebo výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="c18c2-207">The *Async* feature allows you to invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>  
  
 <span data-ttu-id="c18c2-208">Pokud označíte funkce s [asynchronní](../../../visual-basic/language-reference/modifiers/async.md) modifikátor, můžete použít [Await](../../../visual-basic/language-reference/operators/await-operator.md) operátor ve funkci.</span><span class="sxs-lookup"><span data-stu-id="c18c2-208">If you mark a function with the [Async](../../../visual-basic/language-reference/modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the function.</span></span> <span data-ttu-id="c18c2-209">Při řízení dosáhnou `Await` výrazu v `Async` funkce, vrátí ovládací prvek volajícímu a průběh ve funkci je pozastaveno, dokud dokončení awaited úlohy.</span><span class="sxs-lookup"><span data-stu-id="c18c2-209">When control reaches an `Await` expression in the `Async` function, control returns to the caller, and progress in the function is suspended until the awaited task completes.</span></span> <span data-ttu-id="c18c2-210">Po dokončení úlohy můžete pokračovat v provádění ve funkci.</span><span class="sxs-lookup"><span data-stu-id="c18c2-210">When the task is complete, execution can resume in the function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c18c2-211">`Async` Postup vrátí volajícímu při buď zjistí první awaited objekt, který ještě není dokončena nebo získá na konec `Async` postup, cokoliv nastane dříve.</span><span class="sxs-lookup"><span data-stu-id="c18c2-211">An `Async` procedure returns to the caller when either it encounters the first awaited object that’s not yet complete, or it gets to the end of the `Async` procedure, whichever occurs first.</span></span>  
  
 <span data-ttu-id="c18c2-212">`Async` Funkce může mít návratový typ <xref:System.Threading.Tasks.Task%601> nebo <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="c18c2-212">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="c18c2-213">Příklad `Async` funkce, která má návratový typ <xref:System.Threading.Tasks.Task%601> najdete níže.</span><span class="sxs-lookup"><span data-stu-id="c18c2-213">An example of an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601> is provided below.</span></span>  
  
 <span data-ttu-id="c18c2-214">`Async` Funkce nelze deklarovat všechny [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parametry.</span><span class="sxs-lookup"><span data-stu-id="c18c2-214">An `Async` function cannot declare any [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parameters.</span></span>  
  
 <span data-ttu-id="c18c2-215">A [Sub – příkaz](sub-statement.md) může také být označen `Async` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="c18c2-215">A [Sub Statement](sub-statement.md) can also be marked with the `Async` modifier.</span></span> <span data-ttu-id="c18c2-216">Především používá se pro obslužné rutiny událostí, kde nejde vrátit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c18c2-216">This is primarily used for event handlers, where a value cannot be returned.</span></span> <span data-ttu-id="c18c2-217">`Async``Sub` Procedury nelze očekáváno a volající `Async``Sub` procedury nelze catch výjimky, které jsou vyvolány `Sub` postupu.</span><span class="sxs-lookup"><span data-stu-id="c18c2-217">An `Async``Sub` procedure can't be awaited, and the caller of an `Async``Sub` procedure can't catch exceptions that are thrown by the `Sub` procedure.</span></span>  
  
 <span data-ttu-id="c18c2-218">Další informace o `Async` funkce, najdete v části [asynchronní programování s Async a Await](../../../visual-basic/programming-guide/concepts/async/index.md), [řízení toku v asynchronních programech](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), a [asynchronní vrátit typy](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="c18c2-218">For more information about `Async` functions, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="iterator-functions"></a><span data-ttu-id="c18c2-219">Iterator funkce</span><span class="sxs-lookup"><span data-stu-id="c18c2-219">Iterator Functions</span></span>  
 <span data-ttu-id="c18c2-220">*Iterator* funkce provede vlastní iterace nad kolekcí, jako je například seznam nebo pole.</span><span class="sxs-lookup"><span data-stu-id="c18c2-220">An *iterator* function performs a custom iteration over a collection, such as a list or array.</span></span> <span data-ttu-id="c18c2-221">Iterator funkce používá [Yield](yield-statement.md) příkaz vrátit každý element, jeden v čase.</span><span class="sxs-lookup"><span data-stu-id="c18c2-221">An iterator function uses the [Yield](yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="c18c2-222">Když [Yield](yield-statement.md) příkaz je dosaženo, uloží je aktuální umístění v kódu.</span><span class="sxs-lookup"><span data-stu-id="c18c2-222">When a [Yield](yield-statement.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="c18c2-223">Provádění restartování z tohoto umístění při příštím iterator funkce je volána.</span><span class="sxs-lookup"><span data-stu-id="c18c2-223">Execution is restarted from that location the next time the iterator function is called.</span></span>  
  
 <span data-ttu-id="c18c2-224">Volání iterovat z kódu klienta pomocí [For Each... Další](for-each-next-statement.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="c18c2-224">You call an iterator from client code by using a [For Each…Next](for-each-next-statement.md) statement.</span></span>  
  
 <span data-ttu-id="c18c2-225">Návratový typ funkce iterator může být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, nebo <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="c18c2-225">The return type of an iterator function can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="c18c2-226">Další informace najdete v tématu [iterátory](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="c18c2-226">For more information, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c18c2-227">Příklad</span><span class="sxs-lookup"><span data-stu-id="c18c2-227">Example</span></span>  
 <span data-ttu-id="c18c2-228">Následující příklad používá `Function` příkaz deklarovat název, parametry a kód, který vytvoří text `Function` postupu.</span><span class="sxs-lookup"><span data-stu-id="c18c2-228">The following example uses the `Function` statement to declare the name, parameters, and code that form the body of a `Function` procedure.</span></span> <span data-ttu-id="c18c2-229">`ParamArray` Modifikátor umožňuje funkci tak, aby přijímal proměnný počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="c18c2-229">The `ParamArray` modifier enables the function to accept a variable number of arguments.</span></span>  
  
 [!code-vb[VbVbalrStatements#25](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="c18c2-230">Příklad</span><span class="sxs-lookup"><span data-stu-id="c18c2-230">Example</span></span>  
 <span data-ttu-id="c18c2-231">Následující příklad popisuje vyvolání funkce deklarované v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c18c2-231">The following example invokes the function declared in the preceding example.</span></span>  
  
 [!code-vb[VbVbalrStatements#26](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="c18c2-232">Příklad</span><span class="sxs-lookup"><span data-stu-id="c18c2-232">Example</span></span>  
 <span data-ttu-id="c18c2-233">V následujícím příkladu `DelayAsync` je `Async``Function` s návratovým typem <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="c18c2-233">In the following example, `DelayAsync` is an `Async``Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="c18c2-234">`DelayAsync`má `Return` příkaz, který vrátí celé číslo.</span><span class="sxs-lookup"><span data-stu-id="c18c2-234">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="c18c2-235">Proto funkce deklaraci `DelayAsync` musí mít návratový typ `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="c18c2-235">Therefore the function declaration of `DelayAsync` needs to have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="c18c2-236">Vzhledem k tomu, že je návratový typ `Task(Of Integer)`, vyhodnocení `Await` výrazu v `DoSomethingAsync` vytváří celé číslo.</span><span class="sxs-lookup"><span data-stu-id="c18c2-236">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer.</span></span> <span data-ttu-id="c18c2-237">Tento postup je znázorněn v tomto prohlášení: `Dim result As Integer = Await delayTask`.</span><span class="sxs-lookup"><span data-stu-id="c18c2-237">This is demonstrated in this statement: `Dim result As Integer = Await delayTask`.</span></span>  
  
 <span data-ttu-id="c18c2-238">`startButton_Click` Postup je příklad `Async Sub` postupu.</span><span class="sxs-lookup"><span data-stu-id="c18c2-238">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="c18c2-239">Protože `DoSomethingAsync` je `Async` funkce, úlohy pro volání `DoSomethingAsync` musí být očekáváno, jak ukazuje následující příkaz: `Await DoSomethingAsync()`.</span><span class="sxs-lookup"><span data-stu-id="c18c2-239">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement demonstrates: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="c18c2-240">`startButton_Click``Sub` Postupu musí být definovány se `Async` modifikátor vzhledem k tomu, že má `Await` výrazu.</span><span class="sxs-lookup"><span data-stu-id="c18c2-240">The `startButton_Click``Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/function-statement_5.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c18c2-241">Viz také</span><span class="sxs-lookup"><span data-stu-id="c18c2-241">See Also</span></span>  
 [<span data-ttu-id="c18c2-242">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="c18c2-242">Sub Statement</span></span>](sub-statement.md)  
 [<span data-ttu-id="c18c2-243">Function – procedury</span><span class="sxs-lookup"><span data-stu-id="c18c2-243">Function Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)  
 [<span data-ttu-id="c18c2-244">Seznam parametrů</span><span class="sxs-lookup"><span data-stu-id="c18c2-244">Parameter List</span></span>](parameter-list.md)  
 [<span data-ttu-id="c18c2-245">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="c18c2-245">Dim Statement</span></span>](dim-statement.md)  
 [<span data-ttu-id="c18c2-246">Call – příkaz</span><span class="sxs-lookup"><span data-stu-id="c18c2-246">Call Statement</span></span>](call-statement.md)  
 [<span data-ttu-id="c18c2-247">Z</span><span class="sxs-lookup"><span data-stu-id="c18c2-247">Of</span></span>](of-clause.md)  
 [<span data-ttu-id="c18c2-248">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="c18c2-248">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)  
 [<span data-ttu-id="c18c2-249">Postupy: použití obecné třídy</span><span class="sxs-lookup"><span data-stu-id="c18c2-249">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [<span data-ttu-id="c18c2-250">Řešení potíží s procedurami</span><span class="sxs-lookup"><span data-stu-id="c18c2-250">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)  
 [<span data-ttu-id="c18c2-251">Lambda – výrazy</span><span class="sxs-lookup"><span data-stu-id="c18c2-251">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="c18c2-252">Function – výraz</span><span class="sxs-lookup"><span data-stu-id="c18c2-252">Function Expression</span></span>](../../../visual-basic/language-reference/operators/function-expression.md)
