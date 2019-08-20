---
title: Delegáti s pojmenovanými vs. Anonymní metody – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
ms.openlocfilehash: 9df143fb183ef2fc7e951b2cee47d18ce4b11942
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590645"
---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a><span data-ttu-id="95306-102">Delegáti s pojmenovanými vs. Anonymní metody (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="95306-102">Delegates with Named vs. Anonymous Methods (C# Programming Guide)</span></span>
<span data-ttu-id="95306-103">[Delegát](../../language-reference/keywords/delegate.md) může být spojen s pojmenovanou metodou.</span><span class="sxs-lookup"><span data-stu-id="95306-103">A [delegate](../../language-reference/keywords/delegate.md) can be associated with a named method.</span></span> <span data-ttu-id="95306-104">Při vytváření instance delegáta pomocí pojmenované metody je metoda předána jako parametr, například:</span><span class="sxs-lookup"><span data-stu-id="95306-104">When you instantiate a delegate by using a named method, the method is passed as a parameter, for example:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#1)]  
  
 <span data-ttu-id="95306-105">Tato metoda je volána pomocí pojmenované metody.</span><span class="sxs-lookup"><span data-stu-id="95306-105">This is called using a named method.</span></span> <span data-ttu-id="95306-106">Delegáty vytvořené pomocí pojmenované metody mohou zapouzdřit buď [statickou](../../language-reference/keywords/static.md) metodu, nebo metodu instance.</span><span class="sxs-lookup"><span data-stu-id="95306-106">Delegates constructed with a named method can encapsulate either a [static](../../language-reference/keywords/static.md) method or an instance method.</span></span> <span data-ttu-id="95306-107">Pojmenované metody jsou jediným způsobem, jak vytvořit instanci delegáta v dřívějších verzích nástroje C#.</span><span class="sxs-lookup"><span data-stu-id="95306-107">Named methods are the only way to instantiate a delegate in earlier versions of C#.</span></span> <span data-ttu-id="95306-108">Nicméně v situaci, kdy je vytvoření nové metody nežádoucí režijní náklady, C# umožňuje vytvořit instanci delegáta a ihned zadat blok kódu, který bude delegát zpracovávat při volání.</span><span class="sxs-lookup"><span data-stu-id="95306-108">However, in a situation where creating a new method is unwanted overhead, C# enables you to instantiate a delegate and immediately specify a code block that the delegate will process when it is called.</span></span> <span data-ttu-id="95306-109">Blok může obsahovat buď výraz lambda, nebo anonymní metodu.</span><span class="sxs-lookup"><span data-stu-id="95306-109">The block can contain either a lambda expression or an anonymous method.</span></span> <span data-ttu-id="95306-110">Další informace najdete v tématu [anonymní funkce](../statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="95306-110">For more information, see [Anonymous Functions](../statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95306-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="95306-111">Remarks</span></span>  
 <span data-ttu-id="95306-112">Metoda, kterou předáte jako parametr delegáta, musí mít stejnou signaturu jako deklarace delegáta.</span><span class="sxs-lookup"><span data-stu-id="95306-112">The method that you pass as a delegate parameter must have the same signature as the delegate declaration.</span></span>  
  
 <span data-ttu-id="95306-113">Instance delegáta může zapouzdřit buď statickou, nebo metodu instance.</span><span class="sxs-lookup"><span data-stu-id="95306-113">A delegate instance may encapsulate either static or instance method.</span></span>  
  
 <span data-ttu-id="95306-114">I když delegát může použít [výstupní](../../language-reference/keywords/out-parameter-modifier.md) parametr, nedoporučujeme ho používat s delegáty událostí vícesměrového vysílání, protože nemůžete zjistit, který delegát se bude volat.</span><span class="sxs-lookup"><span data-stu-id="95306-114">Although the delegate can use an [out](../../language-reference/keywords/out-parameter-modifier.md) parameter, we do not recommend its use with multicast event delegates because you cannot know which delegate will be called.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="95306-115">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="95306-115">Example 1</span></span>  
 <span data-ttu-id="95306-116">Následuje jednoduchý příklad deklarace a použití delegáta.</span><span class="sxs-lookup"><span data-stu-id="95306-116">The following is a simple example of declaring and using a delegate.</span></span> <span data-ttu-id="95306-117">Všimněte si, že delegát, `Del`i přidružená `MultiplyNumbers`metoda mají stejnou signaturu.</span><span class="sxs-lookup"><span data-stu-id="95306-117">Notice that both the delegate, `Del`, and the associated method, `MultiplyNumbers`, have the same signature</span></span>  
  
 [!code-csharp[csProgGuideDelegates#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#2)]  
  
## <a name="example-2"></a><span data-ttu-id="95306-118">Příklad 2</span><span class="sxs-lookup"><span data-stu-id="95306-118">Example 2</span></span>  
 <span data-ttu-id="95306-119">V následujícím příkladu je jeden delegát mapován na statické a instanční metody a vrátí konkrétní informace z každého z nich.</span><span class="sxs-lookup"><span data-stu-id="95306-119">In the following example, one delegate is mapped to both static and instance methods and returns specific information from each.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#3)]  
  
## <a name="see-also"></a><span data-ttu-id="95306-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="95306-120">See also</span></span>

- [<span data-ttu-id="95306-121">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="95306-121">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="95306-122">Delegáti</span><span class="sxs-lookup"><span data-stu-id="95306-122">Delegates</span></span>](./index.md)
- [<span data-ttu-id="95306-123">Postupy: Kombinovat delegáty (Delegáti vícesměrového vysílání)</span><span class="sxs-lookup"><span data-stu-id="95306-123">How to: Combine Delegates (Multicast Delegates)</span></span>](./how-to-combine-delegates-multicast-delegates.md)
- [<span data-ttu-id="95306-124">Události</span><span class="sxs-lookup"><span data-stu-id="95306-124">Events</span></span>](../events/index.md)
