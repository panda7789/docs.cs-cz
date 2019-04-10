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
ms.openlocfilehash: 59766999c5b03aac7aec13b293feaa8c17f2ced0
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59338563"
---
# <a name="option-infer-statement"></a><span data-ttu-id="e4662-102">Option Infer – příkaz</span><span class="sxs-lookup"><span data-stu-id="e4662-102">Option Infer Statement</span></span>
<span data-ttu-id="e4662-103">Umožňuje použití odvození místního typu v deklarujících proměnných.</span><span class="sxs-lookup"><span data-stu-id="e4662-103">Enables the use of local type inference in declaring variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4662-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4662-104">Syntax</span></span>  
  
```  
Option Infer { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="e4662-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="e4662-105">Parts</span></span>  
  
|<span data-ttu-id="e4662-106">Termín</span><span class="sxs-lookup"><span data-stu-id="e4662-106">Term</span></span>|<span data-ttu-id="e4662-107">Definice</span><span class="sxs-lookup"><span data-stu-id="e4662-107">Definition</span></span>|  
|---|---|  
|`On`|<span data-ttu-id="e4662-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e4662-108">Optional.</span></span> <span data-ttu-id="e4662-109">Umožňuje odvození místního typu.</span><span class="sxs-lookup"><span data-stu-id="e4662-109">Enables local type inference.</span></span>|  
|`Off`|<span data-ttu-id="e4662-110">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e4662-110">Optional.</span></span> <span data-ttu-id="e4662-111">Zakáže odvození místního typu.</span><span class="sxs-lookup"><span data-stu-id="e4662-111">Disables local type inference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4662-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e4662-112">Remarks</span></span>  
 <span data-ttu-id="e4662-113">Chcete-li nastavit `Option Infer` v souboru, zadejte `Option Infer On` nebo `Option Infer Off` v horní části souboru, než jakýkoli jiný zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="e4662-113">To set `Option Infer` in a file, type `Option Infer On` or `Option Infer Off` at the top of the file, before any other source code.</span></span> <span data-ttu-id="e4662-114">Je-li nastavena hodnota pro `Option Infer` v souboru konflikty s hodnotou nastavenou v integrovaném vývojovém prostředí nebo na příkazovém řádku, hodnota v souboru má prioritu.</span><span class="sxs-lookup"><span data-stu-id="e4662-114">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="e4662-115">Pokud nastavíte `Option Infer` k `On`, bez explicitní uvedení datový typ je možné deklarovat lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="e4662-115">When you set `Option Infer` to `On`, you can declare local variables without explicitly stating a data type.</span></span> <span data-ttu-id="e4662-116">Kompilátor odvodí datový typ proměnné z typu výrazu jeho inicializaci.</span><span class="sxs-lookup"><span data-stu-id="e4662-116">The compiler infers the data type of a variable from the type of its initialization expression.</span></span>  
  
 <span data-ttu-id="e4662-117">Na následujícím obrázku `Option Infer` zapnutý.</span><span class="sxs-lookup"><span data-stu-id="e4662-117">In the following illustration, `Option Infer` is turned on.</span></span> <span data-ttu-id="e4662-118">Proměnné v deklaraci `Dim someVar = 2` je deklarován jako celé číslo odvození typu proměnné.</span><span class="sxs-lookup"><span data-stu-id="e4662-118">The variable in the declaration `Dim someVar = 2` is declared as an integer by type inference.</span></span>

 <span data-ttu-id="e4662-119">Následující snímek obrazovky ukazuje technologie IntelliSense, když Option Infer na:</span><span class="sxs-lookup"><span data-stu-id="e4662-119">The following screenshot shows IntelliSense when Option Infer is on:</span></span> 
  
 ![Snímek obrazovky s IntelliSense zobrazení Option Infer je na.](./media/option-infer-statement/option-infer-as-integer-on.png)  
  
 <span data-ttu-id="e4662-121">Na následujícím obrázku `Option Infer` je vypnutý.</span><span class="sxs-lookup"><span data-stu-id="e4662-121">In the following illustration, `Option Infer` is turned off.</span></span> <span data-ttu-id="e4662-122">Proměnné v deklaraci `Dim someVar = 2` je deklarován jako `Object` podle odvození typu proměnné.</span><span class="sxs-lookup"><span data-stu-id="e4662-122">The variable in the declaration `Dim someVar = 2` is declared as an `Object` by type inference.</span></span> <span data-ttu-id="e4662-123">V tomto příkladu **Option Strict** nastavená na **vypnout** na [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="e4662-123">In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="e4662-124">Následující snímek obrazovky ukazuje technologie IntelliSense, když Option Infer je vypnuté:</span><span class="sxs-lookup"><span data-stu-id="e4662-124">The following screenshot shows IntelliSense when Option Infer is off:</span></span>
 
 ![Snímek obrazovky zobrazení technologie IntelliSense při Option Infer je vypnuté.](./media/option-infer-statement/option-infer-as-object-off.png)  
  
> [!NOTE]
>  <span data-ttu-id="e4662-126">Pokud je proměnná deklarována jako `Object`, run-time typu můžete změnit, zatímco program běží.</span><span class="sxs-lookup"><span data-stu-id="e4662-126">When a variable is declared as an `Object`, the run-time type can change while the program is running.</span></span> <span data-ttu-id="e4662-127">Visual Basic provádí operace volat *zabalení* a *rozbalení* k převodu mezi `Object` a typ hodnoty, takže provádění pomalejší.</span><span class="sxs-lookup"><span data-stu-id="e4662-127">Visual Basic performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower.</span></span> <span data-ttu-id="e4662-128">Informace o zabalení a rozbalení, najdete v článku [specifikace jazyka Visual Basic](~/_vblang/spec/conversions.md#value-type-conversions).</span><span class="sxs-lookup"><span data-stu-id="e4662-128">For information about boxing and unboxing, see the [Visual Basic Language Specification](~/_vblang/spec/conversions.md#value-type-conversions).</span></span>
  
 <span data-ttu-id="e4662-129">Odvození typu proměnné se vztahuje na úrovni postup a doporučení se netýká mimo proceduru v třída, struktura, modul nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e4662-129">Type inference applies at the procedure level, and does not apply outside a procedure in a class, structure, module, or interface.</span></span>  
  
 <span data-ttu-id="e4662-130">Další informace najdete v tématu [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="e4662-130">For additional information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
## <a name="when-an-option-infer-statement-is-not-present"></a><span data-ttu-id="e4662-131">Když Option Infer – příkaz není k dispozici</span><span class="sxs-lookup"><span data-stu-id="e4662-131">When an Option Infer Statement Is Not Present</span></span>  
 <span data-ttu-id="e4662-132">Pokud zdrojový kód neobsahuje `Option Infer` příkazu **Option Infer** nastavení [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) se používá.</span><span class="sxs-lookup"><span data-stu-id="e4662-132">If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="e4662-133">Pokud se používá kompilátor příkazového řádku, [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) – možnost kompilátoru je používá.</span><span class="sxs-lookup"><span data-stu-id="e4662-133">If the command-line compiler is used, the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-infer-in-the-ide"></a><span data-ttu-id="e4662-134">Nastavení Option Infer v integrovaném vývojovém prostředí</span><span class="sxs-lookup"><span data-stu-id="e4662-134">To set Option Infer in the IDE</span></span>  
  
1. <span data-ttu-id="e4662-135">V **Průzkumníka řešení**, vyberte projekt.</span><span class="sxs-lookup"><span data-stu-id="e4662-135">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="e4662-136">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="e4662-136">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="e4662-137">Klikněte na tlačítko **kompilaci** kartu.</span><span class="sxs-lookup"><span data-stu-id="e4662-137">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="e4662-138">Nastavte hodnotu **Option infer** pole.</span><span class="sxs-lookup"><span data-stu-id="e4662-138">Set the value in the **Option infer** box.</span></span>  
  
 <span data-ttu-id="e4662-139">Když vytvoříte nový projekt **Option Infer** nastavení na **kompilaci** karty nastavená na **Option Infer** nastavení **VB výchozí** Dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="e4662-139">When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="e4662-140">Pro přístup **VB výchozí** dialogovém okně **nástroje** nabídky, klikněte na tlačítko **možnosti**.</span><span class="sxs-lookup"><span data-stu-id="e4662-140">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="e4662-141">V **možnosti** dialogového okna rozbalte **projekty a řešení**a potom klikněte na tlačítko **VB výchozí**.</span><span class="sxs-lookup"><span data-stu-id="e4662-141">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="e4662-142">Počáteční výchozí nastavení v **výchozí hodnoty pro VB** je `On`.</span><span class="sxs-lookup"><span data-stu-id="e4662-142">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-infer-on-the-command-line"></a><span data-ttu-id="e4662-143">Chcete-li nastavit možnost Infer na příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="e4662-143">To set Option Infer on the command line</span></span>  
  
-   <span data-ttu-id="e4662-144">Zahrnout [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) – možnost kompilátoru v **Vbc –** příkazu.</span><span class="sxs-lookup"><span data-stu-id="e4662-144">Include the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="default-data-types-and-values"></a><span data-ttu-id="e4662-145">Výchozí datové typy a hodnoty</span><span class="sxs-lookup"><span data-stu-id="e4662-145">Default Data Types and Values</span></span>  
 <span data-ttu-id="e4662-146">Následující tabulka popisuje výsledky různých kombinací určující typ dat a obsahuje inicializační proceduru `Dim` příkazu.</span><span class="sxs-lookup"><span data-stu-id="e4662-146">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="e4662-147">Zadaný datový typ?</span><span class="sxs-lookup"><span data-stu-id="e4662-147">Data type specified?</span></span>|<span data-ttu-id="e4662-148">Inicializátor zadaný?</span><span class="sxs-lookup"><span data-stu-id="e4662-148">Initializer specified?</span></span>|<span data-ttu-id="e4662-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="e4662-149">Example</span></span>|<span data-ttu-id="e4662-150">Výsledek</span><span class="sxs-lookup"><span data-stu-id="e4662-150">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="e4662-151">Ne</span><span class="sxs-lookup"><span data-stu-id="e4662-151">No</span></span>|<span data-ttu-id="e4662-152">Ne</span><span class="sxs-lookup"><span data-stu-id="e4662-152">No</span></span>|`Dim qty`|<span data-ttu-id="e4662-153">Pokud `Option Strict` je vypnuto (výchozí), je proměnná nastavena `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="e4662-153">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="e4662-154">Pokud `Option Strict` zapnutý, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="e4662-154">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="e4662-155">Ne</span><span class="sxs-lookup"><span data-stu-id="e4662-155">No</span></span>|<span data-ttu-id="e4662-156">Ano</span><span class="sxs-lookup"><span data-stu-id="e4662-156">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="e4662-157">Pokud `Option Infer` je zapnuto (výchozí), zadejte proměnné přijímá data z inicializátoru.</span><span class="sxs-lookup"><span data-stu-id="e4662-157">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="e4662-158">Zobrazit [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="e4662-158">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="e4662-159">Pokud `Option Infer` je vypnuté a `Option Strict` je vypnuté, nabývá datový typ `Object`.</span><span class="sxs-lookup"><span data-stu-id="e4662-159">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="e4662-160">Pokud `Option Infer` je vypnuté a `Option Strict` zapnutý, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="e4662-160">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="e4662-161">Ano</span><span class="sxs-lookup"><span data-stu-id="e4662-161">Yes</span></span>|<span data-ttu-id="e4662-162">Ne</span><span class="sxs-lookup"><span data-stu-id="e4662-162">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="e4662-163">Proměnná je inicializována na výchozí hodnotu pro typ dat.</span><span class="sxs-lookup"><span data-stu-id="e4662-163">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="e4662-164">Další informace najdete v tématu [příkazu Dim](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e4662-164">For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>|  
|<span data-ttu-id="e4662-165">Ano</span><span class="sxs-lookup"><span data-stu-id="e4662-165">Yes</span></span>|<span data-ttu-id="e4662-166">Ano</span><span class="sxs-lookup"><span data-stu-id="e4662-166">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="e4662-167">Pokud datový typ inicializátor není lze převést na zadaný datový typ, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="e4662-167">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e4662-168">Příklad</span><span class="sxs-lookup"><span data-stu-id="e4662-168">Example</span></span>  
 <span data-ttu-id="e4662-169">Následující příklady ukazují, jak `Option Infer` příkaz povolí odvození místního typu.</span><span class="sxs-lookup"><span data-stu-id="e4662-169">The following examples demonstrate how the `Option Infer` statement enables local type inference.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="e4662-170">Příklad</span><span class="sxs-lookup"><span data-stu-id="e4662-170">Example</span></span>  
 <span data-ttu-id="e4662-171">Následující příklad ukazuje, že run-time typu se může lišit při proměnné se identifikuje jako `Object`.</span><span class="sxs-lookup"><span data-stu-id="e4662-171">The following example demonstrates that the run-time type can differ when a variable is identified as an `Object`.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="e4662-172">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4662-172">See also</span></span>

- [<span data-ttu-id="e4662-173">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="e4662-173">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="e4662-174">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="e4662-174">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="e4662-175">Option Compare – příkaz</span><span class="sxs-lookup"><span data-stu-id="e4662-175">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="e4662-176">Option Explicit – příkaz</span><span class="sxs-lookup"><span data-stu-id="e4662-176">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="e4662-177">Option Strict – příkaz</span><span class="sxs-lookup"><span data-stu-id="e4662-177">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="e4662-178">Výchozí možnosti jazyka Visual Basic, projekty, dialogové okno Možnosti</span><span class="sxs-lookup"><span data-stu-id="e4662-178">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [<span data-ttu-id="e4662-179">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="e4662-179">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="e4662-180">Zabalení a rozbalení</span><span class="sxs-lookup"><span data-stu-id="e4662-180">Boxing and Unboxing</span></span>](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
