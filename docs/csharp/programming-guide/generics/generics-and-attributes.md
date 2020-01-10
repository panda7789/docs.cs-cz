---
title: Obecné typy a atributy – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 47bf4e8f07a8b6778db8fa675d745d362dc10d7d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75703023"
---
# <a name="generics-and-attributes-c-programming-guide"></a><span data-ttu-id="37ea3-102">Obecné typy a atributy (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="37ea3-102">Generics and Attributes (C# Programming Guide)</span></span>
<span data-ttu-id="37ea3-103">Atributy lze použít na obecné typy stejným způsobem jako jiné než obecné typy.</span><span class="sxs-lookup"><span data-stu-id="37ea3-103">Attributes can be applied to generic types in the same way as non-generic types.</span></span> <span data-ttu-id="37ea3-104">Další informace o použití atributů naleznete v tématu [Attributes](../concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="37ea3-104">For more information on applying attributes, see [Attributes](../concepts/attributes/index.md).</span></span>  
  
 <span data-ttu-id="37ea3-105">Vlastní atributy jsou povoleny pouze odkazům na otevřené obecné typy, což jsou obecné typy, pro které nejsou zadány žádné argumenty typu, a uzavřené konstruované obecné typy, které dodávají argumenty pro všechny parametry typu.</span><span class="sxs-lookup"><span data-stu-id="37ea3-105">Custom attributes are only permitted to reference open generic types, which are generic types for which no type arguments are supplied, and closed constructed generic types, which supply arguments for all type parameters.</span></span>  
  
 <span data-ttu-id="37ea3-106">Následující příklady používají tento vlastní atribut:</span><span class="sxs-lookup"><span data-stu-id="37ea3-106">The following examples use this custom attribute:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#48)]  
  
 <span data-ttu-id="37ea3-107">Atribut může odkazovat na otevřený obecný typ:</span><span class="sxs-lookup"><span data-stu-id="37ea3-107">An attribute can reference an open generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#49)]  
  
 <span data-ttu-id="37ea3-108">Zadejte více parametrů typu pomocí vhodného počtu čárek.</span><span class="sxs-lookup"><span data-stu-id="37ea3-108">Specify multiple type parameters using the appropriate number of commas.</span></span> <span data-ttu-id="37ea3-109">V tomto příkladu má `GenericClass2` dva parametry typu:</span><span class="sxs-lookup"><span data-stu-id="37ea3-109">In this example, `GenericClass2` has two type parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#50)]  
  
 <span data-ttu-id="37ea3-110">Atribut může odkazovat na uzavřený konstruovaný obecný typ:</span><span class="sxs-lookup"><span data-stu-id="37ea3-110">An attribute can reference a closed constructed generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#51)]  
  
 <span data-ttu-id="37ea3-111">Atribut, který odkazuje na parametr obecného typu, způsobí chybu při kompilaci:</span><span class="sxs-lookup"><span data-stu-id="37ea3-111">An attribute that references a generic type parameter will cause a compile-time error:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#52)]  
  
 <span data-ttu-id="37ea3-112">Obecný typ nemůže dědit z <xref:System.Attribute>:</span><span class="sxs-lookup"><span data-stu-id="37ea3-112">A generic type cannot inherit from <xref:System.Attribute>:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#53)]  
  
 <span data-ttu-id="37ea3-113">Chcete-li získat informace o obecném typu nebo parametru typu v době běhu, můžete použít metody <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="37ea3-113">To obtain information about a generic type or type parameter at run time, you can use the methods of <xref:System.Reflection>.</span></span> <span data-ttu-id="37ea3-114">Další informace naleznete v tématu [Obecné typy a reflexe](./generics-and-reflection.md) .</span><span class="sxs-lookup"><span data-stu-id="37ea3-114">For more information, see [Generics and Reflection](./generics-and-reflection.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37ea3-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="37ea3-115">See also</span></span>

- [<span data-ttu-id="37ea3-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="37ea3-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="37ea3-117">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="37ea3-117">Generics</span></span>](./index.md)
- [<span data-ttu-id="37ea3-118">Atributy</span><span class="sxs-lookup"><span data-stu-id="37ea3-118">Attributes</span></span>](../../../standard/attributes/index.md)
