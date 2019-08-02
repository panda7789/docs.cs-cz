---
title: Referenční buňky
description: Přečtěte F# si, jak jsou referenční buňky umístění úložiště, která umožňují vytvářet proměnlivé hodnoty pomocí referenční sémantiky.
ms.date: 05/16/2016
ms.openlocfilehash: faaa4a6b54ff0366163b6821edff7fa4cb2f5a88
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627247"
---
# <a name="reference-cells"></a><span data-ttu-id="45e15-103">Referenční buňky</span><span class="sxs-lookup"><span data-stu-id="45e15-103">Reference Cells</span></span>

<span data-ttu-id="45e15-104">*Odkazové buňky* jsou umístění úložiště, která umožňují vytvářet proměnlivé hodnoty pomocí referenční sémantiky.</span><span class="sxs-lookup"><span data-stu-id="45e15-104">*Reference cells* are storage locations that enable you to create mutable values with reference semantics.</span></span>

## <a name="syntax"></a><span data-ttu-id="45e15-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45e15-105">Syntax</span></span>

```fsharp
ref expression
```

## <a name="remarks"></a><span data-ttu-id="45e15-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="45e15-106">Remarks</span></span>

<span data-ttu-id="45e15-107">`ref` Operátor použijete před hodnotou k vytvoření nové referenční buňky, která tuto hodnotu zapouzdří.</span><span class="sxs-lookup"><span data-stu-id="45e15-107">You use the `ref` operator before a value to create a new reference cell that encapsulates the value.</span></span> <span data-ttu-id="45e15-108">Zdrojovou hodnotu pak můžete změnit, protože je proměnlivá.</span><span class="sxs-lookup"><span data-stu-id="45e15-108">You can then change the underlying value because it is mutable.</span></span>

<span data-ttu-id="45e15-109">Odkazové buňky obsahují skutečnou hodnotu; není to pouze adresa.</span><span class="sxs-lookup"><span data-stu-id="45e15-109">A reference cell holds an actual value; it is not just an address.</span></span> <span data-ttu-id="45e15-110">Když vytvoříte odkazovou buňku pomocí `ref` operátoru, vytvoříte kopii základní hodnoty jako zapouzdřenou proměnlivou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="45e15-110">When you create a reference cell by using the `ref` operator, you create a copy of the underlying value as an encapsulated mutable value.</span></span>

<span data-ttu-id="45e15-111">Můžete odkázat na odkazovou buňku pomocí `!` operátoru (vykřičník).</span><span class="sxs-lookup"><span data-stu-id="45e15-111">You can dereference a reference cell by using the `!` (bang) operator.</span></span>

<span data-ttu-id="45e15-112">Následující příklad kódu znázorňuje deklaraci a použití odkazových buněk.</span><span class="sxs-lookup"><span data-stu-id="45e15-112">The following code example illustrates the declaration and use of reference cells.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

<span data-ttu-id="45e15-113">Výstup je `50`.</span><span class="sxs-lookup"><span data-stu-id="45e15-113">The output is `50`.</span></span>

<span data-ttu-id="45e15-114">Odkazové buňky jsou instancemi `Ref` obecného typu záznamu, který je deklarován následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="45e15-114">Reference cells are instances of the `Ref` generic record type, which is declared as follows.</span></span>

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

<span data-ttu-id="45e15-115">Typ `'a ref` je synonymum pro `Ref<'a>`.</span><span class="sxs-lookup"><span data-stu-id="45e15-115">The type `'a ref` is a synonym for `Ref<'a>`.</span></span> <span data-ttu-id="45e15-116">Kompilátor a technologie IntelliSense v integrovaném vývojovém prostředí zobrazují nejprve tento typ a následně zdrojovou definici.</span><span class="sxs-lookup"><span data-stu-id="45e15-116">The compiler and IntelliSense in the IDE display the former for this type, but the underlying definition is the latter.</span></span>

<span data-ttu-id="45e15-117">`ref` Operátor vytvoří novou odkazovou buňku.</span><span class="sxs-lookup"><span data-stu-id="45e15-117">The `ref` operator creates a new reference cell.</span></span> <span data-ttu-id="45e15-118">Následující kód je deklarace `ref` operátoru.</span><span class="sxs-lookup"><span data-stu-id="45e15-118">The following code is the declaration of the `ref` operator.</span></span>

```fsharp
let ref x = { contents = x }
```

<span data-ttu-id="45e15-119">V následující tabulce jsou uvedeny funkce, které jsou u odkazové buňky dostupné.</span><span class="sxs-lookup"><span data-stu-id="45e15-119">The following table shows the features that are available on the reference cell.</span></span>

|<span data-ttu-id="45e15-120">Operátor, člen nebo pole</span><span class="sxs-lookup"><span data-stu-id="45e15-120">Operator, member, or field</span></span>|<span data-ttu-id="45e15-121">Popis</span><span class="sxs-lookup"><span data-stu-id="45e15-121">Description</span></span>|<span data-ttu-id="45e15-122">type</span><span class="sxs-lookup"><span data-stu-id="45e15-122">Type</span></span>|<span data-ttu-id="45e15-123">Definice</span><span class="sxs-lookup"><span data-stu-id="45e15-123">Definition</span></span>|
|--------------------------|-----------|----|----------|
|<span data-ttu-id="45e15-124">`!`(operátor zpětného odkazování)</span><span class="sxs-lookup"><span data-stu-id="45e15-124">`!` (dereference operator)</span></span>|<span data-ttu-id="45e15-125">Vrátí zdrojovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="45e15-125">Returns the underlying value.</span></span>|`'a ref -> 'a`|`let (!) r = r.contents`|
|<span data-ttu-id="45e15-126">`:=`(operátor přiřazení)</span><span class="sxs-lookup"><span data-stu-id="45e15-126">`:=` (assignment operator)</span></span>|<span data-ttu-id="45e15-127">Změní zdrojovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="45e15-127">Changes the underlying value.</span></span>|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|<span data-ttu-id="45e15-128">`ref`podnikatel</span><span class="sxs-lookup"><span data-stu-id="45e15-128">`ref` (operator)</span></span>|<span data-ttu-id="45e15-129">Zapouzdří hodnotu do nové odkazové buňky.</span><span class="sxs-lookup"><span data-stu-id="45e15-129">Encapsulates a value into a new reference cell.</span></span>|`'a -> 'a ref`|`let ref x = { contents = x }`|
|<span data-ttu-id="45e15-130">`Value`majetek</span><span class="sxs-lookup"><span data-stu-id="45e15-130">`Value` (property)</span></span>|<span data-ttu-id="45e15-131">Získá nebo nastaví zdrojovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="45e15-131">Gets or sets the underlying value.</span></span>|`unit -> 'a`|`member x.Value = x.contents`|
|<span data-ttu-id="45e15-132">`contents`(pole záznamu)</span><span class="sxs-lookup"><span data-stu-id="45e15-132">`contents` (record field)</span></span>|<span data-ttu-id="45e15-133">Získá nebo nastaví zdrojovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="45e15-133">Gets or sets the underlying value.</span></span>|`'a`|`let ref x = { contents = x }`|

<span data-ttu-id="45e15-134">Ke zdrojové hodnotě lze získat přístup několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="45e15-134">There are several ways to access the underlying value.</span></span> <span data-ttu-id="45e15-135">Hodnota vrácená operátorem dereference (`!`) není hodnotou, kterou lze přiřadit.</span><span class="sxs-lookup"><span data-stu-id="45e15-135">The value returned by the dereference operator (`!`) is not an assignable value.</span></span> <span data-ttu-id="45e15-136">Proto pokud upravujete podkladovou hodnotu, je místo toho nutné použít operátor přiřazení (`:=`).</span><span class="sxs-lookup"><span data-stu-id="45e15-136">Therefore, if you are modifying the underlying value, you must use the assignment operator (`:=`) instead.</span></span>

<span data-ttu-id="45e15-137">`Value` Obě vlastnosti`contents` i pole jsou přiřaditelné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="45e15-137">Both the `Value` property and the `contents` field are assignable values.</span></span> <span data-ttu-id="45e15-138">Můžete je proto použít ke zpřístupnění nebo změně zdrojové hodnoty, jak znázorňuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="45e15-138">Therefore, you can use these to either access or change the underlying value, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

<span data-ttu-id="45e15-139">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="45e15-139">The output is as follows.</span></span>

```
10
10
11
12
```

<span data-ttu-id="45e15-140">Pole `contents` je k dispozici pro kompatibilitu s jinými verzemi ml a během kompilace vytvoří upozornění.</span><span class="sxs-lookup"><span data-stu-id="45e15-140">The field `contents` is provided for compatibility with other versions of ML and will produce a warning during compilation.</span></span> <span data-ttu-id="45e15-141">Chcete-li zakázat upozornění, použijte `--mlcompatibility` možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="45e15-141">To disable the warning, use the `--mlcompatibility` compiler option.</span></span> <span data-ttu-id="45e15-142">Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="45e15-142">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="45e15-143">C#Programátoři by měli znát `ref` , C# že v nástroji není totéž jako `ref` v F#nástroji.</span><span class="sxs-lookup"><span data-stu-id="45e15-143">C# programmers should know that `ref` in C# is not the same thing as `ref` in F#.</span></span> <span data-ttu-id="45e15-144">Ekvivalentní konstrukce v F# jsou byrefs [](byrefs.md), což jsou jiný koncept z referenčních buněk.</span><span class="sxs-lookup"><span data-stu-id="45e15-144">The equivalent constructs in F# are [byrefs](byrefs.md), which are a different concept from reference cells.</span></span>

<span data-ttu-id="45e15-145">Hodnoty označené jako `mutable`mohou být automaticky povýšeny `'a ref` na hodnotu, je-li zachycena uzávěrkou; viz [hodnoty](./values/index.md).</span><span class="sxs-lookup"><span data-stu-id="45e15-145">Values marked as `mutable`may be automatically promoted to `'a ref` if captured by a closure; see [Values](./values/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="45e15-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="45e15-146">See also</span></span>

- [<span data-ttu-id="45e15-147">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="45e15-147">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="45e15-148">Parametry a argumenty</span><span class="sxs-lookup"><span data-stu-id="45e15-148">Parameters and Arguments</span></span>](parameters-and-arguments.md)
- [<span data-ttu-id="45e15-149">Referenční dokumentace symbolů a operátorů</span><span class="sxs-lookup"><span data-stu-id="45e15-149">Symbol and Operator Reference</span></span>](./symbol-and-operator-reference/index.md)
- [<span data-ttu-id="45e15-150">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="45e15-150">Values</span></span>](./values/index.md)
