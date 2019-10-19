---
title: Seznam typů (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- StructureConstraint
- vb.StructureConstraint
- ClassConstraint
- vb.ClassConstraint
helpviewer_keywords:
- class constraint
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- generics [Visual Basic], type list
- structure constraint
- constraints, in type parameters
- generics [Visual Basic], generic types
- parameters [Visual Basic], type
- constraints, Structure keyword
- type parameters [Visual Basic], constraints
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], type parameters
- type parameters
- constraints, Class keyword
ms.assetid: 56db947a-2ae8-40f2-a70a-960764e9d0db
ms.openlocfilehash: a0d489684b8f98e871211e6d0d95d42284275954
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582900"
---
# <a name="type-list-visual-basic"></a><span data-ttu-id="be1f9-102">Seznam typů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="be1f9-102">Type List (Visual Basic)</span></span>

<span data-ttu-id="be1f9-103">Určuje *parametry typu* pro *obecný* programovací prvek.</span><span class="sxs-lookup"><span data-stu-id="be1f9-103">Specifies the *type parameters* for a *generic* programming element.</span></span> <span data-ttu-id="be1f9-104">Více parametrů je odděleno čárkami.</span><span class="sxs-lookup"><span data-stu-id="be1f9-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="be1f9-105">Následuje syntaxe pro jeden parametr typu.</span><span class="sxs-lookup"><span data-stu-id="be1f9-105">Following is the syntax for one type parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="be1f9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be1f9-106">Syntax</span></span>

```vb
[genericmodifier] typename [ As constraintlist ]
```

## <a name="parts"></a><span data-ttu-id="be1f9-107">Součásti</span><span class="sxs-lookup"><span data-stu-id="be1f9-107">Parts</span></span>

|<span data-ttu-id="be1f9-108">Termín</span><span class="sxs-lookup"><span data-stu-id="be1f9-108">Term</span></span>|<span data-ttu-id="be1f9-109">Definice</span><span class="sxs-lookup"><span data-stu-id="be1f9-109">Definition</span></span>|
|---|---|
|`genericmodifier`|<span data-ttu-id="be1f9-110">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="be1f9-110">Optional.</span></span> <span data-ttu-id="be1f9-111">Dá se použít jenom v obecných rozhraních a delegátech.</span><span class="sxs-lookup"><span data-stu-id="be1f9-111">Can be used only in generic interfaces and delegates.</span></span> <span data-ttu-id="be1f9-112">Kovariantu typu lze deklarovat pomocí klíčového slova [out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) nebo kontravariantní pomocí klíčového slova [in](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) .</span><span class="sxs-lookup"><span data-stu-id="be1f9-112">You can declare a type covariant by using the [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) keyword or contravariant by using the [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) keyword.</span></span> <span data-ttu-id="be1f9-113">Viz [kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="be1f9-113">See [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>|
|`typename`|<span data-ttu-id="be1f9-114">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="be1f9-114">Required.</span></span> <span data-ttu-id="be1f9-115">Název parametru typu</span><span class="sxs-lookup"><span data-stu-id="be1f9-115">Name of the type parameter.</span></span> <span data-ttu-id="be1f9-116">Toto je zástupný symbol, který bude nahrazen definovaným typem poskytnutým odpovídajícím argumentem typu.</span><span class="sxs-lookup"><span data-stu-id="be1f9-116">This is a placeholder, to be replaced by a defined type supplied by the corresponding type argument.</span></span>|
|`constraintlist`|<span data-ttu-id="be1f9-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="be1f9-117">Optional.</span></span> <span data-ttu-id="be1f9-118">Seznam požadavků, které omezí datový typ, který lze zadat pro `typename`.</span><span class="sxs-lookup"><span data-stu-id="be1f9-118">List of requirements that constrain the data type that can be supplied for `typename`.</span></span> <span data-ttu-id="be1f9-119">Pokud máte více omezení, vložte je do složených závorek (`{ }`) a oddělte je čárkami.</span><span class="sxs-lookup"><span data-stu-id="be1f9-119">If you have multiple constraints, enclose them in curly braces (`{ }`) and separate them with commas.</span></span> <span data-ttu-id="be1f9-120">Seznam omezení je nutné zavést pomocí klíčového slova [as](../../../visual-basic/language-reference/statements/as-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="be1f9-120">You must introduce the constraint list with the [As](../../../visual-basic/language-reference/statements/as-clause.md) keyword.</span></span> <span data-ttu-id="be1f9-121">Na začátku seznamu se používá `As` jenom jednou.</span><span class="sxs-lookup"><span data-stu-id="be1f9-121">You use `As` only once, at the beginning of the list.</span></span>|

## <a name="remarks"></a><span data-ttu-id="be1f9-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="be1f9-122">Remarks</span></span>

<span data-ttu-id="be1f9-123">Každý obecný programovací prvek musí mít alespoň jeden parametr typu.</span><span class="sxs-lookup"><span data-stu-id="be1f9-123">Every generic programming element must take at least one type parameter.</span></span> <span data-ttu-id="be1f9-124">Parametr typu je zástupný symbol pro konkrétní typ ( *konstruovaný element*), který určuje kód klienta při vytváření instance obecného typu.</span><span class="sxs-lookup"><span data-stu-id="be1f9-124">A type parameter is a placeholder for a specific type (a *constructed element*) that client code specifies when it creates an instance of the generic type.</span></span> <span data-ttu-id="be1f9-125">Můžete definovat obecnou třídu, strukturu, rozhraní, proceduru nebo delegáta.</span><span class="sxs-lookup"><span data-stu-id="be1f9-125">You can define a generic class, structure, interface, procedure, or delegate.</span></span>

<span data-ttu-id="be1f9-126">Další informace o tom, kdy definovat obecný typ, naleznete [v tématu Obecné typy v Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="be1f9-126">For more information on when to define a generic type, see [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span> <span data-ttu-id="be1f9-127">Další informace o názvech parametrů typů naleznete v tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="be1f9-127">For more information on type parameter names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

## <a name="rules"></a><span data-ttu-id="be1f9-128">Pravidly</span><span class="sxs-lookup"><span data-stu-id="be1f9-128">Rules</span></span>

- <span data-ttu-id="be1f9-129">**Závorky.**</span><span class="sxs-lookup"><span data-stu-id="be1f9-129">**Parentheses.**</span></span> <span data-ttu-id="be1f9-130">Pokud zadáte seznam parametrů typu, je nutné jej uzavřít do závorek a je třeba uvést seznam [s klíčovým](../../../visual-basic/language-reference/statements/of-clause.md) slovem.</span><span class="sxs-lookup"><span data-stu-id="be1f9-130">If you supply a type parameter list, you must enclose it in parentheses, and you must introduce the list with the [Of](../../../visual-basic/language-reference/statements/of-clause.md) keyword.</span></span> <span data-ttu-id="be1f9-131">Na začátku seznamu se používá `Of` jenom jednou.</span><span class="sxs-lookup"><span data-stu-id="be1f9-131">You use `Of` only once, at the beginning of the list.</span></span>

- <span data-ttu-id="be1f9-132">**Jednotlivým.**</span><span class="sxs-lookup"><span data-stu-id="be1f9-132">**Constraints.**</span></span> <span data-ttu-id="be1f9-133">Seznam *omezení* pro parametr typu může zahrnovat následující položky v libovolné kombinaci:</span><span class="sxs-lookup"><span data-stu-id="be1f9-133">A list of *constraints* on a type parameter can include the following items in any combination:</span></span>

  - <span data-ttu-id="be1f9-134">Libovolný počet rozhraní.</span><span class="sxs-lookup"><span data-stu-id="be1f9-134">Any number of interfaces.</span></span> <span data-ttu-id="be1f9-135">Zadaný typ musí implementovat každé rozhraní v tomto seznamu.</span><span class="sxs-lookup"><span data-stu-id="be1f9-135">The supplied type must implement every interface in this list.</span></span>

  - <span data-ttu-id="be1f9-136">Nejvýše jedna třída.</span><span class="sxs-lookup"><span data-stu-id="be1f9-136">At most one class.</span></span> <span data-ttu-id="be1f9-137">Poskytnutý typ musí dědit z této třídy.</span><span class="sxs-lookup"><span data-stu-id="be1f9-137">The supplied type must inherit from that class.</span></span>

  - <span data-ttu-id="be1f9-138">Klíčové slovo `New`.</span><span class="sxs-lookup"><span data-stu-id="be1f9-138">The `New` keyword.</span></span> <span data-ttu-id="be1f9-139">Zadaný typ musí vystavit konstruktor bez parametrů, ke kterému má přístup váš obecný typ.</span><span class="sxs-lookup"><span data-stu-id="be1f9-139">The supplied type must expose a parameterless constructor that your generic type can access.</span></span> <span data-ttu-id="be1f9-140">To je užitečné, pokud omezíte parametr typu jedním nebo více rozhraními.</span><span class="sxs-lookup"><span data-stu-id="be1f9-140">This is useful if you constrain a type parameter by one or more interfaces.</span></span> <span data-ttu-id="be1f9-141">Typ, který implementuje rozhraní, nutně nezveřejňuje konstruktor a v závislosti na úrovni přístupu konstruktoru, kód v obecném typu nemusí mít přístup k němu.</span><span class="sxs-lookup"><span data-stu-id="be1f9-141">A type that implements interfaces does not necessarily expose a constructor, and depending on the access level of a constructor, the code within the generic type might not be able to access it.</span></span>

  - <span data-ttu-id="be1f9-142">Buď klíčové slovo `Class`, nebo klíčové slovo `Structure`.</span><span class="sxs-lookup"><span data-stu-id="be1f9-142">Either the `Class` keyword or the `Structure` keyword.</span></span> <span data-ttu-id="be1f9-143">Klíčové slovo `Class` omezuje parametr obecného typu tak, aby vyžadovalo, aby jakýkoliv argument typu, který je předaný, byl odkazovým typem, například řetězcem, polem nebo delegátem nebo objektem vytvořeným z třídy.</span><span class="sxs-lookup"><span data-stu-id="be1f9-143">The `Class` keyword constrains a generic type parameter to require that any type argument passed to it be a reference type, for example a string, array, or delegate, or an object created from a class.</span></span> <span data-ttu-id="be1f9-144">Klíčové slovo `Structure` omezuje parametr obecného typu tak, aby vyžadovalo, aby jakýkoli argument typu, který je předaný, byl typ hodnoty, například struktura, výčet nebo základní datový typ.</span><span class="sxs-lookup"><span data-stu-id="be1f9-144">The `Structure` keyword constrains a generic type parameter to require that any type argument passed to it be a value type, for example a structure, enumeration, or elementary data type.</span></span> <span data-ttu-id="be1f9-145">Do stejného `constraintlist` nemůžete zahrnout `Class` i `Structure`.</span><span class="sxs-lookup"><span data-stu-id="be1f9-145">You cannot include both `Class` and `Structure` in the same `constraintlist`.</span></span>

  <span data-ttu-id="be1f9-146">Zadaný typ musí splňovat všechny požadavky, které zahrnete do `constraintlist`.</span><span class="sxs-lookup"><span data-stu-id="be1f9-146">The supplied type must satisfy every requirement you include in `constraintlist`.</span></span>

  <span data-ttu-id="be1f9-147">Omezení pro jednotlivé parametry typu jsou nezávislá na omezeních u jiných parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="be1f9-147">Constraints on each type parameter are independent of constraints on other type parameters.</span></span>

## <a name="behavior"></a><span data-ttu-id="be1f9-148">Předvídatelně</span><span class="sxs-lookup"><span data-stu-id="be1f9-148">Behavior</span></span>

- <span data-ttu-id="be1f9-149">**Nahrazování v době kompilace.**</span><span class="sxs-lookup"><span data-stu-id="be1f9-149">**Compile-Time Substitution.**</span></span> <span data-ttu-id="be1f9-150">Když vytvoříte konstruovaný typ z obecného programovacího prvku, zadáte definovaný typ pro každý parametr typu.</span><span class="sxs-lookup"><span data-stu-id="be1f9-150">When you create a constructed type from a generic programming element, you supply a defined type for each type parameter.</span></span> <span data-ttu-id="be1f9-151">Kompilátor Visual Basic nahradí zadaný typ pro všechny výskyty `typename` v rámci obecného prvku.</span><span class="sxs-lookup"><span data-stu-id="be1f9-151">The Visual Basic compiler substitutes that supplied type for every occurrence of `typename` within the generic element.</span></span>

- <span data-ttu-id="be1f9-152">**Neexistence omezení**</span><span class="sxs-lookup"><span data-stu-id="be1f9-152">**Absence of Constraints.**</span></span> <span data-ttu-id="be1f9-153">Pokud nezadáte žádná omezení parametru typu, je váš kód omezen na operace a členy podporované [datovým typem objektu](../../../visual-basic/language-reference/data-types/object-data-type.md) pro tento parametr typu.</span><span class="sxs-lookup"><span data-stu-id="be1f9-153">If you do not specify any constraints on a type parameter, your code is limited to the operations and members supported by the [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md) for that type parameter.</span></span>

## <a name="example"></a><span data-ttu-id="be1f9-154">Příklad</span><span class="sxs-lookup"><span data-stu-id="be1f9-154">Example</span></span>

<span data-ttu-id="be1f9-155">Následující příklad znázorňuje kostru definice třídy obecného slovníku, včetně funkce kostry pro přidání nové položky do slovníku.</span><span class="sxs-lookup"><span data-stu-id="be1f9-155">The following example shows a skeleton definition of a generic dictionary class, including a skeleton function to add a new entry to the dictionary.</span></span>

[!code-vb[VbVbalrStatements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#3)]

## <a name="example"></a><span data-ttu-id="be1f9-156">Příklad</span><span class="sxs-lookup"><span data-stu-id="be1f9-156">Example</span></span>

<span data-ttu-id="be1f9-157">Vzhledem k tomu, že `dictionary` je obecný, kód, který ho používá, může z něj vytvořit nejrůznější objekty, každý má stejné funkce, ale funguje na jiném datovém typu.</span><span class="sxs-lookup"><span data-stu-id="be1f9-157">Because `dictionary` is generic, the code that uses it can create a variety of objects from it, each having the same functionality but acting on a different data type.</span></span> <span data-ttu-id="be1f9-158">Následující příklad ukazuje řádek kódu, který vytvoří objekt `dictionary` s `String`mi položkami a `Integer`mi klíči.</span><span class="sxs-lookup"><span data-stu-id="be1f9-158">The following example shows a line of code that creates a `dictionary` object with `String` entries and `Integer` keys.</span></span>

[!code-vb[VbVbalrStatements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#4)]

## <a name="example"></a><span data-ttu-id="be1f9-159">Příklad</span><span class="sxs-lookup"><span data-stu-id="be1f9-159">Example</span></span>

<span data-ttu-id="be1f9-160">Následující příklad ukazuje ekvivalentní kostru definice vygenerovanou předchozím příkladem.</span><span class="sxs-lookup"><span data-stu-id="be1f9-160">The following example shows the equivalent skeleton definition generated by the preceding example.</span></span>

[!code-vb[VbVbalrStatements#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="be1f9-161">Viz také:</span><span class="sxs-lookup"><span data-stu-id="be1f9-161">See also</span></span>

- [<span data-ttu-id="be1f9-162">Tohoto</span><span class="sxs-lookup"><span data-stu-id="be1f9-162">Of</span></span>](../../../visual-basic/language-reference/statements/of-clause.md)
- [<span data-ttu-id="be1f9-163">Operátor New</span><span class="sxs-lookup"><span data-stu-id="be1f9-163">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="be1f9-164">Úrovně přístupu v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="be1f9-164">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="be1f9-165">Datový typ Object</span><span class="sxs-lookup"><span data-stu-id="be1f9-165">Object Data Type</span></span>](../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="be1f9-166">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="be1f9-166">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="be1f9-167">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="be1f9-167">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="be1f9-168">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="be1f9-168">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="be1f9-169">Postupy: Použití obecné třídy</span><span class="sxs-lookup"><span data-stu-id="be1f9-169">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="be1f9-170">Kovariance a kontravariance</span><span class="sxs-lookup"><span data-stu-id="be1f9-170">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="be1f9-171">Pro</span><span class="sxs-lookup"><span data-stu-id="be1f9-171">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [<span data-ttu-id="be1f9-172">Mimo</span><span class="sxs-lookup"><span data-stu-id="be1f9-172">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
