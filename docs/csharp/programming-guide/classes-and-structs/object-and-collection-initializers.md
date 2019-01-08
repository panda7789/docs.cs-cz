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
# <a name="object-and-collection-initializers-c-programming-guide"></a><span data-ttu-id="0a983-102">Inicializátory objektu a kolekce (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="0a983-102">Object and Collection Initializers (C# Programming Guide)</span></span>

<span data-ttu-id="0a983-103">C#Umožňuje vytvořit instanci objektu nebo kolekci a provést přiřazení členů v jediném příkazu.</span><span class="sxs-lookup"><span data-stu-id="0a983-103">C# lets you instantiate an object or collection and perform member assignments in a single statement.</span></span>

## <a name="object-initializers"></a><span data-ttu-id="0a983-104">Inicializátory objektů</span><span class="sxs-lookup"><span data-stu-id="0a983-104">Object initializers</span></span>

<span data-ttu-id="0a983-105">Inicializátory objektů umožňují přiřadit hodnoty k jakýmkoli přístupným polím nebo vlastnostem objektu při vytváření, bez nutnosti vyvolání konstruktoru následovaného řádky příkazů přiřazení.</span><span class="sxs-lookup"><span data-stu-id="0a983-105">Object initializers let you assign values to any accessible fields or properties of an object at creation time without having to invoke a constructor followed by lines of assignment statements.</span></span> <span data-ttu-id="0a983-106">Syntaxe inicializátoru objektu umožňuje zadat argumenty pro konstruktor, nebo tyto argumenty (a syntaxi se závorkami) vynechat.</span><span class="sxs-lookup"><span data-stu-id="0a983-106">The object initializer syntax enables you to specify arguments for a constructor or omit the arguments (and parentheses syntax).</span></span>  <span data-ttu-id="0a983-107">Následující příklad ukazuje, jak použít inicializátor objektu s pojmenovaným typem `Cat` a vyvolání výchozího konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="0a983-107">The following example shows how to use an object initializer with a named type, `Cat` and how to invoke the default constructor.</span></span> <span data-ttu-id="0a983-108">Všimněte si použití automaticky implementované vlastnosti v `Cat` třídy.</span><span class="sxs-lookup"><span data-stu-id="0a983-108">Note the use of auto-implemented properties in the `Cat` class.</span></span> <span data-ttu-id="0a983-109">Další informace najdete v tématu [implemented Properties](auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="0a983-109">For more information, see [Auto-Implemented Properties](auto-implemented-properties.md).</span></span>  
  
[!code-csharp[ObjectInitializer1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#CatDeclaration)]  
[!code-csharp[ObjectInitializer1a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ObjectPropertyInitialization)]  
 
<span data-ttu-id="0a983-110">Syntaxi inicializátory objektů lze vytvářet instance, a poté přiřadí nově vytvořený objekt s vlastností přiřazené k proměnné v přiřazení.</span><span class="sxs-lookup"><span data-stu-id="0a983-110">The object initializers syntax allows you to create an instance, and after that it assigns the newly created object, with its assigned properties, to the variable in the assignment.</span></span>

<span data-ttu-id="0a983-111">Počínaje C# 6, objekt inicializátory můžete nastavit indexery, kromě přiřazení polí a vlastností.</span><span class="sxs-lookup"><span data-stu-id="0a983-111">Starting with C# 6, object initializers can set indexers, in addition to assigning fields and properties.</span></span> <span data-ttu-id="0a983-112">Zvažte proto základní `Matrix` třídy:</span><span class="sxs-lookup"><span data-stu-id="0a983-112">Consider this basic `Matrix` class:</span></span>

[!code-csharp[ObjectInitializer2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixDeclaration)]  

<span data-ttu-id="0a983-113">Může inicializovat jednotkovou matici s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="0a983-113">You could initialize the identity matrix with the following code:</span></span>

[!code-csharp[ObjectInitializer2a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixInitialization)]  

<span data-ttu-id="0a983-114">Žádné přístupné indexer, který obsahuje přístupnou metodu setter může sloužit jako jeden z výrazů v inicializátoru objektu bez ohledu na čísla nebo typy argumentů.</span><span class="sxs-lookup"><span data-stu-id="0a983-114">Any accessible indexer that contains an accessible setter can be used as one of the expressions in an object initializer, regardless of the number or types of arguments.</span></span> <span data-ttu-id="0a983-115">Argumenty index formu levé části přiřazení a hodnota představuje pravou stranu výrazu.</span><span class="sxs-lookup"><span data-stu-id="0a983-115">The index arguments form the left side of the assignment, and the value is the right side of the expression.</span></span>  <span data-ttu-id="0a983-116">Například toto jsou všechny platné if `IndexersExample` má odpovídající indexování:</span><span class="sxs-lookup"><span data-stu-id="0a983-116">For example, these are all valid if `IndexersExample` has the appropriate indexers:</span></span>

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

<span data-ttu-id="0a983-117">Pro předchozí kód mohl zkompilovat `IndexersExample` typ musí mít následující členy:</span><span class="sxs-lookup"><span data-stu-id="0a983-117">For the preceding code to compile, the `IndexersExample` type must have the following members:</span></span>

```csharp
public string name;
public double Size { set { ... }; }
public char this[int i] { set { ... }; }
public string this[char c, int i] {  set { ... }; }
}
```

## <a name="object-initializers-with-anonymous-types"></a><span data-ttu-id="0a983-118">Inicializátory objektů s anonymními typy</span><span class="sxs-lookup"><span data-stu-id="0a983-118">Object Initializers with anonymous types</span></span>

<span data-ttu-id="0a983-119">Přestože inicializátory objektů lze použít v libovolném kontextu, jsou zvláště užitečná v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazech dotazů.</span><span class="sxs-lookup"><span data-stu-id="0a983-119">Although object initializers can be used in any context, they are especially useful in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="0a983-120">Výrazy dotazů používají často [anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), které lze inicializovat pouze pomocí inicializátoru objektu, jak je znázorněno v následující deklaraci.</span><span class="sxs-lookup"><span data-stu-id="0a983-120">Query expressions make frequent use of [anonymous types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), which can only be initialized by using an object initializer, as shown in the following declaration.</span></span>  

```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```

<span data-ttu-id="0a983-121">Anonymní typy umožňují `select` klauzule [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazu transformovat objekty původní sekvence na objekty, jejichž hodnota a tvar se může lišit od původního dotazu.</span><span class="sxs-lookup"><span data-stu-id="0a983-121">Anonymous types enable the `select` clause in a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression to transform objects of the original sequence into objects whose value and shape may differ from the original.</span></span> <span data-ttu-id="0a983-122">Tato možnost je užitečná, pokud chcete uložit pouze část informace z jednotlivých objektů v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="0a983-122">This is useful if you want to store only a part of the information from each object in a sequence.</span></span> <span data-ttu-id="0a983-123">V následujícím příkladu se předpokládá, že objekt produktu (`p`) obsahuje mnoho polí a metod, a že si jenom chcete vytvořit pouze sekvenci objektů, které obsahují název produktu a jednotkovou cenu.</span><span class="sxs-lookup"><span data-stu-id="0a983-123">In the following example, assume that a product object (`p`) contains many fields and methods, and that you are only interested in creating a sequence of objects that contain the product name and the unit price.</span></span>  
  
[!code-csharp[ObjectInitializer3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#AnonymousUse)]  

<span data-ttu-id="0a983-124">Při spuštění tohoto dotazu `productInfos` proměnná bude obsahovat sekvenci objektů, které mohou být přístupné v `foreach` jak je uvedeno v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="0a983-124">When this query is executed, the `productInfos` variable will contain a sequence of objects that can be accessed in a `foreach` statement as shown in this example:</span></span>  

```csharp
foreach(var p in productInfos){...}  
```

<span data-ttu-id="0a983-125">Každý objekt v novém anonymním typu mají dvě veřejné vlastnosti, které budou přiděleny stejné názvy jako vlastnosti nebo pole v původním objektu.</span><span class="sxs-lookup"><span data-stu-id="0a983-125">Each object in the new anonymous type has two public properties that receive the same names as the properties or fields in the original object.</span></span> <span data-ttu-id="0a983-126">Můžete také přejmenovat pole při vytváření anonymního typu; Následující příklad přejmenuje `UnitPrice` pole `Price`.</span><span class="sxs-lookup"><span data-stu-id="0a983-126">You can also rename a field when you are creating an anonymous type; the following example renames the `UnitPrice` field to `Price`.</span></span>  

```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```

## <a name="collection-initializers"></a><span data-ttu-id="0a983-127">Inicializátory kolekce</span><span class="sxs-lookup"><span data-stu-id="0a983-127">Collection initializers</span></span>

<span data-ttu-id="0a983-128">Inicializátory kolekce umožňují určit jeden nebo více inicializátorů prvku při inicializaci kolekce typu tohoto implementuje <xref:System.Collections.IEnumerable> a má `Add` s odpovídajícím podpisem jako metodu instance nebo metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="0a983-128">Collection initializers let you specify one or more element initializers when you initialize a collection type that implements <xref:System.Collections.IEnumerable> and has `Add` with the appropriate signature as an instance method or an extension method.</span></span> <span data-ttu-id="0a983-129">Inicializátory elementů polí může být jednoduchých hodnot, výrazem nebo inicializátorem objektu.</span><span class="sxs-lookup"><span data-stu-id="0a983-129">The element initializers can be a simple value, an expression, or an object initializer.</span></span> <span data-ttu-id="0a983-130">Pomocí inicializátoru kolekce, není nutné zadávat větší počet volání; volání přidá kompilátor automaticky.</span><span class="sxs-lookup"><span data-stu-id="0a983-130">By using a collection initializer, you do not have to specify multiple calls; the compiler adds the calls automatically.</span></span>  
  
<span data-ttu-id="0a983-131">Následující příklad ukazuje dva jednoduché inicializátory kolekce:</span><span class="sxs-lookup"><span data-stu-id="0a983-131">The following example shows two simple collection initializers:</span></span>  

```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```

<span data-ttu-id="0a983-132">Následující inicializátor kolekce používá inicializátory objektů k inicializaci objektů třídy `Cat` třídy definované v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0a983-132">The following collection initializer uses object initializers to initialize objects of the `Cat` class defined in a previous example.</span></span> <span data-ttu-id="0a983-133">Pamatujte, že jednotlivé incializátory objektů jsou uzavřeny ve složených závorkách a odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="0a983-133">Note that the individual object initializers are enclosed in braces and separated by commas.</span></span>  
  
[!code-csharp[ListInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitializer)]  
  
<span data-ttu-id="0a983-134">Můžete zadat [null](../../language-reference/keywords/null.md) jako prvek v incializátoru kolekce Pokud kolekce `Add` metoda umožňuje.</span><span class="sxs-lookup"><span data-stu-id="0a983-134">You can specify [null](../../language-reference/keywords/null.md) as an element in a collection initializer if the collection's `Add` method allows it.</span></span>  
  
[!code-csharp[ListInitializerNull](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitialerWithNull)]  
  
 <span data-ttu-id="0a983-135">Indexované prvky můžete zadat, pokud kolekce podporuje čtení / zápis indexování.</span><span class="sxs-lookup"><span data-stu-id="0a983-135">You can specify indexed elements if the collection supports read / write indexing.</span></span>
  
[!code-csharp[DictionaryInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryIndexerInitializer)]  

<span data-ttu-id="0a983-136">V předchozím příkladu generuje kód, který volá <xref:System.Collections.Generic.Dictionary%602.Item(%600)> nastavit hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0a983-136">The preceding sample generates code that calls the <xref:System.Collections.Generic.Dictionary%602.Item(%600)> to set the values.</span></span> <span data-ttu-id="0a983-137">Počínaje C# 6, můžete inicializovat slovníky a dalších asociativní kontejnery pomocí následující syntaxe.</span><span class="sxs-lookup"><span data-stu-id="0a983-137">Beginning with C# 6, you can initialize dictionaries and other associative containers using the following syntax.</span></span> <span data-ttu-id="0a983-138">Všimněte si, že místo indexer syntaxe se závorkami a přiřazení, používá objekt s více hodnotami:</span><span class="sxs-lookup"><span data-stu-id="0a983-138">Notice that instead of indexer syntax, with parentheses and an assignment, it uses an object with multiple values:</span></span>

[!code-csharp[DictionaryAddInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryAddInitializer)]  

<span data-ttu-id="0a983-139">V tomto příkladu inicializátor volá <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)> přidáte tři položky do slovníku.</span><span class="sxs-lookup"><span data-stu-id="0a983-139">This initializer example calls <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)> to add the three items into the dictionary.</span></span> <span data-ttu-id="0a983-140">Tyto dva různé způsoby inicializovat asociativní kolekcí mají mírně odlišné chování kvůli volání metody, které generuje kompilátor.</span><span class="sxs-lookup"><span data-stu-id="0a983-140">These two different ways to initialize associative collections have slightly different behavior because of the method calls the compiler generates.</span></span> <span data-ttu-id="0a983-141">Obě varianty pracovat `Dictionary` třídy.</span><span class="sxs-lookup"><span data-stu-id="0a983-141">Both variants work with the `Dictionary` class.</span></span> <span data-ttu-id="0a983-142">Jiné typy může podporovat pouze jednu nebo další závislosti na jejich veřejné rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="0a983-142">Other types may only support one or the other based on their public API.</span></span>

## <a name="examples"></a><span data-ttu-id="0a983-143">Příklady</span><span class="sxs-lookup"><span data-stu-id="0a983-143">Examples</span></span>

<span data-ttu-id="0a983-144">Následující příklad kombinuje koncepty inicializátory objektu a kolekce.</span><span class="sxs-lookup"><span data-stu-id="0a983-144">The following example combines the concepts of object and collection initializers.</span></span>

[!code-csharp-interactive[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullExample)]  

<span data-ttu-id="0a983-145">Následující příklad ukazuje, objekt, který implementuje <xref:System.Collections.IEnumerable> a obsahuje `Add` metodu s více parametry používá inicializátor kolekce s více prvky každou položku v seznamu, které odpovídají podpis `Add`metody.</span><span class="sxs-lookup"><span data-stu-id="0a983-145">The following example shows an object that implements <xref:System.Collections.IEnumerable> and contains an `Add` method with multiple parameters, It uses a collection initializer with multiple elements per item in the list that correspond to the signature of the `Add` method.</span></span>

[!code-csharp-interactive[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullListExample)]  

<span data-ttu-id="0a983-146">`Add` můžete použít metody `params` – klíčové slovo se proměnný počet argumentů, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0a983-146">`Add` methods can use the `params` keyword to take a variable number of arguments, as shown in the following example.</span></span> <span data-ttu-id="0a983-147">Tento příklad také ukazuje vlastní implementaci indexeru k inicializaci kolekce pomocí indexů.</span><span class="sxs-lookup"><span data-stu-id="0a983-147">This example also demonstrates the custom implementation of an indexer to initialize a collection using indexes.</span></span>

[!code-csharp-interactive[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullDictionaryInitializer)]  

## <a name="see-also"></a><span data-ttu-id="0a983-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="0a983-148">See Also</span></span>

- [<span data-ttu-id="0a983-149">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0a983-149">C# Programming Guide</span></span>](../index.md)  
- [<span data-ttu-id="0a983-150">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="0a983-150">LINQ Query Expressions</span></span>](../linq-query-expressions/index.md)  
- [<span data-ttu-id="0a983-151">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="0a983-151">Anonymous Types</span></span>](anonymous-types.md)
