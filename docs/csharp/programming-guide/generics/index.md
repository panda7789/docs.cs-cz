---
title: Obecné typy - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: 186c5bc91204770e636eed5c008db23b798b6880
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61710248"
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="6f1b1-102">Obecné typy (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="6f1b1-102">Generics (C# Programming Guide)</span></span>
<span data-ttu-id="6f1b1-103">Obecné typy byly přidány do verze 2.0 jazyka C# a common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="6f1b1-103">Generics were added to version 2.0 of the C# language and the common language runtime (CLR).</span></span> <span data-ttu-id="6f1b1-104">Obecné typy rozhraní .NET Framework přinášejí koncept parametry typu, které umožňují návrh tříd a metod, které specifikace jeden nebo více typů odložit, dokud třídy nebo metody je deklarována a vytvořena kódem na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="6f1b1-104">Generics introduce to the .NET Framework the concept of type parameters, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="6f1b1-105">Například můžete pomocí parametru obecného typu T napsat jednu třídu, jiný kód klienta můžete použít bez dalších nákladů na náklady nebo rizikem přetypování modulu runtime nebo operace zabalení, jak je znázorněno zde:</span><span class="sxs-lookup"><span data-stu-id="6f1b1-105">For example, by using a generic type parameter T you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]  
  
## <a name="generics-overview"></a><span data-ttu-id="6f1b1-106">Přehled obecných typů</span><span class="sxs-lookup"><span data-stu-id="6f1b1-106">Generics Overview</span></span>  
  
- <span data-ttu-id="6f1b1-107">Maximalizujte opakované využívání kódu, bezpečnost typů a výkonu pomocí obecných typů.</span><span class="sxs-lookup"><span data-stu-id="6f1b1-107">Use generic types to maximize code reuse, type safety, and performance.</span></span>  
  
- <span data-ttu-id="6f1b1-108">Nejběžnější použití obecných typů je pro vytvoření kolekce tříd.</span><span class="sxs-lookup"><span data-stu-id="6f1b1-108">The most common use of generics is to create collection classes.</span></span>  
  
- <span data-ttu-id="6f1b1-109">Obsahuje několik nových obecné kolekce tříd v knihovně tříd rozhraní .NET Framework <xref:System.Collections.Generic> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6f1b1-109">The .NET Framework class library contains several new generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="6f1b1-110">Ty se používají vždy, když je možné namísto třídy, jako <xref:System.Collections.ArrayList> v <xref:System.Collections> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6f1b1-110">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>  
  
- <span data-ttu-id="6f1b1-111">Můžete vytvořit vlastní obecných rozhraní, třídy, metody, události a delegáti.</span><span class="sxs-lookup"><span data-stu-id="6f1b1-111">You can create your own generic interfaces, classes, methods, events and delegates.</span></span>  
  
- <span data-ttu-id="6f1b1-112">Obecné třídy může být omezený na povolení přístupu k metodám pro konkrétní datové typy.</span><span class="sxs-lookup"><span data-stu-id="6f1b1-112">Generic classes may be constrained to enable access to methods on particular data types.</span></span>  
  
- <span data-ttu-id="6f1b1-113">Informace o typech, které se používají v obecného datového typu mohou být získány při spuštění pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="6f1b1-113">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6f1b1-114">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="6f1b1-114">Related Sections</span></span>  
 <span data-ttu-id="6f1b1-115">Další informace:</span><span class="sxs-lookup"><span data-stu-id="6f1b1-115">For more information:</span></span>  
  
- [<span data-ttu-id="6f1b1-116">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="6f1b1-116">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
  
- [<span data-ttu-id="6f1b1-117">Výhody obecných typů</span><span class="sxs-lookup"><span data-stu-id="6f1b1-117">Benefits of Generics</span></span>](../../../csharp/programming-guide/generics/benefits-of-generics.md)  
  
- [<span data-ttu-id="6f1b1-118">Parametry obecného typu</span><span class="sxs-lookup"><span data-stu-id="6f1b1-118">Generic Type Parameters</span></span>](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
- [<span data-ttu-id="6f1b1-119">Omezení parametrů typů</span><span class="sxs-lookup"><span data-stu-id="6f1b1-119">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
- [<span data-ttu-id="6f1b1-120">Obecné třídy</span><span class="sxs-lookup"><span data-stu-id="6f1b1-120">Generic Classes</span></span>](../../../csharp/programming-guide/generics/generic-classes.md)  
  
- [<span data-ttu-id="6f1b1-121">Obecná rozhraní</span><span class="sxs-lookup"><span data-stu-id="6f1b1-121">Generic Interfaces</span></span>](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
- [<span data-ttu-id="6f1b1-122">Obecné metody</span><span class="sxs-lookup"><span data-stu-id="6f1b1-122">Generic Methods</span></span>](../../../csharp/programming-guide/generics/generic-methods.md)  
  
- [<span data-ttu-id="6f1b1-123">Obecní delegáti</span><span class="sxs-lookup"><span data-stu-id="6f1b1-123">Generic Delegates</span></span>](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
- [<span data-ttu-id="6f1b1-124">Rozdíly mezi šablonami C++ a obecnými typy C#</span><span class="sxs-lookup"><span data-stu-id="6f1b1-124">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
- [<span data-ttu-id="6f1b1-125">Obecné typy a reflexe</span><span class="sxs-lookup"><span data-stu-id="6f1b1-125">Generics and Reflection</span></span>](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
- [<span data-ttu-id="6f1b1-126">Obecné typy v běhovém prostředí</span><span class="sxs-lookup"><span data-stu-id="6f1b1-126">Generics in the Run Time</span></span>](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="6f1b1-127">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6f1b1-127">C# Language Specification</span></span>  
 <span data-ttu-id="6f1b1-128">Další informace najdete v tématu [Specifikace jazyka C#](~/_csharplang/spec/types.md#constructed-types).</span><span class="sxs-lookup"><span data-stu-id="6f1b1-128">For more information, see the [C# Language Specification](~/_csharplang/spec/types.md#constructed-types).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f1b1-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6f1b1-129">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="6f1b1-130">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="6f1b1-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="6f1b1-131">Typy</span><span class="sxs-lookup"><span data-stu-id="6f1b1-131">Types</span></span>](../../../csharp/programming-guide/types/index.md)
- [<span data-ttu-id="6f1b1-132">\<typeparam ></span><span class="sxs-lookup"><span data-stu-id="6f1b1-132">\<typeparam></span></span>](../../../csharp/programming-guide/xmldoc/typeparam.md)
- [<span data-ttu-id="6f1b1-133">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="6f1b1-133">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)
- [<span data-ttu-id="6f1b1-134">Obecné typy v .NET</span><span class="sxs-lookup"><span data-stu-id="6f1b1-134">Generics in .NET</span></span>](../../../standard/generics/index.md)
