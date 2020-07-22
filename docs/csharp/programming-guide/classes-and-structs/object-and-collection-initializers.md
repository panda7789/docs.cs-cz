---
title: Inicializátory objektů a kolekcí – Průvodce programováním v C#
description: Inicializátory objektů v jazyce C# přiřadí hodnoty k přístupným polím nebo vlastnostem objektu při vytvoření po vyvolání konstruktoru.
ms.date: 12/19/2018
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
ms.openlocfilehash: 81deed8a21bff10364524c3e0784c562d4e727e6
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864771"
---
# <a name="object-and-collection-initializers-c-programming-guide"></a><span data-ttu-id="c7ded-103">Inicializátory objektu a kolekce (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="c7ded-103">Object and Collection Initializers (C# Programming Guide)</span></span>

<span data-ttu-id="c7ded-104">Jazyk C# umožňuje vytvořit instanci objektu nebo kolekce a provést přiřazení členů v rámci jednoho příkazu.</span><span class="sxs-lookup"><span data-stu-id="c7ded-104">C# lets you instantiate an object or collection and perform member assignments in a single statement.</span></span>

## <a name="object-initializers"></a><span data-ttu-id="c7ded-105">Inicializátory objektů</span><span class="sxs-lookup"><span data-stu-id="c7ded-105">Object initializers</span></span>

<span data-ttu-id="c7ded-106">Inicializátory objektů umožňují přiřadit hodnoty k jakýmkoli přístupným polím nebo vlastnostem objektu při vytváření, bez nutnosti vyvolání konstruktoru následovaného řádky příkazů přiřazení.</span><span class="sxs-lookup"><span data-stu-id="c7ded-106">Object initializers let you assign values to any accessible fields or properties of an object at creation time without having to invoke a constructor followed by lines of assignment statements.</span></span> <span data-ttu-id="c7ded-107">Syntaxe inicializátoru objektu umožňuje zadat argumenty pro konstruktor, nebo tyto argumenty (a syntaxi se závorkami) vynechat.</span><span class="sxs-lookup"><span data-stu-id="c7ded-107">The object initializer syntax enables you to specify arguments for a constructor or omit the arguments (and parentheses syntax).</span></span>  <span data-ttu-id="c7ded-108">Následující příklad ukazuje, jak použít inicializátor objektu s pojmenovaným typem `Cat` a jak vyvolat konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="c7ded-108">The following example shows how to use an object initializer with a named type, `Cat` and how to invoke the parameterless constructor.</span></span> <span data-ttu-id="c7ded-109">Všimněte si použití automaticky implementovaných vlastností ve `Cat` třídě.</span><span class="sxs-lookup"><span data-stu-id="c7ded-109">Note the use of auto-implemented properties in the `Cat` class.</span></span> <span data-ttu-id="c7ded-110">Další informace najdete v tématu věnovaném [automaticky implementovaným vlastnostem](auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="c7ded-110">For more information, see [Auto-Implemented Properties](auto-implemented-properties.md).</span></span>  
  
[!code-csharp[ObjectInitializer1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#CatDeclaration)]  
[!code-csharp[ObjectInitializer1a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ObjectPropertyInitialization)]  

<span data-ttu-id="c7ded-111">Syntaxe inicializátorů objektů umožňuje vytvořit instanci a poté, co přiřadí nově vytvořený objekt s přiřazenými vlastnostmi k proměnné v přiřazení.</span><span class="sxs-lookup"><span data-stu-id="c7ded-111">The object initializers syntax allows you to create an instance, and after that it assigns the newly created object, with its assigned properties, to the variable in the assignment.</span></span>

<span data-ttu-id="c7ded-112">Počínaje jazykem C# 6 můžou Inicializátory objektů nastavovat indexery kromě přiřazování polí a vlastností.</span><span class="sxs-lookup"><span data-stu-id="c7ded-112">Starting with C# 6, object initializers can set indexers, in addition to assigning fields and properties.</span></span> <span data-ttu-id="c7ded-113">Zvažte tuto základní `Matrix` třídu:</span><span class="sxs-lookup"><span data-stu-id="c7ded-113">Consider this basic `Matrix` class:</span></span>

[!code-csharp[ObjectInitializer2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixDeclaration)]  

<span data-ttu-id="c7ded-114">Můžete inicializovat matici identity pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="c7ded-114">You could initialize the identity matrix with the following code:</span></span>

[!code-csharp[ObjectInitializer2a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixInitialization)]  

<span data-ttu-id="c7ded-115">Jakýkoli přístupný indexer, který obsahuje přístupný Setter, lze použít jako jeden z výrazů v inicializátoru objektu, bez ohledu na počet nebo typy argumentů.</span><span class="sxs-lookup"><span data-stu-id="c7ded-115">Any accessible indexer that contains an accessible setter can be used as one of the expressions in an object initializer, regardless of the number or types of arguments.</span></span> <span data-ttu-id="c7ded-116">Argumenty indexu tvoří levou stranu přiřazení a hodnota je pravá strana výrazu.</span><span class="sxs-lookup"><span data-stu-id="c7ded-116">The index arguments form the left side of the assignment, and the value is the right side of the expression.</span></span>  <span data-ttu-id="c7ded-117">Jsou to například všechny platné, pokud `IndexersExample` mají příslušné indexery:</span><span class="sxs-lookup"><span data-stu-id="c7ded-117">For example, these are all valid if `IndexersExample` has the appropriate indexers:</span></span>

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

<span data-ttu-id="c7ded-118">Aby byl předchozí kód zkompilován, `IndexersExample` musí mít tento typ následující členy:</span><span class="sxs-lookup"><span data-stu-id="c7ded-118">For the preceding code to compile, the `IndexersExample` type must have the following members:</span></span>

```csharp
public string name;
public double Size { set { ... }; }
public char this[int i] { set { ... }; }
public string this[char c, int i] {  set { ... }; }
```

## <a name="object-initializers-with-anonymous-types"></a><span data-ttu-id="c7ded-119">Inicializátory objektů s anonymními typy</span><span class="sxs-lookup"><span data-stu-id="c7ded-119">Object Initializers with anonymous types</span></span>

<span data-ttu-id="c7ded-120">I když Inicializátory objektů lze použít v jakémkoli kontextu, jsou zvláště užitečné ve výrazech dotazů LINQ.</span><span class="sxs-lookup"><span data-stu-id="c7ded-120">Although object initializers can be used in any context, they are especially useful in LINQ query expressions.</span></span> <span data-ttu-id="c7ded-121">Výrazy dotazů často využívají [anonymní typy](./anonymous-types.md), které lze inicializovat pouze pomocí inicializátoru objektu, jak je znázorněno v následující deklaraci.</span><span class="sxs-lookup"><span data-stu-id="c7ded-121">Query expressions make frequent use of [anonymous types](./anonymous-types.md), which can only be initialized by using an object initializer, as shown in the following declaration.</span></span>  

```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```

<span data-ttu-id="c7ded-122">Anonymní typy umožňují `select` klauzuli ve výrazu dotazu LINQ pro transformaci objektů původní sekvence na objekty, jejichž hodnota a tvar se mohou lišit od původní.</span><span class="sxs-lookup"><span data-stu-id="c7ded-122">Anonymous types enable the `select` clause in a LINQ query expression to transform objects of the original sequence into objects whose value and shape may differ from the original.</span></span> <span data-ttu-id="c7ded-123">Tato možnost je užitečná, pokud chcete uložit pouze část informace z jednotlivých objektů v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="c7ded-123">This is useful if you want to store only a part of the information from each object in a sequence.</span></span> <span data-ttu-id="c7ded-124">V následujícím příkladu Předpokládejme, že objekt produktu ( `p` ) obsahuje mnoho polí a metod a že máte zájem pouze vytvořit sekvenci objektů, které obsahují název produktu a jednotkovou cenu.</span><span class="sxs-lookup"><span data-stu-id="c7ded-124">In the following example, assume that a product object (`p`) contains many fields and methods, and that you are only interested in creating a sequence of objects that contain the product name and the unit price.</span></span>  
  
[!code-csharp[ObjectInitializer3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#AnonymousUse)]  

<span data-ttu-id="c7ded-125">Při spuštění tohoto dotazu `productInfos` proměnná bude obsahovat sekvenci objektů, které jsou k dispozici v `foreach` příkazu, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c7ded-125">When this query is executed, the `productInfos` variable will contain a sequence of objects that can be accessed in a `foreach` statement as shown in this example:</span></span>  

```csharp
foreach(var p in productInfos){...}  
```

<span data-ttu-id="c7ded-126">Každý objekt v novém anonymním typu má dvě veřejné vlastnosti, které obdrží stejné názvy jako vlastnosti nebo pole v původním objektu.</span><span class="sxs-lookup"><span data-stu-id="c7ded-126">Each object in the new anonymous type has two public properties that receive the same names as the properties or fields in the original object.</span></span> <span data-ttu-id="c7ded-127">Pole můžete také přejmenovat při vytváření anonymního typu. Následující příklad přejmenuje `UnitPrice` pole na `Price` .</span><span class="sxs-lookup"><span data-stu-id="c7ded-127">You can also rename a field when you are creating an anonymous type; the following example renames the `UnitPrice` field to `Price`.</span></span>  

```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```

## <a name="collection-initializers"></a><span data-ttu-id="c7ded-128">Inicializátory kolekce</span><span class="sxs-lookup"><span data-stu-id="c7ded-128">Collection initializers</span></span>

<span data-ttu-id="c7ded-129">Inicializátory kolekce umožňují určit jeden nebo více inicializátorů elementů při inicializaci typu kolekce, který implementuje <xref:System.Collections.IEnumerable> a má `Add` odpovídající signaturu jako metodu instance nebo metodu rozšíření.</span><span class="sxs-lookup"><span data-stu-id="c7ded-129">Collection initializers let you specify one or more element initializers when you initialize a collection type that implements <xref:System.Collections.IEnumerable> and has `Add` with the appropriate signature as an instance method or an extension method.</span></span> <span data-ttu-id="c7ded-130">Inicializátory elementu můžou být jednoduchou hodnotou, výrazem nebo inicializátorem objektu.</span><span class="sxs-lookup"><span data-stu-id="c7ded-130">The element initializers can be a simple value, an expression, or an object initializer.</span></span> <span data-ttu-id="c7ded-131">Pomocí inicializátoru kolekce není nutné zadávat více volání; kompilátor automaticky přidá volání.</span><span class="sxs-lookup"><span data-stu-id="c7ded-131">By using a collection initializer, you do not have to specify multiple calls; the compiler adds the calls automatically.</span></span>  
  
<span data-ttu-id="c7ded-132">Následující příklad ukazuje dva jednoduché inicializátory kolekce:</span><span class="sxs-lookup"><span data-stu-id="c7ded-132">The following example shows two simple collection initializers:</span></span>  

```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```

<span data-ttu-id="c7ded-133">Následující inicializátor kolekce používá Inicializátory objektů k inicializaci objektů `Cat` třídy definované v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c7ded-133">The following collection initializer uses object initializers to initialize objects of the `Cat` class defined in a previous example.</span></span> <span data-ttu-id="c7ded-134">Pamatujte, že jednotlivé incializátory objektů jsou uzavřeny ve složených závorkách a odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="c7ded-134">Note that the individual object initializers are enclosed in braces and separated by commas.</span></span>  
  
[!code-csharp[ListInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitializer)]  
  
<span data-ttu-id="c7ded-135">[Hodnotu null](../../language-reference/keywords/null.md) můžete zadat jako prvek v inicializátoru kolekce, pokud `Add` to metoda kolekce povoluje.</span><span class="sxs-lookup"><span data-stu-id="c7ded-135">You can specify [null](../../language-reference/keywords/null.md) as an element in a collection initializer if the collection's `Add` method allows it.</span></span>  
  
[!code-csharp[ListInitializerNull](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitialerWithNull)]  
  
 <span data-ttu-id="c7ded-136">Můžete zadat indexované prvky, pokud kolekce podporuje indexování pro čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="c7ded-136">You can specify indexed elements if the collection supports read / write indexing.</span></span>
  
[!code-csharp[DictionaryInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryIndexerInitializer)]  

<span data-ttu-id="c7ded-137">Předchozí ukázka vygeneruje kód, který volá, <xref:System.Collections.Generic.Dictionary%602.Item(%600)> aby se nastavily hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c7ded-137">The preceding sample generates code that calls the <xref:System.Collections.Generic.Dictionary%602.Item(%600)> to set the values.</span></span> <span data-ttu-id="c7ded-138">Před C# 6 můžete inicializovat slovníky a další asociativní kontejnery pomocí následující syntaxe.</span><span class="sxs-lookup"><span data-stu-id="c7ded-138">Before C# 6, you could initialize dictionaries and other associative containers using the following syntax.</span></span> <span data-ttu-id="c7ded-139">Všimněte si, že místo syntaxe indexeru, pomocí závorek a přiřazení, používá objekt s více hodnotami:</span><span class="sxs-lookup"><span data-stu-id="c7ded-139">Notice that instead of indexer syntax, with parentheses and an assignment, it uses an object with multiple values:</span></span>

[!code-csharp[DictionaryAddInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryAddInitializer)]  

<span data-ttu-id="c7ded-140">Tento příklad inicializátoru volá <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)> , aby se přidaly tři položky do slovníku.</span><span class="sxs-lookup"><span data-stu-id="c7ded-140">This initializer example calls <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)> to add the three items into the dictionary.</span></span> <span data-ttu-id="c7ded-141">Tyto dva různé způsoby inicializace asociativních kolekcí mají mírně odlišné chování, protože metoda volá kompilátor generuje.</span><span class="sxs-lookup"><span data-stu-id="c7ded-141">These two different ways to initialize associative collections have slightly different behavior because of the method calls the compiler generates.</span></span> <span data-ttu-id="c7ded-142">Obě varianty pracují s `Dictionary` třídou.</span><span class="sxs-lookup"><span data-stu-id="c7ded-142">Both variants work with the `Dictionary` class.</span></span> <span data-ttu-id="c7ded-143">Jiné typy mohou podporovat pouze jeden nebo druhý na základě jejich veřejného rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="c7ded-143">Other types may only support one or the other based on their public API.</span></span>

## <a name="examples"></a><span data-ttu-id="c7ded-144">Příklady</span><span class="sxs-lookup"><span data-stu-id="c7ded-144">Examples</span></span>

<span data-ttu-id="c7ded-145">Následující příklad kombinuje koncepty objektů a inicializátorů kolekcí.</span><span class="sxs-lookup"><span data-stu-id="c7ded-145">The following example combines the concepts of object and collection initializers.</span></span>

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullExample)]  

<span data-ttu-id="c7ded-146">Následující příklad ukazuje objekt, který implementuje <xref:System.Collections.IEnumerable> a obsahuje `Add` metodu s více parametry, používá inicializátor kolekce s více prvky na položku v seznamu, který odpovídá podpisu `Add` metody.</span><span class="sxs-lookup"><span data-stu-id="c7ded-146">The following example shows an object that implements <xref:System.Collections.IEnumerable> and contains an `Add` method with multiple parameters, It uses a collection initializer with multiple elements per item in the list that correspond to the signature of the `Add` method.</span></span>

[!code-csharp[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullListExample)]  

<span data-ttu-id="c7ded-147">`Add`metody mohou použít `params` klíčové slovo k převzetí variabilního počtu argumentů, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c7ded-147">`Add` methods can use the `params` keyword to take a variable number of arguments, as shown in the following example.</span></span> <span data-ttu-id="c7ded-148">Tento příklad také ukazuje vlastní implementaci indexeru pro inicializaci kolekce pomocí indexů.</span><span class="sxs-lookup"><span data-stu-id="c7ded-148">This example also demonstrates the custom implementation of an indexer to initialize a collection using indexes.</span></span>

[!code-csharp[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullDictionaryInitializer)]  

## <a name="see-also"></a><span data-ttu-id="c7ded-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7ded-149">See also</span></span>

- [<span data-ttu-id="c7ded-150">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="c7ded-150">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c7ded-151">LINQ v jazyku C#</span><span class="sxs-lookup"><span data-stu-id="c7ded-151">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="c7ded-152">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="c7ded-152">Anonymous Types</span></span>](anonymous-types.md)
