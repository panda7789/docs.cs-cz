---
title: Dekonstrukce řazených kolekcí členů a ostatními typy
description: Zjistěte, jak dekonstruovat řazených kolekcí členů a dalších typů.
author: rpetrusha
ms.author: ronpet
ms.date: 07/18/2016
ms.assetid: 0b0c4b0f-4a47-4f66-9b8e-f5c63b195960
ms.openlocfilehash: 48724c65de4fe71294eb5c61c1891d9d56c9b5a4
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44271780"
---
# <a name="deconstructing-tuples-and-other-types"></a>Dekonstrukce řazených kolekcí členů a ostatními typy

Řazená kolekce členů poskytuje odlehčené způsob, jak načíst několik hodnot z volání metody. Ale po načtení řazené kolekce členů je potřeba zpracovat jeho jednotlivé prvky. Na základě prvek po prvku je to náročná, jak ukazuje následující příklad. `QueryCityData` Metoda vrátí hodnotu 3-n-tice a každý z jeho prvků je přiřazená k proměnné v samostatné operaci.

[!code-csharp[WithoutDeconstruction](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple1.cs)]

Načítání více hodnot pole a vlastnosti z objektu může být stejně náročné: je potřeba přiřadit hodnotu pole nebo vlastnost každý člen členské proměnné.

Od verze C# 7.0, můžete načíst několik elementů z řazené kolekce členů nebo načtení více pole, vlastnosti a vypočítané hodnoty z objektu do jediného *dekonstruovat* operace. Pokud jste dekonstruovat řazené kolekce členů, přiřadíte jeho prvky jednotlivé proměnné. Když jste dekonstruovat objektu, přiřadíte vybraných hodnot jednotlivé proměnné.

## <a name="deconstructing-a-tuple"></a>Dekonstrukce řazené kolekce členů

Funkce C# integrovanou podporu pro dekonstrukce řazených kolekcí členů, které umožňuje rozbalit všechny položky v řazené kolekce členů v rámci jedné operace. Obecná syntaxe dekonstrukce řazené kolekce členů je podobná syntaxe pro definování: uzavřete proměnné, ke kterým má být přiřazena v závorkách na levé straně příkazu přiřazení jednotlivých prvků. Například následující příkaz přiřadí prvky 4-řazenou kolekci členů na čtyřech samostatných proměnné:

```csharp
var (name, address, city, zip) = contact.GetAddressInfo();
```

Existují tři způsoby, jak dekonstruovat řazené kolekce členů:

- Můžete explicitně deklarovat typ každého pole uvnitř závorek. Následující příklad používá tento přístup k dekonstruovat 3 řazené kolekce členů vrácené `QueryCityData` metody.

    [!code-csharp[Deconstruction-Explicit](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple2.cs#1)]

- Můžete použít `var` – klíčové slovo tak tohoto jazyka C# odvodí typ každou proměnnou. Umístíte `var` – klíčové slovo mimo závorky. Následující příklad používá odvození typu při dekonstrukce 3 řazené kolekce členů vrácené `QueryCityData` metody.

    [!code-csharp[Deconstruction-Infer](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple3.cs#1)]

    Můžete také použít `var` – klíčové slovo samostatně pomocí některé nebo všechny deklarace proměnných v závorkách.

    [!code-csharp[Deconstruction-Infer-Some](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple4.cs#1)]

    To je náročné a nedoporučuje se používat.

- A konečně může dekonstruovat řazené kolekce členů do proměnné, které už je deklarovaný.

    [!code-csharp[Deconstruction-Declared](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple5.cs#1)]

Všimněte si, že nelze zadat konkrétní typ mimo závorky i v případě každé pole v n-tice stejného typu. Tím se vygeneruje Chyba kompilátoru CS8136 "formulář Dekonstrukce 'var (...)' zakazuje určitého typu pro"var".".

Všimněte si, že musíte také přiřadit každý prvek řazené kolekce členů k proměnné. Pokud nezadáte žádné elementy, kompilátor vygeneruje chybu CS8132 "Nejde dekonstruovat se řazená kolekce členů"x"prvky do proměnné"y"."

Všimněte si, že nejde kombinovat deklarace a přiřazení existujících proměnných na levé straně dekonstrukce. Kompilátor vygeneruje chybu CS8184 "při dekonstrukci nejde kombinovat deklarace a výrazy v levé straně." Když členy obsahovat nově deklarované a existující proměnné.

## <a name="deconstructing-tuple-elements-with-discards"></a>Dekonstrukce elementů řazené kolekce členů se zahodí.

Při dekonstrukce řazené kolekce členů, často máte zájem hodnoty jenom některé prvky. Od verze C# 7.0, můžete využít výhod podpory jazyka C# pro *zahodí*, které jsou jen pro zápis proměnné jehož hodnoty, které jste se rozhodli ignorovat. Zahození je určeno znakem podtržítka ("\_") v přiřazení. Zahodit libovolný počet hodnot, jak chcete; všechny jsou reprezentované pomocí jedné zahození `_`.

Následující příklad ukazuje použití řazených kolekcí členů se zahodí. `QueryCityDataForYears` Metoda vrátí 6-řazené kolekce členů s názvem Město, jeho oblast, rok, název města plnění pro daný rok, druhý rok a název města plnění pro daný druhý rok. Příklad ukazuje změnu počtu obyvatel mezi tyto dva roky. Data k dispozici z řazené kolekce členů, jsme unconcerned k oblasti města a víme název města a dvěma kalendářními daty v době návrhu. V důsledku toho jsme zajímá pouze dvě naplnění hodnoty uložené v řazené kolekci členů a dokáže zpracovat zbývající hodnoty jako zahození.  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

### <a name="deconstructing-user-defined-types"></a>Dekonstrukce uživatelem definované typy

Typy bez řazené kolekce členů nejsou nabízejí integrovanou podporu pro zahodí. Jako autor třídy, struktury nebo rozhraní, můžete ale povolit instance daného typu, který možné dekonstruovat implementací jeden nebo více `Deconstruct` metody. Metoda vrací hodnotu void a každá hodnota na možné dekonstruovat. je označen [si](language-reference/keywords/out-parameter-modifier.md) parametr v podpisu metody. Například následující `Deconstruct` metodu `Person` vrátí první a poslední název třídy:

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#1)]

Potom můžete dekonstruovat instance `Person` třídu s názvem `p` s přiřazení následujícím postupem:

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#2)]

Následující příklad přetížení `Deconstruct` metoda vrátí různé kombinace vlastností `Person` objektu. Vrátí jednotlivé přetížení:

- První a poslední název.
- První, poslední a druhé křestní jméno.
- Křestní jméno, příjmení, název města a název stavu.

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class2.cs)]

Vzhledem k tomu může dojít k přetížení `Deconstruct` metodu tak, aby odrážely skupin dat, která se běžně extrahují z objektu, je třeba pečlivě definovat `Deconstruct` metody s podpisy, které jsou charakteristické a jednoznačný. Více `Deconstruct` metody, které mají stejný počet `out` parametry nebo stejný počet a typ `out` parametry v jiném pořadí, může způsobit zmatení.

Přetížené `Deconstruct` metodu v následujícím příkladu znázorňuje jeden stávají možným zdrojem nejasnostem. První přetížení vrátí křestní jméno, křestní jméno, příjmení a věk `Person` objekt v tomto pořadí. Druhé přetížení vrátí informace o názvu pouze spolu s roční příjem, ale první a poslední název jsou v jiném pořadí. To umožňuje snadno zaměnit pořadí argumentů při dekonstrukce `Person` instance.

[!code-csharp[Deconstruct-ambiguity](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-ambiguous.cs)]

## <a name="deconstructing-a-user-defined-type-with-discards"></a>Dekonstrukce typ definovaný uživatelem se zahodí.

Stejně, jako je tomu u [řazených kolekcí členů](#deconstructing-tuple-elements-with-discards), můžete ignorovat vybrané položky vrácené zahození `Deconstruct` metoda. Každý zahození je určené proměnnou s názvem "\_", a jeden dekonstrukce operace může obsahovat více zahození.

Následující příklad deconstructs `Person` objektu do čtyř řetězců (jména a příjmení, města a státu) ale zahodí poslední názvu a stavu.

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs#1)]

## <a name="deconstructing-a-user-defined-type-with-an-extension-method"></a>Uživatelem definovaný typ dekonstrukce s metodu rozšíření

Pokud jste neměli vytvářet třídy, struktury nebo rozhraní, můžete stále dekonstruovat objekty daného typu implementací jeden nebo více `Deconstruct` [rozšiřující metody](programming-guide/classes-and-structs/extension-methods.md) vracet hodnoty, které vás zajímá.

Následující příklad definuje dvě `Deconstruct` rozšiřující metody pro <xref:System.Reflection.PropertyInfo?displayProperty=nameWithType> třídy. Vrátí první sadu hodnot, které charakteristiku vlastnosti, včetně jeho typ, ať už jde o statické nebo instance, zda je jen pro čtení a určuje, zda se indexují. Druhý určuje vlastnosti usnadnění. Protože usnadnění get a přístupové objekty set se může lišit, logické hodnoty označuje, zda vlastnost má samostatné get i set přístupové objekty a pokud ano, ať už mají stejné usnadnění. Pokud existuje jenom jeden přistupující objekt nebo get i přístupový objekt set mají stejnou přístupností `access` proměnné označuje usnadnění vlastnost jako celek. V opačném případě usnadnění operace get a set přístupové objekty jsou označeny accessaccessibility je indikován `getAccess` a `setAccess` proměnné.

[!code-csharp[Extension-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-extension1.cs)]

## <a name="see-also"></a>Viz také:

- [Zahození](discards.md)
- [Řazené kolekce členů](tuples.md)  
