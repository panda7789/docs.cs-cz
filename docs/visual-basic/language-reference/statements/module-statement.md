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
ms.openlocfilehash: 73d4a5cc8fd4bad41ead1fda830504b19877a8d8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625473"
---
# <a name="module-statement"></a><span data-ttu-id="5bfb7-102">Module – příkaz</span><span class="sxs-lookup"><span data-stu-id="5bfb7-102">Module Statement</span></span>
<span data-ttu-id="5bfb7-103">Deklaruje název modulu a zavádí definici proměnných, vlastností, událostí a postupů, které se skládá z modulu.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-103">Declares the name of a module and introduces the definition of the variables, properties, events, and procedures that the module comprises.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bfb7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5bfb7-104">Syntax</span></span>  
  
```vb 
[ <attributelist> ] [ accessmodifier ]  Module name  
    [ statements ]  
End Module  
```  
  
## <a name="parts"></a><span data-ttu-id="5bfb7-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="5bfb7-105">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="5bfb7-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-106">Optional.</span></span> <span data-ttu-id="5bfb7-107">Zobrazit [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="5bfb7-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
 `accessmodifier`  
 <span data-ttu-id="5bfb7-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-108">Optional.</span></span> <span data-ttu-id="5bfb7-109">Může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="5bfb7-109">Can be one of the following:</span></span>  
  
- [<span data-ttu-id="5bfb7-110">Public</span><span class="sxs-lookup"><span data-stu-id="5bfb7-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
- [<span data-ttu-id="5bfb7-111">Friend</span><span class="sxs-lookup"><span data-stu-id="5bfb7-111">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
 <span data-ttu-id="5bfb7-112">Zobrazit [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="5bfb7-112">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 `name`  
 <span data-ttu-id="5bfb7-113">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-113">Required.</span></span> <span data-ttu-id="5bfb7-114">Název tohoto modulu.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-114">Name of this module.</span></span> <span data-ttu-id="5bfb7-115">Zobrazit [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="5bfb7-115">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 `statements`  
 <span data-ttu-id="5bfb7-116">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-116">Optional.</span></span> <span data-ttu-id="5bfb7-117">Příkazy, které definují proměnné, vlastnosti, události, postupy a vnořené typy tohoto modulu.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-117">Statements which define the variables, properties, events, procedures, and nested types of this module.</span></span>  
  
 `End Module`  
 <span data-ttu-id="5bfb7-118">Ukončuje `Module` definice.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-118">Terminates the `Module` definition.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5bfb7-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5bfb7-119">Remarks</span></span>  
 <span data-ttu-id="5bfb7-120">A `Module` prohlášení definuje typ odkazu, který je k dispozici v rámci svého oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-120">A `Module` statement defines a reference type available throughout its namespace.</span></span> <span data-ttu-id="5bfb7-121">A *modulu* (říká se jim *standardní modul*) se podobá do třídy, ale některé důležité rozdíly.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-121">A *module* (sometimes called a *standard module*)is similar to a class but with some important distinctions.</span></span> <span data-ttu-id="5bfb7-122">Každý modul nemá přesně jednu instanci a není nutné vytvořit či přiřazen proměnné.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-122">Every module has exactly one instance and does not need to be created or assigned to a variable.</span></span> <span data-ttu-id="5bfb7-123">Moduly nepodporují dědičnosti nebo implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-123">Modules do not support inheritance or implement interfaces.</span></span> <span data-ttu-id="5bfb7-124">Všimněte si, že je modul *typ* v tom smyslu, že třídu nebo strukturu – programovací element má datový typ modulu nelze deklarovat.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-124">Notice that a module is not a *type* in the sense that a class or structure is — you cannot declare a programming element to have the data type of a module.</span></span>  
  
 <span data-ttu-id="5bfb7-125">Můžete použít `Module` pouze na úrovni oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-125">You can use `Module` only at namespace level.</span></span> <span data-ttu-id="5bfb7-126">To znamená, že *kontext deklarace* modulu musí být zdrojový soubor nebo obor názvů a nemůže být třída, struktura, modulu, rozhraní, procedura nebo blok.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-126">This means the *declaration context* for a module must be a source file or namespace, and cannot be a class, structure, module, interface, procedure, or block.</span></span> <span data-ttu-id="5bfb7-127">Nelze vnořovat modulu jiný modul, nebo v rámci libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-127">You cannot nest a module within another module, or within any type.</span></span> <span data-ttu-id="5bfb7-128">Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="5bfb7-128">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="5bfb7-129">Modul má stejnou dobu života jako aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-129">A module has the same lifetime as your program.</span></span> <span data-ttu-id="5bfb7-130">Protože všechny její členy jsou `Shared`, mají také životnosti rovna vlastnosti programu.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-130">Because its members are all `Shared`, they also have lifetimes equal to that of the program.</span></span>  
  
 <span data-ttu-id="5bfb7-131">Moduly ve výchozím nastavení [Friend](../../../visual-basic/language-reference/modifiers/friend.md) přístup.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-131">Modules default to [Friend](../../../visual-basic/language-reference/modifiers/friend.md) access.</span></span> <span data-ttu-id="5bfb7-132">Můžete nastavit jejich úrovně přístupu modifikátory přístupu.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-132">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="5bfb7-133">Další informace najdete v tématu [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="5bfb7-133">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="5bfb7-134">Všichni členové modulu jsou implicitně `Shared`.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-134">All members of a module are implicitly `Shared`.</span></span>  
  
## <a name="classes-and-modules"></a><span data-ttu-id="5bfb7-135">Třídy a moduly</span><span class="sxs-lookup"><span data-stu-id="5bfb7-135">Classes and Modules</span></span>  
 <span data-ttu-id="5bfb7-136">Tyto prvky řada podobností, ale existuje několik důležitých rozdílů.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-136">These elements have many similarities, but there are some important differences as well.</span></span>  
  
- <span data-ttu-id="5bfb7-137">**Terminologie.**</span><span class="sxs-lookup"><span data-stu-id="5bfb7-137">**Terminology.**</span></span> <span data-ttu-id="5bfb7-138">Předchozí verzí jazyka Visual Basic rozpoznat dva typy modulů: *moduly tříd* (.cls soubory) a *standardní moduly* (BAS soubory).</span><span class="sxs-lookup"><span data-stu-id="5bfb7-138">Previous versions of Visual Basic recognize two types of modules: *class modules* (.cls files) and *standard modules* (.bas files).</span></span> <span data-ttu-id="5bfb7-139">Aktuální verze volá tyto *třídy* a *moduly*v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-139">The current version calls these *classes* and *modules*, respectively.</span></span>  
  
- <span data-ttu-id="5bfb7-140">**Sdílené členy.**</span><span class="sxs-lookup"><span data-stu-id="5bfb7-140">**Shared Members.**</span></span> <span data-ttu-id="5bfb7-141">Můžete řídit, jestli je sdílené člen třídy nebo člena instance.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-141">You can control whether a member of a class is a shared or instance member.</span></span>  
  
- <span data-ttu-id="5bfb7-142">**Objekt orientace.**</span><span class="sxs-lookup"><span data-stu-id="5bfb7-142">**Object Orientation.**</span></span> <span data-ttu-id="5bfb7-143">Třídy jsou objektově orientované, ale nejsou moduly.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-143">Classes are object-oriented, but modules are not.</span></span> <span data-ttu-id="5bfb7-144">Proto pouze třídy může být vytvořen jako objekty.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-144">So only classes can be instantiated as objects.</span></span> <span data-ttu-id="5bfb7-145">Další informace najdete v tématu [objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span><span class="sxs-lookup"><span data-stu-id="5bfb7-145">For more information, see [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="5bfb7-146">pravidla</span><span class="sxs-lookup"><span data-stu-id="5bfb7-146">Rules</span></span>  
  
- <span data-ttu-id="5bfb7-147">**Modifikátory.**</span><span class="sxs-lookup"><span data-stu-id="5bfb7-147">**Modifiers.**</span></span> <span data-ttu-id="5bfb7-148">Všichni členové modulu jsou implicitně [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="5bfb7-148">All module members are implicitly [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="5bfb7-149">Nelze použít `Shared` – klíčové slovo deklarace člena a není možné pozměnit sdílený stav kteréhokoli člena.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-149">You cannot use the `Shared` keyword when declaring a member, and you cannot alter the shared status of any member.</span></span>  
  
- <span data-ttu-id="5bfb7-150">**Dědičnost.**</span><span class="sxs-lookup"><span data-stu-id="5bfb7-150">**Inheritance.**</span></span> <span data-ttu-id="5bfb7-151">Modul nemůže dědit z libovolného typu jiného než <xref:System.Object>, ze které všechny moduly dědit.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-151">A module cannot inherit from any type other than <xref:System.Object>, from which all modules inherit.</span></span> <span data-ttu-id="5bfb7-152">Konkrétně se jeden modul nemůže dědit z jiné.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-152">In particular, one module cannot inherit from another.</span></span>  
  
     <span data-ttu-id="5bfb7-153">Nelze použít [dědí příkaz](../../../visual-basic/language-reference/statements/inherits-statement.md) v definici modulu ani k určení <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-153">You cannot use the [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md) in a module definition, even to specify <xref:System.Object>.</span></span>  
  
- <span data-ttu-id="5bfb7-154">**Výchozí vlastnost.**</span><span class="sxs-lookup"><span data-stu-id="5bfb7-154">**Default Property.**</span></span> <span data-ttu-id="5bfb7-155">V modulu nejde definovat žádné výchozí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-155">You cannot define any default properties in a module.</span></span> <span data-ttu-id="5bfb7-156">Další informace najdete v tématu [výchozí](../../../visual-basic/language-reference/modifiers/default.md).</span><span class="sxs-lookup"><span data-stu-id="5bfb7-156">For more information, see [Default](../../../visual-basic/language-reference/modifiers/default.md).</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="5bfb7-157">Chování</span><span class="sxs-lookup"><span data-stu-id="5bfb7-157">Behavior</span></span>  
  
- <span data-ttu-id="5bfb7-158">**Úroveň přístupu.**</span><span class="sxs-lookup"><span data-stu-id="5bfb7-158">**Access Level.**</span></span> <span data-ttu-id="5bfb7-159">V rámci modulu můžete deklarovat každého člena se svou vlastní úroveň přístupu.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-159">Within a module, you can declare each member with its own access level.</span></span> <span data-ttu-id="5bfb7-160">Modul členy ve výchozím nastavení [veřejné](../../../visual-basic/language-reference/modifiers/public.md) přístup, s výjimkou proměnné a konstanty, které výchozí [privátní](../../../visual-basic/language-reference/modifiers/private.md) přístup.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-160">Module members default to [Public](../../../visual-basic/language-reference/modifiers/public.md) access, except variables and constants, which default to [Private](../../../visual-basic/language-reference/modifiers/private.md) access.</span></span> <span data-ttu-id="5bfb7-161">Pokud modul má omezený přístup k více než jeden z jejích členů, úroveň přístupu zadaného modulu přednost.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-161">When a module has more restricted access than one of its members, the specified module access level takes precedence.</span></span>  
  
- <span data-ttu-id="5bfb7-162">**Obor.**</span><span class="sxs-lookup"><span data-stu-id="5bfb7-162">**Scope.**</span></span> <span data-ttu-id="5bfb7-163">Modul je v oboru v rámci svého oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-163">A module is in scope throughout its namespace.</span></span>  
  
     <span data-ttu-id="5bfb7-164">Obor každého člena modulu je celý modul.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-164">The scope of every module member is the entire module.</span></span> <span data-ttu-id="5bfb7-165">Všimněte si, že všichni členové této oblasti podstupovali *zadejte povýšení*, což způsobí, že jejich obor má být převeden na obor názvů obsahující modul.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-165">Notice that all members undergo *type promotion*, which causes their scope to be promoted to the namespace containing the module.</span></span> <span data-ttu-id="5bfb7-166">Další informace najdete v tématu [propagace typu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="5bfb7-166">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span></span>  
  
- <span data-ttu-id="5bfb7-167">**Kvalifikace.**</span><span class="sxs-lookup"><span data-stu-id="5bfb7-167">**Qualification.**</span></span> <span data-ttu-id="5bfb7-168">Máte více modulů v projektu a je možné deklarovat členy se stejným názvem ve dvou nebo více modulů.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-168">You can have multiple modules in a project, and you can declare members with the same name in two or more modules.</span></span> <span data-ttu-id="5bfb7-169">Pokud je odkaz z mimo modul, však musí kvalifikovat všechny odkazy na tento člen s názvem příslušný modul.</span><span class="sxs-lookup"><span data-stu-id="5bfb7-169">However, you must qualify any reference to such a member with the appropriate module name if the reference is from outside that module.</span></span> <span data-ttu-id="5bfb7-170">Další informace najdete v tématu [odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="5bfb7-170">For more information, see [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5bfb7-171">Příklad</span><span class="sxs-lookup"><span data-stu-id="5bfb7-171">Example</span></span>  
 [!code-vb[VbVbalrStatements#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#69)]  
  
## <a name="see-also"></a><span data-ttu-id="5bfb7-172">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5bfb7-172">See also</span></span>

- [<span data-ttu-id="5bfb7-173">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="5bfb7-173">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="5bfb7-174">Příkaz Namespace</span><span class="sxs-lookup"><span data-stu-id="5bfb7-174">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="5bfb7-175">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="5bfb7-175">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="5bfb7-176">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="5bfb7-176">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="5bfb7-177">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="5bfb7-177">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="5bfb7-178">Propagace typu</span><span class="sxs-lookup"><span data-stu-id="5bfb7-178">Type Promotion</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
