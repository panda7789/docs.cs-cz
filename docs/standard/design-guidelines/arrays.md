---
title: Pole
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ac7e28c3172f2ed68d402e1d04a1664644c7f25
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47080946"
---
# <a name="arrays"></a><span data-ttu-id="4dc96-102">Pole</span><span class="sxs-lookup"><span data-stu-id="4dc96-102">Arrays</span></span>
<span data-ttu-id="4dc96-103">**✓ DO** raději pomocí kolekcí přes pole v veřejná rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="4dc96-103">**✓ DO** prefer using collections over arrays in public APIs.</span></span> <span data-ttu-id="4dc96-104">[Kolekce](../../../docs/standard/design-guidelines/guidelines-for-collections.md) čísti najdete podrobnosti o tom, jak si vybrat mezi kolekcí a polí.</span><span class="sxs-lookup"><span data-stu-id="4dc96-104">The [Collections](../../../docs/standard/design-guidelines/guidelines-for-collections.md) section provides details about how to choose between collections and arrays.</span></span>  
  
 <span data-ttu-id="4dc96-105">**X DO NOT** použít pole pouze pro čtení.</span><span class="sxs-lookup"><span data-stu-id="4dc96-105">**X DO NOT** use read-only array fields.</span></span> <span data-ttu-id="4dc96-106">Vlastní pole je jen pro čtení a nedá se změnit, ale prvky pole mohou být změněny.</span><span class="sxs-lookup"><span data-stu-id="4dc96-106">The field itself is read-only and can't be changed, but elements in the array can be changed.</span></span>  
  
 <span data-ttu-id="4dc96-107">**✓ CONSIDER** pomocí Vícenásobná pole místo vícerozměrná pole.</span><span class="sxs-lookup"><span data-stu-id="4dc96-107">**✓ CONSIDER** using jagged arrays instead of multidimensional arrays.</span></span>  
  
 <span data-ttu-id="4dc96-108">Vícenásobné pole je pole s prvky, které jsou také pole.</span><span class="sxs-lookup"><span data-stu-id="4dc96-108">A jagged array is an array with elements that are also arrays.</span></span> <span data-ttu-id="4dc96-109">Pole tvořící prvky mohou být různě velká, což vede k menšímu nevyužitému místu u některých sad dat (např. zhuštěný matice) ve srovnání s multidimenzionálními poli.</span><span class="sxs-lookup"><span data-stu-id="4dc96-109">The arrays that make up the elements can be of different sizes, leading to less wasted space for some sets of data (e.g., sparse matrix) compared to multidimensional arrays.</span></span> <span data-ttu-id="4dc96-110">Navíc CLR optimalizuje operace indexu pro vícenásobné pole, proto se může vykazovat lepší běhový výkon v některých scénářích.</span><span class="sxs-lookup"><span data-stu-id="4dc96-110">Furthermore, the CLR optimizes index operations on jagged arrays, so they might exhibit better runtime performance in some scenarios.</span></span>  
  
 <span data-ttu-id="4dc96-111">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="4dc96-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="4dc96-112">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="4dc96-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dc96-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4dc96-113">See also</span></span>

- <xref:System.Array>  
- [<span data-ttu-id="4dc96-114">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="4dc96-114">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="4dc96-115">Pokyny k používání</span><span class="sxs-lookup"><span data-stu-id="4dc96-115">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
