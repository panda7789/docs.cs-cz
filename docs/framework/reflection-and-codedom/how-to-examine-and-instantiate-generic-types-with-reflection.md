---
title: 'Postupy: Prozkoumání a vytvoření instancí obecných typů pomocí reflexe'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection, generic types
- generics [.NET Framework], reflection
ms.assetid: f93b03b0-1778-43fc-bc6d-35983d210e74
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 41070b5d51f0b613d7a6bbbc72b24a8c1793964d
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586110"
---
# <a name="how-to-examine-and-instantiate-generic-types-with-reflection"></a><span data-ttu-id="1d411-102">Postupy: Prozkoumání a vytvoření instancí obecných typů pomocí reflexe</span><span class="sxs-lookup"><span data-stu-id="1d411-102">How to: Examine and Instantiate Generic Types with Reflection</span></span>
<span data-ttu-id="1d411-103">Získat informace o obecných typů stejným způsobem jako informace o ostatních typech: prozkoumáním <xref:System.Type> objekt, který reprezentuje obecného typu.</span><span class="sxs-lookup"><span data-stu-id="1d411-103">Information about generic types is obtained in the same way as information about other types: by examining a <xref:System.Type> object that represents the generic type.</span></span> <span data-ttu-id="1d411-104">Hlavní rozdíl je, že obecný typ obsahuje seznam <xref:System.Type> reprezentují jeho parametry obecného typu.</span><span class="sxs-lookup"><span data-stu-id="1d411-104">The principle difference is that a generic type has a list of <xref:System.Type> objects representing its generic type parameters.</span></span> <span data-ttu-id="1d411-105">První postup v této části prozkoumá obecných typů.</span><span class="sxs-lookup"><span data-stu-id="1d411-105">The first procedure in this section examines generic types.</span></span>  
  
 <span data-ttu-id="1d411-106">Můžete vytvořit <xref:System.Type> objekt, který reprezentuje konstruovaný typ argumenty typu vazby parametrů typu v definici obecného typu.</span><span class="sxs-lookup"><span data-stu-id="1d411-106">You can create a <xref:System.Type> object that represents a constructed type by binding type arguments to the type parameters of a generic type definition.</span></span> <span data-ttu-id="1d411-107">Druhý postup ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="1d411-107">The second procedure demonstrates this.</span></span>  
  
### <a name="to-examine-a-generic-type-and-its-type-parameters"></a><span data-ttu-id="1d411-108">Prozkoumat obecného typu a jeho parametry typu</span><span class="sxs-lookup"><span data-stu-id="1d411-108">To examine a generic type and its type parameters</span></span>  
  
1. <span data-ttu-id="1d411-109">Získat instanci <xref:System.Type> , která představuje obecného typu.</span><span class="sxs-lookup"><span data-stu-id="1d411-109">Get an instance of <xref:System.Type> that represents the generic type.</span></span> <span data-ttu-id="1d411-110">V následujícím kódu je získat pomocí typu C# `typeof` – operátor (`GetType` v jazyce Visual Basic `typeid` v jazyce Visual C++).</span><span class="sxs-lookup"><span data-stu-id="1d411-110">In the following code, the type is obtained using the C# `typeof` operator (`GetType` in Visual Basic, `typeid` in Visual C++).</span></span> <span data-ttu-id="1d411-111">Najdete v článku <xref:System.Type> tématu třídy pro další způsoby, jak získat <xref:System.Type> objektu.</span><span class="sxs-lookup"><span data-stu-id="1d411-111">See the <xref:System.Type> class topic for other ways to get a <xref:System.Type> object.</span></span> <span data-ttu-id="1d411-112">Všimněte si, že ve zbývající části tohoto postupu, je typ obsažen v parametru metody s názvem `t`.</span><span class="sxs-lookup"><span data-stu-id="1d411-112">Note that in the rest of this procedure, the type is contained in a method parameter named `t`.</span></span>  
  
     [!code-cpp[HowToGeneric#2](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#2)]
     [!code-csharp[HowToGeneric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#2)]
     [!code-vb[HowToGeneric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#2)]  
  
2. <span data-ttu-id="1d411-113">Použít <xref:System.Type.IsGenericType%2A> vlastnosti k určení, zda je typ obecný a použít <xref:System.Type.IsGenericTypeDefinition%2A> a určí, zda je typ definice obecného typu.</span><span class="sxs-lookup"><span data-stu-id="1d411-113">Use the <xref:System.Type.IsGenericType%2A> property to determine whether the type is generic, and use the <xref:System.Type.IsGenericTypeDefinition%2A> property to determine whether the type is a generic type definition.</span></span>  
  
     [!code-cpp[HowToGeneric#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#3)]
     [!code-csharp[HowToGeneric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#3)]
     [!code-vb[HowToGeneric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#3)]  
  
3. <span data-ttu-id="1d411-114">Získat pole obsahující argumenty obecného typu, pomocí <xref:System.Type.GetGenericArguments%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1d411-114">Get an array that contains the generic type arguments, using the <xref:System.Type.GetGenericArguments%2A> method.</span></span>  
  
     [!code-cpp[HowToGeneric#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#4)]
     [!code-csharp[HowToGeneric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#4)]
     [!code-vb[HowToGeneric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#4)]  
  
4. <span data-ttu-id="1d411-115">Pro každý typ argumentu, určete, zda je parametr typu (například v definici obecného typu) nebo typ, který se zadal pro parametr typu (například v konstruovaný typ), pomocí <xref:System.Type.IsGenericParameter%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1d411-115">For each type argument, determine whether it is a type parameter (for example, in a generic type definition) or a type that has been specified for a type parameter (for example, in a constructed type), using the <xref:System.Type.IsGenericParameter%2A> property.</span></span>  
  
     [!code-cpp[HowToGeneric#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#5)]
     [!code-csharp[HowToGeneric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#5)]
     [!code-vb[HowToGeneric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#5)]  
  
5. <span data-ttu-id="1d411-116">V systému typů, parametr obecného typu je reprezentována instance <xref:System.Type>, stejně jako běžné typy.</span><span class="sxs-lookup"><span data-stu-id="1d411-116">In the type system, a generic type parameter is represented by an instance of <xref:System.Type>, just as ordinary types are.</span></span> <span data-ttu-id="1d411-117">Následující kód zobrazí název a parametru umístění <xref:System.Type> objekt, který reprezentuje parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="1d411-117">The following code displays the name and parameter position of a <xref:System.Type> object that represents a generic type parameter.</span></span> <span data-ttu-id="1d411-118">Pozice parametru je triviální informace. je důležitější, když zkoumáte parametr typu, který se použil jako argument typu jiným obecným typem.</span><span class="sxs-lookup"><span data-stu-id="1d411-118">The parameter position is trivial information here; it is of more interest when you are examining a type parameter that has been used as a type argument of another generic type.</span></span>  
  
     [!code-cpp[HowToGeneric#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#6)]
     [!code-csharp[HowToGeneric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#6)]
     [!code-vb[HowToGeneric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#6)]  
  
6. <span data-ttu-id="1d411-119">Určit základní typ omezení a interface omezení parametru obecného typu pomocí <xref:System.Type.GetGenericParameterConstraints%2A> metodu k získání všech omezení jedno pole.</span><span class="sxs-lookup"><span data-stu-id="1d411-119">Determine the base type constraint and the interface constraints of a generic type parameter by using the <xref:System.Type.GetGenericParameterConstraints%2A> method to obtain all the constraints in a single array.</span></span> <span data-ttu-id="1d411-120">Omezení nemusí být v libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="1d411-120">Constraints are not guaranteed to be in any particular order.</span></span>  
  
     [!code-cpp[HowToGeneric#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#7)]
     [!code-csharp[HowToGeneric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#7)]
     [!code-vb[HowToGeneric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#7)]  
  
7. <span data-ttu-id="1d411-121">Použití <xref:System.Type.GenericParameterAttributes%2A> vlastnost ke zjištění zvláštní omezení pro parametr typu, třeba vyžadovat, aby být odkazovým typem.</span><span class="sxs-lookup"><span data-stu-id="1d411-121">Use the <xref:System.Type.GenericParameterAttributes%2A> property to discover the special constraints on a type parameter, such as requiring that it be a reference type.</span></span> <span data-ttu-id="1d411-122">Vlastnost také obsahuje hodnoty, které představují odchylku, což může zastínit vypnout, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="1d411-122">The property also includes values that represent variance, which you can mask off as shown in the following code.</span></span>  
  
     [!code-cpp[HowToGeneric#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#8)]
     [!code-csharp[HowToGeneric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#8)]
     [!code-vb[HowToGeneric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#8)]  
  
8. <span data-ttu-id="1d411-123">Atributy zvláštní omezení jsou příznaky a stejný příznak (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>), která představuje žádné zvláštní omezení taky představuje žádné kovariance a kontravariance.</span><span class="sxs-lookup"><span data-stu-id="1d411-123">The special constraint attributes are flags, and the same flag (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>) that represents no special constraints also represents no covariance or contravariance.</span></span> <span data-ttu-id="1d411-124">Díky tomu se k otestování pro některý z těchto podmínek je nutné použít odpovídající masku.</span><span class="sxs-lookup"><span data-stu-id="1d411-124">Thus, to test for either of these conditions you must use the appropriate mask.</span></span> <span data-ttu-id="1d411-125">V takovém případě použijte <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> izolovat příznaky zvláštní omezení.</span><span class="sxs-lookup"><span data-stu-id="1d411-125">In this case, use <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> to isolate the special constraint flags.</span></span>  
  
     [!code-cpp[HowToGeneric#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#9)]
     [!code-csharp[HowToGeneric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#9)]
     [!code-vb[HowToGeneric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#9)]  
  
## <a name="constructing-an-instance-of-a-generic-type"></a><span data-ttu-id="1d411-126">Vytváření Instance obecného typu</span><span class="sxs-lookup"><span data-stu-id="1d411-126">Constructing an Instance of a Generic Type</span></span>  
 <span data-ttu-id="1d411-127">Obecný typ je jako šablonu.</span><span class="sxs-lookup"><span data-stu-id="1d411-127">A generic type is like a template.</span></span> <span data-ttu-id="1d411-128">Nelze vytvořit instance ji, pokud neurčíte skutečné typy pro parametry obecného typu.</span><span class="sxs-lookup"><span data-stu-id="1d411-128">You cannot create instances of it unless you specify real types for its generic type parameters.</span></span> <span data-ttu-id="1d411-129">Chcete-li to provést v době běhu pomocí reflexe, vyžaduje <xref:System.Type.MakeGenericType%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1d411-129">To do this at run time, using reflection, requires the <xref:System.Type.MakeGenericType%2A> method.</span></span>  
  
#### <a name="to-construct-an-instance-of-a-generic-type"></a><span data-ttu-id="1d411-130">K vytvoření instance obecného typu</span><span class="sxs-lookup"><span data-stu-id="1d411-130">To construct an instance of a generic type</span></span>  
  
1. <span data-ttu-id="1d411-131">Získání <xref:System.Type> objekt, který reprezentuje obecného typu.</span><span class="sxs-lookup"><span data-stu-id="1d411-131">Get a <xref:System.Type> object that represents the generic type.</span></span> <span data-ttu-id="1d411-132">Následující kód načte obecného typu <xref:System.Collections.Generic.Dictionary%602> dvěma různými způsoby: pomocí <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> přetížení metody řetězec, který popisuje typ a ve volání <xref:System.Type.GetGenericTypeDefinition%2A> metodu na konstruovaný typ `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` v Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="1d411-132">The following code gets the generic type <xref:System.Collections.Generic.Dictionary%602> in two different ways: by using the <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> method overload with a string describing the type, and by calling the <xref:System.Type.GetGenericTypeDefinition%2A> method on the constructed type `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` in Visual Basic).</span></span> <span data-ttu-id="1d411-133"><xref:System.Type.MakeGenericType%2A> Metoda vyžaduje definici obecného typu.</span><span class="sxs-lookup"><span data-stu-id="1d411-133">The <xref:System.Type.MakeGenericType%2A> method requires a generic type definition.</span></span>  
  
     [!code-cpp[HowToGeneric#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#10)]
     [!code-csharp[HowToGeneric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#10)]
     [!code-vb[HowToGeneric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#10)]  
  
2. <span data-ttu-id="1d411-134">Vytvoření pole argumentů typu pro nahrazení pro parametry typu.</span><span class="sxs-lookup"><span data-stu-id="1d411-134">Construct an array of type arguments to substitute for the type parameters.</span></span> <span data-ttu-id="1d411-135">Pole musí obsahovat správný počet <xref:System.Type> objekty ve stejném pořadí, jak se objeví v seznamu parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="1d411-135">The array must contain the correct number of <xref:System.Type> objects, in the same order as they appear in the type parameter list.</span></span> <span data-ttu-id="1d411-136">V takovém případě klíč (první parametr typu) je typu <xref:System.String>, a hodnoty ve slovníku jsou instance třídy s názvem `Example`.</span><span class="sxs-lookup"><span data-stu-id="1d411-136">In this case, the key (first type parameter) is of type <xref:System.String>, and the values in the dictionary are instances of a class named `Example`.</span></span>  
  
     [!code-cpp[HowToGeneric#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#11)]
     [!code-csharp[HowToGeneric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#11)]
     [!code-vb[HowToGeneric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#11)]  
  
3. <span data-ttu-id="1d411-137">Volání <xref:System.Type.MakeGenericType%2A> způsob svázání parametrů typu argumentů typu a vytvořit tento typ.</span><span class="sxs-lookup"><span data-stu-id="1d411-137">Call the <xref:System.Type.MakeGenericType%2A> method to bind the type arguments to the type parameters and construct the type.</span></span>  
  
     [!code-cpp[HowToGeneric#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#12)]
     [!code-csharp[HowToGeneric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#12)]
     [!code-vb[HowToGeneric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#12)]  
  
4. <span data-ttu-id="1d411-138">Použití <xref:System.Activator.CreateInstance%28System.Type%29> přetížení metody pro vytvoření objektu konstruovaný typ.</span><span class="sxs-lookup"><span data-stu-id="1d411-138">Use the <xref:System.Activator.CreateInstance%28System.Type%29> method overload to create an object of the constructed type.</span></span> <span data-ttu-id="1d411-139">Následující kód obsahuje dvě instance `Example` třídy ve výsledné `Dictionary<String, Example>` objektu.</span><span class="sxs-lookup"><span data-stu-id="1d411-139">The following code stores two instances of the `Example` class in the resulting `Dictionary<String, Example>` object.</span></span>  
  
     [!code-cpp[HowToGeneric#13](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#13)]
     [!code-csharp[HowToGeneric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#13)]
     [!code-vb[HowToGeneric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="1d411-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d411-140">Example</span></span>  
 <span data-ttu-id="1d411-141">Následující příklad kódu definuje `DisplayGenericType` metoda k prozkoumání definice obecného typu a typy konstrukcí používá v kódu a zobrazit jejich informace.</span><span class="sxs-lookup"><span data-stu-id="1d411-141">The following code example defines a `DisplayGenericType` method to examine the generic type definitions and constructed types used in the code and display their information.</span></span> <span data-ttu-id="1d411-142">`DisplayGenericType` Metoda ukazuje způsob použití <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A>, a <xref:System.Type.GenericParameterPosition%2A> vlastnosti a <xref:System.Type.GetGenericArguments%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="1d411-142">The `DisplayGenericType` method shows how to use the <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A>, and <xref:System.Type.GenericParameterPosition%2A> properties and the <xref:System.Type.GetGenericArguments%2A> method.</span></span>  
  
 <span data-ttu-id="1d411-143">Příklad také definuje `DisplayGenericParameter` metoda sloužící ke zkoumání parametr obecného typu a zobrazit jeho omezení.</span><span class="sxs-lookup"><span data-stu-id="1d411-143">The example also defines a `DisplayGenericParameter` method to examine a generic type parameter and display its constraints.</span></span>  
  
 <span data-ttu-id="1d411-144">Příklad kódu definuje sadu typů testů, včetně obecného typu, který znázorňuje omezeními parametrů typů a ukazuje, jak zobrazit informace o těchto typech.</span><span class="sxs-lookup"><span data-stu-id="1d411-144">The code example defines a set of test types, including a generic type that illustrates type parameter constraints, and shows how to display information about these types.</span></span>  
  
 <span data-ttu-id="1d411-145">Tento příklad vytvoří typ z <xref:System.Collections.Generic.Dictionary%602> třídy vytvořením pole argumentů typu a volání <xref:System.Type.MakeGenericType%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1d411-145">The example constructs a type from the <xref:System.Collections.Generic.Dictionary%602> class by creating an array of type arguments and calling the <xref:System.Type.MakeGenericType%2A> method.</span></span> <span data-ttu-id="1d411-146">Porovná program <xref:System.Type> přiřazený objekt vytvořený pomocí <xref:System.Type.MakeGenericType%2A> s <xref:System.Type> objektu pomocí `typeof` (`GetType` v jazyce Visual Basic), představením toho, že jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="1d411-146">The program compares the <xref:System.Type> object constructed using <xref:System.Type.MakeGenericType%2A> with a <xref:System.Type> object obtained using `typeof` (`GetType` in Visual Basic), demonstrating that they are the same.</span></span> <span data-ttu-id="1d411-147">Podobně program používá <xref:System.Type.GetGenericTypeDefinition%2A> metoda získat definici obecných typů konstruovaný typ a porovná ji <xref:System.Type> objekt představující <xref:System.Collections.Generic.Dictionary%602> třídy.</span><span class="sxs-lookup"><span data-stu-id="1d411-147">Similarly, the program uses the <xref:System.Type.GetGenericTypeDefinition%2A> method to obtain the generic type definition of the constructed type, and compares it to the <xref:System.Type> object representing the <xref:System.Collections.Generic.Dictionary%602> class.</span></span>  
  
 [!code-cpp[HowToGeneric#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#1)]
 [!code-csharp[HowToGeneric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#1)]
 [!code-vb[HowToGeneric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1d411-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d411-148">See also</span></span>

- <xref:System.Type>
- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="1d411-149">Reflexe a obecné typy</span><span class="sxs-lookup"><span data-stu-id="1d411-149">Reflection and Generic Types</span></span>](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)
- [<span data-ttu-id="1d411-150">Zobrazení informací o typu</span><span class="sxs-lookup"><span data-stu-id="1d411-150">Viewing Type Information</span></span>](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
- [<span data-ttu-id="1d411-151">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="1d411-151">Generics</span></span>](../../../docs/standard/generics/index.md)
