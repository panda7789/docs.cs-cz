---
title: Module – příkaz (Visual Basic)
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
ms.openlocfilehash: 9b1aae08d0009a9fd23d6441207f1601ffec2568
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583099"
---
# <a name="module-statement"></a><span data-ttu-id="74c6c-102">Module – příkaz</span><span class="sxs-lookup"><span data-stu-id="74c6c-102">Module Statement</span></span>

<span data-ttu-id="74c6c-103">Deklaruje název modulu a zavádí definici proměnných, vlastností, událostí a procedur, které modul zahrnuje.</span><span class="sxs-lookup"><span data-stu-id="74c6c-103">Declares the name of a module and introduces the definition of the variables, properties, events, and procedures that the module comprises.</span></span>

## <a name="syntax"></a><span data-ttu-id="74c6c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74c6c-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ]  Module name
    [ statements ]
End Module
```

## <a name="parts"></a><span data-ttu-id="74c6c-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="74c6c-105">Parts</span></span>

`attributelist`  
<span data-ttu-id="74c6c-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="74c6c-106">Optional.</span></span> <span data-ttu-id="74c6c-107">Viz [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="74c6c-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>

`accessmodifier`  
<span data-ttu-id="74c6c-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="74c6c-108">Optional.</span></span> <span data-ttu-id="74c6c-109">Může to být jedna z následujících:</span><span class="sxs-lookup"><span data-stu-id="74c6c-109">Can be one of the following:</span></span>

- [<span data-ttu-id="74c6c-110">Public</span><span class="sxs-lookup"><span data-stu-id="74c6c-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)

- [<span data-ttu-id="74c6c-111">Friend</span><span class="sxs-lookup"><span data-stu-id="74c6c-111">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)

<span data-ttu-id="74c6c-112">Podívejte [se na úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="74c6c-112">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

`name`  
<span data-ttu-id="74c6c-113">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="74c6c-113">Required.</span></span> <span data-ttu-id="74c6c-114">Název tohoto modulu</span><span class="sxs-lookup"><span data-stu-id="74c6c-114">Name of this module.</span></span> <span data-ttu-id="74c6c-115">Viz [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="74c6c-115">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

`statements`  
<span data-ttu-id="74c6c-116">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="74c6c-116">Optional.</span></span> <span data-ttu-id="74c6c-117">Příkazy definující proměnné, vlastnosti, události, procedury a vnořené typy tohoto modulu.</span><span class="sxs-lookup"><span data-stu-id="74c6c-117">Statements which define the variables, properties, events, procedures, and nested types of this module.</span></span>

`End Module`  
<span data-ttu-id="74c6c-118">Ukončí definici `Module`.</span><span class="sxs-lookup"><span data-stu-id="74c6c-118">Terminates the `Module` definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="74c6c-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74c6c-119">Remarks</span></span>

<span data-ttu-id="74c6c-120">Příkaz `Module` definuje typ odkazu dostupný v celém svém oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="74c6c-120">A `Module` statement defines a reference type available throughout its namespace.</span></span> <span data-ttu-id="74c6c-121">*Modul* (někdy označovaný jako *Standardní modul*) je podobný třídě, ale s některými důležitými odlišnostmi.</span><span class="sxs-lookup"><span data-stu-id="74c6c-121">A *module* (sometimes called a *standard module*) is similar to a class but with some important distinctions.</span></span> <span data-ttu-id="74c6c-122">Každý modul obsahuje přesně jednu instanci a není nutné jej vytvářet ani přiřazovat proměnné.</span><span class="sxs-lookup"><span data-stu-id="74c6c-122">Every module has exactly one instance and does not need to be created or assigned to a variable.</span></span> <span data-ttu-id="74c6c-123">Moduly nepodporují dědičnost ani implementují rozhraní.</span><span class="sxs-lookup"><span data-stu-id="74c6c-123">Modules do not support inheritance or implement interfaces.</span></span> <span data-ttu-id="74c6c-124">Všimněte si, že modul není *typu* v tom smyslu, že třída nebo struktura je – nelze deklarovat programový prvek tak, aby měl datový typ modulu.</span><span class="sxs-lookup"><span data-stu-id="74c6c-124">Notice that a module is not a *type* in the sense that a class or structure is — you cannot declare a programming element to have the data type of a module.</span></span>

<span data-ttu-id="74c6c-125">@No__t_0 můžete použít pouze na úrovni oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="74c6c-125">You can use `Module` only at namespace level.</span></span> <span data-ttu-id="74c6c-126">To znamená, že *kontext deklarace* pro modul musí být zdrojový soubor nebo obor názvů a nemůže být třída, struktura, modul, rozhraní, procedura nebo blok.</span><span class="sxs-lookup"><span data-stu-id="74c6c-126">This means the *declaration context* for a module must be a source file or namespace, and cannot be a class, structure, module, interface, procedure, or block.</span></span> <span data-ttu-id="74c6c-127">Nemůžete vnořovat modul v jiném modulu nebo v žádném typu.</span><span class="sxs-lookup"><span data-stu-id="74c6c-127">You cannot nest a module within another module, or within any type.</span></span> <span data-ttu-id="74c6c-128">Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="74c6c-128">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="74c6c-129">Modul má stejnou životnost jako váš program.</span><span class="sxs-lookup"><span data-stu-id="74c6c-129">A module has the same lifetime as your program.</span></span> <span data-ttu-id="74c6c-130">Vzhledem k tomu, že se jedná o všechny členy `Shared`, mají také životní cyklus stejné jako u programu.</span><span class="sxs-lookup"><span data-stu-id="74c6c-130">Because its members are all `Shared`, they also have lifetimes equal to that of the program.</span></span>

<span data-ttu-id="74c6c-131">Moduly jako výchozí mají přístup [typu Friend](../../../visual-basic/language-reference/modifiers/friend.md) .</span><span class="sxs-lookup"><span data-stu-id="74c6c-131">Modules default to [Friend](../../../visual-basic/language-reference/modifiers/friend.md) access.</span></span> <span data-ttu-id="74c6c-132">Můžete upravit jejich úrovně přístupu modifikátory přístupu.</span><span class="sxs-lookup"><span data-stu-id="74c6c-132">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="74c6c-133">Další informace najdete v tématu [úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="74c6c-133">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="74c6c-134">Všichni členové modulu jsou implicitně `Shared`.</span><span class="sxs-lookup"><span data-stu-id="74c6c-134">All members of a module are implicitly `Shared`.</span></span>

## <a name="classes-and-modules"></a><span data-ttu-id="74c6c-135">Třídy a moduly</span><span class="sxs-lookup"><span data-stu-id="74c6c-135">Classes and Modules</span></span>

<span data-ttu-id="74c6c-136">Tyto prvky mají hodně podobnosti, ale existují i některé důležité rozdíly.</span><span class="sxs-lookup"><span data-stu-id="74c6c-136">These elements have many similarities, but there are some important differences as well.</span></span>

- <span data-ttu-id="74c6c-137">**Vede.**</span><span class="sxs-lookup"><span data-stu-id="74c6c-137">**Terminology.**</span></span> <span data-ttu-id="74c6c-138">Předchozí verze Visual Basic rozpoznávají dva typy modulů: *moduly tříd* (soubory. CLS) a *standardní moduly* (soubory. bas).</span><span class="sxs-lookup"><span data-stu-id="74c6c-138">Previous versions of Visual Basic recognize two types of modules: *class modules* (.cls files) and *standard modules* (.bas files).</span></span> <span data-ttu-id="74c6c-139">Aktuální verze volá tyto *třídy* a *moduly*, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="74c6c-139">The current version calls these *classes* and *modules*, respectively.</span></span>

- <span data-ttu-id="74c6c-140">**Sdílené členy.**</span><span class="sxs-lookup"><span data-stu-id="74c6c-140">**Shared Members.**</span></span> <span data-ttu-id="74c6c-141">Můžete určit, zda je člen třídy sdíleným členem nebo členem instance.</span><span class="sxs-lookup"><span data-stu-id="74c6c-141">You can control whether a member of a class is a shared or instance member.</span></span>

- <span data-ttu-id="74c6c-142">**Orientace objektu.**</span><span class="sxs-lookup"><span data-stu-id="74c6c-142">**Object Orientation.**</span></span> <span data-ttu-id="74c6c-143">Třídy jsou objektově orientované, ale moduly nejsou.</span><span class="sxs-lookup"><span data-stu-id="74c6c-143">Classes are object-oriented, but modules are not.</span></span> <span data-ttu-id="74c6c-144">Takže pouze třídy mohou být vytvořeny jako objekty.</span><span class="sxs-lookup"><span data-stu-id="74c6c-144">So only classes can be instantiated as objects.</span></span> <span data-ttu-id="74c6c-145">Další informace naleznete v tématu [objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span><span class="sxs-lookup"><span data-stu-id="74c6c-145">For more information, see [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>

## <a name="rules"></a><span data-ttu-id="74c6c-146">Pravidly</span><span class="sxs-lookup"><span data-stu-id="74c6c-146">Rules</span></span>

- <span data-ttu-id="74c6c-147">**Modifikátory.**</span><span class="sxs-lookup"><span data-stu-id="74c6c-147">**Modifiers.**</span></span> <span data-ttu-id="74c6c-148">Všechny členy modulů jsou implicitně [sdíleny](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="74c6c-148">All module members are implicitly [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="74c6c-149">Klíčové slovo `Shared` nelze použít při deklaraci člena a nelze změnit sdílený stav žádného člena.</span><span class="sxs-lookup"><span data-stu-id="74c6c-149">You cannot use the `Shared` keyword when declaring a member, and you cannot alter the shared status of any member.</span></span>

- <span data-ttu-id="74c6c-150">**Dědičnost.**</span><span class="sxs-lookup"><span data-stu-id="74c6c-150">**Inheritance.**</span></span> <span data-ttu-id="74c6c-151">Modul nemůže dědit z jiného typu než <xref:System.Object>, ze kterého všechny moduly dědí.</span><span class="sxs-lookup"><span data-stu-id="74c6c-151">A module cannot inherit from any type other than <xref:System.Object>, from which all modules inherit.</span></span> <span data-ttu-id="74c6c-152">Konkrétně jeden modul nemůže dědit z jiného modulu.</span><span class="sxs-lookup"><span data-stu-id="74c6c-152">In particular, one module cannot inherit from another.</span></span>

  <span data-ttu-id="74c6c-153">[Příkaz Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md) nelze použít v definici modulu, ani pro určení <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="74c6c-153">You cannot use the [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md) in a module definition, even to specify <xref:System.Object>.</span></span>

- <span data-ttu-id="74c6c-154">**Výchozí vlastnost.**</span><span class="sxs-lookup"><span data-stu-id="74c6c-154">**Default Property.**</span></span> <span data-ttu-id="74c6c-155">V modulu nelze definovat žádné výchozí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="74c6c-155">You cannot define any default properties in a module.</span></span> <span data-ttu-id="74c6c-156">Další informace najdete v tématu [výchozí](../../../visual-basic/language-reference/modifiers/default.md).</span><span class="sxs-lookup"><span data-stu-id="74c6c-156">For more information, see [Default](../../../visual-basic/language-reference/modifiers/default.md).</span></span>

## <a name="behavior"></a><span data-ttu-id="74c6c-157">Předvídatelně</span><span class="sxs-lookup"><span data-stu-id="74c6c-157">Behavior</span></span>

- <span data-ttu-id="74c6c-158">**Úroveň přístupu.**</span><span class="sxs-lookup"><span data-stu-id="74c6c-158">**Access Level.**</span></span> <span data-ttu-id="74c6c-159">V rámci modulu můžete deklarovat každého člena s vlastní úrovní přístupu.</span><span class="sxs-lookup"><span data-stu-id="74c6c-159">Within a module, you can declare each member with its own access level.</span></span> <span data-ttu-id="74c6c-160">Členy modulu jsou ve výchozím nastavení [veřejný](../../../visual-basic/language-reference/modifiers/public.md) přístup, s výjimkou proměnných a konstant, které jsou ve výchozím nastavení [privátním](../../../visual-basic/language-reference/modifiers/private.md) přístupem.</span><span class="sxs-lookup"><span data-stu-id="74c6c-160">Module members default to [Public](../../../visual-basic/language-reference/modifiers/public.md) access, except variables and constants, which default to [Private](../../../visual-basic/language-reference/modifiers/private.md) access.</span></span> <span data-ttu-id="74c6c-161">Pokud má modul více omezený přístup než jeden z jeho členů, má zadaná úroveň přístupu k modulu přednost.</span><span class="sxs-lookup"><span data-stu-id="74c6c-161">When a module has more restricted access than one of its members, the specified module access level takes precedence.</span></span>

- <span data-ttu-id="74c6c-162">**Oboru.**</span><span class="sxs-lookup"><span data-stu-id="74c6c-162">**Scope.**</span></span> <span data-ttu-id="74c6c-163">Modul je v rozsahu celého oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="74c6c-163">A module is in scope throughout its namespace.</span></span>

  <span data-ttu-id="74c6c-164">Rozsah každého člena modulu je celý modul.</span><span class="sxs-lookup"><span data-stu-id="74c6c-164">The scope of every module member is the entire module.</span></span> <span data-ttu-id="74c6c-165">Všimněte si, že všichni členové přecházejí na *povýšení typu*, což způsobí, že jejich obor bude povýšen na obor názvů obsahující modul.</span><span class="sxs-lookup"><span data-stu-id="74c6c-165">Notice that all members undergo *type promotion*, which causes their scope to be promoted to the namespace containing the module.</span></span> <span data-ttu-id="74c6c-166">Další informace najdete v tématu o [typu propagace](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="74c6c-166">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span></span>

- <span data-ttu-id="74c6c-167">**Vydal.**</span><span class="sxs-lookup"><span data-stu-id="74c6c-167">**Qualification.**</span></span> <span data-ttu-id="74c6c-168">V projektu může být více modulů a můžete deklarovat členy se stejným názvem ve dvou nebo více modulech.</span><span class="sxs-lookup"><span data-stu-id="74c6c-168">You can have multiple modules in a project, and you can declare members with the same name in two or more modules.</span></span> <span data-ttu-id="74c6c-169">Pokud je však odkaz z vnějšku tohoto modulu, musíte kvalifikovat jakýkoliv odkaz na takový člen s odpovídajícím názvem modulu.</span><span class="sxs-lookup"><span data-stu-id="74c6c-169">However, you must qualify any reference to such a member with the appropriate module name if the reference is from outside that module.</span></span> <span data-ttu-id="74c6c-170">Další informace naleznete v tématu [odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="74c6c-170">For more information, see [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

## <a name="example"></a><span data-ttu-id="74c6c-171">Příklad</span><span class="sxs-lookup"><span data-stu-id="74c6c-171">Example</span></span>

[!code-vb[VbVbalrStatements#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#69)]

## <a name="see-also"></a><span data-ttu-id="74c6c-172">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74c6c-172">See also</span></span>

- [<span data-ttu-id="74c6c-173">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="74c6c-173">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="74c6c-174">Příkaz Namespace</span><span class="sxs-lookup"><span data-stu-id="74c6c-174">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="74c6c-175">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="74c6c-175">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="74c6c-176">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="74c6c-176">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="74c6c-177">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="74c6c-177">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="74c6c-178">Propagace typu</span><span class="sxs-lookup"><span data-stu-id="74c6c-178">Type Promotion</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
