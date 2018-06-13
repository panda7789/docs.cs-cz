---
title: Imports – příkaz (obor názvů a typ rozhraní .NET)
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
ms.openlocfilehash: ef569b0ed6428d24d019e00c500e4d4b91c83d49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604481"
---
# <a name="imports-statement-net-namespace-and-type"></a><span data-ttu-id="f74aa-102">Imports – příkaz (obor názvů a typ rozhraní .NET)</span><span class="sxs-lookup"><span data-stu-id="f74aa-102">Imports Statement (.NET Namespace and Type)</span></span>
<span data-ttu-id="f74aa-103">Umožňuje zadat názvy bude odkazovat bez kvalifikace názvů.</span><span class="sxs-lookup"><span data-stu-id="f74aa-103">Enables type names to be referenced without namespace qualification.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f74aa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f74aa-104">Syntax</span></span>  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## <a name="parts"></a><span data-ttu-id="f74aa-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="f74aa-105">Parts</span></span>  
  
|<span data-ttu-id="f74aa-106">Termín</span><span class="sxs-lookup"><span data-stu-id="f74aa-106">Term</span></span>|<span data-ttu-id="f74aa-107">Definice</span><span class="sxs-lookup"><span data-stu-id="f74aa-107">Definition</span></span>|  
|---|---|  
|`aliasname`|<span data-ttu-id="f74aa-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f74aa-108">Optional.</span></span> <span data-ttu-id="f74aa-109">*Importovat alias* nebo název, pomocí kterého může kódu odkazovat na `namespace` místo úplné kvalifikace řetězec.</span><span class="sxs-lookup"><span data-stu-id="f74aa-109">An *import alias* or name by which code can refer to `namespace` instead of the full qualification string.</span></span> <span data-ttu-id="f74aa-110">V tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="f74aa-110">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`namespace`|<span data-ttu-id="f74aa-111">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="f74aa-111">Required.</span></span> <span data-ttu-id="f74aa-112">Plně kvalifikovaný název oboru názvů importována.</span><span class="sxs-lookup"><span data-stu-id="f74aa-112">The fully qualified name of the namespace being imported.</span></span> <span data-ttu-id="f74aa-113">Mohou být řetězec o délce obory názvů vnořené na libovolnou úroveň.</span><span class="sxs-lookup"><span data-stu-id="f74aa-113">Can be a string of namespaces nested to any level.</span></span>|  
|`element`|<span data-ttu-id="f74aa-114">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f74aa-114">Optional.</span></span> <span data-ttu-id="f74aa-115">Název programovací element deklarované v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="f74aa-115">The name of a programming element declared in the namespace.</span></span> <span data-ttu-id="f74aa-116">Může být libovolný element kontejneru.</span><span class="sxs-lookup"><span data-stu-id="f74aa-116">Can be any container element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f74aa-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f74aa-117">Remarks</span></span>  
 <span data-ttu-id="f74aa-118">`Imports` Příkaz umožňuje typy, které jsou obsaženy v daném oboru názvů bude odkazovat přímo.</span><span class="sxs-lookup"><span data-stu-id="f74aa-118">The `Imports`  statement enables types that are contained in a given namespace to be referenced directly.</span></span>  
  
 <span data-ttu-id="f74aa-119">Můžete zadat název jednoho oboru názvů nebo řetězec vnořené obory názvů.</span><span class="sxs-lookup"><span data-stu-id="f74aa-119">You can supply a single namespace name or a string of nested namespaces.</span></span> <span data-ttu-id="f74aa-120">Každý vnořené obor názvů je oddělená od další vyšší úrovni oboru názvů tečkou (`.`), jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="f74aa-120">Each nested namespace is separated from the next higher level namespace by a period (`.`), as the following example illustrates.</span></span>  
  
 `Imports System.Collections.Generic`  
  
 <span data-ttu-id="f74aa-121">Každý zdrojový soubor může obsahovat libovolný počet `Imports` příkazy.</span><span class="sxs-lookup"><span data-stu-id="f74aa-121">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="f74aa-122">Tyto postupujte deklarace všechny možnosti, jako `Option Strict` příkaz a musí předcházet jakékoli programovací element deklarace, jako například `Module` nebo `Class` příkazy.</span><span class="sxs-lookup"><span data-stu-id="f74aa-122">These must follow any option declarations, such as the `Option Strict` statement, and they must precede any programming element declarations, such as `Module` or `Class` statements.</span></span>  
  
 <span data-ttu-id="f74aa-123">Můžete použít `Imports` pouze na úrovni souborů.</span><span class="sxs-lookup"><span data-stu-id="f74aa-123">You can use `Imports` only at file level.</span></span> <span data-ttu-id="f74aa-124">To znamená kontext deklarace pro import musí být zdrojový soubor a nemůže být obor názvů, třídy, struktury, modulu, rozhraní, postup nebo bloku.</span><span class="sxs-lookup"><span data-stu-id="f74aa-124">This means the declaration context for importation must be a source file, and cannot be a namespace, class, structure, module, interface, procedure, or block.</span></span>  
  
 <span data-ttu-id="f74aa-125">Všimněte si, že `Imports` příkaz zpřístupnění elementy z jiných projekty a sestavení do projektu.</span><span class="sxs-lookup"><span data-stu-id="f74aa-125">Note that the `Imports` statement does not make elements from other projects and assemblies available to your project.</span></span> <span data-ttu-id="f74aa-126">Import nevyžaduje místní nastavení odkaz.</span><span class="sxs-lookup"><span data-stu-id="f74aa-126">Importing does not take the place of setting a reference.</span></span> <span data-ttu-id="f74aa-127">Pouze eliminuje nutnost ke kvalifikaci názvy, které jsou již k dispozici do projektu.</span><span class="sxs-lookup"><span data-stu-id="f74aa-127">It only removes the need to qualify names that are already available to your project.</span></span> <span data-ttu-id="f74aa-128">Další informace najdete v tématu "Import obsahující prvků" v [odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="f74aa-128">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f74aa-129">Můžete definovat implicitní `Imports` příkazy pomocí [stránka odkazy, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="f74aa-129">You can define implicit `Imports` statements by using the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span> <span data-ttu-id="f74aa-130">Další informace najdete v tématu [postupy: Přidání nebo odebrání importovaných oborů názvů (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="f74aa-130">For more information, see [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>  
  
## <a name="import-aliases"></a><span data-ttu-id="f74aa-131">Import aliasů</span><span class="sxs-lookup"><span data-stu-id="f74aa-131">Import Aliases</span></span>  
 <span data-ttu-id="f74aa-132">*Importovat alias* definuje alias oboru názvů nebo typu.</span><span class="sxs-lookup"><span data-stu-id="f74aa-132">An *import alias* defines the alias for a namespace or type.</span></span> <span data-ttu-id="f74aa-133">Import aliasů jsou užitečné, když potřebujete použití položek se stejným názvem, které jsou deklarované v jedné nebo více oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="f74aa-133">Import aliases are useful when you need to use items with the same name that are declared in one or more namespaces.</span></span> <span data-ttu-id="f74aa-134">Další informace a příklad najdete v tématu "Kvalifikující elementu název" v [odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="f74aa-134">For more information and an example, see "Qualifying an Element Name" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="f74aa-135">Nesmí deklarovat člena na úrovni modulu se stejným názvem jako `aliasname`.</span><span class="sxs-lookup"><span data-stu-id="f74aa-135">You should not declare a member at module level with the same name as `aliasname`.</span></span> <span data-ttu-id="f74aa-136">Pokud tak učiníte, Visual Basic – kompilátor používá `aliasname` pouze pro deklarované člena a už se rozpozná jako alias importu.</span><span class="sxs-lookup"><span data-stu-id="f74aa-136">If you do, the Visual Basic compiler uses `aliasname` only for the declared member and no longer recognizes it as an import alias.</span></span>  
  
 <span data-ttu-id="f74aa-137">I když syntaxe pro deklarování import alias se používá jako je například pro import předponu oboru názvů XML, výsledky se liší.</span><span class="sxs-lookup"><span data-stu-id="f74aa-137">Although the syntax used for declaring an import alias is like that used for importing an XML namespace prefix, the results are different.</span></span> <span data-ttu-id="f74aa-138">Import alias můžete použít jako výraz ve vašem kódu, zatímco předponu oboru názvů XML lze použít pouze v literálech XML nebo vlastnosti osy XML jako předpona pro kvalifikované element nebo atribut name.</span><span class="sxs-lookup"><span data-stu-id="f74aa-138">An import alias can be used as an expression in your code, whereas an XML namespace prefix can be used only in XML literals or XML axis properties as the prefix for a qualified element or attribute name.</span></span>  
  
### <a name="element-names"></a><span data-ttu-id="f74aa-139">Názvy elementů</span><span class="sxs-lookup"><span data-stu-id="f74aa-139">Element Names</span></span>  
 <span data-ttu-id="f74aa-140">Pokud zadáte `element`, musí představovat *kontejnerový element*, který je programovací element, který může obsahovat další prvky.</span><span class="sxs-lookup"><span data-stu-id="f74aa-140">If you supply `element`, it must represent a *container element*, that is, a programming element that can contain other elements.</span></span> <span data-ttu-id="f74aa-141">Elementy kontejneru zahrnují třídy, struktury, moduly, rozhraní a výčty.</span><span class="sxs-lookup"><span data-stu-id="f74aa-141">Container elements include classes, structures, modules, interfaces, and enumerations.</span></span>  
  
 <span data-ttu-id="f74aa-142">Rozsah elementy, které poskytují `Imports` příkaz závisí na tom, jestli je zadat `element`.</span><span class="sxs-lookup"><span data-stu-id="f74aa-142">The scope of the elements made available by an `Imports` statement depends on whether you specify `element`.</span></span> <span data-ttu-id="f74aa-143">Pokud zadáte pouze `namespace`, všechny jednoznačně s názvem Členové tento obor názvů a elementy kontejneru v daném oboru názvů, jsou k dispozici bez kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="f74aa-143">If you specify only `namespace`, all uniquely named members of that namespace, and members of container elements within that namespace, are available without qualification.</span></span> <span data-ttu-id="f74aa-144">Pokud zadáte oba `namespace` a `element`jen členové tohoto elementu jsou k dispozici bez kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="f74aa-144">If you specify both `namespace` and `element`, only the members of that element are available without qualification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f74aa-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="f74aa-145">Example</span></span>  
 <span data-ttu-id="f74aa-146">Následující příklad vrátí všechny složky v adresáři C:\ pomocí <xref:System.IO.DirectoryInfo> třídy.</span><span class="sxs-lookup"><span data-stu-id="f74aa-146">The following example returns all the folders in the C:\ directory by using the <xref:System.IO.DirectoryInfo> class.</span></span>  
  
 <span data-ttu-id="f74aa-147">Kód neobsahuje žádné `Imports` příkazy v horní části souboru.</span><span class="sxs-lookup"><span data-stu-id="f74aa-147">The code has no `Imports` statements at the top of the file.</span></span> <span data-ttu-id="f74aa-148">Proto `DirectoryInfo`, <xref:System.Text.StringBuilder>, a <xref:Microsoft.VisualBasic.ControlChars.CrLf> jsou odkazy na všechny plně kvalifikovaný s obory názvů.</span><span class="sxs-lookup"><span data-stu-id="f74aa-148">Therefore, the `DirectoryInfo`, <xref:System.Text.StringBuilder>, and <xref:Microsoft.VisualBasic.ControlChars.CrLf> references are all fully qualified with the namespaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#152](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="f74aa-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="f74aa-149">Example</span></span>  
 <span data-ttu-id="f74aa-150">Následující příklad obsahuje `Imports` příkazy pro odkazované obory názvů.</span><span class="sxs-lookup"><span data-stu-id="f74aa-150">The following example includes `Imports` statements for the referenced namespaces.</span></span> <span data-ttu-id="f74aa-151">Typy proto nemusí být plně kvalifikovaná s obory názvů.</span><span class="sxs-lookup"><span data-stu-id="f74aa-151">Therefore, the types do not have to be fully qualified with the namespaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#153](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_2.vb)]  
  
 [!code-vb[VbVbalrStatements#154](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="f74aa-152">Příklad</span><span class="sxs-lookup"><span data-stu-id="f74aa-152">Example</span></span>  
 <span data-ttu-id="f74aa-153">Následující příklad obsahuje `Imports` příkazy, které vytvořit aliasy pro odkazované obory názvů.</span><span class="sxs-lookup"><span data-stu-id="f74aa-153">The following example includes `Imports` statements that create aliases for the referenced namespaces.</span></span> <span data-ttu-id="f74aa-154">Typy jsou kvalifikovaný s aliasy.</span><span class="sxs-lookup"><span data-stu-id="f74aa-154">The types are qualified with the aliases.</span></span>  
  
 [!code-vb[VbVbalrStatements#155](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_4.vb)]  
  
 [!code-vb[VbVbalrStatements#156](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_5.vb)]  
  
## <a name="example"></a><span data-ttu-id="f74aa-155">Příklad</span><span class="sxs-lookup"><span data-stu-id="f74aa-155">Example</span></span>  
 <span data-ttu-id="f74aa-156">Následující příklad obsahuje `Imports` příkazy, které vytvořit aliasy pro odkazované typy.</span><span class="sxs-lookup"><span data-stu-id="f74aa-156">The following example includes `Imports` statements that create aliases for the referenced types.</span></span> <span data-ttu-id="f74aa-157">Aliasy slouží k určení typů.</span><span class="sxs-lookup"><span data-stu-id="f74aa-157">Aliases are used to specify the types.</span></span>  
  
 [!code-vb[VbVbalrStatements#157](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_6.vb)]  
  
 [!code-vb[VbVbalrStatements#158](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_7.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f74aa-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="f74aa-158">See Also</span></span>  
 [<span data-ttu-id="f74aa-159">Příkaz Namespace</span><span class="sxs-lookup"><span data-stu-id="f74aa-159">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [<span data-ttu-id="f74aa-160">Obory názvů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f74aa-160">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="f74aa-161">Odkazy a příkaz Imports</span><span class="sxs-lookup"><span data-stu-id="f74aa-161">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [<span data-ttu-id="f74aa-162">Příkaz Imports (obor názvů XML)</span><span class="sxs-lookup"><span data-stu-id="f74aa-162">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)  
 [<span data-ttu-id="f74aa-163">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="f74aa-163">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
