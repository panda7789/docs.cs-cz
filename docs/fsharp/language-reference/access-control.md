---
title: Řízení přístupu (F#)
description: Zjistěte, jak řídit přístup k programovací prvky, jako jsou typy, metody a funkce v programovacím jazyce F#.
ms.date: 05/16/2016
ms.openlocfilehash: 66a260d326acf07391e3775e5a7853654b4feee4
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "43803971"
---
# <a name="access-control"></a><span data-ttu-id="2047f-103">Access Control</span><span class="sxs-lookup"><span data-stu-id="2047f-103">Access Control</span></span>

<span data-ttu-id="2047f-104">*Řízení přístupu* odkazuje na deklarace, které klienty můžete použít některé prvky programu, jako jsou typy, metody a funkce.</span><span class="sxs-lookup"><span data-stu-id="2047f-104">*Access control* refers to declaring which clients can use certain program elements, such as types, methods, and functions.</span></span>

## <a name="basics-of-access-control"></a><span data-ttu-id="2047f-105">Základní informace o řízení přístupu</span><span class="sxs-lookup"><span data-stu-id="2047f-105">Basics of Access Control</span></span>

<span data-ttu-id="2047f-106">V jazyce F#, řízení přístupu specifikátory `public`, `internal`, a `private` lze použít u modulů, typy, metody, definice hodnot, funkce, vlastnosti a explicitní pole.</span><span class="sxs-lookup"><span data-stu-id="2047f-106">In F#, the access control specifiers `public`, `internal`, and `private` can be applied to modules, types, methods, value definitions, functions, properties, and explicit fields.</span></span>

- <span data-ttu-id="2047f-107">`public` Označuje, že entita je přístupný všem volajícím.</span><span class="sxs-lookup"><span data-stu-id="2047f-107">`public` indicates that the entity can be accessed by all callers.</span></span>

- <span data-ttu-id="2047f-108">`internal` Označuje, že entita je přístupný jenom ze stejného sestavení.</span><span class="sxs-lookup"><span data-stu-id="2047f-108">`internal` indicates that the entity can be accessed only from the same assembly.</span></span>

- <span data-ttu-id="2047f-109">`private` Označuje, že entita je přístupný pouze z nadřazeného typu nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="2047f-109">`private` indicates that the entity can be accessed only from the enclosing type or module.</span></span>

>[!NOTE]
<span data-ttu-id="2047f-110">Specifikátor přístupu `protected` se nepoužívá v jazyce F#, i když je přijatelné, pokud používáte typů definovaných v jazycích, které podporují `protected` přístup.</span><span class="sxs-lookup"><span data-stu-id="2047f-110">The access specifier `protected` is not used in F#, although it is acceptable if you are using types authored in languages that do support `protected` access.</span></span> <span data-ttu-id="2047f-111">Proto pokud je přepsat chráněnou metodu, metodu zůstane dostupný jenom v rámci třídy a jeho následovníky.</span><span class="sxs-lookup"><span data-stu-id="2047f-111">Therefore, if you override a protected method, your method remains accessible only within the class and its descendents.</span></span>

<span data-ttu-id="2047f-112">Obecně platí, je specifikátor umístit před název sady entit, kromě případů, kdy `mutable` nebo `inline` specifikátor se používá, které se zobrazí po specifikátoru přístupu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2047f-112">In general, the specifier is put in front of the name of the entity, except when a `mutable` or `inline` specifier is used, which appear after the access control specifier.</span></span>

<span data-ttu-id="2047f-113">Pokud není použit žádný specifikátor přístupu, výchozí hodnota je `public`, s výjimkou `let` vazby v typu, které jsou vždy `private` typu.</span><span class="sxs-lookup"><span data-stu-id="2047f-113">If no access specifier is used, the default is `public`, except for `let` bindings in a type, which are always `private` to the type.</span></span>

<span data-ttu-id="2047f-114">Podpisy v jazyce F# zadejte jiný mechanismus pro řízení přístupu na prvky programu F#.</span><span class="sxs-lookup"><span data-stu-id="2047f-114">Signatures in F# provide another mechanism for controlling access to F# program elements.</span></span> <span data-ttu-id="2047f-115">Podpisy nejsou požadována pro řízení přístupu.</span><span class="sxs-lookup"><span data-stu-id="2047f-115">Signatures are not required for access control.</span></span> <span data-ttu-id="2047f-116">Další informace najdete v tématu [podpisy](signatures.md).</span><span class="sxs-lookup"><span data-stu-id="2047f-116">For more information, see [Signatures](signatures.md).</span></span>

## <a name="rules-for-access-control"></a><span data-ttu-id="2047f-117">Pravidla pro řízení přístupu</span><span class="sxs-lookup"><span data-stu-id="2047f-117">Rules for Access Control</span></span>

<span data-ttu-id="2047f-118">Řízení přístupu se vztahují následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="2047f-118">Access control is subject to the following rules:</span></span>

- <span data-ttu-id="2047f-119">Deklarace dědičnosti (to znamená použití `inherit` k určení základní třída pro třídu), deklarace (které se určuje, že třída implementuje rozhraní) rozhraní a abstraktní členové mají vždy stejnou přístupností jako nadřazený typ.</span><span class="sxs-lookup"><span data-stu-id="2047f-119">Inheritance declarations (that is, the use of `inherit` to specify a base class for a class), interface declarations (that is, specifying that a class implements an interface), and abstract members always have the same accessibility as the enclosing type.</span></span> <span data-ttu-id="2047f-120">Proto nelze použít specifikátor řízení přístupu na tyto konstrukce.</span><span class="sxs-lookup"><span data-stu-id="2047f-120">Therefore, an access control specifier cannot be used on these constructs.</span></span>

- <span data-ttu-id="2047f-121">Usnadnění pro jednotlivé případy diskriminovaného sjednocení se určuje podle usnadnění diskriminované sjednocení, samotného.</span><span class="sxs-lookup"><span data-stu-id="2047f-121">Accessibility for individual cases in a discriminated union is determined by the accessibility of the discriminated union itself.</span></span> <span data-ttu-id="2047f-122">To znamená je konkrétní – případ typu union ne míň dostupný než samotné sjednocení.</span><span class="sxs-lookup"><span data-stu-id="2047f-122">That is, a particular union case is no less accessible than the union itself.</span></span>

- <span data-ttu-id="2047f-123">Usnadnění pro jednotlivá pole záznamu typu nelze je určena dostupnost samotného záznamu.</span><span class="sxs-lookup"><span data-stu-id="2047f-123">Accessibility for individual fields of a record type cannot is determined by the accessibility of the record itself.</span></span> <span data-ttu-id="2047f-124">Popisek konkrétního záznamu je tedy ne míň dostupný než samotného záznamu.</span><span class="sxs-lookup"><span data-stu-id="2047f-124">That is, a particular record label is no less accessible than the record itself.</span></span>

## <a name="example"></a><span data-ttu-id="2047f-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="2047f-125">Example</span></span>

<span data-ttu-id="2047f-126">Následující kód ukazuje použití specifikátorů řízení přístupu.</span><span class="sxs-lookup"><span data-stu-id="2047f-126">The following code illustrates the use of access control specifiers.</span></span> <span data-ttu-id="2047f-127">Existují dva soubory v projektu `Module1.fs` a `Module2.fs`.</span><span class="sxs-lookup"><span data-stu-id="2047f-127">There are two files in the project, `Module1.fs` and `Module2.fs`.</span></span> <span data-ttu-id="2047f-128">Každý soubor je implicitně modul.</span><span class="sxs-lookup"><span data-stu-id="2047f-128">Each file is implicitly a module.</span></span> <span data-ttu-id="2047f-129">Proto existují dva moduly `Module1` a `Module2`.</span><span class="sxs-lookup"><span data-stu-id="2047f-129">Therefore, there are two modules, `Module1` and `Module2`.</span></span> <span data-ttu-id="2047f-130">Typ privátní a interní typ jsou definovány v `Module1`.</span><span class="sxs-lookup"><span data-stu-id="2047f-130">A private type and an internal type are defined in `Module1`.</span></span> <span data-ttu-id="2047f-131">Privátní typ nejde přistupovat z `Module2`, ale můžete vnitřního typu.</span><span class="sxs-lookup"><span data-stu-id="2047f-131">The private type cannot be accessed from `Module2`, but the internal type can.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet1.fs)]

<span data-ttu-id="2047f-132">Následující kód testy přístupnost typů vytvořených v `Module1.fs`.</span><span class="sxs-lookup"><span data-stu-id="2047f-132">The following code tests the accessibility of the types created in `Module1.fs`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet2.fs)]

## <a name="see-also"></a><span data-ttu-id="2047f-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2047f-133">See also</span></span>

- [<span data-ttu-id="2047f-134">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="2047f-134">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="2047f-135">Signatury</span><span class="sxs-lookup"><span data-stu-id="2047f-135">Signatures</span></span>](signatures.md)
