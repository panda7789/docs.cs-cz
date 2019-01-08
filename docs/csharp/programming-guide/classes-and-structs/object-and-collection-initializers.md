---
title: Inicializátory objektu a kolekce - C# Průvodce programováním
ms.custom: seodec18
ms.date: 12/19/2018
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
ms.openlocfilehash: 1dc28ac218eb0325095641840834b40594ad67ab
ms.sourcegitcommit: d09c77414e9e4fc72c79b04deee7a756a120674e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2019
ms.locfileid: "54084859"
---
# <a name="object-and-collection-initializers-c-programming-guide"></a>Inicializátory objektu a kolekce (Průvodce programováním v C#)

C#Umožňuje vytvořit instanci objektu nebo kolekci a provést přiřazení členů v jediném příkazu.

## <a name="object-initializers"></a>Inicializátory objektů

Inicializátory objektů umožňují přiřadit hodnoty k jakýmkoli přístupným polím nebo vlastnostem objektu při vytváření, bez nutnosti vyvolání konstruktoru následovaného řádky příkazů přiřazení. Syntaxe inicializátoru objektu umožňuje zadat argumenty pro konstruktor, nebo tyto argumenty (a syntaxi se závorkami) vynechat.  Následující příklad ukazuje, jak použít inicializátor objektu s pojmenovaným typem `Cat` a vyvolání výchozího konstruktoru. Všimněte si použití automaticky implementované vlastnosti v `Cat` třídy. Další informace najdete v tématu [implemented Properties](auto-implemented-properties.md).  
  
[!code-csharp[ObjectInitializer1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#CatDeclaration)]  
[!code-csharp[ObjectInitializer1a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ObjectPropertyInitialization)]  
 
Syntaxi inicializátory objektů lze vytvářet instance, a poté přiřadí nově vytvořený objekt s vlastností přiřazené k proměnné v přiřazení.

Počínaje C# 6, objekt inicializátory můžete nastavit indexery, kromě přiřazení polí a vlastností. Zvažte proto základní `Matrix` třídy:

[!code-csharp[ObjectInitializer2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixDeclaration)]  

Může inicializovat jednotkovou matici s následujícím kódem:

[!code-csharp[ObjectInitializer2a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixInitialization)]  

Žádné přístupné indexer, který obsahuje přístupnou metodu setter může sloužit jako jeden z výrazů v inicializátoru objektu bez ohledu na čísla nebo typy argumentů. Argumenty index formu levé části přiřazení a hodnota představuje pravou stranu výrazu.  Například toto jsou všechny platné if `IndexersExample` má odpovídající indexování:

```csharp
var thing = new IndexersExample {
    name = "object one",
    [1] = '1',
    [2] = '4',
    [3] = '9',
    Baz = Math.PI,
    ['C',4] = "Middle C"
}
```

Pro předchozí kód mohl zkompilovat `IndexersExample` typ musí mít následující členy:

```csharp
public string name;
public double Size { set { ... }; }
public char this[int i] { set { ... }; }
public string this[char c, int i] {  set { ... }; }
}
```

## <a name="object-initializers-with-anonymous-types"></a>Inicializátory objektů s anonymními typy

Přestože inicializátory objektů lze použít v libovolném kontextu, jsou zvláště užitečná v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazech dotazů. Výrazy dotazů používají často [anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), které lze inicializovat pouze pomocí inicializátoru objektu, jak je znázorněno v následující deklaraci.  

```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```

Anonymní typy umožňují `select` klauzule [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazu transformovat objekty původní sekvence na objekty, jejichž hodnota a tvar se může lišit od původního dotazu. Tato možnost je užitečná, pokud chcete uložit pouze část informace z jednotlivých objektů v sekvenci. V následujícím příkladu se předpokládá, že objekt produktu (`p`) obsahuje mnoho polí a metod, a že si jenom chcete vytvořit pouze sekvenci objektů, které obsahují název produktu a jednotkovou cenu.  
  
[!code-csharp[ObjectInitializer3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#AnonymousUse)]  

Při spuštění tohoto dotazu `productInfos` proměnná bude obsahovat sekvenci objektů, které mohou být přístupné v `foreach` jak je uvedeno v tomto příkladu:  

```csharp
foreach(var p in productInfos){...}  
```

Každý objekt v novém anonymním typu mají dvě veřejné vlastnosti, které budou přiděleny stejné názvy jako vlastnosti nebo pole v původním objektu. Můžete také přejmenovat pole při vytváření anonymního typu; Následující příklad přejmenuje `UnitPrice` pole `Price`.  

```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```

## <a name="collection-initializers"></a>Inicializátory kolekce

Inicializátory kolekce umožňují určit jeden nebo více inicializátorů prvku při inicializaci kolekce typu tohoto implementuje <xref:System.Collections.IEnumerable> a má `Add` s odpovídajícím podpisem jako metodu instance nebo metody rozšíření. Inicializátory elementů polí může být jednoduchých hodnot, výrazem nebo inicializátorem objektu. Pomocí inicializátoru kolekce, není nutné zadávat větší počet volání; volání přidá kompilátor automaticky.  
  
Následující příklad ukazuje dva jednoduché inicializátory kolekce:  

```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```

Následující inicializátor kolekce používá inicializátory objektů k inicializaci objektů třídy `Cat` třídy definované v předchozím příkladu. Pamatujte, že jednotlivé incializátory objektů jsou uzavřeny ve složených závorkách a odděleny čárkami.  
  
[!code-csharp[ListInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitializer)]  
  
Můžete zadat [null](../../language-reference/keywords/null.md) jako prvek v incializátoru kolekce Pokud kolekce `Add` metoda umožňuje.  
  
[!code-csharp[ListInitializerNull](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitialerWithNull)]  
  
 Indexované prvky můžete zadat, pokud kolekce podporuje čtení / zápis indexování.
  
[!code-csharp[DictionaryInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryIndexerInitializer)]  

V předchozím příkladu generuje kód, který volá <xref:System.Collections.Generic.Dictionary%602.Item(%600)> nastavit hodnoty. Počínaje C# 6, můžete inicializovat slovníky a dalších asociativní kontejnery pomocí následující syntaxe. Všimněte si, že místo indexer syntaxe se závorkami a přiřazení, používá objekt s více hodnotami:

[!code-csharp[DictionaryAddInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryAddInitializer)]  

V tomto příkladu inicializátor volá <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)> přidáte tři položky do slovníku. Tyto dva různé způsoby inicializovat asociativní kolekcí mají mírně odlišné chování kvůli volání metody, které generuje kompilátor. Obě varianty pracovat `Dictionary` třídy. Jiné typy může podporovat pouze jednu nebo další závislosti na jejich veřejné rozhraní API.

## <a name="examples"></a>Příklady

Následující příklad kombinuje koncepty inicializátory objektu a kolekce.

[!code-csharp-interactive[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullExample)]  

Následující příklad ukazuje, objekt, který implementuje <xref:System.Collections.IEnumerable> a obsahuje `Add` metodu s více parametry používá inicializátor kolekce s více prvky každou položku v seznamu, které odpovídají podpis `Add`metody.

[!code-csharp-interactive[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullListExample)]  

`Add` můžete použít metody `params` – klíčové slovo se proměnný počet argumentů, jak je znázorněno v následujícím příkladu. Tento příklad také ukazuje vlastní implementaci indexeru k inicializaci kolekce pomocí indexů.

[!code-csharp-interactive[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullDictionaryInitializer)]  

## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../index.md)  
- [LINQ – výrazy dotazů](../linq-query-expressions/index.md)  
- [Anonymní typy](anonymous-types.md)
