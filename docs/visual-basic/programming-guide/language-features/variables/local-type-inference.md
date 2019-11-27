---
title: Odvození místního typu
ms.date: 07/20/2015
f1_keywords:
- local type inference
- vb.TypeInfer
helpviewer_keywords:
- Option Infer statement [Visual Basic]
- local type inference [Visual Basic]
- implicitly-typed local variables [Visual Basic]
- variables [Visual Basic], type inference
- inference [Visual Basic]
- type inference [Visual Basic]
ms.assetid: b8307f18-2e56-4ab3-a45a-826873f400f6
ms.openlocfilehash: f79ac70aecb5805a3a4a4fea8f7e7ccd3f8243fc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351838"
---
# <a name="local-type-inference-visual-basic"></a><span data-ttu-id="d28b8-102">Odvození místního typu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d28b8-102">Local Type Inference (Visual Basic)</span></span>

<span data-ttu-id="d28b8-103">Kompilátor Visual Basic používá *odvození typu* k určení datových typů místních proměnných deklarovaných bez klauzule `As`.</span><span class="sxs-lookup"><span data-stu-id="d28b8-103">The Visual Basic compiler uses *type inference* to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="d28b8-104">Kompilátor odvodí typ proměnné z typu inicializačního výrazu.</span><span class="sxs-lookup"><span data-stu-id="d28b8-104">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="d28b8-105">To umožňuje deklarovat proměnné bez explicitního oznámení typu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d28b8-105">This enables you to declare variables without explicitly stating a type, as shown in the following example.</span></span> <span data-ttu-id="d28b8-106">V důsledku deklarací jsou jako celé číslo `num1` i `num2` silného typu.</span><span class="sxs-lookup"><span data-stu-id="d28b8-106">As a result of the declarations, both `num1` and `num2` are strongly typed as integers.</span></span>

[!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]

> [!NOTE]
> <span data-ttu-id="d28b8-107">Pokud nechcete, aby `num2` v předchozím příkladu jako `Integer`, můžete zadat jiný typ pomocí deklarace, jako je `Dim num3 As Object = 3` nebo `Dim num4 As Double = 3`.</span><span class="sxs-lookup"><span data-stu-id="d28b8-107">If you do not want `num2` in the previous example to be typed as an `Integer`, you can specify another type by using a declaration like `Dim num3 As Object = 3` or `Dim num4 As Double = 3`.</span></span>

> [!NOTE]
> <span data-ttu-id="d28b8-108">Odvození typu lze použít pouze pro nestatické lokální proměnné; nelze ji použít k určení typu polí třídy, vlastností nebo funkcí.</span><span class="sxs-lookup"><span data-stu-id="d28b8-108">Type inference can be used only for non-static local variables; it cannot be used to determine the type of class fields, properties, or functions.</span></span>

<span data-ttu-id="d28b8-109">Odvození místního typu se vztahuje na úrovni procedury.</span><span class="sxs-lookup"><span data-stu-id="d28b8-109">Local type inference applies at procedure level.</span></span> <span data-ttu-id="d28b8-110">Nedá se použít k deklaraci proměnných na úrovni modulu (v rámci třídy, struktury, modulu nebo rozhraní, ale ne v rámci procedury nebo bloku).</span><span class="sxs-lookup"><span data-stu-id="d28b8-110">It cannot be used to declare variables at module level (within a class, structure, module, or interface but not within a procedure or block).</span></span> <span data-ttu-id="d28b8-111">Pokud `num2` v předchozím příkladu byly polem třídy namísto lokální proměnné v proceduře, by deklarace způsobila chybu s `Option Strict` na a mohla klasifikovat `num2` jako `Object` s `Option Strict` vypnuto.</span><span class="sxs-lookup"><span data-stu-id="d28b8-111">If `num2` in the previous example were a field of a class instead of a local variable in a procedure, the declaration would cause an error with `Option Strict` on, and would classify `num2` as an `Object` with `Option Strict` off.</span></span> <span data-ttu-id="d28b8-112">Podobně odvození místního typu se nevztahuje na proměnné na úrovni procedury deklarované jako `Static`.</span><span class="sxs-lookup"><span data-stu-id="d28b8-112">Similarly, local type inference does not apply to procedure level variables declared as `Static`.</span></span>

## <a name="type-inference-vs-late-binding"></a><span data-ttu-id="d28b8-113">Odvození typu a pozdní vazba</span><span class="sxs-lookup"><span data-stu-id="d28b8-113">Type Inference vs. Late Binding</span></span>

<span data-ttu-id="d28b8-114">Kód, který používá odvození typu, se podobá kódu, který závisí na pozdní vazbě.</span><span class="sxs-lookup"><span data-stu-id="d28b8-114">Code that uses type inference resembles code that relies on late binding.</span></span> <span data-ttu-id="d28b8-115">Nicméně odvození typu je místo toho, aby byla proměnná ponechána jako `Object`.</span><span class="sxs-lookup"><span data-stu-id="d28b8-115">However, type inference strongly types the variable instead of leaving it as `Object`.</span></span> <span data-ttu-id="d28b8-116">Kompilátor používá inicializátor proměnné k určení typu proměnné v době kompilace pro vytvoření kódu na začátku vazby.</span><span class="sxs-lookup"><span data-stu-id="d28b8-116">The compiler uses a variable's initializer to determine the variable's type at compile time to produce early-bound code.</span></span> <span data-ttu-id="d28b8-117">V předchozím příkladu je `num2`jako `num1`typu `Integer`.</span><span class="sxs-lookup"><span data-stu-id="d28b8-117">In the previous example, `num2`, like `num1`, is typed as an `Integer`.</span></span>

<span data-ttu-id="d28b8-118">Chování proměnných s časnou vazbou se liší od proměnné s pozdní vazbou, pro které je typ znám pouze v době běhu.</span><span class="sxs-lookup"><span data-stu-id="d28b8-118">The behavior of early-bound variables differs from that of late-bound variables, for which the type is known only at run time.</span></span> <span data-ttu-id="d28b8-119">Znalost typu předčasné umožňuje kompilátoru identifikovat problémy před provedením, přidělit paměť přesně a provádět další optimalizace.</span><span class="sxs-lookup"><span data-stu-id="d28b8-119">Knowing the type early enables the compiler to identify problems before execution, allocate memory precisely, and perform other optimizations.</span></span> <span data-ttu-id="d28b8-120">Časná vazba také umožňuje Visual Basic integrované vývojové prostředí (IDE), které poskytuje nápovědu IntelliSense o členech objektu.</span><span class="sxs-lookup"><span data-stu-id="d28b8-120">Early binding also enables the Visual Basic integrated development environment (IDE) to provide IntelliSense Help about the members of an object.</span></span> <span data-ttu-id="d28b8-121">Pro výkon je upřednostňována i počáteční vazba.</span><span class="sxs-lookup"><span data-stu-id="d28b8-121">Early binding is also preferred for performance.</span></span> <span data-ttu-id="d28b8-122">Důvodem je, že všechna data uložená v proměnné s pozdní vazbou musí být zabalena jako typ `Object`a přístup k členům typu za běhu program zpomalí.</span><span class="sxs-lookup"><span data-stu-id="d28b8-122">This is because all data stored in a late-bound variable must be wrapped as type `Object`, and accessing members of the type at run time makes the program slower.</span></span>

## <a name="examples"></a><span data-ttu-id="d28b8-123">Příklady</span><span class="sxs-lookup"><span data-stu-id="d28b8-123">Examples</span></span>

<span data-ttu-id="d28b8-124">Odvození typu nastane, pokud je místní proměnná deklarována bez klauzule `As` a inicializovaná.</span><span class="sxs-lookup"><span data-stu-id="d28b8-124">Type inference occurs when a local variable is declared without an `As` clause and initialized.</span></span> <span data-ttu-id="d28b8-125">Kompilátor používá typ přiřazené počáteční hodnoty jako typ proměnné.</span><span class="sxs-lookup"><span data-stu-id="d28b8-125">The compiler uses the type of the assigned initial value as the type of the variable.</span></span> <span data-ttu-id="d28b8-126">Například každý z následujících řádků kódu deklaruje proměnnou typu `String`.</span><span class="sxs-lookup"><span data-stu-id="d28b8-126">For example, each of the following lines of code declares a variable of type `String`.</span></span>

[!code-vb[VbVbalrTypeInference#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#2)]

<span data-ttu-id="d28b8-127">Následující kód ukazuje dva ekvivalentní způsoby, jak vytvořit pole celých čísel.</span><span class="sxs-lookup"><span data-stu-id="d28b8-127">The following code demonstrates two equivalent ways to create an array of integers.</span></span>

[!code-vb[VbVbalrTypeInference#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#3)]

<span data-ttu-id="d28b8-128">Je vhodné použít odvození typu k určení typu řídicí proměnné smyčky.</span><span class="sxs-lookup"><span data-stu-id="d28b8-128">It is convenient to use type inference to determine the type of a loop control variable.</span></span> <span data-ttu-id="d28b8-129">V následujícím kódu kompilátor odvodí, že `number` je `Integer`, protože `someNumbers2` z předchozího příkladu je pole celých čísel.</span><span class="sxs-lookup"><span data-stu-id="d28b8-129">In the following code, the compiler infers that `number` is an `Integer` because `someNumbers2` from the previous example is an array of integers.</span></span>

[!code-vb[VbVbalrTypeInference#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#4)]

<span data-ttu-id="d28b8-130">Odvození místního typu lze použít v příkazech `Using` pro vytvoření typu názvu prostředku, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="d28b8-130">Local type inference can be used in `Using` statements to establish the type of the resource name, as the following example demonstrates.</span></span>

[!code-vb[VbVbalrTypeInference#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#7)]

<span data-ttu-id="d28b8-131">Typ proměnné lze také odvodit z vrácených hodnot funkcí, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="d28b8-131">The type of a variable can also be inferred from the return values of functions, as the following example demonstrates.</span></span> <span data-ttu-id="d28b8-132">`pList1` i `pList2` jsou pole procesů, protože `Process.GetProcesses` vrací pole procesů.</span><span class="sxs-lookup"><span data-stu-id="d28b8-132">Both `pList1` and `pList2` are arrays of processes because `Process.GetProcesses` returns an array of processes.</span></span>

[!code-vb[VbVbalrTypeInference#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#5)]

## <a name="option-infer"></a><span data-ttu-id="d28b8-133">Odvoditelné možnosti</span><span class="sxs-lookup"><span data-stu-id="d28b8-133">Option Infer</span></span>

<span data-ttu-id="d28b8-134">`Option Infer` umožňuje určit, zda je místní odvozený typ povolen v určitém souboru.</span><span class="sxs-lookup"><span data-stu-id="d28b8-134">`Option Infer` enables you specify whether local type inference is allowed in a particular file.</span></span> <span data-ttu-id="d28b8-135">Chcete-li povolit nebo zablokovat možnost, zadejte na začátku souboru jeden z následujících příkazů.</span><span class="sxs-lookup"><span data-stu-id="d28b8-135">To enable or to block the option, type one of the following statements at the start of the file.</span></span>

`Option Infer On`

`Option Infer Off`

<span data-ttu-id="d28b8-136">Pokud nezadáte hodnotu pro `Option Infer` v kódu, výchozí hodnota kompilátoru je `Option Infer On`.</span><span class="sxs-lookup"><span data-stu-id="d28b8-136">If you do not specify a value for `Option Infer` in your code, the compiler default is `Option Infer On`.</span></span>

<span data-ttu-id="d28b8-137">Pokud je hodnota nastavená pro `Option Infer` v souboru v konfliktu s hodnotou nastavenou v integrovaném vývojovém prostředí (IDE) nebo na příkazovém řádku, má hodnota v souboru přednost.</span><span class="sxs-lookup"><span data-stu-id="d28b8-137">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>

<span data-ttu-id="d28b8-138">Další informace naleznete v tématu [možnost odvození příkazu](../../../../visual-basic/language-reference/statements/option-infer-statement.md) a [Stránka kompilace, návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="d28b8-138">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>

## <a name="see-also"></a><span data-ttu-id="d28b8-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d28b8-139">See also</span></span>

- [<span data-ttu-id="d28b8-140">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="d28b8-140">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="d28b8-141">Statické a pozdní vazby</span><span class="sxs-lookup"><span data-stu-id="d28b8-141">Early and Late Binding</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [<span data-ttu-id="d28b8-142">Příkaz For Each...Next</span><span class="sxs-lookup"><span data-stu-id="d28b8-142">For Each...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="d28b8-143">Příkaz For...Next</span><span class="sxs-lookup"><span data-stu-id="d28b8-143">For...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="d28b8-144">Příkaz Option Infer</span><span class="sxs-lookup"><span data-stu-id="d28b8-144">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="d28b8-145">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="d28b8-145">-optioninfer</span></span>](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="d28b8-146">Úvod do jazyka LINQ v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d28b8-146">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
