---
title: Dim – příkaz (Visual Basic)
ms.date: 05/12/2018
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
ms.openlocfilehash: b3384b771748a1f2c9e841407042f81ce6ebe76d
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34234724"
---
# <a name="dim-statement-visual-basic"></a><span data-ttu-id="9e81e-102">Dim – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e81e-102">Dim Statement (Visual Basic)</span></span>
<span data-ttu-id="9e81e-103">Deklaruje a přidělí prostor úložiště pro jeden nebo více proměnných.</span><span class="sxs-lookup"><span data-stu-id="9e81e-103">Declares and allocates storage space for one or more variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e81e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e81e-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]   
Dim [ WithEvents ] variablelist  
```  
  
## <a name="parts"></a><span data-ttu-id="9e81e-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="9e81e-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="9e81e-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="9e81e-106">Optional.</span></span> <span data-ttu-id="9e81e-107">V tématu [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="9e81e-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="9e81e-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="9e81e-108">Optional.</span></span> <span data-ttu-id="9e81e-109">Může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="9e81e-109">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="9e81e-110">Public</span><span class="sxs-lookup"><span data-stu-id="9e81e-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="9e81e-111">Protected</span><span class="sxs-lookup"><span data-stu-id="9e81e-111">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="9e81e-112">Friend</span><span class="sxs-lookup"><span data-stu-id="9e81e-112">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="9e81e-113">Private</span><span class="sxs-lookup"><span data-stu-id="9e81e-113">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   [<span data-ttu-id="9e81e-114">Chráněné Friend</span><span class="sxs-lookup"><span data-stu-id="9e81e-114">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)
    
    - [<span data-ttu-id="9e81e-115">Privátní chráněný</span><span class="sxs-lookup"><span data-stu-id="9e81e-115">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)

     <span data-ttu-id="9e81e-116">V tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="9e81e-116">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `Shared`  
  
     <span data-ttu-id="9e81e-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="9e81e-117">Optional.</span></span> <span data-ttu-id="9e81e-118">V tématu [sdílené](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="9e81e-118">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="9e81e-119">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="9e81e-119">Optional.</span></span> <span data-ttu-id="9e81e-120">V tématu [stínů](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="9e81e-120">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `Static`  
  
     <span data-ttu-id="9e81e-121">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="9e81e-121">Optional.</span></span> <span data-ttu-id="9e81e-122">V tématu [statické](../../../visual-basic/language-reference/modifiers/static.md).</span><span class="sxs-lookup"><span data-stu-id="9e81e-122">See [Static](../../../visual-basic/language-reference/modifiers/static.md).</span></span>  
  
-   `ReadOnly`  
  
     <span data-ttu-id="9e81e-123">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="9e81e-123">Optional.</span></span> <span data-ttu-id="9e81e-124">V tématu [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="9e81e-124">See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
-   `WithEvents`  
  
     <span data-ttu-id="9e81e-125">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="9e81e-125">Optional.</span></span> <span data-ttu-id="9e81e-126">Určuje, že jsou objektové proměnné, které odkazují na instancí třídy, který může vyvolat události.</span><span class="sxs-lookup"><span data-stu-id="9e81e-126">Specifies that these are object variables that refer to instances of a class that can raise events.</span></span> <span data-ttu-id="9e81e-127">V tématu [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).</span><span class="sxs-lookup"><span data-stu-id="9e81e-127">See [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).</span></span>  
  
-   `variablelist`  
  
     <span data-ttu-id="9e81e-128">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="9e81e-128">Required.</span></span> <span data-ttu-id="9e81e-129">Seznam proměnných se deklarovaných v tomto příkazu.</span><span class="sxs-lookup"><span data-stu-id="9e81e-129">List of variables being declared in this statement.</span></span>  
  
     `variable [ , variable ... ]`  
  
     <span data-ttu-id="9e81e-130">Každý `variable` má následující syntaxe a částí:</span><span class="sxs-lookup"><span data-stu-id="9e81e-130">Each `variable` has the following syntax and parts:</span></span>  
  
     <span data-ttu-id="9e81e-131">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="9e81e-131">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span></span>  
  
    |<span data-ttu-id="9e81e-132">Část</span><span class="sxs-lookup"><span data-stu-id="9e81e-132">Part</span></span>|<span data-ttu-id="9e81e-133">Popis</span><span class="sxs-lookup"><span data-stu-id="9e81e-133">Description</span></span>|  
    |---|---|  
    |`variablename`|<span data-ttu-id="9e81e-134">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="9e81e-134">Required.</span></span> <span data-ttu-id="9e81e-135">Název proměnné.</span><span class="sxs-lookup"><span data-stu-id="9e81e-135">Name of the variable.</span></span> <span data-ttu-id="9e81e-136">V tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="9e81e-136">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
    |`boundslist`|<span data-ttu-id="9e81e-137">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="9e81e-137">Optional.</span></span> <span data-ttu-id="9e81e-138">Seznam mezí Každá dimenze proměnná typu pole.</span><span class="sxs-lookup"><span data-stu-id="9e81e-138">List of bounds of each dimension of an array variable.</span></span>|  
    |`New`|<span data-ttu-id="9e81e-139">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="9e81e-139">Optional.</span></span> <span data-ttu-id="9e81e-140">Vytvoří novou instanci třídy, když `Dim` příkaz spustí.</span><span class="sxs-lookup"><span data-stu-id="9e81e-140">Creates a new instance of the class when the `Dim` statement runs.</span></span>|  
    |`datatype`|<span data-ttu-id="9e81e-141">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="9e81e-141">Optional.</span></span> <span data-ttu-id="9e81e-142">Datový typ proměnné.</span><span class="sxs-lookup"><span data-stu-id="9e81e-142">Data type of the variable.</span></span>|  
    |`With`|<span data-ttu-id="9e81e-143">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="9e81e-143">Optional.</span></span> <span data-ttu-id="9e81e-144">Představuje seznam inicializátoru objektu.</span><span class="sxs-lookup"><span data-stu-id="9e81e-144">Introduces the object initializer list.</span></span>|  
    |`propertyname`|<span data-ttu-id="9e81e-145">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="9e81e-145">Optional.</span></span> <span data-ttu-id="9e81e-146">Název vlastnosti ve třídě provádíte instanci.</span><span class="sxs-lookup"><span data-stu-id="9e81e-146">The name of a property in the class you are making an instance of.</span></span>|  
    |`propinitializer`|<span data-ttu-id="9e81e-147">Požadované po `propertyname` =.</span><span class="sxs-lookup"><span data-stu-id="9e81e-147">Required after `propertyname` =.</span></span> <span data-ttu-id="9e81e-148">Výraz, který se vyhodnotí a přiřadí název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9e81e-148">The expression that is evaluated and assigned to the property name.</span></span>|  
    |`initializer`|<span data-ttu-id="9e81e-149">Nepovinný, pokud `New` není zadán.</span><span class="sxs-lookup"><span data-stu-id="9e81e-149">Optional if `New` is not specified.</span></span> <span data-ttu-id="9e81e-150">Výraz, který se vyhodnotí a přiřadí do proměnné při jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="9e81e-150">Expression that is evaluated and assigned to the variable when it is created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e81e-151">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9e81e-151">Remarks</span></span>  
 <span data-ttu-id="9e81e-152">Visual Basic – kompilátor používá `Dim` příkaz k určení typu dat proměnné a další informace, například jaké kódu mají přístup k proměnné.</span><span class="sxs-lookup"><span data-stu-id="9e81e-152">The Visual Basic compiler uses the `Dim` statement to determine the variable's data type and other information, such as what code can access the variable.</span></span> <span data-ttu-id="9e81e-153">Následující příklad deklaruje proměnnou pro uložení `Integer` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9e81e-153">The following example declares a variable to hold an `Integer` value.</span></span>  
  
```vb  
Dim numberOfStudents As Integer  
```  
  
 <span data-ttu-id="9e81e-154">Můžete zadat jakýkoli datový typ nebo název výčtu, struktura, třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9e81e-154">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
```vb  
Dim finished As Boolean  
Dim monitorBox As System.Windows.Forms.Form  
```  
  
 <span data-ttu-id="9e81e-155">Pro odkaz na typ, můžete použít `New` – klíčové slovo vytvořit novou instanci třídy nebo struktury, která je zadána datového typu.</span><span class="sxs-lookup"><span data-stu-id="9e81e-155">For a reference type, you use the `New` keyword to create a new instance of the class or structure that is specified by the data type.</span></span> <span data-ttu-id="9e81e-156">Pokud používáte `New`, nepoužívejte inicializátoru výrazu.</span><span class="sxs-lookup"><span data-stu-id="9e81e-156">If you use `New`, you do not use an initializer expression.</span></span> <span data-ttu-id="9e81e-157">Místo toho zadáte argumenty, pokud jsou požadována konstruktoru třídy, ze kterého jsou vytváření proměnné.</span><span class="sxs-lookup"><span data-stu-id="9e81e-157">Instead, you supply arguments, if they are required, to the constructor of the class from which you are creating the variable.</span></span>  
  
```vb  
Dim bottomLabel As New System.Windows.Forms.Label  
```  
  
 <span data-ttu-id="9e81e-158">Je možné deklarovat proměnnou v postupu, blok, třída, struktura nebo modul.</span><span class="sxs-lookup"><span data-stu-id="9e81e-158">You can declare a variable in a procedure, block, class, structure, or module.</span></span> <span data-ttu-id="9e81e-159">Nelze deklarovat proměnnou v zdrojový soubor, obor názvů nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9e81e-159">You cannot declare a variable in a source file, namespace, or interface.</span></span> <span data-ttu-id="9e81e-160">Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="9e81e-160">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="9e81e-161">Proměnné, která je deklarovaná na úrovni modulu mimo libovolná procedura je *členské proměnné* nebo *pole*.</span><span class="sxs-lookup"><span data-stu-id="9e81e-161">A variable that is declared at module level, outside any procedure, is a *member variable* or *field*.</span></span> <span data-ttu-id="9e81e-162">Členské proměnné jsou v oboru v rámci své třídy, struktury nebo modul.</span><span class="sxs-lookup"><span data-stu-id="9e81e-162">Member variables are in scope throughout their class, structure, or module.</span></span> <span data-ttu-id="9e81e-163">Proměnné, která je deklarovaná na úrovni postup je *místní proměnné*.</span><span class="sxs-lookup"><span data-stu-id="9e81e-163">A variable that is declared at procedure level is a *local variable*.</span></span> <span data-ttu-id="9e81e-164">Jsou místní proměnné v oboru pouze v rámci postupu nebo bloku.</span><span class="sxs-lookup"><span data-stu-id="9e81e-164">Local variables are in scope only within their procedure or block.</span></span>  
  
 <span data-ttu-id="9e81e-165">Následující modifikátory přístupu slouží k deklarujte proměnné mimo proceduru: `Public`, `Protected`, `Friend`, `Protected Friend`, a `Private`.</span><span class="sxs-lookup"><span data-stu-id="9e81e-165">The following access modifiers are used to declare variables outside a procedure: `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private`.</span></span> <span data-ttu-id="9e81e-166">Další informace najdete v tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="9e81e-166">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="9e81e-167">`Dim` – Klíčové slovo je volitelný a obvykle vynechána, pokud je zadána některá z následujících modifikátory: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, nebo `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="9e81e-167">The `Dim` keyword is optional and usually omitted if you specify any of the following modifiers: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, or `WithEvents`.</span></span>  
  
```vb  
Public maximumAllowed As Double  
Protected Friend currentUserName As String  
Private salary As Decimal  
Static runningTotal As Integer  
```  
  
 <span data-ttu-id="9e81e-168">Pokud `Option Explicit` je na (výchozí), vyžaduje kompilátor deklaraci pro každou proměnnou můžete použít.</span><span class="sxs-lookup"><span data-stu-id="9e81e-168">If `Option Explicit` is on (the default), the compiler requires a declaration for every variable you use.</span></span> <span data-ttu-id="9e81e-169">Další informace najdete v tématu [Option Explicit – příkaz](../../../visual-basic/language-reference/statements/option-explicit-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9e81e-169">For more information, see [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md).</span></span>  
  
## <a name="specifying-an-initial-value"></a><span data-ttu-id="9e81e-170">Pokud zadáte počáteční hodnotu</span><span class="sxs-lookup"><span data-stu-id="9e81e-170">Specifying an Initial Value</span></span>  
 <span data-ttu-id="9e81e-171">Při vytvoření, můžete přiřadit hodnotu proměnné.</span><span class="sxs-lookup"><span data-stu-id="9e81e-171">You can assign a value to a variable when it is created.</span></span> <span data-ttu-id="9e81e-172">Pro typ hodnoty, můžete použít *inicializátoru* k poskytování výraz pro přiřazení k proměnné.</span><span class="sxs-lookup"><span data-stu-id="9e81e-172">For a value type, you use an *initializer* to supply an expression to be assigned to the variable.</span></span> <span data-ttu-id="9e81e-173">Výsledkem výrazu musí být konstanta, která lze vypočítat v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="9e81e-173">The expression must evaluate to a constant that can be calculated at compile time.</span></span>  
  
```vb  
Dim quantity As Integer = 10  
Dim message As String = "Just started"  
```  
  
 <span data-ttu-id="9e81e-174">Pokud je zadán inicializátoru a datový typ není zadán `As` klauzuli *odvození typu* se používá k odvození typu dat z inicializátoru.</span><span class="sxs-lookup"><span data-stu-id="9e81e-174">If an initializer is specified and a data type is not specified in an `As` clause, *type inference* is used to infer the data type from the initializer.</span></span> <span data-ttu-id="9e81e-175">V následujícím příkladu obě `num1` a `num2` jsou silného typu jako celá čísla.</span><span class="sxs-lookup"><span data-stu-id="9e81e-175">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span> <span data-ttu-id="9e81e-176">V druhé deklaraci odvození typu odvodí typ z hodnotu 3.</span><span class="sxs-lookup"><span data-stu-id="9e81e-176">In the second declaration, type inference infers the type from the value 3.</span></span>  
  
```vb  
' Use explicit typing.  
Dim num1 As Integer = 3  
  
' Use local type inference.  
Dim num2 = 3  
```  
  
 <span data-ttu-id="9e81e-177">Odvození typu se vztahuje na úrovni postupu.</span><span class="sxs-lookup"><span data-stu-id="9e81e-177">Type inference applies at the procedure level.</span></span> <span data-ttu-id="9e81e-178">Nevztahuje se mimo proceduru v třída, struktura, modulu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9e81e-178">It does not apply outside a procedure in a class, structure, module, or interface.</span></span> <span data-ttu-id="9e81e-179">Další informace o odvození typu najdete v tématu [Option Infer – příkaz](../../../visual-basic/language-reference/statements/option-infer-statement.md) a [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="9e81e-179">For more information about type inference, see [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
 <span data-ttu-id="9e81e-180">Informace o tom co se stane, když není zadaný datový typ nebo inicializátoru najdete v tématu [výchozí datových typů a hodnot](../../../visual-basic/language-reference/statements/dim-statement.md#default) dál v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="9e81e-180">For information about what happens when a data type or initializer is not specified, see [Default Data Types and Values](../../../visual-basic/language-reference/statements/dim-statement.md#default) later in this topic.</span></span>  
  
 <span data-ttu-id="9e81e-181">Můžete použít *inicializátoru objektu* deklarovat instance pojmenované a anonymní typy.</span><span class="sxs-lookup"><span data-stu-id="9e81e-181">You can use an *object initializer* to declare instances of named and anonymous types.</span></span> <span data-ttu-id="9e81e-182">Následující kód vytvoří instanci `Student` třídy a inicializace vlastností pomocí inicializátoru objektu.</span><span class="sxs-lookup"><span data-stu-id="9e81e-182">The following code creates an instance of a `Student` class and uses an object initializer to initialize properties.</span></span>  
  
```vb  
Dim student1 As New Student With {.First = "Michael",   
                                  .Last = "Tucker"}  
```  
  
 <span data-ttu-id="9e81e-183">Další informace o inicializátory objektů najdete v tématu [postupy: Deklarace objektu pomocí inicializátoru objektu](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [inicializátory objektů: pojmenované a anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), a [anonymní typy ](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="9e81e-183">For more information about object initializers, see [How to: Declare an Object by Using an Object Initializer](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), and [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="declaring-multiple-variables"></a><span data-ttu-id="9e81e-184">Deklarování více proměnných</span><span class="sxs-lookup"><span data-stu-id="9e81e-184">Declaring Multiple Variables</span></span>  
 <span data-ttu-id="9e81e-185">Je možné deklarovat několik proměnné v rámci jedné deklarace příkazu zadání názvu proměnné pro každé z nich a název každého pole v závorkách.</span><span class="sxs-lookup"><span data-stu-id="9e81e-185">You can declare several variables in one declaration statement, specifying the variable name for each one, and following each array name with parentheses.</span></span> <span data-ttu-id="9e81e-186">Více proměnných jsou oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="9e81e-186">Multiple variables are separated by commas.</span></span>  
  
```vb  
Dim lastTime, nextTime, allTimes() As Date  
```  
  
 <span data-ttu-id="9e81e-187">Pokud je deklarovat více než jednu proměnnou na jednu `As` klauzule, nelze zadat inicializátoru pro tuto skupinu proměnných.</span><span class="sxs-lookup"><span data-stu-id="9e81e-187">If you declare more than one variable with one `As` clause, you cannot supply an initializer for that group of variables.</span></span>  
  
 <span data-ttu-id="9e81e-188">Můžete zadat různé datové typy pro jiné proměnné pomocí samostatné `As` klauzule pro každou proměnnou můžete deklarovat.</span><span class="sxs-lookup"><span data-stu-id="9e81e-188">You can specify different data types for different variables by using a separate `As` clause for each variable you declare.</span></span> <span data-ttu-id="9e81e-189">Každá proměnná má datový typ zadaný v prvním `As` klauzule došlo po jeho `variablename` část.</span><span class="sxs-lookup"><span data-stu-id="9e81e-189">Each variable takes the data type specified in the first `As` clause encountered after its `variablename` part.</span></span>  
  
```vb  
Dim a, b, c As Single, x, y As Double, i As Integer  
' a, b, and c are all Single; x and y are both Double  
```  
  
## <a name="arrays"></a><span data-ttu-id="9e81e-190">Pole</span><span class="sxs-lookup"><span data-stu-id="9e81e-190">Arrays</span></span>  
 <span data-ttu-id="9e81e-191">Je možné deklarovat proměnnou pro uložení *pole*, která může pojmout více hodnot.</span><span class="sxs-lookup"><span data-stu-id="9e81e-191">You can declare a variable to hold an *array*, which can hold multiple values.</span></span> <span data-ttu-id="9e81e-192">Chcete-li určit, že proměnné obsahuje pole, postupujte podle jeho `variablename` okamžitě v závorkách.</span><span class="sxs-lookup"><span data-stu-id="9e81e-192">To specify that a variable holds an array, follow its `variablename` immediately with parentheses.</span></span> <span data-ttu-id="9e81e-193">Další informace o polích najdete v tématu [pole](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="9e81e-193">For more information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="9e81e-194">Můžete zadat dolní a horní mez Každá dimenze pole.</span><span class="sxs-lookup"><span data-stu-id="9e81e-194">You can specify the lower and upper bound of each dimension of an array.</span></span> <span data-ttu-id="9e81e-195">Chcete-li to provést, zahrňte `boundslist` v závorkách.</span><span class="sxs-lookup"><span data-stu-id="9e81e-195">To do this, include a `boundslist` inside the parentheses.</span></span> <span data-ttu-id="9e81e-196">Pro každou dimenzi `boundslist` Určuje horní mez a volitelně dolní hranice.</span><span class="sxs-lookup"><span data-stu-id="9e81e-196">For each dimension, the `boundslist` specifies the upper bound and optionally the lower bound.</span></span> <span data-ttu-id="9e81e-197">Dolní hranice, je vždy nula, a jestli ho zadáte nebo ne.</span><span class="sxs-lookup"><span data-stu-id="9e81e-197">The lower bound is always zero, whether you specify it or not.</span></span> <span data-ttu-id="9e81e-198">Každý index se může lišit od nuly pomocí jeho horní mez hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9e81e-198">Each index can vary from zero through its upper bound value.</span></span>  
  
 <span data-ttu-id="9e81e-199">Následující dva příkazy jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="9e81e-199">The following two statements are equivalent.</span></span> <span data-ttu-id="9e81e-200">Každý příkaz deklaruje pole 21 `Integer` elementy.</span><span class="sxs-lookup"><span data-stu-id="9e81e-200">Each statement declares an array of 21 `Integer` elements.</span></span> <span data-ttu-id="9e81e-201">Pokud získáváte přístup k poli, index se může lišit od 0 do 20.</span><span class="sxs-lookup"><span data-stu-id="9e81e-201">When you access the array, the index can vary from 0 through 20.</span></span>  
  
```vb  
Dim totals(20) As Integer  
Dim totals(0 To 20) As Integer  
```  
  
 <span data-ttu-id="9e81e-202">Následující příkaz deklaruje dvourozměrná pole typu `Double`.</span><span class="sxs-lookup"><span data-stu-id="9e81e-202">The following statement declares a two-dimensional array of type `Double`.</span></span> <span data-ttu-id="9e81e-203">Pole má 6 sloupců (5 + 1) každé 4 řádky (3 + 1).</span><span class="sxs-lookup"><span data-stu-id="9e81e-203">The array has 4 rows (3 + 1) of 6 columns (5 + 1) each.</span></span> <span data-ttu-id="9e81e-204">Všimněte si, že horní mez představuje nejvyšší možná hodnota pro index, nebyl délka dimenze.</span><span class="sxs-lookup"><span data-stu-id="9e81e-204">Note that an upper bound represents the highest possible value for the index, not the length of the dimension.</span></span> <span data-ttu-id="9e81e-205">Délka dimenze je horní mez plus jedna.</span><span class="sxs-lookup"><span data-stu-id="9e81e-205">The length of the dimension is the upper bound plus one.</span></span>  
  
```vb  
Dim matrix2(3, 5) As Double  
```  
  
 <span data-ttu-id="9e81e-206">Pole může mít od 1 do 32 dimenzí.</span><span class="sxs-lookup"><span data-stu-id="9e81e-206">An array can have from 1 to 32 dimensions.</span></span>  
  
 <span data-ttu-id="9e81e-207">Všechny hranice můžete nechat prázdné v deklarace pole.</span><span class="sxs-lookup"><span data-stu-id="9e81e-207">You can leave all the bounds blank in an array declaration.</span></span> <span data-ttu-id="9e81e-208">Pokud to uděláte, pole má počet dimenzí, které zadáte, ale není inicializován.</span><span class="sxs-lookup"><span data-stu-id="9e81e-208">If you do this, the array has the number of dimensions you specify, but it is uninitialized.</span></span> <span data-ttu-id="9e81e-209">Má hodnotu `Nothing` dokud alespoň inicializaci některé z jejích elementů.</span><span class="sxs-lookup"><span data-stu-id="9e81e-209">It has a value of `Nothing` until you initialize at least some of its elements.</span></span> <span data-ttu-id="9e81e-210">`Dim` Příkaz musíte zadat rozsah pro všechny dimenze nebo žádné dimenze.</span><span class="sxs-lookup"><span data-stu-id="9e81e-210">The `Dim` statement must specify bounds either for all dimensions or for no dimensions.</span></span>  
  
```vb  
' Declare an array with blank array bounds.  
Dim messages() As String  
' Initialize the array.  
ReDim messages(4)  
```  
  
 <span data-ttu-id="9e81e-211">Pokud pole má více než jednou dimenzí, je nutné zahrnout čárkami k označení počet dimenzí v závorkách.</span><span class="sxs-lookup"><span data-stu-id="9e81e-211">If the array has more than one dimension, you must include commas between the parentheses to indicate the number of dimensions.</span></span>  
  
```vb  
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte  
```  
  
 <span data-ttu-id="9e81e-212">Je možné deklarovat *nulová délka pole* deklarováním jeden z tohoto pole dimenze mít hodnotu -1.</span><span class="sxs-lookup"><span data-stu-id="9e81e-212">You can declare a *zero-length array* by declaring one of the array's dimensions to be -1.</span></span> <span data-ttu-id="9e81e-213">Proměnné, která obsahuje pole nulovou délkou nemá hodnotu `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="9e81e-213">A variable that holds a zero-length array does not have the value `Nothing`.</span></span> <span data-ttu-id="9e81e-214">Pole s nulovou délkou vyžadují některé běžné funkce runtime jazyka.</span><span class="sxs-lookup"><span data-stu-id="9e81e-214">Zero-length arrays are required by certain common language runtime functions.</span></span> <span data-ttu-id="9e81e-215">Pokud se pokusíte přístup k takové pole, došlo k výjimce modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="9e81e-215">If you try to access such an array, a runtime exception occurs.</span></span> <span data-ttu-id="9e81e-216">Další informace najdete v tématu [pole](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="9e81e-216">For more information, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="9e81e-217">Hodnoty pole lze inicializovat pomocí pole literálu.</span><span class="sxs-lookup"><span data-stu-id="9e81e-217">You can initialize the values of an array by using an array literal.</span></span> <span data-ttu-id="9e81e-218">Chcete-li to provést, uzavřete inicializace hodnoty se složené závorky (`{}`).</span><span class="sxs-lookup"><span data-stu-id="9e81e-218">To do this, surround the initialization values with braces (`{}`).</span></span>  
  
```vb  
Dim longArray() As Long = {0, 1, 2, 3}  
```  
  
 <span data-ttu-id="9e81e-219">Pro vícerozměrná pole je inicializace pro každý samostatný dimenzi uzavřené do složených závorek v vnější dimenzi.</span><span class="sxs-lookup"><span data-stu-id="9e81e-219">For multidimensional arrays, the initialization for each separate dimension is enclosed in braces in the outer dimension.</span></span> <span data-ttu-id="9e81e-220">Elementy jsou určené v řádku hlavní pořadí.</span><span class="sxs-lookup"><span data-stu-id="9e81e-220">The elements are specified in row-major order.</span></span>  
  
```vb  
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}  
```  
  
 <span data-ttu-id="9e81e-221">Další informace o literálech pole najdete v tématu [pole](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="9e81e-221">For more information about array literals, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
##  <a name="default"></a> <span data-ttu-id="9e81e-222">Typy a hodnoty výchozí Data</span><span class="sxs-lookup"><span data-stu-id="9e81e-222">Default Data Types and Values</span></span>  
 <span data-ttu-id="9e81e-223">Následující tabulka popisuje výsledky datový typ a inicializátoru v různých kombinacích `Dim` příkaz.</span><span class="sxs-lookup"><span data-stu-id="9e81e-223">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="9e81e-224">Datový typ zadaný?</span><span class="sxs-lookup"><span data-stu-id="9e81e-224">Data type specified?</span></span>|<span data-ttu-id="9e81e-225">Zadaný inicializační?</span><span class="sxs-lookup"><span data-stu-id="9e81e-225">Initializer specified?</span></span>|<span data-ttu-id="9e81e-226">Příklad</span><span class="sxs-lookup"><span data-stu-id="9e81e-226">Example</span></span>|<span data-ttu-id="9e81e-227">Výsledek</span><span class="sxs-lookup"><span data-stu-id="9e81e-227">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="9e81e-228">Ne</span><span class="sxs-lookup"><span data-stu-id="9e81e-228">No</span></span>|<span data-ttu-id="9e81e-229">Ne</span><span class="sxs-lookup"><span data-stu-id="9e81e-229">No</span></span>|`Dim qty`|<span data-ttu-id="9e81e-230">Pokud [možnost striktní](../../../visual-basic/language-reference/statements/option-strict-statement.md) je vypnuto (výchozí), proměnná je nastavená na `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="9e81e-230">If [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="9e81e-231">Pokud `Option Strict` zapnutý, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="9e81e-231">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="9e81e-232">Ne</span><span class="sxs-lookup"><span data-stu-id="9e81e-232">No</span></span>|<span data-ttu-id="9e81e-233">Ano</span><span class="sxs-lookup"><span data-stu-id="9e81e-233">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="9e81e-234">Pokud [Option Infer –](../../../visual-basic/language-reference/statements/option-infer-statement.md) je na (výchozí), typ inicializátoru proměnné přijímá data.</span><span class="sxs-lookup"><span data-stu-id="9e81e-234">If [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="9e81e-235">V tématu [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="9e81e-235">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="9e81e-236">Pokud `Option Infer` vypnuté a `Option Strict` je vypnutý, nabývá datový typ `Object`.</span><span class="sxs-lookup"><span data-stu-id="9e81e-236">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="9e81e-237">Pokud `Option Infer` vypnuté a `Option Strict` zapnutý, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="9e81e-237">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="9e81e-238">Ano</span><span class="sxs-lookup"><span data-stu-id="9e81e-238">Yes</span></span>|<span data-ttu-id="9e81e-239">Ne</span><span class="sxs-lookup"><span data-stu-id="9e81e-239">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="9e81e-240">Výchozí hodnota pro typ dat je inicializováno proměnnou.</span><span class="sxs-lookup"><span data-stu-id="9e81e-240">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="9e81e-241">Najdete v tabulce dál v této části.</span><span class="sxs-lookup"><span data-stu-id="9e81e-241">See the table later in this section.</span></span>|  
|<span data-ttu-id="9e81e-242">Ano</span><span class="sxs-lookup"><span data-stu-id="9e81e-242">Yes</span></span>|<span data-ttu-id="9e81e-243">Ano</span><span class="sxs-lookup"><span data-stu-id="9e81e-243">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="9e81e-244">Pokud datový typ inicializátoru není převést na zadaný datový typ, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="9e81e-244">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
 <span data-ttu-id="9e81e-245">Pokud zadáte datový typ, ale nezadávejte žádné inicializátoru, Visual Basic inicializuje proměnnou na výchozí hodnotu pro jeho datového typu.</span><span class="sxs-lookup"><span data-stu-id="9e81e-245">If you specify a data type but do not specify an initializer, Visual Basic initializes the variable to the default value for its data type.</span></span> <span data-ttu-id="9e81e-246">Následující tabulka uvádí výchozí hodnoty inicializace.</span><span class="sxs-lookup"><span data-stu-id="9e81e-246">The following table shows the default initialization values.</span></span>  
  
|<span data-ttu-id="9e81e-247">Datový typ</span><span class="sxs-lookup"><span data-stu-id="9e81e-247">Data type</span></span>|<span data-ttu-id="9e81e-248">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="9e81e-248">Default value</span></span>|  
|---|---|  
|<span data-ttu-id="9e81e-249">Všechny číselnými typy (včetně `Byte` a `SByte`)</span><span class="sxs-lookup"><span data-stu-id="9e81e-249">All numeric types (including `Byte` and `SByte`)</span></span>|<span data-ttu-id="9e81e-250">0</span><span class="sxs-lookup"><span data-stu-id="9e81e-250">0</span></span>|  
|`Char`|<span data-ttu-id="9e81e-251">Binární 0</span><span class="sxs-lookup"><span data-stu-id="9e81e-251">Binary 0</span></span>|  
|<span data-ttu-id="9e81e-252">Všechny odkazové typy (včetně `Object`, `String`a všechna pole)</span><span class="sxs-lookup"><span data-stu-id="9e81e-252">All reference types (including `Object`, `String`, and all arrays)</span></span>|`Nothing`|  
|`Boolean`|`False`|  
|`Date`|<span data-ttu-id="9e81e-253">12:00:00 1. ledna roku 1 (01/01/0001 12:00:00 AM)</span><span class="sxs-lookup"><span data-stu-id="9e81e-253">12:00 AM of January 1 of the year 1 (01/01/0001 12:00:00 AM)</span></span>|  
  
 <span data-ttu-id="9e81e-254">Každý prvek strukturou je inicializován, jako by šlo samostatná proměnná.</span><span class="sxs-lookup"><span data-stu-id="9e81e-254">Each element of a structure is initialized as if it were a separate variable.</span></span> <span data-ttu-id="9e81e-255">Pokud deklarovat délka pole, ale není inicializovat jeho prvky, každý prvek je inicializován, jako by šlo samostatná proměnná.</span><span class="sxs-lookup"><span data-stu-id="9e81e-255">If you declare the length of an array but do not initialize its elements, each element is initialized as if it were a separate variable.</span></span>  
  
## <a name="static-local-variable-lifetime"></a><span data-ttu-id="9e81e-256">Statické místní proměnné doba platnosti</span><span class="sxs-lookup"><span data-stu-id="9e81e-256">Static Local Variable Lifetime</span></span>  
 <span data-ttu-id="9e81e-257">A `Static` místní proměnné má delší doba platnosti než procesu, ve kterém je deklarovaná.</span><span class="sxs-lookup"><span data-stu-id="9e81e-257">A `Static` local variable has a longer lifetime than that of the procedure in which it is declared.</span></span> <span data-ttu-id="9e81e-258">Hranice životního cyklu proměnné závisí na kterém je deklarovaná postupu a zda je `Shared`.</span><span class="sxs-lookup"><span data-stu-id="9e81e-258">The boundaries of the variable's lifetime depend on where the procedure is declared and whether it is `Shared`.</span></span>  
  
|<span data-ttu-id="9e81e-259">Deklarace procedur</span><span class="sxs-lookup"><span data-stu-id="9e81e-259">Procedure declaration</span></span>|<span data-ttu-id="9e81e-260">Proměnná inicializována</span><span class="sxs-lookup"><span data-stu-id="9e81e-260">Variable initialized</span></span>|<span data-ttu-id="9e81e-261">Proměnná zastaví existující</span><span class="sxs-lookup"><span data-stu-id="9e81e-261">Variable stops existing</span></span>|  
|---|---|---|  
|<span data-ttu-id="9e81e-262">V modulu</span><span class="sxs-lookup"><span data-stu-id="9e81e-262">In a module</span></span>|<span data-ttu-id="9e81e-263">Při prvním volání procedury</span><span class="sxs-lookup"><span data-stu-id="9e81e-263">The first time the procedure is called</span></span>|<span data-ttu-id="9e81e-264">Pokud váš program zastaví provádění</span><span class="sxs-lookup"><span data-stu-id="9e81e-264">When your program stops execution</span></span>|  
|<span data-ttu-id="9e81e-265">Ve třídě nebo struktuře postup je `Shared`</span><span class="sxs-lookup"><span data-stu-id="9e81e-265">In a class or structure, procedure is `Shared`</span></span>|<span data-ttu-id="9e81e-266">První postup se nazývá na konkrétní instanci nebo na třídu nebo strukturu, sám sebe</span><span class="sxs-lookup"><span data-stu-id="9e81e-266">The first time the procedure is called either on a specific instance or on the class or structure itself</span></span>|<span data-ttu-id="9e81e-267">Pokud váš program zastaví provádění</span><span class="sxs-lookup"><span data-stu-id="9e81e-267">When your program stops execution</span></span>|  
|<span data-ttu-id="9e81e-268">Ve třídě nebo struktuře není postup `Shared`</span><span class="sxs-lookup"><span data-stu-id="9e81e-268">In a class or structure, procedure isn't `Shared`</span></span>|<span data-ttu-id="9e81e-269">První postup se nazývá na konkrétní instanci</span><span class="sxs-lookup"><span data-stu-id="9e81e-269">The first time the procedure is called on a specific instance</span></span>|<span data-ttu-id="9e81e-270">Uvolnění instance pro uvolňování paměti (GC)</span><span class="sxs-lookup"><span data-stu-id="9e81e-270">When the instance is released for garbage collection (GC)</span></span>|  
  
## <a name="attributes-and-modifiers"></a><span data-ttu-id="9e81e-271">Atributy a modifikátory</span><span class="sxs-lookup"><span data-stu-id="9e81e-271">Attributes and Modifiers</span></span>  
 <span data-ttu-id="9e81e-272">Atributy lze použít pouze k členské proměnné, nikoli k lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="9e81e-272">You can apply attributes only to member variables, not to local variables.</span></span> <span data-ttu-id="9e81e-273">Atribut přispívá informace metadat sestavení, která není smysl pro dočasné úložiště, jako je například místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="9e81e-273">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local variables.</span></span>  
  
 <span data-ttu-id="9e81e-274">Na úrovni modulu, nemůžete použít `Static` modifikátor deklarovat členské proměnné.</span><span class="sxs-lookup"><span data-stu-id="9e81e-274">At module level, you cannot use the `Static` modifier to declare member variables.</span></span> <span data-ttu-id="9e81e-275">Na úrovni postup, nemůžete použít `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, nebo žádný přístup modifikátory deklarovat lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="9e81e-275">At procedure level, you cannot use `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, or any access modifiers to declare local variables.</span></span>  
  
 <span data-ttu-id="9e81e-276">Můžete určit, jaký kód můžete přístup k proměnné zadáním `accessmodifier`.</span><span class="sxs-lookup"><span data-stu-id="9e81e-276">You can specify what code can access a variable by supplying an `accessmodifier`.</span></span> <span data-ttu-id="9e81e-277">Třídy a modul výchozí proměnné (mimo libovolná procedura) člena privátní přístup a struktura členské proměnné výchozí nastavení veřejný přístup.</span><span class="sxs-lookup"><span data-stu-id="9e81e-277">Class and module member variables (outside any procedure) default to private access, and structure member variables default to public access.</span></span> <span data-ttu-id="9e81e-278">Můžete nastavit jejich úrovně přístupu s modifikátory přístupu.</span><span class="sxs-lookup"><span data-stu-id="9e81e-278">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="9e81e-279">Modifikátory přístupu nelze použít na lokální proměnné (uvnitř procedury).</span><span class="sxs-lookup"><span data-stu-id="9e81e-279">You cannot use access modifiers on local variables (inside a procedure).</span></span>  
  
 <span data-ttu-id="9e81e-280">Můžete zadat `WithEvents` pouze na členské proměnné, nikoli na lokální proměnné uvnitř procedury.</span><span class="sxs-lookup"><span data-stu-id="9e81e-280">You can specify `WithEvents` only on member variables, not on local variables inside a procedure.</span></span> <span data-ttu-id="9e81e-281">Pokud zadáte `WithEvents`, datový typ proměnné, musí typu určité třídy, ne `Object`.</span><span class="sxs-lookup"><span data-stu-id="9e81e-281">If you specify `WithEvents`, the data type of the variable must be a specific class type, not `Object`.</span></span> <span data-ttu-id="9e81e-282">Nelze deklarovat pole s `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="9e81e-282">You cannot declare an array with `WithEvents`.</span></span> <span data-ttu-id="9e81e-283">Další informace o událostech najdete v tématu [události](../../../visual-basic/programming-guide/language-features/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="9e81e-283">For more information about events, see [Events](../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e81e-284">Kód mimo třída, struktura, modul nebo kvalifikaci název členské proměnné s názvem třídy, struktury nebo modul.</span><span class="sxs-lookup"><span data-stu-id="9e81e-284">Code outside a class, structure, or module must qualify a member variable's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="9e81e-285">Mimo území procedura nebo bloku nemůže odkazovat na žádné místní proměnné v rámci tohoto postupu nebo bloku kódu.</span><span class="sxs-lookup"><span data-stu-id="9e81e-285">Code outside a procedure or block cannot refer to any local variables within that procedure or block.</span></span>  
  
## <a name="releasing-managed-resources"></a><span data-ttu-id="9e81e-286">Uvolnění spravované prostředky</span><span class="sxs-lookup"><span data-stu-id="9e81e-286">Releasing Managed Resources</span></span>  
 <span data-ttu-id="9e81e-287">Uvolňování paměti rozhraní .NET Framework uvolní spravované prostředky bez další kódování z vaší strany.</span><span class="sxs-lookup"><span data-stu-id="9e81e-287">The .NET Framework garbage collector disposes of managed resources without any extra coding on your part.</span></span> <span data-ttu-id="9e81e-288">Ale můžete vynutit vyřazení spravovaných prostředků, místo abyste čekali, bude systém uvolňování.</span><span class="sxs-lookup"><span data-stu-id="9e81e-288">However, you can force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>  
  
 <span data-ttu-id="9e81e-289">Pokud do zvlášť cenné a omezených prostředků (například databáze připojení nebo soubor popisovač) obsahuje třídu, nechcete čekat na další uvolňování paměti pro vyčištění instance třídy, která je již používána.</span><span class="sxs-lookup"><span data-stu-id="9e81e-289">If a class holds onto a particularly valuable and scarce resource (such as a database connection or file handle), you might not want to wait until the next garbage collection to clean up a class instance that's no longer in use.</span></span> <span data-ttu-id="9e81e-290">Třída může implementovat <xref:System.IDisposable> rozhraní a poskytují způsob k uvolnění prostředků než uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="9e81e-290">A class may implement the <xref:System.IDisposable> interface to provide a way to release resources before a garbage collection.</span></span> <span data-ttu-id="9e81e-291">Poskytuje třídu, která implementuje rozhraní `Dispose` metoda, kterou lze volat vynutit cenné prostředky k uvolnění okamžitě.</span><span class="sxs-lookup"><span data-stu-id="9e81e-291">A class that implements that interface exposes a `Dispose` method that can be called to force valuable resources to be released immediately.</span></span>  
  
 <span data-ttu-id="9e81e-292">`Using` Příkaz automatizuje proces získávání prostředku, provádění sadu příkazů a pak uvolnění prostředku.</span><span class="sxs-lookup"><span data-stu-id="9e81e-292">The `Using` statement automates the process of acquiring a resource, executing a set of statements, and then disposing of the resource.</span></span> <span data-ttu-id="9e81e-293">Však musí implementovat prostředku <xref:System.IDisposable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9e81e-293">However, the resource must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="9e81e-294">Další informace najdete v tématu [pomocí příkazu](../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9e81e-294">For more information, see [Using Statement](../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e81e-295">Příklad</span><span class="sxs-lookup"><span data-stu-id="9e81e-295">Example</span></span>  
 <span data-ttu-id="9e81e-296">Následující příklad deklaruje proměnné pomocí `Dim` příkaz s různé možnosti.</span><span class="sxs-lookup"><span data-stu-id="9e81e-296">The following example declares variables by using the `Dim` statement with various options.</span></span>  
  
 [!code-vb[VbVbalrStatements#141](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="9e81e-297">Příklad</span><span class="sxs-lookup"><span data-stu-id="9e81e-297">Example</span></span>  
 <span data-ttu-id="9e81e-298">Následující příklad uvádí prvočísel od 1 do 30.</span><span class="sxs-lookup"><span data-stu-id="9e81e-298">The following example lists the prime numbers between 1 and 30.</span></span> <span data-ttu-id="9e81e-299">Rozsah místních proměnných je popsaná v komentáře kódu.</span><span class="sxs-lookup"><span data-stu-id="9e81e-299">The scope of local variables is described in code comments.</span></span>  
  
 [!code-vb[VbVbalrStatements#142](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="9e81e-300">Příklad</span><span class="sxs-lookup"><span data-stu-id="9e81e-300">Example</span></span>  
 <span data-ttu-id="9e81e-301">V následujícím příkladu `speedValue` proměnné je deklarovaná na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="9e81e-301">In the following example, the `speedValue` variable is declared at the class level.</span></span> <span data-ttu-id="9e81e-302">`Private` – Klíčové slovo se používá k deklaraci proměnnou.</span><span class="sxs-lookup"><span data-stu-id="9e81e-302">The `Private` keyword is used to declare the variable.</span></span> <span data-ttu-id="9e81e-303">Proměnná je přístupná procedurou v `Car` třídy.</span><span class="sxs-lookup"><span data-stu-id="9e81e-303">The variable can be accessed by any procedure in the `Car` class.</span></span>  
  
 [!code-vb[VbVbalrStatements#144](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_3.vb)]  
  
 [!code-vb[VbVbalrStatements#145](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9e81e-304">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e81e-304">See Also</span></span>  
 [<span data-ttu-id="9e81e-305">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="9e81e-305">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="9e81e-306">Příkaz ReDim</span><span class="sxs-lookup"><span data-stu-id="9e81e-306">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="9e81e-307">Příkaz Option Explicit</span><span class="sxs-lookup"><span data-stu-id="9e81e-307">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="9e81e-308">Příkaz Option Infer</span><span class="sxs-lookup"><span data-stu-id="9e81e-308">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [<span data-ttu-id="9e81e-309">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="9e81e-309">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="9e81e-310">Stránka Kompilovat, Návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e81e-310">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [<span data-ttu-id="9e81e-311">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="9e81e-311">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="9e81e-312">Pole</span><span class="sxs-lookup"><span data-stu-id="9e81e-312">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="9e81e-313">Inicializátory objektů: pojmenované a anonymní typy</span><span class="sxs-lookup"><span data-stu-id="9e81e-313">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [<span data-ttu-id="9e81e-314">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="9e81e-314">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="9e81e-315">Inicializátory objektů: pojmenované a anonymní typy</span><span class="sxs-lookup"><span data-stu-id="9e81e-315">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [<span data-ttu-id="9e81e-316">Postupy: Deklarace objektu pomocí inicializátoru objektu</span><span class="sxs-lookup"><span data-stu-id="9e81e-316">How to: Declare an Object by Using an Object Initializer</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)  
 [<span data-ttu-id="9e81e-317">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="9e81e-317">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
