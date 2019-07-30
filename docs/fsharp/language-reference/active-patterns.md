---
title: Aktivní vzorky
description: Naučte se používat aktivní vzory k definování pojmenovaných oddílů, které rozdělují vstupní F# data v programovacím jazyce.
ms.date: 05/16/2016
ms.openlocfilehash: 12f423abe05e649e0b527ed04124b991feb5d592
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629949"
---
# <a name="active-patterns"></a>Aktivní vzorky

*Aktivní vzory* umožňují definovat pojmenované oddíly, které rozdělují vstupní data, abyste je mohli použít ve výrazu porovnávání vzorů stejně jako u rozlišeného sjednocení. Můžete použít aktivní vzory a rozložit data vlastním způsobem pro každý oddíl.

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

V předchozí syntaxi jsou identifikátory názvy pro oddíly vstupních dat, která jsou reprezentována *argumenty*, nebo jinými slovy názvy pro podmnožiny sady všech hodnot argumentů. V aktivní definici vzoru může být až sedm oddílů. *Výraz* popisuje formulář, do kterého se mají data rozložit. Pomocí aktivní definice vzoru můžete definovat pravidla pro určení, které z uvedených oddílů mají hodnoty zadané jako argumenty patřit do. Symboly (| a |) jsou označovány jako *klipy banánů* a funkce vytvořená tímto typem dovolit, aby vazba byla volána jako *aktivní nástroj pro rozpoznávání*.

Jako příklad zvažte následující aktivní vzor s argumentem.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

Můžete použít aktivní vzor ve výrazu pro porovnávání vzorů, jak je uvedeno v následujícím příkladu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

Výstup tohoto programu je následující:

```
7 is odd
11 is odd
32 is even
```

Další možností použití aktivních vzorů je rozložit datové typy různými způsoby, například když mají stejná základní data různé možné reprezentace. Například `Color` objekt může být rozložen do reprezentace v modelu RGB nebo v rámci zobrazení HSB.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

Výstup výše uvedeného programu je následující:

```
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

V kombinaci těchto dvou způsobů použití aktivních vzorů můžete rozdělit data do oddílů a rozložit je pouze do příslušné formy a provádět odpovídající výpočty pro příslušná data ve formuláři nejužitečnější pro výpočet.

Výsledné výrazy pro porovnávání vzorů umožňují psát data pohodlným způsobem, který je velmi čitelný a významně zjednodušuje potenciálně složitý kód pro větvení a analýzu dat.

## <a name="partial-active-patterns"></a>Částečné aktivní vzory

V některých případech je potřeba rozdělit jenom část vstupního prostoru. V takovém případě napíšete sadu částečných vzorů, které odpovídají určitým vstupům, ale neodpovídají jiným vstupům. Aktivní vzory, které nevytváří vždy hodnotu, se nazývají *částečné aktivní vzory*; mají návratovou hodnotu, která je typu možnosti. Chcete-li definovat částečný aktivní vzor, použijte zástupný znak (\_) na konci seznamu vzorů uvnitř klipů banánů. Následující kód ilustruje použití částečného aktivního vzoru.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

Výstup předchozího příkladu je následující:

```
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

Při použití částečných aktivních vzorů mohou být jednotlivé volby odděleny nebo vzájemně exkluzivní, ale nemusí být. V následujícím příkladu nejsou odděleny vzorce čtverce a vzorová krychle, protože některá čísla jsou čtverce i datové krychle, například 64. Následující program používá vzor a ke kombinování čtverců a vzorů krychle. Vytiskněte všechna celá čísla až 1000, která jsou čtverce i datové krychle, i ty, které jsou jenom datové krychle. 

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

Výstup je následující:

```
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

## <a name="parameterized-active-patterns"></a>Parametrizované aktivní vzory

Aktivní vzory vždycky přebírají aspoň jeden argument pro odpovídající položku, ale můžou také použít další argumenty. v takovém případě se použije název parametrizovaný *aktivní vzor* . Další argumenty umožňují specializované obecné vzory. Například aktivní vzory, které používají regulární výrazy k analýze řetězců často obsahují regulární výraz jako další parametr, jak je uvedeno v následujícím kódu, který používá také částečný aktivní vzor `Integer` definovaný v předchozím příkladu kódu. V tomto příkladu jsou přidány řetězce, které používají regulární výrazy pro různé formáty data pro přizpůsobení obecného ParseRegex aktivního vzoru. Celočíselný aktivní vzor slouží k převodu odpovídajících řetězců na celá čísla, která lze předat konstruktoru DateTime.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

Výstup předchozího kódu je následující:

```
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

Aktivní vzory nejsou omezené jenom na výrazy porovnávání vzorů, můžete je také použít na vazby let.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

Výstup předchozího kódu je následující:

```
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Výrazy shody](match-expressions.md)
