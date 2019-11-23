---
title: Seznam atributů
ms.date: 07/20/2015
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
ms.openlocfilehash: f9332f52622551bb6b944242f71bd80f439982e9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354065"
---
# <a name="attribute-list-visual-basic"></a><span data-ttu-id="7232a-102">Seznam atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7232a-102">Attribute List (Visual Basic)</span></span>
<span data-ttu-id="7232a-103">Specifies the attributes to be applied to a declared programming element.</span><span class="sxs-lookup"><span data-stu-id="7232a-103">Specifies the attributes to be applied to a declared programming element.</span></span> <span data-ttu-id="7232a-104">Multiple attributes are separated by commas.</span><span class="sxs-lookup"><span data-stu-id="7232a-104">Multiple attributes are separated by commas.</span></span> <span data-ttu-id="7232a-105">Following is the syntax for one attribute.</span><span class="sxs-lookup"><span data-stu-id="7232a-105">Following is the syntax for one attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7232a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7232a-106">Syntax</span></span>  
  
```vb  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="7232a-107">Součásti</span><span class="sxs-lookup"><span data-stu-id="7232a-107">Parts</span></span>  
|||
|---|---|
|`attributemodifier`|<span data-ttu-id="7232a-108">Required for attributes applied at the beginning of a source file.</span><span class="sxs-lookup"><span data-stu-id="7232a-108">Required for attributes applied at the beginning of a source file.</span></span> <span data-ttu-id="7232a-109">Can be [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) or [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="7232a-109">Can be [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) or [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md).</span></span>|
|`attributename`| <span data-ttu-id="7232a-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="7232a-110">Required.</span></span> <span data-ttu-id="7232a-111">Name of the attribute.</span><span class="sxs-lookup"><span data-stu-id="7232a-111">Name of the attribute.</span></span>|
|`attributearguments`|<span data-ttu-id="7232a-112">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="7232a-112">Optional.</span></span> <span data-ttu-id="7232a-113">List of positional arguments for this attribute.</span><span class="sxs-lookup"><span data-stu-id="7232a-113">List of positional arguments for this attribute.</span></span> <span data-ttu-id="7232a-114">Multiple arguments are separated by commas.</span><span class="sxs-lookup"><span data-stu-id="7232a-114">Multiple arguments are separated by commas.</span></span>|
|`attributeinitializer`|<span data-ttu-id="7232a-115">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="7232a-115">Optional.</span></span> <span data-ttu-id="7232a-116">List of variable or property initializers for this attribute.</span><span class="sxs-lookup"><span data-stu-id="7232a-116">List of variable or property initializers for this attribute.</span></span> <span data-ttu-id="7232a-117">Multiple initializers are separated by commas.</span><span class="sxs-lookup"><span data-stu-id="7232a-117">Multiple initializers are separated by commas.</span></span>|
  
## <a name="remarks"></a><span data-ttu-id="7232a-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7232a-118">Remarks</span></span>  
 <span data-ttu-id="7232a-119">You can apply one or more attributes to nearly any programming element (types, procedures, properties, and so forth).</span><span class="sxs-lookup"><span data-stu-id="7232a-119">You can apply one or more attributes to nearly any programming element (types, procedures, properties, and so forth).</span></span> <span data-ttu-id="7232a-120">Attributes appear in your assembly's metadata, and they can help you annotate your code or specify how to use a particular programming element.</span><span class="sxs-lookup"><span data-stu-id="7232a-120">Attributes appear in your assembly's metadata, and they can help you annotate your code or specify how to use a particular programming element.</span></span> <span data-ttu-id="7232a-121">You can apply attributes defined by Visual Basic and the .NET Framework, and you can define your own attributes.</span><span class="sxs-lookup"><span data-stu-id="7232a-121">You can apply attributes defined by Visual Basic and the .NET Framework, and you can define your own attributes.</span></span>  

 <span data-ttu-id="7232a-122">For more information on when to use attributes, see [Attributes overview](../../../visual-basic/programming-guide/concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="7232a-122">For more information on when to use attributes, see [Attributes overview](../../../visual-basic/programming-guide/concepts/attributes/index.md).</span></span> <span data-ttu-id="7232a-123">For information on attribute names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="7232a-123">For information on attribute names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="7232a-124">Rules</span><span class="sxs-lookup"><span data-stu-id="7232a-124">Rules</span></span>  
  
- <span data-ttu-id="7232a-125">**Placement.**</span><span class="sxs-lookup"><span data-stu-id="7232a-125">**Placement.**</span></span> <span data-ttu-id="7232a-126">You can apply attributes to most declared programming elements.</span><span class="sxs-lookup"><span data-stu-id="7232a-126">You can apply attributes to most declared programming elements.</span></span> <span data-ttu-id="7232a-127">To apply one or more attributes, you place an *attribute block* at the beginning of the element declaration.</span><span class="sxs-lookup"><span data-stu-id="7232a-127">To apply one or more attributes, you place an *attribute block* at the beginning of the element declaration.</span></span> <span data-ttu-id="7232a-128">Each entry in the attribute list specifies an attribute you wish to apply, and the modifier and arguments you are using for this invocation of the attribute.</span><span class="sxs-lookup"><span data-stu-id="7232a-128">Each entry in the attribute list specifies an attribute you wish to apply, and the modifier and arguments you are using for this invocation of the attribute.</span></span>  
  
- <span data-ttu-id="7232a-129">**Angle Brackets.**</span><span class="sxs-lookup"><span data-stu-id="7232a-129">**Angle Brackets.**</span></span> <span data-ttu-id="7232a-130">If you supply an attribute list, you must enclose it in angle brackets ("`<`" and "`>`").</span><span class="sxs-lookup"><span data-stu-id="7232a-130">If you supply an attribute list, you must enclose it in angle brackets ("`<`" and "`>`").</span></span>  
  
- <span data-ttu-id="7232a-131">**Part of the Declaration.**</span><span class="sxs-lookup"><span data-stu-id="7232a-131">**Part of the Declaration.**</span></span> <span data-ttu-id="7232a-132">The attribute must be part of the element declaration, not a separate statement.</span><span class="sxs-lookup"><span data-stu-id="7232a-132">The attribute must be part of the element declaration, not a separate statement.</span></span> <span data-ttu-id="7232a-133">You can use the line-continuation sequence (" `_`") to extend the declaration statement onto multiple source-code lines.</span><span class="sxs-lookup"><span data-stu-id="7232a-133">You can use the line-continuation sequence (" `_`") to extend the declaration statement onto multiple source-code lines.</span></span>  
  
- <span data-ttu-id="7232a-134">**Modifiers.**</span><span class="sxs-lookup"><span data-stu-id="7232a-134">**Modifiers.**</span></span> <span data-ttu-id="7232a-135">An attribute modifier (`Assembly` or `Module`) is required on every attribute applied to a programming element at the beginning of a source file.</span><span class="sxs-lookup"><span data-stu-id="7232a-135">An attribute modifier (`Assembly` or `Module`) is required on every attribute applied to a programming element at the beginning of a source file.</span></span> <span data-ttu-id="7232a-136">Attribute modifiers are not allowed on attributes applied to elements that are not at the beginning of a source file.</span><span class="sxs-lookup"><span data-stu-id="7232a-136">Attribute modifiers are not allowed on attributes applied to elements that are not at the beginning of a source file.</span></span>  
  
- <span data-ttu-id="7232a-137">**Arguments.**</span><span class="sxs-lookup"><span data-stu-id="7232a-137">**Arguments.**</span></span> <span data-ttu-id="7232a-138">All positional arguments for an attribute must precede any variable or property initializers.</span><span class="sxs-lookup"><span data-stu-id="7232a-138">All positional arguments for an attribute must precede any variable or property initializers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7232a-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="7232a-139">Example</span></span>  
 <span data-ttu-id="7232a-140">The following example applies the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute to a skeleton definition of a `Function` procedure.</span><span class="sxs-lookup"><span data-stu-id="7232a-140">The following example applies the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute to a skeleton definition of a `Function` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]  
  
 <span data-ttu-id="7232a-141"><xref:System.Runtime.InteropServices.DllImportAttribute> indicates that the attributed procedure represents an entry point in an unmanaged dynamic-link library (DLL).</span><span class="sxs-lookup"><span data-stu-id="7232a-141"><xref:System.Runtime.InteropServices.DllImportAttribute> indicates that the attributed procedure represents an entry point in an unmanaged dynamic-link library (DLL).</span></span> <span data-ttu-id="7232a-142">The attribute supplies the DLL name as a positional argument and the other information as variable initializers.</span><span class="sxs-lookup"><span data-stu-id="7232a-142">The attribute supplies the DLL name as a positional argument and the other information as variable initializers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7232a-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7232a-143">See also</span></span>

- [<span data-ttu-id="7232a-144">Assembly</span><span class="sxs-lookup"><span data-stu-id="7232a-144">Assembly</span></span>](../../../visual-basic/language-reference/modifiers/assembly.md)
- [<span data-ttu-id="7232a-145">Module \<keyword></span><span class="sxs-lookup"><span data-stu-id="7232a-145">Module \<keyword></span></span>](../../../visual-basic/language-reference/modifiers/module-keyword.md)
- [<span data-ttu-id="7232a-146">Attributes overview</span><span class="sxs-lookup"><span data-stu-id="7232a-146">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="7232a-147">Postupy: Přerušení a kombinace příkazů v kódu</span><span class="sxs-lookup"><span data-stu-id="7232a-147">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
