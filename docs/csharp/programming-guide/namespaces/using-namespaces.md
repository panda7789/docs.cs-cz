---
title: Používání oborů názvů C# – Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: abd4c34661d96d8c3188e92dd2d76f847e17aae7
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433538"
---
# <a name="using-namespaces-c-programming-guide"></a><span data-ttu-id="316e5-102">Použití oboru názvů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="316e5-102">Using Namespaces (C# Programming Guide)</span></span>
<span data-ttu-id="316e5-103">Obory názvů jsou v C# rámci programů silně používány dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="316e5-103">Namespaces are heavily used within C# programs in two ways.</span></span> <span data-ttu-id="316e5-104">Nejprve třídy .NET Framework používají obory názvů k uspořádání svých mnoha tříd.</span><span class="sxs-lookup"><span data-stu-id="316e5-104">Firstly, the .NET Framework classes use namespaces to organize its many classes.</span></span> <span data-ttu-id="316e5-105">Následně deklarace vlastních oborů názvů vám může pomáhat řídit obor názvů tříd a metod ve větších programovacích projektech.</span><span class="sxs-lookup"><span data-stu-id="316e5-105">Secondly, declaring your own namespaces can help control the scope of class and method names in larger programming projects.</span></span>  
  
## <a name="accessing-namespaces"></a><span data-ttu-id="316e5-106">Přístup k oborům názvů</span><span class="sxs-lookup"><span data-stu-id="316e5-106">Accessing Namespaces</span></span>  
 <span data-ttu-id="316e5-107">Většina C# aplikací začíná oddílem `using` direktiv.</span><span class="sxs-lookup"><span data-stu-id="316e5-107">Most C# applications begin with a section of `using` directives.</span></span> <span data-ttu-id="316e5-108">V této části jsou uvedeny obory názvů, které aplikace často používá, a uloží programátora z určení plně kvalifikovaného názvu pokaždé, když se použije metoda, která je obsažena v rámci.</span><span class="sxs-lookup"><span data-stu-id="316e5-108">This section lists the namespaces that the application will be using frequently, and saves the programmer from specifying a fully qualified name every time that a method that is contained within is used.</span></span>  
  
 <span data-ttu-id="316e5-109">Například zahrnutím řádku:</span><span class="sxs-lookup"><span data-stu-id="316e5-109">For example, by including the line:</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 <span data-ttu-id="316e5-110">Na začátku programu může programátor použít kód:</span><span class="sxs-lookup"><span data-stu-id="316e5-110">At the start of a program, the programmer can use the code:</span></span>  
  
 [!code-csharp[csProgGuide#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#31)]  
  
 <span data-ttu-id="316e5-111">Namísto:</span><span class="sxs-lookup"><span data-stu-id="316e5-111">Instead of:</span></span>  
  
 [!code-csharp[csProgGuide#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#30)]  
  
## <a name="namespace-aliases"></a><span data-ttu-id="316e5-112">Aliasy oboru názvů</span><span class="sxs-lookup"><span data-stu-id="316e5-112">Namespace Aliases</span></span>  
 <span data-ttu-id="316e5-113">[Direktivu using](../../../csharp/language-reference/keywords/using-directive.md) lze použít také k vytvoření aliasu pro [obor názvů](../../../csharp/language-reference/keywords/namespace.md).</span><span class="sxs-lookup"><span data-stu-id="316e5-113">The [using Directive](../../../csharp/language-reference/keywords/using-directive.md) can also be used to create an alias for a [namespace](../../../csharp/language-reference/keywords/namespace.md).</span></span> <span data-ttu-id="316e5-114">Například pokud používáte dříve psaný obor názvů, který obsahuje vnořené obory názvů, můžete chtít deklarovat alias pro poskytnutí zkrácený způsob odkazování na sebe, jak je uvedeno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="316e5-114">For example, if you are using a previously written namespace that contains nested namespaces, you might want to declare an alias to provide a shorthand way of referencing one in particular, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#7)]  
  
## <a name="using-namespaces-to-control-scope"></a><span data-ttu-id="316e5-115">Použití oborů názvů k řízení oboru</span><span class="sxs-lookup"><span data-stu-id="316e5-115">Using Namespaces to control scope</span></span>  
 <span data-ttu-id="316e5-116">`namespace` Klíčové slovo se používá k deklarování oboru.</span><span class="sxs-lookup"><span data-stu-id="316e5-116">The `namespace` keyword is used to declare a scope.</span></span> <span data-ttu-id="316e5-117">Schopnost vytvářet obory v rámci projektu pomáhá organizovat kód a umožňuje vytvářet globálně jedinečné typy.</span><span class="sxs-lookup"><span data-stu-id="316e5-117">The ability to create scopes within your project helps organize code and lets you create globally-unique types.</span></span> <span data-ttu-id="316e5-118">V následujícím příkladu je třída s názvem `SampleClass` definována ve dvou oborech názvů, jedna vnořená uvnitř druhé.</span><span class="sxs-lookup"><span data-stu-id="316e5-118">In the following example, a class titled `SampleClass` is defined in two namespaces, one nested inside the other.</span></span> <span data-ttu-id="316e5-119">[ `.` Operátor přístupu členů](../../language-reference/operators/member-access-operators.md#member-access-operator-) slouží k odlišení, která metoda se volá.</span><span class="sxs-lookup"><span data-stu-id="316e5-119">The [member access `.` operator](../../language-reference/operators/member-access-operators.md#member-access-operator-) is used to differentiate which method gets called.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#8)]  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="316e5-120">Plně kvalifikované názvy</span><span class="sxs-lookup"><span data-stu-id="316e5-120">Fully Qualified Names</span></span>  
 <span data-ttu-id="316e5-121">Obory názvů a typy mají jedinečné názvy, které popisují plně kvalifikované názvy, které označují logickou hierarchii.</span><span class="sxs-lookup"><span data-stu-id="316e5-121">Namespaces and types have unique titles described by fully qualified names that indicate a logical hierarchy.</span></span> <span data-ttu-id="316e5-122">Například příkaz `A.B` předpokládá, že `A` se jedná o název oboru názvů nebo typu a `B` je v něm vnořený.</span><span class="sxs-lookup"><span data-stu-id="316e5-122">For example, the statement `A.B` implies that `A` is the name of the namespace or type, and `B` is nested inside it.</span></span>  
  
 <span data-ttu-id="316e5-123">V následujícím příkladu jsou vnořené třídy a obory názvů.</span><span class="sxs-lookup"><span data-stu-id="316e5-123">In the following example, there are nested classes and namespaces.</span></span> <span data-ttu-id="316e5-124">Plně kvalifikovaný název je označen jako komentář za každou entitou.</span><span class="sxs-lookup"><span data-stu-id="316e5-124">The fully qualified name is indicated as a comment following each entity.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#9)]  
  
 <span data-ttu-id="316e5-125">V předchozím segmentu kódu:</span><span class="sxs-lookup"><span data-stu-id="316e5-125">In the previous code segment:</span></span>  
  
- <span data-ttu-id="316e5-126">Obor názvů `N1` je členem globálního oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="316e5-126">The namespace `N1` is a member of the global namespace.</span></span> <span data-ttu-id="316e5-127">Jeho plně kvalifikovaný název je `N1`.</span><span class="sxs-lookup"><span data-stu-id="316e5-127">Its fully qualified name is `N1`.</span></span>  
  
- <span data-ttu-id="316e5-128">Obor názvů `N2` je `N1`členem.</span><span class="sxs-lookup"><span data-stu-id="316e5-128">The namespace `N2` is a member of `N1`.</span></span> <span data-ttu-id="316e5-129">Jeho plně kvalifikovaný název je `N1.N2`.</span><span class="sxs-lookup"><span data-stu-id="316e5-129">Its fully qualified name is `N1.N2`.</span></span>  
  
- <span data-ttu-id="316e5-130">Třída `C1` je`N1`členem.</span><span class="sxs-lookup"><span data-stu-id="316e5-130">The class `C1` is a member of `N1`.</span></span> <span data-ttu-id="316e5-131">Jeho plně kvalifikovaný název je `N1.C1`.</span><span class="sxs-lookup"><span data-stu-id="316e5-131">Its fully qualified name is `N1.C1`.</span></span>  
  
- <span data-ttu-id="316e5-132">Název `C2` třídy se v tomto kódu použije dvakrát.</span><span class="sxs-lookup"><span data-stu-id="316e5-132">The class name `C2` is used two times in this code.</span></span> <span data-ttu-id="316e5-133">Plně kvalifikované názvy jsou ale jedinečné.</span><span class="sxs-lookup"><span data-stu-id="316e5-133">However, the fully qualified names are unique.</span></span> <span data-ttu-id="316e5-134">První instance `C2` je deklarována uvnitř `C1`; proto je plně kvalifikovaný název: `N1.C1.C2`.</span><span class="sxs-lookup"><span data-stu-id="316e5-134">The first instance of `C2` is declared inside `C1`; therefore, its fully qualified name is: `N1.C1.C2`.</span></span> <span data-ttu-id="316e5-135">Druhá instance `C2` je deklarována uvnitř oboru názvů `N2`; proto je `N1.N2.C2`jeho plně kvalifikovaný název.</span><span class="sxs-lookup"><span data-stu-id="316e5-135">The second instance of `C2` is declared inside a namespace `N2`; therefore, its fully qualified name is `N1.N2.C2`.</span></span>  
  
 <span data-ttu-id="316e5-136">Pomocí předchozího segmentu kódu můžete přidat nového člena `C3`třídy do oboru názvů `N1.N2` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="316e5-136">Using the previous code segment, you can add a new class member, `C3`, to the namespace `N1.N2` as follows:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#10)]  
  
 <span data-ttu-id="316e5-137">Obecně použijte `::` pro odkaz na alias oboru názvů nebo `global::` pro odkazování na globální obor názvů `.` a pro kvalifikaci typů nebo členů.</span><span class="sxs-lookup"><span data-stu-id="316e5-137">In general, use `::` to reference a namespace alias or `global::` to reference the global namespace and `.` to qualify types or members.</span></span>  
  
 <span data-ttu-id="316e5-138">Použití `::` s aliasem, který odkazuje na typ namísto oboru názvů, je chyba.</span><span class="sxs-lookup"><span data-stu-id="316e5-138">It is an error to use `::` with an alias that references a type instead of a namespace.</span></span> <span data-ttu-id="316e5-139">Příklad:</span><span class="sxs-lookup"><span data-stu-id="316e5-139">For example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#11)]  
  
 [!code-csharp[csProgGuideNamespaces#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#12)]  
  
 <span data-ttu-id="316e5-140">Mějte na paměti, `global` že slovo není předdefinovaným aliasem `global.X` . proto nemá žádný zvláštní význam.</span><span class="sxs-lookup"><span data-stu-id="316e5-140">Remember that the word `global` is not a predefined alias; therefore, `global.X` does not have any special meaning.</span></span> <span data-ttu-id="316e5-141">Získá zvláštní význam pouze v případě, že je použit s `::`.</span><span class="sxs-lookup"><span data-stu-id="316e5-141">It acquires a special meaning only when it is used with `::`.</span></span>  
  
 <span data-ttu-id="316e5-142">Při definování aliasu s názvem Global se vygeneruje upozornění kompilátoru CS0440 `global::` , protože vždycky odkazuje na globální obor názvů, ne na alias.</span><span class="sxs-lookup"><span data-stu-id="316e5-142">Compiler warning CS0440 is generated if you define an alias named global because `global::` always references the global namespace and not an alias.</span></span> <span data-ttu-id="316e5-143">Například následující řádek vygeneruje upozornění:</span><span class="sxs-lookup"><span data-stu-id="316e5-143">For example, the following line generates the warning:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#13)]  
  
 <span data-ttu-id="316e5-144">Použití `::` s aliasy je dobrý nápad a chrání proti neočekávanému zavedení dalších typů.</span><span class="sxs-lookup"><span data-stu-id="316e5-144">Using `::` with aliases is a good idea and protects against the unexpected introduction of additional types.</span></span> <span data-ttu-id="316e5-145">Zvažte například tento příklad:</span><span class="sxs-lookup"><span data-stu-id="316e5-145">For example, consider this example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#14)]  
  
 [!code-csharp[csProgGuideNamespaces#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#15)]  
  
 <span data-ttu-id="316e5-146">To funguje, ale pokud by byl následně `Alias` zaveden typ s názvem, `Alias.` měl by se místo toho vytvořit vazba na tento typ.</span><span class="sxs-lookup"><span data-stu-id="316e5-146">This works, but if a type named `Alias` were to subsequently be introduced, `Alias.` would bind to that type instead.</span></span> <span data-ttu-id="316e5-147">Pomocí `Alias::Exception` této vlastnosti `Alias` je zajištěno, že se jako alias oboru názvů považuje označení pro typ.</span><span class="sxs-lookup"><span data-stu-id="316e5-147">Using `Alias::Exception` ensures that `Alias` is treated as a namespace alias and not mistaken for a type.</span></span>  
  
 <span data-ttu-id="316e5-148">Další informace najdete [v tématu Postup: Pro další informace `global` týkající se](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) aliasu použijte globální alias oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="316e5-148">See the topic [How to: Use the Global Namespace Alias](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) for more information regarding the `global` alias.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="316e5-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="316e5-149">See also</span></span>

- [<span data-ttu-id="316e5-150">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="316e5-150">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="316e5-151">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="316e5-151">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)
- [<span data-ttu-id="316e5-152">. – operátor</span><span class="sxs-lookup"><span data-stu-id="316e5-152">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operators.md#member-access-operator-)
- [<span data-ttu-id="316e5-153">:: – operátor</span><span class="sxs-lookup"><span data-stu-id="316e5-153">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)
- [<span data-ttu-id="316e5-154">extern</span><span class="sxs-lookup"><span data-stu-id="316e5-154">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)
