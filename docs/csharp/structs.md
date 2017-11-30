---
title: "Struktury – Průvodce C#"
description: "Další informace o typu Struktura a jak vytvořit"
keywords: "Rozhraní .NET, rozhraní .NET core, C#"
author: BillWagner
ms.author: wiwagn
ms.date: 10/12/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a7094b8c-7229-4b6f-82fc-824d0ea0ec40
ms.openlocfilehash: 4c12e886ec388671fc47f08f8df6d6f2af8aac62
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2017
---
# <a name="structs"></a>Struktury
A *struktura* je typ hodnoty. Když je vytvořen struktury, obsahuje proměnnou, ke kterému je přiřazena struct struktura na skutečná data. Když struktura je přiřazen k nové proměnné, je zkopírována. Novou proměnnou a původní proměnná proto obsahovat dvě samostatné kopie stejná data. Změny provedené v jedné kopie nemají vliv na jiné kopie.

Hodnota typu proměnné přímo obsahovat jejich hodnoty, které znamená, že je paměť přidělená vložený v jakémkoli kontextu je deklarovaná proměnnou. Neexistuje žádné přidělení haldy samostatný nebo Režijní náklady na shromažďování uvolňování paměti pro typ hodnoty proměnné.  
  
Existují dvě kategorie typů hodnot: [struktura](./language-reference/keywords/struct.md) a [výčtu](./language-reference/keywords/enum.md).  
  
Předdefinované číselnými typy jsou struktury a mají vlastnosti a metody, které dostanete:  
  
[!code-csharp[Static Method](../../samples/snippets/csharp/concepts/structs/static-method.cs)]
  
Ale deklarace a k nim přiřadíte hodnoty, jako kdyby byly jednoduché typy neagregačními:  
  
[!code-csharp[Assign Values](../../samples/snippets/csharp/concepts/structs/assign-value.cs)] 
  
Typy hodnot jsou *zapečetěné*, což znamená, například, že nelze odvodit typ z <xref:System.Int32>, a nelze definovat struktury dědění z jakékoli uživatelsky definované třídy, nebo struktura, protože struktury může dědit vlastnosti pouze z <xref:System.ValueType> . Struktury však můžete implementovat jednu nebo více rozhraní. Může odevzdat typu Struktura k typu rozhraní; To způsobí, že *zabalení* operace obtékat spravovaná halda struktura uvnitř objekt typu odkaz. Operace zabalení dojít, když na metodu, která přebírá předáte typ hodnoty <xref:System.Object> jako vstupní parametr. Další informace najdete v tématu [zabalení a rozbalení](./programming-guide/types/boxing-and-unboxing.md ).  
  
Můžete použít [struktura](./language-reference/keywords/struct.md) – klíčové slovo k vytvoření vlastních typů vlastní hodnotu. Obvykle struktury slouží jako kontejner pro malou sadu související proměnné, jak je znázorněno v následujícím příkladu:  
  
[!code-csharp[Struct Keyword](../../samples/snippets/csharp/concepts/structs/struct-keyword.cs)]  
  
Další informace o typech hodnota v rozhraní .NET Framework najdete v tématu [obecný systém typů](../standard/common-type-system.md).  
    
Struktury sdílet většina stejnou syntaxi jako třídy, i když jsou omezenější než třídy struktury:  
  
-   V deklaraci struktura nelze inicializovat pole, pokud jsou deklarovány jako `const` nebo `static`.  
  
-   Struktury nelze deklarovat výchozí konstruktor (konstruktor bez parametrů) nebo finalizační metody.  
  
-   Struktury se zkopírují na přiřazení. Když struktury je přiřazen k nové proměnné, ale data se zkopírují a všechny změny nové kopie nezmění data pro původní kopii. To je důležité si pamatovat při práci s kolekcí typů hodnot, jako je například slovník < string, myStruct >.  
  
-   Struktury jsou hodnotové typy a třídy jsou odkazové typy.  
  
-   Na rozdíl od třídy, struktury se dá vytvořit instance bez použití `new` operátor.  
  
-   Struktury můžou deklarovat konstruktory, které mají parametry.  
  
-   Struktury nemůže Zdědit z jiné třídy nebo struktury a nesmí být základní třídy. Všechny struktury dědí přímo z <xref:System.ValueType>, který dědí z <xref:System.Object>.  
  
-   Struktury můžete implementovat rozhraní.

## <a name="literal-values"></a>Literálových hodnot  
V jazyce C# literálových hodnot z kompilátoru přijímat typu. Můžete určit, jak by měla být zadána číselný literál připojením písmeno na konec číslo. Například k určení, že hodnota 4.56 by měl být považovány za plovoucí desetinné čárky, připojit "f" nebo "F" po číslo: `4.56f`. Pokud je připojen žádný písmeno, kompilátor odvodí `double` typ pro literál. Další informace o tom, které lze určit typy přípony písmeno, najdete na stránkách odkaz pro jednotlivé typy v [typy hodnot](./language-reference/keywords/value-types.md).  
  
Protože jsou zadány literály, a všechny typy odvození nakonec z <xref:System.Object>, můžete napsat a kompilace kódu, například následující:  
  
[!code-csharp[Literal Values](../../samples/snippets/csharp/concepts/structs/literals.cs)]

Jazykové funkce byla zavedená v C# 7.0 na posledních dvou příkladech. První umožňuje používat jako podtržítkem *oddělujících číslice* uvnitř číselné literály. Můžete je umístit kdekoli mezi číslic ke zlepšení čitelnosti. Nemají žádný vliv na hodnotu.

Druhá ukazuje *binární literály*, které vám umožňují určit bit vzory přímo místo použití šestnáctkové soustavě.

## <a name="nullable-types"></a>Typy s možnou hodnotou Null  
Typy hodnot obyčejnou nemůže mít hodnotu [null](./language-reference/keywords/null.md). Ale můžete vytvořit typy s možnou hodnotou Null hodnot připojení **?** Po typ. Například **int?** je **int** typ, který může mít hodnotu [null](./language-reference/keywords/null.md). V CTS, s možnou hodnotou Null typy jsou instance typu Obecná struktura <xref:System.Nullable%601>. Typy s možnou hodnotou Null jsou zvláště užitečné, když jsou předávání dat do a z databáze, ve kterých může být číselné hodnoty null. Další informace najdete v tématu [typy s možnou hodnotou Null (C# programování průvodce)](./programming-guide/nullable-types/index.md).

## <a name="see-also"></a>Viz také
[Třídy](classes.md)

[Základní typy](basic-types.md)
