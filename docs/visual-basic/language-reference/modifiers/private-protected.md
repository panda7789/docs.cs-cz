---
title: Chráněné privátní (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: 23fd6583182a1fee544d0458dc3fc390aed86b9f
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
---
# <a name="private-protected-visual-basic"></a><span data-ttu-id="c55be-102">Chráněné privátní (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c55be-102">Private Protected (Visual Basic)</span></span>

<span data-ttu-id="c55be-103">`Private Protected` – Kombinace klíčových slov je modifikátor přístupu členů.</span><span class="sxs-lookup"><span data-stu-id="c55be-103">The `Private Protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="c55be-104">A `Private Protected` člen je dostupný ve své třídě obsahující všechny členy, a také pro typy odvozené od třídy obsahující, ale pouze v případě, že se nacházejí v jeho obsahující sestavení.</span><span class="sxs-lookup"><span data-stu-id="c55be-104">A `Private Protected` member is accessible by all members in its containing class, as well as by types derived from the containing class, but only if they are found in its containing assembly.</span></span> 

<span data-ttu-id="c55be-105">Můžete zadat `Private Protected` pouze u členů tříd; nelze použít `Private Protected` u členů struktury protože struktury nemůže být zděděno.</span><span class="sxs-lookup"><span data-stu-id="c55be-105">You can specify `Private Protected` only on members of classes; you cannot apply `Private Protected` to members of a structure because structures cannot be inherited.</span></span>

<span data-ttu-id="c55be-106">`Private Protected` – Modifikátor přístupu jsou podporovány nástrojem 15,5 Visual Basic a vyšší.</span><span class="sxs-lookup"><span data-stu-id="c55be-106">The `Private Protected` access modifier is supported by Visual Basic 15.5 and later.</span></span> <span data-ttu-id="c55be-107">Pokud chcete použít, můžete přidat následující prvek se v souboru projektu (\*.vbproj) jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c55be-107">To use it, you can add the following element to your Visual Basic project (\*.vbproj) file.</span></span> <span data-ttu-id="c55be-108">Jak dlouho jako 15,5 Visual Basic nebo novější je nainstalován ve vašem systému, umožňuje využít výhod všech funkcí jazyka nejnovější verze kompilátoru jazyka Visual Basic nepodporuje:</span><span class="sxs-lookup"><span data-stu-id="c55be-108">As long as Visual Basic 15.5 or later is installed on your system, it lets you take advantage of all the language features supported by the latest version of the Visual Basic compiler:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="c55be-109">V sadě Visual Studio, výběr F1 – Nápověda na `private protected` poskytuje nápovědu pro buď [privátní](private.md) nebo [chráněné](protected.md).</span><span class="sxs-lookup"><span data-stu-id="c55be-109">In Visual Studio, selecting F1 help on `private protected` provides help for either [private](private.md) or [protected](protected.md).</span></span> <span data-ttu-id="c55be-110">Prostředí IDE vybere jeden token pod kurzor spíše než složené aplikace word.</span><span class="sxs-lookup"><span data-stu-id="c55be-110">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="c55be-111">Pravidla</span><span class="sxs-lookup"><span data-stu-id="c55be-111">Rules</span></span>

- <span data-ttu-id="c55be-112">**Kontext deklarace.**</span><span class="sxs-lookup"><span data-stu-id="c55be-112">**Declaration Context.**</span></span> <span data-ttu-id="c55be-113">Můžete použít `Private Protected` pouze na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="c55be-113">You can use `Private Protected` only at the class level.</span></span> <span data-ttu-id="c55be-114">To znamená kontext deklarace `Protected` element musí být třída a nesmí být zdrojový soubor, obor názvů, rozhraní, modul, struktura nebo postup.</span><span class="sxs-lookup"><span data-stu-id="c55be-114">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="behavior"></a><span data-ttu-id="c55be-115">Chování</span><span class="sxs-lookup"><span data-stu-id="c55be-115">Behavior</span></span>

- <span data-ttu-id="c55be-116">**Úroveň přístupu.**</span><span class="sxs-lookup"><span data-stu-id="c55be-116">**Access Level.**</span></span> <span data-ttu-id="c55be-117">Všechny kódu v třídě mají přístup k jeho elementy.</span><span class="sxs-lookup"><span data-stu-id="c55be-117">All code in a class can access its elements.</span></span> <span data-ttu-id="c55be-118">Kód do třídy, která je odvozena ze základní třídy a je obsažený ve stejném sestavení přístup k veškerým `Private Protected` elementy základní třídy.</span><span class="sxs-lookup"><span data-stu-id="c55be-118">Code in any class that derives from a base class and is contained in the same assembly can access all the `Private Protected` elements of the base class.</span></span> <span data-ttu-id="c55be-119">Však se kód do třídy, která je odvozena ze základní třídy a je obsažený v jiném sestavení nemůže přistupovat k základní třídy `Private Protected` elementy.</span><span class="sxs-lookup"><span data-stu-id="c55be-119">However, code in any class that derives from a base class and is contained in a different assembly can't access the base class `Private Protected` elements.</span></span>

- <span data-ttu-id="c55be-120">**Modifikátory přístupu.**</span><span class="sxs-lookup"><span data-stu-id="c55be-120">**Access Modifiers.**</span></span> <span data-ttu-id="c55be-121">Klíčová slova, které určují úroveň přístupu, se nazývají *přístup modifikátory*.</span><span class="sxs-lookup"><span data-stu-id="c55be-121">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="c55be-122">Porovnání modifikátory přístupu najdete v tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="c55be-122">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>
  
 <span data-ttu-id="c55be-123">`Private Protected` Modifikátor lze použít v těchto kontexty:</span><span class="sxs-lookup"><span data-stu-id="c55be-123">The `Private Protected` modifier can be used in these contexts:</span></span>  
  
 <span data-ttu-id="c55be-124">[Class – příkaz](../../../visual-basic/language-reference/statements/class-statement.md) vnořené třídy</span><span class="sxs-lookup"><span data-stu-id="c55be-124">[Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) of a nested class</span></span>  
  
 [<span data-ttu-id="c55be-125">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="c55be-125">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="c55be-126">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="c55be-126">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 <span data-ttu-id="c55be-127">[Delegate – příkaz](../../../visual-basic/language-reference/statements/delegate-statement.md) delegáta vnořené v třídě</span><span class="sxs-lookup"><span data-stu-id="c55be-127">[Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) of a delegate nested in a class</span></span>  
  
 [<span data-ttu-id="c55be-128">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="c55be-128">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 <span data-ttu-id="c55be-129">[Enum – příkaz](../../../visual-basic/language-reference/statements/enum-statement.md) z eumeration vnořené v třídě</span><span class="sxs-lookup"><span data-stu-id="c55be-129">[Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md) of an eumeration nested in a class</span></span> 
  
 [<span data-ttu-id="c55be-130">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="c55be-130">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="c55be-131">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="c55be-131">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 <span data-ttu-id="c55be-132">[Interface – příkaz](../../../visual-basic/language-reference/statements/interface-statement.md) rozhraní vnořené v třídě</span><span class="sxs-lookup"><span data-stu-id="c55be-132">[Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md) of an interface nested in a class</span></span> 
  
 [<span data-ttu-id="c55be-133">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="c55be-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 <span data-ttu-id="c55be-134">[Struktury příkaz](../../../visual-basic/language-reference/statements/structure-statement.md) struktury vnořené v třídě</span><span class="sxs-lookup"><span data-stu-id="c55be-134">[Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) of a structure nested in a class</span></span> 
  
 [<span data-ttu-id="c55be-135">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="c55be-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="c55be-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="c55be-136">See Also</span></span>

[<span data-ttu-id="c55be-137">Public</span><span class="sxs-lookup"><span data-stu-id="c55be-137">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
[<span data-ttu-id="c55be-138">Protected</span><span class="sxs-lookup"><span data-stu-id="c55be-138">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
<span data-ttu-id="c55be-139">[Friend](friend.md) </span><span class="sxs-lookup"><span data-stu-id="c55be-139">[Friend](friend.md) </span></span>  
[<span data-ttu-id="c55be-140">Private</span><span class="sxs-lookup"><span data-stu-id="c55be-140">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
<span data-ttu-id="c55be-141">[Chráněné Friend](./protected-friend.md) </span><span class="sxs-lookup"><span data-stu-id="c55be-141">[Protected Friend](./protected-friend.md) </span></span>  
[<span data-ttu-id="c55be-142">Úrovně přístupu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c55be-142">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
[<span data-ttu-id="c55be-143">Procedury</span><span class="sxs-lookup"><span data-stu-id="c55be-143">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
[<span data-ttu-id="c55be-144">Struktury</span><span class="sxs-lookup"><span data-stu-id="c55be-144">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
[<span data-ttu-id="c55be-145">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="c55be-145">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
