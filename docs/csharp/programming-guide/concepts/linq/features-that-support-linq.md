---
title: "Funkce C# podporující LINQ"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2f5accb188e54e0d3e2b941832637ec33afc26b2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="c-features-that-support-linq"></a><span data-ttu-id="d1bbd-102">Funkce C# podporující LINQ</span><span class="sxs-lookup"><span data-stu-id="d1bbd-102">C# Features That Support LINQ</span></span>
<span data-ttu-id="d1bbd-103">Následující části jsou popsány nové jazykové konstrukty byla zavedená v C# 3.0.</span><span class="sxs-lookup"><span data-stu-id="d1bbd-103">The following section introduces new language constructs introduced in C# 3.0.</span></span> <span data-ttu-id="d1bbd-104">I když tyto nové funkce jsou používány pro určitý stupeň s [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy, nejsou omezeny na [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] a lze použít v libovolném kontextu, kde můžete najít je užitečné.</span><span class="sxs-lookup"><span data-stu-id="d1bbd-104">Although these new features are all used to a degree with [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, they are not limited to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] and can be used in any context where you find them useful.</span></span>  
  
## <a name="query-expressions"></a><span data-ttu-id="d1bbd-105">Výrazy dotazu</span><span class="sxs-lookup"><span data-stu-id="d1bbd-105">Query Expressions</span></span>  
 <span data-ttu-id="d1bbd-106">Výrazy dotazů použít deklarativní syntaxi SQL nebo XQuery dotazu přes rozhraní IEnumerable kolekce.</span><span class="sxs-lookup"><span data-stu-id="d1bbd-106">Queries expressions use a declarative syntax similar to SQL or XQuery to query over IEnumerable collections.</span></span> <span data-ttu-id="d1bbd-107">Při kompilování čas syntaxe dotazu je převedeno na volání metody [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] poskytovatele implementace metod rozšíření operátor standardní dotazu.</span><span class="sxs-lookup"><span data-stu-id="d1bbd-107">At compile time query syntax is converted to method calls to a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provider's implementation of the standard query operator extension methods.</span></span> <span data-ttu-id="d1bbd-108">Operátory standardní dotazu, které jsou v oboru tak, že zadáte odpovídající oboru názvů s řízení aplikací `using` – direktiva.</span><span class="sxs-lookup"><span data-stu-id="d1bbd-108">Applications control the standard query operators that are in scope by specifying the appropriate namespace with a `using` directive.</span></span> <span data-ttu-id="d1bbd-109">Následující výraz dotazu přijímá pole řetězce, je skupin podle prvního znaku v řetězci a řadí do skupin.</span><span class="sxs-lookup"><span data-stu-id="d1bbd-109">The following query expression takes an array of strings, groups them according to the first character in the string, and orders the groups.</span></span>  
  
```  
var query = from str in stringArray  
            group str by str[0] into stringGroup  
            orderby stringGroup.Key  
            select stringGroup;  
```  
  
 <span data-ttu-id="d1bbd-110">Další informace najdete v tématu [LINQ – výrazy dotazů](../../../../csharp/programming-guide/linq-query-expressions/index.md).</span><span class="sxs-lookup"><span data-stu-id="d1bbd-110">For more information, see [LINQ Query Expressions](../../../../csharp/programming-guide/linq-query-expressions/index.md).</span></span>  
  
## <a name="implicitly-typed-variables-var"></a><span data-ttu-id="d1bbd-111">Implicitně typované proměnné (var)</span><span class="sxs-lookup"><span data-stu-id="d1bbd-111">Implicitly Typed Variables (var)</span></span>  
 <span data-ttu-id="d1bbd-112">Namísto explicitním zadáním typu, pokud deklarace a inicializace proměnné, můžete použít [var](../../../../csharp/language-reference/keywords/var.md) modifikátor na pokyn kompilátoru odvození a přiřadit typu, jak je vidět tady:</span><span class="sxs-lookup"><span data-stu-id="d1bbd-112">Instead of explicitly specifying a type when you declare and initialize a variable, you can use the [var](../../../../csharp/language-reference/keywords/var.md) modifier to instruct the compiler to infer and assign the type, as shown here:</span></span>  
  
```  
var number = 5;  
var name = "Virginia";  
var query = from str in stringArray  
            where str[0] == 'm'  
            select str;  
```  
  
 <span data-ttu-id="d1bbd-113">Proměnných deklarovaných jako `var` jsou, stejně jako silného typu jako proměnné s typem explicitně zadáte.</span><span class="sxs-lookup"><span data-stu-id="d1bbd-113">Variables declared as `var` are just as strongly-typed as variables whose type you specify explicitly.</span></span> <span data-ttu-id="d1bbd-114">Použití `var` díky je možné vytvořit anonymní typy, ale lze použít pro všechny místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="d1bbd-114">The use of `var` makes it possible to create anonymous types, but it can be used for any local variable.</span></span> <span data-ttu-id="d1bbd-115">Pole lze také deklarovat s implicitní zadáním.</span><span class="sxs-lookup"><span data-stu-id="d1bbd-115">Arrays can also be declared with implicit typing.</span></span>  
  
 <span data-ttu-id="d1bbd-116">Další informace najdete v tématu [implicitně typované lokální proměnné](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="d1bbd-116">For more information, see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
## <a name="object-and-collection-initializers"></a><span data-ttu-id="d1bbd-117">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="d1bbd-117">Object and Collection Initializers</span></span>  
 <span data-ttu-id="d1bbd-118">Inicializátory objektu a kolekce umožňují inicializovat objekty bez nutnosti explicitně volání konstruktoru objektu.</span><span class="sxs-lookup"><span data-stu-id="d1bbd-118">Object and collection initializers make it possible to initialize objects without explicitly calling a constructor for the object.</span></span> <span data-ttu-id="d1bbd-119">Inicializátory jsou obvykle používány ve výrazech dotazů, když se projektu zdrojová data do nového datového typu.</span><span class="sxs-lookup"><span data-stu-id="d1bbd-119">Initializers are typically used in query expressions when they project the source data into a new data type.</span></span> <span data-ttu-id="d1bbd-120">Za předpokladu, že třídy s názvem `Customer` s veřejnou `Name` a `Phone` vlastnosti, inicializátoru objektu lze použít jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="d1bbd-120">Assuming a class named `Customer` with public `Name` and `Phone` properties, the object initializer can be used as in the following code:</span></span>  
  
```  
Customer cust = new Customer { Name = "Mike", Phone = "555-1212" };  
```  
  
 <span data-ttu-id="d1bbd-121">Další informace najdete v tématu [inicializátory objektu a kolekce](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="d1bbd-121">For more information, see [Object and Collection Initializers](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
## <a name="anonymous-types"></a><span data-ttu-id="d1bbd-122">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="d1bbd-122">Anonymous Types</span></span>  
 <span data-ttu-id="d1bbd-123">Anonymní typ je vytvořený pomocí kompilátoru a je k dispozici pro kompilátor pouze název typu.</span><span class="sxs-lookup"><span data-stu-id="d1bbd-123">An anonymous type is constructed by the compiler and the type name is only available to the compiler.</span></span> <span data-ttu-id="d1bbd-124">Anonymní typy poskytnout vhodný způsob k seskupení sady vlastností dočasně ve výsledku dotazu bez nutnosti definovat samostatné pojmenovaného typu.</span><span class="sxs-lookup"><span data-stu-id="d1bbd-124">Anonymous types provide a convenient way to group a set of properties temporarily in a query result without having to define a separate named type.</span></span> <span data-ttu-id="d1bbd-125">Anonymní typy jsou inicializovány s nový výraz a inicializátoru objektu, jak je vidět tady:</span><span class="sxs-lookup"><span data-stu-id="d1bbd-125">Anonymous types are initialized with a new expression and an object initializer, as shown here:</span></span>  
  
```  
select new {name = cust.Name, phone = cust.Phone};  
```  
  
 <span data-ttu-id="d1bbd-126">Další informace najdete v tématu [anonymní typy](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="d1bbd-126">For more information, see [Anonymous Types](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
## <a name="extension-methods"></a><span data-ttu-id="d1bbd-127">Metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="d1bbd-127">Extension Methods</span></span>  
 <span data-ttu-id="d1bbd-128">Metody rozšíření je statickou metodu, která může být přidružený k typu, takže může být volána, jako by šlo metodu instance typu.</span><span class="sxs-lookup"><span data-stu-id="d1bbd-128">An extension method is a static method that can be associated with a type, so that it can be called as if it were an instance method on the type.</span></span> <span data-ttu-id="d1bbd-129">Tato funkce umožňuje, v důsledku toho "Přidat" nové metody k existujícím typům beze změny je ve skutečnosti.</span><span class="sxs-lookup"><span data-stu-id="d1bbd-129">This feature enables you to, in effect, "add" new methods to existing types without actually modifying them.</span></span> <span data-ttu-id="d1bbd-130">Standardní operátory dotazu jsou sady rozšiřující metody, které poskytují [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz funkce pro žádný typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="d1bbd-130">The standard query operators are a set of extension methods that provide [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query functionality for any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="d1bbd-131">Další informace najdete v tématu [rozšiřující metody](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="d1bbd-131">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>  
  
## <a name="lambda-expressions"></a><span data-ttu-id="d1bbd-132">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="d1bbd-132">Lambda Expressions</span></span>  
 <span data-ttu-id="d1bbd-133">Výraz lambda je vložená funkce, která používá = > – operátor k oddělení vstupní parametry z tělo funkce a může být převedena v době kompilace delegáta nebo strom výrazu se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="d1bbd-133">A lambda expression is an inline function that uses the => operator to separate input parameters from the function body and can be converted at compile time to a delegate or an expression tree.</span></span> <span data-ttu-id="d1bbd-134">V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] programování, můžete narazit výrazy lambda při provedete přímá metoda volání standardní operátory dotazu.</span><span class="sxs-lookup"><span data-stu-id="d1bbd-134">In [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] programming, you will encounter lambda expressions when you make direct method calls to the standard query operators.</span></span>  
  
 <span data-ttu-id="d1bbd-135">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="d1bbd-135">For more information, see:</span></span>  
  
-   [<span data-ttu-id="d1bbd-136">Anonymní funkce</span><span class="sxs-lookup"><span data-stu-id="d1bbd-136">Anonymous Functions</span></span>](../../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)  
  
-   [<span data-ttu-id="d1bbd-137">Lambda – výrazy</span><span class="sxs-lookup"><span data-stu-id="d1bbd-137">Lambda Expressions</span></span>](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
  
-   [<span data-ttu-id="d1bbd-138">Stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="d1bbd-138">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
  
## <a name="auto-implemented-properties"></a><span data-ttu-id="d1bbd-139">Automaticky implementované vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d1bbd-139">Auto-Implemented Properties</span></span>  
 <span data-ttu-id="d1bbd-140">Automaticky implementované vlastnosti zkontrolujte přesnější deklarace vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d1bbd-140">Auto-implemented properties make property-declaration more concise.</span></span> <span data-ttu-id="d1bbd-141">Pokud vlastnost deklarovat, jak je znázorněno v následujícím příkladu, bude vytvořen privátní, anonymní základní pole, které není přístupná kromě prostřednictvím vlastnost getter a setter.</span><span class="sxs-lookup"><span data-stu-id="d1bbd-141">When you declare a property as shown in the following example, the compiler will create a private, anonymous backing field that is not accessible except through the property getter and setter.</span></span>  
  
```  
public string Name {get; set;}  
```  
  
 <span data-ttu-id="d1bbd-142">Další informace najdete v tématu [Auto-Implemented vlastnosti](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="d1bbd-142">For more information, see [Auto-Implemented Properties](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1bbd-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1bbd-143">See Also</span></span>  
 [<span data-ttu-id="d1bbd-144">Language-Integrated Query (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d1bbd-144">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)
