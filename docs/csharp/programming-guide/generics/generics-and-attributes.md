---
title: Obecné typy a atributy (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 3bfb4028fb5efce693abd83b40636b0149962e3b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339671"
---
# <a name="generics-and-attributes-c-programming-guide"></a><span data-ttu-id="eec5f-102">Obecné typy a atributy (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="eec5f-102">Generics and Attributes (C# Programming Guide)</span></span>
<span data-ttu-id="eec5f-103">Atributy lze použít jako obecné typy stejným způsobem jako neobecné typy.</span><span class="sxs-lookup"><span data-stu-id="eec5f-103">Attributes can be applied to generic types in the same way as non-generic types.</span></span> <span data-ttu-id="eec5f-104">Další informace o použití atributů naleznete v tématu [atributy](../../../csharp/programming-guide/concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="eec5f-104">For more information on applying attributes, see [Attributes](../../../csharp/programming-guide/concepts/attributes/index.md).</span></span>  
  
 <span data-ttu-id="eec5f-105">Chcete-li otevřít obecné typy, které jsou obecné typy, pro které žádný typ jsou zadané argumenty a uzavřené sestavené obecné typy, které zadat argumenty pro všechny parametry typu jsou povolená jenom vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="eec5f-105">Custom attributes are only permitted to reference open generic types, which are generic types for which no type arguments are supplied, and closed constructed generic types, which supply arguments for all type parameters.</span></span>  
  
 <span data-ttu-id="eec5f-106">Tento vlastní atribut použít v následujících příkladech:</span><span class="sxs-lookup"><span data-stu-id="eec5f-106">The following examples use this custom attribute:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#48](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_1.cs)]  
  
 <span data-ttu-id="eec5f-107">Atribut může odkazovat otevřený obecný typ.:</span><span class="sxs-lookup"><span data-stu-id="eec5f-107">An attribute can reference an open generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#49](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_2.cs)]  
  
 <span data-ttu-id="eec5f-108">Zadejte několik parametrů typu pomocí příslušného počtu čárkami.</span><span class="sxs-lookup"><span data-stu-id="eec5f-108">Specify multiple type parameters using the appropriate number of commas.</span></span> <span data-ttu-id="eec5f-109">V tomto příkladu `GenericClass2` má dva parametry typu:</span><span class="sxs-lookup"><span data-stu-id="eec5f-109">In this example, `GenericClass2` has two type parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#50](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_3.cs)]  
  
 <span data-ttu-id="eec5f-110">Atribut může odkazovat uzavřené sestavené obecného typu:</span><span class="sxs-lookup"><span data-stu-id="eec5f-110">An attribute can reference a closed constructed generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#51](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_4.cs)]  
  
 <span data-ttu-id="eec5f-111">Atribut, který odkazuje na parametr obecného typu způsobí chybu kompilace:</span><span class="sxs-lookup"><span data-stu-id="eec5f-111">An attribute that references a generic type parameter will cause a compile-time error:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#52](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_5.cs)]  
  
 <span data-ttu-id="eec5f-112">Obecný typ nemůže Zdědit z <xref:System.Attribute>:</span><span class="sxs-lookup"><span data-stu-id="eec5f-112">A generic type cannot inherit from <xref:System.Attribute>:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#53](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_6.cs)]  
  
 <span data-ttu-id="eec5f-113">Pokud chcete získat informace o obecný typ nebo parametr typu za běhu, můžete použít metody <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="eec5f-113">To obtain information about a generic type or type parameter at run time, you can use the methods of <xref:System.Reflection>.</span></span> <span data-ttu-id="eec5f-114">Další informace najdete v tématu [obecné typy a reflexe](../../../csharp/programming-guide/generics/generics-and-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="eec5f-114">For more information, see [Generics and Reflection](../../../csharp/programming-guide/generics/generics-and-reflection.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eec5f-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="eec5f-115">See Also</span></span>  
 [<span data-ttu-id="eec5f-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="eec5f-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="eec5f-117">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="eec5f-117">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
 [<span data-ttu-id="eec5f-118">Atributy</span><span class="sxs-lookup"><span data-stu-id="eec5f-118">Attributes</span></span>](../../../../docs/standard/attributes/index.md)
