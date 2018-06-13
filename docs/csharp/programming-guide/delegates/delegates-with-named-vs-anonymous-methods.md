---
title: Delegáti s pojmenované vs. Anonymní metody (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
ms.openlocfilehash: 93e140859e44aab860577feede40df6eab4c8e00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33330762"
---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a><span data-ttu-id="e71b3-102">Delegáti s pojmenované vs. Anonymní metody (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="e71b3-102">Delegates with Named vs. Anonymous Methods (C# Programming Guide)</span></span>
<span data-ttu-id="e71b3-103">A [delegovat](../../../csharp/language-reference/keywords/delegate.md) může být přidružen metodu s názvem.</span><span class="sxs-lookup"><span data-stu-id="e71b3-103">A [delegate](../../../csharp/language-reference/keywords/delegate.md) can be associated with a named method.</span></span> <span data-ttu-id="e71b3-104">Pokud instanci delegáta můžete vytvořit pomocí metodu s názvem, metodu předávána jako parametr, například:</span><span class="sxs-lookup"><span data-stu-id="e71b3-104">When you instantiate a delegate by using a named method, the method is passed as a parameter, for example:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#1](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_1.cs)]  
  
 <span data-ttu-id="e71b3-105">Tomu se říká pomocí metodu s názvem.</span><span class="sxs-lookup"><span data-stu-id="e71b3-105">This is called using a named method.</span></span> <span data-ttu-id="e71b3-106">Delegáti zkonstruovat s metodu s názvem může zapouzdřit buď [statické](../../../csharp/language-reference/keywords/static.md) metodu nebo metody instance.</span><span class="sxs-lookup"><span data-stu-id="e71b3-106">Delegates constructed with a named method can encapsulate either a [static](../../../csharp/language-reference/keywords/static.md) method or an instance method.</span></span> <span data-ttu-id="e71b3-107">Pojmenované metody jsou jediný způsob, jak vytvořit instanci delegáta v dřívějších verzích systému C#.</span><span class="sxs-lookup"><span data-stu-id="e71b3-107">Named methods are the only way to instantiate a delegate in earlier versions of C#.</span></span> <span data-ttu-id="e71b3-108">Ale v situaci, kdy vytvoření nové metody nežádoucí režie, C# umožňuje vytvořit instanci delegáta a okamžitě zadejte blok kódu, která zpracuje delegáta, když je volána.</span><span class="sxs-lookup"><span data-stu-id="e71b3-108">However, in a situation where creating a new method is unwanted overhead, C# enables you to instantiate a delegate and immediately specify a code block that the delegate will process when it is called.</span></span> <span data-ttu-id="e71b3-109">Blok může obsahovat výraz lambda nebo anonymní metody.</span><span class="sxs-lookup"><span data-stu-id="e71b3-109">The block can contain either a lambda expression or an anonymous method.</span></span> <span data-ttu-id="e71b3-110">Další informace najdete v tématu [anonymní funkce](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="e71b3-110">For more information, see [Anonymous Functions](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e71b3-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e71b3-111">Remarks</span></span>  
 <span data-ttu-id="e71b3-112">Metoda, kterou předáte jako parametr delegáta musí mít stejný podpis jako deklaraci delegáta.</span><span class="sxs-lookup"><span data-stu-id="e71b3-112">The method that you pass as a delegate parameter must have the same signature as the delegate declaration.</span></span>  
  
 <span data-ttu-id="e71b3-113">Instanci delegáta může zapouzdřit buď statickou nebo metodu instance.</span><span class="sxs-lookup"><span data-stu-id="e71b3-113">A delegate instance may encapsulate either static or instance method.</span></span>  
  
 <span data-ttu-id="e71b3-114">I když delegát můžete použít [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametr, nedoporučujeme jeho použití s delegáty vícesměrového vysílání událostí protože nelze zjistit, které delegáta bude volána.</span><span class="sxs-lookup"><span data-stu-id="e71b3-114">Although the delegate can use an [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter, we do not recommend its use with multicast event delegates because you cannot know which delegate will be called.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="e71b3-115">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="e71b3-115">Example 1</span></span>  
 <span data-ttu-id="e71b3-116">Toto je jednoduchý příklad deklarování a použití delegáta.</span><span class="sxs-lookup"><span data-stu-id="e71b3-116">The following is a simple example of declaring and using a delegate.</span></span> <span data-ttu-id="e71b3-117">Všimněte si, že oba delegáta, `Del`a metodu přidružené `MultiplyNumbers`, mají stejným podpisem</span><span class="sxs-lookup"><span data-stu-id="e71b3-117">Notice that both the delegate, `Del`, and the associated method, `MultiplyNumbers`, have the same signature</span></span>  
  
 [!code-csharp[csProgGuideDelegates#2](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_2.cs)]  
  
## <a name="example-2"></a><span data-ttu-id="e71b3-118">Příklad 2</span><span class="sxs-lookup"><span data-stu-id="e71b3-118">Example 2</span></span>  
 <span data-ttu-id="e71b3-119">V následujícím příkladu je namapovaný jeden delegáta statických a instanci metody a vrátí konkrétní informace z každého.</span><span class="sxs-lookup"><span data-stu-id="e71b3-119">In the following example, one delegate is mapped to both static and instance methods and returns specific information from each.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#3](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="e71b3-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="e71b3-120">See Also</span></span>  
 [<span data-ttu-id="e71b3-121">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e71b3-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e71b3-122">Delegáti</span><span class="sxs-lookup"><span data-stu-id="e71b3-122">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="e71b3-123">Anonymní metody</span><span class="sxs-lookup"><span data-stu-id="e71b3-123">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
 [<span data-ttu-id="e71b3-124">Postupy: kombinování delegátů (vícesměroví delegáti)</span><span class="sxs-lookup"><span data-stu-id="e71b3-124">How to: Combine Delegates (Multicast Delegates)</span></span>](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)  
 [<span data-ttu-id="e71b3-125">Události</span><span class="sxs-lookup"><span data-stu-id="e71b3-125">Events</span></span>](../../../csharp/programming-guide/events/index.md)
