---
title: "Přetypování a převody (F#)"
description: "Zjistěte, jak programovací jazyk F # poskytuje operátory převodu pro aritmetické převody mezi různými primitivní typy."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: db30db67-da21-4206-bf0c-9211bd3cb22f
ms.openlocfilehash: f17d3919c59c5881213d28a59cea7ae184493949
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="casting-and-conversions-f"></a>Přetypování a převody (F#)

Toto téma popisuje podporu pro převody typů v jazyce F #.

## <a name="arithmetic-types"></a>Aritmetické typy
F # poskytuje operátory převodu pro aritmetické převody mezi různými primitivní typy, jako třeba mezi celé číslo a plovoucí typy bodů. Operátory převodu integrální a char mají zaškrtnuto a nezaškrtnuto forms; procedura bodu operátory a `enum` operátor převodu nepodporují. Nezaškrtnuté formuláře jsou definovány v `Microsoft.FSharp.Core.Operators` a zaškrtnuté formuláře jsou definovány v `Microsoft.FSharp.Core.Operators.Checked`. Checked formuláře zkontrolujte přetečení a generovat výjimku modulu runtime, pokud výsledná hodnota překročí omezení na typ cíle.

Každý z těchto operátorů má stejný název jako název cílového typu. Například v následujícím kódu, ve kterém jsou typy explicitně poznámky, `byte` se zobrazí se dva různé významy. První výskyt je typ a druhý je operátor převodu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

V následující tabulce jsou definované v F # operátory převodu.

|Operátor|Popis|
|--------|-----------|
|`byte`|Převeďte na bajtů, 8bitové typu bez znaménka.|
|`sbyte`|Převeďte na podepsané bajtů.|
|`int16`|Převeďte na 16bitové celé číslo se znaménkem.|
|`uint16`|Převeďte na celé číslo bez znaménka 16 bitů.|
|`int32, int`|Převeďte na 32bitové celé číslo se znaménkem.|
|`uint32`|Převeďte na celé číslo bez znaménka 32-bit.|
|`int64`|Převeďte na 64bitové celé číslo se znaménkem.|
|`uint64`|Převeďte na celé číslo bez znaménka 64-bit.|
|`nativeint`|Převeďte na nativní celé číslo.|
|`unativeint`|Převeďte na celé číslo bez znaménka nativní.|
|`float, double`|Převeďte 64-bit Dvojitá přesnost IEEE bodu číslo s plovoucí čárkou.|
|`float32, single`|Převeďte 32-bit jednoduchou přesností IEEE bodu číslo s plovoucí čárkou.|
|`decimal`|Převést na `System.Decimal`.|
|`char`|Převést na `System.Char`, znak Unicode.|
|`enum`|Převeďte na výčtového typu.|
Kromě předdefinovaných primitivní typy, můžete použít tyto operátory s typy, které implementují `op_Explicit` nebo `op_Implicit` metody s odpovídajícími podpisy. Například `int` operátor převodu pracuje s žádný typ, který poskytuje statickou metodu `op_Explicit` který přebere typ jako parametr a vrátí `int`. Speciální výjimkou obecně platí, že metody nemohou být přetíženy o návratový typ, můžete k tomu `op_Explicit` a `op_Implicit`.

## <a name="enumerated-types"></a>Výčtové typy
`enum` Operátor je obecný operátor, který přijímá jeden parametr typu, který představuje typ `enum` převést. Když se převede na Výčtový typ, zadejte odvození pokusí zjistit typ `enum` , kterou chcete převést. V následujícím příkladu, proměnná `col1` není explicitně označena, ale jeho typ je odvozen z novější test rovnosti. Proto můžete kompilátor odvodit převádíte na `Color` výčtu. Alternativně můžete poskytnout anotaci typu stejně jako u `col2` v následujícím příkladu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]
    
Můžete také určit typ výčtu cíl explicitně jako parametr typu, jako v následujícím kódu:

```fsharp
let col3 = enum<Color> 3
```

Všimněte si, že výčtu vrhá pracovní pouze v případě, že je kompatibilní s typem převáděné s podkladovým typem výčtu. V následujícím kódu, převod se nepovede zkompilovat z důvodu neshody mezi `int32` a `uint32`.

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

Další informace najdete v tématu [výčty](enumerations.md).

## <a name="casting-object-types"></a>Přetypování typy objektů
Převod mezi typy v hierarchii objektu je nezbytné, aby objektově orientované programování. Existují dva základní typy převody: přetypování nahoru (přetypování nahoru) a přetypování dolů (přetypování dolů). Přetypování nahoru hierarchie znamená přetypování z odvozené objekt odkazů na základní objekt odkaz. Takové přetypování záruku, že fungovat, dokud základní třída je v hierarchii dědičnosti odvozené třídy. Přetypování dolů hierarchii, postupně od základní objekt odkaz na objekt odvozené odkaz, bude úspěšné pouze v případě, že objekt je ve skutečnosti instance typu správnou cílovou (Odvozený) nebo typu odvozeného od cílového typu.

F # poskytuje operátory pro tyto typy převody. `:>` Operátor vrhá nahoru v hierarchii a `:?>` operátor vrhá hierarchií směrem dolů.

### <a name="upcasting"></a>Přetypování nahoru
V mnoha jazycích objektově orientované je implicitní; přetypování nahoru v F # pravidla se mírně liší. Předání argumentů metody na typ objektu, který je automaticky použito přetypování nahoru. Ale pro umožňují vazby funkce v modulu, přetypování nahoru není automatické, pokud typ parametru je deklarován jako typ flexibilní. Další informace najdete v tématu [flexibilní typy](flexible-Types.md).

`:>` Operátor provádí statického přetypování, což znamená, že v době kompilace je určen úspěch přetypování. Pokud přetypování, který používá `:>` zkompiluje úspěšně, je platný přetypování a nemá žádné riziko selhání za běhu.

Můžete také `upcast` operátor proveďte takový převod. Následující výraz určuje převod nahoru v hierarchii:

```fsharp
upcast expression
```

Pokud použijete operátor přetypování nahoru, pokusí se kompilátor odvození typu, který převádíte na z kontextu. Pokud kompilátor se nepodařilo určit typ cíle, kompilátor ohlásí chybu.

### <a name="downcasting"></a>Přetypování dolů
`:?>` Operátor provádí dynamický přetypování, což znamená, že v době běhu je určen úspěch přetypování. Přetypování, který používá `:?>` operátor kontrolována v době kompilace; ale v době běhu je proveden pokus o převést na zadaný typ. Pokud je objekt kompatibilní s typem cíl, bude úspěšná přetypování. Pokud objekt není kompatibilní s typem cíl, modul runtime vyvolává `InvalidCastException`.

Můžete také `downcast` operátor provést převod dynamického typu. Následující výraz určuje převod hierarchií směrem dolů na typ, který je odvozeno z kontextu program:

```fsharp
downcast expression
```

Jako u `upcast` operátor, pokud kompilátor nelze odvodit typ specifické cíle z kontextu, ohlásí chybu.

Následující kód ukazuje použití `:>` a `:?>` operátory. Kód ukazuje, že `:?>` operátor je nejvhodnější při vědět, převod bude úspěšné, protože je vyvolává `InvalidCastException` Pokud převod selže. Pokud si nejste jisti, že bude převodu z úspěšné, typ testu, který používá `match` výrazu je lepší, protože při ní nedochází režii generování výjimku.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

Protože obecné operátory `downcast` a `upcast` spoléhají na odvození typu určit typ argumentu a vraťte se ve výše uvedeném kódu, můžete nahradit

```fsharp
let base1 = d1 :> Base1
```

with

```fsharp
base1 = upcast d1
```

V předchozí kód typ argumentu a návratové typy jsou `Derived1` a `Base1`, v uvedeném pořadí.

Další informace o testech typu najdete v tématu [výrazy shody](match-Expressions.md).

## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F #](index.md)
