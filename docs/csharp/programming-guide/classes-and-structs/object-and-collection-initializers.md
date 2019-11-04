---
title: Inicializátory objektů a kolekcí – C# Průvodce programováním
ms.custom: seodec18
ms.date: 12/19/2018
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
ms.openlocfilehash: 837be04208d438f15b4cc7c7124a47ef6c038cb2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73455437"
---
# <a name="object-and-collection-initializers-c-programming-guide"></a>Inicializátory objektu a kolekce (Průvodce programováním v C#)

C#umožňuje vytvořit instanci objektu nebo kolekce a provést přiřazení členů v rámci jednoho příkazu.

## <a name="object-initializers"></a>Inicializátory objektů

Inicializátory objektů umožňují přiřadit hodnoty k jakýmkoli přístupným polím nebo vlastnostem objektu při vytváření, bez nutnosti vyvolání konstruktoru následovaného řádky příkazů přiřazení. Syntaxe inicializátoru objektu umožňuje zadat argumenty pro konstruktor, nebo tyto argumenty (a syntaxi se závorkami) vynechat.  Následující příklad ukazuje, jak použít inicializátor objektu s pojmenovaným typem, `Cat` a jak vyvolat konstruktor bez parametrů. Všimněte si použití automaticky implementovaných vlastností ve třídě `Cat`. Další informace najdete v tématu věnovaném [automaticky implementovaným vlastnostem](auto-implemented-properties.md).  
  
[!code-csharp[ObjectInitializer1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#CatDeclaration)]  
[!code-csharp[ObjectInitializer1a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ObjectPropertyInitialization)]  
 
Syntaxe inicializátorů objektů umožňuje vytvořit instanci a poté, co přiřadí nově vytvořený objekt s přiřazenými vlastnostmi k proměnné v přiřazení.

Počínaje C# 6, Inicializátory objektů mohou nastavovat indexery kromě přiřazování polí a vlastností. Zvažte tuto základní třídu `Matrix`:

[!code-csharp[ObjectInitializer2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixDeclaration)]  

Můžete inicializovat matici identity pomocí následujícího kódu:

[!code-csharp[ObjectInitializer2a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixInitialization)]  

Jakýkoli přístupný indexer, který obsahuje přístupný Setter, lze použít jako jeden z výrazů v inicializátoru objektu, bez ohledu na počet nebo typy argumentů. Argumenty indexu tvoří levou stranu přiřazení a hodnota je pravá strana výrazu.  Jsou to například všechny platné, pokud `IndexersExample` má příslušné indexery:

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

Aby bylo možné kompilovat předchozí kód, `IndexersExample` typ musí mít následující členy:

```csharp
public string name;
public double Size { set { ... }; }
public char this[int i] { set { ... }; }
public string this[char c, int i] {  set { ... }; }
```

## <a name="object-initializers-with-anonymous-types"></a>Inicializátory objektů s anonymními typy

I když se Inicializátory objektů dají použít v jakémkoli kontextu, jsou zvláště užitečné v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazech dotazů. Výrazy dotazů často využívají [anonymní typy](./anonymous-types.md), které lze inicializovat pouze pomocí inicializátoru objektu, jak je znázorněno v následující deklaraci.  

```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```

Anonymní typy umožňují klauzuli `select` ve výrazu dotazu [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] k transformaci objektů původní sekvence na objekty, jejichž hodnota a tvar se mohou lišit od původní hodnoty. Tato možnost je užitečná, pokud chcete uložit pouze část informace z jednotlivých objektů v sekvenci. V následujícím příkladu Předpokládejme, že objekt produktu (`p`) obsahuje mnoho polí a metod a že máte zájem pouze vytvořit sekvenci objektů, které obsahují název produktu a jednotkovou cenu.  
  
[!code-csharp[ObjectInitializer3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#AnonymousUse)]  

Při spuštění tohoto dotazu bude proměnná `productInfos` obsahovat sekvenci objektů, které jsou k dispozici v příkazu `foreach`, jak je znázorněno v následujícím příkladu:  

```csharp
foreach(var p in productInfos){...}  
```

Každý objekt v novém anonymním typu má dvě veřejné vlastnosti, které obdrží stejné názvy jako vlastnosti nebo pole v původním objektu. Pole můžete také přejmenovat při vytváření anonymního typu. Následující příklad přejmenuje pole `UnitPrice` na `Price`.  

```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```

## <a name="collection-initializers"></a>Inicializátory kolekce

Inicializátory kolekce umožňují určit jeden nebo více inicializátorů elementů při inicializaci typu kolekce, který implementuje <xref:System.Collections.IEnumerable> a má `Add` s odpovídající signaturou jako metodu instance nebo metodu rozšíření. Inicializátory elementu můžou být jednoduchou hodnotou, výrazem nebo inicializátorem objektu. Pomocí inicializátoru kolekce není nutné zadávat více volání; kompilátor automaticky přidá volání.  
  
Následující příklad ukazuje dva jednoduché inicializátory kolekce:  

```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```

Následující inicializátor kolekce používá Inicializátory objektů k inicializaci objektů `Cat` třídy definované v předchozím příkladu. Pamatujte, že jednotlivé incializátory objektů jsou uzavřeny ve složených závorkách a odděleny čárkami.  
  
[!code-csharp[ListInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitializer)]  
  
[Hodnotu null](../../language-reference/keywords/null.md) můžete zadat jako prvek v inicializátoru kolekce, pokud to metoda `Add` kolekce povoluje.  
  
[!code-csharp[ListInitializerNull](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitialerWithNull)]  
  
 Můžete zadat indexované prvky, pokud kolekce podporuje indexování pro čtení a zápis.
  
[!code-csharp[DictionaryInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryIndexerInitializer)]  

Předchozí ukázka vygeneruje kód, který volá <xref:System.Collections.Generic.Dictionary%602.Item(%600)> pro nastavení hodnot. Do C# 6 můžete pomocí následující syntaxe inicializovat slovníky a další asociativní kontejnery. Všimněte si, že místo syntaxe indexeru, pomocí závorek a přiřazení, používá objekt s více hodnotami:

[!code-csharp[DictionaryAddInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryAddInitializer)]  

Tento příklad inicializátoru volá <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)> pro přidání tří položek do slovníku. Tyto dva různé způsoby inicializace asociativních kolekcí mají mírně odlišné chování, protože metoda volá kompilátor generuje. Obě varianty pracují s třídou `Dictionary`. Jiné typy mohou podporovat pouze jeden nebo druhý na základě jejich veřejného rozhraní API.

## <a name="examples"></a>Příklady

Následující příklad kombinuje koncepty objektů a inicializátorů kolekcí.

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullExample)]  

Následující příklad ukazuje objekt, který implementuje <xref:System.Collections.IEnumerable> a obsahuje metodu `Add` s více parametry, používá inicializátor kolekce s více prvky na položku v seznamu, který odpovídá podpisu metody `Add`.

[!code-csharp[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullListExample)]  

metody `Add` mohou pomocí klíčového slova `params` přebírat proměnlivý počet argumentů, jak je znázorněno v následujícím příkladu. Tento příklad také ukazuje vlastní implementaci indexeru pro inicializaci kolekce pomocí indexů.

[!code-csharp[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullDictionaryInitializer)]  

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [LINQ v jazyce C#](../../linq/index.md)
- [Anonymní typy](anonymous-types.md)
