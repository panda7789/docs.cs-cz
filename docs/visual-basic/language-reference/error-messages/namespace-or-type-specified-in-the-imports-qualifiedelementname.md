---
title: Obor názvů nebo typ zadaný v příkazu Imports '<qualifiedelementname>' neobsahuje žádný veřejný člen nebo nebyl nalezen.
ms.date: 07/20/2015
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
ms.openlocfilehash: 8675d9c3b202200c89e12e7a5f51a19d9e3e0e64
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409462"
---
# <a name="namespace-or-type-specified-in-the-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="c0f85-102">Obor názvů nebo typ zadaný v příkazu Imports '\<qualifiedelementname>' neobsahuje žádný veřejný člen nebo nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="c0f85-102">Namespace or type specified in the Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found</span></span>

<span data-ttu-id="c0f85-103">Obor názvů nebo typ zadaný v importech neobsahuje \<qualifiedelementname> žádné veřejné členy nebo se nedá najít.</span><span class="sxs-lookup"><span data-stu-id="c0f85-103">Namespace or type specified in the Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="c0f85-104">Ujistěte se, že je obor názvů nebo typ definován a obsahuje nejméně jeden veřejný člen.</span><span class="sxs-lookup"><span data-stu-id="c0f85-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="c0f85-105">Ujistěte se, že název aliasu neobsahuje další aliasy.</span><span class="sxs-lookup"><span data-stu-id="c0f85-105">Make sure the alias name doesn't contain other aliases.</span></span>

<span data-ttu-id="c0f85-106">`Imports`Příkaz určuje obsahující prvek, který buď nebyl nalezen, nebo nedefinuje žádné `Public` členy.</span><span class="sxs-lookup"><span data-stu-id="c0f85-106">An `Imports` statement specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>

<span data-ttu-id="c0f85-107">*Obsahující element* může být obor názvů, třída, struktura, modul, rozhraní nebo výčet.</span><span class="sxs-lookup"><span data-stu-id="c0f85-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="c0f85-108">Obsahující element obsahuje členy, jako jsou proměnné, procedury nebo jiné obsahující prvky.</span><span class="sxs-lookup"><span data-stu-id="c0f85-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>

<span data-ttu-id="c0f85-109">Účelem importu je dovolit vašemu kódu přístup k oboru názvů nebo členům typu bez nutnosti jejich zařazení.</span><span class="sxs-lookup"><span data-stu-id="c0f85-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="c0f85-110">Projekt může také potřebovat přidat odkaz na obor názvů nebo typ.</span><span class="sxs-lookup"><span data-stu-id="c0f85-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="c0f85-111">Další informace naleznete v tématu "Import obsahující prvky" v [odkazech na deklarované elementy](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="c0f85-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

<span data-ttu-id="c0f85-112">Pokud kompilátor nemůže najít zadaný element, který obsahuje, nemůže vyřešit odkazy, které ho používají.</span><span class="sxs-lookup"><span data-stu-id="c0f85-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="c0f85-113">Pokud prvek najde, ale nezveřejňuje žádné `Public` členy, nemůže být žádný odkaz úspěšný.</span><span class="sxs-lookup"><span data-stu-id="c0f85-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="c0f85-114">V obou případech je to pro import elementu nevýznamný.</span><span class="sxs-lookup"><span data-stu-id="c0f85-114">In either case it is meaningless to import the element.</span></span>

<span data-ttu-id="c0f85-115">Mějte na paměti, že Pokud importujete element, který obsahuje, a přiřadíte mu alias pro import, nemůžete použít tento alias importu k importu jiného elementu.</span><span class="sxs-lookup"><span data-stu-id="c0f85-115">Keep in mind that if you import a containing element and assign an import alias to it, then you cannot use that import alias to import another element.</span></span> <span data-ttu-id="c0f85-116">Následující kód vygeneruje chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="c0f85-116">The following code generates a compiler error.</span></span>

```vb
Imports winfrm = System.Windows.Forms

' The following statement is INVALID  because it reuses an import alias.

Imports behave = winfrm.Design.Behavior`
```

<span data-ttu-id="c0f85-117">**ID chyby:** BC40056</span><span class="sxs-lookup"><span data-stu-id="c0f85-117">**Error ID:** BC40056</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="c0f85-118">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="c0f85-118">To correct this error</span></span>

1. <span data-ttu-id="c0f85-119">Ověřte, zda je obsažený element přístupný z vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="c0f85-119">Verify that the containing element is accessible from your project.</span></span>

2. <span data-ttu-id="c0f85-120">Ověřte, že specifikace obsahujícího elementu neobsahuje žádný alias importu z jiného importu.</span><span class="sxs-lookup"><span data-stu-id="c0f85-120">Verify that the specification of the containing element does not include any import alias from another import.</span></span>

3. <span data-ttu-id="c0f85-121">Ověřte, zda nadřazený element zveřejňuje alespoň jeden `Public` člen.</span><span class="sxs-lookup"><span data-stu-id="c0f85-121">Verify that the containing element exposes at least one `Public` member.</span></span>

## <a name="see-also"></a><span data-ttu-id="c0f85-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="c0f85-122">See also</span></span>

- [<span data-ttu-id="c0f85-123">Imports – příkaz (obor názvů a typ rozhraní .NET)</span><span class="sxs-lookup"><span data-stu-id="c0f85-123">Imports Statement (.NET Namespace and Type)</span></span>](../statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="c0f85-124">Namespace – příkaz</span><span class="sxs-lookup"><span data-stu-id="c0f85-124">Namespace Statement</span></span>](../statements/namespace-statement.md)
- [<span data-ttu-id="c0f85-125">Republik</span><span class="sxs-lookup"><span data-stu-id="c0f85-125">Public</span></span>](../modifiers/public.md)
- [<span data-ttu-id="c0f85-126">Obory názvů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c0f85-126">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="c0f85-127">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="c0f85-127">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
