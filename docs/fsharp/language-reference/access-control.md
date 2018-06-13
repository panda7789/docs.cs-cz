---
title: Řízení přístupu (F#)
description: 'Zjistěte, jak řídit přístup k elementům programování, jako jsou typy, metod a funkce v programovací jazyk F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 0a5cc1faa1aef343aaca0abb0c42a0dd9a52fcbb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566519"
---
# <a name="access-control"></a><span data-ttu-id="1076d-103">Access Control</span><span class="sxs-lookup"><span data-stu-id="1076d-103">Access Control</span></span>

<span data-ttu-id="1076d-104">*Řízení přístupu* odkazuje na deklarace, které klienty můžete použít určité program elementů, například typy, metod a funkce.</span><span class="sxs-lookup"><span data-stu-id="1076d-104">*Access control* refers to declaring which clients can use certain program elements, such as types, methods, and functions.</span></span>


## <a name="basics-of-access-control"></a><span data-ttu-id="1076d-105">Základní informace o řízení přístupu</span><span class="sxs-lookup"><span data-stu-id="1076d-105">Basics of Access Control</span></span>
<span data-ttu-id="1076d-106">V jazyce F #, řízení přístupu specifikátory `public`, `internal`, a `private` lze použít na moduly, typy, metody, definice hodnotu, funkce, vlastnosti a explicitní pole.</span><span class="sxs-lookup"><span data-stu-id="1076d-106">In F#, the access control specifiers `public`, `internal`, and `private` can be applied to modules, types, methods, value definitions, functions, properties, and explicit fields.</span></span>


- <span data-ttu-id="1076d-107">`public` Označuje, že entita byla přístupná pomocí všechny volající.</span><span class="sxs-lookup"><span data-stu-id="1076d-107">`public` indicates that the entity can be accessed by all callers.</span></span>

- <span data-ttu-id="1076d-108">`internal` Označuje, že entita může přistupovat pouze z stejného sestavení.</span><span class="sxs-lookup"><span data-stu-id="1076d-108">`internal` indicates that the entity can be accessed only from the same assembly.</span></span>

- <span data-ttu-id="1076d-109">`private` Označuje, že entita může přistupovat pouze z nadřazených modul nebo typ.</span><span class="sxs-lookup"><span data-stu-id="1076d-109">`private` indicates that the entity can be accessed only from the enclosing type or module.</span></span>


>[!NOTE] 
<span data-ttu-id="1076d-110">Specifikátor přístupu `protected` se nepoužívá v F # je přijatelné, pokud používáte typy vytvořené v jazycích, které podporují `protected` přístup.</span><span class="sxs-lookup"><span data-stu-id="1076d-110">The access specifier `protected` is not used in F#, although it is acceptable if you are using types authored in languages that do support `protected` access.</span></span> <span data-ttu-id="1076d-111">Proto pokud chráněný metodu přepíšete, metodu zůstávají dostupné pouze v rámci třídy a jejího podřízeného prvku.</span><span class="sxs-lookup"><span data-stu-id="1076d-111">Therefore, if you override a protected method, your method remains accessible only within the class and its descendents.</span></span>

<span data-ttu-id="1076d-112">Obecně platí, je před název entity, s výjimkou případů, kdy se umístí specifikátor `mutable` nebo `inline` specifikátor se používá, které jsou uvedeny po specifikátor řízení přístupu.</span><span class="sxs-lookup"><span data-stu-id="1076d-112">In general, the specifier is put in front of the name of the entity, except when a `mutable` or `inline` specifier is used, which appear after the access control specifier.</span></span>

<span data-ttu-id="1076d-113">Pokud se používá žádný přístup specifikátor, výchozí hodnota je `public`, s výjimkou `let` vazeb v typu, které jsou vždy `private` typu.</span><span class="sxs-lookup"><span data-stu-id="1076d-113">If no access specifier is used, the default is `public`, except for `let` bindings in a type, which are always `private` to the type.</span></span>

<span data-ttu-id="1076d-114">Podpisy v jazyce F # nabízejí jiný mechanismus řízení přístupu na elementy program F #.</span><span class="sxs-lookup"><span data-stu-id="1076d-114">Signatures in F# provide another mechanism for controlling access to F# program elements.</span></span> <span data-ttu-id="1076d-115">Podpisy nejsou nutné pro řízení přístupu.</span><span class="sxs-lookup"><span data-stu-id="1076d-115">Signatures are not required for access control.</span></span> <span data-ttu-id="1076d-116">Další informace najdete v tématu [podpisy](signatures.md).</span><span class="sxs-lookup"><span data-stu-id="1076d-116">For more information, see [Signatures](signatures.md).</span></span>


## <a name="rules-for-access-control"></a><span data-ttu-id="1076d-117">Pravidla pro řízení přístupu</span><span class="sxs-lookup"><span data-stu-id="1076d-117">Rules for Access Control</span></span>
<span data-ttu-id="1076d-118">Řízení přístupu podléhá následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="1076d-118">Access control is subject to the following rules:</span></span>


- <span data-ttu-id="1076d-119">Deklarace dědičnosti (to znamená použití `inherit` určit základní třídu pro třídu), rozhraní deklarace (které se určuje, že třída implementuje rozhraní) a abstraktní členy, bude mít vždy stejnou usnadnění jako nadřazených typů.</span><span class="sxs-lookup"><span data-stu-id="1076d-119">Inheritance declarations (that is, the use of `inherit` to specify a base class for a class), interface declarations (that is, specifying that a class implements an interface), and abstract members always have the same accessibility as the enclosing type.</span></span> <span data-ttu-id="1076d-120">Proto nelze použít specifikátor řízení přístupu na tyto konstrukce.</span><span class="sxs-lookup"><span data-stu-id="1076d-120">Therefore, an access control specifier cannot be used on these constructs.</span></span>

- <span data-ttu-id="1076d-121">Rozlišovaná sjednocení jednotlivých případech, nemůže mít vlastní ovládací prvek modifikátory přístupu odděleně od typu union.</span><span class="sxs-lookup"><span data-stu-id="1076d-121">Individual cases in a discriminated union cannot have their own access control modifiers separate from the union type.</span></span>

- <span data-ttu-id="1076d-122">Jednotlivá pole typu záznamu nemůže mít vlastní ovládací prvek modifikátory přístupu odděleně od typ záznamu.</span><span class="sxs-lookup"><span data-stu-id="1076d-122">Individual fields of a record type cannot have their own access control modifiers separate from the record type.</span></span>


## <a name="example"></a><span data-ttu-id="1076d-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="1076d-123">Example</span></span>
<span data-ttu-id="1076d-124">Následující kód ukazuje použití specifikátory řízení přístupu.</span><span class="sxs-lookup"><span data-stu-id="1076d-124">The following code illustrates the use of access control specifiers.</span></span> <span data-ttu-id="1076d-125">Existují dva soubory v projektu `Module1.fs` a `Module2.fs`.</span><span class="sxs-lookup"><span data-stu-id="1076d-125">There are two files in the project, `Module1.fs` and `Module2.fs`.</span></span> <span data-ttu-id="1076d-126">Každý soubor je implicitně modul.</span><span class="sxs-lookup"><span data-stu-id="1076d-126">Each file is implicitly a module.</span></span> <span data-ttu-id="1076d-127">Proto existují dvě moduly `Module1` a `Module2`.</span><span class="sxs-lookup"><span data-stu-id="1076d-127">Therefore, there are two modules, `Module1` and `Module2`.</span></span> <span data-ttu-id="1076d-128">Typu privátní a interní typ jsou definovány v `Module1`.</span><span class="sxs-lookup"><span data-stu-id="1076d-128">A private type and an internal type are defined in `Module1`.</span></span> <span data-ttu-id="1076d-129">Typ privátního není přístupný z `Module2`, ale můžete interní typ.</span><span class="sxs-lookup"><span data-stu-id="1076d-129">The private type cannot be accessed from `Module2`, but the internal type can.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet1.fs)]
    
<span data-ttu-id="1076d-130">Následující kód testy usnadnění typů vytvořené v `Module1.fs`.</span><span class="sxs-lookup"><span data-stu-id="1076d-130">The following code tests the accessibility of the types created in `Module1.fs`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet2.fs)]
    
## <a name="see-also"></a><span data-ttu-id="1076d-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="1076d-131">See Also</span></span>
[<span data-ttu-id="1076d-132">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="1076d-132">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="1076d-133">Signatury</span><span class="sxs-lookup"><span data-stu-id="1076d-133">Signatures</span></span>](signatures.md)
