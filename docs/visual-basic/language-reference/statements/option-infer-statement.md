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
ms.openlocfilehash: 53bc9d41f28f63061db2012395480aa6be7515dd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346496"
---
# <a name="option-infer-statement"></a><span data-ttu-id="20a78-102">Option Infer – příkaz</span><span class="sxs-lookup"><span data-stu-id="20a78-102">Option Infer Statement</span></span>

<span data-ttu-id="20a78-103">Enables the use of local type inference in declaring variables.</span><span class="sxs-lookup"><span data-stu-id="20a78-103">Enables the use of local type inference in declaring variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="20a78-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20a78-104">Syntax</span></span>

```vb
Option Infer { On | Off }
```

## <a name="parts"></a><span data-ttu-id="20a78-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="20a78-105">Parts</span></span>

|<span data-ttu-id="20a78-106">Termín</span><span class="sxs-lookup"><span data-stu-id="20a78-106">Term</span></span>|<span data-ttu-id="20a78-107">Definice</span><span class="sxs-lookup"><span data-stu-id="20a78-107">Definition</span></span>|
|---|---|
|`On`|<span data-ttu-id="20a78-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="20a78-108">Optional.</span></span> <span data-ttu-id="20a78-109">Enables local type inference.</span><span class="sxs-lookup"><span data-stu-id="20a78-109">Enables local type inference.</span></span>|
|`Off`|<span data-ttu-id="20a78-110">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="20a78-110">Optional.</span></span> <span data-ttu-id="20a78-111">Disables local type inference.</span><span class="sxs-lookup"><span data-stu-id="20a78-111">Disables local type inference.</span></span>|

## <a name="remarks"></a><span data-ttu-id="20a78-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="20a78-112">Remarks</span></span>

<span data-ttu-id="20a78-113">To set `Option Infer` in a file, type `Option Infer On` or `Option Infer Off` at the top of the file, before any other source code.</span><span class="sxs-lookup"><span data-stu-id="20a78-113">To set `Option Infer` in a file, type `Option Infer On` or `Option Infer Off` at the top of the file, before any other source code.</span></span> <span data-ttu-id="20a78-114">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span><span class="sxs-lookup"><span data-stu-id="20a78-114">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>

<span data-ttu-id="20a78-115">When you set `Option Infer` to `On`, you can declare local variables without explicitly stating a data type.</span><span class="sxs-lookup"><span data-stu-id="20a78-115">When you set `Option Infer` to `On`, you can declare local variables without explicitly stating a data type.</span></span> <span data-ttu-id="20a78-116">The compiler infers the data type of a variable from the type of its initialization expression.</span><span class="sxs-lookup"><span data-stu-id="20a78-116">The compiler infers the data type of a variable from the type of its initialization expression.</span></span>

<span data-ttu-id="20a78-117">In the following illustration, `Option Infer` is turned on.</span><span class="sxs-lookup"><span data-stu-id="20a78-117">In the following illustration, `Option Infer` is turned on.</span></span> <span data-ttu-id="20a78-118">The variable in the declaration `Dim someVar = 2` is declared as an integer by type inference.</span><span class="sxs-lookup"><span data-stu-id="20a78-118">The variable in the declaration `Dim someVar = 2` is declared as an integer by type inference.</span></span>

<span data-ttu-id="20a78-119">The following screenshot shows IntelliSense when Option Infer is on:</span><span class="sxs-lookup"><span data-stu-id="20a78-119">The following screenshot shows IntelliSense when Option Infer is on:</span></span>

![Screenshot showing IntelliSense view when Option Infer is on.](./media/option-infer-statement/option-infer-as-integer-on.png)

<span data-ttu-id="20a78-121">In the following illustration, `Option Infer` is turned off.</span><span class="sxs-lookup"><span data-stu-id="20a78-121">In the following illustration, `Option Infer` is turned off.</span></span> <span data-ttu-id="20a78-122">The variable in the declaration `Dim someVar = 2` is declared as an `Object` by type inference.</span><span class="sxs-lookup"><span data-stu-id="20a78-122">The variable in the declaration `Dim someVar = 2` is declared as an `Object` by type inference.</span></span> <span data-ttu-id="20a78-123">In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="20a78-123">In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>

<span data-ttu-id="20a78-124">The following screenshot shows IntelliSense when Option Infer is off:</span><span class="sxs-lookup"><span data-stu-id="20a78-124">The following screenshot shows IntelliSense when Option Infer is off:</span></span>

![Screenshot showing IntelliSense view when Option Infer is off.](./media/option-infer-statement/option-infer-as-object-off.png)

> [!NOTE]
> <span data-ttu-id="20a78-126">When a variable is declared as an `Object`, the run-time type can change while the program is running.</span><span class="sxs-lookup"><span data-stu-id="20a78-126">When a variable is declared as an `Object`, the run-time type can change while the program is running.</span></span> <span data-ttu-id="20a78-127">Visual Basic performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower.</span><span class="sxs-lookup"><span data-stu-id="20a78-127">Visual Basic performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower.</span></span> <span data-ttu-id="20a78-128">For information about boxing and unboxing, see the [Visual Basic Language Specification](~/_vblang/spec/conversions.md#value-type-conversions).</span><span class="sxs-lookup"><span data-stu-id="20a78-128">For information about boxing and unboxing, see the [Visual Basic Language Specification](~/_vblang/spec/conversions.md#value-type-conversions).</span></span>

<span data-ttu-id="20a78-129">Type inference applies at the procedure level, and does not apply outside a procedure in a class, structure, module, or interface.</span><span class="sxs-lookup"><span data-stu-id="20a78-129">Type inference applies at the procedure level, and does not apply outside a procedure in a class, structure, module, or interface.</span></span>

<span data-ttu-id="20a78-130">For additional information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="20a78-130">For additional information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>

## <a name="when-an-option-infer-statement-is-not-present"></a><span data-ttu-id="20a78-131">When an Option Infer Statement Is Not Present</span><span class="sxs-lookup"><span data-stu-id="20a78-131">When an Option Infer Statement Is Not Present</span></span>

<span data-ttu-id="20a78-132">If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span><span class="sxs-lookup"><span data-stu-id="20a78-132">If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="20a78-133">If the command-line compiler is used, the [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option is used.</span><span class="sxs-lookup"><span data-stu-id="20a78-133">If the command-line compiler is used, the [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option is used.</span></span>

#### <a name="to-set-option-infer-in-the-ide"></a><span data-ttu-id="20a78-134">To set Option Infer in the IDE</span><span class="sxs-lookup"><span data-stu-id="20a78-134">To set Option Infer in the IDE</span></span>

1. <span data-ttu-id="20a78-135">In **Solution Explorer**, select a project.</span><span class="sxs-lookup"><span data-stu-id="20a78-135">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="20a78-136">On the **Project** menu, click **Properties**.</span><span class="sxs-lookup"><span data-stu-id="20a78-136">On the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="20a78-137">Click the **Compile** tab.</span><span class="sxs-lookup"><span data-stu-id="20a78-137">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="20a78-138">Set the value in the **Option infer** box.</span><span class="sxs-lookup"><span data-stu-id="20a78-138">Set the value in the **Option infer** box.</span></span>

<span data-ttu-id="20a78-139">When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box.</span><span class="sxs-lookup"><span data-stu-id="20a78-139">When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="20a78-140">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span><span class="sxs-lookup"><span data-stu-id="20a78-140">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="20a78-141">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span><span class="sxs-lookup"><span data-stu-id="20a78-141">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="20a78-142">The initial default setting in **VB Defaults** is `On`.</span><span class="sxs-lookup"><span data-stu-id="20a78-142">The initial default setting in **VB Defaults** is `On`.</span></span>

#### <a name="to-set-option-infer-on-the-command-line"></a><span data-ttu-id="20a78-143">To set Option Infer on the command line</span><span class="sxs-lookup"><span data-stu-id="20a78-143">To set Option Infer on the command line</span></span>

<span data-ttu-id="20a78-144">Include the [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.</span><span class="sxs-lookup"><span data-stu-id="20a78-144">Include the [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.</span></span>

## <a name="default-data-types-and-values"></a><span data-ttu-id="20a78-145">Default Data Types and Values</span><span class="sxs-lookup"><span data-stu-id="20a78-145">Default Data Types and Values</span></span>

<span data-ttu-id="20a78-146">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span><span class="sxs-lookup"><span data-stu-id="20a78-146">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>

|<span data-ttu-id="20a78-147">Data type specified?</span><span class="sxs-lookup"><span data-stu-id="20a78-147">Data type specified?</span></span>|<span data-ttu-id="20a78-148">Initializer specified?</span><span class="sxs-lookup"><span data-stu-id="20a78-148">Initializer specified?</span></span>|<span data-ttu-id="20a78-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="20a78-149">Example</span></span>|<span data-ttu-id="20a78-150">Výsledek</span><span class="sxs-lookup"><span data-stu-id="20a78-150">Result</span></span>|
|---|---|---|---|
|<span data-ttu-id="20a78-151">Ne</span><span class="sxs-lookup"><span data-stu-id="20a78-151">No</span></span>|<span data-ttu-id="20a78-152">Ne</span><span class="sxs-lookup"><span data-stu-id="20a78-152">No</span></span>|`Dim qty`|<span data-ttu-id="20a78-153">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="20a78-153">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="20a78-154">If `Option Strict` is on, a compile-time error occurs.</span><span class="sxs-lookup"><span data-stu-id="20a78-154">If `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="20a78-155">Ne</span><span class="sxs-lookup"><span data-stu-id="20a78-155">No</span></span>|<span data-ttu-id="20a78-156">Ano</span><span class="sxs-lookup"><span data-stu-id="20a78-156">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="20a78-157">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span><span class="sxs-lookup"><span data-stu-id="20a78-157">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="20a78-158">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="20a78-158">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="20a78-159">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span><span class="sxs-lookup"><span data-stu-id="20a78-159">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="20a78-160">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span><span class="sxs-lookup"><span data-stu-id="20a78-160">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="20a78-161">Ano</span><span class="sxs-lookup"><span data-stu-id="20a78-161">Yes</span></span>|<span data-ttu-id="20a78-162">Ne</span><span class="sxs-lookup"><span data-stu-id="20a78-162">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="20a78-163">The variable is initialized to the default value for the data type.</span><span class="sxs-lookup"><span data-stu-id="20a78-163">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="20a78-164">For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="20a78-164">For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>|
|<span data-ttu-id="20a78-165">Ano</span><span class="sxs-lookup"><span data-stu-id="20a78-165">Yes</span></span>|<span data-ttu-id="20a78-166">Ano</span><span class="sxs-lookup"><span data-stu-id="20a78-166">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="20a78-167">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span><span class="sxs-lookup"><span data-stu-id="20a78-167">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|

## <a name="example"></a><span data-ttu-id="20a78-168">Příklad</span><span class="sxs-lookup"><span data-stu-id="20a78-168">Example</span></span>

<span data-ttu-id="20a78-169">The following examples demonstrate how the `Option Infer` statement enables local type inference.</span><span class="sxs-lookup"><span data-stu-id="20a78-169">The following examples demonstrate how the `Option Infer` statement enables local type inference.</span></span>

[!code-vb[VbVbalrTypeInference#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#6)]

## <a name="example"></a><span data-ttu-id="20a78-170">Příklad</span><span class="sxs-lookup"><span data-stu-id="20a78-170">Example</span></span>

<span data-ttu-id="20a78-171">The following example demonstrates that the run-time type can differ when a variable is identified as an `Object`.</span><span class="sxs-lookup"><span data-stu-id="20a78-171">The following example demonstrates that the run-time type can differ when a variable is identified as an `Object`.</span></span>

[!code-vb[VbVbalrTypeInference#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#11)]

## <a name="see-also"></a><span data-ttu-id="20a78-172">Viz také:</span><span class="sxs-lookup"><span data-stu-id="20a78-172">See also</span></span>

- [<span data-ttu-id="20a78-173">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="20a78-173">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="20a78-174">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="20a78-174">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="20a78-175">Příkaz Option Compare</span><span class="sxs-lookup"><span data-stu-id="20a78-175">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="20a78-176">Příkaz Option Explicit</span><span class="sxs-lookup"><span data-stu-id="20a78-176">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="20a78-177">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="20a78-177">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="20a78-178">Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti</span><span class="sxs-lookup"><span data-stu-id="20a78-178">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [<span data-ttu-id="20a78-179">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="20a78-179">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="20a78-180">Zabalení a rozbalení</span><span class="sxs-lookup"><span data-stu-id="20a78-180">Boxing and Unboxing</span></span>](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
