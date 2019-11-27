---
title: WithEvents
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 2309c675b50a2025d73841a47fe8e30e7cecd522
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350740"
---
# <a name="withevents-visual-basic"></a><span data-ttu-id="b77f0-102">WithEvents (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b77f0-102">WithEvents (Visual Basic)</span></span>
<span data-ttu-id="b77f0-103">Určuje, že nejmíň jedna deklarovaná členská proměnná odkazuje na instanci třídy, která může vyvolat události.</span><span class="sxs-lookup"><span data-stu-id="b77f0-103">Specifies that one or more declared member variables refer to an instance of a class that can raise events.</span></span>

## <a name="remarks"></a><span data-ttu-id="b77f0-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b77f0-104">Remarks</span></span>

<span data-ttu-id="b77f0-105">Pokud je proměnná definována pomocí `WithEvents`, lze deklarativně určit, že metoda zpracovává události proměnné pomocí klíčového slova `Handles`.</span><span class="sxs-lookup"><span data-stu-id="b77f0-105">When a variable is defined using `WithEvents`, you can declaratively specify that a method handles the variable's events using the `Handles` keyword.</span></span>

<span data-ttu-id="b77f0-106">`WithEvents` můžete použít pouze na úrovni třídy nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="b77f0-106">You can use `WithEvents` only at class or module level.</span></span> <span data-ttu-id="b77f0-107">To znamená, že kontext deklarace pro proměnnou `WithEvents` musí být třída nebo modul a nemůže se jednat o zdrojový soubor, obor názvů, strukturu nebo proceduru.</span><span class="sxs-lookup"><span data-stu-id="b77f0-107">This means the declaration context for a `WithEvents` variable must be a class or module and cannot be a source file, namespace, structure, or procedure.</span></span>

<span data-ttu-id="b77f0-108">Nelze použít `WithEvents` pro člena struktury.</span><span class="sxs-lookup"><span data-stu-id="b77f0-108">You cannot use `WithEvents` on a structure member.</span></span>

<span data-ttu-id="b77f0-109">Můžete deklarovat pouze jednotlivé proměnné – ne pole – s `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="b77f0-109">You can declare only individual variables—not arrays—with `WithEvents`.</span></span>

## <a name="rules"></a><span data-ttu-id="b77f0-110">Pravidla</span><span class="sxs-lookup"><span data-stu-id="b77f0-110">Rules</span></span>

<span data-ttu-id="b77f0-111">**Typy prvků.**</span><span class="sxs-lookup"><span data-stu-id="b77f0-111">**Element Types.**</span></span> <span data-ttu-id="b77f0-112">Je nutné deklarovat `WithEvents` proměnné, aby byly proměnné objektu, aby mohly přijímat instance třídy.</span><span class="sxs-lookup"><span data-stu-id="b77f0-112">You must declare `WithEvents` variables to be object variables so that they can accept class instances.</span></span> <span data-ttu-id="b77f0-113">Nemůžete je však deklarovat jako `Object`.</span><span class="sxs-lookup"><span data-stu-id="b77f0-113">However, you cannot declare them as `Object`.</span></span> <span data-ttu-id="b77f0-114">Je nutné je deklarovat jako konkrétní třídu, která může události vyvolat.</span><span class="sxs-lookup"><span data-stu-id="b77f0-114">You must declare them as the specific class that can raise the events.</span></span>

<span data-ttu-id="b77f0-115">V tomto kontextu se dá použít modifikátor `WithEvents`: [příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="b77f0-115">The `WithEvents` modifier can be used in this context: [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)</span></span>

## <a name="example"></a><span data-ttu-id="b77f0-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="b77f0-116">Example</span></span>

```vb
Dim WithEvents app As Application
```

## <a name="see-also"></a><span data-ttu-id="b77f0-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b77f0-117">See also</span></span>

- [<span data-ttu-id="b77f0-118">Řeší</span><span class="sxs-lookup"><span data-stu-id="b77f0-118">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="b77f0-119">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="b77f0-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="b77f0-120">Události</span><span class="sxs-lookup"><span data-stu-id="b77f0-120">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
