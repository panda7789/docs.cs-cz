---
title: Použití oboru názvů (Průvodce programováním v C#)
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: 773add221317a2154ac620acf766607ec22c629d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33329544"
---
# <a name="using-namespaces-c-programming-guide"></a><span data-ttu-id="27836-102">Použití oboru názvů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="27836-102">Using Namespaces (C# Programming Guide)</span></span>
<span data-ttu-id="27836-103">Obory názvů jsou nejčastěji používá v rámci programy C# dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="27836-103">Namespaces are heavily used within C# programs in two ways.</span></span> <span data-ttu-id="27836-104">Za prvé tříd rozhraní .NET Framework použít obory názvů k uspořádání jeho mnoho tříd.</span><span class="sxs-lookup"><span data-stu-id="27836-104">Firstly, the .NET Framework classes use namespaces to organize its many classes.</span></span> <span data-ttu-id="27836-105">Za druhé deklarace vlastní oborů názvů umožňují omezit rozsah třídy a metody názvy v projektech větší programování.</span><span class="sxs-lookup"><span data-stu-id="27836-105">Secondly, declaring your own namespaces can help control the scope of class and method names in larger programming projects.</span></span>  
  
## <a name="accessing-namespaces"></a><span data-ttu-id="27836-106">Přístup k obory názvů</span><span class="sxs-lookup"><span data-stu-id="27836-106">Accessing Namespaces</span></span>  
 <span data-ttu-id="27836-107">Většina aplikací v C# začínat oddíl `using` direktivy.</span><span class="sxs-lookup"><span data-stu-id="27836-107">Most C# applications begin with a section of `using` directives.</span></span> <span data-ttu-id="27836-108">Tato část uvádí obory názvů, že aplikace budou často používat a uloží programátorů zadat pokaždé, když se používá metoda, která je obsažená v plně kvalifikovaný název.</span><span class="sxs-lookup"><span data-stu-id="27836-108">This section lists the namespaces that the application will be using frequently, and saves the programmer from specifying a fully qualified name every time that a method that is contained within is used.</span></span>  
  
 <span data-ttu-id="27836-109">Například zahrnutím řádku:</span><span class="sxs-lookup"><span data-stu-id="27836-109">For example, by including the line:</span></span>  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_1.cs)]  
  
 <span data-ttu-id="27836-110">Při spuštění programu můžete použít programátorů kód:</span><span class="sxs-lookup"><span data-stu-id="27836-110">At the start of a program, the programmer can use the code:</span></span>  
  
 [!code-csharp[csProgGuide#31](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_2.cs)]  
  
 <span data-ttu-id="27836-111">Namísto:</span><span class="sxs-lookup"><span data-stu-id="27836-111">Instead of:</span></span>  
  
 [!code-csharp[csProgGuide#30](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_3.cs)]  
  
## <a name="namespace-aliases"></a><span data-ttu-id="27836-112">Namespace aliasy</span><span class="sxs-lookup"><span data-stu-id="27836-112">Namespace Aliases</span></span>  
 <span data-ttu-id="27836-113">[Using – direktiva](../../../csharp/language-reference/keywords/using-directive.md) lze také použít k vytvoření zástupce pro [obor názvů](../../../csharp/language-reference/keywords/namespace.md).</span><span class="sxs-lookup"><span data-stu-id="27836-113">The [using Directive](../../../csharp/language-reference/keywords/using-directive.md) can also be used to create an alias for a [namespace](../../../csharp/language-reference/keywords/namespace.md).</span></span> <span data-ttu-id="27836-114">Pokud používáte dříve napsané obor názvů, který obsahuje vnořené obory názvů, můžete chtít deklarovat alias zajistit zjednodušený způsob jeden odkazující na konkrétní jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="27836-114">For example, if you are using a previously written namespace that contains nested namespaces, you might want to declare an alias to provide a shorthand way of referencing one in particular, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#7](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_4.cs)]  
  
## <a name="using-namespaces-to-control-scope"></a><span data-ttu-id="27836-115">Použití oboru názvů do oboru ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="27836-115">Using Namespaces to control scope</span></span>  
 <span data-ttu-id="27836-116">`namespace` – Klíčové slovo se používá k deklaraci oboru.</span><span class="sxs-lookup"><span data-stu-id="27836-116">The `namespace` keyword is used to declare a scope.</span></span> <span data-ttu-id="27836-117">Schopnost vytvářet oborů v rámci projektu pomáhá uspořádat kódu a umožňuje vytvořit globálně jedinečné typy.</span><span class="sxs-lookup"><span data-stu-id="27836-117">The ability to create scopes within your project helps organize code and lets you create globally-unique types.</span></span> <span data-ttu-id="27836-118">V následujícím příkladu třída s názvem `SampleClass` je definována v dva obory názvů, jeden vnořený do druhého.</span><span class="sxs-lookup"><span data-stu-id="27836-118">In the following example, a class titled `SampleClass` is defined in two namespaces, one nested inside the other.</span></span> <span data-ttu-id="27836-119">[. Operátor](../../../csharp/language-reference/operators/member-access-operator.md) se používá k rozlišení, které metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="27836-119">The [. Operator](../../../csharp/language-reference/operators/member-access-operator.md) is used to differentiate which method gets called.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#8](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_5.cs)]  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="27836-120">Plně kvalifikované názvy</span><span class="sxs-lookup"><span data-stu-id="27836-120">Fully Qualified Names</span></span>  
 <span data-ttu-id="27836-121">Obory názvů a typy mít jedinečné názvy, které jsou popsané ve plně kvalifikované názvy, které označují logické hierarchie.</span><span class="sxs-lookup"><span data-stu-id="27836-121">Namespaces and types have unique titles described by fully qualified names that indicate a logical hierarchy.</span></span> <span data-ttu-id="27836-122">Například příkaz `A.B` vyplývá, že `A` je název oboru názvů nebo typu, a `B` je vnořit.</span><span class="sxs-lookup"><span data-stu-id="27836-122">For example, the statement `A.B` implies that `A` is the name of the namespace or type, and `B` is nested inside it.</span></span>  
  
 <span data-ttu-id="27836-123">V následujícím příkladu jsou vnořené třídy a obory názvů.</span><span class="sxs-lookup"><span data-stu-id="27836-123">In the following example, there are nested classes and namespaces.</span></span> <span data-ttu-id="27836-124">Plně kvalifikovaný název je označen jako komentář následující každé entity.</span><span class="sxs-lookup"><span data-stu-id="27836-124">The fully qualified name is indicated as a comment following each entity.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#9](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_6.cs)]  
  
 <span data-ttu-id="27836-125">V předchozí segment kódu:</span><span class="sxs-lookup"><span data-stu-id="27836-125">In the previous code segment:</span></span>  
  
-   <span data-ttu-id="27836-126">Obor názvů `N1` je členem globální obor názvů.</span><span class="sxs-lookup"><span data-stu-id="27836-126">The namespace `N1` is a member of the global namespace.</span></span> <span data-ttu-id="27836-127">Je plně kvalifikovaným názvem `N1`.</span><span class="sxs-lookup"><span data-stu-id="27836-127">Its fully qualified name is `N1`.</span></span>  
  
-   <span data-ttu-id="27836-128">Obor názvů `N2` je členem `N1`.</span><span class="sxs-lookup"><span data-stu-id="27836-128">The namespace `N2` is a member of `N1`.</span></span> <span data-ttu-id="27836-129">Je plně kvalifikovaným názvem `N1.N2`.</span><span class="sxs-lookup"><span data-stu-id="27836-129">Its fully qualified name is `N1.N2`.</span></span>  
  
-   <span data-ttu-id="27836-130">Třída `C1` je členem `N1`.</span><span class="sxs-lookup"><span data-stu-id="27836-130">The class `C1` is a member of `N1`.</span></span> <span data-ttu-id="27836-131">Je plně kvalifikovaným názvem `N1.C1`.</span><span class="sxs-lookup"><span data-stu-id="27836-131">Its fully qualified name is `N1.C1`.</span></span>  
  
-   <span data-ttu-id="27836-132">Název třídy `C2` dvakrát se používá v tomto kódu.</span><span class="sxs-lookup"><span data-stu-id="27836-132">The class name `C2` is used two times in this code.</span></span> <span data-ttu-id="27836-133">Plně kvalifikované názvy jsou však jedinečný.</span><span class="sxs-lookup"><span data-stu-id="27836-133">However, the fully qualified names are unique.</span></span> <span data-ttu-id="27836-134">První instance `C2` je deklarovaná uvnitř `C1`; proto je plně kvalifikovaným názvem: `N1.C1.C2`.</span><span class="sxs-lookup"><span data-stu-id="27836-134">The first instance of `C2` is declared inside `C1`; therefore, its fully qualified name is: `N1.C1.C2`.</span></span> <span data-ttu-id="27836-135">Druhou instanci `C2` je deklarovaná uvnitř oboru názvů `N2`; proto je plně kvalifikovaným názvem `N1.N2.C2`.</span><span class="sxs-lookup"><span data-stu-id="27836-135">The second instance of `C2` is declared inside a namespace `N2`; therefore, its fully qualified name is `N1.N2.C2`.</span></span>  
  
 <span data-ttu-id="27836-136">Pomocí předchozího segmentu kódu, můžete přidat nového člena třídy `C3`, do oboru názvů `N1.N2` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="27836-136">Using the previous code segment, you can add a new class member, `C3`, to the namespace `N1.N2` as follows:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#10](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_7.cs)]  
  
 <span data-ttu-id="27836-137">Obecně platí, použijte `::` tak, aby odkazovaly alias oboru názvů nebo `global::` tak, aby odkazovaly na globální obor názvů a `.` ke kvalifikaci typy nebo členy.</span><span class="sxs-lookup"><span data-stu-id="27836-137">In general, use `::` to reference a namespace alias or `global::` to reference the global namespace and `.` to qualify types or members.</span></span>  
  
 <span data-ttu-id="27836-138">Jedná se o chybu používat `::` s alias, který odkazuje na typ místo obor názvů.</span><span class="sxs-lookup"><span data-stu-id="27836-138">It is an error to use `::` with an alias that references a type instead of a namespace.</span></span> <span data-ttu-id="27836-139">Příklad:</span><span class="sxs-lookup"><span data-stu-id="27836-139">For example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#11](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_8.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#12](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_9.cs)]  
  
 <span data-ttu-id="27836-140">Nezapomeňte, že slovo `global` není i předdefinovanou alias; proto `global.X` nemá žádný speciální význam.</span><span class="sxs-lookup"><span data-stu-id="27836-140">Remember that the word `global` is not a predefined alias; therefore, `global.X` does not have any special meaning.</span></span> <span data-ttu-id="27836-141">Operace čtení, zvláštní význam jenom v případě, že se používá s `::`.</span><span class="sxs-lookup"><span data-stu-id="27836-141">It acquires a special meaning only when it is used with `::`.</span></span>  
  
 <span data-ttu-id="27836-142">Kompilátoru upozornění CS0440 se vygeneruje, pokud definujete alias s názvem globální protože `global::` vždy odkazuje na obor názvů globální a není alias.</span><span class="sxs-lookup"><span data-stu-id="27836-142">Compiler warning CS0440 is generated if you define an alias named global because `global::` always references the global namespace and not an alias.</span></span> <span data-ttu-id="27836-143">Například následující řádek vygeneruje upozornění:</span><span class="sxs-lookup"><span data-stu-id="27836-143">For example, the following line generates the warning:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#13](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_10.cs)]  
  
 <span data-ttu-id="27836-144">Pomocí `::` s aliasy je vhodné a chrání před neočekávané zavedení další typy.</span><span class="sxs-lookup"><span data-stu-id="27836-144">Using `::` with aliases is a good idea and protects against the unexpected introduction of additional types.</span></span> <span data-ttu-id="27836-145">Představte si třeba v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="27836-145">For example, consider this example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#14](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_11.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#15](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_12.cs)]  
  
 <span data-ttu-id="27836-146">Tento postup funguje, ale pokud typu s názvem `Alias` měla být následně zavést, `Alias.` by navázat na daný typ místo.</span><span class="sxs-lookup"><span data-stu-id="27836-146">This works, but if a type named `Alias` were to subsequently be introduced, `Alias.` would bind to that type instead.</span></span> <span data-ttu-id="27836-147">Pomocí `Alias::Exception` , tomu se budou `Alias` je považován za alias oboru názvů a není pro typ zaměněny.</span><span class="sxs-lookup"><span data-stu-id="27836-147">Using `Alias::Exception` insures that `Alias` is treated as a namespace alias and not mistaken for a type.</span></span>  
  
 <span data-ttu-id="27836-148">Podívejte se na téma [postupy: použití aliasu globálního Namespace](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) Další informace ohledně `global` alias.</span><span class="sxs-lookup"><span data-stu-id="27836-148">See the topic [How to: Use the Global Namespace Alias](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) for more information regarding the `global` alias.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27836-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="27836-149">See Also</span></span>  
 [<span data-ttu-id="27836-150">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="27836-150">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="27836-151">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="27836-151">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
 [<span data-ttu-id="27836-152">Klíčová slova oboru názvů</span><span class="sxs-lookup"><span data-stu-id="27836-152">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="27836-153">. – operátor</span><span class="sxs-lookup"><span data-stu-id="27836-153">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)  
 [<span data-ttu-id="27836-154">:: – operátor</span><span class="sxs-lookup"><span data-stu-id="27836-154">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [<span data-ttu-id="27836-155">extern</span><span class="sxs-lookup"><span data-stu-id="27836-155">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)
