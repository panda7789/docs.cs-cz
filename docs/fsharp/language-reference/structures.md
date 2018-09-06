---
title: Struktury (F#)
description: 'Další informace o F # strukturu, typ compact objektu, který je často efektivnější než třída pro typy s menším objemem dat a jednoduché chování.'
ms.date: 05/16/2016
ms.openlocfilehash: 889d493af3c9c388bdc7969c02bc7b021b82517d
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43799668"
---
# <a name="structures"></a><span data-ttu-id="e0e61-103">Struktury</span><span class="sxs-lookup"><span data-stu-id="e0e61-103">Structures</span></span>

<span data-ttu-id="e0e61-104">A *struktura* typ compact objekt, který může být efektivnější než třída pro typy, které mají malé množství dat a jednoduché chování.</span><span class="sxs-lookup"><span data-stu-id="e0e61-104">A *structure* is a compact object type that can be more efficient than a class for types that have a small amount of data and simple behavior.</span></span>

## <a name="syntax"></a><span data-ttu-id="e0e61-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0e61-105">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    struct
        type-definition-elements-and-members
    end
// or
[ attributes ]
[<StructAttribute>]
type [accessibility-modifier] type-name =
    type-definition-elements-and-members
```

## <a name="remarks"></a><span data-ttu-id="e0e61-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e0e61-106">Remarks</span></span>

<span data-ttu-id="e0e61-107">Struktury jsou *typů hodnot*, to znamená, že se ukládají přímo na zásobníku, nebo když se používají jako pole nebo typ prvků pole, vložený v nadřazeném prvku.</span><span class="sxs-lookup"><span data-stu-id="e0e61-107">Structures are *value types*, which means that they are stored directly on the stack or, when they are used as fields or array elements, inline in the parent type.</span></span> <span data-ttu-id="e0e61-108">Na rozdíl od třídy a záznamů struktury mají sémantiku pass podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e0e61-108">Unlike classes and records, structures have pass-by-value semantics.</span></span> <span data-ttu-id="e0e61-109">To znamená, že jsou užitečné především pro malé agregace dat, které jsou přístupné a často zkopírován.</span><span class="sxs-lookup"><span data-stu-id="e0e61-109">This means that they are useful primarily for small aggregates of data that are accessed and copied frequently.</span></span>

<span data-ttu-id="e0e61-110">V předchozí syntaxi jsou uvedeny dva formuláře.</span><span class="sxs-lookup"><span data-stu-id="e0e61-110">In the previous syntax, two forms are shown.</span></span> <span data-ttu-id="e0e61-111">První není nenáročném syntaxi, ale přesto často se používá proto, že při použití `struct` a `end` klíčová slova, můžete vynechat `StructAttribute` atribut, který se zobrazí ve formuláři druhý.</span><span class="sxs-lookup"><span data-stu-id="e0e61-111">The first is not the lightweight syntax, but it is nevertheless frequently used because, when you use the `struct` and `end` keywords, you can omit the `StructAttribute` attribute, which appears in the second form.</span></span> <span data-ttu-id="e0e61-112">Můžete zkrátit `StructAttribute` jenom `Struct`.</span><span class="sxs-lookup"><span data-stu-id="e0e61-112">You can abbreviate `StructAttribute` to just `Struct`.</span></span>

<span data-ttu-id="e0e61-113">*– Definice – elementy a členy typu* v předchozí syntaxi představuje člen deklarace a definice.</span><span class="sxs-lookup"><span data-stu-id="e0e61-113">The *type-definition-elements-and-members* in the previous syntax represents member declarations and definitions.</span></span> <span data-ttu-id="e0e61-114">Struktury mohou mít konstruktory a pole proměnlivé a neměnné a lze deklarovat členy a implementace rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e0e61-114">Structures can have constructors and mutable and immutable fields, and they can declare members and interface implementations.</span></span> <span data-ttu-id="e0e61-115">Další informace najdete v tématu [členy](members/index.md).</span><span class="sxs-lookup"><span data-stu-id="e0e61-115">For more information, see [Members](members/index.md).</span></span>

<span data-ttu-id="e0e61-116">Struktury nemůže být součástí dědičnosti, nesmí obsahovat `let` nebo `do` vazby, a nemůže rekurzivně obsahovat pole vlastní typu (i když mohou obsahovat odkazové buňky, které odkazují na své vlastní typ).</span><span class="sxs-lookup"><span data-stu-id="e0e61-116">Structures cannot participate in inheritance, cannot contain `let` or `do` bindings, and cannot recursively contain fields of their own type (although they can contain reference cells that reference their own type).</span></span>

<span data-ttu-id="e0e61-117">Protože struktury nejsou povoleny `let` vazby, je třeba deklarovat s použitím pole ve strukturách `val` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="e0e61-117">Because structures do not allow `let` bindings, you must declare fields in structures by using the `val` keyword.</span></span> <span data-ttu-id="e0e61-118">`val` – Klíčové slovo definuje pole a jeho typ, ale neumožňuje inicializace.</span><span class="sxs-lookup"><span data-stu-id="e0e61-118">The `val` keyword defines a field and its type but does not allow initialization.</span></span> <span data-ttu-id="e0e61-119">Místo toho `val` deklarace jsou inicializována na hodnotu nula nebo mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="e0e61-119">Instead, `val` declarations are initialized to zero or null.</span></span> <span data-ttu-id="e0e61-120">Z tohoto důvodu struktury, které mají implicitní konstruktor (to znamená, parametrů, která jsou uvedena ihned po název struktury v deklaraci) vyžadují, aby `val` deklarace být komentována atributem `DefaultValue` atribut.</span><span class="sxs-lookup"><span data-stu-id="e0e61-120">For this reason, structures that have an implicit constructor (that is, parameters that are given immediately after the structure name in the declaration) require that `val` declarations be annotated with the `DefaultValue` attribute.</span></span> <span data-ttu-id="e0e61-121">Struktury, které mají definovanou konstruktor podporovat inicializace nula.</span><span class="sxs-lookup"><span data-stu-id="e0e61-121">Structures that have a defined constructor still support zero-initialization.</span></span> <span data-ttu-id="e0e61-122">Proto `DefaultValue` atribut je deklarace platnost těchto nulová hodnota pro pole.</span><span class="sxs-lookup"><span data-stu-id="e0e61-122">Therefore, the `DefaultValue` attribute is a declaration that such a zero value is valid for the field.</span></span> <span data-ttu-id="e0e61-123">Implicitní konstruktory pro struktury nebudete provádět všechny akce, protože `let` a `do` vazby nejsou povolené pro typ, ale jsou k dispozici jako privátní pole předané hodnoty parametrů implicitní konstruktor.</span><span class="sxs-lookup"><span data-stu-id="e0e61-123">Implicit constructors for structures do not perform any actions because `let` and `do` bindings aren’t allowed on the type, but the implicit constructor parameter values passed in are available as private fields.</span></span>

<span data-ttu-id="e0e61-124">Explicitní konstruktory může zahrnovat inicializace hodnot polí.</span><span class="sxs-lookup"><span data-stu-id="e0e61-124">Explicit constructors might involve initialization of field values.</span></span> <span data-ttu-id="e0e61-125">Pokud máte strukturu, která má explicitní konstruktor, stále podporuje inicializace nula; ale je velmi riskantní používat `DefaultValue` atribut na `val` deklarace vzhledem k tomu, že je v konfliktu s explicitní konstruktor.</span><span class="sxs-lookup"><span data-stu-id="e0e61-125">When you have a structure that has an explicit constructor, it still supports zero-initialization; however, you do not use the `DefaultValue` attribute on the `val` declarations because it conflicts with the explicit constructor.</span></span> <span data-ttu-id="e0e61-126">Další informace o `val` deklarací, naleznete v tématu [explicitní pole: `val` – klíčové slovo](members/explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="e0e61-126">For more information about `val` declarations, see [Explicit Fields: The `val` Keyword](members/explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="e0e61-127">Atributy a modifikátory dostupnosti pro struktury jsou povolené a řídit stejnými pravidly jako u jiných typů.</span><span class="sxs-lookup"><span data-stu-id="e0e61-127">Attributes and accessibility modifiers are allowed on structures, and follow the same rules as those for other types.</span></span> <span data-ttu-id="e0e61-128">Další informace najdete v tématu [atributy](attributes.md) a [řízení přístupu](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="e0e61-128">For more information, see [Attributes](attributes.md) and [Access Control](access-control.md).</span></span>

<span data-ttu-id="e0e61-129">Následující příklady kódu znázorňují definice struktury.</span><span class="sxs-lookup"><span data-stu-id="e0e61-129">The following code examples illustrate structure definitions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="struct-records-and-discriminated-unions"></a><span data-ttu-id="e0e61-130">Rozlišovaná sjednocení a struktura záznamů</span><span class="sxs-lookup"><span data-stu-id="e0e61-130">Struct Records and Discriminated Unions</span></span>

<span data-ttu-id="e0e61-131">Od verze F # 4.1, může představovat [záznamy](records.md) a [Rozlišované sjednocení](discriminated-unions.md) jako struktury s `[<Struct>]` atribut.</span><span class="sxs-lookup"><span data-stu-id="e0e61-131">Starting with F# 4.1, you can represent [Records](records.md) and [Discriminated Unions](discriminated-unions.md) as structs with the `[<Struct>]` attribute.</span></span>  <span data-ttu-id="e0e61-132">Další informace v každého článku.</span><span class="sxs-lookup"><span data-stu-id="e0e61-132">See each article to learn more.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0e61-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0e61-133">See also</span></span>

- [<span data-ttu-id="e0e61-134">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="e0e61-134">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="e0e61-135">Třídy</span><span class="sxs-lookup"><span data-stu-id="e0e61-135">Classes</span></span>](classes.md)
- [<span data-ttu-id="e0e61-136">Záznamy</span><span class="sxs-lookup"><span data-stu-id="e0e61-136">Records</span></span>](records.md)
- [<span data-ttu-id="e0e61-137">Členové</span><span class="sxs-lookup"><span data-stu-id="e0e61-137">Members</span></span>](members/index.md)
