---
title: Struktury – průvodce v C#
description: Další informace o typu Struktura a jak vytvořit
ms.date: 10/12/2016
ms.assetid: a7094b8c-7229-4b6f-82fc-824d0ea0ec40
ms.openlocfilehash: 6fcd30907880be9159b3cc2e3ab10659ddec248b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706452"
---
# <a name="structs"></a>Struktury
A *struktura* je typ hodnoty. Když se vytvoří struktura, obsahuje proměnné, ke kterému je přiřazena struktura, obsahovat skutečná data. Když je struktura přiřazena nové proměnné, zkopíruje se. Nové proměnné a původní proměnné proto obsahují dvě oddělené kopie stejných dat. Změny provedené v jedné kopii neovlivní druhou kopii.

Hodnoty typových proměnných přímo obsahují své hodnoty, což znamená, že paměť je přidělena vnitřně v jakémkoli kontextu je proměnná deklarována. Neexistuje samostatné přidělení haldy nebo zařazení kolekce paměti pro proměnné typu hodnoty.  
  
Existují dvě kategorie typů hodnot: [struktura](./language-reference/keywords/struct.md) a [výčtu](./language-reference/keywords/enum.md).  
  
Předdefinované číselné typy jsou struktury a mají vlastnosti a metody, které dostanete:  
  
[!code-csharp[Static Method](../../samples/snippets/csharp/concepts/structs/static-method.cs)]
  
Ale deklarujete je a přiřadit jim hodnoty tak jako by byly jednoduché neagregované typy:  
  
[!code-csharp[Assign Values](../../samples/snippets/csharp/concepts/structs/assign-value.cs)] 
  
Typy hodnot jsou *zapečetěné*, což znamená, že, například, že nemůžete odvodit typ z <xref:System.Int32>, a nemůžete definovat strukturu pro dědění z jakéhokoli uživatelsky definované třídy nebo struktury, protože struktura může dědit jedině z <xref:System.ValueType> . Strukturu však můžete implementovat jednu nebo více rozhraní. Můžete přetypovat obsadit typ struktury pro typ rozhraní; To způsobí, že *zabalení* operace zalomí strukturu uvnitř odkazu typu objektu na spravované haldě. K operaci zabalení dochází při předání typu hodnoty metodě, která přebírá <xref:System.Object> jako vstupní parametr. Další informace najdete v tématu [zabalení a rozbalení](./programming-guide/types/boxing-and-unboxing.md ).  
  
Můžete použít [struktura](./language-reference/keywords/struct.md) – klíčové slovo k tvorbě vlastních typů vlastní hodnotu. Obvykle struktura slouží jako kontejner pro malou skupinu příbuzných proměnných, jak je znázorněno v následujícím příkladu:  
  
[!code-csharp[Struct Keyword](../../samples/snippets/csharp/concepts/structs/struct-keyword.cs)]  
  
Další informace o typech hodnot v rozhraní .NET Framework najdete v tématu [obecný systém typů](../standard/common-type-system.md).  
    
Většinu podle stejné syntaxe jako třídy, struktury sdílet, ačkoli struktury jsou omezeny více než třídy:  
  
- V deklaraci struktury nelze inicializovat pole, jestliže nejsou deklarovány jako `const` nebo `static`.  
  
- Struktury nelze deklarovat konstruktor bez parametrů (konstruktor bez parametrů) nebo finalizační metodu.  
  
- Struktury se zkopírují na přiřazení. Když je struktura přiřazena nové proměnné, se data kopírují a jakékoli změny nová kopie nezmění data pro původní kopírování. To je důležité pamatovat při práci s kolekcemi typů hodnot, jako je například Dictionary < string, myStruct >.  
  
- Struktury jsou typy hodnot a třídy jsou odkazové typy.  
  
- Na rozdíl od tříd, struktur dá vytvořit instance bez použití `new` operátor.  
  
- Struktury můžete deklarovat konstruktory, které mají parametry.  
  
- Struktura nemůže dědit z jiné třídy nebo struktury a nemůže být základní třídy. Všechny struktury dědí přímo z <xref:System.ValueType>, který dědí z <xref:System.Object>.  
  
- Struktury můžou implementovat rozhraní.

## <a name="literal-values"></a>Hodnoty literálu  
V jazyce C# hodnoty literálu získávají typ z kompilátoru. Můžete určit, jak by měly být typu číselný literál přidáním písmene na konci čísla. Například chcete-li určit, že by měl hodnotou 4,56 zacházet jako s float, přidejte k "f" nebo "F" za číslo: `4.56f`. Pokud není připojeno žádné písmeno, kompilátor odvodí `double` typ literál. Další informace o tom, které mohou být typy specifikovat písmennými příponami, najdete v referenčních stránkách pro jednotlivé typy v [hodnotách](./language-reference/keywords/value-types.md).  
  
Vzhledem k tomu, že jsou literály typovány a všechny typy jsou nakonec odvozeny z <xref:System.Object>, můžete psát a kompilovat kód následujícím:  
  
[!code-csharp[Literal Values](../../samples/snippets/csharp/concepts/structs/literals.cs)]

Poslední dva příklady znázorňují funkce jazyka C# 7.0. První umožňuje použít jako podtržítkem *oddělovač číslic* v numerických literálech. Můžete je umístit kdekoli budete chtít mezi číslicemi, aby se zlepšila čitelnost. Nemají žádný účinek na hodnotě.

Ukazuje, druhý *binární literály:*, které vám umožňují určit bitové vzory přímo namísto použití šestnáctkové soustavě.

## <a name="nullable-types"></a>Typy s povolenou hodnotou Null  
Typy běžných hodnot nemohou mít hodnotu [null](./language-reference/keywords/null.md). Můžete však vytvořit typy s možnou hodnotou Null přidáním **?** Po vytvoření typu. Například **int?** je **int** typ, který může mít také hodnotu [null](./language-reference/keywords/null.md). V CTS jsou typy připouštějící hodnotu Null instancemi obecného typu struktury <xref:System.Nullable%601>. Typy s možnou hodnotou Null jsou zvláště užitečné při předávání dat do a z databáze, ve kterých mohou být číselné hodnoty null. Další informace najdete v tématu [typy s možnou hodnotou Null (C# Programming Guide)](./programming-guide/nullable-types/index.md).

## <a name="see-also"></a>Viz také:

- [Třídy](classes.md)
- [Základní typy](basic-types.md)
