---
title: Aktivní vzorky
description: Zjistěte, jak pomocí aktivních vzorů definovat pojmenované oddíly, které rozdělují vstupní data v programovacím jazyce F#.
ms.date: 05/16/2016
ms.openlocfilehash: 898ef201369683bfd49d53e863e86f919f5837fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187062"
---
# <a name="active-patterns"></a>Aktivní vzorky

*Aktivní vzorky* umožňují definovat pojmenované oddíly, které rozdělují vstupní data, takže tyto názvy můžete použít ve výrazu porovnávání vzorů stejně jako pro discriminated sjednocení. Aktivní vzorky můžete použít k rozkladu dat přizpůsobeným způsobem pro každý oddíl.

## <a name="syntax"></a>Syntaxe

```fsharp
// Active pattern of one choice.
let (|identifier|) [arguments] valueToMatch= expression

// Active Pattern with multiple choices.
// Uses a FSharp.Core.Choice<_,...,_> based on the number of case names. In F#, the limitation n <= 7 applies.
let (|identifer1|identifier2|...|) valueToMatch = expression

// Partial active pattern definition.
// Uses a FSharp.Core.option<_> to represent if the type is satisfied at the call site.
let (|identifier|_|) [arguments ] valueToMatch = expression
```

## <a name="remarks"></a>Poznámky

V předchozí syntaxi jsou identifikátory názvy oddílů vstupních dat, které jsou reprezentovány argumenty , nebo jinými slovy *názvy*podmnožiny sady všech hodnot argumentů. V definici aktivního vzoru může být až sedm oddílů. *Výraz* popisuje formulář, do kterého chcete rozložit data. Pomocí definice aktivního vzoru můžete definovat pravidla pro určení, ke kterému z pojmenovaných oddílů patří hodnoty uvedené jako argumenty. Symboly (| a |) se označují jako *banánové klipy* a funkce vytvořená tímto typem vazby let se nazývá *aktivní nástroj pro rozpoznávání*.

Jako příklad zvažte následující aktivní vzorek s argumentem.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

Aktivní vzorek můžete použít ve výrazu odpovídajícího vzorku, jako v následujícím příkladu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

Výstup tohoto programu je následující:

```console
7 is odd
11 is odd
32 is even
```

Dalším použitím aktivních vzorů je rozkládat datové typy několika způsoby, například když mají stejná podkladová data různé možné reprezentace. `Color` Objekt může být například rozložen do reprezentace RGB nebo reprezentace HSB.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

Výstup výše uvedeného programu je následující:

```console
Red
 Red: 255 Green: 0 Blue: 0
 Hue: 360.000000 Saturation: 1.000000 Brightness: 0.500000
Black
 Red: 0 Green: 0 Blue: 0
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.000000
White
 Red: 255 Green: 255 Blue: 255
 Hue: 0.000000 Saturation: 0.000000 Brightness: 1.000000
Gray
 Red: 128 Green: 128 Blue: 128
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.501961
BlanchedAlmond
 Red: 255 Green: 235 Blue: 205
 Hue: 36.000000 Saturation: 1.000000 Brightness: 0.901961
```

V kombinaci tyto dva způsoby použití aktivní vzorky umožňují rozdělit a rozložit data do pouze příslušné formě a provést příslušné výpočty na příslušná data ve formuláři nejvhodnější pro výpočtu.

Výsledné výrazy porovnávání vzorů umožňují zapisovat data pohodlným způsobem, který je velmi čitelný, což značně zjednodušuje potenciálně složitý kód větvení a analýzy dat.

## <a name="partial-active-patterns"></a>Částečné aktivní vzorky

Někdy je třeba rozdělit pouze část vstupního prostoru. V takovém případě napíšete sadu částečných vzorů, z nichž každý odpovídá některé vstupy, ale nepodaří odpovídat jiné vstupy. Aktivní vzorky, které ne vždy vytvářejí hodnotu, se nazývají *částečné aktivní vzorky*; mají vrácenou hodnotu, která je typ možnosti. Chcete-li definovat částečný aktivní vzorek, použijte\_zástupný znak ( ) na konci seznamu vzorků uvnitř banánových klipů. Následující kód ilustruje použití částečné aktivní vzor.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

Výstup z předchozího příkladu je následující:

```console
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

Při použití částečné aktivní vzory, někdy jednotlivé volby mohou být nesouvislé nebo vzájemně se vylučující, ale nemusí být. V následujícím příkladu nejsou čtvercové a datová krychle vzorku nesouvislé, protože některá čísla jsou čtverce i krychle, například 64. Následující program používá a vzor kombinovat čtvercové a datové krychle vzorky. Vytiskne všechna celá čísla až do 1000, které jsou jak čtverce, tak kostky, stejně jako ty, které jsou pouze kostky.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

Výstup je následující:

```console
1 is a cube and a square
8 is a cube
27 is a cube
64 is a cube and a square
125 is a cube
216 is a cube
343 is a cube
512 is a cube
729 is a cube and a square
1000 is a cube
```

## <a name="parameterized-active-patterns"></a>Parametrizované aktivní vzorky

Aktivní vzorky vždy trvat alespoň jeden argument pro položku, která odpovídá, ale mohou mít další argumenty také, v takovém případě název *parametrizovaný aktivní vzor* platí. Další argumenty umožňují obecný vzor, který má být specializovaný. Například aktivní vzorky, které používají regulární výrazy k analýzě řetězců, často zahrnují regulární výraz jako `Integer` další parametr, jako v následujícím kódu, který také používá částečný aktivní vzor definovaný v předchozím příkladu kódu. V tomto příkladu jsou k přizpůsobení obecného aktivního vzoru ParseRegex uvedeny řetězce, které používají regulární výrazy pro různé formáty kalendářních dat. Aktivní vzorek Integer se používá k převodu odpovídajícířetězce na celá čísla, které mohou být předány DateTime konstruktoru.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

Výstup předchozího kódu je následující:

```console
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

Aktivní vzorky nejsou omezeny pouze na výrazy odpovídající vzorek, můžete je také použít na let-vazby.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

Výstup předchozího kódu je následující:

```console
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a>Viz také

- [Referenční příručka jazyka F#](index.md)
- [Výrazy shody](match-expressions.md)
