---
title: Soukromé
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: 524f03e77e075bef08a1b41b563985de41baacb6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404807"
---
# <a name="private-visual-basic"></a><span data-ttu-id="692d5-102">Private (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="692d5-102">Private (Visual Basic)</span></span>
<span data-ttu-id="692d5-103">Určuje, že nejmíň jeden deklarovaný programový prvek je přístupný jenom v rámci svého kontextu deklarace, včetně v rámci libovolných obsažených typů.</span><span class="sxs-lookup"><span data-stu-id="692d5-103">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="692d5-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="692d5-104">Remarks</span></span>  
 <span data-ttu-id="692d5-105">Pokud programovací element představuje proprietární funkce nebo obsahuje důvěrné údaje, obvykle chcete omezit přístup k němu, co je to možné.</span><span class="sxs-lookup"><span data-stu-id="692d5-105">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="692d5-106">Dosáhnete maximálního omezení tím, že povolíte pouze modul, třídu nebo strukturu, které ji definují k přístupu.</span><span class="sxs-lookup"><span data-stu-id="692d5-106">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="692d5-107">Chcete-li omezit přístup k prvku tímto způsobem, můžete jej deklarovat pomocí `Private` .</span><span class="sxs-lookup"><span data-stu-id="692d5-107">To limit access to an element in this way, you can declare it with `Private`.</span></span>  

> [!NOTE]
> <span data-ttu-id="692d5-108">Můžete také použít modifikátor [privátního chráněného](private-protected.md) přístupu, který zpřístupňuje člena v rámci této třídy a z odvozených tříd umístěných v jeho obsahujícím sestavení.</span><span class="sxs-lookup"><span data-stu-id="692d5-108">You can also use the [Private Protected](private-protected.md) access modifier, which makes a member accessible from within that class and from derived classes located in its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="692d5-109">Pravidla</span><span class="sxs-lookup"><span data-stu-id="692d5-109">Rules</span></span>  

- <span data-ttu-id="692d5-110">**Kontext deklarace**</span><span class="sxs-lookup"><span data-stu-id="692d5-110">**Declaration Context.**</span></span> <span data-ttu-id="692d5-111">Můžete použít `Private` pouze na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="692d5-111">You can use `Private` only at module level.</span></span> <span data-ttu-id="692d5-112">To znamená, že kontext deklarace pro `Private` prvek musí být modul, třída nebo struktura a nemůže se jednat o zdrojový soubor, obor názvů, rozhraní nebo proceduru.</span><span class="sxs-lookup"><span data-stu-id="692d5-112">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="692d5-113">Chování</span><span class="sxs-lookup"><span data-stu-id="692d5-113">Behavior</span></span>  
  
- <span data-ttu-id="692d5-114">**Úroveň přístupu.**</span><span class="sxs-lookup"><span data-stu-id="692d5-114">**Access Level.**</span></span> <span data-ttu-id="692d5-115">Veškerý kód v kontextu deklarace má přístup k jeho `Private` prvkům.</span><span class="sxs-lookup"><span data-stu-id="692d5-115">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="692d5-116">To zahrnuje kód v rámci obsaženého typu, jako je vnořená třída nebo výraz přiřazení ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="692d5-116">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="692d5-117">Žádný kód mimo kontext deklarace má přístup k jeho `Private` prvkům.</span><span class="sxs-lookup"><span data-stu-id="692d5-117">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
- <span data-ttu-id="692d5-118">**Modifikátory přístupu.**</span><span class="sxs-lookup"><span data-stu-id="692d5-118">**Access Modifiers.**</span></span> <span data-ttu-id="692d5-119">Klíčová slova, která určují úroveň přístupu, se nazývají *modifikátory přístupu*.</span><span class="sxs-lookup"><span data-stu-id="692d5-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="692d5-120">Porovnání modifikátorů přístupu najdete [v tématu úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="692d5-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="692d5-121">`Private`V těchto kontextech lze použít modifikátor:</span><span class="sxs-lookup"><span data-stu-id="692d5-121">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="692d5-122">Class – příkaz</span><span class="sxs-lookup"><span data-stu-id="692d5-122">Class Statement</span></span>](../statements/class-statement.md)  
  
 [<span data-ttu-id="692d5-123">Const – příkaz</span><span class="sxs-lookup"><span data-stu-id="692d5-123">Const Statement</span></span>](../statements/const-statement.md)  
  
 [<span data-ttu-id="692d5-124">Declare – příkaz</span><span class="sxs-lookup"><span data-stu-id="692d5-124">Declare Statement</span></span>](../statements/declare-statement.md)  
  
 [<span data-ttu-id="692d5-125">Delegate – příkaz</span><span class="sxs-lookup"><span data-stu-id="692d5-125">Delegate Statement</span></span>](../statements/delegate-statement.md)  
  
 [<span data-ttu-id="692d5-126">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="692d5-126">Dim Statement</span></span>](../statements/dim-statement.md)  
  
 [<span data-ttu-id="692d5-127">Enum – příkaz</span><span class="sxs-lookup"><span data-stu-id="692d5-127">Enum Statement</span></span>](../statements/enum-statement.md)  
  
 [<span data-ttu-id="692d5-128">Event – příkaz</span><span class="sxs-lookup"><span data-stu-id="692d5-128">Event Statement</span></span>](../statements/event-statement.md)  
  
 [<span data-ttu-id="692d5-129">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="692d5-129">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="692d5-130">Interface – příkaz</span><span class="sxs-lookup"><span data-stu-id="692d5-130">Interface Statement</span></span>](../statements/interface-statement.md)  
  
 [<span data-ttu-id="692d5-131">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="692d5-131">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="692d5-132">Structure – příkaz</span><span class="sxs-lookup"><span data-stu-id="692d5-132">Structure Statement</span></span>](../statements/structure-statement.md)  
  
 [<span data-ttu-id="692d5-133">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="692d5-133">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="692d5-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="692d5-134">See also</span></span>

- [<span data-ttu-id="692d5-135">Republik</span><span class="sxs-lookup"><span data-stu-id="692d5-135">Public</span></span>](public.md)
- [<span data-ttu-id="692d5-136">Proti</span><span class="sxs-lookup"><span data-stu-id="692d5-136">Protected</span></span>](protected.md)
- [<span data-ttu-id="692d5-137">Friend</span><span class="sxs-lookup"><span data-stu-id="692d5-137">Friend</span></span>](friend.md)
- [<span data-ttu-id="692d5-138">Soukromé chráněné</span><span class="sxs-lookup"><span data-stu-id="692d5-138">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="692d5-139">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="692d5-139">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="692d5-140">Úrovně přístupu v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="692d5-140">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="692d5-141">Procedury</span><span class="sxs-lookup"><span data-stu-id="692d5-141">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="692d5-142">Struktury</span><span class="sxs-lookup"><span data-stu-id="692d5-142">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="692d5-143">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="692d5-143">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
