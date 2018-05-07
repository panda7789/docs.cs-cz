---
title: Zahození – průvodce v C#
description: Popisuje C# pro podporu zahození, které nepřiřazené, discardable proměnné a způsoby, ve které je možné zahození.
author: rpetrusha
ms.author: ronpet
ms.date: 07/21/2017
ms.openlocfilehash: 9688ea596fa3d534c6c48d5874b04bb257d0dbce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="discards---c-guide"></a>Zahození – průvodce v C#

Od verze 7.0 C#, C# podporuje zahodí, které jsou dočasné, fiktivní proměnné, které jsou záměrně nepoužívané v kódu aplikace. Zahození odpovídají nepřiřazené proměnné; nemají hodnotu. Protože je pouze jeden zahození proměnnou, a tuto proměnnou i nelze přidělit úložiště, můžete snížit zahození přidělení paměti. Protože záměr vymazat kódu, zvýšit jeho přehlednosti a jeho udržovatelnost.

Můžete znamenat, že proměnné zahození přiřazením podtržítko (`_`) jako její název. Například následující volání metody, které vrací 3 řazenou kolekci členů ve kterém jsou hodnoty první a druhý zahození a *oblasti* je dříve deklarované proměnné na hodnotu odpovídající třetí součást vrácený  *GetCityInformation*:

```csharp
(_, _, area) = city.GetCityInformation(cityName);
```

V jazyce C# 7.0 zahození jsou podporovány v přiřazení v kontextech následující:

- Řazené kolekce členů a objekt [deconstruction](deconstruct.md).
- Porovnávání vzorů s [je](language-reference/keywords/is.md) a [přepínač](language-reference/keywords/switch.md).
- Volání metody s `out` parametry.
- Samostatný `_` při ne `_` nachází v oboru.

Když `_` je platný zahození, pokusu o načtení její hodnota nebo použít v operaci přiřazení vygeneruje Chyba kompilátoru CS0301, "název"\_' neexistuje v aktuálním kontextu ". Důvodem je, že `_` není přiřazenou hodnotu a nemusí dají přiřadit dokonce i umístění úložiště. By měla skutečná proměnná, nelze zrušit více než jednu hodnotu, jako předchozí příklad.

## <a name="tuple-and-object-deconstruction"></a>Řazené kolekce členů a objekt deconstruction

Zahození jsou obzvláště užitečná při práci s řazenými kolekcemi členů, pokud kód aplikace používá některé prvky řazené kolekce členů, ale ignoruje ostatní. Například následující `QueryCityDataForYears` metoda vrátí hodnotu 6-řazené kolekce členů s názvem města, jeho oblasti, rok, název města plnění pro tento rok, druhý roku a název města plnění pro tento druhý roku. Příklad ukazuje změnu v plnění mezi tyto dva roky. Data k dispozici z řazenou kolekci členů, jsme unconcerned oblasti města a víme název města a kalendářní data v době návrhu. V důsledku toho jsme se pouze zajímá dvě naplnění hodnotami uloženými v řazené kolekci členů a jeho zbývající hodnoty jako zahození dokáže zpracovat.  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Další informace o deconstructing řazené kolekce členů s zahození najdete v tématu [Deconstructing řazených kolekcí členů a dalších typů](deconstruct.md#deconstructing-tuple-elements-with-discards).

`Deconstruct` Metoda třída, struktura nebo rozhraní také umožňuje načíst a deconstruct konkrétní sadu dat z objektu. Zahození můžete použít, pokud vás zajímá jenom podmnožinu deconstructed hodnoty práce. Následující příklad deconstructs Ihe `Person` objektu do čtyř řetězce (první a poslední názvů, Město a stav), ale zahodí příjmení a stavu.

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs)]

Další informace o deconstructing uživatelem definované typy s zahození najdete v tématu [Deconstructing řazených kolekcí členů a dalších typů](deconstruct.md#deconstructing-a-user-defined-type-with-discards).

## <a name="pattern-matching-with-switch-and-is"></a>Porovnávání vzorů s `switch` a `is`

*Zahodit vzor* mohou být používány s porovnávání vzorů [je](language-reference/keywords/is.md) a [přepínač](language-reference/keywords/switch.md) klíčová slova. Každý výraz vždy zahození shodu.

V následujícím příkladu definuje `ProvidesFormatInfo` metoda, která používá [je](language-reference/keywords/is.md) tvrzení, abyste zjistili, zda objekt poskytuje <xref:System.IFormatProvider> implementace a testy, jestli je objekt `null`. Také využívá vzor zahození k práci s objekty nesmí být nulová žádného jiného typu.

[!code-csharp[discard-pattern](../../samples/snippets/csharp/programming-guide/discards/discard-pattern2.cs)]

## <a name="calls-to-methods-with-out-parameters"></a>Volání metody s výstupní parametry

Při volání metody `Deconstruct` metodu deconstruct uživatelem definovaný typ (instance třídy, struktury nebo rozhraní), můžete zrušit hodnoty individuální `out` argumenty. Ale můžete také zahodit hodnotu `out` argumenty při voláním jakékoli metody se parametr typu out. 

Následující příklad volání [DateTime.TryParse (řetězec, se data a času)](<xref:System.DateTime.TryParse(System.String,System.DateTime@)>) metoda k určení, zda je řetězec představující datum platný v aktuální jazykovou verzi. Protože příklad se týká pouze s ověřování řetězce data a není analýza ho extrahovat data, `out` argumentu metody je zahození.

[!code-csharp[discard-with-out](../../samples/snippets/csharp/programming-guide/discards/discard-out1.cs)]

## <a name="a-standalone-discard"></a>Samostatné zahození

Samostatné zahození slouží k označení jakékoli proměnné, kterou jste se rozhodli ignorovat. Následující příklad používá samostatné zahození Ignorovat <xref:System.Threading.Tasks.Task> objekt vrácený asynchronní operace. To má za následek potlačení výjimku, která vyvolá operaci, protože se jedná o k dokončení.

[!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard1.cs)]

Všimněte si, že `_` je také platný identifikátor. Při použití mimo kontext-podporované `_` považuje, nikoli jako zahození ale jako platná proměnná. Pokud název identifikátor `_` je již v oboru, použití `_` jako samostatná zahození může mít za následek:

- Náhodných změna hodnoty v oborem `_` proměnné přiřazením hodnotu určený zahození. Příklad:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#1)]
 
- Chyba kompilátoru pro narušení zabezpečení typů. Příklad:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#2)]
 
- Chyba kompilátoru CS0136, "místní instalační cestu nebo parametr s názvem '_' nelze deklarovat v tomto rozsahu vzhledem k tomu, že tento název se používá v nadřazených místní rozsah k definování místní instalační cestu nebo parametr." Příklad:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#3)]

## <a name="see-also"></a>Viz také
[Deconstructing řazených kolekcí členů a dalších typů](deconstruct.md)   
[`is` – Klíčové slovo](language-reference/keywords/is.md)   
[`switch` – Klíčové slovo](language-reference/keywords/switch.md)   
