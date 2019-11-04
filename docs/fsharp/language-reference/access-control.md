---
title: Řízení přístupu
description: Naučte se řídit přístup k programovacím prvkům, jako jsou typy, metody a funkce, v F# programovacím jazyce.
ms.date: 05/16/2016
ms.openlocfilehash: fe204a883a440794fdd033c54d6d8d4fb68e0ce2
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425113"
---
# <a name="access-control"></a><span data-ttu-id="69da8-103">Řízení přístupu</span><span class="sxs-lookup"><span data-stu-id="69da8-103">Access Control</span></span>

<span data-ttu-id="69da8-104">*Řízení přístupu* odkazuje na deklaraci toho, kteří klienti můžou používat určité prvky programu, jako jsou typy, metody a funkce.</span><span class="sxs-lookup"><span data-stu-id="69da8-104">*Access control* refers to declaring which clients can use certain program elements, such as types, methods, and functions.</span></span>

## <a name="basics-of-access-control"></a><span data-ttu-id="69da8-105">Základy Access Control</span><span class="sxs-lookup"><span data-stu-id="69da8-105">Basics of Access Control</span></span>

<span data-ttu-id="69da8-106">V F#nástroji specifikátory řízení přístupu `public`, `internal`a `private` lze použít na moduly, typy, metody, definice hodnot, funkce, vlastnosti a explicitní pole.</span><span class="sxs-lookup"><span data-stu-id="69da8-106">In F#, the access control specifiers `public`, `internal`, and `private` can be applied to modules, types, methods, value definitions, functions, properties, and explicit fields.</span></span>

- <span data-ttu-id="69da8-107">`public` označuje, že k entitě lze přistupovat všichni volající.</span><span class="sxs-lookup"><span data-stu-id="69da8-107">`public` indicates that the entity can be accessed by all callers.</span></span>

- <span data-ttu-id="69da8-108">`internal` označuje, že k entitě lze přistupovat pouze ze stejného sestavení.</span><span class="sxs-lookup"><span data-stu-id="69da8-108">`internal` indicates that the entity can be accessed only from the same assembly.</span></span>

- <span data-ttu-id="69da8-109">`private` označuje, že k entitě lze přistupovat pouze z ohraničujícího typu nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="69da8-109">`private` indicates that the entity can be accessed only from the enclosing type or module.</span></span>

> [!NOTE]
> <span data-ttu-id="69da8-110">Specifikátor přístupu `protected` se nepoužívá v F#, i když je přijatelný, pokud používáte typy vytvořené v jazycích, které podporují přístup `protected`.</span><span class="sxs-lookup"><span data-stu-id="69da8-110">The access specifier `protected` is not used in F#, although it is acceptable if you are using types authored in languages that do support `protected` access.</span></span> <span data-ttu-id="69da8-111">Proto pokud přepíšete chráněnou metodu, vaše metoda zůstane přístupná pouze v rámci třídy a jejích následníků.</span><span class="sxs-lookup"><span data-stu-id="69da8-111">Therefore, if you override a protected method, your method remains accessible only within the class and its descendents.</span></span>

<span data-ttu-id="69da8-112">Obecně je specifikátor umístěn před název entity, s výjimkou použití specifikátoru `mutable` nebo `inline`, který se zobrazí po specifikátoru řízení přístupu.</span><span class="sxs-lookup"><span data-stu-id="69da8-112">In general, the specifier is put in front of the name of the entity, except when a `mutable` or `inline` specifier is used, which appear after the access control specifier.</span></span>

<span data-ttu-id="69da8-113">Pokud není použit žádný specifikátor přístupu, výchozí hodnota je `public`, s výjimkou vazeb `let` v typu, které jsou vždy `private` na typ.</span><span class="sxs-lookup"><span data-stu-id="69da8-113">If no access specifier is used, the default is `public`, except for `let` bindings in a type, which are always `private` to the type.</span></span>

<span data-ttu-id="69da8-114">Signatury F# v nástroji poskytují jiný mechanismus řízení přístupu F# k prvkům programu.</span><span class="sxs-lookup"><span data-stu-id="69da8-114">Signatures in F# provide another mechanism for controlling access to F# program elements.</span></span> <span data-ttu-id="69da8-115">Pro řízení přístupu se signatury nevyžadují.</span><span class="sxs-lookup"><span data-stu-id="69da8-115">Signatures are not required for access control.</span></span> <span data-ttu-id="69da8-116">Další informace najdete v tématu [signatury](signature-files.md).</span><span class="sxs-lookup"><span data-stu-id="69da8-116">For more information, see [Signatures](signature-files.md).</span></span>

## <a name="rules-for-access-control"></a><span data-ttu-id="69da8-117">Pravidla pro Access Control</span><span class="sxs-lookup"><span data-stu-id="69da8-117">Rules for Access Control</span></span>

<span data-ttu-id="69da8-118">Řízení přístupu podléhá následujícím pravidlům:</span><span class="sxs-lookup"><span data-stu-id="69da8-118">Access control is subject to the following rules:</span></span>

- <span data-ttu-id="69da8-119">Deklarace dědičnosti (to znamená použití `inherit` k určení základní třídy pro třídu), deklarace rozhraní (to znamená, že třída implementuje rozhraní) a abstraktní členy mají vždy stejnou přístupnost jako nadřazený typ.</span><span class="sxs-lookup"><span data-stu-id="69da8-119">Inheritance declarations (that is, the use of `inherit` to specify a base class for a class), interface declarations (that is, specifying that a class implements an interface), and abstract members always have the same accessibility as the enclosing type.</span></span> <span data-ttu-id="69da8-120">Proto specifikátor řízení přístupu nelze použít na těchto konstrukcích.</span><span class="sxs-lookup"><span data-stu-id="69da8-120">Therefore, an access control specifier cannot be used on these constructs.</span></span>

- <span data-ttu-id="69da8-121">Přístupnost pro jednotlivé případy v rozlišeném sjednocení je určena přístupným přístupu přímo k rozlišenému sjednocení.</span><span class="sxs-lookup"><span data-stu-id="69da8-121">Accessibility for individual cases in a discriminated union is determined by the accessibility of the discriminated union itself.</span></span> <span data-ttu-id="69da8-122">To znamená, že konkrétní případ typu Union není méně dostupný než samotný sjednocení.</span><span class="sxs-lookup"><span data-stu-id="69da8-122">That is, a particular union case is no less accessible than the union itself.</span></span>

- <span data-ttu-id="69da8-123">Přístupnost pro jednotlivá pole typu záznamu je určena přístupností samotného záznamu.</span><span class="sxs-lookup"><span data-stu-id="69da8-123">Accessibility for individual fields of a record type is determined by the accessibility of the record itself.</span></span> <span data-ttu-id="69da8-124">To znamená, že konkrétní popisek záznamu není méně dostupný než samotný záznam.</span><span class="sxs-lookup"><span data-stu-id="69da8-124">That is, a particular record label is no less accessible than the record itself.</span></span>

## <a name="example"></a><span data-ttu-id="69da8-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="69da8-125">Example</span></span>

<span data-ttu-id="69da8-126">Následující kód ilustruje použití specifikátorů řízení přístupu.</span><span class="sxs-lookup"><span data-stu-id="69da8-126">The following code illustrates the use of access control specifiers.</span></span> <span data-ttu-id="69da8-127">V projektu jsou dva soubory `Module1.fs` a `Module2.fs`.</span><span class="sxs-lookup"><span data-stu-id="69da8-127">There are two files in the project, `Module1.fs` and `Module2.fs`.</span></span> <span data-ttu-id="69da8-128">Každý soubor je implicitně modulem.</span><span class="sxs-lookup"><span data-stu-id="69da8-128">Each file is implicitly a module.</span></span> <span data-ttu-id="69da8-129">Proto existují dva moduly `Module1` a `Module2`.</span><span class="sxs-lookup"><span data-stu-id="69da8-129">Therefore, there are two modules, `Module1` and `Module2`.</span></span> <span data-ttu-id="69da8-130">Privátní typ a interní typ jsou definovány v `Module1`.</span><span class="sxs-lookup"><span data-stu-id="69da8-130">A private type and an internal type are defined in `Module1`.</span></span> <span data-ttu-id="69da8-131">K privátnímu typu nelze přistup z `Module2`, ale interní typ může.</span><span class="sxs-lookup"><span data-stu-id="69da8-131">The private type cannot be accessed from `Module2`, but the internal type can.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet1.fs)]

<span data-ttu-id="69da8-132">Následující kód testuje přístupnost typů vytvořených v `Module1.fs`.</span><span class="sxs-lookup"><span data-stu-id="69da8-132">The following code tests the accessibility of the types created in `Module1.fs`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet2.fs)]

## <a name="see-also"></a><span data-ttu-id="69da8-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69da8-133">See also</span></span>

- [<span data-ttu-id="69da8-134">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="69da8-134">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="69da8-135">Signatury</span><span class="sxs-lookup"><span data-stu-id="69da8-135">Signatures</span></span>](signature-files.md)
