---
title: Obecné typy a pole (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: 6cb205d90d4b6de329a179c5969e2d3b543bfb35
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43528497"
---
# <a name="generics-and-arrays-c-programming-guide"></a><span data-ttu-id="4db75-102">Obecné typy a pole (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="4db75-102">Generics and Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="4db75-103">V jazyce C# 2.0 nebo novější, jednorozměrné pole, které mají nižší mez nula automaticky implementovat <xref:System.Collections.Generic.IList%601>.</span><span class="sxs-lookup"><span data-stu-id="4db75-103">In C# 2.0 and later, single-dimensional arrays that have a lower bound of zero automatically implement <xref:System.Collections.Generic.IList%601>.</span></span> <span data-ttu-id="4db75-104">To umožňuje vytvořit obecné metody, které můžete použít stejný kód k iteraci v rámci pole a typy kolekcí.</span><span class="sxs-lookup"><span data-stu-id="4db75-104">This enables you to create generic methods that can use the same code to iterate through arrays and other collection types.</span></span> <span data-ttu-id="4db75-105">Tato technika je užitečné hlavně pro čtení dat v kolekcích.</span><span class="sxs-lookup"><span data-stu-id="4db75-105">This technique is primarily useful for reading data in collections.</span></span> <span data-ttu-id="4db75-106"><xref:System.Collections.Generic.IList%601> Rozhraní nelze použít k přidání nebo odebrání prvků pole.</span><span class="sxs-lookup"><span data-stu-id="4db75-106">The <xref:System.Collections.Generic.IList%601> interface cannot be used to add or remove elements from an array.</span></span> <span data-ttu-id="4db75-107">Bude vyvolána výjimka, pokud se pokusíte volat <xref:System.Collections.Generic.IList%601> metody, jako <xref:System.Collections.Generic.IList%601.RemoveAt%2A> na pole v tomto kontextu.</span><span class="sxs-lookup"><span data-stu-id="4db75-107">An exception will be thrown if you try to call an <xref:System.Collections.Generic.IList%601> method such as <xref:System.Collections.Generic.IList%601.RemoveAt%2A> on an array in this context.</span></span>  
  
 <span data-ttu-id="4db75-108">Následující příklad kódu ukazuje, jak jedné obecné metody, která přebírá <xref:System.Collections.Generic.IList%601> vstupní parametr iterovat přes seznam a pole, v tomto případě pole celých čísel.</span><span class="sxs-lookup"><span data-stu-id="4db75-108">The following code example demonstrates how a single generic method that takes an <xref:System.Collections.Generic.IList%601> input parameter can iterate through both a list and an array, in this case an array of integers.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#35](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-arrays_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="4db75-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="4db75-109">See Also</span></span>

- <xref:System.Collections.Generic>  
- [<span data-ttu-id="4db75-110">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4db75-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="4db75-111">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="4db75-111">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
- [<span data-ttu-id="4db75-112">Pole</span><span class="sxs-lookup"><span data-stu-id="4db75-112">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
- [<span data-ttu-id="4db75-113">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="4db75-113">Generics</span></span>](~/docs/standard/generics/index.md)
