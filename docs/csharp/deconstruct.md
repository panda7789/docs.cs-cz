---
title: Dekonstrukce řazených kolekcí členů a dalších typů
description: Naučte se, jak dekonstruovat řazené kolekce členů a jiné typy.
ms.technology: csharp-fundamentals
ms.date: 07/18/2016
ms.assetid: 0b0c4b0f-4a47-4f66-9b8e-f5c63b195960
ms.openlocfilehash: 23d193faf9702628698fe558f6667aeb130e8916
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73100665"
---
# <a name="deconstructing-tuples-and-other-types"></a>Dekonstrukce řazených kolekcí členů a dalších typů

Řazená kolekce členů poskytuje jednoduchý způsob, jak načíst více hodnot z volání metody. Po načtení řazené kolekce členů je ale nutné zpracovat jeho jednotlivé prvky. Provedení tohoto postupu na základě prvku je náročné, jak ukazuje následující příklad. Metoda `QueryCityData` vrací 3-Tuple a každý z jeho elementů je přiřazen proměnné v samostatné operaci.

[!code-csharp[WithoutDeconstruction](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple1.cs)]

Načítání více hodnot polí a vlastností z objektu může být stejně náročné: je nutné přiřadit hodnotu pole nebo vlastnosti proměnné na členě v rámci člena.

Počínaje C# 7,0 můžete načíst více prvků z řazené kolekce členů nebo načíst více polí, vlastností a vypočítaných hodnot z objektu v rámci jediné operace *dekonstrukce* . Při dekonstrukci řazené kolekce členů přiřadíte jeho prvky jednotlivým proměnným. Při dekonstrukci objektu přiřadíte vybrané hodnoty jednotlivým proměnným.

## <a name="deconstructing-a-tuple"></a>Dekonstrukce řazené kolekce členů

C#nabízí integrovanou podporu pro dekonstrukci řazených kolekcí členů, která umožňuje odbalit všechny položky v řazené kolekci členů v rámci jedné operace. Obecná syntaxe pro dekonstrukci řazené kolekce členů je podobná syntaxi pro definování jednoho: můžete uzavřít proměnné, ke kterým je každý element přiřazen v závorkách na levé straně příkazu přiřazení. Například následující příkaz přiřadí prvky množiny o 4-tice ke čtyřem samostatným proměnným:

```csharp
var (name, address, city, zip) = contact.GetAddressInfo();
```

Existují tři způsoby, jak vytvořit řazenou kolekci členů:

- Můžete explicitně deklarovat typ každého pole uvnitř závorek. Následující příklad používá tento přístup k dekonstrukci 3 – řazené kolekce členů vráceného metodou `QueryCityData`.

    [!code-csharp[Deconstruction-Explicit](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple2.cs#1)]

- Pomocí klíčového slova `var` lze C# odvodit typ každé proměnné. Klíčové slovo `var` umístíte mimo závorky. Následující příklad používá odvození typu při dekonstrukci 3-řazené kolekce členů vráceného metodou `QueryCityData`.

    [!code-csharp[Deconstruction-Infer](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple3.cs#1)]

    Klíčové slovo `var` lze také použít jednotlivě spolu se všemi nebo všemi deklaracemi proměnných uvnitř závorek.

    [!code-csharp[Deconstruction-Infer-Some](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple4.cs#1)]

    To je náročné a nedoporučuje se.

- Nakonec můžete vytvořit řazenou kolekci členů do proměnných, které již byly deklarovány.

    [!code-csharp[Deconstruction-Declared](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple5.cs#1)]

Všimněte si, že nemůžete zadat konkrétní typ mimo závorky, a to ani v případě, že každé pole v řazené kolekci členů má stejný typ. Tím dojde k chybě kompilátoru CS8136, "Dekonstrukce ' var (...) Form nepovoluje konkrétní typ pro ' var '.

Všimněte si, že musíte také přiřadit každý prvek řazené kolekce členů k proměnné. Vynecháte-li nějaké prvky, kompilátor vygeneruje chybu CS8132, "nelze dekonstruovat řazenou kolekci členů" x "elementů do proměnných" y ".

Všimněte si, že nemůžete kombinovat deklarace a přiřazení k existujícím proměnným na levé straně dekonstrukce. Kompilátor generuje chybu CS8184, "Dekonstrukce nemůže kombinovat deklarace a výrazy na levé straně." Když členové obsahují nově deklarované a existující proměnné.

## <a name="deconstructing-tuple-elements-with-discards"></a>Rekonstrukce elementů řazené kolekce členů s výměty

Při dekonstrukci řazené kolekce členů se často zajímá hodnoty jenom některých prvků. Počínaje C# 7,0 můžete využít výhod C#podpory pro *zahození*, což jsou proměnné jen pro zápis, jejichž hodnoty jste se rozhodli ignorovat. Zahození je určeno znakem podtržítka ("\_") v přiřazení. Můžete zahodit libovolný počet hodnot, které chcete. Všechny jsou reprezentovány jediným zahozením `_`.

Následující příklad znázorňuje použití řazených kolekcí členů s výměty. Metoda `QueryCityDataForYears` vrací 6 – řazené kolekce členů s názvem města, jeho oblasti, roku, populacem města pro tento rok, druhým rokem a plněním města pro daný druhý rok. V tomto příkladu se zobrazuje změna populace mezi těmito dvěma roky. Z dat, která jsou k dispozici v rámci řazené kolekce členů, jsme nevěděli s oblastí město a znali jsme název města a dvě datum v době návrhu. V důsledku toho se zajímá jenom o dvě hodnoty populace uložené v řazené kolekci členů a můžou své zbývající hodnoty zpracovat jako zahozené.  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

## <a name="deconstructing-user-defined-types"></a>Dekonstrukce uživatelem definovaných typů

C#nenabízí integrovanou podporu pro dekonstrukci typů, které nejsou řazené kolekce členů. Nicméně jako autor třídy, struktury nebo rozhraní můžete dovolit, aby byly instance typu dekonstruovány implementací jedné nebo více `Deconstruct` metod. Metoda vrací typ void a každá hodnota, která má být dekonstruována, je v signatuře metody označena [výstupním](language-reference/keywords/out-parameter-modifier.md) parametrem. Například následující metoda `Deconstruct` třídy `Person` vrátí první, prostřední a příjmení:

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#1)]

Pak můžete dekonstruovat instanci `Person` třídy s názvem `p` s přiřazením podobným následujícím:

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#2)]

Následující příklad převede metodu `Deconstruct` pro vrácení různých kombinací vlastností objektu `Person`. Jednotlivá přetížení vrátí:

- Křestní jméno a příjmení.
- První, poslední a prostřední jméno.
- Křestní jméno, příjmení, název města a název stavu.

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class2.cs)]

Vzhledem k tomu, že metodu `Deconstruct` lze přetížit tak, aby odrážela skupiny dat, které jsou běžně extrahovány z objektu, měli byste pečlivě definovat `Deconstruct` metody s signaturami, které jsou charakteristické a jednoznačné. Více `Deconstruct` metod, které mají stejný počet parametrů `out` nebo stejné číslo a typ `out` parametrů v jiném pořadí, může způsobit nejasnost.

Přetížená metoda `Deconstruct` v následujícím příkladu znázorňuje jeden možný zdroj nejasností. První přetížení vrátí křestní jméno, prostřední jméno, příjmení a stáří objektu `Person` v tomto pořadí. Druhé přetížení vrátí pouze informace o názvu společně s ročním příjmem, ale první, prostřední a příjmení jsou v jiném pořadí. Díky tomu je snadné Zaměňujte pořadí argumentů při dekonstrukci instance `Person`.

[!code-csharp[Deconstruct-ambiguity](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-ambiguous.cs)]

## <a name="deconstructing-a-user-defined-type-with-discards"></a>Dekonstrukce uživatelsky definovaného typu s zahozením

Stejně jako v případě [řazených kolekcí členů](#deconstructing-tuple-elements-with-discards)můžete použít zahození pro ignorování vybraných položek vrácených metodou `Deconstruct`. Každé zrušení je definováno proměnnou s názvem "\_" a jedinou operací dekonstrukce může zahrnovat více zahození.

Následující příklad dekonstruuje objekt `Person` do čtyř řetězců (křestní jméno a příjmení, město a stav), ale zahodí příjmení a stav.

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs#1)]

## <a name="deconstructing-a-user-defined-type-with-an-extension-method"></a>Dekonstrukce uživatelsky definovaného typu s metodou rozšíření

Pokud jste nevytvořili třídu, strukturu nebo rozhraní, můžete stále dekonstruovat objekty tohoto typu implementací jedné nebo více `Deconstruct` [rozšiřujících metod](programming-guide/classes-and-structs/extension-methods.md) , abyste vrátili hodnoty, které vás zajímají.

Následující příklad definuje dvě `Deconstruct` rozšiřující metody pro třídu <xref:System.Reflection.PropertyInfo?displayProperty=nameWithType>. První vrátí sadu hodnot, které určují vlastnosti vlastnosti, včetně jejího typu, bez ohledu na to, zda je statická nebo instance, zda je pouze pro čtení a zda je indexována. Druhý označuje přístupnost vlastnosti. Vzhledem k tomu, že přístupnost přístupových objektů Get a set se může lišit, logické hodnoty označují, zda má vlastnost samostatné přístupové objekty get a set, a pokud má, zda mají stejné přístupnost. Je-li k dispozici pouze jeden přistupující objekt, nebo přistupující objekt get i Set musí mít stejné přístupnost, proměnná `access` označuje přístupnost vlastnosti jako celku. V opačném případě jsou přístupnost přístupových objektů Get a set označeny `getAccess` a `setAccess` proměnných.

[!code-csharp[Extension-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-extension1.cs)]

## <a name="see-also"></a>Viz také:

- [Zahození](discards.md)
- [Řazené kolekce členů](tuples.md)
