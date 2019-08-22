---
title: Obecné typy a pole – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: fee66cf7bd0ab3c051ea67acc323efa02a21a017
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659795"
---
# <a name="generics-and-arrays-c-programming-guide"></a><span data-ttu-id="9e0bb-102">Obecné typy a pole (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="9e0bb-102">Generics and Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="9e0bb-103">V C# 2,0 a novějších, jednorozměrná pole, která mají dolní mez s hodnotou nula automaticky implementována <xref:System.Collections.Generic.IList%601>.</span><span class="sxs-lookup"><span data-stu-id="9e0bb-103">In C# 2.0 and later, single-dimensional arrays that have a lower bound of zero automatically implement <xref:System.Collections.Generic.IList%601>.</span></span> <span data-ttu-id="9e0bb-104">To umožňuje vytvořit obecné metody, které mohou použít stejný kód k iterování prostřednictvím polí a dalších typů kolekcí.</span><span class="sxs-lookup"><span data-stu-id="9e0bb-104">This enables you to create generic methods that can use the same code to iterate through arrays and other collection types.</span></span> <span data-ttu-id="9e0bb-105">Tato technika je primárně užitečná pro čtení dat v kolekcích.</span><span class="sxs-lookup"><span data-stu-id="9e0bb-105">This technique is primarily useful for reading data in collections.</span></span> <span data-ttu-id="9e0bb-106"><xref:System.Collections.Generic.IList%601> Rozhraní nelze použít k přidání nebo odebrání prvků z pole.</span><span class="sxs-lookup"><span data-stu-id="9e0bb-106">The <xref:System.Collections.Generic.IList%601> interface cannot be used to add or remove elements from an array.</span></span> <span data-ttu-id="9e0bb-107">Pokud se pokusíte zavolat <xref:System.Collections.Generic.IList%601> metodu, jako <xref:System.Collections.Generic.IList%601.RemoveAt%2A> je například na pole v tomto kontextu, bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="9e0bb-107">An exception will be thrown if you try to call an <xref:System.Collections.Generic.IList%601> method such as <xref:System.Collections.Generic.IList%601.RemoveAt%2A> on an array in this context.</span></span>  
  
 <span data-ttu-id="9e0bb-108">Následující příklad kódu ukazuje, jak jedna obecná metoda, která přijímá <xref:System.Collections.Generic.IList%601> vstupní parametr, může iterovat v seznamu i v poli, v tomto případě pole celých čísel.</span><span class="sxs-lookup"><span data-stu-id="9e0bb-108">The following code example demonstrates how a single generic method that takes an <xref:System.Collections.Generic.IList%601> input parameter can iterate through both a list and an array, in this case an array of integers.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a><span data-ttu-id="9e0bb-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9e0bb-109">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="9e0bb-110">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="9e0bb-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9e0bb-111">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="9e0bb-111">Generics</span></span>](./index.md)
- [<span data-ttu-id="9e0bb-112">Pole</span><span class="sxs-lookup"><span data-stu-id="9e0bb-112">Arrays</span></span>](../arrays/index.md)
- [<span data-ttu-id="9e0bb-113">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="9e0bb-113">Generics</span></span>](../../../standard/generics/index.md)
