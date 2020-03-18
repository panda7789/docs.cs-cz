---
title: Obecné typy a pole – programovací příručka jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: a8fad38fac07b9e8d51529d3ab7070328a333dbb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75703010"
---
# <a name="generics-and-arrays-c-programming-guide"></a><span data-ttu-id="aae72-102">Obecné typy a pole (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="aae72-102">Generics and Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="aae72-103">V C# 2.0 a novější jednorozměrné pole, které mají <xref:System.Collections.Generic.IList%601>dolní mez nula automaticky implementovat .</span><span class="sxs-lookup"><span data-stu-id="aae72-103">In C# 2.0 and later, single-dimensional arrays that have a lower bound of zero automatically implement <xref:System.Collections.Generic.IList%601>.</span></span> <span data-ttu-id="aae72-104">To umožňuje vytvořit obecné metody, které můžete použít stejný kód k iterování prostřednictvím polí a jiných typů kolekcí.</span><span class="sxs-lookup"><span data-stu-id="aae72-104">This enables you to create generic methods that can use the same code to iterate through arrays and other collection types.</span></span> <span data-ttu-id="aae72-105">Tato technika je užitečná především pro čtení dat v kolekcích.</span><span class="sxs-lookup"><span data-stu-id="aae72-105">This technique is primarily useful for reading data in collections.</span></span> <span data-ttu-id="aae72-106">Rozhraní <xref:System.Collections.Generic.IList%601> nelze použít k přidání nebo odebrání prvků z pole.</span><span class="sxs-lookup"><span data-stu-id="aae72-106">The <xref:System.Collections.Generic.IList%601> interface cannot be used to add or remove elements from an array.</span></span> <span data-ttu-id="aae72-107">Výjimka bude vyvolána, pokud se <xref:System.Collections.Generic.IList%601> pokusíte <xref:System.Collections.Generic.IList%601.RemoveAt%2A> volat metodu, například na pole v tomto kontextu.</span><span class="sxs-lookup"><span data-stu-id="aae72-107">An exception will be thrown if you try to call an <xref:System.Collections.Generic.IList%601> method such as <xref:System.Collections.Generic.IList%601.RemoveAt%2A> on an array in this context.</span></span>  
  
 <span data-ttu-id="aae72-108">Následující příklad kódu ukazuje, jak může jedna <xref:System.Collections.Generic.IList%601> obecná metoda, která přebírá vstupní parametr, iterovat seznamem i polem, v tomto případě polem celých čísel.</span><span class="sxs-lookup"><span data-stu-id="aae72-108">The following code example demonstrates how a single generic method that takes an <xref:System.Collections.Generic.IList%601> input parameter can iterate through both a list and an array, in this case an array of integers.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a><span data-ttu-id="aae72-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="aae72-109">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="aae72-110">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="aae72-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="aae72-111">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="aae72-111">Generics</span></span>](./index.md)
- [<span data-ttu-id="aae72-112">Pole</span><span class="sxs-lookup"><span data-stu-id="aae72-112">Arrays</span></span>](../arrays/index.md)
- [<span data-ttu-id="aae72-113">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="aae72-113">Generics</span></span>](../../../standard/generics/index.md)
