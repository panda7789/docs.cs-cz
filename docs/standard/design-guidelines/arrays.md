---
title: Pole
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c957d4336527de8c11b763c31c1fdf0015b675b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="arrays"></a><span data-ttu-id="83938-102">Pole</span><span class="sxs-lookup"><span data-stu-id="83938-102">Arrays</span></span>
<span data-ttu-id="83938-103">**PROVEĎTE ✓** raději pomocí kolekcí přes pole v veřejná rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="83938-103">**✓ DO** prefer using collections over arrays in public APIs.</span></span> <span data-ttu-id="83938-104">[Kolekce](../../../docs/standard/design-guidelines/guidelines-for-collections.md) oddíl obsahuje podrobné informace o tom, jak si vybrat mezi kolekcí a pole.</span><span class="sxs-lookup"><span data-stu-id="83938-104">The [Collections](../../../docs/standard/design-guidelines/guidelines-for-collections.md) section provides details about how to choose between collections and arrays.</span></span>  
  
 <span data-ttu-id="83938-105">**X nesmí** použít pole pouze pro čtení.</span><span class="sxs-lookup"><span data-stu-id="83938-105">**X DO NOT** use read-only array fields.</span></span> <span data-ttu-id="83938-106">Vlastní pole je jen pro čtení a nelze změnit, ale lze změnit prvků v poli.</span><span class="sxs-lookup"><span data-stu-id="83938-106">The field itself is read-only and can't be changed, but elements in the array can be changed.</span></span>  
  
 <span data-ttu-id="83938-107">**✓ ZVAŽTE** pomocí Vícenásobná pole místo vícerozměrná pole.</span><span class="sxs-lookup"><span data-stu-id="83938-107">**✓ CONSIDER** using jagged arrays instead of multidimensional arrays.</span></span>  
  
 <span data-ttu-id="83938-108">Vícenásobná pole je pole s prvky, které jsou také pole.</span><span class="sxs-lookup"><span data-stu-id="83938-108">A jagged array is an array with elements that are also arrays.</span></span> <span data-ttu-id="83938-109">Pole, které tvoří elementy lze různých velikostí, což méně nevyužité místo pro některé sady dat (např. zhuštěný matice) ve srovnání s vícerozměrná pole.</span><span class="sxs-lookup"><span data-stu-id="83938-109">The arrays that make up the elements can be of different sizes, leading to less wasted space for some sets of data (e.g., sparse matrix) compared to multidimensional arrays.</span></span> <span data-ttu-id="83938-110">Navíc modulu CLR optimalizuje operace indexu na Vícenásobná pole, takže se mohou vykazovat lepší běhový výkon v některých scénářích.</span><span class="sxs-lookup"><span data-stu-id="83938-110">Furthermore, the CLR optimizes index operations on jagged arrays, so they might exhibit better runtime performance in some scenarios.</span></span>  
  
 <span data-ttu-id="83938-111">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="83938-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="83938-112">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="83938-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83938-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="83938-113">See Also</span></span>  
 <xref:System.Array>  
 [<span data-ttu-id="83938-114">Pokyny pro návrh Framework</span><span class="sxs-lookup"><span data-stu-id="83938-114">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="83938-115">Pokyny týkající se používání</span><span class="sxs-lookup"><span data-stu-id="83938-115">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
