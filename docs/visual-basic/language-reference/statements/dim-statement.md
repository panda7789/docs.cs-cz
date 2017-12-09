---
title: "Dim – příkaz (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Dim
- Dim
helpviewer_keywords:
- Public keyword [Visual Basic], in Dim statement
- Dim statement [Visual Basic]
- fixed-length strings [Visual Basic], declaring
- variables [Visual Basic], declaring
- WithEvents keyword [Visual Basic], Dim statement
- dynamic arrays [Visual Basic], Dim statement
- variables [Visual Basic], initializing
- '{} braces'
- fields [Visual Basic], as member variables
- declarations [Visual Basic], dynamic arrays
- member variables [Visual Basic]
- default values [Visual Basic]
- data types [Visual Basic], assigning
- braces {}
- As keyword [Visual Basic], in Dim statement
- arrays [Visual Basic], declaring
- New keyword [Visual Basic], Dim statement
- To keyword [Visual Basic], in Dim statement
- storage [Visual Basic], allocating
- local variables [Visual Basic]
- declaration statements [Visual Basic]
- Dim statement [Visual Basic], syntax
- variables [Visual Basic], member and local
ms.assetid: fae3eca1-f0b2-4400-994b-7aa58a848448
caps.latest.revision: "72"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a428f8be7b62600ca8fffd3160039c1de911e34e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="dim-statement-visual-basic"></a><span data-ttu-id="485c0-102">Dim – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="485c0-102">Dim Statement (Visual Basic)</span></span>
<span data-ttu-id="485c0-103">Deklaruje a přidělí prostor úložiště pro jeden nebo více proměnných.</span><span class="sxs-lookup"><span data-stu-id="485c0-103">Declares and allocates storage space for one or more variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="485c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="485c0-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]   
Dim [ WithEvents ] variablelist  
```  
  
## <a name="parts"></a><span data-ttu-id="485c0-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="485c0-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="485c0-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="485c0-106">Optional.</span></span> <span data-ttu-id="485c0-107">V tématu [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="485c0-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="485c0-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="485c0-108">Optional.</span></span> <span data-ttu-id="485c0-109">Může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="485c0-109">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="485c0-110">Veřejné</span><span class="sxs-lookup"><span data-stu-id="485c0-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="485c0-111">Chráněný</span><span class="sxs-lookup"><span data-stu-id="485c0-111">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="485c0-112">Friend</span><span class="sxs-lookup"><span data-stu-id="485c0-112">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="485c0-113">Privátní</span><span class="sxs-lookup"><span data-stu-id="485c0-113">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     <span data-ttu-id="485c0-114">V tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="485c0-114">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `Shared`  
  
     <span data-ttu-id="485c0-115">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="485c0-115">Optional.</span></span> <span data-ttu-id="485c0-116">V tématu [sdílené](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="485c0-116">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="485c0-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="485c0-117">Optional.</span></span> <span data-ttu-id="485c0-118">V tématu [stínů](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="485c0-118">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `Static`  
  
     <span data-ttu-id="485c0-119">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="485c0-119">Optional.</span></span> <span data-ttu-id="485c0-120">V tématu [statické](../../../visual-basic/language-reference/modifiers/static.md).</span><span class="sxs-lookup"><span data-stu-id="485c0-120">See [Static](../../../visual-basic/language-reference/modifiers/static.md).</span></span>  
  
-   `ReadOnly`  
  
     <span data-ttu-id="485c0-121">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="485c0-121">Optional.</span></span> <span data-ttu-id="485c0-122">V tématu [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="485c0-122">See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
-   `WithEvents`  
  
     <span data-ttu-id="485c0-123">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="485c0-123">Optional.</span></span> <span data-ttu-id="485c0-124">Určuje, že jsou objektové proměnné, které odkazují na instancí třídy, který může vyvolat události.</span><span class="sxs-lookup"><span data-stu-id="485c0-124">Specifies that these are object variables that refer to instances of a class that can raise events.</span></span> <span data-ttu-id="485c0-125">V tématu [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).</span><span class="sxs-lookup"><span data-stu-id="485c0-125">See [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).</span></span>  
  
-   `variablelist`  
  
     <span data-ttu-id="485c0-126">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="485c0-126">Required.</span></span> <span data-ttu-id="485c0-127">Seznam proměnných se deklarovaných v tomto příkazu.</span><span class="sxs-lookup"><span data-stu-id="485c0-127">List of variables being declared in this statement.</span></span>  
  
     `variable [ , variable ... ]`  
  
     <span data-ttu-id="485c0-128">Každý `variable` má následující syntaxe a částí:</span><span class="sxs-lookup"><span data-stu-id="485c0-128">Each `variable` has the following syntax and parts:</span></span>  
  
     <span data-ttu-id="485c0-129">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="485c0-129">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span></span>  
  
    |<span data-ttu-id="485c0-130">Část</span><span class="sxs-lookup"><span data-stu-id="485c0-130">Part</span></span>|<span data-ttu-id="485c0-131">Popis</span><span class="sxs-lookup"><span data-stu-id="485c0-131">Description</span></span>|  
    |---|---|  
    |`variablename`|<span data-ttu-id="485c0-132">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="485c0-132">Required.</span></span> <span data-ttu-id="485c0-133">Název proměnné.</span><span class="sxs-lookup"><span data-stu-id="485c0-133">Name of the variable.</span></span> <span data-ttu-id="485c0-134">V tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="485c0-134">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
    |`boundslist`|<span data-ttu-id="485c0-135">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="485c0-135">Optional.</span></span> <span data-ttu-id="485c0-136">Seznam mezí Každá dimenze proměnná typu pole.</span><span class="sxs-lookup"><span data-stu-id="485c0-136">List of bounds of each dimension of an array variable.</span></span>|  
    |`New`|<span data-ttu-id="485c0-137">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="485c0-137">Optional.</span></span> <span data-ttu-id="485c0-138">Vytvoří novou instanci třídy, když `Dim` příkaz spustí.</span><span class="sxs-lookup"><span data-stu-id="485c0-138">Creates a new instance of the class when the `Dim` statement runs.</span></span>|  
    |`datatype`|<span data-ttu-id="485c0-139">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="485c0-139">Optional.</span></span> <span data-ttu-id="485c0-140">Datový typ proměnné.</span><span class="sxs-lookup"><span data-stu-id="485c0-140">Data type of the variable.</span></span>|  
    |`With`|<span data-ttu-id="485c0-141">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="485c0-141">Optional.</span></span> <span data-ttu-id="485c0-142">Představuje seznam inicializátoru objektu.</span><span class="sxs-lookup"><span data-stu-id="485c0-142">Introduces the object initializer list.</span></span>|  
    |`propertyname`|<span data-ttu-id="485c0-143">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="485c0-143">Optional.</span></span> <span data-ttu-id="485c0-144">Název vlastnosti ve třídě provádíte instanci.</span><span class="sxs-lookup"><span data-stu-id="485c0-144">The name of a property in the class you are making an instance of.</span></span>|  
    |`propinitializer`|<span data-ttu-id="485c0-145">Požadované po `propertyname` =.</span><span class="sxs-lookup"><span data-stu-id="485c0-145">Required after `propertyname` =.</span></span> <span data-ttu-id="485c0-146">Výraz, který se vyhodnotí a přiřadí název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="485c0-146">The expression that is evaluated and assigned to the property name.</span></span>|  
    |`initializer`|<span data-ttu-id="485c0-147">Nepovinný, pokud `New` není zadán.</span><span class="sxs-lookup"><span data-stu-id="485c0-147">Optional if `New` is not specified.</span></span> <span data-ttu-id="485c0-148">Výraz, který se vyhodnotí a přiřadí do proměnné při jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="485c0-148">Expression that is evaluated and assigned to the variable when it is created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="485c0-149">Poznámky</span><span class="sxs-lookup"><span data-stu-id="485c0-149">Remarks</span></span>  
 <span data-ttu-id="485c0-150">Visual Basic – kompilátor používá `Dim` příkaz k určení typu dat proměnné a další informace, například jaké kódu mají přístup k proměnné.</span><span class="sxs-lookup"><span data-stu-id="485c0-150">The Visual Basic compiler uses the `Dim` statement to determine the variable's data type and other information, such as what code can access the variable.</span></span> <span data-ttu-id="485c0-151">Následující příklad deklaruje proměnnou pro uložení `Integer` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="485c0-151">The following example declares a variable to hold an `Integer` value.</span></span>  
  
```vb  
Dim numberOfStudents As Integer  
```  
  
 <span data-ttu-id="485c0-152">Můžete zadat jakýkoli datový typ nebo název výčtu, struktura, třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="485c0-152">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
```vb  
Dim finished As Boolean  
Dim monitorBox As System.Windows.Forms.Form  
```  
  
 <span data-ttu-id="485c0-153">Pro odkaz na typ, můžete použít `New` – klíčové slovo vytvořit novou instanci třídy nebo struktury, která je zadána datového typu.</span><span class="sxs-lookup"><span data-stu-id="485c0-153">For a reference type, you use the `New` keyword to create a new instance of the class or structure that is specified by the data type.</span></span> <span data-ttu-id="485c0-154">Pokud používáte `New`, nepoužívejte inicializátoru výrazu.</span><span class="sxs-lookup"><span data-stu-id="485c0-154">If you use `New`, you do not use an initializer expression.</span></span> <span data-ttu-id="485c0-155">Místo toho zadáte argumenty, pokud jsou požadována konstruktoru třídy, ze kterého jsou vytváření proměnné.</span><span class="sxs-lookup"><span data-stu-id="485c0-155">Instead, you supply arguments, if they are required, to the constructor of the class from which you are creating the variable.</span></span>  
  
```vb  
Dim bottomLabel As New System.Windows.Forms.Label  
```  
  
 <span data-ttu-id="485c0-156">Je možné deklarovat proměnnou v postupu, blok, třída, struktura nebo modul.</span><span class="sxs-lookup"><span data-stu-id="485c0-156">You can declare a variable in a procedure, block, class, structure, or module.</span></span> <span data-ttu-id="485c0-157">Nelze deklarovat proměnnou v zdrojový soubor, obor názvů nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="485c0-157">You cannot declare a variable in a source file, namespace, or interface.</span></span> <span data-ttu-id="485c0-158">Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="485c0-158">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="485c0-159">Proměnné, která je deklarovaná na úrovni modulu mimo libovolná procedura je *členské proměnné* nebo *pole*.</span><span class="sxs-lookup"><span data-stu-id="485c0-159">A variable that is declared at module level, outside any procedure, is a *member variable* or *field*.</span></span> <span data-ttu-id="485c0-160">Členské proměnné jsou v oboru v rámci své třídy, struktury nebo modul.</span><span class="sxs-lookup"><span data-stu-id="485c0-160">Member variables are in scope throughout their class, structure, or module.</span></span> <span data-ttu-id="485c0-161">Proměnné, která je deklarovaná na úrovni postup je *místní proměnné*.</span><span class="sxs-lookup"><span data-stu-id="485c0-161">A variable that is declared at procedure level is a *local variable*.</span></span> <span data-ttu-id="485c0-162">Jsou místní proměnné v oboru pouze v rámci postupu nebo bloku.</span><span class="sxs-lookup"><span data-stu-id="485c0-162">Local variables are in scope only within their procedure or block.</span></span>  
  
 <span data-ttu-id="485c0-163">Následující modifikátory přístupu slouží k deklarujte proměnné mimo proceduru: `Public`, `Protected`, `Friend`, `Protected Friend`, a `Private`.</span><span class="sxs-lookup"><span data-stu-id="485c0-163">The following access modifiers are used to declare variables outside a procedure: `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private`.</span></span> <span data-ttu-id="485c0-164">Další informace najdete v tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="485c0-164">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="485c0-165">`Dim` – Klíčové slovo je volitelný a obvykle vynechána, pokud je zadána některá z následujících modifikátory: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, nebo `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="485c0-165">The `Dim` keyword is optional and usually omitted if you specify any of the following modifiers: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, or `WithEvents`.</span></span>  
  
```vb  
Public maximumAllowed As Double  
Protected Friend currentUserName As String  
Private salary As Decimal  
Static runningTotal As Integer  
```  
  
 <span data-ttu-id="485c0-166">Pokud `Option Explicit` je na (výchozí), vyžaduje kompilátor deklaraci pro každou proměnnou můžete použít.</span><span class="sxs-lookup"><span data-stu-id="485c0-166">If `Option Explicit` is on (the default), the compiler requires a declaration for every variable you use.</span></span> <span data-ttu-id="485c0-167">Další informace najdete v tématu [Option Explicit – příkaz](../../../visual-basic/language-reference/statements/option-explicit-statement.md).</span><span class="sxs-lookup"><span data-stu-id="485c0-167">For more information, see [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md).</span></span>  
  
## <a name="specifying-an-initial-value"></a><span data-ttu-id="485c0-168">Pokud zadáte počáteční hodnotu</span><span class="sxs-lookup"><span data-stu-id="485c0-168">Specifying an Initial Value</span></span>  
 <span data-ttu-id="485c0-169">Při vytvoření, můžete přiřadit hodnotu proměnné.</span><span class="sxs-lookup"><span data-stu-id="485c0-169">You can assign a value to a variable when it is created.</span></span> <span data-ttu-id="485c0-170">Pro typ hodnoty, můžete použít *inicializátoru* k poskytování výraz pro přiřazení k proměnné.</span><span class="sxs-lookup"><span data-stu-id="485c0-170">For a value type, you use an *initializer* to supply an expression to be assigned to the variable.</span></span> <span data-ttu-id="485c0-171">Výsledkem výrazu musí být konstanta, která lze vypočítat v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="485c0-171">The expression must evaluate to a constant that can be calculated at compile time.</span></span>  
  
```vb  
Dim quantity As Integer = 10  
Dim message As String = "Just started"  
```  
  
 <span data-ttu-id="485c0-172">Pokud je zadán inicializátoru a datový typ není zadán `As` klauzuli *odvození typu* se používá k odvození typu dat z inicializátoru.</span><span class="sxs-lookup"><span data-stu-id="485c0-172">If an initializer is specified and a data type is not specified in an `As` clause, *type inference* is used to infer the data type from the initializer.</span></span> <span data-ttu-id="485c0-173">V následujícím příkladu obě `num1` a `num2` jsou silného typu jako celá čísla.</span><span class="sxs-lookup"><span data-stu-id="485c0-173">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span> <span data-ttu-id="485c0-174">V druhé deklaraci odvození typu odvodí typ z hodnotu 3.</span><span class="sxs-lookup"><span data-stu-id="485c0-174">In the second declaration, type inference infers the type from the value 3.</span></span>  
  
```vb  
' Use explicit typing.  
Dim num1 As Integer = 3  
  
' Use local type inference.  
Dim num2 = 3  
```  
  
 <span data-ttu-id="485c0-175">Odvození typu se vztahuje na úrovni postupu.</span><span class="sxs-lookup"><span data-stu-id="485c0-175">Type inference applies at the procedure level.</span></span> <span data-ttu-id="485c0-176">Nevztahuje se mimo proceduru v třída, struktura, modulu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="485c0-176">It does not apply outside a procedure in a class, structure, module, or interface.</span></span> <span data-ttu-id="485c0-177">Další informace o odvození typu najdete v tématu [Option Infer – příkaz](../../../visual-basic/language-reference/statements/option-infer-statement.md) a [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="485c0-177">For more information about type inference, see [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
 <span data-ttu-id="485c0-178">Informace o tom co se stane, když není zadaný datový typ nebo inicializátoru najdete v tématu [výchozí datových typů a hodnot](../../../visual-basic/language-reference/statements/dim-statement.md#default) dál v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="485c0-178">For information about what happens when a data type or initializer is not specified, see [Default Data Types and Values](../../../visual-basic/language-reference/statements/dim-statement.md#default) later in this topic.</span></span>  
  
 <span data-ttu-id="485c0-179">Můžete použít *inicializátoru objektu* deklarovat instance pojmenované a anonymní typy.</span><span class="sxs-lookup"><span data-stu-id="485c0-179">You can use an *object initializer* to declare instances of named and anonymous types.</span></span> <span data-ttu-id="485c0-180">Následující kód vytvoří instanci `Student` třídy a inicializace vlastností pomocí inicializátoru objektu.</span><span class="sxs-lookup"><span data-stu-id="485c0-180">The following code creates an instance of a `Student` class and uses an object initializer to initialize properties.</span></span>  
  
```vb  
Dim student1 As New Student With {.First = "Michael",   
                                  .Last = "Tucker"}  
```  
  
 <span data-ttu-id="485c0-181">Další informace o inicializátory objektů najdete v tématu [postupy: Deklarace objektu pomocí inicializátoru objektu](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [inicializátory objektů: pojmenované a anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), a [anonymní typy ](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="485c0-181">For more information about object initializers, see [How to: Declare an Object by Using an Object Initializer](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), and [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="declaring-multiple-variables"></a><span data-ttu-id="485c0-182">Deklarování více proměnných</span><span class="sxs-lookup"><span data-stu-id="485c0-182">Declaring Multiple Variables</span></span>  
 <span data-ttu-id="485c0-183">Je možné deklarovat několik proměnné v rámci jedné deklarace příkazu zadání názvu proměnné pro každé z nich a název každého pole v závorkách.</span><span class="sxs-lookup"><span data-stu-id="485c0-183">You can declare several variables in one declaration statement, specifying the variable name for each one, and following each array name with parentheses.</span></span> <span data-ttu-id="485c0-184">Více proměnných jsou oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="485c0-184">Multiple variables are separated by commas.</span></span>  
  
```vb  
Dim lastTime, nextTime, allTimes() As Date  
```  
  
 <span data-ttu-id="485c0-185">Pokud je deklarovat více než jednu proměnnou na jednu `As` klauzule, nelze zadat inicializátoru pro tuto skupinu proměnných.</span><span class="sxs-lookup"><span data-stu-id="485c0-185">If you declare more than one variable with one `As` clause, you cannot supply an initializer for that group of variables.</span></span>  
  
 <span data-ttu-id="485c0-186">Můžete zadat různé datové typy pro jiné proměnné pomocí samostatné `As` klauzule pro každou proměnnou můžete deklarovat.</span><span class="sxs-lookup"><span data-stu-id="485c0-186">You can specify different data types for different variables by using a separate `As` clause for each variable you declare.</span></span> <span data-ttu-id="485c0-187">Každá proměnná má datový typ zadaný v prvním `As` klauzule došlo po jeho `variablename` část.</span><span class="sxs-lookup"><span data-stu-id="485c0-187">Each variable takes the data type specified in the first `As` clause encountered after its `variablename` part.</span></span>  
  
```vb  
Dim a, b, c As Single, x, y As Double, i As Integer  
' a, b, and c are all Single; x and y are both Double  
```  
  
## <a name="arrays"></a><span data-ttu-id="485c0-188">Pole</span><span class="sxs-lookup"><span data-stu-id="485c0-188">Arrays</span></span>  
 <span data-ttu-id="485c0-189">Je možné deklarovat proměnnou pro uložení *pole*, která může pojmout více hodnot.</span><span class="sxs-lookup"><span data-stu-id="485c0-189">You can declare a variable to hold an *array*, which can hold multiple values.</span></span> <span data-ttu-id="485c0-190">Chcete-li určit, že proměnné obsahuje pole, postupujte podle jeho `variablename` okamžitě v závorkách.</span><span class="sxs-lookup"><span data-stu-id="485c0-190">To specify that a variable holds an array, follow its `variablename` immediately with parentheses.</span></span> <span data-ttu-id="485c0-191">Další informace o polích najdete v tématu [pole](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="485c0-191">For more information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="485c0-192">Můžete zadat dolní a horní mez Každá dimenze pole.</span><span class="sxs-lookup"><span data-stu-id="485c0-192">You can specify the lower and upper bound of each dimension of an array.</span></span> <span data-ttu-id="485c0-193">Chcete-li to provést, zahrňte `boundslist` v závorkách.</span><span class="sxs-lookup"><span data-stu-id="485c0-193">To do this, include a `boundslist` inside the parentheses.</span></span> <span data-ttu-id="485c0-194">Pro každou dimenzi `boundslist` Určuje horní mez a volitelně dolní hranice.</span><span class="sxs-lookup"><span data-stu-id="485c0-194">For each dimension, the `boundslist` specifies the upper bound and optionally the lower bound.</span></span> <span data-ttu-id="485c0-195">Dolní hranice, je vždy nula, a jestli ho zadáte nebo ne.</span><span class="sxs-lookup"><span data-stu-id="485c0-195">The lower bound is always zero, whether you specify it or not.</span></span> <span data-ttu-id="485c0-196">Každý index se může lišit od nuly pomocí jeho horní mez hodnoty.</span><span class="sxs-lookup"><span data-stu-id="485c0-196">Each index can vary from zero through its upper bound value.</span></span>  
  
 <span data-ttu-id="485c0-197">Následující dva příkazy jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="485c0-197">The following two statements are equivalent.</span></span> <span data-ttu-id="485c0-198">Každý příkaz deklaruje pole 21 `Integer` elementy.</span><span class="sxs-lookup"><span data-stu-id="485c0-198">Each statement declares an array of 21 `Integer` elements.</span></span> <span data-ttu-id="485c0-199">Pokud získáváte přístup k poli, index se může lišit od 0 do 20.</span><span class="sxs-lookup"><span data-stu-id="485c0-199">When you access the array, the index can vary from 0 through 20.</span></span>  
  
```vb  
Dim totals(20) As Integer  
Dim totals(0 To 20) As Integer  
```  
  
 <span data-ttu-id="485c0-200">Následující příkaz deklaruje dvourozměrná pole typu `Double`.</span><span class="sxs-lookup"><span data-stu-id="485c0-200">The following statement declares a two-dimensional array of type `Double`.</span></span> <span data-ttu-id="485c0-201">Pole má 6 sloupců (5 + 1) každé 4 řádky (3 + 1).</span><span class="sxs-lookup"><span data-stu-id="485c0-201">The array has 4 rows (3 + 1) of 6 columns (5 + 1) each.</span></span> <span data-ttu-id="485c0-202">Všimněte si, že horní mez představuje nejvyšší možná hodnota pro index, nebyl délka dimenze.</span><span class="sxs-lookup"><span data-stu-id="485c0-202">Note that an upper bound represents the highest possible value for the index, not the length of the dimension.</span></span> <span data-ttu-id="485c0-203">Délka dimenze je horní mez plus jedna.</span><span class="sxs-lookup"><span data-stu-id="485c0-203">The length of the dimension is the upper bound plus one.</span></span>  
  
```vb  
Dim matrix2(3, 5) As Double  
```  
  
 <span data-ttu-id="485c0-204">Pole může mít od 1 do 32 dimenzí.</span><span class="sxs-lookup"><span data-stu-id="485c0-204">An array can have from 1 to 32 dimensions.</span></span>  
  
 <span data-ttu-id="485c0-205">Všechny hranice můžete nechat prázdné v deklarace pole.</span><span class="sxs-lookup"><span data-stu-id="485c0-205">You can leave all the bounds blank in an array declaration.</span></span> <span data-ttu-id="485c0-206">Pokud to uděláte, pole má počet dimenzí, které zadáte, ale není inicializován.</span><span class="sxs-lookup"><span data-stu-id="485c0-206">If you do this, the array has the number of dimensions you specify, but it is uninitialized.</span></span> <span data-ttu-id="485c0-207">Má hodnotu `Nothing` dokud alespoň inicializaci některé z jejích elementů.</span><span class="sxs-lookup"><span data-stu-id="485c0-207">It has a value of `Nothing` until you initialize at least some of its elements.</span></span> <span data-ttu-id="485c0-208">`Dim` Příkaz musíte zadat rozsah pro všechny dimenze nebo žádné dimenze.</span><span class="sxs-lookup"><span data-stu-id="485c0-208">The `Dim` statement must specify bounds either for all dimensions or for no dimensions.</span></span>  
  
```vb  
' Declare an array with blank array bounds.  
Dim messages() As String  
' Initialize the array.  
ReDim messages(4)  
```  
  
 <span data-ttu-id="485c0-209">Pokud pole má více než jednou dimenzí, je nutné zahrnout čárkami k označení počet dimenzí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="485c0-209">If the array has more than one dimension, you must include commas between the parentheses to indicate the number of dimensions.</span></span>  
  
```vb  
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte  
```  
  
 <span data-ttu-id="485c0-210">Je možné deklarovat *nulová délka pole* deklarováním jeden z tohoto pole dimenze mít hodnotu -1.</span><span class="sxs-lookup"><span data-stu-id="485c0-210">You can declare a *zero-length array* by declaring one of the array's dimensions to be -1.</span></span> <span data-ttu-id="485c0-211">Proměnné, která obsahuje pole nulovou délkou nemá hodnotu `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="485c0-211">A variable that holds a zero-length array does not have the value `Nothing`.</span></span> <span data-ttu-id="485c0-212">Pole s nulovou délkou vyžadují některé běžné funkce runtime jazyka.</span><span class="sxs-lookup"><span data-stu-id="485c0-212">Zero-length arrays are required by certain common language runtime functions.</span></span> <span data-ttu-id="485c0-213">Pokud se pokusíte přístup k takové pole, došlo k výjimce modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="485c0-213">If you try to access such an array, a runtime exception occurs.</span></span> <span data-ttu-id="485c0-214">Další informace najdete v tématu [pole](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="485c0-214">For more information, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="485c0-215">Hodnoty pole lze inicializovat pomocí pole literálu.</span><span class="sxs-lookup"><span data-stu-id="485c0-215">You can initialize the values of an array by using an array literal.</span></span> <span data-ttu-id="485c0-216">Chcete-li to provést, uzavřete inicializace hodnoty se složené závorky (`{}`).</span><span class="sxs-lookup"><span data-stu-id="485c0-216">To do this, surround the initialization values with braces (`{}`).</span></span>  
  
```vb  
Dim longArray() As Long = {0, 1, 2, 3}  
```  
  
 <span data-ttu-id="485c0-217">Pro vícerozměrná pole je inicializace pro každý samostatný dimenzi uzavřené do složených závorek v vnější dimenzi.</span><span class="sxs-lookup"><span data-stu-id="485c0-217">For multidimensional arrays, the initialization for each separate dimension is enclosed in braces in the outer dimension.</span></span> <span data-ttu-id="485c0-218">Elementy jsou určené v řádku hlavní pořadí.</span><span class="sxs-lookup"><span data-stu-id="485c0-218">The elements are specified in row-major order.</span></span>  
  
```vb  
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}  
```  
  
 <span data-ttu-id="485c0-219">Další informace o literálech pole najdete v tématu [pole](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="485c0-219">For more information about array literals, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
##  <a name="default"></a><span data-ttu-id="485c0-220">Typy a hodnoty výchozí Data</span><span class="sxs-lookup"><span data-stu-id="485c0-220">Default Data Types and Values</span></span>  
 <span data-ttu-id="485c0-221">Následující tabulka popisuje výsledky datový typ a inicializátoru v různých kombinacích `Dim` příkaz.</span><span class="sxs-lookup"><span data-stu-id="485c0-221">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="485c0-222">Datový typ zadaný?</span><span class="sxs-lookup"><span data-stu-id="485c0-222">Data type specified?</span></span>|<span data-ttu-id="485c0-223">Zadaný inicializační?</span><span class="sxs-lookup"><span data-stu-id="485c0-223">Initializer specified?</span></span>|<span data-ttu-id="485c0-224">Příklad</span><span class="sxs-lookup"><span data-stu-id="485c0-224">Example</span></span>|<span data-ttu-id="485c0-225">Výsledek</span><span class="sxs-lookup"><span data-stu-id="485c0-225">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="485c0-226">Ne</span><span class="sxs-lookup"><span data-stu-id="485c0-226">No</span></span>|<span data-ttu-id="485c0-227">Ne</span><span class="sxs-lookup"><span data-stu-id="485c0-227">No</span></span>|`Dim qty`|<span data-ttu-id="485c0-228">Pokud [možnost striktní](../../../visual-basic/language-reference/statements/option-strict-statement.md) je vypnuto (výchozí), proměnná je nastavená na `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="485c0-228">If [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="485c0-229">Pokud `Option Strict` zapnutý, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="485c0-229">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="485c0-230">Ne</span><span class="sxs-lookup"><span data-stu-id="485c0-230">No</span></span>|<span data-ttu-id="485c0-231">Ano</span><span class="sxs-lookup"><span data-stu-id="485c0-231">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="485c0-232">Pokud [Option Infer –](../../../visual-basic/language-reference/statements/option-infer-statement.md) je na (výchozí), typ inicializátoru proměnné přijímá data.</span><span class="sxs-lookup"><span data-stu-id="485c0-232">If [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="485c0-233">V tématu [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="485c0-233">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="485c0-234">Pokud `Option Infer` vypnuté a `Option Strict` je vypnutý, nabývá datový typ `Object`.</span><span class="sxs-lookup"><span data-stu-id="485c0-234">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="485c0-235">Pokud `Option Infer` vypnuté a `Option Strict` zapnutý, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="485c0-235">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="485c0-236">Ano</span><span class="sxs-lookup"><span data-stu-id="485c0-236">Yes</span></span>|<span data-ttu-id="485c0-237">Ne</span><span class="sxs-lookup"><span data-stu-id="485c0-237">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="485c0-238">Výchozí hodnota pro typ dat je inicializováno proměnnou.</span><span class="sxs-lookup"><span data-stu-id="485c0-238">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="485c0-239">Najdete v tabulce dál v této části.</span><span class="sxs-lookup"><span data-stu-id="485c0-239">See the table later in this section.</span></span>|  
|<span data-ttu-id="485c0-240">Ano</span><span class="sxs-lookup"><span data-stu-id="485c0-240">Yes</span></span>|<span data-ttu-id="485c0-241">Ano</span><span class="sxs-lookup"><span data-stu-id="485c0-241">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="485c0-242">Pokud datový typ inicializátoru není převést na zadaný datový typ, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="485c0-242">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
 <span data-ttu-id="485c0-243">Pokud zadáte datový typ, ale nezadávejte žádné inicializátoru, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] inicializuje proměnnou na výchozí hodnotu pro jeho datového typu.</span><span class="sxs-lookup"><span data-stu-id="485c0-243">If you specify a data type but do not specify an initializer, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] initializes the variable to the default value for its data type.</span></span> <span data-ttu-id="485c0-244">Následující tabulka uvádí výchozí hodnoty inicializace.</span><span class="sxs-lookup"><span data-stu-id="485c0-244">The following table shows the default initialization values.</span></span>  
  
|<span data-ttu-id="485c0-245">Datový typ</span><span class="sxs-lookup"><span data-stu-id="485c0-245">Data type</span></span>|<span data-ttu-id="485c0-246">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="485c0-246">Default value</span></span>|  
|---|---|  
|<span data-ttu-id="485c0-247">Všechny číselnými typy (včetně `Byte` a `SByte`)</span><span class="sxs-lookup"><span data-stu-id="485c0-247">All numeric types (including `Byte` and `SByte`)</span></span>|<span data-ttu-id="485c0-248">0</span><span class="sxs-lookup"><span data-stu-id="485c0-248">0</span></span>|  
|`Char`|<span data-ttu-id="485c0-249">Binární 0</span><span class="sxs-lookup"><span data-stu-id="485c0-249">Binary 0</span></span>|  
|<span data-ttu-id="485c0-250">Všechny odkazové typy (včetně `Object`, `String`a všechna pole)</span><span class="sxs-lookup"><span data-stu-id="485c0-250">All reference types (including `Object`, `String`, and all arrays)</span></span>|`Nothing`|  
|`Boolean`|`False`|  
|`Date`|<span data-ttu-id="485c0-251">12:00:00 1. ledna roku 1 (01/01/0001 12:00:00 AM)</span><span class="sxs-lookup"><span data-stu-id="485c0-251">12:00 AM of January 1 of the year 1 (01/01/0001 12:00:00 AM)</span></span>|  
  
 <span data-ttu-id="485c0-252">Každý prvek strukturou je inicializován, jako by šlo samostatná proměnná.</span><span class="sxs-lookup"><span data-stu-id="485c0-252">Each element of a structure is initialized as if it were a separate variable.</span></span> <span data-ttu-id="485c0-253">Pokud deklarovat délka pole, ale není inicializovat jeho prvky, každý prvek je inicializován, jako by šlo samostatná proměnná.</span><span class="sxs-lookup"><span data-stu-id="485c0-253">If you declare the length of an array but do not initialize its elements, each element is initialized as if it were a separate variable.</span></span>  
  
## <a name="static-local-variable-lifetime"></a><span data-ttu-id="485c0-254">Statické místní proměnné doba platnosti</span><span class="sxs-lookup"><span data-stu-id="485c0-254">Static Local Variable Lifetime</span></span>  
 <span data-ttu-id="485c0-255">A `Static` místní proměnné má delší doba platnosti než procesu, ve kterém je deklarovaná.</span><span class="sxs-lookup"><span data-stu-id="485c0-255">A `Static` local variable has a longer lifetime than that of the procedure in which it is declared.</span></span> <span data-ttu-id="485c0-256">Hranice životního cyklu proměnné závisí na kterém je deklarovaná postupu a zda je `Shared`.</span><span class="sxs-lookup"><span data-stu-id="485c0-256">The boundaries of the variable's lifetime depend on where the procedure is declared and whether it is `Shared`.</span></span>  
  
|<span data-ttu-id="485c0-257">Deklarace procedur</span><span class="sxs-lookup"><span data-stu-id="485c0-257">Procedure declaration</span></span>|<span data-ttu-id="485c0-258">Proměnná inicializována</span><span class="sxs-lookup"><span data-stu-id="485c0-258">Variable initialized</span></span>|<span data-ttu-id="485c0-259">Proměnná zastaví existující</span><span class="sxs-lookup"><span data-stu-id="485c0-259">Variable stops existing</span></span>|  
|---|---|---|  
|<span data-ttu-id="485c0-260">V modulu</span><span class="sxs-lookup"><span data-stu-id="485c0-260">In a module</span></span>|<span data-ttu-id="485c0-261">Při prvním volání procedury</span><span class="sxs-lookup"><span data-stu-id="485c0-261">The first time the procedure is called</span></span>|<span data-ttu-id="485c0-262">Pokud váš program zastaví provádění</span><span class="sxs-lookup"><span data-stu-id="485c0-262">When your program stops execution</span></span>|  
|<span data-ttu-id="485c0-263">Ve třídě nebo struktuře postup je`Shared`</span><span class="sxs-lookup"><span data-stu-id="485c0-263">In a class or structure, procedure is `Shared`</span></span>|<span data-ttu-id="485c0-264">První postup se nazývá na konkrétní instanci nebo na třídu nebo strukturu, sám sebe</span><span class="sxs-lookup"><span data-stu-id="485c0-264">The first time the procedure is called either on a specific instance or on the class or structure itself</span></span>|<span data-ttu-id="485c0-265">Pokud váš program zastaví provádění</span><span class="sxs-lookup"><span data-stu-id="485c0-265">When your program stops execution</span></span>|  
|<span data-ttu-id="485c0-266">Ve třídě nebo struktuře není postup`Shared`</span><span class="sxs-lookup"><span data-stu-id="485c0-266">In a class or structure, procedure isn't `Shared`</span></span>|<span data-ttu-id="485c0-267">První postup se nazývá na konkrétní instanci</span><span class="sxs-lookup"><span data-stu-id="485c0-267">The first time the procedure is called on a specific instance</span></span>|<span data-ttu-id="485c0-268">Uvolnění instance pro uvolňování paměti (GC)</span><span class="sxs-lookup"><span data-stu-id="485c0-268">When the instance is released for garbage collection (GC)</span></span>|  
  
## <a name="attributes-and-modifiers"></a><span data-ttu-id="485c0-269">Atributy a modifikátory</span><span class="sxs-lookup"><span data-stu-id="485c0-269">Attributes and Modifiers</span></span>  
 <span data-ttu-id="485c0-270">Atributy lze použít pouze k členské proměnné, nikoli k lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="485c0-270">You can apply attributes only to member variables, not to local variables.</span></span> <span data-ttu-id="485c0-271">Atribut přispívá informace metadat sestavení, která není smysl pro dočasné úložiště, jako je například místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="485c0-271">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local variables.</span></span>  
  
 <span data-ttu-id="485c0-272">Na úrovni modulu, nemůžete použít `Static` modifikátor deklarovat členské proměnné.</span><span class="sxs-lookup"><span data-stu-id="485c0-272">At module level, you cannot use the `Static` modifier to declare member variables.</span></span> <span data-ttu-id="485c0-273">Na úrovni postup, nemůžete použít `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, nebo žádný přístup modifikátory deklarovat lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="485c0-273">At procedure level, you cannot use `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, or any access modifiers to declare local variables.</span></span>  
  
 <span data-ttu-id="485c0-274">Můžete určit, jaký kód můžete přístup k proměnné zadáním `accessmodifier`.</span><span class="sxs-lookup"><span data-stu-id="485c0-274">You can specify what code can access a variable by supplying an `accessmodifier`.</span></span> <span data-ttu-id="485c0-275">Třídy a modul výchozí proměnné (mimo libovolná procedura) člena privátní přístup a struktura členské proměnné výchozí nastavení veřejný přístup.</span><span class="sxs-lookup"><span data-stu-id="485c0-275">Class and module member variables (outside any procedure) default to private access, and structure member variables default to public access.</span></span> <span data-ttu-id="485c0-276">Můžete nastavit jejich úrovně přístupu s modifikátory přístupu.</span><span class="sxs-lookup"><span data-stu-id="485c0-276">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="485c0-277">Modifikátory přístupu nelze použít na lokální proměnné (uvnitř procedury).</span><span class="sxs-lookup"><span data-stu-id="485c0-277">You cannot use access modifiers on local variables (inside a procedure).</span></span>  
  
 <span data-ttu-id="485c0-278">Můžete zadat `WithEvents` pouze na členské proměnné, nikoli na lokální proměnné uvnitř procedury.</span><span class="sxs-lookup"><span data-stu-id="485c0-278">You can specify `WithEvents` only on member variables, not on local variables inside a procedure.</span></span> <span data-ttu-id="485c0-279">Pokud zadáte `WithEvents`, datový typ proměnné, musí typu určité třídy, ne `Object`.</span><span class="sxs-lookup"><span data-stu-id="485c0-279">If you specify `WithEvents`, the data type of the variable must be a specific class type, not `Object`.</span></span> <span data-ttu-id="485c0-280">Nelze deklarovat pole s `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="485c0-280">You cannot declare an array with `WithEvents`.</span></span> <span data-ttu-id="485c0-281">Další informace o událostech najdete v tématu [události](../../../visual-basic/programming-guide/language-features/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="485c0-281">For more information about events, see [Events](../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="485c0-282">Kód mimo třída, struktura, modul nebo kvalifikaci název členské proměnné s názvem třídy, struktury nebo modul.</span><span class="sxs-lookup"><span data-stu-id="485c0-282">Code outside a class, structure, or module must qualify a member variable's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="485c0-283">Mimo území procedura nebo bloku nemůže odkazovat na žádné místní proměnné v rámci tohoto postupu nebo bloku kódu.</span><span class="sxs-lookup"><span data-stu-id="485c0-283">Code outside a procedure or block cannot refer to any local variables within that procedure or block.</span></span>  
  
## <a name="releasing-managed-resources"></a><span data-ttu-id="485c0-284">Uvolnění spravované prostředky</span><span class="sxs-lookup"><span data-stu-id="485c0-284">Releasing Managed Resources</span></span>  
 <span data-ttu-id="485c0-285">Uvolňování paměti rozhraní .NET Framework uvolní spravované prostředky bez další kódování z vaší strany.</span><span class="sxs-lookup"><span data-stu-id="485c0-285">The .NET Framework garbage collector disposes of managed resources without any extra coding on your part.</span></span> <span data-ttu-id="485c0-286">Ale můžete vynutit vyřazení spravovaných prostředků, místo abyste čekali, bude systém uvolňování.</span><span class="sxs-lookup"><span data-stu-id="485c0-286">However, you can force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>  
  
 <span data-ttu-id="485c0-287">Pokud do zvlášť cenné a omezených prostředků (například databáze připojení nebo soubor popisovač) obsahuje třídu, nechcete čekat na další uvolňování paměti pro vyčištění instance třídy, která je již používána.</span><span class="sxs-lookup"><span data-stu-id="485c0-287">If a class holds onto a particularly valuable and scarce resource (such as a database connection or file handle), you might not want to wait until the next garbage collection to clean up a class instance that's no longer in use.</span></span> <span data-ttu-id="485c0-288">Třída může implementovat <xref:System.IDisposable> rozhraní a poskytují způsob k uvolnění prostředků než uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="485c0-288">A class may implement the <xref:System.IDisposable> interface to provide a way to release resources before a garbage collection.</span></span> <span data-ttu-id="485c0-289">Poskytuje třídu, která implementuje rozhraní `Dispose` metoda, kterou lze volat vynutit cenné prostředky k uvolnění okamžitě.</span><span class="sxs-lookup"><span data-stu-id="485c0-289">A class that implements that interface exposes a `Dispose` method that can be called to force valuable resources to be released immediately.</span></span>  
  
 <span data-ttu-id="485c0-290">`Using` Příkaz automatizuje proces získávání prostředku, provádění sadu příkazů a pak uvolnění prostředku.</span><span class="sxs-lookup"><span data-stu-id="485c0-290">The `Using` statement automates the process of acquiring a resource, executing a set of statements, and then disposing of the resource.</span></span> <span data-ttu-id="485c0-291">Však musí implementovat prostředku <xref:System.IDisposable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="485c0-291">However, the resource must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="485c0-292">Další informace najdete v tématu [pomocí příkazu](../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="485c0-292">For more information, see [Using Statement](../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="485c0-293">Příklad</span><span class="sxs-lookup"><span data-stu-id="485c0-293">Example</span></span>  
 <span data-ttu-id="485c0-294">Následující příklad deklaruje proměnné pomocí `Dim` příkaz s různé možnosti.</span><span class="sxs-lookup"><span data-stu-id="485c0-294">The following example declares variables by using the `Dim` statement with various options.</span></span>  
  
 [!code-vb[VbVbalrStatements#141](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="485c0-295">Příklad</span><span class="sxs-lookup"><span data-stu-id="485c0-295">Example</span></span>  
 <span data-ttu-id="485c0-296">Následující příklad uvádí prvočísel od 1 do 30.</span><span class="sxs-lookup"><span data-stu-id="485c0-296">The following example lists the prime numbers between 1 and 30.</span></span> <span data-ttu-id="485c0-297">Rozsah místních proměnných je popsaná v komentáře kódu.</span><span class="sxs-lookup"><span data-stu-id="485c0-297">The scope of local variables is described in code comments.</span></span>  
  
 [!code-vb[VbVbalrStatements#142](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="485c0-298">Příklad</span><span class="sxs-lookup"><span data-stu-id="485c0-298">Example</span></span>  
 <span data-ttu-id="485c0-299">V následujícím příkladu `speedValue` proměnné je deklarovaná na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="485c0-299">In the following example, the `speedValue` variable is declared at the class level.</span></span> <span data-ttu-id="485c0-300">`Private` – Klíčové slovo se používá k deklaraci proměnnou.</span><span class="sxs-lookup"><span data-stu-id="485c0-300">The `Private` keyword is used to declare the variable.</span></span> <span data-ttu-id="485c0-301">Proměnná je přístupná procedurou v `Car` třídy.</span><span class="sxs-lookup"><span data-stu-id="485c0-301">The variable can be accessed by any procedure in the `Car` class.</span></span>  
  
 [!code-vb[VbVbalrStatements#144](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_3.vb)]  
  
 [!code-vb[VbVbalrStatements#145](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="485c0-302">Viz také</span><span class="sxs-lookup"><span data-stu-id="485c0-302">See Also</span></span>  
 [<span data-ttu-id="485c0-303">Const – příkaz</span><span class="sxs-lookup"><span data-stu-id="485c0-303">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="485c0-304">ReDim – příkaz</span><span class="sxs-lookup"><span data-stu-id="485c0-304">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="485c0-305">Option Explicit – příkaz</span><span class="sxs-lookup"><span data-stu-id="485c0-305">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="485c0-306">Option Infer – příkaz</span><span class="sxs-lookup"><span data-stu-id="485c0-306">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [<span data-ttu-id="485c0-307">Option Strict – příkaz</span><span class="sxs-lookup"><span data-stu-id="485c0-307">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="485c0-308">Stránka kompilovat, Návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="485c0-308">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [<span data-ttu-id="485c0-309">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="485c0-309">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="485c0-310">Pole</span><span class="sxs-lookup"><span data-stu-id="485c0-310">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="485c0-311">Inicializátory objektů: Pojmenované a anonymní typy</span><span class="sxs-lookup"><span data-stu-id="485c0-311">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [<span data-ttu-id="485c0-312">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="485c0-312">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="485c0-313">Inicializátory objektů: Pojmenované a anonymní typy</span><span class="sxs-lookup"><span data-stu-id="485c0-313">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [<span data-ttu-id="485c0-314">Postupy: Deklarace objektu pomocí inicializátoru objektu</span><span class="sxs-lookup"><span data-stu-id="485c0-314">How to: Declare an Object by Using an Object Initializer</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)  
 [<span data-ttu-id="485c0-315">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="485c0-315">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
