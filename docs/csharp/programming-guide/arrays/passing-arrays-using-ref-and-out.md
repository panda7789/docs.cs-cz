---
title: Předávání polí pomocí parametrů ref a out (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], passing using ref and out
ms.assetid: 6a2b261e-a1cc-49a6-b4f0-6cacae385a1e
ms.openlocfilehash: 8da3bf9f8eede72a7bc3cf8380eab66ca2b56e86
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526762"
---
# <a name="passing-arrays-using-ref-and-out-c-programming-guide"></a><span data-ttu-id="9f110-102">Předávání polí pomocí parametrů ref a out (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="9f110-102">Passing Arrays Using ref and out (C# Programming Guide)</span></span>

<span data-ttu-id="9f110-103">Stejně jako všechny [si](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametry, `out` před se používá, musí být přiřazeno parametr typu pole; to znamená, musíte být přiřazeni volaným.</span><span class="sxs-lookup"><span data-stu-id="9f110-103">Like all [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters, an `out` parameter of an array type must be assigned before it is used; that is, it must be assigned by the callee.</span></span> <span data-ttu-id="9f110-104">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9f110-104">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_1.cs)]  
  
 <span data-ttu-id="9f110-105">Stejně jako všechny [ref](../../../csharp/language-reference/keywords/ref.md) parametry, `ref` parametr typu pole musí být přiřazen volajícím.</span><span class="sxs-lookup"><span data-stu-id="9f110-105">Like all [ref](../../../csharp/language-reference/keywords/ref.md) parameters, a `ref` parameter of an array type must be definitely assigned by the caller.</span></span> <span data-ttu-id="9f110-106">Z tohoto důvodu není nutné je jednoznačně přiřazovat volaným.</span><span class="sxs-lookup"><span data-stu-id="9f110-106">Therefore, there is no need to be definitely assigned by the callee.</span></span> <span data-ttu-id="9f110-107">A `ref` parametr typu pole může být změněn v důsledku volání.</span><span class="sxs-lookup"><span data-stu-id="9f110-107">A `ref` parameter of an array type may be altered as a result of the call.</span></span> <span data-ttu-id="9f110-108">Například je možné přiřadit pole [null](../../../csharp/language-reference/keywords/null.md) hodnotu, nebo může být inicializována jinému poli.</span><span class="sxs-lookup"><span data-stu-id="9f110-108">For example, the array can be assigned the [null](../../../csharp/language-reference/keywords/null.md) value or can be initialized to a different array.</span></span> <span data-ttu-id="9f110-109">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9f110-109">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_2.cs)]  
  
 <span data-ttu-id="9f110-110">Následující dva příklady znázorňují rozdíl mezi `out` a `ref` při použití předání polí metodám.</span><span class="sxs-lookup"><span data-stu-id="9f110-110">The following two examples demonstrate the difference between `out` and `ref` when used in passing arrays to methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f110-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f110-111">Example</span></span>

 <span data-ttu-id="9f110-112">V tomto příkladu je pole `theArray` je deklarováno pro volajícího ( `Main` metoda) a inicializováno v `FillArray` metody.</span><span class="sxs-lookup"><span data-stu-id="9f110-112">In this example, the array `theArray` is declared in the caller (the `Main` method), and initialized in the `FillArray` method.</span></span> <span data-ttu-id="9f110-113">Prvky pole jsou poté vráceny volajícímu a zobrazeny.</span><span class="sxs-lookup"><span data-stu-id="9f110-113">Then, the array elements are returned to the caller and displayed.</span></span>  
  
 [!code-csharp[csProgGuideArrays#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_3.cs)]

## <a name="example"></a><span data-ttu-id="9f110-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f110-114">Example</span></span>

 <span data-ttu-id="9f110-115">V tomto příkladu je pole `theArray` je inicializováno pro volajícího ( `Main` metoda) a předat `FillArray` metoda pomocí `ref` parametr.</span><span class="sxs-lookup"><span data-stu-id="9f110-115">In this example, the array `theArray` is initialized in the caller (the `Main` method), and passed to the `FillArray` method by using the `ref` parameter.</span></span> <span data-ttu-id="9f110-116">Některé prvky pole jsou aktualizovány v `FillArray` metody.</span><span class="sxs-lookup"><span data-stu-id="9f110-116">Some of the array elements are updated in the `FillArray` method.</span></span> <span data-ttu-id="9f110-117">Prvky pole jsou poté vráceny volajícímu a zobrazeny.</span><span class="sxs-lookup"><span data-stu-id="9f110-117">Then, the array elements are returned to the caller and displayed.</span></span>  
  
 [!code-csharp[csProgGuideArrays#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_4.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="9f110-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f110-118">See Also</span></span>

- [<span data-ttu-id="9f110-119">ref</span><span class="sxs-lookup"><span data-stu-id="9f110-119">ref</span></span>](../../../csharp/language-reference/keywords/ref.md)  
- [<span data-ttu-id="9f110-120">out – modifikátor parametrů</span><span class="sxs-lookup"><span data-stu-id="9f110-120">out parameter modifier</span></span>](../../../csharp/language-reference/keywords/out-parameter-modifier.md)  
- [<span data-ttu-id="9f110-121">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="9f110-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="9f110-122">Pole</span><span class="sxs-lookup"><span data-stu-id="9f110-122">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
- [<span data-ttu-id="9f110-123">Jednorozměrná pole</span><span class="sxs-lookup"><span data-stu-id="9f110-123">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
- [<span data-ttu-id="9f110-124">Vícerozměrná pole</span><span class="sxs-lookup"><span data-stu-id="9f110-124">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
- [<span data-ttu-id="9f110-125">Vícenásobná pole</span><span class="sxs-lookup"><span data-stu-id="9f110-125">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
