---
title: Inicializátory objektů a kolekcí – programovací příručka jazyka C#
ms.date: 12/19/2018
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
ms.openlocfilehash: ae8741e2f29db0a470ad8d3b121375fbdeaff0d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170192"
---
# <a name="object-and-collection-initializers-c-programming-guide"></a>Inicializátory objektu a kolekce (Průvodce programováním v C#)

C# umožňuje vytvořit konkretizovat objekt nebo kolekci a provádět přiřazení členů v jednom příkazu.

## <a name="object-initializers"></a>Inicializátory objektů

Inicializátory objektů umožňují přiřadit hodnoty k jakýmkoli přístupným polím nebo vlastnostem objektu při vytváření, bez nutnosti vyvolání konstruktoru následovaného řádky příkazů přiřazení. Syntaxe inicializátoru objektu umožňuje zadat argumenty pro konstruktor, nebo tyto argumenty (a syntaxi se závorkami) vynechat.  Následující příklad ukazuje, jak používat inicializátor `Cat` objektu s pojmenovaným typem a jak vyvolat konstruktor bez parametrů. Všimněte si použití automaticky implementovaných vlastností ve `Cat` třídě. Další informace naleznete [v tématu Auto-Implemented Properties](auto-implemented-properties.md).  
  
[!code-csharp[ObjectInitializer1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#CatDeclaration)]  
[!code-csharp[ObjectInitializer1a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ObjectPropertyInitialization)]  

Syntaxe inicializačních objektů umožňuje vytvořit instanci a poté přiřadí nově vytvořený objekt s přiřazenými vlastnostmi proměnné v přiřazení.

Počínaje C# 6, inicializační objekty mohou nastavit indexery kromě přiřazení polí a vlastností. Zvažte `Matrix` tuto základní třídu:

[!code-csharp[ObjectInitializer2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixDeclaration)]  

Můžete inicializovat matici identity s následujícím kódem:

[!code-csharp[ObjectInitializer2a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixInitialization)]  

Všechny přístupné indexer, který obsahuje přístupné setter lze použít jako jeden z výrazů v inicializátoru objektu, bez ohledu na počet nebo typy argumentů. Argumenty indexu tvoří levou stranu přiřazení a hodnota je pravá strana výrazu.  Například jsou všechny platné, pokud `IndexersExample` má příslušné indexery:

```csharp
var thing = new IndexersExample {
    name = "object one",
    [1] = '1',
    [2] = '4',
    [3] = '9',
    Size = Math.PI,
    ['C',4] = "Middle C"
}
```

Pro předchozí kód zkompilovat `IndexersExample` typ musí mít následující členy:

```csharp
public string name;
public double Size { set { ... }; }
public char this[int i] { set { ... }; }
public string this[char c, int i] {  set { ... }; }
```

## <a name="object-initializers-with-anonymous-types"></a>Inicializátory objektů s anonymními typy

Přestože inicializátory objektů lze použít v libovolném kontextu, jsou užitečné zejména ve výrazech dotazu LINQ. Výrazy dotazu často používají [anonymní typy](./anonymous-types.md), které lze inicializovat pouze pomocí inicializačního objektu, jak je znázorněno v následující deklaraci.  

```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```

Anonymní typy `select` umožňují klauzuli ve výrazu dotazu LINQ transformovat objekty původní sekvence do objektů, jejichž hodnota a tvar se mohou lišit od originálu. Tato možnost je užitečná, pokud chcete uložit pouze část informace z jednotlivých objektů v sekvenci. V následujícím příkladu předpokládejme,`p`že produkt produktu ( ) obsahuje mnoho polí a metod a že vás zajímá pouze vytvoření posloupnosti objektů, které obsahují název produktu a jednotkovou cenu.  
  
[!code-csharp[ObjectInitializer3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#AnonymousUse)]  

Při spuštění tohoto dotazu `productInfos` bude proměnná obsahovat posloupnost objektů, ke kterým lze získat přístup v příkazu, `foreach` jak je znázorněno v tomto příkladu:  

```csharp
foreach(var p in productInfos){...}  
```

Každý objekt v novém anonymním typu má dvě veřejné vlastnosti, které obdrží stejné názvy jako vlastnosti nebo pole v původním objektu. Pole můžete také přejmenovat při vytváření anonymního typu. následující příklad přejmenuje `UnitPrice` pole `Price`na .  

```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```

## <a name="collection-initializers"></a>Inicializátory kolekce

Inicializátory kolekce umožňují zadat jeden nebo více inicializátorů <xref:System.Collections.IEnumerable> elementu při inicializaci typu kolekce, který implementuje a má `Add` s příslušným podpisem jako metodu instance nebo metodu rozšíření. Inicializátory prvku může být jednoduchá hodnota, výraz nebo inicializátor objektu. Pomocí inicializátoru kolekce není nutné zadat více volání; kompilátor přidá volání automaticky.  
  
Následující příklad ukazuje dvě jednoduché kolekce inicializátory:  

```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```

Následující inicializátor kolekce používá inicializační `Cat` objekty k inicializaci objektů třídy definované v předchozím příkladu. Pamatujte, že jednotlivé incializátory objektů jsou uzavřeny ve složených závorkách a odděleny čárkami.  
  
[!code-csharp[ListInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitializer)]  
  
Můžete zadat [null](../../language-reference/keywords/null.md) jako prvek v inicializátoru kolekce, pokud to `Add` metoda kolekce umožňuje.  
  
[!code-csharp[ListInitializerNull](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitialerWithNull)]  
  
 Indexované prvky můžete zadat, pokud kolekce podporuje indexování čtení a zápisu.
  
[!code-csharp[DictionaryInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryIndexerInitializer)]  

Předchozí ukázka generuje kód, <xref:System.Collections.Generic.Dictionary%602.Item(%600)> který volá nastavit hodnoty. Před C# 6 můžete inicializovat slovníky a jiné asociativní kontejnery pomocí následující syntaxe. Všimněte si, že místo syntaxe indexeru s závorky a přiřazením používá objekt s více hodnotami:

[!code-csharp[DictionaryAddInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryAddInitializer)]  

Tento inicializační příklad volá <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)> přidat tři položky do slovníku. Tyto dva různé způsoby inicializovat asociativní kolekce mají mírně odlišné chování z důvodu volání metody kompilátor generuje. Obě varianty pracují `Dictionary` s třídou. Jiné typy mohou podporovat pouze jeden nebo druhý na základě jejich veřejné rozhraní API.

## <a name="examples"></a>Příklady

Následující příklad kombinuje koncepty inicializátory objektu a kolekce.

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullExample)]  

Následující příklad ukazuje objekt, <xref:System.Collections.IEnumerable> který implementuje a obsahuje metodu `Add` s více parametry, Používá inicializátor kolekce `Add` s více prvky na položku v seznamu, které odpovídají podpisu metody.

[!code-csharp[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullListExample)]  

`Add`metody mohou `params` použít klíčové slovo, aby se proměnný počet argumentů, jak je znázorněno v následujícím příkladu. Tento příklad také ukazuje vlastní implementaci indexeru inicializovat kolekce pomocí indexů.

[!code-csharp[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullDictionaryInitializer)]  

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [LINQ v jazyce C#](../../linq/index.md)
- [Anonymní typy](anonymous-types.md)
