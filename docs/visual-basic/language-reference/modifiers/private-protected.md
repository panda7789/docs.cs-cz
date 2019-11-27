---
title: Private Protected
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: 265141f77f4a61a61414a07214830feaa8a1ab05
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351344"
---
# <a name="private-protected-visual-basic"></a><span data-ttu-id="908bc-102">Soukromé chráněné (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="908bc-102">Private Protected (Visual Basic)</span></span>

<span data-ttu-id="908bc-103">Kombinací klíčového slova `Private Protected` je modifikátor přístupu ke členu.</span><span class="sxs-lookup"><span data-stu-id="908bc-103">The `Private Protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="908bc-104">`Private Protected` člen je přístupný pro všechny členy v příslušné třídě, stejně jako typy odvozené z nadřazené třídy, ale pouze v případě, že jsou nalezeny ve svém obsahujícím sestavení.</span><span class="sxs-lookup"><span data-stu-id="908bc-104">A `Private Protected` member is accessible by all members in its containing class, as well as by types derived from the containing class, but only if they are found in its containing assembly.</span></span>

<span data-ttu-id="908bc-105">Můžete zadat `Private Protected` pouze pro členy třídy; `Private Protected` nelze použít u členů struktury, protože struktury nelze dědit.</span><span class="sxs-lookup"><span data-stu-id="908bc-105">You can specify `Private Protected` only on members of classes; you cannot apply `Private Protected` to members of a structure because structures cannot be inherited.</span></span>

<span data-ttu-id="908bc-106">Modifikátor přístupu `Private Protected` je podporován Visual Basic 15,5 a novějším.</span><span class="sxs-lookup"><span data-stu-id="908bc-106">The `Private Protected` access modifier is supported by Visual Basic 15.5 and later.</span></span> <span data-ttu-id="908bc-107">Chcete-li jej použít, můžete přidat následující prvek do souboru Visual Basic projektu (\*. vbproj).</span><span class="sxs-lookup"><span data-stu-id="908bc-107">To use it, you can add the following element to your Visual Basic project (\*.vbproj) file.</span></span> <span data-ttu-id="908bc-108">Pokud je v systému nainstalovaná Visual Basic 15,5 nebo novější, umožní vám využít všechny jazykové funkce podporované nejnovější verzí Visual Basic kompilátoru:</span><span class="sxs-lookup"><span data-stu-id="908bc-108">As long as Visual Basic 15.5 or later is installed on your system, it lets you take advantage of all the language features supported by the latest version of the Visual Basic compiler:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="908bc-109">Další informace najdete v tématu [nastavení jazykové verze Visual Basic](../../language-reference/configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="908bc-109">For more information see [setting the Visual Basic language version](../../language-reference/configure-language-version.md).</span></span>

> [!NOTE]
> <span data-ttu-id="908bc-110">V aplikaci Visual Studio vyberte nápovědu F1 pro `private protected` poskytuje nápovědu pro [privátní](private.md) nebo [chráněné](protected.md).</span><span class="sxs-lookup"><span data-stu-id="908bc-110">In Visual Studio, selecting F1 help on `private protected` provides help for either [private](private.md) or [protected](protected.md).</span></span> <span data-ttu-id="908bc-111">Rozhraní IDE vybere jeden token pod kurzorem namísto složeného slova.</span><span class="sxs-lookup"><span data-stu-id="908bc-111">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="908bc-112">Pravidla</span><span class="sxs-lookup"><span data-stu-id="908bc-112">Rules</span></span>

- <span data-ttu-id="908bc-113">**Kontext deklarace**</span><span class="sxs-lookup"><span data-stu-id="908bc-113">**Declaration Context.**</span></span> <span data-ttu-id="908bc-114">`Private Protected` lze použít pouze na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="908bc-114">You can use `Private Protected` only at the class level.</span></span> <span data-ttu-id="908bc-115">To znamená, že kontext deklarace pro prvek `Protected` musí být třída a nemůže se jednat o zdrojový soubor, obor názvů, rozhraní, modul, strukturu nebo proceduru.</span><span class="sxs-lookup"><span data-stu-id="908bc-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="behavior"></a><span data-ttu-id="908bc-116">Chování</span><span class="sxs-lookup"><span data-stu-id="908bc-116">Behavior</span></span>

- <span data-ttu-id="908bc-117">**Úroveň přístupu.**</span><span class="sxs-lookup"><span data-stu-id="908bc-117">**Access Level.**</span></span> <span data-ttu-id="908bc-118">Veškerý kód ve třídě má přístup k jeho prvkům.</span><span class="sxs-lookup"><span data-stu-id="908bc-118">All code in a class can access its elements.</span></span> <span data-ttu-id="908bc-119">Kód v jakékoli třídě, která je odvozena od základní třídy a je obsažen ve stejném sestavení, má přístup ke všem prvkům `Private Protected` základní třídy.</span><span class="sxs-lookup"><span data-stu-id="908bc-119">Code in any class that derives from a base class and is contained in the same assembly can access all the `Private Protected` elements of the base class.</span></span> <span data-ttu-id="908bc-120">Nicméně kód v jakékoli třídě, která je odvozena od základní třídy a je obsažen v jiném sestavení, nemůže přistupovat k základní třídě `Private Protected` prvky.</span><span class="sxs-lookup"><span data-stu-id="908bc-120">However, code in any class that derives from a base class and is contained in a different assembly can't access the base class `Private Protected` elements.</span></span>

- <span data-ttu-id="908bc-121">**Modifikátory přístupu.**</span><span class="sxs-lookup"><span data-stu-id="908bc-121">**Access Modifiers.**</span></span> <span data-ttu-id="908bc-122">Klíčová slova, která určují úroveň přístupu, se nazývají *modifikátory přístupu*.</span><span class="sxs-lookup"><span data-stu-id="908bc-122">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="908bc-123">Porovnání modifikátorů přístupu najdete [v tématu úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="908bc-123">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="908bc-124">V těchto kontextech lze použít modifikátor `Private Protected`:</span><span class="sxs-lookup"><span data-stu-id="908bc-124">The `Private Protected` modifier can be used in these contexts:</span></span>

- <span data-ttu-id="908bc-125">[Příkaz třídy](../../../visual-basic/language-reference/statements/class-statement.md) vnořené třídy</span><span class="sxs-lookup"><span data-stu-id="908bc-125">[Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) of a nested class</span></span>

- [<span data-ttu-id="908bc-126">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="908bc-126">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)

- [<span data-ttu-id="908bc-127">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="908bc-127">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)

- <span data-ttu-id="908bc-128">[Příkaz Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md) pro delegáta vnořený ve třídě</span><span class="sxs-lookup"><span data-stu-id="908bc-128">[Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) of a delegate nested in a class</span></span>

- [<span data-ttu-id="908bc-129">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="908bc-129">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)

- <span data-ttu-id="908bc-130">[Enum – příkaz](../../../visual-basic/language-reference/statements/enum-statement.md) pro výčet vnořený ve třídě</span><span class="sxs-lookup"><span data-stu-id="908bc-130">[Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md) of an enumeration nested in a class</span></span>

- [<span data-ttu-id="908bc-131">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="908bc-131">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)

- [<span data-ttu-id="908bc-132">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="908bc-132">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- <span data-ttu-id="908bc-133">[Příkaz rozhraní](../../../visual-basic/language-reference/statements/interface-statement.md) rozhraní vnořeného ve třídě</span><span class="sxs-lookup"><span data-stu-id="908bc-133">[Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md) of an interface nested in a class</span></span>

- [<span data-ttu-id="908bc-134">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="908bc-134">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- <span data-ttu-id="908bc-135">[Příkaz struktury](../../../visual-basic/language-reference/statements/structure-statement.md) struktury vnořené ve třídě</span><span class="sxs-lookup"><span data-stu-id="908bc-135">[Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) of a structure nested in a class</span></span>

- [<span data-ttu-id="908bc-136">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="908bc-136">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="908bc-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="908bc-137">See also</span></span>

- [<span data-ttu-id="908bc-138">Public</span><span class="sxs-lookup"><span data-stu-id="908bc-138">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="908bc-139">Protected</span><span class="sxs-lookup"><span data-stu-id="908bc-139">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="908bc-140">Friend</span><span class="sxs-lookup"><span data-stu-id="908bc-140">Friend</span></span>](friend.md)
- [<span data-ttu-id="908bc-141">Private</span><span class="sxs-lookup"><span data-stu-id="908bc-141">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="908bc-142">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="908bc-142">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="908bc-143">Úrovně přístupu v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="908bc-143">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="908bc-144">Procedury</span><span class="sxs-lookup"><span data-stu-id="908bc-144">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="908bc-145">Struktury</span><span class="sxs-lookup"><span data-stu-id="908bc-145">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="908bc-146">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="908bc-146">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
