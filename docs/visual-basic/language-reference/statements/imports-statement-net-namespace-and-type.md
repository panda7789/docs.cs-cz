---
title: Imports Statement - .NET Namespace and Type
ms.date: 07/20/2015
f1_keywords:
- vb.Imports
- imports
helpviewer_keywords:
- declared element names [Visual Basic], qualification
- imports [Visual Basic]
- Imports statement [Visual Basic]
- aliases [Visual Basic], Imports statement
- container elements [Visual Basic]
- namespaces [Visual Basic], importing
- Imports statement [Visual Basic], syntax
- import aliases [Visual Basic]
- aliases [Visual Basic], import
- declared elements [Visual Basic], container elements
ms.assetid: 7062f8aa-d890-4232-9eed-92836e13fb6e
ms.openlocfilehash: 39fa4e74f973bcb575b5751c387c0b879f4e398d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351071"
---
# <a name="imports-statement-net-namespace-and-type"></a><span data-ttu-id="84436-102">Imports – příkaz (obor názvů a typ rozhraní .NET)</span><span class="sxs-lookup"><span data-stu-id="84436-102">Imports Statement (.NET Namespace and Type)</span></span>

<span data-ttu-id="84436-103">Enables type names to be referenced without namespace qualification.</span><span class="sxs-lookup"><span data-stu-id="84436-103">Enables type names to be referenced without namespace qualification.</span></span>

## <a name="syntax"></a><span data-ttu-id="84436-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84436-104">Syntax</span></span>

```vb
Imports [ aliasname = ] namespace
' -or-
Imports [ aliasname = ] namespace.element
```

## <a name="parts"></a><span data-ttu-id="84436-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="84436-105">Parts</span></span>

|<span data-ttu-id="84436-106">Termín</span><span class="sxs-lookup"><span data-stu-id="84436-106">Term</span></span>|<span data-ttu-id="84436-107">Definice</span><span class="sxs-lookup"><span data-stu-id="84436-107">Definition</span></span>|
|---|---|
|`aliasname`|<span data-ttu-id="84436-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="84436-108">Optional.</span></span> <span data-ttu-id="84436-109">An *import alias* or name by which code can refer to `namespace` instead of the full qualification string.</span><span class="sxs-lookup"><span data-stu-id="84436-109">An *import alias* or name by which code can refer to `namespace` instead of the full qualification string.</span></span> <span data-ttu-id="84436-110">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="84436-110">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
|`namespace`|<span data-ttu-id="84436-111">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="84436-111">Required.</span></span> <span data-ttu-id="84436-112">The fully qualified name of the namespace being imported.</span><span class="sxs-lookup"><span data-stu-id="84436-112">The fully qualified name of the namespace being imported.</span></span> <span data-ttu-id="84436-113">Can be a string of namespaces nested to any level.</span><span class="sxs-lookup"><span data-stu-id="84436-113">Can be a string of namespaces nested to any level.</span></span>|
|`element`|<span data-ttu-id="84436-114">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="84436-114">Optional.</span></span> <span data-ttu-id="84436-115">The name of a programming element declared in the namespace.</span><span class="sxs-lookup"><span data-stu-id="84436-115">The name of a programming element declared in the namespace.</span></span> <span data-ttu-id="84436-116">Can be any container element.</span><span class="sxs-lookup"><span data-stu-id="84436-116">Can be any container element.</span></span>|

## <a name="remarks"></a><span data-ttu-id="84436-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="84436-117">Remarks</span></span>

<span data-ttu-id="84436-118">The `Imports` statement enables types that are contained in a given namespace to be referenced directly.</span><span class="sxs-lookup"><span data-stu-id="84436-118">The `Imports` statement enables types that are contained in a given namespace to be referenced directly.</span></span>

<span data-ttu-id="84436-119">You can supply a single namespace name or a string of nested namespaces.</span><span class="sxs-lookup"><span data-stu-id="84436-119">You can supply a single namespace name or a string of nested namespaces.</span></span> <span data-ttu-id="84436-120">Each nested namespace is separated from the next higher level namespace by a period (`.`), as the following example illustrates:</span><span class="sxs-lookup"><span data-stu-id="84436-120">Each nested namespace is separated from the next higher level namespace by a period (`.`), as the following example illustrates:</span></span>

```vb
Imports System.Collections.Generic
```

<span data-ttu-id="84436-121">Each source file can contain any number of `Imports` statements.</span><span class="sxs-lookup"><span data-stu-id="84436-121">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="84436-122">These must follow any option declarations, such as the `Option Strict` statement, and they must precede any programming element declarations, such as `Module` or `Class` statements.</span><span class="sxs-lookup"><span data-stu-id="84436-122">These must follow any option declarations, such as the `Option Strict` statement, and they must precede any programming element declarations, such as `Module` or `Class` statements.</span></span>

<span data-ttu-id="84436-123">You can use `Imports` only at file level.</span><span class="sxs-lookup"><span data-stu-id="84436-123">You can use `Imports` only at file level.</span></span> <span data-ttu-id="84436-124">This means the declaration context for importation must be a source file, and cannot be a namespace, class, structure, module, interface, procedure, or block.</span><span class="sxs-lookup"><span data-stu-id="84436-124">This means the declaration context for importation must be a source file, and cannot be a namespace, class, structure, module, interface, procedure, or block.</span></span>

<span data-ttu-id="84436-125">Note that the `Imports` statement does not make elements from other projects and assemblies available to your project.</span><span class="sxs-lookup"><span data-stu-id="84436-125">Note that the `Imports` statement does not make elements from other projects and assemblies available to your project.</span></span> <span data-ttu-id="84436-126">Importing does not take the place of setting a reference.</span><span class="sxs-lookup"><span data-stu-id="84436-126">Importing does not take the place of setting a reference.</span></span> <span data-ttu-id="84436-127">It only removes the need to qualify names that are already available to your project.</span><span class="sxs-lookup"><span data-stu-id="84436-127">It only removes the need to qualify names that are already available to your project.</span></span> <span data-ttu-id="84436-128">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="84436-128">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

> [!NOTE]
> <span data-ttu-id="84436-129">You can define implicit `Imports` statements by using the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="84436-129">You can define implicit `Imports` statements by using the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span> <span data-ttu-id="84436-130">For more information, see [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="84436-130">For more information, see [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>

## <a name="import-aliases"></a><span data-ttu-id="84436-131">Import Aliases</span><span class="sxs-lookup"><span data-stu-id="84436-131">Import Aliases</span></span>

<span data-ttu-id="84436-132">An *import alias* defines the alias for a namespace or type.</span><span class="sxs-lookup"><span data-stu-id="84436-132">An *import alias* defines the alias for a namespace or type.</span></span> <span data-ttu-id="84436-133">Import aliases are useful when you need to use items with the same name that are declared in one or more namespaces.</span><span class="sxs-lookup"><span data-stu-id="84436-133">Import aliases are useful when you need to use items with the same name that are declared in one or more namespaces.</span></span> <span data-ttu-id="84436-134">For more information and an example, see "Qualifying an Element Name" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="84436-134">For more information and an example, see "Qualifying an Element Name" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

<span data-ttu-id="84436-135">You should not declare a member at module level with the same name as `aliasname`.</span><span class="sxs-lookup"><span data-stu-id="84436-135">You should not declare a member at module level with the same name as `aliasname`.</span></span> <span data-ttu-id="84436-136">If you do, the Visual Basic compiler uses `aliasname` only for the declared member and no longer recognizes it as an import alias.</span><span class="sxs-lookup"><span data-stu-id="84436-136">If you do, the Visual Basic compiler uses `aliasname` only for the declared member and no longer recognizes it as an import alias.</span></span>

<span data-ttu-id="84436-137">Although the syntax used for declaring an import alias is like that used for importing an XML namespace prefix, the results are different.</span><span class="sxs-lookup"><span data-stu-id="84436-137">Although the syntax used for declaring an import alias is like that used for importing an XML namespace prefix, the results are different.</span></span> <span data-ttu-id="84436-138">An import alias can be used as an expression in your code, whereas an XML namespace prefix can be used only in XML literals or XML axis properties as the prefix for a qualified element or attribute name.</span><span class="sxs-lookup"><span data-stu-id="84436-138">An import alias can be used as an expression in your code, whereas an XML namespace prefix can be used only in XML literals or XML axis properties as the prefix for a qualified element or attribute name.</span></span>

### <a name="element-names"></a><span data-ttu-id="84436-139">Názvy elementů</span><span class="sxs-lookup"><span data-stu-id="84436-139">Element Names</span></span>

<span data-ttu-id="84436-140">If you supply `element`, it must represent a *container element*, that is, a programming element that can contain other elements.</span><span class="sxs-lookup"><span data-stu-id="84436-140">If you supply `element`, it must represent a *container element*, that is, a programming element that can contain other elements.</span></span> <span data-ttu-id="84436-141">Container elements include classes, structures, modules, interfaces, and enumerations.</span><span class="sxs-lookup"><span data-stu-id="84436-141">Container elements include classes, structures, modules, interfaces, and enumerations.</span></span>

<span data-ttu-id="84436-142">The scope of the elements made available by an `Imports` statement depends on whether you specify `element`.</span><span class="sxs-lookup"><span data-stu-id="84436-142">The scope of the elements made available by an `Imports` statement depends on whether you specify `element`.</span></span> <span data-ttu-id="84436-143">If you specify only `namespace`, all uniquely named members of that namespace, and members of container elements within that namespace, are available without qualification.</span><span class="sxs-lookup"><span data-stu-id="84436-143">If you specify only `namespace`, all uniquely named members of that namespace, and members of container elements within that namespace, are available without qualification.</span></span> <span data-ttu-id="84436-144">If you specify both `namespace` and `element`, only the members of that element are available without qualification.</span><span class="sxs-lookup"><span data-stu-id="84436-144">If you specify both `namespace` and `element`, only the members of that element are available without qualification.</span></span>

## <a name="example"></a><span data-ttu-id="84436-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="84436-145">Example</span></span>

<span data-ttu-id="84436-146">The following example returns all the folders in the *C:\\* directory by using the <xref:System.IO.DirectoryInfo> class:</span><span class="sxs-lookup"><span data-stu-id="84436-146">The following example returns all the folders in the *C:\\* directory by using the <xref:System.IO.DirectoryInfo> class:</span></span>

<span data-ttu-id="84436-147">The code has no `Imports` statements at the top of the file.</span><span class="sxs-lookup"><span data-stu-id="84436-147">The code has no `Imports` statements at the top of the file.</span></span> <span data-ttu-id="84436-148">Therefore, the <xref:System.IO.DirectoryInfo>, <xref:System.Text.StringBuilder>, and <xref:Microsoft.VisualBasic.ControlChars.CrLf> references are all fully qualified with the namespaces.</span><span class="sxs-lookup"><span data-stu-id="84436-148">Therefore, the <xref:System.IO.DirectoryInfo>, <xref:System.Text.StringBuilder>, and <xref:Microsoft.VisualBasic.ControlChars.CrLf> references are all fully qualified with the namespaces.</span></span>

[!code-vb[VbVbalrStatements#152](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#152)]

## <a name="example"></a><span data-ttu-id="84436-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="84436-149">Example</span></span>

<span data-ttu-id="84436-150">The following example includes `Imports` statements for the referenced namespaces.</span><span class="sxs-lookup"><span data-stu-id="84436-150">The following example includes `Imports` statements for the referenced namespaces.</span></span> <span data-ttu-id="84436-151">Therefore, the types do not have to be fully qualified with the namespaces.</span><span class="sxs-lookup"><span data-stu-id="84436-151">Therefore, the types do not have to be fully qualified with the namespaces.</span></span>

[!code-vb[VbVbalrStatements#153](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#153)]

[!code-vb[VbVbalrStatements#154](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#154)]
  
## <a name="example"></a><span data-ttu-id="84436-152">Příklad</span><span class="sxs-lookup"><span data-stu-id="84436-152">Example</span></span>

<span data-ttu-id="84436-153">The following example includes `Imports` statements that create aliases for the referenced namespaces.</span><span class="sxs-lookup"><span data-stu-id="84436-153">The following example includes `Imports` statements that create aliases for the referenced namespaces.</span></span> <span data-ttu-id="84436-154">The types are qualified with the aliases.</span><span class="sxs-lookup"><span data-stu-id="84436-154">The types are qualified with the aliases.</span></span>

[!code-vb[VbVbalrStatements#155](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#155)]

[!code-vb[VbVbalrStatements#156](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#156)]

## <a name="example"></a><span data-ttu-id="84436-155">Příklad</span><span class="sxs-lookup"><span data-stu-id="84436-155">Example</span></span>

<span data-ttu-id="84436-156">The following example includes `Imports` statements that create aliases for the referenced types.</span><span class="sxs-lookup"><span data-stu-id="84436-156">The following example includes `Imports` statements that create aliases for the referenced types.</span></span> <span data-ttu-id="84436-157">Aliases are used to specify the types.</span><span class="sxs-lookup"><span data-stu-id="84436-157">Aliases are used to specify the types.</span></span>

[!code-vb[VbVbalrStatements#157](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#157)]

[!code-vb[VbVbalrStatements#158](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#158)]
  
## <a name="see-also"></a><span data-ttu-id="84436-158">Viz také:</span><span class="sxs-lookup"><span data-stu-id="84436-158">See also</span></span>

- [<span data-ttu-id="84436-159">Příkaz Namespace</span><span class="sxs-lookup"><span data-stu-id="84436-159">Namespace Statement</span></span>](namespace-statement.md)
- [<span data-ttu-id="84436-160">Namespaces in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="84436-160">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="84436-161">Odkazy a příkaz Imports</span><span class="sxs-lookup"><span data-stu-id="84436-161">References and the Imports Statement</span></span>](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="84436-162">Příkaz Imports (obor názvů XML)</span><span class="sxs-lookup"><span data-stu-id="84436-162">Imports Statement (XML Namespace)</span></span>](imports-statement-xml-namespace.md)
- [<span data-ttu-id="84436-163">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="84436-163">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
