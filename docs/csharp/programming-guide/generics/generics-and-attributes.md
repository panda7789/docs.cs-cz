---
title: Obecné typy a atributy – Průvodce programováním v C#
description: Přečtěte si o použití atributů u obecných typů. Podívejte se na příklady kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 17556af2e1bc2963de953cea242d7000509acbcd
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299874"
---
# <a name="generics-and-attributes-c-programming-guide"></a><span data-ttu-id="86b80-104">Obecné typy a atributy (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="86b80-104">Generics and Attributes (C# Programming Guide)</span></span>
<span data-ttu-id="86b80-105">Atributy lze použít na obecné typy stejným způsobem jako jiné než obecné typy.</span><span class="sxs-lookup"><span data-stu-id="86b80-105">Attributes can be applied to generic types in the same way as non-generic types.</span></span> <span data-ttu-id="86b80-106">Další informace o použití atributů naleznete v tématu [Attributes](../concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="86b80-106">For more information on applying attributes, see [Attributes](../concepts/attributes/index.md).</span></span>  
  
 <span data-ttu-id="86b80-107">Vlastní atributy jsou povoleny pouze odkazům na otevřené obecné typy, což jsou obecné typy, pro které nejsou zadány žádné argumenty typu, a uzavřené konstruované obecné typy, které dodávají argumenty pro všechny parametry typu.</span><span class="sxs-lookup"><span data-stu-id="86b80-107">Custom attributes are only permitted to reference open generic types, which are generic types for which no type arguments are supplied, and closed constructed generic types, which supply arguments for all type parameters.</span></span>  
  
 <span data-ttu-id="86b80-108">Následující příklady používají tento vlastní atribut:</span><span class="sxs-lookup"><span data-stu-id="86b80-108">The following examples use this custom attribute:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#48)]  
  
 <span data-ttu-id="86b80-109">Atribut může odkazovat na otevřený obecný typ:</span><span class="sxs-lookup"><span data-stu-id="86b80-109">An attribute can reference an open generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#49)]  
  
 <span data-ttu-id="86b80-110">Zadejte více parametrů typu pomocí vhodného počtu čárek.</span><span class="sxs-lookup"><span data-stu-id="86b80-110">Specify multiple type parameters using the appropriate number of commas.</span></span> <span data-ttu-id="86b80-111">V tomto příkladu `GenericClass2` má dva parametry typu:</span><span class="sxs-lookup"><span data-stu-id="86b80-111">In this example, `GenericClass2` has two type parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#50)]  
  
 <span data-ttu-id="86b80-112">Atribut může odkazovat na uzavřený konstruovaný obecný typ:</span><span class="sxs-lookup"><span data-stu-id="86b80-112">An attribute can reference a closed constructed generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#51)]  
  
 <span data-ttu-id="86b80-113">Atribut, který odkazuje na parametr obecného typu, způsobí chybu při kompilaci:</span><span class="sxs-lookup"><span data-stu-id="86b80-113">An attribute that references a generic type parameter will cause a compile-time error:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#52)]  
  
 <span data-ttu-id="86b80-114">Obecný typ nemůže dědit z <xref:System.Attribute> :</span><span class="sxs-lookup"><span data-stu-id="86b80-114">A generic type cannot inherit from <xref:System.Attribute>:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#53)]  
  
 <span data-ttu-id="86b80-115">Chcete-li získat informace o obecném typu nebo parametru typu v době běhu, můžete použít metody <xref:System.Reflection> .</span><span class="sxs-lookup"><span data-stu-id="86b80-115">To obtain information about a generic type or type parameter at run time, you can use the methods of <xref:System.Reflection>.</span></span> <span data-ttu-id="86b80-116">Další informace naleznete v tématu [Obecné typy a reflexe](./generics-and-reflection.md) .</span><span class="sxs-lookup"><span data-stu-id="86b80-116">For more information, see [Generics and Reflection](./generics-and-reflection.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86b80-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="86b80-117">See also</span></span>

- [<span data-ttu-id="86b80-118">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="86b80-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="86b80-119">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="86b80-119">Generics</span></span>](./index.md)
- [<span data-ttu-id="86b80-120">Atributy</span><span class="sxs-lookup"><span data-stu-id="86b80-120">Attributes</span></span>](../../../standard/attributes/index.md)
