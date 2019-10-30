---
title: Zahození – C# Průvodce
description: Popisuje C#podporu pro zahození, které jsou nepřiřazené, hodíelné proměnné a způsoby, jak je možné je použít.
author: rpetrusha
ms.technology: csharp-fundamentals
ms.date: 07/21/2017
ms.openlocfilehash: 783266b6893a597d790af82db50b4f52a00ad0bf
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037349"
---
# <a name="discards---c-guide"></a>Zahození – C# Průvodce

Počínaje C# 7,0 C# podporuje zahození, což jsou dočasné a fiktivní proměnné, které jsou záměrně nepoužívané v kódu aplikace. Zahození jsou ekvivalentní nepřiřazeným proměnným; nemají hodnotu. Vzhledem k tomu, že existuje pouze jedna proměnná zahození a tato proměnná nesmí být přidělena jako úložiště, zrušení zahození může snížit přidělení paměti. Vzhledem k tomu, že záměr vašeho kódu je jasný, zvyšují jeho čitelnost a udržovatelnost.

Označíte, že proměnná je zahozena přiřazením podtržítka (`_`) jako názvu. Například následující volání metody vrací 3-Tuple, ve kterém jsou první a druhé hodnoty zahozeny a *oblast* je dřív deklarovaná proměnná, která má být nastavena na odpovídající třetí komponentu vrácenou *GetCityInformation*:

```csharp
(_, _, area) = city.GetCityInformation(cityName);
```

V C# rámci přiřazení v následujících kontextech jsou zahozena 7,0:

- Řazená kolekce členů a [dekonstrukce](deconstruct.md)objektu.
- Porovnávání vzorů s [je](language-reference/keywords/is.md) a [Switch](language-reference/keywords/switch.md).
- Volá metody s parametry `out`.
- Samostatný `_`, pokud není v oboru žádné `_`.

Pokud je `_` platným zahozením, pokus o načtení jeho hodnoty nebo jeho použití v operaci přiřazení generuje chybu kompilátoru CS0301, název\_v aktuálním kontextu neexistuje. Důvodem je to, že `_` nemá přiřazenou hodnotu a nemusí být ani přiřazeno umístění úložiště. Pokud se jednalo o skutečnou proměnnou, nemůžete zahodit více než jednu hodnotu, protože předchozí příklad proběhl.

## <a name="tuple-and-object-deconstruction"></a>Tuple a dekonstrukce objektu

Zahození jsou zvláště užitečné při práci s řazenými kolekcemi členů, když kód aplikace používá některé prvky řazené kolekce členů, ale ignoruje jiné. Například následující metoda `QueryCityDataForYears` vrátí 6-řazené kolekce členů s názvem města, jeho oblastí, rokem, populacem města pro daný rok, druhým rokem a plněním města pro daný druhý rok. V tomto příkladu se zobrazuje změna populace mezi těmito dvěma roky. Z dat, která jsou k dispozici v rámci řazené kolekce členů, jsme nevěděli s oblastí město a znali jsme název města a dvě datum v době návrhu. V důsledku toho se zajímá jenom o dvě hodnoty populace uložené v řazené kolekci členů a můžou své zbývající hodnoty zpracovat jako zahozené.  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Další informace o dekonstrukci řazených kolekcí členů pomocí výmětů naleznete v tématu [dekonstrukce řazených kolekcí členů a dalších typů](deconstruct.md#deconstructing-tuple-elements-with-discards).

Metoda `Deconstruct` třídy, struktury nebo rozhraní také umožňuje načíst a dekonstruovat konkrétní sadu dat z objektu. Pokud vás zajímá, že pracujete jenom s podmnožinou dekonstruovaných hodnot, můžete zahození použít. Následující příklad dekonstruuje objekt `Person` do čtyř řetězců (křestní jméno a příjmení, město a stav), ale zahodí příjmení a stav.

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs)]

Další informace o dekonstrukci uživatelsky definovaných typů pomocí zahození naleznete v tématu [dekonstrukce řazených kolekcí členů a dalších typů](deconstruct.md#deconstructing-a-user-defined-type-with-discards).

## <a name="pattern-matching-with-switch-and-is"></a>Porovnávání vzorů s `switch` a `is`

*Vzor zahození* lze použít při porovnávání vzorů s klíčovým slovem [is](language-reference/keywords/is.md) a [Switch](language-reference/keywords/switch.md) . Každý výraz vždy odpovídá vzoru zahození.

Následující příklad definuje metodu `ProvidesFormatInfo`, [která používá příkazy, k určení](language-reference/keywords/is.md) , zda objekt poskytuje <xref:System.IFormatProvider> implementaci a testuje, zda je objekt `null`. Používá také vzor zahození pro zpracování objektů jiného typu, které nejsou null.

[!code-csharp[discard-pattern](../../samples/snippets/csharp/programming-guide/discards/discard-pattern2.cs)]

## <a name="calls-to-methods-with-out-parameters"></a>Volání metod s výstupními parametry

Při volání metody `Deconstruct` pro dekonstrukci uživatelsky definovaného typu (instance třídy, struktury nebo rozhraní) můžete zahodit hodnoty jednotlivých argumentů `out`. Ale při volání libovolné metody s parametrem out můžete také zahodit hodnotu `out` argumenty.

Následující příklad volá metodu [DateTime. TryParse (String, out DateTime)](<xref:System.DateTime.TryParse(System.String,System.DateTime@)>) k určení, zda řetězcové vyjádření data je platné v aktuální jazykové verzi. Vzhledem k tomu, že se jedná o příklad pouze při ověřování řetězce data a nikoli při jeho analýze pro extrakci data, argument `out` metody je zahození.

[!code-csharp[discard-with-out](../../samples/snippets/csharp/programming-guide/discards/discard-out1.cs)]

## <a name="a-standalone-discard"></a>Samostatné zahození

Samostatné zahození můžete použít k označení všech proměnných, které se rozhodnete ignorovat. Následující příklad používá samostatné zahození pro ignorování objektu <xref:System.Threading.Tasks.Task> vráceného asynchronní operací. To má dopad na potlačení výjimky, kterou operace vyvolá, protože se chystá její dokončení.

[!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard1.cs)]

Všimněte si, že `_` je také platný identifikátor. Pokud se používá mimo podporovaný kontext, `_` se považuje za zahození, ale jako platnou proměnnou. Pokud je v oboru již identifikátor s názvem `_`, použití `_` jako samostatné zahození může mít za následek:

- Náhodné úpravy hodnoty proměnné `_` v oboru přiřazením hodnoty zamýšleného zahození. Příklad:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#1)]

- Chyba kompilátoru pro porušení bezpečnosti typů. Příklad:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#2)]

- Chyba kompilátoru CS0136, v tomto oboru nelze deklarovat místní nebo parametr s názvem\_, protože tento název se používá v nadřazeném místním oboru pro definování místní proměnné nebo parametru. Příklad:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#3)]

## <a name="see-also"></a>Viz také:

- [Dekonstrukce řazených kolekcí členů a dalších typů](deconstruct.md)
- [`is` – klíčové slovo](language-reference/keywords/is.md)
- [`switch` – klíčové slovo](language-reference/keywords/switch.md)
