---
title: Formátování prostého textu
description: 'Naučte se používat printf a jiné formátování prostého textu v aplikacích a skriptech F #.'
ms.date: 07/22/2020
ms.openlocfilehash: 90a861736dae69dfbc199a19e24f587c42404737
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063780"
---
# <a name="plain-text-formatting"></a><span data-ttu-id="41a11-103">Formátování prostého textu</span><span class="sxs-lookup"><span data-stu-id="41a11-103">Plain text formatting</span></span>

<span data-ttu-id="41a11-104">Jazyk F # podporuje formátování prostého textu se zaškrtnutým typem `printf` , a to pomocí `printfn` souvisejících funkcí,, `sprintf` a.</span><span class="sxs-lookup"><span data-stu-id="41a11-104">F# supports type-checked formatting of plain text using `printf`, `printfn`, `sprintf`, and related functions.</span></span>
<span data-ttu-id="41a11-105">Příklad:</span><span class="sxs-lookup"><span data-stu-id="41a11-105">For example,</span></span>

```console
dotnet fsi

> printfn "Hello %s, %d + %d is %d" "world" 2 2 (2+2);;
```

<span data-ttu-id="41a11-106">poskytne výstup</span><span class="sxs-lookup"><span data-stu-id="41a11-106">gives the output</span></span>

```fsharp
Hello world, 2 + 2 is 4
```

<span data-ttu-id="41a11-107">Jazyk F # také umožňuje formátování strukturovaných hodnot jako prostý text.</span><span class="sxs-lookup"><span data-stu-id="41a11-107">F# also allows structured values to be formatted as plain text.</span></span>
<span data-ttu-id="41a11-108">Zvažte například následující příklad, který formátuje výstup jako zobrazení řazených kolekcí členů jako matice.</span><span class="sxs-lookup"><span data-stu-id="41a11-108">For example, consider the following example that formats the output as a matrix-like display of tuples.</span></span>

```console
dotnet fsi

> printfn "%A" [ for i in 1 .. 5 -> [ for j in 1 .. 5 -> (i, j) ] ];;

[[(1, 1); (1, 2); (1, 3); (1, 4); (1, 5)];
 [(2, 1); (2, 2); (2, 3); (2, 4); (2, 5)];
 [(3, 1); (3, 2); (3, 3); (3, 4); (3, 5)];
 [(4, 1); (4, 2); (4, 3); (4, 4); (4, 5)];
 [(5, 1); (5, 2); (5, 3); (5, 4); (5, 5)]]
```

<span data-ttu-id="41a11-109">Strukturované formátování prostého textu je aktivováno při použití `%A` formátu při `printf` formátování řetězců.</span><span class="sxs-lookup"><span data-stu-id="41a11-109">Structured plain text formatting is activated when you use the `%A` format in `printf` formatting strings.</span></span>
<span data-ttu-id="41a11-110">Aktivuje se také při formátování výstupu hodnot v F # Interactive, kde výstup zahrnuje další informace a je navíc přizpůsobitelná.</span><span class="sxs-lookup"><span data-stu-id="41a11-110">It's also activated when formatting the output of values in F# interactive, where the output includes extra information and is additionally customizable.</span></span>
<span data-ttu-id="41a11-111">Formátování prostého textu je také možné pozorovat prostřednictvím jakýchkoli volání `x.ToString()` na základě sjednocení F # a záznamů, včetně těch, které se vyskytují implicitně v ladění, protokolování a dalších nástrojích.</span><span class="sxs-lookup"><span data-stu-id="41a11-111">Plain text formatting is also observable through any calls to `x.ToString()` on F# union and record values, including those that occur implicitly in debugging, logging, and other tooling.</span></span>

## <a name="checking-of-printf-format-strings"></a><span data-ttu-id="41a11-112">Kontrola `printf` formátovacích řetězců</span><span class="sxs-lookup"><span data-stu-id="41a11-112">Checking of `printf`-format strings</span></span>

<span data-ttu-id="41a11-113">Pokud `printf` se funkce formátování používá s argumentem, který se neshoduje s specifikátory formátu printf ve formátu řetězce, bude zaznamenána chyba při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="41a11-113">A compile-time error will be reported if a `printf` formatting function is used with an argument that doesn't match the printf format specifiers in the format string.</span></span>  <span data-ttu-id="41a11-114">Příklad:</span><span class="sxs-lookup"><span data-stu-id="41a11-114">For example,</span></span>

```fsharp
sprintf "Hello %s" (2+2)
```

<span data-ttu-id="41a11-115">poskytne výstup</span><span class="sxs-lookup"><span data-stu-id="41a11-115">gives the output</span></span>

```console
  sprintf "Hello %s" (2+2)
  ----------------------^

stdin(3,25): error FS0001: The type 'string' does not match the type 'int'
```

<span data-ttu-id="41a11-116">Technicky řečeno, při použití `printf` a dalších souvisejících funkcích kontroluje zvláštní pravidlo v kompilátoru F # řetězcový literál předaný jako formátovací řetězec, který zajišťuje, že následné použité argumenty jsou správného typu, aby se shodovaly s použitými specifikátory formátu.</span><span class="sxs-lookup"><span data-stu-id="41a11-116">Technically speaking, when using `printf` and other related functions, a special rule in the F# compiler checks the string literal passed as the format string, ensuring the subsequent arguments applied are of the correct type to match the format specifiers used.</span></span>

## <a name="format-specifiers-for-printf"></a><span data-ttu-id="41a11-117">Specifikátory formátu pro`printf`</span><span class="sxs-lookup"><span data-stu-id="41a11-117">Format specifiers for `printf`</span></span>

<span data-ttu-id="41a11-118">Specifikace formátu pro `printf` formáty jsou řetězce se `%` značkami, které označují formát.</span><span class="sxs-lookup"><span data-stu-id="41a11-118">Format specifications for `printf` formats are strings with `%` markers that indicate format.</span></span> <span data-ttu-id="41a11-119">Zástupné symboly formátu `%[flags][width][.precision][type]` se skládají z místa, kde je typ interpretován takto:</span><span class="sxs-lookup"><span data-stu-id="41a11-119">Format placeholders consist of `%[flags][width][.precision][type]` where the type is interpreted as follows:</span></span>

| <span data-ttu-id="41a11-120">Specifikátor formátu</span><span class="sxs-lookup"><span data-stu-id="41a11-120">Format specifier</span></span>   | <span data-ttu-id="41a11-121">Typ (y)</span><span class="sxs-lookup"><span data-stu-id="41a11-121">Type(s)</span></span>        | <span data-ttu-id="41a11-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="41a11-122">Remarks</span></span>                      |
|:-------------------|:---------------|:-----------------------------|
| `%b`               | <span data-ttu-id="41a11-123">bool</span><span class="sxs-lookup"><span data-stu-id="41a11-123">bool</span></span>      | <span data-ttu-id="41a11-124">Formátováno jako `true` nebo`false`</span><span class="sxs-lookup"><span data-stu-id="41a11-124">Formatted as `true` or `false`</span></span>                |
| `%s`               | <span data-ttu-id="41a11-125">řetězec</span><span class="sxs-lookup"><span data-stu-id="41a11-125">string</span></span>    | <span data-ttu-id="41a11-126">Formátováno jako jeho neřídicí obsah</span><span class="sxs-lookup"><span data-stu-id="41a11-126">Formatted as its unescaped contents</span></span>         |
| `%c`               | <span data-ttu-id="41a11-127">char</span><span class="sxs-lookup"><span data-stu-id="41a11-127">char</span></span>      | <span data-ttu-id="41a11-128">Formátováno jako znakový literál</span><span class="sxs-lookup"><span data-stu-id="41a11-128">Formatted as the character literal</span></span>  |
| <span data-ttu-id="41a11-129">`%d`, `%i`</span><span class="sxs-lookup"><span data-stu-id="41a11-129">`%d`, `%i`</span></span>         | <span data-ttu-id="41a11-130">základní celočíselný typ</span><span class="sxs-lookup"><span data-stu-id="41a11-130">a basic integer type</span></span> | <span data-ttu-id="41a11-131">Formátováno jako desítkové celé číslo, podepsané, pokud je základní celočíselný typ podepsán</span><span class="sxs-lookup"><span data-stu-id="41a11-131">Formatted as a decimal integer, signed if the basic integer type is signed</span></span> |
| `%u`               | <span data-ttu-id="41a11-132">základní celočíselný typ</span><span class="sxs-lookup"><span data-stu-id="41a11-132">a basic integer type</span></span> | <span data-ttu-id="41a11-133">Formátováno jako desítkové celé číslo bez znaménka</span><span class="sxs-lookup"><span data-stu-id="41a11-133">Formatted as an unsigned decimal integer</span></span>   |
| <span data-ttu-id="41a11-134">`%x`, `%X`</span><span class="sxs-lookup"><span data-stu-id="41a11-134">`%x`, `%X`</span></span>         | <span data-ttu-id="41a11-135">základní celočíselný typ</span><span class="sxs-lookup"><span data-stu-id="41a11-135">a basic integer type</span></span> | <span data-ttu-id="41a11-136">Formátováno jako šestnáctkové číslo bez znaménka (a-f nebo A-F pro šestnáctkové číslice v uvedeném pořadí)</span><span class="sxs-lookup"><span data-stu-id="41a11-136">Formatted as an unsigned hexadecimal number (a-f or A-F for hex digits respectively)</span></span>  |
|  `%o`              | <span data-ttu-id="41a11-137">základní celočíselný typ</span><span class="sxs-lookup"><span data-stu-id="41a11-137">a basic integer type</span></span> | <span data-ttu-id="41a11-138">Formátováno jako osmičkové číslo bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="41a11-138">Formatted as an unsigned octal number</span></span> |
| <span data-ttu-id="41a11-139">`%e`, `%E`</span><span class="sxs-lookup"><span data-stu-id="41a11-139">`%e`, `%E`</span></span>         | <span data-ttu-id="41a11-140">základní typ s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="41a11-140">a basic floating point type</span></span> | <span data-ttu-id="41a11-141">Formátováno jako podepsaná hodnota s formulářem, `[-]d.dddde[sign]ddd` kde d je jedna desítková číslice, dddd je jedna nebo více desítkových číslic, DDD je přesně tři desítkové číslice a znak je `+` nebo`-`</span><span class="sxs-lookup"><span data-stu-id="41a11-141">Formatted as a signed value having the form `[-]d.dddde[sign]ddd` where d is a single decimal digit, dddd is one or more decimal digits, ddd is exactly three decimal digits, and sign is `+` or `-`</span></span> |
| `%f`               | <span data-ttu-id="41a11-142">základní typ s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="41a11-142">a basic floating point type</span></span> | <span data-ttu-id="41a11-143">Formátováno jako podepsaná hodnota, která má formu `[-]dddd.dddd` , kde `dddd` je jedna nebo více desítkových číslic.</span><span class="sxs-lookup"><span data-stu-id="41a11-143">Formatted as a signed value having the form `[-]dddd.dddd`, where `dddd` is one or more decimal digits.</span></span> <span data-ttu-id="41a11-144">Počet číslic před desetinnou čárkou závisí na velikosti čísla a počet číslic po desetinné čárkě závisí na požadované přesnosti.</span><span class="sxs-lookup"><span data-stu-id="41a11-144">The number of digits before the decimal point depends on the magnitude of the number, and the number of digits after the decimal point depends on the requested precision.</span></span> |
| <span data-ttu-id="41a11-145">`%g`, `%G`</span><span class="sxs-lookup"><span data-stu-id="41a11-145">`%g`, `%G`</span></span> | <span data-ttu-id="41a11-146">základní typ s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="41a11-146">a basic floating point type</span></span> |  <span data-ttu-id="41a11-147">Formátováno pomocí formátu jako hodnota, která je vytištěna v `%f` nebo `%e` Format, podle toho, která je pro danou hodnotu a přesnost kompaktnější.</span><span class="sxs-lookup"><span data-stu-id="41a11-147">Formatted using as a signed value printed in `%f` or `%e` format, whichever is more compact for the given value and precision.</span></span> |
| `%M` | <span data-ttu-id="41a11-148">`System.Decimal`hodnota</span><span class="sxs-lookup"><span data-stu-id="41a11-148">a `System.Decimal` value</span></span>  |    <span data-ttu-id="41a11-149">Formátování pomocí `"G"` specifikátoru formátu pro`System.Decimal.ToString(format)`</span><span class="sxs-lookup"><span data-stu-id="41a11-149">Formatted using the `"G"` format specifier for `System.Decimal.ToString(format)`</span></span> |
| `%O` | <span data-ttu-id="41a11-150">libovolná hodnota</span><span class="sxs-lookup"><span data-stu-id="41a11-150">any value</span></span>  |   <span data-ttu-id="41a11-151">Formátováno zabalením objektu a voláním jeho `System.Object.ToString()` metody</span><span class="sxs-lookup"><span data-stu-id="41a11-151">Formatted by boxing the object and calling its `System.Object.ToString()` method</span></span> |
| `%A` | <span data-ttu-id="41a11-152">libovolná hodnota</span><span class="sxs-lookup"><span data-stu-id="41a11-152">any value</span></span>  |   <span data-ttu-id="41a11-153">Formátování pomocí [strukturovaného formátu prostého textu](plaintext-formatting.md) s výchozím nastavením rozložení</span><span class="sxs-lookup"><span data-stu-id="41a11-153">Formatted using [structured plain text formatting](plaintext-formatting.md) with the default layout settings</span></span> |
| `%a` | <span data-ttu-id="41a11-154">libovolná hodnota</span><span class="sxs-lookup"><span data-stu-id="41a11-154">any value</span></span>  |   <span data-ttu-id="41a11-155">Vyžaduje dva argumenty: funkce formátování přijímající kontextový parametr a hodnotu a určitou hodnotu pro tisk.</span><span class="sxs-lookup"><span data-stu-id="41a11-155">Requires two arguments: a formatting function accepting a context parameter and the value, and the particular value to print</span></span> |
| `%t` | <span data-ttu-id="41a11-156">libovolná hodnota</span><span class="sxs-lookup"><span data-stu-id="41a11-156">any value</span></span>  |   <span data-ttu-id="41a11-157">Vyžaduje jeden argument: funkce formátování přijímá kontextový parametr, který buď výstup, nebo vrátí příslušný text.</span><span class="sxs-lookup"><span data-stu-id="41a11-157">Requires one argument: a formatting function accepting a context parameter that either outputs or returns the appropriate text</span></span> |
| `%%` | <span data-ttu-id="41a11-158">(žádná)</span><span class="sxs-lookup"><span data-stu-id="41a11-158">(none)</span></span>  |   <span data-ttu-id="41a11-159">Nevyžaduje žádné argumenty a tiskne znak v podobě jednoduchého procenta:`%`</span><span class="sxs-lookup"><span data-stu-id="41a11-159">Requires no arguments and prints a plain percent sign: `%`</span></span> |

<span data-ttu-id="41a11-160">Základní celočíselné typy jsou `byte` (), (), (), (), (), (), (), (), (), `System.Byte` `sbyte` `System.SByte` `int16` `System.Int16` `uint16` () `System.UInt16` `int32` `System.Int32` `uint32` `System.UInt32` `int64` `System.Int64` `uint64` `System.UInt64` `nativeint` `System.IntPtr` a `unativeint` ( `System.UIntPtr` ).</span><span class="sxs-lookup"><span data-stu-id="41a11-160">Basic integer types are `byte` (`System.Byte`), `sbyte` (`System.SByte`), `int16` (`System.Int16`), `uint16` (`System.UInt16`), `int32` (`System.Int32`), `uint32` (`System.UInt32`), `int64` (`System.Int64`), `uint64` (`System.UInt64`), `nativeint`  (`System.IntPtr`), and `unativeint`  (`System.UIntPtr`).</span></span>
<span data-ttu-id="41a11-161">Základní typy s plovoucí desetinnou čárkou jsou `float` ( `System.Double` ) a `float32` ( `System.Single` ).</span><span class="sxs-lookup"><span data-stu-id="41a11-161">Basic floating point types are `float` (`System.Double`) and `float32` (`System.Single`).</span></span>

<span data-ttu-id="41a11-162">Volitelná šířka je celé číslo označující minimální šířku výsledku.</span><span class="sxs-lookup"><span data-stu-id="41a11-162">The optional width is an integer indicating the minimal width of the result.</span></span> <span data-ttu-id="41a11-163">Například `%6d` vytiskne celé číslo s předponou mezer, aby vyplnila alespoň šest znaků.</span><span class="sxs-lookup"><span data-stu-id="41a11-163">For instance, `%6d` prints an integer, prefixing it with spaces to fill at least six characters.</span></span> <span data-ttu-id="41a11-164">Pokud je Width `*` , pak je proveden další celočíselný argument pro určení odpovídající šířky.</span><span class="sxs-lookup"><span data-stu-id="41a11-164">If width is `*`, then an extra integer  argument is taken to specify the corresponding width.</span></span>

<span data-ttu-id="41a11-165">Platné příznaky:</span><span class="sxs-lookup"><span data-stu-id="41a11-165">Valid flags are:</span></span>

| <span data-ttu-id="41a11-166">Příznak</span><span class="sxs-lookup"><span data-stu-id="41a11-166">Flag</span></span>   | <span data-ttu-id="41a11-167">Účinek</span><span class="sxs-lookup"><span data-stu-id="41a11-167">Effect</span></span>        | <span data-ttu-id="41a11-168">Poznámky</span><span class="sxs-lookup"><span data-stu-id="41a11-168">Remarks</span></span>                      |
|:-------------------|:---------------|:-----------------------------|
| `0`  | <span data-ttu-id="41a11-169">Místo mezer přidejte nuly, aby se zajistila požadovaná šířka.</span><span class="sxs-lookup"><span data-stu-id="41a11-169">Add zeros instead of spaces to make up the required width</span></span> |    |
| `-` |  <span data-ttu-id="41a11-170">Vlevo zarovnat výsledek v zadané šířce</span><span class="sxs-lookup"><span data-stu-id="41a11-170">Left justify the result within the specified width</span></span> |   |
| `+`  | <span data-ttu-id="41a11-171">Přidejte `+` znak, pokud je číslo kladné (aby odpovídalo `-` znaménku pro záporné znaky).</span><span class="sxs-lookup"><span data-stu-id="41a11-171">Add a `+` character if the number is positive (to match a `-` sign for negatives)</span></span> |   |
| <span data-ttu-id="41a11-172">znak mezery</span><span class="sxs-lookup"><span data-stu-id="41a11-172">space character</span></span> | <span data-ttu-id="41a11-173">Přidejte mezeru navíc, pokud je číslo kladné (aby odpovídalo znaku '-' pro záporné znaky).</span><span class="sxs-lookup"><span data-stu-id="41a11-173">Add an extra space if the number is positive (to match a '-' sign for negatives)</span></span> |

<span data-ttu-id="41a11-174">Příznak printf `#` je neplatný a v případě, že se používá, bude hlášena chyba při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="41a11-174">The printf `#` flag is invalid and a compile-time error will be reported if it is used.</span></span>

<span data-ttu-id="41a11-175">Hodnoty jsou formátovány pomocí invariantní jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="41a11-175">Values are formatted using invariant culture.</span></span> <span data-ttu-id="41a11-176">Nastavení jazykové verze je nepodstatné pro `printf` formátování s výjimkou případů, kdy mají vliv na výsledky `%O` a `%A` formátování.</span><span class="sxs-lookup"><span data-stu-id="41a11-176">Culture settings are irrelevant to `printf` formatting except when they affect the results of `%O` and `%A` formatting.</span></span> <span data-ttu-id="41a11-177">Další informace najdete v tématu [strukturované formátování prostého textu](plaintext-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="41a11-177">For more information, see [structured plain text formatting](plaintext-formatting.md).</span></span>

## <a name="a-formatting"></a><span data-ttu-id="41a11-178">`%A`kurzívy</span><span class="sxs-lookup"><span data-stu-id="41a11-178">`%A` formatting</span></span>

<span data-ttu-id="41a11-179">`%A`Specifikátor formátu slouží k formátování hodnot způsobem čitelným lidmi a může být také užitečný pro vytváření sestav diagnostických informací.</span><span class="sxs-lookup"><span data-stu-id="41a11-179">The `%A` format specifier is used to format values in a human-readable way, and can also be useful for reporting diagnostic information.</span></span>

### <a name="primitive-values"></a><span data-ttu-id="41a11-180">Primitivní hodnoty</span><span class="sxs-lookup"><span data-stu-id="41a11-180">Primitive values</span></span>

<span data-ttu-id="41a11-181">Při formátování prostého textu pomocí `%A` specifikátoru jsou číselné hodnoty F # formátovány s jejich příponou a invariantní jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="41a11-181">When formatting plain text using the `%A` specifier, F# numeric values are formatted with their suffix and invariant culture.</span></span> <span data-ttu-id="41a11-182">Hodnoty s plovoucí desetinnou čárkou jsou formátovány pomocí 10 míst přesnosti s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="41a11-182">Floating point values are formatted using 10 places of floating point precision.</span></span> <span data-ttu-id="41a11-183">Příklad:</span><span class="sxs-lookup"><span data-stu-id="41a11-183">For example,</span></span>

```fsharp
printfn "%A" (1L, 3n, 5u, 7, 4.03f, 5.000000001, 5.0000000001)
```

<span data-ttu-id="41a11-184">uslyší</span><span class="sxs-lookup"><span data-stu-id="41a11-184">produces</span></span>

```console
(1L, 3n, 5u, 7, 4.03000021f, 5.000000001, 5.0)
```

<span data-ttu-id="41a11-185">Při použití `%A` specifikátoru jsou řetězce formátovány pomocí uvozovek.</span><span class="sxs-lookup"><span data-stu-id="41a11-185">When using the `%A` specifier, strings are formatted using quotes.</span></span> <span data-ttu-id="41a11-186">Řídicí kódy nejsou přidány a místo nich jsou vytištěny nezpracované znaky.</span><span class="sxs-lookup"><span data-stu-id="41a11-186">Escape codes are not added and instead the raw characters are printed.</span></span> <span data-ttu-id="41a11-187">Příklad:</span><span class="sxs-lookup"><span data-stu-id="41a11-187">For example,</span></span>

```fsharp
printfn "%A" ("abc", "a\tb\nc\"d")

```

<span data-ttu-id="41a11-188">uslyší</span><span class="sxs-lookup"><span data-stu-id="41a11-188">produces</span></span>

```console
("abc", "a      b
c"d")
```

### <a name="net-values"></a><span data-ttu-id="41a11-189">Hodnoty .NET</span><span class="sxs-lookup"><span data-stu-id="41a11-189">.NET values</span></span>

<span data-ttu-id="41a11-190">Při formátování prostého textu pomocí `%A` specifikátoru jsou objekty rozhraní .NET bez F # formátovány pomocí `x.ToString()` výchozího nastavení rozhraní .NET, které je zadáno pomocí `System.Globalization.CultureInfo.CurrentCulture` a `System.Globalization.CultureInfo.CurrentUICulture` .</span><span class="sxs-lookup"><span data-stu-id="41a11-190">When formatting plain text using the `%A` specifier, non-F# .NET objects are formatted by using `x.ToString()` using the default settings of .NET given by `System.Globalization.CultureInfo.CurrentCulture` and `System.Globalization.CultureInfo.CurrentUICulture`.</span></span>  <span data-ttu-id="41a11-191">Příklad:</span><span class="sxs-lookup"><span data-stu-id="41a11-191">For example,</span></span>

```fsharp
open System.Globalization

let date = System.DateTime(1999, 12, 31)

CultureInfo.CurrentCulture <- CultureInfo.GetCultureInfo("de-DE")
printfn "Culture 1: %A" date

CultureInfo.CurrentCulture <- CultureInfo.GetCultureInfo("en-US")
printfn "Culture 2: %A" date
```

<span data-ttu-id="41a11-192">uslyší</span><span class="sxs-lookup"><span data-stu-id="41a11-192">produces</span></span>

```console
Culture 1: 31.12.1999 00:00:00
Culture 2: 12/31/1999 12:00:00 AM
```

### <a name="structured-values"></a><span data-ttu-id="41a11-193">Strukturované hodnoty</span><span class="sxs-lookup"><span data-stu-id="41a11-193">Structured values</span></span>

<span data-ttu-id="41a11-194">Při formátování prostého textu pomocí `%A` specifikátoru se pro seznamy F # a n-tice použije blokové odsazení.</span><span class="sxs-lookup"><span data-stu-id="41a11-194">When formatting plain text using the `%A` specifier, block indentation is used for F# lists and tuples.</span></span> <span data-ttu-id="41a11-195">Zobrazuje se v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="41a11-195">This shown in the previous example.</span></span>
<span data-ttu-id="41a11-196">Také se používá struktura polí včetně multidimenzionálních polí.</span><span class="sxs-lookup"><span data-stu-id="41a11-196">The structure of arrays is also used, including multi-dimensional arrays.</span></span>  <span data-ttu-id="41a11-197">Jednorozměrná pole se zobrazují se `[| ... |]` syntaxí.</span><span class="sxs-lookup"><span data-stu-id="41a11-197">Single-dimensional arrays are shown with `[| ... |]` syntax.</span></span> <span data-ttu-id="41a11-198">Příklad:</span><span class="sxs-lookup"><span data-stu-id="41a11-198">For example,</span></span>

```fsharp
printfn "%A" [| for i in 1 .. 20 -> (i, i*i) |]
```

<span data-ttu-id="41a11-199">uslyší</span><span class="sxs-lookup"><span data-stu-id="41a11-199">produces</span></span>

```console
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25); (6, 36); (7, 49); (8, 64); (9, 81);
  (10, 100); (11, 121); (12, 144); (13, 169); (14, 196); (15, 225); (16, 256);
  (17, 289); (18, 324); (19, 361); (20, 400)|]
```

<span data-ttu-id="41a11-200">Výchozí šířka tisku je 80.</span><span class="sxs-lookup"><span data-stu-id="41a11-200">The default print width is 80.</span></span>  <span data-ttu-id="41a11-201">Tuto šířku lze přizpůsobit pomocí šířky tisku ve specifikátoru formátu.</span><span class="sxs-lookup"><span data-stu-id="41a11-201">This width can be customized by using a print width in the format specifier.</span></span> <span data-ttu-id="41a11-202">Příklad:</span><span class="sxs-lookup"><span data-stu-id="41a11-202">For example,</span></span>

```fsharp
printfn "%10A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%20A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%50A" [| for i in 1 .. 5 -> (i, i*i) |]
```

<span data-ttu-id="41a11-203">uslyší</span><span class="sxs-lookup"><span data-stu-id="41a11-203">produces</span></span>

```console
[|(1, 1);
  (2, 4);
  (3, 9);
  (4, 16);
  (5, 25)|]
[|(1, 1); (2, 4);
  (3, 9); (4, 16);
  (5, 25)|]
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25)|]
```

<span data-ttu-id="41a11-204">Zadání šířky tisku 0 způsobí, že se nepoužívá žádná šířka tisku.</span><span class="sxs-lookup"><span data-stu-id="41a11-204">Specifying a print width of 0 results in no print width being used.</span></span> <span data-ttu-id="41a11-205">Výsledkem bude jeden řádek textu s výjimkou případů, kdy vložené řetězce ve výstupu obsahují zalomení řádků.</span><span class="sxs-lookup"><span data-stu-id="41a11-205">A single line of text will result, except where embedded strings in the output contain line breaks.</span></span>  <span data-ttu-id="41a11-206">Například</span><span class="sxs-lookup"><span data-stu-id="41a11-206">For example</span></span>

```fsharp
printfn "%0A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%0A" [| for i in 1 .. 5 -> "abc\ndef" |]
```

<span data-ttu-id="41a11-207">uslyší</span><span class="sxs-lookup"><span data-stu-id="41a11-207">produces</span></span>

```console
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25)|]
[|"abc
def"; "abc
def"; "abc
def"; "abc
def"; "abc
def"|]
```

<span data-ttu-id="41a11-208">Pro hodnoty Sequence () se používá limit hloubky 4 `IEnumerable` , který se zobrazuje jako `seq { ...}` .</span><span class="sxs-lookup"><span data-stu-id="41a11-208">A depth limit of 4 is used for sequence (`IEnumerable`) values, which are shown as `seq { ...}`.</span></span> <span data-ttu-id="41a11-209">Pro hodnoty list a Array se používá limit hloubky 100.</span><span class="sxs-lookup"><span data-stu-id="41a11-209">A depth limit of 100 is used for list and array values.</span></span>
<span data-ttu-id="41a11-210">Příklad:</span><span class="sxs-lookup"><span data-stu-id="41a11-210">For example,</span></span>

```fsharp
printfn "%A" (seq { for i in 1 .. 10 -> (i, i*i) })
```

<span data-ttu-id="41a11-211">uslyší</span><span class="sxs-lookup"><span data-stu-id="41a11-211">produces</span></span>

```console
seq [(1, 1); (2, 4); (3, 9); (4, 16); ...]
```

<span data-ttu-id="41a11-212">Pro strukturu hodnot veřejného záznamu a sjednocení se používá také odsazení bloku.</span><span class="sxs-lookup"><span data-stu-id="41a11-212">Block indentation is also used for the structure of public record and union values.</span></span> <span data-ttu-id="41a11-213">Příklad:</span><span class="sxs-lookup"><span data-stu-id="41a11-213">For example,</span></span>

```fsharp
type R = { X : int list; Y : string list }

printfn "%A" { X =  [ 1;2;3 ]; Y = ["one"; "two"; "three"] }
```

<span data-ttu-id="41a11-214">uslyší</span><span class="sxs-lookup"><span data-stu-id="41a11-214">produces</span></span>

```console
{ X = [1; 2; 3]
  Y = ["one"; "two"; "three"] }
```

<span data-ttu-id="41a11-215">Pokud `%+A` se používá, pak je soukromá struktura záznamů a sjednocení také odhalena pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="41a11-215">If `%+A` is used, then the private structure of records and unions is also revealed by using reflection.</span></span> <span data-ttu-id="41a11-216">Například</span><span class="sxs-lookup"><span data-stu-id="41a11-216">For example</span></span>

```fsharp
type internal R =
    { X : int list; Y : string list }
    override _.ToString() = "R"

let internal data = { X = [ 1;2;3 ]; Y = ["one"; "two"; "three"] }

printfn "external view:\n%A" data

printfn "internal view:\n%+A" data

```

<span data-ttu-id="41a11-217">uslyší</span><span class="sxs-lookup"><span data-stu-id="41a11-217">produces</span></span>

```console
external view:
R

internal view:
{ X = [1; 2; 3]
  Y = ["one"; "two"; "three"] }
```

### <a name="large-cyclic-or-deeply-nested-values"></a><span data-ttu-id="41a11-218">Velké, cyklické nebo hluboko vnořené hodnoty</span><span class="sxs-lookup"><span data-stu-id="41a11-218">Large, cyclic, or deeply nested values</span></span>

<span data-ttu-id="41a11-219">Velké strukturované hodnoty jsou formátovány na maximální celkový počet uzlů objektu 10000.</span><span class="sxs-lookup"><span data-stu-id="41a11-219">Large structured values are formatted to a maximum overall object node count of 10000.</span></span>
<span data-ttu-id="41a11-220">Hluboko vnořené hodnoty jsou formátovány na hloubku 100.</span><span class="sxs-lookup"><span data-stu-id="41a11-220">Deeply nested values are formatted to a depth of 100.</span></span>  <span data-ttu-id="41a11-221">V obou případech `...` slouží k elideí některých výstupů.</span><span class="sxs-lookup"><span data-stu-id="41a11-221">In both cases `...` is used to elide some of the output.</span></span>  <span data-ttu-id="41a11-222">Příklad:</span><span class="sxs-lookup"><span data-stu-id="41a11-222">For example,</span></span>

```fsharp
type Tree =
    | Tip
    | Node of Tree * Tree

let rec make n =
    if n = 0 then
        Tip
    else
        Node(Tip, make (n-1))

printfn "%A" (make 1000)
```

<span data-ttu-id="41a11-223">Vytvoří velký výstup s některými částmi vynechaného Copy:</span><span class="sxs-lookup"><span data-stu-id="41a11-223">produces a large output with some parts elided:</span></span>

```console
Node(Tip, Node(Tip, ....Node (..., ...)...))
```

<span data-ttu-id="41a11-224">V grafech objektů jsou zjištěny cykly, `...` které se používají na místech, kde jsou zjištěny cykly.</span><span class="sxs-lookup"><span data-stu-id="41a11-224">Cycles are detected in the object graphs and `...` is used at places where cycles are detected.</span></span> <span data-ttu-id="41a11-225">Například</span><span class="sxs-lookup"><span data-stu-id="41a11-225">For example</span></span>

```fsharp
type R = { mutable Links: R list }
let r = { Links = [] }
r.Links <- [r]
printfn "%A" r
```

<span data-ttu-id="41a11-226">uslyší</span><span class="sxs-lookup"><span data-stu-id="41a11-226">produces</span></span>

```console
{ Links = [...] }
```

### <a name="lazy-null-and-function-values"></a><span data-ttu-id="41a11-227">Opožděné, null a hodnoty funkcí</span><span class="sxs-lookup"><span data-stu-id="41a11-227">Lazy, null, and function values</span></span>

<span data-ttu-id="41a11-228">Opožděné hodnoty jsou vytištěny jako `Value is not created` nebo ekvivalentní text, pokud hodnota ještě nebyla vyhodnocena.</span><span class="sxs-lookup"><span data-stu-id="41a11-228">Lazy values are printed as `Value is not created` or equivalent text when the value has not yet been evaluated.</span></span>

<span data-ttu-id="41a11-229">Hodnoty null jsou vytištěny, s `null` výjimkou případů, kdy je statický typ hodnoty určen jako typ sjednocení, kde `null` je povolená reprezentace.</span><span class="sxs-lookup"><span data-stu-id="41a11-229">Null values are printed as `null` unless the static type of the value is determined to be a union type where `null` is a permitted representation.</span></span>

<span data-ttu-id="41a11-230">Hodnoty funkcí F # jsou vytištěny jako název vnitřně generovaného uzavření, například `<fun:it@43-7>` .</span><span class="sxs-lookup"><span data-stu-id="41a11-230">F# function values are printed as their internally generated closure name, for example, `<fun:it@43-7>`.</span></span>

### <a name="customize-plain-text-formatting-with-structuredformatdisplay"></a><span data-ttu-id="41a11-231">Přizpůsobení formátování prostého textu pomocí`StructuredFormatDisplay`</span><span class="sxs-lookup"><span data-stu-id="41a11-231">Customize plain text formatting with `StructuredFormatDisplay`</span></span>

<span data-ttu-id="41a11-232">Při použití `%A` specifikátoru `StructuredFormatDisplay` je respektována přítomnost atributu v deklaracích typů.</span><span class="sxs-lookup"><span data-stu-id="41a11-232">When using the `%A` specifier, the presence of the `StructuredFormatDisplay` attribute on type declarations is respected.</span></span>  <span data-ttu-id="41a11-233">Dá se použít k zadání náhradního textu a vlastnosti k zobrazení hodnoty.</span><span class="sxs-lookup"><span data-stu-id="41a11-233">This can be used to specify surrogate text and property to display a value.</span></span> <span data-ttu-id="41a11-234">Například:</span><span class="sxs-lookup"><span data-stu-id="41a11-234">For example:</span></span>

```fsharp
[<StructuredFormatDisplay("Counts({Clicks})")>]
type Counts = { Clicks:int list}

printfn "%20A" {Clicks=[0..20]}
```

<span data-ttu-id="41a11-235">uslyší</span><span class="sxs-lookup"><span data-stu-id="41a11-235">produces</span></span>

```console
Counts([0; 1; 2; 3;
        4; 5; 6; 7;
        8; 9; 10; 11;
        12; 13; 14;
        15; 16; 17;
        18; 19; 20])
```

### <a name="customize-plain-text-formatting-by-overriding-tostring"></a><span data-ttu-id="41a11-236">Přizpůsobení formátování prostého textu přepsáním`ToString`</span><span class="sxs-lookup"><span data-stu-id="41a11-236">Customize plain text formatting by overriding `ToString`</span></span>

<span data-ttu-id="41a11-237">Výchozí implementace `ToString` je v programování F # pozorovatelná.</span><span class="sxs-lookup"><span data-stu-id="41a11-237">The default implementation of `ToString` is observable in F# programming.</span></span> <span data-ttu-id="41a11-238">Výchozí výsledky nejsou často vhodné pro použití ve formě zobrazení informací nebo v uživatelském výstupu, a v důsledku toho je běžné přepsat výchozí implementaci.</span><span class="sxs-lookup"><span data-stu-id="41a11-238">Often, the default results aren't suitable for use in either programmer-facing information display or user output, and as a result it is common to override the default implementation.</span></span>  

<span data-ttu-id="41a11-239">Ve výchozím nastavení typy záznamu a sjednocení jazyka F # přepisují implementaci `ToString` s implementací, kterou používá `sprintf "%+A"` .</span><span class="sxs-lookup"><span data-stu-id="41a11-239">By default, F# record and union types override the implementation of `ToString` with an implementation that uses `sprintf "%+A"`.</span></span>  <span data-ttu-id="41a11-240">Příklad:</span><span class="sxs-lookup"><span data-stu-id="41a11-240">For example,</span></span>

```fsharp
type Counts = { Clicks:int list }

printfn "%s" ({Clicks=[0..10]}.ToString())
```

<span data-ttu-id="41a11-241">uslyší</span><span class="sxs-lookup"><span data-stu-id="41a11-241">produces</span></span>

```console
{ Clicks = [0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10] }
```

<span data-ttu-id="41a11-242">U typů tříd není k dispozici žádná výchozí implementace `ToString` a použije se výchozí rozhraní .NET, které hlásí název typu.</span><span class="sxs-lookup"><span data-stu-id="41a11-242">For class types, no default implementation of `ToString` is provided and the .NET default is used, which reports the name of the type.</span></span> <span data-ttu-id="41a11-243">Příklad:</span><span class="sxs-lookup"><span data-stu-id="41a11-243">For example,</span></span>

```fsharp
type MyClassType(clicks: int list) =
   member _.Clicks = clicks

let data = [ MyClassType([1..5]); MyClassType([1..5]) ]
printfn "Default structured print gives this:\n%A" data
printfn "Default ToString gives:\n%s" (data.ToString())
```

<span data-ttu-id="41a11-244">uslyší</span><span class="sxs-lookup"><span data-stu-id="41a11-244">produces</span></span>

```console
Default structured print gives this:
[MyClassType; MyClassType]
Default ToString gives:
[MyClassType; MyClassType]
```

<span data-ttu-id="41a11-245">Přidání přepsání pro `ToString` může mít lepší formátování.</span><span class="sxs-lookup"><span data-stu-id="41a11-245">Adding an override for `ToString` can give better formatting.</span></span>

```fsharp
type MyClassType(clicks: int list) =
   member _.Clicks = clicks
   override _.ToString() = sprintf "MyClassType(%0A)" clicks

let data = [ MyClassType([1..5]); MyClassType([1..5]) ]
printfn "Now structured print gives this:\n%A" data
printfn "Now ToString gives:\n%s" (data.ToString())
```

<span data-ttu-id="41a11-246">uslyší</span><span class="sxs-lookup"><span data-stu-id="41a11-246">produces</span></span>

```console
Now structured print gives this:
[MyClassType([1; 2; 3; 4; 5]); MyClassType([1; 2; 3; 4; 5])]
Now ToString gives:
[MyClassType([1; 2; 3; 4; 5]); MyClassType([1; 2; 3; 4; 5])]
```

## <a name="f-interactive-structured-printing"></a><span data-ttu-id="41a11-247">F# Interactive strukturovaný tisk</span><span class="sxs-lookup"><span data-stu-id="41a11-247">F# Interactive structured printing</span></span>

<span data-ttu-id="41a11-248">F# Interactive ( `dotnet fsi` ) používá rozšířenou verzi strukturovaného formátování prostého textu k vykazování hodnot a umožňuje dodatečnou možnost úprav.</span><span class="sxs-lookup"><span data-stu-id="41a11-248">F# Interactive (`dotnet fsi`) uses an extended version of structured plain text formatting to report values and allows additional customizability.</span></span> <span data-ttu-id="41a11-249">Další informace najdete v tématu [F# Interactive](fsharp-interactive-options.md).</span><span class="sxs-lookup"><span data-stu-id="41a11-249">For more information, see [F# Interactive](fsharp-interactive-options.md).</span></span>

## <a name="customize-debug-displays"></a><span data-ttu-id="41a11-250">Přizpůsobení zobrazení ladění</span><span class="sxs-lookup"><span data-stu-id="41a11-250">Customize debug displays</span></span>

<span data-ttu-id="41a11-251">Ladicí programy pro .NET respektují použití atributů jako `DebuggerDisplay` a a `DebuggerTypeProxy` mají vliv na strukturované zobrazení objektů v oknech pro kontrolu ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="41a11-251">Debuggers for .NET respect the use of attributes such as `DebuggerDisplay` and `DebuggerTypeProxy`, and these affect the structured display of objects in debugger inspection windows.</span></span>
<span data-ttu-id="41a11-252">Kompilátor jazyka F # automaticky vygeneroval tyto atributy pro rozlišené typy sjednocení a záznamů, ale ne typy třídy, rozhraní nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="41a11-252">The F# compiler automatically generated these attributes for discriminated union and record types, but not class, interface, or struct types.</span></span>

<span data-ttu-id="41a11-253">Tyto atributy jsou ignorovány ve formátu prostého textu F #, ale mohou být užitečné při implementaci těchto metod pro zlepšení zobrazení při ladění typů F #.</span><span class="sxs-lookup"><span data-stu-id="41a11-253">These attributes are ignored in F# plain text formatting, but it can be useful to implement these methods to improve displays when debugging F# types.</span></span>

## <a name="see-also"></a><span data-ttu-id="41a11-254">Viz také</span><span class="sxs-lookup"><span data-stu-id="41a11-254">See also</span></span>

- [<span data-ttu-id="41a11-255">Řetězce</span><span class="sxs-lookup"><span data-stu-id="41a11-255">Strings</span></span>](strings.md)
- [<span data-ttu-id="41a11-256">Záznamy</span><span class="sxs-lookup"><span data-stu-id="41a11-256">Records</span></span>](records.md)
- [<span data-ttu-id="41a11-257">Rozlišovaná sjednocení</span><span class="sxs-lookup"><span data-stu-id="41a11-257">Discriminated Unions</span></span>](discriminated-unions.md)
- [<span data-ttu-id="41a11-258">F# Interactive</span><span class="sxs-lookup"><span data-stu-id="41a11-258">F# Interactive</span></span>](fsharp-interactive-options.md)
