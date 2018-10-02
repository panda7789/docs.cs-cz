---
title: Použití oboru názvů (Průvodce programováním v C#)
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: 81876d1818a6e82764e4aea0ae2b6f9e091f0ba3
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48034977"
---
# <a name="using-namespaces-c-programming-guide"></a><span data-ttu-id="671eb-102">Použití oboru názvů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="671eb-102">Using Namespaces (C# Programming Guide)</span></span>
<span data-ttu-id="671eb-103">V aplikacích jazyka C# dvě možnosti, jak se hojně používají obory názvů.</span><span class="sxs-lookup"><span data-stu-id="671eb-103">Namespaces are heavily used within C# programs in two ways.</span></span> <span data-ttu-id="671eb-104">Za prvé tříd rozhraní .NET Framework pomocí oborů názvů můžete organizovat jeho mnoho tříd.</span><span class="sxs-lookup"><span data-stu-id="671eb-104">Firstly, the .NET Framework classes use namespaces to organize its many classes.</span></span> <span data-ttu-id="671eb-105">Za druhé deklarující vlastní obory názvů umožňují omezit rozsah třídy a metody názvy ve větších programovací projektů.</span><span class="sxs-lookup"><span data-stu-id="671eb-105">Secondly, declaring your own namespaces can help control the scope of class and method names in larger programming projects.</span></span>  
  
## <a name="accessing-namespaces"></a><span data-ttu-id="671eb-106">Přístup k obory názvů</span><span class="sxs-lookup"><span data-stu-id="671eb-106">Accessing Namespaces</span></span>  
 <span data-ttu-id="671eb-107">Většina aplikací C# začínat část `using` direktivy.</span><span class="sxs-lookup"><span data-stu-id="671eb-107">Most C# applications begin with a section of `using` directives.</span></span> <span data-ttu-id="671eb-108">Tato část obsahuje seznam oborů názvů, že aplikace budou často používat a ušetří programátor zadáním plně kvalifikovaného názvu pokaždé, když se používá metodu, která je součástí.</span><span class="sxs-lookup"><span data-stu-id="671eb-108">This section lists the namespaces that the application will be using frequently, and saves the programmer from specifying a fully qualified name every time that a method that is contained within is used.</span></span>  
  
 <span data-ttu-id="671eb-109">Například přidáním řádku:</span><span class="sxs-lookup"><span data-stu-id="671eb-109">For example, by including the line:</span></span>  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_1.cs)]  
  
 <span data-ttu-id="671eb-110">Na začátku programu můžete použít programátor kód:</span><span class="sxs-lookup"><span data-stu-id="671eb-110">At the start of a program, the programmer can use the code:</span></span>  
  
 [!code-csharp[csProgGuide#31](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_2.cs)]  
  
 <span data-ttu-id="671eb-111">Namísto:</span><span class="sxs-lookup"><span data-stu-id="671eb-111">Instead of:</span></span>  
  
 [!code-csharp[csProgGuide#30](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_3.cs)]  
  
## <a name="namespace-aliases"></a><span data-ttu-id="671eb-112">Aliasy Namespace</span><span class="sxs-lookup"><span data-stu-id="671eb-112">Namespace Aliases</span></span>  
 <span data-ttu-id="671eb-113">[Direktiva using](../../../csharp/language-reference/keywords/using-directive.md) lze také použít k vytvoření zástupce pro [obor názvů](../../../csharp/language-reference/keywords/namespace.md).</span><span class="sxs-lookup"><span data-stu-id="671eb-113">The [using Directive](../../../csharp/language-reference/keywords/using-directive.md) can also be used to create an alias for a [namespace](../../../csharp/language-reference/keywords/namespace.md).</span></span> <span data-ttu-id="671eb-114">Pokud používáte doposud zapsán obor názvů, který obsahuje vnořené obory názvů, můžete chtít deklarování aliasu. k poskytování zjednodušený způsob odkazujete na jednu zejména, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="671eb-114">For example, if you are using a previously written namespace that contains nested namespaces, you might want to declare an alias to provide a shorthand way of referencing one in particular, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#7](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_4.cs)]  
  
## <a name="using-namespaces-to-control-scope"></a><span data-ttu-id="671eb-115">Použití oboru názvů do oboru ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="671eb-115">Using Namespaces to control scope</span></span>  
 <span data-ttu-id="671eb-116">`namespace` – Klíčové slovo se používá k deklarování oboru.</span><span class="sxs-lookup"><span data-stu-id="671eb-116">The `namespace` keyword is used to declare a scope.</span></span> <span data-ttu-id="671eb-117">Schopnost vytvářet oborů v rámci svého projektu pomáhá organizovat kód a umožňuje vytvářet globálně jedinečných typů.</span><span class="sxs-lookup"><span data-stu-id="671eb-117">The ability to create scopes within your project helps organize code and lets you create globally-unique types.</span></span> <span data-ttu-id="671eb-118">V následujícím příkladu třída s názvem `SampleClass` je definována v dva obory názvů, jeden vnořit do druhé.</span><span class="sxs-lookup"><span data-stu-id="671eb-118">In the following example, a class titled `SampleClass` is defined in two namespaces, one nested inside the other.</span></span> <span data-ttu-id="671eb-119">[. Operátor](../../../csharp/language-reference/operators/member-access-operator.md) se používá k rozlišení, které metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="671eb-119">The [. Operator](../../../csharp/language-reference/operators/member-access-operator.md) is used to differentiate which method gets called.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#8](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_5.cs)]  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="671eb-120">Plně kvalifikované názvy</span><span class="sxs-lookup"><span data-stu-id="671eb-120">Fully Qualified Names</span></span>  
 <span data-ttu-id="671eb-121">Obory názvů a typy mají jedinečné názvy popsal plně kvalifikované názvy, které indikují logické hierarchie.</span><span class="sxs-lookup"><span data-stu-id="671eb-121">Namespaces and types have unique titles described by fully qualified names that indicate a logical hierarchy.</span></span> <span data-ttu-id="671eb-122">Například příkaz `A.B` vyplývá, že `A` je název oboru názvů nebo typ, a `B` je vnořená do ho.</span><span class="sxs-lookup"><span data-stu-id="671eb-122">For example, the statement `A.B` implies that `A` is the name of the namespace or type, and `B` is nested inside it.</span></span>  
  
 <span data-ttu-id="671eb-123">V následujícím příkladu jsou vnořené třídy a obory názvů.</span><span class="sxs-lookup"><span data-stu-id="671eb-123">In the following example, there are nested classes and namespaces.</span></span> <span data-ttu-id="671eb-124">Plně kvalifikovaný název je označen jako komentář po každé entity.</span><span class="sxs-lookup"><span data-stu-id="671eb-124">The fully qualified name is indicated as a comment following each entity.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#9](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_6.cs)]  
  
 <span data-ttu-id="671eb-125">V předchozí segment kódu:</span><span class="sxs-lookup"><span data-stu-id="671eb-125">In the previous code segment:</span></span>  
  
-   <span data-ttu-id="671eb-126">Obor názvů `N1` je členem skupiny globální obor názvů.</span><span class="sxs-lookup"><span data-stu-id="671eb-126">The namespace `N1` is a member of the global namespace.</span></span> <span data-ttu-id="671eb-127">Jeho plně kvalifikovaný název je `N1`.</span><span class="sxs-lookup"><span data-stu-id="671eb-127">Its fully qualified name is `N1`.</span></span>  
  
-   <span data-ttu-id="671eb-128">Obor názvů `N2` je členem skupiny `N1`.</span><span class="sxs-lookup"><span data-stu-id="671eb-128">The namespace `N2` is a member of `N1`.</span></span> <span data-ttu-id="671eb-129">Jeho plně kvalifikovaný název je `N1.N2`.</span><span class="sxs-lookup"><span data-stu-id="671eb-129">Its fully qualified name is `N1.N2`.</span></span>  
  
-   <span data-ttu-id="671eb-130">Třída `C1` je členem skupiny `N1`.</span><span class="sxs-lookup"><span data-stu-id="671eb-130">The class `C1` is a member of `N1`.</span></span> <span data-ttu-id="671eb-131">Jeho plně kvalifikovaný název je `N1.C1`.</span><span class="sxs-lookup"><span data-stu-id="671eb-131">Its fully qualified name is `N1.C1`.</span></span>  
  
-   <span data-ttu-id="671eb-132">Název třídy `C2` dvakrát se používá v tomto kódu.</span><span class="sxs-lookup"><span data-stu-id="671eb-132">The class name `C2` is used two times in this code.</span></span> <span data-ttu-id="671eb-133">Plně kvalifikované názvy jsou však jedinečné.</span><span class="sxs-lookup"><span data-stu-id="671eb-133">However, the fully qualified names are unique.</span></span> <span data-ttu-id="671eb-134">První výskyt `C2` je deklarována uvnitř `C1`, proto jeho plně kvalifikovaný název je: `N1.C1.C2`.</span><span class="sxs-lookup"><span data-stu-id="671eb-134">The first instance of `C2` is declared inside `C1`; therefore, its fully qualified name is: `N1.C1.C2`.</span></span> <span data-ttu-id="671eb-135">Druhou instanci `C2` je deklarován uvnitř oboru názvů `N2`, proto jeho plně kvalifikovaný název je `N1.N2.C2`.</span><span class="sxs-lookup"><span data-stu-id="671eb-135">The second instance of `C2` is declared inside a namespace `N2`; therefore, its fully qualified name is `N1.N2.C2`.</span></span>  
  
 <span data-ttu-id="671eb-136">Pomocí předchozího segmentu kódu, můžete přidat nového člena třídy `C3`, do oboru názvů `N1.N2` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="671eb-136">Using the previous code segment, you can add a new class member, `C3`, to the namespace `N1.N2` as follows:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#10](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_7.cs)]  
  
 <span data-ttu-id="671eb-137">Obecně platí, `::` k odkazování aliasu oboru názvů nebo `global::` k odkazu na globální obor názvů a `.` kvalifikovat typy nebo členy.</span><span class="sxs-lookup"><span data-stu-id="671eb-137">In general, use `::` to reference a namespace alias or `global::` to reference the global namespace and `.` to qualify types or members.</span></span>  
  
 <span data-ttu-id="671eb-138">Jedná se o chybu použití `::` s aliasem, který odkazuje na typ místo oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="671eb-138">It is an error to use `::` with an alias that references a type instead of a namespace.</span></span> <span data-ttu-id="671eb-139">Příklad:</span><span class="sxs-lookup"><span data-stu-id="671eb-139">For example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#11](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_8.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#12](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_9.cs)]  
  
 <span data-ttu-id="671eb-140">Nezapomeňte, že slovo `global` alias, proto není i předdefinovanou `global.X` nemá žádný speciální význam.</span><span class="sxs-lookup"><span data-stu-id="671eb-140">Remember that the word `global` is not a predefined alias; therefore, `global.X` does not have any special meaning.</span></span> <span data-ttu-id="671eb-141">Získá zvláštní význam pouze v případě, že se použije s parametrem `::`.</span><span class="sxs-lookup"><span data-stu-id="671eb-141">It acquires a special meaning only when it is used with `::`.</span></span>  
  
 <span data-ttu-id="671eb-142">Kompilátor varování CS0440 se vygeneruje při definování aliasu s názvem global protože `global::` vždy odkazuje na globální obor názvů, ne na alias.</span><span class="sxs-lookup"><span data-stu-id="671eb-142">Compiler warning CS0440 is generated if you define an alias named global because `global::` always references the global namespace and not an alias.</span></span> <span data-ttu-id="671eb-143">Například následující řádek vygeneruje upozornění:</span><span class="sxs-lookup"><span data-stu-id="671eb-143">For example, the following line generates the warning:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#13](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_10.cs)]  
  
 <span data-ttu-id="671eb-144">Pomocí `::` s aliasy je vhodné a chrání před neočekávaným Úvod další typy.</span><span class="sxs-lookup"><span data-stu-id="671eb-144">Using `::` with aliases is a good idea and protects against the unexpected introduction of additional types.</span></span> <span data-ttu-id="671eb-145">Představte si třeba v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="671eb-145">For example, consider this example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#14](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_11.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#15](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_12.cs)]  
  
 <span data-ttu-id="671eb-146">Tento postup funguje, ale pokud typ s názvem `Alias` bylo následně zavést `Alias.` by místo toho vázat k danému typu.</span><span class="sxs-lookup"><span data-stu-id="671eb-146">This works, but if a type named `Alias` were to subsequently be introduced, `Alias.` would bind to that type instead.</span></span> <span data-ttu-id="671eb-147">Pomocí `Alias::Exception` , která díky `Alias` je považován za aliasu oboru názvů a není pro typ zaměněny.</span><span class="sxs-lookup"><span data-stu-id="671eb-147">Using `Alias::Exception` insures that `Alias` is treated as a namespace alias and not mistaken for a type.</span></span>  
  
 <span data-ttu-id="671eb-148">Naleznete v tématu [postupy: použití aliasu globálního Namespace](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) Další informace týkající `global` alias.</span><span class="sxs-lookup"><span data-stu-id="671eb-148">See the topic [How to: Use the Global Namespace Alias](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) for more information regarding the `global` alias.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="671eb-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="671eb-149">See Also</span></span>

- [<span data-ttu-id="671eb-150">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="671eb-150">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="671eb-151">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="671eb-151">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
- [<span data-ttu-id="671eb-152">Klíčová slova oboru názvů</span><span class="sxs-lookup"><span data-stu-id="671eb-152">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
- [<span data-ttu-id="671eb-153">. – operátor</span><span class="sxs-lookup"><span data-stu-id="671eb-153">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)  
- [<span data-ttu-id="671eb-154">:: – operátor</span><span class="sxs-lookup"><span data-stu-id="671eb-154">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
- [<span data-ttu-id="671eb-155">extern</span><span class="sxs-lookup"><span data-stu-id="671eb-155">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)
