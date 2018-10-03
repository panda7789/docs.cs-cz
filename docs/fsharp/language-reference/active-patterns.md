---
title: Aktivní vzorky (F#)
description: 'Další informace o použití aktivní vzory definovat pojmenované oddíly, které rozdělit vstupní data v programovacím jazyce F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 4fb7d3e2b9c7e6f1c1ed9d64a47728c7f40017c8
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48030639"
---
# <a name="active-patterns"></a>Aktivní vzorky

*Aktivní vzory* vám umožňují definovat pojmenované oddíly, které rozdělit vstupní data tak, aby tyto názvy můžete používat ve vzorku s odpovídajícím výrazem, stejně jako byste to udělali pro diskriminované sjednocení. Aktivní vzory můžete použít k rozložení dat v podobě přizpůsobené pro každý oddíl.

## <a name="syntax"></a>Syntaxe

```fsharp
// Complete active pattern definition.
let (|identifer1|identifier2|...|) [ arguments ] = expression
// Partial active pattern definition.
let (|identifier|_|) [ arguments ] = expression
```

## <a name="remarks"></a>Poznámky

V předchozí syntaxi identifikátory jsou názvy pro oddíly vstupních dat, která je reprezentována *argumenty*, nebo jinými slovy, názvy pro dílčí sadu všechny hodnoty argumentů. V definici – aktivní vzor může být až sedm oddíly. *Výraz* popisuje formulář, do kterého chcete rozložit data. Můžete definovat pravidla pro zjišťování, který pojmenovaných oddílů hodnot uvedených jako argumenty patří do definici – aktivní vzor. (| A |) symboly jsou označovány jako *banánů klipy* a je volána funkce vytvořené pomocí tohoto typu umožňují vazby *aktivní rozlišovač*.

Jako příklad zvažte následující active vzor s argumentem.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

Aktivní vzor můžete použít ve vzoru porovnávání výrazů jako v následujícím příkladu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

Výstup tohoto programu je následující:

```
7 is odd
11 is odd
32 is even
```

Jiné aktivní vzory používá k rozložení datových typů v několika způsoby, například pokud má stejná podkladová data různé možné reprezentace. Například `Color` objekt může lze rozložit na reprezentaci RGB nebo reprezentaci HSB.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

Výstup programu výše je následujícím způsobem:

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

V kombinaci tyto dva způsoby použití aktivní vzorky umožňují oddílu a jak rozložit data na příslušný formulář a provádí výpočty odpovídající příslušná data ve formuláři pro výpočet nejvíce usnadnil.

Výsledné výrazy odpovídající vzor povolit data mají být zapsána do pohodlný způsob, který je velmi čitelný, jehož cílem je výrazně zjednodušit potenciálně velmi složitý větvení a datové analýzy kódu.

## <a name="partial-active-patterns"></a>Částečné aktivní vzory

V některých případech je potřeba rozdělit pouze část prostoru vstupní. V takovém případě můžete zapsat sadu částečné vzorů z nich odpovídá některými vstupy ale selhání tak, aby odpovídaly ostatní vstupy. Aktivní vzory, které nevytváří vždy hodnotu, se nazývají *částečné aktivní vzory*; má návratovou hodnotu, je typ možnosti. K definování částečné active vzor, můžete použít zástupný znak (\_) na konci seznamu vzorků uvnitř banánů klipy. Následující kód ukazuje použití částečné aktivní vzor.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

Výstup z předchozího příkladu vypadá takto:

```
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

Při použití částečné aktivní vzory, někdy jednotlivé volby lze nesouvislé, nebo vylučují, ale nemusí být. V následujícím příkladu model datové krychle a druhou mocninu vzoru nejsou nesouvislý, protože některá čísla jsou pole a datové krychle, jako je například 64. Následující program vytiskne všechny celých čísel až 1000000, které jsou pole a datové krychle.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

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

## <a name="parameterized-active-patterns"></a>Parametrizované aktivní vzory

Aktivní vzory vždy provést aspoň jeden argument pro položku je nalezena shoda, může ale trvat další argumenty, v takovém případě název *parametrizované – aktivní vzor* platí. Další argumenty povolit obecný vzor specificky určené. Například obsahovat aktivní vzory, které často Analýza řetězců pomocí regulárních výrazů regulární výraz jako další parametr, stejně jako v následujícím kódem, který také používá částečné active vzor `Integer` definované v předcházejícím příkladu. V tomto příkladu jsou uvedeny řetězce, které používá regulární výrazy pro různé formáty kalendářního data k přizpůsobení obecné ParseRegex active vzor. Aktivní vzor celé číslo se používá k převod odpovídající řetězců na celá čísla, která může být předán konstruktoru data a času.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

Výstup předchozího kódu vypadá takto:

```
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

Aktivní vzory nejsou omezeny pouze na vzor odpovídající výrazy, můžete také použít na vazby let.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

Výstup předchozího kódu vypadá takto:

```
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Výrazy shody](match-expressions.md)
