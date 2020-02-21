---
title: Přetypování a převody
description: Přečtěte si F# , jak programovací jazyk poskytuje operátory převodu pro aritmetické převody mezi různými primitivními typy.
ms.date: 02/20/2020
ms.openlocfilehash: 5f9727d14a7ae070e0f0f71fa0a0abe04f662071
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543583"
---
# <a name="casting-and-conversions-f"></a>Přetypování a převody (F#)

Toto téma popisuje podporu pro převody typu v F#nástroji.

## <a name="arithmetic-types"></a>Aritmetické typy

F#poskytuje operátory převodu pro aritmetické převody mezi různými primitivními typy, jako je například typ Integer a plovoucí desetinná čárka. Operátory převodu integrálu a znaků mají kontrolované a nezaškrtnuté formuláře. operátory s plovoucí desetinnou čárkou a operátor převodu `enum`. Nezaškrtnuté formuláře jsou definovány v `Microsoft.FSharp.Core.Operators` a zaškrtnuté formuláře jsou definovány v `Microsoft.FSharp.Core.Operators.Checked`. Kontroluje kontrolované formuláře pro přetečení a generuje výjimku za běhu, pokud výsledná hodnota překračuje limity cílového typu.

Každý z těchto operátorů má stejný název jako název cílového typu. Například v následujícím kódu, ve kterém jsou typy explicitně opatřeny poznámkami, `byte` se zobrazí se dvěma různými významy. První výskyt je typ a druhý je operátor převodu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

V následující tabulce jsou uvedeny operátory převodu definované F#v.

|Operátor|Popis|
|--------|-----------|
|`byte`|Převod na bajt, 8bitový typ bez znaménka.|
|`sbyte`|Převod na bajt se znaménkem.|
|`int16`|Převede na 16bitové celé číslo se znaménkem.|
|`uint16`|Převod na 16 bitů unsigned integer.|
|`int32, int`|Převede na celé číslo se znaménkem 32.|
|`uint32`|Převod na 32-bitovou unsigned integer.|
|`int64`|Převede na celé číslo se znaménkem 64.|
|`uint64`|Převod na 64-bitovou unsigned integer.|
|`nativeint`|Převést na nativní celé číslo.|
|`unativeint`|Převod na nativní celé číslo bez znaménka.|
|`float, double`|Převeďte na 64 čísla s plovoucí desetinnou čárkou s dvojitou přesností IEEE.|
|`float32, single`|Převod na 32 číslo s plovoucí desetinnou čárkou s jednoduchou přesností.|
|`decimal`|Převést na `System.Decimal`.|
|`char`|Převést na `System.Char`, znak Unicode.|
|`enum`|Převod na Výčtový typ.|

Kromě integrovaných primitivních typů můžete použít tyto operátory s typy, které implementují `op_Explicit` nebo `op_Implicit` metody s příslušnými signaturami. Například operátor převodu `int` pracuje s jakýmkoli typem, který poskytuje statickou metodu `op_Explicit`, která přebírá typ jako parametr a vrací `int`. Jako speciální výjimka pro obecné pravidlo, že metody nemohou být přetíženy návratovým typem, můžete to provést pro `op_Explicit` a `op_Implicit`.

## <a name="enumerated-types"></a>Výčtové typy

Operátor `enum` je obecný operátor, který přijímá jeden parametr typu, který představuje typ `enum` pro převod na. Když se převede na Výčtový typ, pokusy o odvození typu určují typ `enum`, na který chcete převést. V následujícím příkladu není proměnná `col1` explicitně Poznáma, ale její typ je odvozen z pozdějšího testu rovnosti. Proto může kompilátor odvodit, že převedete na výčet `Color`. Alternativně můžete zadat anotaci typu, jak je uvedeno v následujícím příkladu `col2`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]

Cílový typ výčtu můžete zadat také explicitně jako parametr typu, jak je uvedeno v následujícím kódu:

```fsharp
let col3 = enum<Color> 3
```

Všimněte si, že přetypování výčtu funguje pouze v případě, že podkladový typ výčtu je kompatibilní s převáděným typem. V následujícím kódu se převod nezdařil, protože se neshoduje mezi `int32` a `uint32`.

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

Další informace naleznete v tématu [výčty](enumerations.md).

## <a name="casting-object-types"></a>Přetypování typů objektů

Převod mezi typy v hierarchii objektů je zásadní pro objektově orientované programování. Existují dva základní typy převodů: přetypování (přetypování) a přetypování (potřeby). Při přetypování hierarchie znamená přetypování z odvozeného objektu na odkaz na základní objekt. Takovému přetypování je zaručeno, že bude fungovat, pokud je základní třída v hierarchii dědičnosti odvozené třídy. Přetypování dolů v hierarchii ze základního objektu na odkaz na odvozený objekt je úspěšný pouze v případě, že objekt je ve skutečnosti instancí správného cílového (odvozeného) typu nebo typu odvozeného z cílového typu.

F#poskytuje operátory pro tyto typy převodů. Operátor `:>` přetypování hierarchii a operátor `:?>` přetypování dolů na hierarchii.

### <a name="upcasting"></a>Přetypování

V mnoha objektově orientovaných jazycích je přetypování implicitní. v F#nástroji se pravidla mírně liší. Při předávání argumentů metodám typu objektu je přetypování použito automaticky. Pro funkce vázané na let v modulu však není automatické přetypování automatické, pokud typ parametru není deklarován jako flexibilní typ. Další informace naleznete v tématu [flexibilní typy](flexible-Types.md).

Operátor `:>` provádí statické přetypování, což znamená, že úspěch přetypování je určen v době kompilace. Pokud přetypování, které používá `:>`, je úspěšně zkompilováno, jedná se o platné přetypování a v době běhu není pravděpodobné selhání.

K provedení takového převodu můžete použít také operátor `upcast`. Následující výraz určuje převod hierarchie:

```fsharp
upcast expression
```

Při použití operátoru přetypování se kompilátor pokusí odvodit typ, na který převádíte z kontextu. Pokud kompilátor nemůže určit cílový typ, kompilátor ohlásí chybu. Může být vyžadována anotace typu.

### <a name="downcasting"></a>Potřeby

Operátor `:?>` provádí dynamické přetypování, což znamená, že úspěch přetypování je určen v době běhu. Přetypování, které používá operátor `:?>`, není kontrolováno v době kompilace; v době spuštění se ale za běhu provede pokus o přetypování na zadaný typ. Pokud je objekt kompatibilní s cílovým typem, přetypování je úspěšné. Pokud objekt není kompatibilní s cílovým typem, modul runtime vyvolá `InvalidCastException`.

Pomocí operátoru `downcast` lze také provést převod dynamického typu. Následující výraz určuje převod mimo hierarchii na typ, který je odvozen z kontextu programu:

```fsharp
downcast expression
```

Jako operátor `upcast`, pokud kompilátor nemůže odvodit konkrétní cílový typ z kontextu, ohlásí chybu. Může být vyžadována anotace typu.

Následující kód ilustruje použití operátorů `:>` a `:?>`. Kód ilustruje, že operátor `:?>` je nejlépe použit, pokud víte, že převod proběhne úspěšně, protože vyvolá `InvalidCastException`, pokud převod selže. Pokud si nejste jisti, že převod proběhne úspěšně, test typu, který používá výraz `match` je lepší, protože se vyhne režii vygenerování výjimky.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

Vzhledem k tomu, že obecné operátory `downcast` a `upcast` spoléhají na odvození typu k určení argumentu a návratového typu ve výše uvedeném kódu, můžete nahradit

```fsharp
let base1 = d1 :> Base1
```

with

```fsharp
let base1: Base1 = upcast d1
```

Všimněte si, že je požadována anotace typu, protože `upcast` sama o sobě nemohla určit základní třídu.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
