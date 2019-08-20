---
title: Funkce C# podporující LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: 1029d34ae8823fe91c7e4bc92e168fcc1061c707
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594412"
---
# <a name="c-features-that-support-linq"></a><span data-ttu-id="b40ed-102">Funkce C# podporující LINQ</span><span class="sxs-lookup"><span data-stu-id="b40ed-102">C# Features That Support LINQ</span></span>

<span data-ttu-id="b40ed-103">V následující části jsou představeny nové jazykové konstrukce představené v C# 3,0.</span><span class="sxs-lookup"><span data-stu-id="b40ed-103">The following section introduces new language constructs introduced in C# 3.0.</span></span> <span data-ttu-id="b40ed-104">I když jsou tyto nové funkce využité pro určitý stupeň [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] s dotazy, nejsou omezené na [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] a je možné je používat v jakémkoli kontextu, kde je najdete, které jsou užitečné.</span><span class="sxs-lookup"><span data-stu-id="b40ed-104">Although these new features are all used to a degree with [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, they are not limited to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] and can be used in any context where you find them useful.</span></span>

## <a name="query-expressions"></a><span data-ttu-id="b40ed-105">Výrazy dotazu</span><span class="sxs-lookup"><span data-stu-id="b40ed-105">Query Expressions</span></span>

<span data-ttu-id="b40ed-106">Výrazy dotazů používají deklarativní syntaxi podobnou syntaxi SQL nebo XQuery pro dotazování přes kolekce IEnumerable.</span><span class="sxs-lookup"><span data-stu-id="b40ed-106">Query expressions use a declarative syntax similar to SQL or XQuery to query over IEnumerable collections.</span></span> <span data-ttu-id="b40ed-107">Syntaxe dotazu v době kompilace je převedena na volání metody do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] implementace standardních metod rozšíření operátoru dotazu.</span><span class="sxs-lookup"><span data-stu-id="b40ed-107">At compile time query syntax is converted to method calls to a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provider's implementation of the standard query operator extension methods.</span></span> <span data-ttu-id="b40ed-108">Aplikace řídí standardní operátory dotazů, které jsou v oboru, zadáním příslušného oboru názvů s `using` direktivou.</span><span class="sxs-lookup"><span data-stu-id="b40ed-108">Applications control the standard query operators that are in scope by specifying the appropriate namespace with a `using` directive.</span></span> <span data-ttu-id="b40ed-109">Následující výraz dotazu přebírá pole řetězců, seskupuje je podle prvního znaku v řetězci a řadí skupiny.</span><span class="sxs-lookup"><span data-stu-id="b40ed-109">The following query expression takes an array of strings, groups them according to the first character in the string, and orders the groups.</span></span>

```csharp
var query = from str in stringArray
            group str by str[0] into stringGroup
            orderby stringGroup.Key
            select stringGroup;
```

<span data-ttu-id="b40ed-110">Další informace najdete v tématu [výrazy dotazů LINQ](../../linq-query-expressions/index.md).</span><span class="sxs-lookup"><span data-stu-id="b40ed-110">For more information, see [LINQ Query Expressions](../../linq-query-expressions/index.md).</span></span>

## <a name="implicitly-typed-variables-var"></a><span data-ttu-id="b40ed-111">Implicitně typované proměnné (var)</span><span class="sxs-lookup"><span data-stu-id="b40ed-111">Implicitly Typed Variables (var)</span></span>

<span data-ttu-id="b40ed-112">Namísto explicitního určení typu při deklaraci a inicializaci proměnné lze použít modifikátor [var](../../../language-reference/keywords/var.md) k tomu, aby kompilátor mohl odvodit a přiřadit typ, jak je znázorněno zde:</span><span class="sxs-lookup"><span data-stu-id="b40ed-112">Instead of explicitly specifying a type when you declare and initialize a variable, you can use the [var](../../../language-reference/keywords/var.md) modifier to instruct the compiler to infer and assign the type, as shown here:</span></span>

```csharp
var number = 5;
var name = "Virginia";
var query = from str in stringArray
            where str[0] == 'm'
            select str;
```

<span data-ttu-id="b40ed-113">Proměnné deklarované jako `var` jsou pouze silně typované jako proměnné, jejichž typ zadáte explicitně.</span><span class="sxs-lookup"><span data-stu-id="b40ed-113">Variables declared as `var` are just as strongly-typed as variables whose type you specify explicitly.</span></span> <span data-ttu-id="b40ed-114">Použití `var` je možné vytvořit anonymní typy, ale lze je použít pouze pro místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="b40ed-114">The use of `var` makes it possible to create anonymous types, but it can be used only for local variables.</span></span> <span data-ttu-id="b40ed-115">Pole lze také deklarovat pomocí implicitního zadání.</span><span class="sxs-lookup"><span data-stu-id="b40ed-115">Arrays can also be declared with implicit typing.</span></span>

<span data-ttu-id="b40ed-116">Další informace naleznete v tématu [implicitně typované lokální proměnné](../../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="b40ed-116">For more information, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>

## <a name="object-and-collection-initializers"></a><span data-ttu-id="b40ed-117">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="b40ed-117">Object and Collection Initializers</span></span>

<span data-ttu-id="b40ed-118">Inicializátory objektů a kolekcí umožňují inicializovat objekty bez explicitního volání konstruktoru objektu.</span><span class="sxs-lookup"><span data-stu-id="b40ed-118">Object and collection initializers make it possible to initialize objects without explicitly calling a constructor for the object.</span></span> <span data-ttu-id="b40ed-119">Inicializátory se obvykle používají ve výrazech dotazů při projektování zdrojových dat do nového datového typu.</span><span class="sxs-lookup"><span data-stu-id="b40ed-119">Initializers are typically used in query expressions when they project the source data into a new data type.</span></span> <span data-ttu-id="b40ed-120">Za předpokladu, `Customer` že třída `Name` s `Phone` názvem Public a Properties, může být inicializátor objektu použit jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="b40ed-120">Assuming a class named `Customer` with public `Name` and `Phone` properties, the object initializer can be used as in the following code:</span></span>

```csharp
var cust = new Customer { Name = "Mike", Phone = "555-1212" };
```

<span data-ttu-id="b40ed-121">V případě pokračování `Customer` v naší třídě se předpokládá, že je k dispozici zdroj dat s názvem `IncomingOrders`a že pro každou `OrderSize`objednávku má velký, chtěli bychom vytvořit nové `Customer` založené na tomto pořadí.</span><span class="sxs-lookup"><span data-stu-id="b40ed-121">Continuing with our `Customer` class, assume that there is a data source called `IncomingOrders`, and that for each order with a large `OrderSize`, we would like to create a new `Customer` based off of that order.</span></span> <span data-ttu-id="b40ed-122">V tomto zdroji dat lze spustit dotaz LINQ a k vyplnění kolekce použít inicializaci objektu:</span><span class="sxs-lookup"><span data-stu-id="b40ed-122">A LINQ query can be executed on this data source and use object initialization to fill a collection:</span></span>

```csharp
var newLargeOrderCustomers = from o in IncomingOrders
                            where o.OrderSize > 5
                            select new Customer { Name = o.Name, Phone = o.Phone };
```

<span data-ttu-id="b40ed-123">Zdroj dat může mít více vlastností ležící pod digestoří `Customer` `OrderSize`, než je třída, jako je například, ale s inicializací objektu, data vrácená z dotazu jsou molded na požadovaný datový typ. vybíráme data, která jsou relevantní pro naši třídu.</span><span class="sxs-lookup"><span data-stu-id="b40ed-123">The data source may have more properties lying under the hood than the `Customer` class such as `OrderSize`, but with object initialization, the data returned from the query is molded into the desired data type; we choose the data that is relevant to our class.</span></span> <span data-ttu-id="b40ed-124">V důsledku toho jsme teď `IEnumerable` naplnili nové `Customer`s, které jsme chtěli.</span><span class="sxs-lookup"><span data-stu-id="b40ed-124">As a result, we now have an `IEnumerable` filled with the new `Customer`s we wanted.</span></span> <span data-ttu-id="b40ed-125">Výše uvedený postup lze také zapsat v syntaxi metody LINQ:</span><span class="sxs-lookup"><span data-stu-id="b40ed-125">The above can also be written in LINQ's method syntax:</span></span>

```csharp
var newLargeOrderCustomers = IncomingOrders.Where(x => x.OrderSize > 5).Select(y => new Customer { Name = y.Name, Phone = y.Phone });
```

<span data-ttu-id="b40ed-126">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="b40ed-126">For more information, see:</span></span>

- [<span data-ttu-id="b40ed-127">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="b40ed-127">Object and Collection Initializers</span></span>](../../classes-and-structs/object-and-collection-initializers.md)

- [<span data-ttu-id="b40ed-128">Syntaxe výrazu dotazu pro standardní operátory dotazu</span><span class="sxs-lookup"><span data-stu-id="b40ed-128">Query Expression Syntax for Standard Query Operators</span></span>](./query-expression-syntax-for-standard-query-operators.md)

## <a name="anonymous-types"></a><span data-ttu-id="b40ed-129">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="b40ed-129">Anonymous Types</span></span>

<span data-ttu-id="b40ed-130">Anonymní typ je vytvořen kompilátorem a název typu je k dispozici pouze pro kompilátor.</span><span class="sxs-lookup"><span data-stu-id="b40ed-130">An anonymous type is constructed by the compiler and the type name is only available to the compiler.</span></span> <span data-ttu-id="b40ed-131">Anonymní typy poskytují pohodlný způsob, jak dočasně seskupit sadu vlastností do výsledku dotazu bez nutnosti definovat samostatný pojmenovaný typ.</span><span class="sxs-lookup"><span data-stu-id="b40ed-131">Anonymous types provide a convenient way to group a set of properties temporarily in a query result without having to define a separate named type.</span></span> <span data-ttu-id="b40ed-132">Anonymní typy jsou inicializovány s novým výrazem a inicializátorem objektu, jak je znázorněno zde:</span><span class="sxs-lookup"><span data-stu-id="b40ed-132">Anonymous types are initialized with a new expression and an object initializer, as shown here:</span></span>

```csharp
select new {name = cust.Name, phone = cust.Phone};
```

<span data-ttu-id="b40ed-133">Další informace najdete v tématu [anonymní typy](../../classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="b40ed-133">For more information, see [Anonymous Types](../../classes-and-structs/anonymous-types.md).</span></span>

## <a name="extension-methods"></a><span data-ttu-id="b40ed-134">Metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="b40ed-134">Extension Methods</span></span>

<span data-ttu-id="b40ed-135">Rozšiřující metoda je statická metoda, která může být přidružena k typu, aby mohla být volána jako metoda instance typu.</span><span class="sxs-lookup"><span data-stu-id="b40ed-135">An extension method is a static method that can be associated with a type, so that it can be called as if it were an instance method on the type.</span></span> <span data-ttu-id="b40ed-136">Tato funkce umožňuje přidat nové metody do stávajících typů, aniž by bylo nutné je skutečně upravovat.</span><span class="sxs-lookup"><span data-stu-id="b40ed-136">This feature enables you to, in effect, "add" new methods to existing types without actually modifying them.</span></span> <span data-ttu-id="b40ed-137">Standardní operátory dotazu jsou sada rozšiřujících metod, které poskytují [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] funkce dotazů pro jakýkoli typ, který implementuje. <xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="b40ed-137">The standard query operators are a set of extension methods that provide [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query functionality for any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>

<span data-ttu-id="b40ed-138">Další informace naleznete v tématu [metody rozšíření](../../classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="b40ed-138">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span>

## <a name="lambda-expressions"></a><span data-ttu-id="b40ed-139">Lambda – výrazy</span><span class="sxs-lookup"><span data-stu-id="b40ed-139">Lambda Expressions</span></span>

<span data-ttu-id="b40ed-140">Výraz lambda je vložená funkce, která používá operátor = > pro oddělení vstupních parametrů z těla funkce a může být převedena v době kompilace na delegáta nebo strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="b40ed-140">A lambda expression is an inline function that uses the => operator to separate input parameters from the function body and can be converted at compile time to a delegate or an expression tree.</span></span> <span data-ttu-id="b40ed-141">V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] programování dojde k vyvolání výrazů lambda při přímém volání metody do standardních operátorů dotazu.</span><span class="sxs-lookup"><span data-stu-id="b40ed-141">In [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] programming, you will encounter lambda expressions when you make direct method calls to the standard query operators.</span></span>

<span data-ttu-id="b40ed-142">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="b40ed-142">For more information, see:</span></span>

- [<span data-ttu-id="b40ed-143">Anonymní funkce</span><span class="sxs-lookup"><span data-stu-id="b40ed-143">Anonymous Functions</span></span>](../../statements-expressions-operators/anonymous-functions.md)

- [<span data-ttu-id="b40ed-144">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="b40ed-144">Lambda Expressions</span></span>](../../statements-expressions-operators/lambda-expressions.md)

- [<span data-ttu-id="b40ed-145">Stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="b40ed-145">Expression Trees (C#)</span></span>](../expression-trees/index.md)

## <a name="see-also"></a><span data-ttu-id="b40ed-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b40ed-146">See also</span></span>

- [<span data-ttu-id="b40ed-147">Dotaz integrovaný na jazyku (LINQ)C#()</span><span class="sxs-lookup"><span data-stu-id="b40ed-147">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
