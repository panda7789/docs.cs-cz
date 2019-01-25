---
title: Implicitně typované pole - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], implicity-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
ms.openlocfilehash: 2b52bca57bde2fd198fd1621cb8a8f7dfc73ec9e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54740759"
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a><span data-ttu-id="ef7e6-102">Implicitně typovaná pole (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="ef7e6-102">Implicitly Typed Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="ef7e6-103">Implicitně typovaná pole ve kterém je odvozený typ pole instance můžete vytvořit z elementů zadaný v inicializátoru pole.</span><span class="sxs-lookup"><span data-stu-id="ef7e6-103">You can create an implicitly-typed array in which the type of the array instance is inferred from the elements specified in the array initializer.</span></span> <span data-ttu-id="ef7e6-104">Pravidla pro všechny implicitně typované proměnné platí také pro implicitně typovaná pole.</span><span class="sxs-lookup"><span data-stu-id="ef7e6-104">The rules for any implicitly-typed variable also apply to implicitly-typed arrays.</span></span> <span data-ttu-id="ef7e6-105">Další informace najdete v tématu [implicitně typované lokální proměnné](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="ef7e6-105">For more information, see [Implicitly Typed Local Variables](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
 <span data-ttu-id="ef7e6-106">Implicitně typovaná pole se obvykle používají ve výrazech dotazů spolu s inicializátory objektu a kolekce a anonymní typy.</span><span class="sxs-lookup"><span data-stu-id="ef7e6-106">Implicitly-typed arrays are usually used in query expressions together with anonymous types and object and collection initializers.</span></span>  
  
 <span data-ttu-id="ef7e6-107">Následující příklady ukazují, jak vytvořit implicitně typované pole:</span><span class="sxs-lookup"><span data-stu-id="ef7e6-107">The following examples show how to create an implicitly-typed array:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_1.cs)]  
  
 <span data-ttu-id="ef7e6-108">V předchozím příkladu Všimněte si, že se implicitně typovaná pole se žádné hranaté závorky používají na levé straně výrazu inicializace.</span><span class="sxs-lookup"><span data-stu-id="ef7e6-108">In the previous example, notice that with implicitly-typed arrays, no square brackets are used on the left side of the initialization statement.</span></span> <span data-ttu-id="ef7e6-109">Všimněte si také, že Vícenásobná pole jsou inicializovány pomocí `new []` stejně jako pole jednou dimenzí.</span><span class="sxs-lookup"><span data-stu-id="ef7e6-109">Note also that jagged arrays are initialized by using `new []` just like single-dimension arrays.</span></span>  
  
## <a name="implicitly-typed-arrays-in-object-initializers"></a><span data-ttu-id="ef7e6-110">Implicitně typovaná pole v inicializátorech objektů</span><span class="sxs-lookup"><span data-stu-id="ef7e6-110">Implicitly-typed Arrays in Object Initializers</span></span>

 <span data-ttu-id="ef7e6-111">Při vytváření anonymního typu, který obsahuje pole, musí být pole implicitně typované v inicializátoru objektu tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="ef7e6-111">When you create an anonymous type that contains an array, the array must be implicitly typed in the type's object initializer.</span></span> <span data-ttu-id="ef7e6-112">V následujícím příkladu `contacts` je implicitně typované pole anonymních typů, z nichž každý obsahuje pole s názvem `PhoneNumbers`.</span><span class="sxs-lookup"><span data-stu-id="ef7e6-112">In the following example, `contacts` is an implicitly-typed array of anonymous types, each of which contains an array named `PhoneNumbers`.</span></span> <span data-ttu-id="ef7e6-113">Všimněte si, `var` – klíčové slovo se nepoužívá v inicializátorech objektů.</span><span class="sxs-lookup"><span data-stu-id="ef7e6-113">Note that the `var` keyword is not used inside the object initializers.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="ef7e6-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ef7e6-114">See also</span></span>

- [<span data-ttu-id="ef7e6-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ef7e6-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="ef7e6-116">Implicitně typované lokální proměnné</span><span class="sxs-lookup"><span data-stu-id="ef7e6-116">Implicitly Typed Local Variables</span></span>](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
- [<span data-ttu-id="ef7e6-117">Pole</span><span class="sxs-lookup"><span data-stu-id="ef7e6-117">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)
- [<span data-ttu-id="ef7e6-118">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="ef7e6-118">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="ef7e6-119">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="ef7e6-119">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
- [<span data-ttu-id="ef7e6-120">var</span><span class="sxs-lookup"><span data-stu-id="ef7e6-120">var</span></span>](../../../csharp/language-reference/keywords/var.md)
- [<span data-ttu-id="ef7e6-121">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="ef7e6-121">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)
