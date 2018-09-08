---
title: Referenční buňky (F#)
description: 'Zjistěte, jak F # odkazové buňky jsou úložná místa, které umožňují vytvořit proměnlivé hodnoty pomocí odkazové sémantiky.'
ms.date: 05/16/2016
ms.openlocfilehash: e2e1a91c62fd76e4992bc5ae11bb672766850718
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44192252"
---
# <a name="reference-cells"></a><span data-ttu-id="1968a-103">Referenční buňky</span><span class="sxs-lookup"><span data-stu-id="1968a-103">Reference Cells</span></span>

<span data-ttu-id="1968a-104">*Odkazové buňky* jsou úložná místa, které umožňují vytvořit proměnlivé hodnoty pomocí odkazové sémantiky.</span><span class="sxs-lookup"><span data-stu-id="1968a-104">*Reference cells* are storage locations that enable you to create mutable values with reference semantics.</span></span>

## <a name="syntax"></a><span data-ttu-id="1968a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1968a-105">Syntax</span></span>

```fsharp
ref expression
```

## <a name="remarks"></a><span data-ttu-id="1968a-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1968a-106">Remarks</span></span>

<span data-ttu-id="1968a-107">Můžete použít `ref` operátor před hodnotou, má-li vytvořit novou odkazovou buňku, která zapouzdřuje hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1968a-107">You use the `ref` operator before a value to create a new reference cell that encapsulates the value.</span></span> <span data-ttu-id="1968a-108">Zdrojovou hodnotu pak můžete změnit, protože je proměnlivá.</span><span class="sxs-lookup"><span data-stu-id="1968a-108">You can then change the underlying value because it is mutable.</span></span>

<span data-ttu-id="1968a-109">Odkazové buňky obsahují skutečnou hodnotu; není to pouze adresa.</span><span class="sxs-lookup"><span data-stu-id="1968a-109">A reference cell holds an actual value; it is not just an address.</span></span> <span data-ttu-id="1968a-110">Při vytvoření odkazové buňky pomocí `ref` operátoru, vytvoření kopie zdrojové hodnoty ve formě zapouzdřené proměnlivé hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1968a-110">When you create a reference cell by using the `ref` operator, you create a copy of the underlying value as an encapsulated mutable value.</span></span>

<span data-ttu-id="1968a-111">Že přestoupíte odkazové buňky pomocí `!` – operátor (vykřičník).</span><span class="sxs-lookup"><span data-stu-id="1968a-111">You can dereference a reference cell by using the `!` (bang) operator.</span></span>

<span data-ttu-id="1968a-112">Následující příklad kódu znázorňuje deklaraci a použití odkazových buněk.</span><span class="sxs-lookup"><span data-stu-id="1968a-112">The following code example illustrates the declaration and use of reference cells.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

<span data-ttu-id="1968a-113">Výstup je `50`.</span><span class="sxs-lookup"><span data-stu-id="1968a-113">The output is `50`.</span></span>

<span data-ttu-id="1968a-114">Odkazové buňky jsou instance `Ref` generického typu záznamu, který je deklarován následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="1968a-114">Reference cells are instances of the `Ref` generic record type, which is declared as follows.</span></span>

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

<span data-ttu-id="1968a-115">Typ `'a ref` je synonymum pro `Ref<'a>`.</span><span class="sxs-lookup"><span data-stu-id="1968a-115">The type `'a ref` is a synonym for `Ref<'a>`.</span></span> <span data-ttu-id="1968a-116">Kompilátor a technologie IntelliSense v integrovaném vývojovém prostředí zobrazují nejprve tento typ a následně zdrojovou definici.</span><span class="sxs-lookup"><span data-stu-id="1968a-116">The compiler and IntelliSense in the IDE display the former for this type, but the underlying definition is the latter.</span></span>

<span data-ttu-id="1968a-117">`ref` Operátor vytvoří novou odkazovou buňku.</span><span class="sxs-lookup"><span data-stu-id="1968a-117">The `ref` operator creates a new reference cell.</span></span> <span data-ttu-id="1968a-118">Následující kód je deklarace `ref` operátor.</span><span class="sxs-lookup"><span data-stu-id="1968a-118">The following code is the declaration of the `ref` operator.</span></span>

```fsharp
let ref x = { contents = x }
```

<span data-ttu-id="1968a-119">V následující tabulce jsou uvedeny funkce, které jsou u odkazové buňky dostupné.</span><span class="sxs-lookup"><span data-stu-id="1968a-119">The following table shows the features that are available on the reference cell.</span></span>

|<span data-ttu-id="1968a-120">Operátor, člen nebo pole</span><span class="sxs-lookup"><span data-stu-id="1968a-120">Operator, member, or field</span></span>|<span data-ttu-id="1968a-121">Popis</span><span class="sxs-lookup"><span data-stu-id="1968a-121">Description</span></span>|<span data-ttu-id="1968a-122">Typ</span><span class="sxs-lookup"><span data-stu-id="1968a-122">Type</span></span>|<span data-ttu-id="1968a-123">Definice</span><span class="sxs-lookup"><span data-stu-id="1968a-123">Definition</span></span>|
|--------------------------|-----------|----|----------|
|<span data-ttu-id="1968a-124">`!` (operátor zrušení odkazu)</span><span class="sxs-lookup"><span data-stu-id="1968a-124">`!` (dereference operator)</span></span>|<span data-ttu-id="1968a-125">Vrátí zdrojovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1968a-125">Returns the underlying value.</span></span>|`'a ref -> 'a`|`let (!) r = r.contents`|
|<span data-ttu-id="1968a-126">`:=` (operátor přiřazení)</span><span class="sxs-lookup"><span data-stu-id="1968a-126">`:=` (assignment operator)</span></span>|<span data-ttu-id="1968a-127">Změní zdrojovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1968a-127">Changes the underlying value.</span></span>|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|<span data-ttu-id="1968a-128">`ref` (operátor)</span><span class="sxs-lookup"><span data-stu-id="1968a-128">`ref` (operator)</span></span>|<span data-ttu-id="1968a-129">Zapouzdří hodnotu do nové odkazové buňky.</span><span class="sxs-lookup"><span data-stu-id="1968a-129">Encapsulates a value into a new reference cell.</span></span>|`'a -> 'a ref`|`let ref x = { contents = x }`|
|<span data-ttu-id="1968a-130">`Value` (vlastnost)</span><span class="sxs-lookup"><span data-stu-id="1968a-130">`Value` (property)</span></span>|<span data-ttu-id="1968a-131">Získá nebo nastaví zdrojovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1968a-131">Gets or sets the underlying value.</span></span>|`unit -> 'a`|`member x.Value = x.contents`|
|<span data-ttu-id="1968a-132">`contents` (pole záznamu)</span><span class="sxs-lookup"><span data-stu-id="1968a-132">`contents` (record field)</span></span>|<span data-ttu-id="1968a-133">Získá nebo nastaví zdrojovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1968a-133">Gets or sets the underlying value.</span></span>|`'a`|`let ref x = { contents = x }`|
<span data-ttu-id="1968a-134">Ke zdrojové hodnotě lze získat přístup několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="1968a-134">There are several ways to access the underlying value.</span></span> <span data-ttu-id="1968a-135">Hodnota vrácená operátorem zrušení odkazu (`!`) není Přiřaditelná.</span><span class="sxs-lookup"><span data-stu-id="1968a-135">The value returned by the dereference operator (`!`) is not an assignable value.</span></span> <span data-ttu-id="1968a-136">Proto se při změně zdrojové hodnoty, musíte použít operátor přiřazení (`:=`) místo toho.</span><span class="sxs-lookup"><span data-stu-id="1968a-136">Therefore, if you are modifying the underlying value, you must use the assignment operator (`:=`) instead.</span></span>

<span data-ttu-id="1968a-137">Oba `Value` vlastnost a `contents` pole jsou Přiřaditelné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1968a-137">Both the `Value` property and the `contents` field are assignable values.</span></span> <span data-ttu-id="1968a-138">Můžete je proto použít ke zpřístupnění nebo změně zdrojové hodnoty, jak znázorňuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="1968a-138">Therefore, you can use these to either access or change the underlying value, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

<span data-ttu-id="1968a-139">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="1968a-139">The output is as follows.</span></span>

```
10
10
11
12
```

<span data-ttu-id="1968a-140">Pole `contents` zajišťuje kompatibilitu s jinými verzemi ML a během kompilace zobrazí upozornění.</span><span class="sxs-lookup"><span data-stu-id="1968a-140">The field `contents` is provided for compatibility with other versions of ML and will produce a warning during compilation.</span></span> <span data-ttu-id="1968a-141">Chcete-li toto upozornění zakážete, použijte `--mlcompatibility` – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="1968a-141">To disable the warning, use the `--mlcompatibility` compiler option.</span></span> <span data-ttu-id="1968a-142">Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="1968a-142">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="1968a-143">Programátoři v C# měli vědět, že `ref` v jazyce C# není totéž jako `ref` v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="1968a-143">C# programmers should know that `ref` in C# is not the same thing as `ref` in F#.</span></span> <span data-ttu-id="1968a-144">Ekvivalentní konstrukce v jazyce F # jsou [ByRef](byrefs.md), které jsou různé koncept z odkazové buňky.</span><span class="sxs-lookup"><span data-stu-id="1968a-144">The equivalent constructs in F# are [byrefs](byrefs.md), which are a different concept from reference cells.</span></span>

<span data-ttu-id="1968a-145">Hodnoty označeny jako `mutable`může automaticky povýšen na `'a ref` nezachytává uzavření; naleznete v tématu [hodnoty](values/index.md).</span><span class="sxs-lookup"><span data-stu-id="1968a-145">Values marked as `mutable`may be automatically promoted to `'a ref` if captured by a closure; see [Values](values/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1968a-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1968a-146">See also</span></span>

- [<span data-ttu-id="1968a-147">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="1968a-147">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="1968a-148">Parametry a argumenty</span><span class="sxs-lookup"><span data-stu-id="1968a-148">Parameters and Arguments</span></span>](parameters-and-arguments.md)
- [<span data-ttu-id="1968a-149">Referenční dokumentace symbolů a operátorů</span><span class="sxs-lookup"><span data-stu-id="1968a-149">Symbol and Operator Reference</span></span>](symbol-and-operator-reference/index.md)
- [<span data-ttu-id="1968a-150">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="1968a-150">Values</span></span>](values/index.md)
