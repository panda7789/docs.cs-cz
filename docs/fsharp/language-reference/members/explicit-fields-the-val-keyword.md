---
title: "Explicitní pole: Klíčové slovo val (F#)"
description: "Další informace o F # 'val' – klíčové slovo, které se používá k deklaraci umístění pro uložení hodnotu v typu třídu nebo strukturu nebyl zadán typ."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3bdbc745-436b-407f-bf54-5d11ca829cd0
ms.openlocfilehash: cee53a48f08aec89b0bdd40189ed331cadee877d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="explicit-fields-the-val-keyword"></a><span data-ttu-id="b58ba-104">Explicitní pole: Klíčové slovo val</span><span class="sxs-lookup"><span data-stu-id="b58ba-104">Explicit Fields: The val Keyword</span></span>

<span data-ttu-id="b58ba-105">`val` – Klíčové slovo se používá k deklaraci umístění pro uložení hodnotu v typu třídy nebo struktura bez jeho inicializaci.</span><span class="sxs-lookup"><span data-stu-id="b58ba-105">The `val` keyword is used to declare a location to store a value in a class or structure type, without initializing it.</span></span> <span data-ttu-id="b58ba-106">Umístění úložiště deklarovaný tímto způsobem se nazývají *explicitní pole*.</span><span class="sxs-lookup"><span data-stu-id="b58ba-106">Storage locations declared in this manner are called *explicit fields*.</span></span> <span data-ttu-id="b58ba-107">Další používání `val` – klíčové slovo je ve spojení s `member` – klíčové slovo deklarovat ve automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b58ba-107">Another use of the `val` keyword is in conjunction with the `member` keyword to declare an auto-implemented property.</span></span> <span data-ttu-id="b58ba-108">Další informace o automaticky implementované vlastnosti najdete v tématu [vlastnosti](properties.md).</span><span class="sxs-lookup"><span data-stu-id="b58ba-108">For more information on auto-implemented properties, see [Properties](properties.md).</span></span>


## <a name="syntax"></a><span data-ttu-id="b58ba-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b58ba-109">Syntax</span></span>

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a><span data-ttu-id="b58ba-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b58ba-110">Remarks</span></span>
<span data-ttu-id="b58ba-111">Obvyklým definování polí v typu třídu nebo strukturu, je použít `let` vazby.</span><span class="sxs-lookup"><span data-stu-id="b58ba-111">The usual way to define fields in a class or structure type is to use a `let` binding.</span></span> <span data-ttu-id="b58ba-112">Ale `let` vazby musí být inicializován jako součást konstruktoru třídy, která není vždy možná, potřebná nebo žádoucí.</span><span class="sxs-lookup"><span data-stu-id="b58ba-112">However, `let` bindings must be initialized as part of the class constructor, which is not always possible, necessary, or desirable.</span></span> <span data-ttu-id="b58ba-113">Můžete použít `val` – klíčové slovo chcete pole, které není inicializován.</span><span class="sxs-lookup"><span data-stu-id="b58ba-113">You can use the `val` keyword when you want a field that is uninitialized.</span></span>

<span data-ttu-id="b58ba-114">Explicitní pole můžou být statické nebo nestatické.</span><span class="sxs-lookup"><span data-stu-id="b58ba-114">Explicit fields can be static or non-static.</span></span> <span data-ttu-id="b58ba-115">*– Modifikátor přístupu* může být `public`, `private`, nebo `internal`.</span><span class="sxs-lookup"><span data-stu-id="b58ba-115">The *access-modifier* can be `public`, `private`, or `internal`.</span></span> <span data-ttu-id="b58ba-116">Ve výchozím nastavení jsou explicitní pole veřejné.</span><span class="sxs-lookup"><span data-stu-id="b58ba-116">By default, explicit fields are public.</span></span> <span data-ttu-id="b58ba-117">Tím se liší od `let` vazby do ve třídách, které jsou vždy privátní.</span><span class="sxs-lookup"><span data-stu-id="b58ba-117">This differs from `let` bindings in classes, which are always private.</span></span>

<span data-ttu-id="b58ba-118">[DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) atribut je požadován u explicitní pole v typy tříd, které mají primární konstruktor.</span><span class="sxs-lookup"><span data-stu-id="b58ba-118">The [DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) attribute is required on explicit fields in class types that have a primary constructor.</span></span> <span data-ttu-id="b58ba-119">Tento atribut určuje, že pole je inicializováno na nulu.</span><span class="sxs-lookup"><span data-stu-id="b58ba-119">This attribute specifies that the field is initialized to zero.</span></span> <span data-ttu-id="b58ba-120">Typ pole musí podporovat inicializace nula.</span><span class="sxs-lookup"><span data-stu-id="b58ba-120">The type of the field must support zero-initialization.</span></span> <span data-ttu-id="b58ba-121">Typ podporuje inicializace nula. Pokud jde o jeden z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="b58ba-121">A type supports zero-initialization if it is one of the following:</span></span>

- <span data-ttu-id="b58ba-122">Primitivní typ, který má nulovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b58ba-122">A primitive type that has a zero value.</span></span>

- <span data-ttu-id="b58ba-123">Typ, který podporuje hodnotu null, buď jako hodnotu Normální, jako neobvyklé hodnoty nebo jako reprezentace hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b58ba-123">A type that supports a null value, either as a normal value, as an abnormal value, or as a representation of a value.</span></span> <span data-ttu-id="b58ba-124">To zahrnuje třídy, řazené kolekce členů, záznamy, funkce, rozhraní, referenční typy .NET, `unit` typ a rozlišovaná sjednocení typů.</span><span class="sxs-lookup"><span data-stu-id="b58ba-124">This includes classes, tuples, records, functions, interfaces, .NET reference types, the `unit` type, and discriminated union types.</span></span>

- <span data-ttu-id="b58ba-125">Typ hodnoty .NET.</span><span class="sxs-lookup"><span data-stu-id="b58ba-125">A .NET value type.</span></span>

- <span data-ttu-id="b58ba-126">Struktura, jejichž pole všechny podporují výchozí nulovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b58ba-126">A structure whose fields all support a default zero value.</span></span>


<span data-ttu-id="b58ba-127">Například neměnné pole s názvem `someField` má základní pole v .NET zkompilovat reprezentace s názvem `someField@`, a získat přístup k hodnotě uložené pomocí vlastnost s názvem `someField`.</span><span class="sxs-lookup"><span data-stu-id="b58ba-127">For example, an immutable field called `someField` has a backing field in the .NET compiled representation with the name `someField@`, and you access the stored value using a property named `someField`.</span></span>

<span data-ttu-id="b58ba-128">Pro měnitelný pole je reprezentace .NET zkompilovat pole rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="b58ba-128">For a mutable field, the .NET compiled representation is a .NET field.</span></span>


>[!WARNING] 
<span data-ttu-id="b58ba-129">`Note`Obor názvů rozhraní .NET Framework `System.ComponentModel` obsahuje atribut, který má stejný název.</span><span class="sxs-lookup"><span data-stu-id="b58ba-129">`Note` The .NET Framework namespace `System.ComponentModel` contains an attribute that has the same name.</span></span> <span data-ttu-id="b58ba-130">Informace o tento atribut najdete v tématu `System.ComponentModel.DefaultValueAttribute`.</span><span class="sxs-lookup"><span data-stu-id="b58ba-130">For information about this attribute, see `System.ComponentModel.DefaultValueAttribute`.</span></span>


<span data-ttu-id="b58ba-131">Následující kód ukazuje použití explicitní pole a pro porovnání, `let` vazby ve třídy, která má primární konstruktor.</span><span class="sxs-lookup"><span data-stu-id="b58ba-131">The following code shows the use of explicit fields and, for comparison, a `let` binding in a class that has a primary constructor.</span></span> <span data-ttu-id="b58ba-132">Všimněte si, že `let`-vázané pole `myInt1` je soukromé.</span><span class="sxs-lookup"><span data-stu-id="b58ba-132">Note that the `let`-bound field `myInt1` is private.</span></span> <span data-ttu-id="b58ba-133">Když `let`-vázané pole `myInt1` se odkazuje z metody člen, vlastní identifikátor `this` se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="b58ba-133">When the `let`-bound field `myInt1` is referenced from a member method, the self identifier `this` is not required.</span></span> <span data-ttu-id="b58ba-134">Když odkazujete explicitní pole, ale `myInt2` a `myString`, je vyžadován vlastní identifikátor.</span><span class="sxs-lookup"><span data-stu-id="b58ba-134">But when you are referencing the explicit fields `myInt2` and `myString`, the self identifier is required.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

<span data-ttu-id="b58ba-135">Výstup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="b58ba-135">The output is as follows:</span></span>

```
11 12 abc
30 def
```

<span data-ttu-id="b58ba-136">Následující kód ukazuje použití explicitní pole ve třídě, která neobsahuje primární konstruktor.</span><span class="sxs-lookup"><span data-stu-id="b58ba-136">The following code shows the use of explicit fields in a class that does not have a primary constructor.</span></span> <span data-ttu-id="b58ba-137">V takovém případě `DefaultValue` atribut se nevyžaduje, ale v konstruktorech, které jsou definovány pro typ se musí inicializovat všechna pole.</span><span class="sxs-lookup"><span data-stu-id="b58ba-137">In this case, the `DefaultValue` attribute is not required, but all the fields must be initialized in the constructors that are defined for the type.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

<span data-ttu-id="b58ba-138">Výstupem je `35 22`.</span><span class="sxs-lookup"><span data-stu-id="b58ba-138">The output is `35 22`.</span></span>

<span data-ttu-id="b58ba-139">Následující kód ukazuje použití explicitní pole ve struktuře.</span><span class="sxs-lookup"><span data-stu-id="b58ba-139">The following code shows the use of explicit fields in a structure.</span></span> <span data-ttu-id="b58ba-140">Vzhledem k tomu, že typ hodnoty strukturu se má automaticky výchozí konstruktor, která nastavuje hodnoty jeho polí na nulu.</span><span class="sxs-lookup"><span data-stu-id="b58ba-140">Because a structure is a value type, it automatically has a default constructor that sets the values of its fields to zero.</span></span> <span data-ttu-id="b58ba-141">Proto `DefaultValue` atribut se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="b58ba-141">Therefore, the `DefaultValue` attribute is not required.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

<span data-ttu-id="b58ba-142">Výstupem je `11 xyz`.</span><span class="sxs-lookup"><span data-stu-id="b58ba-142">The output is `11 xyz`.</span></span>

<span data-ttu-id="b58ba-143">Explicitní pole nejsou určeny k použití rutiny.</span><span class="sxs-lookup"><span data-stu-id="b58ba-143">Explicit fields are not intended for routine use.</span></span> <span data-ttu-id="b58ba-144">Obecně platí, pokud je to možné byste měli používat `let` vazby v třídě místo explicitní pole.</span><span class="sxs-lookup"><span data-stu-id="b58ba-144">In general, when possible you should use a `let` binding in a class instead of an explicit field.</span></span> <span data-ttu-id="b58ba-145">Explicitní pole jsou užitečné v některých scénářích vzájemná funkční spolupráce, například když je třeba definovat strukturu, která bude použita v platformu vyvolání volání do nativního rozhraní API, nebo ve scénářích zprostředkovatele komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="b58ba-145">Explicit fields are useful in certain interoperability scenarios, such as when you need to define a structure that will be used in a platform invoke call to a native API, or in COM interop scenarios.</span></span> <span data-ttu-id="b58ba-146">Další informace najdete v tématu [externí funkce](../functions/external-functions.md).</span><span class="sxs-lookup"><span data-stu-id="b58ba-146">For more information, see [External Functions](../functions/external-functions.md).</span></span> <span data-ttu-id="b58ba-147">Další situace, ve kterém může být nezbytné explicitní pole je při práci s F # generátor kódu, který vysílá tříd bez objektů primární konstruktor.</span><span class="sxs-lookup"><span data-stu-id="b58ba-147">Another situation in which an explicit field might be necessary is when you are working with an F# code generator which emits classes without a primary constructor.</span></span> <span data-ttu-id="b58ba-148">Explicitní pole jsou také užitečná pro přístup z více vláken statické proměnné a podobné konstrukce.</span><span class="sxs-lookup"><span data-stu-id="b58ba-148">Explicit fields are also useful for thread-static variables or similar constructs.</span></span> <span data-ttu-id="b58ba-149">Další informace naleznete v tématu `System.ThreadStaticAttribute`.</span><span class="sxs-lookup"><span data-stu-id="b58ba-149">For more information, see `System.ThreadStaticAttribute`.</span></span>

<span data-ttu-id="b58ba-150">Když klíčová slova `member val` objeví spolu v definici typu je definice automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b58ba-150">When the keywords `member val` appear together in a type definition, it is a definition of an automatically implemented property.</span></span> <span data-ttu-id="b58ba-151">Další informace najdete v tématu [vlastnosti](properties.md).</span><span class="sxs-lookup"><span data-stu-id="b58ba-151">For more information, see [Properties](properties.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="b58ba-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="b58ba-152">See Also</span></span>
[<span data-ttu-id="b58ba-153">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b58ba-153">Properties</span></span>](properties.md)

[<span data-ttu-id="b58ba-154">Členy</span><span class="sxs-lookup"><span data-stu-id="b58ba-154">Members</span></span>](index.md)

[<span data-ttu-id="b58ba-155">`let`Vazby do ve třídách</span><span class="sxs-lookup"><span data-stu-id="b58ba-155">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)
