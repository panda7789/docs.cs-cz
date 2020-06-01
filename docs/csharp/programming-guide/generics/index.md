---
title: Obecné typy – Průvodce programováním v C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: a3ed3aa412c7d9c9d6b705dba80b527057c647fa
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241666"
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="96dda-102">Obecné typy (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="96dda-102">Generics (C# Programming Guide)</span></span>

<span data-ttu-id="96dda-103">Obecné typy představují koncept parametrů typu na rozhraní .NET, který umožňuje navrhovat třídy a metody, které odloží specifikaci jednoho nebo více typů, dokud není deklarována třída nebo metoda a vytvořena instance klientského kódu.</span><span class="sxs-lookup"><span data-stu-id="96dda-103">Generics introduce the concept of type parameters to .NET, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="96dda-104">Například pomocí obecného typu parametru `T` můžete napsat jednu třídu, kterou může jiný klientský kód použít, aniž by vznikly náklady nebo riziko přetypování za běhu nebo operace zabalení, jak je znázorněno zde:</span><span class="sxs-lookup"><span data-stu-id="96dda-104">For example, by using a generic type parameter `T`, you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>

[!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]

<span data-ttu-id="96dda-105">Obecné třídy a metody kombinují opětovné použitelnost, bezpečnost typů a efektivitu způsobem, že jejich neobecné protějšky nejsou.</span><span class="sxs-lookup"><span data-stu-id="96dda-105">Generic classes and methods combine reusability, type safety, and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="96dda-106">Obecné typy se nejčastěji používají s kolekcemi a metodami, které na nich pracují.</span><span class="sxs-lookup"><span data-stu-id="96dda-106">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="96dda-107"><xref:System.Collections.Generic>Obor názvů obsahuje několik obecných tříd kolekcí.</span><span class="sxs-lookup"><span data-stu-id="96dda-107">The <xref:System.Collections.Generic> namespace contains several generic-based collection classes.</span></span> <span data-ttu-id="96dda-108">Neobecné kolekce, například, <xref:System.Collections.ArrayList> se nedoporučují a jsou udržovány pro účely kompatibility.</span><span class="sxs-lookup"><span data-stu-id="96dda-108">The non-generic collections, such as <xref:System.Collections.ArrayList> are not recommended and are maintained for compatibility purposes.</span></span> <span data-ttu-id="96dda-109">Další informace naleznete v tématu [Obecné typy v rozhraní .NET](../../../standard/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="96dda-109">For more information, see [Generics in .NET](../../../standard/generics/index.md).</span></span>

<span data-ttu-id="96dda-110">Samozřejmě můžete také vytvořit vlastní obecné typy a metody, které poskytují vlastní generalizovaná řešení a vzory návrhu, které jsou typově bezpečné a efektivní.</span><span class="sxs-lookup"><span data-stu-id="96dda-110">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="96dda-111">Následující příklad kódu ukazuje jednoduchou obecnou třídu propojených seznamů pro demonstrační účely.</span><span class="sxs-lookup"><span data-stu-id="96dda-111">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="96dda-112">(Ve většině případů byste měli použít <xref:System.Collections.Generic.List%601> třídu poskytovanou rozhraním .NET namísto vytvoření vlastní.) Parametr typu `T` se používá v několika umístěních, kde konkrétní typ by byl obvykle použit k označení typu položky uložené v seznamu.</span><span class="sxs-lookup"><span data-stu-id="96dda-112">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by .NET instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="96dda-113">Používá se následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="96dda-113">It is used in the following ways:</span></span>

- <span data-ttu-id="96dda-114">Jako typ parametru metody v `AddHead` metodě.</span><span class="sxs-lookup"><span data-stu-id="96dda-114">As the type of a method parameter in the `AddHead` method.</span></span>
- <span data-ttu-id="96dda-115">Jako návratový typ `Data` vlastnosti ve vnořené `Node` třídě.</span><span class="sxs-lookup"><span data-stu-id="96dda-115">As the return type of the `Data` property in the nested `Node` class.</span></span>
- <span data-ttu-id="96dda-116">Jako typ privátního člena `data` ve vnořené třídě.</span><span class="sxs-lookup"><span data-stu-id="96dda-116">As the type of the private member `data` in the nested class.</span></span>

 <span data-ttu-id="96dda-117">Všimněte si, že `T` je k dispozici pro vnořenou `Node` třídu.</span><span class="sxs-lookup"><span data-stu-id="96dda-117">Note that `T` is available to the nested `Node` class.</span></span> <span data-ttu-id="96dda-118">Při `GenericList<T>` vytvoření instance se konkrétním typem, například jako `GenericList<int>` , každý výskyt `T` bude nahrazen `int` .</span><span class="sxs-lookup"><span data-stu-id="96dda-118">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>

[!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]

<span data-ttu-id="96dda-119">Následující příklad kódu ukazuje, jak klientský kód používá obecnou `GenericList<T>` třídu k vytvoření seznamu celých čísel.</span><span class="sxs-lookup"><span data-stu-id="96dda-119">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="96dda-120">Jednoduše změnou argumentu typu lze následující kód snadno upravit, aby bylo možné vytvořit seznam řetězců nebo jakýkoli jiný vlastní typ:</span><span class="sxs-lookup"><span data-stu-id="96dda-120">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>

[!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]

## <a name="generics-overview"></a><span data-ttu-id="96dda-121">Obecné typy – přehled</span><span class="sxs-lookup"><span data-stu-id="96dda-121">Generics overview</span></span>

- <span data-ttu-id="96dda-122">Pomocí obecných typů maximalizujete opětovné použití kódu, bezpečnost typů a výkon.</span><span class="sxs-lookup"><span data-stu-id="96dda-122">Use generic types to maximize code reuse, type safety, and performance.</span></span>
- <span data-ttu-id="96dda-123">Nejběžnějším použitím obecných typů je vytvoření tříd kolekcí.</span><span class="sxs-lookup"><span data-stu-id="96dda-123">The most common use of generics is to create collection classes.</span></span>
- <span data-ttu-id="96dda-124">Knihovna tříd .NET obsahuje několik obecných tříd kolekcí v <xref:System.Collections.Generic> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="96dda-124">The .NET class library contains several generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="96dda-125">Ty by měly být použity, kdykoli je to možné, nikoli třídy, jako <xref:System.Collections.ArrayList> je například v <xref:System.Collections> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="96dda-125">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>
- <span data-ttu-id="96dda-126">Můžete vytvořit vlastní Obecná rozhraní, třídy, metody, události a delegáty.</span><span class="sxs-lookup"><span data-stu-id="96dda-126">You can create your own generic interfaces, classes, methods, events, and delegates.</span></span>
- <span data-ttu-id="96dda-127">Obecné třídy mohou být omezeny, aby bylo možné povolit přístup k metodám pro konkrétní datové typy.</span><span class="sxs-lookup"><span data-stu-id="96dda-127">Generic classes may be constrained to enable access to methods on particular data types.</span></span>
- <span data-ttu-id="96dda-128">Informace o typech, které jsou použity v obecném datovém typu, lze získat za běhu pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="96dda-128">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>

## <a name="related-sections"></a><span data-ttu-id="96dda-129">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="96dda-129">Related sections</span></span>

- [<span data-ttu-id="96dda-130">Parametry obecného typu</span><span class="sxs-lookup"><span data-stu-id="96dda-130">Generic Type Parameters</span></span>](generic-type-parameters.md)
- [<span data-ttu-id="96dda-131">Omezení parametrů typů</span><span class="sxs-lookup"><span data-stu-id="96dda-131">Constraints on Type Parameters</span></span>](constraints-on-type-parameters.md)
- [<span data-ttu-id="96dda-132">Obecné třídy</span><span class="sxs-lookup"><span data-stu-id="96dda-132">Generic Classes</span></span>](generic-classes.md)
- [<span data-ttu-id="96dda-133">Obecná rozhraní</span><span class="sxs-lookup"><span data-stu-id="96dda-133">Generic Interfaces</span></span>](generic-interfaces.md)
- [<span data-ttu-id="96dda-134">Obecné metody</span><span class="sxs-lookup"><span data-stu-id="96dda-134">Generic Methods</span></span>](generic-methods.md)
- [<span data-ttu-id="96dda-135">Obecní delegáti</span><span class="sxs-lookup"><span data-stu-id="96dda-135">Generic Delegates</span></span>](generic-delegates.md)
- [<span data-ttu-id="96dda-136">Rozdíly mezi šablonami C++ a obecnými typy C#</span><span class="sxs-lookup"><span data-stu-id="96dda-136">Differences Between C++ Templates and C# Generics</span></span>](differences-between-cpp-templates-and-csharp-generics.md)
- [<span data-ttu-id="96dda-137">Obecné typy a reflexe</span><span class="sxs-lookup"><span data-stu-id="96dda-137">Generics and Reflection</span></span>](generics-and-reflection.md)
- [<span data-ttu-id="96dda-138">Obecné typy v běhovém prostředí</span><span class="sxs-lookup"><span data-stu-id="96dda-138">Generics in the Run Time</span></span>](generics-in-the-run-time.md)

## <a name="c-language-specification"></a><span data-ttu-id="96dda-139">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="96dda-139">C# language specification</span></span>

<span data-ttu-id="96dda-140">Další informace najdete v tématu [Specifikace jazyka C#](~/_csharplang/spec/types.md#constructed-types).</span><span class="sxs-lookup"><span data-stu-id="96dda-140">For more information, see the [C# Language Specification](~/_csharplang/spec/types.md#constructed-types).</span></span>

## <a name="see-also"></a><span data-ttu-id="96dda-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="96dda-141">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="96dda-142">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="96dda-142">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="96dda-143">Typy</span><span class="sxs-lookup"><span data-stu-id="96dda-143">Types</span></span>](../types/index.md)
- [\<typeparam>](../xmldoc/typeparam.md)
- [\<typeparamref>](../xmldoc/typeparamref.md)
- [<span data-ttu-id="96dda-144">Obecné typy v .NET</span><span class="sxs-lookup"><span data-stu-id="96dda-144">Generics in .NET</span></span>](../../../standard/generics/index.md)
