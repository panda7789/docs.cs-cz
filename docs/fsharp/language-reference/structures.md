---
title: Struktury
description: Další informace o f# struktury, kompaktní typ objektu často efektivnější než třída pro typy s malým množstvím dat a jednoduché chování.
ms.date: 05/16/2016
ms.openlocfilehash: 1e9652cc4776e4d1d52eb20e41b6dd87a6c5ba05
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400279"
---
# <a name="structures"></a><span data-ttu-id="2929f-103">Struktury</span><span class="sxs-lookup"><span data-stu-id="2929f-103">Structures</span></span>

<span data-ttu-id="2929f-104">*Struktura* je kompaktní typ objektu, který může být efektivnější než třída pro typy, které mají malé množství dat a jednoduché chování.</span><span class="sxs-lookup"><span data-stu-id="2929f-104">A *structure* is a compact object type that can be more efficient than a class for types that have a small amount of data and simple behavior.</span></span>

## <a name="syntax"></a><span data-ttu-id="2929f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2929f-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="2929f-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2929f-106">Remarks</span></span>

<span data-ttu-id="2929f-107">Struktury jsou *typy hodnot*, což znamená, že jsou uloženy přímo v zásobníku nebo, pokud jsou použity jako pole nebo prvky pole, vložených do nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="2929f-107">Structures are *value types*, which means that they are stored directly on the stack or, when they are used as fields or array elements, inline in the parent type.</span></span> <span data-ttu-id="2929f-108">Na rozdíl od tříd a záznamů mají struktury sémantiku pass-by-value.</span><span class="sxs-lookup"><span data-stu-id="2929f-108">Unlike classes and records, structures have pass-by-value semantics.</span></span> <span data-ttu-id="2929f-109">To znamená, že jsou užitečné především pro malé agregace dat, ke kterým se často přistupuje a kopírují.</span><span class="sxs-lookup"><span data-stu-id="2929f-109">This means that they are useful primarily for small aggregates of data that are accessed and copied frequently.</span></span>

<span data-ttu-id="2929f-110">V předchozí syntaxi jsou zobrazeny dva formuláře.</span><span class="sxs-lookup"><span data-stu-id="2929f-110">In the previous syntax, two forms are shown.</span></span> <span data-ttu-id="2929f-111">První není zjednodušená syntaxe, ale přesto se často používá, `end` protože při použití klíčových `StructAttribute` slov `struct` a můžete vynechat atribut, který se zobrazí ve druhém formuláři.</span><span class="sxs-lookup"><span data-stu-id="2929f-111">The first is not the lightweight syntax, but it is nevertheless frequently used because, when you use the `struct` and `end` keywords, you can omit the `StructAttribute` attribute, which appears in the second form.</span></span> <span data-ttu-id="2929f-112">Můžete zkrátit `StructAttribute` na jen `Struct`.</span><span class="sxs-lookup"><span data-stu-id="2929f-112">You can abbreviate `StructAttribute` to just `Struct`.</span></span>

<span data-ttu-id="2929f-113">*Typ definice elementů a členů* v předchozí syntaxi představuje deklarace členů a definice.</span><span class="sxs-lookup"><span data-stu-id="2929f-113">The *type-definition-elements-and-members* in the previous syntax represents member declarations and definitions.</span></span> <span data-ttu-id="2929f-114">Struktury mohou mít konstruktory a proměnlivá a neměnná pole a mohou deklarovat implementace členů a rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2929f-114">Structures can have constructors and mutable and immutable fields, and they can declare members and interface implementations.</span></span> <span data-ttu-id="2929f-115">Další informace naleznete v [tématu Členové](./members/index.md).</span><span class="sxs-lookup"><span data-stu-id="2929f-115">For more information, see [Members](./members/index.md).</span></span>

<span data-ttu-id="2929f-116">Struktury se nemohou účastnit `let` dědičnosti, nemohou obsahovat nebo `do` vazby a nemohou rekurzivně obsahovat pole vlastního typu (i když mohou obsahovat referenční buňky, které odkazují na jejich vlastní typ).</span><span class="sxs-lookup"><span data-stu-id="2929f-116">Structures cannot participate in inheritance, cannot contain `let` or `do` bindings, and cannot recursively contain fields of their own type (although they can contain reference cells that reference their own type).</span></span>

<span data-ttu-id="2929f-117">Vzhledem k tomu, že struktury neumožňují `let` vazby, `val` je nutné deklarovat pole ve strukturách pomocí klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="2929f-117">Because structures do not allow `let` bindings, you must declare fields in structures by using the `val` keyword.</span></span> <span data-ttu-id="2929f-118">Klíčové `val` slovo definuje pole a jeho typ, ale neumožňuje inicializaci.</span><span class="sxs-lookup"><span data-stu-id="2929f-118">The `val` keyword defines a field and its type but does not allow initialization.</span></span> <span data-ttu-id="2929f-119">Místo `val` toho jsou deklarace inicializovány na nulu nebo hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="2929f-119">Instead, `val` declarations are initialized to zero or null.</span></span> <span data-ttu-id="2929f-120">Z tohoto důvodu struktury, které mají implicitní konstruktor (to znamená parametry, které jsou `val` uvedeny bezprostředně za název `DefaultValue` struktury v deklaraci) vyžadují, aby deklarace být anotovány s atributem.</span><span class="sxs-lookup"><span data-stu-id="2929f-120">For this reason, structures that have an implicit constructor (that is, parameters that are given immediately after the structure name in the declaration) require that `val` declarations be annotated with the `DefaultValue` attribute.</span></span> <span data-ttu-id="2929f-121">Struktury, které mají definovaný konstruktor stále podporují nulovou inicializaci.</span><span class="sxs-lookup"><span data-stu-id="2929f-121">Structures that have a defined constructor still support zero-initialization.</span></span> <span data-ttu-id="2929f-122">`DefaultValue` Proto atribut je deklarace, že taková nulová hodnota je platná pro pole.</span><span class="sxs-lookup"><span data-stu-id="2929f-122">Therefore, the `DefaultValue` attribute is a declaration that such a zero value is valid for the field.</span></span> <span data-ttu-id="2929f-123">Implicitní konstruktory pro struktury neprovádějí `let` `do` žádné akce, protože a vazby nejsou povoleny na typu, ale implicitní hodnoty parametrů konstruktoru předané jsou k dispozici jako soukromá pole.</span><span class="sxs-lookup"><span data-stu-id="2929f-123">Implicit constructors for structures do not perform any actions because `let` and `do` bindings aren’t allowed on the type, but the implicit constructor parameter values passed in are available as private fields.</span></span>

<span data-ttu-id="2929f-124">Explicitní konstruktory mohou zahrnovat inicializaci hodnot polí.</span><span class="sxs-lookup"><span data-stu-id="2929f-124">Explicit constructors might involve initialization of field values.</span></span> <span data-ttu-id="2929f-125">Pokud máte strukturu, která má explicitní konstruktor, stále podporuje nulovou inicializaci; však nepoužívejte `DefaultValue` atribut na `val` deklarace, protože je v konfliktu s explicitní konstruktor.</span><span class="sxs-lookup"><span data-stu-id="2929f-125">When you have a structure that has an explicit constructor, it still supports zero-initialization; however, you do not use the `DefaultValue` attribute on the `val` declarations because it conflicts with the explicit constructor.</span></span> <span data-ttu-id="2929f-126">Další informace `val` o deklaracích naleznete [v `val` tématu Explicitní pole: Klíčové slovo](./members/explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="2929f-126">For more information about `val` declarations, see [Explicit Fields: The `val` Keyword](./members/explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="2929f-127">Atributy a modifikátory usnadnění jsou povoleny na struktury a postupujte podle stejných pravidel jako pro jiné typy.</span><span class="sxs-lookup"><span data-stu-id="2929f-127">Attributes and accessibility modifiers are allowed on structures, and follow the same rules as those for other types.</span></span> <span data-ttu-id="2929f-128">Další informace naleznete v [tématu Atributy](attributes.md) a [řízení přístupu](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="2929f-128">For more information, see [Attributes](attributes.md) and [Access Control](access-control.md).</span></span>

<span data-ttu-id="2929f-129">Následující příklady kódu ilustrují definice struktury.</span><span class="sxs-lookup"><span data-stu-id="2929f-129">The following code examples illustrate structure definitions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="byreflike-structs"></a><span data-ttu-id="2929f-130">ByRefLike struktury</span><span class="sxs-lookup"><span data-stu-id="2929f-130">ByRefLike structs</span></span>

<span data-ttu-id="2929f-131">Můžete definovat vlastní struktury, které mohou `byref`dodržovat -like sémantiku: další informace naleznete v tématu [Byrefs.](byrefs.md)</span><span class="sxs-lookup"><span data-stu-id="2929f-131">You can define your own structs that can adhere to `byref`-like semantics: see [Byrefs](byrefs.md) for more information.</span></span> <span data-ttu-id="2929f-132">To se provádí <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> s atributem:</span><span class="sxs-lookup"><span data-stu-id="2929f-132">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="2929f-133">`IsByRefLike`neznamená `Struct`.</span><span class="sxs-lookup"><span data-stu-id="2929f-133">`IsByRefLike` does not imply `Struct`.</span></span> <span data-ttu-id="2929f-134">Oba musí být přítomen na typu.</span><span class="sxs-lookup"><span data-stu-id="2929f-134">Both must be present on the type.</span></span>

<span data-ttu-id="2929f-135">Struktura`byref`"-like" v F# je typ hodnoty vázaný na zásobník.</span><span class="sxs-lookup"><span data-stu-id="2929f-135">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="2929f-136">Nikdy přidělena na spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="2929f-136">It is never allocated on the managed heap.</span></span> <span data-ttu-id="2929f-137">-like `byref`struct je užitečné pro vysoce výkonné programování, protože je vynuceno se sadou silných kontrol o životnosti a bez zachycení.</span><span class="sxs-lookup"><span data-stu-id="2929f-137">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="2929f-138">Pravidla jsou:</span><span class="sxs-lookup"><span data-stu-id="2929f-138">The rules are:</span></span>

- <span data-ttu-id="2929f-139">Mohou být použity jako parametry funkce, parametry metody, lokální proměnné, výnosy metod.</span><span class="sxs-lookup"><span data-stu-id="2929f-139">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
- <span data-ttu-id="2929f-140">Nemohou být statické nebo instance členy třídy nebo normální struktury.</span><span class="sxs-lookup"><span data-stu-id="2929f-140">They cannot be static or instance members of a class or normal struct.</span></span>
- <span data-ttu-id="2929f-141">Nemohou být zachyceny žádnou`async` uzavírací konstrukcí (metodami nebo výrazy lambda).</span><span class="sxs-lookup"><span data-stu-id="2929f-141">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
- <span data-ttu-id="2929f-142">Nelze je použít jako obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="2929f-142">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="2929f-143">Ačkoli tato pravidla velmi silně omezují použití, činí tak, aby splnila slib vysoce výkonné výpočetní techniky bezpečným způsobem.</span><span class="sxs-lookup"><span data-stu-id="2929f-143">Although these rules very strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="readonly-structs"></a><span data-ttu-id="2929f-144">Struktury pouze pro čtení</span><span class="sxs-lookup"><span data-stu-id="2929f-144">ReadOnly structs</span></span>

<span data-ttu-id="2929f-145">Struktury můžete oznamovat atributem. <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute></span><span class="sxs-lookup"><span data-stu-id="2929f-145">You can annotate structs with the <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> attribute.</span></span> <span data-ttu-id="2929f-146">Například:</span><span class="sxs-lookup"><span data-stu-id="2929f-146">For example:</span></span>

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="2929f-147">`IsReadOnly`neznamená `Struct`.</span><span class="sxs-lookup"><span data-stu-id="2929f-147">`IsReadOnly` does not imply `Struct`.</span></span> <span data-ttu-id="2929f-148">Chcete-li mít `IsReadOnly` strukturu, musíte přidat obě.</span><span class="sxs-lookup"><span data-stu-id="2929f-148">You must add both to have an `IsReadOnly` struct.</span></span>

<span data-ttu-id="2929f-149">Použití tohoto atributu vydává metadata umožňuje F# a `inref<'T>` C# vědět zacházet jako a `in ref`, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="2929f-149">Use of this attribute emits metadata letting F# and C# know to treat it as `inref<'T>` and `in ref`, respectively.</span></span>

<span data-ttu-id="2929f-150">Definování proměnlivé hodnoty uvnitř struktury jen pro čtení způsobí chybu.</span><span class="sxs-lookup"><span data-stu-id="2929f-150">Defining a mutable value inside of a readonly struct produces an error.</span></span>

## <a name="struct-records-and-discriminated-unions"></a><span data-ttu-id="2929f-151">Strukturovat záznamy a diskriminované odbory</span><span class="sxs-lookup"><span data-stu-id="2929f-151">Struct Records and Discriminated Unions</span></span>

<span data-ttu-id="2929f-152">[Záznamy](records.md) a [discriminated sjednocení](discriminated-unions.md) můžete reprezentovat jako `[<Struct>]` struktury s atributem.</span><span class="sxs-lookup"><span data-stu-id="2929f-152">You can represent [Records](records.md) and [Discriminated Unions](discriminated-unions.md) as structs with the `[<Struct>]` attribute.</span></span>  <span data-ttu-id="2929f-153">Další informace najdete v jednotlivých článku.</span><span class="sxs-lookup"><span data-stu-id="2929f-153">See each article to learn more.</span></span>

## <a name="see-also"></a><span data-ttu-id="2929f-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="2929f-154">See also</span></span>

- [<span data-ttu-id="2929f-155">Referenční příručka jazyka F#</span><span class="sxs-lookup"><span data-stu-id="2929f-155">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="2929f-156">Třídy</span><span class="sxs-lookup"><span data-stu-id="2929f-156">Classes</span></span>](classes.md)
- [<span data-ttu-id="2929f-157">Záznamy</span><span class="sxs-lookup"><span data-stu-id="2929f-157">Records</span></span>](records.md)
- [<span data-ttu-id="2929f-158">Členové</span><span class="sxs-lookup"><span data-stu-id="2929f-158">Members</span></span>](./members/index.md)
