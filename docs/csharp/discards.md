---
title: Zahození - průvodce v C#
description: Popisuje podporu jazyka C# pro zahození, což nepřiřazené discardable proměnné a způsoby, ve které je možné zahození.
author: rpetrusha
ms.author: ronpet
ms.date: 07/21/2017
ms.openlocfilehash: 761fb69d3bc774975caf63b8aa665f8c19c0430a
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50045649"
---
# <a name="discards---c-guide"></a>Zahození - průvodce v C#

Od verze C# 7.0, C# podporuje zahodí, které jsou dočasné a fiktivní proměnné, které nejsou používány záměrně v kódu aplikace. Zahození jsou ekvivalentní nepřiřazené proměnné; nemají hodnotu. Protože existuje pouze jeden discard proměnné a tuto proměnnou i nelze přidělit úložiště, můžete snížit zahození přidělení paměti. Protože jsou záměr kódu jasný, zvýšit jeho čitelnost a udržovatelnosti.

Určujete, že proměnná je zahození přiřazením podtržítko (`_`) jako jeho název. Například následující volání metody vrací 3 řazené kolekce členů ve kterém jsou hodnoty prvního a druhého zahození a *oblasti* je dřív deklarovanou proměnnou nastavit na odpovídající komponentě třetího vrácený  *GetCityInformation*:

```csharp
(_, _, area) = city.GetCityInformation(cityName);
```

V jazyce C# 7.0 jsou podporovány zahození v přiřazení v následujících kontextů:

- Řazené kolekce členů a objekt [dekonstrukce](deconstruct.md).
- Porovnávání vzorů s [je](language-reference/keywords/is.md) a [přepnout](language-reference/keywords/switch.md).
- Volání metody s `out` parametry.
- Samostatný `_` když ne `_` je v oboru.

Když `_` je platný zahození, pokusu o načtení jeho hodnoty nebo použít operace přiřazení vygeneruje Chyba kompilátoru CS0301, "název"\_' neexistuje v aktuálním kontextu ". Důvodem je, že `_` není přiřazena hodnota a nemusí dají přiřadit dokonce i umístění úložiště. Kdyby skutečná proměnná, nemohl zahodit více než jednu hodnotu, jako předchozí příklad udělal.

## <a name="tuple-and-object-deconstruction"></a>Dekonstrukce řazené kolekce členů a objektu

Zahození jsou obzvláště užitečná při práci s řazenými kolekcemi členů, když kód aplikace používá několik elementů řazené kolekce členů, ale ignoruje ostatní. Například následující `QueryCityDataForYears` metoda vrátí 6-řazené kolekce členů s názvem Město, jeho oblast, rok, název města plnění pro daný rok, druhý rok a název města plnění pro daný druhý rok. Příklad ukazuje změnu počtu obyvatel mezi tyto dva roky. Data k dispozici z řazené kolekce členů, jsme unconcerned k oblasti města a víme název města a dvěma kalendářními daty v době návrhu. V důsledku toho jsme zajímá pouze dvě naplnění hodnoty uložené v řazené kolekci členů a dokáže zpracovat zbývající hodnoty jako zahození.  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Další informace o dekonstrukce řazených kolekcí členů se zahodí, naleznete v tématu [Dekonstrukce řazených kolekcí členů a dalších typů](deconstruct.md#deconstructing-tuple-elements-with-discards).

`Deconstruct` Metoda třídy, struktury nebo rozhraní umožňuje také budete moct načítat a dekonstruovat konkrétní sadu dat z objektu. Pokud vás zajímají práce s pouze podmnožinu dekonstruovanou hodnoty můžete zahození. Následující příklad deconstructs `Person` objektu do čtyř řetězců (jména a příjmení, města a státu), ale zahodí poslední názvu a stavu.

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs)]

Další informace o uživatelem definovaných typů s zahození dekonstrukce, naleznete v tématu [Dekonstrukce řazených kolekcí členů a dalších typů](deconstruct.md#deconstructing-a-user-defined-type-with-discards).

## <a name="pattern-matching-with-switch-and-is"></a>Porovnávání vzorů s `switch` a `is`

*Zahodit vzor* lze použít v porovnávání vzorů s [je](language-reference/keywords/is.md) a [přepnout](language-reference/keywords/switch.md) klíčová slova. Každý výraz vždy shoduje se vzorem zahození.

Následující příklad definuje `ProvidesFormatInfo` metodu, která používá [je](language-reference/keywords/is.md) příkazy k určení, zda objekt poskytuje <xref:System.IFormatProvider> implementaci a testování, zda je objekt `null`. Také používá vzor pro zrušení zpracování objektů jinou hodnotu než null jakéhokoli jiného typu.

[!code-csharp[discard-pattern](../../samples/snippets/csharp/programming-guide/discards/discard-pattern2.cs)]

## <a name="calls-to-methods-with-out-parameters"></a>Volání metody s výstupním parametrům

Při volání `Deconstruct` metoda dekonstruovat uživatelem definovaný typ (instance třídy, struktury nebo rozhraní), můžete zrušit hodnoty jednotlivých `out` argumenty. Ale můžete také zrušit hodnotu `out` argumenty při volání metody jakoukoli metodou s výstupní parametr.

Následující příklad volá [DateTime.TryParse (String, si data a času)](<xref:System.DateTime.TryParse(System.String,System.DateTime@)>) metodou ke zjištění, zda je v aktuální jazykovou verzi platný řetězec představující datum. Protože příklad se týká pouze s ověřuje řetězec data a není ho extrahovat data, analýza `out` argument metody je zahození.

[!code-csharp[discard-with-out](../../samples/snippets/csharp/programming-guide/discards/discard-out1.cs)]

## <a name="a-standalone-discard"></a>Samostatná zrušit

Samostatná zrušit můžete použít k označení jakákoli proměnná, která se můžete rozhodnout ignorovat. Následující příklad používá samostatná zrušit Ignorovat <xref:System.Threading.Tasks.Task> vrácený asynchronní operace. To má za následek výjimku, která vyvolá operaci, jako je dokončení potlačení.

[!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard1.cs)]

Všimněte si, že `_` je také platný identifikátor. Při použití mimo podporované kontext `_` je zpracováván, nikoli jako zahození ale jako platná proměnná. Pokud identifikátor s názvem `_` je již v oboru, použití `_` jako samostatná zrušit může vést k:

- Nechtěné změny hodnoty příslušné `_` proměnné přiřazením hodnoty určené zahození. Příklad:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#1)]

- Chyba kompilátoru za porušení bezpečnosti typů. Příklad:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#2)]

- Chyba kompilátoru CS0136, "místní proměnná nebo parametr s názvem"\_"nelze deklarovat v tomto oboru, protože tento název se používá v uzavírajícím místním oboru pro definování místní proměnné nebo parametru." Příklad:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#3)]

## <a name="see-also"></a>Viz také:

- [Dekonstrukce řazených kolekcí členů a dalších typů](deconstruct.md)
- [`is` Klíčové slovo](language-reference/keywords/is.md)
- [`switch` Klíčové slovo](language-reference/keywords/switch.md)
