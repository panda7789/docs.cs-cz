---
title: "Obecné typy a atributy (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5535334514afb0b9891dfce2e0cc0a0e95526069
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="generics-and-attributes-c-programming-guide"></a><span data-ttu-id="6daaf-102">Obecné typy a atributy (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="6daaf-102">Generics and Attributes (C# Programming Guide)</span></span>
<span data-ttu-id="6daaf-103">Atributy lze použít jako obecné typy stejným způsobem jako neobecné typy.</span><span class="sxs-lookup"><span data-stu-id="6daaf-103">Attributes can be applied to generic types in the same way as non-generic types.</span></span> <span data-ttu-id="6daaf-104">Další informace o použití atributů naleznete v tématu [atributy](../../../csharp/programming-guide/concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="6daaf-104">For more information on applying attributes, see [Attributes](../../../csharp/programming-guide/concepts/attributes/index.md).</span></span>  
  
 <span data-ttu-id="6daaf-105">Chcete-li otevřít obecné typy, které jsou obecné typy, pro které žádný typ jsou zadané argumenty a uzavřené sestavené obecné typy, které zadat argumenty pro všechny parametry typu jsou povolená jenom vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="6daaf-105">Custom attributes are only permitted to reference open generic types, which are generic types for which no type arguments are supplied, and closed constructed generic types, which supply arguments for all type parameters.</span></span>  
  
 <span data-ttu-id="6daaf-106">Tento vlastní atribut použít v následujících příkladech:</span><span class="sxs-lookup"><span data-stu-id="6daaf-106">The following examples use this custom attribute:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#48](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_1.cs)]  
  
 <span data-ttu-id="6daaf-107">Atribut může odkazovat otevřený obecný typ.:</span><span class="sxs-lookup"><span data-stu-id="6daaf-107">An attribute can reference an open generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#49](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_2.cs)]  
  
 <span data-ttu-id="6daaf-108">Zadejte několik parametrů typu pomocí příslušného počtu čárkami.</span><span class="sxs-lookup"><span data-stu-id="6daaf-108">Specify multiple type parameters using the appropriate number of commas.</span></span> <span data-ttu-id="6daaf-109">V tomto příkladu `GenericClass2` má dva parametry typu:</span><span class="sxs-lookup"><span data-stu-id="6daaf-109">In this example, `GenericClass2` has two type parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#50](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_3.cs)]  
  
 <span data-ttu-id="6daaf-110">Atribut může odkazovat uzavřené sestavené obecného typu:</span><span class="sxs-lookup"><span data-stu-id="6daaf-110">An attribute can reference a closed constructed generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#51](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_4.cs)]  
  
 <span data-ttu-id="6daaf-111">Atribut, který odkazuje na parametr obecného typu způsobí chybu kompilace:</span><span class="sxs-lookup"><span data-stu-id="6daaf-111">An attribute that references a generic type parameter will cause a compile-time error:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#52](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_5.cs)]  
  
 <span data-ttu-id="6daaf-112">Obecný typ nemůže Zdědit z <xref:System.Attribute>:</span><span class="sxs-lookup"><span data-stu-id="6daaf-112">A generic type cannot inherit from <xref:System.Attribute>:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#53](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_6.cs)]  
  
 <span data-ttu-id="6daaf-113">Pokud chcete získat informace o obecný typ nebo parametr typu za běhu, můžete použít metody <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="6daaf-113">To obtain information about a generic type or type parameter at run time, you can use the methods of <xref:System.Reflection>.</span></span> <span data-ttu-id="6daaf-114">Další informace najdete v tématu [obecné typy a reflexe](../../../csharp/programming-guide/generics/generics-and-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="6daaf-114">For more information, see [Generics and Reflection](../../../csharp/programming-guide/generics/generics-and-reflection.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6daaf-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="6daaf-115">See Also</span></span>  
 [<span data-ttu-id="6daaf-116">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="6daaf-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6daaf-117">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="6daaf-117">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
 [<span data-ttu-id="6daaf-118">Atributy</span><span class="sxs-lookup"><span data-stu-id="6daaf-118">Attributes</span></span>](https://msdn.microsoft.com/library/5x6cd29c)
