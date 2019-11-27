---
title: Shadows
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
ms.openlocfilehash: e9a423fa69ad1dcd8c1d4a5b7085e5b5da548f93
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351265"
---
# <a name="shadows-visual-basic"></a><span data-ttu-id="5852d-102">Shadows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5852d-102">Shadows (Visual Basic)</span></span>

<span data-ttu-id="5852d-103">Určuje, že deklarovaný programový prvek znovu deklaruje a skryje identicky pojmenovaný element nebo množinu přetížených prvků v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="5852d-103">Specifies that a declared programming element redeclares and hides an identically named element, or set of overloaded elements, in a base class.</span></span>

## <a name="remarks"></a><span data-ttu-id="5852d-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5852d-104">Remarks</span></span>

<span data-ttu-id="5852d-105">Hlavní účel vytváření stínových kopií (který se také označuje jako *skrytí podle názvu*) je zachování definice členů vaší třídy.</span><span class="sxs-lookup"><span data-stu-id="5852d-105">The main purpose of shadowing (which is also known as *hiding by name*) is to preserve the definition of your class members.</span></span> <span data-ttu-id="5852d-106">Základní třída se může podrobit změně, která vytvoří element se stejným názvem jako ten, který jste už definovali.</span><span class="sxs-lookup"><span data-stu-id="5852d-106">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="5852d-107">Pokud k tomu dojde, modifikátor `Shadows` vynutí, aby byly odkazy prostřednictvím vaší třídy přeloženy na člen, který jste definovali, místo na nový prvek základní třídy.</span><span class="sxs-lookup"><span data-stu-id="5852d-107">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>

<span data-ttu-id="5852d-108">Jak Stínová, tak i přepsání předefinují zděděný element, ale existují významné rozdíly mezi těmito dvěma přístupy.</span><span class="sxs-lookup"><span data-stu-id="5852d-108">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="5852d-109">Další informace najdete v tématu [vytváření stínových kopií v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="5852d-109">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>

## <a name="rules"></a><span data-ttu-id="5852d-110">Pravidla</span><span class="sxs-lookup"><span data-stu-id="5852d-110">Rules</span></span>

- <span data-ttu-id="5852d-111">**Kontext deklarace**</span><span class="sxs-lookup"><span data-stu-id="5852d-111">**Declaration Context.**</span></span> <span data-ttu-id="5852d-112">`Shadows` lze použít pouze na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="5852d-112">You can use `Shadows` only at class level.</span></span> <span data-ttu-id="5852d-113">To znamená, že kontext deklarace pro prvek `Shadows` musí být třída a nemůže se jednat o zdrojový soubor, obor názvů, rozhraní, modul, strukturu nebo proceduru.</span><span class="sxs-lookup"><span data-stu-id="5852d-113">This means the declaration context for a `Shadows` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

  <span data-ttu-id="5852d-114">V jednom příkazu deklarace lze deklarovat pouze jeden element shadowing.</span><span class="sxs-lookup"><span data-stu-id="5852d-114">You can declare only one shadowing element in a single declaration statement.</span></span>

- <span data-ttu-id="5852d-115">**Kombinované modifikátory.**</span><span class="sxs-lookup"><span data-stu-id="5852d-115">**Combined Modifiers.**</span></span> <span data-ttu-id="5852d-116">V rámci stejné deklarace nelze zadat `Shadows` společně s `Overloads`, `Overrides`nebo `Static`.</span><span class="sxs-lookup"><span data-stu-id="5852d-116">You cannot specify `Shadows` together with `Overloads`, `Overrides`, or `Static` in the same declaration.</span></span>

- <span data-ttu-id="5852d-117">**Typy prvků.**</span><span class="sxs-lookup"><span data-stu-id="5852d-117">**Element Types.**</span></span> <span data-ttu-id="5852d-118">Můžete vystínovat jakýkoliv druh deklarovaného prvku s jakýmkoli jiným druhem.</span><span class="sxs-lookup"><span data-stu-id="5852d-118">You can shadow any kind of declared element with any other kind.</span></span> <span data-ttu-id="5852d-119">Pokud nastínete vlastnost nebo proceduru pomocí jiné vlastnosti nebo procedury, parametry a návratový typ nemusejí odpovídat hodnotám ve vlastnosti nebo proceduře základní třídy.</span><span class="sxs-lookup"><span data-stu-id="5852d-119">If you shadow a property or procedure with another property or procedure, the parameters and the return type do not have to match those in the base class property or procedure.</span></span>

- <span data-ttu-id="5852d-120">**Přístup k.**</span><span class="sxs-lookup"><span data-stu-id="5852d-120">**Accessing.**</span></span> <span data-ttu-id="5852d-121">Stínovaný element v základní třídě není obvykle k dispozici v odvozené třídě, která ho nastínuje.</span><span class="sxs-lookup"><span data-stu-id="5852d-121">The shadowed element in the base class is normally unavailable from within the derived class that shadows it.</span></span> <span data-ttu-id="5852d-122">Platí však následující požadavky.</span><span class="sxs-lookup"><span data-stu-id="5852d-122">However, the following considerations apply.</span></span>

  - <span data-ttu-id="5852d-123">Pokud není stínový element přístupný z kódu, který se na něj odkazuje, odkaz je přeložen na stínovaný element.</span><span class="sxs-lookup"><span data-stu-id="5852d-123">If the shadowing element is not accessible from the code referring to it, the reference is resolved to the shadowed element.</span></span> <span data-ttu-id="5852d-124">Například pokud `Private` element stínování elementu základní třídy, kód, který nemá oprávnění pro přístup k `Private` elementu, přistupuje k elementu základní třídy místo toho.</span><span class="sxs-lookup"><span data-stu-id="5852d-124">For example, if a `Private` element shadows a base class element, code that does not have permission to access the `Private` element accesses the base class element instead.</span></span>

  - <span data-ttu-id="5852d-125">Pokud vytvoříte stín elementu, můžete ke stínovaný element přistupovat i přes objekt deklarovaný s typem základní třídy.</span><span class="sxs-lookup"><span data-stu-id="5852d-125">If you shadow an element, you can still access the shadowed element through an object declared with the type of the base class.</span></span> <span data-ttu-id="5852d-126">K němu taky můžete přistupovat prostřednictvím `MyBase`.</span><span class="sxs-lookup"><span data-stu-id="5852d-126">You can also access it through `MyBase`.</span></span>

<span data-ttu-id="5852d-127">V těchto kontextech lze použít modifikátor `Shadows`:</span><span class="sxs-lookup"><span data-stu-id="5852d-127">The `Shadows` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="5852d-128">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="5852d-128">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)

- [<span data-ttu-id="5852d-129">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="5852d-129">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)

- [<span data-ttu-id="5852d-130">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="5852d-130">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)

- [<span data-ttu-id="5852d-131">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="5852d-131">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)

- [<span data-ttu-id="5852d-132">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="5852d-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)

- [<span data-ttu-id="5852d-133">Příkaz Enum</span><span class="sxs-lookup"><span data-stu-id="5852d-133">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)

- [<span data-ttu-id="5852d-134">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="5852d-134">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)

- [<span data-ttu-id="5852d-135">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="5852d-135">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- [<span data-ttu-id="5852d-136">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="5852d-136">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)

- [<span data-ttu-id="5852d-137">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="5852d-137">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- [<span data-ttu-id="5852d-138">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="5852d-138">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)

- [<span data-ttu-id="5852d-139">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="5852d-139">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="5852d-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5852d-140">See also</span></span>

- [<span data-ttu-id="5852d-141">Shared</span><span class="sxs-lookup"><span data-stu-id="5852d-141">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="5852d-142">Static</span><span class="sxs-lookup"><span data-stu-id="5852d-142">Static</span></span>](../../../visual-basic/language-reference/modifiers/static.md)
- [<span data-ttu-id="5852d-143">Private</span><span class="sxs-lookup"><span data-stu-id="5852d-143">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="5852d-144">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="5852d-144">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="5852d-145">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="5852d-145">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="5852d-146">MustOverride</span><span class="sxs-lookup"><span data-stu-id="5852d-146">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="5852d-147">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="5852d-147">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="5852d-148">Overloads</span><span class="sxs-lookup"><span data-stu-id="5852d-148">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="5852d-149">Overridable</span><span class="sxs-lookup"><span data-stu-id="5852d-149">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="5852d-150">Overrides</span><span class="sxs-lookup"><span data-stu-id="5852d-150">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="5852d-151">Stínování v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5852d-151">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
