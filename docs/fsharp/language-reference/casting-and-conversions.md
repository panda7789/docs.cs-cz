---
title: Přetypování a převody (F#)
description: 'Zjistěte, jak programovací jazyk F # poskytuje operátory převodu pro aritmetické převody mezi různými primitivní typy.'
ms.date: 05/16/2016
ms.openlocfilehash: aca1a2523130ee485a7e7c9a6a45a410904cb246
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/16/2018
ms.locfileid: "45677926"
---
# <a name="casting-and-conversions-f"></a>Přetypování a převody (F#)

Toto téma popisuje podporu pro převody typů v jazyce F #.

## <a name="arithmetic-types"></a>Aritmetické typy

Jazyk F # poskytuje operátory převodu pro aritmetické převody mezi různými primitivní typy, jako například mezi celými čísly a typy plovoucího bodu. Operátory převodu celé číslo a char kontrole a zaškrtnuté políčko formuláře; operátory s plovoucí desetinnou čárkou a `enum` operátor převodu tomu tak není. Unchecked formuláře jsou definovány v `Microsoft.FSharp.Core.Operators` a kontrolovaný formuláře jsou definovány v `Microsoft.FSharp.Core.Operators.Checked`. Checked formuláře kontrola přetečení a generovat výjimku při běhu, pokud výsledná hodnota překračuje omezení cílového typu.

Každý z těchto operátorů má stejný název jako název cílového typu. Například v následujícím kódu, ve kterém jsou typy explicitně označena, `byte` zobrazí se dvě různé významy. První výskyt je pro typ a druhý je operátor převodu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

V následující tabulce jsou uvedeny operátory převodu, které jsou definovány v jazyce F #.

|Operátor|Popis|
|--------|-----------|
|`byte`|Převeďte na byte, typ bez znaménka 8 bitů.|
|`sbyte`|Převod na bajty se znaménkem.|
|`int16`|Převeďte na celé číslo se znaménkem 16 bitů.|
|`uint16`|Převeďte na celé číslo bez znaménka 16 bitů.|
|`int32, int`|Převeďte na 32bitové celé číslo se znaménkem.|
|`uint32`|Převeďte na 32-bit znaménka.|
|`int64`|Převeďte na 64bitové celé číslo se znaménkem.|
|`uint64`|Převeďte na 64-bit znaménka.|
|`nativeint`|Převeďte na nativní celé číslo.|
|`unativeint`|Převeďte na celé číslo bez znaménka nativní.|
|`float, double`|Převeďte na IEEE dvojité přesnosti 64bitovým kompilátorem plovoucí desetinné číslo s desetinnou čárkou.|
|`float32, single`|Převeďte IEEE jednoduchou přesností 32-bit plovoucí desetinné číslo s desetinnou čárkou.|
|`decimal`|Převést na `System.Decimal`.|
|`char`|Převést na `System.Char`, znaku Unicode.|
|`enum`|Převeďte na typ výčtu.|
Kromě předdefinované primitivní typy, můžete použít tyto operátory s typy, které implementují `op_Explicit` nebo `op_Implicit` metody s odpovídajícími podpisy. Například `int` operátor převodu funguje s jakýmkoli typem, který poskytuje statické metody `op_Explicit` , která přebírá typ jako parametr a vrací `int`. Jako speciální výjimky k obecným pravidlem, že metody nemohou být přetíženy návratovým typem, můžete udělat `op_Explicit` a `op_Implicit`.

## <a name="enumerated-types"></a>Výčtové typy

`enum` Operátor je obecný operátor, který přijímá jeden parametr typu, který představuje typ `enum` k převodu. Když ji převede na Výčtový typ, typ odvození se pokusí určit typ `enum` , který chcete převést. V následujícím příkladu je proměnná `col1` není explicitně označena, ale jeho typ je odvozen z novější test rovnosti. Kompilátor může odvodit proto, že převádíte na `Color` výčtu. Alternativně můžete zadat poznámku typu, stejně jako u `col2` v následujícím příkladu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]

Cílový typ výčtu můžete také explicitně zadat jako parametr typu, stejně jako v následujícím kódu:

```fsharp
let col3 = enum<Color> 3
```

Všimněte si, že výčet přetypování pracovní pouze v případě, že základní typ výčtu je kompatibilní s typem převodu. V následujícím kódu, že je převod neúspěšný kompilace z důvodu neshody mezi `int32` a `uint32`.

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

Další informace najdete v tématu [výčty](enumerations.md).

## <a name="casting-object-types"></a>Přetypování typy objektů

Převod mezi typy v hierarchii objektů je zásadní pro objektově orientované programování. Existují dva základní typy převodů: přetypování nahoru (upcasting) a přetypování dolů (přetypování na nižší). Přetypování hierarchii znamená, že přetypování z odvozeného objektu odkaz na odkaz na základní objekt. Takový výraz přetypování zaručeně funguje jako základní třída je v hierarchii dědičnosti odvozené třídy. Přetypování dolů hierarchii z základní objekt odkazu na odkaz na objekt odvozené, bude úspěšné pouze v případě, že objekt je ve skutečnosti instance správné cíl (Odvozený) typ nebo typ odvozený z cílového typu.

Jazyk F # poskytuje operátory pro tyto typy převodů. `:>` Operátor přetypování nahoru hierarchii a `:?>` operátor přetypování dolů v hierarchii.

### <a name="upcasting"></a>Upcasting

V řadě jazyků orientovaných upcasting je implicitní; v jazyce F # pravidla se mírně liší. Upcasting se automaticky použije při předání argumentů metody na typu objektu. Však pro funkce vazbou let v modulu upcasting není automaticky, pokud typ parametru není deklarována jako typ flexibilní. Další informace najdete v tématu [flexibilní typy](flexible-Types.md).

`:>` Operátor provádí statickou přetypování, což znamená, že úspěch přetypování je určen v době kompilace. Pokud přetypování, která používá `:>` se zkompiluje úspěšně, je platný přetypování a nemá žádné riziko selhání za běhu.

Můžete také použít `upcast` operátor k provádění těchto převodů. Následující výraz určuje převod hierarchie:

```fsharp
upcast expression
```

Pokud použijete operátor přetypování nahoru, kompilátor se pokusí odvodit typ, který převádíte z kontextu. Pokud kompilátor nemůže určit cílový typ, kompilátor nahlásí chybu.

### <a name="downcasting"></a>Přetypování na nižší

`:?>` Operátor provádí dynamické přetypování, což znamená, že úspěch přetypování je stanovena v době běhu. Přetypování, která používá `:?>` operátor není zaregistrované v době kompilace, ale za běhu, je proveden pokus o přetypování na zadaný typ. Pokud je objekt kompatibilní s cílovým typem, proběhne úspěšně přetypování. Pokud objekt není kompatibilní s cílovým typem, modul runtime vyvolává `InvalidCastException`.

Můžete také použít `downcast` operátor pro převod dynamického typu. Následující výraz určuje převod hierarchií směrem dolů na typ, který je odvozen z kontextu programu:

```fsharp
downcast expression
```

Jako u `upcast` operátora, pokud kompilátor nemůže odvodit typ konkrétní cíl z kontextu, oznámí chybu.

Následující kód ukazuje použití `:>` a `:?>` operátory. Kód ukazuje, že `:?>` operátor je nejlepší použít při vědět, že převod bude úspěšné, protože ji vyvolá `InvalidCastException` Pokud převod selže. Pokud si nejste jisti, že se převod úspěšný, typ testu, který používá `match` výrazu je lepší, protože se eliminuje režijní náklady na generování výjimku.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

Protože obecný operátory `downcast` a `upcast` využívají odvození typu k určení typu argument a vrácená ve výše uvedeném kódu, můžete nahradit

```fsharp
let base1 = d1 :> Base1
```

with

```fsharp
let base1 = upcast d1
```

V předchozím kódu, typ argumentu a návratové typy jsou `Derived1` a `Base1`v uvedeném pořadí.

Další informace o typu testů, naleznete v tématu [odpovídající výrazy](match-Expressions.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
