---
title: Obecné typy a atributy - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 5b65ae794e99602fc84f674be5ec0502d4588a59
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607699"
---
# <a name="generics-and-attributes-c-programming-guide"></a><span data-ttu-id="356fc-102">Obecné typy a atributy (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="356fc-102">Generics and Attributes (C# Programming Guide)</span></span>
<span data-ttu-id="356fc-103">Atributy lze použít na obecných typech stejným způsobem jako obecné typy.</span><span class="sxs-lookup"><span data-stu-id="356fc-103">Attributes can be applied to generic types in the same way as non-generic types.</span></span> <span data-ttu-id="356fc-104">Další informace o použití atributů naleznete v tématu [atributy](../../../csharp/programming-guide/concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="356fc-104">For more information on applying attributes, see [Attributes](../../../csharp/programming-guide/concepts/attributes/index.md).</span></span>  
  
 <span data-ttu-id="356fc-105">Vlastní atributy jsou povolené jenom tak, aby odkazovaly otevřených obecných typů, které jsou obecné typy, pro kterou žádný typ jsou zadané argumenty a uzavřený konstruovaný obecné typy, které zadat argumenty pro všechny parametry typu.</span><span class="sxs-lookup"><span data-stu-id="356fc-105">Custom attributes are only permitted to reference open generic types, which are generic types for which no type arguments are supplied, and closed constructed generic types, which supply arguments for all type parameters.</span></span>  
  
 <span data-ttu-id="356fc-106">Následující příklady používají tento vlastní atribut:</span><span class="sxs-lookup"><span data-stu-id="356fc-106">The following examples use this custom attribute:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#48](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_1.cs)]  
  
 <span data-ttu-id="356fc-107">Otevřený obecný typ. může odkazovat na atribut:</span><span class="sxs-lookup"><span data-stu-id="356fc-107">An attribute can reference an open generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#49](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_2.cs)]  
  
 <span data-ttu-id="356fc-108">Zadejte více parametrů typu pomocí příslušného počtu čárkami.</span><span class="sxs-lookup"><span data-stu-id="356fc-108">Specify multiple type parameters using the appropriate number of commas.</span></span> <span data-ttu-id="356fc-109">V tomto příkladu `GenericClass2` má dva parametry typu:</span><span class="sxs-lookup"><span data-stu-id="356fc-109">In this example, `GenericClass2` has two type parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#50](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_3.cs)]  
  
 <span data-ttu-id="356fc-110">Uzavřený Konstruovaný obecný typ může odkazovat na atribut:</span><span class="sxs-lookup"><span data-stu-id="356fc-110">An attribute can reference a closed constructed generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#51](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_4.cs)]  
  
 <span data-ttu-id="356fc-111">Atribut, který odkazuje na parametr obecného typu způsobí chybu kompilace:</span><span class="sxs-lookup"><span data-stu-id="356fc-111">An attribute that references a generic type parameter will cause a compile-time error:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#52](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_5.cs)]  
  
 <span data-ttu-id="356fc-112">Obecný typ nelze dědit z <xref:System.Attribute>:</span><span class="sxs-lookup"><span data-stu-id="356fc-112">A generic type cannot inherit from <xref:System.Attribute>:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#53](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_6.cs)]  
  
 <span data-ttu-id="356fc-113">Pokud chcete získat informace o obecném typu nebo parametr typu v době běhu, můžete použít metody <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="356fc-113">To obtain information about a generic type or type parameter at run time, you can use the methods of <xref:System.Reflection>.</span></span> <span data-ttu-id="356fc-114">Další informace najdete v tématu [obecné typy a reflexe](../../../csharp/programming-guide/generics/generics-and-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="356fc-114">For more information, see [Generics and Reflection](../../../csharp/programming-guide/generics/generics-and-reflection.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="356fc-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="356fc-115">See also</span></span>

- [<span data-ttu-id="356fc-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="356fc-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="356fc-117">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="356fc-117">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
- [<span data-ttu-id="356fc-118">Atributy</span><span class="sxs-lookup"><span data-stu-id="356fc-118">Attributes</span></span>](../../../../docs/standard/attributes/index.md)
