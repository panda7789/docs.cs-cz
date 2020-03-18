---
title: Obecné typy – programovací příručka jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: c7252180c9c98a8ca99c8cc6b3faaf8b1b8f0749
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79167489"
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="18fbb-102">Obecné typy (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="18fbb-102">Generics (C# Programming Guide)</span></span>

<span data-ttu-id="18fbb-103">Obecné typy zavést koncept parametrů typu rozhraní .NET Framework, které umožňují navrhnout třídy a metody, které odložit specifikaci jednoho nebo více typů, dokud třída nebo metoda je deklarována a vytvořena pomocí kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="18fbb-103">Generics introduce the concept of type parameters to the .NET Framework, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="18fbb-104">Například pomocí parametru `T`obecného typu můžete napsat jednu třídu, kterou může použít jiný kód klienta, aniž by vznikly náklady nebo riziko přetypování za běhu nebo operací zabalení, jak je znázorněno zde:</span><span class="sxs-lookup"><span data-stu-id="18fbb-104">For example, by using a generic type parameter `T`, you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>

[!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]

<span data-ttu-id="18fbb-105">Obecné třídy a metody kombinují opětovnou použitelnost, bezpečnost typů a účinnost způsobem, který jejich neobecné protějšky nemohou.</span><span class="sxs-lookup"><span data-stu-id="18fbb-105">Generic classes and methods combine reusability, type safety, and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="18fbb-106">Obecné typy se nejčastěji používají s kolekcemi a metodami, které na nich pracují.</span><span class="sxs-lookup"><span data-stu-id="18fbb-106">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="18fbb-107">Obor <xref:System.Collections.Generic> názvů obsahuje několik obecných tříd kolekce.</span><span class="sxs-lookup"><span data-stu-id="18fbb-107">The <xref:System.Collections.Generic> namespace contains several generic-based collection classes.</span></span> <span data-ttu-id="18fbb-108">Neobecné kolekce, například <xref:System.Collections.ArrayList> nejsou doporučeny a jsou udržovány pro účely kompatibility.</span><span class="sxs-lookup"><span data-stu-id="18fbb-108">The non-generic collections, such as <xref:System.Collections.ArrayList> are not recommended and are maintained for compatibility purposes.</span></span> <span data-ttu-id="18fbb-109">Další informace naleznete [v tématu Generics in .NET](../../../standard/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="18fbb-109">For more information, see [Generics in .NET](../../../standard/generics/index.md).</span></span>

<span data-ttu-id="18fbb-110">Samozřejmě můžete také vytvořit vlastní obecné typy a metody, které poskytují vlastní zobecněná řešení a návrhové vzory, které jsou bezpečné pro daný typ a efektivní.</span><span class="sxs-lookup"><span data-stu-id="18fbb-110">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="18fbb-111">Následující příklad kódu ukazuje jednoduchou obecnou třídu propojeného seznamu pro demonstrační účely.</span><span class="sxs-lookup"><span data-stu-id="18fbb-111">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="18fbb-112">(Ve většině případů byste <xref:System.Collections.Generic.List%601> měli použít třídu poskytovanou knihovnou tříd rozhraní .NET Framework namísto vytváření vlastních.) Parametr `T` type se používá v několika umístěních, kde by se obvykle používal konkrétní typ k označení typu položky uložené v seznamu.</span><span class="sxs-lookup"><span data-stu-id="18fbb-112">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by the .NET Framework class library instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="18fbb-113">Používá se následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="18fbb-113">It is used in the following ways:</span></span>

- <span data-ttu-id="18fbb-114">Jako typ parametru metody `AddHead` v metodě.</span><span class="sxs-lookup"><span data-stu-id="18fbb-114">As the type of a method parameter in the `AddHead` method.</span></span>
- <span data-ttu-id="18fbb-115">Jako návratový typ `Data` vlastnosti v `Node` nosné třídě.</span><span class="sxs-lookup"><span data-stu-id="18fbb-115">As the return type of the `Data` property in the nested `Node` class.</span></span>
- <span data-ttu-id="18fbb-116">Jako typ soukromého `data` člena v vnořené třídě.</span><span class="sxs-lookup"><span data-stu-id="18fbb-116">As the type of the private member `data` in the nested class.</span></span>

 <span data-ttu-id="18fbb-117">Všimněte `T` si, že `Node` je k dispozici vnořené třídy.</span><span class="sxs-lookup"><span data-stu-id="18fbb-117">Note that `T` is available to the nested `Node` class.</span></span> <span data-ttu-id="18fbb-118">Pokud `GenericList<T>` je vytvořena instance s konkrétním typem, `GenericList<int>`například `T` jako , bude `int`každý výskyt nahrazen .</span><span class="sxs-lookup"><span data-stu-id="18fbb-118">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>

[!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]

<span data-ttu-id="18fbb-119">Následující příklad kódu ukazuje, jak `GenericList<T>` kód klienta používá obecnou třídu k vytvoření seznamu celá čísla.</span><span class="sxs-lookup"><span data-stu-id="18fbb-119">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="18fbb-120">Jednoduše změnou argumentu typu lze následující kód snadno upravit tak, aby vytvářel seznamy řetězců nebo jiného vlastního typu:</span><span class="sxs-lookup"><span data-stu-id="18fbb-120">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>

[!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]

## <a name="generics-overview"></a><span data-ttu-id="18fbb-121">Obecný ch od obecně</span><span class="sxs-lookup"><span data-stu-id="18fbb-121">Generics overview</span></span>

- <span data-ttu-id="18fbb-122">Obecné typy slouží k maximalizaci opakovaného použití kódu, bezpečnosti typů a výkonu.</span><span class="sxs-lookup"><span data-stu-id="18fbb-122">Use generic types to maximize code reuse, type safety, and performance.</span></span>
- <span data-ttu-id="18fbb-123">Nejběžnější použití obecných typů je k vytvoření tříd kolekce.</span><span class="sxs-lookup"><span data-stu-id="18fbb-123">The most common use of generics is to create collection classes.</span></span>
- <span data-ttu-id="18fbb-124">Knihovna tříd rozhraní .NET Framework obsahuje <xref:System.Collections.Generic> několik nových obecných tříd kolekce v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="18fbb-124">The .NET Framework class library contains several new generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="18fbb-125">Ty by měly být použity <xref:System.Collections.ArrayList> vždy, když je to možné namísto tříd, <xref:System.Collections> například v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="18fbb-125">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>
- <span data-ttu-id="18fbb-126">Můžete vytvořit vlastní obecná rozhraní, třídy, metody, události a delegáty.</span><span class="sxs-lookup"><span data-stu-id="18fbb-126">You can create your own generic interfaces, classes, methods, events, and delegates.</span></span>
- <span data-ttu-id="18fbb-127">Obecné třídy mohou být omezeny, aby umožnily přístup k metodám na konkrétních datových typech.</span><span class="sxs-lookup"><span data-stu-id="18fbb-127">Generic classes may be constrained to enable access to methods on particular data types.</span></span>
- <span data-ttu-id="18fbb-128">Informace o typech, které se používají v obecném datovém typu, lze získat za běhu pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="18fbb-128">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>

## <a name="related-sections"></a><span data-ttu-id="18fbb-129">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="18fbb-129">Related sections</span></span>

- [<span data-ttu-id="18fbb-130">Parametry obecného typu</span><span class="sxs-lookup"><span data-stu-id="18fbb-130">Generic Type Parameters</span></span>](generic-type-parameters.md)
- [<span data-ttu-id="18fbb-131">Omezení parametrů typů</span><span class="sxs-lookup"><span data-stu-id="18fbb-131">Constraints on Type Parameters</span></span>](constraints-on-type-parameters.md)
- [<span data-ttu-id="18fbb-132">Obecné třídy</span><span class="sxs-lookup"><span data-stu-id="18fbb-132">Generic Classes</span></span>](generic-classes.md)
- [<span data-ttu-id="18fbb-133">Obecná rozhraní</span><span class="sxs-lookup"><span data-stu-id="18fbb-133">Generic Interfaces</span></span>](generic-interfaces.md)
- [<span data-ttu-id="18fbb-134">Obecné metody</span><span class="sxs-lookup"><span data-stu-id="18fbb-134">Generic Methods</span></span>](generic-methods.md)
- [<span data-ttu-id="18fbb-135">Obecní delegáti</span><span class="sxs-lookup"><span data-stu-id="18fbb-135">Generic Delegates</span></span>](generic-delegates.md)
- [<span data-ttu-id="18fbb-136">Rozdíly mezi šablonami C++ a obecnými typy C#</span><span class="sxs-lookup"><span data-stu-id="18fbb-136">Differences Between C++ Templates and C# Generics</span></span>](differences-between-cpp-templates-and-csharp-generics.md)
- [<span data-ttu-id="18fbb-137">Obecné typy a reflexe</span><span class="sxs-lookup"><span data-stu-id="18fbb-137">Generics and Reflection</span></span>](generics-and-reflection.md)
- [<span data-ttu-id="18fbb-138">Obecné typy v běhovém prostředí</span><span class="sxs-lookup"><span data-stu-id="18fbb-138">Generics in the Run Time</span></span>](generics-in-the-run-time.md)

## <a name="c-language-specification"></a><span data-ttu-id="18fbb-139">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="18fbb-139">C# language specification</span></span>

<span data-ttu-id="18fbb-140">Další informace najdete v tématu [Specifikace jazyka C#](~/_csharplang/spec/types.md#constructed-types).</span><span class="sxs-lookup"><span data-stu-id="18fbb-140">For more information, see the [C# Language Specification](~/_csharplang/spec/types.md#constructed-types).</span></span>

## <a name="see-also"></a><span data-ttu-id="18fbb-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="18fbb-141">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="18fbb-142">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="18fbb-142">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="18fbb-143">Typy</span><span class="sxs-lookup"><span data-stu-id="18fbb-143">Types</span></span>](../types/index.md)
- [<span data-ttu-id="18fbb-144">\<typeparam></span><span class="sxs-lookup"><span data-stu-id="18fbb-144">\<typeparam></span></span>](../xmldoc/typeparam.md)
- [<span data-ttu-id="18fbb-145">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="18fbb-145">\<typeparamref></span></span>](../xmldoc/typeparamref.md)
- [<span data-ttu-id="18fbb-146">Obecné typy v .NET</span><span class="sxs-lookup"><span data-stu-id="18fbb-146">Generics in .NET</span></span>](../../../standard/generics/index.md)
