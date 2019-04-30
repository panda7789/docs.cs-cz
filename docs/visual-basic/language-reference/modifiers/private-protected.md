---
title: Private Protected. (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: fea43558ac0fe8181f2786b69f2621346d446b2e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920494"
---
# <a name="private-protected-visual-basic"></a><span data-ttu-id="f32d6-102">Private Protected. (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f32d6-102">Private Protected (Visual Basic)</span></span>

<span data-ttu-id="f32d6-103">`Private Protected` – Kombinace klíčových slov je modifikátor přístupu členu.</span><span class="sxs-lookup"><span data-stu-id="f32d6-103">The `Private Protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="f32d6-104">A `Private Protected` člen je přístupný podle všech členů v jeho obsahující třídy, a typy odvozené od třídy obsahující, ale pouze v případě, že se nenachází v jeho obsahující sestavení.</span><span class="sxs-lookup"><span data-stu-id="f32d6-104">A `Private Protected` member is accessible by all members in its containing class, as well as by types derived from the containing class, but only if they are found in its containing assembly.</span></span>

<span data-ttu-id="f32d6-105">Můžete zadat `Private Protected` pouze pro členy třídy; nelze použít `Private Protected` na členy struktury protože struktury nelze dědit.</span><span class="sxs-lookup"><span data-stu-id="f32d6-105">You can specify `Private Protected` only on members of classes; you cannot apply `Private Protected` to members of a structure because structures cannot be inherited.</span></span>

<span data-ttu-id="f32d6-106">`Private Protected` Modifikátor přístupu je podporován v jazyce Visual Basic 15.5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="f32d6-106">The `Private Protected` access modifier is supported by Visual Basic 15.5 and later.</span></span> <span data-ttu-id="f32d6-107">Jeho použití, můžete přidat následující prvek do projektu jazyka Visual Basic (\*.vbproj) souboru.</span><span class="sxs-lookup"><span data-stu-id="f32d6-107">To use it, you can add the following element to your Visual Basic project (\*.vbproj) file.</span></span> <span data-ttu-id="f32d6-108">Jak dlouho jako 15.5 jazyka Visual Basic nebo vyšší je nainstalovaný ve vašem systému, umožňuje využít výhod všech funkcí jazyka podporovaná modulem nejnovější verzi kompilátoru jazyka Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="f32d6-108">As long as Visual Basic 15.5 or later is installed on your system, it lets you take advantage of all the language features supported by the latest version of the Visual Basic compiler:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="f32d6-109">Další informace najdete v části [nastavení verze jazyka Visual Basic](../../language-reference/configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="f32d6-109">For more information see [setting the Visual Basic language version](../../language-reference/configure-language-version.md).</span></span>

> [!NOTE]
> <span data-ttu-id="f32d6-110">V sadě Visual Studio, že vyberete nápovědy klávesy F1 na `private protected` poskytuje nápovědu pro buď [privátní](private.md) nebo [chráněné](protected.md).</span><span class="sxs-lookup"><span data-stu-id="f32d6-110">In Visual Studio, selecting F1 help on `private protected` provides help for either [private](private.md) or [protected](protected.md).</span></span> <span data-ttu-id="f32d6-111">Rozhraní IDE zvolí jeden token pod kurzor spíše než složené slovo.</span><span class="sxs-lookup"><span data-stu-id="f32d6-111">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="f32d6-112">pravidla</span><span class="sxs-lookup"><span data-stu-id="f32d6-112">Rules</span></span>

- <span data-ttu-id="f32d6-113">**Místní deklarace.**</span><span class="sxs-lookup"><span data-stu-id="f32d6-113">**Declaration Context.**</span></span> <span data-ttu-id="f32d6-114">Můžete použít `Private Protected` pouze na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="f32d6-114">You can use `Private Protected` only at the class level.</span></span> <span data-ttu-id="f32d6-115">To znamená, že deklarace kontext `Protected` elementu musí být třída a nemůže být zdrojový soubor, obor názvů, rozhraní, modul, struktury nebo proceduru.</span><span class="sxs-lookup"><span data-stu-id="f32d6-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="behavior"></a><span data-ttu-id="f32d6-116">Chování</span><span class="sxs-lookup"><span data-stu-id="f32d6-116">Behavior</span></span>

- <span data-ttu-id="f32d6-117">**Úroveň přístupu.**</span><span class="sxs-lookup"><span data-stu-id="f32d6-117">**Access Level.**</span></span> <span data-ttu-id="f32d6-118">Veškerý kód ve třídě můžete přístup k jeho prvkům.</span><span class="sxs-lookup"><span data-stu-id="f32d6-118">All code in a class can access its elements.</span></span> <span data-ttu-id="f32d6-119">Kód do třídy, která je odvozena ze základní třídy a je obsažený ve stejném sestavení můžete přistupovat ke všem `Private Protected` prvky základní třídy.</span><span class="sxs-lookup"><span data-stu-id="f32d6-119">Code in any class that derives from a base class and is contained in the same assembly can access all the `Private Protected` elements of the base class.</span></span> <span data-ttu-id="f32d6-120">Ale kód do třídy, která je odvozena ze základní třídy a je obsažen v jiném sestavení nelze získat přístup k základní třídy `Private Protected` elementy.</span><span class="sxs-lookup"><span data-stu-id="f32d6-120">However, code in any class that derives from a base class and is contained in a different assembly can't access the base class `Private Protected` elements.</span></span>

- <span data-ttu-id="f32d6-121">**Modifikátory přístupu.**</span><span class="sxs-lookup"><span data-stu-id="f32d6-121">**Access Modifiers.**</span></span> <span data-ttu-id="f32d6-122">Klíčová slova, které určují úroveň přístupu se nazývají *modifikátorů přístupu*.</span><span class="sxs-lookup"><span data-stu-id="f32d6-122">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="f32d6-123">Porovnání přístupu modifikátory přístupu najdete v tématu [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="f32d6-123">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="f32d6-124">`Private Protected` Modifikátor lze použít v těchto kontextech:</span><span class="sxs-lookup"><span data-stu-id="f32d6-124">The `Private Protected` modifier can be used in these contexts:</span></span>

- <span data-ttu-id="f32d6-125">[Class – příkaz](../../../visual-basic/language-reference/statements/class-statement.md) vnořené třídy</span><span class="sxs-lookup"><span data-stu-id="f32d6-125">[Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) of a nested class</span></span>

- [<span data-ttu-id="f32d6-126">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="f32d6-126">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)

- [<span data-ttu-id="f32d6-127">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="f32d6-127">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)

- <span data-ttu-id="f32d6-128">[Delegate – příkaz](../../../visual-basic/language-reference/statements/delegate-statement.md) delegáta vnořená v třídě.</span><span class="sxs-lookup"><span data-stu-id="f32d6-128">[Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) of a delegate nested in a class</span></span>

- [<span data-ttu-id="f32d6-129">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="f32d6-129">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)

- <span data-ttu-id="f32d6-130">[Enum – příkaz](../../../visual-basic/language-reference/statements/enum-statement.md) výčtu vnořená v třídě.</span><span class="sxs-lookup"><span data-stu-id="f32d6-130">[Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md) of an enumeration nested in a class</span></span>

- [<span data-ttu-id="f32d6-131">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="f32d6-131">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)

- [<span data-ttu-id="f32d6-132">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="f32d6-132">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- <span data-ttu-id="f32d6-133">[Interface – příkaz](../../../visual-basic/language-reference/statements/interface-statement.md) rozhraní vnořená v třídě.</span><span class="sxs-lookup"><span data-stu-id="f32d6-133">[Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md) of an interface nested in a class</span></span>

- [<span data-ttu-id="f32d6-134">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="f32d6-134">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- <span data-ttu-id="f32d6-135">[Struktury příkaz](../../../visual-basic/language-reference/statements/structure-statement.md) struktury vnořená v třídě.</span><span class="sxs-lookup"><span data-stu-id="f32d6-135">[Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) of a structure nested in a class</span></span>

- [<span data-ttu-id="f32d6-136">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="f32d6-136">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="f32d6-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f32d6-137">See also</span></span>

- [<span data-ttu-id="f32d6-138">Public</span><span class="sxs-lookup"><span data-stu-id="f32d6-138">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="f32d6-139">Protected</span><span class="sxs-lookup"><span data-stu-id="f32d6-139">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="f32d6-140">Friend</span><span class="sxs-lookup"><span data-stu-id="f32d6-140">Friend</span></span>](friend.md)
- [<span data-ttu-id="f32d6-141">Private</span><span class="sxs-lookup"><span data-stu-id="f32d6-141">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="f32d6-142">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="f32d6-142">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="f32d6-143">Úrovně přístupu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f32d6-143">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="f32d6-144">Procedury</span><span class="sxs-lookup"><span data-stu-id="f32d6-144">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="f32d6-145">Struktury</span><span class="sxs-lookup"><span data-stu-id="f32d6-145">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="f32d6-146">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="f32d6-146">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
