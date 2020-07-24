---
title: Funkce C# podporující LINQ
description: Přečtěte si o funkcích jazyka C# pro použití s dotazy LINQ a v jiných kontextech. Tyto jazykové konstrukce byly představeny v C# 3,0.
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: f72b82180d794086dcea9f11a7a057dc26ab0b26
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105423"
---
# <a name="c-features-that-support-linq"></a><span data-ttu-id="75d7e-104">Funkce C# podporující LINQ</span><span class="sxs-lookup"><span data-stu-id="75d7e-104">C# Features That Support LINQ</span></span>

<span data-ttu-id="75d7e-105">V následující části jsou představeny nové jazykové konstrukce představené v C# 3,0.</span><span class="sxs-lookup"><span data-stu-id="75d7e-105">The following section introduces new language constructs introduced in C# 3.0.</span></span> <span data-ttu-id="75d7e-106">I když jsou tyto nové funkce použity ve stupních s dotazy LINQ, nejsou omezeny na LINQ a je možné je použít v jakémkoli kontextu, kde je najdete užitečné.</span><span class="sxs-lookup"><span data-stu-id="75d7e-106">Although these new features are all used to a degree with LINQ queries, they are not limited to LINQ and can be used in any context where you find them useful.</span></span>

## <a name="query-expressions"></a><span data-ttu-id="75d7e-107">Výrazy dotazu</span><span class="sxs-lookup"><span data-stu-id="75d7e-107">Query Expressions</span></span>

<span data-ttu-id="75d7e-108">Výrazy dotazů používají deklarativní syntaxi podobnou syntaxi SQL nebo XQuery pro dotazování přes kolekce IEnumerable.</span><span class="sxs-lookup"><span data-stu-id="75d7e-108">Query expressions use a declarative syntax similar to SQL or XQuery to query over IEnumerable collections.</span></span> <span data-ttu-id="75d7e-109">Syntaxe dotazu v čase kompilace je převedena na volání metody do implementace metod rozšíření standardních operátorů dotazu poskytovatele LINQ.</span><span class="sxs-lookup"><span data-stu-id="75d7e-109">At compile time query syntax is converted to method calls to a LINQ provider's implementation of the standard query operator extension methods.</span></span> <span data-ttu-id="75d7e-110">Aplikace řídí standardní operátory dotazů, které jsou v oboru, zadáním příslušného oboru názvů s `using` direktivou.</span><span class="sxs-lookup"><span data-stu-id="75d7e-110">Applications control the standard query operators that are in scope by specifying the appropriate namespace with a `using` directive.</span></span> <span data-ttu-id="75d7e-111">Následující výraz dotazu přebírá pole řetězců, seskupuje je podle prvního znaku v řetězci a řadí skupiny.</span><span class="sxs-lookup"><span data-stu-id="75d7e-111">The following query expression takes an array of strings, groups them according to the first character in the string, and orders the groups.</span></span>

```csharp
var query = from str in stringArray
            group str by str[0] into stringGroup
            orderby stringGroup.Key
            select stringGroup;
```

<span data-ttu-id="75d7e-112">Další informace najdete v tématu [výrazy dotazů LINQ](../../../linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="75d7e-112">For more information, see [LINQ Query Expressions](../../../linq/index.md).</span></span>

## <a name="implicitly-typed-variables-var"></a><span data-ttu-id="75d7e-113">Implicitně typované proměnné (var)</span><span class="sxs-lookup"><span data-stu-id="75d7e-113">Implicitly Typed Variables (var)</span></span>

<span data-ttu-id="75d7e-114">Namísto explicitního určení typu při deklaraci a inicializaci proměnné lze použít modifikátor [var](../../../language-reference/keywords/var.md) k tomu, aby kompilátor mohl odvodit a přiřadit typ, jak je znázorněno zde:</span><span class="sxs-lookup"><span data-stu-id="75d7e-114">Instead of explicitly specifying a type when you declare and initialize a variable, you can use the [var](../../../language-reference/keywords/var.md) modifier to instruct the compiler to infer and assign the type, as shown here:</span></span>

```csharp
var number = 5;
var name = "Virginia";
var query = from str in stringArray
            where str[0] == 'm'
            select str;
```

<span data-ttu-id="75d7e-115">Proměnné deklarované jako `var` jsou pouze silně typované jako proměnné, jejichž typ zadáte explicitně.</span><span class="sxs-lookup"><span data-stu-id="75d7e-115">Variables declared as `var` are just as strongly typed as variables whose type you specify explicitly.</span></span> <span data-ttu-id="75d7e-116">Použití je `var` možné vytvořit anonymní typy, ale lze je použít pouze pro místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="75d7e-116">The use of `var` makes it possible to create anonymous types, but it can be used only for local variables.</span></span> <span data-ttu-id="75d7e-117">Pole lze také deklarovat pomocí implicitního zadání.</span><span class="sxs-lookup"><span data-stu-id="75d7e-117">Arrays can also be declared with implicit typing.</span></span>

<span data-ttu-id="75d7e-118">Další informace naleznete v tématu [implicitně typované lokální proměnné](../../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="75d7e-118">For more information, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>

## <a name="object-and-collection-initializers"></a><span data-ttu-id="75d7e-119">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="75d7e-119">Object and Collection Initializers</span></span>

<span data-ttu-id="75d7e-120">Inicializátory objektů a kolekcí umožňují inicializovat objekty bez explicitního volání konstruktoru objektu.</span><span class="sxs-lookup"><span data-stu-id="75d7e-120">Object and collection initializers make it possible to initialize objects without explicitly calling a constructor for the object.</span></span> <span data-ttu-id="75d7e-121">Inicializátory se obvykle používají ve výrazech dotazů při projektování zdrojových dat do nového datového typu.</span><span class="sxs-lookup"><span data-stu-id="75d7e-121">Initializers are typically used in query expressions when they project the source data into a new data type.</span></span> <span data-ttu-id="75d7e-122">Za předpokladu, že třída s názvem `Customer` Public `Name` a `Phone` Properties, může být inicializátor objektu použit jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="75d7e-122">Assuming a class named `Customer` with public `Name` and `Phone` properties, the object initializer can be used as in the following code:</span></span>

```csharp
var cust = new Customer { Name = "Mike", Phone = "555-1212" };
```

<span data-ttu-id="75d7e-123">V případě pokračování v naší `Customer` třídě se předpokládá, že je k dispozici zdroj dat `IncomingOrders` s názvem a že pro každou objednávku má velký `OrderSize` , chtěli bychom vytvořit nové `Customer` založené na tomto pořadí.</span><span class="sxs-lookup"><span data-stu-id="75d7e-123">Continuing with our `Customer` class, assume that there is a data source called `IncomingOrders`, and that for each order with a large `OrderSize`, we would like to create a new `Customer` based off of that order.</span></span> <span data-ttu-id="75d7e-124">V tomto zdroji dat lze spustit dotaz LINQ a k vyplnění kolekce použít inicializaci objektu:</span><span class="sxs-lookup"><span data-stu-id="75d7e-124">A LINQ query can be executed on this data source and use object initialization to fill a collection:</span></span>

```csharp
var newLargeOrderCustomers = from o in IncomingOrders
                            where o.OrderSize > 5
                            select new Customer { Name = o.Name, Phone = o.Phone };
```

<span data-ttu-id="75d7e-125">Zdroj dat může mít více vlastností ležící pod digestoří, než je `Customer` třída, jako `OrderSize` je například, ale s inicializací objektu, data vrácená z dotazu jsou molded na požadovaný datový typ. vybíráme data, která jsou relevantní pro naši třídu.</span><span class="sxs-lookup"><span data-stu-id="75d7e-125">The data source may have more properties lying under the hood than the `Customer` class such as `OrderSize`, but with object initialization, the data returned from the query is molded into the desired data type; we choose the data that is relevant to our class.</span></span> <span data-ttu-id="75d7e-126">V důsledku toho jsme teď `IEnumerable` naplnili nové s, které `Customer` jsme chtěli.</span><span class="sxs-lookup"><span data-stu-id="75d7e-126">As a result, we now have an `IEnumerable` filled with the new `Customer`s we wanted.</span></span> <span data-ttu-id="75d7e-127">Výše uvedený postup lze také zapsat v syntaxi metody LINQ:</span><span class="sxs-lookup"><span data-stu-id="75d7e-127">The above can also be written in LINQ's method syntax:</span></span>

```csharp
var newLargeOrderCustomers = IncomingOrders.Where(x => x.OrderSize > 5).Select(y => new Customer { Name = y.Name, Phone = y.Phone });
```

<span data-ttu-id="75d7e-128">Další informace najdete tady:</span><span class="sxs-lookup"><span data-stu-id="75d7e-128">For more information, see:</span></span>

- [<span data-ttu-id="75d7e-129">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="75d7e-129">Object and Collection Initializers</span></span>](../../classes-and-structs/object-and-collection-initializers.md)

- [<span data-ttu-id="75d7e-130">Syntaxe výrazu dotazu pro standardní operátory dotazu</span><span class="sxs-lookup"><span data-stu-id="75d7e-130">Query Expression Syntax for Standard Query Operators</span></span>](./query-expression-syntax-for-standard-query-operators.md)

## <a name="anonymous-types"></a><span data-ttu-id="75d7e-131">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="75d7e-131">Anonymous Types</span></span>

<span data-ttu-id="75d7e-132">Anonymní typ je vytvořen kompilátorem a název typu je k dispozici pouze pro kompilátor.</span><span class="sxs-lookup"><span data-stu-id="75d7e-132">An anonymous type is constructed by the compiler and the type name is only available to the compiler.</span></span> <span data-ttu-id="75d7e-133">Anonymní typy poskytují pohodlný způsob, jak dočasně seskupit sadu vlastností do výsledku dotazu bez nutnosti definovat samostatný pojmenovaný typ.</span><span class="sxs-lookup"><span data-stu-id="75d7e-133">Anonymous types provide a convenient way to group a set of properties temporarily in a query result without having to define a separate named type.</span></span> <span data-ttu-id="75d7e-134">Anonymní typy jsou inicializovány s novým výrazem a inicializátorem objektu, jak je znázorněno zde:</span><span class="sxs-lookup"><span data-stu-id="75d7e-134">Anonymous types are initialized with a new expression and an object initializer, as shown here:</span></span>

```csharp
select new {name = cust.Name, phone = cust.Phone};
```

<span data-ttu-id="75d7e-135">Další informace najdete v tématu [anonymní typy](../../classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="75d7e-135">For more information, see [Anonymous Types](../../classes-and-structs/anonymous-types.md).</span></span>

## <a name="extension-methods"></a><span data-ttu-id="75d7e-136">Metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="75d7e-136">Extension Methods</span></span>

<span data-ttu-id="75d7e-137">Rozšiřující metoda je statická metoda, která může být přidružena k typu, aby mohla být volána jako metoda instance typu.</span><span class="sxs-lookup"><span data-stu-id="75d7e-137">An extension method is a static method that can be associated with a type, so that it can be called as if it were an instance method on the type.</span></span> <span data-ttu-id="75d7e-138">Tato funkce umožňuje přidat nové metody do stávajících typů, aniž by bylo nutné je skutečně upravovat.</span><span class="sxs-lookup"><span data-stu-id="75d7e-138">This feature enables you to, in effect, "add" new methods to existing types without actually modifying them.</span></span> <span data-ttu-id="75d7e-139">Standardní operátory dotazu jsou sada rozšiřujících metod, které poskytují funkce dotazů LINQ pro jakýkoli typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="75d7e-139">The standard query operators are a set of extension methods that provide LINQ query functionality for any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>

<span data-ttu-id="75d7e-140">Další informace naleznete v tématu [metody rozšíření](../../classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="75d7e-140">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span>

## <a name="lambda-expressions"></a><span data-ttu-id="75d7e-141">Lambda – výrazy</span><span class="sxs-lookup"><span data-stu-id="75d7e-141">Lambda Expressions</span></span>

<span data-ttu-id="75d7e-142">Výraz lambda je vložená funkce, která používá operátor => pro oddělení vstupních parametrů z těla funkce a může být převedena v době kompilace na delegáta nebo strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="75d7e-142">A lambda expression is an inline function that uses the => operator to separate input parameters from the function body and can be converted at compile time to a delegate or an expression tree.</span></span> <span data-ttu-id="75d7e-143">V programování LINQ dojde k vyvolání výrazů lambda při přímém volání metody do standardních operátorů dotazu.</span><span class="sxs-lookup"><span data-stu-id="75d7e-143">In LINQ programming, you will encounter lambda expressions when you make direct method calls to the standard query operators.</span></span>

<span data-ttu-id="75d7e-144">Další informace najdete tady:</span><span class="sxs-lookup"><span data-stu-id="75d7e-144">For more information, see:</span></span>

- [<span data-ttu-id="75d7e-145">Anonymní funkce</span><span class="sxs-lookup"><span data-stu-id="75d7e-145">Anonymous Functions</span></span>](../../statements-expressions-operators/anonymous-functions.md)

- [<span data-ttu-id="75d7e-146">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="75d7e-146">Lambda Expressions</span></span>](../../statements-expressions-operators/lambda-expressions.md)

- [<span data-ttu-id="75d7e-147">Stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="75d7e-147">Expression Trees (C#)</span></span>](../expression-trees/index.md)

## <a name="see-also"></a><span data-ttu-id="75d7e-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="75d7e-148">See also</span></span>

- [<span data-ttu-id="75d7e-149">LINQ (Language-Integrated Query) (C#)</span><span class="sxs-lookup"><span data-stu-id="75d7e-149">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
