---
title: Obecné typy a pole – Průvodce programováním v C#
description: Seznamte se s obecnými typy a poli v programování v jazyce C#. Podívejte se na příklady kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: f3d9e9e0c84d954278780e7598545f80aea0e58c
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299042"
---
# <a name="generics-and-arrays-c-programming-guide"></a><span data-ttu-id="30f22-104">Obecné typy a pole (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="30f22-104">Generics and Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="30f22-105">V C# 2,0 a novějších, jednorozměrná pole, která mají dolní mez nulového automatického implementace <xref:System.Collections.Generic.IList%601> .</span><span class="sxs-lookup"><span data-stu-id="30f22-105">In C# 2.0 and later, single-dimensional arrays that have a lower bound of zero automatically implement <xref:System.Collections.Generic.IList%601>.</span></span> <span data-ttu-id="30f22-106">To umožňuje vytvořit obecné metody, které mohou použít stejný kód k iterování prostřednictvím polí a dalších typů kolekcí.</span><span class="sxs-lookup"><span data-stu-id="30f22-106">This enables you to create generic methods that can use the same code to iterate through arrays and other collection types.</span></span> <span data-ttu-id="30f22-107">Tato technika je primárně užitečná pro čtení dat v kolekcích.</span><span class="sxs-lookup"><span data-stu-id="30f22-107">This technique is primarily useful for reading data in collections.</span></span> <span data-ttu-id="30f22-108"><xref:System.Collections.Generic.IList%601>Rozhraní nelze použít k přidání nebo odebrání prvků z pole.</span><span class="sxs-lookup"><span data-stu-id="30f22-108">The <xref:System.Collections.Generic.IList%601> interface cannot be used to add or remove elements from an array.</span></span> <span data-ttu-id="30f22-109">Pokud se pokusíte zavolat <xref:System.Collections.Generic.IList%601> metodu, jako je například <xref:System.Collections.Generic.IList%601.RemoveAt%2A> na pole v tomto kontextu, bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="30f22-109">An exception will be thrown if you try to call an <xref:System.Collections.Generic.IList%601> method such as <xref:System.Collections.Generic.IList%601.RemoveAt%2A> on an array in this context.</span></span>  
  
 <span data-ttu-id="30f22-110">Následující příklad kódu ukazuje, jak jedna obecná metoda, která přijímá <xref:System.Collections.Generic.IList%601> vstupní parametr, může iterovat v seznamu i v poli, v tomto případě pole celých čísel.</span><span class="sxs-lookup"><span data-stu-id="30f22-110">The following code example demonstrates how a single generic method that takes an <xref:System.Collections.Generic.IList%601> input parameter can iterate through both a list and an array, in this case an array of integers.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a><span data-ttu-id="30f22-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30f22-111">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="30f22-112">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="30f22-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="30f22-113">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="30f22-113">Generics</span></span>](./index.md)
- [<span data-ttu-id="30f22-114">Pole</span><span class="sxs-lookup"><span data-stu-id="30f22-114">Arrays</span></span>](../arrays/index.md)
- [<span data-ttu-id="30f22-115">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="30f22-115">Generics</span></span>](../../../standard/generics/index.md)
