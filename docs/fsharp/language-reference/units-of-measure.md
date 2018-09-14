---
title: Měrné jednotky (F#)
description: 'Zjistěte, jak plovoucí desetinnou čárkou a celé číslo se znaménkem hodnoty v jazyce F # můžete mít přidružené jednotky měření, které se obvykle používají k označení délku, svazek a velkokapacitních.'
ms.date: 05/16/2016
ms.openlocfilehash: ad2193e25f3c0cee6e73cd529ab43d1e4b6b549b
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45616150"
---
# <a name="units-of-measure"></a>Měrné jednotky

Plovoucí desetinná čárka a číslo se znaménkem hodnoty v jazyce F # můžete mít přidružené jednotky měření, které se obvykle používají k označení délku, svazek, hmotnost, a tak dále. Pomocí množství s jednotkami povolíte kompilátor ověřte, že aritmetické vztahy mají správnou jednotek, která pomáhá zabránit programovací chyby.

## <a name="syntax"></a>Syntaxe

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a>Poznámky

Předchozí syntaxe definuje *název jednotky* jako měrné jednotky. Volitelná součást se používá k definování novou míru dříve definované jednotkách. Například následující řádek určuje míru `cm` (centimetr).

```fsharp
[<Measure>] type cm
```

Následující řádek určuje míru `ml` (milliliter) jako kubické centimetru (`cm^3`).

```fsharp
[<Measure>] type ml = cm^3
```

V předchozí syntaxi *míru* je vzorec, který zahrnuje jednotky. Ve vzorcích, které se týkají jednotky, integrální mocniny podporují (kladné a záporné) mezery mezi jednotkami určete, součin dvou jednotky `*` také určuje produkt jednotek a `/` označuje podíl jednotky. Pro vzájemné jednotek, můžete použít buď power záporné celé číslo nebo `/` určující oddělení mezi čitatelem a jmenovatelem částí vzorce. Několik jednotek v jmenovatel by měl být uzavřen v závorkách. Jednotky oddělené mezerami po `/` jsou interpretovány jako součást jmenovatel, ale všechny jednotky po `*` jsou interpretovány jako součást čítač.

1 můžete použít ve výrazech jednotek, buď samostatně k označení bezrozměrná množství nebo společně s další jednotky, jako je například čítač. Například jednotky pro mírou by byla zapsána jako `1/s`, kde `s` označuje sekund. Ve vzorcích jednotek nejsou použity závorky. Ve vzorcích jednotek; není zadán číselný převod konstanty ale můžete definovat převod konstanty s jednotkami samostatně a jejich použití v částí kontroluje výpočty.

Jednotka vzorce, které mají stejný význam je možné psát v různých ekvivalentní způsoby. Proto kompilátor převede částí vzorce konzistentní formulář, který převede negativní mocniny recipročních, skupiny jednotky do jednoho čitatelem a jmenovatelem a seřadí podle abecedy jednotek v čitatelem a jmenovatelem.

Například jednotky vzorce `kg m s^-2` a `m /s s * kg` jsou převedeny na `kg m/s^2`.

Ve výrazech s plovoucí desetinnou čárkou bod použijete měrné jednotky. Pomocí čísel s plovoucí desetinnou spolu s přidružené jednotky měření přidává další úroveň bezpečnost typů a pomáhá zabránit jednotky chybám, které se mohou vyskytnout ve vzorcích, když použijete slabě typované čísel s plovoucí desetinnou. Pokud píšete plovoucí bodu výraz, který používá jednotky, musí odpovídat jednotky ve výrazu.

Literály s částí vzorce v lomených závorkách, může opatřit poznámkami, jak je znázorněno v následujícím příkladu.

```fsharp
1.0<cm>
55.0<miles/hour>
```

Není vložíme mezeru mezi číslo a ostré závorky; však může zahrnovat přípona literálu jako `f`, jako v následujícím příkladu.

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

Taková anotace změní typ literálu z jeho primitivního typu (například `float`) rozměrový typ jako `float<cm>` nebo v tomto případě `float<miles/hour>`. Jednotka anotace `<1>` označuje bezrozměrná množství a její typ je ekvivalentní primitivní typ bez parametru jednotky.

Typ měrné jednotky se plovoucí desetinnou čárkou nebo společně s další jednotky anotaci, uvedené v závorkách celočíselný typ se znaménkem. Proto při psaní typ převodu z `g` (g) k `kg` (kg), které popisují typy následujícím způsobem.

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

Měrné jednotky se používají pro jednotku kompilace kontrolu, ale nejsou zachované v prostředí za běhu. Proto neovlivňují výkon.

Měrné jednotky lze použít u libovolného typu, ne jenom plovoucí typy bodů; pouze typy plovoucího bodu, ale podepsané celočíselných typů a desítkové typy podporu dimenzovanými počty. Proto pouze má smysl použít měrné jednotky na primitivní typy a agregátů, které obsahují tyto primitivní typy.

Následující příklad ukazuje použití měrné jednotky.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]

Následující příklad kódu ukazuje, jak převést bezrozměrná číslo s plovoucí desetinnou čárkou na dimenzované hodnotu s plovoucí desetinnou čárkou. Můžete pouze vynásobit 1.0, použití dimenze pro rozhraní příkazového řádku 1.0. Můžete to abstraktní do funkce, jako je `degreesFahrenheit`.

Navíc při předání dimenzované hodnoty do funkce, které očekávají. bezrozměrná čísel s plovoucí desetinnou musíte zrušit jednotky nebo přetypován na `float` pomocí `float` operátor. V tomto příkladu budete dělit `1.0<degC>` pro argumenty, které mají `printf` protože `printf` očekává, že. bezrozměrná množství.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

Následující příklad relace ukazuje vytvořené jako výstupy z a vstupy pro tento kód.

```
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a>Použití obecného jednotek

Můžete napsat obecné funkce, které pracují s daty, která má související jednotka měření. To provedete tak, že zadáte typ spolu s Obecné jednotky jako parametr typu, jak je znázorněno v následujícím příkladu kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]

## <a name="creating-aggregate-types-with-generic-units"></a>Vytvoření agregované typy pomocí obecného jednotky

Následující kód ukazuje, jak vytvořit agregační typ, který se skládá z jednotlivých hodnot s plovoucí desetinnou, které mají jednotek, které jsou obecné. To umožňuje jeden typ má být vytvořen, který spolupracuje s řadou jednotky. Obecné jednotky také zachovat bezpečnost typů tím, že zajišťuje, že je obecný typ, který má jednu sadu jednotky jiného typu než stejný obecný typ s jinou sadu jednotky. Základ této techniky je, že `Measure` atribut lze použít pro parametr typu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]

## <a name="units-at-runtime"></a>Jednotky za běhu

Měrné jednotky se používají pro kontrolu statického typu. Po zkompilování hodnoty s plovoucí desetinnou měrné jednotky jsou odstraněny, tak, aby v době běhu byly ztraceny jednotky. Jakékoli pokusy o implementaci funkcí, které závisí na kontrolu za běhu jednotky proto není možné. Příklad implementace `ToString` funkce, který vytiskne jednotky není možné.

## <a name="conversions"></a>Převody

Převést typ, který má jednotky (například `float<'u>`) na typ, který nemá jednotek, můžete použít funkci standardní převod. Například můžete použít `float` pro převod na `float` hodnotu, která nemá žádné jednotky, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

Pro převedení unitless hodnoty na hodnotu, která má jednotky, můžete hodnotu 1 nebo 1.0, která je označena vynásobit se vhodné jednotky. Pro psaní vrstvy vzájemná funkční spolupráce, existují však také některé explicitní funkce, které můžete použít k převodu unitless hodnot na hodnoty s jednotkami. Toto jsou v [Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) modulu. Například chcete převést unitless `float` k `float<cm>`, použijte [floatwithmeasure –](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9), jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]

## <a name="units-of-measure-in-the-f-core-library"></a>Měrné jednotky v knihovně F # Core

Je k dispozici v knihovně jednotky `FSharp.Data.UnitSystems.SI` oboru názvů. V obou jejich symbol formulář obsahuje jednotek SI (podobně jako `m` pro měření) v `UnitSymbols` podřízeném oboru názvů a jejich úplný název (jako `meter` pro měření) v `UnitNames` podřízeném oboru názvů.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
