---
title: "Aktivní vzorky (F#)"
description: "Další informace o použití aktivní vzorky k definování pojmenované oddíly, které rozdělit vstupní data v programovací jazyk F #."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 11a724ff-f9ff-4056-b5e0-87e9ed986f4a
ms.openlocfilehash: 845184e6150cf0b93393038ca3d39f0e6d898a2e
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="active-patterns"></a>Aktivní vzorky

*Aktivní vzorky* umožňují definovat pojmenované oddíly, které rozdělit vstupních dat, takže můžete použít tyto názvy v vzor odpovídající výrazu stejným způsobem jako pro rozlišovaná sjednocení. Aktivní vzorky můžete rozložit data způsobem přizpůsobené pro každý oddíl.


## <a name="syntax"></a>Syntaxe

```fsharp
// Complete active pattern definition.
let (|identifer1|identifier2|...|) [ arguments ] = expression
// Partial active pattern definition.
let (|identifier|_|) [ arguments ] = expression
```

## <a name="remarks"></a>Poznámky
V předchozích syntaxi identifikátory jsou názvy pro oddíly vstupních dat, která je reprezentována *argumenty*, nebo jinými slovy, názvy pro podmnožiny sadu všechny hodnoty argumentů. V definici – aktivní vzor může být až sedm oddíly. *Výraz* popisuje, do kterého chcete rozložit data formuláře. Definici – aktivní vzor můžete definovat pravidla pro zjišťování, který pojmenovaný oddíl hodnoty zadané jako argumenty patří. (| A |) symboly jsou označovány jako *banánů klipů* a je volána funkce vytvořené tento typ umožňují vazby *active pro rozpoznávání*.

Jako příklad zvažte následující aktivní vzor s parametrem.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

Aktivní vzor můžete použít ve tvaru odpovídající výrazu, jako v následujícím příkladu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

Výstup tohoto programu je následující:

```
7 is odd
11 is odd
32 is even
```

Jiný aktivní vzorky slouží k rozložit datových typů v několika způsoby, například když stejné základní data mají různé možné reprezentace. Například `Color` objekt může rozložit na reprezentaci RGB nebo reprezentaci HSB.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

Výstup programu výše je následující:

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

V kombinaci tyto dva způsoby použití aktivní vzorky umožňují oddílu a rozložit data na příslušný formulář a proveďte příslušné výpočtů na příslušná data ve formuláři nejvhodnější pro výpočet.

Výsledné výrazy odpovídající vzor povolit zápis v pohodlný způsob, který je velmi čitelný, výrazně zjednodušení potenciálně složité větvení a kód analýzy dat dat.


## <a name="partial-active-patterns"></a>Částečné aktivní vzorky
V některých případech budete muset oddílu jenom část vstupní místa. V takovém případě napíšete sady částečné vzorů, které odpovídat některých vstupních hodnot, ale nezdaří tak, aby odpovídaly ostatní vstupy. Aktivní vzorky, které vždy nevytváří hodnotu, se nazývají *částečné aktivní vzorky*; mají návratovou hodnotu, která je typu možnost. K definování částečné – aktivní vzor, se na konci seznam vzorů uvnitř klipů banánů použít zástupný znak (_). Následující kód ukazuje použití částečné aktivní vzor.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

Výstup v předchozím příkladu vypadá takto:

```
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

Při použití částečné aktivní vzorky, někdy jednotlivé možnosti může být nesouvislé, nebo vzájemně vylučují, ale jejich nemusí být. V následujícím příkladu hranaté vzor a vzor datové krychle nejsou nesouvislý, protože jsou některé čísla čtverce a datové krychle, jako je například 64. Následující program vytiskne všechny celá čísla až 1000000, které jsou čtverce a datové krychle.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

Výstup vypadá takto:

```
1
64
729
4096
15625
46656
117649
262144
531441
1000000
```

## <a name="parameterized-active-patterns"></a>Parametrizované aktivní vzorky
Aktivní vzorky vždy provést alespoň jeden argument pro položku se shodoval, ale v takovém případě název se může trvat i, další argumenty *parametrizované – aktivní vzor* platí. Další argumenty povolit obecné vzor nutné zadat. Aktivní vzorky, které často Analýza řetězců pomocí regulárních výrazů příklady regulární výraz jako další parametr jako v následujícím kódu, který také používá částečné aktivní vzor `Integer` definované v předchozím příkladu kódu. V tomto příkladu jsou uvedeny přizpůsobení obecné ParseRegex aktivní vzor řetězce, které použití regulárních výrazů pro různých formátů data. Aktivní vzor celé číslo se používá k převod odpovídající řetězců na celá čísla, které lze předat do konstruktoru data a času.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

Výstup předchozí kód je následující:

```
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

Aktivní vzorky nejsou omezeny pouze na vzor odpovídající výrazy, můžete také použít na umožňují vazby.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

Výstup předchozí kód je následující:

```
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F #](index.md)

[Výrazy shody](match-expressions.md)

