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
ms.openlocfilehash: c9dfff99e2634b79ad6b44721f40583d21c9b98e
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67664134"
---
# <a name="shadows-visual-basic"></a><span data-ttu-id="27317-102">Shadows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27317-102">Shadows (Visual Basic)</span></span>

<span data-ttu-id="27317-103">Určuje, že deklarovaný programový prvek znovu deklaruje a skryje identicky pojmenovanou elementu, nebo sadu přetížených elementů v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="27317-103">Specifies that a declared programming element redeclares and hides an identically named element, or set of overloaded elements, in a base class.</span></span>

## <a name="remarks"></a><span data-ttu-id="27317-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="27317-104">Remarks</span></span>

<span data-ttu-id="27317-105">Hlavním účelem stínový provoz (což je také označován jako *skrývání podle názvu*) je zachovat definice členů třídy.</span><span class="sxs-lookup"><span data-stu-id="27317-105">The main purpose of shadowing (which is also known as *hiding by name*) is to preserve the definition of your class members.</span></span> <span data-ttu-id="27317-106">Základní třídy může být změnu, která vytvoří element se stejným názvem jako ten, který je již definován.</span><span class="sxs-lookup"><span data-stu-id="27317-106">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="27317-107">Pokud k tomu dojde, `Shadows` modifikátor vynutí odkazuje prostřednictvím vaší třídy, které je potřeba vyřešit členovi definované, namísto nový prvek základní třídy.</span><span class="sxs-lookup"><span data-stu-id="27317-107">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>

<span data-ttu-id="27317-108">Jak stínováním a přepsáním znovu definovat element zděděné, ale existují významné rozdíly mezi dvěma přístupy.</span><span class="sxs-lookup"><span data-stu-id="27317-108">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="27317-109">Další informace najdete v tématu [stínění v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="27317-109">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>

## <a name="rules"></a><span data-ttu-id="27317-110">pravidla</span><span class="sxs-lookup"><span data-stu-id="27317-110">Rules</span></span>

- <span data-ttu-id="27317-111">**Místní deklarace.**</span><span class="sxs-lookup"><span data-stu-id="27317-111">**Declaration Context.**</span></span> <span data-ttu-id="27317-112">Můžete použít `Shadows` pouze na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="27317-112">You can use `Shadows` only at class level.</span></span> <span data-ttu-id="27317-113">To znamená, že deklarace kontext `Shadows` elementu musí být třída a nemůže být zdrojový soubor, obor názvů, rozhraní, modul, struktury nebo proceduru.</span><span class="sxs-lookup"><span data-stu-id="27317-113">This means the declaration context for a `Shadows` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

  <span data-ttu-id="27317-114">Je možné deklarovat pouze jeden element stínového provozu v jedné deklaraci příkazu.</span><span class="sxs-lookup"><span data-stu-id="27317-114">You can declare only one shadowing element in a single declaration statement.</span></span>

- <span data-ttu-id="27317-115">**Kombinované modifikátory.**</span><span class="sxs-lookup"><span data-stu-id="27317-115">**Combined Modifiers.**</span></span> <span data-ttu-id="27317-116">Nelze zadat `Shadows` spolu s `Overloads`, `Overrides`, nebo `Static` ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="27317-116">You cannot specify `Shadows` together with `Overloads`, `Overrides`, or `Static` in the same declaration.</span></span>

- <span data-ttu-id="27317-117">**Typy elementů.**</span><span class="sxs-lookup"><span data-stu-id="27317-117">**Element Types.**</span></span> <span data-ttu-id="27317-118">Můžete stínové jakýkoli druh element deklarovaný pomocí jakéhokoli druhu.</span><span class="sxs-lookup"><span data-stu-id="27317-118">You can shadow any kind of declared element with any other kind.</span></span> <span data-ttu-id="27317-119">Pokud jste stínovou kopii se vlastnost nebo procedura s jinou vlastnost nebo procedura, parametry a návratovým typem není potřeba odpovídají polím v základní třídě vlastnost nebo procedura.</span><span class="sxs-lookup"><span data-stu-id="27317-119">If you shadow a property or procedure with another property or procedure, the parameters and the return type do not have to match those in the base class property or procedure.</span></span>

- <span data-ttu-id="27317-120">**Přístup k.**</span><span class="sxs-lookup"><span data-stu-id="27317-120">**Accessing.**</span></span> <span data-ttu-id="27317-121">Stínovaný element v základní třídě je obvykle nedostupná z v rámci odvozené třídy, která zastiňuje ho.</span><span class="sxs-lookup"><span data-stu-id="27317-121">The shadowed element in the base class is normally unavailable from within the derived class that shadows it.</span></span> <span data-ttu-id="27317-122">Nicméně platí následující aspekty.</span><span class="sxs-lookup"><span data-stu-id="27317-122">However, the following considerations apply.</span></span>

  - <span data-ttu-id="27317-123">Pokud stínového provozu element není přístupné z kódu na ni odkazuje, odkaz je přeložen na stínovaný elementu.</span><span class="sxs-lookup"><span data-stu-id="27317-123">If the shadowing element is not accessible from the code referring to it, the reference is resolved to the shadowed element.</span></span> <span data-ttu-id="27317-124">Například pokud `Private` element zastiňuje prvek základní třídy, kód, který nemá oprávnění k přístupu `Private` element má přístup k elementu základní třídy místo toho.</span><span class="sxs-lookup"><span data-stu-id="27317-124">For example, if a `Private` element shadows a base class element, code that does not have permission to access the `Private` element accesses the base class element instead.</span></span>

  - <span data-ttu-id="27317-125">Pokud jste stínové elementu, budete k němu přístup stínovaný element prostřednictvím objektu, který deklarovat s typem základní třídy.</span><span class="sxs-lookup"><span data-stu-id="27317-125">If you shadow an element, you can still access the shadowed element through an object declared with the type of the base class.</span></span> <span data-ttu-id="27317-126">Můžete také k němu přístup prostřednictvím `MyBase`.</span><span class="sxs-lookup"><span data-stu-id="27317-126">You can also access it through `MyBase`.</span></span>

<span data-ttu-id="27317-127">`Shadows` Modifikátor lze použít v těchto kontextech:</span><span class="sxs-lookup"><span data-stu-id="27317-127">The `Shadows` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="27317-128">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="27317-128">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)

- [<span data-ttu-id="27317-129">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="27317-129">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)

- [<span data-ttu-id="27317-130">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="27317-130">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)

- [<span data-ttu-id="27317-131">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="27317-131">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)

- [<span data-ttu-id="27317-132">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="27317-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)

- [<span data-ttu-id="27317-133">Příkaz Enum</span><span class="sxs-lookup"><span data-stu-id="27317-133">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)

- [<span data-ttu-id="27317-134">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="27317-134">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)

- [<span data-ttu-id="27317-135">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="27317-135">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- [<span data-ttu-id="27317-136">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="27317-136">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)

- [<span data-ttu-id="27317-137">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="27317-137">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- [<span data-ttu-id="27317-138">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="27317-138">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)

- [<span data-ttu-id="27317-139">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="27317-139">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="27317-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="27317-140">See also</span></span>

- [<span data-ttu-id="27317-141">Shared</span><span class="sxs-lookup"><span data-stu-id="27317-141">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="27317-142">Static</span><span class="sxs-lookup"><span data-stu-id="27317-142">Static</span></span>](../../../visual-basic/language-reference/modifiers/static.md)
- [<span data-ttu-id="27317-143">Private</span><span class="sxs-lookup"><span data-stu-id="27317-143">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="27317-144">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="27317-144">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="27317-145">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="27317-145">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="27317-146">MustOverride</span><span class="sxs-lookup"><span data-stu-id="27317-146">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="27317-147">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="27317-147">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="27317-148">Overloads</span><span class="sxs-lookup"><span data-stu-id="27317-148">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="27317-149">Overridable</span><span class="sxs-lookup"><span data-stu-id="27317-149">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="27317-150">Overrides</span><span class="sxs-lookup"><span data-stu-id="27317-150">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="27317-151">Stínění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="27317-151">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
