---
title: "Option Infer – příkaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "72"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4634c198b5fc41a4834cbd3cd96f9d3f1863d09b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="option-infer-statement"></a><span data-ttu-id="43dcc-102">Option Infer – příkaz</span><span class="sxs-lookup"><span data-stu-id="43dcc-102">Option Infer Statement</span></span>
<span data-ttu-id="43dcc-103">Umožňuje použití odvození místního typu v deklarování proměnných.</span><span class="sxs-lookup"><span data-stu-id="43dcc-103">Enables the use of local type inference in declaring variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43dcc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43dcc-104">Syntax</span></span>  
  
```  
Option Infer { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="43dcc-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="43dcc-105">Parts</span></span>  
  
|<span data-ttu-id="43dcc-106">Termín</span><span class="sxs-lookup"><span data-stu-id="43dcc-106">Term</span></span>|<span data-ttu-id="43dcc-107">Definice</span><span class="sxs-lookup"><span data-stu-id="43dcc-107">Definition</span></span>|  
|---|---|  
|`On`|<span data-ttu-id="43dcc-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="43dcc-108">Optional.</span></span> <span data-ttu-id="43dcc-109">Umožňuje odvození místního typu.</span><span class="sxs-lookup"><span data-stu-id="43dcc-109">Enables local type inference.</span></span>|  
|`Off`|<span data-ttu-id="43dcc-110">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="43dcc-110">Optional.</span></span> <span data-ttu-id="43dcc-111">Zakáže odvození místního typu.</span><span class="sxs-lookup"><span data-stu-id="43dcc-111">Disables local type inference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43dcc-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="43dcc-112">Remarks</span></span>  
 <span data-ttu-id="43dcc-113">Chcete-li nastavit `Option Infer` v souboru, zadejte `Option Infer On` nebo `Option Infer Off` v horní části souboru, před spuštěním zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="43dcc-113">To set `Option Infer` in a file, type `Option Infer On` or `Option Infer Off` at the top of the file, before any other source code.</span></span> <span data-ttu-id="43dcc-114">Pokud je hodnota nastavená pro `Option Infer` souboru konflikty s hodnotu nastavenou v prostředí IDE nebo na příkazovém řádku, v souboru hodnota má vyšší prioritu.</span><span class="sxs-lookup"><span data-stu-id="43dcc-114">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="43dcc-115">Když nastavíte `Option Infer` k `On`, místní proměnné můžou deklarovat bez explicitně s informacemi o tom datový typ.</span><span class="sxs-lookup"><span data-stu-id="43dcc-115">When you set `Option Infer` to `On`, you can declare local variables without explicitly stating a data type.</span></span> <span data-ttu-id="43dcc-116">Kompilátor odvodí datový typ proměnné z typu jejího výrazu inicializace.</span><span class="sxs-lookup"><span data-stu-id="43dcc-116">The compiler infers the data type of a variable from the type of its initialization expression.</span></span>  
  
 <span data-ttu-id="43dcc-117">Na následujícím obrázku `Option Infer` je zapnutý.</span><span class="sxs-lookup"><span data-stu-id="43dcc-117">In the following illustration, `Option Infer` is turned on.</span></span> <span data-ttu-id="43dcc-118">Proměnné v deklaraci `Dim someVar = 2` je deklarovaná odvození typu jako celé číslo.</span><span class="sxs-lookup"><span data-stu-id="43dcc-118">The variable in the declaration `Dim someVar = 2` is declared as an integer by type inference.</span></span>  
  
 <span data-ttu-id="43dcc-119">![Zobrazení technologie IntelliSense deklarace. ] (../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")</span><span class="sxs-lookup"><span data-stu-id="43dcc-119">![IntelliSense view of the declaration.](../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")</span></span>  
<span data-ttu-id="43dcc-120">Option Infer – je na IntelliSense</span><span class="sxs-lookup"><span data-stu-id="43dcc-120">IntelliSense when Option Infer is on</span></span>  
  
 <span data-ttu-id="43dcc-121">Na následujícím obrázku `Option Infer` je vypnutý.</span><span class="sxs-lookup"><span data-stu-id="43dcc-121">In the following illustration, `Option Infer` is turned off.</span></span> <span data-ttu-id="43dcc-122">Proměnné v deklaraci `Dim someVar = 2` je deklarován jako `Object` podle odvození typu.</span><span class="sxs-lookup"><span data-stu-id="43dcc-122">The variable in the declaration `Dim someVar = 2` is declared as an `Object` by type inference.</span></span> <span data-ttu-id="43dcc-123">V tomto příkladu **možnost striktní** nastavení je **vypnout** na [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="43dcc-123">In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="43dcc-124">![Zobrazení technologie IntelliSense deklarace. ] (../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")</span><span class="sxs-lookup"><span data-stu-id="43dcc-124">![IntelliSense view of the declaration.](../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")</span></span>  
<span data-ttu-id="43dcc-125">IntelliSense při Option Infer – vypnuté</span><span class="sxs-lookup"><span data-stu-id="43dcc-125">IntelliSense when Option Infer is off</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="43dcc-126">Když je proměnná deklarován jako `Object`, při spuštění programu, můžete změnit typ spuštění.</span><span class="sxs-lookup"><span data-stu-id="43dcc-126">When a variable is declared as an `Object`, the run-time type can change while the program is running.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="43dcc-127">provede operace s názvem *zabalení* a *rozbalení* pro převod mezi `Object` a typ hodnoty, které umožňuje provádění pomalejší.</span><span class="sxs-lookup"><span data-stu-id="43dcc-127"> performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower.</span></span> <span data-ttu-id="43dcc-128">Informace o zabalení a rozbalení najdete v tématu [specifikace jazyka Visual Basic](../../../visual-basic/reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="43dcc-128">For information about boxing and unboxing, see the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification/index.md).</span></span>
  
 <span data-ttu-id="43dcc-129">Odvození typu se vztahuje na úrovni procedury a doporučení se netýká mimo proceduru v třída, struktura, modulu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="43dcc-129">Type inference applies at the procedure level, and does not apply outside a procedure in a class, structure, module, or interface.</span></span>  
  
 <span data-ttu-id="43dcc-130">Další informace najdete v tématu [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="43dcc-130">For additional information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
## <a name="when-an-option-infer-statement-is-not-present"></a><span data-ttu-id="43dcc-131">Když Option Infer – příkaz není k dispozici</span><span class="sxs-lookup"><span data-stu-id="43dcc-131">When an Option Infer Statement Is Not Present</span></span>  
 <span data-ttu-id="43dcc-132">Pokud zdrojový kód neobsahuje `Option Infer` příkaz, **Option Infer –** nastavení na [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) se používá.</span><span class="sxs-lookup"><span data-stu-id="43dcc-132">If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="43dcc-133">Pokud se používá kompilátoru příkazového řádku, [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) – možnost kompilátoru se používá.</span><span class="sxs-lookup"><span data-stu-id="43dcc-133">If the command-line compiler is used, the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-infer-in-the-ide"></a><span data-ttu-id="43dcc-134">Chcete-li nastavit Option Infer – v prostředí IDE</span><span class="sxs-lookup"><span data-stu-id="43dcc-134">To set Option Infer in the IDE</span></span>  
  
1.  <span data-ttu-id="43dcc-135">V **Průzkumníku**, vyberte projektu.</span><span class="sxs-lookup"><span data-stu-id="43dcc-135">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="43dcc-136">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="43dcc-136">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="43dcc-137">Další informace najdete v tématu [NIB: Správa vlastností projektu s Návrhář projektu](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span><span class="sxs-lookup"><span data-stu-id="43dcc-137">For more information, see [NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span></span>  
  
2.  <span data-ttu-id="43dcc-138">Klikněte **zkompilovat** kartě.</span><span class="sxs-lookup"><span data-stu-id="43dcc-138">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="43dcc-139">Nastavte hodnotu v **Option infer –** pole.</span><span class="sxs-lookup"><span data-stu-id="43dcc-139">Set the value in the **Option infer** box.</span></span>  
  
 <span data-ttu-id="43dcc-140">Při vytvoření nového projektu, **Option Infer –** nastavení na **zkompilovat** karta je nastaven na **Option Infer –** nastavení v **VB výchozí** Dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="43dcc-140">When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="43dcc-141">Pro přístup k **VB výchozí** v dialogovém **nástroje** nabídky, klikněte na tlačítko **možnosti**.</span><span class="sxs-lookup"><span data-stu-id="43dcc-141">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="43dcc-142">V **možnosti** dialogové okno, rozbalte seznam **projekty a řešení**a potom klikněte na **VB výchozí**.</span><span class="sxs-lookup"><span data-stu-id="43dcc-142">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="43dcc-143">Počáteční výchozí nastavení v **VB výchozí** je `On`.</span><span class="sxs-lookup"><span data-stu-id="43dcc-143">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-infer-on-the-command-line"></a><span data-ttu-id="43dcc-144">Chcete-li nastavit Option Infer – na příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="43dcc-144">To set Option Infer on the command line</span></span>  
  
-   <span data-ttu-id="43dcc-145">Zahrnout [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) – možnost kompilátoru v **Vbc –** příkaz.</span><span class="sxs-lookup"><span data-stu-id="43dcc-145">Include the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="default-data-types-and-values"></a><span data-ttu-id="43dcc-146">Typy a hodnoty výchozí Data</span><span class="sxs-lookup"><span data-stu-id="43dcc-146">Default Data Types and Values</span></span>  
 <span data-ttu-id="43dcc-147">Následující tabulka popisuje výsledky datový typ a inicializátoru v různých kombinacích `Dim` příkaz.</span><span class="sxs-lookup"><span data-stu-id="43dcc-147">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="43dcc-148">Datový typ zadaný?</span><span class="sxs-lookup"><span data-stu-id="43dcc-148">Data type specified?</span></span>|<span data-ttu-id="43dcc-149">Zadaný inicializační?</span><span class="sxs-lookup"><span data-stu-id="43dcc-149">Initializer specified?</span></span>|<span data-ttu-id="43dcc-150">Příklad</span><span class="sxs-lookup"><span data-stu-id="43dcc-150">Example</span></span>|<span data-ttu-id="43dcc-151">Výsledek</span><span class="sxs-lookup"><span data-stu-id="43dcc-151">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="43dcc-152">Ne</span><span class="sxs-lookup"><span data-stu-id="43dcc-152">No</span></span>|<span data-ttu-id="43dcc-153">Ne</span><span class="sxs-lookup"><span data-stu-id="43dcc-153">No</span></span>|`Dim qty`|<span data-ttu-id="43dcc-154">Pokud `Option Strict` je vypnuto (výchozí), proměnná je nastavená na `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="43dcc-154">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="43dcc-155">Pokud `Option Strict` zapnutý, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="43dcc-155">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="43dcc-156">Ne</span><span class="sxs-lookup"><span data-stu-id="43dcc-156">No</span></span>|<span data-ttu-id="43dcc-157">Ano</span><span class="sxs-lookup"><span data-stu-id="43dcc-157">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="43dcc-158">Pokud `Option Infer` je na (výchozí), typ inicializátoru proměnné přijímá data.</span><span class="sxs-lookup"><span data-stu-id="43dcc-158">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="43dcc-159">V tématu [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="43dcc-159">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="43dcc-160">Pokud `Option Infer` vypnuté a `Option Strict` je vypnutý, nabývá datový typ `Object`.</span><span class="sxs-lookup"><span data-stu-id="43dcc-160">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="43dcc-161">Pokud `Option Infer` vypnuté a `Option Strict` zapnutý, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="43dcc-161">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="43dcc-162">Ano</span><span class="sxs-lookup"><span data-stu-id="43dcc-162">Yes</span></span>|<span data-ttu-id="43dcc-163">Ne</span><span class="sxs-lookup"><span data-stu-id="43dcc-163">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="43dcc-164">Výchozí hodnota pro typ dat je inicializováno proměnnou.</span><span class="sxs-lookup"><span data-stu-id="43dcc-164">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="43dcc-165">Další informace najdete v tématu [Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="43dcc-165">For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>|  
|<span data-ttu-id="43dcc-166">Ano</span><span class="sxs-lookup"><span data-stu-id="43dcc-166">Yes</span></span>|<span data-ttu-id="43dcc-167">Ano</span><span class="sxs-lookup"><span data-stu-id="43dcc-167">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="43dcc-168">Pokud datový typ inicializátoru není převést na zadaný datový typ, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="43dcc-168">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="43dcc-169">Příklad</span><span class="sxs-lookup"><span data-stu-id="43dcc-169">Example</span></span>  
 <span data-ttu-id="43dcc-170">Následující příklady ukazují, jak `Option Infer` příkaz umožňuje odvození místního typu.</span><span class="sxs-lookup"><span data-stu-id="43dcc-170">The following examples demonstrate how the `Option Infer` statement enables local type inference.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="43dcc-171">Příklad</span><span class="sxs-lookup"><span data-stu-id="43dcc-171">Example</span></span>  
 <span data-ttu-id="43dcc-172">Následující příklad ukazuje, že běhového typu se může lišit při proměnné je označený `Object`.</span><span class="sxs-lookup"><span data-stu-id="43dcc-172">The following example demonstrates that the run-time type can differ when a variable is identified as an `Object`.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#11](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="43dcc-173">Viz také</span><span class="sxs-lookup"><span data-stu-id="43dcc-173">See Also</span></span>  
 [<span data-ttu-id="43dcc-174">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="43dcc-174">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="43dcc-175">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="43dcc-175">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="43dcc-176">Option Compare – příkaz</span><span class="sxs-lookup"><span data-stu-id="43dcc-176">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="43dcc-177">Option Explicit – příkaz</span><span class="sxs-lookup"><span data-stu-id="43dcc-177">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="43dcc-178">Option Strict – příkaz</span><span class="sxs-lookup"><span data-stu-id="43dcc-178">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="43dcc-179">Dialogové okno Možnosti výchozí hodnoty, projekty, Visual Basic</span><span class="sxs-lookup"><span data-stu-id="43dcc-179">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)  
 [<span data-ttu-id="43dcc-180">/ optioninfer</span><span class="sxs-lookup"><span data-stu-id="43dcc-180">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="43dcc-181">Zabalení a rozbalení</span><span class="sxs-lookup"><span data-stu-id="43dcc-181">Boxing and Unboxing</span></span>](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
