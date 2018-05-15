---
title: Referenční buňky (F#)
description: 'Zjistěte, jak referenční buňky F # jsou umístění úložiště, které vám umožní vytvořit měnitelný hodnoty s sémantiku odkaz.'
ms.date: 05/16/2016
ms.openlocfilehash: 3a632425356a250f07e5babd2751b9923eec6552
ms.sourcegitcommit: e5bb395ec86f536e114314184288f40a8c745e2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2018
---
# <a name="reference-cells"></a><span data-ttu-id="dabdd-103">Referenční buňky</span><span class="sxs-lookup"><span data-stu-id="dabdd-103">Reference Cells</span></span>

<span data-ttu-id="dabdd-104">*Referenční buňky* jsou umístění úložiště, které vám umožní vytvořit měnitelný hodnoty s sémantiku odkaz.</span><span class="sxs-lookup"><span data-stu-id="dabdd-104">*Reference cells* are storage locations that enable you to create mutable values with reference semantics.</span></span>

## <a name="syntax"></a><span data-ttu-id="dabdd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dabdd-105">Syntax</span></span>

```fsharp
ref expression
```

## <a name="remarks"></a><span data-ttu-id="dabdd-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dabdd-106">Remarks</span></span>
<span data-ttu-id="dabdd-107">Můžete použít `ref` operátor před hodnotu k vytvoření nové buňky odkaz, který zapouzdřuje hodnotu.</span><span class="sxs-lookup"><span data-stu-id="dabdd-107">You use the `ref` operator before a value to create a new reference cell that encapsulates the value.</span></span> <span data-ttu-id="dabdd-108">Zdrojovou hodnotu pak můžete změnit, protože je proměnlivá.</span><span class="sxs-lookup"><span data-stu-id="dabdd-108">You can then change the underlying value because it is mutable.</span></span>

<span data-ttu-id="dabdd-109">Odkazové buňky obsahují skutečnou hodnotu; není to pouze adresa.</span><span class="sxs-lookup"><span data-stu-id="dabdd-109">A reference cell holds an actual value; it is not just an address.</span></span> <span data-ttu-id="dabdd-110">Když vytvoříte odkaz na buňku pomocí `ref` operátor, vytvořit kopii základní hodnoty jako zapouzdřené měnitelný hodnota.</span><span class="sxs-lookup"><span data-stu-id="dabdd-110">When you create a reference cell by using the `ref` operator, you create a copy of the underlying value as an encapsulated mutable value.</span></span>

<span data-ttu-id="dabdd-111">Odkaz na buňku můžete dereference pomocí `!` operátor (vykřičník).</span><span class="sxs-lookup"><span data-stu-id="dabdd-111">You can dereference a reference cell by using the `!` (bang) operator.</span></span>

<span data-ttu-id="dabdd-112">Následující příklad kódu znázorňuje deklaraci a použití odkazových buněk.</span><span class="sxs-lookup"><span data-stu-id="dabdd-112">The following code example illustrates the declaration and use of reference cells.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

<span data-ttu-id="dabdd-113">Výstupem je `50`.</span><span class="sxs-lookup"><span data-stu-id="dabdd-113">The output is `50`.</span></span>

<span data-ttu-id="dabdd-114">Referenční buňky jsou instancemi třídy `Ref` typ obecné záznamu, který je deklarován následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="dabdd-114">Reference cells are instances of the `Ref` generic record type, which is declared as follows.</span></span>

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

<span data-ttu-id="dabdd-115">Typ `'a ref` se jedná o synonymum `Ref<'a>`.</span><span class="sxs-lookup"><span data-stu-id="dabdd-115">The type `'a ref` is a synonym for `Ref<'a>`.</span></span> <span data-ttu-id="dabdd-116">Kompilátor a technologie IntelliSense v integrovaném vývojovém prostředí zobrazují nejprve tento typ a následně zdrojovou definici.</span><span class="sxs-lookup"><span data-stu-id="dabdd-116">The compiler and IntelliSense in the IDE display the former for this type, but the underlying definition is the latter.</span></span>

<span data-ttu-id="dabdd-117">`ref` Operátor vytvoří nový odkaz na buňku.</span><span class="sxs-lookup"><span data-stu-id="dabdd-117">The `ref` operator creates a new reference cell.</span></span> <span data-ttu-id="dabdd-118">Následující kód je deklaraci `ref` operátor.</span><span class="sxs-lookup"><span data-stu-id="dabdd-118">The following code is the declaration of the `ref` operator.</span></span>

```fsharp
let ref x = { contents = x }
```

<span data-ttu-id="dabdd-119">V následující tabulce jsou uvedeny funkce, které jsou u odkazové buňky dostupné.</span><span class="sxs-lookup"><span data-stu-id="dabdd-119">The following table shows the features that are available on the reference cell.</span></span>

|<span data-ttu-id="dabdd-120">Operátor, člen nebo pole</span><span class="sxs-lookup"><span data-stu-id="dabdd-120">Operator, member, or field</span></span>|<span data-ttu-id="dabdd-121">Popis</span><span class="sxs-lookup"><span data-stu-id="dabdd-121">Description</span></span>|<span data-ttu-id="dabdd-122">Typ</span><span class="sxs-lookup"><span data-stu-id="dabdd-122">Type</span></span>|<span data-ttu-id="dabdd-123">Definice</span><span class="sxs-lookup"><span data-stu-id="dabdd-123">Definition</span></span>|
|--------------------------|-----------|----|----------|
|<span data-ttu-id="dabdd-124">`!` (operátoru zrušení)</span><span class="sxs-lookup"><span data-stu-id="dabdd-124">`!` (dereference operator)</span></span>|<span data-ttu-id="dabdd-125">Vrátí zdrojovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="dabdd-125">Returns the underlying value.</span></span>|`'a ref -> 'a`|`let (!) r = r.contents`|
|<span data-ttu-id="dabdd-126">`:=` (operátor přiřazení)</span><span class="sxs-lookup"><span data-stu-id="dabdd-126">`:=` (assignment operator)</span></span>|<span data-ttu-id="dabdd-127">Změní zdrojovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="dabdd-127">Changes the underlying value.</span></span>|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|<span data-ttu-id="dabdd-128">`ref` (operátor)</span><span class="sxs-lookup"><span data-stu-id="dabdd-128">`ref` (operator)</span></span>|<span data-ttu-id="dabdd-129">Zapouzdří hodnotu do nové odkazové buňky.</span><span class="sxs-lookup"><span data-stu-id="dabdd-129">Encapsulates a value into a new reference cell.</span></span>|`'a -> 'a ref`|`let ref x = { contents = x }`|
|<span data-ttu-id="dabdd-130">`Value` (vlastnost)</span><span class="sxs-lookup"><span data-stu-id="dabdd-130">`Value` (property)</span></span>|<span data-ttu-id="dabdd-131">Získá nebo nastaví zdrojovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="dabdd-131">Gets or sets the underlying value.</span></span>|`unit -> 'a`|`member x.Value = x.contents`|
|<span data-ttu-id="dabdd-132">`contents` (záznam pole)</span><span class="sxs-lookup"><span data-stu-id="dabdd-132">`contents` (record field)</span></span>|<span data-ttu-id="dabdd-133">Získá nebo nastaví zdrojovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="dabdd-133">Gets or sets the underlying value.</span></span>|`'a`|`let ref x = { contents = x }`|
<span data-ttu-id="dabdd-134">Ke zdrojové hodnotě lze získat přístup několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="dabdd-134">There are several ways to access the underlying value.</span></span> <span data-ttu-id="dabdd-135">Hodnota vrácená operátorem dereference (`!`) není přiřadit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="dabdd-135">The value returned by the dereference operator (`!`) is not an assignable value.</span></span> <span data-ttu-id="dabdd-136">Proto pokud měníte základní hodnotu, musíte použít operátor přiřazení (`:=`) místo.</span><span class="sxs-lookup"><span data-stu-id="dabdd-136">Therefore, if you are modifying the underlying value, you must use the assignment operator (`:=`) instead.</span></span>

<span data-ttu-id="dabdd-137">Obě `Value` vlastnost a `contents` pole jsou Přiřaditelné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="dabdd-137">Both the `Value` property and the `contents` field are assignable values.</span></span> <span data-ttu-id="dabdd-138">Můžete je proto použít ke zpřístupnění nebo změně zdrojové hodnoty, jak znázorňuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="dabdd-138">Therefore, you can use these to either access or change the underlying value, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

<span data-ttu-id="dabdd-139">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="dabdd-139">The output is as follows.</span></span>

```
10
10
11
12
```

<span data-ttu-id="dabdd-140">Pole `contents` zajišťuje kompatibilitu s jinými verzemi ML a vygeneruje upozornění během kompilace.</span><span class="sxs-lookup"><span data-stu-id="dabdd-140">The field `contents` is provided for compatibility with other versions of ML and will produce a warning during compilation.</span></span> <span data-ttu-id="dabdd-141">Chcete-li zakázat upozornění, použijte `--mlcompatibility` – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="dabdd-141">To disable the warning, use the `--mlcompatibility` compiler option.</span></span> <span data-ttu-id="dabdd-142">Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="dabdd-142">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="dabdd-143">Následující kód znázorňuje použití odkazových buněk při předávání parametrů.</span><span class="sxs-lookup"><span data-stu-id="dabdd-143">The following code illustrates the use of reference cells in parameter passing.</span></span> <span data-ttu-id="dabdd-144">Typ Incrementor má metoda přírůstek, která přebírá parametr, který obsahuje byref typ parametru.</span><span class="sxs-lookup"><span data-stu-id="dabdd-144">The Incrementor type has a method Increment that takes a parameter that includes byref in the parameter type.</span></span> <span data-ttu-id="dabdd-145">Byref v parametru typu označuje, že volající musí projít odkaz na buňku nebo adresu typické proměnné zadaného typu, v této případu int. Zbývající kód ukazuje, jak volat přírůstek s oběma typy argumentů a ukazuje použití operátoru ref na proměnnou, do které vytvořit odkaz na buňku (ref myDelta1).</span><span class="sxs-lookup"><span data-stu-id="dabdd-145">The byref in the parameter type indicates that callers must pass a reference cell or the address of a typical variable of the specified type, in this case int. The remaining code illustrates how to call Increment with both of these types of arguments, and shows the use of the ref operator on a variable to create a reference cell (ref myDelta1).</span></span> <span data-ttu-id="dabdd-146">Potom ukazuje použití address-of – operátor (&amp;) ke generování odpovídající argument.</span><span class="sxs-lookup"><span data-stu-id="dabdd-146">It then shows the use of the address-of operator (&amp;) to generate an appropriate argument.</span></span> <span data-ttu-id="dabdd-147">Nakonec přírůstek je volání metody znovu pomocí odkaz na buňku, která je deklarovaná použití umožňují vazby.</span><span class="sxs-lookup"><span data-stu-id="dabdd-147">Finally, the Increment method is called again by using a reference cell that is declared by using a let binding.</span></span> <span data-ttu-id="dabdd-148">Poslední řádek kódu demonstruje použití!</span><span class="sxs-lookup"><span data-stu-id="dabdd-148">The final line of code demonstrates the use of the !</span></span> <span data-ttu-id="dabdd-149">operátor pro dereference – odkaz na buňku pro tisk.</span><span class="sxs-lookup"><span data-stu-id="dabdd-149">operator to dereference the reference cell for printing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2204.fs)]

<span data-ttu-id="dabdd-150">Další informace o tom, jak předat odkazem najdete v tématu [parametry a argumenty](parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="dabdd-150">For more information about how to pass by reference, see [Parameters and Arguments](parameters-and-arguments.md).</span></span>

>[!NOTE]
<span data-ttu-id="dabdd-151">Programátory v jazyce C# měli vědět, že tento ref funguje jinak v jazyce F # než v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="dabdd-151">C# programmers should know that ref works differently in F# than it does in C#.</span></span> <span data-ttu-id="dabdd-152">Například použití ref při předání argumentu nemá stejného efektu v jazyce F # stejně jako v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="dabdd-152">For example, the use of ref when you pass an argument does not have the same effect in F# as it does in C#.</span></span>

>[!NOTE]
<span data-ttu-id="dabdd-153">`mutable` proměnné mohou být automaticky povýšen na `'a ref` zachycenou uzavření; najdete v části [hodnoty](values/index.md).</span><span class="sxs-lookup"><span data-stu-id="dabdd-153">`mutable` variables may be automatically promoted to `'a ref` if captured by a closure; see [Values](values/index.md).</span></span>

## <a name="consuming-c-ref-returns"></a><span data-ttu-id="dabdd-154">Přijímání C# `ref` vrátí</span><span class="sxs-lookup"><span data-stu-id="dabdd-154">Consuming C# `ref` returns</span></span>

<span data-ttu-id="dabdd-155">Od verze 4.1 F #, můžete využívat `ref` vrátí vygenerované v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="dabdd-155">Starting with F# 4.1, you can consume `ref` returns generated in C#.</span></span>  <span data-ttu-id="dabdd-156">Výsledkem volání je `byref<_>` ukazatel.</span><span class="sxs-lookup"><span data-stu-id="dabdd-156">The result of such a call is a `byref<_>` pointer.</span></span>

<span data-ttu-id="dabdd-157">C# metodu:</span><span class="sxs-lookup"><span data-stu-id="dabdd-157">The following C# method:</span></span>

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

<span data-ttu-id="dabdd-158">Je možné transparentně volat v F # se žádné speciální syntaxí:</span><span class="sxs-lookup"><span data-stu-id="dabdd-158">Can be transparently called by F# with no special syntax:</span></span>

```fsharp
open RefReturns

let consumeRefReturn() =
    let result = RefClass.Find(3, [| 1; 2; 3; 4; 5 |]) // 'result' is of type 'byref<int>'.
    ()
```

<span data-ttu-id="dabdd-159">Můžete také deklarovat funkce, které může trvat `ref` vrátit jako vstup, například:</span><span class="sxs-lookup"><span data-stu-id="dabdd-159">You can also declare functions which could take a `ref` return as input, for example:</span></span>

```fsharp
let f (x: byref<int>) = &x
```

<span data-ttu-id="dabdd-160">Aktuálně neexistuje žádný způsob, jak vygenerovat `ref` návratový v jazyce F # které by mohly spotřebovat v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="dabdd-160">There is currently no way to generate a `ref` return in F# which could be consumed in C#.</span></span>

## <a name="see-also"></a><span data-ttu-id="dabdd-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="dabdd-161">See Also</span></span>
[<span data-ttu-id="dabdd-162">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="dabdd-162">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="dabdd-163">Parametry a argumenty</span><span class="sxs-lookup"><span data-stu-id="dabdd-163">Parameters and Arguments</span></span>](parameters-and-arguments.md)

[<span data-ttu-id="dabdd-164">Referenční dokumentace symbolů a operátorů</span><span class="sxs-lookup"><span data-stu-id="dabdd-164">Symbol and Operator Reference</span></span>](symbol-and-operator-reference/index.md)

[<span data-ttu-id="dabdd-165">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="dabdd-165">Values</span></span>](values/index.md)
