---
title: Option Compare – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.Compare
- vb.OptionCompare
helpviewer_keywords:
- case sensitivity, Option Compare statement
- Compare keyword [Visual Basic]
- binary comparison [Visual Basic]
- strings [Visual Basic], returning from functions
- binary comparison [Visual Basic], Option Compare statement
- strings [Visual Basic], comparing
- string comparison [Visual Basic], Option Compare statement
- Text keyword [Visual Basic], Option Compare statement
- Binary keyword [Visual Basic], Option Compare statement
- string comparison [Visual Basic], sorting data
- Option Compare statement [Visual Basic]
- text [Visual Basic], comparing
ms.assetid: 54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e
ms.openlocfilehash: 7538466c8f4b90e2e655a2ec762d8c545546a481
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344432"
---
# <a name="option-compare-statement"></a><span data-ttu-id="3e7fd-102">Option Compare – příkaz</span><span class="sxs-lookup"><span data-stu-id="3e7fd-102">Option Compare Statement</span></span>
<span data-ttu-id="3e7fd-103">Declares the default comparison method to use when comparing string data.</span><span class="sxs-lookup"><span data-stu-id="3e7fd-103">Declares the default comparison method to use when comparing string data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e7fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e7fd-104">Syntax</span></span>  
  
```vb  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a><span data-ttu-id="3e7fd-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="3e7fd-105">Parts</span></span>  
  
|<span data-ttu-id="3e7fd-106">Termín</span><span class="sxs-lookup"><span data-stu-id="3e7fd-106">Term</span></span>|<span data-ttu-id="3e7fd-107">Definice</span><span class="sxs-lookup"><span data-stu-id="3e7fd-107">Definition</span></span>|  
|---|---|  
|`Binary`|<span data-ttu-id="3e7fd-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3e7fd-108">Optional.</span></span> <span data-ttu-id="3e7fd-109">Results in string comparisons based on a sort order derived from the internal binary representations of the characters.</span><span class="sxs-lookup"><span data-stu-id="3e7fd-109">Results in string comparisons based on a sort order derived from the internal binary representations of the characters.</span></span><br /><br /> <span data-ttu-id="3e7fd-110">This type of comparison is useful especially if the strings can contain characters that are not to be interpreted as text.</span><span class="sxs-lookup"><span data-stu-id="3e7fd-110">This type of comparison is useful especially if the strings can contain characters that are not to be interpreted as text.</span></span> <span data-ttu-id="3e7fd-111">In this case, you do not want to bias comparisons with alphabetical equivalences, such as case insensitivity.</span><span class="sxs-lookup"><span data-stu-id="3e7fd-111">In this case, you do not want to bias comparisons with alphabetical equivalences, such as case insensitivity.</span></span>|  
|`Text`|<span data-ttu-id="3e7fd-112">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3e7fd-112">Optional.</span></span> <span data-ttu-id="3e7fd-113">Results in string comparisons based on a case-insensitive text sort order determined by your system's locale.</span><span class="sxs-lookup"><span data-stu-id="3e7fd-113">Results in string comparisons based on a case-insensitive text sort order determined by your system's locale.</span></span><br /><br /> <span data-ttu-id="3e7fd-114">This type of comparison is useful if your strings contain all text characters, and you want to compare them taking into account alphabetic equivalences such as case insensitivity and closely related letters.</span><span class="sxs-lookup"><span data-stu-id="3e7fd-114">This type of comparison is useful if your strings contain all text characters, and you want to compare them taking into account alphabetic equivalences such as case insensitivity and closely related letters.</span></span> <span data-ttu-id="3e7fd-115">For example, you might want to consider `A` and `a` to be equal, and `Ä` and `ä` to come before `B` and `b`.</span><span class="sxs-lookup"><span data-stu-id="3e7fd-115">For example, you might want to consider `A` and `a` to be equal, and `Ä` and `ä` to come before `B` and `b`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e7fd-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3e7fd-116">Remarks</span></span>  
 <span data-ttu-id="3e7fd-117">If used, the `Option Compare` statement must appear in a file before any other source code statements.</span><span class="sxs-lookup"><span data-stu-id="3e7fd-117">If used, the `Option Compare` statement must appear in a file before any other source code statements.</span></span>  
  
 <span data-ttu-id="3e7fd-118">The `Option Compare` statement specifies the string comparison method (`Binary` or `Text`).</span><span class="sxs-lookup"><span data-stu-id="3e7fd-118">The `Option Compare` statement specifies the string comparison method (`Binary` or `Text`).</span></span>  <span data-ttu-id="3e7fd-119">The default text comparison method is `Binary`.</span><span class="sxs-lookup"><span data-stu-id="3e7fd-119">The default text comparison method is `Binary`.</span></span>  
  
 <span data-ttu-id="3e7fd-120">A `Binary` comparison compares the numeric Unicode value of each character in each string.</span><span class="sxs-lookup"><span data-stu-id="3e7fd-120">A `Binary` comparison compares the numeric Unicode value of each character in each string.</span></span> <span data-ttu-id="3e7fd-121">A `Text` comparison compares each Unicode character based on its lexical meaning in the current culture.</span><span class="sxs-lookup"><span data-stu-id="3e7fd-121">A `Text` comparison compares each Unicode character based on its lexical meaning in the current culture.</span></span>  
  
 <span data-ttu-id="3e7fd-122">In Microsoft Windows, sort order is determined by the code page.</span><span class="sxs-lookup"><span data-stu-id="3e7fd-122">In Microsoft Windows, sort order is determined by the code page.</span></span> <span data-ttu-id="3e7fd-123">For more information, see [Code Pages](/cpp/c-runtime-library/code-pages).</span><span class="sxs-lookup"><span data-stu-id="3e7fd-123">For more information, see [Code Pages](/cpp/c-runtime-library/code-pages).</span></span>  
  
 <span data-ttu-id="3e7fd-124">In the following example, characters in the English/European code page (ANSI 1252) are sorted by using `Option Compare Binary`, which produces a typical binary sort order.</span><span class="sxs-lookup"><span data-stu-id="3e7fd-124">In the following example, characters in the English/European code page (ANSI 1252) are sorted by using `Option Compare Binary`, which produces a typical binary sort order.</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="3e7fd-125">When the same characters in the same code page are sorted by using `Option Compare Text`, the following text sort order is produced.</span><span class="sxs-lookup"><span data-stu-id="3e7fd-125">When the same characters in the same code page are sorted by using `Option Compare Text`, the following text sort order is produced.</span></span>  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a><span data-ttu-id="3e7fd-126">When an Option Compare Statement Is Not Present</span><span class="sxs-lookup"><span data-stu-id="3e7fd-126">When an Option Compare Statement Is Not Present</span></span>  
 <span data-ttu-id="3e7fd-127">If the source code does not contain an `Option Compare` statement, the **Option Compare** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span><span class="sxs-lookup"><span data-stu-id="3e7fd-127">If the source code does not contain an `Option Compare` statement, the **Option Compare** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="3e7fd-128">If you use the command-line compiler, the setting specified by the [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option is used.</span><span class="sxs-lookup"><span data-stu-id="3e7fd-128">If you use the command-line compiler, the setting specified by the [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option is used.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a><span data-ttu-id="3e7fd-129">To set Option Compare in the IDE</span><span class="sxs-lookup"><span data-stu-id="3e7fd-129">To set Option Compare in the IDE</span></span>  
  
1. <span data-ttu-id="3e7fd-130">In **Solution Explorer**, select a project.</span><span class="sxs-lookup"><span data-stu-id="3e7fd-130">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="3e7fd-131">On the **Project** menu, click **Properties**.</span><span class="sxs-lookup"><span data-stu-id="3e7fd-131">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="3e7fd-132">Click the **Compile** tab.</span><span class="sxs-lookup"><span data-stu-id="3e7fd-132">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="3e7fd-133">Set the value in the **Option Compare** box.</span><span class="sxs-lookup"><span data-stu-id="3e7fd-133">Set the value in the **Option Compare** box.</span></span>  
  
 <span data-ttu-id="3e7fd-134">When you create a project, the **Option Compare** setting on the **Compile** tab is set to the **Option Compare** setting in the **Options** dialog box.</span><span class="sxs-lookup"><span data-stu-id="3e7fd-134">When you create a project, the **Option Compare** setting on the **Compile** tab is set to the **Option Compare** setting in the **Options** dialog box.</span></span> <span data-ttu-id="3e7fd-135">To change this setting, on the **Tools** menu, click **Options**.</span><span class="sxs-lookup"><span data-stu-id="3e7fd-135">To change this setting, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="3e7fd-136">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span><span class="sxs-lookup"><span data-stu-id="3e7fd-136">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="3e7fd-137">The initial default setting in **VB Defaults** is **Binary**.</span><span class="sxs-lookup"><span data-stu-id="3e7fd-137">The initial default setting in **VB Defaults** is **Binary**.</span></span>  
  
#### <a name="to-set-option-compare-on-the-command-line"></a><span data-ttu-id="3e7fd-138">To set Option Compare on the command line</span><span class="sxs-lookup"><span data-stu-id="3e7fd-138">To set Option Compare on the command line</span></span>  
  
- <span data-ttu-id="3e7fd-139">Include the [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option in the **vbc** command.</span><span class="sxs-lookup"><span data-stu-id="3e7fd-139">Include the [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e7fd-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="3e7fd-140">Example</span></span>  
 <span data-ttu-id="3e7fd-141">The following example uses the `Option Compare` statement to set the binary comparison as the default string comparison method.</span><span class="sxs-lookup"><span data-stu-id="3e7fd-141">The following example uses the `Option Compare` statement to set the binary comparison as the default string comparison method.</span></span> <span data-ttu-id="3e7fd-142">To use this code, uncomment the `Option Compare Binary` statement, and put it at the top of the source file.</span><span class="sxs-lookup"><span data-stu-id="3e7fd-142">To use this code, uncomment the `Option Compare Binary` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#45)]  
  
## <a name="example"></a><span data-ttu-id="3e7fd-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="3e7fd-143">Example</span></span>  
 <span data-ttu-id="3e7fd-144">The following example uses the `Option Compare` statement to set the case-insensitive text sort order as the default string comparison method.</span><span class="sxs-lookup"><span data-stu-id="3e7fd-144">The following example uses the `Option Compare` statement to set the case-insensitive text sort order as the default string comparison method.</span></span> <span data-ttu-id="3e7fd-145">To use this code, uncomment the `Option Compare Text` statement, and put it at the top of the source file.</span><span class="sxs-lookup"><span data-stu-id="3e7fd-145">To use this code, uncomment the `Option Compare Text` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="3e7fd-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3e7fd-146">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>
- <xref:Microsoft.VisualBasic.Strings.Replace%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [<span data-ttu-id="3e7fd-147">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="3e7fd-147">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="3e7fd-148">Operátory porovnání</span><span class="sxs-lookup"><span data-stu-id="3e7fd-148">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="3e7fd-149">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3e7fd-149">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="3e7fd-150">Operátor Like</span><span class="sxs-lookup"><span data-stu-id="3e7fd-150">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)
- [<span data-ttu-id="3e7fd-151">Funkce řetězce</span><span class="sxs-lookup"><span data-stu-id="3e7fd-151">String Functions</span></span>](../../../visual-basic/language-reference/functions/string-functions.md)
- [<span data-ttu-id="3e7fd-152">Příkaz Option Explicit</span><span class="sxs-lookup"><span data-stu-id="3e7fd-152">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="3e7fd-153">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="3e7fd-153">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
