---
title: "Měrné jednotky (F#)"
description: "Zjistěte, jak plovoucí desetinná čárka a číslo se znaménkem hodnoty v jazyce F # mohou být přidruženy jednotky míry, které jsou obvykle používány k označení Délka svazku a velkokapacitních."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: cb2eb658-df6c-422e-afad-97422609c773
ms.openlocfilehash: 2d0683e864c5684a78c02e177c296d3067295723
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="units-of-measure"></a>Měrné jednotky

Plovoucí desetinná čárka a číslo se znaménkem hodnoty v jazyce F # může mít přidružené jednotky míry, které jsou obvykle používány k označení délku svazku, hromadně, a tak dále. Pomocí počty jednotek, povolíte kompilátor ověřit, že aritmetické vztahy mají správnou jednotky, která pomáhá zabránit programování chyby.


## <a name="syntax"></a>Syntaxe

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a>Poznámky
Definuje předchozí syntaxe *název jednotky* jako jednotku míry. Volitelná součást se používá k definování novou míru z hlediska dříve definovaném jednotky. Například následující řádek definuje míry `cm` (centimetr).

```fsharp
[<Measure>] type cm
```

Následující řádek definuje míry `ml` (milliliter) jako krychlový centimetru (`cm^3`).

```fsharp
[<Measure>] type ml = cm^3
```

V předchozích syntaxi *měr* je vzorec, který zahrnuje jednotky. Ve vzorcích, které zahrnují jednotky, integrální zajišťuje jsou podporovány (kladné a záporné), mezery mezi jednotky znamenat součin dvou jednotky `*` také určuje produktem jednotky, a `/` označuje podíl jednotky. Pro vzájemné jednotku, můžete použít buď power záporné celé číslo nebo `/` určující oddělení mezi čítači a jmenovatel vzorec jednotky. Několik jednotek v jmenovatel by měl být uzavřeny v závorkách. Jednotky oddělené mezerami po `/` se interpretují jako součást jmenovatel, ale žádné jednotky následující `*` se interpretují jako součást čítači.

1 můžete použít ve výrazech jednotek, buď udávajících bezrozměrný množství, samostatně nebo společně s další jednotky, například v čítači. Například jednotky pro na míru by byla zapsána jako `1/s`, kde `s` určuje v sekundách. V jednotce vzorce nejsou použity závorky. Nezadáte číselný převod konstanty ve vzorcích jednotky; Můžete však definovat převod konstanty u jednotek samostatně a použít na jednotku zaškrtnutí výpočty.

Jednotka vzorce, které mají stejný význam může být napsán v různých způsobů ekvivalentní. Proto kompilátor převede jednotky vzorce konzistentní formulář, který převede záporné zajišťuje recipročních, jednotky skupiny na jednom čítači a jmenovatel a seřadí podle abecedy jednotky v čítači a jmenovatel.

Například jednotky vzorce `kg m s^-2` a `m /s s * kg` se převedou na `kg m/s^2`.

Ve výrazech plovoucí bod použijete měrné jednotky. Pomocí čísla s plovoucí desetinnou společně s přidružené jednotky míry zvyšuje úroveň zabezpečení typů a pomáhá zabránit chybách neshoda jednotky, ke kterým může dojít ve vzorcích, když používáte slabě typovaná čísla s plovoucí desetinnou. Pokud píšete plovoucí bodu výraz, který používá jednotky, musí odpovídat jednotky ve výrazu.

Literály se vzorcem jednotky v lomených závorkách může opatřit poznámkami, jak je znázorněno v následujících příkladech.

```fsharp
1.0<cm>
55.0<miles/hour>
```

Nevkládejte mezeru mezi číslo a lomená závorka; však může zahrnovat příponou literálu, jako `f`, jako v následujícím příkladu.

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

Tyto poznámky změní typ literálové z jeho primitivní typ (například `float`) typu rozměry, jako `float<cm>` nebo v tomto případě `float<miles/hour>`. Jednotka anotaci objektu `<1>` označuje bezrozměrný množství a její typ je ekvivalentní primitivní typ bez parametru jednotky.

Typ měrné jednotky plovoucí desetinné čárky nebo podepsané integrální typ společně s poznámky další jednotky, uvedeným v závorkách. Proto při psaní typ převodu z `g` (gram) k `kg` (kg), které popisují typy následujícím způsobem.

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

Měrné jednotky se používají pro jednotku kompilace kontrola ale nejsou trvalé v běhové prostředí. Proto že nemají vliv výkon.

Měrné jednotky lze použít k libovolnému typu, nikoli pouze plovoucí typy bodů; však pouze plovoucí typy bodů podepsané integrální typy a počty podporu dimenzovány decimal typy. Proto pouze má smysl používat jednotky, na primitivní typy a agregace, které obsahují tyto primitivní typy.

Následující příklad ukazuje použití měrné jednotky.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]
    
Následující příklad kódu ukazuje, jak převést z bezrozměrný číslo s plovoucí desetinnou čárkou rozměry hodnotu s plovoucí desetinnou čárkou. Jste právě vynásobit 1.0, dimenze použití rozhraní 1.0. Můžete to abstraktní do funkce jako `degreesFahrenheit`.

Navíc pokud předáte rozměry hodnoty na funkce, které očekávají bezrozměrný čísla s plovoucí desetinnou, musíte zrušit jednotky nebo přetypovat na `float` pomocí `float` operátor. V tomto příkladu budete provádět dělení po `1.0<degC>` pro argumenty, které mají `printf` protože `printf` očekává bezrozměrný počty.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

Následující příklad relace se zobrazuje výstup z a vstupy pro tento kód.

```
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a>Pomocí obecné jednotky
Obecné funkce, které provozují může zapisovat na data, která je přidružená Měrná jednotka má. To uděláte tak, že zadáte typu společně s Obecné jednotky jako parametr typu, jak je znázorněno v následujícím příkladu kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]
    
## <a name="creating-aggregate-types-with-generic-units"></a>Vytváření typů agregace s Obecné jednotky
Následující kód ukazuje, jak vytvořit typ agregace, který se skládá z jednotlivých hodnot s plovoucí desetinnou mající jednotkách, které jsou obecné. To umožňuje vytvořit jeden typ, který funguje s různými jednotky. Obecné jednotky navíc zachovávají bezpečnost typů tím zajistí, že obecného typu, který má jednu sadu jednotky je jiného typu než stejné obecného typu pomocí jiné sady jednotky. Základ pro tento postup je, že `Measure` atribut lze použít pro parametr typu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]
    
## <a name="units-at-runtime"></a>Jednotky při běhu
Měrné jednotky se používají pro kontrolu statického typu. Když hodnot s plovoucí desetinnou kompilovány, jednotky, jsou odstraněny, tak s jednotkami jsou ztraceny za běhu. Pokusy o implementovat funkce, které závisí na Kontrola jednotky v době běhu proto není možné. Například implementace `ToString` funkce vytiskněte jednotky není možné.


## <a name="conversions"></a>Převody
Převést typ, který má jednotky (například `float<'u>`) na typ, který nemá jednotky, můžete použít funkci standardní převod. Například můžete použít `float` převést `float` hodnotu, která nemá jednotek, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

Převést hodnotu unitless na hodnotu, která má jednotky, můžete hodnotu 1 nebo 1.0, která je označena vynásobit v odpovídajících jednotkách. Pro psaní interoperabilita vrstev, existují však také některé explicitní funkce, které můžete použít k převodu unitless hodnoty na hodnoty s jednotky. Toto jsou v [Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) modulu. Například pro převod unitless `float` k `float<cm>`, použijte [floatwithmeasure –](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9), jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]
    
## <a name="units-of-measure-in-the-f-power-pack"></a>Jednotky, v F # Power Pack
Jednotka knihovny je k dispozici v PowerPack F #. Jednotka knihovny zahrnuje jednotek SI a fyzické konstanty.


## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F #](index.md)
