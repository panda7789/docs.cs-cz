---
title: Obecné typy a pole - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: 145203d259b943bea1f43a9e49db2c7889bf914a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978907"
---
# <a name="generics-and-arrays-c-programming-guide"></a><span data-ttu-id="b1dfd-102">Obecné typy a pole (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="b1dfd-102">Generics and Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="b1dfd-103">V jazyce C# 2.0 nebo novější, jednorozměrné pole, které mají nižší mez nula automaticky implementovat <xref:System.Collections.Generic.IList%601>.</span><span class="sxs-lookup"><span data-stu-id="b1dfd-103">In C# 2.0 and later, single-dimensional arrays that have a lower bound of zero automatically implement <xref:System.Collections.Generic.IList%601>.</span></span> <span data-ttu-id="b1dfd-104">To umožňuje vytvořit obecné metody, které můžete použít stejný kód k iteraci v rámci pole a typy kolekcí.</span><span class="sxs-lookup"><span data-stu-id="b1dfd-104">This enables you to create generic methods that can use the same code to iterate through arrays and other collection types.</span></span> <span data-ttu-id="b1dfd-105">Tato technika je užitečné hlavně pro čtení dat v kolekcích.</span><span class="sxs-lookup"><span data-stu-id="b1dfd-105">This technique is primarily useful for reading data in collections.</span></span> <span data-ttu-id="b1dfd-106"><xref:System.Collections.Generic.IList%601> Rozhraní nelze použít k přidání nebo odebrání prvků pole.</span><span class="sxs-lookup"><span data-stu-id="b1dfd-106">The <xref:System.Collections.Generic.IList%601> interface cannot be used to add or remove elements from an array.</span></span> <span data-ttu-id="b1dfd-107">Bude vyvolána výjimka, pokud se pokusíte volat <xref:System.Collections.Generic.IList%601> metody, jako <xref:System.Collections.Generic.IList%601.RemoveAt%2A> na pole v tomto kontextu.</span><span class="sxs-lookup"><span data-stu-id="b1dfd-107">An exception will be thrown if you try to call an <xref:System.Collections.Generic.IList%601> method such as <xref:System.Collections.Generic.IList%601.RemoveAt%2A> on an array in this context.</span></span>  
  
 <span data-ttu-id="b1dfd-108">Následující příklad kódu ukazuje, jak jedné obecné metody, která přebírá <xref:System.Collections.Generic.IList%601> vstupní parametr iterovat přes seznam a pole, v tomto případě pole celých čísel.</span><span class="sxs-lookup"><span data-stu-id="b1dfd-108">The following code example demonstrates how a single generic method that takes an <xref:System.Collections.Generic.IList%601> input parameter can iterate through both a list and an array, in this case an array of integers.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a><span data-ttu-id="b1dfd-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1dfd-109">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="b1dfd-110">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b1dfd-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="b1dfd-111">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="b1dfd-111">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
- [<span data-ttu-id="b1dfd-112">Pole</span><span class="sxs-lookup"><span data-stu-id="b1dfd-112">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)
- [<span data-ttu-id="b1dfd-113">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="b1dfd-113">Generics</span></span>](~/docs/standard/generics/index.md)
