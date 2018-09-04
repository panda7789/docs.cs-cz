---
title: Obecné typy (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: 638612a0ece8e701b088c97e5dfc49362e6d6419
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506078"
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="bb236-102">Obecné typy (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="bb236-102">Generics (C# Programming Guide)</span></span>
<span data-ttu-id="bb236-103">Obecné typy byly přidány do verze 2.0 jazyka C# a common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="bb236-103">Generics were added to version 2.0 of the C# language and the common language runtime (CLR).</span></span> <span data-ttu-id="bb236-104">Obecné typy rozhraní .NET Framework přinášejí koncept parametry typu, které umožňují návrh tříd a metod, které specifikace jeden nebo více typů odložit, dokud třídy nebo metody je deklarována a vytvořena kódem na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="bb236-104">Generics introduce to the .NET Framework the concept of type parameters, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="bb236-105">Například můžete pomocí parametru obecného typu T napsat jednu třídu, jiný kód klienta můžete použít bez dalších nákladů na náklady nebo rizikem přetypování modulu runtime nebo operace zabalení, jak je znázorněno zde:</span><span class="sxs-lookup"><span data-stu-id="bb236-105">For example, by using a generic type parameter T you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#1](../../../csharp/programming-guide/generics/codesnippet/CSharp/index_1.cs)]  
  
## <a name="generics-overview"></a><span data-ttu-id="bb236-106">Přehled obecných typů</span><span class="sxs-lookup"><span data-stu-id="bb236-106">Generics Overview</span></span>  
  
-   <span data-ttu-id="bb236-107">Maximalizujte opakované využívání kódu, bezpečnost typů a výkonu pomocí obecných typů.</span><span class="sxs-lookup"><span data-stu-id="bb236-107">Use generic types to maximize code reuse, type safety, and performance.</span></span>  
  
-   <span data-ttu-id="bb236-108">Nejběžnější použití obecných typů je pro vytvoření kolekce tříd.</span><span class="sxs-lookup"><span data-stu-id="bb236-108">The most common use of generics is to create collection classes.</span></span>  
  
-   <span data-ttu-id="bb236-109">Obsahuje několik nových obecné kolekce tříd v knihovně tříd rozhraní .NET Framework <xref:System.Collections.Generic> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="bb236-109">The .NET Framework class library contains several new generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="bb236-110">Ty se používají vždy, když je možné namísto třídy, jako <xref:System.Collections.ArrayList> v <xref:System.Collections> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="bb236-110">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>  
  
-   <span data-ttu-id="bb236-111">Můžete vytvořit vlastní obecných rozhraní, třídy, metody, události a delegáti.</span><span class="sxs-lookup"><span data-stu-id="bb236-111">You can create your own generic interfaces, classes, methods, events and delegates.</span></span>  
  
-   <span data-ttu-id="bb236-112">Obecné třídy může být omezený na povolení přístupu k metodám pro konkrétní datové typy.</span><span class="sxs-lookup"><span data-stu-id="bb236-112">Generic classes may be constrained to enable access to methods on particular data types.</span></span>  
  
-   <span data-ttu-id="bb236-113">Informace o typech, které se používají v obecného datového typu mohou být získány při spuštění pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="bb236-113">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bb236-114">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="bb236-114">Related Sections</span></span>  
 <span data-ttu-id="bb236-115">Další informace:</span><span class="sxs-lookup"><span data-stu-id="bb236-115">For more information:</span></span>  
  
-   [<span data-ttu-id="bb236-116">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="bb236-116">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
  
-   [<span data-ttu-id="bb236-117">Výhody obecných typů</span><span class="sxs-lookup"><span data-stu-id="bb236-117">Benefits of Generics</span></span>](../../../csharp/programming-guide/generics/benefits-of-generics.md)  
  
-   [<span data-ttu-id="bb236-118">Parametry obecného typu</span><span class="sxs-lookup"><span data-stu-id="bb236-118">Generic Type Parameters</span></span>](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
-   [<span data-ttu-id="bb236-119">Omezení parametrů typů</span><span class="sxs-lookup"><span data-stu-id="bb236-119">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
-   [<span data-ttu-id="bb236-120">Obecné třídy</span><span class="sxs-lookup"><span data-stu-id="bb236-120">Generic Classes</span></span>](../../../csharp/programming-guide/generics/generic-classes.md)  
  
-   [<span data-ttu-id="bb236-121">Obecná rozhraní</span><span class="sxs-lookup"><span data-stu-id="bb236-121">Generic Interfaces</span></span>](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
-   [<span data-ttu-id="bb236-122">Obecné metody</span><span class="sxs-lookup"><span data-stu-id="bb236-122">Generic Methods</span></span>](../../../csharp/programming-guide/generics/generic-methods.md)  
  
-   [<span data-ttu-id="bb236-123">Obecní delegáti</span><span class="sxs-lookup"><span data-stu-id="bb236-123">Generic Delegates</span></span>](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
-   [<span data-ttu-id="bb236-124">Rozdíly mezi šablonami C++ a obecnými typy C#</span><span class="sxs-lookup"><span data-stu-id="bb236-124">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
-   [<span data-ttu-id="bb236-125">Obecné typy a reflexe</span><span class="sxs-lookup"><span data-stu-id="bb236-125">Generics and Reflection</span></span>](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
-   [<span data-ttu-id="bb236-126">Obecné typy v běhovém prostředí</span><span class="sxs-lookup"><span data-stu-id="bb236-126">Generics in the Run Time</span></span>](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="bb236-127">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bb236-127">C# Language Specification</span></span>  
 <span data-ttu-id="bb236-128">Další informace najdete v tématu [Specifikace jazyka C#](../../../csharp/language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="bb236-128">For more information, see the [C# Language Specification](../../../csharp/language-reference/language-specification/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb236-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="bb236-129">See Also</span></span>

- <xref:System.Collections.Generic>  
- [<span data-ttu-id="bb236-130">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="bb236-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="bb236-131">Typy</span><span class="sxs-lookup"><span data-stu-id="bb236-131">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
- [<span data-ttu-id="bb236-132">\<typeparam ></span><span class="sxs-lookup"><span data-stu-id="bb236-132">\<typeparam></span></span>](../../../csharp/programming-guide/xmldoc/typeparam.md)  
- [<span data-ttu-id="bb236-133">\<typeparamref ></span><span class="sxs-lookup"><span data-stu-id="bb236-133">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)  
- [<span data-ttu-id="bb236-134">Obecné typy v .NET</span><span class="sxs-lookup"><span data-stu-id="bb236-134">Generics in .NET</span></span>](../../../standard/generics/index.md)  