---
title: Obecné typy a atributy (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 0fe2d61001584aa7c175500bfa754b2ae2244660
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44209248"
---
# <a name="generics-and-attributes-c-programming-guide"></a><span data-ttu-id="d6ce5-102">Obecné typy a atributy (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="d6ce5-102">Generics and Attributes (C# Programming Guide)</span></span>
<span data-ttu-id="d6ce5-103">Atributy lze použít na obecných typech stejným způsobem jako obecné typy.</span><span class="sxs-lookup"><span data-stu-id="d6ce5-103">Attributes can be applied to generic types in the same way as non-generic types.</span></span> <span data-ttu-id="d6ce5-104">Další informace o použití atributů naleznete v tématu [atributy](../../../csharp/programming-guide/concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="d6ce5-104">For more information on applying attributes, see [Attributes](../../../csharp/programming-guide/concepts/attributes/index.md).</span></span>  
  
 <span data-ttu-id="d6ce5-105">Vlastní atributy jsou povolené jenom tak, aby odkazovaly otevřených obecných typů, které jsou obecné typy, pro kterou žádný typ jsou zadané argumenty a uzavřený konstruovaný obecné typy, které zadat argumenty pro všechny parametry typu.</span><span class="sxs-lookup"><span data-stu-id="d6ce5-105">Custom attributes are only permitted to reference open generic types, which are generic types for which no type arguments are supplied, and closed constructed generic types, which supply arguments for all type parameters.</span></span>  
  
 <span data-ttu-id="d6ce5-106">Následující příklady používají tento vlastní atribut:</span><span class="sxs-lookup"><span data-stu-id="d6ce5-106">The following examples use this custom attribute:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#48](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_1.cs)]  
  
 <span data-ttu-id="d6ce5-107">Otevřený obecný typ. může odkazovat na atribut:</span><span class="sxs-lookup"><span data-stu-id="d6ce5-107">An attribute can reference an open generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#49](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_2.cs)]  
  
 <span data-ttu-id="d6ce5-108">Zadejte více parametrů typu pomocí příslušného počtu čárkami.</span><span class="sxs-lookup"><span data-stu-id="d6ce5-108">Specify multiple type parameters using the appropriate number of commas.</span></span> <span data-ttu-id="d6ce5-109">V tomto příkladu `GenericClass2` má dva parametry typu:</span><span class="sxs-lookup"><span data-stu-id="d6ce5-109">In this example, `GenericClass2` has two type parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#50](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_3.cs)]  
  
 <span data-ttu-id="d6ce5-110">Uzavřený Konstruovaný obecný typ může odkazovat na atribut:</span><span class="sxs-lookup"><span data-stu-id="d6ce5-110">An attribute can reference a closed constructed generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#51](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_4.cs)]  
  
 <span data-ttu-id="d6ce5-111">Atribut, který odkazuje na parametr obecného typu způsobí chybu kompilace:</span><span class="sxs-lookup"><span data-stu-id="d6ce5-111">An attribute that references a generic type parameter will cause a compile-time error:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#52](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_5.cs)]  
  
 <span data-ttu-id="d6ce5-112">Obecný typ nelze dědit z <xref:System.Attribute>:</span><span class="sxs-lookup"><span data-stu-id="d6ce5-112">A generic type cannot inherit from <xref:System.Attribute>:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#53](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_6.cs)]  
  
 <span data-ttu-id="d6ce5-113">Pokud chcete získat informace o obecném typu nebo parametr typu v době běhu, můžete použít metody <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="d6ce5-113">To obtain information about a generic type or type parameter at run time, you can use the methods of <xref:System.Reflection>.</span></span> <span data-ttu-id="d6ce5-114">Další informace najdete v tématu [obecné typy a reflexe](../../../csharp/programming-guide/generics/generics-and-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="d6ce5-114">For more information, see [Generics and Reflection](../../../csharp/programming-guide/generics/generics-and-reflection.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6ce5-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6ce5-115">See Also</span></span>

- [<span data-ttu-id="d6ce5-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d6ce5-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="d6ce5-117">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="d6ce5-117">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
- [<span data-ttu-id="d6ce5-118">Atributy</span><span class="sxs-lookup"><span data-stu-id="d6ce5-118">Attributes</span></span>](../../../../docs/standard/attributes/index.md)
