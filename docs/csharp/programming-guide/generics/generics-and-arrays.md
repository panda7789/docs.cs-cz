---
title: "Obecné typy a pole (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 94b144075fac44ff749474a5bfa8e81aaadc0a0c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="generics-and-arrays-c-programming-guide"></a><span data-ttu-id="27dba-102">Obecné typy a pole (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="27dba-102">Generics and Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="27dba-103">V C# 2.0 nebo novější, jednorozměrná pole, které mají dolní mez 0 automaticky implementovat <xref:System.Collections.Generic.IList%601>.</span><span class="sxs-lookup"><span data-stu-id="27dba-103">In C# 2.0 and later, single-dimensional arrays that have a lower bound of zero automatically implement <xref:System.Collections.Generic.IList%601>.</span></span> <span data-ttu-id="27dba-104">To umožňuje vytvářet obecné metody, které můžete použít stejný kód k iteraci v rámci pole a dalších typů kolekce.</span><span class="sxs-lookup"><span data-stu-id="27dba-104">This enables you to create generic methods that can use the same code to iterate through arrays and other collection types.</span></span> <span data-ttu-id="27dba-105">Tento postup je užitečné hlavně pro čtení dat v kolekcích.</span><span class="sxs-lookup"><span data-stu-id="27dba-105">This technique is primarily useful for reading data in collections.</span></span> <span data-ttu-id="27dba-106"><xref:System.Collections.Generic.IList%601> Rozhraní nelze použít k přidání nebo odebrání elementy z pole.</span><span class="sxs-lookup"><span data-stu-id="27dba-106">The <xref:System.Collections.Generic.IList%601> interface cannot be used to add or remove elements from an array.</span></span> <span data-ttu-id="27dba-107">Bude vyvolána výjimka, pokud se pokusíte volání <xref:System.Collections.Generic.IList%601> metoda jako <xref:System.Collections.Generic.IList%601.RemoveAt%2A> na pole v tomto kontextu.</span><span class="sxs-lookup"><span data-stu-id="27dba-107">An exception will be thrown if you try to call an <xref:System.Collections.Generic.IList%601> method such as <xref:System.Collections.Generic.IList%601.RemoveAt%2A> on an array in this context.</span></span>  
  
 <span data-ttu-id="27dba-108">Následující příklad kódu ukazuje, jak jeden obecná metoda, která přebírá <xref:System.Collections.Generic.IList%601> vstupní parametr můžete iteraci v rámci seznamu a pole, v tomto případě pole celých čísel.</span><span class="sxs-lookup"><span data-stu-id="27dba-108">The following code example demonstrates how a single generic method that takes an <xref:System.Collections.Generic.IList%601> input parameter can iterate through both a list and an array, in this case an array of integers.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#35](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-arrays_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="27dba-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="27dba-109">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="27dba-110">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="27dba-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="27dba-111">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="27dba-111">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
 [<span data-ttu-id="27dba-112">Pole</span><span class="sxs-lookup"><span data-stu-id="27dba-112">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="27dba-113">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="27dba-113">Generics</span></span>](~/docs/standard/generics/index.md)
