---
title: Dim – příkaz
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
ms.openlocfilehash: 1b0c3089c366c417af926c8c0703cea021674432
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744725"
---
# <a name="dim-statement-visual-basic"></a><span data-ttu-id="56e86-102">Dim – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56e86-102">Dim statement (Visual Basic)</span></span>

<span data-ttu-id="56e86-103">Deklaruje a přiděluje prostor úložiště pro jednu nebo více proměnných.</span><span class="sxs-lookup"><span data-stu-id="56e86-103">Declares and allocates storage space for one or more variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="56e86-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56e86-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]
Dim [ WithEvents ] variablelist
```

## <a name="parts"></a><span data-ttu-id="56e86-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="56e86-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="56e86-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="56e86-106">Optional.</span></span> <span data-ttu-id="56e86-107">Viz [seznam atributů](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="56e86-107">See [Attribute List](attribute-list.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="56e86-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="56e86-108">Optional.</span></span> <span data-ttu-id="56e86-109">Může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="56e86-109">Can be one of the following:</span></span>

  - [<span data-ttu-id="56e86-110">Public</span><span class="sxs-lookup"><span data-stu-id="56e86-110">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="56e86-111">Protected</span><span class="sxs-lookup"><span data-stu-id="56e86-111">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="56e86-112">Friend</span><span class="sxs-lookup"><span data-stu-id="56e86-112">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="56e86-113">Private</span><span class="sxs-lookup"><span data-stu-id="56e86-113">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="56e86-114">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="56e86-114">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="56e86-115">Private Protected</span><span class="sxs-lookup"><span data-stu-id="56e86-115">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="56e86-116">Podívejte [se na úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="56e86-116">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `Shared`

  <span data-ttu-id="56e86-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="56e86-117">Optional.</span></span> <span data-ttu-id="56e86-118">Viz [Shared](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="56e86-118">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="56e86-119">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="56e86-119">Optional.</span></span> <span data-ttu-id="56e86-120">Viz [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="56e86-120">See [Shadows](../modifiers/shadows.md).</span></span>

- `Static`

  <span data-ttu-id="56e86-121">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="56e86-121">Optional.</span></span> <span data-ttu-id="56e86-122">Viz [static](../modifiers/static.md).</span><span class="sxs-lookup"><span data-stu-id="56e86-122">See [Static](../modifiers/static.md).</span></span>

- `ReadOnly`

  <span data-ttu-id="56e86-123">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="56e86-123">Optional.</span></span> <span data-ttu-id="56e86-124">Zobrazit [jen pro čtení](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="56e86-124">See [ReadOnly](../modifiers/readonly.md).</span></span>

- `WithEvents`

  <span data-ttu-id="56e86-125">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="56e86-125">Optional.</span></span> <span data-ttu-id="56e86-126">Určuje, že se jedná o objektové proměnné, které odkazují na instance třídy, které mohou vyvolat události.</span><span class="sxs-lookup"><span data-stu-id="56e86-126">Specifies that these are object variables that refer to instances of a class that can raise events.</span></span> <span data-ttu-id="56e86-127">Viz [WithEvents](../modifiers/withevents.md).</span><span class="sxs-lookup"><span data-stu-id="56e86-127">See [WithEvents](../modifiers/withevents.md).</span></span>

- `variablelist`

  <span data-ttu-id="56e86-128">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="56e86-128">Required.</span></span> <span data-ttu-id="56e86-129">Seznam proměnných, které jsou deklarovány v tomto příkazu.</span><span class="sxs-lookup"><span data-stu-id="56e86-129">List of variables being declared in this statement.</span></span>

  `variable [ , variable ... ]`

  <span data-ttu-id="56e86-130">Každý `variable` má následující syntaxi a části:</span><span class="sxs-lookup"><span data-stu-id="56e86-130">Each `variable` has the following syntax and parts:</span></span>

  <span data-ttu-id="56e86-131">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="56e86-131">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span></span>

  |<span data-ttu-id="56e86-132">Částí</span><span class="sxs-lookup"><span data-stu-id="56e86-132">Part</span></span>|<span data-ttu-id="56e86-133">Popis</span><span class="sxs-lookup"><span data-stu-id="56e86-133">Description</span></span>|
  |---|---|
  |`variablename`|<span data-ttu-id="56e86-134">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="56e86-134">Required.</span></span> <span data-ttu-id="56e86-135">Název proměnné</span><span class="sxs-lookup"><span data-stu-id="56e86-135">Name of the variable.</span></span> <span data-ttu-id="56e86-136">Viz [deklarované názvy elementů](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="56e86-136">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
  |`boundslist`|<span data-ttu-id="56e86-137">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="56e86-137">Optional.</span></span> <span data-ttu-id="56e86-138">Seznam mezí jednotlivých dimenzí proměnné pole</span><span class="sxs-lookup"><span data-stu-id="56e86-138">List of bounds of each dimension of an array variable.</span></span>|
  |`New`|<span data-ttu-id="56e86-139">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="56e86-139">Optional.</span></span> <span data-ttu-id="56e86-140">Vytvoří novou instanci třídy při spuštění příkazu `Dim`.</span><span class="sxs-lookup"><span data-stu-id="56e86-140">Creates a new instance of the class when the `Dim` statement runs.</span></span>|
  |`datatype`|<span data-ttu-id="56e86-141">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="56e86-141">Optional.</span></span> <span data-ttu-id="56e86-142">Datový typ proměnné</span><span class="sxs-lookup"><span data-stu-id="56e86-142">Data type of the variable.</span></span>|
  |`With`|<span data-ttu-id="56e86-143">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="56e86-143">Optional.</span></span> <span data-ttu-id="56e86-144">Zavádí seznam inicializátorů objektů.</span><span class="sxs-lookup"><span data-stu-id="56e86-144">Introduces the object initializer list.</span></span>|
  |`propertyname`|<span data-ttu-id="56e86-145">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="56e86-145">Optional.</span></span> <span data-ttu-id="56e86-146">Název vlastnosti ve třídě, pro kterou vytváříte instanci.</span><span class="sxs-lookup"><span data-stu-id="56e86-146">The name of a property in the class you are making an instance of.</span></span>|
  |`propinitializer`|<span data-ttu-id="56e86-147">Vyžadováno po `propertyname` =.</span><span class="sxs-lookup"><span data-stu-id="56e86-147">Required after `propertyname` =.</span></span> <span data-ttu-id="56e86-148">Výraz, který je vyhodnocen a přiřazen k názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="56e86-148">The expression that is evaluated and assigned to the property name.</span></span>|
  |`initializer`|<span data-ttu-id="56e86-149">Volitelné, pokud není zadán `New`.</span><span class="sxs-lookup"><span data-stu-id="56e86-149">Optional if `New` is not specified.</span></span> <span data-ttu-id="56e86-150">Výraz, který je vyhodnocen a přiřazen k proměnné při jejím vytvoření.</span><span class="sxs-lookup"><span data-stu-id="56e86-150">Expression that is evaluated and assigned to the variable when it is created.</span></span>|

## <a name="remarks"></a><span data-ttu-id="56e86-151">Poznámky</span><span class="sxs-lookup"><span data-stu-id="56e86-151">Remarks</span></span>

<span data-ttu-id="56e86-152">Kompilátor Visual Basic používá příkaz `Dim` k určení datového typu proměnné a dalších informací, jako je například jaký kód má přístup k proměnné.</span><span class="sxs-lookup"><span data-stu-id="56e86-152">The Visual Basic compiler uses the `Dim` statement to determine the variable's data type and other information, such as what code can access the variable.</span></span> <span data-ttu-id="56e86-153">Následující příklad deklaruje proměnnou pro uchování `Integer` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="56e86-153">The following example declares a variable to hold an `Integer` value.</span></span>

```vb
Dim numberOfStudents As Integer
```

<span data-ttu-id="56e86-154">Můžete zadat libovolný datový typ nebo název výčtu, struktury, třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="56e86-154">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>

```vb
Dim finished As Boolean
Dim monitorBox As System.Windows.Forms.Form
```

<span data-ttu-id="56e86-155">Pro typ odkazu použijete klíčové slovo `New` k vytvoření nové instance třídy nebo struktury, která je určena datovým typem.</span><span class="sxs-lookup"><span data-stu-id="56e86-155">For a reference type, you use the `New` keyword to create a new instance of the class or structure that is specified by the data type.</span></span> <span data-ttu-id="56e86-156">Použijete-li `New`, nepoužijete výraz inicializátoru.</span><span class="sxs-lookup"><span data-stu-id="56e86-156">If you use `New`, you do not use an initializer expression.</span></span> <span data-ttu-id="56e86-157">Místo toho zadáte argumenty, pokud jsou požadovány, do konstruktoru třídy, ze které vytváříte proměnnou.</span><span class="sxs-lookup"><span data-stu-id="56e86-157">Instead, you supply arguments, if they are required, to the constructor of the class from which you are creating the variable.</span></span>

```vb
Dim bottomLabel As New System.Windows.Forms.Label
```

<span data-ttu-id="56e86-158">Proměnnou lze deklarovat v proceduře, bloku, třídě, struktuře nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="56e86-158">You can declare a variable in a procedure, block, class, structure, or module.</span></span> <span data-ttu-id="56e86-159">Nelze deklarovat proměnnou ve zdrojovém souboru, oboru názvů nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="56e86-159">You cannot declare a variable in a source file, namespace, or interface.</span></span> <span data-ttu-id="56e86-160">Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="56e86-160">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="56e86-161">Proměnná deklarovaná na úrovni modulu, mimo jakoukoli proceduru, je *členskou proměnnou* nebo *polem*.</span><span class="sxs-lookup"><span data-stu-id="56e86-161">A variable that is declared at module level, outside any procedure, is a *member variable* or *field*.</span></span> <span data-ttu-id="56e86-162">Členské proměnné jsou v oboru v rámci své třídy, struktury nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="56e86-162">Member variables are in scope throughout their class, structure, or module.</span></span> <span data-ttu-id="56e86-163">Proměnná, která je deklarována na úrovni procedury, je *místní proměnná*.</span><span class="sxs-lookup"><span data-stu-id="56e86-163">A variable that is declared at procedure level is a *local variable*.</span></span> <span data-ttu-id="56e86-164">Lokální proměnné jsou v oboru pouze v rámci jejich procedury nebo bloku.</span><span class="sxs-lookup"><span data-stu-id="56e86-164">Local variables are in scope only within their procedure or block.</span></span>

<span data-ttu-id="56e86-165">Následující modifikátory přístupu se používají k deklarování proměnných mimo proceduru: `Public`, `Protected`, `Friend`, `Protected Friend`a `Private`.</span><span class="sxs-lookup"><span data-stu-id="56e86-165">The following access modifiers are used to declare variables outside a procedure: `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private`.</span></span> <span data-ttu-id="56e86-166">Další informace najdete v tématu [úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="56e86-166">For more information, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="56e86-167">Klíčové slovo `Dim` je nepovinné a obvykle se vynechává, pokud zadáte některý z následujících modifikátorů: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`nebo `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="56e86-167">The `Dim` keyword is optional and usually omitted if you specify any of the following modifiers: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, or `WithEvents`.</span></span>

```vb
Public maximumAllowed As Double
Protected Friend currentUserName As String
Private salary As Decimal
Static runningTotal As Integer
```

<span data-ttu-id="56e86-168">Pokud je `Option Explicit` zapnuto (výchozí), kompilátor vyžaduje deklaraci pro každou proměnnou, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="56e86-168">If `Option Explicit` is on (the default), the compiler requires a declaration for every variable you use.</span></span> <span data-ttu-id="56e86-169">Další informace naleznete v tématu [Option Explicit – příkaz](option-explicit-statement.md).</span><span class="sxs-lookup"><span data-stu-id="56e86-169">For more information, see [Option Explicit Statement](option-explicit-statement.md).</span></span>

## <a name="specifying-an-initial-value"></a><span data-ttu-id="56e86-170">Určení počáteční hodnoty</span><span class="sxs-lookup"><span data-stu-id="56e86-170">Specifying an initial value</span></span>

<span data-ttu-id="56e86-171">Můžete přiřadit hodnotu proměnné při jejím vytvoření.</span><span class="sxs-lookup"><span data-stu-id="56e86-171">You can assign a value to a variable when it is created.</span></span> <span data-ttu-id="56e86-172">Pro typ hodnoty použijete *inicializátor* k zadání výrazu, který má být přiřazen proměnné.</span><span class="sxs-lookup"><span data-stu-id="56e86-172">For a value type, you use an *initializer* to supply an expression to be assigned to the variable.</span></span> <span data-ttu-id="56e86-173">Výraz se musí vyhodnotit na konstantu, kterou lze vypočítat v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="56e86-173">The expression must evaluate to a constant that can be calculated at compile time.</span></span>

```vb
Dim quantity As Integer = 10
Dim message As String = "Just started"
```

<span data-ttu-id="56e86-174">Pokud je určen inicializátor a datový typ není zadán v klauzuli `As`, je použita *odvození typu* pro odvození datového typu z inicializátoru.</span><span class="sxs-lookup"><span data-stu-id="56e86-174">If an initializer is specified and a data type is not specified in an `As` clause, *type inference* is used to infer the data type from the initializer.</span></span> <span data-ttu-id="56e86-175">V následujícím příkladu jsou `num1` i `num2` silně typované jako celá čísla.</span><span class="sxs-lookup"><span data-stu-id="56e86-175">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span> <span data-ttu-id="56e86-176">Ve druhé deklaraci typu odvození typu odvodí typ z hodnoty 3.</span><span class="sxs-lookup"><span data-stu-id="56e86-176">In the second declaration, type inference infers the type from the value 3.</span></span>

```vb
' Use explicit typing.
Dim num1 As Integer = 3

' Use local type inference.
Dim num2 = 3
```

<span data-ttu-id="56e86-177">Odvození typu se vztahuje na úroveň procedury.</span><span class="sxs-lookup"><span data-stu-id="56e86-177">Type inference applies at the procedure level.</span></span> <span data-ttu-id="56e86-178">Nevztahuje se mimo proceduru ve třídě, struktuře, modulu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="56e86-178">It does not apply outside a procedure in a class, structure, module, or interface.</span></span> <span data-ttu-id="56e86-179">Další informace o odvození typu naleznete v tématu [Option include Statement](option-infer-statement.md) a [místní typ odvození](../../programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="56e86-179">For more information about type inference, see [Option Infer Statement](option-infer-statement.md) and [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span>

<span data-ttu-id="56e86-180">Informace o tom, co se stane, když není zadán datový typ nebo inicializátor, naleznete v části [výchozí datové typy a hodnoty](dim-statement.md#default) dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="56e86-180">For information about what happens when a data type or initializer is not specified, see [Default Data Types and Values](dim-statement.md#default) later in this topic.</span></span>

<span data-ttu-id="56e86-181">Můžete použít *inicializátor objektu* pro deklaraci instancí pojmenovaného a anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="56e86-181">You can use an *object initializer* to declare instances of named and anonymous types.</span></span> <span data-ttu-id="56e86-182">Následující kód vytvoří instanci třídy `Student` a k inicializaci vlastností používá inicializátor objektu.</span><span class="sxs-lookup"><span data-stu-id="56e86-182">The following code creates an instance of a `Student` class and uses an object initializer to initialize properties.</span></span>

```vb
Dim student1 As New Student With {.First = "Michael",
                                  .Last = "Tucker"}
```

<span data-ttu-id="56e86-183">Další informace o inicializátorech objektů naleznete v tématu [How to: Declare a Object Using](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)a inicializátor Object, [Inicializátory objektů: pojmenované a anonymní typy](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)a [anonymní typy](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="56e86-183">For more information about object initializers, see [How to: Declare an Object by Using an Object Initializer](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [Object Initializers: Named and Anonymous Types](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), and [Anonymous Types](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>

## <a name="declaring-multiple-variables"></a><span data-ttu-id="56e86-184">Deklarace více proměnných</span><span class="sxs-lookup"><span data-stu-id="56e86-184">Declaring multiple variables</span></span>

<span data-ttu-id="56e86-185">Můžete deklarovat několik proměnných v jednom příkazu deklarace, zadat název proměnné pro každý z nich a za každým názvem pole pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="56e86-185">You can declare several variables in one declaration statement, specifying the variable name for each one, and following each array name with parentheses.</span></span> <span data-ttu-id="56e86-186">Více proměnných je odděleno čárkami.</span><span class="sxs-lookup"><span data-stu-id="56e86-186">Multiple variables are separated by commas.</span></span>

```vb
Dim lastTime, nextTime, allTimes() As Date
```

<span data-ttu-id="56e86-187">Pokud deklarujete více než jednu proměnnou s jednou `As` klauzulí, nemůžete pro tuto skupinu proměnných dodat inicializátor.</span><span class="sxs-lookup"><span data-stu-id="56e86-187">If you declare more than one variable with one `As` clause, you cannot supply an initializer for that group of variables.</span></span>

<span data-ttu-id="56e86-188">Pro každou proměnnou, kterou deklarujete, můžete určit různé typy dat pro různé proměnné pomocí samostatné klauzule `As`.</span><span class="sxs-lookup"><span data-stu-id="56e86-188">You can specify different data types for different variables by using a separate `As` clause for each variable you declare.</span></span> <span data-ttu-id="56e86-189">Každá proměnná přebírá datový typ zadaný v první klauzuli `As`, který se objevil po jeho `variablename` část.</span><span class="sxs-lookup"><span data-stu-id="56e86-189">Each variable takes the data type specified in the first `As` clause encountered after its `variablename` part.</span></span>

```vb
Dim a, b, c As Single, x, y As Double, i As Integer
' a, b, and c are all Single; x and y are both Double
```

## <a name="arrays"></a><span data-ttu-id="56e86-190">Pole</span><span class="sxs-lookup"><span data-stu-id="56e86-190">Arrays</span></span>

<span data-ttu-id="56e86-191">Můžete deklarovat proměnnou pro uchování *pole*, které může obsahovat více hodnot.</span><span class="sxs-lookup"><span data-stu-id="56e86-191">You can declare a variable to hold an *array*, which can hold multiple values.</span></span> <span data-ttu-id="56e86-192">Chcete-li určit, že proměnná obsahuje pole, postupujte podle `variablename` hned pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="56e86-192">To specify that a variable holds an array, follow its `variablename` immediately with parentheses.</span></span> <span data-ttu-id="56e86-193">Další informace o polích naleznete v tématu [Arrays](../../programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="56e86-193">For more information about arrays, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>

<span data-ttu-id="56e86-194">Můžete zadat dolní a horní mez každého rozměru pole.</span><span class="sxs-lookup"><span data-stu-id="56e86-194">You can specify the lower and upper bound of each dimension of an array.</span></span> <span data-ttu-id="56e86-195">Chcete-li to provést, zahrňte `boundslist` do závorek.</span><span class="sxs-lookup"><span data-stu-id="56e86-195">To do this, include a `boundslist` inside the parentheses.</span></span> <span data-ttu-id="56e86-196">Pro každou dimenzi `boundslist` určuje horní mez a volitelně i dolní mez.</span><span class="sxs-lookup"><span data-stu-id="56e86-196">For each dimension, the `boundslist` specifies the upper bound and optionally the lower bound.</span></span> <span data-ttu-id="56e86-197">Dolní mez je vždycky nulová, ať už ji zadáte, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="56e86-197">The lower bound is always zero, whether you specify it or not.</span></span> <span data-ttu-id="56e86-198">Každý index se může od nuly pohybovat od hodnoty horní meze.</span><span class="sxs-lookup"><span data-stu-id="56e86-198">Each index can vary from zero through its upper bound value.</span></span>

<span data-ttu-id="56e86-199">Následující dva příkazy jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="56e86-199">The following two statements are equivalent.</span></span> <span data-ttu-id="56e86-200">Každý příkaz deklaruje pole 21 `Integer` prvků.</span><span class="sxs-lookup"><span data-stu-id="56e86-200">Each statement declares an array of 21 `Integer` elements.</span></span> <span data-ttu-id="56e86-201">Když přistupujete k poli, index se může lišit od 0 do 20.</span><span class="sxs-lookup"><span data-stu-id="56e86-201">When you access the array, the index can vary from 0 through 20.</span></span>

```vb
Dim totals(20) As Integer
Dim totals(0 To 20) As Integer
```

<span data-ttu-id="56e86-202">Následující příkaz deklaruje dvojrozměrné pole typu `Double`.</span><span class="sxs-lookup"><span data-stu-id="56e86-202">The following statement declares a two-dimensional array of type `Double`.</span></span> <span data-ttu-id="56e86-203">Pole má 4 řádky (3 + 1) z 6 sloupců (5 + 1).</span><span class="sxs-lookup"><span data-stu-id="56e86-203">The array has 4 rows (3 + 1) of 6 columns (5 + 1) each.</span></span> <span data-ttu-id="56e86-204">Všimněte si, že horní mez představuje nejvyšší možnou hodnotu indexu, nikoli délku dimenze.</span><span class="sxs-lookup"><span data-stu-id="56e86-204">Note that an upper bound represents the highest possible value for the index, not the length of the dimension.</span></span> <span data-ttu-id="56e86-205">Délka dimenze je horní mez plus jedna.</span><span class="sxs-lookup"><span data-stu-id="56e86-205">The length of the dimension is the upper bound plus one.</span></span>

```vb
Dim matrix2(3, 5) As Double
```

<span data-ttu-id="56e86-206">Pole může mít 1 až 32 dimenzí.</span><span class="sxs-lookup"><span data-stu-id="56e86-206">An array can have from 1 to 32 dimensions.</span></span>

<span data-ttu-id="56e86-207">V deklaraci pole můžete ponechat všechny meze prázdné.</span><span class="sxs-lookup"><span data-stu-id="56e86-207">You can leave all the bounds blank in an array declaration.</span></span> <span data-ttu-id="56e86-208">Pokud to uděláte, pole má počet dimenzí, které zadáte, ale není inicializovaný.</span><span class="sxs-lookup"><span data-stu-id="56e86-208">If you do this, the array has the number of dimensions you specify, but it is uninitialized.</span></span> <span data-ttu-id="56e86-209">Má hodnotu `Nothing`, dokud neinicializujete alespoň některé z jeho prvků.</span><span class="sxs-lookup"><span data-stu-id="56e86-209">It has a value of `Nothing` until you initialize at least some of its elements.</span></span> <span data-ttu-id="56e86-210">Příkaz `Dim` musí určovat meze buď pro všechny dimenze, nebo pro žádné dimenze.</span><span class="sxs-lookup"><span data-stu-id="56e86-210">The `Dim` statement must specify bounds either for all dimensions or for no dimensions.</span></span>

```vb
' Declare an array with blank array bounds.
Dim messages() As String
' Initialize the array.
ReDim messages(4)
```

<span data-ttu-id="56e86-211">Pokud má pole více než jednu dimenzi, je nutné zahrnout čárky mezi závorky, které označují počet rozměrů.</span><span class="sxs-lookup"><span data-stu-id="56e86-211">If the array has more than one dimension, you must include commas between the parentheses to indicate the number of dimensions.</span></span>

```vb
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte
```

<span data-ttu-id="56e86-212">*Pole s nulovou délkou* můžete deklarovat deklarováním jednoho z dimenzí pole, které je-1.</span><span class="sxs-lookup"><span data-stu-id="56e86-212">You can declare a *zero-length array* by declaring one of the array's dimensions to be -1.</span></span> <span data-ttu-id="56e86-213">Proměnná, která obsahuje pole s nulovou délkou, nemá hodnotu `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="56e86-213">A variable that holds a zero-length array does not have the value `Nothing`.</span></span> <span data-ttu-id="56e86-214">Pole s nulovou délkou jsou vyžadovány některými funkcemi modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="56e86-214">Zero-length arrays are required by certain common language runtime functions.</span></span> <span data-ttu-id="56e86-215">Pokud se pokusíte o přístup k takovému poli, dojde k výjimce modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="56e86-215">If you try to access such an array, a runtime exception occurs.</span></span> <span data-ttu-id="56e86-216">Další informace naleznete v tématu [pole](../../programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="56e86-216">For more information, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>

<span data-ttu-id="56e86-217">Hodnoty pole lze inicializovat pomocí literálu pole.</span><span class="sxs-lookup"><span data-stu-id="56e86-217">You can initialize the values of an array by using an array literal.</span></span> <span data-ttu-id="56e86-218">Provedete to tak, že tyto inicializační hodnoty uzavřete do složených závorek (`{}`).</span><span class="sxs-lookup"><span data-stu-id="56e86-218">To do this, surround the initialization values with braces (`{}`).</span></span>

```vb
Dim longArray() As Long = {0, 1, 2, 3}
```

<span data-ttu-id="56e86-219">Pro multidimenzionální pole je inicializace pro každou samostatnou dimenzi uzavřena do složených závorek ve vnější dimenzi.</span><span class="sxs-lookup"><span data-stu-id="56e86-219">For multidimensional arrays, the initialization for each separate dimension is enclosed in braces in the outer dimension.</span></span> <span data-ttu-id="56e86-220">Prvky jsou uvedeny v pořadí podle hlavní řady.</span><span class="sxs-lookup"><span data-stu-id="56e86-220">The elements are specified in row-major order.</span></span>

```vb
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}
```

<span data-ttu-id="56e86-221">Další informace o literálech pole naleznete v tématu [Arrays](../../programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="56e86-221">For more information about array literals, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>

## <a name="default"></a><span data-ttu-id="56e86-222">Výchozí datové typy a hodnoty</span><span class="sxs-lookup"><span data-stu-id="56e86-222">Default data types and values</span></span>

<span data-ttu-id="56e86-223">Následující tabulka popisuje výsledky různých kombinací určení datového typu a inicializátoru v příkazu `Dim`.</span><span class="sxs-lookup"><span data-stu-id="56e86-223">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>

|<span data-ttu-id="56e86-224">Byl zadán datový typ?</span><span class="sxs-lookup"><span data-stu-id="56e86-224">Data type specified?</span></span>|<span data-ttu-id="56e86-225">Byl určen inicializátor?</span><span class="sxs-lookup"><span data-stu-id="56e86-225">Initializer specified?</span></span>|<span data-ttu-id="56e86-226">Příklad</span><span class="sxs-lookup"><span data-stu-id="56e86-226">Example</span></span>|<span data-ttu-id="56e86-227">Výsledek</span><span class="sxs-lookup"><span data-stu-id="56e86-227">Result</span></span>|
|---|---|---|---|
|<span data-ttu-id="56e86-228">Ne</span><span class="sxs-lookup"><span data-stu-id="56e86-228">No</span></span>|<span data-ttu-id="56e86-229">Ne</span><span class="sxs-lookup"><span data-stu-id="56e86-229">No</span></span>|`Dim qty`|<span data-ttu-id="56e86-230">Pokud je [možnost Option Strict](option-strict-statement.md) vypnutá (výchozí nastavení), proměnná je nastavená na `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="56e86-230">If [Option Strict](option-strict-statement.md) is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="56e86-231">Pokud je `Option Strict` zapnutý, dojde k chybě při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="56e86-231">If `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="56e86-232">Ne</span><span class="sxs-lookup"><span data-stu-id="56e86-232">No</span></span>|<span data-ttu-id="56e86-233">Ano</span><span class="sxs-lookup"><span data-stu-id="56e86-233">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="56e86-234">Pokud je nastavená [možnost odvodit](option-infer-statement.md) (výchozí), proměnná vezme datový typ inicializátoru.</span><span class="sxs-lookup"><span data-stu-id="56e86-234">If [Option Infer](option-infer-statement.md) is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="56e86-235">Viz [odvození místního typu](../../programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="56e86-235">See [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="56e86-236">Pokud je `Option Infer` vypnuto a `Option Strict` je vypnutý, proměnná převezme datový typ `Object`.</span><span class="sxs-lookup"><span data-stu-id="56e86-236">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="56e86-237">Pokud je `Option Infer` vypnuto a `Option Strict` je zapnutá, dojde k chybě při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="56e86-237">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="56e86-238">Ano</span><span class="sxs-lookup"><span data-stu-id="56e86-238">Yes</span></span>|<span data-ttu-id="56e86-239">Ne</span><span class="sxs-lookup"><span data-stu-id="56e86-239">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="56e86-240">Proměnná je inicializována na výchozí hodnotu pro datový typ.</span><span class="sxs-lookup"><span data-stu-id="56e86-240">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="56e86-241">Další informace najdete v tabulce dále v této části.</span><span class="sxs-lookup"><span data-stu-id="56e86-241">See the table later in this section.</span></span>|
|<span data-ttu-id="56e86-242">Ano</span><span class="sxs-lookup"><span data-stu-id="56e86-242">Yes</span></span>|<span data-ttu-id="56e86-243">Ano</span><span class="sxs-lookup"><span data-stu-id="56e86-243">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="56e86-244">Pokud datový typ inicializátoru nelze převést na zadaný datový typ, dojde k chybě při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="56e86-244">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|

<span data-ttu-id="56e86-245">Zadáte-li datový typ, ale nezadáte inicializátor, Visual Basic inicializuje proměnnou na výchozí hodnotu pro svůj datový typ.</span><span class="sxs-lookup"><span data-stu-id="56e86-245">If you specify a data type but do not specify an initializer, Visual Basic initializes the variable to the default value for its data type.</span></span> <span data-ttu-id="56e86-246">V následující tabulce jsou uvedeny výchozí inicializační hodnoty.</span><span class="sxs-lookup"><span data-stu-id="56e86-246">The following table shows the default initialization values.</span></span>

|<span data-ttu-id="56e86-247">Datový typ</span><span class="sxs-lookup"><span data-stu-id="56e86-247">Data type</span></span>|<span data-ttu-id="56e86-248">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="56e86-248">Default value</span></span>|
|---|---|
|<span data-ttu-id="56e86-249">Všechny číselné typy (včetně `Byte` a `SByte`)</span><span class="sxs-lookup"><span data-stu-id="56e86-249">All numeric types (including `Byte` and `SByte`)</span></span>|<span data-ttu-id="56e86-250">0</span><span class="sxs-lookup"><span data-stu-id="56e86-250">0</span></span>|
|`Char`|<span data-ttu-id="56e86-251">Binární hodnota 0</span><span class="sxs-lookup"><span data-stu-id="56e86-251">Binary 0</span></span>|
|<span data-ttu-id="56e86-252">Všechny typy odkazů (včetně `Object`, `String`a všech polí)</span><span class="sxs-lookup"><span data-stu-id="56e86-252">All reference types (including `Object`, `String`, and all arrays)</span></span>|`Nothing`|
|`Boolean`|`False`|
|`Date`|<span data-ttu-id="56e86-253">12:00 z 1. ledna v roce 1 (01/01/0001 12:00:00 dop.)</span><span class="sxs-lookup"><span data-stu-id="56e86-253">12:00 AM of January 1 of the year 1 (01/01/0001 12:00:00 AM)</span></span>|

<span data-ttu-id="56e86-254">Každý prvek struktury je inicializován, jako by šlo o samostatnou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="56e86-254">Each element of a structure is initialized as if it were a separate variable.</span></span> <span data-ttu-id="56e86-255">Pokud deklarujete délku pole, ale neinicializujete jeho prvky, každý prvek je inicializován, jako by šlo o samostatnou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="56e86-255">If you declare the length of an array but do not initialize its elements, each element is initialized as if it were a separate variable.</span></span>

## <a name="static-local-variable-lifetime"></a><span data-ttu-id="56e86-256">Životnost statické lokální proměnné</span><span class="sxs-lookup"><span data-stu-id="56e86-256">Static local variable lifetime</span></span>

<span data-ttu-id="56e86-257">`Static` místní proměnná má delší dobu života, než je procedura, ve které je deklarována.</span><span class="sxs-lookup"><span data-stu-id="56e86-257">A `Static` local variable has a longer lifetime than that of the procedure in which it is declared.</span></span> <span data-ttu-id="56e86-258">Hranice životnosti proměnné závisí na tom, kde je procedura deklarována a zda je `Shared`.</span><span class="sxs-lookup"><span data-stu-id="56e86-258">The boundaries of the variable's lifetime depend on where the procedure is declared and whether it is `Shared`.</span></span>

|<span data-ttu-id="56e86-259">Deklarace procedury</span><span class="sxs-lookup"><span data-stu-id="56e86-259">Procedure declaration</span></span>|<span data-ttu-id="56e86-260">Proměnná inicializovaná</span><span class="sxs-lookup"><span data-stu-id="56e86-260">Variable initialized</span></span>|<span data-ttu-id="56e86-261">Proměnná zastaví existující.</span><span class="sxs-lookup"><span data-stu-id="56e86-261">Variable stops existing</span></span>|
|---|---|---|
|<span data-ttu-id="56e86-262">V modulu</span><span class="sxs-lookup"><span data-stu-id="56e86-262">In a module</span></span>|<span data-ttu-id="56e86-263">Při prvním volání procedury</span><span class="sxs-lookup"><span data-stu-id="56e86-263">The first time the procedure is called</span></span>|<span data-ttu-id="56e86-264">Když váš program zastaví provádění</span><span class="sxs-lookup"><span data-stu-id="56e86-264">When your program stops execution</span></span>|
|<span data-ttu-id="56e86-265">V rámci třídy nebo struktury je procedura `Shared`</span><span class="sxs-lookup"><span data-stu-id="56e86-265">In a class or structure, procedure is `Shared`</span></span>|<span data-ttu-id="56e86-266">Při prvním volání procedury buď na konkrétní instanci, nebo v samotné třídě nebo struktuře</span><span class="sxs-lookup"><span data-stu-id="56e86-266">The first time the procedure is called either on a specific instance or on the class or structure itself</span></span>|<span data-ttu-id="56e86-267">Když váš program zastaví provádění</span><span class="sxs-lookup"><span data-stu-id="56e86-267">When your program stops execution</span></span>|
|<span data-ttu-id="56e86-268">V třídě nebo struktuře není procedura `Shared`</span><span class="sxs-lookup"><span data-stu-id="56e86-268">In a class or structure, procedure isn't `Shared`</span></span>|<span data-ttu-id="56e86-269">Při prvním volání procedury na konkrétní instanci</span><span class="sxs-lookup"><span data-stu-id="56e86-269">The first time the procedure is called on a specific instance</span></span>|<span data-ttu-id="56e86-270">Při uvolnění instance pro uvolňování paměti (GC)</span><span class="sxs-lookup"><span data-stu-id="56e86-270">When the instance is released for garbage collection (GC)</span></span>|

## <a name="attributes-and-modifiers"></a><span data-ttu-id="56e86-271">Atributy a modifikátory</span><span class="sxs-lookup"><span data-stu-id="56e86-271">Attributes and modifiers</span></span>

<span data-ttu-id="56e86-272">Můžete použít atributy pouze na členské proměnné, nikoli na lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="56e86-272">You can apply attributes only to member variables, not to local variables.</span></span> <span data-ttu-id="56e86-273">Atribut přispívá k metadatům sestavení, která nejsou smysluplná pro dočasné úložiště, jako jsou místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="56e86-273">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local variables.</span></span>

<span data-ttu-id="56e86-274">Na úrovni modulu nemůžete použít modifikátor `Static` k deklaraci proměnných členů.</span><span class="sxs-lookup"><span data-stu-id="56e86-274">At module level, you cannot use the `Static` modifier to declare member variables.</span></span> <span data-ttu-id="56e86-275">Na úrovni procedury nelze použít `Shared`, `Shadows`, `ReadOnly`, `WithEvents`nebo žádné modifikátory přístupu k deklaraci místních proměnných.</span><span class="sxs-lookup"><span data-stu-id="56e86-275">At procedure level, you cannot use `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, or any access modifiers to declare local variables.</span></span>

<span data-ttu-id="56e86-276">Můžete určit, který kód má přístup k proměnné, zadáním `accessmodifier`.</span><span class="sxs-lookup"><span data-stu-id="56e86-276">You can specify what code can access a variable by supplying an `accessmodifier`.</span></span> <span data-ttu-id="56e86-277">Proměnné členů třídy a modulu (mimo všechny procedury) výchozí pro privátní přístup a proměnné členů struktury jako výchozí pro veřejný přístup.</span><span class="sxs-lookup"><span data-stu-id="56e86-277">Class and module member variables (outside any procedure) default to private access, and structure member variables default to public access.</span></span> <span data-ttu-id="56e86-278">Můžete upravit jejich úrovně přístupu modifikátory přístupu.</span><span class="sxs-lookup"><span data-stu-id="56e86-278">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="56e86-279">Modifikátory přístupu nemůžete použít u místních proměnných (uvnitř procedury).</span><span class="sxs-lookup"><span data-stu-id="56e86-279">You cannot use access modifiers on local variables (inside a procedure).</span></span>

<span data-ttu-id="56e86-280">`WithEvents` lze zadat pouze pro členské proměnné, nikoli pro lokální proměnné v rámci procedury.</span><span class="sxs-lookup"><span data-stu-id="56e86-280">You can specify `WithEvents` only on member variables, not on local variables inside a procedure.</span></span> <span data-ttu-id="56e86-281">Pokud zadáte `WithEvents`, datový typ proměnné musí být konkrétní typ třídy, ne `Object`.</span><span class="sxs-lookup"><span data-stu-id="56e86-281">If you specify `WithEvents`, the data type of the variable must be a specific class type, not `Object`.</span></span> <span data-ttu-id="56e86-282">Pole nelze deklarovat pomocí `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="56e86-282">You cannot declare an array with `WithEvents`.</span></span> <span data-ttu-id="56e86-283">Další informace o událostech najdete v tématu [události](../../programming-guide/language-features/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="56e86-283">For more information about events, see [Events](../../programming-guide/language-features/events/index.md).</span></span>

> [!NOTE]
> <span data-ttu-id="56e86-284">Kód mimo třídu, strukturu nebo modul musí kvalifikovat název členské proměnné s názvem této třídy, struktury nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="56e86-284">Code outside a class, structure, or module must qualify a member variable's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="56e86-285">Kód mimo proceduru nebo blok nemůže odkazovat na žádné místní proměnné v rámci tohoto postupu nebo bloku.</span><span class="sxs-lookup"><span data-stu-id="56e86-285">Code outside a procedure or block cannot refer to any local variables within that procedure or block.</span></span>

## <a name="releasing-managed-resources"></a><span data-ttu-id="56e86-286">Uvolňování spravovaných prostředků</span><span class="sxs-lookup"><span data-stu-id="56e86-286">Releasing managed resources</span></span>

<span data-ttu-id="56e86-287">Systém uvolňování paměti .NET Framework uvolní spravované prostředky bez jakéhokoli dalšího kódování na vaší straně.</span><span class="sxs-lookup"><span data-stu-id="56e86-287">The .NET Framework garbage collector disposes of managed resources without any extra coding on your part.</span></span> <span data-ttu-id="56e86-288">Místo toho, abyste čekali na uvolňování paměti, ale můžete vynutit vyřazení spravovaného prostředku.</span><span class="sxs-lookup"><span data-stu-id="56e86-288">However, you can force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>

<span data-ttu-id="56e86-289">Pokud třída obsahuje obzvláště cenný a omezených prostředek (například připojení k databázi nebo popisovač souboru), nebudete chtít počkat do dalšího uvolňování paměti, aby se vyčistila instance třídy, která se už nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="56e86-289">If a class holds onto a particularly valuable and scarce resource (such as a database connection or file handle), you might not want to wait until the next garbage collection to clean up a class instance that's no longer in use.</span></span> <span data-ttu-id="56e86-290">Třída může implementovat rozhraní <xref:System.IDisposable>, aby poskytovala způsob, jak uvolnit prostředky před uvolňováním paměti.</span><span class="sxs-lookup"><span data-stu-id="56e86-290">A class may implement the <xref:System.IDisposable> interface to provide a way to release resources before a garbage collection.</span></span> <span data-ttu-id="56e86-291">Třída, která implementuje toto rozhraní, zpřístupňuje `Dispose` metodu, která může být volána, aby vynutila okamžité vydání cenných prostředků.</span><span class="sxs-lookup"><span data-stu-id="56e86-291">A class that implements that interface exposes a `Dispose` method that can be called to force valuable resources to be released immediately.</span></span>

<span data-ttu-id="56e86-292">Příkaz `Using` automatizuje proces získání prostředku, spuštění sady příkazů a následné likvidaci prostředku.</span><span class="sxs-lookup"><span data-stu-id="56e86-292">The `Using` statement automates the process of acquiring a resource, executing a set of statements, and then disposing of the resource.</span></span> <span data-ttu-id="56e86-293">Prostředek však musí implementovat rozhraní <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="56e86-293">However, the resource must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="56e86-294">Další informace naleznete v tématu [using – příkaz](using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="56e86-294">For more information, see [Using Statement](using-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="56e86-295">Příklad</span><span class="sxs-lookup"><span data-stu-id="56e86-295">Example</span></span>

<span data-ttu-id="56e86-296">Následující příklad deklaruje proměnné pomocí příkazu `Dim` s různými možnostmi.</span><span class="sxs-lookup"><span data-stu-id="56e86-296">The following example declares variables by using the `Dim` statement with various options.</span></span>

[!code-vb[VbVbalrStatements#141](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#141)]

## <a name="example"></a><span data-ttu-id="56e86-297">Příklad</span><span class="sxs-lookup"><span data-stu-id="56e86-297">Example</span></span>

<span data-ttu-id="56e86-298">Následující příklad uvádí hlavní čísla mezi 1 a 30.</span><span class="sxs-lookup"><span data-stu-id="56e86-298">The following example lists the prime numbers between 1 and 30.</span></span> <span data-ttu-id="56e86-299">Rozsah místních proměnných je popsán v komentářích ke kódu.</span><span class="sxs-lookup"><span data-stu-id="56e86-299">The scope of local variables is described in code comments.</span></span>

[!code-vb[VbVbalrStatements#142](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#142)]

## <a name="example"></a><span data-ttu-id="56e86-300">Příklad</span><span class="sxs-lookup"><span data-stu-id="56e86-300">Example</span></span>

<span data-ttu-id="56e86-301">V následujícím příkladu je proměnná `speedValue` deklarována na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="56e86-301">In the following example, the `speedValue` variable is declared at the class level.</span></span> <span data-ttu-id="56e86-302">Klíčové slovo `Private` slouží k deklaraci proměnné.</span><span class="sxs-lookup"><span data-stu-id="56e86-302">The `Private` keyword is used to declare the variable.</span></span> <span data-ttu-id="56e86-303">K proměnné lze přistupovat jakýmkoli postupem ve třídě `Car`.</span><span class="sxs-lookup"><span data-stu-id="56e86-303">The variable can be accessed by any procedure in the `Car` class.</span></span>

[!code-vb[VbVbalrStatements#144](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#144)]

[!code-vb[VbVbalrStatements#145](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#145)]

## <a name="see-also"></a><span data-ttu-id="56e86-304">Viz také</span><span class="sxs-lookup"><span data-stu-id="56e86-304">See also</span></span>

- [<span data-ttu-id="56e86-305">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="56e86-305">Const Statement</span></span>](const-statement.md)
- [<span data-ttu-id="56e86-306">Příkaz ReDim</span><span class="sxs-lookup"><span data-stu-id="56e86-306">ReDim Statement</span></span>](redim-statement.md)
- [<span data-ttu-id="56e86-307">Příkaz Option Explicit</span><span class="sxs-lookup"><span data-stu-id="56e86-307">Option Explicit Statement</span></span>](option-explicit-statement.md)
- [<span data-ttu-id="56e86-308">Příkaz Option Infer</span><span class="sxs-lookup"><span data-stu-id="56e86-308">Option Infer Statement</span></span>](option-infer-statement.md)
- [<span data-ttu-id="56e86-309">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="56e86-309">Option Strict Statement</span></span>](option-strict-statement.md)
- [<span data-ttu-id="56e86-310">Stránka Kompilovat, Návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56e86-310">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [<span data-ttu-id="56e86-311">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="56e86-311">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="56e86-312">Pole</span><span class="sxs-lookup"><span data-stu-id="56e86-312">Arrays</span></span>](../../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="56e86-313">Inicializátory objektů: pojmenované a anonymní typy</span><span class="sxs-lookup"><span data-stu-id="56e86-313">Object Initializers: Named and Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="56e86-314">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="56e86-314">Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="56e86-315">Inicializátory objektů: pojmenované a anonymní typy</span><span class="sxs-lookup"><span data-stu-id="56e86-315">Object Initializers: Named and Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="56e86-316">Postupy: Deklarace objektu pomocí inicializátoru objektu</span><span class="sxs-lookup"><span data-stu-id="56e86-316">How to: Declare an Object by Using an Object Initializer</span></span>](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
- [<span data-ttu-id="56e86-317">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="56e86-317">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
