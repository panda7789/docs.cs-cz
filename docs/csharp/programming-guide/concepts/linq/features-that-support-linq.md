---
title: Funkce C# podporující LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: 51cc24fd8054b87b6c92a02450420a9c4abef525
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50191087"
---
# <a name="c-features-that-support-linq"></a><span data-ttu-id="b4e0d-102">Funkce C# podporující LINQ</span><span class="sxs-lookup"><span data-stu-id="b4e0d-102">C# Features That Support LINQ</span></span>
<span data-ttu-id="b4e0d-103">Následující část představuje nové jazykové konstrukce zavedené v jazyce C# 3.0.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-103">The following section introduces new language constructs introduced in C# 3.0.</span></span> <span data-ttu-id="b4e0d-104">I když tyto nové funkce se používají v míře s [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy, nejsou omezena na [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] a můžete použít v libovolném kontextu, kde můžete najít je užitečné.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-104">Although these new features are all used to a degree with [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, they are not limited to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] and can be used in any context where you find them useful.</span></span>  
  
## <a name="query-expressions"></a><span data-ttu-id="b4e0d-105">Výrazy dotazu</span><span class="sxs-lookup"><span data-stu-id="b4e0d-105">Query Expressions</span></span>  
 <span data-ttu-id="b4e0d-106">Výrazy dotazů pomocí deklarativní syntaxe SQL nebo výraz XQuery podobný dotaz nad kolekcí IEnumerable.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-106">Query expressions use a declarative syntax similar to SQL or XQuery to query over IEnumerable collections.</span></span> <span data-ttu-id="b4e0d-107">Při kompilaci syntaxe dotazu čas převést na volání metody [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] implementace poskytovatele rozšíření metody standardních dotazovacích operátorů.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-107">At compile time query syntax is converted to method calls to a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provider's implementation of the standard query operator extension methods.</span></span> <span data-ttu-id="b4e0d-108">Operátory standardního dotazu, které jsou v oboru tak, že zadáte odpovídající obor názvů s řízení aplikací `using` směrnice.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-108">Applications control the standard query operators that are in scope by specifying the appropriate namespace with a `using` directive.</span></span> <span data-ttu-id="b4e0d-109">Následující výraz dotazu přijímá pole řetězců, skupin podle prvního znaku v řetězci a řadí skupiny.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-109">The following query expression takes an array of strings, groups them according to the first character in the string, and orders the groups.</span></span>  
  
```csharp  
var query = from str in stringArray  
            group str by str[0] into stringGroup  
            orderby stringGroup.Key  
            select stringGroup;  
```  
  
 <span data-ttu-id="b4e0d-110">Další informace najdete v tématu [LINQ – výrazy dotazů](../../../../csharp/programming-guide/linq-query-expressions/index.md).</span><span class="sxs-lookup"><span data-stu-id="b4e0d-110">For more information, see [LINQ Query Expressions](../../../../csharp/programming-guide/linq-query-expressions/index.md).</span></span>  
  
## <a name="implicitly-typed-variables-var"></a><span data-ttu-id="b4e0d-111">Implicitně typované proměnné (var)</span><span class="sxs-lookup"><span data-stu-id="b4e0d-111">Implicitly Typed Variables (var)</span></span>  
 <span data-ttu-id="b4e0d-112">Namísto explicitního určení typu, když deklarujete a inicializujete proměnnou, můžete použít [var](../../../../csharp/language-reference/keywords/var.md) modifikátor, abyste instruovali kompilátor k odvození a přiřadit typ, jak je znázorněno zde:</span><span class="sxs-lookup"><span data-stu-id="b4e0d-112">Instead of explicitly specifying a type when you declare and initialize a variable, you can use the [var](../../../../csharp/language-reference/keywords/var.md) modifier to instruct the compiler to infer and assign the type, as shown here:</span></span>  
  
```csharp  
var number = 5;  
var name = "Virginia";  
var query = from str in stringArray  
            where str[0] == 'm'  
            select str;  
```  
  
 <span data-ttu-id="b4e0d-113">Proměnné deklarované jako `var` jsou stejně jako silného typu jako proměnné, jejíž typ zadat explicitně.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-113">Variables declared as `var` are just as strongly-typed as variables whose type you specify explicitly.</span></span> <span data-ttu-id="b4e0d-114">Použití `var` je možné vytvořit anonymní typy, ale lze použít pouze pro místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-114">The use of `var` makes it possible to create anonymous types, but it can be used only for local variables.</span></span> <span data-ttu-id="b4e0d-115">Pole lze také deklarovat pomocí implicitního zápisu.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-115">Arrays can also be declared with implicit typing.</span></span>  
  
 <span data-ttu-id="b4e0d-116">Další informace najdete v tématu [implicitně typované lokální proměnné](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="b4e0d-116">For more information, see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
## <a name="object-and-collection-initializers"></a><span data-ttu-id="b4e0d-117">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="b4e0d-117">Object and Collection Initializers</span></span>  
 <span data-ttu-id="b4e0d-118">Inicializátory objektu a kolekce umožňují inicializace objektů bez explicitního volání konstruktoru objektu.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-118">Object and collection initializers make it possible to initialize objects without explicitly calling a constructor for the object.</span></span> <span data-ttu-id="b4e0d-119">Inicializátory jsou obvykle používány ve výrazech dotazů, když jsou zdroje dat projektu do nového datového typu.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-119">Initializers are typically used in query expressions when they project the source data into a new data type.</span></span> <span data-ttu-id="b4e0d-120">Za předpokladu, že třídu s názvem `Customer` pomocí veřejného `Name` a `Phone` vlastnosti, inicializátor objektu můžete použít stejně jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="b4e0d-120">Assuming a class named `Customer` with public `Name` and `Phone` properties, the object initializer can be used as in the following code:</span></span>  
  
```csharp  
Customer cust = new Customer { Name = "Mike", Phone = "555-1212" };  
```  
<span data-ttu-id="b4e0d-121">Pokračujte v našich `Customer` třídy, se předpokládá, že je zdroj dat s názvem `IncomingOrders`a že pro jednotlivé objednávky s velkým `OrderSize`, jsme chtěli vytvořit nový `Customer` podle pořadí.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-121">Continuing with our `Customer` class, assume that there is a data source called `IncomingOrders`, and that for each order with a large `OrderSize`, we would like to create a new `Customer` based off of that order.</span></span> <span data-ttu-id="b4e0d-122">Dotaz LINQ mohou být provedeny na tento zdroj dat a použití inicializace objektu tak, aby vyplnil kolekce:</span><span class="sxs-lookup"><span data-stu-id="b4e0d-122">A LINQ query can be executed on this data source and use object initialization to fill a collection:</span></span>
```csharp
var newLargeOrderCustomers = from o in IncomingOrders
                            where o.OrderSize > 5
                            select new Customer { Name = o.Name, Phone = o.Phone };
```
<span data-ttu-id="b4e0d-123">Zdroj dat může mít více vlastností ležící pod pokličkou než `Customer` třídy jako `OrderSize`, ale s inicializace objektu se lisovaný data vrácená z dotazu na požadovaný datový typ, jsme zvolte data, která je relevantní pro naše třída.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-123">The data source may have more properties lying under the hood than the `Customer` class such as `OrderSize`, but with object initialization, the data returned from the query is molded into the desired data type; we choose the data that is relevant to our class.</span></span> <span data-ttu-id="b4e0d-124">V důsledku toho jsme teď mají `IEnumerable` vyplněný novými `Customer`s jsme chtěli.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-124">As a result, we now have an `IEnumerable` filled with the new `Customer`s we wanted.</span></span> <span data-ttu-id="b4e0d-125">Výše uvedené je také možné psát v syntaxe využívající metody LINQ na:</span><span class="sxs-lookup"><span data-stu-id="b4e0d-125">The above can also be written in LINQ's method syntax:</span></span>
```csharp
var newLargeOrderCustomers = IncomingOrders.Where(x => x.OrderSize > 5).Select(y => new Customer { Name = y.Name, Phone = y.Phone });
```
 <span data-ttu-id="b4e0d-126">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="b4e0d-126">For more information, see:</span></span>
 
 - [<span data-ttu-id="b4e0d-127">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="b4e0d-127">Object and Collection Initializers</span></span>](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)

 - [<span data-ttu-id="b4e0d-128">Syntaxe výrazu dotazu pro standardní operátory dotazu</span><span class="sxs-lookup"><span data-stu-id="b4e0d-128">Query Expression Syntax for Standard Query Operators</span></span>](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)

## <a name="anonymous-types"></a><span data-ttu-id="b4e0d-129">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="b4e0d-129">Anonymous Types</span></span>  
 <span data-ttu-id="b4e0d-130">Anonymní typ, který je vytvořen kompilátorem a název typu je dostupná jenom pro kompilátor.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-130">An anonymous type is constructed by the compiler and the type name is only available to the compiler.</span></span> <span data-ttu-id="b4e0d-131">Anonymní typy poskytují pohodlný způsob, jak seskupit sadu vlastností dočasně ve výsledku dotazu bez nutnosti definovat samostatně pojmenovaných typů.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-131">Anonymous types provide a convenient way to group a set of properties temporarily in a query result without having to define a separate named type.</span></span> <span data-ttu-id="b4e0d-132">Anonymní typy jsou inicializovány s výraz new a inicializátoru objektu, jak je znázorněno zde:</span><span class="sxs-lookup"><span data-stu-id="b4e0d-132">Anonymous types are initialized with a new expression and an object initializer, as shown here:</span></span>  
  
```csharp
select new {name = cust.Name, phone = cust.Phone};  
```  
  
 <span data-ttu-id="b4e0d-133">Další informace najdete v tématu [anonymní typy](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="b4e0d-133">For more information, see [Anonymous Types](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
## <a name="extension-methods"></a><span data-ttu-id="b4e0d-134">Metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="b4e0d-134">Extension Methods</span></span>  
 <span data-ttu-id="b4e0d-135">Rozšiřující metoda je statická metoda, která může být přidružený k typu, aby může být volán, jako by šlo o metodu instance na typu.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-135">An extension method is a static method that can be associated with a type, so that it can be called as if it were an instance method on the type.</span></span> <span data-ttu-id="b4e0d-136">Tato funkce umožňuje, v důsledku toho "Přidání" nové metody ke stávajícím typům bez skutečně jejich úpravou.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-136">This feature enables you to, in effect, "add" new methods to existing types without actually modifying them.</span></span> <span data-ttu-id="b4e0d-137">Operátory standardního dotazu představují sadu rozšiřujících metod, které poskytují [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazování funkce pro libovolný typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-137">The standard query operators are a set of extension methods that provide [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query functionality for any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="b4e0d-138">Další informace najdete v tématu [rozšiřující metody](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="b4e0d-138">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>  
  
## <a name="lambda-expressions"></a><span data-ttu-id="b4e0d-139">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="b4e0d-139">Lambda Expressions</span></span>  
 <span data-ttu-id="b4e0d-140">Výraz lambda je vložená funkce, která používá = > – operátor k oddělení vstupní parametry z těla funkce a je možné převést v době kompilace, delegáta nebo strom výrazů.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-140">A lambda expression is an inline function that uses the => operator to separate input parameters from the function body and can be converted at compile time to a delegate or an expression tree.</span></span> <span data-ttu-id="b4e0d-141">V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] programování, můžete narazit výrazy lambda při provedení volání přímé metody standardních dotazovacích operátorů.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-141">In [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] programming, you will encounter lambda expressions when you make direct method calls to the standard query operators.</span></span>  
  
 <span data-ttu-id="b4e0d-142">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="b4e0d-142">For more information, see:</span></span>  
  
-   [<span data-ttu-id="b4e0d-143">Anonymní funkce</span><span class="sxs-lookup"><span data-stu-id="b4e0d-143">Anonymous Functions</span></span>](../../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)  
  
-   [<span data-ttu-id="b4e0d-144">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="b4e0d-144">Lambda Expressions</span></span>](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
  
-   [<span data-ttu-id="b4e0d-145">Stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="b4e0d-145">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
   
## <a name="see-also"></a><span data-ttu-id="b4e0d-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="b4e0d-146">See Also</span></span>

- [<span data-ttu-id="b4e0d-147">Language-Integrated Query (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="b4e0d-147">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)
