---
title: Inicializátory objektu a kolekce (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
ms.openlocfilehash: def33041c4202c80aad9f08d1ff8d9dbbc477061
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43780046"
---
# <a name="object-and-collection-initializers-c-programming-guide"></a><span data-ttu-id="af061-102">Inicializátory objektu a kolekce (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="af061-102">Object and Collection Initializers (C# Programming Guide)</span></span>
<span data-ttu-id="af061-103">Inicializátory objektů umožňují přiřadit hodnoty k jakýmkoli přístupným polím nebo vlastnostem objektu při vytváření, bez nutnosti vyvolání konstruktoru následovaného řádky příkazů přiřazení.</span><span class="sxs-lookup"><span data-stu-id="af061-103">Object initializers let you assign values to any accessible fields or properties of an object at creation time without having to invoke a constructor followed by lines of assignment statements.</span></span> <span data-ttu-id="af061-104">Syntaxe inicializátoru objektu umožňuje zadat argumenty pro konstruktor, nebo tyto argumenty (a syntaxi se závorkami) vynechat.</span><span class="sxs-lookup"><span data-stu-id="af061-104">The object initializer syntax enables you to specify arguments for a constructor or omit the arguments (and parentheses syntax).</span></span>  <span data-ttu-id="af061-105">Následující příklad ukazuje, jak použít inicializátor objektu s pojmenovaným typem `Cat` a vyvolání výchozího konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="af061-105">The following example shows how to use an object initializer with a named type, `Cat` and how to invoke the default constructor.</span></span> <span data-ttu-id="af061-106">Všimněte si použití automaticky implementované vlastnosti v `Cat` třídy.</span><span class="sxs-lookup"><span data-stu-id="af061-106">Note the use of auto-implemented properties in the `Cat` class.</span></span> <span data-ttu-id="af061-107">Další informace najdete v tématu [implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="af061-107">For more information, see [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>  
  
 [!code-csharp[csProgGuideLINQ#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_1.cs)]  
  
 [!code-csharp[csProgGuideLINQ#45](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_2.cs)] 
 
<span data-ttu-id="af061-108">Syntaxi inicializátory objektů lze vytvářet instance, a poté přiřadí nově vytvořený objekt s vlastností přiřazené k proměnné v přiřazení.</span><span class="sxs-lookup"><span data-stu-id="af061-108">The object initializers syntax allows you to create an instance, and after that it assigns the newly created object, with its assigned properties, to the variable in the assignment.</span></span>
  
## <a name="object-initializers-with-anonymous-types"></a><span data-ttu-id="af061-109">Inicializátory objektů s anonymními typy</span><span class="sxs-lookup"><span data-stu-id="af061-109">Object Initializers with anonymous types</span></span>  
 <span data-ttu-id="af061-110">Přestože inicializátory objektů lze použít v libovolném kontextu, jsou zvláště užitečná v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazech dotazů.</span><span class="sxs-lookup"><span data-stu-id="af061-110">Although object initializers can be used in any context, they are especially useful in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="af061-111">Výrazy dotazů používají často [anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), které lze inicializovat pouze pomocí inicializátoru objektu, jak je znázorněno v následující deklaraci.</span><span class="sxs-lookup"><span data-stu-id="af061-111">Query expressions make frequent use of [anonymous types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), which can only be initialized by using an object initializer, as shown in the following declaration.</span></span>  
  
```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```  
  
 <span data-ttu-id="af061-112">Anonymní typy umožňují `select` klauzule [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazu transformovat objekty původní sekvence na objekty, jejichž hodnota a tvar se může lišit od původního dotazu.</span><span class="sxs-lookup"><span data-stu-id="af061-112">Anonymous types enable the `select` clause in a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression to transform objects of the original sequence into objects whose value and shape may differ from the original.</span></span> <span data-ttu-id="af061-113">Tato možnost je užitečná, pokud chcete uložit pouze část informace z jednotlivých objektů v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="af061-113">This is useful if you want to store only a part of the information from each object in a sequence.</span></span> <span data-ttu-id="af061-114">V následujícím příkladu se předpokládá, že objekt produktu (`p`) obsahuje mnoho polí a metod, a že si jenom chcete vytvořit pouze sekvenci objektů, které obsahují název produktu a jednotkovou cenu.</span><span class="sxs-lookup"><span data-stu-id="af061-114">In the following example, assume that a product object (`p`) contains many fields and methods, and that you are only interested in creating a sequence of objects that contain the product name and the unit price.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_3.cs)]  
  
 <span data-ttu-id="af061-115">Při spuštění tohoto dotazu `productInfos` proměnná bude obsahovat sekvenci objektů, které mohou být přístupné v `foreach` jak je uvedeno v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="af061-115">When this query is executed, the `productInfos` variable will contain a sequence of objects that can be accessed in a `foreach` statement as shown in this example:</span></span>  
  
```csharp
foreach(var p in productInfos){...}  
```  
  
 <span data-ttu-id="af061-116">Jednotlivé objekty v novém anonymním typu mají dvě veřejné vlastnosti, kterým budou přiděleny stejné názvy, jako mají vlastnosti nebo pole v původním objektu.</span><span class="sxs-lookup"><span data-stu-id="af061-116">Each object in the new anonymous type has two public properties which receive the same names as the properties or fields in the original object.</span></span> <span data-ttu-id="af061-117">Můžete také přejmenovat pole při vytváření anonymního typu; Následující příklad přejmenuje `UnitPrice` pole `Price`.</span><span class="sxs-lookup"><span data-stu-id="af061-117">You can also rename a field when you are creating an anonymous type; the following example renames the `UnitPrice` field to `Price`.</span></span>  
  
```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```  
  
## <a name="collection-initializers"></a><span data-ttu-id="af061-118">Inicializátory kolekce</span><span class="sxs-lookup"><span data-stu-id="af061-118">Collection initializers</span></span>  
 <span data-ttu-id="af061-119">Inicializátory kolekce umožňují určit jeden nebo více inicializátorů prvku při inicializaci kolekce typu tohoto implementuje <xref:System.Collections.IEnumerable> a má `Add` s odpovídajícím podpisem jako metodu instance nebo metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="af061-119">Collection initializers let you specify one or more element initializers when you initialize a collection type that implements <xref:System.Collections.IEnumerable> and has `Add` with the appropriate signature as an instance method or an extension method.</span></span> <span data-ttu-id="af061-120">Inicializátory prvku mohou být tvořeny jednoduchou hodnotou, výrazem nebo inicializátorem objektu.</span><span class="sxs-lookup"><span data-stu-id="af061-120">The element initializers can be a simple value, an expression or an object initializer.</span></span> <span data-ttu-id="af061-121">Pomocí inicializátoru kolekce není nutné zadat více volání `Add` metoda třídy ve zdrojovém kódu; volání přidá kompilátor.</span><span class="sxs-lookup"><span data-stu-id="af061-121">By using a collection initializer you do not have to specify multiple calls to the `Add` method of the class in your source code; the compiler adds the calls.</span></span>  
  
 <span data-ttu-id="af061-122">Následující příklady znázorňují dva jednoduché inicializátory kolekce:</span><span class="sxs-lookup"><span data-stu-id="af061-122">The following examples shows two simple collection initializers:</span></span>  
  
```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```  
  
 <span data-ttu-id="af061-123">Následující inicializátor kolekce používá inicializátory objektů k inicializaci objektů třídy `Cat` třídy definované v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="af061-123">The following collection initializer uses object initializers to initialize objects of the `Cat` class defined in a previous example.</span></span> <span data-ttu-id="af061-124">Pamatujte, že jednotlivé incializátory objektů jsou uzavřeny ve složených závorkách a odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="af061-124">Note that the individual object initializers are enclosed in braces and separated by commas.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_4.cs)]  
  
 <span data-ttu-id="af061-125">Můžete zadat [null](../../../csharp/language-reference/keywords/null.md) jako prvek v incializátoru kolekce Pokud kolekce `Add` metoda umožňuje.</span><span class="sxs-lookup"><span data-stu-id="af061-125">You can specify [null](../../../csharp/language-reference/keywords/null.md) as an element in a collection initializer if the collection's `Add` method allows it.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_5.cs)]  
  
 <span data-ttu-id="af061-126">Můžete zadat indexované elementy, pokud kolekce podporuje indexování.</span><span class="sxs-lookup"><span data-stu-id="af061-126">You can specify indexed elements if the collection supports indexing.</span></span>  
  
```csharp
var numbers = new Dictionary<int, string> {   
    [7] = "seven",   
    [9] = "nine",   
    [13] = "thirteen"   
};  
```  
  
## <a name="examples"></a><span data-ttu-id="af061-127">Příklady</span><span class="sxs-lookup"><span data-stu-id="af061-127">Examples</span></span>

 <span data-ttu-id="af061-128">Následující příklad kombinuje koncepty inicializátory objektu a kolekce.</span><span class="sxs-lookup"><span data-stu-id="af061-128">The following example combines the concepts of object and collection initializers.</span></span>

 [!code-csharp[csProgGuideLINQ#46](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_6.cs)]  
 
 <span data-ttu-id="af061-129">Je znázorněno v následujícím příkladu, objekt, který implementuje <xref:System.Collections.IEnumerable> obsahující `Add` metodu s více parametry umožňuje inicializátory kolekce s více prvky každou položku v seznamu odpovídající podpis `Add` metody.</span><span class="sxs-lookup"><span data-stu-id="af061-129">Shown in the following example, an object which implements <xref:System.Collections.IEnumerable> containing an `Add` method with multiple parameters allows for collection initializers with multiple elements per item in the list corresponding to the signature of the `Add` method.</span></span> 
 
 [!code-csharp[csProgGuideLINQ#84](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_7.cs)]
 
 <span data-ttu-id="af061-130">`Add` můžete použít metody `params` – klíčové slovo se proměnný počet argumentů, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="af061-130">`Add` methods can use the `params` keyword to take a variable number of arguments as shown in the following example.</span></span> <span data-ttu-id="af061-131">Tento příklad ukazuje vlastní implementaci indexer i k inicializaci kolekce pomocí indexů.</span><span class="sxs-lookup"><span data-stu-id="af061-131">This example demonstrates the custom implementation of an indexer as well to initialize a collection using indexes.</span></span>
 
 [!code-csharp[csProgGuideLINQ#85](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_8.cs)]
 
## <a name="see-also"></a><span data-ttu-id="af061-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="af061-132">See Also</span></span>

- [<span data-ttu-id="af061-133">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="af061-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="af061-134">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="af061-134">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
- [<span data-ttu-id="af061-135">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="af061-135">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
