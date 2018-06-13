---
title: Předávání polí pomocí parametrů ref a out (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], passing using ref and out
ms.assetid: 6a2b261e-a1cc-49a6-b4f0-6cacae385a1e
ms.openlocfilehash: a186399125e01bb2535f3a8b488c6fbd85932246
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33313567"
---
# <a name="passing-arrays-using-ref-and-out-c-programming-guide"></a><span data-ttu-id="7662a-102">Předávání polí pomocí parametrů ref a out (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="7662a-102">Passing Arrays Using ref and out (C# Programming Guide)</span></span>
<span data-ttu-id="7662a-103">Všechny jako [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametry, `out` parametr typu pole musí mít přiřazenou před jeho použitím; to znamená, musí být přiřazen volaného.</span><span class="sxs-lookup"><span data-stu-id="7662a-103">Like all [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters, an `out` parameter of an array type must be assigned before it is used; that is, it must be assigned by the callee.</span></span> <span data-ttu-id="7662a-104">Příklad:</span><span class="sxs-lookup"><span data-stu-id="7662a-104">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_1.cs)]  
  
 <span data-ttu-id="7662a-105">Všechny jako [ref](../../../csharp/language-reference/keywords/ref.md) parametrů, `ref` parametr pole typu musí být výborný přiřadila volající.</span><span class="sxs-lookup"><span data-stu-id="7662a-105">Like all [ref](../../../csharp/language-reference/keywords/ref.md) parameters, a `ref` parameter of an array type must be definitely assigned by the caller.</span></span> <span data-ttu-id="7662a-106">Z tohoto důvodu není nutné je jednoznačně přiřazovat volaným.</span><span class="sxs-lookup"><span data-stu-id="7662a-106">Therefore, there is no need to be definitely assigned by the callee.</span></span> <span data-ttu-id="7662a-107">A `ref` parametr pole typu mohou být změněny v důsledku volání.</span><span class="sxs-lookup"><span data-stu-id="7662a-107">A `ref` parameter of an array type may be altered as a result of the call.</span></span> <span data-ttu-id="7662a-108">Například můžete přiřadit pole [null](../../../csharp/language-reference/keywords/null.md) hodnotu nebo může být inicializována na jiné pole.</span><span class="sxs-lookup"><span data-stu-id="7662a-108">For example, the array can be assigned the [null](../../../csharp/language-reference/keywords/null.md) value or can be initialized to a different array.</span></span> <span data-ttu-id="7662a-109">Příklad:</span><span class="sxs-lookup"><span data-stu-id="7662a-109">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_2.cs)]  
  
 <span data-ttu-id="7662a-110">Následující dva příklady ukazují rozdíl mezi `out` a `ref` při použití v předávání do metod pole.</span><span class="sxs-lookup"><span data-stu-id="7662a-110">The following two examples demonstrate the difference between `out` and `ref` when used in passing arrays to methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7662a-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="7662a-111">Example</span></span>  
 <span data-ttu-id="7662a-112">V tomto příkladu pole `theArray` deklarovaného v volající ( `Main` metoda) a inicializované v `FillArray` metoda.</span><span class="sxs-lookup"><span data-stu-id="7662a-112">In this example, the array `theArray` is declared in the caller (the `Main` method), and initialized in the `FillArray` method.</span></span> <span data-ttu-id="7662a-113">Prvky pole jsou poté vráceny volajícímu a zobrazeny.</span><span class="sxs-lookup"><span data-stu-id="7662a-113">Then, the array elements are returned to the caller and displayed.</span></span>  
  
 [!code-csharp[csProgGuideArrays#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="7662a-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="7662a-114">Example</span></span>  
 <span data-ttu-id="7662a-115">V tomto příkladu pole `theArray` je inicializován v volající ( `Main` metoda) a předaný `FillArray` metoda pomocí `ref` parametr.</span><span class="sxs-lookup"><span data-stu-id="7662a-115">In this example, the array `theArray` is initialized in the caller (the `Main` method), and passed to the `FillArray` method by using the `ref` parameter.</span></span> <span data-ttu-id="7662a-116">Některé elementy pole jsou aktualizovány v `FillArray` metoda.</span><span class="sxs-lookup"><span data-stu-id="7662a-116">Some of the array elements are updated in the `FillArray` method.</span></span> <span data-ttu-id="7662a-117">Prvky pole jsou poté vráceny volajícímu a zobrazeny.</span><span class="sxs-lookup"><span data-stu-id="7662a-117">Then, the array elements are returned to the caller and displayed.</span></span>  
  
 [!code-csharp[csProgGuideArrays#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_4.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="7662a-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="7662a-118">See Also</span></span>  
 [<span data-ttu-id="7662a-119">ref</span><span class="sxs-lookup"><span data-stu-id="7662a-119">ref</span></span>](../../../csharp/language-reference/keywords/ref.md)  
 [<span data-ttu-id="7662a-120">out – modifikátor parametrů</span><span class="sxs-lookup"><span data-stu-id="7662a-120">out parameter modifier</span></span>](../../../csharp/language-reference/keywords/out-parameter-modifier.md)  
 [<span data-ttu-id="7662a-121">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="7662a-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7662a-122">Pole</span><span class="sxs-lookup"><span data-stu-id="7662a-122">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="7662a-123">Jednorozměrná pole</span><span class="sxs-lookup"><span data-stu-id="7662a-123">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="7662a-124">Vícerozměrná pole</span><span class="sxs-lookup"><span data-stu-id="7662a-124">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [<span data-ttu-id="7662a-125">Vícenásobná pole</span><span class="sxs-lookup"><span data-stu-id="7662a-125">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
