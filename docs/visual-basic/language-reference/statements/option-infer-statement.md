---
title: Option Infer – příkaz (Visual Basic)
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
ms.openlocfilehash: f5c824df43997282d50c9c2a458fb1d854cc160a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43672582"
---
# <a name="option-infer-statement"></a><span data-ttu-id="ad757-102">Option Infer – příkaz</span><span class="sxs-lookup"><span data-stu-id="ad757-102">Option Infer Statement</span></span>
<span data-ttu-id="ad757-103">Umožňuje použití odvození místního typu v deklarujících proměnných.</span><span class="sxs-lookup"><span data-stu-id="ad757-103">Enables the use of local type inference in declaring variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad757-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad757-104">Syntax</span></span>  
  
```  
Option Infer { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="ad757-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="ad757-105">Parts</span></span>  
  
|<span data-ttu-id="ad757-106">Termín</span><span class="sxs-lookup"><span data-stu-id="ad757-106">Term</span></span>|<span data-ttu-id="ad757-107">Definice</span><span class="sxs-lookup"><span data-stu-id="ad757-107">Definition</span></span>|  
|---|---|  
|`On`|<span data-ttu-id="ad757-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="ad757-108">Optional.</span></span> <span data-ttu-id="ad757-109">Umožňuje odvození místního typu.</span><span class="sxs-lookup"><span data-stu-id="ad757-109">Enables local type inference.</span></span>|  
|`Off`|<span data-ttu-id="ad757-110">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="ad757-110">Optional.</span></span> <span data-ttu-id="ad757-111">Zakáže odvození místního typu.</span><span class="sxs-lookup"><span data-stu-id="ad757-111">Disables local type inference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad757-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ad757-112">Remarks</span></span>  
 <span data-ttu-id="ad757-113">Chcete-li nastavit `Option Infer` v souboru, zadejte `Option Infer On` nebo `Option Infer Off` v horní části souboru, než jakýkoli jiný zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="ad757-113">To set `Option Infer` in a file, type `Option Infer On` or `Option Infer Off` at the top of the file, before any other source code.</span></span> <span data-ttu-id="ad757-114">Je-li nastavena hodnota pro `Option Infer` v souboru konflikty s hodnotou nastavenou v integrovaném vývojovém prostředí nebo na příkazovém řádku, hodnota v souboru má prioritu.</span><span class="sxs-lookup"><span data-stu-id="ad757-114">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="ad757-115">Pokud nastavíte `Option Infer` k `On`, bez explicitní uvedení datový typ je možné deklarovat lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="ad757-115">When you set `Option Infer` to `On`, you can declare local variables without explicitly stating a data type.</span></span> <span data-ttu-id="ad757-116">Kompilátor odvodí datový typ proměnné z typu výrazu jeho inicializaci.</span><span class="sxs-lookup"><span data-stu-id="ad757-116">The compiler infers the data type of a variable from the type of its initialization expression.</span></span>  
  
 <span data-ttu-id="ad757-117">Na následujícím obrázku `Option Infer` zapnutý.</span><span class="sxs-lookup"><span data-stu-id="ad757-117">In the following illustration, `Option Infer` is turned on.</span></span> <span data-ttu-id="ad757-118">Proměnné v deklaraci `Dim someVar = 2` je deklarován jako celé číslo odvození typu proměnné.</span><span class="sxs-lookup"><span data-stu-id="ad757-118">The variable in the declaration `Dim someVar = 2` is declared as an integer by type inference.</span></span>  
  
 <span data-ttu-id="ad757-119">![Zobrazení technologie IntelliSense deklarace. ](../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")</span><span class="sxs-lookup"><span data-stu-id="ad757-119">![IntelliSense view of the declaration.](../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")</span></span>  
<span data-ttu-id="ad757-120">Technologie IntelliSense při Option Infer zapnutý</span><span class="sxs-lookup"><span data-stu-id="ad757-120">IntelliSense when Option Infer is on</span></span>  
  
 <span data-ttu-id="ad757-121">Na následujícím obrázku `Option Infer` je vypnutý.</span><span class="sxs-lookup"><span data-stu-id="ad757-121">In the following illustration, `Option Infer` is turned off.</span></span> <span data-ttu-id="ad757-122">Proměnné v deklaraci `Dim someVar = 2` je deklarován jako `Object` podle odvození typu proměnné.</span><span class="sxs-lookup"><span data-stu-id="ad757-122">The variable in the declaration `Dim someVar = 2` is declared as an `Object` by type inference.</span></span> <span data-ttu-id="ad757-123">V tomto příkladu **Option Strict** nastavená na **vypnout** na [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="ad757-123">In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="ad757-124">![Zobrazení technologie IntelliSense deklarace. ](../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")</span><span class="sxs-lookup"><span data-stu-id="ad757-124">![IntelliSense view of the declaration.](../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")</span></span>  
<span data-ttu-id="ad757-125">Technologie IntelliSense při Option Infer je vypnuté</span><span class="sxs-lookup"><span data-stu-id="ad757-125">IntelliSense when Option Infer is off</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ad757-126">Pokud je proměnná deklarována jako `Object`, run-time typu můžete změnit, zatímco program běží.</span><span class="sxs-lookup"><span data-stu-id="ad757-126">When a variable is declared as an `Object`, the run-time type can change while the program is running.</span></span> <span data-ttu-id="ad757-127">Visual Basic provádí operace volat *zabalení* a *rozbalení* k převodu mezi `Object` a typ hodnoty, takže provádění pomalejší.</span><span class="sxs-lookup"><span data-stu-id="ad757-127">Visual Basic performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower.</span></span> <span data-ttu-id="ad757-128">Informace o zabalení a rozbalení, najdete v článku [specifikace jazyka Visual Basic](../../../visual-basic/reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="ad757-128">For information about boxing and unboxing, see the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification/index.md).</span></span>
  
 <span data-ttu-id="ad757-129">Odvození typu proměnné se vztahuje na úrovni postup a doporučení se netýká mimo proceduru v třída, struktura, modul nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ad757-129">Type inference applies at the procedure level, and does not apply outside a procedure in a class, structure, module, or interface.</span></span>  
  
 <span data-ttu-id="ad757-130">Další informace najdete v tématu [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="ad757-130">For additional information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
## <a name="when-an-option-infer-statement-is-not-present"></a><span data-ttu-id="ad757-131">Když Option Infer – příkaz není k dispozici</span><span class="sxs-lookup"><span data-stu-id="ad757-131">When an Option Infer Statement Is Not Present</span></span>  
 <span data-ttu-id="ad757-132">Pokud zdrojový kód neobsahuje `Option Infer` příkazu **Option Infer** nastavení [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) se používá.</span><span class="sxs-lookup"><span data-stu-id="ad757-132">If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="ad757-133">Pokud se používá kompilátor příkazového řádku, [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) – možnost kompilátoru je používá.</span><span class="sxs-lookup"><span data-stu-id="ad757-133">If the command-line compiler is used, the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-infer-in-the-ide"></a><span data-ttu-id="ad757-134">Nastavení Option Infer v integrovaném vývojovém prostředí</span><span class="sxs-lookup"><span data-stu-id="ad757-134">To set Option Infer in the IDE</span></span>  
  
1.  <span data-ttu-id="ad757-135">V **Průzkumníka řešení**, vyberte projekt.</span><span class="sxs-lookup"><span data-stu-id="ad757-135">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="ad757-136">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="ad757-136">On the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="ad757-137">Klikněte na tlačítko **kompilaci** kartu.</span><span class="sxs-lookup"><span data-stu-id="ad757-137">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="ad757-138">Nastavte hodnotu **Option infer** pole.</span><span class="sxs-lookup"><span data-stu-id="ad757-138">Set the value in the **Option infer** box.</span></span>  
  
 <span data-ttu-id="ad757-139">Když vytvoříte nový projekt **Option Infer** nastavení na **kompilaci** karty nastavená na **Option Infer** nastavení **VB výchozí** Dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="ad757-139">When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="ad757-140">Pro přístup **VB výchozí** dialogovém okně **nástroje** nabídky, klikněte na tlačítko **možnosti**.</span><span class="sxs-lookup"><span data-stu-id="ad757-140">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="ad757-141">V **možnosti** dialogového okna rozbalte **projekty a řešení**a potom klikněte na tlačítko **VB výchozí**.</span><span class="sxs-lookup"><span data-stu-id="ad757-141">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="ad757-142">Počáteční výchozí nastavení v **výchozí hodnoty pro VB** je `On`.</span><span class="sxs-lookup"><span data-stu-id="ad757-142">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-infer-on-the-command-line"></a><span data-ttu-id="ad757-143">Chcete-li nastavit možnost Infer na příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="ad757-143">To set Option Infer on the command line</span></span>  
  
-   <span data-ttu-id="ad757-144">Zahrnout [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) – možnost kompilátoru v **Vbc –** příkazu.</span><span class="sxs-lookup"><span data-stu-id="ad757-144">Include the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="default-data-types-and-values"></a><span data-ttu-id="ad757-145">Výchozí datové typy a hodnoty</span><span class="sxs-lookup"><span data-stu-id="ad757-145">Default Data Types and Values</span></span>  
 <span data-ttu-id="ad757-146">Následující tabulka popisuje výsledky různých kombinací určující typ dat a obsahuje inicializační proceduru `Dim` příkazu.</span><span class="sxs-lookup"><span data-stu-id="ad757-146">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="ad757-147">Zadaný datový typ?</span><span class="sxs-lookup"><span data-stu-id="ad757-147">Data type specified?</span></span>|<span data-ttu-id="ad757-148">Inicializátor zadaný?</span><span class="sxs-lookup"><span data-stu-id="ad757-148">Initializer specified?</span></span>|<span data-ttu-id="ad757-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="ad757-149">Example</span></span>|<span data-ttu-id="ad757-150">Výsledek</span><span class="sxs-lookup"><span data-stu-id="ad757-150">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="ad757-151">Ne</span><span class="sxs-lookup"><span data-stu-id="ad757-151">No</span></span>|<span data-ttu-id="ad757-152">Ne</span><span class="sxs-lookup"><span data-stu-id="ad757-152">No</span></span>|`Dim qty`|<span data-ttu-id="ad757-153">Pokud `Option Strict` je vypnuto (výchozí), je proměnná nastavena `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="ad757-153">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="ad757-154">Pokud `Option Strict` zapnutý, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="ad757-154">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="ad757-155">Ne</span><span class="sxs-lookup"><span data-stu-id="ad757-155">No</span></span>|<span data-ttu-id="ad757-156">Ano</span><span class="sxs-lookup"><span data-stu-id="ad757-156">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="ad757-157">Pokud `Option Infer` je zapnuto (výchozí), zadejte proměnné přijímá data z inicializátoru.</span><span class="sxs-lookup"><span data-stu-id="ad757-157">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="ad757-158">Zobrazit [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="ad757-158">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="ad757-159">Pokud `Option Infer` je vypnuté a `Option Strict` je vypnuté, nabývá datový typ `Object`.</span><span class="sxs-lookup"><span data-stu-id="ad757-159">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="ad757-160">Pokud `Option Infer` je vypnuté a `Option Strict` zapnutý, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="ad757-160">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="ad757-161">Ano</span><span class="sxs-lookup"><span data-stu-id="ad757-161">Yes</span></span>|<span data-ttu-id="ad757-162">Ne</span><span class="sxs-lookup"><span data-stu-id="ad757-162">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="ad757-163">Proměnná je inicializována na výchozí hodnotu pro typ dat.</span><span class="sxs-lookup"><span data-stu-id="ad757-163">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="ad757-164">Další informace najdete v tématu [příkazu Dim](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ad757-164">For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>|  
|<span data-ttu-id="ad757-165">Ano</span><span class="sxs-lookup"><span data-stu-id="ad757-165">Yes</span></span>|<span data-ttu-id="ad757-166">Ano</span><span class="sxs-lookup"><span data-stu-id="ad757-166">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="ad757-167">Pokud datový typ inicializátor není lze převést na zadaný datový typ, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="ad757-167">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ad757-168">Příklad</span><span class="sxs-lookup"><span data-stu-id="ad757-168">Example</span></span>  
 <span data-ttu-id="ad757-169">Následující příklady ukazují, jak `Option Infer` příkaz povolí odvození místního typu.</span><span class="sxs-lookup"><span data-stu-id="ad757-169">The following examples demonstrate how the `Option Infer` statement enables local type inference.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="ad757-170">Příklad</span><span class="sxs-lookup"><span data-stu-id="ad757-170">Example</span></span>  
 <span data-ttu-id="ad757-171">Následující příklad ukazuje, že run-time typu se může lišit při proměnné se identifikuje jako `Object`.</span><span class="sxs-lookup"><span data-stu-id="ad757-171">The following example demonstrates that the run-time type can differ when a variable is identified as an `Object`.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#11](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ad757-172">Viz také</span><span class="sxs-lookup"><span data-stu-id="ad757-172">See Also</span></span>  
 [<span data-ttu-id="ad757-173">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="ad757-173">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="ad757-174">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="ad757-174">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="ad757-175">Příkaz Option Compare</span><span class="sxs-lookup"><span data-stu-id="ad757-175">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="ad757-176">Příkaz Option Explicit</span><span class="sxs-lookup"><span data-stu-id="ad757-176">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="ad757-177">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="ad757-177">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="ad757-178">Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti</span><span class="sxs-lookup"><span data-stu-id="ad757-178">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)  
 [<span data-ttu-id="ad757-179">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="ad757-179">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="ad757-180">Zabalení a rozbalení</span><span class="sxs-lookup"><span data-stu-id="ad757-180">Boxing and Unboxing</span></span>](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
