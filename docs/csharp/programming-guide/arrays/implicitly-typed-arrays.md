---
title: Implicitně typovaná pole (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], implicity-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
ms.openlocfilehash: 60d320b233986154c3c51c409bade24d0862dedd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33315201"
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a><span data-ttu-id="df821-102">Implicitně typovaná pole (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="df821-102">Implicitly Typed Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="df821-103">Implicitně typovaná pole ve kterém je odvodit typ pole instance, můžete vytvořit z prvky určené ve inicializátor pole.</span><span class="sxs-lookup"><span data-stu-id="df821-103">You can create an implicitly-typed array in which the type of the array instance is inferred from the elements specified in the array initializer.</span></span> <span data-ttu-id="df821-104">Pravidla pro všechny proměnné implicitně typované platit taky pro implicitně typovaná pole.</span><span class="sxs-lookup"><span data-stu-id="df821-104">The rules for any implicitly-typed variable also apply to implicitly-typed arrays.</span></span> <span data-ttu-id="df821-105">Další informace najdete v tématu [implicitně typované lokální proměnné](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="df821-105">For more information, see [Implicitly Typed Local Variables](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
 <span data-ttu-id="df821-106">Implicitně typovaná pole jsou obvykle použít ve výrazech dotazů společně s inicializátory objektu a kolekce a anonymní typy.</span><span class="sxs-lookup"><span data-stu-id="df821-106">Implicitly-typed arrays are usually used in query expressions together with anonymous types and object and collection initializers.</span></span>  
  
 <span data-ttu-id="df821-107">Následující příklady ukazují, jak vytvořit implicitně typovaná pole:</span><span class="sxs-lookup"><span data-stu-id="df821-107">The following examples show how to create an implicitly-typed array:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_1.cs)]  
  
 <span data-ttu-id="df821-108">V předchozím příkladu Všimněte si, že se implicitně typovaná pole žádné hranaté závorky použito na levé straně příkaz inicializace.</span><span class="sxs-lookup"><span data-stu-id="df821-108">In the previous example, notice that with implicitly-typed arrays, no square brackets are used on the left side of the initialization statement.</span></span> <span data-ttu-id="df821-109">Všimněte si také, že Vícenásobná pole jsou inicializovány pomocí `new []` stejně jako dimenze jednoho pole.</span><span class="sxs-lookup"><span data-stu-id="df821-109">Note also that jagged arrays are initialized by using `new []` just like single-dimension arrays.</span></span>  
  
## <a name="implicitly-typed-arrays-in-object-initializers"></a><span data-ttu-id="df821-110">Implicitně typovaná pole v inicializátory objektů</span><span class="sxs-lookup"><span data-stu-id="df821-110">Implicitly-typed Arrays in Object Initializers</span></span>  
 <span data-ttu-id="df821-111">Když vytvoříte anonymní typ, který obsahuje pole, pole musí implicitně typovaných ve inicializátoru objektu tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="df821-111">When you create an anonymous type that contains an array, the array must be implicitly typed in the type's object initializer.</span></span> <span data-ttu-id="df821-112">V následujícím příkladu `contacts` je implicitně typovaná pole typů anonymní, z nichž každý obsahuje pole s názvem `PhoneNumbers`.</span><span class="sxs-lookup"><span data-stu-id="df821-112">In the following example, `contacts` is an implicitly-typed array of anonymous types, each of which contains an array named `PhoneNumbers`.</span></span> <span data-ttu-id="df821-113">Všimněte si, že `var` – klíčové slovo není použít uvnitř inicializátory objektů.</span><span class="sxs-lookup"><span data-stu-id="df821-113">Note that the `var` keyword is not used inside the object initializers.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="df821-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="df821-114">See Also</span></span>  
 [<span data-ttu-id="df821-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="df821-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="df821-116">Implicitně typované lokální proměnné</span><span class="sxs-lookup"><span data-stu-id="df821-116">Implicitly Typed Local Variables</span></span>](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)  
 [<span data-ttu-id="df821-117">Pole</span><span class="sxs-lookup"><span data-stu-id="df821-117">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="df821-118">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="df821-118">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [<span data-ttu-id="df821-119">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="df821-119">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [<span data-ttu-id="df821-120">var</span><span class="sxs-lookup"><span data-stu-id="df821-120">var</span></span>](../../../csharp/language-reference/keywords/var.md)  
 [<span data-ttu-id="df821-121">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="df821-121">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)
