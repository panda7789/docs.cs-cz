---
title: Příkaz Imports – obor názvů a typ .NET
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
# <a name="imports-statement-net-namespace-and-type"></a><span data-ttu-id="ef2f1-102">Imports – příkaz (obor názvů a typ rozhraní .NET)</span><span class="sxs-lookup"><span data-stu-id="ef2f1-102">Imports Statement (.NET Namespace and Type)</span></span>

<span data-ttu-id="ef2f1-103">Povoluje odkazování na názvy typů bez kvalifikace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-103">Enables type names to be referenced without namespace qualification.</span></span>

## <a name="syntax"></a><span data-ttu-id="ef2f1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef2f1-104">Syntax</span></span>

```vb
Imports [ aliasname = ] namespace
' -or-
Imports [ aliasname = ] namespace.element
```

## <a name="parts"></a><span data-ttu-id="ef2f1-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="ef2f1-105">Parts</span></span>

|<span data-ttu-id="ef2f1-106">Termín</span><span class="sxs-lookup"><span data-stu-id="ef2f1-106">Term</span></span>|<span data-ttu-id="ef2f1-107">Definice</span><span class="sxs-lookup"><span data-stu-id="ef2f1-107">Definition</span></span>|
|---|---|
|`aliasname`|<span data-ttu-id="ef2f1-108">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-108">Optional.</span></span> <span data-ttu-id="ef2f1-109">Alias nebo název *importu* , pomocí kterého může kód odkazovat `namespace` místo úplného řetězce kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-109">An *import alias* or name by which code can refer to `namespace` instead of the full qualification string.</span></span> <span data-ttu-id="ef2f1-110">Viz [deklarované názvy elementů](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="ef2f1-110">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
|`namespace`|<span data-ttu-id="ef2f1-111">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-111">Required.</span></span> <span data-ttu-id="ef2f1-112">Plně kvalifikovaný název oboru názvů, který se má importovat</span><span class="sxs-lookup"><span data-stu-id="ef2f1-112">The fully qualified name of the namespace being imported.</span></span> <span data-ttu-id="ef2f1-113">Může to být řetězec oborů názvů vnořený do libovolné úrovně.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-113">Can be a string of namespaces nested to any level.</span></span>|
|`element`|<span data-ttu-id="ef2f1-114">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-114">Optional.</span></span> <span data-ttu-id="ef2f1-115">Název programovacího prvku deklarovaného v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-115">The name of a programming element declared in the namespace.</span></span> <span data-ttu-id="ef2f1-116">Může to být libovolný element kontejneru.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-116">Can be any container element.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ef2f1-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ef2f1-117">Remarks</span></span>

<span data-ttu-id="ef2f1-118">Příkaz `Imports` umožňuje, aby typy, které jsou obsaženy v daném oboru názvů, odkazovaly přímo.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-118">The `Imports` statement enables types that are contained in a given namespace to be referenced directly.</span></span>

<span data-ttu-id="ef2f1-119">Můžete dodat jeden název oboru názvů nebo řetězec pro vnořené obory názvů.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-119">You can supply a single namespace name or a string of nested namespaces.</span></span> <span data-ttu-id="ef2f1-120">Každý vnořený obor názvů je oddělený od dalšího oboru názvů vyšší úrovně o periodě (`.`), jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="ef2f1-120">Each nested namespace is separated from the next higher level namespace by a period (`.`), as the following example illustrates:</span></span>

```vb
Imports System.Collections.Generic
```

<span data-ttu-id="ef2f1-121">Každý zdrojový soubor může obsahovat libovolný počet příkazů `Imports`.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-121">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="ef2f1-122">Ty musí splňovat jakékoli deklarace možností, jako je například příkaz `Option Strict`, a musí předcházet deklaraci všech programovacích prvků, jako jsou například `Module` nebo `Class` příkazy.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-122">These must follow any option declarations, such as the `Option Strict` statement, and they must precede any programming element declarations, such as `Module` or `Class` statements.</span></span>

<span data-ttu-id="ef2f1-123">`Imports` můžete použít pouze na úrovni souborů.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-123">You can use `Imports` only at file level.</span></span> <span data-ttu-id="ef2f1-124">To znamená, že kontext deklarace pro import musí být zdrojový soubor a nemůže být obor názvů, třída, struktura, modul, rozhraní, procedura nebo blok.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-124">This means the declaration context for importation must be a source file, and cannot be a namespace, class, structure, module, interface, procedure, or block.</span></span>

<span data-ttu-id="ef2f1-125">Všimněte si, že příkaz `Imports` nezpřístupňuje prvky z jiných projektů a sestavení, která jsou k dispozici pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-125">Note that the `Imports` statement does not make elements from other projects and assemblies available to your project.</span></span> <span data-ttu-id="ef2f1-126">Import nebere v úvahu místo nastavení odkazu.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-126">Importing does not take the place of setting a reference.</span></span> <span data-ttu-id="ef2f1-127">Pouze odebere nutnost kvalifikovat názvy, které jsou již k dispozici pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-127">It only removes the need to qualify names that are already available to your project.</span></span> <span data-ttu-id="ef2f1-128">Další informace naleznete v tématu "Import obsahující prvky" v [odkazech na deklarované elementy](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="ef2f1-128">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

> [!NOTE]
> <span data-ttu-id="ef2f1-129">Můžete definovat implicitní příkazy `Imports` pomocí [stránky odkazy, Návrháře projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="ef2f1-129">You can define implicit `Imports` statements by using the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span> <span data-ttu-id="ef2f1-130">Další informace najdete v tématu [Postup: Přidání nebo odebrání importovaných oborů názvů (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="ef2f1-130">For more information, see [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>

## <a name="import-aliases"></a><span data-ttu-id="ef2f1-131">Importovat aliasy</span><span class="sxs-lookup"><span data-stu-id="ef2f1-131">Import Aliases</span></span>

<span data-ttu-id="ef2f1-132">*Alias importu* definuje alias pro obor názvů nebo typ.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-132">An *import alias* defines the alias for a namespace or type.</span></span> <span data-ttu-id="ef2f1-133">Importovat aliasy jsou užitečné v případě, že potřebujete použít položky se stejným názvem, které jsou deklarovány v jednom nebo více oborech názvů.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-133">Import aliases are useful when you need to use items with the same name that are declared in one or more namespaces.</span></span> <span data-ttu-id="ef2f1-134">Další informace a příklad naleznete v tématu "získání názvu elementu" v [odkazech na deklarované elementy](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="ef2f1-134">For more information and an example, see "Qualifying an Element Name" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

<span data-ttu-id="ef2f1-135">Člena byste neměli deklarovat na úrovni modulu se stejným názvem jako `aliasname`.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-135">You should not declare a member at module level with the same name as `aliasname`.</span></span> <span data-ttu-id="ef2f1-136">Pokud tak učiníte, Visual Basic kompilátor používá `aliasname` pouze pro deklarovaný člen a již jej nerozezná jako alias pro import.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-136">If you do, the Visual Basic compiler uses `aliasname` only for the declared member and no longer recognizes it as an import alias.</span></span>

<span data-ttu-id="ef2f1-137">I když syntaxe použitá pro deklarování aliasu importu je stejná jako ta, která se používá pro import předpony oboru názvů XML, výsledky se liší.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-137">Although the syntax used for declaring an import alias is like that used for importing an XML namespace prefix, the results are different.</span></span> <span data-ttu-id="ef2f1-138">Alias importu lze použít jako výraz v kódu, zatímco předponu oboru názvů XML lze použít pouze v literálech XML nebo ve vlastnostech osy XML jako předponu pro kvalifikovaný element nebo název atributu.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-138">An import alias can be used as an expression in your code, whereas an XML namespace prefix can be used only in XML literals or XML axis properties as the prefix for a qualified element or attribute name.</span></span>

### <a name="element-names"></a><span data-ttu-id="ef2f1-139">Názvy elementů</span><span class="sxs-lookup"><span data-stu-id="ef2f1-139">Element Names</span></span>

<span data-ttu-id="ef2f1-140">Pokud zadáte `element`, musí reprezentovat *prvek kontejneru*, to znamená, že programovací prvek, který může obsahovat další prvky.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-140">If you supply `element`, it must represent a *container element*, that is, a programming element that can contain other elements.</span></span> <span data-ttu-id="ef2f1-141">Prvky kontejneru zahrnují třídy, struktury, moduly, rozhraní a výčty.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-141">Container elements include classes, structures, modules, interfaces, and enumerations.</span></span>

<span data-ttu-id="ef2f1-142">Rozsah prvků, které byly k dispozici v příkazu `Imports`, závisí na tom, zda zadáte `element`.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-142">The scope of the elements made available by an `Imports` statement depends on whether you specify `element`.</span></span> <span data-ttu-id="ef2f1-143">Zadáte-li pouze `namespace`, jsou k dispozici všechny jedinečně pojmenované členy tohoto oboru názvů a členy prvků kontejneru v rámci tohoto oboru názvů bez kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-143">If you specify only `namespace`, all uniquely named members of that namespace, and members of container elements within that namespace, are available without qualification.</span></span> <span data-ttu-id="ef2f1-144">Pokud zadáte jak `namespace`, tak `element`, jsou k dispozici pouze členové tohoto prvku bez kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-144">If you specify both `namespace` and `element`, only the members of that element are available without qualification.</span></span>

## <a name="example"></a><span data-ttu-id="ef2f1-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="ef2f1-145">Example</span></span>

<span data-ttu-id="ef2f1-146">Následující příklad vrátí všechny složky v adresáři *C:\\* pomocí <xref:System.IO.DirectoryInfo> třídy:</span><span class="sxs-lookup"><span data-stu-id="ef2f1-146">The following example returns all the folders in the *C:\\* directory by using the <xref:System.IO.DirectoryInfo> class:</span></span>

<span data-ttu-id="ef2f1-147">Kód neobsahuje žádné příkazy `Imports` v horní části souboru.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-147">The code has no `Imports` statements at the top of the file.</span></span> <span data-ttu-id="ef2f1-148">Proto jsou odkazy <xref:System.IO.DirectoryInfo>, <xref:System.Text.StringBuilder>a <xref:Microsoft.VisualBasic.ControlChars.CrLf> plně kvalifikované s obory názvů.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-148">Therefore, the <xref:System.IO.DirectoryInfo>, <xref:System.Text.StringBuilder>, and <xref:Microsoft.VisualBasic.ControlChars.CrLf> references are all fully qualified with the namespaces.</span></span>

[!code-vb[VbVbalrStatements#152](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#152)]

## <a name="example"></a><span data-ttu-id="ef2f1-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="ef2f1-149">Example</span></span>

<span data-ttu-id="ef2f1-150">Následující příklad obsahuje příkazy `Imports` pro odkazované obory názvů.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-150">The following example includes `Imports` statements for the referenced namespaces.</span></span> <span data-ttu-id="ef2f1-151">Proto nemusí být typy plně kvalifikované pro obory názvů.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-151">Therefore, the types do not have to be fully qualified with the namespaces.</span></span>

[!code-vb[VbVbalrStatements#153](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#153)]

[!code-vb[VbVbalrStatements#154](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#154)]
  
## <a name="example"></a><span data-ttu-id="ef2f1-152">Příklad</span><span class="sxs-lookup"><span data-stu-id="ef2f1-152">Example</span></span>

<span data-ttu-id="ef2f1-153">Následující příklad obsahuje příkazy `Imports`, které vytvářejí aliasy pro odkazované obory názvů.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-153">The following example includes `Imports` statements that create aliases for the referenced namespaces.</span></span> <span data-ttu-id="ef2f1-154">Typy jsou kvalifikovány s aliasy.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-154">The types are qualified with the aliases.</span></span>

[!code-vb[VbVbalrStatements#155](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#155)]

[!code-vb[VbVbalrStatements#156](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#156)]

## <a name="example"></a><span data-ttu-id="ef2f1-155">Příklad</span><span class="sxs-lookup"><span data-stu-id="ef2f1-155">Example</span></span>

<span data-ttu-id="ef2f1-156">Následující příklad obsahuje příkazy `Imports`, které vytvářejí aliasy pro odkazované typy.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-156">The following example includes `Imports` statements that create aliases for the referenced types.</span></span> <span data-ttu-id="ef2f1-157">Aliasy slouží k určení typů.</span><span class="sxs-lookup"><span data-stu-id="ef2f1-157">Aliases are used to specify the types.</span></span>

[!code-vb[VbVbalrStatements#157](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#157)]

[!code-vb[VbVbalrStatements#158](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#158)]
  
## <a name="see-also"></a><span data-ttu-id="ef2f1-158">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ef2f1-158">See also</span></span>

- [<span data-ttu-id="ef2f1-159">Příkaz Namespace</span><span class="sxs-lookup"><span data-stu-id="ef2f1-159">Namespace Statement</span></span>](namespace-statement.md)
- [<span data-ttu-id="ef2f1-160">Obory názvů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ef2f1-160">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="ef2f1-161">Odkazy a příkaz Imports</span><span class="sxs-lookup"><span data-stu-id="ef2f1-161">References and the Imports Statement</span></span>](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="ef2f1-162">Příkaz Imports (obor názvů XML)</span><span class="sxs-lookup"><span data-stu-id="ef2f1-162">Imports Statement (XML Namespace)</span></span>](imports-statement-xml-namespace.md)
- [<span data-ttu-id="ef2f1-163">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="ef2f1-163">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
