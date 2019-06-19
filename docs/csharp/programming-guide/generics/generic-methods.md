---
title: Obecné metody - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
ms.openlocfilehash: 443d4367cc64eb7f9054b2cd52bef59e589f55b3
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2019
ms.locfileid: "67170258"
---
# <a name="generic-methods-c-programming-guide"></a><span data-ttu-id="cbe87-102">Obecné metody (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="cbe87-102">Generic Methods (C# Programming Guide)</span></span>
<span data-ttu-id="cbe87-103">Obecná metoda je metoda, která je deklarována s parametry typu, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="cbe87-103">A generic method is a method that is declared with type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#22)]  
  
 <span data-ttu-id="cbe87-104">Následující příklad kódu ukazuje jeden způsob, jak volat metodu pomocí `int` pro argument typu:</span><span class="sxs-lookup"><span data-stu-id="cbe87-104">The following code example shows one way to call the method by using `int` for the type argument:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#23)]  
  
 <span data-ttu-id="cbe87-105">Také můžete vynechat argument typu a kompilátor odvodí.</span><span class="sxs-lookup"><span data-stu-id="cbe87-105">You can also omit the type argument and the compiler will infer it.</span></span> <span data-ttu-id="cbe87-106">Následující volání `Swap` je ekvivalentem předchozího volání:</span><span class="sxs-lookup"><span data-stu-id="cbe87-106">The following call to `Swap` is equivalent to the previous call:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#24)]  
  
 <span data-ttu-id="cbe87-107">Stejná pravidla pro odvození typu platí pro statické metody a metody instance.</span><span class="sxs-lookup"><span data-stu-id="cbe87-107">The same rules for type inference apply to static methods and instance methods.</span></span> <span data-ttu-id="cbe87-108">Kompilátor může odvodit typ parametrů na základě argumentů metody, které můžete předat nelze jej odvodit jenom z omezení parametry typu nebo návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cbe87-108">The compiler can infer the type parameters based on the method arguments you pass in; it cannot infer the type parameters only from a constraint or return value.</span></span> <span data-ttu-id="cbe87-109">Odvození typu proměnné proto nefunguje s metodami, které mají žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="cbe87-109">Therefore type inference does not work with methods that have no parameters.</span></span> <span data-ttu-id="cbe87-110">Odvození typu vyvolá v době kompilace předtím, než kompilátor pokusí přeložit podpisy přetížené metody.</span><span class="sxs-lookup"><span data-stu-id="cbe87-110">Type inference occurs at compile time before the compiler tries to resolve overloaded method signatures.</span></span> <span data-ttu-id="cbe87-111">Kompilátor použije logiku odvození typu na všechny obecné metody, které mají stejný název.</span><span class="sxs-lookup"><span data-stu-id="cbe87-111">The compiler applies type inference logic to all generic methods that share the same name.</span></span> <span data-ttu-id="cbe87-112">V kroku rozlišení přetížení kompilátor obsahuje pouze tyto obecné metody, na které bylo úspěšné odvození typu proměnné.</span><span class="sxs-lookup"><span data-stu-id="cbe87-112">In the overload resolution step, the compiler includes only those generic methods on which type inference succeeded.</span></span>  
  
 <span data-ttu-id="cbe87-113">V rámci obecné třídy neobecné metody mají přístup k úrovni třídy typové parametry, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="cbe87-113">Within a generic class, non-generic methods can access the class-level type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#25)]  
  
 <span data-ttu-id="cbe87-114">Při definování obecné metody, která má stejné parametry typu jako obsahující třídu, kompilátor vygeneruje upozornění [CS0693](../../misc/cs0693.md) protože v rámci oboru metody argument zadaný pro vnitřní `T` skryje argumentu zadaný pro vnější `T`.</span><span class="sxs-lookup"><span data-stu-id="cbe87-114">If you define a generic method that takes the same type parameters as the containing class, the compiler generates warning [CS0693](../../misc/cs0693.md) because within the method scope, the argument supplied for the inner `T` hides the argument supplied for the outer `T`.</span></span> <span data-ttu-id="cbe87-115">Pokud požadujete flexibilitu volání metody obecnou třídu s argumenty typů než ty, pokud byla vytvořena instance třídy, zvažte poskytnutí jiný identifikátor pro typ parametru metody, jak je znázorněno v `GenericList2<T>` následující Příklad.</span><span class="sxs-lookup"><span data-stu-id="cbe87-115">If you require the flexibility of calling a generic class method with type arguments other than the ones provided when the class was instantiated, consider providing another identifier for the type parameter of the method, as shown in `GenericList2<T>` in the following example.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#26)]  
  
 <span data-ttu-id="cbe87-116">Umožňuje povolit více specializované operace u parametrů typu v metodách omezení.</span><span class="sxs-lookup"><span data-stu-id="cbe87-116">Use constraints to enable more specialized operations on type parameters in methods.</span></span> <span data-ttu-id="cbe87-117">Tato verze `Swap<T>`teď s názvem `SwapIfGreater<T>`, lze použít pouze s argumenty typů, které implementují <xref:System.IComparable%601>.</span><span class="sxs-lookup"><span data-stu-id="cbe87-117">This version of `Swap<T>`, now named `SwapIfGreater<T>`, can only be used with type arguments that implement <xref:System.IComparable%601>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#27)]  
  
 <span data-ttu-id="cbe87-118">Obecné metody lze přetížit na několik parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="cbe87-118">Generic methods can be overloaded on several type parameters.</span></span> <span data-ttu-id="cbe87-119">Například následující metody můžete všechny nacházet ve stejné třídě:</span><span class="sxs-lookup"><span data-stu-id="cbe87-119">For example, the following methods can all be located in the same class:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#28)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="cbe87-120">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cbe87-120">C# Language Specification</span></span>  
 <span data-ttu-id="cbe87-121">Další informace najdete v tématu [Specifikace jazyka C#](~/_csharplang/spec/classes.md#methods).</span><span class="sxs-lookup"><span data-stu-id="cbe87-121">For more information, see the [C# Language Specification](~/_csharplang/spec/classes.md#methods).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbe87-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cbe87-122">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="cbe87-123">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="cbe87-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="cbe87-124">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="cbe87-124">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
- [<span data-ttu-id="cbe87-125">Metody</span><span class="sxs-lookup"><span data-stu-id="cbe87-125">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
