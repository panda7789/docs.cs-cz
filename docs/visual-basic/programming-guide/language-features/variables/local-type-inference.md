---
title: Odvození místního typu (Visual Basic)
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
ms.openlocfilehash: 62f46f8f9691dd260e4a4c40c0ffccbce4c5beb7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973402"
---
# <a name="local-type-inference-visual-basic"></a><span data-ttu-id="2d8e1-102">Odvození místního typu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d8e1-102">Local Type Inference (Visual Basic)</span></span>
<span data-ttu-id="2d8e1-103">Kompilátor jazyka Visual Basic používá *odvození typu* určit typy dat místní proměnné deklarované bez `As` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="2d8e1-103">The Visual Basic compiler uses *type inference* to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="2d8e1-104">Kompilátor odvodí typ proměnné z typu výrazu inicializace.</span><span class="sxs-lookup"><span data-stu-id="2d8e1-104">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="2d8e1-105">To umožňuje deklarovat proměnné bez explicitně typu, s informacemi o tom, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2d8e1-105">This enables you to declare variables without explicitly stating a type, as shown in the following example.</span></span> <span data-ttu-id="2d8e1-106">V důsledku deklarace obě `num1` a `num2` jsou silného typu jako celá čísla.</span><span class="sxs-lookup"><span data-stu-id="2d8e1-106">As a result of the declarations, both `num1` and `num2` are strongly typed as integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
 
> [!NOTE]
>  <span data-ttu-id="2d8e1-107">Pokud nechcete, aby `num2` v předchozím příkladu na zadaný jako `Integer`, můžete určit jiný typ pomocí deklarací, jako `Dim num3 As Object = 3` nebo `Dim num4 As Double = 3`.</span><span class="sxs-lookup"><span data-stu-id="2d8e1-107">If you do not want `num2` in the previous example to be typed as an `Integer`, you can specify another type by using a declaration like `Dim num3 As Object = 3` or `Dim num4 As Double = 3`.</span></span>  

> [!NOTE]
>  <span data-ttu-id="2d8e1-108">Odvození typu proměnné lze použít pouze pro nestatické lokální proměnné; nedá se použít k určení typu třídy pole, vlastnosti a funkce.</span><span class="sxs-lookup"><span data-stu-id="2d8e1-108">Type inference can be used only for non-static local variables; it cannot be used to determine the type of class fields, properties, or functions.</span></span>
 
 <span data-ttu-id="2d8e1-109">Odvození místního typu se vztahuje na úrovni postup.</span><span class="sxs-lookup"><span data-stu-id="2d8e1-109">Local type inference applies at procedure level.</span></span> <span data-ttu-id="2d8e1-110">Nelze použít pro deklarování proměnných na úrovni modulu (v rámci třídy, struktury, modul nebo rozhraní, ale není v rozsahu proceduru nebo blok).</span><span class="sxs-lookup"><span data-stu-id="2d8e1-110">It cannot be used to declare variables at module level (within a class, structure, module, or interface but not within a procedure or block).</span></span> <span data-ttu-id="2d8e1-111">Pokud `num2` v předchozím příkladu se o pole třídy místo místní proměnné v postupu, deklarace by způsobila chybu s `Option Strict` a bude klasifikovat `num2` jako `Object` s `Option Strict` vypnout.</span><span class="sxs-lookup"><span data-stu-id="2d8e1-111">If `num2` in the previous example were a field of a class instead of a local variable in a procedure, the declaration would cause an error with `Option Strict` on, and would classify `num2` as an `Object` with `Option Strict` off.</span></span> <span data-ttu-id="2d8e1-112">Podobně, se nedá použít odvození místního typu k postupu úrovně proměnné deklarované jako `Static`.</span><span class="sxs-lookup"><span data-stu-id="2d8e1-112">Similarly, local type inference does not apply to procedure level variables declared as `Static`.</span></span>  
  
## <a name="type-inference-vs-late-binding"></a><span data-ttu-id="2d8e1-113">Typ odvození vs. Pozdní vazby</span><span class="sxs-lookup"><span data-stu-id="2d8e1-113">Type Inference vs. Late Binding</span></span>  
 <span data-ttu-id="2d8e1-114">Kód, že použití odvození typu vypadá podobně jako kód, který využívá pozdní vazby.</span><span class="sxs-lookup"><span data-stu-id="2d8e1-114">Code that uses type inference resembles code that relies on late binding.</span></span> <span data-ttu-id="2d8e1-115">Však odvození typu silnými typy proměnnou nenechávejte jako `Object`.</span><span class="sxs-lookup"><span data-stu-id="2d8e1-115">However, type inference strongly types the variable instead of leaving it as `Object`.</span></span> <span data-ttu-id="2d8e1-116">Kompilátor používá k určení typu proměnné v době kompilace pro vytvoření kódu časné vazby proměnná inicializátor.</span><span class="sxs-lookup"><span data-stu-id="2d8e1-116">The compiler uses a variable's initializer to determine the variable's type at compile time to produce early-bound code.</span></span> <span data-ttu-id="2d8e1-117">V předchozím příkladu `num2`, třeba `num1`, je `Integer`.</span><span class="sxs-lookup"><span data-stu-id="2d8e1-117">In the previous example, `num2`, like `num1`, is typed as an `Integer`.</span></span>  
  
 <span data-ttu-id="2d8e1-118">Chování časné vazby proměnné se liší od proměnné s pozdní vazbou, pro které typ je znám pouze za běhu.</span><span class="sxs-lookup"><span data-stu-id="2d8e1-118">The behavior of early-bound variables differs from that of late-bound variables, for which the type is known only at run time.</span></span> <span data-ttu-id="2d8e1-119">Vědomí, že typ již v rané fázi umožňuje kompilátoru k identifikaci problémů před spuštěním, přesně přidělení paměti a provádět další optimalizace.</span><span class="sxs-lookup"><span data-stu-id="2d8e1-119">Knowing the type early enables the compiler to identify problems before execution, allocate memory precisely, and perform other optimizations.</span></span> <span data-ttu-id="2d8e1-120">Časná vazba umožňuje také integrovaného vývojového prostředí (IDE) k poskytnutí technologie IntelliSense nápovědy o členy objektu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2d8e1-120">Early binding also enables the Visual Basic integrated development environment (IDE) to provide IntelliSense Help about the members of an object.</span></span> <span data-ttu-id="2d8e1-121">Časná vazba je také upřednostněny výkonu.</span><span class="sxs-lookup"><span data-stu-id="2d8e1-121">Early binding is also preferred for performance.</span></span> <span data-ttu-id="2d8e1-122">Důvodem je, že všechna data uložená v proměnné s pozdní vazbou, musí být zabalené jako typ `Object`, a přístup k členům typu za běhu programu pomalejší.</span><span class="sxs-lookup"><span data-stu-id="2d8e1-122">This is because all data stored in a late-bound variable must be wrapped as type `Object`, and accessing members of the type at run time makes the program slower.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="2d8e1-123">Příklady</span><span class="sxs-lookup"><span data-stu-id="2d8e1-123">Examples</span></span>  
 <span data-ttu-id="2d8e1-124">Odvození typu vyvolá se v případě lokální proměnná je deklarovaná bez `As` klauzule a inicializován.</span><span class="sxs-lookup"><span data-stu-id="2d8e1-124">Type inference occurs when a local variable is declared without an `As` clause and initialized.</span></span> <span data-ttu-id="2d8e1-125">Kompilátor používá jako typ proměnné typu počáteční hodnota.</span><span class="sxs-lookup"><span data-stu-id="2d8e1-125">The compiler uses the type of the assigned initial value as the type of the variable.</span></span> <span data-ttu-id="2d8e1-126">Například všechny následující řádky kódu deklaruje proměnnou typu `String`.</span><span class="sxs-lookup"><span data-stu-id="2d8e1-126">For example, each of the following lines of code declares a variable of type `String`.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#2)]  
  
 <span data-ttu-id="2d8e1-127">Následující kód ukazuje dva ekvivalentní způsoby, jak vytvořit pole celých čísel.</span><span class="sxs-lookup"><span data-stu-id="2d8e1-127">The following code demonstrates two equivalent ways to create an array of integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#3)]  
  
 <span data-ttu-id="2d8e1-128">Je vhodné použít odvození typu k určení typu řídicí proměnná smyčky for.</span><span class="sxs-lookup"><span data-stu-id="2d8e1-128">It is convenient to use type inference to determine the type of a loop control variable.</span></span> <span data-ttu-id="2d8e1-129">V následujícím kódu, kompilátor odvodí, které `number` je `Integer` protože `someNumbers2` z předchozího příkladu je pole celých čísel.</span><span class="sxs-lookup"><span data-stu-id="2d8e1-129">In the following code, the compiler infers that `number` is an `Integer` because `someNumbers2` from the previous example is an array of integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#4)]  
  
 <span data-ttu-id="2d8e1-130">Odvození místního typu lze použít v `Using` příkazy k vytvoření typu název prostředku, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="2d8e1-130">Local type inference can be used in `Using` statements to establish the type of the resource name, as the following example demonstrates.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#7)]  
  
 <span data-ttu-id="2d8e1-131">Typ proměnné také jde odvodit z návratové hodnoty funkce, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="2d8e1-131">The type of a variable can also be inferred from the return values of functions, as the following example demonstrates.</span></span> <span data-ttu-id="2d8e1-132">Obě `pList1` a `pList2` jsou pole procesů, protože `Process.GetProcesses` vrátí celou řadu procesů.</span><span class="sxs-lookup"><span data-stu-id="2d8e1-132">Both `pList1` and `pList2` are arrays of processes because `Process.GetProcesses` returns an array of processes.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#5)]  
  
## <a name="option-infer"></a><span data-ttu-id="2d8e1-133">Option Infer</span><span class="sxs-lookup"><span data-stu-id="2d8e1-133">Option Infer</span></span>  
 <span data-ttu-id="2d8e1-134">`Option Infer` Umožňuje určit, zda je povolena odvození místního typu v určitý soubor.</span><span class="sxs-lookup"><span data-stu-id="2d8e1-134">`Option Infer` enables you specify whether local type inference is allowed in a particular file.</span></span> <span data-ttu-id="2d8e1-135">Povolit nebo blokovat možnost, zadejte jeden z následujících příkazů na začátku souboru.</span><span class="sxs-lookup"><span data-stu-id="2d8e1-135">To enable or to block the option, type one of the following statements at the start of the file.</span></span>  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 <span data-ttu-id="2d8e1-136">Pokud nezadáte hodnotu `Option Infer` ve vašem kódu, je výchozí nastavení kompilátoru `Option Infer On`.</span><span class="sxs-lookup"><span data-stu-id="2d8e1-136">If you do not specify a value for `Option Infer` in your code, the compiler default is `Option Infer On`.</span></span> <span data-ttu-id="2d8e1-137">Pro projekty upgradovali z [!INCLUDE[vb_orcas_long](~/includes/vb-orcas-long-md.md)] nebo starší, je výchozí nastavení kompilátoru `Option Infer Off`.</span><span class="sxs-lookup"><span data-stu-id="2d8e1-137">For projects upgraded from [!INCLUDE[vb_orcas_long](~/includes/vb-orcas-long-md.md)] or earlier, the compiler default is `Option Infer Off`.</span></span>  
  
 <span data-ttu-id="2d8e1-138">Je-li nastavena hodnota pro `Option Infer` v souboru konflikty s hodnotou nastavenou v integrovaném vývojovém prostředí nebo na příkazovém řádku, hodnota v souboru má prioritu.</span><span class="sxs-lookup"><span data-stu-id="2d8e1-138">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="2d8e1-139">Další informace najdete v tématu [Option Infer – příkaz](../../../../visual-basic/language-reference/statements/option-infer-statement.md) a [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="2d8e1-139">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d8e1-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d8e1-140">See also</span></span>
- [<span data-ttu-id="2d8e1-141">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="2d8e1-141">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="2d8e1-142">Statické a dynamické vazby</span><span class="sxs-lookup"><span data-stu-id="2d8e1-142">Early and Late Binding</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [<span data-ttu-id="2d8e1-143">Příkaz For Each...Next</span><span class="sxs-lookup"><span data-stu-id="2d8e1-143">For Each...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="2d8e1-144">Příkaz For...Next</span><span class="sxs-lookup"><span data-stu-id="2d8e1-144">For...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="2d8e1-145">Příkaz Option Infer</span><span class="sxs-lookup"><span data-stu-id="2d8e1-145">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="2d8e1-146">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="2d8e1-146">/optioninfer</span></span>](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="2d8e1-147">Úvod do LINQ v JAZYKU Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2d8e1-147">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
