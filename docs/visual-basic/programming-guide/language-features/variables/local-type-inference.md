---
title: "Odvození místního typu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "43"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d753d1fbdc60f70dcf0513d809f28a112243c111
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="local-type-inference-visual-basic"></a><span data-ttu-id="052dc-102">Odvození místního typu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="052dc-102">Local Type Inference (Visual Basic)</span></span>
<span data-ttu-id="052dc-103">Visual Basic – kompilátor používá *odvození typu* k určení datové typy lokální proměnné deklarované bez `As` klauzule.</span><span class="sxs-lookup"><span data-stu-id="052dc-103">The Visual Basic compiler uses *type inference* to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="052dc-104">Kompilátor odvodí typ proměnné z typu inicializace výrazu.</span><span class="sxs-lookup"><span data-stu-id="052dc-104">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="052dc-105">To umožňuje deklarujte proměnné bez explicitně typu, s informacemi o tom, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="052dc-105">This enables you to declare variables without explicitly stating a type, as shown in the following example.</span></span> <span data-ttu-id="052dc-106">V důsledku deklarace obě `num1` a `num2` jsou silného typu jako celá čísla.</span><span class="sxs-lookup"><span data-stu-id="052dc-106">As a result of the declarations, both `num1` and `num2` are strongly typed as integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_1.vb)]  
 
> [!NOTE]
>  <span data-ttu-id="052dc-107">Pokud nechcete, aby `num2` v předchozím příkladu zadat jako `Integer`, můžete zadat jiný typ pomocí deklaraci jako `Dim num3 As Object = 3` nebo `Dim num4 As Double = 3`.</span><span class="sxs-lookup"><span data-stu-id="052dc-107">If you do not want `num2` in the previous example to be typed as an `Integer`, you can specify another type by using a declaration like `Dim num3 As Object = 3` or `Dim num4 As Double = 3`.</span></span>  

> [!NOTE]
>  <span data-ttu-id="052dc-108">Odvození typu proměnné lze použít pouze pro místní proměnné nestatické; nedá se použít k určení typ pole třídy, vlastnosti a funkce.</span><span class="sxs-lookup"><span data-stu-id="052dc-108">Type inference can be used only for non-static local variables; it cannot be used to determine the type of class fields, properties, or functions.</span></span>
 
 <span data-ttu-id="052dc-109">Odvození místního typu se vztahuje na úrovni postupu.</span><span class="sxs-lookup"><span data-stu-id="052dc-109">Local type inference applies at procedure level.</span></span> <span data-ttu-id="052dc-110">Nelze se používá k deklaraci proměnné na úrovni modulu (v rámci třídy, struktury, modul nebo rozhraní ale není uvnitř procedury nebo bloku).</span><span class="sxs-lookup"><span data-stu-id="052dc-110">It cannot be used to declare variables at module level (within a class, structure, module, or interface but not within a procedure or block).</span></span> <span data-ttu-id="052dc-111">Pokud `num2` v předchozím příkladu byly pole třídy místo místní proměnné v postupu, deklaraci by způsobilo chybu s `Option Strict` a by klasifikaci `num2` jako `Object` s `Option Strict` vypnout.</span><span class="sxs-lookup"><span data-stu-id="052dc-111">If `num2` in the previous example were a field of a class instead of a local variable in a procedure, the declaration would cause an error with `Option Strict` on, and would classify `num2` as an `Object` with `Option Strict` off.</span></span> <span data-ttu-id="052dc-112">Podobně odvození místního typu nelze použít na postup úrovně proměnných deklarovaných jako `Static`.</span><span class="sxs-lookup"><span data-stu-id="052dc-112">Similarly, local type inference does not apply to procedure level variables declared as `Static`.</span></span>  
  
## <a name="type-inference-vs-late-binding"></a><span data-ttu-id="052dc-113">Zadejte odvození vs. Pozdní vazba</span><span class="sxs-lookup"><span data-stu-id="052dc-113">Type Inference vs. Late Binding</span></span>  
 <span data-ttu-id="052dc-114">Odvození používá typu kódu vypadá takto: kód, který využívá pozdní vazbu.</span><span class="sxs-lookup"><span data-stu-id="052dc-114">Code that uses type inference resembles code that relies on late binding.</span></span> <span data-ttu-id="052dc-115">Ale odvození typu důrazně typy proměnnou místo ponechání jako `Object`.</span><span class="sxs-lookup"><span data-stu-id="052dc-115">However, type inference strongly types the variable instead of leaving it as `Object`.</span></span> <span data-ttu-id="052dc-116">Kompilátor proměnná inicializátoru používá k určení typu proměnné v době kompilace k vytvoření časné vazby kódu.</span><span class="sxs-lookup"><span data-stu-id="052dc-116">The compiler uses a variable's initializer to determine the variable's type at compile time to produce early-bound code.</span></span> <span data-ttu-id="052dc-117">V předchozím příkladu `num2`, například `num1`, je zadán jako `Integer`.</span><span class="sxs-lookup"><span data-stu-id="052dc-117">In the previous example, `num2`, like `num1`, is typed as an `Integer`.</span></span>  
  
 <span data-ttu-id="052dc-118">Chování časné vazby proměnné se liší od pozdní vazbou proměnné, pro které je známý typ pouze za běhu.</span><span class="sxs-lookup"><span data-stu-id="052dc-118">The behavior of early-bound variables differs from that of late-bound variables, for which the type is known only at run time.</span></span> <span data-ttu-id="052dc-119">Zároveň budete vědět, že typ již v rané fázi umožňuje kompilátoru identifikaci problémů před spuštěním, přesněji přidělit paměť a provádět další optimalizace.</span><span class="sxs-lookup"><span data-stu-id="052dc-119">Knowing the type early enables the compiler to identify problems before execution, allocate memory precisely, and perform other optimizations.</span></span> <span data-ttu-id="052dc-120">Časná vazba taky umožňuje jazyka Visual Basic integrované vývojové prostředí (IDE) k poskytnutí nápovědy IntelliSense o členům v objektu.</span><span class="sxs-lookup"><span data-stu-id="052dc-120">Early binding also enables the Visual Basic integrated development environment (IDE) to provide IntelliSense Help about the members of an object.</span></span> <span data-ttu-id="052dc-121">Časná vazba je také upřednostňuje výkonu.</span><span class="sxs-lookup"><span data-stu-id="052dc-121">Early binding is also preferred for performance.</span></span> <span data-ttu-id="052dc-122">Důvodem je, že všechna data, které jsou uložené v proměnné pozdní vazbou musí být uzavřen jako typ `Object`, a přístup ke členům typu v době běhu programu pomalejší.</span><span class="sxs-lookup"><span data-stu-id="052dc-122">This is because all data stored in a late-bound variable must be wrapped as type `Object`, and accessing members of the type at run time makes the program slower.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="052dc-123">Příklady</span><span class="sxs-lookup"><span data-stu-id="052dc-123">Examples</span></span>  
 <span data-ttu-id="052dc-124">Odvození typu nastane, když místní proměnné je deklarovaná bez `As` klauzule a inicializovat.</span><span class="sxs-lookup"><span data-stu-id="052dc-124">Type inference occurs when a local variable is declared without an `As` clause and initialized.</span></span> <span data-ttu-id="052dc-125">Kompilátor používá typ přiřazené počáteční hodnoty jako typ proměnné.</span><span class="sxs-lookup"><span data-stu-id="052dc-125">The compiler uses the type of the assigned initial value as the type of the variable.</span></span> <span data-ttu-id="052dc-126">Například každý následující řádek kódu deklaruje proměnné typu `String`.</span><span class="sxs-lookup"><span data-stu-id="052dc-126">For example, each of the following lines of code declares a variable of type `String`.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#2](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_2.vb)]  
  
 <span data-ttu-id="052dc-127">Následující kód ukazuje dva způsoby ekvivalentní vytvoření pole celých čísel.</span><span class="sxs-lookup"><span data-stu-id="052dc-127">The following code demonstrates two equivalent ways to create an array of integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#3](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_3.vb)]  
  
 <span data-ttu-id="052dc-128">Je vhodnější použít odvození typu určit typ řídicí proměnná smyčky.</span><span class="sxs-lookup"><span data-stu-id="052dc-128">It is convenient to use type inference to determine the type of a loop control variable.</span></span> <span data-ttu-id="052dc-129">V následujícím kódu, který odvodí kompilátor `number` je `Integer` protože `someNumbers2` z předchozího příkladu je pole celých čísel.</span><span class="sxs-lookup"><span data-stu-id="052dc-129">In the following code, the compiler infers that `number` is an `Integer` because `someNumbers2` from the previous example is an array of integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#4](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_4.vb)]  
  
 <span data-ttu-id="052dc-130">Odvození místního typu mohou být používány `Using` příkazy k vytvoření je typ názvu prostředku, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="052dc-130">Local type inference can be used in `Using` statements to establish the type of the resource name, as the following example demonstrates.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_5.vb)]  
  
 <span data-ttu-id="052dc-131">Typ proměnné lze také odvodit z návratové hodnoty funkce, jako následující příklad ukazuje.</span><span class="sxs-lookup"><span data-stu-id="052dc-131">The type of a variable can also be inferred from the return values of functions, as the following example demonstrates.</span></span> <span data-ttu-id="052dc-132">Obě `pList1` a `pList2` jsou pole procesů, protože `Process.GetProcesses` vrátí pole procesů.</span><span class="sxs-lookup"><span data-stu-id="052dc-132">Both `pList1` and `pList2` are arrays of processes because `Process.GetProcesses` returns an array of processes.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#5](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_6.vb)]  
  
## <a name="option-infer"></a><span data-ttu-id="052dc-133">Option Infer –</span><span class="sxs-lookup"><span data-stu-id="052dc-133">Option Infer</span></span>  
 <span data-ttu-id="052dc-134">`Option Infer`povoluje, který zadáte, jestli je povolené odvození místního typu v konkrétním souboru.</span><span class="sxs-lookup"><span data-stu-id="052dc-134">`Option Infer` enables you specify whether local type inference is allowed in a particular file.</span></span> <span data-ttu-id="052dc-135">Chcete-li povolit nebo blokovat možnost, zadejte jednu z následujících příkazů na začátku souboru.</span><span class="sxs-lookup"><span data-stu-id="052dc-135">To enable or to block the option, type one of the following statements at the start of the file.</span></span>  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 <span data-ttu-id="052dc-136">Pokud nezadáte hodnotu `Option Infer` ve vašem kódu kompilátoru výchozí hodnota je `Option Infer On`.</span><span class="sxs-lookup"><span data-stu-id="052dc-136">If you do not specify a value for `Option Infer` in your code, the compiler default is `Option Infer On`.</span></span> <span data-ttu-id="052dc-137">Pro projekty upgradovali z [!INCLUDE[vb_orcas_long](~/includes/vb-orcas-long-md.md)] nebo starší, je výchozí nastavení kompilátoru `Option Infer Off`.</span><span class="sxs-lookup"><span data-stu-id="052dc-137">For projects upgraded from [!INCLUDE[vb_orcas_long](~/includes/vb-orcas-long-md.md)] or earlier, the compiler default is `Option Infer Off`.</span></span>  
  
 <span data-ttu-id="052dc-138">Pokud je hodnota nastavená pro `Option Infer` souboru konflikty s hodnotu nastavenou v prostředí IDE nebo na příkazovém řádku, v souboru hodnota má vyšší prioritu.</span><span class="sxs-lookup"><span data-stu-id="052dc-138">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="052dc-139">Další informace najdete v tématu [Option Infer – příkaz](../../../../visual-basic/language-reference/statements/option-infer-statement.md) a [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="052dc-139">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="052dc-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="052dc-140">See Also</span></span>  
 [<span data-ttu-id="052dc-141">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="052dc-141">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="052dc-142">Statické a pozdní vazby</span><span class="sxs-lookup"><span data-stu-id="052dc-142">Early and Late Binding</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 [<span data-ttu-id="052dc-143">Pro každou... Next – příkaz</span><span class="sxs-lookup"><span data-stu-id="052dc-143">For Each...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="052dc-144">Pro... Next – příkaz</span><span class="sxs-lookup"><span data-stu-id="052dc-144">For...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="052dc-145">Option Infer – příkaz</span><span class="sxs-lookup"><span data-stu-id="052dc-145">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [<span data-ttu-id="052dc-146">/ optioninfer</span><span class="sxs-lookup"><span data-stu-id="052dc-146">/optioninfer</span></span>](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="052dc-147">Úvod do LINQ v jazyku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="052dc-147">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
