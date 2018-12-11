---
title: Obecné typy a pole - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: 50d649c4662114e76fdc0a6161ab0cbbeb04756d
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237451"
---
# <a name="generics-and-arrays-c-programming-guide"></a><span data-ttu-id="5cdf1-102">Obecné typy a pole (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="5cdf1-102">Generics and Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="5cdf1-103">V jazyce C# 2.0 nebo novější, jednorozměrné pole, které mají nižší mez nula automaticky implementovat <xref:System.Collections.Generic.IList%601>.</span><span class="sxs-lookup"><span data-stu-id="5cdf1-103">In C# 2.0 and later, single-dimensional arrays that have a lower bound of zero automatically implement <xref:System.Collections.Generic.IList%601>.</span></span> <span data-ttu-id="5cdf1-104">To umožňuje vytvořit obecné metody, které můžete použít stejný kód k iteraci v rámci pole a typy kolekcí.</span><span class="sxs-lookup"><span data-stu-id="5cdf1-104">This enables you to create generic methods that can use the same code to iterate through arrays and other collection types.</span></span> <span data-ttu-id="5cdf1-105">Tato technika je užitečné hlavně pro čtení dat v kolekcích.</span><span class="sxs-lookup"><span data-stu-id="5cdf1-105">This technique is primarily useful for reading data in collections.</span></span> <span data-ttu-id="5cdf1-106"><xref:System.Collections.Generic.IList%601> Rozhraní nelze použít k přidání nebo odebrání prvků pole.</span><span class="sxs-lookup"><span data-stu-id="5cdf1-106">The <xref:System.Collections.Generic.IList%601> interface cannot be used to add or remove elements from an array.</span></span> <span data-ttu-id="5cdf1-107">Bude vyvolána výjimka, pokud se pokusíte volat <xref:System.Collections.Generic.IList%601> metody, jako <xref:System.Collections.Generic.IList%601.RemoveAt%2A> na pole v tomto kontextu.</span><span class="sxs-lookup"><span data-stu-id="5cdf1-107">An exception will be thrown if you try to call an <xref:System.Collections.Generic.IList%601> method such as <xref:System.Collections.Generic.IList%601.RemoveAt%2A> on an array in this context.</span></span>  
  
 <span data-ttu-id="5cdf1-108">Následující příklad kódu ukazuje, jak jedné obecné metody, která přebírá <xref:System.Collections.Generic.IList%601> vstupní parametr iterovat přes seznam a pole, v tomto případě pole celých čísel.</span><span class="sxs-lookup"><span data-stu-id="5cdf1-108">The following code example demonstrates how a single generic method that takes an <xref:System.Collections.Generic.IList%601> input parameter can iterate through both a list and an array, in this case an array of integers.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#35](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-arrays_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="5cdf1-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="5cdf1-109">See Also</span></span>

- <xref:System.Collections.Generic>  
- [<span data-ttu-id="5cdf1-110">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="5cdf1-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="5cdf1-111">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="5cdf1-111">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
- [<span data-ttu-id="5cdf1-112">Pole</span><span class="sxs-lookup"><span data-stu-id="5cdf1-112">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
- [<span data-ttu-id="5cdf1-113">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="5cdf1-113">Generics</span></span>](~/docs/standard/generics/index.md)
