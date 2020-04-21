---
title: Použití oborů názvů – programovací příručka jazyka C#
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: b4326be8c9e299a96477096ec21864ec69037abe
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738248"
---
# <a name="using-namespaces-c-programming-guide"></a><span data-ttu-id="698df-102">Použití oborů názvů (Programovací příručka Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="698df-102">Using namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="698df-103">Obory názvů jsou v rámci programů jazyka C# používány dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="698df-103">Namespaces are heavily used within C# programs in two ways.</span></span> <span data-ttu-id="698df-104">Za prvé, třídy rozhraní .NET Framework používají prostory názvů k uspořádání mnoha tříd.</span><span class="sxs-lookup"><span data-stu-id="698df-104">Firstly, the .NET Framework classes use namespaces to organize its many classes.</span></span> <span data-ttu-id="698df-105">Za druhé deklarování vlastní chodů názvů může pomoci řídit rozsah názvů tříd a metod ve větších programovacích projektech.</span><span class="sxs-lookup"><span data-stu-id="698df-105">Secondly, declaring your own namespaces can help control the scope of class and method names in larger programming projects.</span></span>  
  
## <a name="accessing-namespaces"></a><span data-ttu-id="698df-106">Přístup k oborům názvů</span><span class="sxs-lookup"><span data-stu-id="698df-106">Accessing namespaces</span></span>

 <span data-ttu-id="698df-107">Většina aplikací Jazyka C# `using` začíná částí direktiv.</span><span class="sxs-lookup"><span data-stu-id="698df-107">Most C# applications begin with a section of `using` directives.</span></span> <span data-ttu-id="698df-108">V této části jsou uvedeny obory názvů, které bude aplikace často používat, a programátor ovi ušetří zadání plně kvalifikovaného názvu při každém použití metody, která je obsažena v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="698df-108">This section lists the namespaces that the application will be using frequently, and saves the programmer from specifying a fully qualified name every time that a method that is contained within is used.</span></span>  
  
 <span data-ttu-id="698df-109">Například zahrnutím řádku:</span><span class="sxs-lookup"><span data-stu-id="698df-109">For example, by including the line:</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 <span data-ttu-id="698df-110">Na začátku programu může programátor použít kód:</span><span class="sxs-lookup"><span data-stu-id="698df-110">At the start of a program, the programmer can use the code:</span></span>  
  
 [!code-csharp[csProgGuide#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#31)]  
  
 <span data-ttu-id="698df-111">Namísto:</span><span class="sxs-lookup"><span data-stu-id="698df-111">Instead of:</span></span>  
  
 [!code-csharp[csProgGuide#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#30)]  
  
## <a name="namespace-aliases"></a><span data-ttu-id="698df-112">Aliasy oboru názvů</span><span class="sxs-lookup"><span data-stu-id="698df-112">Namespace aliases</span></span>

 <span data-ttu-id="698df-113">[ `using` Direktivu](../../language-reference/keywords/using-directive.md) můžete také použít k vytvoření aliasu pro obor názvů.</span><span class="sxs-lookup"><span data-stu-id="698df-113">You can also use the [`using` directive](../../language-reference/keywords/using-directive.md) to create an alias for a namespace.</span></span> <span data-ttu-id="698df-114">[Kvalifikátor `::` aliasu oboru názvů](../../language-reference/operators/namespace-alias-qualifier.md) použijte pro přístup k členům aliasového oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="698df-114">Use the [namespace alias qualifier `::`](../../language-reference/operators/namespace-alias-qualifier.md) to access the members of the aliased namespace.</span></span> <span data-ttu-id="698df-115">Následující příklad ukazuje, jak vytvořit a použít alias oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="698df-115">The following example shows how to create and use a namespace alias:</span></span>
  
[!code-csharp[csProgGuideNamespaces#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#5)]
  
## <a name="using-namespaces-to-control-scope"></a><span data-ttu-id="698df-116">Použití oborů názvů k řízení oboru</span><span class="sxs-lookup"><span data-stu-id="698df-116">Using namespaces to control scope</span></span>

 <span data-ttu-id="698df-117">Klíčové `namespace` slovo se používá k deklarování oboru.</span><span class="sxs-lookup"><span data-stu-id="698df-117">The `namespace` keyword is used to declare a scope.</span></span> <span data-ttu-id="698df-118">Možnost vytvářet obory v rámci projektu pomáhá organizovat kód a umožňuje vytvářet globálně jedinečné typy.</span><span class="sxs-lookup"><span data-stu-id="698df-118">The ability to create scopes within your project helps organize code and lets you create globally-unique types.</span></span> <span data-ttu-id="698df-119">V následujícím příkladu je `SampleClass` třída s názvem definována ve dvou oborech názvů, jeden vnořený uvnitř druhého.</span><span class="sxs-lookup"><span data-stu-id="698df-119">In the following example, a class titled `SampleClass` is defined in two namespaces, one nested inside the other.</span></span> <span data-ttu-id="698df-120">[ `.` Token](../../language-reference/operators/member-access-operators.md#member-access-expression-) se používá k rozlišení, která metoda se nazývá.</span><span class="sxs-lookup"><span data-stu-id="698df-120">The [`.` token](../../language-reference/operators/member-access-operators.md#member-access-expression-) is used to differentiate which method gets called.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#8)]  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="698df-121">Plně kvalifikované názvy</span><span class="sxs-lookup"><span data-stu-id="698df-121">Fully qualified names</span></span>

 <span data-ttu-id="698df-122">Obory názvů a typy mají jedinečné názvy popsané plně kvalifikovanými názvy, které označují logickou hierarchii.</span><span class="sxs-lookup"><span data-stu-id="698df-122">Namespaces and types have unique titles described by fully qualified names that indicate a logical hierarchy.</span></span> <span data-ttu-id="698df-123">Například příkaz `A.B` znamená, `A` že je název oboru názvů `B` nebo typu a je vnořen uvnitř něj.</span><span class="sxs-lookup"><span data-stu-id="698df-123">For example, the statement `A.B` implies that `A` is the name of the namespace or type, and `B` is nested inside it.</span></span>  
  
 <span data-ttu-id="698df-124">V následujícím příkladu jsou vnořené třídy a obory názvů.</span><span class="sxs-lookup"><span data-stu-id="698df-124">In the following example, there are nested classes and namespaces.</span></span> <span data-ttu-id="698df-125">Plně kvalifikovaný název je uveden jako komentář za každou entitou.</span><span class="sxs-lookup"><span data-stu-id="698df-125">The fully qualified name is indicated as a comment following each entity.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#9)]  
  
 <span data-ttu-id="698df-126">V předchozím segmentu kódu:</span><span class="sxs-lookup"><span data-stu-id="698df-126">In the previous code segment:</span></span>  
  
- <span data-ttu-id="698df-127">Obor názvů `N1` je členem globálního oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="698df-127">The namespace `N1` is a member of the global namespace.</span></span> <span data-ttu-id="698df-128">Jeho plně kvalifikovaný `N1`název je .</span><span class="sxs-lookup"><span data-stu-id="698df-128">Its fully qualified name is `N1`.</span></span>  
  
- <span data-ttu-id="698df-129">Obor názvů `N2` je členem `N1`společnosti .</span><span class="sxs-lookup"><span data-stu-id="698df-129">The namespace `N2` is a member of `N1`.</span></span> <span data-ttu-id="698df-130">Jeho plně kvalifikovaný `N1.N2`název je .</span><span class="sxs-lookup"><span data-stu-id="698df-130">Its fully qualified name is `N1.N2`.</span></span>  
  
- <span data-ttu-id="698df-131">Třída `C1` je členem `N1`.</span><span class="sxs-lookup"><span data-stu-id="698df-131">The class `C1` is a member of `N1`.</span></span> <span data-ttu-id="698df-132">Jeho plně kvalifikovaný `N1.C1`název je .</span><span class="sxs-lookup"><span data-stu-id="698df-132">Its fully qualified name is `N1.C1`.</span></span>  
  
- <span data-ttu-id="698df-133">Název `C2` třídy se používá dvakrát v tomto kódu.</span><span class="sxs-lookup"><span data-stu-id="698df-133">The class name `C2` is used two times in this code.</span></span> <span data-ttu-id="698df-134">Plně kvalifikované názvy jsou však jedinečné.</span><span class="sxs-lookup"><span data-stu-id="698df-134">However, the fully qualified names are unique.</span></span> <span data-ttu-id="698df-135">První instance `C2` je deklarována uvnitř `C1`; proto je jeho plně `N1.C1.C2`kvalifikovaný název: .</span><span class="sxs-lookup"><span data-stu-id="698df-135">The first instance of `C2` is declared inside `C1`; therefore, its fully qualified name is: `N1.C1.C2`.</span></span> <span data-ttu-id="698df-136">Druhá instance `C2` je deklarována uvnitř oboru názvů `N2`; proto je `N1.N2.C2`jeho plně kvalifikovaný název .</span><span class="sxs-lookup"><span data-stu-id="698df-136">The second instance of `C2` is declared inside a namespace `N2`; therefore, its fully qualified name is `N1.N2.C2`.</span></span>  
  
 <span data-ttu-id="698df-137">Pomocí předchozího segmentu kódu můžete do `C3`oboru `N1.N2` názvů přidat nového člena třídy:</span><span class="sxs-lookup"><span data-stu-id="698df-137">Using the previous code segment, you can add a new class member, `C3`, to the namespace `N1.N2` as follows:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#10)]  
  
 <span data-ttu-id="698df-138">Obecně použijte [kvalifikátor `::` aliasu oboru názvů](../../language-reference/operators/namespace-alias-qualifier.md) k odkazování na `.` alias oboru názvů nebo `global::` k odkazování na globální obor názvů a ke kvalifikaci typů nebo členů.</span><span class="sxs-lookup"><span data-stu-id="698df-138">In general, use the [namespace alias qualifier `::`](../../language-reference/operators/namespace-alias-qualifier.md) to reference a namespace alias or `global::` to reference the global namespace and `.` to qualify types or members.</span></span>  
  
 <span data-ttu-id="698df-139">Je chyba použít `::` s alias, který odkazuje na typ namísto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="698df-139">It is an error to use `::` with an alias that references a type instead of a namespace.</span></span> <span data-ttu-id="698df-140">Příklad:</span><span class="sxs-lookup"><span data-stu-id="698df-140">For example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#11)]  
  
 [!code-csharp[csProgGuideNamespaces#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#12)]  
  
 <span data-ttu-id="698df-141">Nezapomeňte, že `global` slovo není předdefinovaný alias; `global.X` proto nemá žádný zvláštní význam.</span><span class="sxs-lookup"><span data-stu-id="698df-141">Remember that the word `global` is not a predefined alias; therefore, `global.X` does not have any special meaning.</span></span> <span data-ttu-id="698df-142">Zvláštní význam získává pouze v případě, `::`že se používá s .</span><span class="sxs-lookup"><span data-stu-id="698df-142">It acquires a special meaning only when it is used with `::`.</span></span>  
  
 <span data-ttu-id="698df-143">Upozornění kompilátoru CS0440 je generováno, `global::` pokud definujete alias s názvem global, protože vždy odkazuje na globální obor názvů a nikoli na alias.</span><span class="sxs-lookup"><span data-stu-id="698df-143">Compiler warning CS0440 is generated if you define an alias named global because `global::` always references the global namespace and not an alias.</span></span> <span data-ttu-id="698df-144">Například následující řádek generuje upozornění:</span><span class="sxs-lookup"><span data-stu-id="698df-144">For example, the following line generates the warning:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#13)]  
  
 <span data-ttu-id="698df-145">Použití `::` s aliasy je dobrý nápad a chrání před neočekávaným zavedením dalších typů.</span><span class="sxs-lookup"><span data-stu-id="698df-145">Using `::` with aliases is a good idea and protects against the unexpected introduction of additional types.</span></span> <span data-ttu-id="698df-146">Zvažte například tento příklad:</span><span class="sxs-lookup"><span data-stu-id="698df-146">For example, consider this example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#14)]  
  
 [!code-csharp[csProgGuideNamespaces#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#15)]  
  
 <span data-ttu-id="698df-147">To funguje, ale pokud `Alias` typ s názvem byly `Alias.` následně zavedeny, by se vázat na tento typ místo.</span><span class="sxs-lookup"><span data-stu-id="698df-147">This works, but if a type named `Alias` were to subsequently be introduced, `Alias.` would bind to that type instead.</span></span> <span data-ttu-id="698df-148">Použití `Alias::Exception` zajišťuje, `Alias` že je považován za alias oboru názvů a není zaměněn za typ.</span><span class="sxs-lookup"><span data-stu-id="698df-148">Using `Alias::Exception` ensures that `Alias` is treated as a namespace alias and not mistaken for a type.</span></span>  

## <a name="see-also"></a><span data-ttu-id="698df-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="698df-149">See also</span></span>

- [<span data-ttu-id="698df-150">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="698df-150">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="698df-151">Jmenné prostory</span><span class="sxs-lookup"><span data-stu-id="698df-151">Namespaces</span></span>](./index.md)
- [<span data-ttu-id="698df-152">Výraz přístupu člena</span><span class="sxs-lookup"><span data-stu-id="698df-152">Member access expression</span></span>](../../language-reference/operators/member-access-operators.md#member-access-expression-)
- [<span data-ttu-id="698df-153">:: – operátor</span><span class="sxs-lookup"><span data-stu-id="698df-153">:: operator</span></span>](../../language-reference/operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="698df-154">externí alias</span><span class="sxs-lookup"><span data-stu-id="698df-154">extern alias</span></span>](../../language-reference/keywords/extern-alias.md)
