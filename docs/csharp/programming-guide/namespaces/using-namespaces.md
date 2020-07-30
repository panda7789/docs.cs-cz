---
title: Používání oborů názvů – Průvodce programováním v C#
description: Naučte se používat obory názvů v programování v jazyce C#, jako je přístup k oborům názvů, aliasům oboru názvů a používání oborů názvů k řízení oboru.
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: 86892f50e059c16ee9c133d7ba9f2716e11a8e56
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381694"
---
# <a name="using-namespaces-c-programming-guide"></a><span data-ttu-id="00b40-103">Používání oborů názvů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="00b40-103">Using namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="00b40-104">Obory názvů se silně používají v rámci programů C# dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="00b40-104">Namespaces are heavily used within C# programs in two ways.</span></span> <span data-ttu-id="00b40-105">Za prvé, třídy .NET používají obory názvů k uspořádání celé řady tříd.</span><span class="sxs-lookup"><span data-stu-id="00b40-105">Firstly, the .NET classes use namespaces to organize its many classes.</span></span> <span data-ttu-id="00b40-106">Následně deklarace vlastních oborů názvů vám může pomáhat řídit obor názvů tříd a metod ve větších programovacích projektech.</span><span class="sxs-lookup"><span data-stu-id="00b40-106">Secondly, declaring your own namespaces can help control the scope of class and method names in larger programming projects.</span></span>  
  
## <a name="accessing-namespaces"></a><span data-ttu-id="00b40-107">Přístup k oborům názvů</span><span class="sxs-lookup"><span data-stu-id="00b40-107">Accessing namespaces</span></span>

 <span data-ttu-id="00b40-108">Většina aplikací C# začíná oddílem `using` direktiv.</span><span class="sxs-lookup"><span data-stu-id="00b40-108">Most C# applications begin with a section of `using` directives.</span></span> <span data-ttu-id="00b40-109">V této části jsou uvedeny obory názvů, které aplikace často používá, a uloží programátora z určení plně kvalifikovaného názvu pokaždé, když se použije metoda, která je obsažena v rámci.</span><span class="sxs-lookup"><span data-stu-id="00b40-109">This section lists the namespaces that the application will be using frequently, and saves the programmer from specifying a fully qualified name every time that a method that is contained within is used.</span></span>  
  
 <span data-ttu-id="00b40-110">Například zahrnutím řádku:</span><span class="sxs-lookup"><span data-stu-id="00b40-110">For example, by including the line:</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 <span data-ttu-id="00b40-111">Na začátku programu může programátor použít kód:</span><span class="sxs-lookup"><span data-stu-id="00b40-111">At the start of a program, the programmer can use the code:</span></span>  
  
 [!code-csharp[csProgGuide#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#31)]  
  
 <span data-ttu-id="00b40-112">Namísto:</span><span class="sxs-lookup"><span data-stu-id="00b40-112">Instead of:</span></span>  
  
 [!code-csharp[csProgGuide#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#30)]  
  
## <a name="namespace-aliases"></a><span data-ttu-id="00b40-113">Aliasy oboru názvů</span><span class="sxs-lookup"><span data-stu-id="00b40-113">Namespace aliases</span></span>

 <span data-ttu-id="00b40-114">Můžete také použít [ `using` direktivu](../../language-reference/keywords/using-directive.md) pro vytvoření aliasu pro obor názvů.</span><span class="sxs-lookup"><span data-stu-id="00b40-114">You can also use the [`using` directive](../../language-reference/keywords/using-directive.md) to create an alias for a namespace.</span></span> <span data-ttu-id="00b40-115">Pro přístup ke členům oboru názvů s aliasy použijte [kvalifikátor `::` aliasu oboru názvů](../../language-reference/operators/namespace-alias-qualifier.md) .</span><span class="sxs-lookup"><span data-stu-id="00b40-115">Use the [namespace alias qualifier `::`](../../language-reference/operators/namespace-alias-qualifier.md) to access the members of the aliased namespace.</span></span> <span data-ttu-id="00b40-116">Následující příklad ukazuje, jak vytvořit a použít alias oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="00b40-116">The following example shows how to create and use a namespace alias:</span></span>
  
[!code-csharp[csProgGuideNamespaces#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#5)]
  
## <a name="using-namespaces-to-control-scope"></a><span data-ttu-id="00b40-117">Použití oborů názvů k řízení oboru</span><span class="sxs-lookup"><span data-stu-id="00b40-117">Using namespaces to control scope</span></span>

 <span data-ttu-id="00b40-118">`namespace`Klíčové slovo se používá k deklarování oboru.</span><span class="sxs-lookup"><span data-stu-id="00b40-118">The `namespace` keyword is used to declare a scope.</span></span> <span data-ttu-id="00b40-119">Schopnost vytvářet obory v rámci projektu pomáhá organizovat kód a umožňuje vytvářet globálně jedinečné typy.</span><span class="sxs-lookup"><span data-stu-id="00b40-119">The ability to create scopes within your project helps organize code and lets you create globally-unique types.</span></span> <span data-ttu-id="00b40-120">V následujícím příkladu je třída s názvem `SampleClass` definována ve dvou oborech názvů, jedna vnořená uvnitř druhé.</span><span class="sxs-lookup"><span data-stu-id="00b40-120">In the following example, a class titled `SampleClass` is defined in two namespaces, one nested inside the other.</span></span> <span data-ttu-id="00b40-121">[ `.` Token](../../language-reference/operators/member-access-operators.md#member-access-expression-) slouží k odlišení, která metoda se volá.</span><span class="sxs-lookup"><span data-stu-id="00b40-121">The [`.` token](../../language-reference/operators/member-access-operators.md#member-access-expression-) is used to differentiate which method gets called.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#8)]  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="00b40-122">Plně kvalifikované názvy</span><span class="sxs-lookup"><span data-stu-id="00b40-122">Fully qualified names</span></span>

 <span data-ttu-id="00b40-123">Obory názvů a typy mají jedinečné názvy, které popisují plně kvalifikované názvy, které označují logickou hierarchii.</span><span class="sxs-lookup"><span data-stu-id="00b40-123">Namespaces and types have unique titles described by fully qualified names that indicate a logical hierarchy.</span></span> <span data-ttu-id="00b40-124">Například příkaz `A.B` předpokládá, že `A` se jedná o název oboru názvů nebo typu a `B` je v něm vnořený.</span><span class="sxs-lookup"><span data-stu-id="00b40-124">For example, the statement `A.B` implies that `A` is the name of the namespace or type, and `B` is nested inside it.</span></span>  
  
 <span data-ttu-id="00b40-125">V následujícím příkladu jsou vnořené třídy a obory názvů.</span><span class="sxs-lookup"><span data-stu-id="00b40-125">In the following example, there are nested classes and namespaces.</span></span> <span data-ttu-id="00b40-126">Plně kvalifikovaný název je označen jako komentář za každou entitou.</span><span class="sxs-lookup"><span data-stu-id="00b40-126">The fully qualified name is indicated as a comment following each entity.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#9)]  
  
 <span data-ttu-id="00b40-127">V předchozím segmentu kódu:</span><span class="sxs-lookup"><span data-stu-id="00b40-127">In the previous code segment:</span></span>  
  
- <span data-ttu-id="00b40-128">Obor názvů `N1` je členem globálního oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="00b40-128">The namespace `N1` is a member of the global namespace.</span></span> <span data-ttu-id="00b40-129">Jeho plně kvalifikovaný název je `N1` .</span><span class="sxs-lookup"><span data-stu-id="00b40-129">Its fully qualified name is `N1`.</span></span>  
  
- <span data-ttu-id="00b40-130">Obor názvů `N2` je členem `N1` .</span><span class="sxs-lookup"><span data-stu-id="00b40-130">The namespace `N2` is a member of `N1`.</span></span> <span data-ttu-id="00b40-131">Jeho plně kvalifikovaný název je `N1.N2` .</span><span class="sxs-lookup"><span data-stu-id="00b40-131">Its fully qualified name is `N1.N2`.</span></span>  
  
- <span data-ttu-id="00b40-132">Třída `C1` je členem `N1` .</span><span class="sxs-lookup"><span data-stu-id="00b40-132">The class `C1` is a member of `N1`.</span></span> <span data-ttu-id="00b40-133">Jeho plně kvalifikovaný název je `N1.C1` .</span><span class="sxs-lookup"><span data-stu-id="00b40-133">Its fully qualified name is `N1.C1`.</span></span>  
  
- <span data-ttu-id="00b40-134">Název třídy `C2` se v tomto kódu použije dvakrát.</span><span class="sxs-lookup"><span data-stu-id="00b40-134">The class name `C2` is used two times in this code.</span></span> <span data-ttu-id="00b40-135">Plně kvalifikované názvy jsou ale jedinečné.</span><span class="sxs-lookup"><span data-stu-id="00b40-135">However, the fully qualified names are unique.</span></span> <span data-ttu-id="00b40-136">První instance `C2` je deklarována uvnitř `C1` ; proto je plně kvalifikovaný název: `N1.C1.C2` .</span><span class="sxs-lookup"><span data-stu-id="00b40-136">The first instance of `C2` is declared inside `C1`; therefore, its fully qualified name is: `N1.C1.C2`.</span></span> <span data-ttu-id="00b40-137">Druhá instance `C2` je deklarována uvnitř oboru názvů `N2` ; proto je jeho plně kvalifikovaný název `N1.N2.C2` .</span><span class="sxs-lookup"><span data-stu-id="00b40-137">The second instance of `C2` is declared inside a namespace `N2`; therefore, its fully qualified name is `N1.N2.C2`.</span></span>  
  
 <span data-ttu-id="00b40-138">Pomocí předchozího segmentu kódu můžete přidat nového člena třídy `C3` do oboru názvů následujícím `N1.N2` způsobem:</span><span class="sxs-lookup"><span data-stu-id="00b40-138">Using the previous code segment, you can add a new class member, `C3`, to the namespace `N1.N2` as follows:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#10)]  
  
 <span data-ttu-id="00b40-139">Obecně použijte [kvalifikátor `::` aliasu oboru názvů](../../language-reference/operators/namespace-alias-qualifier.md) pro odkazování na alias oboru názvů nebo `global::` na odkaz na globální obor názvů a `.` pro kvalifikaci typů nebo členů.</span><span class="sxs-lookup"><span data-stu-id="00b40-139">In general, use the [namespace alias qualifier `::`](../../language-reference/operators/namespace-alias-qualifier.md) to reference a namespace alias or `global::` to reference the global namespace and `.` to qualify types or members.</span></span>  
  
 <span data-ttu-id="00b40-140">Použití `::` s aliasem, který odkazuje na typ namísto oboru názvů, je chyba.</span><span class="sxs-lookup"><span data-stu-id="00b40-140">It is an error to use `::` with an alias that references a type instead of a namespace.</span></span> <span data-ttu-id="00b40-141">Příklad:</span><span class="sxs-lookup"><span data-stu-id="00b40-141">For example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#11)]  
  
 [!code-csharp[csProgGuideNamespaces#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#12)]  
  
 <span data-ttu-id="00b40-142">Mějte na paměti, že slovo není `global` předdefinovaným aliasem. proto nemá `global.X` žádný zvláštní význam.</span><span class="sxs-lookup"><span data-stu-id="00b40-142">Remember that the word `global` is not a predefined alias; therefore, `global.X` does not have any special meaning.</span></span> <span data-ttu-id="00b40-143">Získá zvláštní význam pouze v případě, že je použit s `::` .</span><span class="sxs-lookup"><span data-stu-id="00b40-143">It acquires a special meaning only when it is used with `::`.</span></span>  
  
 <span data-ttu-id="00b40-144">Při definování aliasu s názvem Global se vygeneruje upozornění kompilátoru CS0440, protože `global::` vždycky odkazuje na globální obor názvů, ne na alias.</span><span class="sxs-lookup"><span data-stu-id="00b40-144">Compiler warning CS0440 is generated if you define an alias named global because `global::` always references the global namespace and not an alias.</span></span> <span data-ttu-id="00b40-145">Například následující řádek vygeneruje upozornění:</span><span class="sxs-lookup"><span data-stu-id="00b40-145">For example, the following line generates the warning:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#13)]  
  
 <span data-ttu-id="00b40-146">Použití `::` s aliasy je dobrý nápad a chrání proti neočekávanému zavedení dalších typů.</span><span class="sxs-lookup"><span data-stu-id="00b40-146">Using `::` with aliases is a good idea and protects against the unexpected introduction of additional types.</span></span> <span data-ttu-id="00b40-147">Zvažte například tento příklad:</span><span class="sxs-lookup"><span data-stu-id="00b40-147">For example, consider this example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#14)]  
  
 [!code-csharp[csProgGuideNamespaces#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#15)]  
  
 <span data-ttu-id="00b40-148">To funguje, ale pokud `Alias` by byl následně zaveden typ s názvem, `Alias.` měl by se místo toho vytvořit vazba na tento typ.</span><span class="sxs-lookup"><span data-stu-id="00b40-148">This works, but if a type named `Alias` were to subsequently be introduced, `Alias.` would bind to that type instead.</span></span> <span data-ttu-id="00b40-149">Pomocí `Alias::Exception` této vlastnosti je zajištěno, že `Alias` se jako alias oboru názvů považuje označení pro typ.</span><span class="sxs-lookup"><span data-stu-id="00b40-149">Using `Alias::Exception` ensures that `Alias` is treated as a namespace alias and not mistaken for a type.</span></span>  

## <a name="see-also"></a><span data-ttu-id="00b40-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="00b40-150">See also</span></span>

- [<span data-ttu-id="00b40-151">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="00b40-151">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="00b40-152">Jmenné prostory</span><span class="sxs-lookup"><span data-stu-id="00b40-152">Namespaces</span></span>](./index.md)
- [<span data-ttu-id="00b40-153">Výraz přístupu členů</span><span class="sxs-lookup"><span data-stu-id="00b40-153">Member access expression</span></span>](../../language-reference/operators/member-access-operators.md#member-access-expression-)
- [<span data-ttu-id="00b40-154">:: – operátor</span><span class="sxs-lookup"><span data-stu-id="00b40-154">:: operator</span></span>](../../language-reference/operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="00b40-155">externí alias</span><span class="sxs-lookup"><span data-stu-id="00b40-155">extern alias</span></span>](../../language-reference/keywords/extern-alias.md)
