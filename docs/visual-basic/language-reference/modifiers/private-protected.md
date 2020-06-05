---
title: Private Protected
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: b7d9f81e41950b92c787e2e50fb94fe3d7c07559
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84362226"
---
# <a name="private-protected-visual-basic"></a><span data-ttu-id="a7d34-102">Soukromé chráněné (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7d34-102">Private Protected (Visual Basic)</span></span>

<span data-ttu-id="a7d34-103">`Private Protected`Kombinace klíčového slova je modifikátor přístupu ke členu.</span><span class="sxs-lookup"><span data-stu-id="a7d34-103">The `Private Protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="a7d34-104">`Private Protected`Člen je přístupný pro všechny členy ve své nadřazené třídě a také podle typů odvozených z obsahující třídy, ale pouze v případě, že jsou nalezeny ve svém nadřazeném sestavení.</span><span class="sxs-lookup"><span data-stu-id="a7d34-104">A `Private Protected` member is accessible by all members in its containing class, as well as by types derived from the containing class, but only if they are found in its containing assembly.</span></span>

<span data-ttu-id="a7d34-105">Můžete zadat `Private Protected` pouze členy tříd. nemůžete použít `Private Protected` pro členy struktury, protože struktury nelze dědit.</span><span class="sxs-lookup"><span data-stu-id="a7d34-105">You can specify `Private Protected` only on members of classes; you cannot apply `Private Protected` to members of a structure because structures cannot be inherited.</span></span>

<span data-ttu-id="a7d34-106">`Private Protected`Modifikátor přístupu je podporován Visual Basic 15,5 a novějším.</span><span class="sxs-lookup"><span data-stu-id="a7d34-106">The `Private Protected` access modifier is supported by Visual Basic 15.5 and later.</span></span> <span data-ttu-id="a7d34-107">Chcete-li jej použít, můžete přidat následující prvek do souboru projektu Visual Basic ( \* . vbproj).</span><span class="sxs-lookup"><span data-stu-id="a7d34-107">To use it, you can add the following element to your Visual Basic project (\*.vbproj) file.</span></span> <span data-ttu-id="a7d34-108">Pokud je v systému nainstalovaná Visual Basic 15,5 nebo novější, umožní vám využít všechny jazykové funkce podporované nejnovější verzí Visual Basic kompilátoru:</span><span class="sxs-lookup"><span data-stu-id="a7d34-108">As long as Visual Basic 15.5 or later is installed on your system, it lets you take advantage of all the language features supported by the latest version of the Visual Basic compiler:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="a7d34-109">Další informace najdete v tématu [nastavení jazykové verze Visual Basic](../configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="a7d34-109">For more information see [setting the Visual Basic language version](../configure-language-version.md).</span></span>

> [!NOTE]
> <span data-ttu-id="a7d34-110">V aplikaci Visual Studio, když vyberete nápovědu pro klávesu F1, získáte `private protected` nápovědu pro buď [soukromou](private.md) , nebo [chráněnou](protected.md).</span><span class="sxs-lookup"><span data-stu-id="a7d34-110">In Visual Studio, selecting F1 help on `private protected` provides help for either [private](private.md) or [protected](protected.md).</span></span> <span data-ttu-id="a7d34-111">Rozhraní IDE vybere jeden token pod kurzorem namísto složeného slova.</span><span class="sxs-lookup"><span data-stu-id="a7d34-111">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="a7d34-112">Pravidla</span><span class="sxs-lookup"><span data-stu-id="a7d34-112">Rules</span></span>

- <span data-ttu-id="a7d34-113">**Kontext deklarace**</span><span class="sxs-lookup"><span data-stu-id="a7d34-113">**Declaration Context.**</span></span> <span data-ttu-id="a7d34-114">Můžete použít `Private Protected` pouze na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="a7d34-114">You can use `Private Protected` only at the class level.</span></span> <span data-ttu-id="a7d34-115">To znamená, že kontext deklarace pro `Protected` prvek musí být třída a nemůže se jednat o zdrojový soubor, obor názvů, rozhraní, modul, strukturu nebo proceduru.</span><span class="sxs-lookup"><span data-stu-id="a7d34-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="behavior"></a><span data-ttu-id="a7d34-116">Chování</span><span class="sxs-lookup"><span data-stu-id="a7d34-116">Behavior</span></span>

- <span data-ttu-id="a7d34-117">**Úroveň přístupu.**</span><span class="sxs-lookup"><span data-stu-id="a7d34-117">**Access Level.**</span></span> <span data-ttu-id="a7d34-118">Veškerý kód ve třídě má přístup k jeho prvkům.</span><span class="sxs-lookup"><span data-stu-id="a7d34-118">All code in a class can access its elements.</span></span> <span data-ttu-id="a7d34-119">Kód v jakékoli třídě, která je odvozena od základní třídy a je obsažen ve stejném sestavení, má přístup ke všem `Private Protected` prvkům základní třídy.</span><span class="sxs-lookup"><span data-stu-id="a7d34-119">Code in any class that derives from a base class and is contained in the same assembly can access all the `Private Protected` elements of the base class.</span></span> <span data-ttu-id="a7d34-120">Nicméně kód v jakékoli třídě, která je odvozena od základní třídy a je obsažen v jiném sestavení, nemůže přistupovat k `Private Protected` prvkům základní třídy.</span><span class="sxs-lookup"><span data-stu-id="a7d34-120">However, code in any class that derives from a base class and is contained in a different assembly can't access the base class `Private Protected` elements.</span></span>

- <span data-ttu-id="a7d34-121">**Modifikátory přístupu.**</span><span class="sxs-lookup"><span data-stu-id="a7d34-121">**Access Modifiers.**</span></span> <span data-ttu-id="a7d34-122">Klíčová slova, která určují úroveň přístupu, se nazývají *modifikátory přístupu*.</span><span class="sxs-lookup"><span data-stu-id="a7d34-122">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="a7d34-123">Porovnání modifikátorů přístupu najdete [v tématu úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="a7d34-123">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="a7d34-124">`Private Protected`V těchto kontextech lze použít modifikátor:</span><span class="sxs-lookup"><span data-stu-id="a7d34-124">The `Private Protected` modifier can be used in these contexts:</span></span>

- <span data-ttu-id="a7d34-125">[Příkaz třídy](../statements/class-statement.md) vnořené třídy</span><span class="sxs-lookup"><span data-stu-id="a7d34-125">[Class Statement](../statements/class-statement.md) of a nested class</span></span>

- [<span data-ttu-id="a7d34-126">Const – příkaz</span><span class="sxs-lookup"><span data-stu-id="a7d34-126">Const Statement</span></span>](../statements/const-statement.md)

- [<span data-ttu-id="a7d34-127">Declare – příkaz</span><span class="sxs-lookup"><span data-stu-id="a7d34-127">Declare Statement</span></span>](../statements/declare-statement.md)

- <span data-ttu-id="a7d34-128">[Příkaz Delegate](../statements/delegate-statement.md) pro delegáta vnořený ve třídě</span><span class="sxs-lookup"><span data-stu-id="a7d34-128">[Delegate Statement](../statements/delegate-statement.md) of a delegate nested in a class</span></span>

- [<span data-ttu-id="a7d34-129">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="a7d34-129">Dim Statement</span></span>](../statements/dim-statement.md)

- <span data-ttu-id="a7d34-130">[Enum – příkaz](../statements/enum-statement.md) pro výčet vnořený ve třídě</span><span class="sxs-lookup"><span data-stu-id="a7d34-130">[Enum Statement](../statements/enum-statement.md) of an enumeration nested in a class</span></span>

- [<span data-ttu-id="a7d34-131">Event – příkaz</span><span class="sxs-lookup"><span data-stu-id="a7d34-131">Event Statement</span></span>](../statements/event-statement.md)

- [<span data-ttu-id="a7d34-132">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="a7d34-132">Function Statement</span></span>](../statements/function-statement.md)

- <span data-ttu-id="a7d34-133">[Příkaz rozhraní](../statements/interface-statement.md) rozhraní vnořeného ve třídě</span><span class="sxs-lookup"><span data-stu-id="a7d34-133">[Interface Statement](../statements/interface-statement.md) of an interface nested in a class</span></span>

- [<span data-ttu-id="a7d34-134">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="a7d34-134">Property Statement</span></span>](../statements/property-statement.md)

- <span data-ttu-id="a7d34-135">[Příkaz struktury](../statements/structure-statement.md) struktury vnořené ve třídě</span><span class="sxs-lookup"><span data-stu-id="a7d34-135">[Structure Statement](../statements/structure-statement.md) of a structure nested in a class</span></span>

- [<span data-ttu-id="a7d34-136">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="a7d34-136">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="a7d34-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="a7d34-137">See also</span></span>

- [<span data-ttu-id="a7d34-138">Republik</span><span class="sxs-lookup"><span data-stu-id="a7d34-138">Public</span></span>](public.md)
- [<span data-ttu-id="a7d34-139">Proti</span><span class="sxs-lookup"><span data-stu-id="a7d34-139">Protected</span></span>](protected.md)
- [<span data-ttu-id="a7d34-140">Friend</span><span class="sxs-lookup"><span data-stu-id="a7d34-140">Friend</span></span>](friend.md)
- [<span data-ttu-id="a7d34-141">Hlášen</span><span class="sxs-lookup"><span data-stu-id="a7d34-141">Private</span></span>](private.md)
- [<span data-ttu-id="a7d34-142">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="a7d34-142">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="a7d34-143">Úrovně přístupu v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a7d34-143">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="a7d34-144">Procedury</span><span class="sxs-lookup"><span data-stu-id="a7d34-144">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="a7d34-145">Struktury</span><span class="sxs-lookup"><span data-stu-id="a7d34-145">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="a7d34-146">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="a7d34-146">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
