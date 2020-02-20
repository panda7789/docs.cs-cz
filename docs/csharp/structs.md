---
title: Struktury – C# Průvodce
description: Přečtěte si o typu struktury a způsobu jejich vytváření.
ms.date: 10/12/2016
ms.technology: csharp-fundamentals
ms.assetid: a7094b8c-7229-4b6f-82fc-824d0ea0ec40
ms.openlocfilehash: 540742ea6a215e09f0cc31b218ac10fbf6192352
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503988"
---
# <a name="structs"></a>Struktury

*Struktura* je typ hodnoty. Při vytvoření struktury obsahuje proměnná, ke které je přiřazena struktura, vlastní data struktury. Když je struktura přiřazena nové proměnné, je zkopírována. Nová proměnná a původní proměnná proto obsahují dvě samostatné kopie stejných dat. Změny provedené v jedné kopii nemají vliv na ostatní kopírování.

Proměnné typu hodnoty přímo obsahují jejich hodnoty, což znamená, že je paměť přidělena vloženému v jakémkoli kontextu, kdy je proměnná deklarována. Neexistuje žádné samostatné přidělení haldy nebo režie uvolňování paměti pro proměnné typu hodnoty.

Existují dvě kategorie typů hodnot: [struct](language-reference/keywords/struct.md) a [Enum](language-reference/builtin-types/enum.md).

Předdefinované číselné typy jsou struktury a mají vlastnosti a metody, ke kterým máte přístup:

[!code-csharp[Static Method](../../samples/snippets/csharp/concepts/structs/static-method.cs)]

Ale deklarujete a přiřadíte jim hodnoty, jako kdyby byly jednoduché neagregované typy:

[!code-csharp[Assign Values](../../samples/snippets/csharp/concepts/structs/assign-value.cs)]

Typy hodnot jsou *zapečetěné*, což znamená, že nemůžete odvodit typ z <xref:System.Int32>a nemůžete definovat strukturu, která by dědila z jakékoli uživatelsky definované třídy nebo struktury, protože struktura může dědit pouze z <xref:System.ValueType>. Struktura však může implementovat jedno nebo více rozhraní. Typ struktury můžete přetypovat na typ rozhraní; To způsobí, že operace *zabalení* zabalí strukturu uvnitř objektu typu reference na spravované haldě. K operacím zabalení dojde, když předáte typ hodnoty metodě, která přijímá <xref:System.Object> jako vstupní parametr. Další informace naleznete v tématu [zabalení a rozbalení](./programming-guide/types/boxing-and-unboxing.md ).

Klíčové slovo [struct](./language-reference/keywords/struct.md) můžete použít k vytvoření vlastních typů hodnot. Struktura se obvykle používá jako kontejner pro malou sadu souvisejících proměnných, jak je znázorněno v následujícím příkladu:

[!code-csharp[Struct Keyword](../../samples/snippets/csharp/concepts/structs/struct-keyword.cs)]

Další informace o typech hodnot v .NET Framework naleznete v tématu [Common Type System](../standard/common-type-system.md).

Struktury sdílejí většinu stejné syntaxe jako třídy, i když jsou struktury více omezené než třídy:

- V rámci deklarace struktury nelze pole inicializovat, pokud nejsou deklarována jako `const` nebo `static`.

- Struktura nemůže deklarovat konstruktor bez parametrů (konstruktor bez parametrů) nebo finalizační metodu.

- Struktury se zkopírují při přiřazení. Když je struktura přiřazena nové proměnné, zkopírují se všechna data a jakákoli změna nové kopie nemění data původní kopie. To je důležité pamatovat při práci s kolekcemi typů hodnot, jako je slovník < String, myStruct >.

- Struktury jsou typy hodnot a třídy jsou odkazové typy.

- Na rozdíl od tříd lze vytvořit instanci struktur bez použití operátoru `new`.

- Struktury mohou deklarovat konstruktory, které mají parametry.

- Struktura nemůže dědit z jiné struktury nebo třídy a nemůže být základem třídy. Všechny struktury dědí přímo z <xref:System.ValueType>, které dědí z <xref:System.Object>.

- Struktura, jako je třída, může implementovat rozhraní.

## <a name="nullable-value-types"></a>Typy hodnot s povolenou hodnotou Null

Typy běžných hodnot nemohou mít hodnotu [null](language-reference/keywords/null.md). Můžete však vytvořit typy hodnot s možnou hodnotou null, a to tak, že po typu napřipojíte `?`. Například `int?` je `int` typ, který může mít také hodnotu [null](./language-reference/keywords/null.md). Typy s možnou hodnotou null jsou instancemi obecného typu struktury <xref:System.Nullable%601>. Typy hodnot s možnou hodnotou null jsou zvláště užitečné při předávání dat do a z databází, ve kterých mohou být číselné hodnoty null nebo nedefinovány. Další informace naleznete v tématu [typy hodnot s možnou hodnotou null](language-reference/builtin-types/nullable-value-types.md).

## <a name="see-also"></a>Viz také

- [Třídy](programming-guide/classes-and-structs/classes.md)
- [Základní typy](basic-types.md)
