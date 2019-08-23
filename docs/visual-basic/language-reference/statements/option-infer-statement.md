---
title: Option odvod – příkaz (Visual Basic)
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
ms.openlocfilehash: e7f5fcc6d76f654f53eea6677962cb097e98b881
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912303"
---
# <a name="option-infer-statement"></a><span data-ttu-id="c86fd-102">Option Infer – příkaz</span><span class="sxs-lookup"><span data-stu-id="c86fd-102">Option Infer Statement</span></span>
<span data-ttu-id="c86fd-103">Umožňuje použití odvození místního typu v deklaraci proměnných.</span><span class="sxs-lookup"><span data-stu-id="c86fd-103">Enables the use of local type inference in declaring variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c86fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c86fd-104">Syntax</span></span>  
  
```  
Option Infer { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="c86fd-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="c86fd-105">Parts</span></span>  
  
|<span data-ttu-id="c86fd-106">Termín</span><span class="sxs-lookup"><span data-stu-id="c86fd-106">Term</span></span>|<span data-ttu-id="c86fd-107">Definice</span><span class="sxs-lookup"><span data-stu-id="c86fd-107">Definition</span></span>|  
|---|---|  
|`On`|<span data-ttu-id="c86fd-108">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="c86fd-108">Optional.</span></span> <span data-ttu-id="c86fd-109">Povoluje odvození místního typu.</span><span class="sxs-lookup"><span data-stu-id="c86fd-109">Enables local type inference.</span></span>|  
|`Off`|<span data-ttu-id="c86fd-110">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="c86fd-110">Optional.</span></span> <span data-ttu-id="c86fd-111">Zakáže odvození místního typu.</span><span class="sxs-lookup"><span data-stu-id="c86fd-111">Disables local type inference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c86fd-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c86fd-112">Remarks</span></span>  
 <span data-ttu-id="c86fd-113">Chcete- `Option Infer` li nastavit v souboru, `Option Infer On` zadejte `Option Infer Off` nebo v horní části souboru před jakýkoliv jiný zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="c86fd-113">To set `Option Infer` in a file, type `Option Infer On` or `Option Infer Off` at the top of the file, before any other source code.</span></span> <span data-ttu-id="c86fd-114">Pokud je hodnota nastavená `Option Infer` v souboru v konfliktu s hodnotou nastavenou v integrovaném vývojovém prostředí (IDE) nebo na příkazovém řádku, má hodnota v souboru přednost.</span><span class="sxs-lookup"><span data-stu-id="c86fd-114">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="c86fd-115">Když nastavíte `Option Infer` na `On`, můžete deklarovat místní proměnné bez explicitního oznámení datového typu.</span><span class="sxs-lookup"><span data-stu-id="c86fd-115">When you set `Option Infer` to `On`, you can declare local variables without explicitly stating a data type.</span></span> <span data-ttu-id="c86fd-116">Kompilátor odvodí datový typ proměnné z typu jeho inicializačního výrazu.</span><span class="sxs-lookup"><span data-stu-id="c86fd-116">The compiler infers the data type of a variable from the type of its initialization expression.</span></span>  
  
 <span data-ttu-id="c86fd-117">Na následujícím obrázku `Option Infer` je zapnutý.</span><span class="sxs-lookup"><span data-stu-id="c86fd-117">In the following illustration, `Option Infer` is turned on.</span></span> <span data-ttu-id="c86fd-118">Proměnná v deklaraci `Dim someVar = 2` je deklarována jako celé číslo podle odvození typu.</span><span class="sxs-lookup"><span data-stu-id="c86fd-118">The variable in the declaration `Dim someVar = 2` is declared as an integer by type inference.</span></span>

 <span data-ttu-id="c86fd-119">Následující snímek obrazovky ukazuje IntelliSense, pokud je možnost odvozená:</span><span class="sxs-lookup"><span data-stu-id="c86fd-119">The following screenshot shows IntelliSense when Option Infer is on:</span></span> 
  
 ![Snímek obrazovky znázorňující zobrazení IntelliSense, pokud je zapnutá možnost odvodit.](./media/option-infer-statement/option-infer-as-integer-on.png)  
  
 <span data-ttu-id="c86fd-121">Na následujícím obrázku `Option Infer` je vypnutý.</span><span class="sxs-lookup"><span data-stu-id="c86fd-121">In the following illustration, `Option Infer` is turned off.</span></span> <span data-ttu-id="c86fd-122">Proměnná v deklaraci `Dim someVar = 2` je deklarována `Object` jako odvození typu.</span><span class="sxs-lookup"><span data-stu-id="c86fd-122">The variable in the declaration `Dim someVar = 2` is declared as an `Object` by type inference.</span></span> <span data-ttu-id="c86fd-123">V tomto příkladu je **možnost Option Strict** nastavená na hodnotu **vypnuto** na [stránce kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="c86fd-123">In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="c86fd-124">Následující snímek obrazovky ukazuje IntelliSense, pokud je volba odvoditelné:</span><span class="sxs-lookup"><span data-stu-id="c86fd-124">The following screenshot shows IntelliSense when Option Infer is off:</span></span>
 
 ![Snímek obrazovky znázorňující zobrazení IntelliSense, pokud je volba odvoditelné](./media/option-infer-statement/option-infer-as-object-off.png)  
  
> [!NOTE]
> <span data-ttu-id="c86fd-126">Pokud je proměnná deklarována jako `Object`, typ za běhu se může změnit během běhu programu.</span><span class="sxs-lookup"><span data-stu-id="c86fd-126">When a variable is declared as an `Object`, the run-time type can change while the program is running.</span></span> <span data-ttu-id="c86fd-127">Visual Basic provádí operace označované jako zabalení a rozbalení pro `Object` převod mezi a hodnotovým typem, což činí provádění pomaleji.</span><span class="sxs-lookup"><span data-stu-id="c86fd-127">Visual Basic performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower.</span></span> <span data-ttu-id="c86fd-128">Informace o zabalení a rozbalení najdete v tématu [specifikace jazyka Visual Basic](~/_vblang/spec/conversions.md#value-type-conversions).</span><span class="sxs-lookup"><span data-stu-id="c86fd-128">For information about boxing and unboxing, see the [Visual Basic Language Specification](~/_vblang/spec/conversions.md#value-type-conversions).</span></span>
  
 <span data-ttu-id="c86fd-129">Odvození typu se vztahuje na úroveň procedury a neplatí mimo proceduru ve třídě, struktuře, modulu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c86fd-129">Type inference applies at the procedure level, and does not apply outside a procedure in a class, structure, module, or interface.</span></span>  
  
 <span data-ttu-id="c86fd-130">Další informace naleznete v tématu [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="c86fd-130">For additional information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
## <a name="when-an-option-infer-statement-is-not-present"></a><span data-ttu-id="c86fd-131">Pokud není k dispozici příkaz k odvození možnosti</span><span class="sxs-lookup"><span data-stu-id="c86fd-131">When an Option Infer Statement Is Not Present</span></span>  
 <span data-ttu-id="c86fd-132">Pokud zdrojový kód `Option Infer` neobsahuje příkaz, je použita **možnost odvodit** nastavení na [stránce kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) .</span><span class="sxs-lookup"><span data-stu-id="c86fd-132">If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="c86fd-133">Pokud je použit kompilátor příkazového řádku, je použita možnost kompilátoru [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) .</span><span class="sxs-lookup"><span data-stu-id="c86fd-133">If the command-line compiler is used, the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-infer-in-the-ide"></a><span data-ttu-id="c86fd-134">Nastavení volby odvoditelné v integrovaném vývojovém prostředí</span><span class="sxs-lookup"><span data-stu-id="c86fd-134">To set Option Infer in the IDE</span></span>  
  
1. <span data-ttu-id="c86fd-135">V **Průzkumník řešení**vyberte projekt.</span><span class="sxs-lookup"><span data-stu-id="c86fd-135">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="c86fd-136">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="c86fd-136">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="c86fd-137">Klikněte na kartu **kompilovat** .</span><span class="sxs-lookup"><span data-stu-id="c86fd-137">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="c86fd-138">Nastavte hodnotu v poli odvoditelné **Možnosti** .</span><span class="sxs-lookup"><span data-stu-id="c86fd-138">Set the value in the **Option infer** box.</span></span>  
  
 <span data-ttu-id="c86fd-139">Při vytváření nového projektu je **možnost odvodit** nastavení na kartě **kompilovat** nastavena na **možnost odvodit** nastavení v dialogovém okně **výchozí hodnoty VB** .</span><span class="sxs-lookup"><span data-stu-id="c86fd-139">When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="c86fd-140">Chcete-li získat přístup k dialogovému oknu **výchozí hodnoty VB** , v nabídce **nástroje** klikněte na možnost **Možnosti**.</span><span class="sxs-lookup"><span data-stu-id="c86fd-140">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="c86fd-141">V dialogovém okně **Možnosti** rozbalte **projekty a řešení**a potom klikněte na **výchozí hodnoty VB**.</span><span class="sxs-lookup"><span data-stu-id="c86fd-141">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="c86fd-142">Výchozí výchozí nastavení ve výchozím nastavení **jazyka VB** je `On`.</span><span class="sxs-lookup"><span data-stu-id="c86fd-142">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-infer-on-the-command-line"></a><span data-ttu-id="c86fd-143">Nastavení možnosti odvození v příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="c86fd-143">To set Option Infer on the command line</span></span>  
  
- <span data-ttu-id="c86fd-144">Do příkazu **Vbc** zahrňte možnost kompilátoru [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) .</span><span class="sxs-lookup"><span data-stu-id="c86fd-144">Include the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="default-data-types-and-values"></a><span data-ttu-id="c86fd-145">Výchozí datové typy a hodnoty</span><span class="sxs-lookup"><span data-stu-id="c86fd-145">Default Data Types and Values</span></span>  
 <span data-ttu-id="c86fd-146">Následující tabulka popisuje výsledky různých kombinací určení datového typu a inicializátoru v `Dim` příkazu.</span><span class="sxs-lookup"><span data-stu-id="c86fd-146">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="c86fd-147">Byl zadán datový typ?</span><span class="sxs-lookup"><span data-stu-id="c86fd-147">Data type specified?</span></span>|<span data-ttu-id="c86fd-148">Byl určen inicializátor?</span><span class="sxs-lookup"><span data-stu-id="c86fd-148">Initializer specified?</span></span>|<span data-ttu-id="c86fd-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="c86fd-149">Example</span></span>|<span data-ttu-id="c86fd-150">Výsledek</span><span class="sxs-lookup"><span data-stu-id="c86fd-150">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="c86fd-151">Ne</span><span class="sxs-lookup"><span data-stu-id="c86fd-151">No</span></span>|<span data-ttu-id="c86fd-152">Ne</span><span class="sxs-lookup"><span data-stu-id="c86fd-152">No</span></span>|`Dim qty`|<span data-ttu-id="c86fd-153">Pokud `Option Strict` je vypnuto (výchozí nastavení), proměnná je nastavena na `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="c86fd-153">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="c86fd-154">Pokud `Option Strict` je, dojde k chybě při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="c86fd-154">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="c86fd-155">Ne</span><span class="sxs-lookup"><span data-stu-id="c86fd-155">No</span></span>|<span data-ttu-id="c86fd-156">Ano</span><span class="sxs-lookup"><span data-stu-id="c86fd-156">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="c86fd-157">Pokud `Option Infer` je zapnuto (výchozí), proměnná převezme datový typ inicializátoru.</span><span class="sxs-lookup"><span data-stu-id="c86fd-157">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="c86fd-158">Viz [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="c86fd-158">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="c86fd-159">Pokud `Option Infer` je vypnutý `Option Strict` a je vypnutý, proměnná `Object`vezme datový typ.</span><span class="sxs-lookup"><span data-stu-id="c86fd-159">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="c86fd-160">Pokud `Option Infer` je vypnutý `Option Strict` a je zapnutý, dojde k chybě při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="c86fd-160">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="c86fd-161">Ano</span><span class="sxs-lookup"><span data-stu-id="c86fd-161">Yes</span></span>|<span data-ttu-id="c86fd-162">Ne</span><span class="sxs-lookup"><span data-stu-id="c86fd-162">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="c86fd-163">Proměnná je inicializována na výchozí hodnotu pro datový typ.</span><span class="sxs-lookup"><span data-stu-id="c86fd-163">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="c86fd-164">Další informace naleznete v tématu [Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c86fd-164">For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>|  
|<span data-ttu-id="c86fd-165">Ano</span><span class="sxs-lookup"><span data-stu-id="c86fd-165">Yes</span></span>|<span data-ttu-id="c86fd-166">Ano</span><span class="sxs-lookup"><span data-stu-id="c86fd-166">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="c86fd-167">Pokud datový typ inicializátoru nelze převést na zadaný datový typ, dojde k chybě při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="c86fd-167">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c86fd-168">Příklad</span><span class="sxs-lookup"><span data-stu-id="c86fd-168">Example</span></span>  
 <span data-ttu-id="c86fd-169">Následující příklady ukazují, jak `Option Infer` příkaz umožňuje odvození místního typu.</span><span class="sxs-lookup"><span data-stu-id="c86fd-169">The following examples demonstrate how the `Option Infer` statement enables local type inference.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="c86fd-170">Příklad</span><span class="sxs-lookup"><span data-stu-id="c86fd-170">Example</span></span>  
 <span data-ttu-id="c86fd-171">Následující příklad ukazuje, že běhový typ se může lišit, když je proměnná identifikována jako `Object`.</span><span class="sxs-lookup"><span data-stu-id="c86fd-171">The following example demonstrates that the run-time type can differ when a variable is identified as an `Object`.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="c86fd-172">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c86fd-172">See also</span></span>

- [<span data-ttu-id="c86fd-173">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="c86fd-173">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="c86fd-174">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="c86fd-174">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="c86fd-175">Příkaz Option Compare</span><span class="sxs-lookup"><span data-stu-id="c86fd-175">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="c86fd-176">Příkaz Option Explicit</span><span class="sxs-lookup"><span data-stu-id="c86fd-176">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="c86fd-177">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="c86fd-177">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="c86fd-178">Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti</span><span class="sxs-lookup"><span data-stu-id="c86fd-178">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [<span data-ttu-id="c86fd-179">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="c86fd-179">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="c86fd-180">Zabalení a rozbalení</span><span class="sxs-lookup"><span data-stu-id="c86fd-180">Boxing and Unboxing</span></span>](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
