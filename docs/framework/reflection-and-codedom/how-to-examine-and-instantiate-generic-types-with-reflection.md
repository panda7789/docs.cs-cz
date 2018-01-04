---
title: "Postupy: Prozkoumání a vytvoření instancí obecných typů pomocí reflexe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection, generic types
- generics [.NET Framework], reflection
ms.assetid: f93b03b0-1778-43fc-bc6d-35983d210e74
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc95b8474cdf9398d5b6705cce1b98772e5add98
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-examine-and-instantiate-generic-types-with-reflection"></a><span data-ttu-id="4cc47-102">Postupy: Prozkoumání a vytvoření instancí obecných typů pomocí reflexe</span><span class="sxs-lookup"><span data-stu-id="4cc47-102">How to: Examine and Instantiate Generic Types with Reflection</span></span>
<span data-ttu-id="4cc47-103">Stejným způsobem jako informace o jiných typech se získat informace o obecných typů: prověřením <xref:System.Type> objekt, který reprezentuje obecného typu.</span><span class="sxs-lookup"><span data-stu-id="4cc47-103">Information about generic types is obtained in the same way as information about other types: by examining a <xref:System.Type> object that represents the generic type.</span></span> <span data-ttu-id="4cc47-104">Princip rozdíl je, že obecného typu má seznam <xref:System.Type> objekty, které představují jeho parametry obecného typu.</span><span class="sxs-lookup"><span data-stu-id="4cc47-104">The principle difference is that a generic type has a list of <xref:System.Type> objects representing its generic type parameters.</span></span> <span data-ttu-id="4cc47-105">První postup v této části prověří obecné typy.</span><span class="sxs-lookup"><span data-stu-id="4cc47-105">The first procedure in this section examines generic types.</span></span>  
  
 <span data-ttu-id="4cc47-106">Můžete vytvořit <xref:System.Type> objekt, který představuje vytvořený typ pomocí vazby argumenty typu do parametrů definice obecného typu.</span><span class="sxs-lookup"><span data-stu-id="4cc47-106">You can create a <xref:System.Type> object that represents a constructed type by binding type arguments to the type parameters of a generic type definition.</span></span> <span data-ttu-id="4cc47-107">Druhý postup ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="4cc47-107">The second procedure demonstrates this.</span></span>  
  
### <a name="to-examine-a-generic-type-and-its-type-parameters"></a><span data-ttu-id="4cc47-108">K prozkoumání obecného typu a jeho parametry typu</span><span class="sxs-lookup"><span data-stu-id="4cc47-108">To examine a generic type and its type parameters</span></span>  
  
1.  <span data-ttu-id="4cc47-109">Získat instanci <xref:System.Type> představující obecného typu.</span><span class="sxs-lookup"><span data-stu-id="4cc47-109">Get an instance of <xref:System.Type> that represents the generic type.</span></span> <span data-ttu-id="4cc47-110">V následujícím kódu, se získávají pomocí jazyka C# typ `typeof` – operátor (`GetType` v jazyce Visual Basic `typeid` v jazyce Visual C++).</span><span class="sxs-lookup"><span data-stu-id="4cc47-110">In the following code, the type is obtained using the C# `typeof` operator (`GetType` in Visual Basic, `typeid` in Visual C++).</span></span> <span data-ttu-id="4cc47-111">Najdete v článku <xref:System.Type> téma třída pro jiné způsoby, jak získat <xref:System.Type> objektu.</span><span class="sxs-lookup"><span data-stu-id="4cc47-111">See the <xref:System.Type> class topic for other ways to get a <xref:System.Type> object.</span></span> <span data-ttu-id="4cc47-112">Všimněte si, že v zbytek tohoto postupu je typ obsažené v metoda parametr s názvem `t`.</span><span class="sxs-lookup"><span data-stu-id="4cc47-112">Note that in the rest of this procedure, the type is contained in a method parameter named `t`.</span></span>  
  
     [!code-cpp[HowToGeneric#2](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#2)]
     [!code-csharp[HowToGeneric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#2)]
     [!code-vb[HowToGeneric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#2)]  
  
2.  <span data-ttu-id="4cc47-113">Použít <xref:System.Type.IsGenericType%2A> vlastnosti a určit, zda je obecný typ, použijte <xref:System.Type.IsGenericTypeDefinition%2A> vlastnosti k určení, zda je typ definice obecného typu.</span><span class="sxs-lookup"><span data-stu-id="4cc47-113">Use the <xref:System.Type.IsGenericType%2A> property to determine whether the type is generic, and use the <xref:System.Type.IsGenericTypeDefinition%2A> property to determine whether the type is a generic type definition.</span></span>  
  
     [!code-cpp[HowToGeneric#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#3)]
     [!code-csharp[HowToGeneric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#3)]
     [!code-vb[HowToGeneric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#3)]  
  
3.  <span data-ttu-id="4cc47-114">Získat pole, které obsahuje argumenty obecného typu, pomocí <xref:System.Type.GetGenericArguments%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="4cc47-114">Get an array that contains the generic type arguments, using the <xref:System.Type.GetGenericArguments%2A> method.</span></span>  
  
     [!code-cpp[HowToGeneric#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#4)]
     [!code-csharp[HowToGeneric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#4)]
     [!code-vb[HowToGeneric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#4)]  
  
4.  <span data-ttu-id="4cc47-115">Pro každý typ argumentu, určují, zda je parametr typu (například v definici obecného typu) nebo typu, který byl zadaný pro parametr typu (například v vytvořený typ), pomocí <xref:System.Type.IsGenericParameter%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4cc47-115">For each type argument, determine whether it is a type parameter (for example, in a generic type definition) or a type that has been specified for a type parameter (for example, in a constructed type), using the <xref:System.Type.IsGenericParameter%2A> property.</span></span>  
  
     [!code-cpp[HowToGeneric#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#5)]
     [!code-csharp[HowToGeneric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#5)]
     [!code-vb[HowToGeneric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#5)]  
  
5.  <span data-ttu-id="4cc47-116">V systému typu parametr obecného typu je reprezentována instanci <xref:System.Type>, stejně jako obyčejnou typy.</span><span class="sxs-lookup"><span data-stu-id="4cc47-116">In the type system, a generic type parameter is represented by an instance of <xref:System.Type>, just as ordinary types are.</span></span> <span data-ttu-id="4cc47-117">Následující kód zobrazí název a parametru umístění <xref:System.Type> objekt, který reprezentuje parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="4cc47-117">The following code displays the name and parameter position of a <xref:System.Type> object that represents a generic type parameter.</span></span> <span data-ttu-id="4cc47-118">Pozice parametr je trivial informace; je důležitější sledovat při kontrole parametr typu, která byla použita jako argument typu jiného obecného typu.</span><span class="sxs-lookup"><span data-stu-id="4cc47-118">The parameter position is trivial information here; it is of more interest when you are examining a type parameter that has been used as a type argument of another generic type.</span></span>  
  
     [!code-cpp[HowToGeneric#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#6)]
     [!code-csharp[HowToGeneric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#6)]
     [!code-vb[HowToGeneric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#6)]  
  
6.  <span data-ttu-id="4cc47-119">Určit základní typ omezení a omezení rozhraní parametr obecného typu pomocí <xref:System.Type.GetGenericParameterConstraints%2A> metoda získat všechna omezení v jednom poli.</span><span class="sxs-lookup"><span data-stu-id="4cc47-119">Determine the base type constraint and the interface constraints of a generic type parameter by using the <xref:System.Type.GetGenericParameterConstraints%2A> method to obtain all the constraints in a single array.</span></span> <span data-ttu-id="4cc47-120">Omezení nemusí být v libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="4cc47-120">Constraints are not guaranteed to be in any particular order.</span></span>  
  
     [!code-cpp[HowToGeneric#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#7)]
     [!code-csharp[HowToGeneric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#7)]
     [!code-vb[HowToGeneric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#7)]  
  
7.  <span data-ttu-id="4cc47-121">Použití <xref:System.Type.GenericParameterAttributes%2A> vlastnost ke zjištění zvláštní omezení pro parametr typu, jako je například požadavek, aby byl odkazového typu.</span><span class="sxs-lookup"><span data-stu-id="4cc47-121">Use the <xref:System.Type.GenericParameterAttributes%2A> property to discover the special constraints on a type parameter, such as requiring that it be a reference type.</span></span> <span data-ttu-id="4cc47-122">Vlastnost také obsahuje hodnoty, které představují odchylku, která můžete vypnout maskování, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="4cc47-122">The property also includes values that represent variance, which you can mask off as shown in the following code.</span></span>  
  
     [!code-cpp[HowToGeneric#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#8)]
     [!code-csharp[HowToGeneric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#8)]
     [!code-vb[HowToGeneric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#8)]  
  
8.  <span data-ttu-id="4cc47-123">Atributy speciální omezení jsou příznaky a příznak stejné (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>), která představuje žádné zvláštní omezení také představuje žádné kovariance a kontravariance.</span><span class="sxs-lookup"><span data-stu-id="4cc47-123">The special constraint attributes are flags, and the same flag (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>) that represents no special constraints also represents no covariance or contravariance.</span></span> <span data-ttu-id="4cc47-124">Proto k testování pro některá z těchto podmínek je nutné použít příslušné masky.</span><span class="sxs-lookup"><span data-stu-id="4cc47-124">Thus, to test for either of these conditions you must use the appropriate mask.</span></span> <span data-ttu-id="4cc47-125">V takovém případě použijte <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> izolovat příznaky zvláštní omezení.</span><span class="sxs-lookup"><span data-stu-id="4cc47-125">In this case, use <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> to isolate the special constraint flags.</span></span>  
  
     [!code-cpp[HowToGeneric#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#9)]
     [!code-csharp[HowToGeneric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#9)]
     [!code-vb[HowToGeneric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#9)]  
  
## <a name="constructing-an-instance-of-a-generic-type"></a><span data-ttu-id="4cc47-126">Vytváření instancí obecného typu</span><span class="sxs-lookup"><span data-stu-id="4cc47-126">Constructing an Instance of a Generic Type</span></span>  
 <span data-ttu-id="4cc47-127">Obecný typ je jako šablonu.</span><span class="sxs-lookup"><span data-stu-id="4cc47-127">A generic type is like a template.</span></span> <span data-ttu-id="4cc47-128">Nelze vytvořit instance ji, pokud nezadáte skutečné typy pro jeho parametry obecného typu.</span><span class="sxs-lookup"><span data-stu-id="4cc47-128">You cannot create instances of it unless you specify real types for its generic type parameters.</span></span> <span data-ttu-id="4cc47-129">K tomu v době běhu pomocí reflexe, vyžaduje <xref:System.Type.MakeGenericType%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="4cc47-129">To do this at run time, using reflection, requires the <xref:System.Type.MakeGenericType%2A> method.</span></span>  
  
#### <a name="to-construct-an-instance-of-a-generic-type"></a><span data-ttu-id="4cc47-130">K vytvoření instance obecného typu</span><span class="sxs-lookup"><span data-stu-id="4cc47-130">To construct an instance of a generic type</span></span>  
  
1.  <span data-ttu-id="4cc47-131">Získání <xref:System.Type> objekt, který reprezentuje obecného typu.</span><span class="sxs-lookup"><span data-stu-id="4cc47-131">Get a <xref:System.Type> object that represents the generic type.</span></span> <span data-ttu-id="4cc47-132">Následující kód získá obecného typu <xref:System.Collections.Generic.Dictionary%602> dvěma různými způsoby: pomocí <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> přetížení metody s řetězec popisující typ a voláním <xref:System.Type.GetGenericTypeDefinition%2A> metoda sestavené typu `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` v Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="4cc47-132">The following code gets the generic type <xref:System.Collections.Generic.Dictionary%602> in two different ways: by using the <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> method overload with a string describing the type, and by calling the <xref:System.Type.GetGenericTypeDefinition%2A> method on the constructed type `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` in Visual Basic).</span></span> <span data-ttu-id="4cc47-133"><xref:System.Type.MakeGenericType%2A> Metoda vyžaduje definice obecného typu.</span><span class="sxs-lookup"><span data-stu-id="4cc47-133">The <xref:System.Type.MakeGenericType%2A> method requires a generic type definition.</span></span>  
  
     [!code-cpp[HowToGeneric#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#10)]
     [!code-csharp[HowToGeneric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#10)]
     [!code-vb[HowToGeneric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#10)]  
  
2.  <span data-ttu-id="4cc47-134">Vytvořte pole argumenty typu nelze nahradit pro parametry typu.</span><span class="sxs-lookup"><span data-stu-id="4cc47-134">Construct an array of type arguments to substitute for the type parameters.</span></span> <span data-ttu-id="4cc47-135">Pole musí obsahovat správný počet <xref:System.Type> objekty ve stejném pořadí, jak se zobrazují v seznamu parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="4cc47-135">The array must contain the correct number of <xref:System.Type> objects, in the same order as they appear in the type parameter list.</span></span> <span data-ttu-id="4cc47-136">V tomto případě klíč (první parametr typu) je typu <xref:System.String>, a hodnoty ve slovníku jsou instancemi třídy s názvem `Example`.</span><span class="sxs-lookup"><span data-stu-id="4cc47-136">In this case, the key (first type parameter) is of type <xref:System.String>, and the values in the dictionary are instances of a class named `Example`.</span></span>  
  
     [!code-cpp[HowToGeneric#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#11)]
     [!code-csharp[HowToGeneric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#11)]
     [!code-vb[HowToGeneric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#11)]  
  
3.  <span data-ttu-id="4cc47-137">Volání <xref:System.Type.MakeGenericType%2A> metoda svázat argumenty typu do parametrů a vytvořit typ.</span><span class="sxs-lookup"><span data-stu-id="4cc47-137">Call the <xref:System.Type.MakeGenericType%2A> method to bind the type arguments to the type parameters and construct the type.</span></span>  
  
     [!code-cpp[HowToGeneric#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#12)]
     [!code-csharp[HowToGeneric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#12)]
     [!code-vb[HowToGeneric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#12)]  
  
4.  <span data-ttu-id="4cc47-138">Použití <xref:System.Activator.CreateInstance%28System.Type%29> přetížení metody pro vytvoření objektu sestavené typu.</span><span class="sxs-lookup"><span data-stu-id="4cc47-138">Use the <xref:System.Activator.CreateInstance%28System.Type%29> method overload to create an object of the constructed type.</span></span> <span data-ttu-id="4cc47-139">Následující kód ukládá dvě instance `Example` třídy v výsledná `Dictionary<String, Example>` objektu.</span><span class="sxs-lookup"><span data-stu-id="4cc47-139">The following code stores two instances of the `Example` class in the resulting `Dictionary<String, Example>` object.</span></span>  
  
     [!code-cpp[HowToGeneric#13](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#13)]
     [!code-csharp[HowToGeneric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#13)]
     [!code-vb[HowToGeneric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="4cc47-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="4cc47-140">Example</span></span>  
 <span data-ttu-id="4cc47-141">Následující příklad kódu definuje `DisplayGenericType` metoda sloužící ke zkoumání definice obecného typu a sestavené typy používá v kódu a zobrazení jejich informací.</span><span class="sxs-lookup"><span data-stu-id="4cc47-141">The following code example defines a `DisplayGenericType` method to examine the generic type definitions and constructed types used in the code and display their information.</span></span> <span data-ttu-id="4cc47-142">`DisplayGenericType` Metoda ukazuje způsob použití <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A>, a <xref:System.Type.GenericParameterPosition%2A> vlastnosti a <xref:System.Type.GetGenericArguments%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="4cc47-142">The `DisplayGenericType` method shows how to use the <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A>, and <xref:System.Type.GenericParameterPosition%2A> properties and the <xref:System.Type.GetGenericArguments%2A> method.</span></span>  
  
 <span data-ttu-id="4cc47-143">Tento příklad také definuje `DisplayGenericParameter` metoda sloužící ke zkoumání parametr obecného typu a zobrazit její omezení.</span><span class="sxs-lookup"><span data-stu-id="4cc47-143">The example also defines a `DisplayGenericParameter` method to examine a generic type parameter and display its constraints.</span></span>  
  
 <span data-ttu-id="4cc47-144">Příklad kódu definuje sadu typů testu, včetně obecného typu, který ukazuje parametr omezení typu a ukazuje, jak zobrazit informace o těchto typech.</span><span class="sxs-lookup"><span data-stu-id="4cc47-144">The code example defines a set of test types, including a generic type that illustrates type parameter constraints, and shows how to display information about these types.</span></span>  
  
 <span data-ttu-id="4cc47-145">Tento příklad vytvoří určitého typu <xref:System.Collections.Generic.Dictionary%602> třída vytvořením pole typu argumentů a volání <xref:System.Type.MakeGenericType%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="4cc47-145">The example constructs a type from the <xref:System.Collections.Generic.Dictionary%602> class by creating an array of type arguments and calling the <xref:System.Type.MakeGenericType%2A> method.</span></span> <span data-ttu-id="4cc47-146">Program porovná <xref:System.Type> objekt vytvořený <xref:System.Type.MakeGenericType%2A> s <xref:System.Type> objektu získat pomocí `typeof` (`GetType` v jazyce Visual Basic), ukázka, aby byly stejné.</span><span class="sxs-lookup"><span data-stu-id="4cc47-146">The program compares the <xref:System.Type> object constructed using <xref:System.Type.MakeGenericType%2A> with a <xref:System.Type> object obtained using `typeof` (`GetType` in Visual Basic), demonstrating that they are the same.</span></span> <span data-ttu-id="4cc47-147">Podobně, program používá <xref:System.Type.GetGenericTypeDefinition%2A> metoda získat definice obecného typu sestavené typu a porovná ho k <xref:System.Type> objekt reprezentující <xref:System.Collections.Generic.Dictionary%602> – třída.</span><span class="sxs-lookup"><span data-stu-id="4cc47-147">Similarly, the program uses the <xref:System.Type.GetGenericTypeDefinition%2A> method to obtain the generic type definition of the constructed type, and compares it to the <xref:System.Type> object representing the <xref:System.Collections.Generic.Dictionary%602> class.</span></span>  
  
 [!code-cpp[HowToGeneric#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#1)]
 [!code-csharp[HowToGeneric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#1)]
 [!code-vb[HowToGeneric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4cc47-148">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="4cc47-148">Compiling the Code</span></span>  
  
-   <span data-ttu-id="4cc47-149">Obsahuje kód jazyka C# `using` příkazy (`Imports` v jazyce Visual Basic) potřebné pro kompilaci.</span><span class="sxs-lookup"><span data-stu-id="4cc47-149">The code contains the C# `using` statements (`Imports` in Visual Basic) necessary for compilation.</span></span>  
  
-   <span data-ttu-id="4cc47-150">Nejsou vyžadovány žádné odkazy na další sestavení.</span><span class="sxs-lookup"><span data-stu-id="4cc47-150">No additional assembly references are required.</span></span>  
  
-   <span data-ttu-id="4cc47-151">Kompilace kódu na příkazovém řádku pomocí csc.exe, vbc.exe nebo cl.exe.</span><span class="sxs-lookup"><span data-stu-id="4cc47-151">Compile the code at the command line using csc.exe, vbc.exe, or cl.exe.</span></span> <span data-ttu-id="4cc47-152">Kompilace kódu v sadě Visual Studio, umístěte ho do šablony projektu konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="4cc47-152">To compile the code in Visual Studio, place it in a console application project template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cc47-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="4cc47-153">See Also</span></span>  
 <xref:System.Type>  
 <xref:System.Reflection.MethodInfo>  
 [<span data-ttu-id="4cc47-154">Reflexe a obecné typy</span><span class="sxs-lookup"><span data-stu-id="4cc47-154">Reflection and Generic Types</span></span>](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)  
 [<span data-ttu-id="4cc47-155">Zobrazení informací o typu</span><span class="sxs-lookup"><span data-stu-id="4cc47-155">Viewing Type Information</span></span>](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)  
 [<span data-ttu-id="4cc47-156">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="4cc47-156">Generics</span></span>](../../../docs/standard/generics/index.md)
