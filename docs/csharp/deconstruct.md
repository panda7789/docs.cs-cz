---
title: Deconstructing řazených kolekcí členů a dalších typů
description: Naučte se deconstruct řazených kolekcí členů a dalších typů.
author: rpetrusha
ms.author: ronpet
ms.date: 07/18/2016
ms.assetid: 0b0c4b0f-4a47-4f66-9b8e-f5c63b195960
ms.openlocfilehash: 726a391a4a747e5446e252e669c5b16248a5e0ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217742"
---
# <a name="deconstructing-tuples-and-other-types"></a>Deconstructing řazených kolekcí členů a dalších typů #

Řazené kolekce členů poskytuje šedé – způsob, jak načíst více hodnot z volání metody. Ale po načtete řazenou kolekci členů, je potřeba zpracovat jeho jednotlivé prvky. To na základě elementu pomocí elementu je náročnější, jak ukazuje následující příklad. `QueryCityData` , Metoda vrátí 3-řazené kolekce členů, každý z jeho elementy je přiřazený k proměnné v rámci samostatné operace.

[!code-csharp[WithoutDeconstruction](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple1.cs)]

Načítání více hodnot pro pole a vlastnosti z objektu může být stejně náročná: je potřeba přiřadit hodnotu pole nebo vlastnost proměnné na základě člena člena. 

Od verze 7.0 C#, můžete načíst více prvků z řazené kolekce členů nebo načíst více pole, vlastnosti a počítaných hodnot z objektu v jedné *deconstruct* operaci. Pokud jste deconstruct řazené kolekce členů, přiřadíte jeho elementy jednotlivé proměnné. Pokud jste deconstruct objekt, přiřadíte vybrané hodnoty jednotlivých proměnné. 

## <a name="deconstructing-a-tuple"></a>Deconstructing řazené kolekce členů

C# – funkce integrovanou podporu pro deconstructing řazené kolekce členů, který vám umožňuje rozbalit všechny položky v řazené kolekce členů v rámci jedné operace. Obecná syntaxe deconstructing řazené kolekce členů je podobná syntaxi pro definování jednu: uzavřete proměnné, do kterých má být přiřazena v závorkách v levé části příkazu přiřazení každý prvek. Například následující příkaz přiřadí elementy 4-řazené kolekce členů čtyři samostatné proměnné:

```csharp
var (name, address, city, zip) = contact.GetAddressInfo();
```

Existují tři způsoby, jak deconstruct řazené kolekce členů:

- Je možné deklarovat explicitně typ každé pole v závorkách. Následující příklad používá tento přístup k deconstruct 3 řazené kolekce členů vrácený `QueryCityData` metoda.

    [!code-csharp[Deconstruction-Explicit](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple2.cs#1)]

- Můžete použít `var` – klíčové slovo, že C# odvodí typ pro každou proměnnou. Umístit `var` – klíčové slovo mimo závorkách. Následující příklad používá odvození typu při deconstructing 3 řazené kolekce členů vrácený `QueryCityData` metoda.
 
    [!code-csharp[Deconstruction-Infer](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple3.cs#1)]

    Můžete také `var` – klíčové slovo jednotlivě s některého nebo všech deklarace proměnných v závorkách. 

    [!code-csharp[Deconstruction-Infer-Some](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple4.cs#1)]

    Toto je náročná a se nedoporučuje.

- Nakonec může deconstruct řazenou kolekci členů do proměnné, které již byl deklarován.

    [!code-csharp[Deconstruction-Declared](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple5.cs#1)]

Všimněte si, že i v případě, že každé pole v řazené kolekci členů má stejný typ nelze zadat konkrétní typ mimo závorkách. To vygeneruje Chyba kompilátoru CS8136, "formuláře 'var (...)' Deconstruction zakáže konkrétního typu pro 'var'.".

Všimněte si, že je nutné přiřadit také každý prvek řazenou kolekci členů k proměnné. Pokud nezadáte žádné elementy, kompilátor vygeneruje chyba CS8132, "Nelze deconstruct řazená kolekce členů x elementy do proměnné"y"."

Všimněte si, že není možné kombinovat deklarace a přiřazení do existujících proměnných na levé straně deconstruction. Kompilátor vygeneruje chyba CS8184, "deconstruction nelze kombinovat deklarace a výrazy na levou-stranu-straně." Když členy obsahovat nově deklarované a existující proměnné.

## <a name="deconstructing-tuple-elements-with-discards"></a>Deconstructing prvky řazené kolekce členů s zahodí

Často při deconstructing řazené kolekce členů, co vás zajímá hodnoty jenom některé prvky. Od verze 7.0 C#, můžete využít výhod podpory jazyka C# na pro *zahodí*, které jsou jen pro zápis proměnné, jejichž hodnoty, které jste se rozhodli ignorovat. Zahození je určen znakem podtržítka ("\_") v přiřazení. Zahodit tolik hodnoty podle potřeby; všechny jsou reprezentované pomocí jedné zahození `_`.

Následující příklad ukazuje použití řazené kolekce členů s zahození. `QueryCityDataForYears` Metoda vrátí hodnotu 6-řazené kolekce členů s názvem města, jeho oblasti, rok, název města plnění pro tento rok, druhý roku a název města plnění pro tento druhý roku. Příklad ukazuje změnu v plnění mezi tyto dva roky. Data k dispozici z řazenou kolekci členů, jsme unconcerned oblasti města a víme název města a kalendářní data v době návrhu. V důsledku toho jsme se pouze zajímá dvě naplnění hodnotami uloženými v řazené kolekci členů a jeho zbývající hodnoty jako zahození dokáže zpracovat.  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

### <a name="deconstructing-user-defined-types"></a>Deconstructing uživatelem definované typy

Typy bez řazené kolekce členů není nabízí integrovanou podporu pro zahodí. Však můžete jako autor třídy, struktury nebo rozhraní povolit typ, který má být deconstructed implementací jeden nebo více instancí `Deconstruct` metody. Metoda vrátí void a každou hodnotu být deconstructed je indikován [out](language-reference/keywords/out-parameter-modifier.md) parametr v podpis metody. Například následující `Deconstruct` metodu `Person` vrátí první a poslední název třídy:

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#1)]

Potom můžete deconstruct instanci `Person` třídu s názvem `p` spolu s přiřazením takto:

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#2)]

Následující příklad přetížení `Deconstruct` metoda vrátí různé kombinace vlastnosti `Person` objektu. Jednotlivé přetížení vrátit:

- První a poslední název.
- First, last a křestní jméno.
- Křestní jméno, příjmení, název města a název stavu.

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class2.cs)]

Vzhledem k tomu může dojít k přetížení `Deconstruct` metoda tak, aby odrážela skupiny dat, která se běžně extrahují z objekt, je třeba pečlivě k definování `Deconstruct` metody s podpisy, které jsou charakteristické a jednoznačné. Více `Deconstruct` metody, které mají stejný počet `out` parametry nebo stejný počet a typ `out` parametry v jiném pořadí může způsobit nejasnostem. 

Přetížené `Deconstruct` metoda následující příklad znázorňuje jeden zdroj možné záměny. Vrátí první přetížení křestní jméno, křestní jméno, příjmení a stáří `Person` objekt v tomto pořadí. Druhý přetížení vrátí název informace pouze společně s roční příjem, ale první a poslední název je v jiném pořadí. To umožňuje snadno zaměnit pořadí argumentů při deconstructing `Person` instance.

[!code-csharp[Deconstruct-ambiguity](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-ambiguous.cs)]

## <a name="deconstructing-a-user-defined-type-with-discards"></a>Deconstructing uživatelsky definovaný typ. se zahodí.

Stejně jako s [řazených kolekcí členů](#deconstructing-tuple-elements-with-discards), zahození můžete ignorovat vybraných položek vrácených `Deconstruct` metoda. Každý zahození je definované proměnné s názvem "\_", a operaci jeden deconstruction může obsahovat více zahození.

Následující příklad deconstructs `Person` objektu do čtyř řetězce (první a poslední názvů, Město a stav), ale zahodí příjmení a stavu.

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs#1)]

## <a name="deconstructing-a-user-defined-type-with-an-extension-method"></a>Deconstructing uživatelem definovaný typ pomocí metody rozšíření

Pokud vytváříte nebyla třída, struktura nebo rozhraní, můžete stále deconstruct objekty daného typu implementací jeden nebo více `Deconstruct` [rozšiřující metody](programming-guide/classes-and-structs/extension-methods.md) k návratu hodnot, které vás zajímají. 

V následujícím příkladu definuje dvě `Deconstruct` rozšiřující metody pro <xref:System.Reflection.PropertyInfo?displayProperty=nameWithType> třídy. Vrátí první sadu hodnot, které uvést parametry vlastnosti, včetně jeho typu, zda je statický nebo instanci, zda je jen pro čtení a jestli je indexovaný. Druhý určuje vlastnosti usnadnění. Protože usnadnění get a sadu přístupových objektů se může lišit, logické hodnoty označuje, zda má vlastnost samostatné získání a nastavení přístupových objektů a pokud ano, zda mají stejné usnadnění. Pokud je pouze jeden přistupujícího objektu nebo get i přistupující objekt set mají stejné usnadnění `access` proměnné označuje usnadnění vlastnost jako celek. V opačném usnadnění operace get a sadu přístupových objektů jsou označeny accessaccessibility je indikován `getAccess` a `setAccess` proměnné.

[!code-csharp[Extension-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-extension1.cs)]
 
## <a name="see-also"></a>Viz také
[Zahození](discards.md)   
[Řazené kolekce členů](tuples.md)  
