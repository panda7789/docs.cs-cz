---
title: Obecné typy (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: 8f412366072c81b8aaca94829e0aa214f356200d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333811"
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="09826-102">Obecné typy (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="09826-102">Generics (C# Programming Guide)</span></span>
<span data-ttu-id="09826-103">Obecné typy byly přidány do verze 2.0 jazyka C# a modul CLR (CLR).</span><span class="sxs-lookup"><span data-stu-id="09826-103">Generics were added to version 2.0 of the C# language and the common language runtime (CLR).</span></span> <span data-ttu-id="09826-104">Obecné typy představit rozhraní .NET Framework koncept parametry typu, které umožňují provádět návrhu třídy a metody, které odložení specifikace jeden nebo více typů, dokud třída nebo metoda je deklarována a vytvořena kódem na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="09826-104">Generics introduce to the .NET Framework the concept of type parameters, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="09826-105">Například můžete pomocí parametr obecného typu T zápisu jednu třídu, která jiný kód klienta můžete použít aniž by docházelo k náklady nebo riziko přetypování runtime nebo zabalení operace, jak je vidět tady:</span><span class="sxs-lookup"><span data-stu-id="09826-105">For example, by using a generic type parameter T you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#1](../../../csharp/programming-guide/generics/codesnippet/CSharp/index_1.cs)]  
  
## <a name="generics-overview"></a><span data-ttu-id="09826-106">Přehled obecných typů</span><span class="sxs-lookup"><span data-stu-id="09826-106">Generics Overview</span></span>  
  
-   <span data-ttu-id="09826-107">Použijte obecné typy a maximalizovat tak opakované použití kódu, typ zabezpečení a výkonu.</span><span class="sxs-lookup"><span data-stu-id="09826-107">Use generic types to maximize code reuse, type safety, and performance.</span></span>  
  
-   <span data-ttu-id="09826-108">Obecné typy slouží nejčastěji pro vytvoření kolekce tříd.</span><span class="sxs-lookup"><span data-stu-id="09826-108">The most common use of generics is to create collection classes.</span></span>  
  
-   <span data-ttu-id="09826-109">Obsahuje několik nových tříd obecnou kolekci v knihovně tříd rozhraní .NET Framework <xref:System.Collections.Generic> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="09826-109">The .NET Framework class library contains several new generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="09826-110">Tyto by měl použít, kdykoli je možné místo třídy, jako <xref:System.Collections.ArrayList> v <xref:System.Collections> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="09826-110">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>  
  
-   <span data-ttu-id="09826-111">Můžete vytvořit vlastní obecná rozhraní, tříd, metod, události a delegáti.</span><span class="sxs-lookup"><span data-stu-id="09826-111">You can create your own generic interfaces, classes, methods, events and delegates.</span></span>  
  
-   <span data-ttu-id="09826-112">Obecné třídy může být omezené na povolení přístupu k metodám pro konkrétní datové typy.</span><span class="sxs-lookup"><span data-stu-id="09826-112">Generic classes may be constrained to enable access to methods on particular data types.</span></span>  
  
-   <span data-ttu-id="09826-113">Informace o typech, které se používají v obecný typ dat může získat za běhu pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="09826-113">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="09826-114">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="09826-114">Related Sections</span></span>  
 <span data-ttu-id="09826-115">Další informace:</span><span class="sxs-lookup"><span data-stu-id="09826-115">For more information:</span></span>  
  
-   [<span data-ttu-id="09826-116">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="09826-116">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
  
-   [<span data-ttu-id="09826-117">Výhody obecných typů</span><span class="sxs-lookup"><span data-stu-id="09826-117">Benefits of Generics</span></span>](../../../csharp/programming-guide/generics/benefits-of-generics.md)  
  
-   [<span data-ttu-id="09826-118">Parametry obecného typu</span><span class="sxs-lookup"><span data-stu-id="09826-118">Generic Type Parameters</span></span>](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
-   [<span data-ttu-id="09826-119">Omezení parametrů typů</span><span class="sxs-lookup"><span data-stu-id="09826-119">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
-   [<span data-ttu-id="09826-120">Obecné třídy</span><span class="sxs-lookup"><span data-stu-id="09826-120">Generic Classes</span></span>](../../../csharp/programming-guide/generics/generic-classes.md)  
  
-   [<span data-ttu-id="09826-121">Obecná rozhraní</span><span class="sxs-lookup"><span data-stu-id="09826-121">Generic Interfaces</span></span>](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
-   [<span data-ttu-id="09826-122">Obecné metody</span><span class="sxs-lookup"><span data-stu-id="09826-122">Generic Methods</span></span>](../../../csharp/programming-guide/generics/generic-methods.md)  
  
-   [<span data-ttu-id="09826-123">Obecní delegáti</span><span class="sxs-lookup"><span data-stu-id="09826-123">Generic Delegates</span></span>](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
-   [<span data-ttu-id="09826-124">Rozdíly mezi šablonami C++ a obecnými typy C#</span><span class="sxs-lookup"><span data-stu-id="09826-124">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
-   [<span data-ttu-id="09826-125">Obecné typy a reflexe</span><span class="sxs-lookup"><span data-stu-id="09826-125">Generics and Reflection</span></span>](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
-   [<span data-ttu-id="09826-126">Obecné typy v běhovém prostředí</span><span class="sxs-lookup"><span data-stu-id="09826-126">Generics in the Run Time</span></span>](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="09826-127">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="09826-127">C# Language Specification</span></span>  
 <span data-ttu-id="09826-128">Další informace najdete v tématu [Specifikace jazyka C#](../../../csharp/language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="09826-128">For more information, see the [C# Language Specification](../../../csharp/language-reference/language-specification/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09826-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="09826-129">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="09826-130">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="09826-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="09826-131">Typy</span><span class="sxs-lookup"><span data-stu-id="09826-131">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
 [<span data-ttu-id="09826-132">\<typeparam ></span><span class="sxs-lookup"><span data-stu-id="09826-132">\<typeparam></span></span>](../../../csharp/programming-guide/xmldoc/typeparam.md)  
 [<span data-ttu-id="09826-133">\<typeparamref ></span><span class="sxs-lookup"><span data-stu-id="09826-133">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)  
 [<span data-ttu-id="09826-134">Obecné typy v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="09826-134">Generics in .NET</span></span>](../../../standard/generics/index.md)  