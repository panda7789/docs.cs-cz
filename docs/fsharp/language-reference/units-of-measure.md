---
title: Měrné jednotky
description: 'Přečtěte si, jak plovoucí desetinná čárka a čísla se znaménkem v F # můžou mít přidružené měrné jednotky, které se obvykle používají k označení délky, objemu a hmotnosti.'
ms.date: 08/15/2020
ms.openlocfilehash: 0262f89e80697dd86161c93fe37381122972b56f
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811571"
---
# <a name="units-of-measure"></a>Měrné jednotky

Plovoucí desetinná čárka a čísla se znaménkem v F # můžou mít přidružené měrné jednotky, které se obvykle používají k označení délky, objemu, hmotnosti a tak dále. Pomocí množství s jednotkami povolíte kompilátoru, aby ověřil, že aritmetické relace mají správné jednotky, což pomáhá předejít chybám při programování.

## <a name="syntax"></a>Syntax

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a>Poznámky

Předchozí syntaxe definuje *jednotkový název* jako měrnou jednotku. Volitelná část se používá k definování nové míry z podmínek dříve definovaných jednotek. Například následující řádek definuje míru `cm` (centimetr).

```fsharp
[<Measure>] type cm
```

Následující řádek definuje míru `ml` (milliliter) jako krychlové centimetr ( `cm^3` ).

```fsharp
[<Measure>] type ml = cm^3
```

V předchozí syntaxi je *míra* vzorec, který zahrnuje jednotky. Ve vzorcích, které zahrnují jednotky, jsou podporovány integrální pravomoci (kladné a záporné), mezery mezi jednotkami znamenají součin dvou jednotek, `*` také označuje součin jednotek a `/` označuje podíl jednotek. U reciproční jednotky můžete buď použít záporné celočíselné napájení, nebo `/` , které označuje oddělení a jmenovatel vzorec jednotky. Více jednotek ve jmenovateli musí být uzavřeny v závorkách. Jednotky oddělené mezerami po `/` interpretaci jsou interpretovány jako součást jmenovatele, ale jakékoli jednotky následující za `*` jsou interpretovány jako součást čitatele.

Můžete použít 1 ve výrazech jednotek, buď samostatně k označení množství bez dimenze, nebo spolu s jinými jednotkami, jako je například v čitateli. Například jednotky pro sazbu by byly zapsány jako `1/s` , kde `s` označuje sekundy. Ve vzorcích jednotek se nepoužívají kulaté závorky. Ve vzorcích jednotek neurčíte číselné konstanty převodu. Můžete však definovat konstanty převodu s jednotkami samostatně a použít je v výpočtech kontrolovaných jednotkou.

Vzorce jednotek, které znamenají stejnou věc, mohou být napsány různými podobnými způsoby. Kompilátor proto převede vzorce jednotek do konzistentního formátu, který převede záporné pravomoci na reciprocals, seskupí jednotky do jednoho čitatele a jmenovatele a alphabetizes jednotky v čitateli a jmenovateli.

Například vzorce jednotek `kg m s^-2` a `m /s s * kg` jsou převedeny na `kg m/s^2` .

Měrné jednotky se používají ve výrazech s plovoucí desetinnou čárkou. Použití čísel s plovoucí desetinnou čárkou spolu s přidruženými jednotkami míry přidává další úroveň zabezpečení typu a pomáhá vyhnout se chybám neshody jednotek, ke kterým může dojít ve vzorcích při použití slabého typu čísla s plovoucí desetinnou čárkou. Pokud napíšete výraz s plovoucí desetinnou čárkou, který používá jednotky, jednotky ve výrazu se musí shodovat.

Literály můžete opatřit poznámkami pomocí vzorce jednotky v lomených závorkách, jak je znázorněno v následujících příkladech.

```fsharp
1.0<cm>
55.0<miles/hour>
```

Mezi číslem a lomenou závorkou nelze vložit mezeru. Můžete však zahrnout příponu literálu `f` , například, jako v následujícím příkladu.

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

Tato poznámka mění typ literálu z jeho primitivního typu (například `float` ) na typ dimenze, například `float<cm>` nebo, v tomto případě `float<miles/hour>` . Jednotka anotace `<1>` indikuje množství bez dimenzí a její typ je ekvivalentní primitivnímu typu bez parametr jednotky.

Typ měrné jednotky je plovoucí desetinná čárka nebo podepsaný integrální typ společně s poznámkou jednotky navíc, která je uvedena v závorkách. Proto při psaní typu převodu z `g` (gramů) na `kg` (kilogramy), popíšete typy následujícím způsobem.

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

Měrné jednotky se používají pro kontrolu jednotky při kompilaci, ale v běhovém prostředí nejsou trvalé. Proto nemají vliv na výkon.

Měrné jednotky lze použít na jakýkoli typ, nikoli pouze na typy s plovoucí desetinnou čárkou. pouze typy s plovoucí desetinnou čárkou, podepsané celočíselné typy a typy Decimal podporují dimenze množství. Proto má smysl použít měrné jednotky u primitivních typů a agregací, které obsahují tyto primitivní typy.

Následující příklad znázorňuje použití měrných jednotek.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]

Následující příklad kódu ukazuje, jak převést hodnoty s plovoucí desetinnou čárkou na dimenze s hodnotou s plovoucí desetinnou čárkou. Jenom vynásobte 1,0, aplikujete rozměry na 1,0. Tuto možnost můžete zaabstraktit do funkce jako `degreesFahrenheit` .

Také při předání hodnot dimenzí funkcím, které očekávají bez dimenzí čísla s plovoucí desetinnou čárkou, je nutné zrušit jednotky nebo přetypovat na `float` pomocí `float` operátoru. V tomto příkladu je rozdělen `1.0<degC>` argument pro argumenty, které mají za následek, že `printf` `printf` neočekáváte množství bez dimenzí.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

Následující příklad relace zobrazuje výstupy a vstupy tohoto kódu.

```console
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a>Použití obecných jednotek

Můžete napsat obecné funkce, které pracují s daty, která mají přidruženou jednotku měření. To provedete tak, že zadáte typ společně s obecnou jednotkou jako parametr typu, jak je znázorněno v následujícím příkladu kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]

## <a name="creating-aggregate-types-with-generic-units"></a>Vytváření agregovaných typů s obecnými jednotkami

Následující kód ukazuje, jak vytvořit agregovaný typ, který se skládá z jednotlivých hodnot s plovoucí desetinnou čárkou, které mají Obecné jednotky. To umožňuje vytvořit jeden typ, který pracuje s nejrůznějšími jednotkami. Obecné jednotky zachovávají bezpečnost typů také tím, že zajistí, že obecný typ, který má jednu sadu jednotek, je jiný typ než stejný obecný typ s jinou sadou jednotek. Základem této techniky je, že `Measure` atribut lze použít na parametr typu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]

## <a name="units-at-runtime"></a>Jednotky za běhu

Měrné jednotky se používají pro kontrolu statického typu. Pokud jsou kompilovány hodnoty s plovoucí desetinnou čárkou, jsou jednotky míry eliminovány, takže jednotky budou za běhu ztraceny. Proto není možné provádět jakékoli pokus o implementaci funkcí, které závisí na kontrole jednotek za běhu. Například implementace `ToString` funkce pro tisk jednotek není možná.

## <a name="conversions"></a>Převody

Chcete-li převést typ, který obsahuje jednotky (například `float<'u>` ) na typ, který nemá jednotky, můžete použít funkci standardního převodu. Například můžete použít `float` k převodu na `float` hodnotu, která nemá jednotky, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

Chcete-li převést jednotkovou hodnotu na hodnotu, která má jednotky, můžete vynásobit hodnotu 1 nebo 1,0, která je opatřena příslušnými jednotkami. Pro psaní vrstev interoperability ale existují i některé explicitní funkce, které můžete použít k převodu hodnot bez jednotek na hodnoty s jednotkami. Ty jsou v modulu [FSharp. Core. LanguagePrimitives](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-languageprimitives.html) . Například pro převod z jednotky `float` bez jednotek na `float<cm>` , použijte [floatwithmeasure –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-languageprimitives.html#FloatWithMeasure), jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]

## <a name="units-of-measure-in-the-f-core-library"></a>Měrné jednotky v základní knihovně jazyka F #

V oboru názvů je k dispozici knihovna jednotek `FSharp.Data.UnitSystems.SI` . Obsahuje jednotky v obou svých symbolových formách (jako `m` měřič) v `UnitSymbols` suboboru názvů a jejich úplný název (jako `meter` měřič) v `UnitNames` oboru názvů sub.

## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka F #](index.md)
