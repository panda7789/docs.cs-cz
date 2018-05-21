---
title: Function – příkaz (Visual Basic)
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
ms.openlocfilehash: 908aa594ecbdd8ae2ec5a06de8181a1b16bb7e40
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
---
# <a name="function-statement-visual-basic"></a><span data-ttu-id="48854-102">Function – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48854-102">Function Statement (Visual Basic)</span></span>
<span data-ttu-id="48854-103">Deklaruje název, parametry a kód, který definovat `Function` postupu.</span><span class="sxs-lookup"><span data-stu-id="48854-103">Declares the name, parameters, and code that define a `Function` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48854-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48854-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]  
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Function ]  
    [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="48854-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="48854-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="48854-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="48854-106">Optional.</span></span> <span data-ttu-id="48854-107">V tématu [seznam atributů](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="48854-107">See [Attribute List](attribute-list.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="48854-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="48854-108">Optional.</span></span> <span data-ttu-id="48854-109">Může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="48854-109">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="48854-110">Public</span><span class="sxs-lookup"><span data-stu-id="48854-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="48854-111">Protected</span><span class="sxs-lookup"><span data-stu-id="48854-111">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="48854-112">Friend</span><span class="sxs-lookup"><span data-stu-id="48854-112">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="48854-113">Private</span><span class="sxs-lookup"><span data-stu-id="48854-113">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   [<span data-ttu-id="48854-114">Chráněné Friend</span><span class="sxs-lookup"><span data-stu-id="48854-114">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)

    - [<span data-ttu-id="48854-115">Privátní chráněný</span><span class="sxs-lookup"><span data-stu-id="48854-115">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)  
  
     <span data-ttu-id="48854-116">V tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="48854-116">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `proceduremodifiers`  
  
     <span data-ttu-id="48854-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="48854-117">Optional.</span></span> <span data-ttu-id="48854-118">Může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="48854-118">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="48854-119">Overloads</span><span class="sxs-lookup"><span data-stu-id="48854-119">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [<span data-ttu-id="48854-120">Overrides</span><span class="sxs-lookup"><span data-stu-id="48854-120">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [<span data-ttu-id="48854-121">Overridable</span><span class="sxs-lookup"><span data-stu-id="48854-121">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [<span data-ttu-id="48854-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="48854-122">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="48854-123">MustOverride</span><span class="sxs-lookup"><span data-stu-id="48854-123">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="48854-124">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="48854-124">Optional.</span></span> <span data-ttu-id="48854-125">V tématu [sdílené](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="48854-125">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="48854-126">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="48854-126">Optional.</span></span> <span data-ttu-id="48854-127">V tématu [stínů](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="48854-127">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `Async`  
  
     <span data-ttu-id="48854-128">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="48854-128">Optional.</span></span> <span data-ttu-id="48854-129">V tématu [asynchronní](../../../visual-basic/language-reference/modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="48854-129">See [Async](../../../visual-basic/language-reference/modifiers/async.md).</span></span>  
  
-   `Iterator`  
  
     <span data-ttu-id="48854-130">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="48854-130">Optional.</span></span> <span data-ttu-id="48854-131">V tématu [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="48854-131">See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="48854-132">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="48854-132">Required.</span></span> <span data-ttu-id="48854-133">Název procedury.</span><span class="sxs-lookup"><span data-stu-id="48854-133">Name of the procedure.</span></span> <span data-ttu-id="48854-134">V tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="48854-134">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `typeparamlist`  
  
     <span data-ttu-id="48854-135">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="48854-135">Optional.</span></span> <span data-ttu-id="48854-136">Seznam parametrů typu pro obecný postup.</span><span class="sxs-lookup"><span data-stu-id="48854-136">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="48854-137">V tématu [zadejte seznam](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="48854-137">See [Type List](type-list.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="48854-138">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="48854-138">Optional.</span></span> <span data-ttu-id="48854-139">Seznam místní názvy proměnných představující parametry tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="48854-139">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="48854-140">V tématu [seznam parametrů](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="48854-140">See [Parameter List](parameter-list.md).</span></span>  
  
-   `returntype`  
  
     <span data-ttu-id="48854-141">Požadováno pokud `Option Strict` je `On`.</span><span class="sxs-lookup"><span data-stu-id="48854-141">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="48854-142">Datový typ hodnoty vrácené tímto postupem.</span><span class="sxs-lookup"><span data-stu-id="48854-142">Data type of the value returned by this procedure.</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="48854-143">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="48854-143">Optional.</span></span> <span data-ttu-id="48854-144">Označuje, že tento postup implementuje jeden nebo více `Function` postupy, každé z nich definované v rozhraní implementované obsahující třídu nebo strukturu tento postup.</span><span class="sxs-lookup"><span data-stu-id="48854-144">Indicates that this procedure implements one or more `Function` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="48854-145">V tématu [implementuje příkaz](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="48854-145">See [Implements Statement](implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="48854-146">Požadováno pokud `Implements` pochází.</span><span class="sxs-lookup"><span data-stu-id="48854-146">Required if `Implements` is supplied.</span></span> <span data-ttu-id="48854-147">Seznam `Function` postupy se implementuje.</span><span class="sxs-lookup"><span data-stu-id="48854-147">List of `Function` procedures being implemented.</span></span>  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     <span data-ttu-id="48854-148">Každý `implementedprocedure` má následující syntaxe a částí:</span><span class="sxs-lookup"><span data-stu-id="48854-148">Each `implementedprocedure` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="48854-149">Část</span><span class="sxs-lookup"><span data-stu-id="48854-149">Part</span></span>|<span data-ttu-id="48854-150">Popis</span><span class="sxs-lookup"><span data-stu-id="48854-150">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="48854-151">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="48854-151">Required.</span></span> <span data-ttu-id="48854-152">Název rozhraní implementované tento postup obsahující třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="48854-152">Name of an interface implemented by this procedure's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="48854-153">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="48854-153">Required.</span></span> <span data-ttu-id="48854-154">Název, podle kterého postupu je definována v `interface`.</span><span class="sxs-lookup"><span data-stu-id="48854-154">Name by which the procedure is defined in `interface`.</span></span>|  
  
-   `Handles`  
  
     <span data-ttu-id="48854-155">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="48854-155">Optional.</span></span> <span data-ttu-id="48854-156">Označuje, že tento postup může zpracovat jeden nebo více konkrétní události.</span><span class="sxs-lookup"><span data-stu-id="48854-156">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="48854-157">V tématu [zpracovává](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="48854-157">See [Handles](handles-clause.md).</span></span>  
  
-   `eventlist`  
  
     <span data-ttu-id="48854-158">Požadováno pokud `Handles` pochází.</span><span class="sxs-lookup"><span data-stu-id="48854-158">Required if `Handles` is supplied.</span></span> <span data-ttu-id="48854-159">Seznam událostí, který zpracovává tento postup.</span><span class="sxs-lookup"><span data-stu-id="48854-159">List of events this procedure handles.</span></span>  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     <span data-ttu-id="48854-160">Každý `eventspecifier` má následující syntaxe a částí:</span><span class="sxs-lookup"><span data-stu-id="48854-160">Each `eventspecifier` has the following syntax and parts:</span></span>  
  
     `eventvariable.event`  
  
    |<span data-ttu-id="48854-161">Část</span><span class="sxs-lookup"><span data-stu-id="48854-161">Part</span></span>|<span data-ttu-id="48854-162">Popis</span><span class="sxs-lookup"><span data-stu-id="48854-162">Description</span></span>|  
    |---|---|  
    |`eventvariable`|<span data-ttu-id="48854-163">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="48854-163">Required.</span></span> <span data-ttu-id="48854-164">Objektová proměnná deklarovat s datový typ třídu nebo strukturu, která vyvolává událost.</span><span class="sxs-lookup"><span data-stu-id="48854-164">Object variable declared with the data type of the class or structure that raises the event.</span></span>|  
    |`event`|<span data-ttu-id="48854-165">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="48854-165">Required.</span></span> <span data-ttu-id="48854-166">Název události, který zpracovává tento postup.</span><span class="sxs-lookup"><span data-stu-id="48854-166">Name of the event this procedure handles.</span></span>|  
  
-   `statements`  
  
     <span data-ttu-id="48854-167">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="48854-167">Optional.</span></span> <span data-ttu-id="48854-168">Blok příkazů k provedení v rámci tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="48854-168">Block of statements to be executed within this procedure.</span></span>  
  
-   `End Function`  
  
     <span data-ttu-id="48854-169">Ukončí definici tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="48854-169">Terminates the definition of this procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48854-170">Poznámky</span><span class="sxs-lookup"><span data-stu-id="48854-170">Remarks</span></span>  
 <span data-ttu-id="48854-171">Všechny spustitelný kód musí být uvnitř procedury.</span><span class="sxs-lookup"><span data-stu-id="48854-171">All executable code must be inside a procedure.</span></span> <span data-ttu-id="48854-172">Každý postup je pak deklarované v rámci třídy, struktury nebo modul, který se označuje jako obsahující třídy, struktury nebo modul.</span><span class="sxs-lookup"><span data-stu-id="48854-172">Each procedure, in turn, is declared within a class, a structure, or a module that is referred to as the containing class, structure, or module.</span></span>  
  
 <span data-ttu-id="48854-173">Chcete-li vrátit hodnotu volání kódu, použijte `Function` postupu; jinak použijte `Sub` postup.</span><span class="sxs-lookup"><span data-stu-id="48854-173">To return a value to the calling code, use a `Function` procedure; otherwise, use a `Sub` procedure.</span></span>  
  
## <a name="defining-a-function"></a><span data-ttu-id="48854-174">Definování funkcí</span><span class="sxs-lookup"><span data-stu-id="48854-174">Defining a Function</span></span>  
 <span data-ttu-id="48854-175">Můžete definovat `Function` postup jenom na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="48854-175">You can define a `Function` procedure only at the module level.</span></span> <span data-ttu-id="48854-176">Kontext deklarace pro funkci proto musí být třídy, struktury, modul nebo rozhraní a nemůže být zdrojový soubor, obor názvů, procedury nebo blok.</span><span class="sxs-lookup"><span data-stu-id="48854-176">Therefore, the declaration context for a function must be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="48854-177">Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="48854-177">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="48854-178">`Function` Výchozí nastavení postupy veřejný přístup.</span><span class="sxs-lookup"><span data-stu-id="48854-178">`Function` procedures default to public access.</span></span> <span data-ttu-id="48854-179">Můžete nastavit jejich úrovně přístupu s modifikátory přístupu.</span><span class="sxs-lookup"><span data-stu-id="48854-179">You can adjust their access levels with the access modifiers.</span></span>  
  
 <span data-ttu-id="48854-180">A `Function` postupu můžou deklarovat datový typ hodnoty, která vrátí postupu.</span><span class="sxs-lookup"><span data-stu-id="48854-180">A `Function` procedure can declare the data type of the value that the procedure returns.</span></span> <span data-ttu-id="48854-181">Můžete zadat jakýkoli datový typ nebo název výčet, struktury, třídu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="48854-181">You can specify any data type or the name of an enumeration, a structure, a class, or an interface.</span></span> <span data-ttu-id="48854-182">Pokud nezadáte `returntype` vrátí parametr postupu `Object`.</span><span class="sxs-lookup"><span data-stu-id="48854-182">If you don't specify the `returntype` parameter, the procedure returns `Object`.</span></span>  
  
 <span data-ttu-id="48854-183">Pokud tento postup používá `Implements` – klíčové slovo, obsahující třídu nebo strukturu musí také mít `Implements` příkaz, který následuje jeho `Class` nebo `Structure` příkaz.</span><span class="sxs-lookup"><span data-stu-id="48854-183">If this procedure uses the `Implements` keyword, the containing class or structure must also have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="48854-184">`Implements` Příkaz musí zahrnovat každé rozhraní, který je uveden v `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="48854-184">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="48854-185">Ale název, podle kterého rozhraní definuje `Function` (v `definedname`) nemusí odpovídat názvu tohoto postupu (v `name`).</span><span class="sxs-lookup"><span data-stu-id="48854-185">However, the name by which an interface defines the `Function` (in `definedname`) doesn't need to match the name of this procedure (in `name`).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="48854-186">Lambda – výrazy můžete použít k definování vložené výrazy funkce.</span><span class="sxs-lookup"><span data-stu-id="48854-186">You can use lambda expressions to define function expressions inline.</span></span> <span data-ttu-id="48854-187">Další informace najdete v tématu [výraz funkce](../../../visual-basic/language-reference/operators/function-expression.md) a [výrazy Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="48854-187">For more information, see [Function Expression](../../../visual-basic/language-reference/operators/function-expression.md) and [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
## <a name="returning-from-a-function"></a><span data-ttu-id="48854-188">Vrácení z funkce</span><span class="sxs-lookup"><span data-stu-id="48854-188">Returning from a Function</span></span>  
 <span data-ttu-id="48854-189">Když `Function` postup vrátí kód volání, pokračuje provádění příkaz, který následuje příkaz, který volá postup.</span><span class="sxs-lookup"><span data-stu-id="48854-189">When the `Function` procedure returns to the calling code, execution continues with the statement that follows the statement that called the procedure.</span></span>  
  
 <span data-ttu-id="48854-190">Vrácení hodnoty z funkce, můžete přiřadit hodnotu název funkce nebo ji v zahrnout `Return` příkaz.</span><span class="sxs-lookup"><span data-stu-id="48854-190">To return a value from a function, you can either assign the value to the function name or include it in a `Return` statement.</span></span>  
  
 <span data-ttu-id="48854-191">`Return` Příkaz současně přiřadí návratovou hodnotu a ukončí funkce, jako ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="48854-191">The `Return` statement simultaneously assigns the return value and exits the function, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_1.vb)]  
  
 <span data-ttu-id="48854-192">Následující příklad přiřadí návratovou hodnotu pro název funkce `myFunction` a použije je `Exit Function` příkaz, který má vrátit.</span><span class="sxs-lookup"><span data-stu-id="48854-192">The following example assigns the return value to the function name `myFunction` and then uses the `Exit Function` statement to return.</span></span>  
  
 [!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_2.vb)]  
  
 <span data-ttu-id="48854-193">`Exit Function` a `Return` příkazy způsobit okamžitou výstupu z `Function` postupu.</span><span class="sxs-lookup"><span data-stu-id="48854-193">The `Exit Function` and `Return` statements cause an immediate exit from a `Function` procedure.</span></span> <span data-ttu-id="48854-194">Libovolný počet `Exit Function` a `Return` příkazy může vyskytovat kdekoli v postupu, a je možné kombinovat `Exit Function` a `Return` příkazy.</span><span class="sxs-lookup"><span data-stu-id="48854-194">Any number of `Exit Function` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Function` and `Return` statements.</span></span>  
  
 <span data-ttu-id="48854-195">Pokud používáte `Exit Function` bez přiřazení hodnoty k `name`, vrátí výchozí hodnota pro datový typ, který je uveden v postupu `returntype`.</span><span class="sxs-lookup"><span data-stu-id="48854-195">If you use `Exit Function` without assigning a value to `name`, the procedure returns the default value for the data type that's specified in `returntype`.</span></span> <span data-ttu-id="48854-196">Pokud `returntype` není zadán, vrátí postup `Nothing`, což je výchozí hodnota pro `Object`.</span><span class="sxs-lookup"><span data-stu-id="48854-196">If `returntype` isn't specified, the procedure returns `Nothing`, which is the default value for `Object`.</span></span>  
  
## <a name="calling-a-function"></a><span data-ttu-id="48854-197">Volání funkce</span><span class="sxs-lookup"><span data-stu-id="48854-197">Calling a Function</span></span>  
 <span data-ttu-id="48854-198">Volání `Function` postup pomocí název postupu, za nímž následuje seznam argumentů v závorkách ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="48854-198">You call a `Function` procedure by using the procedure name, followed by the argument list in parentheses, in an expression.</span></span> <span data-ttu-id="48854-199">Závorky můžete vynechat, pouze v případě, že nejsou zadávání žádné argumenty.</span><span class="sxs-lookup"><span data-stu-id="48854-199">You can omit the parentheses only if you aren't supplying any arguments.</span></span> <span data-ttu-id="48854-200">Váš kód je však lépe čitelný, pokud vždy zahrnovat závorkách.</span><span class="sxs-lookup"><span data-stu-id="48854-200">However, your code is more readable if you always include the parentheses.</span></span>  
  
 <span data-ttu-id="48854-201">Volání `Function` postup volat žádnou knihovnu stejným způsobem jako funkce, jako `Sqrt`, `Cos`, nebo `ChrW`.</span><span class="sxs-lookup"><span data-stu-id="48854-201">You call a `Function` procedure the same way that you call any library function such as `Sqrt`, `Cos`, or `ChrW`.</span></span>  
  
 <span data-ttu-id="48854-202">Můžete také zavolat funkci pomocí `Call` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="48854-202">You can also call a function by using the `Call` keyword.</span></span> <span data-ttu-id="48854-203">V takovém případě se ignoruje návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="48854-203">In that case, the return value is ignored.</span></span> <span data-ttu-id="48854-204">Použití `Call` ve většině případů se nedoporučuje – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="48854-204">Use of the `Call` keyword isn't recommended in most cases.</span></span> <span data-ttu-id="48854-205">Další informace najdete v tématu [volání příkazu](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="48854-205">For more information, see [Call Statement](call-statement.md).</span></span>  
  
 <span data-ttu-id="48854-206">Visual Basic někdy Přeuspořádá aritmetických výrazech ke zvýšení efektivity interní.</span><span class="sxs-lookup"><span data-stu-id="48854-206">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="48854-207">Z tohoto důvodu byste neměli používat `Function` postup ve výrazu aritmetické při změně hodnot proměnných ve stejném výrazu funkce.</span><span class="sxs-lookup"><span data-stu-id="48854-207">For that reason, you shouldn't use a `Function` procedure in an arithmetic expression when the function changes the value of variables in the same expression.</span></span>  
  
## <a name="async-functions"></a><span data-ttu-id="48854-208">Asynchronní funkce</span><span class="sxs-lookup"><span data-stu-id="48854-208">Async Functions</span></span>  
 <span data-ttu-id="48854-209">*Asynchronní* funkce umožňuje vyvolání asynchronní funkce bez použití explicitní zpětná volání nebo Ruční rozdělení kódu napříč více funkcí nebo výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="48854-209">The *Async* feature allows you to invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>  
  
 <span data-ttu-id="48854-210">Pokud označíte funkce s [asynchronní](../../../visual-basic/language-reference/modifiers/async.md) modifikátor, můžete použít [Await](../../../visual-basic/language-reference/operators/await-operator.md) operátor ve funkci.</span><span class="sxs-lookup"><span data-stu-id="48854-210">If you mark a function with the [Async](../../../visual-basic/language-reference/modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the function.</span></span> <span data-ttu-id="48854-211">Při řízení dosáhnou `Await` výrazu v `Async` funkce, vrátí ovládací prvek volajícímu a průběh ve funkci je pozastaveno, dokud dokončení awaited úlohy.</span><span class="sxs-lookup"><span data-stu-id="48854-211">When control reaches an `Await` expression in the `Async` function, control returns to the caller, and progress in the function is suspended until the awaited task completes.</span></span> <span data-ttu-id="48854-212">Po dokončení úlohy můžete pokračovat v provádění ve funkci.</span><span class="sxs-lookup"><span data-stu-id="48854-212">When the task is complete, execution can resume in the function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="48854-213">`Async` Postup vrátí volajícímu při buď zjistí první awaited objekt, který ještě není dokončena nebo získá na konec `Async` postup, cokoliv nastane dříve.</span><span class="sxs-lookup"><span data-stu-id="48854-213">An `Async` procedure returns to the caller when either it encounters the first awaited object that’s not yet complete, or it gets to the end of the `Async` procedure, whichever occurs first.</span></span>  
  
 <span data-ttu-id="48854-214">`Async` Funkce může mít návratový typ <xref:System.Threading.Tasks.Task%601> nebo <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="48854-214">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="48854-215">Příklad `Async` funkce, která má návratový typ <xref:System.Threading.Tasks.Task%601> najdete níže.</span><span class="sxs-lookup"><span data-stu-id="48854-215">An example of an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601> is provided below.</span></span>  
  
 <span data-ttu-id="48854-216">`Async` Funkce nelze deklarovat všechny [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parametry.</span><span class="sxs-lookup"><span data-stu-id="48854-216">An `Async` function cannot declare any [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parameters.</span></span>  
  
 <span data-ttu-id="48854-217">A [Sub – příkaz](sub-statement.md) může také být označen `Async` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="48854-217">A [Sub Statement](sub-statement.md) can also be marked with the `Async` modifier.</span></span> <span data-ttu-id="48854-218">Především používá se pro obslužné rutiny událostí, kde nejde vrátit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="48854-218">This is primarily used for event handlers, where a value cannot be returned.</span></span> <span data-ttu-id="48854-219">`Async``Sub` Procedury nelze očekáváno a volající `Async``Sub` procedury nelze catch výjimky, které jsou vyvolány `Sub` postupu.</span><span class="sxs-lookup"><span data-stu-id="48854-219">An `Async``Sub` procedure can't be awaited, and the caller of an `Async``Sub` procedure can't catch exceptions that are thrown by the `Sub` procedure.</span></span>  
  
 <span data-ttu-id="48854-220">Další informace o `Async` funkce, najdete v části [asynchronní programování s Async a Await](../../../visual-basic/programming-guide/concepts/async/index.md), [řízení toku v asynchronních programech](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), a [asynchronní vrátit typy](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="48854-220">For more information about `Async` functions, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="iterator-functions"></a><span data-ttu-id="48854-221">Iterator funkce</span><span class="sxs-lookup"><span data-stu-id="48854-221">Iterator Functions</span></span>  
 <span data-ttu-id="48854-222">*Iterator* funkce provede vlastní iterace nad kolekcí, jako je například seznam nebo pole.</span><span class="sxs-lookup"><span data-stu-id="48854-222">An *iterator* function performs a custom iteration over a collection, such as a list or array.</span></span> <span data-ttu-id="48854-223">Iterator funkce používá [Yield](yield-statement.md) příkaz vrátit každý element, jeden v čase.</span><span class="sxs-lookup"><span data-stu-id="48854-223">An iterator function uses the [Yield](yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="48854-224">Když [Yield](yield-statement.md) příkaz je dosaženo, uloží je aktuální umístění v kódu.</span><span class="sxs-lookup"><span data-stu-id="48854-224">When a [Yield](yield-statement.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="48854-225">Provádění restartování z tohoto umístění při příštím iterator funkce je volána.</span><span class="sxs-lookup"><span data-stu-id="48854-225">Execution is restarted from that location the next time the iterator function is called.</span></span>  
  
 <span data-ttu-id="48854-226">Volání iterovat z kódu klienta pomocí [For Each... Další](for-each-next-statement.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="48854-226">You call an iterator from client code by using a [For Each…Next](for-each-next-statement.md) statement.</span></span>  
  
 <span data-ttu-id="48854-227">Návratový typ funkce iterator může být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, nebo <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="48854-227">The return type of an iterator function can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="48854-228">Další informace najdete v tématu [iterátory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="48854-228">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="48854-229">Příklad</span><span class="sxs-lookup"><span data-stu-id="48854-229">Example</span></span>  
 <span data-ttu-id="48854-230">Následující příklad používá `Function` příkaz deklarovat název, parametry a kód, který vytvoří text `Function` postupu.</span><span class="sxs-lookup"><span data-stu-id="48854-230">The following example uses the `Function` statement to declare the name, parameters, and code that form the body of a `Function` procedure.</span></span> <span data-ttu-id="48854-231">`ParamArray` Modifikátor umožňuje funkci tak, aby přijímal proměnný počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="48854-231">The `ParamArray` modifier enables the function to accept a variable number of arguments.</span></span>  
  
 [!code-vb[VbVbalrStatements#25](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="48854-232">Příklad</span><span class="sxs-lookup"><span data-stu-id="48854-232">Example</span></span>  
 <span data-ttu-id="48854-233">Následující příklad popisuje vyvolání funkce deklarované v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="48854-233">The following example invokes the function declared in the preceding example.</span></span>  
  
 [!code-vb[VbVbalrStatements#26](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="48854-234">Příklad</span><span class="sxs-lookup"><span data-stu-id="48854-234">Example</span></span>  
 <span data-ttu-id="48854-235">V následujícím příkladu `DelayAsync` je `Async``Function` s návratovým typem <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="48854-235">In the following example, `DelayAsync` is an `Async``Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="48854-236">`DelayAsync` má `Return` příkaz, který vrátí celé číslo.</span><span class="sxs-lookup"><span data-stu-id="48854-236">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="48854-237">Proto funkce deklaraci `DelayAsync` musí mít návratový typ `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="48854-237">Therefore the function declaration of `DelayAsync` needs to have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="48854-238">Vzhledem k tomu, že je návratový typ `Task(Of Integer)`, vyhodnocení `Await` výrazu v `DoSomethingAsync` vytváří celé číslo.</span><span class="sxs-lookup"><span data-stu-id="48854-238">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer.</span></span> <span data-ttu-id="48854-239">Tento postup je znázorněn v tomto prohlášení: `Dim result As Integer = Await delayTask`.</span><span class="sxs-lookup"><span data-stu-id="48854-239">This is demonstrated in this statement: `Dim result As Integer = Await delayTask`.</span></span>  
  
 <span data-ttu-id="48854-240">`startButton_Click` Postup je příklad `Async Sub` postupu.</span><span class="sxs-lookup"><span data-stu-id="48854-240">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="48854-241">Protože `DoSomethingAsync` je `Async` funkce, úlohy pro volání `DoSomethingAsync` musí být očekáváno, jak ukazuje následující příkaz: `Await DoSomethingAsync()`.</span><span class="sxs-lookup"><span data-stu-id="48854-241">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement demonstrates: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="48854-242">`startButton_Click``Sub` Postupu musí být definovány se `Async` modifikátor vzhledem k tomu, že má `Await` výrazu.</span><span class="sxs-lookup"><span data-stu-id="48854-242">The `startButton_Click``Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/function-statement_5.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="48854-243">Viz také</span><span class="sxs-lookup"><span data-stu-id="48854-243">See Also</span></span>  
 [<span data-ttu-id="48854-244">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="48854-244">Sub Statement</span></span>](sub-statement.md)  
 [<span data-ttu-id="48854-245">Procedury funkce</span><span class="sxs-lookup"><span data-stu-id="48854-245">Function Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)  
 [<span data-ttu-id="48854-246">Seznam parametrů</span><span class="sxs-lookup"><span data-stu-id="48854-246">Parameter List</span></span>](parameter-list.md)  
 [<span data-ttu-id="48854-247">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="48854-247">Dim Statement</span></span>](dim-statement.md)  
 [<span data-ttu-id="48854-248">Příkaz Call</span><span class="sxs-lookup"><span data-stu-id="48854-248">Call Statement</span></span>](call-statement.md)  
 [<span data-ttu-id="48854-249">z</span><span class="sxs-lookup"><span data-stu-id="48854-249">Of</span></span>](of-clause.md)  
 [<span data-ttu-id="48854-250">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="48854-250">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)  
 [<span data-ttu-id="48854-251">Postupy: Použití obecné třídy</span><span class="sxs-lookup"><span data-stu-id="48854-251">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [<span data-ttu-id="48854-252">Řešení potíží s procedurami</span><span class="sxs-lookup"><span data-stu-id="48854-252">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)  
 [<span data-ttu-id="48854-253">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="48854-253">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="48854-254">Výraz Function</span><span class="sxs-lookup"><span data-stu-id="48854-254">Function Expression</span></span>](../../../visual-basic/language-reference/operators/function-expression.md)
