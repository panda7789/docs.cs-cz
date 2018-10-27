---
title: Obecné typy (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: 9aa57fd31b8d969bbbbf4329a028007f42d3e097
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50042308"
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="3473f-102">Obecné typy (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="3473f-102">Generics (C# Programming Guide)</span></span>
<span data-ttu-id="3473f-103">Obecné typy byly přidány do verze 2.0 jazyka C# a common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="3473f-103">Generics were added to version 2.0 of the C# language and the common language runtime (CLR).</span></span> <span data-ttu-id="3473f-104">Obecné typy rozhraní .NET Framework přinášejí koncept parametry typu, které umožňují návrh tříd a metod, které specifikace jeden nebo více typů odložit, dokud třídy nebo metody je deklarována a vytvořena kódem na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="3473f-104">Generics introduce to the .NET Framework the concept of type parameters, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="3473f-105">Například můžete pomocí parametru obecného typu T napsat jednu třídu, jiný kód klienta můžete použít bez dalších nákladů na náklady nebo rizikem přetypování modulu runtime nebo operace zabalení, jak je znázorněno zde:</span><span class="sxs-lookup"><span data-stu-id="3473f-105">For example, by using a generic type parameter T you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#1](../../../csharp/programming-guide/generics/codesnippet/CSharp/index_1.cs)]  
  
## <a name="generics-overview"></a><span data-ttu-id="3473f-106">Přehled obecných typů</span><span class="sxs-lookup"><span data-stu-id="3473f-106">Generics Overview</span></span>  
  
-   <span data-ttu-id="3473f-107">Maximalizujte opakované využívání kódu, bezpečnost typů a výkonu pomocí obecných typů.</span><span class="sxs-lookup"><span data-stu-id="3473f-107">Use generic types to maximize code reuse, type safety, and performance.</span></span>  
  
-   <span data-ttu-id="3473f-108">Nejběžnější použití obecných typů je pro vytvoření kolekce tříd.</span><span class="sxs-lookup"><span data-stu-id="3473f-108">The most common use of generics is to create collection classes.</span></span>  
  
-   <span data-ttu-id="3473f-109">Obsahuje několik nových obecné kolekce tříd v knihovně tříd rozhraní .NET Framework <xref:System.Collections.Generic> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3473f-109">The .NET Framework class library contains several new generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="3473f-110">Ty se používají vždy, když je možné namísto třídy, jako <xref:System.Collections.ArrayList> v <xref:System.Collections> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3473f-110">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>  
  
-   <span data-ttu-id="3473f-111">Můžete vytvořit vlastní obecných rozhraní, třídy, metody, události a delegáti.</span><span class="sxs-lookup"><span data-stu-id="3473f-111">You can create your own generic interfaces, classes, methods, events and delegates.</span></span>  
  
-   <span data-ttu-id="3473f-112">Obecné třídy může být omezený na povolení přístupu k metodám pro konkrétní datové typy.</span><span class="sxs-lookup"><span data-stu-id="3473f-112">Generic classes may be constrained to enable access to methods on particular data types.</span></span>  
  
-   <span data-ttu-id="3473f-113">Informace o typech, které se používají v obecného datového typu mohou být získány při spuštění pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="3473f-113">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3473f-114">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="3473f-114">Related Sections</span></span>  
 <span data-ttu-id="3473f-115">Další informace:</span><span class="sxs-lookup"><span data-stu-id="3473f-115">For more information:</span></span>  
  
-   [<span data-ttu-id="3473f-116">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="3473f-116">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
  
-   [<span data-ttu-id="3473f-117">Výhody obecných typů</span><span class="sxs-lookup"><span data-stu-id="3473f-117">Benefits of Generics</span></span>](../../../csharp/programming-guide/generics/benefits-of-generics.md)  
  
-   [<span data-ttu-id="3473f-118">Parametry obecného typu</span><span class="sxs-lookup"><span data-stu-id="3473f-118">Generic Type Parameters</span></span>](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
-   [<span data-ttu-id="3473f-119">Omezení parametrů typů</span><span class="sxs-lookup"><span data-stu-id="3473f-119">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
-   [<span data-ttu-id="3473f-120">Obecné třídy</span><span class="sxs-lookup"><span data-stu-id="3473f-120">Generic Classes</span></span>](../../../csharp/programming-guide/generics/generic-classes.md)  
  
-   [<span data-ttu-id="3473f-121">Obecná rozhraní</span><span class="sxs-lookup"><span data-stu-id="3473f-121">Generic Interfaces</span></span>](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
-   [<span data-ttu-id="3473f-122">Obecné metody</span><span class="sxs-lookup"><span data-stu-id="3473f-122">Generic Methods</span></span>](../../../csharp/programming-guide/generics/generic-methods.md)  
  
-   [<span data-ttu-id="3473f-123">Obecní delegáti</span><span class="sxs-lookup"><span data-stu-id="3473f-123">Generic Delegates</span></span>](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
-   [<span data-ttu-id="3473f-124">Rozdíly mezi šablonami C++ a obecnými typy C#</span><span class="sxs-lookup"><span data-stu-id="3473f-124">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
-   [<span data-ttu-id="3473f-125">Obecné typy a reflexe</span><span class="sxs-lookup"><span data-stu-id="3473f-125">Generics and Reflection</span></span>](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
-   [<span data-ttu-id="3473f-126">Obecné typy v běhovém prostředí</span><span class="sxs-lookup"><span data-stu-id="3473f-126">Generics in the Run Time</span></span>](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="3473f-127">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3473f-127">C# Language Specification</span></span>  
 <span data-ttu-id="3473f-128">Další informace najdete v tématu [Specifikace jazyka C#](~/_csharplang/spec/types.md#constructed-types).</span><span class="sxs-lookup"><span data-stu-id="3473f-128">For more information, see the [C# Language Specification](~/_csharplang/spec/types.md#constructed-types).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3473f-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="3473f-129">See Also</span></span>

- <xref:System.Collections.Generic>  
- [<span data-ttu-id="3473f-130">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="3473f-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="3473f-131">Typy</span><span class="sxs-lookup"><span data-stu-id="3473f-131">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
- [<span data-ttu-id="3473f-132">\<typeparam ></span><span class="sxs-lookup"><span data-stu-id="3473f-132">\<typeparam></span></span>](../../../csharp/programming-guide/xmldoc/typeparam.md)  
- [<span data-ttu-id="3473f-133">\<typeparamref ></span><span class="sxs-lookup"><span data-stu-id="3473f-133">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)  
- [<span data-ttu-id="3473f-134">Obecné typy v .NET</span><span class="sxs-lookup"><span data-stu-id="3473f-134">Generics in .NET</span></span>](../../../standard/generics/index.md)  