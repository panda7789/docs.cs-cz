---
title: Obecné typy (Průvodce programováním v C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
caps.latest.revision: 23
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0804ca0fcefcc53e06352accf9a2db19edb31037
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="5436e-102">Obecné typy (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="5436e-102">Generics (C# Programming Guide)</span></span>
<span data-ttu-id="5436e-103">Obecné typy byly přidány do verze 2.0 jazyka C# a modul CLR (CLR).</span><span class="sxs-lookup"><span data-stu-id="5436e-103">Generics were added to version 2.0 of the C# language and the common language runtime (CLR).</span></span> <span data-ttu-id="5436e-104">Obecné typy představit rozhraní .NET Framework koncept parametry typu, které umožňují provádět návrhu třídy a metody, které odložení specifikace jeden nebo více typů, dokud třída nebo metoda je deklarována a vytvořena kódem na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="5436e-104">Generics introduce to the .NET Framework the concept of type parameters, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="5436e-105">Například můžete pomocí parametr obecného typu T zápisu jednu třídu, která jiný kód klienta můžete použít aniž by docházelo k náklady nebo riziko přetypování runtime nebo zabalení operace, jak je vidět tady:</span><span class="sxs-lookup"><span data-stu-id="5436e-105">For example, by using a generic type parameter T you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#1](../../../csharp/programming-guide/generics/codesnippet/CSharp/index_1.cs)]  
  
## <a name="generics-overview"></a><span data-ttu-id="5436e-106">Přehled obecných typů</span><span class="sxs-lookup"><span data-stu-id="5436e-106">Generics Overview</span></span>  
  
-   <span data-ttu-id="5436e-107">Použijte obecné typy a maximalizovat tak opakované použití kódu, typ zabezpečení a výkonu.</span><span class="sxs-lookup"><span data-stu-id="5436e-107">Use generic types to maximize code reuse, type safety, and performance.</span></span>  
  
-   <span data-ttu-id="5436e-108">Obecné typy slouží nejčastěji pro vytvoření kolekce tříd.</span><span class="sxs-lookup"><span data-stu-id="5436e-108">The most common use of generics is to create collection classes.</span></span>  
  
-   <span data-ttu-id="5436e-109">Obsahuje několik nových tříd obecnou kolekci v knihovně tříd rozhraní .NET Framework <xref:System.Collections.Generic> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5436e-109">The .NET Framework class library contains several new generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="5436e-110">Tyto by měl použít, kdykoli je možné místo třídy, jako <xref:System.Collections.ArrayList> v <xref:System.Collections> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5436e-110">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>  
  
-   <span data-ttu-id="5436e-111">Můžete vytvořit vlastní obecná rozhraní, tříd, metod, události a delegáti.</span><span class="sxs-lookup"><span data-stu-id="5436e-111">You can create your own generic interfaces, classes, methods, events and delegates.</span></span>  
  
-   <span data-ttu-id="5436e-112">Obecné třídy může být omezené na povolení přístupu k metodám pro konkrétní datové typy.</span><span class="sxs-lookup"><span data-stu-id="5436e-112">Generic classes may be constrained to enable access to methods on particular data types.</span></span>  
  
-   <span data-ttu-id="5436e-113">Informace o typech, které se používají v obecný typ dat může získat za běhu pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="5436e-113">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5436e-114">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="5436e-114">Related Sections</span></span>  
 <span data-ttu-id="5436e-115">Další informace:</span><span class="sxs-lookup"><span data-stu-id="5436e-115">For more information:</span></span>  
  
-   [<span data-ttu-id="5436e-116">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="5436e-116">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
  
-   [<span data-ttu-id="5436e-117">Výhody obecných typů</span><span class="sxs-lookup"><span data-stu-id="5436e-117">Benefits of Generics</span></span>](../../../csharp/programming-guide/generics/benefits-of-generics.md)  
  
-   [<span data-ttu-id="5436e-118">Parametry obecného typu</span><span class="sxs-lookup"><span data-stu-id="5436e-118">Generic Type Parameters</span></span>](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
-   [<span data-ttu-id="5436e-119">Omezení parametrů typů</span><span class="sxs-lookup"><span data-stu-id="5436e-119">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
-   [<span data-ttu-id="5436e-120">Obecné třídy</span><span class="sxs-lookup"><span data-stu-id="5436e-120">Generic Classes</span></span>](../../../csharp/programming-guide/generics/generic-classes.md)  
  
-   [<span data-ttu-id="5436e-121">Obecná rozhraní</span><span class="sxs-lookup"><span data-stu-id="5436e-121">Generic Interfaces</span></span>](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
-   [<span data-ttu-id="5436e-122">Obecné metody</span><span class="sxs-lookup"><span data-stu-id="5436e-122">Generic Methods</span></span>](../../../csharp/programming-guide/generics/generic-methods.md)  
  
-   [<span data-ttu-id="5436e-123">Obecní delegáti</span><span class="sxs-lookup"><span data-stu-id="5436e-123">Generic Delegates</span></span>](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
-   [<span data-ttu-id="5436e-124">Rozdíly mezi šablonami C++ a obecnými typy C#</span><span class="sxs-lookup"><span data-stu-id="5436e-124">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
-   [<span data-ttu-id="5436e-125">Obecné typy a reflexe</span><span class="sxs-lookup"><span data-stu-id="5436e-125">Generics and Reflection</span></span>](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
-   [<span data-ttu-id="5436e-126">Obecné typy v běhovém prostředí</span><span class="sxs-lookup"><span data-stu-id="5436e-126">Generics in the Run Time</span></span>](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
-   [<span data-ttu-id="5436e-127">Obecné typy v knihovně tříd rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5436e-127">Generics in the .NET Framework Class Library</span></span>](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="5436e-128">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5436e-128">C# Language Specification</span></span>  
 <span data-ttu-id="5436e-129">Další informace najdete v tématu [Specifikace jazyka C#](../../../csharp/language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="5436e-129">For more information, see the [C# Language Specification](../../../csharp/language-reference/language-specification/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5436e-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="5436e-130">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="5436e-131">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="5436e-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5436e-132">Typy</span><span class="sxs-lookup"><span data-stu-id="5436e-132">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
 [<span data-ttu-id="5436e-133">\<typeparam ></span><span class="sxs-lookup"><span data-stu-id="5436e-133">\<typeparam></span></span>](../../../csharp/programming-guide/xmldoc/typeparam.md)  
 [<span data-ttu-id="5436e-134">\<typeparamref ></span><span class="sxs-lookup"><span data-stu-id="5436e-134">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)
