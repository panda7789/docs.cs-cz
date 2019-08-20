---
title: Obecné typy – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: 7d212aeaa7d7a8c3f152f8610a7ef3fe5de0fe23
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589604"
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="9acff-102">Obecné typy (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="9acff-102">Generics (C# Programming Guide)</span></span>
<span data-ttu-id="9acff-103">Obecné typy byly přidány do verze 2,0 C# jazyka a modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="9acff-103">Generics were added to version 2.0 of the C# language and the common language runtime (CLR).</span></span> <span data-ttu-id="9acff-104">Obecné typy představují .NET Framework konceptu parametrů typu, který umožňuje navrhovat třídy a metody, které odloží specifikaci jednoho nebo více typů, dokud není deklarována třída nebo metoda a vytvořena instance klientského kódu.</span><span class="sxs-lookup"><span data-stu-id="9acff-104">Generics introduce to the .NET Framework the concept of type parameters, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="9acff-105">Například pomocí obecného typu parametru T můžete napsat jednu třídu, kterou může jiný klientský kód použít, aniž by vznikly náklady nebo riziko přetypování za běhu nebo zabalení, jak je znázorněno zde:</span><span class="sxs-lookup"><span data-stu-id="9acff-105">For example, by using a generic type parameter T you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]  

<span data-ttu-id="9acff-106">Obecné třídy a metody kombinují opětovné použitelnost, bezpečnost typů a efektivitu způsobem, že jejich neobecné protějšky nemůžou.</span><span class="sxs-lookup"><span data-stu-id="9acff-106">Generic classes and methods combine reusability, type safety and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="9acff-107">Obecné typy se nejčastěji používají s kolekcemi a metodami, které na nich pracují.</span><span class="sxs-lookup"><span data-stu-id="9acff-107">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="9acff-108">Verze 2,0 knihovny tříd .NET Framework poskytuje nový obor názvů <xref:System.Collections.Generic>, který obsahuje několik nových obecných tříd kolekcí.</span><span class="sxs-lookup"><span data-stu-id="9acff-108">Version 2.0 of the .NET Framework class library provides a new namespace, <xref:System.Collections.Generic>, which contains several new generic-based collection classes.</span></span> <span data-ttu-id="9acff-109">Doporučuje se, aby všechny aplikace, které cílí na .NET Framework 2,0 a později používaly nové obecné třídy kolekce namísto starších neobecných protějšků, jako je <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="9acff-109">It is recommended that all applications that target the .NET Framework 2.0 and later use the new generic collection classes instead of the older non-generic counterparts such as <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="9acff-110">Další informace naleznete v tématu [Obecné typy v rozhraní .NET](../../../standard/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="9acff-110">For more information, see [Generics in .NET](../../../standard/generics/index.md).</span></span>  
  
 <span data-ttu-id="9acff-111">Samozřejmě můžete také vytvořit vlastní obecné typy a metody, které poskytují vlastní generalizovaná řešení a vzory návrhu, které jsou typově bezpečné a efektivní.</span><span class="sxs-lookup"><span data-stu-id="9acff-111">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="9acff-112">Následující příklad kódu ukazuje jednoduchou obecnou třídu propojených seznamů pro demonstrační účely.</span><span class="sxs-lookup"><span data-stu-id="9acff-112">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="9acff-113">(Ve většině případů byste měli použít <xref:System.Collections.Generic.List%601> třídu poskytnutou .NET Framework knihovny tříd namísto vytvoření vlastní.) Parametr `T` typu se používá v několika umístěních, kde konkrétní typ by byl obvykle použit k označení typu položky uložené v seznamu.</span><span class="sxs-lookup"><span data-stu-id="9acff-113">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by the .NET Framework class library instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="9acff-114">Používá se následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="9acff-114">It is used in the following ways:</span></span>  
  
- <span data-ttu-id="9acff-115">Jako typ parametru metody v `AddHead` metodě.</span><span class="sxs-lookup"><span data-stu-id="9acff-115">As the type of a method parameter in the `AddHead` method.</span></span>  
  
- <span data-ttu-id="9acff-116">Jako návratový typ `Data` vlastnosti ve vnořené `Node` třídě.</span><span class="sxs-lookup"><span data-stu-id="9acff-116">As the return type of the `Data` property in the nested `Node` class.</span></span>  
  
- <span data-ttu-id="9acff-117">Jako typ privátního člena `data` ve vnořené třídě.</span><span class="sxs-lookup"><span data-stu-id="9acff-117">As the type of the private member `data` in the nested class.</span></span>  
  
 <span data-ttu-id="9acff-118">Všimněte si, že T je k dispozici pro vnořenou `Node` třídu.</span><span class="sxs-lookup"><span data-stu-id="9acff-118">Note that T is available to the nested `Node` class.</span></span> <span data-ttu-id="9acff-119">Při `GenericList<T>` vytvoření instance se konkrétním typem, například `GenericList<int>`jako, každý výskyt `T` bude nahrazen `int`.</span><span class="sxs-lookup"><span data-stu-id="9acff-119">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]  
  
 <span data-ttu-id="9acff-120">Následující příklad kódu ukazuje, jak klientský kód používá obecnou `GenericList<T>` třídu k vytvoření seznamu celých čísel.</span><span class="sxs-lookup"><span data-stu-id="9acff-120">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="9acff-121">Jednoduše změnou argumentu typu lze následující kód snadno upravit, aby bylo možné vytvořit seznam řetězců nebo jakýkoli jiný vlastní typ:</span><span class="sxs-lookup"><span data-stu-id="9acff-121">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]  
  
## <a name="generics-overview"></a><span data-ttu-id="9acff-122">Obecné typy – přehled</span><span class="sxs-lookup"><span data-stu-id="9acff-122">Generics Overview</span></span>  
  
- <span data-ttu-id="9acff-123">Pomocí obecných typů maximalizujete opětovné použití kódu, bezpečnost typů a výkon.</span><span class="sxs-lookup"><span data-stu-id="9acff-123">Use generic types to maximize code reuse, type safety, and performance.</span></span>  
  
- <span data-ttu-id="9acff-124">Nejběžnějším použitím obecných typů je vytvoření tříd kolekcí.</span><span class="sxs-lookup"><span data-stu-id="9acff-124">The most common use of generics is to create collection classes.</span></span>  
  
- <span data-ttu-id="9acff-125">Knihovna tříd .NET Framework obsahuje několik nových obecných tříd kolekcí v <xref:System.Collections.Generic> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="9acff-125">The .NET Framework class library contains several new generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="9acff-126">Ty by měly být použity, kdykoli je to možné, <xref:System.Collections.ArrayList> nikoli třídy <xref:System.Collections> , jako je například v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="9acff-126">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>  
  
- <span data-ttu-id="9acff-127">Můžete vytvořit vlastní Obecná rozhraní, třídy, metody, události a delegáty.</span><span class="sxs-lookup"><span data-stu-id="9acff-127">You can create your own generic interfaces, classes, methods, events and delegates.</span></span>  
  
- <span data-ttu-id="9acff-128">Obecné třídy mohou být omezeny, aby bylo možné povolit přístup k metodám pro konkrétní datové typy.</span><span class="sxs-lookup"><span data-stu-id="9acff-128">Generic classes may be constrained to enable access to methods on particular data types.</span></span>  
  
- <span data-ttu-id="9acff-129">Informace o typech, které jsou použity v obecném datovém typu, lze získat za běhu pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="9acff-129">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9acff-130">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="9acff-130">Related Sections</span></span>  
 <span data-ttu-id="9acff-131">Další informace:</span><span class="sxs-lookup"><span data-stu-id="9acff-131">For more information:</span></span>  
  
- [<span data-ttu-id="9acff-132">Parametry obecného typu</span><span class="sxs-lookup"><span data-stu-id="9acff-132">Generic Type Parameters</span></span>](./generic-type-parameters.md)  
  
- [<span data-ttu-id="9acff-133">Omezení parametrů typů</span><span class="sxs-lookup"><span data-stu-id="9acff-133">Constraints on Type Parameters</span></span>](./constraints-on-type-parameters.md)  
  
- [<span data-ttu-id="9acff-134">Obecné třídy</span><span class="sxs-lookup"><span data-stu-id="9acff-134">Generic Classes</span></span>](./generic-classes.md)  
  
- [<span data-ttu-id="9acff-135">Obecná rozhraní</span><span class="sxs-lookup"><span data-stu-id="9acff-135">Generic Interfaces</span></span>](./generic-interfaces.md)  
  
- [<span data-ttu-id="9acff-136">Obecné metody</span><span class="sxs-lookup"><span data-stu-id="9acff-136">Generic Methods</span></span>](./generic-methods.md)  
  
- [<span data-ttu-id="9acff-137">Obecní delegáti</span><span class="sxs-lookup"><span data-stu-id="9acff-137">Generic Delegates</span></span>](./generic-delegates.md)  
  
- [<span data-ttu-id="9acff-138">Rozdíly mezi šablonami C++ a obecnými typy C#</span><span class="sxs-lookup"><span data-stu-id="9acff-138">Differences Between C++ Templates and C# Generics</span></span>](./differences-between-cpp-templates-and-csharp-generics.md)  
  
- [<span data-ttu-id="9acff-139">Obecné typy a reflexe</span><span class="sxs-lookup"><span data-stu-id="9acff-139">Generics and Reflection</span></span>](./generics-and-reflection.md)  
  
- [<span data-ttu-id="9acff-140">Obecné typy v běhovém prostředí</span><span class="sxs-lookup"><span data-stu-id="9acff-140">Generics in the Run Time</span></span>](./generics-in-the-run-time.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="9acff-141">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9acff-141">C# Language Specification</span></span>  
 <span data-ttu-id="9acff-142">Další informace najdete v tématu [Specifikace jazyka C#](~/_csharplang/spec/types.md#constructed-types).</span><span class="sxs-lookup"><span data-stu-id="9acff-142">For more information, see the [C# Language Specification](~/_csharplang/spec/types.md#constructed-types).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9acff-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9acff-143">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="9acff-144">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="9acff-144">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9acff-145">Typy</span><span class="sxs-lookup"><span data-stu-id="9acff-145">Types</span></span>](../types/index.md)
- [<span data-ttu-id="9acff-146">\<typeparam ></span><span class="sxs-lookup"><span data-stu-id="9acff-146">\<typeparam></span></span>](../xmldoc/typeparam.md)
- [<span data-ttu-id="9acff-147">\<typeparamref ></span><span class="sxs-lookup"><span data-stu-id="9acff-147">\<typeparamref></span></span>](../xmldoc/typeparamref.md)
- [<span data-ttu-id="9acff-148">Obecné typy v .NET</span><span class="sxs-lookup"><span data-stu-id="9acff-148">Generics in .NET</span></span>](../../../standard/generics/index.md)
