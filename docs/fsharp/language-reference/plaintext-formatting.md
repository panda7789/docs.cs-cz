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
# <a name="plain-text-formatting"></a>Formátování prostého textu

Jazyk F # podporuje formátování prostého textu se zaškrtnutým typem `printf` , a to pomocí `printfn` souvisejících funkcí,, `sprintf` a.
Příklad:

```console
dotnet fsi

> printfn "Hello %s, %d + %d is %d" "world" 2 2 (2+2);;
```

poskytne výstup

```fsharp
Hello world, 2 + 2 is 4
```

Jazyk F # také umožňuje formátování strukturovaných hodnot jako prostý text.
Zvažte například následující příklad, který formátuje výstup jako zobrazení řazených kolekcí členů jako matice.

```console
dotnet fsi

> printfn "%A" [ for i in 1 .. 5 -> [ for j in 1 .. 5 -> (i, j) ] ];;

[[(1, 1); (1, 2); (1, 3); (1, 4); (1, 5)];
 [(2, 1); (2, 2); (2, 3); (2, 4); (2, 5)];
 [(3, 1); (3, 2); (3, 3); (3, 4); (3, 5)];
 [(4, 1); (4, 2); (4, 3); (4, 4); (4, 5)];
 [(5, 1); (5, 2); (5, 3); (5, 4); (5, 5)]]
```

Strukturované formátování prostého textu je aktivováno při použití `%A` formátu při `printf` formátování řetězců.
Aktivuje se také při formátování výstupu hodnot v F # Interactive, kde výstup zahrnuje další informace a je navíc přizpůsobitelná.
Formátování prostého textu je také možné pozorovat prostřednictvím jakýchkoli volání `x.ToString()` na základě sjednocení F # a záznamů, včetně těch, které se vyskytují implicitně v ladění, protokolování a dalších nástrojích.

## <a name="checking-of-printf-format-strings"></a>Kontrola `printf` formátovacích řetězců

Pokud `printf` se funkce formátování používá s argumentem, který se neshoduje s specifikátory formátu printf ve formátu řetězce, bude zaznamenána chyba při kompilaci.  Příklad:

```fsharp
sprintf "Hello %s" (2+2)
```

poskytne výstup

```console
  sprintf "Hello %s" (2+2)
  ----------------------^

stdin(3,25): error FS0001: The type 'string' does not match the type 'int'
```

Technicky řečeno, při použití `printf` a dalších souvisejících funkcích kontroluje zvláštní pravidlo v kompilátoru F # řetězcový literál předaný jako formátovací řetězec, který zajišťuje, že následné použité argumenty jsou správného typu, aby se shodovaly s použitými specifikátory formátu.

## <a name="format-specifiers-for-printf"></a>Specifikátory formátu pro`printf`

Specifikace formátu pro `printf` formáty jsou řetězce se `%` značkami, které označují formát. Zástupné symboly formátu `%[flags][width][.precision][type]` se skládají z místa, kde je typ interpretován takto:

| Specifikátor formátu   | Typ (y)        | Poznámky                      |
|:-------------------|:---------------|:-----------------------------|
| `%b`               | bool      | Formátováno jako `true` nebo`false`                |
| `%s`               | řetězec    | Formátováno jako jeho neřídicí obsah         |
| `%c`               | char      | Formátováno jako znakový literál  |
| `%d`, `%i`         | základní celočíselný typ | Formátováno jako desítkové celé číslo, podepsané, pokud je základní celočíselný typ podepsán |
| `%u`               | základní celočíselný typ | Formátováno jako desítkové celé číslo bez znaménka   |
| `%x`, `%X`         | základní celočíselný typ | Formátováno jako šestnáctkové číslo bez znaménka (a-f nebo A-F pro šestnáctkové číslice v uvedeném pořadí)  |
|  `%o`              | základní celočíselný typ | Formátováno jako osmičkové číslo bez znaménka. |
| `%e`, `%E`         | základní typ s plovoucí desetinnou čárkou | Formátováno jako podepsaná hodnota s formulářem, `[-]d.dddde[sign]ddd` kde d je jedna desítková číslice, dddd je jedna nebo více desítkových číslic, DDD je přesně tři desítkové číslice a znak je `+` nebo`-` |
| `%f`               | základní typ s plovoucí desetinnou čárkou | Formátováno jako podepsaná hodnota, která má formu `[-]dddd.dddd` , kde `dddd` je jedna nebo více desítkových číslic. Počet číslic před desetinnou čárkou závisí na velikosti čísla a počet číslic po desetinné čárkě závisí na požadované přesnosti. |
| `%g`, `%G` | základní typ s plovoucí desetinnou čárkou |  Formátováno pomocí formátu jako hodnota, která je vytištěna v `%f` nebo `%e` Format, podle toho, která je pro danou hodnotu a přesnost kompaktnější. |
| `%M` | `System.Decimal`hodnota  |    Formátování pomocí `"G"` specifikátoru formátu pro`System.Decimal.ToString(format)` |
| `%O` | libovolná hodnota  |   Formátováno zabalením objektu a valling jeho `System.Object.ToString()` metody. |
| `%A` | libovolná hodnota  |   Formátování pomocí [strukturovaného formátu prostého textu](plaintext-formatting.md) s výchozím nastavením rozložení |
| `%a` | libovolná hodnota  |   Vyžaduje dva argumenty – funkce formátování přijímá kontextový parametr a hodnotu a určitou hodnotu pro tisk. |
| `%t` | libovolná hodnota  |   Vyžaduje jeden argument, funkce formátování přijímá kontextový parametr, který buď výstup, nebo vrátí příslušný text. |

Základní celočíselné typy jsou `byte` (), (), (), (), (), (), (), (), (), `System.Byte` `sbyte` `System.SByte` `int16` `System.Int16` `uint16` () `System.UInt16` `int32` `System.Int32` `uint32` `System.UInt32` `int64` `System.Int64` `uint64` `System.UInt64` `nativeint` `System.IntPtr` a `unativeint` ( `System.UIntPtr` ).
Základní typy s plovoucí desetinnou čárkou jsou `float` ( `System.Double` ) a `float32` ( `System.Single` ).

Volitelná šířka je celé číslo označující minimální šířku výsledku. Například `%6d` vytiskne celé číslo s předponou mezer, aby bylo možné vyplnit alespoň 6 znaků. Pokud je Width `*` , pak je proveden další celočíselný argument pro určení odpovídající šířky.

Platné příznaky:

| Příznak   | Účinek        | Poznámky                      |
|:-------------------|:---------------|:-----------------------------|
| `0`  | Místo mezer přidejte nuly, aby se zajistila požadovaná šířka. |    |
| `-` |  Vlevo zarovnat výsledek v zadané šířce |   |
| `+`  | Přidejte `+` znak, pokud je číslo kladné (aby odpovídalo `-` znaménku pro záporné znaky). |   |
| znak mezery | Přidejte mezeru navíc, pokud je číslo kladné (aby odpovídalo znaku '-' pro záporné znaky). |

Příznak printf `#` je neplatný a v případě, že se používá, bude hlášena chyba při kompilaci.

Hodnoty jsou formátovány pomocí invariantní jazykové verze. Nastavení jazykové verze je nepodstatné pro `printf` formátování s výjimkou případů, kdy mají vliv na výsledky `%O` a `%A` formátování. Další informace najdete v tématu [strukturované formátování prostého textu](plaintext-formatting.md).

## <a name="a-formatting"></a>`%A`kurzívy

`%A`Specifikátor formátu slouží k formátování hodnot způsobem čitelným lidmi a může být také užitečný pro vytváření sestav diagnostických informací.

### <a name="primitive-values"></a>Primitivní hodnoty

Při formátování prostého textu pomocí `%A` specifikátoru jsou číselné hodnoty F # formátovány s jejich příponou a invariantní jazykové verze. Hodnoty s plovoucí desetinnou čárkou jsou formátovány pomocí 10 míst přesnosti s plovoucí desetinnou čárkou. Příklad:

```fsharp
printfn "%A" (1L, 3n, 5u, 7, 4.03f, 5.000000001, 5.0000000001)
```

uslyší

```console
(1L, 3n, 5u, 7, 4.03000021f, 5.000000001, 5.0)
```

Při použití `%A` specifikátoru jsou řetězce formátovány pomocí uvozovek. Řídicí kódy nejsou přidány a místo nich jsou vytištěny nezpracované znaky. Příklad:

```fsharp
printfn "%A" ("abc", "a\tb\nc\"d")

```

uslyší

```console
("abc", "a      b
c"d")
```

### <a name="net-values"></a>Hodnoty .NET

Při formátování prostého textu pomocí `%A` specifikátoru jsou objekty rozhraní .NET bez F # formátovány pomocí `x.ToString()` výchozího nastavení rozhraní .NET, které je zadáno pomocí `System.Globalization.CultureInfo.CurrentCulture` a `System.Globalization.CultureInfo.CurrentUICulture` .  Příklad:

```fsharp
open System.Globalization

let date = System.DateTime(1999, 12, 31)

CultureInfo.CurrentCulture <- CultureInfo.GetCultureInfo("de-DE")
printfn "Culture 1: %A" date

CultureInfo.CurrentCulture <- CultureInfo.GetCultureInfo("en-US")
printfn "Culture 2: %A" date
```

uslyší

```console
Culture 1: 31.12.1999 00:00:00
Culture 2: 12/31/1999 12:00:00 AM
```

### <a name="structured-values"></a>Strukturované hodnoty

Při formátování prostého textu pomocí `%A` specifikátoru se pro seznamy F # a n-tice použije blokové odsazení. Je zobrazen v předchozím příkladu.
Také se používá struktura polí včetně multidimenzionálních polí.  Jednorozměrná pole se zobrazují se `[| ... |]` syntaxí. Příklad:

```fsharp
printfn "%A" [| for i in 1 .. 20 -> (i, i*i) |]
```

uslyší

```console
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25); (6, 36); (7, 49); (8, 64); (9, 81);
  (10, 100); (11, 121); (12, 144); (13, 169); (14, 196); (15, 225); (16, 256);
  (17, 289); (18, 324); (19, 361); (20, 400)|]
```

Výchozí šířka tisku je 80.  Tuto šířku lze přizpůsobit pomocí šířky tisku ve specifikátoru formátu. Příklad:

```fsharp
printfn "%10A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%20A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%50A" [| for i in 1 .. 5 -> (i, i*i) |]
```

uslyší

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

Zadání šířky tisku 0 způsobí, že se nepoužívá žádná šířka tisku. Výsledkem bude jeden řádek textu s výjimkou případů, kdy vložené řetězce ve výstupu samotné obsahují linebreaks.  Například

```fsharp
printfn "%0A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%0A" [| for i in 1 .. 5 -> "abc\ndef |]
```

uslyší

```console
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25)|]
[|"abc
def"; "abc
def"; "abc
def"; "abc
def"; "abc
def"|]
```

Pro hodnoty Sequence () se používá limit hloubky 4 `IEnumerable` , který se zobrazuje jako `seq { ...}` . Pro hodnoty list a Array se používá limit hloubky 100.
Příklad:

```fsharp
printfn "%A" (seq { for i in 1 .. 10 -> (i, i*i) })
```

uslyší

```console
seq [(1, 1); (2, 4); (3, 9); (4, 16); ...]
```

Pro strukturu hodnot veřejného záznamu a sjednocení se používá také odsazení bloku. Příklad:

```fsharp
type R = { X : int list; Y : string list }

printfn "%A" { X =  [ 1;2;3 ]; Y = ["one"; "two"; "three"] }
```

uslyší

```console
{ X = [1; 2; 3]
  Y = ["one"; "two"; "three"] }
```

Pokud `%+A` se používá, pak je soukromá struktura záznamů a sjednocení také odhalena pomocí reflexe. Například

```fsharp
type internal R =
    { X : int list; Y : string list }
    override _.ToString() = "R"

let internal data = { X = [ 1;2;3 ]; Y = ["one"; "two"; "three"] }

printfn "external view:\n%A" data

printfn "internal view:\n%+A" data

```

uslyší

```console
external view:
R

internal view:
{ X = [1; 2; 3]
  Y = ["one"; "two"; "three"] }
```

### <a name="large-cyclic-or-deeply-nested-values"></a>Velké, cyklické nebo hluboko vnořené hodnoty

Velké strukturované hodnoty jsou formátovány na maximální celkový počet uzlů objektu 10000.
Hluboko vnořené hodnoty jsou formátovány na hloubku 100.  V obou případech `...` slouží k elideí některých výstupů.  Příklad:

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

Vytvoří velký výstup s některými částmi vynechaného Copy:

```console
Node(Tip, Node(Tip, ....Node (..., ...)...))
```

V grafech objektů jsou zjištěny cykly, `...` které se používají na místech, kde jsou zjištěny cykly. Například

```fsharp
type R = { mutable Links: R list }
let r = { Links = [] }
r.Links <- [r]
printfn "%A" r
```

uslyší

```console
{ Links = [...] }
```

### <a name="lazy-null-and-function-values"></a>Opožděné, null a hodnoty funkcí

Opožděné hodnoty jsou vytištěny jako `Value is not created` nebo ekvivalentní text, pokud hodnota ještě nebyla vyhodnocena.

Hodnoty null jsou vytištěny, `null` dokud není statický typ hodnoty určen jako typ sjednocení, kde `null` je povolený represenation.

Hodnoty funkcí F # jsou vytištěny jako název vnitřně generovaného uzavření, například `<fun:it@43-7>` .

### <a name="customize-plain-text-formatting-with-structuredformatdisplay"></a>Přizpůsobení formátování prostého textu pomocí`StructuredFormatDisplay`

Při použití `%A` specifikátoru `StructuredFormatDisplay` je respektována přítomnost atributu v deklaracích typů.  Dá se použít k zadání náhradního textu a vlastnosti k zobrazení hodnoty. Příklad:

```fsharp
[<StructuredFormatDisplay("Counts({Clicks})")>]
type Counts = { Clicks:int list}

printfn "%20A" {Clicks=[0..20]}
```

uslyší

```console
Counts([0; 1; 2; 3;
        4; 5; 6; 7;
        8; 9; 10; 11;
        12; 13; 14;
        15; 16; 17;
        18; 19; 20])
```

### <a name="customize-plain-text-formatting-by-overriding-tostring"></a>Přizpůsobení formátování prostého textu přepsáním`ToString`

Výchozí implementace `ToString` je v programování F # pozorovatelná. Výchozí výsledky nejsou často vhodné pro použití ve formě zobrazení informací nebo v uživatelském výstupu, a v důsledku toho je běžné přepsat výchozí implementaci.  

Ve výchozím nastavení typy záznamu a sjednocení jazyka F # přepisují implementaci `ToString` s implementací, kterou používá `sprintf "%+A"` .  Příklad:

```fsharp
type Counts = { Clicks:int list }

printfn "%s" ({Clicks=[0..10]}.ToString())
```

uslyší

```console
{ Clicks = [0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10] }
```

U typů tříd není k dispozici žádná výchozí implementace `ToString` a použije se výchozí rozhraní .NET, které hlásí název typu. Příklad:

```fsharp
type MyClassType(clicks: int list) =
   member _.Clicks = clicks

let data = [ MyClassType([1..5]); MyClassType([1..5]) ]
printfn "Default structured print gives this:\n%A" data
printfn "Default ToString gives:\n%s" (data.ToString())
```

uslyší

```console
Default structured print gives this:
[MyClassType; MyClassType]
Default ToString gives:
[MyClassType; MyClassType]
```

Přidání přepsání pro `ToString` může mít lepší formátování.

```fsharp
type MyClassType(clicks: int list) =
   member _.Clicks = clicks
   override _.ToString() = sprintf "MyClassType(%0A)" clicks

let data = [ MyClassType([1..5]); MyClassType([1..5]) ]
printfn "Now structured print gives this:\n%A" data
printfn "Now ToString gives:\n%s" (data.ToString())
```

uslyší

```console
Now structured print gives this:
[MyClassType([1; 2; 3; 4; 5]); MyClassType([1; 2; 3; 4; 5])]
Now ToString gives:
[MyClassType([1; 2; 3; 4; 5]); MyClassType([1; 2; 3; 4; 5])]
```

## <a name="f-interactive-structured-printing"></a>F# Interactive strukturovaný tisk

F# Interactive ( `dotnet fsi` ) používá rozšířenou verzi strukturovaného formátování prostého textu k vykazování hodnot a umožňuje dodatečnou možnost úprav. Další informace najdete v tématu [F# Interactive](fsharp-interactive-options.md).

## <a name="customize-debug-displays"></a>Přizpůsobení zobrazení ladění

Ladicí programy pro .NET respektují použití atributů jako `DebuggerDisplay` a a `DebuggerTypeProxy` mají vliv na strukturované zobrazení objektů v oknech pro kontrolu ladicího programu.
Kompilátor jazyka F # automaticky vygeneroval tyto atributy pro rozlišené typy sjednocení a záznamů, ale ne typy třídy, rozhraní nebo struktury.

Tyto atributy jsou ignorovány ve formátu prostého textu F #, ale mohou být užitečné při implementaci těchto metod pro zlepšení zobrazení při ladění typů F #.

## <a name="see-also"></a>Viz také

- [Řetězce](strings.md)
- [Záznamy](records.md)
- [Rozlišovaná sjednocení](discriminated-unions.md)
- [F# Interactive](fsharp-interactive-options.md)
