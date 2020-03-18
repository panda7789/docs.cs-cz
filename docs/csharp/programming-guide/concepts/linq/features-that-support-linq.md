---
title: Funkce C# podporující LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: 9fc8adaa49d02f8b69c2db6e94a28b9fab36b3b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635792"
---
# <a name="c-features-that-support-linq"></a><span data-ttu-id="8d1b0-102">Funkce C# podporující LINQ</span><span class="sxs-lookup"><span data-stu-id="8d1b0-102">C# Features That Support LINQ</span></span>

<span data-ttu-id="8d1b0-103">V následující části zavádí nové jazykové konstrukce zavedené v jazyce C# 3.0.</span><span class="sxs-lookup"><span data-stu-id="8d1b0-103">The following section introduces new language constructs introduced in C# 3.0.</span></span> <span data-ttu-id="8d1b0-104">Přestože tyto nové funkce jsou všechny používány do určité míry s dotazy LINQ, nejsou omezeny na LINQ a lze je použít v jakémkoli kontextu, kde je považujete za užitečné.</span><span class="sxs-lookup"><span data-stu-id="8d1b0-104">Although these new features are all used to a degree with LINQ queries, they are not limited to LINQ and can be used in any context where you find them useful.</span></span>

## <a name="query-expressions"></a><span data-ttu-id="8d1b0-105">Výrazy dotazu</span><span class="sxs-lookup"><span data-stu-id="8d1b0-105">Query Expressions</span></span>

<span data-ttu-id="8d1b0-106">Výrazy dotazu používají k dotazování přes kolekce IEnumerable deklarativní syntaxi podobné sql nebo xquery.</span><span class="sxs-lookup"><span data-stu-id="8d1b0-106">Query expressions use a declarative syntax similar to SQL or XQuery to query over IEnumerable collections.</span></span> <span data-ttu-id="8d1b0-107">V době kompilace je syntaxe dotazu převedena na volání metody na implementaci standardních metod rozšíření operátoru dotazu poskytovatele LINQ.</span><span class="sxs-lookup"><span data-stu-id="8d1b0-107">At compile time query syntax is converted to method calls to a LINQ provider's implementation of the standard query operator extension methods.</span></span> <span data-ttu-id="8d1b0-108">Aplikace řídí standardní operátory dotazů, které jsou v `using` oboru zadáním příslušného oboru názvů pomocí směrnice.</span><span class="sxs-lookup"><span data-stu-id="8d1b0-108">Applications control the standard query operators that are in scope by specifying the appropriate namespace with a `using` directive.</span></span> <span data-ttu-id="8d1b0-109">Následující výraz dotazu přebírá pole řetězců, seskupuje je podle prvního znaku v řetězci a uskutečňuje skupiny.</span><span class="sxs-lookup"><span data-stu-id="8d1b0-109">The following query expression takes an array of strings, groups them according to the first character in the string, and orders the groups.</span></span>

```csharp
var query = from str in stringArray
            group str by str[0] into stringGroup
            orderby stringGroup.Key
            select stringGroup;
```

<span data-ttu-id="8d1b0-110">Další informace naleznete v tématu [LINQ Query Expressions](../../../linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="8d1b0-110">For more information, see [LINQ Query Expressions](../../../linq/index.md).</span></span>

## <a name="implicitly-typed-variables-var"></a><span data-ttu-id="8d1b0-111">Implicitně zadané proměnné (var)</span><span class="sxs-lookup"><span data-stu-id="8d1b0-111">Implicitly Typed Variables (var)</span></span>

<span data-ttu-id="8d1b0-112">Namísto explicitního zadání typu při deklarování a inicializaci proměnné můžete pomocí modifikátoru [var](../../../language-reference/keywords/var.md) instruovat kompilátor, aby odvodil a přiřazoval typ, jak je znázorněno zde:</span><span class="sxs-lookup"><span data-stu-id="8d1b0-112">Instead of explicitly specifying a type when you declare and initialize a variable, you can use the [var](../../../language-reference/keywords/var.md) modifier to instruct the compiler to infer and assign the type, as shown here:</span></span>

```csharp
var number = 5;
var name = "Virginia";
var query = from str in stringArray
            where str[0] == 'm'
            select str;
```

<span data-ttu-id="8d1b0-113">Proměnné deklarované jako `var` jsou stejně silně zadali jako proměnné, jejichž typ zadáte explicitně.</span><span class="sxs-lookup"><span data-stu-id="8d1b0-113">Variables declared as `var` are just as strongly-typed as variables whose type you specify explicitly.</span></span> <span data-ttu-id="8d1b0-114">Použití `var` umožňuje vytvářet anonymní typy, ale lze jej použít pouze pro místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="8d1b0-114">The use of `var` makes it possible to create anonymous types, but it can be used only for local variables.</span></span> <span data-ttu-id="8d1b0-115">Pole lze také deklarovat s implicitním psaním.</span><span class="sxs-lookup"><span data-stu-id="8d1b0-115">Arrays can also be declared with implicit typing.</span></span>

<span data-ttu-id="8d1b0-116">Další informace naleznete [v tématu Implicitně zadané místní proměnné](../../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="8d1b0-116">For more information, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>

## <a name="object-and-collection-initializers"></a><span data-ttu-id="8d1b0-117">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="8d1b0-117">Object and Collection Initializers</span></span>

<span data-ttu-id="8d1b0-118">Inicializátory objektu a kolekce umožňují inicializovat objekty bez explicitního volání konstruktoru pro objekt.</span><span class="sxs-lookup"><span data-stu-id="8d1b0-118">Object and collection initializers make it possible to initialize objects without explicitly calling a constructor for the object.</span></span> <span data-ttu-id="8d1b0-119">Inicializátory se obvykle používají ve výrazech dotazu při promítat zdrojová data do nového datového typu.</span><span class="sxs-lookup"><span data-stu-id="8d1b0-119">Initializers are typically used in query expressions when they project the source data into a new data type.</span></span> <span data-ttu-id="8d1b0-120">Za předpokladu, `Name` že `Phone` třída s názvem `Customer` public a vlastnosti, inicializátor objektu lze použít jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="8d1b0-120">Assuming a class named `Customer` with public `Name` and `Phone` properties, the object initializer can be used as in the following code:</span></span>

```csharp
var cust = new Customer { Name = "Mike", Phone = "555-1212" };
```

<span data-ttu-id="8d1b0-121">Pokračování s `Customer` naší třídy, předpokládejme, `IncomingOrders`že je zdroj dat s `OrderSize`názvem , a že `Customer` pro každou objednávku s velkým , bychom chtěli vytvořit nový na základě mimo tuto objednávku.</span><span class="sxs-lookup"><span data-stu-id="8d1b0-121">Continuing with our `Customer` class, assume that there is a data source called `IncomingOrders`, and that for each order with a large `OrderSize`, we would like to create a new `Customer` based off of that order.</span></span> <span data-ttu-id="8d1b0-122">Dotaz LINQ lze spustit na tomto zdroji dat a použít inicializaci objektu k vyplnění kolekce:</span><span class="sxs-lookup"><span data-stu-id="8d1b0-122">A LINQ query can be executed on this data source and use object initialization to fill a collection:</span></span>

```csharp
var newLargeOrderCustomers = from o in IncomingOrders
                            where o.OrderSize > 5
                            select new Customer { Name = o.Name, Phone = o.Phone };
```

<span data-ttu-id="8d1b0-123">Zdroj dat může mít více vlastností `Customer` ležících `OrderSize`pod kapotou než třída, například , ale s inicializací objektu jsou data vrácená z dotazu vylisována do požadovaného datového typu; vybíráme data, která jsou relevantní pro naši třídu.</span><span class="sxs-lookup"><span data-stu-id="8d1b0-123">The data source may have more properties lying under the hood than the `Customer` class such as `OrderSize`, but with object initialization, the data returned from the query is molded into the desired data type; we choose the data that is relevant to our class.</span></span> <span data-ttu-id="8d1b0-124">V důsledku toho máme `IEnumerable` nyní plné `Customer`nových s jsme chtěli.</span><span class="sxs-lookup"><span data-stu-id="8d1b0-124">As a result, we now have an `IEnumerable` filled with the new `Customer`s we wanted.</span></span> <span data-ttu-id="8d1b0-125">Výše uvedené lze také zapsat do syntaxe metody LINQ:</span><span class="sxs-lookup"><span data-stu-id="8d1b0-125">The above can also be written in LINQ's method syntax:</span></span>

```csharp
var newLargeOrderCustomers = IncomingOrders.Where(x => x.OrderSize > 5).Select(y => new Customer { Name = y.Name, Phone = y.Phone });
```

<span data-ttu-id="8d1b0-126">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="8d1b0-126">For more information, see:</span></span>

- [<span data-ttu-id="8d1b0-127">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="8d1b0-127">Object and Collection Initializers</span></span>](../../classes-and-structs/object-and-collection-initializers.md)

- [<span data-ttu-id="8d1b0-128">Syntaxe výrazu dotazu pro standardní operátory dotazu</span><span class="sxs-lookup"><span data-stu-id="8d1b0-128">Query Expression Syntax for Standard Query Operators</span></span>](./query-expression-syntax-for-standard-query-operators.md)

## <a name="anonymous-types"></a><span data-ttu-id="8d1b0-129">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="8d1b0-129">Anonymous Types</span></span>

<span data-ttu-id="8d1b0-130">Anonymní typ je vytvořen kompilátorem a název typu je k dispozici pouze kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="8d1b0-130">An anonymous type is constructed by the compiler and the type name is only available to the compiler.</span></span> <span data-ttu-id="8d1b0-131">Anonymní typy poskytují pohodlný způsob, jak dočasně seskupit sadu vlastností ve výsledku dotazu bez nutnosti definovat samostatný pojmenovaný typ.</span><span class="sxs-lookup"><span data-stu-id="8d1b0-131">Anonymous types provide a convenient way to group a set of properties temporarily in a query result without having to define a separate named type.</span></span> <span data-ttu-id="8d1b0-132">Anonymní typy jsou inicializovány s novým výrazem a inicializátorem objektu, jak je znázorněno zde:</span><span class="sxs-lookup"><span data-stu-id="8d1b0-132">Anonymous types are initialized with a new expression and an object initializer, as shown here:</span></span>

```csharp
select new {name = cust.Name, phone = cust.Phone};
```

<span data-ttu-id="8d1b0-133">Další informace naleznete [v tématu Anonymní typy](../../classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="8d1b0-133">For more information, see [Anonymous Types](../../classes-and-structs/anonymous-types.md).</span></span>

## <a name="extension-methods"></a><span data-ttu-id="8d1b0-134">Metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="8d1b0-134">Extension Methods</span></span>

<span data-ttu-id="8d1b0-135">Metoda rozšíření je statická metoda, která může být přidružena k typu, takže ji lze volat, jako by se jednalo o metodu instance u typu.</span><span class="sxs-lookup"><span data-stu-id="8d1b0-135">An extension method is a static method that can be associated with a type, so that it can be called as if it were an instance method on the type.</span></span> <span data-ttu-id="8d1b0-136">Tato funkce umožňuje, ve skutečnosti "přidat" nové metody stávajících typů bez jejich skutečné úpravy.</span><span class="sxs-lookup"><span data-stu-id="8d1b0-136">This feature enables you to, in effect, "add" new methods to existing types without actually modifying them.</span></span> <span data-ttu-id="8d1b0-137">Standardní operátory dotazu jsou sada rozšiřujících metod, které poskytují funkce <xref:System.Collections.Generic.IEnumerable%601>dotazu LINQ pro libovolný typ, který implementuje .</span><span class="sxs-lookup"><span data-stu-id="8d1b0-137">The standard query operators are a set of extension methods that provide LINQ query functionality for any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>

<span data-ttu-id="8d1b0-138">Další informace naleznete v [tématu Metody rozšíření](../../classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="8d1b0-138">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span>

## <a name="lambda-expressions"></a><span data-ttu-id="8d1b0-139">Lambda – výrazy</span><span class="sxs-lookup"><span data-stu-id="8d1b0-139">Lambda Expressions</span></span>

<span data-ttu-id="8d1b0-140">Výraz lambda je vložená funkce, která používá operátor => k oddělení vstupních parametrů z těla funkce a lze jej v době kompilace převést na delegáta nebo strom výrazů.</span><span class="sxs-lookup"><span data-stu-id="8d1b0-140">A lambda expression is an inline function that uses the => operator to separate input parameters from the function body and can be converted at compile time to a delegate or an expression tree.</span></span> <span data-ttu-id="8d1b0-141">V programování LINQ se setkáte s výrazy lambda při volání přímé metody pro operátory standardnídotaz.</span><span class="sxs-lookup"><span data-stu-id="8d1b0-141">In LINQ programming, you will encounter lambda expressions when you make direct method calls to the standard query operators.</span></span>

<span data-ttu-id="8d1b0-142">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="8d1b0-142">For more information, see:</span></span>

- [<span data-ttu-id="8d1b0-143">Anonymní funkce</span><span class="sxs-lookup"><span data-stu-id="8d1b0-143">Anonymous Functions</span></span>](../../statements-expressions-operators/anonymous-functions.md)

- [<span data-ttu-id="8d1b0-144">Lambda výrazy</span><span class="sxs-lookup"><span data-stu-id="8d1b0-144">Lambda Expressions</span></span>](../../statements-expressions-operators/lambda-expressions.md)

- [<span data-ttu-id="8d1b0-145">Stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="8d1b0-145">Expression Trees (C#)</span></span>](../expression-trees/index.md)

## <a name="see-also"></a><span data-ttu-id="8d1b0-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="8d1b0-146">See also</span></span>

- [<span data-ttu-id="8d1b0-147">Dotaz integrovaný jazykem (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="8d1b0-147">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
