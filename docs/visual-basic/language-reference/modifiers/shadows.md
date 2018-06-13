---
title: Shadows (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Shadows
- shadows
helpviewer_keywords:
- shadowing
- duplicate names [Visual Basic]
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic]
- names [Visual Basic], shadowing
ms.assetid: 6bf687cd-0544-4797-b51b-911125ec57c6
ms.openlocfilehash: 4ca4ec48ee63b71447056a2c5cb68e8948f27ad0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604647"
---
# <a name="shadows-visual-basic"></a><span data-ttu-id="1ebc8-102">Shadows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ebc8-102">Shadows (Visual Basic)</span></span>
<span data-ttu-id="1ebc8-103">Určuje, že deklarované programovací element redeclares a skryje stejně jako s názvem prvku, nebo sadu přetížené elementů v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="1ebc8-103">Specifies that a declared programming element redeclares and hides an identically named element, or set of overloaded elements, in a base class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ebc8-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1ebc8-104">Remarks</span></span>  
 <span data-ttu-id="1ebc8-105">Hlavním účelem stínový provoz (což je také označován jako *skrytí podle názvu*) se zachovat definici členy vaší třídy.</span><span class="sxs-lookup"><span data-stu-id="1ebc8-105">The main purpose of shadowing (which is also known as *hiding by name*) is to preserve the definition of your class members.</span></span> <span data-ttu-id="1ebc8-106">Základní třída může podstoupit změnu, která vytvoří element se stejným názvem jako jeden, který je již definován.</span><span class="sxs-lookup"><span data-stu-id="1ebc8-106">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="1ebc8-107">V takovém případě `Shadows` modifikátor vynutí odkazuje prostřednictvím vaší třídy přeloží na člen definované, místo do nového elementu základní třídy.</span><span class="sxs-lookup"><span data-stu-id="1ebc8-107">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>  
  
 <span data-ttu-id="1ebc8-108">Jak stínováním a přepsáním znovu definovat zděděné elementu, ale existují významné rozdíly mezi dva přístupy.</span><span class="sxs-lookup"><span data-stu-id="1ebc8-108">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="1ebc8-109">Další informace najdete v tématu [stínový provoz v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="1ebc8-109">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="1ebc8-110">Pravidla</span><span class="sxs-lookup"><span data-stu-id="1ebc8-110">Rules</span></span>  
  
-   <span data-ttu-id="1ebc8-111">**Kontext deklarace.**</span><span class="sxs-lookup"><span data-stu-id="1ebc8-111">**Declaration Context.**</span></span> <span data-ttu-id="1ebc8-112">Můžete použít `Shadows` jenom na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="1ebc8-112">You can use `Shadows` only at class level.</span></span> <span data-ttu-id="1ebc8-113">To znamená kontext deklarace `Shadows` element musí být třída a nesmí být zdrojový soubor, obor názvů, rozhraní, modul, struktura nebo postup.</span><span class="sxs-lookup"><span data-stu-id="1ebc8-113">This means the declaration context for a `Shadows` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>  
  
     <span data-ttu-id="1ebc8-114">Lze deklarovat pouze jeden element stínového provozu v jediné deklaraci příkazu.</span><span class="sxs-lookup"><span data-stu-id="1ebc8-114">You can declare only one shadowing element in a single declaration statement.</span></span>  
  
-   <span data-ttu-id="1ebc8-115">**Kombinovaná parametrů.**</span><span class="sxs-lookup"><span data-stu-id="1ebc8-115">**Combined Modifiers.**</span></span> <span data-ttu-id="1ebc8-116">Nelze zadat `Shadows` společně s `Overloads`, `Overrides`, nebo `Static` ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="1ebc8-116">You cannot specify `Shadows` together with `Overloads`, `Overrides`, or `Static` in the same declaration.</span></span>  
  
-   <span data-ttu-id="1ebc8-117">**Typy elementů.**</span><span class="sxs-lookup"><span data-stu-id="1ebc8-117">**Element Types.**</span></span> <span data-ttu-id="1ebc8-118">Můžete stínové jakýkoli druh deklarovaný element s jakéhokoli jiného typu.</span><span class="sxs-lookup"><span data-stu-id="1ebc8-118">You can shadow any kind of declared element with any other kind.</span></span> <span data-ttu-id="1ebc8-119">Pokud jste stínové vlastnosti nebo procedury s jinou vlastnost nebo postup, parametry a návratový typ nemusí se shodovat s hodnotami ve vlastnosti základní třídu nebo postupu.</span><span class="sxs-lookup"><span data-stu-id="1ebc8-119">If you shadow a property or procedure with another property or procedure, the parameters and the return type do not have to match those in the base class property or procedure.</span></span>  
  
-   <span data-ttu-id="1ebc8-120">**Přístup k.**</span><span class="sxs-lookup"><span data-stu-id="1ebc8-120">**Accessing.**</span></span> <span data-ttu-id="1ebc8-121">Element stíněné v základní třídě je obvykle ze není k dispozici v rámci odvozené třídy, stín ho.</span><span class="sxs-lookup"><span data-stu-id="1ebc8-121">The shadowed element in the base class is normally unavailable from within the derived class that shadows it.</span></span> <span data-ttu-id="1ebc8-122">Nicméně, platí následující aspekty.</span><span class="sxs-lookup"><span data-stu-id="1ebc8-122">However, the following considerations apply.</span></span>  
  
    -   <span data-ttu-id="1ebc8-123">Pokud element stínového provozu není přístupný z kódu na ně odkazovat, odkaz je přeložen na stíněné elementu.</span><span class="sxs-lookup"><span data-stu-id="1ebc8-123">If the shadowing element is not accessible from the code referring to it, the reference is resolved to the shadowed element.</span></span> <span data-ttu-id="1ebc8-124">Například pokud `Private` element shadows prvku základní třídy, kód, který nemá oprávnění k přístupu `Private` element přistupuje k prvku základní třídy místo.</span><span class="sxs-lookup"><span data-stu-id="1ebc8-124">For example, if a `Private` element shadows a base class element, code that does not have permission to access the `Private` element accesses the base class element instead.</span></span>  
  
    -   <span data-ttu-id="1ebc8-125">Pokud jste stínové element, můžete ke stíněné element prostřednictvím objektu deklarovat s typem základní třídy.</span><span class="sxs-lookup"><span data-stu-id="1ebc8-125">If you shadow an element, you can still access the shadowed element through an object declared with the type of the base class.</span></span> <span data-ttu-id="1ebc8-126">Můžete taky přejít přes `MyBase`.</span><span class="sxs-lookup"><span data-stu-id="1ebc8-126">You can also access it through `MyBase`.</span></span>  
  
 <span data-ttu-id="1ebc8-127">`Shadows` Modifikátor lze použít v těchto kontexty:</span><span class="sxs-lookup"><span data-stu-id="1ebc8-127">The `Shadows` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="1ebc8-128">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="1ebc8-128">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="1ebc8-129">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="1ebc8-129">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="1ebc8-130">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="1ebc8-130">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="1ebc8-131">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="1ebc8-131">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="1ebc8-132">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="1ebc8-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="1ebc8-133">Příkaz Enum</span><span class="sxs-lookup"><span data-stu-id="1ebc8-133">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="1ebc8-134">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="1ebc8-134">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="1ebc8-135">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="1ebc8-135">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="1ebc8-136">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="1ebc8-136">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="1ebc8-137">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="1ebc8-137">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="1ebc8-138">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="1ebc8-138">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="1ebc8-139">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="1ebc8-139">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="1ebc8-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="1ebc8-140">See Also</span></span>  
 [<span data-ttu-id="1ebc8-141">Shared</span><span class="sxs-lookup"><span data-stu-id="1ebc8-141">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
 [<span data-ttu-id="1ebc8-142">Static</span><span class="sxs-lookup"><span data-stu-id="1ebc8-142">Static</span></span>](../../../visual-basic/language-reference/modifiers/static.md)  
 [<span data-ttu-id="1ebc8-143">Private</span><span class="sxs-lookup"><span data-stu-id="1ebc8-143">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 [<span data-ttu-id="1ebc8-144">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="1ebc8-144">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="1ebc8-145">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="1ebc8-145">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [<span data-ttu-id="1ebc8-146">MustOverride</span><span class="sxs-lookup"><span data-stu-id="1ebc8-146">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [<span data-ttu-id="1ebc8-147">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="1ebc8-147">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [<span data-ttu-id="1ebc8-148">Overloads</span><span class="sxs-lookup"><span data-stu-id="1ebc8-148">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  
 [<span data-ttu-id="1ebc8-149">Overridable</span><span class="sxs-lookup"><span data-stu-id="1ebc8-149">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [<span data-ttu-id="1ebc8-150">Overrides</span><span class="sxs-lookup"><span data-stu-id="1ebc8-150">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="1ebc8-151">Stínový provoz v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1ebc8-151">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
