---
title: Formátování prostého textu
description: 'Naučte se používat printf a jiné formátování prostého textu v aplikacích a skriptech F #.'
ms.date: 07/22/2020
ms.openlocfilehash: a0f2c52431be894c4f74dd2940345a518f620589
ms.sourcegitcommit: 09bad6ec0cbf18be7cd7f62e77286d305a18b607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/05/2020
ms.locfileid: "87795744"
---
# <a name="plain-text-formatting"></a><span data-ttu-id="6cf3d-103">Formátování prostého textu</span><span class="sxs-lookup"><span data-stu-id="6cf3d-103">Plain text formatting</span></span>

<span data-ttu-id="6cf3d-104">Jazyk F # podporuje formátování prostého textu se zaškrtnutým typem `printf` , a to pomocí `printfn` souvisejících funkcí,, `sprintf` a.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-104">F# supports type-checked formatting of plain text using `printf`, `printfn`, `sprintf`, and related functions.</span></span>
<span data-ttu-id="6cf3d-105">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6cf3d-105">For example,</span></span>

```console
dotnet fsi

> printfn "Hello %s, %d + %d is %d" "world" 2 2 (2+2);;
```

<span data-ttu-id="6cf3d-106">poskytne výstup</span><span class="sxs-lookup"><span data-stu-id="6cf3d-106">gives the output</span></span>

```fsharp
Hello world, 2 + 2 is 4
```

<span data-ttu-id="6cf3d-107">Jazyk F # také umožňuje formátování strukturovaných hodnot jako prostý text.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-107">F# also allows structured values to be formatted as plain text.</span></span>
<span data-ttu-id="6cf3d-108">Zvažte například následující příklad, který formátuje výstup jako zobrazení řazených kolekcí členů jako matice.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-108">For example, consider the following example that formats the output as a matrix-like display of tuples.</span></span>

```console
dotnet fsi

> printfn "%A" [ for i in 1 .. 5 -> [ for j in 1 .. 5 -> (i, j) ] ];;

[[(1, 1); (1, 2); (1, 3); (1, 4); (1, 5)];
 [(2, 1); (2, 2); (2, 3); (2, 4); (2, 5)];
 [(3, 1); (3, 2); (3, 3); (3, 4); (3, 5)];
 [(4, 1); (4, 2); (4, 3); (4, 4); (4, 5)];
 [(5, 1); (5, 2); (5, 3); (5, 4); (5, 5)]]
```

<span data-ttu-id="6cf3d-109">Strukturované formátování prostého textu je aktivováno při použití `%A` formátu při `printf` formátování řetězců.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-109">Structured plain text formatting is activated when you use the `%A` format in `printf` formatting strings.</span></span>
<span data-ttu-id="6cf3d-110">Aktivuje se také při formátování výstupu hodnot v F # Interactive, kde výstup zahrnuje další informace a je navíc přizpůsobitelná.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-110">It's also activated when formatting the output of values in F# interactive, where the output includes extra information and is additionally customizable.</span></span>
<span data-ttu-id="6cf3d-111">Formátování prostého textu je také možné pozorovat prostřednictvím jakýchkoli volání `x.ToString()` na základě sjednocení F # a záznamů, včetně těch, které se vyskytují implicitně v ladění, protokolování a dalších nástrojích.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-111">Plain text formatting is also observable through any calls to `x.ToString()` on F# union and record values, including those that occur implicitly in debugging, logging, and other tooling.</span></span>

## <a name="checking-of-printf-format-strings"></a><span data-ttu-id="6cf3d-112">Kontrola `printf` formátovacích řetězců</span><span class="sxs-lookup"><span data-stu-id="6cf3d-112">Checking of `printf`-format strings</span></span>

<span data-ttu-id="6cf3d-113">Pokud `printf` se funkce formátování používá s argumentem, který se neshoduje s specifikátory formátu printf ve formátu řetězce, bude zaznamenána chyba při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-113">A compile-time error will be reported if a `printf` formatting function is used with an argument that doesn't match the printf format specifiers in the format string.</span></span>  <span data-ttu-id="6cf3d-114">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6cf3d-114">For example,</span></span>

```fsharp
sprintf "Hello %s" (2+2)
```

<span data-ttu-id="6cf3d-115">poskytne výstup</span><span class="sxs-lookup"><span data-stu-id="6cf3d-115">gives the output</span></span>

```console
  sprintf "Hello %s" (2+2)
  ----------------------^

stdin(3,25): error FS0001: The type 'string' does not match the type 'int'
```

<span data-ttu-id="6cf3d-116">Technicky řečeno, při použití `printf` a dalších souvisejících funkcích kontroluje zvláštní pravidlo v kompilátoru F # řetězcový literál předaný jako formátovací řetězec, který zajišťuje, že následné použité argumenty jsou správného typu, aby se shodovaly s použitými specifikátory formátu.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-116">Technically speaking, when using `printf` and other related functions, a special rule in the F# compiler checks the string literal passed as the format string, ensuring the subsequent arguments applied are of the correct type to match the format specifiers used.</span></span>

## <a name="format-specifiers-for-printf"></a><span data-ttu-id="6cf3d-117">Specifikátory formátu pro`printf`</span><span class="sxs-lookup"><span data-stu-id="6cf3d-117">Format specifiers for `printf`</span></span>

<span data-ttu-id="6cf3d-118">Specifikace formátu pro `printf` formáty jsou řetězce se `%` značkami, které označují formát.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-118">Format specifications for `printf` formats are strings with `%` markers that indicate format.</span></span> <span data-ttu-id="6cf3d-119">Zástupné symboly formátu `%[flags][width][.precision][type]` se skládají z místa, kde je typ interpretován takto:</span><span class="sxs-lookup"><span data-stu-id="6cf3d-119">Format placeholders consist of `%[flags][width][.precision][type]` where the type is interpreted as follows:</span></span>

| <span data-ttu-id="6cf3d-120">Specifikátor formátu</span><span class="sxs-lookup"><span data-stu-id="6cf3d-120">Format specifier</span></span>   | <span data-ttu-id="6cf3d-121">Typ (y)</span><span class="sxs-lookup"><span data-stu-id="6cf3d-121">Type(s)</span></span>        | <span data-ttu-id="6cf3d-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6cf3d-122">Remarks</span></span>                      |
|:-------------------|:---------------|:-----------------------------|
| `%b`               | <span data-ttu-id="6cf3d-123">bool</span><span class="sxs-lookup"><span data-stu-id="6cf3d-123">bool</span></span>      | <span data-ttu-id="6cf3d-124">Formátováno jako `true` nebo`false`</span><span class="sxs-lookup"><span data-stu-id="6cf3d-124">Formatted as `true` or `false`</span></span>                |
| `%s`               | <span data-ttu-id="6cf3d-125">řetězec</span><span class="sxs-lookup"><span data-stu-id="6cf3d-125">string</span></span>    | <span data-ttu-id="6cf3d-126">Formátováno jako jeho neřídicí obsah</span><span class="sxs-lookup"><span data-stu-id="6cf3d-126">Formatted as its unescaped contents</span></span>         |
| `%c`               | <span data-ttu-id="6cf3d-127">char</span><span class="sxs-lookup"><span data-stu-id="6cf3d-127">char</span></span>      | <span data-ttu-id="6cf3d-128">Formátováno jako znakový literál</span><span class="sxs-lookup"><span data-stu-id="6cf3d-128">Formatted as the character literal</span></span>  |
| <span data-ttu-id="6cf3d-129">`%d`, `%i`</span><span class="sxs-lookup"><span data-stu-id="6cf3d-129">`%d`, `%i`</span></span>         | <span data-ttu-id="6cf3d-130">základní celočíselný typ</span><span class="sxs-lookup"><span data-stu-id="6cf3d-130">a basic integer type</span></span> | <span data-ttu-id="6cf3d-131">Formátováno jako desítkové celé číslo, podepsané, pokud je základní celočíselný typ podepsán</span><span class="sxs-lookup"><span data-stu-id="6cf3d-131">Formatted as a decimal integer, signed if the basic integer type is signed</span></span> |
| `%u`               | <span data-ttu-id="6cf3d-132">základní celočíselný typ</span><span class="sxs-lookup"><span data-stu-id="6cf3d-132">a basic integer type</span></span> | <span data-ttu-id="6cf3d-133">Formátováno jako desítkové celé číslo bez znaménka</span><span class="sxs-lookup"><span data-stu-id="6cf3d-133">Formatted as an unsigned decimal integer</span></span>   |
| <span data-ttu-id="6cf3d-134">`%x`, `%X`</span><span class="sxs-lookup"><span data-stu-id="6cf3d-134">`%x`, `%X`</span></span>         | <span data-ttu-id="6cf3d-135">základní celočíselný typ</span><span class="sxs-lookup"><span data-stu-id="6cf3d-135">a basic integer type</span></span> | <span data-ttu-id="6cf3d-136">Formátováno jako šestnáctkové číslo bez znaménka (a-f nebo A-F pro šestnáctkové číslice v uvedeném pořadí)</span><span class="sxs-lookup"><span data-stu-id="6cf3d-136">Formatted as an unsigned hexadecimal number (a-f or A-F for hex digits respectively)</span></span>  |
|  `%o`              | <span data-ttu-id="6cf3d-137">základní celočíselný typ</span><span class="sxs-lookup"><span data-stu-id="6cf3d-137">a basic integer type</span></span> | <span data-ttu-id="6cf3d-138">Formátováno jako osmičkové číslo bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-138">Formatted as an unsigned octal number</span></span> |
| <span data-ttu-id="6cf3d-139">`%e`, `%E`</span><span class="sxs-lookup"><span data-stu-id="6cf3d-139">`%e`, `%E`</span></span>         | <span data-ttu-id="6cf3d-140">základní typ s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="6cf3d-140">a basic floating point type</span></span> | <span data-ttu-id="6cf3d-141">Formátováno jako podepsaná hodnota s formulářem, `[-]d.dddde[sign]ddd` kde d je jedna desítková číslice, dddd je jedna nebo více desítkových číslic, DDD je přesně tři desítkové číslice a znak je `+` nebo`-`</span><span class="sxs-lookup"><span data-stu-id="6cf3d-141">Formatted as a signed value having the form `[-]d.dddde[sign]ddd` where d is a single decimal digit, dddd is one or more decimal digits, ddd is exactly three decimal digits, and sign is `+` or `-`</span></span> |
| `%f`               | <span data-ttu-id="6cf3d-142">základní typ s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="6cf3d-142">a basic floating point type</span></span> | <span data-ttu-id="6cf3d-143">Formátováno jako podepsaná hodnota, která má formu `[-]dddd.dddd` , kde `dddd` je jedna nebo více desítkových číslic.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-143">Formatted as a signed value having the form `[-]dddd.dddd`, where `dddd` is one or more decimal digits.</span></span> <span data-ttu-id="6cf3d-144">Počet číslic před desetinnou čárkou závisí na velikosti čísla a počet číslic po desetinné čárkě závisí na požadované přesnosti.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-144">The number of digits before the decimal point depends on the magnitude of the number, and the number of digits after the decimal point depends on the requested precision.</span></span> |
| <span data-ttu-id="6cf3d-145">`%g`, `%G`</span><span class="sxs-lookup"><span data-stu-id="6cf3d-145">`%g`, `%G`</span></span> | <span data-ttu-id="6cf3d-146">základní typ s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="6cf3d-146">a basic floating point type</span></span> |  <span data-ttu-id="6cf3d-147">Formátováno pomocí formátu jako hodnota, která je vytištěna v `%f` nebo `%e` Format, podle toho, která je pro danou hodnotu a přesnost kompaktnější.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-147">Formatted using as a signed value printed in `%f` or `%e` format, whichever is more compact for the given value and precision.</span></span> |
| `%M` | <span data-ttu-id="6cf3d-148">`System.Decimal`hodnota</span><span class="sxs-lookup"><span data-stu-id="6cf3d-148">a `System.Decimal` value</span></span>  |    <span data-ttu-id="6cf3d-149">Formátování pomocí `"G"` specifikátoru formátu pro`System.Decimal.ToString(format)`</span><span class="sxs-lookup"><span data-stu-id="6cf3d-149">Formatted using the `"G"` format specifier for `System.Decimal.ToString(format)`</span></span> |
| `%O` | <span data-ttu-id="6cf3d-150">libovolná hodnota</span><span class="sxs-lookup"><span data-stu-id="6cf3d-150">any value</span></span>  |   <span data-ttu-id="6cf3d-151">Formátováno zabalením objektu a valling jeho `System.Object.ToString()` metody.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-151">Formatted by boxing the object and valling its `System.Object.ToString()` method</span></span> |
| `%A` | <span data-ttu-id="6cf3d-152">libovolná hodnota</span><span class="sxs-lookup"><span data-stu-id="6cf3d-152">any value</span></span>  |   <span data-ttu-id="6cf3d-153">Formátování pomocí [strukturovaného formátu prostého textu](plaintext-formatting.md) s výchozím nastavením rozložení</span><span class="sxs-lookup"><span data-stu-id="6cf3d-153">Formatted using [structured plain text formatting](plaintext-formatting.md) with the default layout settings</span></span> |
| `%a` | <span data-ttu-id="6cf3d-154">libovolná hodnota</span><span class="sxs-lookup"><span data-stu-id="6cf3d-154">any value</span></span>  |   <span data-ttu-id="6cf3d-155">Vyžaduje dva argumenty – funkce formátování přijímá kontextový parametr a hodnotu a určitou hodnotu pro tisk.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-155">Requires two arguments - a formatting function accepting a context parameter and the value, and the particular value to print</span></span> |
| `%t` | <span data-ttu-id="6cf3d-156">libovolná hodnota</span><span class="sxs-lookup"><span data-stu-id="6cf3d-156">any value</span></span>  |   <span data-ttu-id="6cf3d-157">Vyžaduje jeden argument, funkce formátování přijímá kontextový parametr, který buď výstup, nebo vrátí příslušný text.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-157">Requires one argument, a formatting function accepting a context parameter that either outputs or returns the appropriate text</span></span> |

<span data-ttu-id="6cf3d-158">Základní celočíselné typy jsou `byte` (), (), (), (), (), (), (), (), (), `System.Byte` `sbyte` `System.SByte` `int16` `System.Int16` `uint16` () `System.UInt16` `int32` `System.Int32` `uint32` `System.UInt32` `int64` `System.Int64` `uint64` `System.UInt64` `nativeint` `System.IntPtr` a `unativeint` ( `System.UIntPtr` ).</span><span class="sxs-lookup"><span data-stu-id="6cf3d-158">Basic integer types are `byte` (`System.Byte`), `sbyte` (`System.SByte`), `int16` (`System.Int16`), `uint16` (`System.UInt16`), `int32` (`System.Int32`), `uint32` (`System.UInt32`), `int64` (`System.Int64`), `uint64` (`System.UInt64`), `nativeint`  (`System.IntPtr`), and `unativeint`  (`System.UIntPtr`).</span></span>
<span data-ttu-id="6cf3d-159">Základní typy s plovoucí desetinnou čárkou jsou `float` ( `System.Double` ) a `float32` ( `System.Single` ).</span><span class="sxs-lookup"><span data-stu-id="6cf3d-159">Basic floating point types are `float` (`System.Double`) and `float32` (`System.Single`).</span></span>

<span data-ttu-id="6cf3d-160">Volitelná šířka je celé číslo označující minimální šířku výsledku.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-160">The optional width is an integer indicating the minimal width of the result.</span></span> <span data-ttu-id="6cf3d-161">Například `%6d` vytiskne celé číslo s předponou mezer, aby bylo možné vyplnit alespoň 6 znaků.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-161">For instance, `%6d` prints an integer, prefixing it with spaces to fill at least 6 characters.</span></span> <span data-ttu-id="6cf3d-162">Pokud je Width `*` , pak je proveden další celočíselný argument pro určení odpovídající šířky.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-162">If width is `*`, then an extra integer  argument is taken to specify the corresponding width.</span></span>

<span data-ttu-id="6cf3d-163">Platné příznaky:</span><span class="sxs-lookup"><span data-stu-id="6cf3d-163">Valid flags are:</span></span>

| <span data-ttu-id="6cf3d-164">Příznak</span><span class="sxs-lookup"><span data-stu-id="6cf3d-164">Flag</span></span>   | <span data-ttu-id="6cf3d-165">Účinek</span><span class="sxs-lookup"><span data-stu-id="6cf3d-165">Effect</span></span>        | <span data-ttu-id="6cf3d-166">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6cf3d-166">Remarks</span></span>                      |
|:-------------------|:---------------|:-----------------------------|
| `0`  | <span data-ttu-id="6cf3d-167">Místo mezer přidejte nuly, aby se zajistila požadovaná šířka.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-167">Add zeros instead of spaces to make up the required width</span></span> |    |
| `-` |  <span data-ttu-id="6cf3d-168">Vlevo zarovnat výsledek v zadané šířce</span><span class="sxs-lookup"><span data-stu-id="6cf3d-168">Left justify the result within the specified width</span></span> |   |
| `+`  | <span data-ttu-id="6cf3d-169">Přidejte `+` znak, pokud je číslo kladné (aby odpovídalo `-` znaménku pro záporné znaky).</span><span class="sxs-lookup"><span data-stu-id="6cf3d-169">Add a `+` character if the number is positive (to match a `-` sign for negatives)</span></span> |   |
| <span data-ttu-id="6cf3d-170">znak mezery</span><span class="sxs-lookup"><span data-stu-id="6cf3d-170">space character</span></span> | <span data-ttu-id="6cf3d-171">Přidejte mezeru navíc, pokud je číslo kladné (aby odpovídalo znaku '-' pro záporné znaky).</span><span class="sxs-lookup"><span data-stu-id="6cf3d-171">Add an extra space if the number is positive (to match a '-' sign for negatives)</span></span> |

<span data-ttu-id="6cf3d-172">Příznak printf `#` je neplatný a v případě, že se používá, bude hlášena chyba při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-172">The printf `#` flag is invalid and a compile-time error will be reported if it is used.</span></span>

<span data-ttu-id="6cf3d-173">Hodnoty jsou formátovány pomocí invariantní jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-173">Values are formatted using invariant culture.</span></span> <span data-ttu-id="6cf3d-174">Nastavení jazykové verze je nepodstatné pro `printf` formátování s výjimkou případů, kdy mají vliv na výsledky `%O` a `%A` formátování.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-174">Culture settings are irrelevant to `printf` formatting except when they affect the results of `%O` and `%A` formatting.</span></span> <span data-ttu-id="6cf3d-175">Další informace najdete v tématu [strukturované formátování prostého textu](plaintext-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="6cf3d-175">For more information, see [structured plain text formatting](plaintext-formatting.md).</span></span>

## <a name="a-formatting"></a><span data-ttu-id="6cf3d-176">`%A`kurzívy</span><span class="sxs-lookup"><span data-stu-id="6cf3d-176">`%A` formatting</span></span>

<span data-ttu-id="6cf3d-177">`%A`Specifikátor formátu slouží k formátování hodnot způsobem čitelným lidmi a může být také užitečný pro vytváření sestav diagnostických informací.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-177">The `%A` format specifier is used to format values in a human-readable way, and can also be useful for reporting diagnostic information.</span></span>

### <a name="primitive-values"></a><span data-ttu-id="6cf3d-178">Primitivní hodnoty</span><span class="sxs-lookup"><span data-stu-id="6cf3d-178">Primitive values</span></span>

<span data-ttu-id="6cf3d-179">Při formátování prostého textu pomocí `%A` specifikátoru jsou číselné hodnoty F # formátovány s jejich příponou a invariantní jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-179">When formatting plain text using the `%A` specifier, F# numeric values are formatted with their suffix and invariant culture.</span></span> <span data-ttu-id="6cf3d-180">Hodnoty s plovoucí desetinnou čárkou jsou formátovány pomocí 10 míst přesnosti s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-180">Floating point values are formatted using 10 places of floating point precision.</span></span> <span data-ttu-id="6cf3d-181">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6cf3d-181">For example,</span></span>

```fsharp
printfn "%A" (1L, 3n, 5u, 7, 4.03f, 5.000000001, 5.0000000001)
```

<span data-ttu-id="6cf3d-182">uslyší</span><span class="sxs-lookup"><span data-stu-id="6cf3d-182">produces</span></span>

```console
(1L, 3n, 5u, 7, 4.03000021f, 5.000000001, 5.0)
```

<span data-ttu-id="6cf3d-183">Při použití `%A` specifikátoru jsou řetězce formátovány pomocí uvozovek.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-183">When using the `%A` specifier, strings are formatted using quotes.</span></span> <span data-ttu-id="6cf3d-184">Řídicí kódy nejsou přidány a místo nich jsou vytištěny nezpracované znaky.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-184">Escape codes are not added and instead the raw characters are printed.</span></span> <span data-ttu-id="6cf3d-185">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6cf3d-185">For example,</span></span>

```fsharp
printfn "%A" ("abc", "a\tb\nc\"d")

```

<span data-ttu-id="6cf3d-186">uslyší</span><span class="sxs-lookup"><span data-stu-id="6cf3d-186">produces</span></span>

```console
("abc", "a      b
c"d")
```

### <a name="net-values"></a><span data-ttu-id="6cf3d-187">Hodnoty .NET</span><span class="sxs-lookup"><span data-stu-id="6cf3d-187">.NET values</span></span>

<span data-ttu-id="6cf3d-188">Při formátování prostého textu pomocí `%A` specifikátoru jsou objekty rozhraní .NET bez F # formátovány pomocí `x.ToString()` výchozího nastavení rozhraní .NET, které je zadáno pomocí `System.Globalization.CultureInfo.CurrentCulture` a `System.Globalization.CultureInfo.CurrentUICulture` .</span><span class="sxs-lookup"><span data-stu-id="6cf3d-188">When formatting plain text using the `%A` specifier, non-F# .NET objects are formatted by using `x.ToString()` using the default settings of .NET given by `System.Globalization.CultureInfo.CurrentCulture` and `System.Globalization.CultureInfo.CurrentUICulture`.</span></span>  <span data-ttu-id="6cf3d-189">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6cf3d-189">For example,</span></span>

```fsharp
open System.Globalization

let date = System.DateTime(1999, 12, 31)

CultureInfo.CurrentCulture <- CultureInfo.GetCultureInfo("de-DE")
printfn "Culture 1: %A" date

CultureInfo.CurrentCulture <- CultureInfo.GetCultureInfo("en-US")
printfn "Culture 2: %A" date
```

<span data-ttu-id="6cf3d-190">uslyší</span><span class="sxs-lookup"><span data-stu-id="6cf3d-190">produces</span></span>

```console
Culture 1: 31.12.1999 00:00:00
Culture 2: 12/31/1999 12:00:00 AM
```

### <a name="structured-values"></a><span data-ttu-id="6cf3d-191">Strukturované hodnoty</span><span class="sxs-lookup"><span data-stu-id="6cf3d-191">Structured values</span></span>

<span data-ttu-id="6cf3d-192">Při formátování prostého textu pomocí `%A` specifikátoru se pro seznamy F # a n-tice použije blokové odsazení.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-192">When formatting plain text using the `%A` specifier, block indentation is used for F# lists and tuples.</span></span> <span data-ttu-id="6cf3d-193">Je zobrazen v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-193">The is shown in the previous example.</span></span>
<span data-ttu-id="6cf3d-194">Také se používá struktura polí včetně multidimenzionálních polí.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-194">The structure of arrays is also used, including multi-dimensional arrays.</span></span>  <span data-ttu-id="6cf3d-195">Jednorozměrná pole se zobrazují se `[| ... |]` syntaxí.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-195">Single-dimensional arrays are shown with `[| ... |]` syntax.</span></span> <span data-ttu-id="6cf3d-196">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6cf3d-196">For example,</span></span>

```fsharp
printfn "%A" [| for i in 1 .. 20 -> (i, i*i) |]
```

<span data-ttu-id="6cf3d-197">uslyší</span><span class="sxs-lookup"><span data-stu-id="6cf3d-197">produces</span></span>

```console
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25); (6, 36); (7, 49); (8, 64); (9, 81);
  (10, 100); (11, 121); (12, 144); (13, 169); (14, 196); (15, 225); (16, 256);
  (17, 289); (18, 324); (19, 361); (20, 400)|]
```

<span data-ttu-id="6cf3d-198">Výchozí šířka tisku je 80.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-198">The default print width is 80.</span></span>  <span data-ttu-id="6cf3d-199">Tuto šířku lze přizpůsobit pomocí šířky tisku ve specifikátoru formátu.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-199">This width can be customized by using a print width in the format specifier.</span></span> <span data-ttu-id="6cf3d-200">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6cf3d-200">For example,</span></span>

```fsharp
printfn "%10A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%20A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%50A" [| for i in 1 .. 5 -> (i, i*i) |]
```

<span data-ttu-id="6cf3d-201">uslyší</span><span class="sxs-lookup"><span data-stu-id="6cf3d-201">produces</span></span>

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

<span data-ttu-id="6cf3d-202">Zadání šířky tisku 0 způsobí, že se nepoužívá žádná šířka tisku.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-202">Specifying a print width of 0 results in no print width being used.</span></span> <span data-ttu-id="6cf3d-203">Výsledkem bude jeden řádek textu s výjimkou případů, kdy vložené řetězce ve výstupu samotné obsahují linebreaks.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-203">A single line of text will result, except where embedded strings in the output themselves contain linebreaks.</span></span>  <span data-ttu-id="6cf3d-204">Například</span><span class="sxs-lookup"><span data-stu-id="6cf3d-204">For example</span></span>

```fsharp
printfn "%0A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%0A" [| for i in 1 .. 5 -> "abc\ndef |]
```

<span data-ttu-id="6cf3d-205">uslyší</span><span class="sxs-lookup"><span data-stu-id="6cf3d-205">produces</span></span>

```console
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25)|]
[|"abc
def"; "abc
def"; "abc
def"; "abc
def"; "abc
def"|]
```

<span data-ttu-id="6cf3d-206">Pro hodnoty Sequence () se používá limit hloubky 4 `IEnumerable` , který se zobrazuje jako `seq { ...}` .</span><span class="sxs-lookup"><span data-stu-id="6cf3d-206">A depth limit of 4 is used for sequence (`IEnumerable`) values, which are shown as `seq { ...}`.</span></span> <span data-ttu-id="6cf3d-207">Pro hodnoty list a Array se používá limit hloubky 100.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-207">A depth limit of 100 is used for list and array values.</span></span>
<span data-ttu-id="6cf3d-208">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6cf3d-208">For example,</span></span>

```fsharp
printfn "%A" (seq { for i in 1 .. 10 -> (i, i*i) })
```

<span data-ttu-id="6cf3d-209">uslyší</span><span class="sxs-lookup"><span data-stu-id="6cf3d-209">produces</span></span>

```console
seq [(1, 1); (2, 4); (3, 9); (4, 16); ...]
```

<span data-ttu-id="6cf3d-210">Pro strukturu hodnot veřejného záznamu a sjednocení se používá také odsazení bloku.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-210">Block indentation is also used for the the structure of public record and union values.</span></span> <span data-ttu-id="6cf3d-211">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6cf3d-211">For example,</span></span>

```fsharp
type R = { X : int list; Y : string list }

printfn "%A" { X =  [ 1;2;3 ]; Y = ["one"; "two"; "three"] }
```

<span data-ttu-id="6cf3d-212">uslyší</span><span class="sxs-lookup"><span data-stu-id="6cf3d-212">produces</span></span>

```console
{ X = [1; 2; 3]
  Y = ["one"; "two"; "three"] }
```

<span data-ttu-id="6cf3d-213">Pokud `%+A` se používá, pak je soukromá struktura záznamů a sjednocení také odhalena pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-213">If `%+A` is used, then the private structure of records and unions is also revealed by using reflection.</span></span> <span data-ttu-id="6cf3d-214">Například</span><span class="sxs-lookup"><span data-stu-id="6cf3d-214">For example</span></span>

```fsharp
type internal R =
    { X : int list; Y : string list }
    override _.ToString() = "R"

let internal data = { X = [ 1;2;3 ]; Y = ["one"; "two"; "three"] }

printfn "external view:\n%A" data

printfn "internal view:\n%+A" data

```

<span data-ttu-id="6cf3d-215">uslyší</span><span class="sxs-lookup"><span data-stu-id="6cf3d-215">produces</span></span>

```console
external view:
R

internal view:
{ X = [1; 2; 3]
  Y = ["one"; "two"; "three"] }
```

### <a name="large-cyclic-or-deeply-nested-values"></a><span data-ttu-id="6cf3d-216">Velké, cyklické nebo hluboko vnořené hodnoty</span><span class="sxs-lookup"><span data-stu-id="6cf3d-216">Large, cyclic, or deeply nested values</span></span>

<span data-ttu-id="6cf3d-217">Velké strukturované hodnoty jsou formátovány na maximální celkový počet uzlů objektu 10000.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-217">Large structured values are formatted to a maximum overall object node count of 10000.</span></span>
<span data-ttu-id="6cf3d-218">Hluboko vnořené hodnoty jsou formátovány na hloubku 100.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-218">Deeply nested values are formatted to a depth of 100.</span></span>  <span data-ttu-id="6cf3d-219">V obou případech `...` slouží k elideí některých výstupů.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-219">In both cases `...` is used to elide some of the output.</span></span>  <span data-ttu-id="6cf3d-220">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6cf3d-220">For example,</span></span>

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

<span data-ttu-id="6cf3d-221">Vytvoří velký výstup s některými částmi vynechaného Copy:</span><span class="sxs-lookup"><span data-stu-id="6cf3d-221">produces a large output with some parts elided:</span></span>

```console
Node(Tip, Node(Tip, ....Node (..., ...)...))
```

<span data-ttu-id="6cf3d-222">V grafech objektů jsou zjištěny cykly, `...` které se používají na místech, kde jsou zjištěny cykly.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-222">Cycles are detected in the object graphs and `...` is used at places where cycles are detected.</span></span> <span data-ttu-id="6cf3d-223">Například</span><span class="sxs-lookup"><span data-stu-id="6cf3d-223">For example</span></span>

```fsharp
type R = { mutable Links: R list }
let r = { Links = [] }
r.Links <- [r]
printfn "%A" r
```

<span data-ttu-id="6cf3d-224">uslyší</span><span class="sxs-lookup"><span data-stu-id="6cf3d-224">produces</span></span>

```console
{ Links = [...] }
```

### <a name="lazy-null-and-function-values"></a><span data-ttu-id="6cf3d-225">Opožděné, null a hodnoty funkcí</span><span class="sxs-lookup"><span data-stu-id="6cf3d-225">Lazy, null, and function values</span></span>

<span data-ttu-id="6cf3d-226">Opožděné hodnoty jsou vytištěny jako `Value is not created` nebo ekvivalentní text, pokud hodnota ještě nebyla vyhodnocena.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-226">Lazy values are printed as `Value is not created` or equivalent text when the value has not yet been evaluated.</span></span>

<span data-ttu-id="6cf3d-227">Hodnoty null jsou vytištěny, `null` dokud není statický typ hodnoty určen jako typ sjednocení, kde `null` je povolený represenation.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-227">Null values are printed as `null` unless the static type of the value is determined to be a union type where `null` is a permitted represenation.</span></span>

<span data-ttu-id="6cf3d-228">Hodnoty funkcí F # jsou vytištěny jako název vnitřně generovaného uzavření, například `<fun:it@43-7>` .</span><span class="sxs-lookup"><span data-stu-id="6cf3d-228">F# function values are printed as their internally generated closure name, for example, `<fun:it@43-7>`.</span></span>

### <a name="customize-plain-text-formatting-with-structuredformatdisplay"></a><span data-ttu-id="6cf3d-229">Přizpůsobení formátování prostého textu pomocí`StructuredFormatDisplay`</span><span class="sxs-lookup"><span data-stu-id="6cf3d-229">Customize plain text formatting with `StructuredFormatDisplay`</span></span>

<span data-ttu-id="6cf3d-230">Při použití `%A` specifikátoru `StructuredFormatDisplay` je respektována přítomnost atributu v deklaracích typů.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-230">When using the `%A` specifier, the presence of the `StructuredFormatDisplay` attribute on type declarations is respected.</span></span>  <span data-ttu-id="6cf3d-231">Dá se použít k zadání náhradního textu a vlastnosti k zobrazení hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-231">This can be used to specify surrogate text and property to display a value.</span></span> <span data-ttu-id="6cf3d-232">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6cf3d-232">For example:</span></span>

```fsharp
[<StructuredFormatDisplay("Counts({Clicks})")>]
type Counts = { Clicks:int list}

printfn "%20A" {Clicks=[0..20]}
```

<span data-ttu-id="6cf3d-233">uslyší</span><span class="sxs-lookup"><span data-stu-id="6cf3d-233">produces</span></span>

```console
Counts([0; 1; 2; 3;
        4; 5; 6; 7;
        8; 9; 10; 11;
        12; 13; 14;
        15; 16; 17;
        18; 19; 20])
```

### <a name="customize-plain-text-formatting-by-overriding-tostring"></a><span data-ttu-id="6cf3d-234">Přizpůsobení formátování prostého textu přepsáním`ToString`</span><span class="sxs-lookup"><span data-stu-id="6cf3d-234">Customize plain text formatting by overriding `ToString`</span></span>

<span data-ttu-id="6cf3d-235">Výchozí implementace `ToString` je v programování F # pozorovatelná.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-235">The default implementation of `ToString` is observable in F# programming.</span></span> <span data-ttu-id="6cf3d-236">Výchozí výsledky nejsou často vhodné pro použití ve formě zobrazení informací nebo v uživatelském výstupu, a v důsledku toho je běžné přepsat výchozí implementaci.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-236">Often, the default results aren't suitable for use in either programmer-facing information display or user output, and as a result it is common to override the default implementation.</span></span>  

<span data-ttu-id="6cf3d-237">Ve výchozím nastavení typy záznamu a sjednocení jazyka F # přepisují implementaci `ToString` s implementací, kterou používá `sprintf "%+A"` .</span><span class="sxs-lookup"><span data-stu-id="6cf3d-237">By default, F# record and union types override the implementation of `ToString` with an implementation that uses `sprintf "%+A"`.</span></span>  <span data-ttu-id="6cf3d-238">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6cf3d-238">For example,</span></span>

```fsharp
type Counts = { Clicks:int list }

printfn "%s" ({Clicks=[0..10]}.ToString())
```

<span data-ttu-id="6cf3d-239">uslyší</span><span class="sxs-lookup"><span data-stu-id="6cf3d-239">produces</span></span>

```console
{ Clicks = [0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10] }
```

<span data-ttu-id="6cf3d-240">U typů tříd není k dispozici žádná výchozí implementace `ToString` a použije se výchozí rozhraní .NET, které hlásí název typu.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-240">For class types, no default implementation of `ToString` is provided and the .NET default is used, which reports the name of the type.</span></span> <span data-ttu-id="6cf3d-241">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6cf3d-241">For example,</span></span>

```fsharp
type MyClassType(clicks: int list) =
   member _.Clicks = clicks

let data = [ MyClassType([1..5]); MyClassType([1..5]) ]
printfn "Default structured print gives this:\n%A" data
printfn "Default ToString gives:\n%s" (data.ToString())
```

<span data-ttu-id="6cf3d-242">uslyší</span><span class="sxs-lookup"><span data-stu-id="6cf3d-242">produces</span></span>

```console
Default structured print gives this:
[MyClassType; MyClassType]
Default ToString gives:
[MyClassType; MyClassType]
```

<span data-ttu-id="6cf3d-243">Přidání přepsání pro `ToString` může mít lepší formátování.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-243">Adding an override for `ToString` can give better formatting.</span></span>

```fsharp
type MyClassType(clicks: int list) =
   member _.Clicks = clicks
   override _.ToString() = sprintf "MyClassType(%0A)" clicks

let data = [ MyClassType([1..5]); MyClassType([1..5]) ]
printfn "Now structured print gives this:\n%A" data
printfn "Now ToString gives:\n%s" (data.ToString())
```

<span data-ttu-id="6cf3d-244">uslyší</span><span class="sxs-lookup"><span data-stu-id="6cf3d-244">produces</span></span>

```console
Now structured print gives this:
[MyClassType([1; 2; 3; 4; 5]); MyClassType([1; 2; 3; 4; 5])]
Now ToString gives:
[MyClassType([1; 2; 3; 4; 5]); MyClassType([1; 2; 3; 4; 5])]
```

## <a name="f-interactive-structured-printing"></a><span data-ttu-id="6cf3d-245">F# Interactive strukturovaný tisk</span><span class="sxs-lookup"><span data-stu-id="6cf3d-245">F# Interactive structured printing</span></span>

<span data-ttu-id="6cf3d-246">F# Interactive ( `dotnet fsi` ) používá rozšířenou verzi strukturovaného formátování prostého textu k vykazování hodnot a umožňuje dodatečnou možnost úprav.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-246">F# Interactive (`dotnet fsi`) uses an extended version of structured plain text formatting to report values and allows additional customizability.</span></span> <span data-ttu-id="6cf3d-247">Další informace najdete v tématu [F# Interactive](fsharp-interactive-options.md).</span><span class="sxs-lookup"><span data-stu-id="6cf3d-247">For more information, see [F# Interactive](fsharp-interactive-options.md).</span></span>

## <a name="customize-debug-displays"></a><span data-ttu-id="6cf3d-248">Přizpůsobení zobrazení ladění</span><span class="sxs-lookup"><span data-stu-id="6cf3d-248">Customize debug displays</span></span>

<span data-ttu-id="6cf3d-249">Ladicí programy pro .NET respektují použití atributů jako `DebuggerDisplay` a a `DebuggerTypeProxy` mají vliv na strukturované zobrazení objektů v oknech pro kontrolu ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-249">Debuggers for .NET respect the use of attributes such as `DebuggerDisplay` and `DebuggerTypeProxy`, and these affect the structured display of objects in debugger inspection windows.</span></span>
<span data-ttu-id="6cf3d-250">Kompilátor jazyka F # automaticky vygeneroval tyto atributy pro rozlišené typy sjednocení a záznamů, ale ne typy třídy, rozhraní nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-250">The F# compiler automatically generated these attributes for discriminated union and record types, but not class, interface, or struct types.</span></span>

<span data-ttu-id="6cf3d-251">Tyto atributy jsou ignorovány ve formátu prostého textu F #, ale mohou být užitečné při implementaci těchto metod pro zlepšení zobrazení při ladění typů F #.</span><span class="sxs-lookup"><span data-stu-id="6cf3d-251">These attributes are ignored in F# plain text formatting, but it can be useful to implement these methods to improve displays when debugging F# types.</span></span>

## <a name="see-also"></a><span data-ttu-id="6cf3d-252">Viz také</span><span class="sxs-lookup"><span data-stu-id="6cf3d-252">See also</span></span>

- [<span data-ttu-id="6cf3d-253">Řetězce</span><span class="sxs-lookup"><span data-stu-id="6cf3d-253">Strings</span></span>](strings.md)
- [<span data-ttu-id="6cf3d-254">Záznamy</span><span class="sxs-lookup"><span data-stu-id="6cf3d-254">Records</span></span>](records.md)
- [<span data-ttu-id="6cf3d-255">Rozlišovaná sjednocení</span><span class="sxs-lookup"><span data-stu-id="6cf3d-255">Discriminated Unions</span></span>](discriminated-unions.md)
- [<span data-ttu-id="6cf3d-256">F# Interactive</span><span class="sxs-lookup"><span data-stu-id="6cf3d-256">F# Interactive</span></span>](fsharp-interactive-options.md)
