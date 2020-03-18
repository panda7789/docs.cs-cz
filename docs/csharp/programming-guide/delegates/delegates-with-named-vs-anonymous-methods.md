---
title: Delegáti s pojmenovanými vs. anonymními metodami – programovací příručka Jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
ms.openlocfilehash: 1ec366999ca6457471b705fa83f06fcde4293f4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712374"
---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a><span data-ttu-id="b884a-102">Delegáti s pojmenovanými vs. anonymními metodami (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="b884a-102">Delegates with Named vs. Anonymous Methods (C# Programming Guide)</span></span>
<span data-ttu-id="b884a-103">[Delegát](../../language-reference/builtin-types/reference-types.md) může být přidružen k pojmenované metodě.</span><span class="sxs-lookup"><span data-stu-id="b884a-103">A [delegate](../../language-reference/builtin-types/reference-types.md) can be associated with a named method.</span></span> <span data-ttu-id="b884a-104">Při vytváření instanci delegáta pomocí pojmenované metody je metoda předána jako parametr, například:</span><span class="sxs-lookup"><span data-stu-id="b884a-104">When you instantiate a delegate by using a named method, the method is passed as a parameter, for example:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#1)]  
  
 <span data-ttu-id="b884a-105">To se nazývá pomocí pojmenované metody.</span><span class="sxs-lookup"><span data-stu-id="b884a-105">This is called using a named method.</span></span> <span data-ttu-id="b884a-106">Delegáti vytvořená s pojmenovanou metodou mohou zapouzdřit [statickou](../../language-reference/keywords/static.md) metodu nebo metodu instance.</span><span class="sxs-lookup"><span data-stu-id="b884a-106">Delegates constructed with a named method can encapsulate either a [static](../../language-reference/keywords/static.md) method or an instance method.</span></span> <span data-ttu-id="b884a-107">Pojmenované metody jsou jediným způsobem, jak vytvořit konkretizovat delegáta v dřívějších verzích jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="b884a-107">Named methods are the only way to instantiate a delegate in earlier versions of C#.</span></span> <span data-ttu-id="b884a-108">Však v situaci, kdy vytváření nové metody je nežádoucí režie, C# umožňuje vytvořit instanci delegáta a okamžitě zadat blok kódu, který delegát zpracuje, když je volána.</span><span class="sxs-lookup"><span data-stu-id="b884a-108">However, in a situation where creating a new method is unwanted overhead, C# enables you to instantiate a delegate and immediately specify a code block that the delegate will process when it is called.</span></span> <span data-ttu-id="b884a-109">Blok může obsahovat výraz lambda nebo anonymní metodu.</span><span class="sxs-lookup"><span data-stu-id="b884a-109">The block can contain either a lambda expression or an anonymous method.</span></span> <span data-ttu-id="b884a-110">Další informace naleznete [v tématu Anonymní funkce](../statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="b884a-110">For more information, see [Anonymous Functions](../statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b884a-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b884a-111">Remarks</span></span>  
 <span data-ttu-id="b884a-112">Metoda, kterou předáte jako parametr delegáta, musí mít stejný podpis jako deklarace delegáta.</span><span class="sxs-lookup"><span data-stu-id="b884a-112">The method that you pass as a delegate parameter must have the same signature as the delegate declaration.</span></span>  
  
 <span data-ttu-id="b884a-113">Instance delegáta může zapouzdřit statickou metodu nebo metodu instance.</span><span class="sxs-lookup"><span data-stu-id="b884a-113">A delegate instance may encapsulate either static or instance method.</span></span>  
  
 <span data-ttu-id="b884a-114">Přestože delegát může použít [out](../../language-reference/keywords/out-parameter-modifier.md) parametr, nedoporučujeme jeho použití s delegáty událostí vícesměrového vysílání, protože nemůžete vědět, který delegát bude volán.</span><span class="sxs-lookup"><span data-stu-id="b884a-114">Although the delegate can use an [out](../../language-reference/keywords/out-parameter-modifier.md) parameter, we do not recommend its use with multicast event delegates because you cannot know which delegate will be called.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="b884a-115">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="b884a-115">Example 1</span></span>  
 <span data-ttu-id="b884a-116">Následuje jednoduchý příklad deklarování a používání delegáta.</span><span class="sxs-lookup"><span data-stu-id="b884a-116">The following is a simple example of declaring and using a delegate.</span></span> <span data-ttu-id="b884a-117">Všimněte si, `Del`že delegát , `MultiplyNumbers`a přidružená metoda , mají stejný podpis</span><span class="sxs-lookup"><span data-stu-id="b884a-117">Notice that both the delegate, `Del`, and the associated method, `MultiplyNumbers`, have the same signature</span></span>  
  
 [!code-csharp[csProgGuideDelegates#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#2)]  
  
## <a name="example-2"></a><span data-ttu-id="b884a-118">Příklad 2</span><span class="sxs-lookup"><span data-stu-id="b884a-118">Example 2</span></span>  
 <span data-ttu-id="b884a-119">V následujícím příkladu je jeden delegát mapován na statické metody a metody instance a vrací konkrétní informace z každého z nich.</span><span class="sxs-lookup"><span data-stu-id="b884a-119">In the following example, one delegate is mapped to both static and instance methods and returns specific information from each.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#3)]  
  
## <a name="see-also"></a><span data-ttu-id="b884a-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="b884a-120">See also</span></span>

- [<span data-ttu-id="b884a-121">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b884a-121">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b884a-122">Delegáty</span><span class="sxs-lookup"><span data-stu-id="b884a-122">Delegates</span></span>](./index.md)
- [<span data-ttu-id="b884a-123">Jak kombinovat delegáty (delegáti vícesměrového vysílání)</span><span class="sxs-lookup"><span data-stu-id="b884a-123">How to combine delegates (Multicast Delegates)</span></span>](./how-to-combine-delegates-multicast-delegates.md)
- [<span data-ttu-id="b884a-124">Akce</span><span class="sxs-lookup"><span data-stu-id="b884a-124">Events</span></span>](../events/index.md)
