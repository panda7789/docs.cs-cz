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
ms.openlocfilehash: dd50435b7cbb5d3d25c0e30618e8733b4eddfe91
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655072"
---
# <a name="type-list-visual-basic"></a><span data-ttu-id="d6026-102">Seznam typů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6026-102">Type List (Visual Basic)</span></span>
<span data-ttu-id="d6026-103">Určuje *parametry typu* pro *obecný* programovací element.</span><span class="sxs-lookup"><span data-stu-id="d6026-103">Specifies the *type parameters* for a *generic* programming element.</span></span> <span data-ttu-id="d6026-104">Více parametrů jsou odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="d6026-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="d6026-105">Následuje syntaxe pro parametr jednoho typu.</span><span class="sxs-lookup"><span data-stu-id="d6026-105">Following is the syntax for one type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6026-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6026-106">Syntax</span></span>  
  
```  
[genericmodifier] typename [ As constraintlist ]  
```  
  
## <a name="parts"></a><span data-ttu-id="d6026-107">Součásti</span><span class="sxs-lookup"><span data-stu-id="d6026-107">Parts</span></span>  
  
|<span data-ttu-id="d6026-108">Termín</span><span class="sxs-lookup"><span data-stu-id="d6026-108">Term</span></span>|<span data-ttu-id="d6026-109">Definice</span><span class="sxs-lookup"><span data-stu-id="d6026-109">Definition</span></span>|  
|---|---|  
|`genericmodifier`|<span data-ttu-id="d6026-110">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="d6026-110">Optional.</span></span> <span data-ttu-id="d6026-111">Je možné jenom v obecných rozhraních a delegátech.</span><span class="sxs-lookup"><span data-stu-id="d6026-111">Can be used only in generic interfaces and delegates.</span></span> <span data-ttu-id="d6026-112">Je možné deklarovat typ kovariantního pomocí [si](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) – klíčové slovo nebo kontravariantní pomocí [v](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="d6026-112">You can declare a type covariant by using the [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) keyword or contravariant by using the [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) keyword.</span></span> <span data-ttu-id="d6026-113">Zobrazit [kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="d6026-113">See [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>|  
|`typename`|<span data-ttu-id="d6026-114">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="d6026-114">Required.</span></span> <span data-ttu-id="d6026-115">Název parametru typu.</span><span class="sxs-lookup"><span data-stu-id="d6026-115">Name of the type parameter.</span></span> <span data-ttu-id="d6026-116">Toto je zástupný symbol bude nahrazen určitého typu poskytl argument typu.</span><span class="sxs-lookup"><span data-stu-id="d6026-116">This is a placeholder, to be replaced by a defined type supplied by the corresponding type argument.</span></span>|  
|`constraintlist`|<span data-ttu-id="d6026-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="d6026-117">Optional.</span></span> <span data-ttu-id="d6026-118">Seznam všech požadavků, které datový typ, který může být zadán pro `typename`.</span><span class="sxs-lookup"><span data-stu-id="d6026-118">List of requirements that constrain the data type that can be supplied for `typename`.</span></span> <span data-ttu-id="d6026-119">Pokud máte více omezení, je uzavřete do složených závorek (`{ }`) a oddělit je čárkami.</span><span class="sxs-lookup"><span data-stu-id="d6026-119">If you have multiple constraints, enclose them in curly braces (`{ }`) and separate them with commas.</span></span> <span data-ttu-id="d6026-120">Musí zavést seznamu omezení [jako](../../../visual-basic/language-reference/statements/as-clause.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="d6026-120">You must introduce the constraint list with the [As](../../../visual-basic/language-reference/statements/as-clause.md) keyword.</span></span> <span data-ttu-id="d6026-121">Použijete `As` jenom jednou na začátku seznamu.</span><span class="sxs-lookup"><span data-stu-id="d6026-121">You use `As` only once, at the beginning of the list.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6026-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d6026-122">Remarks</span></span>  
 <span data-ttu-id="d6026-123">Každý obecný programovací prvek přijme aspoň jeden parametr typu.</span><span class="sxs-lookup"><span data-stu-id="d6026-123">Every generic programming element must take at least one type parameter.</span></span> <span data-ttu-id="d6026-124">Parametr typu je zástupný symbol pro konkrétní typ ( *vytvořený element*), určuje kód klienta při vytváření instance obecného typu.</span><span class="sxs-lookup"><span data-stu-id="d6026-124">A type parameter is a placeholder for a specific type (a *constructed element*) that client code specifies when it creates an instance of the generic type.</span></span> <span data-ttu-id="d6026-125">Můžete definovat obecnou třídu, strukturu, rozhraní, postupu nebo delegovat.</span><span class="sxs-lookup"><span data-stu-id="d6026-125">You can define a generic class, structure, interface, procedure, or delegate.</span></span>  
  
 <span data-ttu-id="d6026-126">Další informace o při definování obecného typu, najdete v části [obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="d6026-126">For more information on when to define a generic type, see [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span> <span data-ttu-id="d6026-127">Další informace o názvy parametrů typů naleznete v tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="d6026-127">For more information on type parameter names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="d6026-128">pravidla</span><span class="sxs-lookup"><span data-stu-id="d6026-128">Rules</span></span>  
  
-   <span data-ttu-id="d6026-129">**Závorky.**</span><span class="sxs-lookup"><span data-stu-id="d6026-129">**Parentheses.**</span></span> <span data-ttu-id="d6026-130">Pokud zadáte seznam parametrů typu, je nutné uzavřít do závorek a musí zavést seznamu [z](../../../visual-basic/language-reference/statements/of-clause.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="d6026-130">If you supply a type parameter list, you must enclose it in parentheses, and you must introduce the list with the [Of](../../../visual-basic/language-reference/statements/of-clause.md) keyword.</span></span> <span data-ttu-id="d6026-131">Použijete `Of` jenom jednou na začátku seznamu.</span><span class="sxs-lookup"><span data-stu-id="d6026-131">You use `Of` only once, at the beginning of the list.</span></span>  
  
-   <span data-ttu-id="d6026-132">**Omezení.**</span><span class="sxs-lookup"><span data-stu-id="d6026-132">**Constraints.**</span></span> <span data-ttu-id="d6026-133">Seznam *omezení* typu parametr může obsahovat následující položky v libovolné kombinaci:</span><span class="sxs-lookup"><span data-stu-id="d6026-133">A list of *constraints* on a type parameter can include the following items in any combination:</span></span>  
  
    -   <span data-ttu-id="d6026-134">Libovolný počet rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d6026-134">Any number of interfaces.</span></span> <span data-ttu-id="d6026-135">Zadaný typ musí implementovat každé rozhraní v tomto seznamu.</span><span class="sxs-lookup"><span data-stu-id="d6026-135">The supplied type must implement every interface in this list.</span></span>  
  
    -   <span data-ttu-id="d6026-136">Nejvýše jednu třídu.</span><span class="sxs-lookup"><span data-stu-id="d6026-136">At most one class.</span></span> <span data-ttu-id="d6026-137">Zadaný typ musí dědit z této třídy.</span><span class="sxs-lookup"><span data-stu-id="d6026-137">The supplied type must inherit from that class.</span></span>  
  
    -   <span data-ttu-id="d6026-138">`New` – Klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="d6026-138">The `New` keyword.</span></span> <span data-ttu-id="d6026-139">Zadaný typ musí vystavit konstruktor bez parametrů, s přístupem k obecného typu.</span><span class="sxs-lookup"><span data-stu-id="d6026-139">The supplied type must expose a parameterless constructor that your generic type can access.</span></span> <span data-ttu-id="d6026-140">To je užitečné, pokud omezení parametru typu jeden nebo více rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d6026-140">This is useful if you constrain a type parameter by one or more interfaces.</span></span> <span data-ttu-id="d6026-141">Typ, který implementuje rozhraní nevystavuje nutně konstruktor a v závislosti na úrovni přístupu konstruktor nemusí být kód v rámci obecného typu k němu mít přístup.</span><span class="sxs-lookup"><span data-stu-id="d6026-141">A type that implements interfaces does not necessarily expose a constructor, and depending on the access level of a constructor, the code within the generic type might not be able to access it.</span></span>  
  
    -   <span data-ttu-id="d6026-142">Buď `Class` – klíčové slovo nebo `Structure` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="d6026-142">Either the `Class` keyword or the `Structure` keyword.</span></span> <span data-ttu-id="d6026-143">`Class` – Klíčové slovo omezuje parametr obecného typu tak, aby vyžadovala, aby libovolný do něho předaný argument typu být typ odkazu, například řetězce, pole nebo delegáta, nebo vytvoří objekt ze třídy.</span><span class="sxs-lookup"><span data-stu-id="d6026-143">The `Class` keyword constrains a generic type parameter to require that any type argument passed to it be a reference type, for example a string, array, or delegate, or an object created from a class.</span></span> <span data-ttu-id="d6026-144">`Structure` – Klíčové slovo omezí vyžadují, aby libovolný do něho předaný argument typu typ hodnoty, parametr obecného typu, například strukturu, výčet nebo základní datového typu.</span><span class="sxs-lookup"><span data-stu-id="d6026-144">The `Structure` keyword constrains a generic type parameter to require that any type argument passed to it be a value type, for example a structure, enumeration, or elementary data type.</span></span> <span data-ttu-id="d6026-145">Nemůže obsahovat oba `Class` a `Structure` ve stejném `constraintlist`.</span><span class="sxs-lookup"><span data-stu-id="d6026-145">You cannot include both `Class` and `Structure` in the same `constraintlist`.</span></span>  
  
     <span data-ttu-id="d6026-146">Zadaný typ musí splňovat každý požadavek zahrnete `constraintlist`.</span><span class="sxs-lookup"><span data-stu-id="d6026-146">The supplied type must satisfy every requirement you include in `constraintlist`.</span></span>  
  
     <span data-ttu-id="d6026-147">U každého parametru typu omezení jsou nezávislé omezení na jiné parametry typu.</span><span class="sxs-lookup"><span data-stu-id="d6026-147">Constraints on each type parameter are independent of constraints on other type parameters.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="d6026-148">Chování</span><span class="sxs-lookup"><span data-stu-id="d6026-148">Behavior</span></span>  
  
-   <span data-ttu-id="d6026-149">**Náhrada za kompilace.**</span><span class="sxs-lookup"><span data-stu-id="d6026-149">**Compile-Time Substitution.**</span></span> <span data-ttu-id="d6026-150">Při vytváření konstruovaný typ z obecného programovací element je zadat typu definované pro každý parametr typu.</span><span class="sxs-lookup"><span data-stu-id="d6026-150">When you create a constructed type from a generic programming element, you supply a defined type for each type parameter.</span></span> <span data-ttu-id="d6026-151">Kompilátor jazyka Visual Basic nahradí zadaného typu pro všechny výskyty `typename` v rámci obecného prvku.</span><span class="sxs-lookup"><span data-stu-id="d6026-151">The Visual Basic compiler substitutes that supplied type for every occurrence of `typename` within the generic element.</span></span>  
  
-   <span data-ttu-id="d6026-152">**Neexistence omezení.**</span><span class="sxs-lookup"><span data-stu-id="d6026-152">**Absence of Constraints.**</span></span> <span data-ttu-id="d6026-153">Pokud nezadáte žádné omezení pro parametr typu, je omezený na konzole operations Console a členy, nepodporuje váš kód [datový typ objektu](../../../visual-basic/language-reference/data-types/object-data-type.md) za parametr daného typu.</span><span class="sxs-lookup"><span data-stu-id="d6026-153">If you do not specify any constraints on a type parameter, your code is limited to the operations and members supported by the [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md) for that type parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6026-154">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6026-154">Example</span></span>  
 <span data-ttu-id="d6026-155">Následující příklad ukazuje definici kostru třídy generický slovník, včetně kostru funkci, kterou chcete přidat novou položku do slovníku.</span><span class="sxs-lookup"><span data-stu-id="d6026-155">The following example shows a skeleton definition of a generic dictionary class, including a skeleton function to add a new entry to the dictionary.</span></span>  
  
 [!code-vb[VbVbalrStatements#3](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="d6026-156">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6026-156">Example</span></span>  
 <span data-ttu-id="d6026-157">Protože `dictionary` je obecný, kód, který používá ho můžete vytvořit různé objekty z něj, každý s stejné funkce, ale funguje na jiný datový typ.</span><span class="sxs-lookup"><span data-stu-id="d6026-157">Because `dictionary` is generic, the code that uses it can create a variety of objects from it, each having the same functionality but acting on a different data type.</span></span> <span data-ttu-id="d6026-158">Následující příklad ukazuje řádek kódu, který vytváří `dictionary` objekt s `String` položky a `Integer` klíče.</span><span class="sxs-lookup"><span data-stu-id="d6026-158">The following example shows a line of code that creates a `dictionary` object with `String` entries and `Integer` keys.</span></span>  
  
 [!code-vb[VbVbalrStatements#4](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="d6026-159">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6026-159">Example</span></span>  
 <span data-ttu-id="d6026-160">Následující příklad ukazuje definici ekvivalentní kostru vygenerované v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d6026-160">The following example shows the equivalent skeleton definition generated by the preceding example.</span></span>  
  
 [!code-vb[VbVbalrStatements#5](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d6026-161">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d6026-161">See also</span></span>
- [<span data-ttu-id="d6026-162">z</span><span class="sxs-lookup"><span data-stu-id="d6026-162">Of</span></span>](../../../visual-basic/language-reference/statements/of-clause.md)
- [<span data-ttu-id="d6026-163">Operátor New</span><span class="sxs-lookup"><span data-stu-id="d6026-163">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="d6026-164">Úrovně přístupu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d6026-164">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="d6026-165">Datový typ Object</span><span class="sxs-lookup"><span data-stu-id="d6026-165">Object Data Type</span></span>](../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="d6026-166">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="d6026-166">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="d6026-167">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="d6026-167">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="d6026-168">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="d6026-168">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="d6026-169">Postupy: Použití obecné třídy</span><span class="sxs-lookup"><span data-stu-id="d6026-169">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="d6026-170">Kovariance a kontravariance</span><span class="sxs-lookup"><span data-stu-id="d6026-170">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="d6026-171">V</span><span class="sxs-lookup"><span data-stu-id="d6026-171">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [<span data-ttu-id="d6026-172">navýšení kapacity</span><span class="sxs-lookup"><span data-stu-id="d6026-172">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
