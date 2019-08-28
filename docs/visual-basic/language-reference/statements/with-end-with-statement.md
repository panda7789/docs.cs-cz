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
ms.openlocfilehash: 3c6766d9084962d006fe5e5d7d5cc723c2aad441
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046633"
---
# <a name="withend-with-statement-visual-basic"></a><span data-ttu-id="a780b-102">With...End With – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a780b-102">With...End With Statement (Visual Basic)</span></span>

<span data-ttu-id="a780b-103">Vykoná řadu příkazů, které opakovaně odkazují na jeden objekt nebo strukturu, takže příkazy mohou při přístupu k členům tohoto objektu nebo struktury použít zjednodušenou syntaxi.</span><span class="sxs-lookup"><span data-stu-id="a780b-103">Executes a series of statements that repeatedly refer to a single object or structure so that the statements can use a simplified syntax when accessing members of the object or structure.</span></span>  <span data-ttu-id="a780b-104">Při použití struktury lze číst pouze hodnoty členů nebo vyvolat metody a při pokusu o přiřazení hodnot členům struktury použité v `With...End With` příkazu se zobrazí chyba.</span><span class="sxs-lookup"><span data-stu-id="a780b-104">When using a structure, you can only read the values of members or invoke methods, and you get an error if you try to assign values to members of a structure used in a `With...End With` statement.</span></span>

## <a name="syntax"></a><span data-ttu-id="a780b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a780b-105">Syntax</span></span>

```
With objectExpression
    [ statements ]
End With
```

## <a name="parts"></a><span data-ttu-id="a780b-106">Součásti</span><span class="sxs-lookup"><span data-stu-id="a780b-106">Parts</span></span>

|<span data-ttu-id="a780b-107">Termín</span><span class="sxs-lookup"><span data-stu-id="a780b-107">Term</span></span>|<span data-ttu-id="a780b-108">Definice</span><span class="sxs-lookup"><span data-stu-id="a780b-108">Definition</span></span>|
|---|---|
|`objectExpression`|<span data-ttu-id="a780b-109">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="a780b-109">Required.</span></span> <span data-ttu-id="a780b-110">Výraz, který se vyhodnotí na objekt.</span><span class="sxs-lookup"><span data-stu-id="a780b-110">An expression that evaluates to an object.</span></span> <span data-ttu-id="a780b-111">Výraz může být libovolně složitý a vyhodnotí se pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="a780b-111">The expression may be arbitrarily complex and is evaluated only once.</span></span> <span data-ttu-id="a780b-112">Výraz lze vyhodnotit na libovolný datový typ včetně základních typů.</span><span class="sxs-lookup"><span data-stu-id="a780b-112">The expression can evaluate to any data type, including elementary types.</span></span>|
|`statements`|<span data-ttu-id="a780b-113">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="a780b-113">Optional.</span></span> <span data-ttu-id="a780b-114">Jeden nebo více příkazů mezi `With` a `End With` , které mohou odkazovat na členy objektu, který je `objectExpression`vytvořen vyhodnocením.</span><span class="sxs-lookup"><span data-stu-id="a780b-114">One or more statements between `With` and `End With` that may refer to members of an object that's produced by the evaluation of `objectExpression`.</span></span>|
|`End With`|<span data-ttu-id="a780b-115">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="a780b-115">Required.</span></span> <span data-ttu-id="a780b-116">Ukončí definici `With` bloku.</span><span class="sxs-lookup"><span data-stu-id="a780b-116">Terminates the definition of the `With` block.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a780b-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a780b-117">Remarks</span></span>

<span data-ttu-id="a780b-118">Pomocí `With...End With`můžete provést sérii příkazů na zadaném objektu bez zadání názvu objektu vícekrát.</span><span class="sxs-lookup"><span data-stu-id="a780b-118">By using `With...End With`, you can perform a series of statements on a specified object without specifying the name of the object multiple times.</span></span> <span data-ttu-id="a780b-119">V rámci bloku `With` příkazumůžeteurčitčlenaobjektuzačínajícíhotečkou,jakobybylpředním`With` uveden objekt příkazu.</span><span class="sxs-lookup"><span data-stu-id="a780b-119">Within a `With` statement block, you can specify a member of the object starting with a period, as if the `With` statement object preceded it.</span></span>

<span data-ttu-id="a780b-120">Chcete-li například změnit více vlastností na jednom objektu, umístěte příkazy přiřazení vlastností dovnitř `With...End With` bloku a odkaz na objekt pouze jednou pro každé přiřazení vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a780b-120">For example, to change multiple properties on a single object, place the property assignment statements inside the `With...End With` block, referring to the object only once instead of once for each property assignment.</span></span>

<span data-ttu-id="a780b-121">Pokud váš kód přistupuje ke stejnému objektu ve více příkazech, získáte následující výhody pomocí `With` příkazu:</span><span class="sxs-lookup"><span data-stu-id="a780b-121">If your code accesses the same object in multiple statements, you gain the following benefits by using the `With` statement:</span></span>

- <span data-ttu-id="a780b-122">Nemusíte vyhodnocovat složitý výraz vícekrát ani přiřazovat výsledek k dočasné proměnné, chcete-li na jeho členy odkazovat vícekrát.</span><span class="sxs-lookup"><span data-stu-id="a780b-122">You don't need to evaluate a complex expression multiple times or assign the result to a temporary variable to refer to its members multiple times.</span></span>

- <span data-ttu-id="a780b-123">Odstraněním opakovaných kvalifikačních výrazů zlepšíte přehlednost kódu.</span><span class="sxs-lookup"><span data-stu-id="a780b-123">You make your code more readable by eliminating repetitive qualifying expressions.</span></span>

<span data-ttu-id="a780b-124">Datový typ `objectExpression` může být libovolný typ třídy nebo struktury nebo i Visual Basic základní typ, jako je `Integer`.</span><span class="sxs-lookup"><span data-stu-id="a780b-124">The data type of `objectExpression` can be any class or structure type or even a Visual Basic elementary type such as `Integer`.</span></span>  <span data-ttu-id="a780b-125">Pokud `objectExpression` je výsledkem cokoli jiného než objekt, můžete číst pouze hodnoty jeho členů nebo vyvolat metody a při pokusu o přiřazení hodnot členům struktury použité `With...End With` v příkazu se zobrazí chyba.</span><span class="sxs-lookup"><span data-stu-id="a780b-125">If `objectExpression` results in anything other than an object, you can only read the values of its members or invoke methods, and you get an error if you try to assign values to members of a structure used in a `With...End With` statement.</span></span>  <span data-ttu-id="a780b-126">Jedná se o stejnou chybu, která by se vám měla zobrazit, pokud jste vyvolali metodu, která vrátila strukturu a hned k ní přistupovala hodnotu a přiřadili `GetAPoint().x = 1`ji členu výsledku funkce, jako je například.</span><span class="sxs-lookup"><span data-stu-id="a780b-126">This is the same error you would get if you invoked a method that returned a structure and immediately accessed and assigned a value to a member of the function’s result, such as `GetAPoint().x = 1`.</span></span>  <span data-ttu-id="a780b-127">Problémem je v obou případech to, že tato struktura existuje pouze v zásobníku volání a neexistuje žádný způsob, jak člena změněné struktury v těchto situacích zapsat někam tak, aby jakýkoli jiný kód v programu tuto změnu zpozoroval.</span><span class="sxs-lookup"><span data-stu-id="a780b-127">The problem in both cases is that the structure exists only on the call stack, and there is no way a modified structure member in these situations can write to  a location such that any other code in the program can observe the change.</span></span>

<span data-ttu-id="a780b-128">`objectExpression` Je vyhodnocen jednou při vstupu do bloku.</span><span class="sxs-lookup"><span data-stu-id="a780b-128">The `objectExpression` is evaluated once, upon entry into the block.</span></span> <span data-ttu-id="a780b-129">Nemůžete znovu přiřadit `objectExpression` v `With` rámci bloku.</span><span class="sxs-lookup"><span data-stu-id="a780b-129">You can't reassign the `objectExpression` from within the `With` block.</span></span>

<span data-ttu-id="a780b-130">V rámci `With` bloku máte přístup k metodám a vlastnostem pouze zadaného objektu, aniž byste je museli kvalifikovat.</span><span class="sxs-lookup"><span data-stu-id="a780b-130">Within a `With` block, you can access the methods and properties of only the specified object without qualifying them.</span></span> <span data-ttu-id="a780b-131">Můžete použít metody a vlastnosti jiného objektu, musíte je ale kvalifikovat pomocí názvů jejich objektů.</span><span class="sxs-lookup"><span data-stu-id="a780b-131">You can use methods and properties of other objects, but you must qualify them with their object names.</span></span>

<span data-ttu-id="a780b-132">Jeden `With...End With` příkaz můžete umístit do jiného.</span><span class="sxs-lookup"><span data-stu-id="a780b-132">You can place one `With...End With` statement within another.</span></span> <span data-ttu-id="a780b-133">Vnořené `With...End With` příkazy mohou být matoucí, pokud objekty, na které se říkáte, nejsou jasné z kontextu.</span><span class="sxs-lookup"><span data-stu-id="a780b-133">Nested `With...End With` statements may be confusing if the objects that are being referred to aren't clear from context.</span></span> <span data-ttu-id="a780b-134">Je nutné zadat plně kvalifikovaný odkaz na objekt, který je uvnitř vnějšího `With` bloku, pokud je objekt odkazován z vnitřního `With` bloku.</span><span class="sxs-lookup"><span data-stu-id="a780b-134">You must provide a fully qualified reference to an object that's in an outer `With` block when the object is referenced from within an inner `With` block.</span></span>

<span data-ttu-id="a780b-135">Do bloku příkazu nemůžete vytvořit `With` větev mimo blok.</span><span class="sxs-lookup"><span data-stu-id="a780b-135">You can't branch into a `With` statement block from outside the block.</span></span>

<span data-ttu-id="a780b-136">Pokud blok neobsahuje cyklus, spustí se příkazy pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="a780b-136">Unless the block contains a loop, the statements run only once.</span></span> <span data-ttu-id="a780b-137">Je možné vnořovat různé druhy řídicích struktur.</span><span class="sxs-lookup"><span data-stu-id="a780b-137">You can nest different kinds of control structures.</span></span> <span data-ttu-id="a780b-138">Další informace najdete v tématu [vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="a780b-138">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>

> [!NOTE]
> <span data-ttu-id="a780b-139">`With` Klíčové slovo lze použít také v inicializátorech objektů.</span><span class="sxs-lookup"><span data-stu-id="a780b-139">You can use the `With` keyword in object initializers also.</span></span> <span data-ttu-id="a780b-140">Další informace a příklady naleznete v tématu [Inicializátory objektů: Pojmenované a anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) a [anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="a780b-140">For more information and examples, see [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) and [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>
>
> <span data-ttu-id="a780b-141">Pokud používáte `With` blok pouze k inicializaci vlastností nebo polí objektu, který jste právě vytvořili, zvažte místo toho použití inicializátoru objektu.</span><span class="sxs-lookup"><span data-stu-id="a780b-141">If you're using a `With` block only to initialize the properties or fields of an object that you've just instantiated, consider using an object initializer instead.</span></span>

## <a name="example"></a><span data-ttu-id="a780b-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="a780b-142">Example</span></span>

<span data-ttu-id="a780b-143">V následujícím příkladu každý `With` blok provádí sérii příkazů na jednom objektu.</span><span class="sxs-lookup"><span data-stu-id="a780b-143">In the following example, each `With` block executes a series of statements on a single object.</span></span>

[!code-vb[VbVbalrWithStatement#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#2)]

## <a name="example"></a><span data-ttu-id="a780b-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="a780b-144">Example</span></span>

<span data-ttu-id="a780b-145">Následující příklad vnořování `With…End With` příkazů.</span><span class="sxs-lookup"><span data-stu-id="a780b-145">The following example nests `With…End With` statements.</span></span> <span data-ttu-id="a780b-146">V rámci vnořeného `With` příkazu syntaxe odkazuje na vnitřní objekt.</span><span class="sxs-lookup"><span data-stu-id="a780b-146">Within the nested `With` statement, the syntax refers to the inner object.</span></span>

[!code-vb[VbVbalrWithStatement#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="a780b-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a780b-147">See also</span></span>

- <xref:System.Collections.Generic.List%601>
- [<span data-ttu-id="a780b-148">Vnořené řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="a780b-148">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="a780b-149">Inicializátory objektů: Pojmenované a anonymní typy</span><span class="sxs-lookup"><span data-stu-id="a780b-149">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="a780b-150">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="a780b-150">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
