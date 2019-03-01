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
ms.openlocfilehash: 9e2370c1b17bfdf103072ff33bf42c4c77706550
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975196"
---
# <a name="dim-statement-visual-basic"></a><span data-ttu-id="f8a9c-102">Dim – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8a9c-102">Dim Statement (Visual Basic)</span></span>
<span data-ttu-id="f8a9c-103">Deklaruje a přiděluje místo pro jednu nebo více proměnných.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-103">Declares and allocates storage space for one or more variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8a9c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8a9c-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]   
Dim [ WithEvents ] variablelist  
```  
  
## <a name="parts"></a><span data-ttu-id="f8a9c-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="f8a9c-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="f8a9c-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-106">Optional.</span></span> <span data-ttu-id="f8a9c-107">Zobrazit [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="f8a9c-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="f8a9c-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-108">Optional.</span></span> <span data-ttu-id="f8a9c-109">Může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="f8a9c-109">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="f8a9c-110">Public</span><span class="sxs-lookup"><span data-stu-id="f8a9c-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="f8a9c-111">Protected</span><span class="sxs-lookup"><span data-stu-id="f8a9c-111">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="f8a9c-112">Friend</span><span class="sxs-lookup"><span data-stu-id="f8a9c-112">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="f8a9c-113">Private</span><span class="sxs-lookup"><span data-stu-id="f8a9c-113">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   [<span data-ttu-id="f8a9c-114">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="f8a9c-114">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)
    
    - [<span data-ttu-id="f8a9c-115">Private Protected</span><span class="sxs-lookup"><span data-stu-id="f8a9c-115">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)

     <span data-ttu-id="f8a9c-116">Zobrazit [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="f8a9c-116">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `Shared`  
  
     <span data-ttu-id="f8a9c-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-117">Optional.</span></span> <span data-ttu-id="f8a9c-118">Zobrazit [sdílené](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="f8a9c-118">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="f8a9c-119">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-119">Optional.</span></span> <span data-ttu-id="f8a9c-120">Zobrazit [stíny](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="f8a9c-120">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `Static`  
  
     <span data-ttu-id="f8a9c-121">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-121">Optional.</span></span> <span data-ttu-id="f8a9c-122">Zobrazit [statické](../../../visual-basic/language-reference/modifiers/static.md).</span><span class="sxs-lookup"><span data-stu-id="f8a9c-122">See [Static](../../../visual-basic/language-reference/modifiers/static.md).</span></span>  
  
-   `ReadOnly`  
  
     <span data-ttu-id="f8a9c-123">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-123">Optional.</span></span> <span data-ttu-id="f8a9c-124">Zobrazit [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="f8a9c-124">See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
-   `WithEvents`  
  
     <span data-ttu-id="f8a9c-125">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-125">Optional.</span></span> <span data-ttu-id="f8a9c-126">Určuje, že jde o objektových proměnných, které odkazují na instance třídy, která může vyvolat události.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-126">Specifies that these are object variables that refer to instances of a class that can raise events.</span></span> <span data-ttu-id="f8a9c-127">Zobrazit [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).</span><span class="sxs-lookup"><span data-stu-id="f8a9c-127">See [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).</span></span>  
  
-   `variablelist`  
  
     <span data-ttu-id="f8a9c-128">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-128">Required.</span></span> <span data-ttu-id="f8a9c-129">Seznam proměnných, které jsou deklarované v tomto prohlášení.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-129">List of variables being declared in this statement.</span></span>  
  
     `variable [ , variable ... ]`  
  
     <span data-ttu-id="f8a9c-130">Každý `variable` má následující syntaxi a části:</span><span class="sxs-lookup"><span data-stu-id="f8a9c-130">Each `variable` has the following syntax and parts:</span></span>  
  
     <span data-ttu-id="f8a9c-131">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="f8a9c-131">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span></span>  
  
    |<span data-ttu-id="f8a9c-132">Část</span><span class="sxs-lookup"><span data-stu-id="f8a9c-132">Part</span></span>|<span data-ttu-id="f8a9c-133">Popis</span><span class="sxs-lookup"><span data-stu-id="f8a9c-133">Description</span></span>|  
    |---|---|  
    |`variablename`|<span data-ttu-id="f8a9c-134">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-134">Required.</span></span> <span data-ttu-id="f8a9c-135">Název proměnné.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-135">Name of the variable.</span></span> <span data-ttu-id="f8a9c-136">Zobrazit [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="f8a9c-136">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
    |`boundslist`|<span data-ttu-id="f8a9c-137">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-137">Optional.</span></span> <span data-ttu-id="f8a9c-138">Seznam mezí jednotlivých rozměrů proměnné pole.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-138">List of bounds of each dimension of an array variable.</span></span>|  
    |`New`|<span data-ttu-id="f8a9c-139">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-139">Optional.</span></span> <span data-ttu-id="f8a9c-140">Vytvoří novou instanci třídy, když `Dim` spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-140">Creates a new instance of the class when the `Dim` statement runs.</span></span>|  
    |`datatype`|<span data-ttu-id="f8a9c-141">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-141">Optional.</span></span> <span data-ttu-id="f8a9c-142">Datový typ proměnné.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-142">Data type of the variable.</span></span>|  
    |`With`|<span data-ttu-id="f8a9c-143">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-143">Optional.</span></span> <span data-ttu-id="f8a9c-144">Představuje seznam inicializátorů objektů.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-144">Introduces the object initializer list.</span></span>|  
    |`propertyname`|<span data-ttu-id="f8a9c-145">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-145">Optional.</span></span> <span data-ttu-id="f8a9c-146">Název vlastnosti ve třídě provádíte instance.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-146">The name of a property in the class you are making an instance of.</span></span>|  
    |`propinitializer`|<span data-ttu-id="f8a9c-147">Opakovaným načtením vyžadovaným po `propertyname` =.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-147">Required after `propertyname` =.</span></span> <span data-ttu-id="f8a9c-148">Výraz, který je vyhodnocen a přiřazen název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-148">The expression that is evaluated and assigned to the property name.</span></span>|  
    |`initializer`|<span data-ttu-id="f8a9c-149">Nepovinné, pokud `New` není zadán.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-149">Optional if `New` is not specified.</span></span> <span data-ttu-id="f8a9c-150">Výraz, který je vyhodnocen a přiřazen do proměnné při jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-150">Expression that is evaluated and assigned to the variable when it is created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8a9c-151">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f8a9c-151">Remarks</span></span>  
 <span data-ttu-id="f8a9c-152">Kompilátor jazyka Visual Basic používá `Dim` příkaz k určení proměnné datový typ a další informace, jako je například jaké kód může přistupovat k proměnné.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-152">The Visual Basic compiler uses the `Dim` statement to determine the variable's data type and other information, such as what code can access the variable.</span></span> <span data-ttu-id="f8a9c-153">Následující příklad deklaruje proměnnou pro uchování `Integer` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-153">The following example declares a variable to hold an `Integer` value.</span></span>  
  
```vb  
Dim numberOfStudents As Integer  
```  
  
 <span data-ttu-id="f8a9c-154">Můžete zadat libovolný datový typ nebo název výčtu, strukturu, třídu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-154">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
```vb  
Dim finished As Boolean  
Dim monitorBox As System.Windows.Forms.Form  
```  
  
 <span data-ttu-id="f8a9c-155">Pro typ odkazu, je použít `New` – klíčové slovo chcete vytvořit novou instanci třídy nebo struktury, která je určená datového typu.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-155">For a reference type, you use the `New` keyword to create a new instance of the class or structure that is specified by the data type.</span></span> <span data-ttu-id="f8a9c-156">Pokud používáte `New`, je velmi riskantní používat inicializační výraz.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-156">If you use `New`, you do not use an initializer expression.</span></span> <span data-ttu-id="f8a9c-157">Místo toho zadáte argumenty, pokud jsou požadována pro konstruktor třídy, ve kterém vytvoříte proměnnou.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-157">Instead, you supply arguments, if they are required, to the constructor of the class from which you are creating the variable.</span></span>  
  
```vb  
Dim bottomLabel As New System.Windows.Forms.Label  
```  
  
 <span data-ttu-id="f8a9c-158">Můžete deklarovat proměnnou v postupu, blok, třídy, struktury nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-158">You can declare a variable in a procedure, block, class, structure, or module.</span></span> <span data-ttu-id="f8a9c-159">Nelze deklarovat proměnnou ve zdrojovém souboru, obor názvů nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-159">You cannot declare a variable in a source file, namespace, or interface.</span></span> <span data-ttu-id="f8a9c-160">Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="f8a9c-160">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="f8a9c-161">Proměnná, která je deklarována na úrovni modulu mimo všechny procedury, je *členskou proměnnou* nebo *pole*.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-161">A variable that is declared at module level, outside any procedure, is a *member variable* or *field*.</span></span> <span data-ttu-id="f8a9c-162">Členské proměnné jsou v oboru v celém jejich třídy, struktury nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-162">Member variables are in scope throughout their class, structure, or module.</span></span> <span data-ttu-id="f8a9c-163">Proměnná, která je deklarována v úroveň procedury je *lokální proměnná*.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-163">A variable that is declared at procedure level is a *local variable*.</span></span> <span data-ttu-id="f8a9c-164">Lokální proměnné jsou v rozsahu pouze v rámci jejich proceduru nebo blok.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-164">Local variables are in scope only within their procedure or block.</span></span>  
  
 <span data-ttu-id="f8a9c-165">Následující modifikátory přístupu slouží k deklaraci proměnné mimo proceduru: `Public`, `Protected`, `Friend`, `Protected Friend`, a `Private`.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-165">The following access modifiers are used to declare variables outside a procedure: `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private`.</span></span> <span data-ttu-id="f8a9c-166">Další informace najdete v tématu [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="f8a9c-166">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="f8a9c-167">`Dim` – Klíčové slovo je volitelný a obvykle vynechána, pokud je zadána některá z následujících parametrů: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, nebo `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-167">The `Dim` keyword is optional and usually omitted if you specify any of the following modifiers: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, or `WithEvents`.</span></span>  
  
```vb  
Public maximumAllowed As Double  
Protected Friend currentUserName As String  
Private salary As Decimal  
Static runningTotal As Integer  
```  
  
 <span data-ttu-id="f8a9c-168">Pokud `Option Explicit` je zapnuto (výchozí), kompilátor vyžaduje deklaraci pro každou proměnnou můžete použít.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-168">If `Option Explicit` is on (the default), the compiler requires a declaration for every variable you use.</span></span> <span data-ttu-id="f8a9c-169">Další informace najdete v tématu [Option Explicit – příkaz](../../../visual-basic/language-reference/statements/option-explicit-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f8a9c-169">For more information, see [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md).</span></span>  
  
## <a name="specifying-an-initial-value"></a><span data-ttu-id="f8a9c-170">Určení počáteční hodnoty</span><span class="sxs-lookup"><span data-stu-id="f8a9c-170">Specifying an Initial Value</span></span>  
 <span data-ttu-id="f8a9c-171">Přiřadit hodnotu k proměnné při jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-171">You can assign a value to a variable when it is created.</span></span> <span data-ttu-id="f8a9c-172">Pro typ hodnoty, použijete *inicializátor* zadat výraz přiřazovaný proměnné.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-172">For a value type, you use an *initializer* to supply an expression to be assigned to the variable.</span></span> <span data-ttu-id="f8a9c-173">Výraz se musí vyhodnotit na konstantu, která lze vypočítat v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-173">The expression must evaluate to a constant that can be calculated at compile time.</span></span>  
  
```vb  
Dim quantity As Integer = 10  
Dim message As String = "Just started"  
```  
  
 <span data-ttu-id="f8a9c-174">Pokud je zadán inicializátor a není zadaný datový typ v `As` klauzule *odvození typu* je použít k odvození typu dat z inicializátoru.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-174">If an initializer is specified and a data type is not specified in an `As` clause, *type inference* is used to infer the data type from the initializer.</span></span> <span data-ttu-id="f8a9c-175">V následujícím příkladu obě `num1` a `num2` jsou silného typu jako celá čísla.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-175">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span> <span data-ttu-id="f8a9c-176">V deklaraci druhý odvození typu odvodí typ z hodnotu 3.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-176">In the second declaration, type inference infers the type from the value 3.</span></span>  
  
```vb  
' Use explicit typing.  
Dim num1 As Integer = 3  
  
' Use local type inference.  
Dim num2 = 3  
```  
  
 <span data-ttu-id="f8a9c-177">Odvození typu proměnné se vztahuje na úrovni postup.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-177">Type inference applies at the procedure level.</span></span> <span data-ttu-id="f8a9c-178">Nevztahuje se mimo proceduru v třída, struktura, modul nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-178">It does not apply outside a procedure in a class, structure, module, or interface.</span></span> <span data-ttu-id="f8a9c-179">Další informace o odvození typu, najdete v části [Option Infer – příkaz](../../../visual-basic/language-reference/statements/option-infer-statement.md) a [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="f8a9c-179">For more information about type inference, see [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
 <span data-ttu-id="f8a9c-180">Informace o tom, co se stane, když není zadaný datový typ nebo inicializační procedury, naleznete v tématu [výchozí datové typy a hodnoty](../../../visual-basic/language-reference/statements/dim-statement.md#default) dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-180">For information about what happens when a data type or initializer is not specified, see [Default Data Types and Values](../../../visual-basic/language-reference/statements/dim-statement.md#default) later in this topic.</span></span>  
  
 <span data-ttu-id="f8a9c-181">Můžete použít *objektu inicializátoru* deklarovat výskyty pojmenované a anonymní typy.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-181">You can use an *object initializer* to declare instances of named and anonymous types.</span></span> <span data-ttu-id="f8a9c-182">Následující kód vytvoří instanci `Student` třídy a pomocí inicializátoru objektu inicializovat vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-182">The following code creates an instance of a `Student` class and uses an object initializer to initialize properties.</span></span>  
  
```vb  
Dim student1 As New Student With {.First = "Michael",   
                                  .Last = "Tucker"}  
```  
  
 <span data-ttu-id="f8a9c-183">Další informace o inicializátory objektů najdete v tématu [jak: Deklarace objektu pomocí inicializátoru objektu](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [inicializátorech objektu: Pojmenované a anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), a [anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="f8a9c-183">For more information about object initializers, see [How to: Declare an Object by Using an Object Initializer](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), and [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="declaring-multiple-variables"></a><span data-ttu-id="f8a9c-184">Deklarování více proměnných</span><span class="sxs-lookup"><span data-stu-id="f8a9c-184">Declaring Multiple Variables</span></span>  
 <span data-ttu-id="f8a9c-185">Je možné deklarovat několik proměnných v příkazu jednu deklaraci, zadáte název proměnné pro každé z nich a po každé pole názvu v závorkách.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-185">You can declare several variables in one declaration statement, specifying the variable name for each one, and following each array name with parentheses.</span></span> <span data-ttu-id="f8a9c-186">Více proměnných jsou odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-186">Multiple variables are separated by commas.</span></span>  
  
```vb  
Dim lastTime, nextTime, allTimes() As Date  
```  
  
 <span data-ttu-id="f8a9c-187">Je-li deklarována více než jednu proměnnou na jednu `As` klauzule, nelze zadat inicializátor pro tuto skupinu proměnných.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-187">If you declare more than one variable with one `As` clause, you cannot supply an initializer for that group of variables.</span></span>  
  
 <span data-ttu-id="f8a9c-188">Různé datové typy pro různé proměnné můžete určit pomocí samostatné `As` klauzuli pro každou proměnnou můžete deklarovat.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-188">You can specify different data types for different variables by using a separate `As` clause for each variable you declare.</span></span> <span data-ttu-id="f8a9c-189">Každá proměnná má datový typ zadaný v prvním `As` klauzule došlo po jeho `variablename` část.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-189">Each variable takes the data type specified in the first `As` clause encountered after its `variablename` part.</span></span>  
  
```vb  
Dim a, b, c As Single, x, y As Double, i As Integer  
' a, b, and c are all Single; x and y are both Double  
```  
  
## <a name="arrays"></a><span data-ttu-id="f8a9c-190">Pole</span><span class="sxs-lookup"><span data-stu-id="f8a9c-190">Arrays</span></span>  
 <span data-ttu-id="f8a9c-191">Můžete deklarovat proměnnou pro uchování *pole*, který může obsahovat více hodnot.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-191">You can declare a variable to hold an *array*, which can hold multiple values.</span></span> <span data-ttu-id="f8a9c-192">Chcete-li určit, že proměnná obsahuje pole, postupujte podle jeho `variablename` okamžitě se závorkami.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-192">To specify that a variable holds an array, follow its `variablename` immediately with parentheses.</span></span> <span data-ttu-id="f8a9c-193">Další informace o polích naleznete v tématu [pole](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="f8a9c-193">For more information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="f8a9c-194">Můžete zadat dolní a horní mez každé dimenze matice.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-194">You can specify the lower and upper bound of each dimension of an array.</span></span> <span data-ttu-id="f8a9c-195">Chcete-li to provést, patří `boundslist` v závorkách.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-195">To do this, include a `boundslist` inside the parentheses.</span></span> <span data-ttu-id="f8a9c-196">Pro každou dimenzi `boundslist` Určuje horní mez a volitelně dolní mez.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-196">For each dimension, the `boundslist` specifies the upper bound and optionally the lower bound.</span></span> <span data-ttu-id="f8a9c-197">Dolní mez, je vždy nula, a zda ho zadáte nebo ne.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-197">The lower bound is always zero, whether you specify it or not.</span></span> <span data-ttu-id="f8a9c-198">Každý index se může lišit od nuly prostřednictvím její hodnotu horní mez.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-198">Each index can vary from zero through its upper bound value.</span></span>  
  
 <span data-ttu-id="f8a9c-199">Následující dva příkazy jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-199">The following two statements are equivalent.</span></span> <span data-ttu-id="f8a9c-200">Každý příkaz deklaruje pole 21 `Integer` elementy.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-200">Each statement declares an array of 21 `Integer` elements.</span></span> <span data-ttu-id="f8a9c-201">Při přístupu k poli, index se může lišit od 0 do 20.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-201">When you access the array, the index can vary from 0 through 20.</span></span>  
  
```vb  
Dim totals(20) As Integer  
Dim totals(0 To 20) As Integer  
```  
  
 <span data-ttu-id="f8a9c-202">Následující příkaz deklaruje dvourozměrné pole typu `Double`.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-202">The following statement declares a two-dimensional array of type `Double`.</span></span> <span data-ttu-id="f8a9c-203">Pole má 6 sloupců (5 + 1) každé 4 řádky (3 + 1).</span><span class="sxs-lookup"><span data-stu-id="f8a9c-203">The array has 4 rows (3 + 1) of 6 columns (5 + 1) each.</span></span> <span data-ttu-id="f8a9c-204">Všimněte si, že horní mez představuje nejvyšší možnou hodnotu pro index, nikoli velikost rozměru.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-204">Note that an upper bound represents the highest possible value for the index, not the length of the dimension.</span></span> <span data-ttu-id="f8a9c-205">Délka druhého rozměru je horní mez plus jedna.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-205">The length of the dimension is the upper bound plus one.</span></span>  
  
```vb  
Dim matrix2(3, 5) As Double  
```  
  
 <span data-ttu-id="f8a9c-206">Pole může mít 1 až 32 rozměrů.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-206">An array can have from 1 to 32 dimensions.</span></span>  
  
 <span data-ttu-id="f8a9c-207">Můžete ponechat všechny hranice v deklaraci pole prázdné.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-207">You can leave all the bounds blank in an array declaration.</span></span> <span data-ttu-id="f8a9c-208">Pokud to uděláte, pole má počet dimenzí, které zadáte, ale není inicializován.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-208">If you do this, the array has the number of dimensions you specify, but it is uninitialized.</span></span> <span data-ttu-id="f8a9c-209">Má hodnotu `Nothing` dokud inicializovat alespoň některé z jeho prvků.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-209">It has a value of `Nothing` until you initialize at least some of its elements.</span></span> <span data-ttu-id="f8a9c-210">`Dim` Příkaz musí určovat hranice pro všechny dimenze nebo žádné dimenze.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-210">The `Dim` statement must specify bounds either for all dimensions or for no dimensions.</span></span>  
  
```vb  
' Declare an array with blank array bounds.  
Dim messages() As String  
' Initialize the array.  
ReDim messages(4)  
```  
  
 <span data-ttu-id="f8a9c-211">Pokud pole má více než jednou dimenzí, je nutné zahrnout čárek mezi závorky k označení počet rozměrů.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-211">If the array has more than one dimension, you must include commas between the parentheses to indicate the number of dimensions.</span></span>  
  
```vb  
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte  
```  
  
 <span data-ttu-id="f8a9c-212">Je možné deklarovat *pole nulové délky* deklarováním jeden z rozměrů pole jako hodnotu-1.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-212">You can declare a *zero-length array* by declaring one of the array's dimensions to be -1.</span></span> <span data-ttu-id="f8a9c-213">Proměnná, která obsahuje pole s nulovou délkou nemá hodnotu `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-213">A variable that holds a zero-length array does not have the value `Nothing`.</span></span> <span data-ttu-id="f8a9c-214">Některé běžné funkce modulu runtime jazyka vyžaduje pole nulové délky.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-214">Zero-length arrays are required by certain common language runtime functions.</span></span> <span data-ttu-id="f8a9c-215">Pokud se pokusíte o přístup k takové pole, dojde k výjimce modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-215">If you try to access such an array, a runtime exception occurs.</span></span> <span data-ttu-id="f8a9c-216">Další informace najdete v tématu [pole](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="f8a9c-216">For more information, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="f8a9c-217">Inicializovat hodnoty pole pomocí literálu pole.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-217">You can initialize the values of an array by using an array literal.</span></span> <span data-ttu-id="f8a9c-218">K tomuto účelu před a za inicializace hodnoty se závorkami (`{}`).</span><span class="sxs-lookup"><span data-stu-id="f8a9c-218">To do this, surround the initialization values with braces (`{}`).</span></span>  
  
```vb  
Dim longArray() As Long = {0, 1, 2, 3}  
```  
  
 <span data-ttu-id="f8a9c-219">Pro vícerozměrná pole je inicializace pro každou samostatnou dimenzi uzavřeny ve složených závorkách v vnější dimenzi.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-219">For multidimensional arrays, the initialization for each separate dimension is enclosed in braces in the outer dimension.</span></span> <span data-ttu-id="f8a9c-220">Prvky jsou uvedeny v pořadí preferujícím řádek.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-220">The elements are specified in row-major order.</span></span>  
  
```vb  
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}  
```  
  
 <span data-ttu-id="f8a9c-221">Další informace o literály pole, naleznete v tématu [pole](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="f8a9c-221">For more information about array literals, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
##  <a name="default"></a> <span data-ttu-id="f8a9c-222">Výchozí datové typy a hodnoty</span><span class="sxs-lookup"><span data-stu-id="f8a9c-222">Default Data Types and Values</span></span>  
 <span data-ttu-id="f8a9c-223">Následující tabulka popisuje výsledky různých kombinací určující typ dat a obsahuje inicializační proceduru `Dim` příkazu.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-223">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="f8a9c-224">Zadaný datový typ?</span><span class="sxs-lookup"><span data-stu-id="f8a9c-224">Data type specified?</span></span>|<span data-ttu-id="f8a9c-225">Inicializátor zadaný?</span><span class="sxs-lookup"><span data-stu-id="f8a9c-225">Initializer specified?</span></span>|<span data-ttu-id="f8a9c-226">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8a9c-226">Example</span></span>|<span data-ttu-id="f8a9c-227">Výsledek</span><span class="sxs-lookup"><span data-stu-id="f8a9c-227">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="f8a9c-228">Ne</span><span class="sxs-lookup"><span data-stu-id="f8a9c-228">No</span></span>|<span data-ttu-id="f8a9c-229">Ne</span><span class="sxs-lookup"><span data-stu-id="f8a9c-229">No</span></span>|`Dim qty`|<span data-ttu-id="f8a9c-230">Pokud [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) je vypnuto (výchozí), je proměnná nastavena `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-230">If [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="f8a9c-231">Pokud `Option Strict` zapnutý, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-231">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="f8a9c-232">Ne</span><span class="sxs-lookup"><span data-stu-id="f8a9c-232">No</span></span>|<span data-ttu-id="f8a9c-233">Ano</span><span class="sxs-lookup"><span data-stu-id="f8a9c-233">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="f8a9c-234">Pokud [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) je zapnuto (výchozí), zadejte proměnné přijímá data z inicializátoru.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-234">If [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="f8a9c-235">Zobrazit [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="f8a9c-235">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="f8a9c-236">Pokud `Option Infer` je vypnuté a `Option Strict` je vypnuté, nabývá datový typ `Object`.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-236">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="f8a9c-237">Pokud `Option Infer` je vypnuté a `Option Strict` zapnutý, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-237">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="f8a9c-238">Ano</span><span class="sxs-lookup"><span data-stu-id="f8a9c-238">Yes</span></span>|<span data-ttu-id="f8a9c-239">Ne</span><span class="sxs-lookup"><span data-stu-id="f8a9c-239">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="f8a9c-240">Proměnná je inicializována na výchozí hodnotu pro typ dat.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-240">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="f8a9c-241">V tabulce dále v tomto oddílu.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-241">See the table later in this section.</span></span>|  
|<span data-ttu-id="f8a9c-242">Ano</span><span class="sxs-lookup"><span data-stu-id="f8a9c-242">Yes</span></span>|<span data-ttu-id="f8a9c-243">Ano</span><span class="sxs-lookup"><span data-stu-id="f8a9c-243">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="f8a9c-244">Pokud datový typ inicializátor není lze převést na zadaný datový typ, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-244">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
 <span data-ttu-id="f8a9c-245">Pokud zadáte datový typ, ale nezadávejte inicializátor, Visual Basic inicializuje proměnnou na výchozí hodnotu pro jeho datového typu.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-245">If you specify a data type but do not specify an initializer, Visual Basic initializes the variable to the default value for its data type.</span></span> <span data-ttu-id="f8a9c-246">V následující tabulce jsou uvedeny výchozí inicializace hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-246">The following table shows the default initialization values.</span></span>  
  
|<span data-ttu-id="f8a9c-247">Datový typ</span><span class="sxs-lookup"><span data-stu-id="f8a9c-247">Data type</span></span>|<span data-ttu-id="f8a9c-248">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="f8a9c-248">Default value</span></span>|  
|---|---|  
|<span data-ttu-id="f8a9c-249">Všechny číselné typy (včetně `Byte` a `SByte`)</span><span class="sxs-lookup"><span data-stu-id="f8a9c-249">All numeric types (including `Byte` and `SByte`)</span></span>|<span data-ttu-id="f8a9c-250">0</span><span class="sxs-lookup"><span data-stu-id="f8a9c-250">0</span></span>|  
|`Char`|<span data-ttu-id="f8a9c-251">Binární 0</span><span class="sxs-lookup"><span data-stu-id="f8a9c-251">Binary 0</span></span>|  
|<span data-ttu-id="f8a9c-252">Všechny typy odkazů (včetně `Object`, `String`a všechna pole)</span><span class="sxs-lookup"><span data-stu-id="f8a9c-252">All reference types (including `Object`, `String`, and all arrays)</span></span>|`Nothing`|  
|`Boolean`|`False`|  
|`Date`|<span data-ttu-id="f8a9c-253">12:00:00 1. ledna roku 1 (01, 01/0001 12:00:00 AM)</span><span class="sxs-lookup"><span data-stu-id="f8a9c-253">12:00 AM of January 1 of the year 1 (01/01/0001 12:00:00 AM)</span></span>|  
  
 <span data-ttu-id="f8a9c-254">Každý prvek struktury je inicializována, jako by šlo samostatná proměnná.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-254">Each element of a structure is initialized as if it were a separate variable.</span></span> <span data-ttu-id="f8a9c-255">Pokud deklarujete délku pole, ale jeho elementy neinicializujte, každý element je inicializována, jako by šlo samostatná proměnná.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-255">If you declare the length of an array but do not initialize its elements, each element is initialized as if it were a separate variable.</span></span>  
  
## <a name="static-local-variable-lifetime"></a><span data-ttu-id="f8a9c-256">Statické místní proměnné dobu platnosti</span><span class="sxs-lookup"><span data-stu-id="f8a9c-256">Static Local Variable Lifetime</span></span>  
 <span data-ttu-id="f8a9c-257">A `Static` lokální proměnná má delší dobu platnosti než u postupu, ve kterém je deklarována.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-257">A `Static` local variable has a longer lifetime than that of the procedure in which it is declared.</span></span> <span data-ttu-id="f8a9c-258">Hranice životnost proměnné závisí na ve kterém je deklarována jako postup a určuje, zda je `Shared`.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-258">The boundaries of the variable's lifetime depend on where the procedure is declared and whether it is `Shared`.</span></span>  
  
|<span data-ttu-id="f8a9c-259">Deklarace procedury</span><span class="sxs-lookup"><span data-stu-id="f8a9c-259">Procedure declaration</span></span>|<span data-ttu-id="f8a9c-260">Proměnná inicializována</span><span class="sxs-lookup"><span data-stu-id="f8a9c-260">Variable initialized</span></span>|<span data-ttu-id="f8a9c-261">Proměnná přestane existující</span><span class="sxs-lookup"><span data-stu-id="f8a9c-261">Variable stops existing</span></span>|  
|---|---|---|  
|<span data-ttu-id="f8a9c-262">V modulu</span><span class="sxs-lookup"><span data-stu-id="f8a9c-262">In a module</span></span>|<span data-ttu-id="f8a9c-263">Při prvním volání procedury</span><span class="sxs-lookup"><span data-stu-id="f8a9c-263">The first time the procedure is called</span></span>|<span data-ttu-id="f8a9c-264">Když váš program zastaví provádění</span><span class="sxs-lookup"><span data-stu-id="f8a9c-264">When your program stops execution</span></span>|  
|<span data-ttu-id="f8a9c-265">Ve třídě nebo struktuře postup je `Shared`</span><span class="sxs-lookup"><span data-stu-id="f8a9c-265">In a class or structure, procedure is `Shared`</span></span>|<span data-ttu-id="f8a9c-266">Při prvním volání procedury na konkrétní instanci nebo na dané třídy nebo struktury samotné</span><span class="sxs-lookup"><span data-stu-id="f8a9c-266">The first time the procedure is called either on a specific instance or on the class or structure itself</span></span>|<span data-ttu-id="f8a9c-267">Když váš program zastaví provádění</span><span class="sxs-lookup"><span data-stu-id="f8a9c-267">When your program stops execution</span></span>|  
|<span data-ttu-id="f8a9c-268">Ve třídě nebo struktuře není postup `Shared`</span><span class="sxs-lookup"><span data-stu-id="f8a9c-268">In a class or structure, procedure isn't `Shared`</span></span>|<span data-ttu-id="f8a9c-269">Při prvním volání procedury na konkrétní instanci</span><span class="sxs-lookup"><span data-stu-id="f8a9c-269">The first time the procedure is called on a specific instance</span></span>|<span data-ttu-id="f8a9c-270">Uvolnění instance pro uvolňování paměti (GC)</span><span class="sxs-lookup"><span data-stu-id="f8a9c-270">When the instance is released for garbage collection (GC)</span></span>|  
  
## <a name="attributes-and-modifiers"></a><span data-ttu-id="f8a9c-271">Atributy a modifikátory</span><span class="sxs-lookup"><span data-stu-id="f8a9c-271">Attributes and Modifiers</span></span>  
 <span data-ttu-id="f8a9c-272">Můžete použít atributy pouze na členské proměnné, nikoli na lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-272">You can apply attributes only to member variables, not to local variables.</span></span> <span data-ttu-id="f8a9c-273">Atribut přispívá informace metadat sestavení, která není smysl pro dočasné úložiště, jako jsou místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-273">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local variables.</span></span>  
  
 <span data-ttu-id="f8a9c-274">Na úrovni modulu nelze použít `Static` Modifikátor pro deklaraci členské proměnné.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-274">At module level, you cannot use the `Static` modifier to declare member variables.</span></span> <span data-ttu-id="f8a9c-275">Na úrovni postupu nelze použít `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, nebo žádný přístup k modifikátory při deklarování lokálních proměnných.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-275">At procedure level, you cannot use `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, or any access modifiers to declare local variables.</span></span>  
  
 <span data-ttu-id="f8a9c-276">Můžete určit, jaký kód může přistupovat k proměnné zadáním `accessmodifier`.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-276">You can specify what code can access a variable by supplying an `accessmodifier`.</span></span> <span data-ttu-id="f8a9c-277">Třídy a modul členské proměnné (mimo všechny procedury) výchozí privátní přístup a struktura členské proměnné výchozí veřejný přístup.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-277">Class and module member variables (outside any procedure) default to private access, and structure member variables default to public access.</span></span> <span data-ttu-id="f8a9c-278">Můžete nastavit jejich úrovně přístupu modifikátory přístupu.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-278">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="f8a9c-279">Na lokální proměnné (uvnitř procedury) nejde použít modifikátory přístupu.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-279">You cannot use access modifiers on local variables (inside a procedure).</span></span>  
  
 <span data-ttu-id="f8a9c-280">Můžete zadat `WithEvents` pouze na členské proměnné, nikoli na lokálních proměnných uvnitř procedury.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-280">You can specify `WithEvents` only on member variables, not on local variables inside a procedure.</span></span> <span data-ttu-id="f8a9c-281">Pokud zadáte `WithEvents`, datový typ proměnné musí určitý typ třídy, ne `Object`.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-281">If you specify `WithEvents`, the data type of the variable must be a specific class type, not `Object`.</span></span> <span data-ttu-id="f8a9c-282">Nelze deklarovat pole `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-282">You cannot declare an array with `WithEvents`.</span></span> <span data-ttu-id="f8a9c-283">Další informace o událostech najdete v tématu [události](../../../visual-basic/programming-guide/language-features/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="f8a9c-283">For more information about events, see [Events](../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8a9c-284">Kód mimo třídu, strukturu nebo modul musí kvalifikovat název členské proměnné s názvem této třídy, struktury nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-284">Code outside a class, structure, or module must qualify a member variable's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="f8a9c-285">Kód mimo území proceduru nebo blok nemůžou odkazovat na žádné místní proměnné v rámci tohoto postupu nebo blok.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-285">Code outside a procedure or block cannot refer to any local variables within that procedure or block.</span></span>  
  
## <a name="releasing-managed-resources"></a><span data-ttu-id="f8a9c-286">Spravované prostředky</span><span class="sxs-lookup"><span data-stu-id="f8a9c-286">Releasing Managed Resources</span></span>  
 <span data-ttu-id="f8a9c-287">Uvolňování paměti rozhraní .NET Framework uvolní spravované prostředky bez dodatečné kódování z vaší strany.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-287">The .NET Framework garbage collector disposes of managed resources without any extra coding on your part.</span></span> <span data-ttu-id="f8a9c-288">Ale můžete vynutit uvolnění spravovaného prostředku, místo abyste čekali, systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-288">However, you can force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>  
  
 <span data-ttu-id="f8a9c-289">Pokud třída obsahuje do zejména cenných a omezených prostředků (jako je například připojení nebo soubor popisovač databáze), nebudete chtít počkat do dalšího uvolnění pro vyčištění instance třídy, která se už používá.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-289">If a class holds onto a particularly valuable and scarce resource (such as a database connection or file handle), you might not want to wait until the next garbage collection to clean up a class instance that's no longer in use.</span></span> <span data-ttu-id="f8a9c-290">Třída může implementovat <xref:System.IDisposable> rozhraní poskytují způsob k uvolnění prostředků než uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-290">A class may implement the <xref:System.IDisposable> interface to provide a way to release resources before a garbage collection.</span></span> <span data-ttu-id="f8a9c-291">Poskytuje třídu, která implementuje rozhraní `Dispose` metoda, kterou lze volat pro vynucení cenné prostředky okamžitě uvolní.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-291">A class that implements that interface exposes a `Dispose` method that can be called to force valuable resources to be released immediately.</span></span>  
  
 <span data-ttu-id="f8a9c-292">`Using` Příkaz automatizuje proces získání prostředku, provedení sady příkazů a pak uvolnění prostředku.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-292">The `Using` statement automates the process of acquiring a resource, executing a set of statements, and then disposing of the resource.</span></span> <span data-ttu-id="f8a9c-293">Však musí implementovat prostředek <xref:System.IDisposable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-293">However, the resource must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="f8a9c-294">Další informace najdete v tématu [příkazu Using](../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f8a9c-294">For more information, see [Using Statement](../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8a9c-295">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8a9c-295">Example</span></span>  
 <span data-ttu-id="f8a9c-296">Následující příklad proměnné deklarovány s použitím `Dim` příkaz různé možnosti.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-296">The following example declares variables by using the `Dim` statement with various options.</span></span>  
  
 [!code-vb[VbVbalrStatements#141](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#141)]  
  
## <a name="example"></a><span data-ttu-id="f8a9c-297">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8a9c-297">Example</span></span>  
 <span data-ttu-id="f8a9c-298">Následující příklad vypíše prvočísel od 1 do 30.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-298">The following example lists the prime numbers between 1 and 30.</span></span> <span data-ttu-id="f8a9c-299">Obor lokální proměnné jsou popsány v komentářích ke kódu.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-299">The scope of local variables is described in code comments.</span></span>  
  
 [!code-vb[VbVbalrStatements#142](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#142)]  
  
## <a name="example"></a><span data-ttu-id="f8a9c-300">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8a9c-300">Example</span></span>  
 <span data-ttu-id="f8a9c-301">V následujícím příkladu `speedValue` proměnná je deklarovaná na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-301">In the following example, the `speedValue` variable is declared at the class level.</span></span> <span data-ttu-id="f8a9c-302">`Private` – Klíčové slovo se používá k deklaraci proměnné.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-302">The `Private` keyword is used to declare the variable.</span></span> <span data-ttu-id="f8a9c-303">Proměnná je možný přes všechny procedury v `Car` třídy.</span><span class="sxs-lookup"><span data-stu-id="f8a9c-303">The variable can be accessed by any procedure in the `Car` class.</span></span>  
  
 [!code-vb[VbVbalrStatements#144](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#144)]  
  
 [!code-vb[VbVbalrStatements#145](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#145)]  
  
## <a name="see-also"></a><span data-ttu-id="f8a9c-304">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8a9c-304">See also</span></span>
- [<span data-ttu-id="f8a9c-305">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="f8a9c-305">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="f8a9c-306">Příkaz ReDim</span><span class="sxs-lookup"><span data-stu-id="f8a9c-306">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="f8a9c-307">Příkaz Option Explicit</span><span class="sxs-lookup"><span data-stu-id="f8a9c-307">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="f8a9c-308">Příkaz Option Infer</span><span class="sxs-lookup"><span data-stu-id="f8a9c-308">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="f8a9c-309">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="f8a9c-309">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="f8a9c-310">Stránka Kompilovat, Návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8a9c-310">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [<span data-ttu-id="f8a9c-311">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="f8a9c-311">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="f8a9c-312">Pole</span><span class="sxs-lookup"><span data-stu-id="f8a9c-312">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="f8a9c-313">Inicializátory objektů: Pojmenované a anonymní typy</span><span class="sxs-lookup"><span data-stu-id="f8a9c-313">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="f8a9c-314">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="f8a9c-314">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="f8a9c-315">Inicializátory objektů: Pojmenované a anonymní typy</span><span class="sxs-lookup"><span data-stu-id="f8a9c-315">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="f8a9c-316">Postupy: Deklarace objektu pomocí inicializátoru objektů</span><span class="sxs-lookup"><span data-stu-id="f8a9c-316">How to: Declare an Object by Using an Object Initializer</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
- [<span data-ttu-id="f8a9c-317">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="f8a9c-317">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
