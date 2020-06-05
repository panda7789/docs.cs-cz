---
title: WithEvents
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 48261e27de302c1809c9725e6e2fc0705a803930
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386773"
---
# <a name="withevents-visual-basic"></a><span data-ttu-id="1b921-102">WithEvents (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b921-102">WithEvents (Visual Basic)</span></span>
<span data-ttu-id="1b921-103">Určuje, že nejmíň jedna deklarovaná členská proměnná odkazuje na instanci třídy, která může vyvolat události.</span><span class="sxs-lookup"><span data-stu-id="1b921-103">Specifies that one or more declared member variables refer to an instance of a class that can raise events.</span></span>

## <a name="remarks"></a><span data-ttu-id="1b921-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1b921-104">Remarks</span></span>

<span data-ttu-id="1b921-105">Pokud je proměnná definována pomocí `WithEvents` , lze deklarativně určit, že metoda zpracovává události proměnné pomocí `Handles` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="1b921-105">When a variable is defined using `WithEvents`, you can declaratively specify that a method handles the variable's events using the `Handles` keyword.</span></span>

<span data-ttu-id="1b921-106">Můžete použít `WithEvents` pouze na úrovni třídy nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="1b921-106">You can use `WithEvents` only at class or module level.</span></span> <span data-ttu-id="1b921-107">To znamená, že kontext deklarace `WithEvents` proměnné musí být třída nebo modul a nemůže se jednat o zdrojový soubor, obor názvů, strukturu nebo proceduru.</span><span class="sxs-lookup"><span data-stu-id="1b921-107">This means the declaration context for a `WithEvents` variable must be a class or module and cannot be a source file, namespace, structure, or procedure.</span></span>

<span data-ttu-id="1b921-108">Nemůžete použít `WithEvents` u člena struktury.</span><span class="sxs-lookup"><span data-stu-id="1b921-108">You cannot use `WithEvents` on a structure member.</span></span>

<span data-ttu-id="1b921-109">Můžete deklarovat pouze jednotlivé proměnné – ne pole – s `WithEvents` .</span><span class="sxs-lookup"><span data-stu-id="1b921-109">You can declare only individual variables—not arrays—with `WithEvents`.</span></span>

## <a name="rules"></a><span data-ttu-id="1b921-110">Pravidla</span><span class="sxs-lookup"><span data-stu-id="1b921-110">Rules</span></span>

<span data-ttu-id="1b921-111">**Typy prvků.**</span><span class="sxs-lookup"><span data-stu-id="1b921-111">**Element Types.**</span></span> <span data-ttu-id="1b921-112">Je nutné deklarovat `WithEvents` proměnné, aby byly proměnné objektu, aby mohly přijímat instance třídy.</span><span class="sxs-lookup"><span data-stu-id="1b921-112">You must declare `WithEvents` variables to be object variables so that they can accept class instances.</span></span> <span data-ttu-id="1b921-113">Nemůžete je však deklarovat jako `Object` .</span><span class="sxs-lookup"><span data-stu-id="1b921-113">However, you cannot declare them as `Object`.</span></span> <span data-ttu-id="1b921-114">Je nutné je deklarovat jako konkrétní třídu, která může události vyvolat.</span><span class="sxs-lookup"><span data-stu-id="1b921-114">You must declare them as the specific class that can raise the events.</span></span>

<span data-ttu-id="1b921-115">`WithEvents`Modifikátor se dá použít v tomto kontextu: [příkaz Dim](../statements/dim-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="1b921-115">The `WithEvents` modifier can be used in this context: [Dim Statement](../statements/dim-statement.md)</span></span>

## <a name="example"></a><span data-ttu-id="1b921-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="1b921-116">Example</span></span>

```vb
Dim WithEvents app As Application
```

## <a name="see-also"></a><span data-ttu-id="1b921-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b921-117">See also</span></span>

- [<span data-ttu-id="1b921-118">Handles</span><span class="sxs-lookup"><span data-stu-id="1b921-118">Handles</span></span>](../statements/handles-clause.md)
- [<span data-ttu-id="1b921-119">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="1b921-119">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="1b921-120">Události</span><span class="sxs-lookup"><span data-stu-id="1b921-120">Events</span></span>](../../programming-guide/language-features/events/index.md)
