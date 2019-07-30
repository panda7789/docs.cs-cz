---
title: Struktury
description: Přečtěte si F# o struktuře, je typ kompaktního objektu často efektivnější než třída pro typy s malým množstvím dat a jednoduchým chováním.
ms.date: 05/16/2016
ms.openlocfilehash: e638b450fe43e0993c9980cade246c3f26d25e2d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630770"
---
# <a name="structures"></a><span data-ttu-id="71a49-103">Struktury</span><span class="sxs-lookup"><span data-stu-id="71a49-103">Structures</span></span>

<span data-ttu-id="71a49-104">*Struktura* je typ kompaktního objektu, který může být efektivnější než třída pro typy, které mají malé množství dat a jednoduché chování.</span><span class="sxs-lookup"><span data-stu-id="71a49-104">A *structure* is a compact object type that can be more efficient than a class for types that have a small amount of data and simple behavior.</span></span>

## <a name="syntax"></a><span data-ttu-id="71a49-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71a49-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="71a49-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="71a49-106">Remarks</span></span>

<span data-ttu-id="71a49-107">Struktury jsou *typy hodnot*, což znamená, že jsou uloženy přímo v zásobníku nebo, když se používají jako pole nebo prvky pole, vložené v nadřazeném typu.</span><span class="sxs-lookup"><span data-stu-id="71a49-107">Structures are *value types*, which means that they are stored directly on the stack or, when they are used as fields or array elements, inline in the parent type.</span></span> <span data-ttu-id="71a49-108">Na rozdíl od tříd a záznamů mají struktury sémantiku předávaných hodnot.</span><span class="sxs-lookup"><span data-stu-id="71a49-108">Unlike classes and records, structures have pass-by-value semantics.</span></span> <span data-ttu-id="71a49-109">To znamená, že jsou vhodné hlavně pro malé agregované údaje, ke kterým se často používá a kopírují.</span><span class="sxs-lookup"><span data-stu-id="71a49-109">This means that they are useful primarily for small aggregates of data that are accessed and copied frequently.</span></span>

<span data-ttu-id="71a49-110">V předchozí syntaxi jsou zobrazeny dva formuláře.</span><span class="sxs-lookup"><span data-stu-id="71a49-110">In the previous syntax, two forms are shown.</span></span> <span data-ttu-id="71a49-111">První není prostá syntaxe, ale je však často používána, protože při použití `struct` klíčových slov a `end` můžete vynechat `StructAttribute` atribut, který se zobrazí ve druhém formuláři.</span><span class="sxs-lookup"><span data-stu-id="71a49-111">The first is not the lightweight syntax, but it is nevertheless frequently used because, when you use the `struct` and `end` keywords, you can omit the `StructAttribute` attribute, which appears in the second form.</span></span> <span data-ttu-id="71a49-112">Můžete zkrátit `StructAttribute` jenom `Struct`na.</span><span class="sxs-lookup"><span data-stu-id="71a49-112">You can abbreviate `StructAttribute` to just `Struct`.</span></span>

<span data-ttu-id="71a49-113">*Prvky Type-Definition-a-Members* v předchozí syntaxi představují deklarace členů a definice.</span><span class="sxs-lookup"><span data-stu-id="71a49-113">The *type-definition-elements-and-members* in the previous syntax represents member declarations and definitions.</span></span> <span data-ttu-id="71a49-114">Struktury můžou mít konstruktory a proměnlivé a neměnné pole a můžou deklarovat implementace členů a rozhraní.</span><span class="sxs-lookup"><span data-stu-id="71a49-114">Structures can have constructors and mutable and immutable fields, and they can declare members and interface implementations.</span></span> <span data-ttu-id="71a49-115">Další informace naleznete v tématu [Členové](./members/index.md).</span><span class="sxs-lookup"><span data-stu-id="71a49-115">For more information, see [Members](./members/index.md).</span></span>

<span data-ttu-id="71a49-116">Struktury se nemůžou účastnit dědičnosti, `let` nemůžou obsahovat ani `do` vazby a nemůžou rekurzivně obsahovat pole vlastního typu (i když můžou obsahovat referenční buňky, které odkazují na jejich vlastní typ).</span><span class="sxs-lookup"><span data-stu-id="71a49-116">Structures cannot participate in inheritance, cannot contain `let` or `do` bindings, and cannot recursively contain fields of their own type (although they can contain reference cells that reference their own type).</span></span>

<span data-ttu-id="71a49-117">Vzhledem k `let` `val` tomu, že struktury neumožňují vazby, je nutné deklarovat pole ve strukturách pomocí klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="71a49-117">Because structures do not allow `let` bindings, you must declare fields in structures by using the `val` keyword.</span></span> <span data-ttu-id="71a49-118">`val` Klíčové slovo definuje pole a jeho typ, ale nepovoluje inicializaci.</span><span class="sxs-lookup"><span data-stu-id="71a49-118">The `val` keyword defines a field and its type but does not allow initialization.</span></span> <span data-ttu-id="71a49-119">Místo toho jsou deklarace inicializovány na hodnotu nula nebo null. `val`</span><span class="sxs-lookup"><span data-stu-id="71a49-119">Instead, `val` declarations are initialized to zero or null.</span></span> <span data-ttu-id="71a49-120">Z tohoto důvodu vyžadují struktury, které mají implicitní konstruktor (tj. parametry, které jsou uvedeny ihned po názvu struktury v deklaraci), vyžaduje, `val` aby deklarace byly opatřeny `DefaultValue` atributem.</span><span class="sxs-lookup"><span data-stu-id="71a49-120">For this reason, structures that have an implicit constructor (that is, parameters that are given immediately after the structure name in the declaration) require that `val` declarations be annotated with the `DefaultValue` attribute.</span></span> <span data-ttu-id="71a49-121">Struktury, které mají definovaný konstruktor, stále podporují nulovou inicializaci.</span><span class="sxs-lookup"><span data-stu-id="71a49-121">Structures that have a defined constructor still support zero-initialization.</span></span> <span data-ttu-id="71a49-122">Proto je `DefaultValue` atributem deklarace, že tato nulová hodnota je pro pole platná.</span><span class="sxs-lookup"><span data-stu-id="71a49-122">Therefore, the `DefaultValue` attribute is a declaration that such a zero value is valid for the field.</span></span> <span data-ttu-id="71a49-123">Implicitní konstruktory pro struktury neprovádí žádné akce, protože `let` a `do` pro daný typ nejsou vazby povoleny, ale hodnoty parametrů implicitního konstruktoru předané jsou k dispozici jako soukromá pole.</span><span class="sxs-lookup"><span data-stu-id="71a49-123">Implicit constructors for structures do not perform any actions because `let` and `do` bindings aren’t allowed on the type, but the implicit constructor parameter values passed in are available as private fields.</span></span>

<span data-ttu-id="71a49-124">Explicitní konstruktory mohou zahrnovat inicializaci hodnot polí.</span><span class="sxs-lookup"><span data-stu-id="71a49-124">Explicit constructors might involve initialization of field values.</span></span> <span data-ttu-id="71a49-125">Pokud máte strukturu, která má explicitní konstruktor, stále podporuje nulovou inicializaci; Nepoužívejte `DefaultValue` však atribut `val` pro deklarace, protože je v konfliktu s explicitním konstruktorem.</span><span class="sxs-lookup"><span data-stu-id="71a49-125">When you have a structure that has an explicit constructor, it still supports zero-initialization; however, you do not use the `DefaultValue` attribute on the `val` declarations because it conflicts with the explicit constructor.</span></span> <span data-ttu-id="71a49-126">Další informace o `val` deklaracích naleznete v [tématu explicitní pole: `val` Klíčové slovo](./members/explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="71a49-126">For more information about `val` declarations, see [Explicit Fields: The `val` Keyword](./members/explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="71a49-127">Atributy a Modifikátory dostupnosti jsou povoleny ve strukturách a používají stejná pravidla jako pro jiné typy.</span><span class="sxs-lookup"><span data-stu-id="71a49-127">Attributes and accessibility modifiers are allowed on structures, and follow the same rules as those for other types.</span></span> <span data-ttu-id="71a49-128">Další informace naleznete v tématu [atributy](attributes.md) a [Access Control](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="71a49-128">For more information, see [Attributes](attributes.md) and [Access Control](access-control.md).</span></span>

<span data-ttu-id="71a49-129">Následující příklady kódu ilustrují definice struktury.</span><span class="sxs-lookup"><span data-stu-id="71a49-129">The following code examples illustrate structure definitions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="byreflike-structs"></a><span data-ttu-id="71a49-130">Struktury ByRefLike</span><span class="sxs-lookup"><span data-stu-id="71a49-130">ByRefLike structs</span></span>

<span data-ttu-id="71a49-131">Můžete definovat vlastní struktury, které mohou splňovat `byref`sémantické sémantiky: Další informace naleznete v tématu [byrefs](byrefs.md) .</span><span class="sxs-lookup"><span data-stu-id="71a49-131">You can define your own structs that can adhere to `byref`-like semantics: see [Byrefs](byrefs.md) for more information.</span></span> <span data-ttu-id="71a49-132">To se provádí s <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> atributem:</span><span class="sxs-lookup"><span data-stu-id="71a49-132">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="71a49-133">`IsByRefLike``Struct`neznamená.</span><span class="sxs-lookup"><span data-stu-id="71a49-133">`IsByRefLike` does not imply `Struct`.</span></span> <span data-ttu-id="71a49-134">Oba typy musí být k dispozici na typu.</span><span class="sxs-lookup"><span data-stu-id="71a49-134">Both must be present on the type.</span></span>

<span data-ttu-id="71a49-135">Struktura "`byref`-like" v F# je typ hodnoty vázaný na zásobník.</span><span class="sxs-lookup"><span data-stu-id="71a49-135">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="71a49-136">Nikdy se nepřiřazuje na spravovanou haldu.</span><span class="sxs-lookup"><span data-stu-id="71a49-136">It is never allocated on the managed heap.</span></span> <span data-ttu-id="71a49-137">`byref`Struktura podobná struktuře je užitečná pro vysoce výkonné programování, protože je vynutila sadou silných kontrol životního cyklu životnosti a nezachycení.</span><span class="sxs-lookup"><span data-stu-id="71a49-137">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="71a49-138">Pravidla jsou:</span><span class="sxs-lookup"><span data-stu-id="71a49-138">The rules are:</span></span>

* <span data-ttu-id="71a49-139">Mohou být použity jako parametry funkce, parametry metody, místní proměnné, metoda vrátí.</span><span class="sxs-lookup"><span data-stu-id="71a49-139">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
* <span data-ttu-id="71a49-140">Nemohou být statické nebo členy instance třídy nebo normální struktury.</span><span class="sxs-lookup"><span data-stu-id="71a49-140">They cannot be static or instance members of a class or normal struct.</span></span>
* <span data-ttu-id="71a49-141">Nemohou být zachyceny žádnou uzavírací konstrukcí (`async` metody nebo výrazy lambda).</span><span class="sxs-lookup"><span data-stu-id="71a49-141">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
* <span data-ttu-id="71a49-142">Nelze je použít jako obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="71a49-142">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="71a49-143">I když tato pravidla velmi silně omezují využití, jejich účelem je plnit vysoce výkonné výpočetní prostředí bezpečným způsobem.</span><span class="sxs-lookup"><span data-stu-id="71a49-143">Although these rules very strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="readonly-structs"></a><span data-ttu-id="71a49-144">Struktury jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="71a49-144">ReadOnly structs</span></span>

<span data-ttu-id="71a49-145">Pomocí <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> atributu můžete přidávat poznámky k strukturám.</span><span class="sxs-lookup"><span data-stu-id="71a49-145">You can annotate structs with the <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> attribute.</span></span> <span data-ttu-id="71a49-146">Příklad:</span><span class="sxs-lookup"><span data-stu-id="71a49-146">For example:</span></span>

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="71a49-147">`IsReadOnly``Struct`neznamená.</span><span class="sxs-lookup"><span data-stu-id="71a49-147">`IsReadOnly` does not imply `Struct`.</span></span> <span data-ttu-id="71a49-148">Aby bylo `IsReadOnly` možné vytvořit strukturu, musíte přidat obojí.</span><span class="sxs-lookup"><span data-stu-id="71a49-148">You must add both to have an `IsReadOnly` struct.</span></span>

<span data-ttu-id="71a49-149">Použití tohoto atributu emituje metadata, která F# zasílají a C# vědí, že `inref<'T>` se `in ref`považují za a v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="71a49-149">Use of this attribute emits metadata letting F# and C# know to treat it as `inref<'T>` and `in ref`, respectively.</span></span>

<span data-ttu-id="71a49-150">Definování proměnlivé hodnoty v rámci struktury jen pro čtení vyvolá chybu.</span><span class="sxs-lookup"><span data-stu-id="71a49-150">Defining a mutable value inside of a readonly struct produces an error.</span></span>

## <a name="struct-records-and-discriminated-unions"></a><span data-ttu-id="71a49-151">Záznamy struktury a rozlišené sjednocení</span><span class="sxs-lookup"><span data-stu-id="71a49-151">Struct Records and Discriminated Unions</span></span>

<span data-ttu-id="71a49-152">Můžete reprezentovat [záznamy](records.md) a [rozlišené sjednocení](discriminated-unions.md) jako struktury s `[<Struct>]` atributem.</span><span class="sxs-lookup"><span data-stu-id="71a49-152">You can represent [Records](records.md) and [Discriminated Unions](discriminated-unions.md) as structs with the `[<Struct>]` attribute.</span></span>  <span data-ttu-id="71a49-153">Další informace najdete v každém článku.</span><span class="sxs-lookup"><span data-stu-id="71a49-153">See each article to learn more.</span></span>

## <a name="see-also"></a><span data-ttu-id="71a49-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="71a49-154">See also</span></span>

- [<span data-ttu-id="71a49-155">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="71a49-155">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="71a49-156">Třídy</span><span class="sxs-lookup"><span data-stu-id="71a49-156">Classes</span></span>](classes.md)
- [<span data-ttu-id="71a49-157">Záznamy</span><span class="sxs-lookup"><span data-stu-id="71a49-157">Records</span></span>](records.md)
- [<span data-ttu-id="71a49-158">Členové</span><span class="sxs-lookup"><span data-stu-id="71a49-158">Members</span></span>](./members/index.md)
