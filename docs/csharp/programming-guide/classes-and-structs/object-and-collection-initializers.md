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
# <a name="object-and-collection-initializers-c-programming-guide"></a><span data-ttu-id="fb548-102">Inicializátory objektu a kolekce (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="fb548-102">Object and Collection Initializers (C# Programming Guide)</span></span>

<span data-ttu-id="fb548-103">C# umožňuje vytvořit konkretizovat objekt nebo kolekci a provádět přiřazení členů v jednom příkazu.</span><span class="sxs-lookup"><span data-stu-id="fb548-103">C# lets you instantiate an object or collection and perform member assignments in a single statement.</span></span>

## <a name="object-initializers"></a><span data-ttu-id="fb548-104">Inicializátory objektů</span><span class="sxs-lookup"><span data-stu-id="fb548-104">Object initializers</span></span>

<span data-ttu-id="fb548-105">Inicializátory objektů umožňují přiřadit hodnoty k jakýmkoli přístupným polím nebo vlastnostem objektu při vytváření, bez nutnosti vyvolání konstruktoru následovaného řádky příkazů přiřazení.</span><span class="sxs-lookup"><span data-stu-id="fb548-105">Object initializers let you assign values to any accessible fields or properties of an object at creation time without having to invoke a constructor followed by lines of assignment statements.</span></span> <span data-ttu-id="fb548-106">Syntaxe inicializátoru objektu umožňuje zadat argumenty pro konstruktor, nebo tyto argumenty (a syntaxi se závorkami) vynechat.</span><span class="sxs-lookup"><span data-stu-id="fb548-106">The object initializer syntax enables you to specify arguments for a constructor or omit the arguments (and parentheses syntax).</span></span>  <span data-ttu-id="fb548-107">Následující příklad ukazuje, jak používat inicializátor `Cat` objektu s pojmenovaným typem a jak vyvolat konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="fb548-107">The following example shows how to use an object initializer with a named type, `Cat` and how to invoke the parameterless constructor.</span></span> <span data-ttu-id="fb548-108">Všimněte si použití automaticky implementovaných vlastností ve `Cat` třídě.</span><span class="sxs-lookup"><span data-stu-id="fb548-108">Note the use of auto-implemented properties in the `Cat` class.</span></span> <span data-ttu-id="fb548-109">Další informace naleznete [v tématu Auto-Implemented Properties](auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="fb548-109">For more information, see [Auto-Implemented Properties](auto-implemented-properties.md).</span></span>  
  
[!code-csharp[ObjectInitializer1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#CatDeclaration)]  
[!code-csharp[ObjectInitializer1a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ObjectPropertyInitialization)]  

<span data-ttu-id="fb548-110">Syntaxe inicializačních objektů umožňuje vytvořit instanci a poté přiřadí nově vytvořený objekt s přiřazenými vlastnostmi proměnné v přiřazení.</span><span class="sxs-lookup"><span data-stu-id="fb548-110">The object initializers syntax allows you to create an instance, and after that it assigns the newly created object, with its assigned properties, to the variable in the assignment.</span></span>

<span data-ttu-id="fb548-111">Počínaje C# 6, inicializační objekty mohou nastavit indexery kromě přiřazení polí a vlastností.</span><span class="sxs-lookup"><span data-stu-id="fb548-111">Starting with C# 6, object initializers can set indexers, in addition to assigning fields and properties.</span></span> <span data-ttu-id="fb548-112">Zvažte `Matrix` tuto základní třídu:</span><span class="sxs-lookup"><span data-stu-id="fb548-112">Consider this basic `Matrix` class:</span></span>

[!code-csharp[ObjectInitializer2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixDeclaration)]  

<span data-ttu-id="fb548-113">Můžete inicializovat matici identity s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="fb548-113">You could initialize the identity matrix with the following code:</span></span>

[!code-csharp[ObjectInitializer2a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixInitialization)]  

<span data-ttu-id="fb548-114">Všechny přístupné indexer, který obsahuje přístupné setter lze použít jako jeden z výrazů v inicializátoru objektu, bez ohledu na počet nebo typy argumentů.</span><span class="sxs-lookup"><span data-stu-id="fb548-114">Any accessible indexer that contains an accessible setter can be used as one of the expressions in an object initializer, regardless of the number or types of arguments.</span></span> <span data-ttu-id="fb548-115">Argumenty indexu tvoří levou stranu přiřazení a hodnota je pravá strana výrazu.</span><span class="sxs-lookup"><span data-stu-id="fb548-115">The index arguments form the left side of the assignment, and the value is the right side of the expression.</span></span>  <span data-ttu-id="fb548-116">Například jsou všechny platné, pokud `IndexersExample` má příslušné indexery:</span><span class="sxs-lookup"><span data-stu-id="fb548-116">For example, these are all valid if `IndexersExample` has the appropriate indexers:</span></span>

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

<span data-ttu-id="fb548-117">Pro předchozí kód zkompilovat `IndexersExample` typ musí mít následující členy:</span><span class="sxs-lookup"><span data-stu-id="fb548-117">For the preceding code to compile, the `IndexersExample` type must have the following members:</span></span>

```csharp
public string name;
public double Size { set { ... }; }
public char this[int i] { set { ... }; }
public string this[char c, int i] {  set { ... }; }
```

## <a name="object-initializers-with-anonymous-types"></a><span data-ttu-id="fb548-118">Inicializátory objektů s anonymními typy</span><span class="sxs-lookup"><span data-stu-id="fb548-118">Object Initializers with anonymous types</span></span>

<span data-ttu-id="fb548-119">Přestože inicializátory objektů lze použít v libovolném kontextu, jsou užitečné zejména ve výrazech dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="fb548-119">Although object initializers can be used in any context, they are especially useful in LINQ query expressions.</span></span> <span data-ttu-id="fb548-120">Výrazy dotazu často používají [anonymní typy](./anonymous-types.md), které lze inicializovat pouze pomocí inicializačního objektu, jak je znázorněno v následující deklaraci.</span><span class="sxs-lookup"><span data-stu-id="fb548-120">Query expressions make frequent use of [anonymous types](./anonymous-types.md), which can only be initialized by using an object initializer, as shown in the following declaration.</span></span>  

```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```

<span data-ttu-id="fb548-121">Anonymní typy `select` umožňují klauzuli ve výrazu dotazu LINQ transformovat objekty původní sekvence do objektů, jejichž hodnota a tvar se mohou lišit od originálu.</span><span class="sxs-lookup"><span data-stu-id="fb548-121">Anonymous types enable the `select` clause in a LINQ query expression to transform objects of the original sequence into objects whose value and shape may differ from the original.</span></span> <span data-ttu-id="fb548-122">Tato možnost je užitečná, pokud chcete uložit pouze část informace z jednotlivých objektů v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="fb548-122">This is useful if you want to store only a part of the information from each object in a sequence.</span></span> <span data-ttu-id="fb548-123">V následujícím příkladu předpokládejme,`p`že produkt produktu ( ) obsahuje mnoho polí a metod a že vás zajímá pouze vytvoření posloupnosti objektů, které obsahují název produktu a jednotkovou cenu.</span><span class="sxs-lookup"><span data-stu-id="fb548-123">In the following example, assume that a product object (`p`) contains many fields and methods, and that you are only interested in creating a sequence of objects that contain the product name and the unit price.</span></span>  
  
[!code-csharp[ObjectInitializer3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#AnonymousUse)]  

<span data-ttu-id="fb548-124">Při spuštění tohoto dotazu `productInfos` bude proměnná obsahovat posloupnost objektů, ke kterým lze získat přístup v příkazu, `foreach` jak je znázorněno v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="fb548-124">When this query is executed, the `productInfos` variable will contain a sequence of objects that can be accessed in a `foreach` statement as shown in this example:</span></span>  

```csharp
foreach(var p in productInfos){...}  
```

<span data-ttu-id="fb548-125">Každý objekt v novém anonymním typu má dvě veřejné vlastnosti, které obdrží stejné názvy jako vlastnosti nebo pole v původním objektu.</span><span class="sxs-lookup"><span data-stu-id="fb548-125">Each object in the new anonymous type has two public properties that receive the same names as the properties or fields in the original object.</span></span> <span data-ttu-id="fb548-126">Pole můžete také přejmenovat při vytváření anonymního typu. následující příklad přejmenuje `UnitPrice` pole `Price`na .</span><span class="sxs-lookup"><span data-stu-id="fb548-126">You can also rename a field when you are creating an anonymous type; the following example renames the `UnitPrice` field to `Price`.</span></span>  

```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```

## <a name="collection-initializers"></a><span data-ttu-id="fb548-127">Inicializátory kolekce</span><span class="sxs-lookup"><span data-stu-id="fb548-127">Collection initializers</span></span>

<span data-ttu-id="fb548-128">Inicializátory kolekce umožňují zadat jeden nebo více inicializátorů <xref:System.Collections.IEnumerable> elementu při inicializaci typu kolekce, který implementuje a má `Add` s příslušným podpisem jako metodu instance nebo metodu rozšíření.</span><span class="sxs-lookup"><span data-stu-id="fb548-128">Collection initializers let you specify one or more element initializers when you initialize a collection type that implements <xref:System.Collections.IEnumerable> and has `Add` with the appropriate signature as an instance method or an extension method.</span></span> <span data-ttu-id="fb548-129">Inicializátory prvku může být jednoduchá hodnota, výraz nebo inicializátor objektu.</span><span class="sxs-lookup"><span data-stu-id="fb548-129">The element initializers can be a simple value, an expression, or an object initializer.</span></span> <span data-ttu-id="fb548-130">Pomocí inicializátoru kolekce není nutné zadat více volání; kompilátor přidá volání automaticky.</span><span class="sxs-lookup"><span data-stu-id="fb548-130">By using a collection initializer, you do not have to specify multiple calls; the compiler adds the calls automatically.</span></span>  
  
<span data-ttu-id="fb548-131">Následující příklad ukazuje dvě jednoduché kolekce inicializátory:</span><span class="sxs-lookup"><span data-stu-id="fb548-131">The following example shows two simple collection initializers:</span></span>  

```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```

<span data-ttu-id="fb548-132">Následující inicializátor kolekce používá inicializační `Cat` objekty k inicializaci objektů třídy definované v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="fb548-132">The following collection initializer uses object initializers to initialize objects of the `Cat` class defined in a previous example.</span></span> <span data-ttu-id="fb548-133">Pamatujte, že jednotlivé incializátory objektů jsou uzavřeny ve složených závorkách a odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="fb548-133">Note that the individual object initializers are enclosed in braces and separated by commas.</span></span>  
  
[!code-csharp[ListInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitializer)]  
  
<span data-ttu-id="fb548-134">Můžete zadat [null](../../language-reference/keywords/null.md) jako prvek v inicializátoru kolekce, pokud to `Add` metoda kolekce umožňuje.</span><span class="sxs-lookup"><span data-stu-id="fb548-134">You can specify [null](../../language-reference/keywords/null.md) as an element in a collection initializer if the collection's `Add` method allows it.</span></span>  
  
[!code-csharp[ListInitializerNull](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitialerWithNull)]  
  
 <span data-ttu-id="fb548-135">Indexované prvky můžete zadat, pokud kolekce podporuje indexování čtení a zápisu.</span><span class="sxs-lookup"><span data-stu-id="fb548-135">You can specify indexed elements if the collection supports read / write indexing.</span></span>
  
[!code-csharp[DictionaryInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryIndexerInitializer)]  

<span data-ttu-id="fb548-136">Předchozí ukázka generuje kód, <xref:System.Collections.Generic.Dictionary%602.Item(%600)> který volá nastavit hodnoty.</span><span class="sxs-lookup"><span data-stu-id="fb548-136">The preceding sample generates code that calls the <xref:System.Collections.Generic.Dictionary%602.Item(%600)> to set the values.</span></span> <span data-ttu-id="fb548-137">Před C# 6 můžete inicializovat slovníky a jiné asociativní kontejnery pomocí následující syntaxe.</span><span class="sxs-lookup"><span data-stu-id="fb548-137">Before C# 6, you could initialize dictionaries and other associative containers using the following syntax.</span></span> <span data-ttu-id="fb548-138">Všimněte si, že místo syntaxe indexeru s závorky a přiřazením používá objekt s více hodnotami:</span><span class="sxs-lookup"><span data-stu-id="fb548-138">Notice that instead of indexer syntax, with parentheses and an assignment, it uses an object with multiple values:</span></span>

[!code-csharp[DictionaryAddInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryAddInitializer)]  

<span data-ttu-id="fb548-139">Tento inicializační příklad volá <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)> přidat tři položky do slovníku.</span><span class="sxs-lookup"><span data-stu-id="fb548-139">This initializer example calls <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)> to add the three items into the dictionary.</span></span> <span data-ttu-id="fb548-140">Tyto dva různé způsoby inicializovat asociativní kolekce mají mírně odlišné chování z důvodu volání metody kompilátor generuje.</span><span class="sxs-lookup"><span data-stu-id="fb548-140">These two different ways to initialize associative collections have slightly different behavior because of the method calls the compiler generates.</span></span> <span data-ttu-id="fb548-141">Obě varianty pracují `Dictionary` s třídou.</span><span class="sxs-lookup"><span data-stu-id="fb548-141">Both variants work with the `Dictionary` class.</span></span> <span data-ttu-id="fb548-142">Jiné typy mohou podporovat pouze jeden nebo druhý na základě jejich veřejné rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="fb548-142">Other types may only support one or the other based on their public API.</span></span>

## <a name="examples"></a><span data-ttu-id="fb548-143">Příklady</span><span class="sxs-lookup"><span data-stu-id="fb548-143">Examples</span></span>

<span data-ttu-id="fb548-144">Následující příklad kombinuje koncepty inicializátory objektu a kolekce.</span><span class="sxs-lookup"><span data-stu-id="fb548-144">The following example combines the concepts of object and collection initializers.</span></span>

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullExample)]  

<span data-ttu-id="fb548-145">Následující příklad ukazuje objekt, <xref:System.Collections.IEnumerable> který implementuje a obsahuje metodu `Add` s více parametry, Používá inicializátor kolekce `Add` s více prvky na položku v seznamu, které odpovídají podpisu metody.</span><span class="sxs-lookup"><span data-stu-id="fb548-145">The following example shows an object that implements <xref:System.Collections.IEnumerable> and contains an `Add` method with multiple parameters, It uses a collection initializer with multiple elements per item in the list that correspond to the signature of the `Add` method.</span></span>

[!code-csharp[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullListExample)]  

<span data-ttu-id="fb548-146">`Add`metody mohou `params` použít klíčové slovo, aby se proměnný počet argumentů, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="fb548-146">`Add` methods can use the `params` keyword to take a variable number of arguments, as shown in the following example.</span></span> <span data-ttu-id="fb548-147">Tento příklad také ukazuje vlastní implementaci indexeru inicializovat kolekce pomocí indexů.</span><span class="sxs-lookup"><span data-stu-id="fb548-147">This example also demonstrates the custom implementation of an indexer to initialize a collection using indexes.</span></span>

[!code-csharp[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullDictionaryInitializer)]  

## <a name="see-also"></a><span data-ttu-id="fb548-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb548-148">See also</span></span>

- [<span data-ttu-id="fb548-149">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="fb548-149">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="fb548-150">LINQ v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="fb548-150">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="fb548-151">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="fb548-151">Anonymous Types</span></span>](anonymous-types.md)
