---
title: Option Infer – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.OptionInfer
- vb.Infer
helpviewer_keywords:
- variables [Visual Basic], declaring
- Option Infer statement [Visual Basic]
- Infer keyword [Visual Basic]
- declaring variables [Visual Basic], inferred
- inferred variable declaration
ms.assetid: 4ad3e6e9-8f5b-4209-a248-de22ef6e4652
ms.openlocfilehash: c7628e5c4c0cda527a4c3b1a211c45760640fc63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605508"
---
# <a name="option-infer-statement"></a><span data-ttu-id="5488a-102">Option Infer – příkaz</span><span class="sxs-lookup"><span data-stu-id="5488a-102">Option Infer Statement</span></span>
<span data-ttu-id="5488a-103">Umožňuje použití odvození místního typu v deklarování proměnných.</span><span class="sxs-lookup"><span data-stu-id="5488a-103">Enables the use of local type inference in declaring variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5488a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5488a-104">Syntax</span></span>  
  
```  
Option Infer { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="5488a-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="5488a-105">Parts</span></span>  
  
|<span data-ttu-id="5488a-106">Termín</span><span class="sxs-lookup"><span data-stu-id="5488a-106">Term</span></span>|<span data-ttu-id="5488a-107">Definice</span><span class="sxs-lookup"><span data-stu-id="5488a-107">Definition</span></span>|  
|---|---|  
|`On`|<span data-ttu-id="5488a-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="5488a-108">Optional.</span></span> <span data-ttu-id="5488a-109">Umožňuje odvození místního typu.</span><span class="sxs-lookup"><span data-stu-id="5488a-109">Enables local type inference.</span></span>|  
|`Off`|<span data-ttu-id="5488a-110">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="5488a-110">Optional.</span></span> <span data-ttu-id="5488a-111">Zakáže odvození místního typu.</span><span class="sxs-lookup"><span data-stu-id="5488a-111">Disables local type inference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5488a-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5488a-112">Remarks</span></span>  
 <span data-ttu-id="5488a-113">Chcete-li nastavit `Option Infer` v souboru, zadejte `Option Infer On` nebo `Option Infer Off` v horní části souboru, před spuštěním zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="5488a-113">To set `Option Infer` in a file, type `Option Infer On` or `Option Infer Off` at the top of the file, before any other source code.</span></span> <span data-ttu-id="5488a-114">Pokud je hodnota nastavená pro `Option Infer` souboru konflikty s hodnotu nastavenou v prostředí IDE nebo na příkazovém řádku, v souboru hodnota má vyšší prioritu.</span><span class="sxs-lookup"><span data-stu-id="5488a-114">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="5488a-115">Když nastavíte `Option Infer` k `On`, místní proměnné můžou deklarovat bez explicitně s informacemi o tom datový typ.</span><span class="sxs-lookup"><span data-stu-id="5488a-115">When you set `Option Infer` to `On`, you can declare local variables without explicitly stating a data type.</span></span> <span data-ttu-id="5488a-116">Kompilátor odvodí datový typ proměnné z typu jejího výrazu inicializace.</span><span class="sxs-lookup"><span data-stu-id="5488a-116">The compiler infers the data type of a variable from the type of its initialization expression.</span></span>  
  
 <span data-ttu-id="5488a-117">Na následujícím obrázku `Option Infer` je zapnutý.</span><span class="sxs-lookup"><span data-stu-id="5488a-117">In the following illustration, `Option Infer` is turned on.</span></span> <span data-ttu-id="5488a-118">Proměnné v deklaraci `Dim someVar = 2` je deklarovaná odvození typu jako celé číslo.</span><span class="sxs-lookup"><span data-stu-id="5488a-118">The variable in the declaration `Dim someVar = 2` is declared as an integer by type inference.</span></span>  
  
 <span data-ttu-id="5488a-119">![Zobrazení technologie IntelliSense deklarace. ] (../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")</span><span class="sxs-lookup"><span data-stu-id="5488a-119">![IntelliSense view of the declaration.](../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")</span></span>  
<span data-ttu-id="5488a-120">Option Infer – je na IntelliSense</span><span class="sxs-lookup"><span data-stu-id="5488a-120">IntelliSense when Option Infer is on</span></span>  
  
 <span data-ttu-id="5488a-121">Na následujícím obrázku `Option Infer` je vypnutý.</span><span class="sxs-lookup"><span data-stu-id="5488a-121">In the following illustration, `Option Infer` is turned off.</span></span> <span data-ttu-id="5488a-122">Proměnné v deklaraci `Dim someVar = 2` je deklarován jako `Object` podle odvození typu.</span><span class="sxs-lookup"><span data-stu-id="5488a-122">The variable in the declaration `Dim someVar = 2` is declared as an `Object` by type inference.</span></span> <span data-ttu-id="5488a-123">V tomto příkladu **možnost striktní** nastavení je **vypnout** na [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="5488a-123">In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="5488a-124">![Zobrazení technologie IntelliSense deklarace. ] (../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")</span><span class="sxs-lookup"><span data-stu-id="5488a-124">![IntelliSense view of the declaration.](../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")</span></span>  
<span data-ttu-id="5488a-125">IntelliSense při Option Infer – vypnuté</span><span class="sxs-lookup"><span data-stu-id="5488a-125">IntelliSense when Option Infer is off</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5488a-126">Když je proměnná deklarován jako `Object`, při spuštění programu, můžete změnit typ spuštění.</span><span class="sxs-lookup"><span data-stu-id="5488a-126">When a variable is declared as an `Object`, the run-time type can change while the program is running.</span></span> <span data-ttu-id="5488a-127">Visual Basic provádí operace názvem *zabalení* a *rozbalení* pro převod mezi `Object` a typ hodnoty, které umožňuje provádění pomalejší.</span><span class="sxs-lookup"><span data-stu-id="5488a-127">Visual Basic performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower.</span></span> <span data-ttu-id="5488a-128">Informace o zabalení a rozbalení najdete v tématu [specifikace jazyka Visual Basic](../../../visual-basic/reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="5488a-128">For information about boxing and unboxing, see the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification/index.md).</span></span>
  
 <span data-ttu-id="5488a-129">Odvození typu se vztahuje na úrovni procedury a doporučení se netýká mimo proceduru v třída, struktura, modulu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5488a-129">Type inference applies at the procedure level, and does not apply outside a procedure in a class, structure, module, or interface.</span></span>  
  
 <span data-ttu-id="5488a-130">Další informace najdete v tématu [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="5488a-130">For additional information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
## <a name="when-an-option-infer-statement-is-not-present"></a><span data-ttu-id="5488a-131">Když Option Infer – příkaz není k dispozici</span><span class="sxs-lookup"><span data-stu-id="5488a-131">When an Option Infer Statement Is Not Present</span></span>  
 <span data-ttu-id="5488a-132">Pokud zdrojový kód neobsahuje `Option Infer` příkaz, **Option Infer –** nastavení na [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) se používá.</span><span class="sxs-lookup"><span data-stu-id="5488a-132">If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="5488a-133">Pokud se používá kompilátoru příkazového řádku, [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) – možnost kompilátoru se používá.</span><span class="sxs-lookup"><span data-stu-id="5488a-133">If the command-line compiler is used, the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-infer-in-the-ide"></a><span data-ttu-id="5488a-134">Chcete-li nastavit Option Infer – v prostředí IDE</span><span class="sxs-lookup"><span data-stu-id="5488a-134">To set Option Infer in the IDE</span></span>  
  
1.  <span data-ttu-id="5488a-135">V **Průzkumníku**, vyberte projektu.</span><span class="sxs-lookup"><span data-stu-id="5488a-135">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="5488a-136">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="5488a-136">On the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="5488a-137">Klikněte **zkompilovat** kartě.</span><span class="sxs-lookup"><span data-stu-id="5488a-137">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="5488a-138">Nastavte hodnotu v **Option infer –** pole.</span><span class="sxs-lookup"><span data-stu-id="5488a-138">Set the value in the **Option infer** box.</span></span>  
  
 <span data-ttu-id="5488a-139">Při vytvoření nového projektu, **Option Infer –** nastavení na **zkompilovat** karta je nastaven na **Option Infer –** nastavení v **VB výchozí** Dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="5488a-139">When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="5488a-140">Pro přístup k **VB výchozí** v dialogovém **nástroje** nabídky, klikněte na tlačítko **možnosti**.</span><span class="sxs-lookup"><span data-stu-id="5488a-140">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="5488a-141">V **možnosti** dialogové okno, rozbalte seznam **projekty a řešení**a potom klikněte na **VB výchozí**.</span><span class="sxs-lookup"><span data-stu-id="5488a-141">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="5488a-142">Počáteční výchozí nastavení v **VB výchozí** je `On`.</span><span class="sxs-lookup"><span data-stu-id="5488a-142">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-infer-on-the-command-line"></a><span data-ttu-id="5488a-143">Chcete-li nastavit Option Infer – na příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="5488a-143">To set Option Infer on the command line</span></span>  
  
-   <span data-ttu-id="5488a-144">Zahrnout [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) – možnost kompilátoru v **Vbc –** příkaz.</span><span class="sxs-lookup"><span data-stu-id="5488a-144">Include the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="default-data-types-and-values"></a><span data-ttu-id="5488a-145">Typy a hodnoty výchozí Data</span><span class="sxs-lookup"><span data-stu-id="5488a-145">Default Data Types and Values</span></span>  
 <span data-ttu-id="5488a-146">Následující tabulka popisuje výsledky datový typ a inicializátoru v různých kombinacích `Dim` příkaz.</span><span class="sxs-lookup"><span data-stu-id="5488a-146">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="5488a-147">Datový typ zadaný?</span><span class="sxs-lookup"><span data-stu-id="5488a-147">Data type specified?</span></span>|<span data-ttu-id="5488a-148">Zadaný inicializační?</span><span class="sxs-lookup"><span data-stu-id="5488a-148">Initializer specified?</span></span>|<span data-ttu-id="5488a-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="5488a-149">Example</span></span>|<span data-ttu-id="5488a-150">Výsledek</span><span class="sxs-lookup"><span data-stu-id="5488a-150">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="5488a-151">Ne</span><span class="sxs-lookup"><span data-stu-id="5488a-151">No</span></span>|<span data-ttu-id="5488a-152">Ne</span><span class="sxs-lookup"><span data-stu-id="5488a-152">No</span></span>|`Dim qty`|<span data-ttu-id="5488a-153">Pokud `Option Strict` je vypnuto (výchozí), proměnná je nastavená na `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="5488a-153">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="5488a-154">Pokud `Option Strict` zapnutý, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="5488a-154">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="5488a-155">Ne</span><span class="sxs-lookup"><span data-stu-id="5488a-155">No</span></span>|<span data-ttu-id="5488a-156">Ano</span><span class="sxs-lookup"><span data-stu-id="5488a-156">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="5488a-157">Pokud `Option Infer` je na (výchozí), typ inicializátoru proměnné přijímá data.</span><span class="sxs-lookup"><span data-stu-id="5488a-157">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="5488a-158">V tématu [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="5488a-158">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="5488a-159">Pokud `Option Infer` vypnuté a `Option Strict` je vypnutý, nabývá datový typ `Object`.</span><span class="sxs-lookup"><span data-stu-id="5488a-159">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="5488a-160">Pokud `Option Infer` vypnuté a `Option Strict` zapnutý, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="5488a-160">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="5488a-161">Ano</span><span class="sxs-lookup"><span data-stu-id="5488a-161">Yes</span></span>|<span data-ttu-id="5488a-162">Ne</span><span class="sxs-lookup"><span data-stu-id="5488a-162">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="5488a-163">Výchozí hodnota pro typ dat je inicializováno proměnnou.</span><span class="sxs-lookup"><span data-stu-id="5488a-163">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="5488a-164">Další informace najdete v tématu [Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5488a-164">For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>|  
|<span data-ttu-id="5488a-165">Ano</span><span class="sxs-lookup"><span data-stu-id="5488a-165">Yes</span></span>|<span data-ttu-id="5488a-166">Ano</span><span class="sxs-lookup"><span data-stu-id="5488a-166">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="5488a-167">Pokud datový typ inicializátoru není převést na zadaný datový typ, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="5488a-167">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5488a-168">Příklad</span><span class="sxs-lookup"><span data-stu-id="5488a-168">Example</span></span>  
 <span data-ttu-id="5488a-169">Následující příklady ukazují, jak `Option Infer` příkaz umožňuje odvození místního typu.</span><span class="sxs-lookup"><span data-stu-id="5488a-169">The following examples demonstrate how the `Option Infer` statement enables local type inference.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="5488a-170">Příklad</span><span class="sxs-lookup"><span data-stu-id="5488a-170">Example</span></span>  
 <span data-ttu-id="5488a-171">Následující příklad ukazuje, že běhového typu se může lišit při proměnné je označený `Object`.</span><span class="sxs-lookup"><span data-stu-id="5488a-171">The following example demonstrates that the run-time type can differ when a variable is identified as an `Object`.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#11](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5488a-172">Viz také</span><span class="sxs-lookup"><span data-stu-id="5488a-172">See Also</span></span>  
 [<span data-ttu-id="5488a-173">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="5488a-173">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="5488a-174">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="5488a-174">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="5488a-175">Příkaz Option Compare</span><span class="sxs-lookup"><span data-stu-id="5488a-175">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="5488a-176">Příkaz Option Explicit</span><span class="sxs-lookup"><span data-stu-id="5488a-176">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="5488a-177">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="5488a-177">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="5488a-178">Dialogové okno Možnosti výchozí hodnoty, projekty, Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5488a-178">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)  
 [<span data-ttu-id="5488a-179">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="5488a-179">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="5488a-180">Zabalení a rozbalení</span><span class="sxs-lookup"><span data-stu-id="5488a-180">Boxing and Unboxing</span></span>](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
