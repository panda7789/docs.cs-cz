---
title: Referenční buňky (F#)
description: 'Zjistěte, jak F # odkazové buňky jsou úložná místa, které umožňují vytvořit proměnlivé hodnoty pomocí odkazové sémantiky.'
ms.date: 05/16/2016
ms.openlocfilehash: 133aec6b162a13306a05c9afa172f859890565eb
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43892415"
---
# <a name="reference-cells"></a><span data-ttu-id="c97b6-103">Referenční buňky</span><span class="sxs-lookup"><span data-stu-id="c97b6-103">Reference Cells</span></span>

<span data-ttu-id="c97b6-104">*Odkazové buňky* jsou úložná místa, které umožňují vytvořit proměnlivé hodnoty pomocí odkazové sémantiky.</span><span class="sxs-lookup"><span data-stu-id="c97b6-104">*Reference cells* are storage locations that enable you to create mutable values with reference semantics.</span></span>

## <a name="syntax"></a><span data-ttu-id="c97b6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c97b6-105">Syntax</span></span>

```fsharp
ref expression
```

## <a name="remarks"></a><span data-ttu-id="c97b6-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c97b6-106">Remarks</span></span>

<span data-ttu-id="c97b6-107">Můžete použít `ref` operátor před hodnotou, má-li vytvořit novou odkazovou buňku, která zapouzdřuje hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c97b6-107">You use the `ref` operator before a value to create a new reference cell that encapsulates the value.</span></span> <span data-ttu-id="c97b6-108">Zdrojovou hodnotu pak můžete změnit, protože je proměnlivá.</span><span class="sxs-lookup"><span data-stu-id="c97b6-108">You can then change the underlying value because it is mutable.</span></span>

<span data-ttu-id="c97b6-109">Odkazové buňky obsahují skutečnou hodnotu; není to pouze adresa.</span><span class="sxs-lookup"><span data-stu-id="c97b6-109">A reference cell holds an actual value; it is not just an address.</span></span> <span data-ttu-id="c97b6-110">Při vytvoření odkazové buňky pomocí `ref` operátoru, vytvoření kopie zdrojové hodnoty ve formě zapouzdřené proměnlivé hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c97b6-110">When you create a reference cell by using the `ref` operator, you create a copy of the underlying value as an encapsulated mutable value.</span></span>

<span data-ttu-id="c97b6-111">Že přestoupíte odkazové buňky pomocí `!` – operátor (vykřičník).</span><span class="sxs-lookup"><span data-stu-id="c97b6-111">You can dereference a reference cell by using the `!` (bang) operator.</span></span>

<span data-ttu-id="c97b6-112">Následující příklad kódu znázorňuje deklaraci a použití odkazových buněk.</span><span class="sxs-lookup"><span data-stu-id="c97b6-112">The following code example illustrates the declaration and use of reference cells.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

<span data-ttu-id="c97b6-113">Výstup je `50`.</span><span class="sxs-lookup"><span data-stu-id="c97b6-113">The output is `50`.</span></span>

<span data-ttu-id="c97b6-114">Odkazové buňky jsou instance `Ref` generického typu záznamu, který je deklarován následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="c97b6-114">Reference cells are instances of the `Ref` generic record type, which is declared as follows.</span></span>

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

<span data-ttu-id="c97b6-115">Typ `'a ref` je synonymum pro `Ref<'a>`.</span><span class="sxs-lookup"><span data-stu-id="c97b6-115">The type `'a ref` is a synonym for `Ref<'a>`.</span></span> <span data-ttu-id="c97b6-116">Kompilátor a technologie IntelliSense v integrovaném vývojovém prostředí zobrazují nejprve tento typ a následně zdrojovou definici.</span><span class="sxs-lookup"><span data-stu-id="c97b6-116">The compiler and IntelliSense in the IDE display the former for this type, but the underlying definition is the latter.</span></span>

<span data-ttu-id="c97b6-117">`ref` Operátor vytvoří novou odkazovou buňku.</span><span class="sxs-lookup"><span data-stu-id="c97b6-117">The `ref` operator creates a new reference cell.</span></span> <span data-ttu-id="c97b6-118">Následující kód je deklarace `ref` operátor.</span><span class="sxs-lookup"><span data-stu-id="c97b6-118">The following code is the declaration of the `ref` operator.</span></span>

```fsharp
let ref x = { contents = x }
```

<span data-ttu-id="c97b6-119">V následující tabulce jsou uvedeny funkce, které jsou u odkazové buňky dostupné.</span><span class="sxs-lookup"><span data-stu-id="c97b6-119">The following table shows the features that are available on the reference cell.</span></span>

|<span data-ttu-id="c97b6-120">Operátor, člen nebo pole</span><span class="sxs-lookup"><span data-stu-id="c97b6-120">Operator, member, or field</span></span>|<span data-ttu-id="c97b6-121">Popis</span><span class="sxs-lookup"><span data-stu-id="c97b6-121">Description</span></span>|<span data-ttu-id="c97b6-122">Typ</span><span class="sxs-lookup"><span data-stu-id="c97b6-122">Type</span></span>|<span data-ttu-id="c97b6-123">Definice</span><span class="sxs-lookup"><span data-stu-id="c97b6-123">Definition</span></span>|
|--------------------------|-----------|----|----------|
|<span data-ttu-id="c97b6-124">`!` (operátor zrušení odkazu)</span><span class="sxs-lookup"><span data-stu-id="c97b6-124">`!` (dereference operator)</span></span>|<span data-ttu-id="c97b6-125">Vrátí zdrojovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c97b6-125">Returns the underlying value.</span></span>|`'a ref -> 'a`|`let (!) r = r.contents`|
|<span data-ttu-id="c97b6-126">`:=` (operátor přiřazení)</span><span class="sxs-lookup"><span data-stu-id="c97b6-126">`:=` (assignment operator)</span></span>|<span data-ttu-id="c97b6-127">Změní zdrojovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c97b6-127">Changes the underlying value.</span></span>|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|<span data-ttu-id="c97b6-128">`ref` (operátor)</span><span class="sxs-lookup"><span data-stu-id="c97b6-128">`ref` (operator)</span></span>|<span data-ttu-id="c97b6-129">Zapouzdří hodnotu do nové odkazové buňky.</span><span class="sxs-lookup"><span data-stu-id="c97b6-129">Encapsulates a value into a new reference cell.</span></span>|`'a -> 'a ref`|`let ref x = { contents = x }`|
|<span data-ttu-id="c97b6-130">`Value` (vlastnost)</span><span class="sxs-lookup"><span data-stu-id="c97b6-130">`Value` (property)</span></span>|<span data-ttu-id="c97b6-131">Získá nebo nastaví zdrojovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c97b6-131">Gets or sets the underlying value.</span></span>|`unit -> 'a`|`member x.Value = x.contents`|
|<span data-ttu-id="c97b6-132">`contents` (pole záznamu)</span><span class="sxs-lookup"><span data-stu-id="c97b6-132">`contents` (record field)</span></span>|<span data-ttu-id="c97b6-133">Získá nebo nastaví zdrojovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c97b6-133">Gets or sets the underlying value.</span></span>|`'a`|`let ref x = { contents = x }`|
<span data-ttu-id="c97b6-134">Ke zdrojové hodnotě lze získat přístup několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="c97b6-134">There are several ways to access the underlying value.</span></span> <span data-ttu-id="c97b6-135">Hodnota vrácená operátorem zrušení odkazu (`!`) není Přiřaditelná.</span><span class="sxs-lookup"><span data-stu-id="c97b6-135">The value returned by the dereference operator (`!`) is not an assignable value.</span></span> <span data-ttu-id="c97b6-136">Proto se při změně zdrojové hodnoty, musíte použít operátor přiřazení (`:=`) místo toho.</span><span class="sxs-lookup"><span data-stu-id="c97b6-136">Therefore, if you are modifying the underlying value, you must use the assignment operator (`:=`) instead.</span></span>

<span data-ttu-id="c97b6-137">Oba `Value` vlastnost a `contents` pole jsou Přiřaditelné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c97b6-137">Both the `Value` property and the `contents` field are assignable values.</span></span> <span data-ttu-id="c97b6-138">Můžete je proto použít ke zpřístupnění nebo změně zdrojové hodnoty, jak znázorňuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="c97b6-138">Therefore, you can use these to either access or change the underlying value, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

<span data-ttu-id="c97b6-139">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="c97b6-139">The output is as follows.</span></span>

```
10
10
11
12
```

<span data-ttu-id="c97b6-140">Pole `contents` zajišťuje kompatibilitu s jinými verzemi ML a během kompilace zobrazí upozornění.</span><span class="sxs-lookup"><span data-stu-id="c97b6-140">The field `contents` is provided for compatibility with other versions of ML and will produce a warning during compilation.</span></span> <span data-ttu-id="c97b6-141">Chcete-li toto upozornění zakážete, použijte `--mlcompatibility` – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="c97b6-141">To disable the warning, use the `--mlcompatibility` compiler option.</span></span> <span data-ttu-id="c97b6-142">Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="c97b6-142">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="c97b6-143">Následující kód znázorňuje použití odkazových buněk při předávání parametrů.</span><span class="sxs-lookup"><span data-stu-id="c97b6-143">The following code illustrates the use of reference cells in parameter passing.</span></span> <span data-ttu-id="c97b6-144">Typ Incrementor má metodu přírůstek, který přijímá parametr, který obsahuje v parametru typu byref.</span><span class="sxs-lookup"><span data-stu-id="c97b6-144">The Incrementor type has a method Increment that takes a parameter that includes byref in the parameter type.</span></span> <span data-ttu-id="c97b6-145">Byref v typu parametru označuje, že volající musejí předat odkazovou buňku nebo adresu typické proměnné zadaného typu, v tomto případu int. Zbývající kód znázorňuje, jak volat přírůstek s oběma těmito typy argumentů a ukazuje použití operátoru ref u proměnné vytvořit odkazovou buňku (ref myDelta1).</span><span class="sxs-lookup"><span data-stu-id="c97b6-145">The byref in the parameter type indicates that callers must pass a reference cell or the address of a typical variable of the specified type, in this case int. The remaining code illustrates how to call Increment with both of these types of arguments, and shows the use of the ref operator on a variable to create a reference cell (ref myDelta1).</span></span> <span data-ttu-id="c97b6-146">Pak znázorňuje použití operátoru address-of (&amp;) ke generování příslušného argumentu.</span><span class="sxs-lookup"><span data-stu-id="c97b6-146">It then shows the use of the address-of operator (&amp;) to generate an appropriate argument.</span></span> <span data-ttu-id="c97b6-147">Nakonec metoda Increment volána znovu pomocí odkazové buňky, která je deklarována pomocí vazby let.</span><span class="sxs-lookup"><span data-stu-id="c97b6-147">Finally, the Increment method is called again by using a reference cell that is declared by using a let binding.</span></span> <span data-ttu-id="c97b6-148">Poslední řádek kódu ukazuje použití!</span><span class="sxs-lookup"><span data-stu-id="c97b6-148">The final line of code demonstrates the use of the !</span></span> <span data-ttu-id="c97b6-149">operátor zrušení odkazu odkazové buňky pro tisk.</span><span class="sxs-lookup"><span data-stu-id="c97b6-149">operator to dereference the reference cell for printing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2204.fs)]

<span data-ttu-id="c97b6-150">Další informace o předávání pomocí odkazu naleznete v tématu [parametry a argumenty](parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="c97b6-150">For more information about how to pass by reference, see [Parameters and Arguments](parameters-and-arguments.md).</span></span>

>[!NOTE]
<span data-ttu-id="c97b6-151">Programátoři v C# měli vědět, že tento odkaz funguje jinak než v jazyce F # než v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="c97b6-151">C# programmers should know that ref works differently in F# than it does in C#.</span></span> <span data-ttu-id="c97b6-152">Například použití ref při předávání argumentu nemá stejný účinek v jazyce F # stejně jako v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="c97b6-152">For example, the use of ref when you pass an argument does not have the same effect in F# as it does in C#.</span></span>

>[!NOTE]
<span data-ttu-id="c97b6-153">`mutable` proměnné mohou být automaticky povýšen na `'a ref` nezachytává uzavření; naleznete v tématu [hodnoty](values/index.md).</span><span class="sxs-lookup"><span data-stu-id="c97b6-153">`mutable` variables may be automatically promoted to `'a ref` if captured by a closure; see [Values](values/index.md).</span></span>

## <a name="consuming-c-ref-returns"></a><span data-ttu-id="c97b6-154">Přijímání C# `ref` vrátí</span><span class="sxs-lookup"><span data-stu-id="c97b6-154">Consuming C# `ref` returns</span></span>

<span data-ttu-id="c97b6-155">Od verze F # 4.1, můžete využívat `ref` vrátí vygenerované v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="c97b6-155">Starting with F# 4.1, you can consume `ref` returns generated in C#.</span></span>  <span data-ttu-id="c97b6-156">Výsledek volání `byref<_>` ukazatele.</span><span class="sxs-lookup"><span data-stu-id="c97b6-156">The result of such a call is a `byref<_>` pointer.</span></span>

<span data-ttu-id="c97b6-157">C# metodu:</span><span class="sxs-lookup"><span data-stu-id="c97b6-157">The following C# method:</span></span>

```csharp
namespace RefReturns
{
    public static class RefClass
    {
        public static ref int Find(int val, int[] vals)
        {
            for (int i = 0; i < vals.Length; i++)
            {
                if (vals[i] == val)
                {
                    return ref numbers[i]; // Returns the location, not the value
                }
            }

            throw new IndexOutOfRangeException($"{nameof(number)} not found");
        }
    }
}
```

<span data-ttu-id="c97b6-158">Je možné transparentně vyvolat v F # se žádná speciální syntax:</span><span class="sxs-lookup"><span data-stu-id="c97b6-158">Can be transparently called by F# with no special syntax:</span></span>

```fsharp
open RefReturns

let consumeRefReturn() =
    let result = RefClass.Find(3, [| 1; 2; 3; 4; 5 |]) // 'result' is of type 'byref<int>'.
    ()
```

<span data-ttu-id="c97b6-159">Můžete také deklarovat funkce, což může trvat `ref` vrátit jako vstup, například:</span><span class="sxs-lookup"><span data-stu-id="c97b6-159">You can also declare functions which could take a `ref` return as input, for example:</span></span>

```fsharp
let f (x: byref<int>) = &x
```

<span data-ttu-id="c97b6-160">Aktuálně neexistuje žádný způsob, jak vygenerovat `ref` vrácené v jazyce F #, která by mohla využívat v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="c97b6-160">There is currently no way to generate a `ref` return in F# which could be consumed in C#.</span></span>

## <a name="see-also"></a><span data-ttu-id="c97b6-161">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c97b6-161">See also</span></span>

- [<span data-ttu-id="c97b6-162">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="c97b6-162">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="c97b6-163">Parametry a argumenty</span><span class="sxs-lookup"><span data-stu-id="c97b6-163">Parameters and Arguments</span></span>](parameters-and-arguments.md)
- [<span data-ttu-id="c97b6-164">Referenční dokumentace symbolů a operátorů</span><span class="sxs-lookup"><span data-stu-id="c97b6-164">Symbol and Operator Reference</span></span>](symbol-and-operator-reference/index.md)
- [<span data-ttu-id="c97b6-165">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="c97b6-165">Values</span></span>](values/index.md)
