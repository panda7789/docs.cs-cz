---
title: Obecné typy - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: e32eb7c60e01ca72824ffb3a1e1269cf34650f5a
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423400"
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="15105-102">Obecné typy (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="15105-102">Generics (C# Programming Guide)</span></span>
<span data-ttu-id="15105-103">Obecné typy byly přidány do verze 2.0 jazyka C# a common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="15105-103">Generics were added to version 2.0 of the C# language and the common language runtime (CLR).</span></span> <span data-ttu-id="15105-104">Obecné typy rozhraní .NET Framework přinášejí koncept parametry typu, které umožňují návrh tříd a metod, které specifikace jeden nebo více typů odložit, dokud třídy nebo metody je deklarována a vytvořena kódem na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="15105-104">Generics introduce to the .NET Framework the concept of type parameters, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="15105-105">Například můžete pomocí parametru obecného typu T napsat jednu třídu, jiný kód klienta můžete použít bez dalších nákladů na náklady nebo rizikem přetypování modulu runtime nebo operace zabalení, jak je znázorněno zde:</span><span class="sxs-lookup"><span data-stu-id="15105-105">For example, by using a generic type parameter T you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]  

<span data-ttu-id="15105-106">Obecné třídy a metody opětovné použití, bezpečnost typů a efektivitu tak, aby jejich obecné protějšky nelze kombinovat.</span><span class="sxs-lookup"><span data-stu-id="15105-106">Generic classes and methods combine reusability, type safety and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="15105-107">Obecné typy se nejčastěji používají s kolekcí a metody, které pracují s nimi.</span><span class="sxs-lookup"><span data-stu-id="15105-107">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="15105-108">Knihovna tříd rozhraní .NET Framework verze 2.0 obsahuje nový obor názvů <xref:System.Collections.Generic>, která obsahuje několik nových obecné kolekce tříd.</span><span class="sxs-lookup"><span data-stu-id="15105-108">Version 2.0 of the .NET Framework class library provides a new namespace, <xref:System.Collections.Generic>, which contains several new generic-based collection classes.</span></span> <span data-ttu-id="15105-109">Doporučuje se, že všechny aplikace, jejichž cílem rozhraní .NET Framework 2.0 a pozdější použití nové obecné kolekce tříd, namísto starší jejich obecné protějšky například <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="15105-109">It is recommended that all applications that target the .NET Framework 2.0 and later use the new generic collection classes instead of the older non-generic counterparts such as <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="15105-110">Další informace najdete v tématu [obecné typy v .NET](../../../standard/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="15105-110">For more information, see [Generics in .NET](../../../standard/generics/index.md).</span></span>  
  
 <span data-ttu-id="15105-111">Samozřejmě můžete také vytvořit vlastní obecné typy a metody, které poskytují vlastní generalizované řešení a vzorů návrhu, které jsou typově bezpečné a efektivní.</span><span class="sxs-lookup"><span data-stu-id="15105-111">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="15105-112">Následující příklad kódu ukazuje jednoduchý obecné třídy propojené seznamy pro demonstrační účely.</span><span class="sxs-lookup"><span data-stu-id="15105-112">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="15105-113">(Ve většině případů byste měli použít <xref:System.Collections.Generic.List%601> poskytovaných knihovnou tříd rozhraní .NET Framework místo vytvoření vlastní třídy.) Parametr typu `T` se používá v několika umístěních, kde konkrétního typu implementujícího typ by obvykle použít k označení typu položky uložené v seznamu.</span><span class="sxs-lookup"><span data-stu-id="15105-113">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by the .NET Framework class library instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="15105-114">Používá se následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="15105-114">It is used in the following ways:</span></span>  
  
- <span data-ttu-id="15105-115">Jako typ parametru metody `AddHead` metody.</span><span class="sxs-lookup"><span data-stu-id="15105-115">As the type of a method parameter in the `AddHead` method.</span></span>  
  
- <span data-ttu-id="15105-116">Jako návratový typ `Data` vlastnost ve vnořeném `Node` třídy.</span><span class="sxs-lookup"><span data-stu-id="15105-116">As the return type of the `Data` property in the nested `Node` class.</span></span>  
  
- <span data-ttu-id="15105-117">Jako typ soukromému členu `data` ve vnořené třídě.</span><span class="sxs-lookup"><span data-stu-id="15105-117">As the type of the private member `data` in the nested class.</span></span>  
  
 <span data-ttu-id="15105-118">Všimněte si, že je k dispozici ve vnořeném T `Node` třídy.</span><span class="sxs-lookup"><span data-stu-id="15105-118">Note that T is available to the nested `Node` class.</span></span> <span data-ttu-id="15105-119">Když `GenericList<T>` je vytvořena instance s konkrétního typu implementujícího typ, třeba jako `GenericList<int>`, každý výskyt `T` bude nahrazena adresou `int`.</span><span class="sxs-lookup"><span data-stu-id="15105-119">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]  
  
 <span data-ttu-id="15105-120">Následující příklad kódu ukazuje, jak kód klienta používá Obecné `GenericList<T>` třídy za účelem vytvoření seznamu celých čísel.</span><span class="sxs-lookup"><span data-stu-id="15105-120">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="15105-121">Jednoduše tak, že změníte typ argumentu, následující kód by mohl snadno upravit tak, aby vytvořit seznam řetězců nebo jiný vlastní typ:</span><span class="sxs-lookup"><span data-stu-id="15105-121">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]  
  
## <a name="generics-overview"></a><span data-ttu-id="15105-122">Přehled obecných typů</span><span class="sxs-lookup"><span data-stu-id="15105-122">Generics Overview</span></span>  
  
- <span data-ttu-id="15105-123">Maximalizujte opakované využívání kódu, bezpečnost typů a výkonu pomocí obecných typů.</span><span class="sxs-lookup"><span data-stu-id="15105-123">Use generic types to maximize code reuse, type safety, and performance.</span></span>  
  
- <span data-ttu-id="15105-124">Nejběžnější použití obecných typů je pro vytvoření kolekce tříd.</span><span class="sxs-lookup"><span data-stu-id="15105-124">The most common use of generics is to create collection classes.</span></span>  
  
- <span data-ttu-id="15105-125">Obsahuje několik nových obecné kolekce tříd v knihovně tříd rozhraní .NET Framework <xref:System.Collections.Generic> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="15105-125">The .NET Framework class library contains several new generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="15105-126">Ty se používají vždy, když je možné namísto třídy, jako <xref:System.Collections.ArrayList> v <xref:System.Collections> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="15105-126">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>  
  
- <span data-ttu-id="15105-127">Můžete vytvořit vlastní obecných rozhraní, třídy, metody, události a delegáti.</span><span class="sxs-lookup"><span data-stu-id="15105-127">You can create your own generic interfaces, classes, methods, events and delegates.</span></span>  
  
- <span data-ttu-id="15105-128">Obecné třídy může být omezený na povolení přístupu k metodám pro konkrétní datové typy.</span><span class="sxs-lookup"><span data-stu-id="15105-128">Generic classes may be constrained to enable access to methods on particular data types.</span></span>  
  
- <span data-ttu-id="15105-129">Informace o typech, které se používají v obecného datového typu mohou být získány při spuštění pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="15105-129">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="15105-130">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="15105-130">Related Sections</span></span>  
 <span data-ttu-id="15105-131">Další informace:</span><span class="sxs-lookup"><span data-stu-id="15105-131">For more information:</span></span>  
  
- [<span data-ttu-id="15105-132">Parametry obecného typu</span><span class="sxs-lookup"><span data-stu-id="15105-132">Generic Type Parameters</span></span>](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
- [<span data-ttu-id="15105-133">Omezení parametrů typů</span><span class="sxs-lookup"><span data-stu-id="15105-133">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
- [<span data-ttu-id="15105-134">Obecné třídy</span><span class="sxs-lookup"><span data-stu-id="15105-134">Generic Classes</span></span>](../../../csharp/programming-guide/generics/generic-classes.md)  
  
- [<span data-ttu-id="15105-135">Obecná rozhraní</span><span class="sxs-lookup"><span data-stu-id="15105-135">Generic Interfaces</span></span>](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
- [<span data-ttu-id="15105-136">Obecné metody</span><span class="sxs-lookup"><span data-stu-id="15105-136">Generic Methods</span></span>](../../../csharp/programming-guide/generics/generic-methods.md)  
  
- [<span data-ttu-id="15105-137">Obecní delegáti</span><span class="sxs-lookup"><span data-stu-id="15105-137">Generic Delegates</span></span>](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
- [<span data-ttu-id="15105-138">Rozdíly mezi šablonami C++ a obecnými typy C#</span><span class="sxs-lookup"><span data-stu-id="15105-138">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
- [<span data-ttu-id="15105-139">Obecné typy a reflexe</span><span class="sxs-lookup"><span data-stu-id="15105-139">Generics and Reflection</span></span>](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
- [<span data-ttu-id="15105-140">Obecné typy v běhovém prostředí</span><span class="sxs-lookup"><span data-stu-id="15105-140">Generics in the Run Time</span></span>](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="15105-141">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="15105-141">C# Language Specification</span></span>  
 <span data-ttu-id="15105-142">Další informace najdete v tématu [Specifikace jazyka C#](~/_csharplang/spec/types.md#constructed-types).</span><span class="sxs-lookup"><span data-stu-id="15105-142">For more information, see the [C# Language Specification](~/_csharplang/spec/types.md#constructed-types).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15105-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15105-143">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="15105-144">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="15105-144">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="15105-145">Typy</span><span class="sxs-lookup"><span data-stu-id="15105-145">Types</span></span>](../../../csharp/programming-guide/types/index.md)
- [<span data-ttu-id="15105-146">\<typeparam ></span><span class="sxs-lookup"><span data-stu-id="15105-146">\<typeparam></span></span>](../../../csharp/programming-guide/xmldoc/typeparam.md)
- [<span data-ttu-id="15105-147">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="15105-147">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)
- [<span data-ttu-id="15105-148">Obecné typy v .NET</span><span class="sxs-lookup"><span data-stu-id="15105-148">Generics in .NET</span></span>](../../../standard/generics/index.md)
