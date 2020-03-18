---
title: Obecné typy a atributy – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 47bf4e8f07a8b6778db8fa675d745d362dc10d7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75703023"
---
# <a name="generics-and-attributes-c-programming-guide"></a><span data-ttu-id="5f77e-102">Obecné typy a atributy (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="5f77e-102">Generics and Attributes (C# Programming Guide)</span></span>
<span data-ttu-id="5f77e-103">Atributy lze použít pro obecné typy stejným způsobem jako neobecné typy.</span><span class="sxs-lookup"><span data-stu-id="5f77e-103">Attributes can be applied to generic types in the same way as non-generic types.</span></span> <span data-ttu-id="5f77e-104">Další informace o použití atributů naleznete v [tématu Atributy](../concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="5f77e-104">For more information on applying attributes, see [Attributes](../concepts/attributes/index.md).</span></span>  
  
 <span data-ttu-id="5f77e-105">Vlastní atributy jsou povoleny pouze odkazovat na otevřené obecné typy, které jsou obecné typy, pro které jsou zadány žádné argumenty typu a uzavřené konstruované obecné typy, které poskytují argumenty pro všechny parametry typu.</span><span class="sxs-lookup"><span data-stu-id="5f77e-105">Custom attributes are only permitted to reference open generic types, which are generic types for which no type arguments are supplied, and closed constructed generic types, which supply arguments for all type parameters.</span></span>  
  
 <span data-ttu-id="5f77e-106">Následující příklady používají tento vlastní atribut:</span><span class="sxs-lookup"><span data-stu-id="5f77e-106">The following examples use this custom attribute:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#48)]  
  
 <span data-ttu-id="5f77e-107">Atribut může odkazovat na otevřený obecný typ:</span><span class="sxs-lookup"><span data-stu-id="5f77e-107">An attribute can reference an open generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#49)]  
  
 <span data-ttu-id="5f77e-108">Zadejte více parametrů typu pomocí příslušného počtu čárek.</span><span class="sxs-lookup"><span data-stu-id="5f77e-108">Specify multiple type parameters using the appropriate number of commas.</span></span> <span data-ttu-id="5f77e-109">V tomto `GenericClass2` příkladu má dva parametry typu:</span><span class="sxs-lookup"><span data-stu-id="5f77e-109">In this example, `GenericClass2` has two type parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#50)]  
  
 <span data-ttu-id="5f77e-110">Atribut může odkazovat na uzavřený vytvořený obecný typ:</span><span class="sxs-lookup"><span data-stu-id="5f77e-110">An attribute can reference a closed constructed generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#51)]  
  
 <span data-ttu-id="5f77e-111">Atribut, který odkazuje na parametr obecného typu, způsobí chybu v době kompilace:</span><span class="sxs-lookup"><span data-stu-id="5f77e-111">An attribute that references a generic type parameter will cause a compile-time error:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#52)]  
  
 <span data-ttu-id="5f77e-112">Obecný typ nemůže <xref:System.Attribute>dědit z :</span><span class="sxs-lookup"><span data-stu-id="5f77e-112">A generic type cannot inherit from <xref:System.Attribute>:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#53)]  
  
 <span data-ttu-id="5f77e-113">Chcete-li získat informace o obecném typu nebo parametru <xref:System.Reflection>typu za běhu, můžete použít metody .</span><span class="sxs-lookup"><span data-stu-id="5f77e-113">To obtain information about a generic type or type parameter at run time, you can use the methods of <xref:System.Reflection>.</span></span> <span data-ttu-id="5f77e-114">Další informace naleznete [v tématu Generics and Reflection](./generics-and-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="5f77e-114">For more information, see [Generics and Reflection](./generics-and-reflection.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f77e-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="5f77e-115">See also</span></span>

- [<span data-ttu-id="5f77e-116">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5f77e-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5f77e-117">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="5f77e-117">Generics</span></span>](./index.md)
- [<span data-ttu-id="5f77e-118">Atributy</span><span class="sxs-lookup"><span data-stu-id="5f77e-118">Attributes</span></span>](../../../standard/attributes/index.md)
