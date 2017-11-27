---
title: "Imports – příkaz (obor názvů a typ rozhraní .NET)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "40"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 46cc78c2fd039fb56fd4d1b797f2d09cbe95d317
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imports-statement-net-namespace-and-type"></a><span data-ttu-id="ac703-102">Imports – příkaz (obor názvů a typ rozhraní .NET)</span><span class="sxs-lookup"><span data-stu-id="ac703-102">Imports Statement (.NET Namespace and Type)</span></span>
<span data-ttu-id="ac703-103">Umožňuje zadat názvy bude odkazovat bez kvalifikace názvů.</span><span class="sxs-lookup"><span data-stu-id="ac703-103">Enables type names to be referenced without namespace qualification.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac703-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac703-104">Syntax</span></span>  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## <a name="parts"></a><span data-ttu-id="ac703-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="ac703-105">Parts</span></span>  
  
|<span data-ttu-id="ac703-106">Termín</span><span class="sxs-lookup"><span data-stu-id="ac703-106">Term</span></span>|<span data-ttu-id="ac703-107">Definice</span><span class="sxs-lookup"><span data-stu-id="ac703-107">Definition</span></span>|  
|---|---|  
|`aliasname`|<span data-ttu-id="ac703-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="ac703-108">Optional.</span></span> <span data-ttu-id="ac703-109">*Importovat alias* nebo název, pomocí kterého může kódu odkazovat na `namespace` místo úplné kvalifikace řetězec.</span><span class="sxs-lookup"><span data-stu-id="ac703-109">An *import alias* or name by which code can refer to `namespace` instead of the full qualification string.</span></span> <span data-ttu-id="ac703-110">V tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="ac703-110">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`namespace`|<span data-ttu-id="ac703-111">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="ac703-111">Required.</span></span> <span data-ttu-id="ac703-112">Plně kvalifikovaný název oboru názvů importována.</span><span class="sxs-lookup"><span data-stu-id="ac703-112">The fully qualified name of the namespace being imported.</span></span> <span data-ttu-id="ac703-113">Mohou být řetězec o délce obory názvů vnořené na libovolnou úroveň.</span><span class="sxs-lookup"><span data-stu-id="ac703-113">Can be a string of namespaces nested to any level.</span></span>|  
|`element`|<span data-ttu-id="ac703-114">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="ac703-114">Optional.</span></span> <span data-ttu-id="ac703-115">Název programovací element deklarované v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ac703-115">The name of a programming element declared in the namespace.</span></span> <span data-ttu-id="ac703-116">Může být libovolný element kontejneru.</span><span class="sxs-lookup"><span data-stu-id="ac703-116">Can be any container element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac703-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ac703-117">Remarks</span></span>  
 <span data-ttu-id="ac703-118">`Imports` Příkaz umožňuje typy, které jsou obsaženy v daném oboru názvů bude odkazovat přímo.</span><span class="sxs-lookup"><span data-stu-id="ac703-118">The `Imports`  statement enables types that are contained in a given namespace to be referenced directly.</span></span>  
  
 <span data-ttu-id="ac703-119">Můžete zadat název jednoho oboru názvů nebo řetězec vnořené obory názvů.</span><span class="sxs-lookup"><span data-stu-id="ac703-119">You can supply a single namespace name or a string of nested namespaces.</span></span> <span data-ttu-id="ac703-120">Každý vnořené obor názvů je oddělená od další vyšší úrovni oboru názvů tečkou (`.`), jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="ac703-120">Each nested namespace is separated from the next higher level namespace by a period (`.`), as the following example illustrates.</span></span>  
  
 `Imports System.Collections.Generic`  
  
 <span data-ttu-id="ac703-121">Každý zdrojový soubor může obsahovat libovolný počet `Imports` příkazy.</span><span class="sxs-lookup"><span data-stu-id="ac703-121">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="ac703-122">Tyto postupujte deklarace všechny možnosti, jako `Option Strict` příkaz a musí předcházet jakékoli programovací element deklarace, jako například `Module` nebo `Class` příkazy.</span><span class="sxs-lookup"><span data-stu-id="ac703-122">These must follow any option declarations, such as the `Option Strict` statement, and they must precede any programming element declarations, such as `Module` or `Class` statements.</span></span>  
  
 <span data-ttu-id="ac703-123">Můžete použít `Imports` pouze na úrovni souborů.</span><span class="sxs-lookup"><span data-stu-id="ac703-123">You can use `Imports` only at file level.</span></span> <span data-ttu-id="ac703-124">To znamená kontext deklarace pro import musí být zdrojový soubor a nemůže být obor názvů, třídy, struktury, modulu, rozhraní, postup nebo bloku.</span><span class="sxs-lookup"><span data-stu-id="ac703-124">This means the declaration context for importation must be a source file, and cannot be a namespace, class, structure, module, interface, procedure, or block.</span></span>  
  
 <span data-ttu-id="ac703-125">Všimněte si, že `Imports` příkaz zpřístupnění elementy z jiných projekty a sestavení do projektu.</span><span class="sxs-lookup"><span data-stu-id="ac703-125">Note that the `Imports` statement does not make elements from other projects and assemblies available to your project.</span></span> <span data-ttu-id="ac703-126">Import nevyžaduje místní nastavení odkaz.</span><span class="sxs-lookup"><span data-stu-id="ac703-126">Importing does not take the place of setting a reference.</span></span> <span data-ttu-id="ac703-127">Pouze eliminuje nutnost ke kvalifikaci názvy, které jsou již k dispozici do projektu.</span><span class="sxs-lookup"><span data-stu-id="ac703-127">It only removes the need to qualify names that are already available to your project.</span></span> <span data-ttu-id="ac703-128">Další informace najdete v tématu "Import obsahující prvků" v [odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="ac703-128">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac703-129">Můžete definovat implicitní `Imports` příkazy pomocí [stránka odkazy, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="ac703-129">You can define implicit `Imports` statements by using the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span> <span data-ttu-id="ac703-130">Další informace najdete v tématu [postupy: Přidání nebo odebrání importovaných oborů názvů (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="ac703-130">For more information, see [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>  
  
## <a name="import-aliases"></a><span data-ttu-id="ac703-131">Import aliasů</span><span class="sxs-lookup"><span data-stu-id="ac703-131">Import Aliases</span></span>  
 <span data-ttu-id="ac703-132">*Importovat alias* definuje alias oboru názvů nebo typu.</span><span class="sxs-lookup"><span data-stu-id="ac703-132">An *import alias* defines the alias for a namespace or type.</span></span> <span data-ttu-id="ac703-133">Import aliasů jsou užitečné, když potřebujete použití položek se stejným názvem, které jsou deklarované v jedné nebo více oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="ac703-133">Import aliases are useful when you need to use items with the same name that are declared in one or more namespaces.</span></span> <span data-ttu-id="ac703-134">Další informace a příklad najdete v tématu "Kvalifikující elementu název" v [odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="ac703-134">For more information and an example, see "Qualifying an Element Name" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="ac703-135">Nesmí deklarovat člena na úrovni modulu se stejným názvem jako `aliasname`.</span><span class="sxs-lookup"><span data-stu-id="ac703-135">You should not declare a member at module level with the same name as `aliasname`.</span></span> <span data-ttu-id="ac703-136">Pokud tak učiníte, Visual Basic – kompilátor používá `aliasname` pouze pro deklarované člena a už se rozpozná jako alias importu.</span><span class="sxs-lookup"><span data-stu-id="ac703-136">If you do, the Visual Basic compiler uses `aliasname` only for the declared member and no longer recognizes it as an import alias.</span></span>  
  
 <span data-ttu-id="ac703-137">I když syntaxe pro deklarování import alias se používá jako je například pro import předponu oboru názvů XML, výsledky se liší.</span><span class="sxs-lookup"><span data-stu-id="ac703-137">Although the syntax used for declaring an import alias is like that used for importing an XML namespace prefix, the results are different.</span></span> <span data-ttu-id="ac703-138">Import alias můžete použít jako výraz ve vašem kódu, zatímco předponu oboru názvů XML lze použít pouze v literálech XML nebo vlastnosti osy XML jako předpona pro kvalifikované element nebo atribut name.</span><span class="sxs-lookup"><span data-stu-id="ac703-138">An import alias can be used as an expression in your code, whereas an XML namespace prefix can be used only in XML literals or XML axis properties as the prefix for a qualified element or attribute name.</span></span>  
  
### <a name="element-names"></a><span data-ttu-id="ac703-139">Názvy elementů</span><span class="sxs-lookup"><span data-stu-id="ac703-139">Element Names</span></span>  
 <span data-ttu-id="ac703-140">Pokud zadáte `element`, musí představovat *kontejnerový element*, který je programovací element, který může obsahovat další prvky.</span><span class="sxs-lookup"><span data-stu-id="ac703-140">If you supply `element`, it must represent a *container element*, that is, a programming element that can contain other elements.</span></span> <span data-ttu-id="ac703-141">Elementy kontejneru zahrnují třídy, struktury, moduly, rozhraní a výčty.</span><span class="sxs-lookup"><span data-stu-id="ac703-141">Container elements include classes, structures, modules, interfaces, and enumerations.</span></span>  
  
 <span data-ttu-id="ac703-142">Rozsah elementy, které poskytují `Imports` příkaz závisí na tom, jestli je zadat `element`.</span><span class="sxs-lookup"><span data-stu-id="ac703-142">The scope of the elements made available by an `Imports` statement depends on whether you specify `element`.</span></span> <span data-ttu-id="ac703-143">Pokud zadáte pouze `namespace`, všechny jednoznačně s názvem Členové tento obor názvů a elementy kontejneru v daném oboru názvů, jsou k dispozici bez kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="ac703-143">If you specify only `namespace`, all uniquely named members of that namespace, and members of container elements within that namespace, are available without qualification.</span></span> <span data-ttu-id="ac703-144">Pokud zadáte oba `namespace` a `element`jen členové tohoto elementu jsou k dispozici bez kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="ac703-144">If you specify both `namespace` and `element`, only the members of that element are available without qualification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac703-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="ac703-145">Example</span></span>  
 <span data-ttu-id="ac703-146">Následující příklad vrátí všechny složky v adresáři C:\ pomocí <xref:System.IO.DirectoryInfo> třídy.</span><span class="sxs-lookup"><span data-stu-id="ac703-146">The following example returns all the folders in the C:\ directory by using the <xref:System.IO.DirectoryInfo> class.</span></span>  
  
 <span data-ttu-id="ac703-147">Kód neobsahuje žádné `Imports` příkazy v horní části souboru.</span><span class="sxs-lookup"><span data-stu-id="ac703-147">The code has no `Imports` statements at the top of the file.</span></span> <span data-ttu-id="ac703-148">Proto `DirectoryInfo`, <xref:System.Text.StringBuilder>, a <xref:Microsoft.VisualBasic.ControlChars.CrLf> jsou odkazy na všechny plně kvalifikovaný s obory názvů.</span><span class="sxs-lookup"><span data-stu-id="ac703-148">Therefore, the `DirectoryInfo`, <xref:System.Text.StringBuilder>, and <xref:Microsoft.VisualBasic.ControlChars.CrLf> references are all fully qualified with the namespaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#152](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="ac703-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="ac703-149">Example</span></span>  
 <span data-ttu-id="ac703-150">Následující příklad obsahuje `Imports` příkazy pro odkazované obory názvů.</span><span class="sxs-lookup"><span data-stu-id="ac703-150">The following example includes `Imports` statements for the referenced namespaces.</span></span> <span data-ttu-id="ac703-151">Typy proto nemusí být plně kvalifikovaná s obory názvů.</span><span class="sxs-lookup"><span data-stu-id="ac703-151">Therefore, the types do not have to be fully qualified with the namespaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#153](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_2.vb)]  
  
 [!code-vb[VbVbalrStatements#154](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="ac703-152">Příklad</span><span class="sxs-lookup"><span data-stu-id="ac703-152">Example</span></span>  
 <span data-ttu-id="ac703-153">Následující příklad obsahuje `Imports` příkazy, které vytvořit aliasy pro odkazované obory názvů.</span><span class="sxs-lookup"><span data-stu-id="ac703-153">The following example includes `Imports` statements that create aliases for the referenced namespaces.</span></span> <span data-ttu-id="ac703-154">Typy jsou kvalifikovaný s aliasy.</span><span class="sxs-lookup"><span data-stu-id="ac703-154">The types are qualified with the aliases.</span></span>  
  
 [!code-vb[VbVbalrStatements#155](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_4.vb)]  
  
 [!code-vb[VbVbalrStatements#156](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_5.vb)]  
  
## <a name="example"></a><span data-ttu-id="ac703-155">Příklad</span><span class="sxs-lookup"><span data-stu-id="ac703-155">Example</span></span>  
 <span data-ttu-id="ac703-156">Následující příklad obsahuje `Imports` příkazy, které vytvořit aliasy pro odkazované typy.</span><span class="sxs-lookup"><span data-stu-id="ac703-156">The following example includes `Imports` statements that create aliases for the referenced types.</span></span> <span data-ttu-id="ac703-157">Aliasy slouží k určení typů.</span><span class="sxs-lookup"><span data-stu-id="ac703-157">Aliases are used to specify the types.</span></span>  
  
 [!code-vb[VbVbalrStatements#157](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_6.vb)]  
  
 [!code-vb[VbVbalrStatements#158](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_7.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ac703-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="ac703-158">See Also</span></span>  
 [<span data-ttu-id="ac703-159">Namespace – příkaz</span><span class="sxs-lookup"><span data-stu-id="ac703-159">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [<span data-ttu-id="ac703-160">Obory názvů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ac703-160">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="ac703-161">Odkazy a příkaz Imports</span><span class="sxs-lookup"><span data-stu-id="ac703-161">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [<span data-ttu-id="ac703-162">Imports – příkaz (Namespace XML)</span><span class="sxs-lookup"><span data-stu-id="ac703-162">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)  
 [<span data-ttu-id="ac703-163">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="ac703-163">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
