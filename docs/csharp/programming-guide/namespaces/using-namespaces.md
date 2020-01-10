---
title: Používání oborů názvů C# – Průvodce programováním
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: 5193fc7aaae83cbc0c75e81835244eaaaece69a5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75700195"
---
# <a name="using-namespaces-c-programming-guide"></a><span data-ttu-id="2e26b-102">Používání oborů názvůC# (Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="2e26b-102">Using namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="2e26b-103">Obory názvů jsou v C# rámci programů silně používány dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="2e26b-103">Namespaces are heavily used within C# programs in two ways.</span></span> <span data-ttu-id="2e26b-104">Nejprve třídy .NET Framework používají obory názvů k uspořádání svých mnoha tříd.</span><span class="sxs-lookup"><span data-stu-id="2e26b-104">Firstly, the .NET Framework classes use namespaces to organize its many classes.</span></span> <span data-ttu-id="2e26b-105">Následně deklarace vlastních oborů názvů vám může pomáhat řídit obor názvů tříd a metod ve větších programovacích projektech.</span><span class="sxs-lookup"><span data-stu-id="2e26b-105">Secondly, declaring your own namespaces can help control the scope of class and method names in larger programming projects.</span></span>  
  
## <a name="accessing-namespaces"></a><span data-ttu-id="2e26b-106">Přístup k oborům názvů</span><span class="sxs-lookup"><span data-stu-id="2e26b-106">Accessing namespaces</span></span>

 <span data-ttu-id="2e26b-107">Většina C# aplikací začíná oddílem direktiv `using`.</span><span class="sxs-lookup"><span data-stu-id="2e26b-107">Most C# applications begin with a section of `using` directives.</span></span> <span data-ttu-id="2e26b-108">V této části jsou uvedeny obory názvů, které aplikace často používá, a uloží programátora z určení plně kvalifikovaného názvu pokaždé, když se použije metoda, která je obsažena v rámci.</span><span class="sxs-lookup"><span data-stu-id="2e26b-108">This section lists the namespaces that the application will be using frequently, and saves the programmer from specifying a fully qualified name every time that a method that is contained within is used.</span></span>  
  
 <span data-ttu-id="2e26b-109">Například zahrnutím řádku:</span><span class="sxs-lookup"><span data-stu-id="2e26b-109">For example, by including the line:</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 <span data-ttu-id="2e26b-110">Na začátku programu může programátor použít kód:</span><span class="sxs-lookup"><span data-stu-id="2e26b-110">At the start of a program, the programmer can use the code:</span></span>  
  
 [!code-csharp[csProgGuide#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#31)]  
  
 <span data-ttu-id="2e26b-111">Namísto:</span><span class="sxs-lookup"><span data-stu-id="2e26b-111">Instead of:</span></span>  
  
 [!code-csharp[csProgGuide#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#30)]  
  
## <a name="namespace-aliases"></a><span data-ttu-id="2e26b-112">Aliasy oboru názvů</span><span class="sxs-lookup"><span data-stu-id="2e26b-112">Namespace aliases</span></span>

 <span data-ttu-id="2e26b-113">Můžete také použít [direktivu`using`](../../language-reference/keywords/using-directive.md) pro vytvoření aliasu pro obor názvů.</span><span class="sxs-lookup"><span data-stu-id="2e26b-113">You also can use the [`using` directive](../../language-reference/keywords/using-directive.md) to create an alias for a namespace.</span></span> <span data-ttu-id="2e26b-114">Pro přístup ke členům oboru názvů s aliasy použijte [kvalifikátor aliasu oboru názvů `::`](../../language-reference/operators/namespace-alias-qualifier.md) .</span><span class="sxs-lookup"><span data-stu-id="2e26b-114">Use the [namespace alias qualifier `::`](../../language-reference/operators/namespace-alias-qualifier.md) to access the members of the aliased namespace.</span></span> <span data-ttu-id="2e26b-115">Následující příklad ukazuje, jak vytvořit a použít alias oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="2e26b-115">The following example shows how to create and use a namespace alias:</span></span>
  
[!code-csharp[csProgGuideNamespaces#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#5)]
  
## <a name="using-namespaces-to-control-scope"></a><span data-ttu-id="2e26b-116">Použití oborů názvů k řízení oboru</span><span class="sxs-lookup"><span data-stu-id="2e26b-116">Using namespaces to control scope</span></span>

 <span data-ttu-id="2e26b-117">Klíčové slovo `namespace` slouží k deklaraci oboru.</span><span class="sxs-lookup"><span data-stu-id="2e26b-117">The `namespace` keyword is used to declare a scope.</span></span> <span data-ttu-id="2e26b-118">Schopnost vytvářet obory v rámci projektu pomáhá organizovat kód a umožňuje vytvářet globálně jedinečné typy.</span><span class="sxs-lookup"><span data-stu-id="2e26b-118">The ability to create scopes within your project helps organize code and lets you create globally-unique types.</span></span> <span data-ttu-id="2e26b-119">V následujícím příkladu je třída s názvem `SampleClass` definovaná ve dvou oborech názvů, jedna vnořená uvnitř druhé.</span><span class="sxs-lookup"><span data-stu-id="2e26b-119">In the following example, a class titled `SampleClass` is defined in two namespaces, one nested inside the other.</span></span> <span data-ttu-id="2e26b-120">[Operátor přístupu členů `.`](../../language-reference/operators/member-access-operators.md#member-access-operator-) slouží k odlišení, která metoda se volá.</span><span class="sxs-lookup"><span data-stu-id="2e26b-120">The [member access `.` operator](../../language-reference/operators/member-access-operators.md#member-access-operator-) is used to differentiate which method gets called.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#8)]  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="2e26b-121">Plně kvalifikované názvy</span><span class="sxs-lookup"><span data-stu-id="2e26b-121">Fully qualified names</span></span>

 <span data-ttu-id="2e26b-122">Obory názvů a typy mají jedinečné názvy, které popisují plně kvalifikované názvy, které označují logickou hierarchii.</span><span class="sxs-lookup"><span data-stu-id="2e26b-122">Namespaces and types have unique titles described by fully qualified names that indicate a logical hierarchy.</span></span> <span data-ttu-id="2e26b-123">Například příkaz `A.B` znamená, že `A` je název oboru názvů nebo typu a `B` je vnořen uvnitř něj.</span><span class="sxs-lookup"><span data-stu-id="2e26b-123">For example, the statement `A.B` implies that `A` is the name of the namespace or type, and `B` is nested inside it.</span></span>  
  
 <span data-ttu-id="2e26b-124">V následujícím příkladu jsou vnořené třídy a obory názvů.</span><span class="sxs-lookup"><span data-stu-id="2e26b-124">In the following example, there are nested classes and namespaces.</span></span> <span data-ttu-id="2e26b-125">Plně kvalifikovaný název je označen jako komentář za každou entitou.</span><span class="sxs-lookup"><span data-stu-id="2e26b-125">The fully qualified name is indicated as a comment following each entity.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#9)]  
  
 <span data-ttu-id="2e26b-126">V předchozím segmentu kódu:</span><span class="sxs-lookup"><span data-stu-id="2e26b-126">In the previous code segment:</span></span>  
  
- <span data-ttu-id="2e26b-127">Obor názvů `N1` je členem globálního oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2e26b-127">The namespace `N1` is a member of the global namespace.</span></span> <span data-ttu-id="2e26b-128">Jeho plně kvalifikovaný název je `N1`.</span><span class="sxs-lookup"><span data-stu-id="2e26b-128">Its fully qualified name is `N1`.</span></span>  
  
- <span data-ttu-id="2e26b-129">Obor názvů `N2` je členem `N1`.</span><span class="sxs-lookup"><span data-stu-id="2e26b-129">The namespace `N2` is a member of `N1`.</span></span> <span data-ttu-id="2e26b-130">Jeho plně kvalifikovaný název je `N1.N2`.</span><span class="sxs-lookup"><span data-stu-id="2e26b-130">Its fully qualified name is `N1.N2`.</span></span>  
  
- <span data-ttu-id="2e26b-131">`C1` třídy je členem `N1`.</span><span class="sxs-lookup"><span data-stu-id="2e26b-131">The class `C1` is a member of `N1`.</span></span> <span data-ttu-id="2e26b-132">Jeho plně kvalifikovaný název je `N1.C1`.</span><span class="sxs-lookup"><span data-stu-id="2e26b-132">Its fully qualified name is `N1.C1`.</span></span>  
  
- <span data-ttu-id="2e26b-133">Název třídy `C2` se v tomto kódu používá dvakrát.</span><span class="sxs-lookup"><span data-stu-id="2e26b-133">The class name `C2` is used two times in this code.</span></span> <span data-ttu-id="2e26b-134">Plně kvalifikované názvy jsou ale jedinečné.</span><span class="sxs-lookup"><span data-stu-id="2e26b-134">However, the fully qualified names are unique.</span></span> <span data-ttu-id="2e26b-135">První instance `C2` je deklarována uvnitř `C1`; Proto je jeho plně kvalifikovaný název: `N1.C1.C2`.</span><span class="sxs-lookup"><span data-stu-id="2e26b-135">The first instance of `C2` is declared inside `C1`; therefore, its fully qualified name is: `N1.C1.C2`.</span></span> <span data-ttu-id="2e26b-136">Druhá instance `C2` je deklarována uvnitř oboru názvů `N2`; Proto je jeho plně kvalifikovaný název `N1.N2.C2`.</span><span class="sxs-lookup"><span data-stu-id="2e26b-136">The second instance of `C2` is declared inside a namespace `N2`; therefore, its fully qualified name is `N1.N2.C2`.</span></span>  
  
 <span data-ttu-id="2e26b-137">Pomocí předchozího segmentu kódu můžete přidat nový člen třídy `C3`do oboru názvů `N1.N2` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="2e26b-137">Using the previous code segment, you can add a new class member, `C3`, to the namespace `N1.N2` as follows:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#10)]  
  
 <span data-ttu-id="2e26b-138">Obecně použijte [kvalifikátor aliasu oboru názvů `::`](../../language-reference/operators/namespace-alias-qualifier.md) pro odkazování na alias oboru názvů nebo `global::` pro odkazování na globální obor názvů a `.` k zařazování typů nebo členů.</span><span class="sxs-lookup"><span data-stu-id="2e26b-138">In general, use the [namespace alias qualifier `::`](../../language-reference/operators/namespace-alias-qualifier.md) to reference a namespace alias or `global::` to reference the global namespace and `.` to qualify types or members.</span></span>  
  
 <span data-ttu-id="2e26b-139">Použití `::` s aliasem, který odkazuje na typ namísto oboru názvů, je chyba.</span><span class="sxs-lookup"><span data-stu-id="2e26b-139">It is an error to use `::` with an alias that references a type instead of a namespace.</span></span> <span data-ttu-id="2e26b-140">Příklad:</span><span class="sxs-lookup"><span data-stu-id="2e26b-140">For example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#11)]  
  
 [!code-csharp[csProgGuideNamespaces#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#12)]  
  
 <span data-ttu-id="2e26b-141">Pamatujte, že slovo `global` není předdefinovaným aliasem. Proto `global.X` nemá žádný zvláštní význam.</span><span class="sxs-lookup"><span data-stu-id="2e26b-141">Remember that the word `global` is not a predefined alias; therefore, `global.X` does not have any special meaning.</span></span> <span data-ttu-id="2e26b-142">Získá zvláštní význam pouze v případě, že se používá s `::`.</span><span class="sxs-lookup"><span data-stu-id="2e26b-142">It acquires a special meaning only when it is used with `::`.</span></span>  
  
 <span data-ttu-id="2e26b-143">Při definování aliasu s názvem Global se vygeneruje upozornění kompilátoru CS0440, protože `global::` vždycky odkazuje na globální obor názvů, ne na alias.</span><span class="sxs-lookup"><span data-stu-id="2e26b-143">Compiler warning CS0440 is generated if you define an alias named global because `global::` always references the global namespace and not an alias.</span></span> <span data-ttu-id="2e26b-144">Například následující řádek vygeneruje upozornění:</span><span class="sxs-lookup"><span data-stu-id="2e26b-144">For example, the following line generates the warning:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#13)]  
  
 <span data-ttu-id="2e26b-145">Použití `::` s aliasy je dobrý nápad a chrání proti neočekávanému zavedení dalších typů.</span><span class="sxs-lookup"><span data-stu-id="2e26b-145">Using `::` with aliases is a good idea and protects against the unexpected introduction of additional types.</span></span> <span data-ttu-id="2e26b-146">Zvažte například tento příklad:</span><span class="sxs-lookup"><span data-stu-id="2e26b-146">For example, consider this example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#14)]  
  
 [!code-csharp[csProgGuideNamespaces#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#15)]  
  
 <span data-ttu-id="2e26b-147">Tento postup funguje, ale pokud byl následně zaveden typ s názvem `Alias`, `Alias.` by se místo toho naváže k tomuto typu.</span><span class="sxs-lookup"><span data-stu-id="2e26b-147">This works, but if a type named `Alias` were to subsequently be introduced, `Alias.` would bind to that type instead.</span></span> <span data-ttu-id="2e26b-148">Pomocí `Alias::Exception` zajistí, že `Alias` je považován za alias oboru názvů a nemusíte ho označit pro typ.</span><span class="sxs-lookup"><span data-stu-id="2e26b-148">Using `Alias::Exception` ensures that `Alias` is treated as a namespace alias and not mistaken for a type.</span></span>  

## <a name="see-also"></a><span data-ttu-id="2e26b-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2e26b-149">See also</span></span>

- [<span data-ttu-id="2e26b-150">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="2e26b-150">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2e26b-151">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="2e26b-151">Namespaces</span></span>](./index.md)
- [<span data-ttu-id="2e26b-152">. podnikatel</span><span class="sxs-lookup"><span data-stu-id="2e26b-152">. operator</span></span>](../../language-reference/operators/member-access-operators.md#member-access-operator-)
- [<span data-ttu-id="2e26b-153">:: – operátor</span><span class="sxs-lookup"><span data-stu-id="2e26b-153">:: operator</span></span>](../../language-reference/operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="2e26b-154">extern alias</span><span class="sxs-lookup"><span data-stu-id="2e26b-154">extern alias</span></span>](../../language-reference/keywords/extern-alias.md)
