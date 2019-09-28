---
title: Struktury – C# Průvodce
description: Přečtěte si o typu struktury a způsobu jejich vytváření.
ms.date: 10/12/2016
ms.assetid: a7094b8c-7229-4b6f-82fc-824d0ea0ec40
ms.openlocfilehash: e0974b7dcf3c0888cb52bea81b07a58e3a98640b
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71396124"
---
# <a name="structs"></a>Struktury

*Struktura* je typ hodnoty. Při vytvoření struktury obsahuje proměnná, ke které je přiřazena struktura, vlastní data struktury. Když je struktura přiřazena nové proměnné, je zkopírována. Nová proměnná a původní proměnná proto obsahují dvě samostatné kopie stejných dat. Změny provedené v jedné kopii nemají vliv na ostatní kopírování.

Proměnné typu hodnoty přímo obsahují jejich hodnoty, což znamená, že je paměť přidělena vloženému v jakémkoli kontextu, kdy je proměnná deklarována. Neexistuje žádné samostatné přidělení haldy nebo režie uvolňování paměti pro proměnné typu hodnoty.  
  
Existují dvě kategorie typů hodnot: [struct](./language-reference/keywords/struct.md) a [Enum](./language-reference/keywords/enum.md).  
  
Předdefinované číselné typy jsou struktury a mají vlastnosti a metody, ke kterým máte přístup:  
  
[!code-csharp[Static Method](../../samples/snippets/csharp/concepts/structs/static-method.cs)]
  
Ale deklarujete a přiřadíte jim hodnoty, jako kdyby byly jednoduché neagregované typy:  
  
[!code-csharp[Assign Values](../../samples/snippets/csharp/concepts/structs/assign-value.cs)] 
  
Typy hodnot jsou *zapečetěné*, což znamená, že nemůžete odvodit typ z <xref:System.Int32> a nemůžete definovat strukturu, která by dědila z jakékoli uživatelsky definované třídy nebo struktury, protože struktura může dědit jenom z <xref:System.ValueType>. Struktura však může implementovat jedno nebo více rozhraní. Typ struktury můžete přetypovat na typ rozhraní; To způsobí, že operace *zabalení* zabalí strukturu uvnitř objektu typu reference na spravované haldě. K operacím zabalení dojde, když předáte typ hodnoty metodě, která jako vstupní parametr přebírá <xref:System.Object>. Další informace naleznete v tématu [zabalení a rozbalení](./programming-guide/types/boxing-and-unboxing.md ).  
  
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
  
- Struktura nemůže dědit z jiné struktury nebo třídy a nemůže být základem třídy. Všechny struktury dědí přímo z <xref:System.ValueType>, který dědí z <xref:System.Object>.  
  
- Struktura může implementovat rozhraní.

## <a name="literal-values"></a>Hodnoty literálu

V C#rozhraní hodnoty literálu obdrží typ z kompilátoru. Můžete určit, jak se má číselný literál zadat připojením písmene ke konci čísla. Například chcete-li určit, že hodnota 4,56 by měla být považována za float, přidejte "f" nebo "F" za číslo: `4.56f`. Pokud není připojeno žádné písmeno, kompilátor odvodí typ `double` pro literál. Další informace o tom, které typy lze zadat s příponami písmen, naleznete v tématu referenční stránky pro jednotlivé typy v [hodnotových typech](./language-reference/keywords/value-types.md).  
  
Vzhledem k tomu, že jsou zadány literály a všechny typy jsou odvozeny od <xref:System.Object>, můžete napsat a zkompilovat kód, například následující:  
  
[!code-csharp[Literal Values](../../samples/snippets/csharp/concepts/structs/literals.cs)]

Poslední dva příklady ukazují jazykové funkce představené v C# 7,0. První umožňuje použití znaku podtržítka jako *oddělovače číslic* v rámci numerických literálů. Můžete je umístit tam, kde chcete, aby se zlepšila čitelnost mezi číslicemi. Nemají na hodnotu žádný vliv.

Druhý ukazuje *binární literály*, které umožňují zadat bitové vzory přímo místo použití šestnáctkového zápisu.

## <a name="nullable-value-types"></a>Typy hodnot s možnou hodnotou null

Typy běžných hodnot nemohou mít hodnotu [null](language-reference/keywords/null.md). Můžete však vytvořit typy hodnot s možnou hodnotou null, a to tak, že za typ připojíte `?`. Například `int?` je typ `int`, který může mít také hodnotu [null](./language-reference/keywords/null.md). Typy s možnou hodnotou null jsou instancemi obecného typu struktury <xref:System.Nullable%601>. Typy hodnot s možnou hodnotou null jsou zvláště užitečné při předávání dat do a z databází, ve kterých mohou být číselné hodnoty null nebo nedefinovány. Další informace naleznete v tématu [typy hodnot s možnou hodnotou null](programming-guide/nullable-types/index.md).

## <a name="see-also"></a>Viz také:

- [Třídy](classes.md)
- [Základní typy](basic-types.md)
