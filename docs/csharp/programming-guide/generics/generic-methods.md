---
title: Obecné metody – Průvodce programováním v C#
description: Další informace o metodách deklarovaných pomocí parametrů typu, označovaných jako obecné metody. Podívejte se na příklady kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
ms.openlocfilehash: 77b81de26961a8b59644643bf043ed723dbf374f
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301876"
---
# <a name="generic-methods-c-programming-guide"></a><span data-ttu-id="0b7a1-104">Obecné metody (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="0b7a1-104">Generic Methods (C# Programming Guide)</span></span>
<span data-ttu-id="0b7a1-105">Obecná metoda je metoda, která je deklarována s parametry typu, následovně:</span><span class="sxs-lookup"><span data-stu-id="0b7a1-105">A generic method is a method that is declared with type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#22)]  
  
 <span data-ttu-id="0b7a1-106">Následující příklad kódu ukazuje jeden ze způsobů, jak volat metodu pomocí `int` argumentu typu:</span><span class="sxs-lookup"><span data-stu-id="0b7a1-106">The following code example shows one way to call the method by using `int` for the type argument:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#23)]  
  
 <span data-ttu-id="0b7a1-107">Můžete také vynechat argument typu a kompilátor ho odvodí.</span><span class="sxs-lookup"><span data-stu-id="0b7a1-107">You can also omit the type argument and the compiler will infer it.</span></span> <span data-ttu-id="0b7a1-108">Následující volání `Swap` je ekvivalentní předchozímu volání:</span><span class="sxs-lookup"><span data-stu-id="0b7a1-108">The following call to `Swap` is equivalent to the previous call:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#24)]  
  
 <span data-ttu-id="0b7a1-109">Stejná pravidla pro odvození typu se vztahují na statické metody a metody instance.</span><span class="sxs-lookup"><span data-stu-id="0b7a1-109">The same rules for type inference apply to static methods and instance methods.</span></span> <span data-ttu-id="0b7a1-110">Kompilátor může odvodit parametry typu na základě argumentů metody, které předáte; nemůže odvodit parametry typu jenom z omezení nebo návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0b7a1-110">The compiler can infer the type parameters based on the method arguments you pass in; it cannot infer the type parameters only from a constraint or return value.</span></span> <span data-ttu-id="0b7a1-111">Proto odvození typu nefunguje s metodami, které nemají žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="0b7a1-111">Therefore type inference does not work with methods that have no parameters.</span></span> <span data-ttu-id="0b7a1-112">K odvození typu dojde v době kompilace předtím, než se kompilátor pokusí přeložit signatury přetížené metody.</span><span class="sxs-lookup"><span data-stu-id="0b7a1-112">Type inference occurs at compile time before the compiler tries to resolve overloaded method signatures.</span></span> <span data-ttu-id="0b7a1-113">Kompilátor aplikuje logiku odvození typu na všechny obecné metody, které mají stejný název.</span><span class="sxs-lookup"><span data-stu-id="0b7a1-113">The compiler applies type inference logic to all generic methods that share the same name.</span></span> <span data-ttu-id="0b7a1-114">V kroku řešení přetížení obsahuje kompilátor pouze ty obecné metody, na které bylo odvození typu úspěšné.</span><span class="sxs-lookup"><span data-stu-id="0b7a1-114">In the overload resolution step, the compiler includes only those generic methods on which type inference succeeded.</span></span>  
  
 <span data-ttu-id="0b7a1-115">V rámci obecné třídy mohou neobecné metody získat přístup k parametrům typu na úrovni třídy, a to následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="0b7a1-115">Within a generic class, non-generic methods can access the class-level type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#25)]  
  
 <span data-ttu-id="0b7a1-116">Definujete-li obecnou metodu, která přebírá stejné parametry typu jako obsahující třídu, kompilátor vygeneruje upozornění [CS0693](../../misc/cs0693.md) , protože v rámci oboru metody vygeneruje argument pro vnitřní hodnotu argumentu, který je zadán pro `T` vnější `T` .</span><span class="sxs-lookup"><span data-stu-id="0b7a1-116">If you define a generic method that takes the same type parameters as the containing class, the compiler generates warning [CS0693](../../misc/cs0693.md) because within the method scope, the argument supplied for the inner `T` hides the argument supplied for the outer `T`.</span></span> <span data-ttu-id="0b7a1-117">Pokud požadujete flexibilitu při volání obecné metody třídy s argumenty typu jiné než ty, které jsou zadány při vytváření instance třídy, zvažte zadání jiného identifikátoru pro parametr typu metody, jak je znázorněno v `GenericList2<T>` následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0b7a1-117">If you require the flexibility of calling a generic class method with type arguments other than the ones provided when the class was instantiated, consider providing another identifier for the type parameter of the method, as shown in `GenericList2<T>` in the following example.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#26)]  
  
 <span data-ttu-id="0b7a1-118">Použijte omezení pro povolení více specializovaných operací u parametrů typu v metodách.</span><span class="sxs-lookup"><span data-stu-id="0b7a1-118">Use constraints to enable more specialized operations on type parameters in methods.</span></span> <span data-ttu-id="0b7a1-119">Tato verze `Swap<T>` , která je nyní pojmenována `SwapIfGreater<T>` , může být použita pouze s argumenty typu, které implementují <xref:System.IComparable%601> .</span><span class="sxs-lookup"><span data-stu-id="0b7a1-119">This version of `Swap<T>`, now named `SwapIfGreater<T>`, can only be used with type arguments that implement <xref:System.IComparable%601>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#27)]  
  
 <span data-ttu-id="0b7a1-120">Obecné metody mohou být přetíženy u několika parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="0b7a1-120">Generic methods can be overloaded on several type parameters.</span></span> <span data-ttu-id="0b7a1-121">Například následující metody mohou být umístěny ve stejné třídě:</span><span class="sxs-lookup"><span data-stu-id="0b7a1-121">For example, the following methods can all be located in the same class:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#28)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="0b7a1-122">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0b7a1-122">C# Language Specification</span></span>  
 <span data-ttu-id="0b7a1-123">Další informace najdete v tématu [Specifikace jazyka C#](~/_csharplang/spec/classes.md#methods).</span><span class="sxs-lookup"><span data-stu-id="0b7a1-123">For more information, see the [C# Language Specification](~/_csharplang/spec/classes.md#methods).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b7a1-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0b7a1-124">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="0b7a1-125">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="0b7a1-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0b7a1-126">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="0b7a1-126">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="0b7a1-127">Metody</span><span class="sxs-lookup"><span data-stu-id="0b7a1-127">Methods</span></span>](../classes-and-structs/methods.md)
