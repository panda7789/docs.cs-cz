---
title: Dekonstrukce řazených kolekcí členů a dalších typů
description: Naučte se, jak dekonstruovat řazené kolekce členů a jiné typy.
ms.technology: csharp-fundamentals
ms.date: 11/23/2017
ms.assetid: 0b0c4b0f-4a47-4f66-9b8e-f5c63b195960
ms.openlocfilehash: 8defd75a7cdff3490d2b0a6097ec2a898576e113
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174163"
---
# <a name="deconstructing-tuples-and-other-types"></a>Dekonstrukce řazených kolekcí členů a dalších typů

Řazená kolekce členů poskytuje jednoduchý způsob, jak načíst více hodnot z volání metody. Po načtení řazené kolekce členů je ale nutné zpracovat jeho jednotlivé prvky. Provedení tohoto postupu na základě prvku je náročné, jak ukazuje následující příklad. `QueryCityData`Metoda vrací tři řazené kolekce členů a každý z jejích elementů je přiřazena proměnné v samostatné operaci.

[!code-csharp[WithoutDeconstruction](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple1.cs)]

Načítání více hodnot polí a vlastností z objektu může být stejně náročné: je nutné přiřadit hodnotu pole nebo vlastnosti proměnné na členě v rámci člena.

Počínaje jazykem C# 7,0 můžete načíst více prvků z řazené kolekce členů nebo načíst více polí, vlastností a vypočítaných hodnot z objektu v rámci jediné operace *dekonstrukce* . Při dekonstrukci řazené kolekce členů přiřadíte jeho prvky jednotlivým proměnným. Při dekonstrukci objektu přiřadíte vybrané hodnoty jednotlivým proměnným.

## <a name="deconstructing-a-tuple"></a>Dekonstrukce řazené kolekce členů

Funkce C# nabízí integrovanou podporu pro dekonstrukci řazených kolekcí členů, která umožňuje odbalit všechny položky v řazené kolekci členů v rámci jedné operace. Obecná syntaxe pro dekonstrukci řazené kolekce členů je podobná syntaxi pro definování jednoho: můžete uzavřít proměnné, ke kterým je každý element přiřazen v závorkách na levé straně příkazu přiřazení. Například následující příkaz přiřadí prvky množiny o 4-tice ke čtyřem samostatným proměnným:

```csharp
var (name, address, city, zip) = contact.GetAddressInfo();
```

Existují tři způsoby, jak vytvořit řazenou kolekci členů:

- Můžete explicitně deklarovat typ každého pole uvnitř závorek. Následující příklad používá tento přístup k dekonstrukci 3 – řazené kolekce členů vráceného `QueryCityData` metodou.

    [!code-csharp[Deconstruction-Explicit](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple2.cs#1)]

- Klíčové slovo lze použít `var` tak, aby C# odvodí typ každé proměnné. `var`Klíčové slovo umístíte mimo závorky. Následující příklad používá odvození typu při dekonstrukci 3 – řazené kolekce členů vráceného `QueryCityData` metodou.

    [!code-csharp[Deconstruction-Infer](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple3.cs#1)]

    Klíčové slovo lze použít také `var` jednotlivě spolu se všemi nebo všemi deklaracemi proměnných uvnitř závorek.

    [!code-csharp[Deconstruction-Infer-Some](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple4.cs#1)]

    To je náročné a nedoporučuje se.

- Nakonec můžete vytvořit řazenou kolekci členů do proměnných, které již byly deklarovány.

    [!code-csharp[Deconstruction-Declared](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple5.cs#1)]

Všimněte si, že nemůžete zadat konkrétní typ mimo závorky, a to ani v případě, že každé pole v řazené kolekci členů má stejný typ. Tím dojde k chybě kompilátoru CS8136, "Dekonstrukce ' var (...) Form nepovoluje konkrétní typ pro ' var '.

Všimněte si, že musíte také přiřadit každý prvek řazené kolekce členů k proměnné. Vynecháte-li nějaké prvky, kompilátor vygeneruje chybu CS8132, "nelze dekonstruovat řazenou kolekci členů" x "elementů do proměnných" y ".

Všimněte si, že nemůžete kombinovat deklarace a přiřazení k existujícím proměnným na levé straně dekonstrukce. Kompilátor generuje chybu CS8184, "Dekonstrukce nemůže kombinovat deklarace a výrazy na levé straně." Když členové obsahují nově deklarované a existující proměnné.

## <a name="deconstructing-tuple-elements-with-discards"></a>Rekonstrukce elementů řazené kolekce členů s výměty

Při dekonstrukci řazené kolekce členů se často zajímá hodnoty jenom některých prvků. Počínaje jazykem C# 7,0 můžete využít výhod podpory jazyka C# pro *zahození*, což jsou proměnné pouze pro zápis, jejichž hodnoty jste se rozhodli ignorovat. Zahození je určeno znakem podtržítka (" \_ ") v přiřazení. Můžete zahodit libovolný počet hodnot, které chcete. Všechny jsou reprezentovány jediným zahozením, `_` .

Následující příklad znázorňuje použití řazených kolekcí členů s výměty. `QueryCityDataForYears`Metoda vrátí 6 – řazené kolekce členů s názvem města, jeho oblastí, rokem, populacem města pro daný rok, druhým rokem a plněním města pro daný druhý rok. V tomto příkladu se zobrazuje změna populace mezi těmito dvěma roky. Z dat, která jsou k dispozici v rámci řazené kolekce členů, jsme nevěděli s oblastí město a znali jsme název města a dvě datum v době návrhu. V důsledku toho se zajímá jenom o dvě hodnoty populace uložené v řazené kolekci členů a můžou své zbývající hodnoty zpracovat jako zahozené.  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

## <a name="deconstructing-user-defined-types"></a>Dekonstrukce uživatelem definovaných typů

Jazyk C# nenabízí integrovanou podporu pro dekonstrukci typů, které nejsou řazené kolekce členů. Nicméně jako autor třídy, struktury nebo rozhraní můžete dovolit, aby byly instance typu dekonstruovány implementací jedné nebo více `Deconstruct` metod. Metoda vrací typ void a každá hodnota, která má být dekonstruována, je v signatuře metody označena [výstupním](language-reference/keywords/out-parameter-modifier.md) parametrem. Například následující `Deconstruct` Metoda `Person` třídy vrátí první, střední a poslední název:

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#1)]

Pak můžete dekonstruovat instanci `Person` třídy s názvem `p` s přiřazením, jako je následující:

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#2)]

Následující příklad přetěžuje `Deconstruct` metodu pro vrácení různých kombinací vlastností `Person` objektu. Jednotlivá přetížení vrátí:

- Křestní jméno a příjmení.
- První, poslední a prostřední jméno.
- Křestní jméno, příjmení, název města a název stavu.

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class2.cs)]

Vzhledem k tomu, že `Deconstruct` metodu lze přetížit tak, aby odrážela skupiny dat, které jsou běžně extrahovány z objektu, měli byste pečlivě definovat `Deconstruct` metody s signaturami, které jsou charakteristické a jednoznačné. Více `Deconstruct` metod, které mají stejný počet `out` parametrů nebo stejný počet a typ `out` parametrů v jiném pořadí, může způsobit nejasnost.

Přetížená `Deconstruct` metoda v následujícím příkladu znázorňuje jeden možný zdroj nejasností. První přetížení vrátí křestní jméno, prostřední jméno, příjmení a stáří `Person` objektu v tomto pořadí. Druhé přetížení vrátí pouze informace o názvu společně s ročním příjmem, ale první, prostřední a příjmení jsou v jiném pořadí. Díky tomu je snadné Zaměňujte pořadí argumentů při dekonstrukci `Person` instance.

[!code-csharp[Deconstruct-ambiguity](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-ambiguous.cs)]

## <a name="deconstructing-a-user-defined-type-with-discards"></a>Dekonstrukce uživatelsky definovaného typu s zahozením

Stejně jako v případě [řazených kolekcí členů](#deconstructing-tuple-elements-with-discards)můžete použít zahození pro ignorování vybraných položek vrácených `Deconstruct` metodou. Každé zrušení je definováno proměnnou s názvem " \_ " a jedinou operací dekonstrukce může zahrnovat více zahození.

Následující příklad dekonstruuje `Person` objekt do čtyř řetězců (křestní jméno a příjmení, město a stav), ale zahodí příjmení a stav.

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs#1)]

## <a name="deconstructing-a-user-defined-type-with-an-extension-method"></a>Dekonstrukce uživatelsky definovaného typu s metodou rozšíření

Pokud jste nevytvořili třídu, strukturu nebo rozhraní, můžete stále dekonstruovat objekty tohoto typu implementací jedné nebo více `Deconstruct` [rozšiřujících metod](programming-guide/classes-and-structs/extension-methods.md) , které vrátí hodnoty, které vás zajímají.

Následující příklad definuje dvě `Deconstruct` metody rozšíření pro <xref:System.Reflection.PropertyInfo?displayProperty=nameWithType> třídu. První vrátí sadu hodnot, které určují vlastnosti vlastnosti, včetně jejího typu, bez ohledu na to, zda je statická nebo instance, zda je pouze pro čtení a zda je indexována. Druhý označuje přístupnost vlastnosti. Vzhledem k tomu, že přístupnost přístupových objektů Get a set se může lišit, logické hodnoty označují, zda má vlastnost samostatné přístupové objekty get a set, a pokud má, zda mají stejné přístupnost. Je-li k dispozici pouze jeden přistupující objekt, nebo přistupující objekt get i Set musí mít stejné přístupnost, `access` Proměnná označuje přístupnost vlastnosti jako celku. V opačném případě přístupnost přístupových objektů Get a set jsou označeny `getAccess` `setAccess` proměnnými a.

[!code-csharp[Extension-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-extension1.cs)]

## <a name="see-also"></a>Viz také

- [Zahození](discards.md)
- [Typy řazené kolekce členů](language-reference/builtin-types/value-tuples.md)
