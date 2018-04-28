---
title: 'Explicitní pole: Klíčové slovo val (F#)'
description: "Další informace o F # 'val' – klíčové slovo, které se používá k deklaraci umístění pro uložení hodnotu v typu třídu nebo strukturu nebyl zadán typ."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: dc277680121976c0469b18c77bd84443cd251afb
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="explicit-fields-the-val-keyword"></a><span data-ttu-id="5af65-103">Explicitní pole: Klíčové slovo val</span><span class="sxs-lookup"><span data-stu-id="5af65-103">Explicit Fields: The val Keyword</span></span>

<span data-ttu-id="5af65-104">`val` – Klíčové slovo se používá k deklaraci umístění pro uložení hodnotu v typu třídy nebo struktura bez jeho inicializaci.</span><span class="sxs-lookup"><span data-stu-id="5af65-104">The `val` keyword is used to declare a location to store a value in a class or structure type, without initializing it.</span></span> <span data-ttu-id="5af65-105">Umístění úložiště deklarovaný tímto způsobem se nazývají *explicitní pole*.</span><span class="sxs-lookup"><span data-stu-id="5af65-105">Storage locations declared in this manner are called *explicit fields*.</span></span> <span data-ttu-id="5af65-106">Další používání `val` – klíčové slovo je ve spojení s `member` – klíčové slovo deklarovat ve automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5af65-106">Another use of the `val` keyword is in conjunction with the `member` keyword to declare an auto-implemented property.</span></span> <span data-ttu-id="5af65-107">Další informace o automaticky implementované vlastnosti najdete v tématu [vlastnosti](properties.md).</span><span class="sxs-lookup"><span data-stu-id="5af65-107">For more information on auto-implemented properties, see [Properties](properties.md).</span></span>


## <a name="syntax"></a><span data-ttu-id="5af65-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5af65-108">Syntax</span></span>

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a><span data-ttu-id="5af65-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5af65-109">Remarks</span></span>
<span data-ttu-id="5af65-110">Obvyklým definování polí v typu třídu nebo strukturu, je použít `let` vazby.</span><span class="sxs-lookup"><span data-stu-id="5af65-110">The usual way to define fields in a class or structure type is to use a `let` binding.</span></span> <span data-ttu-id="5af65-111">Ale `let` vazby musí být inicializován jako součást konstruktoru třídy, která není vždy možná, potřebná nebo žádoucí.</span><span class="sxs-lookup"><span data-stu-id="5af65-111">However, `let` bindings must be initialized as part of the class constructor, which is not always possible, necessary, or desirable.</span></span> <span data-ttu-id="5af65-112">Můžete použít `val` – klíčové slovo chcete pole, které není inicializován.</span><span class="sxs-lookup"><span data-stu-id="5af65-112">You can use the `val` keyword when you want a field that is uninitialized.</span></span>

<span data-ttu-id="5af65-113">Explicitní pole můžou být statické nebo nestatické.</span><span class="sxs-lookup"><span data-stu-id="5af65-113">Explicit fields can be static or non-static.</span></span> <span data-ttu-id="5af65-114">*– Modifikátor přístupu* může být `public`, `private`, nebo `internal`.</span><span class="sxs-lookup"><span data-stu-id="5af65-114">The *access-modifier* can be `public`, `private`, or `internal`.</span></span> <span data-ttu-id="5af65-115">Ve výchozím nastavení jsou explicitní pole veřejné.</span><span class="sxs-lookup"><span data-stu-id="5af65-115">By default, explicit fields are public.</span></span> <span data-ttu-id="5af65-116">Tím se liší od `let` vazby do ve třídách, které jsou vždy privátní.</span><span class="sxs-lookup"><span data-stu-id="5af65-116">This differs from `let` bindings in classes, which are always private.</span></span>

<span data-ttu-id="5af65-117">[DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) atribut je požadován u explicitní pole v typy tříd, které mají primární konstruktor.</span><span class="sxs-lookup"><span data-stu-id="5af65-117">The [DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) attribute is required on explicit fields in class types that have a primary constructor.</span></span> <span data-ttu-id="5af65-118">Tento atribut určuje, že pole je inicializováno na nulu.</span><span class="sxs-lookup"><span data-stu-id="5af65-118">This attribute specifies that the field is initialized to zero.</span></span> <span data-ttu-id="5af65-119">Typ pole musí podporovat inicializace nula.</span><span class="sxs-lookup"><span data-stu-id="5af65-119">The type of the field must support zero-initialization.</span></span> <span data-ttu-id="5af65-120">Typ podporuje inicializace nula. Pokud jde o jeden z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="5af65-120">A type supports zero-initialization if it is one of the following:</span></span>

- <span data-ttu-id="5af65-121">Primitivní typ, který má nulovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5af65-121">A primitive type that has a zero value.</span></span>

- <span data-ttu-id="5af65-122">Typ, který podporuje hodnotu null, buď jako hodnotu Normální, jako neobvyklé hodnoty nebo jako reprezentace hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5af65-122">A type that supports a null value, either as a normal value, as an abnormal value, or as a representation of a value.</span></span> <span data-ttu-id="5af65-123">To zahrnuje třídy, řazené kolekce členů, záznamy, funkce, rozhraní, referenční typy .NET, `unit` typ a rozlišovaná sjednocení typů.</span><span class="sxs-lookup"><span data-stu-id="5af65-123">This includes classes, tuples, records, functions, interfaces, .NET reference types, the `unit` type, and discriminated union types.</span></span>

- <span data-ttu-id="5af65-124">Typ hodnoty .NET.</span><span class="sxs-lookup"><span data-stu-id="5af65-124">A .NET value type.</span></span>

- <span data-ttu-id="5af65-125">Struktura, jejichž pole všechny podporují výchozí nulovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5af65-125">A structure whose fields all support a default zero value.</span></span>


<span data-ttu-id="5af65-126">Například neměnné pole s názvem `someField` má základní pole v .NET zkompilovat reprezentace s názvem `someField@`, a získat přístup k hodnotě uložené pomocí vlastnost s názvem `someField`.</span><span class="sxs-lookup"><span data-stu-id="5af65-126">For example, an immutable field called `someField` has a backing field in the .NET compiled representation with the name `someField@`, and you access the stored value using a property named `someField`.</span></span>

<span data-ttu-id="5af65-127">Pro měnitelný pole je reprezentace .NET zkompilovat pole rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="5af65-127">For a mutable field, the .NET compiled representation is a .NET field.</span></span>


>[!WARNING] 
<span data-ttu-id="5af65-128">`Note` Obor názvů rozhraní .NET Framework `System.ComponentModel` obsahuje atribut, který má stejný název.</span><span class="sxs-lookup"><span data-stu-id="5af65-128">`Note` The .NET Framework namespace `System.ComponentModel` contains an attribute that has the same name.</span></span> <span data-ttu-id="5af65-129">Informace o tento atribut najdete v tématu `System.ComponentModel.DefaultValueAttribute`.</span><span class="sxs-lookup"><span data-stu-id="5af65-129">For information about this attribute, see `System.ComponentModel.DefaultValueAttribute`.</span></span>


<span data-ttu-id="5af65-130">Následující kód ukazuje použití explicitní pole a pro porovnání, `let` vazby ve třídy, která má primární konstruktor.</span><span class="sxs-lookup"><span data-stu-id="5af65-130">The following code shows the use of explicit fields and, for comparison, a `let` binding in a class that has a primary constructor.</span></span> <span data-ttu-id="5af65-131">Všimněte si, že `let`-vázané pole `myInt1` je soukromé.</span><span class="sxs-lookup"><span data-stu-id="5af65-131">Note that the `let`-bound field `myInt1` is private.</span></span> <span data-ttu-id="5af65-132">Když `let`-vázané pole `myInt1` se odkazuje z metody člen, vlastní identifikátor `this` se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="5af65-132">When the `let`-bound field `myInt1` is referenced from a member method, the self identifier `this` is not required.</span></span> <span data-ttu-id="5af65-133">Když odkazujete explicitní pole, ale `myInt2` a `myString`, je vyžadován vlastní identifikátor.</span><span class="sxs-lookup"><span data-stu-id="5af65-133">But when you are referencing the explicit fields `myInt2` and `myString`, the self identifier is required.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

<span data-ttu-id="5af65-134">Výstup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="5af65-134">The output is as follows:</span></span>

```
11 12 abc
30 def
```

<span data-ttu-id="5af65-135">Následující kód ukazuje použití explicitní pole ve třídě, která neobsahuje primární konstruktor.</span><span class="sxs-lookup"><span data-stu-id="5af65-135">The following code shows the use of explicit fields in a class that does not have a primary constructor.</span></span> <span data-ttu-id="5af65-136">V takovém případě `DefaultValue` atribut se nevyžaduje, ale v konstruktorech, které jsou definovány pro typ se musí inicializovat všechna pole.</span><span class="sxs-lookup"><span data-stu-id="5af65-136">In this case, the `DefaultValue` attribute is not required, but all the fields must be initialized in the constructors that are defined for the type.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

<span data-ttu-id="5af65-137">Výstupem je `35 22`.</span><span class="sxs-lookup"><span data-stu-id="5af65-137">The output is `35 22`.</span></span>

<span data-ttu-id="5af65-138">Následující kód ukazuje použití explicitní pole ve struktuře.</span><span class="sxs-lookup"><span data-stu-id="5af65-138">The following code shows the use of explicit fields in a structure.</span></span> <span data-ttu-id="5af65-139">Vzhledem k tomu, že typ hodnoty strukturu se má automaticky výchozí konstruktor, která nastavuje hodnoty jeho polí na nulu.</span><span class="sxs-lookup"><span data-stu-id="5af65-139">Because a structure is a value type, it automatically has a default constructor that sets the values of its fields to zero.</span></span> <span data-ttu-id="5af65-140">Proto `DefaultValue` atribut se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="5af65-140">Therefore, the `DefaultValue` attribute is not required.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

<span data-ttu-id="5af65-141">Výstupem je `11 xyz`.</span><span class="sxs-lookup"><span data-stu-id="5af65-141">The output is `11 xyz`.</span></span>

<span data-ttu-id="5af65-142">Explicitní pole nejsou určeny k použití rutiny.</span><span class="sxs-lookup"><span data-stu-id="5af65-142">Explicit fields are not intended for routine use.</span></span> <span data-ttu-id="5af65-143">Obecně platí, pokud je to možné byste měli používat `let` vazby v třídě místo explicitní pole.</span><span class="sxs-lookup"><span data-stu-id="5af65-143">In general, when possible you should use a `let` binding in a class instead of an explicit field.</span></span> <span data-ttu-id="5af65-144">Explicitní pole jsou užitečné v některých scénářích vzájemná funkční spolupráce, například když je třeba definovat strukturu, která bude použita v platformu vyvolání volání do nativního rozhraní API, nebo ve scénářích zprostředkovatele komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="5af65-144">Explicit fields are useful in certain interoperability scenarios, such as when you need to define a structure that will be used in a platform invoke call to a native API, or in COM interop scenarios.</span></span> <span data-ttu-id="5af65-145">Další informace najdete v tématu [externí funkce](../functions/external-functions.md).</span><span class="sxs-lookup"><span data-stu-id="5af65-145">For more information, see [External Functions](../functions/external-functions.md).</span></span> <span data-ttu-id="5af65-146">Další situace, ve kterém může být nezbytné explicitní pole je při práci s F # generátor kódu, který vysílá tříd bez objektů primární konstruktor.</span><span class="sxs-lookup"><span data-stu-id="5af65-146">Another situation in which an explicit field might be necessary is when you are working with an F# code generator which emits classes without a primary constructor.</span></span> <span data-ttu-id="5af65-147">Explicitní pole jsou také užitečná pro přístup z více vláken statické proměnné a podobné konstrukce.</span><span class="sxs-lookup"><span data-stu-id="5af65-147">Explicit fields are also useful for thread-static variables or similar constructs.</span></span> <span data-ttu-id="5af65-148">Další informace naleznete v tématu `System.ThreadStaticAttribute`.</span><span class="sxs-lookup"><span data-stu-id="5af65-148">For more information, see `System.ThreadStaticAttribute`.</span></span>

<span data-ttu-id="5af65-149">Když klíčová slova `member val` objeví spolu v definici typu je definice automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5af65-149">When the keywords `member val` appear together in a type definition, it is a definition of an automatically implemented property.</span></span> <span data-ttu-id="5af65-150">Další informace najdete v tématu [vlastnosti](properties.md).</span><span class="sxs-lookup"><span data-stu-id="5af65-150">For more information, see [Properties](properties.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="5af65-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="5af65-151">See Also</span></span>
[<span data-ttu-id="5af65-152">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="5af65-152">Properties</span></span>](properties.md)

[<span data-ttu-id="5af65-153">Členové</span><span class="sxs-lookup"><span data-stu-id="5af65-153">Members</span></span>](index.md)

[<span data-ttu-id="5af65-154">`let` Vazby do ve třídách</span><span class="sxs-lookup"><span data-stu-id="5af65-154">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)
