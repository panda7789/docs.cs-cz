---
title: Struktury (F#)
description: 'Další informace o F # strukturu, typ compact objektu, který je často efektivnější než třída pro typy s malé množství dat a jednoduché chování.'
ms.date: 05/16/2016
ms.openlocfilehash: 57c4148aec1d6a19237d74aa99824ef475c3632e
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172461"
---
# <a name="structures"></a><span data-ttu-id="3ba51-103">Struktury</span><span class="sxs-lookup"><span data-stu-id="3ba51-103">Structures</span></span>

<span data-ttu-id="3ba51-104">A *struktura* je typu compact objektu, který může být efektivnější než třída pro typy, které mají malé množství dat a jednoduché chování.</span><span class="sxs-lookup"><span data-stu-id="3ba51-104">A *structure* is a compact object type that can be more efficient than a class for types that have a small amount of data and simple behavior.</span></span>

## <a name="syntax"></a><span data-ttu-id="3ba51-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ba51-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="3ba51-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3ba51-106">Remarks</span></span>
<span data-ttu-id="3ba51-107">Struktury jsou *typů hodnot*, což znamená, že jsou uložené přímo v zásobníku nebo, pokud se používá jako pole nebo elementy pole, vložený v nadřazeném typu.</span><span class="sxs-lookup"><span data-stu-id="3ba51-107">Structures are *value types*, which means that they are stored directly on the stack or, when they are used as fields or array elements, inline in the parent type.</span></span> <span data-ttu-id="3ba51-108">Na rozdíl od třídy a záznamy mají struktury sémantiku průchodu hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3ba51-108">Unlike classes and records, structures have pass-by-value semantics.</span></span> <span data-ttu-id="3ba51-109">To znamená, že jsou užitečné především pro malé agreguje data, která jsou přístup a často zkopírovat.</span><span class="sxs-lookup"><span data-stu-id="3ba51-109">This means that they are useful primarily for small aggregates of data that are accessed and copied frequently.</span></span>

<span data-ttu-id="3ba51-110">V předchozích syntaxi jsou uvedeny dva formuláře.</span><span class="sxs-lookup"><span data-stu-id="3ba51-110">In the previous syntax, two forms are shown.</span></span> <span data-ttu-id="3ba51-111">První není prostá syntaxe, ale přesto často se používá proto, že při použití `struct` a `end` klíčová slova, můžete vynechat `StructAttribute` atribut, který se zobrazí v druhý formulář.</span><span class="sxs-lookup"><span data-stu-id="3ba51-111">The first is not the lightweight syntax, but it is nevertheless frequently used because, when you use the `struct` and `end` keywords, you can omit the `StructAttribute` attribute, which appears in the second form.</span></span> <span data-ttu-id="3ba51-112">Parametr lze zapsat `StructAttribute` těsně `Struct`.</span><span class="sxs-lookup"><span data-stu-id="3ba51-112">You can abbreviate `StructAttribute` to just `Struct`.</span></span>

<span data-ttu-id="3ba51-113">*– Definice – elementy a členy typu* v předchozí syntaxi představuje člen deklarace a definice.</span><span class="sxs-lookup"><span data-stu-id="3ba51-113">The *type-definition-elements-and-members* in the previous syntax represents member declarations and definitions.</span></span> <span data-ttu-id="3ba51-114">Struktury může mít konstruktory a měnitelný a neměnné pole a jejich můžou deklarovat členy a implementace rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3ba51-114">Structures can have constructors and mutable and immutable fields, and they can declare members and interface implementations.</span></span> <span data-ttu-id="3ba51-115">Další informace najdete v tématu [členy](members/index.md).</span><span class="sxs-lookup"><span data-stu-id="3ba51-115">For more information, see [Members](members/index.md).</span></span>

<span data-ttu-id="3ba51-116">Struktury, nemůže se podílet na dědičnosti, nemůže obsahovat `let` nebo `do` vazby, a nemůže rekurzivně obsahovat pole vlastní typu (i když mohou obsahovat referenční buňky, které odkazují na vlastní typ).</span><span class="sxs-lookup"><span data-stu-id="3ba51-116">Structures cannot participate in inheritance, cannot contain `let` or `do` bindings, and cannot recursively contain fields of their own type (although they can contain reference cells that reference their own type).</span></span>

<span data-ttu-id="3ba51-117">Struktury není dovoleno `let` vazby, je potřeba deklarovat pole v struktury pomocí `val` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="3ba51-117">Because structures do not allow `let` bindings, you must declare fields in structures by using the `val` keyword.</span></span> <span data-ttu-id="3ba51-118">`val` – Klíčové slovo definuje pole a její typ, ale neumožňuje inicializace.</span><span class="sxs-lookup"><span data-stu-id="3ba51-118">The `val` keyword defines a field and its type but does not allow initialization.</span></span> <span data-ttu-id="3ba51-119">Místo toho `val` jsou deklarace inicializovaného na nulu nebo má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="3ba51-119">Instead, `val` declarations are initialized to zero or null.</span></span> <span data-ttu-id="3ba51-120">Z tohoto důvodu struktury, které mají implicitní konstruktor (to znamená, parametry, které jsou uvedeny ihned po název struktury v deklaraci) vyžadují, aby `val` být opatřena poznámkou deklarace `DefaultValue` atribut.</span><span class="sxs-lookup"><span data-stu-id="3ba51-120">For this reason, structures that have an implicit constructor (that is, parameters that are given immediately after the structure name in the declaration) require that `val` declarations be annotated with the `DefaultValue` attribute.</span></span> <span data-ttu-id="3ba51-121">Struktury, které mají definovanou konstruktor ještě podporují inicializace nula.</span><span class="sxs-lookup"><span data-stu-id="3ba51-121">Structures that have a defined constructor still support zero-initialization.</span></span> <span data-ttu-id="3ba51-122">Proto `DefaultValue` atribut je deklaraci, že takové nulová hodnota je platný pro pole.</span><span class="sxs-lookup"><span data-stu-id="3ba51-122">Therefore, the `DefaultValue` attribute is a declaration that such a zero value is valid for the field.</span></span> <span data-ttu-id="3ba51-123">Implicitní konstruktory pro struktury neprovádět všechny akce, protože `let` a `do` nejsou povoleny vazby na typ, ale jsou k dispozici jako privátním polím předané hodnoty parametru implicitní konstruktor.</span><span class="sxs-lookup"><span data-stu-id="3ba51-123">Implicit constructors for structures do not perform any actions because `let` and `do` bindings aren’t allowed on the type, but the implicit constructor parameter values passed in are available as private fields.</span></span>

<span data-ttu-id="3ba51-124">Explicitní konstruktory mohou zahrnovat inicializace hodnot polí.</span><span class="sxs-lookup"><span data-stu-id="3ba51-124">Explicit constructors might involve initialization of field values.</span></span> <span data-ttu-id="3ba51-125">Až budete mít struktuře, která má explicitní konstruktor, stále podporuje nula inicializace; ale nepoužijete `DefaultValue` atributu u `val` deklarace vzhledem k tomu, že je v konfliktu s explicitní konstruktor.</span><span class="sxs-lookup"><span data-stu-id="3ba51-125">When you have a structure that has an explicit constructor, it still supports zero-initialization; however, you do not use the `DefaultValue` attribute on the `val` declarations because it conflicts with the explicit constructor.</span></span> <span data-ttu-id="3ba51-126">Další informace o `val` deklarace, najdete v části [explicitní pole: `val` – klíčové slovo](members/explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="3ba51-126">For more information about `val` declarations, see [Explicit Fields: The `val` Keyword](members/explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="3ba51-127">Atributy a modifikátory dostupnosti jsou povoleny na struktury a postupujte podle stejných pravidel jako u jiných typů.</span><span class="sxs-lookup"><span data-stu-id="3ba51-127">Attributes and accessibility modifiers are allowed on structures, and follow the same rules as those for other types.</span></span> <span data-ttu-id="3ba51-128">Další informace najdete v tématu [atributy](attributes.md) a [řízení přístupu](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="3ba51-128">For more information, see [Attributes](attributes.md) and [Access Control](access-control.md).</span></span>

<span data-ttu-id="3ba51-129">Následující příklady kódu ilustrují definice struktury.</span><span class="sxs-lookup"><span data-stu-id="3ba51-129">The following code examples illustrate structure definitions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="struct-records-and-discriminated-unions"></a><span data-ttu-id="3ba51-130">Struktura záznamů a rozlišovaná sjednocení</span><span class="sxs-lookup"><span data-stu-id="3ba51-130">Struct Records and Discriminated Unions</span></span>

<span data-ttu-id="3ba51-131">Od verze 4.1 F #, může představovat [záznamy](records.md) a [Rozlišované sjednocení](discriminated-unions.md) jako struktury s `[<Struct>]` atribut.</span><span class="sxs-lookup"><span data-stu-id="3ba51-131">Starting with F# 4.1, you can represent [Records](records.md) and [Discriminated Unions](discriminated-unions.md) as structs with the `[<Struct>]` attribute.</span></span>  <span data-ttu-id="3ba51-132">V každé článku Další informace.</span><span class="sxs-lookup"><span data-stu-id="3ba51-132">See each article to learn more.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="3ba51-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="3ba51-133">See Also</span></span>
[<span data-ttu-id="3ba51-134">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="3ba51-134">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="3ba51-135">Třídy</span><span class="sxs-lookup"><span data-stu-id="3ba51-135">Classes</span></span>](classes.md)

[<span data-ttu-id="3ba51-136">Záznamy</span><span class="sxs-lookup"><span data-stu-id="3ba51-136">Records</span></span>](records.md)

[<span data-ttu-id="3ba51-137">Členové</span><span class="sxs-lookup"><span data-stu-id="3ba51-137">Members</span></span>](members/index.md)
