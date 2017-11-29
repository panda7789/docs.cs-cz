---
title: "Referenční buňky (F#)"
description: "Zjistěte, jak referenční buňky F # jsou umístění úložiště, které vám umožní vytvořit měnitelný hodnoty s sémantiku odkaz."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 09a0b221-ea21-45c4-bae8-5e4a339750c4
ms.openlocfilehash: c7470c9a36cf2cd24dd89ceffcf6e90c6dc4d2dd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="reference-cells"></a><span data-ttu-id="090e8-104">Referenční buňky</span><span class="sxs-lookup"><span data-stu-id="090e8-104">Reference Cells</span></span>

<span data-ttu-id="090e8-105">*Referenční buňky* jsou umístění úložiště, které vám umožní vytvořit měnitelný hodnoty s sémantiku odkaz.</span><span class="sxs-lookup"><span data-stu-id="090e8-105">*Reference cells* are storage locations that enable you to create mutable values with reference semantics.</span></span>

## <a name="syntax"></a><span data-ttu-id="090e8-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="090e8-106">Syntax</span></span>

```fsharp
ref expression
```

## <a name="remarks"></a><span data-ttu-id="090e8-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="090e8-107">Remarks</span></span>
<span data-ttu-id="090e8-108">Můžete použít `ref` operátor před hodnotu k vytvoření nové buňky odkaz, který zapouzdřuje hodnotu.</span><span class="sxs-lookup"><span data-stu-id="090e8-108">You use the `ref` operator before a value to create a new reference cell that encapsulates the value.</span></span> <span data-ttu-id="090e8-109">Zdrojovou hodnotu pak můžete změnit, protože je proměnlivá.</span><span class="sxs-lookup"><span data-stu-id="090e8-109">You can then change the underlying value because it is mutable.</span></span>

<span data-ttu-id="090e8-110">Odkazové buňky obsahují skutečnou hodnotu; není to pouze adresa.</span><span class="sxs-lookup"><span data-stu-id="090e8-110">A reference cell holds an actual value; it is not just an address.</span></span> <span data-ttu-id="090e8-111">Když vytvoříte odkaz na buňku pomocí `ref` operátor, vytvořit kopii základní hodnoty jako zapouzdřené měnitelný hodnota.</span><span class="sxs-lookup"><span data-stu-id="090e8-111">When you create a reference cell by using the `ref` operator, you create a copy of the underlying value as an encapsulated mutable value.</span></span>

<span data-ttu-id="090e8-112">Odkaz na buňku můžete dereference pomocí `!` operátor (vykřičník).</span><span class="sxs-lookup"><span data-stu-id="090e8-112">You can dereference a reference cell by using the `!` (bang) operator.</span></span>

<span data-ttu-id="090e8-113">Následující příklad kódu znázorňuje deklaraci a použití odkazových buněk.</span><span class="sxs-lookup"><span data-stu-id="090e8-113">The following code example illustrates the declaration and use of reference cells.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

<span data-ttu-id="090e8-114">Výstupem je `50`.</span><span class="sxs-lookup"><span data-stu-id="090e8-114">The output is `50`.</span></span>

<span data-ttu-id="090e8-115">Referenční buňky jsou instancemi třídy `Ref` typ obecné záznamu, který je deklarován následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="090e8-115">Reference cells are instances of the `Ref` generic record type, which is declared as follows.</span></span>

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

<span data-ttu-id="090e8-116">Typ `'a ref` se jedná o synonymum `Ref<'a>`.</span><span class="sxs-lookup"><span data-stu-id="090e8-116">The type `'a ref` is a synonym for `Ref<'a>`.</span></span> <span data-ttu-id="090e8-117">Kompilátor a technologie IntelliSense v integrovaném vývojovém prostředí zobrazují nejprve tento typ a následně zdrojovou definici.</span><span class="sxs-lookup"><span data-stu-id="090e8-117">The compiler and IntelliSense in the IDE display the former for this type, but the underlying definition is the latter.</span></span>

<span data-ttu-id="090e8-118">`ref` Operátor vytvoří nový odkaz na buňku.</span><span class="sxs-lookup"><span data-stu-id="090e8-118">The `ref` operator creates a new reference cell.</span></span> <span data-ttu-id="090e8-119">Následující kód je deklaraci `ref` operátor.</span><span class="sxs-lookup"><span data-stu-id="090e8-119">The following code is the declaration of the `ref` operator.</span></span>

```fsharp
let ref x = { contents = x }
```

<span data-ttu-id="090e8-120">V následující tabulce jsou uvedeny funkce, které jsou u odkazové buňky dostupné.</span><span class="sxs-lookup"><span data-stu-id="090e8-120">The following table shows the features that are available on the reference cell.</span></span>

|<span data-ttu-id="090e8-121">Operátor, člen nebo pole</span><span class="sxs-lookup"><span data-stu-id="090e8-121">Operator, member, or field</span></span>|<span data-ttu-id="090e8-122">Popis</span><span class="sxs-lookup"><span data-stu-id="090e8-122">Description</span></span>|<span data-ttu-id="090e8-123">Typ</span><span class="sxs-lookup"><span data-stu-id="090e8-123">Type</span></span>|<span data-ttu-id="090e8-124">Definice</span><span class="sxs-lookup"><span data-stu-id="090e8-124">Definition</span></span>|
|--------------------------|-----------|----|----------|
|<span data-ttu-id="090e8-125">`!`(operátoru zrušení)</span><span class="sxs-lookup"><span data-stu-id="090e8-125">`!` (dereference operator)</span></span>|<span data-ttu-id="090e8-126">Vrátí zdrojovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="090e8-126">Returns the underlying value.</span></span>|`'a ref -> 'a`|`let (!) r = r.contents`|
|<span data-ttu-id="090e8-127">`:=`(operátor přiřazení)</span><span class="sxs-lookup"><span data-stu-id="090e8-127">`:=` (assignment operator)</span></span>|<span data-ttu-id="090e8-128">Změní zdrojovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="090e8-128">Changes the underlying value.</span></span>|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|<span data-ttu-id="090e8-129">`ref`(operátor)</span><span class="sxs-lookup"><span data-stu-id="090e8-129">`ref` (operator)</span></span>|<span data-ttu-id="090e8-130">Zapouzdří hodnotu do nové odkazové buňky.</span><span class="sxs-lookup"><span data-stu-id="090e8-130">Encapsulates a value into a new reference cell.</span></span>|`'a -> 'a ref`|`let ref x = { contents = x }`|
|<span data-ttu-id="090e8-131">`Value`(vlastnost)</span><span class="sxs-lookup"><span data-stu-id="090e8-131">`Value` (property)</span></span>|<span data-ttu-id="090e8-132">Získá nebo nastaví zdrojovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="090e8-132">Gets or sets the underlying value.</span></span>|`unit -> 'a`|`member x.Value = x.contents`|
|<span data-ttu-id="090e8-133">`contents`(záznam pole)</span><span class="sxs-lookup"><span data-stu-id="090e8-133">`contents` (record field)</span></span>|<span data-ttu-id="090e8-134">Získá nebo nastaví zdrojovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="090e8-134">Gets or sets the underlying value.</span></span>|`'a`|`let ref x = { contents = x }`|
<span data-ttu-id="090e8-135">Ke zdrojové hodnotě lze získat přístup několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="090e8-135">There are several ways to access the underlying value.</span></span> <span data-ttu-id="090e8-136">Hodnota vrácená operátorem dereference (`!`) není přiřadit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="090e8-136">The value returned by the dereference operator (`!`) is not an assignable value.</span></span> <span data-ttu-id="090e8-137">Proto pokud měníte základní hodnotu, musíte použít operátor přiřazení (`:=`) místo.</span><span class="sxs-lookup"><span data-stu-id="090e8-137">Therefore, if you are modifying the underlying value, you must use the assignment operator (`:=`) instead.</span></span>

<span data-ttu-id="090e8-138">Obě `Value` vlastnost a `contents` pole jsou Přiřaditelné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="090e8-138">Both the `Value` property and the `contents` field are assignable values.</span></span> <span data-ttu-id="090e8-139">Můžete je proto použít ke zpřístupnění nebo změně zdrojové hodnoty, jak znázorňuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="090e8-139">Therefore, you can use these to either access or change the underlying value, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

<span data-ttu-id="090e8-140">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="090e8-140">The output is as follows.</span></span>

```
10
10
11
12
```

<span data-ttu-id="090e8-141">Pole `contents` zajišťuje kompatibilitu s jinými verzemi ML a vygeneruje upozornění během kompilace.</span><span class="sxs-lookup"><span data-stu-id="090e8-141">The field `contents` is provided for compatibility with other versions of ML and will produce a warning during compilation.</span></span> <span data-ttu-id="090e8-142">Chcete-li zakázat upozornění, použijte `--mlcompatibility` – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="090e8-142">To disable the warning, use the `--mlcompatibility` compiler option.</span></span> <span data-ttu-id="090e8-143">Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="090e8-143">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="090e8-144">Následující kód znázorňuje použití odkazových buněk při předávání parametrů.</span><span class="sxs-lookup"><span data-stu-id="090e8-144">The following code illustrates the use of reference cells in parameter passing.</span></span> <span data-ttu-id="090e8-145">Typ Incrementor má metoda přírůstek, která přebírá parametr, který obsahuje byref typ parametru.</span><span class="sxs-lookup"><span data-stu-id="090e8-145">The Incrementor type has a method Increment that takes a parameter that includes byref in the parameter type.</span></span> <span data-ttu-id="090e8-146">Byref v parametru typu označuje, že volající musí projít odkaz na buňku nebo adresu typické proměnné zadaného typu, v této případu int. Zbývající kód ukazuje, jak volat přírůstek s oběma typy argumentů a ukazuje použití operátoru ref na proměnnou, do které vytvořit odkaz na buňku (ref myDelta1).</span><span class="sxs-lookup"><span data-stu-id="090e8-146">The byref in the parameter type indicates that callers must pass a reference cell or the address of a typical variable of the specified type, in this case int. The remaining code illustrates how to call Increment with both of these types of arguments, and shows the use of the ref operator on a variable to create a reference cell (ref myDelta1).</span></span> <span data-ttu-id="090e8-147">Potom ukazuje použití address-of – operátor (&amp;) ke generování odpovídající argument.</span><span class="sxs-lookup"><span data-stu-id="090e8-147">It then shows the use of the address-of operator (&amp;) to generate an appropriate argument.</span></span> <span data-ttu-id="090e8-148">Nakonec přírůstek je volání metody znovu pomocí odkaz na buňku, která je deklarovaná použití umožňují vazby.</span><span class="sxs-lookup"><span data-stu-id="090e8-148">Finally, the Increment method is called again by using a reference cell that is declared by using a let binding.</span></span> <span data-ttu-id="090e8-149">Poslední řádek kódu demonstruje použití!</span><span class="sxs-lookup"><span data-stu-id="090e8-149">The final line of code demonstrates the use of the !</span></span> <span data-ttu-id="090e8-150">operátor pro dereference – odkaz na buňku pro tisk.</span><span class="sxs-lookup"><span data-stu-id="090e8-150">operator to dereference the reference cell for printing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2204.fs)]

<span data-ttu-id="090e8-151">Další informace o tom, jak předat odkazem najdete v tématu [parametry a argumenty](parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="090e8-151">For more information about how to pass by reference, see [Parameters and Arguments](parameters-and-arguments.md).</span></span>

>[!NOTE]
<span data-ttu-id="090e8-152">Programátory v jazyce C# měli vědět, že tento ref funguje jinak v jazyce F # než v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="090e8-152">C# programmers should know that ref works differently in F# than it does in C#.</span></span> <span data-ttu-id="090e8-153">Například použití ref při předání argumentu nemá stejného efektu v jazyce F # stejně jako v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="090e8-153">For example, the use of ref when you pass an argument does not have the same effect in F# as it does in C#.</span></span>

## <a name="consuming-c-ref-returns"></a><span data-ttu-id="090e8-154">Přijímání C# `ref` vrátí</span><span class="sxs-lookup"><span data-stu-id="090e8-154">Consuming C# `ref` returns</span></span>

<span data-ttu-id="090e8-155">Od verze 4.1 F #, můžete využívat `ref` vrátí vygenerované v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="090e8-155">Starting with F# 4.1, you can consume `ref` returns generated in C#.</span></span>  <span data-ttu-id="090e8-156">Výsledkem volání je `byref<_>` ukazatel.</span><span class="sxs-lookup"><span data-stu-id="090e8-156">The result of such a call is a `byref<_>` pointer.</span></span>

<span data-ttu-id="090e8-157">C# metodu:</span><span class="sxs-lookup"><span data-stu-id="090e8-157">The following C# method:</span></span>

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

<span data-ttu-id="090e8-158">Je možné transparentně volat v F # se žádné speciální syntaxí:</span><span class="sxs-lookup"><span data-stu-id="090e8-158">Can be transparently called by F# with no special syntax:</span></span>

```fsharp
open RefReturns

let consumeRefReturn() =
    let result = RefClass.Find(3, [| 1; 2; 3; 4; 5 |]) // 'result' is of type 'byref<int>'.
    ()
```

<span data-ttu-id="090e8-159">Můžete také deklarovat funkce, které může trvat `ref` vrátit jako vstup, například:</span><span class="sxs-lookup"><span data-stu-id="090e8-159">You can also declare functions which could take a `ref` return as input, for example:</span></span>

```fsharp
let f (x: byref<int>) = &x
```

<span data-ttu-id="090e8-160">Aktuálně neexistuje žádný způsob, jak vygenerovat `ref` návratový v jazyce F # které by mohly spotřebovat v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="090e8-160">There is currently no way to generate a `ref` return in F# which could be consumed in C#.</span></span>

## <a name="see-also"></a><span data-ttu-id="090e8-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="090e8-161">See Also</span></span>
[<span data-ttu-id="090e8-162">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="090e8-162">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="090e8-163">Parametry a argumenty</span><span class="sxs-lookup"><span data-stu-id="090e8-163">Parameters and Arguments</span></span>](parameters-and-arguments.md)

[<span data-ttu-id="090e8-164">Operátor referenční dokumentace symbolů a</span><span class="sxs-lookup"><span data-stu-id="090e8-164">Symbol and Operator Reference</span></span>](symbol-and-operator-reference/index.md)
