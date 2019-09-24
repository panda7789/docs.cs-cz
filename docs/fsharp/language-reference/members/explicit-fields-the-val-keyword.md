---
title: 'Explicitní pole: Klíčové slovo Val'
description: Přečtěte si F# o klíčovém slově Val, který se používá k deklaraci umístění pro uložení hodnoty v typu třídy nebo struktury bez inicializace typu.
ms.date: 05/16/2016
ms.openlocfilehash: fe339e33dae27ae226022a68dd8247d1ab1994b3
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216479"
---
# <a name="explicit-fields-the-val-keyword"></a><span data-ttu-id="36990-103">Explicitní pole: Klíčové slovo Val</span><span class="sxs-lookup"><span data-stu-id="36990-103">Explicit Fields: The val Keyword</span></span>

<span data-ttu-id="36990-104">`val` Klíčové slovo slouží k deklaraci umístění pro uložení hodnoty v typu třídy nebo struktury, aniž by bylo nutné ji inicializovat.</span><span class="sxs-lookup"><span data-stu-id="36990-104">The `val` keyword is used to declare a location to store a value in a class or structure type, without initializing it.</span></span> <span data-ttu-id="36990-105">Umístění úložiště deklarovaná tímto způsobem se nazývají *explicitní pole*.</span><span class="sxs-lookup"><span data-stu-id="36990-105">Storage locations declared in this manner are called *explicit fields*.</span></span> <span data-ttu-id="36990-106">Jiné použití `val` klíčového slova je ve spojení `member` s klíčovým slovem pro deklaraci automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="36990-106">Another use of the `val` keyword is in conjunction with the `member` keyword to declare an auto-implemented property.</span></span> <span data-ttu-id="36990-107">Další informace o automaticky implementovaných vlastnostech naleznete v tématu [Properties](properties.md).</span><span class="sxs-lookup"><span data-stu-id="36990-107">For more information on auto-implemented properties, see [Properties](properties.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="36990-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36990-108">Syntax</span></span>

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a><span data-ttu-id="36990-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="36990-109">Remarks</span></span>

<span data-ttu-id="36990-110">Obvyklým způsobem, jak definovat pole v typu třídy nebo struktury, je použití `let` vazby.</span><span class="sxs-lookup"><span data-stu-id="36990-110">The usual way to define fields in a class or structure type is to use a `let` binding.</span></span> <span data-ttu-id="36990-111">`let` Vazby je však nutné inicializovat jako součást konstruktoru třídy, který není vždy možný, nutný nebo žádoucí.</span><span class="sxs-lookup"><span data-stu-id="36990-111">However, `let` bindings must be initialized as part of the class constructor, which is not always possible, necessary, or desirable.</span></span> <span data-ttu-id="36990-112">`val` Klíčové slovo lze použít, pokud chcete pole, které není inicializováno.</span><span class="sxs-lookup"><span data-stu-id="36990-112">You can use the `val` keyword when you want a field that is uninitialized.</span></span>

<span data-ttu-id="36990-113">Explicitní pole mohou být statická nebo nestatická.</span><span class="sxs-lookup"><span data-stu-id="36990-113">Explicit fields can be static or non-static.</span></span> <span data-ttu-id="36990-114">*Modifikátor přístupu* může být `public`, `private`, nebo `internal`.</span><span class="sxs-lookup"><span data-stu-id="36990-114">The *access-modifier* can be `public`, `private`, or `internal`.</span></span> <span data-ttu-id="36990-115">Ve výchozím nastavení jsou explicitní pole veřejná.</span><span class="sxs-lookup"><span data-stu-id="36990-115">By default, explicit fields are public.</span></span> <span data-ttu-id="36990-116">To se liší od `let` vazeb ve třídách, které jsou vždy soukromé.</span><span class="sxs-lookup"><span data-stu-id="36990-116">This differs from `let` bindings in classes, which are always private.</span></span>

<span data-ttu-id="36990-117">Atribut [DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) je vyžadován v explicitních polích typu třídy, které mají primární konstruktor.</span><span class="sxs-lookup"><span data-stu-id="36990-117">The [DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) attribute is required on explicit fields in class types that have a primary constructor.</span></span> <span data-ttu-id="36990-118">Tento atribut určuje, že pole je inicializováno na nulu.</span><span class="sxs-lookup"><span data-stu-id="36990-118">This attribute specifies that the field is initialized to zero.</span></span> <span data-ttu-id="36990-119">Typ pole musí podporovat nulovou inicializaci.</span><span class="sxs-lookup"><span data-stu-id="36990-119">The type of the field must support zero-initialization.</span></span> <span data-ttu-id="36990-120">Typ podporuje nulovou inicializaci, pokud se jedná o jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="36990-120">A type supports zero-initialization if it is one of the following:</span></span>

- <span data-ttu-id="36990-121">Primitivní typ, který má nulovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="36990-121">A primitive type that has a zero value.</span></span>

- <span data-ttu-id="36990-122">Typ, který podporuje hodnotu null buď jako normální hodnotu, jako neobvyklou hodnotu, nebo jako reprezentace hodnoty.</span><span class="sxs-lookup"><span data-stu-id="36990-122">A type that supports a null value, either as a normal value, as an abnormal value, or as a representation of a value.</span></span> <span data-ttu-id="36990-123">To zahrnuje třídy, řazené kolekce členů, záznamy, funkce, rozhraní, typy odkazů .NET `unit` , typ a rozlišené typy sjednocení.</span><span class="sxs-lookup"><span data-stu-id="36990-123">This includes classes, tuples, records, functions, interfaces, .NET reference types, the `unit` type, and discriminated union types.</span></span>

- <span data-ttu-id="36990-124">Typ hodnoty .NET.</span><span class="sxs-lookup"><span data-stu-id="36990-124">A .NET value type.</span></span>

- <span data-ttu-id="36990-125">Struktura, jejíž pole všechny podporují výchozí nulovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="36990-125">A structure whose fields all support a default zero value.</span></span>

<span data-ttu-id="36990-126">Například neměnné pole `someField` s názvem má v kompilované reprezentaci .NET s názvem `someField@`pole zálohování a přístup k uložené hodnotě pomocí vlastnosti s názvem `someField`.</span><span class="sxs-lookup"><span data-stu-id="36990-126">For example, an immutable field called `someField` has a backing field in the .NET compiled representation with the name `someField@`, and you access the stored value using a property named `someField`.</span></span>

<span data-ttu-id="36990-127">V případě proměnlivého pole je kompilovaná reprezentace rozhraní .NET pole rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="36990-127">For a mutable field, the .NET compiled representation is a .NET field.</span></span>

>[!WARNING]
><span data-ttu-id="36990-128">Obor názvů `System.ComponentModel` .NET Framework obsahuje atribut, který má stejný název.</span><span class="sxs-lookup"><span data-stu-id="36990-128">The .NET Framework namespace `System.ComponentModel` contains an attribute that has the same name.</span></span> <span data-ttu-id="36990-129">Informace o tomto atributu naleznete v tématu `System.ComponentModel.DefaultValueAttribute`.</span><span class="sxs-lookup"><span data-stu-id="36990-129">For information about this attribute, see `System.ComponentModel.DefaultValueAttribute`.</span></span>

<span data-ttu-id="36990-130">Následující kód ukazuje použití explicitních polí a pro porovnání, `let` vazby ve třídě, která má primární konstruktor.</span><span class="sxs-lookup"><span data-stu-id="36990-130">The following code shows the use of explicit fields and, for comparison, a `let` binding in a class that has a primary constructor.</span></span> <span data-ttu-id="36990-131">Všimněte si, `let`že pole `myInt1` svázané je soukromé.</span><span class="sxs-lookup"><span data-stu-id="36990-131">Note that the `let`-bound field `myInt1` is private.</span></span> <span data-ttu-id="36990-132">Při odkazování na `let`pole `myInt1` vázané z členské metody není identifikátor `this` držitele vyžadován.</span><span class="sxs-lookup"><span data-stu-id="36990-132">When the `let`-bound field `myInt1` is referenced from a member method, the self identifier `this` is not required.</span></span> <span data-ttu-id="36990-133">Ale když odkazujete na explicitní pole `myInt2` a `myString`, je požadován identifikátor autotest.</span><span class="sxs-lookup"><span data-stu-id="36990-133">But when you are referencing the explicit fields `myInt2` and `myString`, the self identifier is required.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

<span data-ttu-id="36990-134">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="36990-134">The output is as follows:</span></span>

```console
11 12 abc
30 def
```

<span data-ttu-id="36990-135">Následující kód ukazuje použití explicitních polí ve třídě, která nemá primární konstruktor.</span><span class="sxs-lookup"><span data-stu-id="36990-135">The following code shows the use of explicit fields in a class that does not have a primary constructor.</span></span> <span data-ttu-id="36990-136">V tomto případě `DefaultValue` není atribut vyžadován, ale všechna pole musí být inicializována v konstruktorech, které jsou definovány pro daný typ.</span><span class="sxs-lookup"><span data-stu-id="36990-136">In this case, the `DefaultValue` attribute is not required, but all the fields must be initialized in the constructors that are defined for the type.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

<span data-ttu-id="36990-137">Výstup je `35 22`.</span><span class="sxs-lookup"><span data-stu-id="36990-137">The output is `35 22`.</span></span>

<span data-ttu-id="36990-138">Následující kód ukazuje použití explicitních polí ve struktuře.</span><span class="sxs-lookup"><span data-stu-id="36990-138">The following code shows the use of explicit fields in a structure.</span></span> <span data-ttu-id="36990-139">Vzhledem k tomu, že struktura je hodnotový typ, má automaticky výchozí konstruktor, který nastaví hodnoty jejich polí na nulu.</span><span class="sxs-lookup"><span data-stu-id="36990-139">Because a structure is a value type, it automatically has a default constructor that sets the values of its fields to zero.</span></span> <span data-ttu-id="36990-140">`DefaultValue` Proto atribut není požadován.</span><span class="sxs-lookup"><span data-stu-id="36990-140">Therefore, the `DefaultValue` attribute is not required.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

<span data-ttu-id="36990-141">Výstup je `11 xyz`.</span><span class="sxs-lookup"><span data-stu-id="36990-141">The output is `11 xyz`.</span></span>

<span data-ttu-id="36990-142">Pokud se chystáte inicializovat strukturu s `mutable` poli bez `mutable` klíčového slova, budou vaše přiřazení fungovat na kopii struktury, která se po přiřazení zahodí hned.</span><span class="sxs-lookup"><span data-stu-id="36990-142">**Beware**, if you are going to initialize your structure with `mutable` fields without `mutable` keyword, your assignments will work on a copy of the structure which will be discarded right after assignment.</span></span> <span data-ttu-id="36990-143">Proto se vaše struktura nemění.</span><span class="sxs-lookup"><span data-stu-id="36990-143">Therefore your structure won't change.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6704.fs)]

<span data-ttu-id="36990-144">Explicitní pole nejsou určena pro rutinové použití.</span><span class="sxs-lookup"><span data-stu-id="36990-144">Explicit fields are not intended for routine use.</span></span> <span data-ttu-id="36990-145">Obecně platí, že pokud je to možné, `let` měli byste použít vazbu ve třídě namísto explicitního pole.</span><span class="sxs-lookup"><span data-stu-id="36990-145">In general, when possible you should use a `let` binding in a class instead of an explicit field.</span></span> <span data-ttu-id="36990-146">Explicitní pole jsou užitečná v některých scénářích interoperability, například když potřebujete definovat strukturu, která bude použita v volání metody Invoke do nativního rozhraní API nebo ve scénářích komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="36990-146">Explicit fields are useful in certain interoperability scenarios, such as when you need to define a structure that will be used in a platform invoke call to a native API, or in COM interop scenarios.</span></span> <span data-ttu-id="36990-147">Další informace najdete v tématu věnovaném [externím funkcím](../functions/external-functions.md).</span><span class="sxs-lookup"><span data-stu-id="36990-147">For more information, see [External Functions](../functions/external-functions.md).</span></span> <span data-ttu-id="36990-148">Další situací, kdy může být explicitní pole nutné, je při práci s generátorem F# kódu, který generuje třídy bez primárního konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="36990-148">Another situation in which an explicit field might be necessary is when you are working with an F# code generator which emits classes without a primary constructor.</span></span> <span data-ttu-id="36990-149">Explicitní pole jsou také užitečná pro proměnné vlákn-static nebo podobné konstrukce.</span><span class="sxs-lookup"><span data-stu-id="36990-149">Explicit fields are also useful for thread-static variables or similar constructs.</span></span> <span data-ttu-id="36990-150">Další informace naleznete v tématu `System.ThreadStaticAttribute`.</span><span class="sxs-lookup"><span data-stu-id="36990-150">For more information, see `System.ThreadStaticAttribute`.</span></span>

<span data-ttu-id="36990-151">Když se klíčová slova `member val` zobrazí v definici typu společně, jedná se o definici automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="36990-151">When the keywords `member val` appear together in a type definition, it is a definition of an automatically implemented property.</span></span> <span data-ttu-id="36990-152">Další informace najdete v tématu [vlastnosti](properties.md).</span><span class="sxs-lookup"><span data-stu-id="36990-152">For more information, see [Properties](properties.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="36990-153">Viz také:</span><span class="sxs-lookup"><span data-stu-id="36990-153">See also</span></span>

- [<span data-ttu-id="36990-154">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="36990-154">Properties</span></span>](properties.md)
- [<span data-ttu-id="36990-155">Členové</span><span class="sxs-lookup"><span data-stu-id="36990-155">Members</span></span>](index.md)
- [<span data-ttu-id="36990-156">`let`Vazby ve třídách</span><span class="sxs-lookup"><span data-stu-id="36990-156">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)
