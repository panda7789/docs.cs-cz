---
title: Module – příkaz
ms.date: 07/20/2015
f1_keywords:
- Module
- vb.Module
helpviewer_keywords:
- modules, classes
- modules
- Module statement [Visual Basic]
- modules, declaring
- standard modules
- classes [Visual Basic], vs. modules
- declarations [Visual Basic], modules
ms.assetid: a1243afc-14a5-45df-95d5-51118aeac362
ms.openlocfilehash: 56fc4f9383f1fc4779358ef18a4e5c611d897eda
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348019"
---
# <a name="module-statement"></a><span data-ttu-id="4bb03-102">Module – příkaz</span><span class="sxs-lookup"><span data-stu-id="4bb03-102">Module Statement</span></span>

<span data-ttu-id="4bb03-103">Deklaruje název modulu a zavádí definici proměnných, vlastností, událostí a procedur, které modul zahrnuje.</span><span class="sxs-lookup"><span data-stu-id="4bb03-103">Declares the name of a module and introduces the definition of the variables, properties, events, and procedures that the module comprises.</span></span>

## <a name="syntax"></a><span data-ttu-id="4bb03-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4bb03-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ]  Module name
    [ statements ]
End Module
```

## <a name="parts"></a><span data-ttu-id="4bb03-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="4bb03-105">Parts</span></span>

`attributelist`  
<span data-ttu-id="4bb03-106">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="4bb03-106">Optional.</span></span> <span data-ttu-id="4bb03-107">Viz [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="4bb03-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>

`accessmodifier`  
<span data-ttu-id="4bb03-108">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="4bb03-108">Optional.</span></span> <span data-ttu-id="4bb03-109">Může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="4bb03-109">Can be one of the following:</span></span>

- [<span data-ttu-id="4bb03-110">Public</span><span class="sxs-lookup"><span data-stu-id="4bb03-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)

- [<span data-ttu-id="4bb03-111">Friend</span><span class="sxs-lookup"><span data-stu-id="4bb03-111">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)

<span data-ttu-id="4bb03-112">Podívejte [se na úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="4bb03-112">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

`name`  
<span data-ttu-id="4bb03-113">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="4bb03-113">Required.</span></span> <span data-ttu-id="4bb03-114">Název tohoto modulu</span><span class="sxs-lookup"><span data-stu-id="4bb03-114">Name of this module.</span></span> <span data-ttu-id="4bb03-115">Viz [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="4bb03-115">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

`statements`  
<span data-ttu-id="4bb03-116">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="4bb03-116">Optional.</span></span> <span data-ttu-id="4bb03-117">Příkazy definující proměnné, vlastnosti, události, procedury a vnořené typy tohoto modulu.</span><span class="sxs-lookup"><span data-stu-id="4bb03-117">Statements which define the variables, properties, events, procedures, and nested types of this module.</span></span>

`End Module`  
<span data-ttu-id="4bb03-118">Ukončí definici `Module`.</span><span class="sxs-lookup"><span data-stu-id="4bb03-118">Terminates the `Module` definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="4bb03-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4bb03-119">Remarks</span></span>

<span data-ttu-id="4bb03-120">Příkaz `Module` definuje typ odkazu dostupný v celém svém oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4bb03-120">A `Module` statement defines a reference type available throughout its namespace.</span></span> <span data-ttu-id="4bb03-121">*Modul* (někdy označovaný jako *Standardní modul*) je podobný třídě, ale s některými důležitými odlišnostmi.</span><span class="sxs-lookup"><span data-stu-id="4bb03-121">A *module* (sometimes called a *standard module*) is similar to a class but with some important distinctions.</span></span> <span data-ttu-id="4bb03-122">Každý modul obsahuje přesně jednu instanci a není nutné jej vytvářet ani přiřazovat proměnné.</span><span class="sxs-lookup"><span data-stu-id="4bb03-122">Every module has exactly one instance and does not need to be created or assigned to a variable.</span></span> <span data-ttu-id="4bb03-123">Moduly nepodporují dědičnost ani implementují rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4bb03-123">Modules do not support inheritance or implement interfaces.</span></span> <span data-ttu-id="4bb03-124">Všimněte si, že modul není *typu* v tom smyslu, že třída nebo struktura je – nelze deklarovat programový prvek tak, aby měl datový typ modulu.</span><span class="sxs-lookup"><span data-stu-id="4bb03-124">Notice that a module is not a *type* in the sense that a class or structure is — you cannot declare a programming element to have the data type of a module.</span></span>

<span data-ttu-id="4bb03-125">`Module` můžete použít pouze na úrovni oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4bb03-125">You can use `Module` only at namespace level.</span></span> <span data-ttu-id="4bb03-126">To znamená, že *kontext deklarace* pro modul musí být zdrojový soubor nebo obor názvů a nemůže být třída, struktura, modul, rozhraní, procedura nebo blok.</span><span class="sxs-lookup"><span data-stu-id="4bb03-126">This means the *declaration context* for a module must be a source file or namespace, and cannot be a class, structure, module, interface, procedure, or block.</span></span> <span data-ttu-id="4bb03-127">Nemůžete vnořovat modul v jiném modulu nebo v žádném typu.</span><span class="sxs-lookup"><span data-stu-id="4bb03-127">You cannot nest a module within another module, or within any type.</span></span> <span data-ttu-id="4bb03-128">Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="4bb03-128">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="4bb03-129">Modul má stejnou životnost jako váš program.</span><span class="sxs-lookup"><span data-stu-id="4bb03-129">A module has the same lifetime as your program.</span></span> <span data-ttu-id="4bb03-130">Vzhledem k tomu, že se jedná o všechny členy `Shared`, mají také životní cyklus stejné jako u programu.</span><span class="sxs-lookup"><span data-stu-id="4bb03-130">Because its members are all `Shared`, they also have lifetimes equal to that of the program.</span></span>

<span data-ttu-id="4bb03-131">Moduly jako výchozí mají přístup [typu Friend](../../../visual-basic/language-reference/modifiers/friend.md) .</span><span class="sxs-lookup"><span data-stu-id="4bb03-131">Modules default to [Friend](../../../visual-basic/language-reference/modifiers/friend.md) access.</span></span> <span data-ttu-id="4bb03-132">Můžete upravit jejich úrovně přístupu modifikátory přístupu.</span><span class="sxs-lookup"><span data-stu-id="4bb03-132">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="4bb03-133">Další informace najdete v tématu [úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="4bb03-133">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="4bb03-134">Všichni členové modulu jsou implicitně `Shared`.</span><span class="sxs-lookup"><span data-stu-id="4bb03-134">All members of a module are implicitly `Shared`.</span></span>

## <a name="classes-and-modules"></a><span data-ttu-id="4bb03-135">Třídy a moduly</span><span class="sxs-lookup"><span data-stu-id="4bb03-135">Classes and Modules</span></span>

<span data-ttu-id="4bb03-136">Tyto prvky mají hodně podobnosti, ale existují i některé důležité rozdíly.</span><span class="sxs-lookup"><span data-stu-id="4bb03-136">These elements have many similarities, but there are some important differences as well.</span></span>

- <span data-ttu-id="4bb03-137">**Vede.**</span><span class="sxs-lookup"><span data-stu-id="4bb03-137">**Terminology.**</span></span> <span data-ttu-id="4bb03-138">Předchozí verze Visual Basic rozpoznávají dva typy modulů: *moduly tříd* (soubory. CLS) a *standardní moduly* (soubory. bas).</span><span class="sxs-lookup"><span data-stu-id="4bb03-138">Previous versions of Visual Basic recognize two types of modules: *class modules* (.cls files) and *standard modules* (.bas files).</span></span> <span data-ttu-id="4bb03-139">Aktuální verze volá tyto *třídy* a *moduly*, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="4bb03-139">The current version calls these *classes* and *modules*, respectively.</span></span>

- <span data-ttu-id="4bb03-140">**Sdílené členy.**</span><span class="sxs-lookup"><span data-stu-id="4bb03-140">**Shared Members.**</span></span> <span data-ttu-id="4bb03-141">Můžete určit, zda je člen třídy sdíleným členem nebo členem instance.</span><span class="sxs-lookup"><span data-stu-id="4bb03-141">You can control whether a member of a class is a shared or instance member.</span></span>

- <span data-ttu-id="4bb03-142">**Orientace objektu.**</span><span class="sxs-lookup"><span data-stu-id="4bb03-142">**Object Orientation.**</span></span> <span data-ttu-id="4bb03-143">Třídy jsou objektově orientované, ale moduly nejsou.</span><span class="sxs-lookup"><span data-stu-id="4bb03-143">Classes are object-oriented, but modules are not.</span></span> <span data-ttu-id="4bb03-144">Takže pouze třídy mohou být vytvořeny jako objekty.</span><span class="sxs-lookup"><span data-stu-id="4bb03-144">So only classes can be instantiated as objects.</span></span> <span data-ttu-id="4bb03-145">Další informace naleznete v tématu [objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span><span class="sxs-lookup"><span data-stu-id="4bb03-145">For more information, see [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>

## <a name="rules"></a><span data-ttu-id="4bb03-146">Pravidla</span><span class="sxs-lookup"><span data-stu-id="4bb03-146">Rules</span></span>

- <span data-ttu-id="4bb03-147">**Modifikátory.**</span><span class="sxs-lookup"><span data-stu-id="4bb03-147">**Modifiers.**</span></span> <span data-ttu-id="4bb03-148">Všechny členy modulů jsou implicitně [sdíleny](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="4bb03-148">All module members are implicitly [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="4bb03-149">Klíčové slovo `Shared` nelze použít při deklaraci člena a nelze změnit sdílený stav žádného člena.</span><span class="sxs-lookup"><span data-stu-id="4bb03-149">You cannot use the `Shared` keyword when declaring a member, and you cannot alter the shared status of any member.</span></span>

- <span data-ttu-id="4bb03-150">**Dědičnost.**</span><span class="sxs-lookup"><span data-stu-id="4bb03-150">**Inheritance.**</span></span> <span data-ttu-id="4bb03-151">Modul nemůže dědit z jiného typu než <xref:System.Object>, ze kterého všechny moduly dědí.</span><span class="sxs-lookup"><span data-stu-id="4bb03-151">A module cannot inherit from any type other than <xref:System.Object>, from which all modules inherit.</span></span> <span data-ttu-id="4bb03-152">Konkrétně jeden modul nemůže dědit z jiného modulu.</span><span class="sxs-lookup"><span data-stu-id="4bb03-152">In particular, one module cannot inherit from another.</span></span>

  <span data-ttu-id="4bb03-153">[Příkaz Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md) nelze použít v definici modulu, ani pro určení <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="4bb03-153">You cannot use the [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md) in a module definition, even to specify <xref:System.Object>.</span></span>

- <span data-ttu-id="4bb03-154">**Výchozí vlastnost.**</span><span class="sxs-lookup"><span data-stu-id="4bb03-154">**Default Property.**</span></span> <span data-ttu-id="4bb03-155">V modulu nelze definovat žádné výchozí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4bb03-155">You cannot define any default properties in a module.</span></span> <span data-ttu-id="4bb03-156">Další informace najdete v tématu [výchozí](../../../visual-basic/language-reference/modifiers/default.md).</span><span class="sxs-lookup"><span data-stu-id="4bb03-156">For more information, see [Default](../../../visual-basic/language-reference/modifiers/default.md).</span></span>

## <a name="behavior"></a><span data-ttu-id="4bb03-157">Chování</span><span class="sxs-lookup"><span data-stu-id="4bb03-157">Behavior</span></span>

- <span data-ttu-id="4bb03-158">**Úroveň přístupu.**</span><span class="sxs-lookup"><span data-stu-id="4bb03-158">**Access Level.**</span></span> <span data-ttu-id="4bb03-159">V rámci modulu můžete deklarovat každého člena s vlastní úrovní přístupu.</span><span class="sxs-lookup"><span data-stu-id="4bb03-159">Within a module, you can declare each member with its own access level.</span></span> <span data-ttu-id="4bb03-160">Členy modulu jsou ve výchozím nastavení [veřejný](../../../visual-basic/language-reference/modifiers/public.md) přístup, s výjimkou proměnných a konstant, které jsou ve výchozím nastavení [privátním](../../../visual-basic/language-reference/modifiers/private.md) přístupem.</span><span class="sxs-lookup"><span data-stu-id="4bb03-160">Module members default to [Public](../../../visual-basic/language-reference/modifiers/public.md) access, except variables and constants, which default to [Private](../../../visual-basic/language-reference/modifiers/private.md) access.</span></span> <span data-ttu-id="4bb03-161">Pokud má modul více omezený přístup než jeden z jeho členů, má zadaná úroveň přístupu k modulu přednost.</span><span class="sxs-lookup"><span data-stu-id="4bb03-161">When a module has more restricted access than one of its members, the specified module access level takes precedence.</span></span>

- <span data-ttu-id="4bb03-162">**Oboru.**</span><span class="sxs-lookup"><span data-stu-id="4bb03-162">**Scope.**</span></span> <span data-ttu-id="4bb03-163">Modul je v rozsahu celého oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4bb03-163">A module is in scope throughout its namespace.</span></span>

  <span data-ttu-id="4bb03-164">Rozsah každého člena modulu je celý modul.</span><span class="sxs-lookup"><span data-stu-id="4bb03-164">The scope of every module member is the entire module.</span></span> <span data-ttu-id="4bb03-165">Všimněte si, že všichni členové přecházejí na *povýšení typu*, což způsobí, že jejich obor bude povýšen na obor názvů obsahující modul.</span><span class="sxs-lookup"><span data-stu-id="4bb03-165">Notice that all members undergo *type promotion*, which causes their scope to be promoted to the namespace containing the module.</span></span> <span data-ttu-id="4bb03-166">Další informace najdete v tématu o [typu propagace](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="4bb03-166">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span></span>

- <span data-ttu-id="4bb03-167">**Vydal.**</span><span class="sxs-lookup"><span data-stu-id="4bb03-167">**Qualification.**</span></span> <span data-ttu-id="4bb03-168">V projektu může být více modulů a můžete deklarovat členy se stejným názvem ve dvou nebo více modulech.</span><span class="sxs-lookup"><span data-stu-id="4bb03-168">You can have multiple modules in a project, and you can declare members with the same name in two or more modules.</span></span> <span data-ttu-id="4bb03-169">Pokud je však odkaz z vnějšku tohoto modulu, musíte kvalifikovat jakýkoliv odkaz na takový člen s odpovídajícím názvem modulu.</span><span class="sxs-lookup"><span data-stu-id="4bb03-169">However, you must qualify any reference to such a member with the appropriate module name if the reference is from outside that module.</span></span> <span data-ttu-id="4bb03-170">Další informace naleznete v tématu [odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="4bb03-170">For more information, see [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

## <a name="example"></a><span data-ttu-id="4bb03-171">Příklad</span><span class="sxs-lookup"><span data-stu-id="4bb03-171">Example</span></span>

[!code-vb[VbVbalrStatements#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#69)]

## <a name="see-also"></a><span data-ttu-id="4bb03-172">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4bb03-172">See also</span></span>

- [<span data-ttu-id="4bb03-173">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="4bb03-173">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="4bb03-174">Příkaz Namespace</span><span class="sxs-lookup"><span data-stu-id="4bb03-174">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="4bb03-175">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="4bb03-175">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="4bb03-176">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="4bb03-176">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="4bb03-177">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="4bb03-177">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="4bb03-178">Propagace typu</span><span class="sxs-lookup"><span data-stu-id="4bb03-178">Type Promotion</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
