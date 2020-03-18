---
title: Obecné metody – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
ms.openlocfilehash: 5f066ca39c97b70554886e423c37c4ee47d49158
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712192"
---
# <a name="generic-methods-c-programming-guide"></a><span data-ttu-id="deedb-102">Obecné metody (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="deedb-102">Generic Methods (C# Programming Guide)</span></span>
<span data-ttu-id="deedb-103">Obecná metoda je metoda, která je deklarována s parametry typu, a to následovně:</span><span class="sxs-lookup"><span data-stu-id="deedb-103">A generic method is a method that is declared with type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#22)]  
  
 <span data-ttu-id="deedb-104">Následující příklad kódu ukazuje jeden způsob volání `int` metody pomocí argumentu typu:</span><span class="sxs-lookup"><span data-stu-id="deedb-104">The following code example shows one way to call the method by using `int` for the type argument:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#23)]  
  
 <span data-ttu-id="deedb-105">Můžete také vynechat argument typu a kompilátor jej odvodí.</span><span class="sxs-lookup"><span data-stu-id="deedb-105">You can also omit the type argument and the compiler will infer it.</span></span> <span data-ttu-id="deedb-106">Následující volání `Swap` je ekvivalentní předchozímu volání:</span><span class="sxs-lookup"><span data-stu-id="deedb-106">The following call to `Swap` is equivalent to the previous call:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#24)]  
  
 <span data-ttu-id="deedb-107">Stejná pravidla pro odvození typu platí pro statické metody a metody instancí.</span><span class="sxs-lookup"><span data-stu-id="deedb-107">The same rules for type inference apply to static methods and instance methods.</span></span> <span data-ttu-id="deedb-108">Kompilátor může odvodit parametry typu na základě argumentů metody, které předáte; nelze odvodit parametry typu pouze z omezení nebo vrácené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="deedb-108">The compiler can infer the type parameters based on the method arguments you pass in; it cannot infer the type parameters only from a constraint or return value.</span></span> <span data-ttu-id="deedb-109">Proto odvození typu nefunguje s metodami, které nemají žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="deedb-109">Therefore type inference does not work with methods that have no parameters.</span></span> <span data-ttu-id="deedb-110">Odvození typu dochází v době kompilace před kompilátor pokusí vyřešit přetížené podpisy metody.</span><span class="sxs-lookup"><span data-stu-id="deedb-110">Type inference occurs at compile time before the compiler tries to resolve overloaded method signatures.</span></span> <span data-ttu-id="deedb-111">Kompilátor použije logiku odvození typu na všechny obecné metody, které sdílejí stejný název.</span><span class="sxs-lookup"><span data-stu-id="deedb-111">The compiler applies type inference logic to all generic methods that share the same name.</span></span> <span data-ttu-id="deedb-112">V kroku řešení přetížení kompilátor zahrnuje pouze ty obecné metody, na kterých byl úspěšný odvození typu.</span><span class="sxs-lookup"><span data-stu-id="deedb-112">In the overload resolution step, the compiler includes only those generic methods on which type inference succeeded.</span></span>  
  
 <span data-ttu-id="deedb-113">V rámci obecné třídy mohou neobecné metody přistupovat k parametrům typu na úrovni třídy následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="deedb-113">Within a generic class, non-generic methods can access the class-level type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#25)]  
  
 <span data-ttu-id="deedb-114">Pokud definujete obecnou metodu, která přebírá stejné parametry typu jako obsahující třída, kompilátor generuje upozornění [CS0693,](../../misc/cs0693.md) protože v rámci oboru metody argument zadaný pro vnitřní `T` skryje argument zadaný pro vnější `T`.</span><span class="sxs-lookup"><span data-stu-id="deedb-114">If you define a generic method that takes the same type parameters as the containing class, the compiler generates warning [CS0693](../../misc/cs0693.md) because within the method scope, the argument supplied for the inner `T` hides the argument supplied for the outer `T`.</span></span> <span data-ttu-id="deedb-115">Pokud požadujete flexibilitu volání metody obecné třídy s argumenty typu jiné než ty, které byly poskytnuty při vytvoření instance třídy, `GenericList2<T>` zvažte poskytnutí jiného identifikátoru pro parametr typu metody, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="deedb-115">If you require the flexibility of calling a generic class method with type arguments other than the ones provided when the class was instantiated, consider providing another identifier for the type parameter of the method, as shown in `GenericList2<T>` in the following example.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#26)]  
  
 <span data-ttu-id="deedb-116">Pomocí omezení povolte specializovanější operace parametrů typu v metodách.</span><span class="sxs-lookup"><span data-stu-id="deedb-116">Use constraints to enable more specialized operations on type parameters in methods.</span></span> <span data-ttu-id="deedb-117">Tuto verzi `Swap<T>`aplikace `SwapIfGreater<T>`, nyní pojmenovanou , lze <xref:System.IComparable%601>použít pouze s argumenty typu , které implementují .</span><span class="sxs-lookup"><span data-stu-id="deedb-117">This version of `Swap<T>`, now named `SwapIfGreater<T>`, can only be used with type arguments that implement <xref:System.IComparable%601>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#27)]  
  
 <span data-ttu-id="deedb-118">Obecné metody mohou být přetíženy na několik parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="deedb-118">Generic methods can be overloaded on several type parameters.</span></span> <span data-ttu-id="deedb-119">Například všechny následující metody mohou být umístěny ve stejné třídě:</span><span class="sxs-lookup"><span data-stu-id="deedb-119">For example, the following methods can all be located in the same class:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#28)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="deedb-120">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="deedb-120">C# Language Specification</span></span>  
 <span data-ttu-id="deedb-121">Další informace najdete v tématu [Specifikace jazyka C#](~/_csharplang/spec/classes.md#methods).</span><span class="sxs-lookup"><span data-stu-id="deedb-121">For more information, see the [C# Language Specification](~/_csharplang/spec/classes.md#methods).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deedb-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="deedb-122">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="deedb-123">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="deedb-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="deedb-124">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="deedb-124">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="deedb-125">Metody</span><span class="sxs-lookup"><span data-stu-id="deedb-125">Methods</span></span>](../classes-and-structs/methods.md)
