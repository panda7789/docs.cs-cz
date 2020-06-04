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
ms.openlocfilehash: 7aed6bec21bd484cca019b061bd5915de13a9eb8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402704"
---
# <a name="shadows-visual-basic"></a><span data-ttu-id="04ac5-102">Shadows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04ac5-102">Shadows (Visual Basic)</span></span>

<span data-ttu-id="04ac5-103">Určuje, že deklarovaný programový prvek znovu deklaruje a skryje identicky pojmenovaný element nebo množinu přetížených prvků v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="04ac5-103">Specifies that a declared programming element redeclares and hides an identically named element, or set of overloaded elements, in a base class.</span></span>

## <a name="remarks"></a><span data-ttu-id="04ac5-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="04ac5-104">Remarks</span></span>

<span data-ttu-id="04ac5-105">Hlavní účel vytváření stínových kopií (který se také označuje jako *skrytí podle názvu*) je zachování definice členů vaší třídy.</span><span class="sxs-lookup"><span data-stu-id="04ac5-105">The main purpose of shadowing (which is also known as *hiding by name*) is to preserve the definition of your class members.</span></span> <span data-ttu-id="04ac5-106">Základní třída se může podrobit změně, která vytvoří element se stejným názvem jako ten, který jste už definovali.</span><span class="sxs-lookup"><span data-stu-id="04ac5-106">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="04ac5-107">Pokud k tomu dojde, `Shadows` Modifikátor vynutí, aby byly odkazy prostřednictvím vaší třídy přeloženy na člen, který jste definovali, místo na nový prvek základní třídy.</span><span class="sxs-lookup"><span data-stu-id="04ac5-107">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>

<span data-ttu-id="04ac5-108">Jak Stínová, tak i přepsání předefinují zděděný element, ale existují významné rozdíly mezi těmito dvěma přístupy.</span><span class="sxs-lookup"><span data-stu-id="04ac5-108">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="04ac5-109">Další informace najdete v tématu [vytváření stínových kopií v Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="04ac5-109">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>

## <a name="rules"></a><span data-ttu-id="04ac5-110">Pravidla</span><span class="sxs-lookup"><span data-stu-id="04ac5-110">Rules</span></span>

- <span data-ttu-id="04ac5-111">**Kontext deklarace**</span><span class="sxs-lookup"><span data-stu-id="04ac5-111">**Declaration Context.**</span></span> <span data-ttu-id="04ac5-112">Můžete použít `Shadows` pouze na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="04ac5-112">You can use `Shadows` only at class level.</span></span> <span data-ttu-id="04ac5-113">To znamená, že kontext deklarace pro `Shadows` prvek musí být třída a nemůže se jednat o zdrojový soubor, obor názvů, rozhraní, modul, strukturu nebo proceduru.</span><span class="sxs-lookup"><span data-stu-id="04ac5-113">This means the declaration context for a `Shadows` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

  <span data-ttu-id="04ac5-114">V jednom příkazu deklarace lze deklarovat pouze jeden element shadowing.</span><span class="sxs-lookup"><span data-stu-id="04ac5-114">You can declare only one shadowing element in a single declaration statement.</span></span>

- <span data-ttu-id="04ac5-115">**Kombinované modifikátory.**</span><span class="sxs-lookup"><span data-stu-id="04ac5-115">**Combined Modifiers.**</span></span> <span data-ttu-id="04ac5-116">Nelze zadat `Shadows` společně s `Overloads` , `Overrides` nebo `Static` ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="04ac5-116">You cannot specify `Shadows` together with `Overloads`, `Overrides`, or `Static` in the same declaration.</span></span>

- <span data-ttu-id="04ac5-117">**Typy prvků.**</span><span class="sxs-lookup"><span data-stu-id="04ac5-117">**Element Types.**</span></span> <span data-ttu-id="04ac5-118">Můžete vystínovat jakýkoliv druh deklarovaného prvku s jakýmkoli jiným druhem.</span><span class="sxs-lookup"><span data-stu-id="04ac5-118">You can shadow any kind of declared element with any other kind.</span></span> <span data-ttu-id="04ac5-119">Pokud nastínete vlastnost nebo proceduru pomocí jiné vlastnosti nebo procedury, parametry a návratový typ nemusejí odpovídat hodnotám ve vlastnosti nebo proceduře základní třídy.</span><span class="sxs-lookup"><span data-stu-id="04ac5-119">If you shadow a property or procedure with another property or procedure, the parameters and the return type do not have to match those in the base class property or procedure.</span></span>

- <span data-ttu-id="04ac5-120">**Přístup k.**</span><span class="sxs-lookup"><span data-stu-id="04ac5-120">**Accessing.**</span></span> <span data-ttu-id="04ac5-121">Stínovaný element v základní třídě není obvykle k dispozici v odvozené třídě, která ho nastínuje.</span><span class="sxs-lookup"><span data-stu-id="04ac5-121">The shadowed element in the base class is normally unavailable from within the derived class that shadows it.</span></span> <span data-ttu-id="04ac5-122">Platí však následující požadavky.</span><span class="sxs-lookup"><span data-stu-id="04ac5-122">However, the following considerations apply.</span></span>

  - <span data-ttu-id="04ac5-123">Pokud není stínový element přístupný z kódu, který se na něj odkazuje, odkaz je přeložen na stínovaný element.</span><span class="sxs-lookup"><span data-stu-id="04ac5-123">If the shadowing element is not accessible from the code referring to it, the reference is resolved to the shadowed element.</span></span> <span data-ttu-id="04ac5-124">Například pokud `Private` prvek vystínuje element základní třídy, kód, který nemá oprávnění pro přístup k `Private` elementu, přistupuje k elementu základní třídy.</span><span class="sxs-lookup"><span data-stu-id="04ac5-124">For example, if a `Private` element shadows a base class element, code that does not have permission to access the `Private` element accesses the base class element instead.</span></span>

  - <span data-ttu-id="04ac5-125">Pokud vytvoříte stín elementu, můžete ke stínovaný element přistupovat i přes objekt deklarovaný s typem základní třídy.</span><span class="sxs-lookup"><span data-stu-id="04ac5-125">If you shadow an element, you can still access the shadowed element through an object declared with the type of the base class.</span></span> <span data-ttu-id="04ac5-126">K němu máte přístup i přes `MyBase` .</span><span class="sxs-lookup"><span data-stu-id="04ac5-126">You can also access it through `MyBase`.</span></span>

<span data-ttu-id="04ac5-127">`Shadows`V těchto kontextech lze použít modifikátor:</span><span class="sxs-lookup"><span data-stu-id="04ac5-127">The `Shadows` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="04ac5-128">Class – příkaz</span><span class="sxs-lookup"><span data-stu-id="04ac5-128">Class Statement</span></span>](../statements/class-statement.md)

- [<span data-ttu-id="04ac5-129">Const – příkaz</span><span class="sxs-lookup"><span data-stu-id="04ac5-129">Const Statement</span></span>](../statements/const-statement.md)

- [<span data-ttu-id="04ac5-130">Declare – příkaz</span><span class="sxs-lookup"><span data-stu-id="04ac5-130">Declare Statement</span></span>](../statements/declare-statement.md)

- [<span data-ttu-id="04ac5-131">Delegate – příkaz</span><span class="sxs-lookup"><span data-stu-id="04ac5-131">Delegate Statement</span></span>](../statements/delegate-statement.md)

- [<span data-ttu-id="04ac5-132">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="04ac5-132">Dim Statement</span></span>](../statements/dim-statement.md)

- [<span data-ttu-id="04ac5-133">Enum – příkaz</span><span class="sxs-lookup"><span data-stu-id="04ac5-133">Enum Statement</span></span>](../statements/enum-statement.md)

- [<span data-ttu-id="04ac5-134">Event – příkaz</span><span class="sxs-lookup"><span data-stu-id="04ac5-134">Event Statement</span></span>](../statements/event-statement.md)

- [<span data-ttu-id="04ac5-135">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="04ac5-135">Function Statement</span></span>](../statements/function-statement.md)

- [<span data-ttu-id="04ac5-136">Interface – příkaz</span><span class="sxs-lookup"><span data-stu-id="04ac5-136">Interface Statement</span></span>](../statements/interface-statement.md)

- [<span data-ttu-id="04ac5-137">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="04ac5-137">Property Statement</span></span>](../statements/property-statement.md)

- [<span data-ttu-id="04ac5-138">Structure – příkaz</span><span class="sxs-lookup"><span data-stu-id="04ac5-138">Structure Statement</span></span>](../statements/structure-statement.md)

- [<span data-ttu-id="04ac5-139">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="04ac5-139">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="04ac5-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="04ac5-140">See also</span></span>

- [<span data-ttu-id="04ac5-141">Shared</span><span class="sxs-lookup"><span data-stu-id="04ac5-141">Shared</span></span>](shared.md)
- [<span data-ttu-id="04ac5-142">Tras</span><span class="sxs-lookup"><span data-stu-id="04ac5-142">Static</span></span>](static.md)
- [<span data-ttu-id="04ac5-143">Hlášen</span><span class="sxs-lookup"><span data-stu-id="04ac5-143">Private</span></span>](private.md)
- [<span data-ttu-id="04ac5-144">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="04ac5-144">Me, My, MyBase, and MyClass</span></span>](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="04ac5-145">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="04ac5-145">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="04ac5-146">MustOverride</span><span class="sxs-lookup"><span data-stu-id="04ac5-146">MustOverride</span></span>](mustoverride.md)
- [<span data-ttu-id="04ac5-147">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="04ac5-147">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="04ac5-148">Přetížení</span><span class="sxs-lookup"><span data-stu-id="04ac5-148">Overloads</span></span>](overloads.md)
- [<span data-ttu-id="04ac5-149">Overridable</span><span class="sxs-lookup"><span data-stu-id="04ac5-149">Overridable</span></span>](overridable.md)
- [<span data-ttu-id="04ac5-150">Přepsání</span><span class="sxs-lookup"><span data-stu-id="04ac5-150">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="04ac5-151">Stínění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="04ac5-151">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
