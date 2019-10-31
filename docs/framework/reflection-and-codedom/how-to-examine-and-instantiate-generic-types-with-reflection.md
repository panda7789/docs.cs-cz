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
ms.openlocfilehash: 62e4e066740d0422f8f7045b043a5725278c209c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130139"
---
# <a name="how-to-examine-and-instantiate-generic-types-with-reflection"></a><span data-ttu-id="cdd81-102">Postupy: Prozkoumání a vytvoření instancí obecných typů pomocí reflexe</span><span class="sxs-lookup"><span data-stu-id="cdd81-102">How to: Examine and Instantiate Generic Types with Reflection</span></span>
<span data-ttu-id="cdd81-103">Informace o obecných typech jsou získány stejným způsobem jako informace o jiných typech: prozkoumáním <xref:System.Type> objektu, který představuje obecný typ.</span><span class="sxs-lookup"><span data-stu-id="cdd81-103">Information about generic types is obtained in the same way as information about other types: by examining a <xref:System.Type> object that represents the generic type.</span></span> <span data-ttu-id="cdd81-104">Hlavní rozdíl je v tom, že obecný typ obsahuje seznam <xref:System.Type> objektů představujících parametry obecného typu.</span><span class="sxs-lookup"><span data-stu-id="cdd81-104">The principle difference is that a generic type has a list of <xref:System.Type> objects representing its generic type parameters.</span></span> <span data-ttu-id="cdd81-105">První postup v této části prověřuje obecné typy.</span><span class="sxs-lookup"><span data-stu-id="cdd81-105">The first procedure in this section examines generic types.</span></span>  
  
 <span data-ttu-id="cdd81-106">Můžete vytvořit objekt <xref:System.Type>, který představuje konstruovaný typ pomocí argumentů typu vazby k parametrům typu definice obecného typu.</span><span class="sxs-lookup"><span data-stu-id="cdd81-106">You can create a <xref:System.Type> object that represents a constructed type by binding type arguments to the type parameters of a generic type definition.</span></span> <span data-ttu-id="cdd81-107">Druhá procedura to demonstruje.</span><span class="sxs-lookup"><span data-stu-id="cdd81-107">The second procedure demonstrates this.</span></span>  
  
### <a name="to-examine-a-generic-type-and-its-type-parameters"></a><span data-ttu-id="cdd81-108">Kontrola obecného typu a jeho parametrů typu</span><span class="sxs-lookup"><span data-stu-id="cdd81-108">To examine a generic type and its type parameters</span></span>  
  
1. <span data-ttu-id="cdd81-109">Získat instanci <xref:System.Type>, která představuje obecný typ.</span><span class="sxs-lookup"><span data-stu-id="cdd81-109">Get an instance of <xref:System.Type> that represents the generic type.</span></span> <span data-ttu-id="cdd81-110">V následujícím kódu je typ získán pomocí operátoru C# `typeof` (`GetType` v Visual Basic, `typeid` ve vizuálu C++).</span><span class="sxs-lookup"><span data-stu-id="cdd81-110">In the following code, the type is obtained using the C# `typeof` operator (`GetType` in Visual Basic, `typeid` in Visual C++).</span></span> <span data-ttu-id="cdd81-111">Další způsoby, jak získat objekt <xref:System.Type>, naleznete v tématu <xref:System.Type> třídy.</span><span class="sxs-lookup"><span data-stu-id="cdd81-111">See the <xref:System.Type> class topic for other ways to get a <xref:System.Type> object.</span></span> <span data-ttu-id="cdd81-112">Všimněte si, že ve zbývající části tohoto postupu je typ obsažen v parametru metody s názvem `t`.</span><span class="sxs-lookup"><span data-stu-id="cdd81-112">Note that in the rest of this procedure, the type is contained in a method parameter named `t`.</span></span>  
  
     [!code-cpp[HowToGeneric#2](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#2)]
     [!code-csharp[HowToGeneric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#2)]
     [!code-vb[HowToGeneric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#2)]  
  
2. <span data-ttu-id="cdd81-113">Pomocí vlastnosti <xref:System.Type.IsGenericType%2A> určete, zda je typ obecný, a pomocí vlastnosti <xref:System.Type.IsGenericTypeDefinition%2A> určete, zda je typ definice obecného typu.</span><span class="sxs-lookup"><span data-stu-id="cdd81-113">Use the <xref:System.Type.IsGenericType%2A> property to determine whether the type is generic, and use the <xref:System.Type.IsGenericTypeDefinition%2A> property to determine whether the type is a generic type definition.</span></span>  
  
     [!code-cpp[HowToGeneric#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#3)]
     [!code-csharp[HowToGeneric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#3)]
     [!code-vb[HowToGeneric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#3)]  
  
3. <span data-ttu-id="cdd81-114">Získejte pole, které obsahuje argumenty obecného typu, pomocí metody <xref:System.Type.GetGenericArguments%2A>.</span><span class="sxs-lookup"><span data-stu-id="cdd81-114">Get an array that contains the generic type arguments, using the <xref:System.Type.GetGenericArguments%2A> method.</span></span>  
  
     [!code-cpp[HowToGeneric#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#4)]
     [!code-csharp[HowToGeneric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#4)]
     [!code-vb[HowToGeneric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#4)]  
  
4. <span data-ttu-id="cdd81-115">Pro každý argument typu určete, zda se jedná o parametr typu (například v definici obecného typu) nebo typ, který byl zadán pro parametr typu (například v konstruovaném typu) pomocí vlastnosti <xref:System.Type.IsGenericParameter%2A>.</span><span class="sxs-lookup"><span data-stu-id="cdd81-115">For each type argument, determine whether it is a type parameter (for example, in a generic type definition) or a type that has been specified for a type parameter (for example, in a constructed type), using the <xref:System.Type.IsGenericParameter%2A> property.</span></span>  
  
     [!code-cpp[HowToGeneric#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#5)]
     [!code-csharp[HowToGeneric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#5)]
     [!code-vb[HowToGeneric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#5)]  
  
5. <span data-ttu-id="cdd81-116">V systému typů je parametr obecného typu reprezentován instancí <xref:System.Type>, stejně jako běžné typy.</span><span class="sxs-lookup"><span data-stu-id="cdd81-116">In the type system, a generic type parameter is represented by an instance of <xref:System.Type>, just as ordinary types are.</span></span> <span data-ttu-id="cdd81-117">Následující kód zobrazuje název a umístění parametru objektu <xref:System.Type>, který představuje parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="cdd81-117">The following code displays the name and parameter position of a <xref:System.Type> object that represents a generic type parameter.</span></span> <span data-ttu-id="cdd81-118">Pozice parametru je sem triviální informace; je mnohem zajímavější při zkoumání parametru typu, který byl použit jako argument typu jiného obecného typu.</span><span class="sxs-lookup"><span data-stu-id="cdd81-118">The parameter position is trivial information here; it is of more interest when you are examining a type parameter that has been used as a type argument of another generic type.</span></span>  
  
     [!code-cpp[HowToGeneric#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#6)]
     [!code-csharp[HowToGeneric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#6)]
     [!code-vb[HowToGeneric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#6)]  
  
6. <span data-ttu-id="cdd81-119">Určete omezení základního typu a omezení rozhraní parametru obecného typu pomocí metody <xref:System.Type.GetGenericParameterConstraints%2A> pro získání všech omezení v jednom poli.</span><span class="sxs-lookup"><span data-stu-id="cdd81-119">Determine the base type constraint and the interface constraints of a generic type parameter by using the <xref:System.Type.GetGenericParameterConstraints%2A> method to obtain all the constraints in a single array.</span></span> <span data-ttu-id="cdd81-120">Omezení nejsou zaručena v žádném konkrétním pořadí.</span><span class="sxs-lookup"><span data-stu-id="cdd81-120">Constraints are not guaranteed to be in any particular order.</span></span>  
  
     [!code-cpp[HowToGeneric#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#7)]
     [!code-csharp[HowToGeneric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#7)]
     [!code-vb[HowToGeneric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#7)]  
  
7. <span data-ttu-id="cdd81-121">Použijte vlastnost <xref:System.Type.GenericParameterAttributes%2A> pro zjištění speciálních omezení parametru typu, například vyžadování, že se jedná o typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="cdd81-121">Use the <xref:System.Type.GenericParameterAttributes%2A> property to discover the special constraints on a type parameter, such as requiring that it be a reference type.</span></span> <span data-ttu-id="cdd81-122">Vlastnost také obsahuje hodnoty, které reprezentují odchylku, které lze odmaskovat, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="cdd81-122">The property also includes values that represent variance, which you can mask off as shown in the following code.</span></span>  
  
     [!code-cpp[HowToGeneric#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#8)]
     [!code-csharp[HowToGeneric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#8)]
     [!code-vb[HowToGeneric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#8)]  
  
8. <span data-ttu-id="cdd81-123">Speciální atributy omezení jsou příznaky a stejný příznak (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>), který představuje žádná zvláštní omezení, také nepředstavuje žádnou koodchylku nebo kontravariance.</span><span class="sxs-lookup"><span data-stu-id="cdd81-123">The special constraint attributes are flags, and the same flag (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>) that represents no special constraints also represents no covariance or contravariance.</span></span> <span data-ttu-id="cdd81-124">Proto je nutné použít k otestování některé z těchto podmínek příslušnou masku.</span><span class="sxs-lookup"><span data-stu-id="cdd81-124">Thus, to test for either of these conditions you must use the appropriate mask.</span></span> <span data-ttu-id="cdd81-125">V takovém případě použijte <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> k izolaci speciálních příznaků omezení.</span><span class="sxs-lookup"><span data-stu-id="cdd81-125">In this case, use <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> to isolate the special constraint flags.</span></span>  
  
     [!code-cpp[HowToGeneric#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#9)]
     [!code-csharp[HowToGeneric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#9)]
     [!code-vb[HowToGeneric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#9)]  
  
## <a name="constructing-an-instance-of-a-generic-type"></a><span data-ttu-id="cdd81-126">Konstrukce instance obecného typu</span><span class="sxs-lookup"><span data-stu-id="cdd81-126">Constructing an Instance of a Generic Type</span></span>  
 <span data-ttu-id="cdd81-127">Obecný typ je jako šablona.</span><span class="sxs-lookup"><span data-stu-id="cdd81-127">A generic type is like a template.</span></span> <span data-ttu-id="cdd81-128">Instance se nedají vytvořit, pokud neurčíte reálné typy pro své parametry obecného typu.</span><span class="sxs-lookup"><span data-stu-id="cdd81-128">You cannot create instances of it unless you specify real types for its generic type parameters.</span></span> <span data-ttu-id="cdd81-129">K tomu v době běhu pomocí reflexe vyžaduje metodu <xref:System.Type.MakeGenericType%2A>.</span><span class="sxs-lookup"><span data-stu-id="cdd81-129">To do this at run time, using reflection, requires the <xref:System.Type.MakeGenericType%2A> method.</span></span>  
  
#### <a name="to-construct-an-instance-of-a-generic-type"></a><span data-ttu-id="cdd81-130">Vytvoření instance obecného typu</span><span class="sxs-lookup"><span data-stu-id="cdd81-130">To construct an instance of a generic type</span></span>  
  
1. <span data-ttu-id="cdd81-131">Získat objekt <xref:System.Type>, který představuje obecný typ.</span><span class="sxs-lookup"><span data-stu-id="cdd81-131">Get a <xref:System.Type> object that represents the generic type.</span></span> <span data-ttu-id="cdd81-132">Následující kód získá obecný typ <xref:System.Collections.Generic.Dictionary%602> dvěma různými způsoby: pomocí přetížení metody <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> s řetězcem, který popisuje typ a voláním metody <xref:System.Type.GetGenericTypeDefinition%2A> na vytvořeném typu `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` in Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="cdd81-132">The following code gets the generic type <xref:System.Collections.Generic.Dictionary%602> in two different ways: by using the <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> method overload with a string describing the type, and by calling the <xref:System.Type.GetGenericTypeDefinition%2A> method on the constructed type `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` in Visual Basic).</span></span> <span data-ttu-id="cdd81-133">Metoda <xref:System.Type.MakeGenericType%2A> vyžaduje definici obecného typu.</span><span class="sxs-lookup"><span data-stu-id="cdd81-133">The <xref:System.Type.MakeGenericType%2A> method requires a generic type definition.</span></span>  
  
     [!code-cpp[HowToGeneric#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#10)]
     [!code-csharp[HowToGeneric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#10)]
     [!code-vb[HowToGeneric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#10)]  
  
2. <span data-ttu-id="cdd81-134">Sestavte pole argumentů typu, které mají být nahrazeny parametry typu.</span><span class="sxs-lookup"><span data-stu-id="cdd81-134">Construct an array of type arguments to substitute for the type parameters.</span></span> <span data-ttu-id="cdd81-135">Pole musí obsahovat správný počet <xref:System.Type> objektů ve stejném pořadí, v jakém jsou uvedeny v seznamu parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="cdd81-135">The array must contain the correct number of <xref:System.Type> objects, in the same order as they appear in the type parameter list.</span></span> <span data-ttu-id="cdd81-136">V tomto případě je klíč (parametr prvního typu) typu <xref:System.String>a hodnoty ve slovníku jsou instancemi třídy s názvem `Example`.</span><span class="sxs-lookup"><span data-stu-id="cdd81-136">In this case, the key (first type parameter) is of type <xref:System.String>, and the values in the dictionary are instances of a class named `Example`.</span></span>  
  
     [!code-cpp[HowToGeneric#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#11)]
     [!code-csharp[HowToGeneric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#11)]
     [!code-vb[HowToGeneric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#11)]  
  
3. <span data-ttu-id="cdd81-137">Zavolejte metodu <xref:System.Type.MakeGenericType%2A> pro svázání argumentů typu s parametry typu a vytvořte typ.</span><span class="sxs-lookup"><span data-stu-id="cdd81-137">Call the <xref:System.Type.MakeGenericType%2A> method to bind the type arguments to the type parameters and construct the type.</span></span>  
  
     [!code-cpp[HowToGeneric#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#12)]
     [!code-csharp[HowToGeneric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#12)]
     [!code-vb[HowToGeneric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#12)]  
  
4. <span data-ttu-id="cdd81-138">Použijte přetížení metody <xref:System.Activator.CreateInstance%28System.Type%29> k vytvoření objektu konstruovaného typu.</span><span class="sxs-lookup"><span data-stu-id="cdd81-138">Use the <xref:System.Activator.CreateInstance%28System.Type%29> method overload to create an object of the constructed type.</span></span> <span data-ttu-id="cdd81-139">Následující kód ukládá dvě instance `Example` třídy ve výsledném objektu `Dictionary<String, Example>`.</span><span class="sxs-lookup"><span data-stu-id="cdd81-139">The following code stores two instances of the `Example` class in the resulting `Dictionary<String, Example>` object.</span></span>  
  
     [!code-cpp[HowToGeneric#13](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#13)]
     [!code-csharp[HowToGeneric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#13)]
     [!code-vb[HowToGeneric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="cdd81-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="cdd81-140">Example</span></span>  
 <span data-ttu-id="cdd81-141">Následující příklad kódu definuje metodu `DisplayGenericType` pro prohlédnutí definice obecného typu a vytvořené typy používané v kódu a zobrazení jejich informací.</span><span class="sxs-lookup"><span data-stu-id="cdd81-141">The following code example defines a `DisplayGenericType` method to examine the generic type definitions and constructed types used in the code and display their information.</span></span> <span data-ttu-id="cdd81-142">Metoda `DisplayGenericType` ukazuje, jak používat vlastnosti <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A>a <xref:System.Type.GenericParameterPosition%2A> a metodu <xref:System.Type.GetGenericArguments%2A>.</span><span class="sxs-lookup"><span data-stu-id="cdd81-142">The `DisplayGenericType` method shows how to use the <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A>, and <xref:System.Type.GenericParameterPosition%2A> properties and the <xref:System.Type.GetGenericArguments%2A> method.</span></span>  
  
 <span data-ttu-id="cdd81-143">V příkladu je také definována metoda `DisplayGenericParameter` pro prověření parametru obecného typu a zobrazení jeho omezení.</span><span class="sxs-lookup"><span data-stu-id="cdd81-143">The example also defines a `DisplayGenericParameter` method to examine a generic type parameter and display its constraints.</span></span>  
  
 <span data-ttu-id="cdd81-144">Příklad kódu definuje sadu typů testů, včetně obecného typu, který ilustruje omezení parametrů typu a ukazuje, jak zobrazit informace o těchto typech.</span><span class="sxs-lookup"><span data-stu-id="cdd81-144">The code example defines a set of test types, including a generic type that illustrates type parameter constraints, and shows how to display information about these types.</span></span>  
  
 <span data-ttu-id="cdd81-145">Příklad vytvoří typ z třídy <xref:System.Collections.Generic.Dictionary%602> vytvořením pole argumentů typu a voláním metody <xref:System.Type.MakeGenericType%2A>.</span><span class="sxs-lookup"><span data-stu-id="cdd81-145">The example constructs a type from the <xref:System.Collections.Generic.Dictionary%602> class by creating an array of type arguments and calling the <xref:System.Type.MakeGenericType%2A> method.</span></span> <span data-ttu-id="cdd81-146">Program porovná objekt <xref:System.Type> vytvořený pomocí <xref:System.Type.MakeGenericType%2A> s objektem <xref:System.Type> získaným pomocí `typeof` (`GetType` v Visual Basic), který demonstruje, že jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="cdd81-146">The program compares the <xref:System.Type> object constructed using <xref:System.Type.MakeGenericType%2A> with a <xref:System.Type> object obtained using `typeof` (`GetType` in Visual Basic), demonstrating that they are the same.</span></span> <span data-ttu-id="cdd81-147">Podobně program používá metodu <xref:System.Type.GetGenericTypeDefinition%2A> k získání definice obecného typu konstruovaného typu a porovná je s objektem <xref:System.Type> reprezentujícím třídu <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="cdd81-147">Similarly, the program uses the <xref:System.Type.GetGenericTypeDefinition%2A> method to obtain the generic type definition of the constructed type, and compares it to the <xref:System.Type> object representing the <xref:System.Collections.Generic.Dictionary%602> class.</span></span>  
  
 [!code-cpp[HowToGeneric#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#1)]
 [!code-csharp[HowToGeneric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#1)]
 [!code-vb[HowToGeneric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="cdd81-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cdd81-148">See also</span></span>

- <xref:System.Type>
- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="cdd81-149">Reflexe a obecné typy</span><span class="sxs-lookup"><span data-stu-id="cdd81-149">Reflection and Generic Types</span></span>](reflection-and-generic-types.md)
- [<span data-ttu-id="cdd81-150">Zobrazení informací o typu</span><span class="sxs-lookup"><span data-stu-id="cdd81-150">Viewing Type Information</span></span>](viewing-type-information.md)
- [<span data-ttu-id="cdd81-151">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="cdd81-151">Generics</span></span>](../../standard/generics/index.md)
