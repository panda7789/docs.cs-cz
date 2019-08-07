---
title: Řízení přístupu
description: Naučte se řídit přístup k programovacím prvkům, jako jsou typy, metody a funkce, v F# programovacím jazyce.
ms.date: 05/16/2016
ms.openlocfilehash: 38f8f3fd4114c0428fbe8baca71594cd07740b2c
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817857"
---
# <a name="access-control"></a><span data-ttu-id="c12e7-103">Řízení přístupu</span><span class="sxs-lookup"><span data-stu-id="c12e7-103">Access Control</span></span>

<span data-ttu-id="c12e7-104">*Řízení přístupu* odkazuje na deklaraci toho, kteří klienti můžou používat určité prvky programu, jako jsou typy, metody a funkce.</span><span class="sxs-lookup"><span data-stu-id="c12e7-104">*Access control* refers to declaring which clients can use certain program elements, such as types, methods, and functions.</span></span>

## <a name="basics-of-access-control"></a><span data-ttu-id="c12e7-105">Základy Access Control</span><span class="sxs-lookup"><span data-stu-id="c12e7-105">Basics of Access Control</span></span>

<span data-ttu-id="c12e7-106">V F#nástroji specifikátory `public`řízení přístupu, `internal`a `private` lze použít na moduly, typy, metody, definice hodnot, funkce, vlastnosti a explicitní pole.</span><span class="sxs-lookup"><span data-stu-id="c12e7-106">In F#, the access control specifiers `public`, `internal`, and `private` can be applied to modules, types, methods, value definitions, functions, properties, and explicit fields.</span></span>

- <span data-ttu-id="c12e7-107">`public`označuje, že k entitě lze přistupovat všichni volající.</span><span class="sxs-lookup"><span data-stu-id="c12e7-107">`public` indicates that the entity can be accessed by all callers.</span></span>

- <span data-ttu-id="c12e7-108">`internal`označuje, že k entitě lze přistupovat pouze ze stejného sestavení.</span><span class="sxs-lookup"><span data-stu-id="c12e7-108">`internal` indicates that the entity can be accessed only from the same assembly.</span></span>

- <span data-ttu-id="c12e7-109">`private`označuje, že k entitě lze přistupovat pouze z ohraničujícího typu nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="c12e7-109">`private` indicates that the entity can be accessed only from the enclosing type or module.</span></span>

> [!NOTE]
> <span data-ttu-id="c12e7-110">Specifikátor `protected` přístupu se nepoužívá v F#, i když je přijatelný, pokud používáte typy vytvořené v `protected` jazycích, které podporují přístup.</span><span class="sxs-lookup"><span data-stu-id="c12e7-110">The access specifier `protected` is not used in F#, although it is acceptable if you are using types authored in languages that do support `protected` access.</span></span> <span data-ttu-id="c12e7-111">Proto pokud přepíšete chráněnou metodu, vaše metoda zůstane přístupná pouze v rámci třídy a jejích následníků.</span><span class="sxs-lookup"><span data-stu-id="c12e7-111">Therefore, if you override a protected method, your method remains accessible only within the class and its descendents.</span></span>

<span data-ttu-id="c12e7-112">Obecně je specifikátor umístěn před název entity, s výjimkou případu, kdy `mutable` se používá specifikátor nebo `inline` , který se zobrazí po specifikátoru řízení přístupu.</span><span class="sxs-lookup"><span data-stu-id="c12e7-112">In general, the specifier is put in front of the name of the entity, except when a `mutable` or `inline` specifier is used, which appear after the access control specifier.</span></span>

<span data-ttu-id="c12e7-113">Pokud není použit žádný specifikátor přístupu, je `public`výchozí hodnota, `let` s výjimkou vazeb v typu, které jsou vždy `private` typu.</span><span class="sxs-lookup"><span data-stu-id="c12e7-113">If no access specifier is used, the default is `public`, except for `let` bindings in a type, which are always `private` to the type.</span></span>

<span data-ttu-id="c12e7-114">Signatury F# v nástroji poskytují jiný mechanismus řízení přístupu F# k prvkům programu.</span><span class="sxs-lookup"><span data-stu-id="c12e7-114">Signatures in F# provide another mechanism for controlling access to F# program elements.</span></span> <span data-ttu-id="c12e7-115">Pro řízení přístupu se signatury nevyžadují.</span><span class="sxs-lookup"><span data-stu-id="c12e7-115">Signatures are not required for access control.</span></span> <span data-ttu-id="c12e7-116">Další informace najdete v tématu [signatury](signatures.md).</span><span class="sxs-lookup"><span data-stu-id="c12e7-116">For more information, see [Signatures](signatures.md).</span></span>

## <a name="rules-for-access-control"></a><span data-ttu-id="c12e7-117">Pravidla pro Access Control</span><span class="sxs-lookup"><span data-stu-id="c12e7-117">Rules for Access Control</span></span>

<span data-ttu-id="c12e7-118">Řízení přístupu podléhá následujícím pravidlům:</span><span class="sxs-lookup"><span data-stu-id="c12e7-118">Access control is subject to the following rules:</span></span>

- <span data-ttu-id="c12e7-119">Deklarace dědičnosti (to znamená použití `inherit` k určení základní třídy pro třídu), deklarace rozhraní (to znamená, že třída implementuje rozhraní) a abstraktní členové mají vždy stejné přístupnost jako nadřazený typ.</span><span class="sxs-lookup"><span data-stu-id="c12e7-119">Inheritance declarations (that is, the use of `inherit` to specify a base class for a class), interface declarations (that is, specifying that a class implements an interface), and abstract members always have the same accessibility as the enclosing type.</span></span> <span data-ttu-id="c12e7-120">Proto specifikátor řízení přístupu nelze použít na těchto konstrukcích.</span><span class="sxs-lookup"><span data-stu-id="c12e7-120">Therefore, an access control specifier cannot be used on these constructs.</span></span>

- <span data-ttu-id="c12e7-121">Přístupnost pro jednotlivé případy v rozlišeném sjednocení je určena přístupným přístupu přímo k rozlišenému sjednocení.</span><span class="sxs-lookup"><span data-stu-id="c12e7-121">Accessibility for individual cases in a discriminated union is determined by the accessibility of the discriminated union itself.</span></span> <span data-ttu-id="c12e7-122">To znamená, že konkrétní případ typu Union není méně dostupný než samotný sjednocení.</span><span class="sxs-lookup"><span data-stu-id="c12e7-122">That is, a particular union case is no less accessible than the union itself.</span></span>

- <span data-ttu-id="c12e7-123">Přístupnost pro jednotlivá pole typu záznamu je určena přístupností samotného záznamu.</span><span class="sxs-lookup"><span data-stu-id="c12e7-123">Accessibility for individual fields of a record type is determined by the accessibility of the record itself.</span></span> <span data-ttu-id="c12e7-124">To znamená, že konkrétní popisek záznamu není méně dostupný než samotný záznam.</span><span class="sxs-lookup"><span data-stu-id="c12e7-124">That is, a particular record label is no less accessible than the record itself.</span></span>

## <a name="example"></a><span data-ttu-id="c12e7-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="c12e7-125">Example</span></span>

<span data-ttu-id="c12e7-126">Následující kód ilustruje použití specifikátorů řízení přístupu.</span><span class="sxs-lookup"><span data-stu-id="c12e7-126">The following code illustrates the use of access control specifiers.</span></span> <span data-ttu-id="c12e7-127">V projektu jsou dva soubory, `Module1.fs` a. `Module2.fs`</span><span class="sxs-lookup"><span data-stu-id="c12e7-127">There are two files in the project, `Module1.fs` and `Module2.fs`.</span></span> <span data-ttu-id="c12e7-128">Každý soubor je implicitně modulem.</span><span class="sxs-lookup"><span data-stu-id="c12e7-128">Each file is implicitly a module.</span></span> <span data-ttu-id="c12e7-129">Proto existují dva moduly `Module1` a. `Module2`</span><span class="sxs-lookup"><span data-stu-id="c12e7-129">Therefore, there are two modules, `Module1` and `Module2`.</span></span> <span data-ttu-id="c12e7-130">Privátní typ a interní typ jsou definovány v `Module1`.</span><span class="sxs-lookup"><span data-stu-id="c12e7-130">A private type and an internal type are defined in `Module1`.</span></span> <span data-ttu-id="c12e7-131">K privátnímu typu nelze přicházet `Module2`z, ale interní typ může.</span><span class="sxs-lookup"><span data-stu-id="c12e7-131">The private type cannot be accessed from `Module2`, but the internal type can.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet1.fs)]

<span data-ttu-id="c12e7-132">Následující kód testuje přístupnost typů vytvořených v `Module1.fs`.</span><span class="sxs-lookup"><span data-stu-id="c12e7-132">The following code tests the accessibility of the types created in `Module1.fs`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet2.fs)]

## <a name="see-also"></a><span data-ttu-id="c12e7-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c12e7-133">See also</span></span>

- [<span data-ttu-id="c12e7-134">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="c12e7-134">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="c12e7-135">Signatury</span><span class="sxs-lookup"><span data-stu-id="c12e7-135">Signatures</span></span>](signatures.md)
