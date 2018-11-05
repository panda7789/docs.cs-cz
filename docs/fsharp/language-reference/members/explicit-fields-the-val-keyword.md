---
title: 'Explicitní pole: Klíčové slovo val (F#)'
description: 'Další informace o F # "val" klíčové slovo, které se používá k deklaraci umístění pro uložení hodnoty v typu třídy nebo struktury bez inicializace typu.'
ms.date: 05/16/2016
ms.openlocfilehash: 9cd06f7e90192be79490dd0ff67f118cce4339c3
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "45746363"
---
# <a name="explicit-fields-the-val-keyword"></a><span data-ttu-id="2444a-103">Explicitní pole: Klíčové slovo val</span><span class="sxs-lookup"><span data-stu-id="2444a-103">Explicit Fields: The val Keyword</span></span>

<span data-ttu-id="2444a-104">`val` – Klíčové slovo se používá k deklaraci umístění pro uložení hodnoty v typu třídy nebo struktury, bez jeho inicializaci.</span><span class="sxs-lookup"><span data-stu-id="2444a-104">The `val` keyword is used to declare a location to store a value in a class or structure type, without initializing it.</span></span> <span data-ttu-id="2444a-105">Umístění úložiště, které jsou deklarovány tímto způsobem se nazývají *explicitní pole*.</span><span class="sxs-lookup"><span data-stu-id="2444a-105">Storage locations declared in this manner are called *explicit fields*.</span></span> <span data-ttu-id="2444a-106">Další používání `val` – klíčové slovo se používá současně se `member` – klíčové slovo Chcete-li deklarovat automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2444a-106">Another use of the `val` keyword is in conjunction with the `member` keyword to declare an auto-implemented property.</span></span> <span data-ttu-id="2444a-107">Další informace o automaticky implementovaných vlastností najdete v tématu [vlastnosti](properties.md).</span><span class="sxs-lookup"><span data-stu-id="2444a-107">For more information on auto-implemented properties, see [Properties](properties.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="2444a-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2444a-108">Syntax</span></span>

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a><span data-ttu-id="2444a-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2444a-109">Remarks</span></span>

<span data-ttu-id="2444a-110">Obvyklým způsobem k definování polí v typu třídy nebo struktury je použít `let` vazby.</span><span class="sxs-lookup"><span data-stu-id="2444a-110">The usual way to define fields in a class or structure type is to use a `let` binding.</span></span> <span data-ttu-id="2444a-111">Ale `let` vazby musí být inicializované jako součást konstruktoru třídy, která není vždy možné, potřebná nebo žádoucí.</span><span class="sxs-lookup"><span data-stu-id="2444a-111">However, `let` bindings must be initialized as part of the class constructor, which is not always possible, necessary, or desirable.</span></span> <span data-ttu-id="2444a-112">Můžete použít `val` – klíčové slovo má pole, které není inicializován.</span><span class="sxs-lookup"><span data-stu-id="2444a-112">You can use the `val` keyword when you want a field that is uninitialized.</span></span>

<span data-ttu-id="2444a-113">Explicitní pole může být statické nebo nestatické.</span><span class="sxs-lookup"><span data-stu-id="2444a-113">Explicit fields can be static or non-static.</span></span> <span data-ttu-id="2444a-114">*Modifikátor přístupu* může být `public`, `private`, nebo `internal`.</span><span class="sxs-lookup"><span data-stu-id="2444a-114">The *access-modifier* can be `public`, `private`, or `internal`.</span></span> <span data-ttu-id="2444a-115">Explicitní pole jsou ve výchozím nastavení veřejné.</span><span class="sxs-lookup"><span data-stu-id="2444a-115">By default, explicit fields are public.</span></span> <span data-ttu-id="2444a-116">Tím se liší od `let` vazby ve třídách, které jsou vždycky privátní.</span><span class="sxs-lookup"><span data-stu-id="2444a-116">This differs from `let` bindings in classes, which are always private.</span></span>

<span data-ttu-id="2444a-117">[DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) atribut je požadován na explicitní pole v typy tříd, které mají primární konstruktor.</span><span class="sxs-lookup"><span data-stu-id="2444a-117">The [DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) attribute is required on explicit fields in class types that have a primary constructor.</span></span> <span data-ttu-id="2444a-118">Tento atribut určuje, že pole je inicializována na nulovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2444a-118">This attribute specifies that the field is initialized to zero.</span></span> <span data-ttu-id="2444a-119">Typ pole musí podporovat inicializace nula.</span><span class="sxs-lookup"><span data-stu-id="2444a-119">The type of the field must support zero-initialization.</span></span> <span data-ttu-id="2444a-120">Typ podporuje inicializace nula, pokud jde o jeden z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="2444a-120">A type supports zero-initialization if it is one of the following:</span></span>

- <span data-ttu-id="2444a-121">Primitivní typ, který má hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="2444a-121">A primitive type that has a zero value.</span></span>

- <span data-ttu-id="2444a-122">Typ, který podporuje hodnotu null jako hodnotu Normální, neobvyklé hodnoty nebo jako reprezentace hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2444a-122">A type that supports a null value, either as a normal value, as an abnormal value, or as a representation of a value.</span></span> <span data-ttu-id="2444a-123">To zahrnuje třídy, řazených kolekcí členů, záznamy, funkce, rozhraní a referenční typy .NET, `unit` typ a typy rozlišených sjednocení.</span><span class="sxs-lookup"><span data-stu-id="2444a-123">This includes classes, tuples, records, functions, interfaces, .NET reference types, the `unit` type, and discriminated union types.</span></span>

- <span data-ttu-id="2444a-124">Typ hodnoty .NET.</span><span class="sxs-lookup"><span data-stu-id="2444a-124">A .NET value type.</span></span>

- <span data-ttu-id="2444a-125">Struktura, jejíž všechna pole podporují výchozí nulovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2444a-125">A structure whose fields all support a default zero value.</span></span>

<span data-ttu-id="2444a-126">Například neměnné pole s názvem `someField` zkompiloval pomocným polem v rozhraní .NET reprezentaci s názvem `someField@`, a přístup k uložené hodnotě pomocí vlastnosti s názvem `someField`.</span><span class="sxs-lookup"><span data-stu-id="2444a-126">For example, an immutable field called `someField` has a backing field in the .NET compiled representation with the name `someField@`, and you access the stored value using a property named `someField`.</span></span>

<span data-ttu-id="2444a-127">Proměnlivé pole je reprezentace .NET zkompilován pole .NET.</span><span class="sxs-lookup"><span data-stu-id="2444a-127">For a mutable field, the .NET compiled representation is a .NET field.</span></span>

>[!WARNING]
<span data-ttu-id="2444a-128">`Note` Obor názvů rozhraní .NET Framework `System.ComponentModel` obsahuje atribut, který má stejný název.</span><span class="sxs-lookup"><span data-stu-id="2444a-128">`Note` The .NET Framework namespace `System.ComponentModel` contains an attribute that has the same name.</span></span> <span data-ttu-id="2444a-129">Informace o tomto atributu naleznete v tématu `System.ComponentModel.DefaultValueAttribute`.</span><span class="sxs-lookup"><span data-stu-id="2444a-129">For information about this attribute, see `System.ComponentModel.DefaultValueAttribute`.</span></span>

<span data-ttu-id="2444a-130">Následující kód ukazuje použití explicitní pole a pro porovnání, `let` vazby ve třídě, která má primární konstruktor.</span><span class="sxs-lookup"><span data-stu-id="2444a-130">The following code shows the use of explicit fields and, for comparison, a `let` binding in a class that has a primary constructor.</span></span> <span data-ttu-id="2444a-131">Všimněte si, že `let`-vázané pole `myInt1` je privátní.</span><span class="sxs-lookup"><span data-stu-id="2444a-131">Note that the `let`-bound field `myInt1` is private.</span></span> <span data-ttu-id="2444a-132">Když `let`-vázané pole `myInt1` se odkazuje z metody člen, identifikátoru samotného `this` se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="2444a-132">When the `let`-bound field `myInt1` is referenced from a member method, the self identifier `this` is not required.</span></span> <span data-ttu-id="2444a-133">Když odkazujete na explicitní pole, ale `myInt2` a `myString`, identifikátoru samotného je povinný.</span><span class="sxs-lookup"><span data-stu-id="2444a-133">But when you are referencing the explicit fields `myInt2` and `myString`, the self identifier is required.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

<span data-ttu-id="2444a-134">Výstup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="2444a-134">The output is as follows:</span></span>

```
11 12 abc
30 def
```

<span data-ttu-id="2444a-135">Následující kód ukazuje použití explicitní pole ve třídě, která nemá primární konstruktor.</span><span class="sxs-lookup"><span data-stu-id="2444a-135">The following code shows the use of explicit fields in a class that does not have a primary constructor.</span></span> <span data-ttu-id="2444a-136">V takovém případě `DefaultValue` atribut není povinný, ale musí se inicializovat všechna pole v konstruktorech, které jsou definovány pro typ.</span><span class="sxs-lookup"><span data-stu-id="2444a-136">In this case, the `DefaultValue` attribute is not required, but all the fields must be initialized in the constructors that are defined for the type.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

<span data-ttu-id="2444a-137">Výstup je `35 22`.</span><span class="sxs-lookup"><span data-stu-id="2444a-137">The output is `35 22`.</span></span>

<span data-ttu-id="2444a-138">Následující kód ukazuje použití explicitní pole ve struktuře.</span><span class="sxs-lookup"><span data-stu-id="2444a-138">The following code shows the use of explicit fields in a structure.</span></span> <span data-ttu-id="2444a-139">Vzhledem k tomu, že struktura je hodnotový typ, má automaticky výchozí konstruktor, který nastaví hodnoty polí na nulu.</span><span class="sxs-lookup"><span data-stu-id="2444a-139">Because a structure is a value type, it automatically has a default constructor that sets the values of its fields to zero.</span></span> <span data-ttu-id="2444a-140">Proto `DefaultValue` atribut se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="2444a-140">Therefore, the `DefaultValue` attribute is not required.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

<span data-ttu-id="2444a-141">Výstup je `11 xyz`.</span><span class="sxs-lookup"><span data-stu-id="2444a-141">The output is `11 xyz`.</span></span>

<span data-ttu-id="2444a-142">Explicitní pole nejsou určené pro běžné použití.</span><span class="sxs-lookup"><span data-stu-id="2444a-142">Explicit fields are not intended for routine use.</span></span> <span data-ttu-id="2444a-143">Obecně platí, pokud je to možné, abyste používali `let` vazby ve třídě místo explicitní pole.</span><span class="sxs-lookup"><span data-stu-id="2444a-143">In general, when possible you should use a `let` binding in a class instead of an explicit field.</span></span> <span data-ttu-id="2444a-144">Explicitní pole jsou užitečné v některých případech interoperability, například když je třeba definovat strukturu, která se použije v vyvolání platformy volání nativního rozhraní API, nebo ve scénářích vzájemné spolupráce COM.</span><span class="sxs-lookup"><span data-stu-id="2444a-144">Explicit fields are useful in certain interoperability scenarios, such as when you need to define a structure that will be used in a platform invoke call to a native API, or in COM interop scenarios.</span></span> <span data-ttu-id="2444a-145">Další informace najdete v tématu [externí funkce](../functions/external-functions.md).</span><span class="sxs-lookup"><span data-stu-id="2444a-145">For more information, see [External Functions](../functions/external-functions.md).</span></span> <span data-ttu-id="2444a-146">Další situace, ve kterém může být nutné explicitní pole je při práci F # generátoru kódu, který generuje třídy bez primárního konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="2444a-146">Another situation in which an explicit field might be necessary is when you are working with an F# code generator which emits classes without a primary constructor.</span></span> <span data-ttu-id="2444a-147">Explicitní pole jsou také užitečné pro proměnné statická na úrovni vlákna nebo podobné konstrukce.</span><span class="sxs-lookup"><span data-stu-id="2444a-147">Explicit fields are also useful for thread-static variables or similar constructs.</span></span> <span data-ttu-id="2444a-148">Další informace naleznete v tématu `System.ThreadStaticAttribute`.</span><span class="sxs-lookup"><span data-stu-id="2444a-148">For more information, see `System.ThreadStaticAttribute`.</span></span>

<span data-ttu-id="2444a-149">Když klíčová slova `member val` pohromadě v definici typu, je to definice automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2444a-149">When the keywords `member val` appear together in a type definition, it is a definition of an automatically implemented property.</span></span> <span data-ttu-id="2444a-150">Další informace najdete v tématu [vlastnosti](properties.md).</span><span class="sxs-lookup"><span data-stu-id="2444a-150">For more information, see [Properties](properties.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2444a-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2444a-151">See also</span></span>

- [<span data-ttu-id="2444a-152">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2444a-152">Properties</span></span>](properties.md)
- [<span data-ttu-id="2444a-153">Členové</span><span class="sxs-lookup"><span data-stu-id="2444a-153">Members</span></span>](index.md)
- [<span data-ttu-id="2444a-154">`let` Vazby ve třídách</span><span class="sxs-lookup"><span data-stu-id="2444a-154">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)
