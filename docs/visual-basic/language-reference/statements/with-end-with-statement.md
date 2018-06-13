---
title: With...End With – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.With
helpviewer_keywords:
- With keyword [Visual Basic]
- loop structures [Visual Basic], and With...End With statements
- execution [Visual Basic], on object
- instructions, repeating
- With...End With statements [Visual Basic]
- With statement [Visual Basic]
- With statement [Visual Basic], nesting
- objects [Visual Basic], accessing
- With block
- End keyword [Visual Basic], With...End With statements
ms.assetid: 340d5fbb-4f43-48ec-a024-80843c137817
ms.openlocfilehash: 9c50d03454860979e3475cb381fefc2acc07cece
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604663"
---
# <a name="withend-with-statement-visual-basic"></a><span data-ttu-id="25857-102">With...End With – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25857-102">With...End With Statement (Visual Basic)</span></span>
<span data-ttu-id="25857-103">Vykoná řadu příkazů, které opakovaně odkazují na jeden objekt nebo strukturu, takže příkazy mohou při přístupu k členům tohoto objektu nebo struktury použít zjednodušenou syntaxi.</span><span class="sxs-lookup"><span data-stu-id="25857-103">Executes a series of statements that repeatedly refer to a single object or structure so that the statements can use a simplified syntax when accessing members of the object or structure.</span></span>  <span data-ttu-id="25857-104">Při použití strukturou, můžou jenom číst hodnoty členů, nebo volat metody a dojde k chybě, pokud se pokusíte přiřadit hodnoty členů struktury používán `With...End With` příkaz.</span><span class="sxs-lookup"><span data-stu-id="25857-104">When using a structure, you can only read the values of members or invoke methods, and you get an error if you try to assign values to members of a structure used in a `With...End With` statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25857-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25857-105">Syntax</span></span>  
  
```  
With objectExpression  
    [ statements ]  
End With  
```  
  
## <a name="parts"></a><span data-ttu-id="25857-106">Součásti</span><span class="sxs-lookup"><span data-stu-id="25857-106">Parts</span></span>  
  
|<span data-ttu-id="25857-107">Termín</span><span class="sxs-lookup"><span data-stu-id="25857-107">Term</span></span>|<span data-ttu-id="25857-108">Definice</span><span class="sxs-lookup"><span data-stu-id="25857-108">Definition</span></span>|  
|---|---|  
|`objectExpression`|<span data-ttu-id="25857-109">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="25857-109">Required.</span></span> <span data-ttu-id="25857-110">Výraz, který se vyhodnotí na objekt.</span><span class="sxs-lookup"><span data-stu-id="25857-110">An expression that evaluates to an object.</span></span> <span data-ttu-id="25857-111">Výraz může být libovolně složitý a vyhodnotí se pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="25857-111">The expression may be arbitrarily complex and is evaluated only once.</span></span> <span data-ttu-id="25857-112">Výraz lze vyhodnotit na libovolný datový typ včetně základních typů.</span><span class="sxs-lookup"><span data-stu-id="25857-112">The expression can evaluate to any data type, including elementary types.</span></span>|  
|`statements`|<span data-ttu-id="25857-113">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="25857-113">Optional.</span></span> <span data-ttu-id="25857-114">Jeden nebo více příkazů mezi `With` a `End With` , mohou odkazovat na objekt, který je produkovaný vyhodnocení členů `objectExpression`.</span><span class="sxs-lookup"><span data-stu-id="25857-114">One or more statements between `With` and `End With` that may refer to members of an object that's produced by the evaluation of `objectExpression`.</span></span>|  
|`End With`|<span data-ttu-id="25857-115">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="25857-115">Required.</span></span> <span data-ttu-id="25857-116">Ukončí definice `With` bloku.</span><span class="sxs-lookup"><span data-stu-id="25857-116">Terminates the definition of the `With` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25857-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="25857-117">Remarks</span></span>  
 <span data-ttu-id="25857-118">Pomocí `With...End With`, můžete provádět řadu příkazů na zadaný objekt bez určení názvu objektu vícekrát.</span><span class="sxs-lookup"><span data-stu-id="25857-118">By using `With...End With`, you can perform a series of statements on a specified object without specifying the name of the object multiple times.</span></span> <span data-ttu-id="25857-119">V rámci `With` příkaz blok, můžete zadat členem objektu spouštění s dobou, jako kdyby `With` příkaz objekt před jeho.</span><span class="sxs-lookup"><span data-stu-id="25857-119">Within a `With` statement block, you can specify a member of the object starting with a period, as if the `With` statement object preceded it.</span></span>  
  
 <span data-ttu-id="25857-120">Například pokud chcete změnit víc vlastností na jeden objekt, umístěte příkazy přiřazení vlastnosti uvnitř `With...End With` bloku, odkaz na objekt pouze jednou místo jednou pro každou vlastnost přiřazení.</span><span class="sxs-lookup"><span data-stu-id="25857-120">For example, to change multiple properties on a single object, place the property assignment statements inside the `With...End With` block, referring to the object only once instead of once for each property assignment.</span></span>  
  
 <span data-ttu-id="25857-121">Pokud váš kód odkazuje na stejný objekt ve více příkazů, získáte následující výhody pomocí `With` příkaz:</span><span class="sxs-lookup"><span data-stu-id="25857-121">If your code accesses the same object in multiple statements, you gain the following benefits by using the `With` statement:</span></span>  
  
-   <span data-ttu-id="25857-122">Nemusíte vyhodnocovat složitý výraz vícekrát ani přiřazovat výsledek k dočasné proměnné, chcete-li na jeho členy odkazovat vícekrát.</span><span class="sxs-lookup"><span data-stu-id="25857-122">You don't need to evaluate a complex expression multiple times or assign the result to a temporary variable to refer to its members multiple times.</span></span>  
  
-   <span data-ttu-id="25857-123">Odstraněním opakovaných kvalifikačních výrazů zlepšíte přehlednost kódu.</span><span class="sxs-lookup"><span data-stu-id="25857-123">You make your code more readable by eliminating repetitive qualifying expressions.</span></span>  
  
 <span data-ttu-id="25857-124">Datový typ `objectExpression` může být jakákoli třída nebo struktura typ nebo i základní typ jazyka Visual Basic, jako `Integer`.</span><span class="sxs-lookup"><span data-stu-id="25857-124">The data type of `objectExpression` can be any class or structure type or even a Visual Basic elementary type such as `Integer`.</span></span>  <span data-ttu-id="25857-125">Pokud `objectExpression` výsledky v jakoukoli jinou hodnotu než objekt, můžete pouze číst hodnoty svých členů nebo volat metody a dojde k chybě, pokud se pokusíte přiřadit hodnoty členů struktury používá v `With...End With` příkaz.</span><span class="sxs-lookup"><span data-stu-id="25857-125">If `objectExpression` results in anything other than an object, you can only read the values of its members or invoke methods, and you get an error if you try to assign values to members of a structure used in a `With...End With` statement.</span></span>  <span data-ttu-id="25857-126">Toto je ke stejné chybě, které byste získali, pokud je vyvolána metoda, která vrátí strukturu a okamžitě získat přístup a přiřazenou hodnotu na člena, výsledku funkce, jako například `GetAPoint().x = 1`.</span><span class="sxs-lookup"><span data-stu-id="25857-126">This is the same error you would get if you invoked a method that returned a structure and immediately accessed and assigned a value to a member of the function’s result, such as `GetAPoint().x = 1`.</span></span>  <span data-ttu-id="25857-127">Problémem je v obou případech to, že tato struktura existuje pouze v zásobníku volání a neexistuje žádný způsob, jak člena změněné struktury v těchto situacích zapsat někam tak, aby jakýkoli jiný kód v programu tuto změnu zpozoroval.</span><span class="sxs-lookup"><span data-stu-id="25857-127">The problem in both cases is that the structure exists only on the call stack, and there is no way a modified structure member in these situations can write to  a location such that any other code in the program can observe the change.</span></span>  
  
 <span data-ttu-id="25857-128">`objectExpression` Jednou, vyhodnotí při vstupu do bloku.</span><span class="sxs-lookup"><span data-stu-id="25857-128">The `objectExpression` is evaluated once, upon entry into the block.</span></span> <span data-ttu-id="25857-129">Nelze přiřadit `objectExpression` uvnitř `With` bloku.</span><span class="sxs-lookup"><span data-stu-id="25857-129">You can't reassign the `objectExpression` from within the `With` block.</span></span>  
  
 <span data-ttu-id="25857-130">V rámci `With` bloku, dostanete metod a vlastností zadaného objektu bez kvalifikace je.</span><span class="sxs-lookup"><span data-stu-id="25857-130">Within a `With` block, you can access the methods and properties of only the specified object without qualifying them.</span></span> <span data-ttu-id="25857-131">Můžete použít metody a vlastnosti jiného objektu, musíte je ale kvalifikovat pomocí názvů jejich objektů.</span><span class="sxs-lookup"><span data-stu-id="25857-131">You can use methods and properties of other objects, but you must qualify them with their object names.</span></span>  
  
 <span data-ttu-id="25857-132">Můžete umístit jeden `With...End With` příkaz v rámci jiného.</span><span class="sxs-lookup"><span data-stu-id="25857-132">You can place one `With...End With` statement within another.</span></span> <span data-ttu-id="25857-133">Vnořené `With...End With` příkazy může být matoucí, pokud nejsou objekty, které jsou právě uvedených vymazat z kontextu.</span><span class="sxs-lookup"><span data-stu-id="25857-133">Nested `With...End With` statements may be confusing if the objects that are being referred to aren't clear from context.</span></span> <span data-ttu-id="25857-134">Je nutné zadat plně kvalifikovaný odkaz na objekt, který je v vnější `With` blokovat, pokud objekt se odkazuje z v rámci vnitřní `With` bloku.</span><span class="sxs-lookup"><span data-stu-id="25857-134">You must provide a fully qualified reference to an object that's in an outer `With` block when the object is referenced from within an inner `With` block.</span></span>  
  
 <span data-ttu-id="25857-135">Můžete nemůže provést větvení do `With` blok příkazu z mimo blok.</span><span class="sxs-lookup"><span data-stu-id="25857-135">You can't branch into a `With` statement block from outside the block.</span></span>  
  
 <span data-ttu-id="25857-136">Pokud blok neobsahuje cyklus, spustí se příkazy pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="25857-136">Unless the block contains a loop, the statements run only once.</span></span> <span data-ttu-id="25857-137">Je možné vnořovat různé druhy řídicích struktur.</span><span class="sxs-lookup"><span data-stu-id="25857-137">You can nest different kinds of control structures.</span></span> <span data-ttu-id="25857-138">Další informace najdete v tématu [vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="25857-138">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="25857-139">Můžete použít `With` – klíčové slovo v objektu inicializátory také.</span><span class="sxs-lookup"><span data-stu-id="25857-139">You can use the `With` keyword in object initializers also.</span></span> <span data-ttu-id="25857-140">Další informace a příklady naleznete v tématu [inicializátory objektů: pojmenované a anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) a [anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="25857-140">For more information and examples, see [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) and [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
>   
>  <span data-ttu-id="25857-141">Pokud používáte `With` blok jenom k inicializaci vlastnosti nebo pole objektu, který jste právě instanci, zvažte namísto toho použití inicializátoru objektu.</span><span class="sxs-lookup"><span data-stu-id="25857-141">If you're using a `With` block only to initialize the properties or fields of an object that you've just instantiated, consider using an object initializer instead.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25857-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="25857-142">Example</span></span>  
 <span data-ttu-id="25857-143">V následujícím příkladu každý `With` bloku provede řadu příkazů na jednoho objektu.</span><span class="sxs-lookup"><span data-stu-id="25857-143">In the following example, each `With` block executes a series of statements on a single object.</span></span>  
  
 [!code-vb[VbVbalrWithStatement#2](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/with-end-with-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="25857-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="25857-144">Example</span></span>  
 <span data-ttu-id="25857-145">Následující příklad vnoří `With…End With` příkazy.</span><span class="sxs-lookup"><span data-stu-id="25857-145">The following example nests `With…End With` statements.</span></span> <span data-ttu-id="25857-146">V rámci vnořeného `With` příkaz, syntaxe odkazuje na vnitřní objekt.</span><span class="sxs-lookup"><span data-stu-id="25857-146">Within the nested `With` statement, the syntax refers to the inner object.</span></span>  
  
 [!code-vb[VbVbalrWithStatement#1](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/with-end-with-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="25857-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="25857-147">See Also</span></span>  
 <xref:System.Collections.Generic.List%601>  
 [<span data-ttu-id="25857-148">Vnořené řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="25857-148">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="25857-149">Inicializátory objektů: pojmenované a anonymní typy</span><span class="sxs-lookup"><span data-stu-id="25857-149">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [<span data-ttu-id="25857-150">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="25857-150">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
