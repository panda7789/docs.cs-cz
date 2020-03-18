---
title: Zahodit - Průvodce C#
description: Popisuje podporu jazyka C#' pro zahození, které jsou nepřiřazené, zahoditelné proměnné a způsoby, ve kterém lze použít zahození.
ms.technology: csharp-fundamentals
ms.date: 07/21/2017
ms.openlocfilehash: a76e7fc13f92ec0de87153bb35eb3924bb317616
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73100642"
---
# <a name="discards---c-guide"></a>Zahodit - Průvodce C#

Počínaje C# 7.0, C# podporuje zahodí, které jsou dočasné, fiktivní proměnné, které jsou záměrně nepoužívané v kódu aplikace. Zahodity jsou ekvivalentní nepřiřazené proměnné; nemají hodnotu. Vzhledem k tomu, že existuje pouze jedna proměnná prohození a tato proměnná nemusí být ani přidělena úložiště, zahodí může snížit přidělení paměti. Vzhledem k tomu, že záměr vašeho kódu jasné, zvyšují jeho čitelnost a udržovatelnost.

Můžete označit, že proměnná je zahození`_`přiřazením podtržítko ( ) jako jeho název. Například následující volání metody vrátí 3-n-tice, ve kterém první a druhé hodnoty jsou zahodí a *oblast* je dříve deklarované proměnné, které mají být nastaveny na odpovídající třetí součást vrácené *GetCityInformation*:

```csharp
(_, _, area) = city.GetCityInformation(cityName);
```

V c# 7.0 zahození jsou podporovány v přiřazení v následujících kontextech:

- N-tice a [objekt dekonstrukce](deconstruct.md).
- Porovnávání vzorů s [je](language-reference/keywords/is.md) a [přepínač](language-reference/keywords/switch.md).
- Volání metod `out` s parametry.
- Samostatný, `_` pokud `_` ne je v oboru.

Pokud `_` je platný zahození, pokus o načtení jeho hodnoty nebo použít v operaci přiřazení generuje\_chybu kompilátoru CS0301, "Název ' ' neexistuje v aktuálním kontextu". Důvodem `_` je, že není přiřazena hodnota a nemusí být ani přiřazeno umístění úložiště. Pokud se jednalo o skutečnou proměnnou, nelze zahodit více než jednu hodnotu, jako tomu bylo v předchozím příkladu.

## <a name="tuple-and-object-deconstruction"></a>N-tice a dekonstrukce objektů

Zahodí jsou užitečné zejména při práci s řazené kolekce členů, když kód aplikace používá některé prvky řazené kolekce členů, ale ignoruje ostatní. Například následující `QueryCityDataForYears` metoda vrátí 6-n-tice s názvem města, jeho oblast, rok, město populace pro tento rok, druhý rok, a populace města pro tento druhý rok. Příklad ukazuje změnu počtu obyvatel mezi těmito dvěma roky. Z údajů dostupných z řazené kolekce členů se nestaráme o městskou oblast a známe název města a dvě data v době návrhu. V důsledku toho nás zajímají pouze dvě hodnoty základního souboru uložené v řazené kolekce členů a mohou zpracovat jeho zbývající hodnoty jako zahození.  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Další informace o deconstructing řazené kolekce členů s výtažky, naleznete v [tématu Deconstructing řazené kolekce členů a další typy](deconstruct.md#deconstructing-tuple-elements-with-discards).

Metoda `Deconstruct` třídy, struktury nebo rozhraní také umožňuje načíst a dekonstruovat konkrétní sadu dat z objektu. Zahodity můžete použít, pokud máte zájem pracovat pouze s podmnožinou deconstructed hodnot. Následující příklad dekonstruuje `Person` objekt do čtyř řetězců (křestní jméno a příjmení, město a stát), ale zahodí příjmení a stav.

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs)]

Další informace o dekonstrukci uživatelem definované typy s zahození, naleznete v [tématu Deconstructing řazené kolekce členů a další typy](deconstruct.md#deconstructing-a-user-defined-type-with-discards).

## <a name="pattern-matching-with-switch-and-is"></a>Porovnávání `switch` vzorů s a`is`

Vzorek *zahození* lze použít v porovnávání vzorů s klíčovými slovy [is](language-reference/keywords/is.md) a [switch.](language-reference/keywords/switch.md) Každý výraz vždy odpovídá vzoru zahození.

Následující příklad definuje `ProvidesFormatInfo` metodu, která používá [příkazy](language-reference/keywords/is.md) is <xref:System.IFormatProvider> k určení, zda `null`objekt poskytuje implementaci a testuje, zda je objekt . Používá také vzorek zahození ke zpracování objektů jiného typu, které nejsou null.

[!code-csharp[discard-pattern](../../samples/snippets/csharp/programming-guide/discards/discard-pattern2.cs)]

## <a name="calls-to-methods-with-out-parameters"></a>Volání metod s out parametry

Při volání `Deconstruct` metody dekonstruovat uživatelem definovaný typ (instance třídy, struktury nebo rozhraní) `out` můžete zahodit hodnoty jednotlivých argumentů. Ale můžete také zahodit `out` hodnotu argumentů při volání libovolné metody s out parametr.

Následující příklad volá [Metodu DateTime.TryParse(String, out DateTime)](<xref:System.DateTime.TryParse(System.String,System.DateTime@)>) k určení, zda je řetězcová reprezentace data platná v aktuální jazykové verzi. Vzhledem k tomu, že se příklad týká pouze ověřování řetězce data a `out` nikoli jeho analýzy za účelem extrahování data, argument metody je zahození.

[!code-csharp[discard-with-out](../../samples/snippets/csharp/programming-guide/discards/discard-out1.cs)]

## <a name="a-standalone-discard"></a>Samostatný výmět

Samostatné zahození můžete použít k označení libovolné proměnné, kterou se rozhodnete ignorovat. Následující příklad používá samostatné zahození <xref:System.Threading.Tasks.Task> ignorovat objekt vrácený asynchronní operace. To má za následek potlačení výjimky, která operace vyvolá, jak se chystá dokončit.

[!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard1.cs)]

Všimněte `_` si, že je také platný identifikátor. Při použití mimo podporovaný `_` kontext, je považován za zahození, ale jako platná proměnná. Pokud je `_` identifikátor s názvem již `_` v oboru, použití jako samostatné zahození může mít za následek:

- Náhodná změna hodnoty proměnné in-scope `_` přiřazením hodnoty zamýšleného zahození. Například:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#1)]

- Chyba kompilátoru pro porušení bezpečnosti typů. Například:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#2)]

- Chyba kompilátoru CS0136, "Místní\_nebo parametr s názvem ' ' nelze deklarovat v tomto oboru, protože tento název se používá v ohraničujícím místním oboru k definování místního nebo parametru." Například:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#3)]

## <a name="see-also"></a>Viz také

- [Dekonstrukce řazených kolekcí členů a dalších typů](deconstruct.md)
- [`is`Klíčové slovo](language-reference/keywords/is.md)
- [`switch`Klíčové slovo](language-reference/keywords/switch.md)
