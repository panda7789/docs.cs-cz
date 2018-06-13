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
ms.openlocfilehash: f4a0c7b772417085718b63569e8368178e348567
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605014"
---
# <a name="module-statement"></a><span data-ttu-id="46113-102">Module – příkaz</span><span class="sxs-lookup"><span data-stu-id="46113-102">Module Statement</span></span>
<span data-ttu-id="46113-103">Deklaruje název modulu a představuje definici proměnné, vlastností, události a postupy, které se skládá z modulu.</span><span class="sxs-lookup"><span data-stu-id="46113-103">Declares the name of a module and introduces the definition of the variables, properties, events, and procedures that the module comprises.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46113-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46113-104">Syntax</span></span>  
  
```vb 
[ <attributelist> ] [ accessmodifier ]  Module name  
    [ statements ]  
End Module  
```  
  
## <a name="parts"></a><span data-ttu-id="46113-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="46113-105">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="46113-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="46113-106">Optional.</span></span> <span data-ttu-id="46113-107">V tématu [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="46113-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
 `accessmodifier`  
 <span data-ttu-id="46113-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="46113-108">Optional.</span></span> <span data-ttu-id="46113-109">Může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="46113-109">Can be one of the following:</span></span>  
  
-   [<span data-ttu-id="46113-110">Public</span><span class="sxs-lookup"><span data-stu-id="46113-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
-   [<span data-ttu-id="46113-111">Friend</span><span class="sxs-lookup"><span data-stu-id="46113-111">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
 <span data-ttu-id="46113-112">V tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="46113-112">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 `name`  
 <span data-ttu-id="46113-113">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="46113-113">Required.</span></span> <span data-ttu-id="46113-114">Název tohoto modulu.</span><span class="sxs-lookup"><span data-stu-id="46113-114">Name of this module.</span></span> <span data-ttu-id="46113-115">V tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="46113-115">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 `statements`  
 <span data-ttu-id="46113-116">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="46113-116">Optional.</span></span> <span data-ttu-id="46113-117">Příkazy, které definují proměnné, vlastnosti, události, postupy a vnořené typy tohoto modulu.</span><span class="sxs-lookup"><span data-stu-id="46113-117">Statements which define the variables, properties, events, procedures, and nested types of this module.</span></span>  
  
 `End Module`  
 <span data-ttu-id="46113-118">Ukončí `Module` definice.</span><span class="sxs-lookup"><span data-stu-id="46113-118">Terminates the `Module` definition.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46113-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="46113-119">Remarks</span></span>  
 <span data-ttu-id="46113-120">A `Module` definuje příkaz k dispozici v rámci svého oboru názvů odkazového typu.</span><span class="sxs-lookup"><span data-stu-id="46113-120">A `Module` statement defines a reference type available throughout its namespace.</span></span> <span data-ttu-id="46113-121">A *modulu* (někdy nazývané *standardní modulu*) je podobný na třídu, ale některé důležité rozdíly.</span><span class="sxs-lookup"><span data-stu-id="46113-121">A *module* (sometimes called a *standard module*)is similar to a class but with some important distinctions.</span></span> <span data-ttu-id="46113-122">Každý modul se přesně jedna instance a není nutné vytvořit či přiřazený k proměnné.</span><span class="sxs-lookup"><span data-stu-id="46113-122">Every module has exactly one instance and does not need to be created or assigned to a variable.</span></span> <span data-ttu-id="46113-123">Moduly nepodporují dědičnosti nebo implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="46113-123">Modules do not support inheritance or implement interfaces.</span></span> <span data-ttu-id="46113-124">Všimněte si, že modul není *typ* v tom smyslu, že třídu nebo strukturu – nelze deklarovat jako programovací element mít datový typ modulu.</span><span class="sxs-lookup"><span data-stu-id="46113-124">Notice that a module is not a *type* in the sense that a class or structure is — you cannot declare a programming element to have the data type of a module.</span></span>  
  
 <span data-ttu-id="46113-125">Můžete použít `Module` jenom na úrovni oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="46113-125">You can use `Module` only at namespace level.</span></span> <span data-ttu-id="46113-126">To znamená *deklarace kontextu* pro modul musí být zdrojový soubor nebo obor názvů a nemůže být třída, struktura, modulu, rozhraní, postup nebo bloku.</span><span class="sxs-lookup"><span data-stu-id="46113-126">This means the *declaration context* for a module must be a source file or namespace, and cannot be a class, structure, module, interface, procedure, or block.</span></span> <span data-ttu-id="46113-127">Nelze vnořit modul v rámci jiný modul, nebo libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="46113-127">You cannot nest a module within another module, or within any type.</span></span> <span data-ttu-id="46113-128">Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="46113-128">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="46113-129">Modul má stejnou dobu života jako programu.</span><span class="sxs-lookup"><span data-stu-id="46113-129">A module has the same lifetime as your program.</span></span> <span data-ttu-id="46113-130">Vzhledem k tomu, že jsou všechny její členy `Shared`, mají také životnosti rovnající se tohoto programu.</span><span class="sxs-lookup"><span data-stu-id="46113-130">Because its members are all `Shared`, they also have lifetimes equal to that of the program.</span></span>  
  
 <span data-ttu-id="46113-131">Moduly výchozí [Friend](../../../visual-basic/language-reference/modifiers/friend.md) přístup.</span><span class="sxs-lookup"><span data-stu-id="46113-131">Modules default to [Friend](../../../visual-basic/language-reference/modifiers/friend.md) access.</span></span> <span data-ttu-id="46113-132">Můžete nastavit jejich úrovně přístupu s modifikátory přístupu.</span><span class="sxs-lookup"><span data-stu-id="46113-132">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="46113-133">Další informace najdete v tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="46113-133">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="46113-134">Implicitně se všichni její členové modulu `Shared`.</span><span class="sxs-lookup"><span data-stu-id="46113-134">All members of a module are implicitly `Shared`.</span></span>  
  
## <a name="classes-and-modules"></a><span data-ttu-id="46113-135">Třídy a modulů</span><span class="sxs-lookup"><span data-stu-id="46113-135">Classes and Modules</span></span>  
 <span data-ttu-id="46113-136">Tyto prvky mít mnoho podobností, ale existuje několik důležitých rozdílů.</span><span class="sxs-lookup"><span data-stu-id="46113-136">These elements have many similarities, but there are some important differences as well.</span></span>  
  
-   <span data-ttu-id="46113-137">**Terminologie.**</span><span class="sxs-lookup"><span data-stu-id="46113-137">**Terminology.**</span></span> <span data-ttu-id="46113-138">Předchozí verze jazyka Visual Basic rozpoznat dva typy modulů: *třídy modulů* (.cls soubory) a *standardní moduly* (BAS soubory).</span><span class="sxs-lookup"><span data-stu-id="46113-138">Previous versions of Visual Basic recognize two types of modules: *class modules* (.cls files) and *standard modules* (.bas files).</span></span> <span data-ttu-id="46113-139">Aktuální verze volá tyto *třídy* a *moduly*, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="46113-139">The current version calls these *classes* and *modules*, respectively.</span></span>  
  
-   <span data-ttu-id="46113-140">**Sdílení členové.**</span><span class="sxs-lookup"><span data-stu-id="46113-140">**Shared Members.**</span></span> <span data-ttu-id="46113-141">Můžete určit, zda je sdílenou člena třídy nebo instance člena.</span><span class="sxs-lookup"><span data-stu-id="46113-141">You can control whether a member of a class is a shared or instance member.</span></span>  
  
-   <span data-ttu-id="46113-142">**Objekt orientace.**</span><span class="sxs-lookup"><span data-stu-id="46113-142">**Object Orientation.**</span></span> <span data-ttu-id="46113-143">Třídy jsou objektově orientované, ale nejsou moduly.</span><span class="sxs-lookup"><span data-stu-id="46113-143">Classes are object-oriented, but modules are not.</span></span> <span data-ttu-id="46113-144">Proto pouze třídy se dá vytvořit instance jako objekty.</span><span class="sxs-lookup"><span data-stu-id="46113-144">So only classes can be instantiated as objects.</span></span> <span data-ttu-id="46113-145">Další informace najdete v tématu [objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span><span class="sxs-lookup"><span data-stu-id="46113-145">For more information, see [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="46113-146">Pravidla</span><span class="sxs-lookup"><span data-stu-id="46113-146">Rules</span></span>  
  
-   <span data-ttu-id="46113-147">**Modifikátory.**</span><span class="sxs-lookup"><span data-stu-id="46113-147">**Modifiers.**</span></span> <span data-ttu-id="46113-148">Všichni členové modulu jsou implicitně [sdílené](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="46113-148">All module members are implicitly [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="46113-149">Nelze použít `Shared` – klíčové slovo deklarace členem a nelze změnit sdílený stav kteréhokoli člena.</span><span class="sxs-lookup"><span data-stu-id="46113-149">You cannot use the `Shared` keyword when declaring a member, and you cannot alter the shared status of any member.</span></span>  
  
-   <span data-ttu-id="46113-150">**Dědičnost.**</span><span class="sxs-lookup"><span data-stu-id="46113-150">**Inheritance.**</span></span> <span data-ttu-id="46113-151">Modul nemůže Zdědit z libovolného typu, jiné než <xref:System.Object>, ze které všechny moduly dědí.</span><span class="sxs-lookup"><span data-stu-id="46113-151">A module cannot inherit from any type other than <xref:System.Object>, from which all modules inherit.</span></span> <span data-ttu-id="46113-152">Konkrétně jeden modul nemůže Zdědit z jiné.</span><span class="sxs-lookup"><span data-stu-id="46113-152">In particular, one module cannot inherit from another.</span></span>  
  
     <span data-ttu-id="46113-153">Nelze použít [dědí příkaz](../../../visual-basic/language-reference/statements/inherits-statement.md) v definici modulu i k určení <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="46113-153">You cannot use the [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md) in a module definition, even to specify <xref:System.Object>.</span></span>  
  
-   <span data-ttu-id="46113-154">**Výchozí vlastnost.**</span><span class="sxs-lookup"><span data-stu-id="46113-154">**Default Property.**</span></span> <span data-ttu-id="46113-155">V modulu nelze definovat všechny výchozí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="46113-155">You cannot define any default properties in a module.</span></span> <span data-ttu-id="46113-156">Další informace najdete v tématu [výchozí](../../../visual-basic/language-reference/modifiers/default.md).</span><span class="sxs-lookup"><span data-stu-id="46113-156">For more information, see [Default](../../../visual-basic/language-reference/modifiers/default.md).</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="46113-157">Chování</span><span class="sxs-lookup"><span data-stu-id="46113-157">Behavior</span></span>  
  
-   <span data-ttu-id="46113-158">**Úroveň přístupu.**</span><span class="sxs-lookup"><span data-stu-id="46113-158">**Access Level.**</span></span> <span data-ttu-id="46113-159">V modulu můžou deklarovat každého člena s vlastní úrovně přístupu.</span><span class="sxs-lookup"><span data-stu-id="46113-159">Within a module, you can declare each member with its own access level.</span></span> <span data-ttu-id="46113-160">Výchozí modul členy [veřejné](../../../visual-basic/language-reference/modifiers/public.md) přístup kromě proměnných a konstant, které používá výchozí [privátní](../../../visual-basic/language-reference/modifiers/private.md) přístup.</span><span class="sxs-lookup"><span data-stu-id="46113-160">Module members default to [Public](../../../visual-basic/language-reference/modifiers/public.md) access, except variables and constants, which default to [Private](../../../visual-basic/language-reference/modifiers/private.md) access.</span></span> <span data-ttu-id="46113-161">Pokud modul má omezený přístup k více než jeden z jejích členů, úroveň přístupu zadaný modul přednost.</span><span class="sxs-lookup"><span data-stu-id="46113-161">When a module has more restricted access than one of its members, the specified module access level takes precedence.</span></span>  
  
-   <span data-ttu-id="46113-162">**Rozsah.**</span><span class="sxs-lookup"><span data-stu-id="46113-162">**Scope.**</span></span> <span data-ttu-id="46113-163">Modul je v oboru v rámci svého oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="46113-163">A module is in scope throughout its namespace.</span></span>  
  
     <span data-ttu-id="46113-164">Rozsah všech členů modulu je celý modulu.</span><span class="sxs-lookup"><span data-stu-id="46113-164">The scope of every module member is the entire module.</span></span> <span data-ttu-id="46113-165">Všimněte si, že všichni členové podstoupit *zadejte povýšení*, což způsobí, že jejich obor, který má být převeden na obor názvů, který obsahuje modul.</span><span class="sxs-lookup"><span data-stu-id="46113-165">Notice that all members undergo *type promotion*, which causes their scope to be promoted to the namespace containing the module.</span></span> <span data-ttu-id="46113-166">Další informace najdete v tématu [propagace typu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="46113-166">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span></span>  
  
-   <span data-ttu-id="46113-167">**Kvalifikace.**</span><span class="sxs-lookup"><span data-stu-id="46113-167">**Qualification.**</span></span> <span data-ttu-id="46113-168">Máte více modulů v projektu a můžou deklarovat členy se stejným názvem ve dvou nebo více modulů.</span><span class="sxs-lookup"><span data-stu-id="46113-168">You can have multiple modules in a project, and you can declare members with the same name in two or more modules.</span></span> <span data-ttu-id="46113-169">Pokud je odkaz z mimo tento modul však musíte před všechny odkazy na člena s názvem příslušný modul.</span><span class="sxs-lookup"><span data-stu-id="46113-169">However, you must qualify any reference to such a member with the appropriate module name if the reference is from outside that module.</span></span> <span data-ttu-id="46113-170">Další informace najdete v tématu [odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="46113-170">For more information, see [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="46113-171">Příklad</span><span class="sxs-lookup"><span data-stu-id="46113-171">Example</span></span>  
 [!code-vb[VbVbalrStatements#69](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/module-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="46113-172">Viz také</span><span class="sxs-lookup"><span data-stu-id="46113-172">See Also</span></span>  
 [<span data-ttu-id="46113-173">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="46113-173">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="46113-174">Příkaz Namespace</span><span class="sxs-lookup"><span data-stu-id="46113-174">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [<span data-ttu-id="46113-175">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="46113-175">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="46113-176">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="46113-176">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="46113-177">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="46113-177">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="46113-178">Propagace typu</span><span class="sxs-lookup"><span data-stu-id="46113-178">Type Promotion</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
