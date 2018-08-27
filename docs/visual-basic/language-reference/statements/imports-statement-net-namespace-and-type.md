---
title: Imports – příkaz - Namespace .NET a typ (Visual Basic)
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
ms.openlocfilehash: 0211438e8b4c02fead910dd7a32e0df9ed73ddc5
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925595"
---
# <a name="imports-statement-net-namespace-and-type"></a><span data-ttu-id="17a40-102">Imports – příkaz (obor názvů a typ rozhraní .NET)</span><span class="sxs-lookup"><span data-stu-id="17a40-102">Imports Statement (.NET Namespace and Type)</span></span>
<span data-ttu-id="17a40-103">Umožňuje zadat názvy se nesmí odkazovat bez kvalifikace názvů.</span><span class="sxs-lookup"><span data-stu-id="17a40-103">Enables type names to be referenced without namespace qualification.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17a40-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17a40-104">Syntax</span></span>  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## <a name="parts"></a><span data-ttu-id="17a40-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="17a40-105">Parts</span></span>  
  
|<span data-ttu-id="17a40-106">Termín</span><span class="sxs-lookup"><span data-stu-id="17a40-106">Term</span></span>|<span data-ttu-id="17a40-107">Definice</span><span class="sxs-lookup"><span data-stu-id="17a40-107">Definition</span></span>|  
|---|---|  
|`aliasname`|<span data-ttu-id="17a40-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="17a40-108">Optional.</span></span> <span data-ttu-id="17a40-109">*Importovat alias* nebo název, pomocí kterého mohou kódu odkazovat na `namespace` místo úplné kvalifikace řetězce.</span><span class="sxs-lookup"><span data-stu-id="17a40-109">An *import alias* or name by which code can refer to `namespace` instead of the full qualification string.</span></span> <span data-ttu-id="17a40-110">Zobrazit [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="17a40-110">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`namespace`|<span data-ttu-id="17a40-111">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="17a40-111">Required.</span></span> <span data-ttu-id="17a40-112">Plně kvalifikovaný název oboru názvů importu.</span><span class="sxs-lookup"><span data-stu-id="17a40-112">The fully qualified name of the namespace being imported.</span></span> <span data-ttu-id="17a40-113">Mohou být řetězec s obory názvů vnořené na libovolné úrovni.</span><span class="sxs-lookup"><span data-stu-id="17a40-113">Can be a string of namespaces nested to any level.</span></span>|  
|`element`|<span data-ttu-id="17a40-114">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="17a40-114">Optional.</span></span> <span data-ttu-id="17a40-115">Název programovací element deklarovaný v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="17a40-115">The name of a programming element declared in the namespace.</span></span> <span data-ttu-id="17a40-116">Může být libovolný prvek kontejneru.</span><span class="sxs-lookup"><span data-stu-id="17a40-116">Can be any container element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17a40-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="17a40-117">Remarks</span></span>  
 <span data-ttu-id="17a40-118">`Imports` Příkaz umožňuje typy, které jsou obsaženy v daném oboru názvů se nesmí odkazovat přímo.</span><span class="sxs-lookup"><span data-stu-id="17a40-118">The `Imports`  statement enables types that are contained in a given namespace to be referenced directly.</span></span>  
  
 <span data-ttu-id="17a40-119">Můžete zadat název jednoho oboru názvů nebo řetězec vnořené obory názvů.</span><span class="sxs-lookup"><span data-stu-id="17a40-119">You can supply a single namespace name or a string of nested namespaces.</span></span> <span data-ttu-id="17a40-120">Každé vnořené oboru názvů je oddělen od další vyšší úroveň oboru názvů tečku (`.`), jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="17a40-120">Each nested namespace is separated from the next higher level namespace by a period (`.`), as the following example illustrates.</span></span>  
  
 `Imports System.Collections.Generic`  
  
 <span data-ttu-id="17a40-121">Každý zdrojový soubor může obsahovat libovolný počet `Imports` příkazy.</span><span class="sxs-lookup"><span data-stu-id="17a40-121">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="17a40-122">Tyto musí následovat deklarace všechny možnosti, jako `Option Strict` příkaz a musí předcházet jakékoli programovací element deklarace, jako například `Module` nebo `Class` příkazy.</span><span class="sxs-lookup"><span data-stu-id="17a40-122">These must follow any option declarations, such as the `Option Strict` statement, and they must precede any programming element declarations, such as `Module` or `Class` statements.</span></span>  
  
 <span data-ttu-id="17a40-123">Můžete použít `Imports` pouze na úrovni souborů.</span><span class="sxs-lookup"><span data-stu-id="17a40-123">You can use `Imports` only at file level.</span></span> <span data-ttu-id="17a40-124">To znamená, že kontext deklarace pro import musí být zdrojový soubor a nemůže být obor názvů, třídy, struktury, modulu, rozhraní, proceduru nebo blok.</span><span class="sxs-lookup"><span data-stu-id="17a40-124">This means the declaration context for importation must be a source file, and cannot be a namespace, class, structure, module, interface, procedure, or block.</span></span>  
  
 <span data-ttu-id="17a40-125">Všimněte si, `Imports` příkaz neprovede elementy z jiných projektů a sestavení k dispozici pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="17a40-125">Note that the `Imports` statement does not make elements from other projects and assemblies available to your project.</span></span> <span data-ttu-id="17a40-126">Import nepřijímá místo nastavení odkaz.</span><span class="sxs-lookup"><span data-stu-id="17a40-126">Importing does not take the place of setting a reference.</span></span> <span data-ttu-id="17a40-127">Odebere pouze potřeba kvalifikovat názvy, které jsou k dispozici pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="17a40-127">It only removes the need to qualify names that are already available to your project.</span></span> <span data-ttu-id="17a40-128">Další informace najdete v tématu "Import obsahující prvky" [odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="17a40-128">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17a40-129">Můžete definovat implicitní `Imports` příkazy pomocí [odkazy na stránky, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="17a40-129">You can define implicit `Imports` statements by using the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span> <span data-ttu-id="17a40-130">Další informace najdete v tématu [postupy: Přidání nebo odebrání importovaných oborů názvů (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="17a40-130">For more information, see [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>  
  
## <a name="import-aliases"></a><span data-ttu-id="17a40-131">Import aliasů</span><span class="sxs-lookup"><span data-stu-id="17a40-131">Import Aliases</span></span>  
 <span data-ttu-id="17a40-132">*Importovat alias* alias pro obor názvů nebo typ definuje.</span><span class="sxs-lookup"><span data-stu-id="17a40-132">An *import alias* defines the alias for a namespace or type.</span></span> <span data-ttu-id="17a40-133">Import aliasů jsou užitečné, pokud je třeba použít položky se stejným názvem, které jsou deklarovány v jedné nebo více oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="17a40-133">Import aliases are useful when you need to use items with the same name that are declared in one or more namespaces.</span></span> <span data-ttu-id="17a40-134">Další informace a příklad najdete v tématu "Kvalifikační Element Name" v [odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="17a40-134">For more information and an example, see "Qualifying an Element Name" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="17a40-135">By neměly deklarovat člena na úrovni modulu se stejným názvem jako `aliasname`.</span><span class="sxs-lookup"><span data-stu-id="17a40-135">You should not declare a member at module level with the same name as `aliasname`.</span></span> <span data-ttu-id="17a40-136">Pokud tak učiníte, kompilátor jazyka Visual Basic používá `aliasname` pouze pro deklarovaná členská a už se rozpozná jako alias importu.</span><span class="sxs-lookup"><span data-stu-id="17a40-136">If you do, the Visual Basic compiler uses `aliasname` only for the declared member and no longer recognizes it as an import alias.</span></span>  
  
 <span data-ttu-id="17a40-137">I když syntaxe pro deklarování aliasu importu se tímto způsobem používá pro import předponu oboru názvů XML, výsledky se liší.</span><span class="sxs-lookup"><span data-stu-id="17a40-137">Although the syntax used for declaring an import alias is like that used for importing an XML namespace prefix, the results are different.</span></span> <span data-ttu-id="17a40-138">Alias importu můžete použít jako výraz ve vašem kódu, zatímco předponu oboru názvů XML lze použít pouze v literály XML a vlastnosti OS XML jako předpona pro kvalifikovaný element nebo název atributu.</span><span class="sxs-lookup"><span data-stu-id="17a40-138">An import alias can be used as an expression in your code, whereas an XML namespace prefix can be used only in XML literals or XML axis properties as the prefix for a qualified element or attribute name.</span></span>  
  
### <a name="element-names"></a><span data-ttu-id="17a40-139">Názvy elementů</span><span class="sxs-lookup"><span data-stu-id="17a40-139">Element Names</span></span>  
 <span data-ttu-id="17a40-140">Pokud zadáte `element`, musí představovat *elementu kontejneru*, to znamená, že programový element, který může obsahovat další prvky.</span><span class="sxs-lookup"><span data-stu-id="17a40-140">If you supply `element`, it must represent a *container element*, that is, a programming element that can contain other elements.</span></span> <span data-ttu-id="17a40-141">Elementy kontejneru zahrnují třídy, struktury, moduly, rozhraní a výčty.</span><span class="sxs-lookup"><span data-stu-id="17a40-141">Container elements include classes, structures, modules, interfaces, and enumerations.</span></span>  
  
 <span data-ttu-id="17a40-142">Rozsah prvků, které jsou k dispozici ve `Imports` příkaz závisí na, jestli mají určovat `element`.</span><span class="sxs-lookup"><span data-stu-id="17a40-142">The scope of the elements made available by an `Imports` statement depends on whether you specify `element`.</span></span> <span data-ttu-id="17a40-143">Pokud zadáte pouze `namespace`, všechny jedinečné s názvem Členové tohoto oboru názvů a prvky kontejneru v daném oboru názvů, jsou k dispozici bez kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="17a40-143">If you specify only `namespace`, all uniquely named members of that namespace, and members of container elements within that namespace, are available without qualification.</span></span> <span data-ttu-id="17a40-144">Pokud zadáte obě `namespace` a `element`pouze členové tohoto prvku jsou k dispozici bez kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="17a40-144">If you specify both `namespace` and `element`, only the members of that element are available without qualification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17a40-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="17a40-145">Example</span></span>  
 <span data-ttu-id="17a40-146">Následující příklad vrátí všechny složky v adresáři C:\ s použitím <xref:System.IO.DirectoryInfo> třídy.</span><span class="sxs-lookup"><span data-stu-id="17a40-146">The following example returns all the folders in the C:\ directory by using the <xref:System.IO.DirectoryInfo> class.</span></span>  
  
 <span data-ttu-id="17a40-147">Kód nemá žádné `Imports` příkazů v horní části souboru.</span><span class="sxs-lookup"><span data-stu-id="17a40-147">The code has no `Imports` statements at the top of the file.</span></span> <span data-ttu-id="17a40-148">Proto `DirectoryInfo`, <xref:System.Text.StringBuilder>, a <xref:Microsoft.VisualBasic.ControlChars.CrLf> odkazy jsou všechny plně kvalifikovaný s obory názvů.</span><span class="sxs-lookup"><span data-stu-id="17a40-148">Therefore, the `DirectoryInfo`, <xref:System.Text.StringBuilder>, and <xref:Microsoft.VisualBasic.ControlChars.CrLf> references are all fully qualified with the namespaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#152](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="17a40-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="17a40-149">Example</span></span>  
 <span data-ttu-id="17a40-150">Následující příklad obsahuje `Imports` příkazy pro odkazované obory názvů.</span><span class="sxs-lookup"><span data-stu-id="17a40-150">The following example includes `Imports` statements for the referenced namespaces.</span></span> <span data-ttu-id="17a40-151">Typy proto nemusí být plně kvalifikovaný s obory názvů.</span><span class="sxs-lookup"><span data-stu-id="17a40-151">Therefore, the types do not have to be fully qualified with the namespaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#153](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_2.vb)]  
  
 [!code-vb[VbVbalrStatements#154](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="17a40-152">Příklad</span><span class="sxs-lookup"><span data-stu-id="17a40-152">Example</span></span>  
 <span data-ttu-id="17a40-153">Následující příklad obsahuje `Imports` příkazy, které vytvořit aliasy pro odkazované obory názvů.</span><span class="sxs-lookup"><span data-stu-id="17a40-153">The following example includes `Imports` statements that create aliases for the referenced namespaces.</span></span> <span data-ttu-id="17a40-154">Typy jsou kvalifikované aliasy.</span><span class="sxs-lookup"><span data-stu-id="17a40-154">The types are qualified with the aliases.</span></span>  
  
 [!code-vb[VbVbalrStatements#155](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_4.vb)]  
  
 [!code-vb[VbVbalrStatements#156](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_5.vb)]  
  
## <a name="example"></a><span data-ttu-id="17a40-155">Příklad</span><span class="sxs-lookup"><span data-stu-id="17a40-155">Example</span></span>  
 <span data-ttu-id="17a40-156">Následující příklad obsahuje `Imports` příkazy, které vytvořit aliasy pro odkazované typy.</span><span class="sxs-lookup"><span data-stu-id="17a40-156">The following example includes `Imports` statements that create aliases for the referenced types.</span></span> <span data-ttu-id="17a40-157">Aliasy slouží k určení typů.</span><span class="sxs-lookup"><span data-stu-id="17a40-157">Aliases are used to specify the types.</span></span>  
  
 [!code-vb[VbVbalrStatements#157](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_6.vb)]  
  
 [!code-vb[VbVbalrStatements#158](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_7.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="17a40-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="17a40-158">See Also</span></span>  
 [<span data-ttu-id="17a40-159">Příkaz Namespace</span><span class="sxs-lookup"><span data-stu-id="17a40-159">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [<span data-ttu-id="17a40-160">Obory názvů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="17a40-160">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="17a40-161">Odkazy a příkaz Imports</span><span class="sxs-lookup"><span data-stu-id="17a40-161">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [<span data-ttu-id="17a40-162">Příkaz Imports (obor názvů XML)</span><span class="sxs-lookup"><span data-stu-id="17a40-162">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)  
 [<span data-ttu-id="17a40-163">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="17a40-163">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
