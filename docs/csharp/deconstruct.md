---
title: Dekonstrukce řazených kolekcí členů a dalších typů
description: Naučte se dekonstruovat řazené kolekce členů a další typy.
ms.technology: csharp-fundamentals
ms.date: 07/18/2016
ms.assetid: 0b0c4b0f-4a47-4f66-9b8e-f5c63b195960
ms.openlocfilehash: 23d193faf9702628698fe558f6667aeb130e8916
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73100665"
---
# <a name="deconstructing-tuples-and-other-types"></a>Dekonstrukce řazených kolekcí členů a dalších typů

Řazená kolekce členů poskytuje lehký způsob, jak načíst více hodnot z volání metody. Ale jakmile načtete řazenou kolekce členů, musíte zpracovat její jednotlivé prvky. To na základě element-by-element je těžkopádné, jak ukazuje následující příklad. Metoda `QueryCityData` vrátí 3 řazené kolekce členů a každý z jeho prvků je přiřazen proměnné v samostatné operaci.

[!code-csharp[WithoutDeconstruction](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple1.cs)]

Načítání více hodnot polí a vlastností z objektu může být stejně těžkopádné: je třeba přiřadit hodnotu pole nebo vlastnosti proměnné na základě člena podle člena.

Počínaje C# 7.0, můžete načíst více prvků z řazené kolekce členů nebo načíst více polí, vlastností a vypočítaných hodnot z objektu v jedné operaci *dekonstrukce.* Při dekonstrukci řazené kolekce členů přiřadíte její prvky k jednotlivým proměnným. Když dekonstruujete objekt, přiřadíte vybrané hodnoty jednotlivým proměnným.

## <a name="deconstructing-a-tuple"></a>Dekonstrukce řazené kolekce členů

C# obsahuje integrovanou podporu pro deconstructing řazené kolekce členů, který umožňuje zrušit balíček všech položek v řazené kolekce členů v jedné operaci. Obecná syntaxe pro deconstructing řazené kolekce členů je podobná syntaxi pro definování jedné: uzavřete proměnné, ke kterým má být každý prvek přiřazen v závorcích na levé straně příkazu přiřazení. Například následující příkaz přiřadí prvky 4-n-tice čtyřma samostatným proměnným:

```csharp
var (name, address, city, zip) = contact.GetAddressInfo();
```

Existují tři způsoby, jak dekonstruovat řazenou n-tice:

- Můžete explicitně deklarovat typ každého pole uvnitř závorek. Následující příklad používá tento přístup k deconstruct 3 `QueryCityData` řazené kolekce členů vrácené metodou.

    [!code-csharp[Deconstruction-Explicit](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple2.cs#1)]

- Můžete použít `var` klíčové slovo tak, aby C# odvodí typ každé proměnné. `var` Klíčové slovo umístíte mimo závorky. Následující příklad používá odvození typu při dekonstrukci 3-n-tice vrácené `QueryCityData` metodou.

    [!code-csharp[Deconstruction-Infer](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple3.cs#1)]

    `var` Klíčové slovo můžete také použít jednotlivě s některou nebo všechny deklarace proměnných uvnitř závorek.

    [!code-csharp[Deconstruction-Infer-Some](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple4.cs#1)]

    To je těžkopádné a nedoporučuje se.

- Nakonec můžete deconstruct řazené kolekce členů do proměnné, které již byly deklarovány.

    [!code-csharp[Deconstruction-Declared](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple5.cs#1)]

Všimněte si, že nelze zadat určitý typ mimo závorky i v případě, že každé pole v n-tice má stejný typ. Tím se vygeneruje chyba kompilátoru CS8136, "Dekonstrukce 'var (...)' formulář zakazuje určitý typ pro 'var'.".

Všimněte si, že je také nutné přiřadit každý prvek řazené kolekce členů proměnné. Pokud vyneche všechny prvky, kompilátor generuje chybu CS8132, "Nelze dekonstruovat n-tice 'x' prvky do 'y' proměnné."

Všimněte si, že nelze kombinovat deklarace a přiřazení k existující proměnné na levé straně deconstruction. Kompilátor generuje chybu CS8184, "dekonstrukce nemůže kombinovat deklarace a výrazy na levé straně." pokud členové zahrnují nově deklarované a existující proměnné.

## <a name="deconstructing-tuple-elements-with-discards"></a>Dekonstrukce prvků n-tice s výměty

Často při dekonstrukci řazené kolekce členů, máte zájem o hodnoty pouze některé prvky. Počínaje C# 7.0, můžete využít c#'s podporu pro *zahození*, které jsou pouze pro zápis proměnné, jejichž hodnoty, které jste se rozhodli ignorovat. Zahození je označeno znakem podtržítka ("\_") v přiřazení. Můžete zahodit tolik hodnot, kolik chcete; všechny jsou reprezentovány jediným `_`výmětem.

Následující příklad ilustruje použití řazené kolekce členů s výtažky. Metoda `QueryCityDataForYears` vrátí 6-n-tice s názvem města, jeho oblast, rok, město populace pro tento rok, druhý rok, a město populace pro tento druhý rok. Příklad ukazuje změnu počtu obyvatel mezi těmito dvěma roky. Z údajů dostupných z řazené kolekce členů se nestaráme o městskou oblast a známe název města a dvě data v době návrhu. V důsledku toho nás zajímají pouze dvě hodnoty základního souboru uložené v řazené kolekce členů a mohou zpracovat jeho zbývající hodnoty jako zahození.  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

## <a name="deconstructing-user-defined-types"></a>Dekonstrukce uživatelem definovaných typů

C# nenabízí integrovanou podporu pro deconstructing typy neřazené kolekce členů. Však jako autor třídy, struktury nebo rozhraní, můžete povolit instance typu deconstructed implementací jedné `Deconstruct` nebo více metod. Metoda vrátí void a každá hodnota, která má být deconstructed je [označena out](language-reference/keywords/out-parameter-modifier.md) parametr v podpisu metody. Například následující `Deconstruct` metoda `Person` třídy vrátí první, střední a příjmení:

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#1)]

Potom můžete dekonstruovat `Person` instanci `p` třídy pojmenované s přiřazením takto:

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#2)]

Následující příklad přetíží metodu `Deconstruct` vrátit různé kombinace `Person` vlastností objektu. Individuální přetížení vrátí:

- Křestní jméno a příjmení.
- První, poslední a prostřední jméno.
- Křestní jméno, příjmení, název města a název státu.

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class2.cs)]

Vzhledem k `Deconstruct` tomu, že můžete přetížení metody tak, aby odrážely skupiny `Deconstruct` dat, které jsou běžně extrahovány z objektu, měli byste být opatrní definovat metody s podpisy, které jsou rozlišovací a jednoznačné. Více `Deconstruct` metod, které mají `out` stejný počet parametrů nebo `out` stejný počet a typ parametrů v jiném pořadí může způsobit nejasnosti.

Přetížená `Deconstruct` metoda v následujícím příkladu ilustruje jeden možný zdroj nejasností. První přetížení vrátí křestní jméno, druhé jméno, příjmení `Person` a stáří objektu v tomto pořadí. Druhé přetížení vrátí informace o názvu pouze spolu s roční příjem, ale první, střední a příjmení jsou v jiném pořadí. To usnadňuje zmást pořadí argumentů při dekonstrukci `Person` instance.

[!code-csharp[Deconstruct-ambiguity](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-ambiguous.cs)]

## <a name="deconstructing-a-user-defined-type-with-discards"></a>Odstranění uživatelem definovaného typu s výměty

Stejně jako u [řazených kolekcí členů](#deconstructing-tuple-elements-with-discards)můžete použít `Deconstruct` zahozené položky k ignorování vybraných položek vrácených metodou. Každý zahození je definovánproměnnou s názvem "\_" a jedna operace dekonstrukce může obsahovat více zahození.

Následující příklad dekonstruuje `Person` objekt do čtyř řetězců (křestní jméno a příjmení, město a stát), ale zahodí příjmení a stav.

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs#1)]

## <a name="deconstructing-a-user-defined-type-with-an-extension-method"></a>Dekonstrukce uživatelem definovaného typu metodou rozšíření

Pokud jste nevytvořili třídu, strukturu nebo rozhraní, můžete stále dekonstruovat objekty `Deconstruct` tohoto typu implementací jedné nebo více [metod rozšíření](programming-guide/classes-and-structs/extension-methods.md) a vrátit hodnoty, které vás zajímají.

Následující příklad definuje `Deconstruct` dvě metody <xref:System.Reflection.PropertyInfo?displayProperty=nameWithType> rozšíření pro třídu. První vrátí sadu hodnot, které označují charakteristiky vlastnosti, včetně jejího typu, zda je statické nebo instance, zda je jen pro čtení a zda je indexován. Druhý označuje dostupnost vlastnosti. Vzhledem k tomu, že přístupové objekty přístupů get a set se mohou lišit, logické hodnoty označují, zda má vlastnost samostatné přístupové objekty get a set, a pokud ano, zda mají stejnou přístupnost. Pokud existuje pouze jeden přistupující objekt nebo oba get a `access` set přístupový objekt mají stejnou přístupnost, proměnná označuje usnadnění vlastnosti jako celku. V opačném případě jsou přístupnosti přístupových částí get `getAccess` `setAccess` a set označeny proměnnými a.

[!code-csharp[Extension-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-extension1.cs)]

## <a name="see-also"></a>Viz také

- [Zahození](discards.md)
- [Záznamů](tuples.md)
